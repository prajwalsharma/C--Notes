---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

							STRINGS

---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
1. String Comparison:

	(i) String.Compare(string1, string2);
		Return "0"  if string1 = string2
		Return "1"   if string1 > string2
		Return "-1"  if string1 < string2
		Case Sensitive

	(ii) String.Compare(string1, string2, true);
	 	Case Insensitive

	(iii) Using Switch Case

		switch(string){
			case "EXIT":
			case "exit":
			case "QUIT":
			case "quit":
			        	return true;
			}
--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

2. String Conversion:

	(i) Convert to uppercase

		string lowerCase = "hello";
		string upperCase = lowerCase.ToUpper();		// HELLO

	(ii) Convert to lowercase

		string upperCase = "HELLO";
		string lowerCase = upperCase.ToLower();		// hello

	(iii) Converting first letter of string to upper/lower case
	
		string s1 = "chuck";
		string properName = char.ToUpper(s1[0]).ToString() + s1.Substring(1, s1.Length - 1);		// Chuck

	(iv) Substring

		string s1 = "hello";
		string subString = s1.Substring(1, s1.Length - 1);			// ello

--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

3. String Traversing:

	(i) Using foreach loop
		
		string s1 = "hello";
		foreach(char ch in s1 ){
			Console.Write(ch);					// hello
		}

----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

4. String Searching:

	(i) IndexOf('c');						// To find index of any character in a string

		string favoriteFood = "cheeseburger";
				   012345678910
		int index = favoriteFood.IndexOf('s');				// 4

		Returns "-1" if not found

	(ii) IndexOfAny(character array[]);					// Find the first occurance of given character array in a string

		char[] charactersToLookFor = { 'a', 'b', 'c'};
		int index = favoriteFood.IndexOfAny(charactersToLookFor );		// 0 - c
					OR
		int index = favoriteFood.IndexOfAny(new char[] { 'a', 'b', 'c' } );	// 0 - c

	(iii) LastIndexOf(character); 					// To find last index of any given character in a string

		int index = favoriteFood.LastIndexOf('e');				// 9 - e

	(iv) LastIndexOfAny(character array)				// Same as IndexOfAny(), but starts from last

		int index = favoriteFood.LastIndexOfAny(new char[] {'a', 'b', 'c'} );	// 6 - b

	(v) Contains("substring")					// To check if a substring exists in a string

		bool isContains = favoriteFood.Contains("ee");			// True
	
	(vi) Substring("substring");					// To get a substring out of a string

		string subString = favoriteFood.Substring(1, favoriteFood.Length - 1);	// eeseburger

---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

5. Check if string is empty:

	(i) IsNullOrEmpty(string);

		bool isNull = string.IsNullOrEmpty(favoriteFood);				// False

	(ii) Declaring Empty strings
		(a) string s1 = "";
		(b) string s2 = string.Empty;

----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

6. String Manipulation: 

	(i) Trim();								// Remove white spaces from both ends

		string s1                 = "     hello     ";
		string goodString = s1.Trim();						// hello

	(ii) use Trim() to remove any given character from string

		string s1                = "$hello$";
		string goodString =  s1.Trim('$');					// hello

	(iii) TrimFront(character)							// Remove white spaces from front only

		string s1 = "$hello$";
		s1 = s1.TrimFront('$');						// hello$

	(iv) TrimEnd(character)							// Remove white spaces from end only

		string s1 = "$hello$";
		s1 = s1.TrimEnd('$');						// $hello

----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

