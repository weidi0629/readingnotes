-- pyramid problem
  - 很多indention
  - 解决方式平铺下来 
  
  - Simple lesson: If a function takes a callback, it’s async and it should never call the callback directly—process.nextTick is your friend.
  
  - async.parallel可以同时处理几个function
  
-- Error Handling

   - two important points:
    - Never call the callback twice
    - Never throw an error
    
    - try to put the cb outside try catch block 
    
    
    pending Introduction to Promises page 205
    
    
    
    
