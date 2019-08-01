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
     
-- Introduction to Promises
   - some function will give you a promise and from that point on you use the then function to create and fulfill or reject promises
    
    
   pending 因为这个是用来async 所以学习暂时停到这里。如果要继续可以改看其他文档。感觉这章讲述promise不是非常清楚。  
    
    
