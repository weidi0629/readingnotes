-- The only difference between file-based modules and node_modules is the way in which the file system is scanned to load the JavaScript file.
  -- /node_modules/bar.js
  --if a path to the module resolves to a folder (instead of a file), Node.js will look for an index.js
    - 这个index.js里面有所有的module的信息 
    
-- JSON Global  
  - global utility to convert string 
  - var json = JSON.stringify(foo);
  
-- NPM

pending page 76 Semantic Versioning in NPM / package.json
