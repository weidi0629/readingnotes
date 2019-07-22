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
     
-- Creating Your Own File Web Server
  
-- Introducing Connect
  - middleware, sit between app and 底层API 
  - listen function can replace previous http的定义 
  
  - create a connect dispatcher
    - var app = connect();
    - 只是一个内置的接受request/response的function，所以可以作为createServer的参数 
       var app = connect();
       http.createServer(app)
  
  -- Creating a Connect Middleware   
    - ‘use’ function take three arguments:
      - request/response/next: pass control to next middleware 
    
  -  Mounting Middleware by Path Prefix
    - .use('/echo', echo) 如果 request里有 /echo才会处理 
   
  -- Using an Object as Middleware
    - 主要这个obj有 handle method 
      - 直接扔到use function里面去 
   
-- The Power of Chaining

   -- Sharing Request/Response Information
    - request/response objects passed into each middleware are mutable and shared
      - 可以前面一个middleware先处理一下 
      - 有个parse json的小例子 
     
    - Chaining Sample: Verifying Requests/Restricting Access
      - 如果不calling next(), 就不会往下一层的 middleware 
      - utility 里面自动的返回一个需要用户名密码的窗口 
        - res.writeHead(401 , {'WWW-Authenticate': 'Basic'}); 
    
   -- Raising a connect Error
     - pass an argument to ‘next’， 告诉他connect 出了点问题 
     - use(function (req, res, next) { next('An error has occurred!') })
     - 如果你继续想process， 需要 register一个四个parameters 的middleware 
        - .use(function (req, res, next) { next(new Error('Big bad error details')); })
           ...
           .use(function (err, req, res, next) { .. 
        - 随便哪里call都可以 
        
   -- https
      - browser generate a pre-master session key, 只能用在这个browser在这个session里面
      - 之后还是跟HTTP 一样 
    
      -- node.js 的https
        - 让你有个option指定 private/public key
          - options = { key: fs.readFileSync('./key.pem'),
             cert: fs.readFileSync('./cert.pem')};
             ...
            https.createServer(options, function (req, res) {
    
         - 可以redirect request from 80 to 433 
          - res.writeHead(301, { "Location": "https://" + req.headers['host'] + req.url });
    
    
    
    
    
    
    
    
    
    
    
    
    
    
   
   
    
    
    
    
    