7. String Conversions:

	(i) Converting string to Integer
		
		string s1 = Console.ReadLine();						// "123445" - string
		int num = Convert.ToInt32(s1);					// 123445 number
			OR
		int num = Int32.Parse(s1);						// 123445


	(ii) Difference between Convert.ToInt32() & Int32.Parse()

		(i) Convert.ToInt32() can take null as an argument - Int32.Parse() will throw ArgumentNullException error
		(ii) Convert.ToInt32('1'); 	// 49 - ASCII value
		      Int32.Parse('1');		// 1
		(iii) Convert.ToInt32() takes an object as an argument - Int32.Parse take string as an argument
		(iv) Convert.ToInt32() calls int.Parse() internally	


	(iii) IsDigit(character);							// Check whether the character is a digit or not

		char c = 's';
		bool isDigit = Char.IsDigit(s);

		char c = '1';							// false
		bool isDigit = Char.IsDigit(c)						// true

	(iv) int.TryParse();								// Check whether parsing can be done or not

		string s1 = "abc";
		string s2 = "10";
		int result;

		bool isValidNumber = int.TryParse(s1, out result);				// False - result = 0
		bool isValidNumber = int.TryParse(s2, out result);				// True - reult = 10

---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

8. String Methods:

	(i) Split();									// Splits a string into array of strings using a delimiter

		string s1 = "There is a cat";
		string[] stringArray = s1 .Split(' ');					// There
										// is
		foreach(string s in stringArray){					// a
			Console.WriteLine(s);					// cat
		}

	(ii) Join();								// Joins an  array of string into one string

		string[] brothers = { "Chuck", "Norris", "Is", "A", "Legend" };
		string theBrothers = string.Join(":", brothers);				// Chuck:Norris:Is:A:Legend

	(iii) Replace('','');								// Replace one character with another

		string s = "Danger No Smoking";
		s = s.Replace(' ', '!');							// Danger!No!Smoking

	(iv) Converting string to char array

		string s = "hello";
		s = s.ToCharArray();

	(v) Converting char array to string

		char[] a = {'a', 'b', 'c'};
		string s = new string(a);
---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

9. Formatting:

	(i)  Console.WriteLine("{0:c}", 123);						// $123
	(ii) Console.WriteLine("{0:F1}", 123.29);						// 123.3
	(iii) Console.WriteLine("{0:F2}", 123.347);					// 123.35		
	(iv) Console.WriteLine("{0:N0}", 12345);						// 12, 345 - Add commas

--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

10. String Builder:

	(i) using System.Text;

		StringBuilder sb = new StringBuilder("012");
		sb.Append("34");
		sb.Append("56");;
		string result = sb.ToString();						// "0123456"

	(ii) StringBuilder sb = new StringBuilder(256);					// Setting the capacity to store 256 strings
	      StringBuilder sb = new StringBuilder();					// Default capacity 16

	(iii) StringBuilder sb = new StringBuilder("jones");
	        sb[0] = char.ToUppper(sb[0]);
	        string s = sb.ToString();							// Jones


----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

							COLLECTIONS

-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

1. Array

	(i) int[] myArray = {1, 2, 3, 4, 5};						// initialized array
	(ii) int[] myArray = new int[6];						// empty array with defined length

	(iii) IndexOutOfRangeException						// if try to access more than arrays length

	(iv) int n = 5;
	       int[] myArray = new myArray[n];						// variable length array

	(v) myArray.Length;								// Returns total number of elements in an array

	(vi) Array.Sort(myArray);							// Sorts the array

	(vii) var myArray = new [] {1, 2, 3, 4, 5}						// Array declaration using var keyword


2. Problem with Arrays
	
	(i) Fixed length 
	(ii) Cost of inserting or deleting elements to/from middle is costly
	(iii) Multidimensional data structures are only possible through arrays.
	(iv) Can store data of only same type



3. Generic Collections - data type is specified



4. Lists:

	(i) List<int> myList = new List<int>();
	     myList.Add(1);
	     myList.Add(2);
	     myList.Add("hello")							// compile time error

	(ii) AddRange(); 								//Add an array into List

		int[] myArray = {1, 2, 3, 4};
		List<int> myList = new List<int>();
		myList.AddRange(myArray);
			OR
		List<int> myList = new List<int>(myArray);

	(iii) int[] my Array = myList.ToArray();						// Converting a List into an Array

	(iv) myList.Count								// Returns count of elements in the List

	(v) myList.Sort();								// Sorts the entire List - Implements IComparable

	(vi) myList.Insert(3, 6);							// inserts 6 at third position

	(vii) myList.Delete(2);							// Deletes the second element




