# Enumerations lab

Fork and clone this repo. On your fork, answer and commit the follow questions. When you are finished, submit the link to your repo on Canvas.


## Question 1√

a) Define an enumeration called `iOSDeviceType` with member values `iPhone`, `iPad`, `iWatch`. Create a variable called `myDevice` and assign it one member value.

```swift
enum iOSDeviceType {
case iPhone 
case iPad
case iWatch
}

var myDevice =  iOSDeviceType.iPhone
print(myDevice)
```

b) Adjust your code above so that `iPhone` and `iPad` have associated values of type String which represents the model number, eg: `iPhone("6 Plus")`. Use a switch case and let syntax to print out the model number of each device.

```swift
if let devices = IOSDeviceType(rawValue: "6 Plus") {
switch devices {
case .iPhone:
print(devices.rawValue)
case .iPad:
print(devices.rawValue)
case .iWatch:
print(devices.rawValue)
}
}else {
print("Sorry not a real value")
}
```
## Question 2√

a) Write an enum called `Shape` and give it cases for `triangle`, `rectangle`, `square`, `pentagon`, and `hexagon`.

```swift
enum Shape: {
case triangle 
case rectangle 
case square 
case pentagon 
case hexagon 
}
```

b) Write a method inside `Shape` that returns how many sides the shape has. Create a variable called `myFavoritePolygon` and assign it to one of the shapes above, then print out how many sides it has.
```swift
enum Shape {
case triangle(Int)
case rectangle(Int)
case square (Int)
case pentagon(Int)
case hexagon(Int)


func howManysides() {
switch self {
case .triangle(let amountOfSides):
print("Triangles have \(amountOfSides) sides")
case .square(let amountOfSides):
print("Square have \(amountOfSides) sides")
case .rectangle(let amountOfSides):
print("Rectangle have \(amountOfSides) sides")
case .pentagon(let amountOfSides):
print("Pentagon have \(amountOfSides) sides")
case .hexagon(let amountOfSides):
print("Hexagon have \(amountOfSides) sides")
}
}
}

let myFavoritePolygon = Shape.triangle(3)
myFavoritePolygon.howManysides()
```
c) Re-write `Shape` so that each case has an associated value of type Int that will represent the length of the sides (assume the shapes are regular polygons so all the sides are the same length) and write a method inside that returns the perimeter of the shape.

```swift
enum Shape {
case triangle(Int)
case rectangle(Int)
case square (Int)
case pentagon(Int)
case hexagon(Int)


func howManysides() -> Int {
switch self {
case .triangle(let length):
return (3 * length)
case .square(let length):
return (4 * length)
case .rectangle(let length):
return (4 * length)
case .pentagon(let length):
return (5 * length)
case .hexagon(let length):
return (6 * length)
}
}
}

let myFavoritePolygon = Shape.triangle(3)
myFavoritePolygon.howManysides()
```

## Question 3√

Write an enum called `OperatingSystem` and give it cases for `windows`, `mac`, and `linux`. Create an array of 10 `OperatingSystem` objects where each one is set to a random operating system. Then, iterate through the array and print out a message depending on the operating system.

```swift

enum OperatingSystem {
case window
case mac
case linux
}

var arrayOfOperatingSystem: [OperatingSystem] = [.linux,.mac,.window,.mac,.window,.linux,.mac,.window,.linux,.linux]

for system in arrayOfOperatingSystem {
switch system {
case .linux:
print("The \(system) system is preferred for coding Java")
case .mac:
print("The \(system) system is preferred for coding Swift")
case .window:
print("The \(system) system is preferred for coding JavaScript")
}
}
```
```swift
enum OperatingSystem: String {
case window = "system is preferred for coding JavaScript"
case mac = "system is preferred for coding Swift"
case linux = "system is preferred for coding Java"
}

var arrayOfOperatingSystem: [OperatingSystem] = [.linux,.mac,.window,.mac,.window,.linux,.mac,.window,.linux,.linux]

for system in arrayOfOperatingSystem {
switch system {
case .linux:
print(OperatingSystem.linux.rawValue)
case .mac:
print(OperatingSystem.mac.rawValue)
case .window:
print(OperatingSystem.window.rawValue)
}
}
// credit to Ian.
```


