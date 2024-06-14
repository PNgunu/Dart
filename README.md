// Example interface
abstract class Printable {
  void printInfo();
}
// Example superclass
class Animal {
  String name;
  int age;

  Animal(this.name, this.age);

  void makeSound() {
    print('Animal makes a sound');
  }
}

// Example subclass implementing interface
class Dog extends Animal implements Printable {
  String breed;

  Dog(String name, int age, this.breed) : super(name, age);

  @override
  void makeSound() {
    print('Dog barks');
  }

  @override
  void printInfo() {
    print('Dog: $name, Age: $age, Breed: $breed');
  }
}
// Example class initializing from file
class DogLoader {
  Dog loadFromFile(String filePath) {
    var file = File(filePath);
    var lines = file.readAsLinesSync();
    var data = lines[0].split(' ');

    var name = data[0];
    var age = int.parse(data[1]);
    var breed = data[2];

    return Dog(name, age, breed);
  }
}
import 'dart:io';

void main() {
  // Demonstrate inheritance
  var dog = Dog('Buddy', 5, 'Labrador');
  dog.makeSound(); // Output: Dog barks

  // Demonstrate interface implementation
  dog.printInfo(); // Output: Dog: Buddy, Age: 5, Breed: Labrador

  // Demonstrate initialization from file
  var loader = DogLoader();
  var loadedDog = loader.loadFromFile('dog_data.txt');
  loadedDog.printInfo(); // Output: Dog: Fido, Age: 3, Breed: Bulldog

  // Demonstrate loop
  printNumbers(5); // Output: 1, 2, 3, 4, 5
}
