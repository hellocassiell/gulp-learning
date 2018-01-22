 
## Sass
(http://www.sasschina.com/guide/)
sass让人们受益的一个重要特性就是它为css引入了变量。

## Gulp
1 安装 
```
npm i gulp -g
```
2 在mypro 
```
npm init
npm i gulp --save--dev
```
![clipboard.png](/img/bVYMYq)
app 开发目录
dist 存放发行目录，存放优化后的文件
gulpfile.js  gulp的配置文件
3 在gulpfile.js中 
```
var gulp = require('gulp');
```
创建任务
```
gulp.task('task-name', function () {
  return gulp.src('source-files') // 待处理文件
    .pipe(aGulpPlugin()) // 用Gulp插件处理文件
    .pipe(gulp.dest('destination')) // 输出到目标文件
})
```
一个真正意义上的任务包含两个Gulp方法 - gulp.src和gulp-dest
### Gulp预处理
gulp-sass插件可以把Sass文件编译成CSS文件
```
npm i gulp-sass --save-dev
```
在app/scss目录下创建styles.scss. 在gulpfile.js里面引入gulp-sass 添加sass任务
```
var sass = require('gulp-sass');
gulp.task('sass', function(){
  return gulp.src('app/scss/styles.scss')
    .pipe(sass()) // 用gulp-sass编译scss文件
    .pipe(gulp.dest('app/css'))
});

```
命令行执行
```
 gulp sass
```
### Node globs
Globs是文件匹配模式，允许在gulp.src方法里面匹配到多个文件
Gulp工作流主要用到以下几种Globs匹配模式：

- *.scss 匹配当前目录下所有以.scss结尾的文件
- **/*.scss 切尔西当前目录及所有子目录下，所有以.scss结尾的文``
- !not-me.scss不包含名为not-me.scss文件
- *.+(scss|sass) 匹配当前目录下所有以.scss或者.sass结尾的文件

使用Gulp "watching". 当Scss文件改动时，Gulp自动执行sass任务
```
//自动监听文件改变
gulp.task('watch', function(){
  gulp.watch('app/scss/**/*.scss', ['sass']); 
  // 其他任务
})
```

插件
learngulp
livereload

