
# 🐍 পাইথন OOP ক্র্যাশ কোর্স — বাংলায় (বিগিনার থেকে অ্যাডভান্সড)

---

## ✅ পর্ব ১: OOP মানে কী?

**OOP = Object Oriented Programming**  
অর্থাৎ — প্রোগ্রামিং কে **বাস্তব জগতের মতো** করে গড়ে তোলা।  
এখানে সবকিছু **অবজেক্ট (বস্তু)** হিসেবে চিন্তা করা হয়।

প্রতিটি অবজেক্টের থাকে:
- **প্রোপার্টি / অ্যাট্রিবিউট** → যেমন: নাম, রং, সাইজ
- **মেথড / ফাংশন** → যেমন: হাঁটা, কথা বলা, গণনা করা

> 🎯 উদাহরণ: “কুকুর” একটি অবজেক্ট — তার নাম, বয়স (অ্যাট্রিবিউট), আর সে ডাকতে পারে “ভউ ভউ” (মেথড)

---

## ✅ পর্ব ২: OOP-এর ৪টি মূল নীতি (The 4 Pillars)

### ১. 🧱 ক্লাস এবং অবজেক্ট

- **ক্লাস (Class)** = ব্লুপ্রিন্ট / টেমপ্লেট (যেমন: “কুকুর” ক্লাস)
- **অবজেক্ট (Object)** = ক্লাস থেকে তৈরি বাস্তব জিনিস (যেমন: “টমি” নামের কুকুর)

```python
class Dog:
    def __init__(self, name, breed):
        self.name = name      # অ্যাট্রিবিউট
        self.breed = breed

    def bark(self):           # মেথড
        print(f"{self.name} বলছে: ভউ ভউ!")

# অবজেক্ট তৈরি
my_dog = Dog("টমি", "জার্মান শেফার্ড")
my_dog.bark()  # আউটপুট: টমি বলছে: ভউ ভউ!
```

> `__init__` হলো **কনস্ট্রাক্টর** — অবজেক্ট তৈরি হওয়ার সময় অটো কল হয়।

---

### ২. 🧬 এনক্যাপসুলেশন (Encapsulation)

> ডাটা এবং ফাংশনকে একসাথে বাঁধা + বাইরে থেকে সরাসরি এক্সেস না দেওয়া।

```python
class BankAccount:
    def __init__(self, balance):
        self.__balance = balance  # প্রাইভেট — বাইরে থেকে এক্সেস নাই

    def deposit(self, amount):
        if amount > 0:
            self.__balance += amount

    def get_balance(self):
        return self.__balance

acc = BankAccount(1000)
acc.deposit(500)
print(acc.get_balance())  # 1500
# print(acc.__balance) → এরর! কারণ প্রাইভেট
```

> `__` (double underscore) দিলে পাইথন অটো লক করে দেয় — একে বলে **name mangling**।

---

### ৩. 🧬 ইনহেরিটেন্স (Inheritance)

> একটা ক্লাস অন্য ক্লাসের প্রোপার্টি/মেথড ইনহেরিট করতে পারে।

```python
class Animal:
    def __init__(self, name):
        self.name = name

    def speak(self):
        pass  # পরে চাইল্ড ক্লাসে ডিফাইন করব

class Cat(Animal):
    def speak(self):
        return f"{self.name} বলছে: ম্যাও ম্যাও!"

class Dog(Animal):
    def speak(self):
        return f"{self.name} বলছে: ভউ ভউ!"

cat = Cat("মিউ")
dog = Dog("টমি")
print(cat.speak())  # মিউ বলছে: ম্যাও ম্যাও!
print(dog.speak())  # টমি বলছে: ভউ ভউ!
```

> `Cat` এবং `Dog`, `Animal` ক্লাস থেকে ইনহেরিট করেছে।

---

### ৪. 🔁 পলিমরফিজম (Polymorphism)

> একই মেথড নাম — কিন্তু আলাদা আলাদা ক্লাসে আলাদা আচরণ।

```python
def animal_sound(animal):
    print(animal.speak())

animal_sound(cat)  # মিউ বলছে: ম্যাও ম্যাও!
animal_sound(dog)  # টমি বলছে: ভউ ভউ!
```

> একে বলে **“duck typing”** — যদি কোনো জিনিস হাঁটে আর ডাকে হাঁসের মতো, তাহলে সে হাঁস!

---

## ✅ পর্ব ৩: ইন্টারমিডিয়েট কনসেপ্ট

### ✳️ ক্লাস ভেরিয়েবল vs ইন্সট্যান্স ভেরিয়েবল

```python
class Dog:
    species = "Canis familiaris"  # ক্লাস ভেরিয়েবল — সব কুকুরের জন্য একই

    def __init__(self, name):
        self.name = name          # ইন্সট্যান্স ভেরিয়েবল — আলাদা

d1 = Dog("টমি")
d2 = Dog("মিনি")
print(d1.species)  # Canis familiaris
print(d2.species)  # Canis familiaris
```

---

### ✳️ স্ট্যাটিক এবং ক্লাস মেথড

