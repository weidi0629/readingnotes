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
   
-- pending Popular Node.js Packages
