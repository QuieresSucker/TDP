# TDP
<?php
header('Content-type: text/html; charset=utf-8');
require_once 'phpQuery/phpQuery/phpQuery.php';

function print_arr($arr){
	echo '<pre>' . print_r($arr, true) . '</pre>';
}

$url = 'http://www.motorpage.ru/Bentley/';
$file = file_get_contents($url);

$doc = phpQuery::newDocument($file);

foreach ($doc->find('.row .mark-model') as $article){
	$article = pq($article);
	$img = $article->find('.col-md-4 img')->attr('src');
	$text = $article->find('.col-md-4')->html();
	print_arr($text);

	echo "<img src='$img'>";
	echo $text;
	echo '<hr>';
}
