-- 唯一能搞scope是function

-- first-class function
  - 可以把别的function作为参数
  
-- closure 
  - 可以调用上层函数内部的参数
  
-- more nodejs internals
  -- single thread, if some long-time process, it would delay the callback 
  
-- JAVA Script 
  - everything is ref 
  - default value: undefined 
  - 5=='5' true, 5 === '5' false
  - null: value is not there 
  
  -- revealing module pattern - OOP 
    - function can return arbitrary (function+data) object
    - page 34 例子很重要 
    
  -- this 
    - refer to the caller 
    - 如果没有scope的话，就是refer to global variable 
    - with new operator, this refer to this new obj 
    
  -- Understanding Prototype 
    - foo.__proto__ foo的上级
      - 一般不用，用.prototype代替 
    - var bas = new foo();
      - 这两个的prototype就一样了 - prototypes are shared between all the objects
        - save memory 
    - prototype is only accessed if the property does not exist on the object.
      - 如果你自己设定了同样名字的type,那就断了跟上级的prototype联系。overwrite
      
    -- 一般function做prototype，因为不怎么改。参数做overwwrite,like this 
       - 这样 'this指向new 建立的obj'就很重要了
       
       page 38页 example很重要 
       
    -- Error Handling 
      - 要把try catch block放到call back function里面不然程序就跑走了。 
      - 要把call back function同时放在try, catch里面，给他第一个参数做个flag
      
      
      
      
      
      
      
      
      
      
      
      
      
      
      
      