```python
class MathUtils:
    @staticmethod
    def add(a, b):
        return a + b

    @classmethod
    def what_am_i(cls):
        return f"আমি {cls.__name__} ক্লাস!"

print(MathUtils.add(5, 3))          # 8
print(MathUtils.what_am_i())        # আমি MathUtils ক্লাস!
```

> `@staticmethod`: `self` বা `cls` লাগে না → ইউটিলিটি ফাংশন  
> `@classmethod`: `cls` পায় → ক্লাস সম্পর্কিত কাজে লাগে

---

### ✳️ প্রোপার্টি (Getter/Setter)

```python
class Temperature:
    def __init__(self, celsius):
        self._celsius = celsius

    @property
    def celsius(self):
        return self._celsius

    @celsius.setter
    def celsius(self, value):
        if value < -273.15:
            raise ValueError("অতি ঠান্ডা!")
        self._celsius = value

temp = Temperature(25)
print(temp.celsius)   # 25
temp.celsius = 30     # OK
# temp.celsius = -300 → ValueError!
```

> প্রোপার্টি ব্যবহার করে আপনি ভ্যালিডেশন, লগিং ইত্যাদি করতে পারেন।

---

## ✅ পর্ব ৪: অ্যাডভান্সড কনসেপ্ট

### 🔄 ম্যাজিক মেথড (Dunder Methods)

অবজেক্টের আচরণ কাস্টমাইজ করতে ব্যবহার করা হয়।

```python
class Vector:
    def __init__(self, x, y):
        self.x = x
        self.y = y

    def __add__(self, other):
        return Vector(self.x + other.x, self.y + other.y)

    def __str__(self):
        return f"ভেক্টর({self.x}, {self.y})"

v1 = Vector(2, 3)
v2 = Vector(4, 5)
v3 = v1 + v2
print(v3)  # ভেক্টর(6, 8)
```

> জনপ্রিয় ম্যাজিক মেথড: `__str__`, `__repr__`, `__len__`, `__eq__`, `__lt__`

---

### 🔄 মাল্টিপল ইনহেরিটেন্স

```python
class Flyer:
    def fly(self):
        return "উড়ছি আকাশে!"

class Swimmer:
    def swim(self):
        return "সাঁতার কাটছি!"

class Duck(Flyer, Swimmer):
    pass

duck = Duck()
print(duck.fly())   # উড়ছি আকাশে!
print(duck.swim())  # সাঁতার কাটছি!
```

> ⚠️ MRO (Method Resolution Order) মনে রাখুন — `ClassName.__mro__` দিয়ে চেক করুন।

---

### 🔄 অ্যাবস্ট্রাক্ট ক্লাস (ABC)

```python
from abc import ABC, abstractmethod

class Shape(ABC):
    @abstractmethod
    def area(self):
        pass

class Circle(Shape):
    def __init__(self, radius):
        self.radius = radius

    def area(self):
        return 3.14 * self.radius ** 2

# s = Shape() → TypeError! অ্যাবস্ট্রাক্ট ক্লাস ইন্সট্যান্স করা যায় না
c = Circle(5)
print(c.area())  # 78.5
```

> অ্যাবস্ট্রাক্ট ক্লাস দিয়ে ফোর্স করুন যে সাবক্লাসগুলো নির্দিষ্ট মেথড ইমপ্লিমেন্ট করবে।

---

### 🔄 কম্পোজিশন (Composition)

> “has-a” রিলেশনশিপ — ইনহেরিটেন্সের চেয়ে বেশি ফ্লেক্সিবল।

```python
class Engine:
    def start(self):
        return "ইঞ্জিন চালু হয়েছে।"

class Car:
    def __init__(self):
        self.engine = Engine()  # Car "has-a" Engine

    def start(self):
        return self.engine.start()

car = Car()
print(car.start())  # ইঞ্জিন চালু হয়েছে।
```

---

## ✅ পর্ব ৫: বেস্ট প্র্যাকটিস

✅ ক্লাসের নাম PascalCase-এ লিখুন (যেমন: `BankAccount`)  
✅ প্রতিটি ক্লাস একটি জিনিসের দায়িত্ব নেবে (Single Responsibility)  
✅ গভীর ইনহেরিটেন্সের চেয়ে কম্পোজিশন ব্যবহার করুন  
✅ `@property` ব্যবহার করে অ্যাট্রিবিউট এক্সেস কন্ট্রোল করুন  
✅ `__slots__` ব্যবহার করে মেমরি অপ্টিমাইজ করুন (অ্যাডভান্সড)  
✅ ইউনিট টেস্ট লিখুন!

---

## ✅ বোনাস: কুইক রেফারেন্স (Quick Reference)

| কনসেপ্ট             | উদাহরণ / সিনট্যাক্স              |
|---------------------|----------------------------------|
| ক্লাস                | `class MyClass:`                 |
| কনস্ট্রাক্টর        | `def __init__(self):`            |
| ইন্সট্যান্স মেথড    | `def method(self):`              |
| ক্লাস মেথড          | `@classmethod def m(cls):`       |
| স্ট্যাটিক মেথড      | `@staticmethod def m():`         |
| প্রোপার্টি           | `@property` + `@x.setter`        |
| ইনহেরিটেন্স         | `class Child(Parent):`           |
| ম্যাজিক মেথড        | `__str__`, `__add__`, `__len__`  |

---
