---
title: Laravel
---
# Page Speed

- [Introduction](#introduction)
- [Auditing Tools](#auditing-tools)
    - [Page Insights](#page-insights)
    - [Lighthouse](#lighthouse)
- [Images](#images)
    - [Image compression automation](#image-compression-automation)
- [HTTP Requests](#http-requests)
- [Non Blocking JavaScript](#non-blocking-js)
- [Defer Loading Assets](#defer-loading-assets)
- [Image Sprites](#image-sprites)
- [Lazy Load Images](#lazy-load)
- [HTTP/2](#http2)
- [Minification](#minification)
- [Combining](#combining)
- [Existing Tools](#existing-tools)
    - [Gulp / Elixir / Rollup and Webpack](#build-tools)
    - [Artisan Assets Less Command](#artisan-assets-less-cmd)
    - [Laravel Mix](#laravel-mix)

<a name="introduction"></a>
## Introduction
The speed in which a web application loads has a big impact not only on the ranking of a website but also the experience and perception for the end user.
Below are a few best practices and tools to take into consideration when optimising your application.

<a name="auditing-tools"></a>
## Auditing Tools
These auditing tools can greatly help in finding improvements that can be made.

<a name="page-insights"></a>
### Page Insights
[https://developers.google.com/...](https://developers.google.com/speed/pagespeed/insights/")

This tool will measure the page and give advice on what to optimise, many of which are discussed below.

<a name="lighthouse"></a>
### Lighthouse (Chrome DevTools)
Under chrome developer tools (F12 or ctrl + shift + i) there is a tab of "Audits", under here you can run audits to identify and fix common problems that affect your site's performance, accessibility and user experience.

Like page insights it gives advice on what to optimise but is more detailed.
![Image](https://admin.netmatters.co.uk/file/embed/2018/8/24/phpocryi55b8003f1571a8.)

<a name="images"></a>
## Images
Images can be the biggest and quickest wins you can achieve on a website.

- Make sure to use the correct format e.g GIF, PNG, JPG or SVG
- Make sure to use correctly sized images - e.g Image size = 2000px by 1000px to fit a gap of 100px by 50px
- Image quality is set to 100% when it could be 85% (you can go lower than 85%, but the lower you go the grainier a jpeg will get), compression etc.
- Please see the section titled "Image compression automation" for a way to optimise uploaded images at the point of upload- Lazy-load images that are not visible.

<a name="image-compression-automation"></a>
### Image compression automation
With the use of the PHP extension [ImageMagick](https://www.imagemagick.org/script/index.php) you can automatically compress and optimise images using PHP with a code snippet that is provided below.

There are some gotchas noted in the comments of the snippet, to do with the fact that in some instances images will not reduce in size enough for the optimisation to be worth the risk.
```php
$imagick = new Imagick(); $imagick-&gt;readImageBlob($dataUri); // reads an image string  ------- OR ----------
$imagick      = new Imagick($path); // reads an image from a file
$originalFileSize = $imagick-&gt;getImageLength(); // gets the file length
$imageDetails     = $imagick-&gt;identifyImage(); // gets details about the image
// don't work with image types outside of these with this snippet
if (!in_array($imageDetails['mimetype'], ['image/pjpeg', 'image/jpeg', 'image/png'])) {        return $dataUri;
}
if ($imageDetails['mimetype'] === 'image/png') {        // png needs handling differently
    // this is a lossless optimisation
    $imagick-&gt;setImageFormat("png");  // sets the image format      $imagick-&gt;stripImage(); // Strips an image of all profiles and comments
} else {        $imagick-&gt;setImageCompression(Imagick::COMPRESSION_JPEG); // sets the image compression to jpeg     $imagick-&gt;setImageCompressionQuality(85); // sets the image quality down to 85, this is most optimal point for lossy optimisation
    $imagick-&gt;setSamplingFactors(['2x2', '1x1', '1x1']); // This option specifies the sampling factors to be used by the JPEG encoder for chroma downsampling. If this option is omitted, the JPEG library will use its own default values. This is equivalent to 4:2:0 which is recommended.
    $imagick-&gt;setImageFormat("jpg"); // sets the image format to jpg
    $imagick-&gt;stripImage(); // Strips an image of all profiles and comments
}
$newImageString = $imagick-&gt;getImageBlob(); // gets the image back as a string
$imagickPost = new Imagick();
$imagickPost-&gt;readImageBlob($newImageString); // read string in as a separate imagemagick instance
$postFileSize = $imagickPost-&gt;getImageLength(); // get new instance image length
// check if the image has had a 2% reduction in size, in some instances already optimised images can go up in filesize or not change enough in filesize to risk the lossy optimisation.
if (($postFileSize / $originalFileSize) * 100 &lt; 98) {       // returns new image string if worked     return $newImageString;
}
// returns old image string if not working
return $dataUri;  ---------- OR save image to file-----------
$imagick-&gt;writeImage($pathToCheckFile); // writes image back to file.
```

<a name="http-requests"></a>
## HTTP Requests
One of the quickest and most noticeable ways to improve the responsiveness of any application is to reduce the number of HTTP requests made to the server.

Each time a page is requested by the end user a series of requests are made to the server in order to render the page.

Most modern browsers are able to process three requests (per domain) at any one time, meaning that for each three requests sent to the server the browser must receive three responses before processing the next batch of requests.

In short, if you want to speed up your web application start by reducing the number of synchronous requests to the server.

<a name="non-blocking-javascript"></a>
## Non blocking JavaScript
Web pages load from top to bottom so where possible always place your JavaScript in the footer of the page.

<a name="defer-loading-assets"></a>
## Defer loading assets
Where possible try to delay the requests for render blocking assets until the page has been loaded. A few examples of this would be to load images via Ajax and your JavaScript and font files [Asynchronously](https://css-tricks.com/thinking-async/).

<a name="image-sprites"></a>
## Image Sprites
Sometimes you may have an image heavy site, reducing the number of image requests for a site like this may seem impossible. One solution is the use of Image Sprites, in summary an image sprite is just a series of images grouped together into a single image file and then mapped together using the CSS background position property. 
Sprites are a great for icons, but should not be used for content based images.

CSS Sprite Generator: [https://draeton.github.io/stit...](https://draeton.github.io/stitches/)

Another solution is to load the images via AJAX.

<a name="lazy-load-images"></a>
## Lazy load images
As previously discussed lazy loading images that are not visible, this reduces the number of page-load requests. Especially useful on galleries and pages with a lot of imagery.

<a name="http2"></a>
## HTTP/2
HTTP/2 enables a more efficient use of network resources and a reduced perception of latency by introducing header field compression and allowing multiple concurrent exchanges on the same connection&hellip; Specifically, it allows interleaving of request and response messages on the same connection and uses an efficient coding for HTTP header fields. It also allows prioritisation of requests, letting more important requests complete more quickly, further improving performance. [*(Hypertext Transfer Protocol version 2, Draft 17)*](https://tools.ietf.org/html/draft-ietf-httpbis-http2-17)

It's faster, allows more concurrent connections, **make sure it is enabled!**

<a name="minification"></a>
## Minification
The process of minification is to remove all comments, formatting and white space from both style and script files.

When the browser downloads and reads in these files comments and white space are automatically ignored, so for this reason it makes sense to provide the browser with a pre minified file as this will result in faster response times and a smaller file to download.

<a name="combining"></a>
## Combining
As previously mentioned, HTTP requests are very costly in terms of performance and the user experience, so for this reason it is a lot more efficient to download one large compressed / minified file than several smaller files.

<a name="existing-tools"></a>
## Existing Tools

<a name="build-tools"></a>
### Gulp / Elixr / Rollup and Webpack
Gulp / Elixr / Rollup and Webpack are all pre-processors. Among other benefits the primary focus of these tools is to aid in compiling, minifying and combining CSS and Javascript files in order to reduce the number of HTTP requests and improve page speed. Prior to Sysflow version 5 gulp played a major part in helping to manage the asset pipeline.

```js
gulp.task('compileFrontendCss', function()
{
    return gulp.src([
        frontendLessPath    + 'compile/frontend.less',
        frontendLessPath    + 'compile/frontend-*.less',
        frontendLessPath    + 'ie/*.less',
        frontendLessPath    + 'pages/*.less',
        frontendCssPath     + 'owl.carousel.css',
        frontendCssPath     + 'owl.theme.css',
        frontendCssPath     + 'owl.transitions.css',
        frontendCssPath     + 'menu.css',
        frontendCssPath     + 'fonts.css'
    ])
        .pipe(less())
        .pipe(autoprefixer('last 10 version'))
        .pipe(minifycss())
        .pipe(concat('frontend-bundle.css'))
        .pipe(gulp.dest(frontendCssPath));
});

gulp.task('compileFrontendPlugins', function()
{
    return gulp.src([
        //bowerPath + 'owl-carousel2/dist/owl.carousel.js',
        frontendJsPath + 'plugins/jquery-*.js',
        frontendJsPath + 'plugins/jquery.validate.js',
        frontendJsPath + 'plugins/bootstrap-*.js',
        frontendJsPath + 'plugins/owl.carousel.min.js',
        frontendJsPath + 'plugins/snap.js',
        frontendJsPath + 'main.js',
        frontendJsPath + 'menu.js'
    ])
        .pipe(plumber({errorHandler: onError}))
        .pipe(sourcemaps.init({loadMaps : true}))
        //.pipe(uglify())
        .pipe(concat('frontend-plugins.js'))
        .pipe(sourcemaps.write('.'))
        .pipe(gulp.dest(frontendJsPath));
});
```

<a name="artisan-assets-less-cmd"></a>
### Artisan Assets Less Command
Sysflow version 5 introduced a new way of managing styles, with the increase of multi domain sites and large e-commerce applications mixed with a growing number of merge conflicts on asset files the decision was made to move the asset processing to the server.

Although this solution solved 95% of the problems faced, the newer versions of Laravel 5+ now come pre-shipped with either elixr or webpack which make this process effortless. Sysflow version 6+ now uses webpack out of the box.

`php artisan assets:less --all`

<a name="laravel-mix"></a>
### Laravel mix
Laravel mix can be used on any project - it doesn't have to be the latest version of Laravel/ Laravel at all.

[https://admin.netmatters.co.uk...](https://admin.netmatters.co.uk/manual.php?mancat=64153)
