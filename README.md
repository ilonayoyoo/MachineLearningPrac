
{
 "cells": [
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "# **OOPs Concepts:**"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "> **1. Data Abstraction:**\n",
    "\n",
    "* Hide internal details and show functionalities only.\n",
    "* Abstraction can be achieved by using abstract classes and interfaces."
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "> **2. Encapsulation:**\n",
    "\n",
    "* Used to restrict access to methods and variables.\n",
    "* Code and data are wrapped together within a single unit, to prevent from being modified accidently."
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "> **3. Inheritance:**\n",
    "* Inheritance is the capability of one class to derive or inherit the properties from another class.\n",
    "* The class that derives properties is called the derived class or child class and the class from which the properties are being derived is called the base class or parent class.\n",
    "* Types of Inheritance:\n",
    "  * Single Inheritance\n",
    "  * Multilevel Inheritance\n",
    "  * Hierarchical Inheritance\n",
    "  * Multiple Inheritance\n",
    "  * Hybrid Inheritance"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "> **4. Polymorphism:**\n",
    "\n",
    "* Polymorphism simply means having many forms.\n",
    "* Means, declaring methods with same name, but performing different actions."
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "# **1. Abstraction:**"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 6,
   "metadata": {},
   "outputs": [
    {
     "name": "stdout",
     "output_type": "stream",
     "text": [
      "Length: 10 Breadth: 20\n",
      "Perimeter 60\n",
      "Area 200\n",
      "Side: 20\n",
      "Perimeter 80\n",
      "Area 400\n"
     ]
    },
    {
     "ename": "TypeError",
     "evalue": "Can't instantiate abstract class Shape with abstract methods area, perimeter, sides",
     "output_type": "error",
     "traceback": [
      "\u001b[1;31m---------------------------------------------------------------------------\u001b[0m",
      "\u001b[1;31mTypeError\u001b[0m                                 Traceback (most recent call last)",
      "Cell \u001b[1;32mIn[6], line 51\u001b[0m\n\u001b[0;32m     48\u001b[0m \u001b[39mprint\u001b[39m(\u001b[39m'\u001b[39m\u001b[39mPerimeter\u001b[39m\u001b[39m'\u001b[39m, s\u001b[39m.\u001b[39mperimeter())\n\u001b[0;32m     49\u001b[0m \u001b[39mprint\u001b[39m(\u001b[39m'\u001b[39m\u001b[39mArea\u001b[39m\u001b[39m'\u001b[39m, s\u001b[39m.\u001b[39marea())\n\u001b[1;32m---> 51\u001b[0m shape \u001b[39m=\u001b[39m Shape()\n\u001b[0;32m     52\u001b[0m \u001b[39mprint\u001b[39m(shape)\n",
      "\u001b[1;31mTypeError\u001b[0m: Can't instantiate abstract class Shape with abstract methods area, perimeter, sides"
     ]
    }
   ],
   "source": [
    "from abc import ABC, abstractmethod\n",
    "\n",
    "class Shape(ABC):\n",
    "    def __init__(self) -> None:\n",
    "        pass\n",
    "    @abstractmethod\n",
    "    def sides(self):\n",
    "        pass\n",
    "    @abstractmethod\n",
    "    def area(self):\n",
    "        pass\n",
    "    @abstractmethod\n",
    "    def perimeter(self):\n",
    "        pass\n",
    "\n",
    "class Rectangle(Shape):\n",
    "    def __init__(self, l: float, b: float) -> None:\n",
    "        super().__init__()\n",
    "        self.l = l\n",
    "        self.b = b\n",
    "    def sides(self):\n",
    "        super().sides()\n",
    "        print('Length:',self.l,'Breadth:',self.b)\n",
    "    def area(self):\n",
    "        return self.l*self.b\n",
    "    def perimeter(self):\n",
    "        return 2*(self.l+self.b)\n",
    "\n",
    "class Square(Shape):\n",
    "    def __init__(self, s: float) -> None:\n",
    "        super().__init__()\n",
    "        self.s = s\n",
    "    def sides(self):\n",
    "        super().sides()\n",
    "        print('Side:',self.s)\n",
    "    def area(self):\n",
    "        return self.s**2\n",
    "    def perimeter(self):\n",
    "        return 4*self.s\n",
    "\n",
    "r = Rectangle(10, 20)\n",
    "r.sides()\n",
    "print('Perimeter', r.perimeter())\n",
    "print('Area', r.area())\n",
    "\n",
    "s = Square(20)\n",
    "s.sides()\n",
    "print('Perimeter', s.perimeter())\n",
    "print('Area', s.area())\n",
    "\n",
    "shape = Shape()\n",
    "# TypeError: Can't instantiate abstract class Shape with abstract methods area, perimeter, sides"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "> **abstractproperty**"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 21,
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/plain": [
       "'Base class'"
      ]
     },
     "execution_count": 21,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "from abc import ABC, abstractmethod, abstractproperty\n",
    "\n",
    "class Base(ABC):\n",
    "    def __init__(self) -> None:\n",
    "        super().__init__()\n",
    "    @abstractproperty\n",
    "    def wish(self) -> str:\n",
    "        return 'Base class'\n",
    "\n",
    "class Derived(Base):\n",
    "    def __init__(self) -> None:\n",
    "        super().__init__()\n",
    "    @property\n",
    "    def wish(self) -> str:\n",
    "        return super().wish\n",
    "\n",
    "d = Derived()\n",
    "d.wish\n",
    "\n",
    "# b = Base()\n",
    "# b.wish"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "# **2. Encapsulation:**"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 15,
   "metadata": {},
   "outputs": [
    {
     "name": "stdout",
     "output_type": "stream",
     "text": [
      "{'pub': 10, '_prot': 20, '_Base__pvt': 30}\n",
      "10\n",
      "20\n",
      "10\n",
      "20\n",
      "30\n",
      "30\n"
     ]
    }
   ],
   "source": [
    "class Base:\n",
    "    # public data member\n",
    "    pub = 0\n",
    "    # protected data member\n",
    "    _prot = 0\n",
    "    # private data member\n",
    "    __pvt = 0\n",
    "    def __init__(self, pub: int, prot: int, pvt: int) -> None:\n",
    "        self.pub = pub\n",
    "        self._prot = prot\n",
    "        self.__pvt = pvt\n",
    "    def pub_method(self) -> int:\n",
    "        return self.pub\n",
    "    def _prot_method(self) -> int:\n",
    "        return self._prot\n",
    "    def __pvt_method(self) -> int:\n",
    "        return self.__pvt\n",
    "    def method(self):\n",
    "        print(self.__pvt)\n",
    "        print(self.__pvt_method())\n",
    "\n",
    "b = Base(10, 20, 30)\n",
    "print(b.__getstate__())\n",
    "print(b.pub)\n",
    "print(b._prot)\n",
    "# print(b.__pvt)\n",
    "# AttributeError: 'Base' object has no attribute '__pvt'\n",
    "\n",
    "print(b.pub_method())\n",
    "print(b._prot_method())\n",
    "# print(b.__pvt_method())\n",
    "# AttributeError: 'Base' object has no attribute '__pvt_method'\n",
    "\n",
    "# Can access the private methods and attributes from public methods\n",
    "# inside the class\n",
    "b.method()"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "# **3. Inheritance:**"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "> **Simple Inheritance Example:**"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 22,
   "metadata": {},
   "outputs": [
    {
     "name": "stdout",
     "output_type": "stream",
     "text": [
      "Person called..\n",
      "Person 1 Snehal\n",
      "Person called..\n",
      "Teacher called..\n",
      "Teacher 21 Shiv 45000.5\n",
      "{'id': 21, 'name': 'Shiv', 'salary': 45000.5}\n",
      "Person called..\n",
      "Student called..\n",
      "Person 11 Shubh\n",
      "{'id': 11, 'name': 'Shubh', 'marks': 89.6}\n"
     ]
    }
   ],
   "source": [
    "# Create the class Person and then inherit to Teacher and Student\n",
    "\n",
    "# Parent Class\n",
    "class Person:\n",
    "    def __init__(self, id:int, name:str) -> None:\n",
    "        self.id = id\n",
    "        self.name = name\n",
    "        print('Person called..')\n",
    "    def display(self, name: str) -> None:\n",
    "        print('Person', self.id, self.name)\n",
    "    def state(self) -> None:\n",
    "        print(self.__getstate__())\n",
    "\n",
    "# Child1 Class\n",
    "class Teacher(Person):\n",
    "    # Have to take the params for parent class initialization\n",
    "    # Also take params for child class, if needed\n",
    "    def __init__(self, id: int, name: str, salary:float) -> None:\n",
    "        # Call Parent class Constructor\n",
    "        super().__init__(id, name)\n",
    "        self.salary = salary\n",
    "        print('Teacher called..')\n",
    "    # Method overridden from the parent\n",
    "    def display(self) -> None:\n",
    "        print('Teacher', self.id, self.name, self.salary)\n",
    "\n",
    "# Child2 Class\n",
    "class Student(Person):\n",
    "    def __init__(self, id: int, name: str, marks:float) -> None:\n",
    "        super().__init__(id, name)\n",
    "        self.marks = marks\n",
    "        print('Student called..')\n",
    "    # If overridden method not present, then call the method from parent class itself\n",
    "    # def display(self) -> None:\n",
    "    #     print('Student', self.id, self.name, self.marks)\n",
    "\n",
    "\n",
    "p1 = Person(1, 'Snehal')\n",
    "p1.display('snehal')\n",
    "\n",
    "t1 = Teacher(21, 'Shiv', 45000.50)\n",
    "t1.display()\n",
    "t1.state()\n",
    "\n",
    "s1 = Student(11, 'Shubh', 89.60)\n",
    "s1.display('asdf')\n",
    "s1.state()\n"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "> **Types of Inheritance:**"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "> **1. Single Inheritance:**"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 1,
   "metadata": {},
   "outputs": [
    {
     "name": "stdout",
     "output_type": "stream",
     "text": [
      "Person called..\n",
      "1, Snehal\n",
      "{'id': 1, 'name': 'Snehal'}\n",
      "Person called..\n",
      "Student called..\n",
      "2, Shubh, 95.5\n",
      "{'id': 2, 'name': 'Shubh', 'marks': 95.5}\n"
     ]
    }
   ],
   "source": [
    "class Person:\n",
    "    def __init__(self, id:int, name:str) -> None:\n",
    "        self.id = id\n",
    "        self.name = name\n",
    "        print('Person called..')\n",
    "    def __str__(self) -> str:\n",
    "        return f'{self.id}, {self.name}'\n",
    "\n",
    "class Student(Person):\n",
    "    def __init__(self, id: int, name: str, marks: float) -> None:\n",
    "        super().__init__(id, name)\n",
    "        self.marks = marks\n",
    "        print('Student called..')\n",
    "    def __str__(self) -> str:\n",
    "        return f'{self.id}, {self.name}, {self.marks}'\n",
    "\n",
    "p = Person(1, 'Snehal')\n",
    "print(p)\n",
    "print(p.__getstate__())\n",
    "\n",
    "s = Student(2, 'Shubh', 95.50)\n",
    "print(s)\n",
    "print(s.__getstate__())"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "> **2. Multiple Inheritance:**"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 3,
   "metadata": {},
   "outputs": [
    {
     "name": "stdout",
     "output_type": "stream",
     "text": [
      "Father constructor..\n",
      "{'f_name': 'Sanjay'}\n",
      "Mother constructor..\n",
      "{'m_name': 'Savita'}\n",
      "Father constructor..\n",
      "Mother constructor..\n",
      "Child constructor..\n",
      "{'f_name': 'Sanjay', 'm_name': 'Savita', 'c_name': 'Snehal'}\n"
     ]
    }
   ],
   "source": [
    "# Create 2 base classes and inherit to one child class\n",
    "\n",
    "class Father:\n",
    "    def __init__(self, f_name:str) -> None:\n",
    "        self.f_name = f_name\n",
    "        print('Father constructor..')\n",
    "\n",
    "class Mother:\n",
    "    def __init__(self, m_name:str) -> None:\n",
    "        self.m_name = m_name\n",
    "        print('Mother constructor..')\n",
    "\n",
    "class Child(Father, Mother):\n",
    "    def __init__(self, f_name: str, m_name: str, c_name: str) -> None:\n",
    "        Father.__init__(self, f_name)\n",
    "        Mother.__init__(self, m_name)\n",
    "        self.c_name = c_name\n",
    "        print('Child constructor..')\n",
    "\n",
    "f = Father('Sanjay')\n",
    "print(f.__getstate__())\n",
    "\n",
    "m = Mother('Savita')\n",
    "print(m.__getstate__())\n",
    "\n",
    "c = Child('Sanjay', 'Savita', 'Snehal')\n",
    "print(c.__getstate__())"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "> **3. Multilevel Inheritance :**"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 4,
   "metadata": {},
   "outputs": [
    {
     "name": "stdout",
     "output_type": "stream",
     "text": [
      "Parent constructor..\n",
      "Child constructor..\n",
      "GrandChild constructor..\n",
      "Parent class name.. mankar\n",
      "Child class name.. sanjay\n",
      "GrandChild class name.. snehal\n",
      "Parent class name.. mankar\n"
     ]
    },
    {
     "data": {
      "text/plain": [
       "'mankar'"
      ]
     },
     "execution_count": 4,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "class Parent:\n",
    "    def __init__(self, p_name: str) -> None:\n",
    "        self.p_name = p_name\n",
    "        print('Parent constructor..')\n",
    "    def get_p_name(self) -> str:\n",
    "        print('Parent class name..', self.p_name)\n",
    "        return self.p_name\n",
    "    \n",
    "\n",
    "class Child(Parent):\n",
    "    def __init__(self, p_name: str, c_name) -> None:\n",
    "        super().__init__(p_name)\n",
    "        self.c_name = c_name\n",
    "        print('Child constructor..')\n",
    "    def get_c_name(self) -> str:\n",
    "        print('Child class name..', self.c_name)\n",
    "        return self.c_name\n",
    "\n",
    "\n",
    "class GrandChild(Child):\n",
    "    def __init__(self, p_name: str, c_name, g_name) -> None:\n",
    "        super().__init__(p_name, c_name)\n",
    "        self.g_name = g_name\n",
    "        print('GrandChild constructor..')\n",
    "    def get_g_name(self) -> str:\n",
    "        print('GrandChild class name..', self.g_name)\n",
    "        return self.g_name\n",
    "    def get(self) -> str:\n",
    "        return super().get_p_name()\n",
    "\n",
    "\n",
    "g = GrandChild('mankar', 'sanjay', 'snehal')\n",
    "g.get_p_name()\n",
    "g.get_c_name()\n",
    "g.get_g_name()\n",
    "g.get()"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "> **4. Hierarchical Inheritance:**"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 48,
   "metadata": {},
   "outputs": [
    {
     "name": "stdout",
     "output_type": "stream",
     "text": [
      "{'id': 1, 'name': 'Snehal', 'experience': 10}\n",
      "{'id': 2, 'name': 'Shubh', 'dept': 'CSE'}\n",
      "{'id': 3, 'name': 'Kal', 'marks': 89.48}\n",
      "{'id': 4, 'name': 'Shiv', 'salary': 67000}\n"
     ]
    }
   ],
   "source": [
    "# More than one derived class can be created from a single base.\n",
    "\n",
    "class Person:\n",
    "    def __init__(self, id: int, name: str) -> None:\n",
    "        self.id = id\n",
    "        self.name = name\n",
    "\n",
    "class Teacher(Person):\n",
    "    def __init__(self, id: int, name: str, salary: float) -> None:\n",
    "        super().__init__(id, name)\n",
    "        self.salary = salary\n",
    "\n",
    "class Student(Person):\n",
    "    def __init__(self, id: int, name: str, marks: float) -> None:\n",
    "        super().__init__(id, name)\n",
    "        self.marks = marks\n",
    "\n",
    "class Assistant(Person):\n",
    "    def __init__(self, id: int, name: str, dept: str) -> None:\n",
    "        super().__init__(id, name)\n",
    "        self.dept = dept\n",
    "\n",
    "class Principal(Person):\n",
    "    def __init__(self, id: int, name: str, exper: int) -> None:\n",
    "        super().__init__(id, name)\n",
    "        self.experience = exper\n",
    "\n",
    "p = Principal(1, 'Snehal', 10)\n",
    "print(p.__getstate__())\n",
    "\n",
    "a = Assistant(2, 'Shubh', 'CSE')\n",
    "print(a.__getstate__())\n",
    "\n",
    "s = Student(3, 'Kal', 89.48)\n",
    "print(s.__getstate__())\n",
    "\n",
    "t = Teacher(4, 'Shiv', 67000)\n",
    "print(t.__getstate__())"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "> **5. Hybrid Inheritance:**"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": null,
   "metadata": {},
   "outputs": [],
   "source": [
    "# This form combines more than one form of inheritance. \n",
    "# Basically, it is a blend of more than one type of inheritance.\n",
    "\n",
    "class Bank:\n",
    "    def __init__(self, bank_name: str, branch: str) -> None:\n",
    "        self.bank_name = bank_name\n",
    "        self.branch = branch\n",
    "\n",
    "class Account(Bank):\n",
    "    def __init__(self, bank_name: str, branch: str, id: int) -> None:\n",
    "        super().__init__(bank_name, branch)\n",
    "        self.id = id\n",
    "\n",
    "class Savings(Account):\n",
    "    def __init__(self, bank_name: str, branch: str, id: int, duration: int, money: float) -> None:\n",
    "        super().__init__(bank_name, branch, id)\n",
    "        self.duration = duration\n",
    "        self.money = money\n",
    "\n",
    "class Current(Account):\n",
    "    def __init__(self, bank_name: str, branch: str, id: int, balance: float) -> None:\n",
    "        super().__init__(bank_name, branch, id)\n",
    "        self.balance = balance\n",
    "\n",
    "class Person:\n",
    "    def __init__(self, name: str, addr: str) -> None:\n",
    "        self.name = name\n",
    "        self.addr = addr\n",
    "\n",
    "class Savings_Holder(Person, Savings):\n",
    "    def __init__(self, name: str, addr: str, bank_name: str, branch: str, id: int, duration: int, money: float) -> None:\n",
    "        Person.__init__(self, name, addr)\n",
    "        Savings.__init__(self, bank_name, branch, id, duration, money)\n",
    "\n",
    "class Current_Holder(Person, Current):\n",
    "    def __init__(self, name: str, addr: str, bank_name: str, branch: str, id: int, balance: float) -> None:\n",
    "        Person.__init__(self, name, addr)\n",
    "        Current.__init__(self, bank_name, branch, id, balance)\n",
    "\n",
    "\n"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "> **Private members of the class:**"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 5,
   "metadata": {},
   "outputs": [
    {
     "name": "stdout",
     "output_type": "stream",
     "text": [
      "{'id': 1, 'name': 'Snehal', '_Account__pwd': 'act_pwd'}\n",
      "1\n",
      "Snehal\n",
      "act_pwd\n",
      "account\n",
      "{'id': 1, 'name': 'Snehal', '_Account__pwd': 'sav_pwd'}\n",
      "1\n",
      "Snehal\n"
     ]
    },
    {
     "ename": "AttributeError",
     "evalue": "'Saving_Account' object has no attribute '_Saving_Account__pwd'",
     "output_type": "error",
     "traceback": [
      "\u001b[1;31m---------------------------------------------------------------------------\u001b[0m",
      "\u001b[1;31mAttributeError\u001b[0m                            Traceback (most recent call last)",
      "Cell \u001b[1;32mIn[5], line 36\u001b[0m\n\u001b[0;32m     33\u001b[0m \u001b[39mprint\u001b[39m(acct2\u001b[39m.\u001b[39mname)\n\u001b[0;32m     34\u001b[0m \u001b[39m# print(acct2.__pwd)\u001b[39;00m\n\u001b[0;32m     35\u001b[0m \u001b[39m# AttributeError: 'Saving_Account' object has no attribute '__pwd'\u001b[39;00m\n\u001b[1;32m---> 36\u001b[0m \u001b[39mprint\u001b[39m(acct2\u001b[39m.\u001b[39;49mget_pwd())\n\u001b[0;32m     37\u001b[0m acct2\u001b[39m.\u001b[39mset_pwd(\u001b[39m'\u001b[39m\u001b[39msaving\u001b[39m\u001b[39m'\u001b[39m)\n\u001b[0;32m     38\u001b[0m \u001b[39mprint\u001b[39m(acct2\u001b[39m.\u001b[39mget_pwd())\n",
      "Cell \u001b[1;32mIn[5], line 16\u001b[0m, in \u001b[0;36mSaving_Account.get_pwd\u001b[1;34m(self)\u001b[0m\n\u001b[0;32m     15\u001b[0m \u001b[39mdef\u001b[39;00m \u001b[39mget_pwd\u001b[39m(\u001b[39mself\u001b[39m) \u001b[39m-\u001b[39m\u001b[39m>\u001b[39m \u001b[39mstr\u001b[39m:\n\u001b[1;32m---> 16\u001b[0m     \u001b[39mreturn\u001b[39;00m \u001b[39mself\u001b[39;49m\u001b[39m.\u001b[39;49m__pwd\n",
      "\u001b[1;31mAttributeError\u001b[0m: 'Saving_Account' object has no attribute '_Saving_Account__pwd'"
     ]
    }
   ],
   "source": [
    "class Account:\n",
    "    def __init__(self, id: int, name: str, pwd: str) -> None:\n",
    "        self.id = id\n",
    "        self.name = name\n",
    "        self.__pwd = pwd\n",
    "    def get_pwd(self) -> str:\n",
    "        return self.__pwd\n",
    "    def set_pwd(self, pwd: str) -> None:\n",
    "        self.__pwd = pwd\n",
    "\n",
    "class Saving_Account(Account):\n",
    "    type = 'Saving'\n",
    "    def __init__(self, id: int, name: str, pwd: str) -> None:\n",
    "        super().__init__(id, name, pwd)\n",
    "    def get_pwd(self) -> str:\n",
    "        return self.__pwd\n",
    "\n",
    "\n",
    "acct = Account(1, 'Snehal', 'act_pwd')\n",
    "print(acct.__getstate__())\n",
    "print(acct.id)\n",
    "print(acct.name)\n",
    "# print(acct.__pwd)\n",
    "# AttributeError: 'Account' object has no attribute '__pwd'\n",
    "print(acct.get_pwd())\n",
    "acct.set_pwd('account')\n",
    "print(acct.get_pwd())\n",
    "\n",
    "\n",
    "acct2 = Saving_Account(1, 'Snehal', 'sav_pwd')\n",
    "print(acct2.__getstate__())\n",
    "print(acct2.id)\n",
    "print(acct2.name)\n",
    "# print(acct2.__pwd)\n",
    "# AttributeError: 'Saving_Account' object has no attribute '__pwd'\n",
    "print(acct2.get_pwd())\n",
    "acct2.set_pwd('saving')\n",
    "print(acct2.get_pwd())\n"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "# **4. Polymorphism:**"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 19,
   "metadata": {},
   "outputs": [
    {
     "name": "stdout",
     "output_type": "stream",
     "text": [
      "Birds can fly, but some cannot..\n",
      "Sparrow can fly..\n",
      "Birds can fly, but some cannot..\n",
      "Hii snehal Ostrich cannot fly..\n"
     ]
    }
   ],
   "source": [
    "class Bird:\n",
    "    def __init__(self, name: str) -> None:\n",
    "        self.name = name\n",
    "    def flight(self) -> None:\n",
    "        print('Birds can fly, but some cannot..')\n",
    "\n",
    "class Sparrow(Bird):\n",
    "    def __init__(self, name: str) -> None:\n",
    "        super().__init__(name)\n",
    "    def flight(self) -> None:\n",
    "        super().flight()\n",
    "        print(self.name, 'can fly..')\n",
    "\n",
    "class Ostrich(Bird):\n",
    "    def __init__(self, name: str) -> None:\n",
    "        super().__init__(name)\n",
    "    def flight(self) -> None:\n",
    "        super().flight()\n",
    "        print(self.name, 'cannot fly..')\n",
    "    def flight(self, name) -> None:\n",
    "        super().flight()\n",
    "        print('Hii', name, self.name, 'cannot fly..')\n",
    "\n",
    "s = Sparrow('Sparrow')\n",
    "s.flight()\n",
    "\n",
    "p = Ostrich('Ostrich')\n",
    "# p.flight()\n",
    "# TypeError: Ostrich.flight() missing 1 required positional argument: 'name'\n",
    "p.flight('snehal')"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "# **issubclass() and isinstance():**"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 12,
   "metadata": {},
   "outputs": [
    {
     "name": "stdout",
     "output_type": "stream",
     "text": [
      "False\n",
      "True\n",
      "True\n",
      "False\n"
     ]
    }
   ],
   "source": [
    "class A:\n",
    "    pass\n",
    "\n",
    "class B(A):\n",
    "    pass\n",
    "\n",
    "a= A()\n",
    "\n",
    "b = B()\n",
    "\n",
    "print(issubclass(A,B))\n",
    "print(issubclass(B,A))\n",
    "\n",
    "print(isinstance(a,A))\n",
    "print(isinstance(a,B))"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": null,
   "metadata": {},
   "outputs": [],
   "source": []
  }
 ],
 "metadata": {
  "kernelspec": {
   "display_name": "Python 3",
   "language": "python",
   "name": "python3"
  },
  "language_info": {
   "codemirror_mode": {
    "name": "ipython",
    "version": 3
   },
   "file_extension": ".py",
   "mimetype": "text/x-python",
   "name": "python",
   "nbconvert_exporter": "python",
   "pygments_lexer": "ipython3",
   "version": "3.11.3"
  },
  "orig_nbformat": 4
 },
 "nbformat": 4,
 "nbformat_minor": 2
}
