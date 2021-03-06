# 物件導向

1. 資料封裝(Encapsulation)

   簡單講，資料封裝就是將資料分成私用(Private)、保護(Protected)、公用(Public)等，實踐 Information hiding 概念, 避免程式各個物件互相干擾，降低程式的複雜度及維護上的困難度。 

2. 繼承(Inheritance)

   有繼承的關係後，父類別 (Super class) 中的資料 (Data) 或方法 (Method) 在次子類(Subclass)就可以繼承使用，次子類別的次子類別也可以繼承使用，最後即能達到資料重覆使用的目的。

3. 多型(Polymorphism)

   多型(Polymorphism) 代表能夠在執行階段，物件能夠依照不同情況變換資料型態，換句話說，多型是指一個物件參考可以在不同環境下，扮演不同角色的特性，指向不同的物件實體，可 透過實作多個繼承或介面來實現父類別，並使用Override或Overload來達成。
   
```
class Person
{
    private int year;

    public int Age
    {
        get { return 2015 - year; }
        set { year = 2015 - value;  }
    }

    // setter
    public void setYear(int year)
    {
        if (year < 2015)
        {
            this.year = year;
        }
    }
}

class Program
{
    static void Main(string[] args)
    {

        Person john = new Person();

        john.setYear(1988);

        Console.WriteLine(john.Age);

        john.Age = 35;

        Console.WriteLine(john.Age);

        Console.ReadKey();
    }
}
```



## 動物

```cs
abstract class Animal
{
    private string name;

    public Animal(string name)
    {
        this.name = name;
    }

    public void eat()
    {
        Console.WriteLine("{0} is eating.", name);
    }
}

interface IPet
{
    void play();
    void eat();
}

class Dog : Animal, IPet
{
    public Dog(string name) : base(name)
    {
    }

    void IPet.play()
    {
        Console.WriteLine("汪");
    }
}

class Cat : Animal, IPet
{
    public Cat(string name) : base(name)
    {
    }

    void IPet.play()
    {
        Console.WriteLine("喵");
    }
}

class Program
{
    static void Main(string[] args)
    {
        //Animal a = new Animal("????");

        List<IPet> list1 = new List<IPet>();

        Dog dog1 = new Dog("doggy");

        list1.Add(dog1);

        Cat cat1 = new Cat("kitty");

        list1.Add(cat1);

        foreach (IPet pet in list1)
        {
            pet.eat();
            pet.play();
        }

        Console.ReadKey();
    }
}
```