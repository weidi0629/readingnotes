############ ch1 Fundamentals of ASP.NET MVC  #######################

-- model 
  - The model represents core business logic and data
  - Encapsulate the properties and behavior 

-- The View
  - generating HTML to be rendered in the user’s browser

-- The Controller
  - get input from user, pass to model to perform specific action, pass result back to view 

--  Routing 
  - pattern-matching system: it matches that request’s URL against the URL patterns registered with it

  - default URL: 
    - {controller}/{action}/{id}
      - 主要要得到 controller 跟 action 
      e.g  new { controller = "Home", action = "Index",  // 设定一个route的example 
            id = UrlParameter.Optional } // Parameter defaults
    - using mapRoute() to register a route:
    - AuctionsController 后面 Controller几个字会被chop off, URL 直接打auction就可以了


-- controller
  -- Action Results
    - call controller 里面的action 会返回一个action result 
    - controller only tell what to do next, not how to do it. 如何tell就是用返回的ActionResult
      - 一般resultAction都是已经定义好的 
      
    - Action Parameters
      - it can get paramters from request 
        - model binding 
          - public ActionResult Create( string title, decimal currentPrice, DateTime startTime, DateTime endTime)
          
          - can retrieve the id value directly 
            public ActionResult Auction(long id)

        - action filter 
          - cross-cutting concern
            - 是一些整个application都要考虑的concern
            - [Authorize]
              public ActionResult Profile()

-- views()
  - when return, MVC will look for the same name
    - 如果什么都没有指定，那就是找名字跟controller一样的view 
      - public ActionResult Index() 就回去找 index view 
      - 会在 view

  - Razor 
    - using code:
    - goal: rendering HTML.
      
  -- differentiate code and markup 
      - Code nuggets
        - Code nuggets are simple expressions that are evaluated and rendered inline
        - Not Logged In: @Html.ActionLink("Login", "Login")
          - 他这个ActionLink()function需要 return markup for the view to render
        
      - Code blocks
          - contains strictly code  
          - no return value. 之后的code可以使用大括号里定义的变量
          
      - Layouts
        - maintain a consistent look and feel throughout your entire website
      
        - @RenderSection([Section Name]) and @RenderBody() to interact with individual views
   
        - view can refer to that layout like this: 
          - @{ Layout = "~/_Layout.cshtml"; }
          
        -- Partial view
          - create a small view inside large view
          - using Html.Partial() to render 
            - @foreach(var auction in Model) {
                  @Html.Partial("Auction", auction)
              - 第一个string 是参数名字，.net 用这个名字去找view 
        
        -- Displaying Data
          - ViewData and TempData.
             - dictionary property 
             
          - controller and view also expose to ViewBag 
             -  ViewData that exposes the ViewData dictionary as a dynamic object. 
             - 它只是ViewData封装起来，显示dictionary的特点   
        
        -- View models
           - primary object that is the target of the request
        
           - in controller: return View("About", company);
             - The second parameter,represents the object that will be assigned to the ViewData.Model property.
           - in view():  
             - @{ var company = (CompanyInfo)ViewData.Model; }
                  <h1>@company.Name</h1> ... 
                  
           - Strongly typed views 
            - using @model keyword
              - @model Auction
                <h1>@Model.Name</h1> .. 
                
        --  HTML and URL Helpers
          - the HtmlHelper class helps you generate HTML markup and the UrlHelper class helps you generate URLs
                    
  -- models
    -- 可以分为 data model and domian model 
    
  
  -- putting all together
    
    -- controller templates 
      - Empty MVC controller
      - MVC controller with read/write actions and views, using Entity Framework  
        
  --  Authentication
    -- AuthorizeAttribute 可以放在单个controller action上，也可以整个controller上面
      - [Authorize]
        public ActionResult Profile() ... 甚至可以指定某一些 users
        
    -- The AccountController 
      - 默认已经在里面了
      - Login/Logoff/New user registration/Changed password 
      - 
        
        
 ######  ch2 ASP.NET MVC for Web Forms Developers
      skip..
      
 
 ######  ch3 working with data 
 -- Handling Form Posts
   - model 跟 view里面参数的名字一定要对应      
        
 -- Saving Data to a Database 
    - System.Data.Entity.DbContext or class derived from it, 做db的gateway 
        
    - public DbSet<Auction> Auctions { get; set; }
      - the application needs to save and edit instances of the Auction class in the database
    
    - Specifying Business Rules with Data Annotations
      - 需要把business logic 放到model里面来
      - data annotation
        - [Required]
          public string Title { get; set; }
        - string maximum [Required, StringLength(50)]
        - valid ranges [Range(1, 10000] 
        - using model state 来判断，在controller里面
          - if (ModelState.IsValid)
       
     -- Displaying Validation Errors 
        - 告诉用户哪里出错了
        - 学会使用 @Html.ValidationSummary()； @Html.ValidationMessageFor(model => model.Title)
        
        
### ch4 Client-Side Development ### 

-- Responding to events 
  - $(function) is a shortcut that tells jQuery to attach the event handlers once the DOM is loaded in the browser

-- DOM Manipulation   

-- AJAX - Asynchronous JavaScript and XML
  - does not have to wait for the full page to load 增加使用度 
  
  - heart of AJAX is the XmlHttpRequest object
    - var xhr = new XMLHttpRequest(); ... 操作这个
  
  - Asynchronous and call back 
    - xhr.open("GET", "http://www.google.com/", true); 这个 true
    - must attach any callbacks before issuing xhr.send(), or they will not be called.
    - jQuery version:
      $.ajax("google.com") ... 
  
-- Client Side Validation 
  - enable/disable at web.config
  - take advantage of the DataAnnotation attributes
  
  
### ch5  Web Application Architecture  ###  
  
-- SOLID
  - The Single Responsibility Principle
    - one obj should have only one responsibility
      - e.g. different controllers for different screens
      
  - The Open/Closed Principle    
    - open for extension, but closed for modification  
      - 多用继承，少加 method 
      - 用interface
   
  - The Liskov Substitution Principle
    - objects should be easily replaceable by instances of their subtypes
  
  -- The Interface Segregation Principle
    - no big base class, have more small specific interface
  
    - 在controller里面直接加使用interface， 看哪个class/model会进来
  
  -- The Dependency Inversion Principle
    - components that depend on each other should interact via an abstraction and not directly with a concrete implementation.
      - e.g relying on an abstract class or interface to communicate with a data access layer,
  
  -- Inversion of Control 
    - Understanding dependencies
    
    pending page 106
  
  
  
  
  
  
  
  
      
      
      
      
      
      
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  











