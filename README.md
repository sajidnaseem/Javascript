# Javascript

((exports) => {
let Animal = function(name){
  // this = Object.create(Animal.prototype)
  this.name = name;
}
Animal.prototype.move = function(){ console.log(this.name, "is moving"); };

// CAT -------------------
let Cat = function(name, sound){
  // this = Object.create(Cat.prototype);
  Animal.call(this, name);                       // connection 1 like super()
  this.sound = sound;
}

Cat.prototype = Object.create(Animal.prototype)  // connection 2 like extends
Cat.prototype.constructor = Cat;                 // fix, broken by connection 2

Cat.prototype.makeSount = function(){ console.log(this, "says ", this.sound)};


// DOG ----------------------
let Dog = function(name, protects){
  Animal.call(this, name);
  this.canProtect = protects;
}

Dog.prototype = Object.create(Animal.prototype);
Dog.prototype.constructor = Dog;

Dog.prototype.protect = function(){
  if(this.canProtect) console.log(this, " is in PROTEK MODE! WHOOFF" );
}
exports.Animal = Animal;
exports.Cat = Cat;
exports.Dog = Dog;
})(this.nml = {})

u = new nml.Animal("whale");
c = new nml.Cat("HelloKitty", "meow");
c2 = new nml.Cat("Meowing Cat", "MEOOOOOW");

d1 = new nml.Dog("Germany", true);
d1.protect();
