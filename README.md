Pagination-PHP-Class
====================

A basic class for creating easy pagination lists. Feel free to contribute. :)

Freely distributable under the MIT License.

##Basic Usage
=============

The class actually only needs one parameter => TOTAL_AMOUNT. CURRENT_PAGE and OPTIONS are all optional. The CURRENT_PAGE needs a single integer number and OPTIONS is an associative array to instantly set all needed options at once. Optional this can also be configured using the given functions. All possible configurations can be found at the bottom of this page.

```php
new pagination(TOTAL_AMOUNT, CURRENT_PAGE, OPTIONS);
```

```php 
<?php
include('pagination.class.php');

$attributes  				=	array();
$attributes['wrapper']		=	array('id'=>'pagination2','class'=>'pagination');
$attributes['item']			=	array('class'=>'test','style'=>'font-size:15px');
$options					=	array();
$options['attributes']		=	$attributes;
$options['items_per_page']	=	20;
$options['maxpages']		=	10;

$pagination	=	new pagination(400,((isset($_GET['pid'])) ? $_GET['pid']:1),$options);

$data	=	$pagination->render();
?>
```

would result in something linke this

```html
<ul id="pagination2" class="pagination">
<li class="test active" style="font-size:15px">1</li>
<li class="test" style="font-size:15px"><a href="?pid=2" title="Go to page no 2">2</a></li>
<li class="test" style="font-size:15px"><a href="?pid=3" title="Go to page no 3">3</a></li>
<li class="test" style="font-size:15px"><a href="?pid=4" title="Go to page no 4">4</a></li>
<li class="test" style="font-size:15px"><a href="?pid=5" title="Go to page no 5">5</a></li>
<li class="test" style="font-size:15px"><a href="?pid=6" title="Go to page no 6">6</a></li>
<li class="test" style="font-size:15px"><a href="?pid=7" title="Go to page no 7">7</a></li>
<li class="test" style="font-size:15px"><a href="?pid=8" title="Go to page no 8">8</a></li>
<li class="test" style="font-size:15px"><a href="?pid=9" title="Go to page no 9">9</a></li>
<li class="test" style="font-size:15px"><a href="?pid=10" title="Go to page no 10">10</a></li>
<li><a href="?pid=2" title="Go to next page">Next Page</a></li>
<li><a href="?pid=20" title="Go to last page">Last</a></li>
</ul>
```

###Configuration Options
=========================
**tag_wrapper**   =>  The element that gets wrapped around the pagination list. *Default: ul*

**tag_item**      =>  The element of each item inside the pagination list. *Default: li*

**activeclass**   =>  Class that gets assigned to the active page. *Default: active*

**activelink**    =>  Allows the active page to be linked too. *Default: false*

**attributes**    =>  Associative array. Used to add attributes to wrapper or items. ##ID## can be used to show the page number. *Example:* array('wrapper'=>array('id'=>'pagination1','class'=>'pagination'),'item'=>array('data-page'=>'cpage##ID##')); *Default: null*

**jumpers**       =>  Toggles jumper links. (Jump to first/last page). *Default: true*

**jumper_first_text**   =>    Text of the button "Go to first page". ##ID## can be used to show the page number. *Default: First Page*

**jumper_first_title**  =>    Link title of the button "Go to first page". ##ID## can be used to show the page number. *Default: Go to first page*

**jumper_last_text**    =>    Same as jumper_first_text but for button "Go to last page". ##ID## can be used to show the page number. *Default: Last Page*

**jumper_last_title**   =>    Same as jumper_last_title but for link title of "Go to last page". ##ID## can be used to show the page number. *Default: Go to last page*

**steps**               =>    Toggles step link. (Go to previous / next page). *Default: true*

**steps_back_text**     =>    Same as jumper_first_text but for button "Go to previous page". ##ID## can be used to show the page number. *Default: Previous Page*

**steps_back_title**    =>    Same as jumper_first_title but for button link "Go to previous page". ##ID## can be used to show the page number. *Default: Go to previous page*

**steps_next_text**     =>    Same as jumper_first_text but for button "Go to next page". ##ID## can be used to show the page number. *Default: Next Page*

**steps_next_title**    =>    Same as jumper_first_title but for button link "Go to next page". ##ID## can be used to show the page number. *Default: Go to next page*

**link_url**            =>    Sets the link url of the pagination list. ##ID## can be used to show the page number. *Default: ?pid=##ID##*

**link_text**           =>    Sets the link text of the pagination list. ##ID## can be used to show the page number. *Default: ##ID##*

**link_title**          =>    Sets the link title of the pagination list. ##ID## can be used to show the page number. *Default: Go to page no ##ID##*