5. Dictionaries

	(i) Dictionary<string, string> dict= new Dictionary<string, string>();			// Creating a Dictionary
	     dict.Add("C#", "Cool");
	     dict.Add("Java", "Good");

	(ii) ContainsKey("string");							// To search a key in dictionary
		
		bool isContain = dict.ContainsKey("C#");					// True

	(iii) ContainsValue("string");
	     
		bool isContain = dict.ContainsValue("C#");				// False

	(iv) Traversing the dictionary

		foreach( KeyValuePair<string, string> pair in dict){
			key = pair.Key;
			value = pair.Value;
		}

	(v) if (dictionary.ContainsKey("apple")) {
           		 int value = dictionary["apple"];
            		Console.WriteLine(value);
        	}

	(vi) TryGetValue();								// To find a value through its key

		string s = "";
		if(dict.TryGetValue("C#", out s)){
			Console.WriteLine(s);					// Cool
		}

	(vii) Using var

		var data = new Dictionary<string, int>();
		data.Add("Cat", 1);
		data.Add("Dog, 2");

		Console.Write(data["Cat"] - data["Dog"]);				// -1



6. HashSet<T>									// Collection with no duplicate values

	(i) Union - Joins the members of two sets into one.
	(ii) Intersection - Find the common elements in two sets.
	(iii) Difference - Find elements in one set that do not appear in a second set.

	(iv) Creating a Set:

		HashSet<int> smallPrimeNumbers = new HashSet<int>;
		smallPrimeNumbers.Add(2);
		smallPrimeNumbers.Add(3);
					OR
		HashSet<int> smallPrimeNumbers = new HashSet<int> {2, 3, 5};
					OR
		List<int> list = new List<int>{1, 2, 3, 4};
		HashSet<int> num = new HashSet<int>(list);				// Add list into HashSet

	(v) hash.Add() returns a bool whether the number is added or not

		hash.Add(2);							// True
		hash.Add(2);							// False - 2 is already added

	(vi) Implement Union:

		List<string> colors = new List<string> { "red", "orange", "yellow" };
		string[] moreColors = new string[] { "orange", "yellow", "green", "blue", "violet" };
		
		HashSet<string> combined = new HashSet<string>(colors);			// Added list to HashSet
		combined.UnionWith(moreColors);					// union list with array

		foreach(string color in combined){
			Console.WriteLine(color);					// "red", "orange", "yellow", "green", "blue", "violet"
		}

	(vii) Implement Intersection:

		List<string> list = new List<string> { "Apple", "Banana", "Grapes", "Orange"};
		List<string> list2 = new List<string> { "Apple", "Apricot", "Guava", "Grapes" };
		
		HashSet<string> hash1 = new HashSet<string>(list);			// Added list to hashset
		hash1.IntersectWith(list2);						// intersect list with list2

		foreach(string s in hash1){
			Console.WriteLine(s);					// "Apple", "Grapes"
		}

	(vii) Opposite of Intersection:

		hash1.SymmetricExceptWith(list2);					// "Banana", "Orange", "Apricot", "Guava"

	(viii) Implement Difference:							// Remove Common elements from list

		Queue<int> queue = new Queue<int>(new int[] {0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 17});
		HashSet<int> unique = new HashSet<int>{1, 3, 5, 7, 9, 11, 13, 15};
		
		unique.ExceptWith(queue);						// Remove queue elements from unique

		foreach(int n in unique){
			Console.WriteLine(n);					// 11, 13, 15
		}
	

7. Files - Skipped


8. Iterators - Skipped


	
----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

							INTERFACES
				https://www.codeproject.com/Articles/18743/Interfaces-in-C-For-Beginners

