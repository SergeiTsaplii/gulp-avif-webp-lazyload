# gulp-avif-webp-lazyload

This is a modified version of the plugin [gulp-webp-html](https://www.npmjs.com/package/gulp-webp-html). Here was fixed thebug that added two dots before webp to the final html file. No SVG format.

## Example
```html
// Input
<img src="/images/catalogImage.jpg">

// Output
<picture>
    <source srcset="/images/catalogImage.avif" type="image/avif">
    <source srcset="/images/catalogImage.webp" type="image/webp">
    <img src="/images/catalogImage.jpg">
</picture>


// Input
<img src="/images/catalogImage.jpg" srcset="/images/catalogImage2x.jpg 2x">

// Output
<picture>
    <source srcset="/images/catalogImage.avif, /images/catalogImage2x.avif 2x" type="image/webp">
    <source srcset="/images/catalogImage.webp, /images/catalogImage2x.webp 2x" type="image/webp">
    <img src="/images/catalogImage.jpg" srcset="/images/catalogImage2x.jpg 2x">
</picture>

// Input
<img src="/images/catalogImage.svg">

// Output
<img src="/images/catalogImage.svg">
```


## Install
```bash
npm i --save-dev gulp-avif-webp-lazyload
```
## Usage
```javascript
let avifWebpHtml = require('gulp-avif-webp-lazyload');

gulp.task('html',function(){
    gulp.src('./assets/**/*.html')
        .pipe(avifWebpHtml())
        .pipe(gulp.dest('./public/'))
});
```
