-- Serving Static Pages
  - var serveStatic = require('serve-static'); 
    ...
    .use(serveStatic(__dirname + '/public'))
  
  - ‘__dirname’ is always relative to the current file 
  
  - 在内部已经做了不少优化
    - 默认找 index.html 
  
  - 也可以这样用
    - use(express.static(__dirname + '/public'))
    
--  Listing Directory Contents
    - var serveIndex = require('serve-index');
    - 因为只是列出 content， 常常跟serve-static middleware 连用 
    
-- Accepting JSON Requests and HTML Form Inputs
  - var bodyParser = require('body-parser');
    - 把json转化成 js obj 
    - put this obj to req.body 
    - 有 parse limit 的限制 
  
-- Handling Cookies   
  - res.cookie(cookieName,value,[options])
    - eg. res.cookie('name', 'foo');
  
  -- cookieparser middler ware, populateds the parsed cookies into req.cookies obj 
      - .use(cookieParser())
        ... 
        if (req.cookies.name) {
        
  - res.clearCookie('name'); 清楚 cookie
  
  -- Preventing Cookie User Modification Using Signing
    - digital signature assures the authenticity 
      - Key-Hash message authentication code (HMAC)
        - server has a screct key to calculate for the content of cookie
        - append the HMAC value to the cookie, then recalculte the HMAC when client resend, to see if the value is good or bad 
        
      - enable: res.cookie(name,value,{signed:true}) 
      - read cookie from req: req.signedCookies
  
      - httpOnly and Secure
        - true (res.cookie(name,value,{httpOnly:true}  不让 javascript 读取 cookie  
        - res.cookie(name,value,{secure:true}) only use https for sending those data 
        
  -- Setting a Cookie Expiry
    -res.cookie('foo', 'bar', { maxAge: 900000, httpOnly: true })
  
  -- Cookie-Based Sessions - 比如这个client 是否在 login的状态 
    - 如果用基本的http cookie 办法，所有cookie都是string，我们想要 js 的obj， 可以有 点点点 obj.xxx
    - var cookieSession = require('cookie-session'); 
      - 把user session object is exposed as req.session
      - must be passed at least one secret key
        - .use(cookieSession({
            keys: ['my super secret sign key']
  
  -- cookie 结束了
  
-- Compression
  - var compression = require('compression');
    .use(compression())
  - in default is 1 kb, you can specify compression({threshold: 512})
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