-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

	(i) Interface in C# is used to achieve runtime Polymorphism.
	(ii) Using Interface we can call functions from different classes with the same Interface object. 
	(iii) It cannot contain variables - Throw error if you declare variables in an Interface.
	(iv) Interface cannot have method definition.
	(v) Implementation of Interface methods should be "Public".

	namespace InterfaceDemo {
		interface IOne {
			void One();
		}

		interface ITwo {
			void Two();
		}

		interface IThree : IOne {
			void Three();
		}

		interface IFour {
			void Four();
		}

		interface IFive : IThree {
			void Five();
		}

		interface IEven : ITwo, IFour {
		
		}

		clasee OddEven : IEven, IFive {
			
			public void One() {
				Console.WriteLine("This is ONE");
			}

			public void Two() {
				Console.WriteLine("This is TWO");
			}

			public void Two() {
				Console.WriteLine("This is TWO");
			}

			public void Three() {
				Console.WriteLine("This is THREE");
			}

			public void Four() {
				Console.WriteLine("This is FOUR");
			}

			public void Five() {
				Console.WriteLine("This is FIVE");
			}
		}

		class Program{
			static void Main(string[] args) {
				Console.WriteLine("This is Odd");
				IFive ob1 = new OddEven();
				ob1.One();
				ob1.Three();
				ob1.Five();

				Console.WriteLine("This is Even");
				IEven ob2 = new OddEven();
				ob2.Two();
				ob2.Four();	
			}
		}
	}

	
	(vi) Service Locator - Loose Coupling in C# using interfaces - http://www.dotnetfunda.com/articles/show/2319/implement-decouple-architecture-in-interface

	namespace BlogProject {
		
		interface IPerson {
			void ShowCountry();
		}

		class IndianPerson : IPerson {
			public void ShowCountry() {
				Console.WriteLine("I am Indian");
			}
		}

		class USPerson : IPerson {
			public void ShowCountry() {
				Console.WriteLine("I am an American");
			}
		}

		class PersonSupplier {
			public static IPerson ReturnPerson(string country) {
				if(country == "India") {
					return new IndianPerson();
				}
				else if (country == "US") {
					return new USPerson();
				}
				else
					return null;
			}
		}

		class Program {
			static void Main ( string[] args ) {
				Iperson objPerson = PersonSupplier.ReturnPerson("India");
				objPerson.ShowCountry();
			}
		}
	}




----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

						     DEPENDENCY INJECTION
				http://www.tutorialsteacher.com/ioc/register-and-resolve-in-unity-container

-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------


1. Inversion of Control (IoC)     			------------------->    		
						              Principle
2. Dependency Injection Principle (DIP)		------------------->		


3. Dependency Injection (DI)			-------------------> Pattern that implements IoC principles to achieve loose coupling
4. IoC Containers - 3rd Party			-------------------> FrameWork for automatic dependency injection



	(i) Inversion of Control

		public class A {
			B b;

			public A() {
				b = new B();
			}

			public void Task1 () {
				b.SomeMethod();
			}
		}

		public class B {
			public void SomeMethod () {
				//doing something
			}
		}

	(a) Class A is dependent on class B
	(b) Class B is a dependency of class A
	(c) It controls the creation and lifetime of objects of dependency class
	(d) IoC principle suggests to invert the control, means separate the controlling stuff to another class.


	(ii)	public class A {
			B b;

			public A() {
				b = Factory.GetObjectOfB();	// Solution
			}

			public void SomeMethod() {
				b.SomeMethod();
			}
		}

		public class Factory {
			public static void SomeMethod () {
				return new B();		// This factory method returns object of the B class
			}
		}

	(a) Dependent object creation is inverted from class A to Factory class


--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

							EXAMPLE

---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
	
