-- '.call' member function force 'this' 指向当前的obj 
  - function Bird(name){
      Animal.call(this,name); // Animal的this 指向的是 bird这个object 
      
      
-- Setting Up the Prototype Chain
    - Bird.prototype.__proto__ = Animal.prototype.

-- The Constructor Property
    - By default, every function has a constructor property that points to the function itself
    - can get access to the constructor using a simple lookup instance.constructor

-- The Proper Node.js Way -- require('utils')
  - inherits(Bird, Animal);

  -- Overriding Functions in Child Classes
     - 在child里面call: Base.prototype.foo.call(this)
    
  -- 查看是否是child object -- b instanceof B 