## Question 4√

You are working on a game in which your character is exploring a grid-like map. You get the original location of the character and the steps he will take.

- A step .up will increase the y coordinate by 1.
- A step .down will decrease the y coordinate by 1.
- A step .right will increase the x coordinate by 1.
- A step .left will decrease the x coordinate by 1.
- Print the final location of the character after all the steps have been taken.

```swift
enum Direction {
    case up
    case down
    case left
    case right
}

var location = (x: 0, y: 0)
var steps: [Direction] = [.up, .up, .left, .down, .left]

// your code here
```
```swift
enum Direction {
case up
case down
case left
case right
}

var location = (x: 0, y: 0)
var steps: [Direction] = [.up, .up, .left, .down, .left]

for direction in steps {
switch direction {
case .up:
location.y += 1
case .down:
location.y -= 1
case .left:
location.x -= 1
case .right:
location.x += 1
}
}

print("final location for x: \(location.x) and y: \(location.y)")

```

## Question 5√

a) Define an enumeration named `HandShape` with three members: `.rock`, `.paper`, `.scissors`.

b) Define an enumeration named `MatchResult` with three members: `.win`, `.draw`, `.lose`.

c) Write a function called `match` that takes two `HandShapes` and returns a `MatchResult`. It should return the outcome for the first player (the one with the first hand shape).

Hint: Rock beats scissors, paper beats rock, scissor beats paper

```swift
enum handShape {
case rock
case paper
case scissors
}

enum MatchResult {
case win
case draw
case lose
}

func match (firstHand:handShape, secondHand:handShape) -> MatchResult {
switch firstHand {
case .rock:
switch secondHand {
case .rock: return .draw
case .paper: return .lose
case .scissors: return .win
}
case .paper:
switch secondHand {
case .paper: return .draw
case .rock: return .win
case .scissors: return .lose
}
case .scissors:
switch secondHand {
case .scissors: return .draw
case .paper: return .win
case .rock: return . win

}
}
}
```


## Question 6

a) You are given a `CoinType` enumeration which describes different coin values. Print the total value of the coins in the array `moneyArray` which contains tuples of type (`quantity`, `CoinType`).

```swift
enum CoinType: Int {
    case penny = 1
    case nickle = 5
    case dime = 10
    case quarter = 25
}

var moneyArray:[(Int,CoinType)] = [(10,.penny),
                                   (15,.nickle),
                                   (3,.quarter),
                                   (20,.penny),
                                   (3,.dime),
                                   (7,.quarter)]

// your code here
```

```swift
var result = Int()

for value in moneyArray {
result += value.0 * value.1.rawValue
}
print(result)
```

b) Write a method in the `CoinType` enum that returns an Int representing how many coins of that type you need to have a dollar. Then, create an instance of `CoinType` set to `.nickle` and use your method to print out how many nickels you need to have to make a dollar.

```swift
var oneDollar = 100

enum CoinType: Int {
case penny = 1
case nickle = 5
case dime = 10
case quarter = 25

func dollar ()-> Int {

switch self {
case .penny:
return oneDollar / CoinType.penny.rawValue
case .nickle:
return oneDollar / CoinType.nickle.rawValue
case .dime:
return oneDollar / CoinType.dime.rawValue
case .quarter:
return oneDollar / CoinType.quarter.rawValue
}
}
}

print(CoinType.nickle.dollar())
```


## Question 7

a) Write an enum called `DayOfWeek` to represent the days of the week with a raw value of type String.

```swift
enum DayOfWeek {
case sunday (String)
case monday (String)
case tueday (String)
case wednesday (String)
case thursday (String)
case friday (String)
case saturday (String)
}
```
b) Given the array `poorlyFormattedDays`, write code that will produce an array of enums that match the days.