1.  In the typical n-tier architecture, the User Interface (UI) uses Service layer to retrieve or save the data.
    The service layer uses the BusinessLogic class to apply business rules on the data.
    The BusinessLogic class depends on the DataAccess class which retrieves or saves the data to the underlying database. 
    This is simple n-tier architecture design. Let's focus on the BusinessLogic and DataAccess class to understand IoC.



	public class BusinessLogicLayer {
		
		DataAccessLayer DalObject;				// Object Creation of DataAcessLayer

		public BusinessLogicLayer() {
			DalObject = new DataAccessLayer();
		}

		public string GetCustomerName(int id) {
			return DalObject.GetCustomerName(id);
		}
	}

	public class DataAccessLayer {
		public DataAccessLayer() {

		}

		public string GetCustomerName(int id) {
			return "Prajwal";
		}
	}

	(i) BusinessLogicLayer class is dependent on DataAccessLayer class.

	(ii) In the above example, BusinessLogicLayer and DataAccessLayer are tightly coupled classes because
	      BusinessLogicLayer class includes the reference of concrete DataAccessLayer class. 
	      It also creates an object of DataAccessLayer class and manages the lifetime of an object.

	(iii) CustomerBusinessLogic and DataAccess classes are tightly coupled classes. 
	       So, changes in the DataAccess class will lead to changes in the CustomerBusinessLogic class.
	       For example, if we add, remove or rename any method in DataAccess class
	       then we need to change CustomerBusinessLogic class accordingly.

	(iv) Suppose, customer data comes from different databases or web service in future 
	       we may need to create different classes for so it leads to changes in CustomerBusinessLogic class.

	(v) CustomerBusinessLogic class creates an object of DataAccess class using new keyword. 
	      There may be multiple classes which use DataAccess class and create its object. 
	      So if you change the name of the class, then you need to find all the places in your source code
	      where you create objects of DataAccess and make the change throughout the code. 
	      This is repetitive code for creating an object of same class and maintaining its dependencies.

	(vi) Because CustomerBusinessLogic class creates an object of concrete DataAccess class, 
	       it cannot be tested independently (TDD). DataAccess class cannot be replaced with mock class.

	(vii) So, to solve the above problems and get a loosely coupled design, we can use IoC and DIP principles together.

	(viii) Patterns to achieve IoC :
		(a) Factory
		(b) Service Locator
		(c) Abstract Factory
		(d) Template Method
		(e) Strategy
		(f) Dependency Injection


 Step 1: - Implement Factory Class

	
	public class DataAccessFactory {
		public static DataAccessLayer GetDataAccessObject() {
			return new DataAccessLayer();
		}
	}

	public class BusinessLogicLayer {
	
		public BusinessLogicLayer() {
			
		}

		public string GetCustomerName(int id) {
			
			DataAccessLayer DalObject = DataAccessFactory.GetDataAccessObject();
			return DalObject.GetCustomerName(id);
		}
	}

Step 2:-	Implement Dependency Inversion Principle (DIP)

	1. High level modules should not depend on Low level Modules.
	2. Abstraction should not depend on details, details should depend on abstraction.


	public class DataAccessFactory {
		public static DataAccessLayer GetDataAccessObject() {
			return new DataAccessLayer();
		}
	}

	public class BusinessLogicLayer {
	
		public BusinessLogicLayer() {
			
		}

		public string GetCustomerName(int id) {
			
			DataAccessLayer DalObject = DataAccessFactory.GetDataAccessObject();
			return DalObject.GetCustomerName(id);
		}
	}

	public class DataAccessLayer {
		public DataAccessLayer() {

		}

		public string GetCustomerName(int id) {
			return "Prajwal";
		}
	}

	(a) In the above example, we implemented factory pattern to achieve IoC. But, CustomerBusinessLogic class
	      uses concrete DataAccess class. So still it is tightly coupled even though we have inverted the
	      dependent object creation to the factory class.

	(b) As per DIP definition, a high-level module should not depend on low-level modules. 
	      Both should depend on abstraction. So, first, decide which is the high-level module (class) and low-level module.
	      High-level module is a module which depends on other modules. 
	      In our example, CustomerBusinessLogic depends on DataAccess class, so CustomerBusinessLogic is high-level
	     module and DataAccess is low-level module. So, as per first rule of DIP, CustomerBusinessLogic should 
	     not depends on concrete DataAccess class, instead both classes depends on abstraction.


