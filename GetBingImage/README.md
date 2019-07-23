# PHP获取必应首页背景图片

代码：

```php
<?php
	$str=file_get_contents('https://cn.bing.com/HPImageArchive.aspx?idx=0&n=1');
	if (preg_match("/<urlBase>(.+?)<\/urlBase>/ies", $str, $matches)) {
		$imgurl='https://cn.bing.com'.$matches[1].'_1920x1080.jpg';
	}
	if ($imgurl) {
		/*header('Content-Type: image/JPEG');
		@ob_end_clean();
		@readfile($imgurl);
		@flush();
		@ob_flush();
		exit();*/  // 直接输出图片
        header("Location: $imgurl");    //输出302跳转
	} else {
		exit('error');
	}
?>
```

---

今天的必应背景：

![1920x1080.jpg](https://originspace.cn/Bing/Bing.php)

[下载](https://originspace.cn/Bing/Bing.php)

---

参考：https://www.moewah.com/archives/693.html