-- The only difference between file-based modules and node_modules is the way in which the file system is scanned to load the JavaScript file.
  -- /node_modules/bar.js
  --if a path to the module resolves to a folder (instead of a file), Node.js will look for an index.js
    - 这个index.js里面有所有的module的信息 
    
-- JSON Global  
  - global utility to convert string 
  - var json = JSON.stringify(foo);
  
-- NPM
  - 如果install的时候加了 -g，表示globally command line都可以用的，否则就要用require
    - npm install -g package 
    
  -- main 是唯一一个node会主动去执行的文件
    - 路径写在 package.json里 
   
-- Popular Node.js Packages
  - _集成了一些功能：
    - var results = _.filter(foo, function (item) { return item > 100 });
    - 还有 _.map, _.reject, 
  
-- Handling Command Line Arguments
  -- optimist: var argv = require('optimist').argv;
    - flag, parameters 
    
-- Handling Date/Time Using Moment
    - npm install moment -> var moment = require('moment');
    
    -- serializing dates 
      date.toJSON() <-->  new Date(jsonString)

-- Customizing Console Colors
  - npm install coloro 更改console的颜色 
    - console.log('hello'.green);
  - how it works?
    - getter/set __defineGetter__/__defineSetter__ member 就可以在member后面直接加点呼叫了
      - foo.__defineSetter__('bar', function (val) {
            console.log('set bar was called with value:',val);
        foo.bar = 'something';













