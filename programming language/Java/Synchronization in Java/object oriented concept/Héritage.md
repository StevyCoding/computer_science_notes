L'héritage permet à une classe (appelée sous-classe ou classe dérivée) d'**hériter** des propriétés et des méthodes d'une autre classe (appelée classe de base ou superclasse). ♻️ Cela favorise la réutilisabilité du code, car les sous-classes peuvent étendre ou modifier le comportement de la classe de base.

```javascript
// Example code demonstrating inheritance
class Animal {
  constructor(name) {
    this.name = name;
  }

  speak() {
    console.log("Generic animal sound");
  }
}

class Dog extends Animal {
  constructor(name, breed) {
    super(name);
    this.breed = breed;
  }

  speak() {
    console.log("Woof!");
  }
}
```