3. Use IoC containers to automatically use DI. e.g Unity, ninject

--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

							DELEGATES
					http://www.tutorialsteacher.com/csharp/csharp-delegates
---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------


1. Delegates contains the reference to a function.
	
	(a) Define a delegate type
	(b) Create an Instance of the delegate type.
	(c) Pass in the delegate instance as a parameter to the workhorse method.
	(d) Invoke the delegate to help do the job.
	(e) Invoking the delegate invokes the callback method.

2. Delegate is a data type, we can create an instance of the delegate type.

3. Example

	(a) Simple delegate

	class Program {
 
		// declare delegate
		public delegate void Print(int value);

		static void Main(string[] args)
    		{
        
			// Print delegate points to PrintNumber
        			Print printDel = PrintNumber;
			 	      OR
			Print printDel = new Print(PrintNumber);
          
        			printDel(100000);
        			printDel(200);

        			// Print delegate points to PrintMoney
        			printDel = PrintMoney;

       			 printDel(10000);
        			printDel(200);
    		}

    		public static void PrintNumber(int num)
    		{
        			Console.WriteLine("Number: {0,-12:N0}",num);
   		 }

    		public static void PrintMoney(int money)
    		{
       		 Console.WriteLine("Money: {0:C}", money);
    		}
	}


	(b) Passing Delegate as a parameter
	
	namespace SimpleDelegateExample {

		class Program {

			delegate int MyDelType(string name);					// Delegate definition

			static void Main( string[] args) {
				
				MyDelType del = new MyDelType(Program.CallBackMethod);		// Delegate instance creation pointing 
											// to the CallBackMethod below

				UseTheDel(del,"hello");					// Call workhorse method to invoke the delegate
				
			}

			private static void UseTheDel( MyDelType del, string arg) {			// workhorse method to invoke the delegate		

				if(del == null) { return; }

				Console.WriteLine("UseTheDel writes {0}", del(arg));

			}

			public static int CallBackMethod (string stringPassed) {			// CallBackMethod
				
				Console.WriteLine("CallBack method writes {0}", stringPassed);
				Return stringPassed.Length;				

			}
			
		}

	} 


	(c) Multicast Delegate

	public delegate void Print(int value);

	static void Main(string[] args)
	{       
    		Print printDel = PrintNumber;
    		printDel += PrintHexadecimal;
   		 printDel += PrintMoney;

    		printDel(100000);
	}

	public static void PrintNumber(int num)
	{
    		Console.WriteLine("Number: {0,-12:N0}",num);
	}

	public static void PrintMoney(int money)
	{
    		Console.WriteLine("Money: {0:C}", money);
	}

	public static void PrintHexadecimal(int dec)
	{
    		Console.WriteLine("Hexadecimal: {0:X}", dec);
	}


--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

							ANONYMOUS METHODS
					    http://www.tutorialsteacher.com/csharp/csharp-delegates
---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

1. Methods without name.
2. Can be defined by using keyword "delegate".

		class Program {

			public delegate void Print(int n);

			static void Main(string[] args) {

				Print print = delegate(int n) {
					Console.WriteLine("Inside Anonymous method {0}", n);
				};	

				print(100);		
			}
		}

3. Pass anonymous method as function parameter

		
		class Program {

			public delegate void Print (int value);

			public static void PrintHelperMethod(Print del, val) {

				val += 1;
				del(val);

			}

			static void Main(string[] args) {

				PrintHelperMethod( delegate(int val){Console.WriteLine("Inside anonymous method {0}",val);} , 100 );
			
			}

		
		}


--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

							Lambda Expression
					    http://www.tutorialsteacher.com/linq/linq-lambda-expression
---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------


1. Lambda expression is a shorter way to express anonymous methods.


		class Program {

			public delegate void Print (int value);

			static void Main(string[] args) {

				Print print = (val) => {Console.WriteLine("Inside Lambda expression {0}", val);};

							OR

				Print print = val => Console.WriteLine(val);

				print(10);
			
			}
		}










	