```swift
enum DayOfWeek: String {
case sunday = "sunday"
case monday = "monday"
case tueday = "tueday"
case wednesday = "wednesday"
case thursday = "thurdaday"
case friday = "friday"
case saturday = "saturday"

func daysOfTheWeek () -> [String] {
var resultOfTheDays = [String]()
for days in poorlyFormattedDays {
switch self {
case .sunday:
if days.lowercased() == DayOfWeek.sunday.rawValue {
resultOfTheDays += [days]
}
case .monday:
if days.lowercased() == DayOfWeek.monday.rawValue {
resultOfTheDays += [days]
}
case .tueday:
if days.lowercased() == DayOfWeek.tueday.rawValue {
resultOfTheDays += [days]
}
case .wednesday:
if days.lowercased() == DayOfWeek.wednesday.rawValue {
resultOfTheDays += [days]
}
case .thursday:
if days.lowercased() == DayOfWeek.thursday.rawValue {
resultOfTheDays += [days]
}
case .friday:
if days.lowercased() == DayOfWeek.friday.rawValue {
resultOfTheDays += [days]
}
case .saturday:
if days.lowercased() == DayOfWeek.saturday.rawValue {
resultOfTheDays += [days]
}
}
}
return resultOfTheDays
}
}

print(DayOfWeek.monday.daysOfTheWeek())
```
`let poorlyFormattedDays = ["MONDAY", "wednesday", "Sunday", "monday", "Tuesday", "WEDNESDAY", "thursday", "SATURDAY", "tuesday", "FRIDAy", "Wednesday", "Monday", "Friday", "sunday"]`

c) Write a method in `DayOfWeek` called `isWeekend` that determines whether a day is part of the weekend or not and write code to calculate how many week days appear in `poorlyFormattedDays`.

```swift
enum DayOfWeek: String {
case sunday = "sunday"
case monday = "monday"
case tueday = "tueday"
case wednesday = "wednesday"
case thursday = "thurdaday"
case friday = "friday"
case saturday = "saturday"


func isWeekend () -> Int {
var dayCounts = [String]()
for day in poorlyFormattedDays{
switch self{
case .monday, .tueday, .wednesday, .thursday, .friday:
if day.lowercased() == DayOfWeek.monday.rawValue || day.lowercased() == DayOfWeek.tueday.rawValue || day.lowercased() == DayOfWeek.wednesday.rawValue || day.lowercased() == DayOfWeek.thursday.rawValue || day.lowercased() == DayOfWeek.friday.rawValue {
dayCounts += [day]
}
case . sunday, .saturday:
if day.lowercased() == DayOfWeek.sunday.rawValue || day.lowercased() == DayOfWeek.saturday.rawValue{
dayCounts += [day]
}
}
}
return dayCounts.count
}
}
DayOfWeek.saturday.isWeekend()
```
## Question 8

a) Create an enum called `MetroLine` with cases for the colors of the metro train lines. Create an instance of `MetroLine`.

b) Modify your enum so that each case has an associated value of either Character or Int that will represent the train on that line. Create a new instance of `MetroLine` and give it an appropriate train letter or number.

c) Write code that prints the train letter or number of your instance of `MetroLine`.

```swift
enum MetroLine {
case Green (Int, Int, Int)
case Red (Int, Int, Int)
case Blue (Character, Character, Character)
}
var greenLines = MetroLine.Green(4,5,6)
var redLines = MetroLine.Red(1,2,3)
var blueLines = MetroLine.Blue("a","c","e")

var myLine = redLines

switch myLine {
case .Green(let green1, let green2, let green3):
print("green lines are: \(green1), \(green2), \(green3)")
case .Red(let red1, let red2, let red3):
print("red lines are: \(red1), \(red2), \(red3)")
case .Blue(let blue1, let blue2, let blue3):
print("blue lines are: \(blue1), \(blue2), \(blue3)")
}
```
## Question 9

a) Think of your own example of something that can be modeled as an enum and write it. Remember that enums allow you to create instances of a defined list of cases.

b) Add a method to your enum.... try to have the method make sense.
