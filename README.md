# Sets lab

Fork and clone this repo. On your fork, answer and commit the follow questions. When you are finished, submit the link to your repo on Canvas.


## Question 1

Ms. Gabriel Williams is a botany professor at District College. One day, she asked her student Mickey to compute the average of all the plants with distinct heights in her greenhouse.

Input: heights of trees below:
`161 182 161 154 176 170 167 171 170 174`

Output:
`169.375`

let treeHeightArr: [Double] =  [161, 182, 161, 154, 176, 170, 167, 171, 170, 174]
let treeHeightSet = Set(treeHeightArr)
var sumOfHeight = Double()

for x in treeHeightSet {
sumOfHeight = sumOfHeight + x
}
var averageHeight: Double = sumOfHeight / Double(treeHeightSet.count)
print(averageHeight)





## Question 2

Determine if a String is a pangram. A pangram is a string that contains every letter of the alphabet at least once.

 e.g `"The quick brown fox jumps over the lazy dog"` is a pangram
 e.g `"The quick brown fox jumped over the lazy dog"` is NOT a pangram

//SOLUTION ONE 
//(this was the solution i came to before realizing that making a string into a set automaticly splits the words into characters not strings)

var sentence = "The quick brown fox jumps over the lazy dog"
sentence = sentence.lowercased()

var char = Set<Character>()
for a in sentence {
if a == a {
char.insert(a)
}
}
char.remove(" ")

let alphabet: Set<Character> = ["a","b","c","d","e","f","g","h","i","j","k","l","m","n","o","p","q","r","s","t","u","v","w","x","y","z"]

var intersect: Set<Character> = char.symmetricDifference(alphabet)

if intersect.count == 0 {
print("its a pangram")
} else {
print("not pangram")
}



//SOLUTION TWO
//(this was the simplier solution which i didnt realize was possible since i thought the original sentence needed to be broken into characters, and didnt realize this naturally happens when a string is made into a set )

var secondSentence = "The quick brown fox jumped over the lazy dog"
secondSentence = secondSentence.lowercased()
var secondSentenceSet = Set(secondSentence)
print(secondSentenceSet)

var alphabet = "abcdefghijklmnopqrstuvwxyz"
var setAlphabet = Set(alphabet)

if secondSentenceSet.isSuperset(of: alphabet) {
print("its a pangram")
} else {
print("not pangram")
}




## Question 3

The set S originally contains numbers from 1 to n in ascending order. Unfortunately, due to the data error, one of the numbers in the set was duplicated to another number in the set. This results in the repetition of one number and loss of another number in the set.

You are given an array `nums` representing the data status of the set S after the error occurred. Your task is to first find the number occurs twice and then find the number that is missing from the sequence. Return these two values in the form of an array.

 Example 1:
 Input: `nums = [1,2,2,4]`
 Output: `[2,3]`

 Example 2:
 Input: `nums = [1,1]`
 Output: `[1,2]`

 Example 3:
 Input: `nums = [2,2]`
 Output: `[2,1]`

// ( i know this dosent use strings to answer the question and will only work for the contex of the question and the orders moving in an asscending order but people said this wouldn't work so naturally i was determined to prove it does)

var nums = [1,2,2,4,]
var answer = [Int]()

var extraNum = Int()
var missingNum = Int()

for x in nums {
if x != extraNum {
extraNum = x
} else {
answer.append(x)
}
}

for i in 1...nums.count {
if nums.contains(i) {

} else {
answer.append(i)
}
}
print(answer)






## Question 4

Given the 4 arrays of Ints below, create a new array, sorted in ascending order, that contains all the values without duplicates.

```swift
let arr1 = [2, 4, 5, 6, 8, 10, 12]
let arr2 = [1, 2, 3, 4, 5, 6]
let arr3 = [5, 6, 7, 8, 9, 10, 11, 12]
let arr4 = [1, 3, 4, 5, 6, 7, 9]
```
// (we did this one in class and this was the answer i first came to, i understand theres better ways to get there then this but this was the way i first thought to solve it)

let arr1 = [2, 4, 5, 6, 8, 10, 12]
let arr2 = [1, 2, 3, 4, 5, 6]
let arr3 = [5, 6, 7, 8, 9, 10, 11, 12]
let arr4 = [1, 3, 4, 5, 6, 7, 9]

var set1 = Set(arr1)
var set2 = Set(arr2)
var set3 = Set(arr3)
var set4 = Set(arr4)

let setUnion = set1.union(set2)
let secondUnion = setUnion.union(set3)
let thirdUnion = secondUnion.union(set4)

var finalArray = Array(thirdUnion)

finalArray = finalArray.sorted()

print(finalArray)





## Question 5

Perform the following set operations on the lists below:

1. Find the intersection and print the result
2. Find the symmetric difference and print the result
3. Find the union and print the result
4. What is the outcome of subtracting `list2` from `list1`? Print the result

```swift
let list1: Set = [1, 3, 4, 6, 2, 7, 9]
let list2: Set = [3, 7, 13, 10, 4]
```

let list1: Set = [1, 3, 4, 6, 2, 7, 9]
let list2: Set = [3, 7, 13, 10, 4]

let intersect = list1.intersection(list2)
print(intersect)

let symDiff = list1.symmetricDifference(list2)
print(symDiff)

let unity = list1.union(list2)
print(unity)

let subtracted = list1.subtracting(list2)
print(subtracted)





## Question 6

What output will be produced by the code below? Select one answer.

```swift
var spaceships = Set()

spaceships.insert("Serenity")
spaceships.insert("Enterprise")
spaceships.insert("TARDIS")
spaceships.insert("Serenity")

print(spaceships.count)
```

- 3
- 4
- Nothing will be output
- 0
- This code will not compile
- 1
- This code will compile but crash



//  my original answer was 4 but then ran the code and realized the variable was never declared or initialized properly, and also that the last line  using.insert() is inserting a value that laready exist in the set and therefor will have no effect on the contents of the string.  if the point was to declare an empty set then the variable would have neeed to be declared as such:    var spaceships = Set<String>()    once this was done then the final print statment would have worked and would ahve returned the answer as the integer 3

//the code below has been corrected
var spaceships = Set<String>()

spaceships.insert("Serenity")
spaceships.insert("Enterprise")
spaceships.insert("TARDIS")
spaceships.insert("Serenity")

print(spaceships.count)


## Question 7

What output will be produced by the code below?

```swift
var spaceships1 = Set()

spaceships1.insert("Serenity")
spaceships1.insert("Enterprise")
spaceships1.insert("TARDIS")

let spaceships2 = spaceships1

if spaceships1.isSubset(of: spaceships2) {
  print("This is a subset")
} else {
  print("This is not a subset")
}
```

- This code will compile but crash
- "This is not a subset"
- This code will not compile
- "This is a subset"
- Nothing will be output



//Considering the above example and this example both use the name incorrect declaration of a variable as set this code will not compile.  Once this variable is properly declared as    var spaceships1 = Set<String>()  then the code will compile and since spaceships1 is identical to spaceship2 they are both subsets and supersets of each other.

//the code below has been corrected
var spaceships1 = Set<String>()

spaceships1.insert("Serenity")
spaceships1.insert("Enterprise")
spaceships1.insert("TARDIS")

let spaceships2 = spaceships1

if spaceships1.isSubset(of: spaceships2) {
print("This is a subset")
} else {
print("This is not a subset")
}
