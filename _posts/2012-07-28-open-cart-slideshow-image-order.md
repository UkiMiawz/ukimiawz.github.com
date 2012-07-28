---
layout: post
title: "Open Cart Slideshow Image Order"
description: "Fixing orders in Opencart Slideshow images"
category: OpenCart
tags: [Opencart, CMS, ecommerce]
---
{% include JB/setup %}

In my attempt to use slideshow module in OpenCart, I came up with a troublesome problem.

I've uploaded my images in the correct order for the slides but opencart manage to jumble the images order everytime I hit the 'Save' button. This thing might not be a big problem if you're just using it like usual but I used thumbnails in my Opencart theme's slideshow and the jumbling down done by Opencart made my image thumbnails mismatch the images in slides. Oh great -_-

It turns out I have to alter the SQL query used to fetch the images a little bit -_-

The altered file : `/catalog/model/design/banner.php`

## The Original Code

	<?php
		class ModelDesignBanner extends Model {	
			public function getBanner($banner_id) {
				$query = $this->db->query("SELECT * FROM " . DB_PREFIX . "banner_image bi LEFT JOIN " . DB_PREFIX . "banner_image_description bid ON (bi.banner_image_id  = bid.banner_image_id) WHERE bi.banner_id = '" . (int)$banner_id . "' AND bid.language_id = '" . (int)$this->config->get('config_language_id') . "'");
		
				return $query->rows;
			}
		}
	?>

## The Altered Code

Add `ORDER BY image ASC`

	<?php
		class ModelDesignBanner extends Model {	
			public function getBanner($banner_id) {
				$query = $this->db->query("SELECT * FROM " . DB_PREFIX . "banner_image bi LEFT JOIN " . DB_PREFIX . "banner_image_description bid ON (bi.banner_image_id  = bid.banner_image_id) WHERE bi.banner_id = '" . (int)$banner_id . "' AND bid.language_id = '" . (int)$this->config->get('config_language_id') . "' ORDER BY image ASC");
		
				return $query->rows;
			}
		}
	?>