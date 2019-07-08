-- Node.js File-Based Module System
  -- each file is a module , just like python 
  - export a function
    - module.exports = function () {
    
  -- Require
    - var foo = require('./foo');
    - Using the require function only gives you the module.exports variable, and you need to assign the result to variable locally in order       to use it in scope - 比如share一个configuration 
    - 如果不要share一个ref,用return
  
  -- Export 
    - module.exports = {} is implicitly present in every file/module 
    
    -- 要export好几个
      - 用 list 
      - 更多用 . module.exports.a = function () { 
        - 因为module.exports is implicitly set to {} by nodejs 
        - exports 可以用export 代替
        
--  Modules Best Practices       
    - avoid adding the .js extension
    - use relative paths
    - 如果要import 很多， create a index.js, import all the modules once and export from here. page 47 
      - more manintainable 
        
-- important Globals 
  - timer
    - clearTimeout/clearInterval 用来clear. ex. page 49 
  - __filename and __dirname 每个文件都有的默认变量 
  
-- command Line Arguments 
  - process.argv 第一个参数是node， 第二个是file name， 后面是参数
  
-- process.nextTick
  - put a callback function at nextloop of nodes event loop 
  
-- Buffer 
  - native and fast support to handle binary data - 
  - 搞 unicode string 互相convert 
    - character encoding 
    - var buffer = new Buffer(str, 'utf-8');

-- global
  - global.something =123; 
  - 最好不要用
  

-- Core Modules 
  -- Path Module 
    - var path = require('path')
    - path.normalize(str) -- fix up slashes to be OS specific 
    - path.join([str1],[str2])
    - dirname, basename, extname 
    
  -- fs Module 
    - filesystem, 处理文件 
    - delete file sync/async
      - unlink('file',callback) - 最好用这个，因为读写硬盘比较慢 
  
  -- os module
    - 知道系统的一些参数 
  
  -- util module - general purpose
    - util.log -> log out to console with timestamp 
    - string format
      - util.format 有点像 c++ print
        - util.format('%s has %d dollars', name, money)
        
   -- AMD  
      - server 端代码可以优化--把东西抓到内存里，但是browser不行，每次都要有个request
        - solution: async, parallel: declear at front and set callback -> async module definition AMD 
          - define(['./foo', './bar'], function(foo, bar){ 
             browser 就知道 这边code可以继续直接下去，不用等loading foo，bar 
             - 但是要使用的话，需要third part 支持，比如 requirejs
             page 56有例子
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
      



