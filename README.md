# CSharp-Notes-Part-1
### 1. Method Call Errors
`
    public static void GetMyNumber(){
        return 5;
    }
`
###### Error:- Argument 1: cannot convert from 'void' to 'bool'
`
   public static string GetMyNumber(){
        return 5;
    }
`
###### Error:- Cannot implicitly convert type 'int' to 'string'
`
 public static bool GetMyNumber(){
        return 5;
    }
`
###### Error:- Cannot implicitly convert type 'int' to 'bool'
`
   public static int GetThoseNumbers(int num1, string num2){
        int ans = num1 + num2;
        return ans;
    }
`
###### Error:- Cannot implicitly convert type 'string' to 'int'
###### Note:- string and int can only be concatenated when the holding variable is a string (the ultimate data type), the vice versa creates the above error.

### 2. Arrays Important Points
`
  int[] numbersArray2;
  Console.WriteLine(numbersArray2);
`
###### Output:- error CS0165: Use of unassigned local variable 'numbersArray2'

`
   int[] numbersArray2={}; OR int[] numbersArray2={4,7};
    Console.WriteLine(numbersArray2);
`
###### Output:- System.Int32[]
`
 foreach(var a in numbersArray2)
 {
            Console.WriteLine(++a);
 }
`
###### Not Allowed As The code foreach(var a in numbersArray2){ Console.WriteLine(++a); } is allowed in C#, but it does not modify the elements of the numbersArray2 array. This is because the foreach loop iterates over a copy of the elements, not the actual elements themselves. Therefore, incrementing a inside the loop does not affect the original array elements. If you want to modify the elements of the array, you should use a for loop instead, which allows direct access to the elements by their index.

`
int[] numberArray2 = new int[] {99,88,77};
`
###### This is the most explicit way to decl;are array as it specifically declares the data type. 
`
        int[] numberArray3 = new int[5];
        foreach(var a in numberArray3){
            Console.WriteLine(a);
        }
`
##### Note: - This will declare an array of size 5 with all values set to be 0, but if i do  int[] numberArray3 = new int[5]{}, well then i need to ensure there are 5 values as {} acts a s an initializer and must have all the value as per the alotted space.  
##### Note:- arr.Length property to get the length of the array
##### Additional Length Error:- System.IndexOutOfRangeException: Index was outside the bounds of the array.
`
  int[] arr={4,7} --> [4,7]
  OR
  int[] arr2 = new int[3] --> Size given but not initialized, hence  [0,0,0]
  OR
  int[] arr3 = new int[2]{4,7} --> Size given and initialized with values, hence [4,7]
`
##### To Access Indexes
`
   int[] arr=new int[5]{1,8,56,21,747};
    arr[0] -> 1
    arr[4] -> 747
    arr[5] -> Index Out Of Bound
    arr[-1] -> Index Out Of Bound as C# doeasn't support -ve indexing like Js
    arr[^1] -> 747
    arr[^5] -> 1
    arr[^6] -> Index Out Of Bound
`
### 3. List Important Points
`
   List<int>lista = new List<int>;  ---> Error as it must be initialized through initializer {}
   List<int> lista2 = new List<int> {21,3,4,5,6} --> Correct Way
`
#### Note:- To get length of list, use -> lista.Count
#### Note:- To get capacity which is 2^n always -> lista.Capacity
#### Note:- Additionally, the Capacity property can be used to get the maximum number of elements the list can hold before it needs to resize. The Capacity is always greater than or equal to the Count. So For a lista.Count = 5, the lista.Capacity = 8, the nearest greater or equal value
`
  int[] arr=new int[5]{1,8,56,21,747};
  List<int> lista2 = new List<int>(arr);
  foreach(var a in lista2)
  {
           Console.WriteLine(a);
  }
`
#### Note:- You can set an iterable in List using ()
#### Note:- lista2.Add() adds the element at the end of list whereas lista.Insert(position, element) does it at a specific position.
#### Note:- To find the index of an element, use [lista2.IndexOf(100)] while for arrays you will have to use [System.Array.IndexOf(arr, 21)]

### 4. Types Of Loops
`
         int[] arr=new int[5]{1,8,56,21,747};
        List<int> lista2 = new List<int>(arr);
       //---------Now While
       var lista2Length = lista2.Count;
       while(lista2Length>0){
           Console.WriteLine(lista2[lista2Length-1]);
           lista2Length--;
       }
        //---------Now Do-While
       var lista3Length = lista2.Count;
       do{
           Console.WriteLine(lista2[lista3Length-1]);
           lista3Length--;
       }while(lista3Length>0);
       //---------For loop
       var lista4Length = lista2.Count;
       for(var i=0; i<lista4Length; i++){
           Console.WriteLine(lista2[i]);
       }
       //-----------For Each Loop
       var lista5Lenght = lista2.Count;
       foreach(var a in lista2){
           Console.WriteLine(a);
       }
`
#### Note:- 
> The difference between new List<int> {2, 7, 74, 56, 98} and new List<int>() {2, 7, 74, 56, 98} lies in how the list is initialized:
> new List<int> {2, 7, 74, 56, 98}: This initializes a new list and immediately adds the elements 2, 7, 74, 56, and 98 to it. The list is created with these specific elements.
> new List<int>() {2, 7, 74, 56, 98}: This also initializes a new list and adds the elements 2, 7, 74, 56, and 98 to it. The difference is that the list is first created with no initial capacity (using the default constructor new List<int>()), and then the elements are added.
> In practice, both lines of code achieve the same result: a list containing the elements 2, 7, 74, 56, and 98. However, the first approach is more concise and is generally preferred for readability.

### 5. Classes
`
  public class HelloWorld
{
    public static void Main(string[] args)
    {
        Action act1 = new Action();
        act1.JohnWick();
        Action.IronMan();
    }
}
public class Action{
    public void JohnWick(){
        Console.WriteLine("This IS Wick!");
    }
    public static void IronMan(){
        Console.WriteLine("This IS IronMan!");
    }
    public static void Valkrye(){
        Console.WriteLine("This IS Valkrye!");
    }
    public static void ArnoldS(){
        Console.WriteLine("This IS ArnoldS!");
    }
}
`
#### Note:- for non-static methods:- Error Is =  An object reference is required for the non-static field and for static methods:- Error Is =  cannot be accessed with an instance reference; qualify it with a type name 

` public static void Main(string[] args)
    {
       Action act1 = new Action(12);
       Action act2 = new Action(42);
    }
   public class Action{
      public Action(int a){
          Console.WriteLine($"Number {a}");    
      }
  }
`
#### Interesting Case:-
`
  public class HelloWorld
{
    public static void Main(string[] args)
    {
        Player player = new Player("John");
        player.SayHello();
    }
}
class Player {
    public string name = "-";    
    public Player(string name) {
        Console.WriteLine($"Creating player {name}!");
    }
    public void SayHello() { 
        Console.WriteLine($"Hello {name}!");
    }
}
`
#### Note:- Output will be :- 
Creating player John!
Hello -!

