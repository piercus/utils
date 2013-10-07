utils
=====

Asynchroous configurable map function for nodejs.

objMapAsync.js contains 2 functions :

require("utils/objMapAsync.js", function(objMapA){
  
  var cbOne = function(value, key, cb){
    cb(null, "key : "+key+", value : "+value);
  };
  
  var cbAll = function(error, results){
    console.log("errors : ", errors, " results : ", results);
  };
  
  //use it on an object :
  
  var obj = {"a" : "c", "foo" : "bar"};
  
  objMapA(obj, cbOne, cbAll);
  
  
  //use it on an arrays :
  
  var arr = ["a", "b", "c"];
  
  arr.mapAsync(obj, cbOne, cbAll);
  
});

options
=====

* stopAfterNErrors : number, if set, the mapAsync function will stop calling functions after n errors, useful if you don't want a break an api key with two many error requests
default 0 (<=> don't sop after n errors)
* nParallel : number, limit parallel calls to n, default : 0 <=> unlimited
* stepByStep : boolean, <=> (nParallel == 1)
