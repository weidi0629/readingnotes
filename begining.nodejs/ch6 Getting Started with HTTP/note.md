-- createServer 
  - callback is passed in two arguments: imcomming request and outgoing server response stream. 
  
  - var server = http.createServer(function (request, response) { // 可以在 request, response 上做文章 
  
-- Using a Debugging Proxy
  - 放在client跟server中间 
  - fiddler 
  
-- Key Members of the Response Stream
  -- header and body 
    - header 只能设定一次 
    
  -- setting Status code 
    - response.statusCode = 404;
    - 404 not found, 200 ok 
  
  -- setting header 
    -- setting the type 
      - response.setHeader("Content-Type", "text/html"); 后面有个表 
    -- remove header: response.removeHeader('Content-Encoding');
    
  -- send header only
    - response.writeHead(200, { 'Content-Type': 'text/html' });
      - 会加在 queued的header上面 
    
-- Key Members of the Request Stream   
  - 都是一些 key-value
    - 'user-agent': 'curl/7.30.0',
    - host: '127.0.0.1:3000',
    
    
-- pending Creating Your Own File Web Server
    
    
    
    
    
    
