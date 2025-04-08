# forexamples
/* //Variable types and declarations
  void main() {
  variablesDemo();
}
  void variablesDemo() {
  int age = 20;
  double height = 1.75;
  bool isStudent = true;
  String name = 'Aysel';

  print('Name: $name, Age: $age, Height: $height, Student: $isStudent');
} 



//Function with return value and parameters
int add(int a, int b) {
  return a + b;
}
void main(){
  int result=add(3,5);
  print(result);
} 



//Function with optional named parameters and default values
void User({String name = 'Guest'}) {
  print('Welcome, $name!');
}
void main(){
 User(); 
 User(name: 'Leyla');
} 



//Null safety with nullable types
void main(){
checkEmail(null);
checkEmail('user@example.com');
}
void checkEmail(String? email) {
  print('Email is: ${email ?? "No email provided"}');
} 


//if-else condition example
void main(){
  int score=85;
  String grade=gradeLetter(score);
  print('Bal: $score, Qiymet: $grade ');
}

String gradeLetter(int score) {
  if (score >= 90) return "A";
  else if (score >= 80) return "B";
  else if (score >= 70) return "C";
  else if (score >= 60) return "D";
  else return "F";
} 



//switch-case example
void main(){
  print('Friday is a ${getDayType("Friday")}');
}
String getDayType(String day) {
  switch (day) {
    case 'Saturday':
    case 'Sunday':
      return 'Weekend';
    case 'Monday':
    case 'Tuesday':
    case 'Wednesday':
    case 'Thursday':
    case 'Friday':
      return 'Weekday';
    default:
      return 'Invalid day';
  }
}








//List Transformations Examples
void main() {
  doubleNumbers();
  filterNumbers();
  sumWithReduce();
  productWithFold();
  
}
void doubleNumbers() {
  List<int> nums = [1, 2, 3, 4];
  var doubled = nums.map((n) => n * 2).toList();
  print(doubled); 
} 
void filterNumbers() {
  List<int> nums = [2, 4, 6, 8, 10];
  var filtered = nums.where((n) => n >= 5).toList();
  print(filtered); // [6, 8, 10]
}

void sumWithReduce() {
  List<int> nums = [1, 2, 3, 4];
  var sum = nums.reduce((a, b) => a + b);
  print(sum); // 10
}

void productWithFold() {
  List<int> nums = [2, 3, 4];
  var product = nums.fold(1, (a, b) => a * b);
  print(product); // 24
}




//Loops Examples
void main(){
countToFive();
printNames();
countdown();
}
void countToFive() {
  for (int i = 1; i <= 5; i++) {
    print(i);
  }
}

void printNames() {
  List<String> names = ['Ali', 'Leyla', 'Nihad'];
  names.forEach((name) {
    print('Hello, $name');
  });
}

void countdown() {
  int n = 3;
  while (n > 0) {
    print(n);
    n--;
  }
  print('Go!');
} 





// Higher-Order Functions
void main(){
  
   testApplyFunction();
  useMultiplier();
  
}
void applyFunction(List<int> list, int Function(int) action) {
  var result = list.map(action).toList();
  print(result);
}

int square(int x) => x * x;

void testApplyFunction() {
  applyFunction([1, 2, 3], square); // [1, 4, 9]
}

Function makeMultiplier(int factor) {
  return (int x) => x * factor;
}

void useMultiplier() {
  var triple = makeMultiplier(3);
  print(triple(5)); // 15
}   




//Sort a list in ascending or descending order using an optional named parameter
void main() {
  var nums = [1, 2, 3, 4, 5, 6];
  print(sumEvenDoubled(nums));
}
  // even: 2, 4, 6 => doubled: 4, 8, 12 => sum: 24
  

int sumEvenDoubled(List<int> nums) {
  var filtered = nums.where((n) => n % 2 == 0);
  var doubled = filtered.map((n) => n * 2);
  return doubled.reduce((a, b) => a + b);
}





//Keep only even numbers, double them, then sum up the results.
List<int> sortList(List<int> nums, {bool descending = false}) {
  nums.sort();
  if (descending) {
    nums = nums.reversed.toList();
  }
  return nums;
}
void main(){
   var numsSorted = [3, 1, 4, 2];
  print(sortList(numsSorted)); // [1, 2, 3, 4]
  print(sortList(numsSorted, descending: true)); // [4, 3, 2, 1]

}  



void main(){
  var student = Person();
  student.greet();
}
class Person {
  String name = 'Asim';
  int age = 10;
  void greet() {
    print("Hello, $name");
  }
}  




void main(){
   var point = Point.origin(newX: 0.5, newY: 0);
  print(Point.immutable.x);
  print(point.x);
}

const double xOrigin = 0;
const double yOrigin = 0;

class Point {
  final double x;
  final double y;

  // Constant constructor
  static const Point immutable = const Point(10, 0);

  // Sets the x and y instance variables
  // before the constructor body runs.
  const Point(this.x, this.y);

  // Named constructor
  Point.origin({required double newX, required double newY})
    : x = newX,
      y = newY;
}






// 5ci chapter
abstract class Vehicle {
  void start();

  final int weight;

  Vehicle({required this.weight});
}

class Bike extends Vehicle {
  Bike({required super.weight});

  @override
  void start() {
    print('rolling into deep');
  }
}

class CarWithImpl implements Vehicle {
  @override
  void start() {
  }

  @override
  int get weight => throw UnimplementedError();
}

abstract class Animal {
  void makeSound(); // Abstract method
}

/// More realistic example of using abstract classes;
abstract class Payment {
  double amount;
  // Generative constructor;
  Payment(this.amount);

  void processPayment(); // Abstract method
}

class CreditCardPayment extends Payment {
  String cardNumber;

  CreditCardPayment(double amount, this.cardNumber) : super(amount);

  @override
  void processPayment() {
    print("Processing Credit Card payment of \$${amount} using card $cardNumber");
  }
}

class PayPalPayment extends Payment {
  String email;

  PayPalPayment(double amount, this.email) : super(amount);

  @override
  void processPayment() {
    print("Processing PayPal payment of \$${amount} from $email");
  }
}

void main() {
  var creditCardPay = CreditCardPayment(110, '416973880000000');
  var payPalPay = PayPalPayment(110, 'myacc@asoiu.edu.az');

  creditCardPay.processPayment();
  payPalPay.processPayment();
//   var myBike = Bike(weight: 4);
//   myBike.start();
//   print(myBike.weight);
}

mixin CanFly {
  void fly() {
    print("Flying...");
  }
}

class User with AgeCalculation {
  final int birthYear;

  User(this.birthYear);

  void calculateAndPrint() {
    print(calculateAge(birthYear));
  }
}

mixin AgeCalculation {
  int calculateAge(int yearOfBirth) {
    int currYear = 2025;
    return currYear - yearOfBirth;
  }
}

class Jet with CanFly {
  void printD() {
    fly();
  }
}

class Bird extends Animal with CanFly {
  @override
  void makeSound() {
    fly();

    print("Chirp Chirp ");
  }
}

*/
