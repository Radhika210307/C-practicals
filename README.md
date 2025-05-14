# C++practicals
# practical 1
**Write a program to compute the sum of first n terms of the following series 
S=1/(1^1)-1/(2^2)+1/(3^3)-...1/(n^n), where ^ is exponentiation
The number of terms n is to be taken from user through cammand line. If command line
argument is not found then prompt the user to enter the value of n.
**


```c++
#include <iostream>
#include <cmath> // For pow()
using namespace std;

double seriesSum(int n) {
    double sum = 0;
    for (int i=1; i <= n; i++) {
        double term 1.0/pow(i, i);
        if (i%2==0) (
            sum -= term; // Alternate terms are negative
        } else {
            sum += term;
        }
   }
   return sum;
}
int main() {
int n;
    cout << "Enter the number of terms: ";
    cin >> n;
    cout << "Sum of series: <<< seriesSum(n) << endl;
    return 0;
}

```











![Screenshot 2025-03-16 203633](https://github.com/user-attachments/assets/726b8a29-11b8-49a3-9901-8a0452d89268)


# practical 2
**write a program to remove the duplicates from an array.**

```c++
#include <iostream>
#include <vector>
#include <set>
using namespace std;

void removeDuplicates(vector<int>& arr) {
    set<int> uniqueElements(arr.begin(), arr.end());
    arr.assign(uniqueElements.begin(), uniqueElements.end());
}
int main() {
    vector<int> arr = {1, 2, 2, 3, 4, 4, 5, 6, 6};

    cout << "Original array: ";
    for (int num : arr) cout << num << " ";

    removeDuplicates(arr);

    cout << "\nArray after removing duplicates: ";
    for (int num : arr) cout << num << " ";

    return 0;
}

```









![Screenshot 2025-03-16 204806](https://github.com/user-attachments/assets/f5e80c34-47b1-402f-bc90-5a62a4a2c260)

# practical 3
write a program that prints a table  indicating the number of occurrences of each alphabet in the text entered as command line arguments.


```c++
#include <iostream>
#include <string>
#include <map>
using namespace std;

void countOccurrences(string str) {
    map<char, int> freq;

    for (char c : str) {
        if (isalpha(c)) { // Consider only alphabets
            freq[tolower(c)]++;
        }
    }
    cout << "Character Frequency Table: \n";
    for (auto pair : freq) {
        cout << pair. first << " -> " << pair.second << endl;
    }
}
int main() {
    string input;
    cout << "Enter a string: ";
    getline(cin, input);

    countOccurrences(input);

    return 0;
}

```







![Screenshot 2025-03-16 205802](https://github.com/user-attachments/assets/156b17c1-3c93-4158-8b59-248cfe1cc796)
![Screenshot 2025-03-16 205832](https://github.com/user-attachments/assets/4319a1de-2422-4415-97f6-dac93938e59f)



# practical 4
**write a menu driven program to perform following operations on strings (without using inbuilt string functions):
a) show address of each character in string .
b) concatenate two strings.
c) compare two strings.
d) convert length of the string (use pointers).
e) convert all lowercase character to uppercase.
f) reverse the string.
**

```c++
#include <cstring> // For strlen()
using namespace std;

// Function to display ASCII values of each character in a string
void displayASCII(const char str[]) {
    cout << "ASCII values:\n";
    for (int i = 0; str[i] != '\0'; i++) {
        cout << str[i] << " -> " << int(str[i]) << endl;
    }
}

// Function to concatenate two strings (without built-in functions)
void concatenateStrings(char str1[], const char str2[]) {
    int i = strlen(str1); // Find length of str1
    int j = 0;

    while (str2[j] != '\0') {
        str1[i] = str2[j]; // Append str2 to str1
        i++;
        j++;
    }
    str1[i] = '\0'; // Null terminate the final string
}

// Function to compare two strings (returns true if equal)
bool compareStrings(const char str1[], const char str2[]) {
    int i = 0;
    while (str1[i] != '\0' && str2[i] != '\0') {
        if (str1[i] != str2[i]) {
            return false; // Strings are not equal
        }
        i++;
    }
    return str1[i] == str2[i]; // Ensure both strings end at the same position
}

// Function to find string length using pointers
int stringLength(const char *str) {
    int len = 0;
    while (*str != '\0') {
        len++;
        str++;
    }
    return len;
}

// Function to convert a string to uppercase
void toUppercase(char str[]) {
    int i = 0;
    while (str[i] != '\0') {
        if (str[i] >= 'a' && str[i] <= 'z') {
            str[i] -= 32; // Convert lowercase to uppercase
        }
        i++;
    }
}

// Function to reverse a string
void reverseString(char str[]) {
    int len = stringLength(str);
    for (int i = 0; i < len / 2; i++) {
        swap(str[i], str[len - i - 1]);
    }
}

int main() {
    char str1[100], str2[100];

    // Input strings
    cout << "Enter first string: ";
    cin >> str1;
    cout << "Enter second string: ";
    cin >> str2;

    // Display ASCII values
    displayASCII(str1);

    // Concatenation
    concatenateStrings(str1, str2);
    cout << "Concatenated String: " << str1 << endl;

    // String comparison
    cout << "Strings are " << (compareStrings(str1, str2) ? "equal" : "not equal") << endl;

    // String length
    cout << "Length of first string: " << stringLength(str1) << endl;

    // Convert to uppercase
    toUppercase(str1);
    cout << "Uppercase String: " << str1 << endl;

    // Reverse string
    reverseString(str1);
    cout << "Reversed String: " << str1 << endl;

    return 0;
}
```






