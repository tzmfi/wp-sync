---
ID: 562
post_title: Tervetuloa liikkeen sivuille
author: Teemu Koskimäki
post_excerpt: ""
layout: page
permalink: http://www.zeitgeist.fi/
published: true
post_date: 2015-03-01 21:36:36
---
<div class="span4" style="margin: 0">
<div class="fb-page" data-href="https://www.facebook.com/ZeitgeistSuomi" data-tabs="timeline" data-width="371" data-height="530" data-small-header="false" data-adapt-container-width="true" data-hide-cover="false" data-show-facepile="true"><div class="fb-xfbml-parse-ignore"><blockquote cite="https://www.facebook.com/ZeitgeistSuomi"><a href="https://www.facebook.com/ZeitgeistSuomi">Liikkeen Facebook-sivut</a></blockquote></div></div>
</div>

<div class="span4" id="zmap">
  <iframe style="z-index: -100" src="https://www.google.com/maps/d/embed?mid=1hcGPRJLOlHoD3D9i9KvrbBlW02s"></iframe><div class="add_to_map"><a target="_blank" href="https://goo.gl/forms/HaXBFwqSfqQPQIkD3">Lisää itsesi kartalle tästä!</a></div> <!-- no line change before because p element was appearing -->
  <div class="loading"><img src="http://www.zeitgeist.fi/wp-content/uploads/ladataan.gif" alt="Karttaa ladataan..."/></div>
</div>

<div class="span4 quote-column">
[insert_php]
  $quotes = array(791,792,793,794,795,796,797,798,799,800,801,802,803,804,805,806,807,808);
  $quote_index = rand(0, count($quotes) - 1);
  $result_array = wp_get_attachment_image_src($quotes[$quote_index], 'large');
  echo '<a href="http://www.zeitgeist.fi/toiminta2/julisteiden-jako-projekti-2016/"><img src="'.$result_array[0].'" alt="Z-mietilause"/></a>';
[/insert_php]<div class="explanation">Katso ja osallistu liikkeen julistekampanjaan!</div>
</div>

<div style="clear:both"></div>

<hr class="featurette-divider" style="margin-top: 48px">

[insert_php]
echo '<div class="latest-articles">';
$args = array(
	'posts_per_page'   => 3,
	'offset'           => 0,
	'category'         => '',
	'category_name'    => '',
	'orderby'          => 'date',
	'order'            => 'DESC',
	'include'          => '',
	'exclude'          => '',
	'meta_key'         => '',
	'meta_value'       => '',
	'post_type'        => 'post',
	'post_mime_type'   => '',
	'post_parent'      => '',
	'author'	   => '',
	'author_name'	   => '',
	'post_status'      => 'publish',
	'suppress_filters' => true 
);

$posts = get_posts($args);
$first_post = true;
foreach ($posts as $post) {
        $permalink = get_permalink($post);
        $date_str = date('j.n.Y', strtotime($post->post_date));
        $style = '';
        if ($first_post) {
            $style = 'margin: 0';
            $first_post = false;
        }
	echo '<div class="span4" style="padding-bottom: 24px; ' . $style . '">';
	echo '<h3><a href="'. $permalink .'">'. $post->post_title . ' <span class="date"> -&nbsp;' . $date_str . '</span></a></h3>';
        echo '<p>' . mb_substr(strip_tags($post->post_content), 0, 250) . '...</p>';
        echo '<br/><a class="btn btn-primary fp-button" style="margin-top: 8px" href="' . $permalink . '">Lue lisää &raquo;</a>';
	echo '</div>';     
}
echo '</div>';
[/insert_php]

<div style="clear:both"></div>