-- What Is a SPA? single page application 
  - all the essential code of your application (the HTML/CSS/JavaScript) is loaded upfront in the first request to the web server
  - client 如果在动作的话，就会只要求那一块的数据using XHRs (XMLHttpRequest).然后用client side的js来render（配合之前已经download的ccs,html）
  
  - XMLHttpRequest (XHR )
    - 所有browser都能用的class
  
  -- DOM (the rendered HTML)
    - The DOM is basically the API provided by the browser to interact with the rendered HTML using JavaScript.
  
  -- Introduction to Twitter Bootstrap
    - <link rel="stylesheet" type="text/css" href="./bootstrap/css/bootstrap.css"> 人家做好的 html/ccs的模板
  
  -- $ variable 不同的用法
    $(function(){ // on document readyJQury 用的。一个callback function page成形时候用的
            $('button').tooltip(); // add tooltip to all buttons
    
    - JQury 有很好的api能跟所有的dom打交道
    
    
 -- AngularJS
 
    -- module
      - 一个可以承载 contorller, directives 等的container
      
    -- Directive 
      - segment of code 
      
    -- Controller and $scope
      -- controller: sync the model and view
      - two-way data-binding, the glue is scope 
  
    - vm, viewModel, model only for view 
    
    
    pending 
  Creating a Simple To-Do List Application
  
  
  
  
  
  
  
  