![Image](https://github.com/user-attachments/assets/83258d6c-aa48-420b-951b-3e44317be151)
![Image](https://github.com/user-attachments/assets/857e1af8-6c37-4ff4-a208-783cc7299e9d)

![Image](https://github.com/user-attachments/assets/4fef2173-dfbe-4913-a916-72fffdabd479)
![Screenshot 2025-03-16 190643](https://github.com/user-attachments/assets/b8419a27-0c97-4d82-898c-49241637e1f6)



# practical 5
**write a program to merge two ordered arrays to get a single  ordered array.**
```c++
#include <iostream>
#include <vector>
using namespace std;
vector<int> mergeArrays(vector<int>& arr1, vector<int>& arr2) {
vector<int> merged;
int i =0, j =0;

while (i < arr1.size() && j < arr2.size()) {
if (arr1[i] < arr2[j])
merged.push_back(arr1[i++]);
else
merged.push_back(arr2[j++]);

while (i < arr1.size()) merged.push_back(arr1[i++]);
while (j < arr2.size()) merged.push_back(arr2[j++]);

return merged;

int main() {
vector<int> arr1 = {1, 3, 5, 7};
vector<int> arr2={2, 4,6,8};

vector<int> merged = mergeArrays(arr1, arr2);

cout << "Merged sorted array: ";
for (int num : merged) cout << num << " ";

return 0;
```






![Image](https://github.com/user-attachments/assets/d4ef3150-3a13-40ec-acb2-8bfb3ff37550)
![Image](https://github.com/user-attachments/assets/2bf3948f-7613-4f07-b83f-d27b3e03315b)

# practical 6
write a program to search a given element in a set of N numbers using binary search
1) with recursion
2) without recursion

```c++
#include <iostream>
#include <vector>
using namespace std;

// Recursive binary search
int binarySearchRecursive(vector<int>& arr, int left, int right, int key) {
if (left > right) return -1;
int mid = left + (right - left) / 2;

if (arr[mid] == key) return mid;
if (arr[mid] > key) return binarySearchRecursive(arr, left, mid - 1, key);
return binarySearchRecursive(arr, mid + 1, right, key);

// Iterative binary search
int binarySearchIterative(vector<int>& arr, int key) {
int left = 0, right = arr.size() - 1;
while (left <= right) {
int mid = left + (right - left) / 2;
if (arr[mid] == key) return mid;
if (arr[mid] > key) right = mid - 1;
else left = mid + 1;

return -1;

int main() {
vector<int> arr = {1, 3, 5, 7, 9, 11};
int key = 5;

// Recursive search
int indexRec = binarySearchRecursive(arr, 0, arr.size() 1, key);
" << (indexRec != -1 ? "Found at index " + to_string(indexRec) : "Not found") << endl;

int indexIter = binarySearchIterative(arr, key);
<< (indexIter != -1 ? "Found at index " + to_string(indexIter) : "Not found") << endl;

cout << "Recursive Binary Search:

// Iterative search

cout << "Iterative Binary Search:

return 0;
```







![Image](https://github.com/user-attachments/assets/1263bf80-1fe7-414e-8d4e-7ffdf734c067)
![Image](https://github.com/user-attachments/assets/90b5beaa-c896-4245-a73a-73b86e02fd02)

# practical 7
write a program to calculate GCD of two numbers
1)  with recursion
2) without recursion

```c++
#include <iostream>
using namespace std;

// Recursive GCD
int gcdRecursive(int a, int b) {
    return (b == 0) ? a : gcdRecursive(b, a % b);
}
// Non-recursive GCD
int gcdIterative(int a, int b) {
    while (b != 0) {
        int temp = b;
        b = a % b;
        a = temp;
    }
    return a;
}
int main() {
int a, b;
cout << "Enter two numbers: ";
cin >> a >> b;

cout << "GCD (Recursive):
cout << "GCD (Iterative):

return 0;
}

```







![Image](https://github.com/user-attachments/assets/563abfe4-d353-4e7e-a902-d253853231c2)
![Image](https://github.com/user-attachments/assets/8732513b-d591-4eb2-a2c1-9e124c74ef3d)

# practical 8
create a matrix class. write a menu- drive program to perform following matrix operations:
a)  sum
b) product
c) tranport

![Image](https://github.com/user-attachments/assets/59d3f351-5d7e-4101-82f7-6c2ab3ad4ff0)
![Image](https://github.com/user-attachments/assets/c66977ca-52ec-4147-8a34-defe22a8ade1)
![Image](https://github.com/user-attachments/assets/0f3de777-c39a-46b5-92db-4fe3647fc1fb)

# practical 9
Define a class Person having name as a data member. Inherit two classes Student and
Employec from Person. Student has additional attributes as course, marks nd yeur and
Employee has department and salary. Write display() method in all the thee classes to
display the coresponding attributes. Provide the necessary methods to show runtime
polymorphism.

```c++
#include <iostream>
using namespace std;

class Person {
protected:
    string name;
    int age;
public:
    void input() {
        cout << "Enter name and age: ";
        cin >> name >> age;
    }
    void display() {
        cout << "Name:"<<name << ", Age: " << age << endl;
    }
};
class Student : public Person {
    string course;
public:
    void input() {
    Person:: input();
    cout << "Enter course: ";
    cin >> course;
    }
    void display() {
    Person :: display();
    cout<<"Course"<< course << endl;
    }
};

class Employee : public Person {
    int salary;
public:
    void input() {
        Person :: input();
        cout << "Enter salary: ";
        cin >> salary;
    }
    void display() {
        Person :: display();
        cout << "Salary:"<< salary << endl;
    }
};
int main() {
    Student s;
    Employee e;

    cout << "Enter student details: \n";
    s.input();

    cout << "Enter employee details:\n";
    e.input();

    cout << "\nStudent Details:\n";
    s.display();

    cout << "\nEmployee Details:\n";
    e.display();
};
```





![Image](https://github.com/user-attachments/assets/38809941-9e71-4033-ac3e-1aa708e02c20)

![Image](https://github.com/user-attachments/assets/adcf7983-343a-4fbf-9dbe-94e4c7b8ddb1)
![Screenshot 2025-03-16 195123](https://github.com/user-attachments/assets/6e422a12-817f-4896-8c48-bfd64e47877b)



# practical 10
Create a class Triangle. Include overloaded functions for calculating area Overload
assignment operator and equality operator.

```c++
#include <iostream>
using namespace std;

class Triangle {
public:
// Area with base & height
double area(double base, double height) {
return 0.5 * base * height;

// Area with 3 sides (Heron's formula)
double area(double a, double b, double c) {
double s = (a + b + c) / 2;
return sqrt(s * (s - a) * (s -b)* (s -c));

}

}

};

int main() {
Triangle t;
cout << "Area (Base, Height): " << t.area(5,10) << endl;
cout << "Area (Three Sides): " << t.area(3, 4, 5) << endl;
return 0;
```





![Image](https://github.com/user-attachments/assets/31b3c6cd-8989-400c-8108-7894e6a36716)

![Image](https://github.com/user-attachments/assets/9e94c24c-6a51-4df2-bcb6-3773f8d93819)

# practical 11
Write a program to read two numbers p und q. If q is O then throw in exception else
display the result of p/q.

```c++
#include <iostream>
#include <stdexcept>
using namespace std;

class MatrixException : public exception {
public:
const char* what() const throw() {
return "Matrix dimensions are incompatible!";

}

};

void checkCompatibility(int rows1, int cols1, int rows2, int cols2) {
if (cols1 != rows2)
throw MatrixException();

int main() {
try {
checkCompatibility(2,6,4,2);
} catch (MatrixException& e) {
cout << "Error: " << e.what() << endl;

return 0;

}
```




![Image](https://github.com/user-attachments/assets/fd428fa0-ab6e-472f-b107-782bc081a83f)

![Image](https://github.com/user-attachments/assets/5554405b-2237-4d24-b663-2fcecc6284df)

# practical 12
Rewrite Matris class of Q8 with exception handling. Esceptions should be thrown by
the functions if matrices passed to them are incompatible and handled by main() function.

```c++
#include <iostream>
#include <stdexcept>
using namespace std;

class PrimeException : public exception {
public:
const char* what() const throw() {
return "Number must be greater than 1!";

// Function to check if a number is prime
bool isPrime(int num) {
if (num < 2)
throw PrimeException();

for (int i = 2; i * i <= num; i++) {
if (num % i == 0)
return false;

return true;

int main() {
int num;
cout << "Enter a number: ";
cin >> num;

try {
if (isPrime(num))
cout << num << " is a prime number. \n";
else
cout << num << " is not a prime number. \n";
} catch (PrimeException& e) {
cout << "Error: " << e.what() << endl;

return 0;

}
```






![Image](https://github.com/user-attachments/assets/9517f2bd-af51-4fbe-b48d-924ddae7fc9f)

![Image](https://github.com/user-attachments/assets/48f116e4-562a-4b26-b8c9-0152113d38b5)

![Image](https://github.com/user-attachments/assets/b51e6005-f1a2-4ef3-b6cf-03cf99fdbed2)

# practical 13
Create a class Student containing fields for Roll No., Name, Class, Year and Total
Marks. Write a program to store 5 objects of Student class in a file. Retrieve these records
from file and display them.

```c++
#include <iostream>
using namespace std;

class Student {
public:
    int rollNo;
    string name;
    string className;
    int year;
    float totalMarks;

    // Function to take input
    void input() {
        cout << "Enter Roll No, Name, Class, Year, and Total Marks: ";
        cin >> rollNo >> name >> className >> year >> totalMarks;
    }

    // Function to display student details
    void display() {
        cout << "Roll No: " << rollNo << ", Name: " << name
             << ", Class: " << className << ", Year: " << year
             << ", Total Marks: " << totalMarks << endl;
    }
};

int main() {
    Student students[5];

    // Taking input for 5 students
    for (int i = 0; i < 5; i++) {
        cout << "Enter details for Student " << i + 1 << ":\n";
        students[i].input();
    }

    cout << "\nStudent Details:\n";
    
    // Displaying student details
    for (int i = 0; i < 5; i++) {
        students[i].display();
    }

    return 0;
}
```





![Image](https://github.com/user-attachments/assets/1546b8b9-5b50-4a15-ae6b-d2aa2eaae97d)
![Screenshot 2025-03-16 200404](https://github.com/user-attachments/assets/9a4b1607-1c69-4ca9-a754-1d6cb0749e82)



# practical 14
**copy the content of one text file to another file,after removing all whitespaces.**

```c++
#include <iostream>
#include <fstream>  // For file handling
#include <cctype>   // For isspace() function

using namespace std;

void removeWhitespaceAndCopy(const string &inputFile, const string &outputFile) {
    ifstream inFile(inputFile);  // Open input file
    ofstream outFile(outputFile); // Open output file

    // Check if both files opened successfully
    if (!inFile) {
        cerr << "Error: Cannot open input file '" << inputFile << "'!\n";
        return;
    }
    if (!outFile) {
        cerr << "Error: Cannot open output file '" << outputFile << "'!\n";
        return;
    }

    char ch;
    while (inFile.get(ch)) {
        if (!isspace(ch)) { // Ignore whitespaces
            outFile.put(ch);
        }
    }

    inFile.close();
    outFile.close();

    cout << "File copied successfully after removing whitespaces!\n";
}

int main() {
    string source = "source.txt";       
    string destination = "output.txt";  

    removeWhitespaceAndCopy(source, destination);
    
    return 0;
}
```
![Screenshot 2025-03-16 202116](https://github.com/user-attachments/assets/dae2dff4-7d46-4eb5-b49c-b1bd778ab4f2)

![Screenshot 2025-03-16 202230](https://github.com/user-attachments/assets/83b7e3b8-6a57-4f54-8d06-25ef522f9453)

