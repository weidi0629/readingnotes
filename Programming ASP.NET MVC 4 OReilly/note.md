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
    - using mapRoute() to register a route:
    - AuctionsController 后面 Controller几个字会被chop off, URL 直接打auction就可以了


-- controller pending












