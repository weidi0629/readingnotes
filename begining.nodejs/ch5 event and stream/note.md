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

-- Deeper Understanding of the Internals of util.inerits 
  - create a blank object with a specified __proto__ 
  - 为防止constructor info lost, 需要pass constructor info 
      Bird.prototype = Object.create(Animal.prototype, {
        constructor: {
        value: Bird,
        enumerable: false,
        writable: true,
        configurable: true
        }


-- Node.js Events 
  - require('events')
  
  -- EventEmitter class
    -- subscribe - on 
      - emitter.on('foo', function (arg1, arg2) {
          console.log('Foo raised, Args:', arg1, arg2);
          
      - muitiple subscriber
           - 是按顺序来的- single thread 
           - 传递的参数是share的，如果第一个方程改了的话，第二个用的是改了的方程
              - emitter.on('foo', function (ev) {
    -- unsubscribe
      - var fooHandler = function () {
          console.log('handler called');
          // Unsubscribe
          emitter.removeListener('foo',fooHandler); -- 之后再来就不会再操作了
     
    -- emit
      - emitter.emit('foo', { a: 123 }, { b: 456 });
  
      -- 只 raise 一次
        - emitter.once('foo', function () {
            console.log('foo has been raised');
        
  -- Listener Management 
    -- linsterners: that takes an event name and returns all the listener subscribed to that event
    
    -- newLinstner: 显示新加的linsterner
    
    -- removeListener: 显示新删除的
  
  -- Memory Leaks    
    - subscribing to events in a callback but forgetting to unsubscribe at the end
      - 比如10个listners, 当中一个除了问题，后面几个都没有这个event了(single thread)
  
  -- Error Event 
    - just like exceptional case 
      - emitter.emit('error', new Error('Something horrible happened'));
      - must be handled, otherwise would stop execution 
  
  -- Creating Your Own Event Emitters
    - using util.inherits
  
  -- the global process object is also an instance of EventEmitter 
  
  -- Global Exception Handler
    - Any global unhandled exceptions can be intercepted by listening on the `uncaughtException` event on process.
      - process.on('uncaughtException', function (err) {
  
  -- exit 
    - there is no way to stop exiting 
      - process.on('exit', function (code) {
  
 -- signals  
  - support UNIX concept of signals: strl+c 
    - process.on('SIGINT', function ()
 
 pending ### streams ### 
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  







