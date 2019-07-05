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
  
  
  pending Buffer page50 
