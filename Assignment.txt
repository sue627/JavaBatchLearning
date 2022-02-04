Assignment 2
● Why do we need packages in java?
○ A package in Java is used to group related classes.
● What is the default imported package?
○ java.lang
● What is Class? What is Object?
○ The basic difference between Class and Object is that – Class is a user-defined
datatype that has its own data members and member functions whereas an
object is an instance of class by which we can access the data members and
member functions of the class.
● Why we need constructor?
○ The purpose of a Java constructor is to initializes the newly created object before
it is use.
● What is the default value of local variable? What is the default value
of instance variable?
○ Instance variables: boolean - false, numbers - 0, objects - null
○ Local variables - no default value
● What is garbage collection?
○ In short, when an object are not referenced by other objects, they will be garbage
collected, GC will release the memory resource that were occupied by those
objects. It will start a root set, named GC roots and find all the leaves that they
can find along the way. When an object has not appeared in the search, it will be
collected by Garbage collectors.
● The protected data can be accessed by subclasses or same
package. True or false?
○ True.
○ While protected members can be accessed anywhere in the same package and
outside package only in its child class and using the child class's reference
variable only, not on the reference variable of the parent class. We can't access
protected members using the parent class's reference
● What is immutable class?
○ Immutable class in java means that once an object is created, we cannot change
its content.
● What’s the difference between “==” and equals method?
○ == compares reference
○ Equals compares value
● What is wrapper class?
○ Wrapper classes provide a way to use primitive data types ( int , boolean , etc..)
as objects.
● What is autoboxing?
○ Autoboxing is the automatic conversion that the Java compiler makes between
the primitive types and their corresponding object wrapper classes. For example,
converting an int to an Integer, a double to a Double, and so on. If the conversion
goes the other way, this is called unboxing.
● StringBuilder is threadsafe but slower than StringBuffer, true or false?
○ False. StringBuilder is faster than StringBuffer. StringBuilder is non-synchronized,
that means it's not thread safe, two threads can call the methods of StringBuilder
simultaneously.
● Constructor can be inherited, true or false?
○ No. constructors are not members, so they are not inherited by subclasses, but
the constructor of the superclass can be invoked from the subclass.
● How to call a super class’s constructor?
○ super()
● Which class is the super class of all classes?
○ The Object class
● Create a program to count how many files/folders are there inside
one folder.
● the count method should take a parameter called Criteria like this:
count(Criteria criteria){}
● For Criteria class, multiple conditions should be included such as:
folder path, includeSubFolder or not, the extension of the file be
counted and so on.
● Optional: Take the input from keyboard.
○
● Take care of the invalid inputs. Exception handling.
○ Try catch, throws
● Get proper result displayed.
”There are XXX file(s) and XXX folder(s) inside folder XXX with
extension XXX.” or something user friendly.
class count {
public static class Criteria{
File diretory;
int numOfFile;
int numOfFolder;
File[] files;
public Criteria(File diretory) {
this.diretory = diretory;
numOfFile = 0;
numOfFolder = 0;
files = diretory.listFiles();
}
public void folderPath() {
for(File f : files) {
if(f.isFile()) numOfFile++;
else numOfFolder++;
}
}
public void print() {
System.out.println("There are " + numOfFile + " files and " + numOfFolder + " folders
inside folder " +
diretory.getAbsolutePath());
}
public boolean includeSubFolder() {
return numOfFolder!=0;
}
}
public static boolean isValidPath(String path) throws Exception {
try {
Paths.get(path);
} catch (Exception e) {
return false;
}
return true;
}
public static void main(String[] args) {
System.out.println("enter file path");
Scanner input = new Scanner(System.in);
String inputPath = input.nextLine();
input.close();
boolean check;
try
{
check = isValidPath(inputPath);
File inputFile = new File(inputPath);
Criteria criteria = new Criteria(inputFile);
criteria.folderPath();
criteria.print();
} catch (Exception e)
{
// TODO Auto-generated catch block
System.out.println("invalid directory");
}
}
}
