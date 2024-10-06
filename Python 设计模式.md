# 23 种设计模式介绍（Python 示例讲解）

链接：https://www.cnblogs.com/liugp/p/17134320.html

## 一、概述

> `设计模式（Design Pattern）`是一套被广泛接受的、可重复使用的软件设计**解决方案**。它们是在软件开发过程中对常见问题的反复实践和总结得出的经验和思想的表现。

1995 年，GoF（Gang of Four，四人组/四人帮）合作出版了《设计模式：可复用面向对象软件的基础》一书，共收录了 **23 种设计模式**，从此树立了软件设计模式领域的里程碑，人称「GoF设计模式」。

设计模式是一种解决特定问题的经过测试和验证的通用解决方案，它们被广泛应用于软件工程和计算机科学中。下面列出了常见的 **23 种设计模式**：

1. **工厂模式（Factory Pattern）**：定义一个创建对象的接口，让子类决定实例化哪一个类。工厂方法使一个类的实例化延迟到其子类。

2. **抽象工厂模式（Abstract Factory Pattern）**：提供一个创建一系列相关或相互依赖对象的接口，而无需指定它们的具体类。

3. **单例模式（Singleton Pattern）**：确保一个类只有一个实例，并提供对该实例的全局访问点。

4. **建造者模式（Builder Pattern）**：将一个复杂对象的构建与它的表示分离，使得同样的构建过程可以创建不同的表示。

5. **原型模式（Prototype Pattern）**：通过复制现有的实例来创建新的对象，而不是使用构造函数。

6. **适配器模式（Adapter Pattern）**：将一个类的接口转换成客户希望的另一个接口。适配器模式可以让原本由于接口不兼容而不能在一起工作的类可以一起工作。

7. **桥接模式（Bridge Pattern）**：将抽象部分与它的实现部分分离，使它们都可以独立地变化。

8. **组合模式（Composite Pattern）**：将对象组合成树形结构以表示部分-整体的层次结构。组合模式使得用户对单个对象和组合对象的使用具有一致性。

   > Q：将对象组织成树形结构，是否可以理解成 MongoDB 的那种嵌套结构呢？

9. **装饰器模式（Decorator Pattern）**：动态地将责任附加到对象上。装饰器模式提供了一种灵活的替代继承的方式。

10. **外观模式（Facade Pattern）**：为子系统中的一组接口提供一个一致的界面，使得子系统更容易使用。

11. **享元模式（Flyweight Pattern）**：运用共享技术来有效地支持大量细粒度对象的复用。

12. **代理模式（Proxy Pattern）**：为其他对象提供一种代理以控制对这个对象的访问。代理对象可以在被代理对象执行操作前后进行一些预处理和后处理。

13. **责任链模式（Chain of Responsibility Pattern）**：为解除请求的发送者和接收者之间耦合，而使多个对象都有机会处理这个请求。

14. **命令模式（Command Pattern）**：将请求封装成一个对象，从而使你可以用不同的请求对客户进行参数化。命令模式也支持撤销操作。

15. **解释器模式（Interpreter Pattern）**：是一种行为型设计模式，它提供了一种方法，可以在运行时解释语言文法中的表达式，并执行相应的操作。

16. **迭代器模式（Iterator Pattern）**：提供一种方法顺序访问一个聚合对象中的各个元素，而又不暴露该对象的内部表示。

17. **中介者模式（Mediator Pattern）**：用一个中介对象来封装一系列的对象交互。中介者使各个对象不需要显式地相互作用，从而使其耦合松散，而且可以独立地改变它们之间的交互。

18. **备忘录模式（Memento Pattern）**：在不破坏封装性的前提下，捕获一个对象的内部状态，并在该对象之外保存这个状态。备忘录模式可以在需要时将对象恢复到先前的状态。

19. **观察者模式（Observer Pattern）**：定义对象间的一种一对多的依赖关系，使得每当一个对象状态发生改变时，所有依赖它的对象都会得到通知并自动更新。

20. **状态模式（State Pattern）**：允许对象在其内部状态发生改变时改变它的行为。对象看起来似乎修改了它的类。

21. **策略模式（Strategy Pattern）**：定义一系列算法，将每个算法都封装起来，并使它们之间可以互换。策略模式使得算法可以独立于使用它的客户而变化。

22. **模板方法模式 (Template Method Pattern)**：定义一个算法框架，并将一些步骤延迟到子类中实现，以便在不改变算法结构的情况下，允许子类重定义算法的某些步骤。

23. **访问者模式（Visitor Pattern）**：是一种行为型设计模式，它可以让你在不修改对象结构的前提下，定义作用于这些对象元素的新操作。

这些设计模式可以被分为三个类别：

- **创建型模式**：这些模式涉及对象的创建机制，并提供了一种将对象的创建和使用分离的方式。工厂模式、抽象工厂模式、单例模式、建造者模式和原型模式都属于这一类别。
- **结构型模式**：这些模式涉及将类或对象组合在一起形成更大的结构，并提供了一种简化设计的方式。适配器模式、桥接模式、组合模式、装饰器模式、外观模式、享元模式和代理模式都属于这一类别。
- **行为型模式**：这些模式涉及对象之间的通信和算法的分配，并提供了一种实现松散耦合的方式。责任链模式、命令模式、解释器模式、迭代器模式、中介者模式、备忘录模式、观察者模式、状态模式、策略模式、模板方法模式和访问者模式都属于这一类别。

![image-20241006184957939](./Typora_Python 设计模式/assets/image-20241006184957939.png)

## 二、设计模式七种原则

![image-20241006185657074](./Typora_Python 设计模式/assets/image-20241006185657074.png)

设计模式的七种原则通常被称为“SOLID原则”，是面向对象设计中的基本原则，能够帮助开发人员编写出更加灵活、可扩展、可维护的代码。这七个原则分别是：

- **单一职责原则（Single Responsibility Principle，SRP）**：一个类只负责一个职责或一个功能。这个原则强调的是**高内聚、低耦合**，可以降低类的复杂度，提高代码的可读性、可维护性和可重用性。
- **开闭原则（Open-Closed Principle，OCP）**：一个类的行为应该是**可扩展**的，但是**不可修改**。这个原则强调的是代码的可维护性和可扩展性，通过抽象化来避免修改已有代码的风险，从而降低软件维护的成本。
- **里氏替换原则（Liskov Substitution Principle，LSP）**：子类应该可以替换其父类并且不会影响程序的正确性。这个原则强调的是**面向对象的继承和多态特性**，通过保证子类的行为和父类一致，从而提高代码的可维护性和可扩展性。
- **接口隔离原则（Interface Segregation Principle，ISP）**：一个类不应该依赖它不需要的接口，即一个类对其它类的依赖应该**建立在最小的接口**上。这个原则强调的是接口设计的合理性，避免不必要的接口导致类之间的耦合性过高，从而提高代码的灵活性和可维护性。
- **依赖倒置原则（Dependency Inversion Principle，DIP）**：依赖于抽象而不是依赖于具体实现。这个原则强调的是代码的可扩展性和可维护性，通过**抽象化来减少组件之间的耦合性**，从而使得代码更加灵活、易于维护和扩展。
- **迪米特法则（Law of Demeter，LoD）**：也叫最少知识原则（Least Knowledge Principle，LKP），一个对象应当对其他对象有尽可能少的了解，不需要了解的内容尽量不要去了解。这个原则强调的是组件之间的**松耦合**，通过**减少组件之间的依赖关系**，提高代码的可维护性和可重用性。
- **组合/聚合复用原则（Composite/Aggregate Reuse Principle，CARP）**：**尽量使用组合或聚合关系**，而不是继承关系来达到代码复用的目的。这个原则强调的是通过组合和聚合的方式来实现代码复用，避免继承带来的一些问题，如父类和子类之间的强耦合性，从而提高代码的灵活性和可维护性。



## 三、设计模式示例讲解

### 创建型模式

#### 工厂模式

简单工厂模式





工厂方法模式



#### 抽象工厂模式

#### 单例模式

#### 建造者模式

#### 原型模式



### 结构型模式

#### 适配器模式

#### 桥接模式

#### 组合模式

#### 装饰模式

#### 外观模式

#### 享元模式

> **享元模式**（`Flyweight`）是一种结构型设计模式，它**通过共享对象来尽可能减少内存使用和对象数量**。在享元模式中，存在两种对象：**内部状态**（`Intrinsic State`）和**外部状态**（`Extrinsic State`）。内部状态指对象的共享部分，不随环境改变而改变；外部状态指对象的非共享部分，会随环境改变而改变。

实现思路：

- 享元模式的核心思想是**尽量重用已经存在的对象**，减少对象的创建和销毁，从而提高性能和节省内存。
- 它通常适用于需要大量创建对象的场景，但又不能因为对象过多而导致内存不足或性能降低的情况。



下面是一个简单的享元模式的示例，假设我们有一个字符工厂，它可以创建不同的字符对象。在实现字符对象时，我们发现有一些字符会被频繁使用，而且它们的状态是不变的，例如空格、逗号、句号等标点符号。因此，我们可以将这些字符设计为享元对象，通过共享来节省内存。

```python
class CharacterFactory:
    def __init__(self):
        self.characters = {}

    def get_character(self, character):
        if character in self.characters:
            return self.characters[character]
        else:
            new_character = Character(character)
            self.characters[character] = new_character
            return new_character

class Character:
    def __init__(self, character):
        self.character = character

    def render(self, font):
        print(f"Rendering character {self.character} in font {font}")

# 创建字符工厂
factory = CharacterFactory()

# 获取不同的字符
char1 = factory.get_character("A")
char2 = factory.get_character("B")
char3 = factory.get_character(" ")
char4 = factory.get_character(",")
char5 = factory.get_character(" ")
char6 = factory.get_character(".")

# 渲染不同的字符
char1.render("Arial")
char2.render("Times New Roman")
char3.render("Arial")
char4.render("Times New Roman")
char5.render("Arial")
char6.render("Times New Roman")

```

代码讲解：

- 在上述示例中，我们创建了一个 CharacterFactory 类来管理字符对象。当客户端需要获取一个字符时，可以调用 get_character 方法。如果该字符已经被创建过了，就直接返回共享的对象；否则，创建一个新的对象并将其保存到工厂中，以备下次使用。
- 字符对象 Characte r有一个 render 方法，用于渲染该字符。在实际使用中，我们可能需要给不同的字符设置不同的字体，这里只是为了演示方便，用字符串代替了字体对象。
- 通过享元模式，我们可以共享多个相同的字符对象，从而减少内存使用和对象数量。在这个例子中，如果没有使用享元模式，我们可能需要创建多个空格、逗号和句号对象，而这些对象的状态都是不变的，这样就会导致内存浪费。通过使用享元模式，我们可以将这些相同的对象共享起来，避免重复创建对象，从而提高性能和节省内存。

> 需要注意的是，享元模式并不是万能的，它**适用于需要大量创建相同对象的场景**。如果对象的数量不大，或者对象状态变化频繁，那么使用享元模式可能会增加代码复杂度，而且也不一定能够带来性能提升。因此，在使用享元模式时需要仔细考虑是否适合当前场景。

**补充说明：**

【一言以蔽之】缓存机制，比如：字符串连接的时候，可以选择 `res=[] "\n".join(res)`的方式实现。



#### 代理模式



### 行为型模式

#### 责任链模式

#### 命令模式

#### ==解释器模式==

> **解释器模式**（Interpreter Pattern）是一种行为型设计模式，它**定义了一种语言文法**，以及一个解释器，用于解释该语言中的句子。解释器模式通常用于解决特定类型的问题，例如解释计算器表达式，SQL 查询语句等。

解释器模式包括三个核心角色：

- **Context（上下文）**：它是解释器的运行环境。它存储解释器所需的一些全局信息。
- **Abstract Expression（抽象表达式）**：它是定义所有表达式的接口，通常包含解释方法 interpret()。
- **Concrete Expression（具体表达式）**：它实现抽象表达式接口，用于解释特定类型的表达式。

下面是解释器模式的 Python 实现示例：

```python
import typing as t


class Context:
    def __init__(self):
        self._variables = {}

    def set_variable(self, name: str, value):
        self._variables[name] = value

    def get_variable(self, name):
        return self._variables.get(name)


class Expression:
    def interpret(self, context: Context):
        raise NotImplementedError


class VariableExpression(Expression):
    def __init__(self, name):
        self._name = name

    def interpret(self, context):
        return context.get_variable(self._name)


class ConstantExpression(Expression):
    def __init__(self, value):
        self._value = value

    def interpret(self, context):
        return self._value


class AddExpression(Expression):
    def __init__(self, left: Expression, right: Expression):
        self._left = left
        self._right = right

    def interpret(self, context):
        return self._left.interpret(context) + self._right.interpret(context)


class SubtractExpression(Expression):
    def __init__(self, left: Expression, right: Expression):
        self._left = left
        self._right = right

    def interpret(self, context):
        return self._left.interpret(context) - self._right.interpret(context)


if __name__ == "__main__":
    # 测试代码
    context_ = Context()
    a = ConstantExpression(1)
    b = ConstantExpression(2)
    c = ConstantExpression(3)
    x = VariableExpression('x')
    y = VariableExpression('y')

    context_.set_variable('x', 10)
    context_.set_variable('y', 5)

    # 1 + 2 + 3 = 6
    expression = AddExpression(AddExpression(a, b), c)
    result = expression.interpret(context_)
    print(result)

    # 10 - 2 + 5 = 13
    expression = AddExpression(SubtractExpression(x, b), y)
    result = expression.interpret(context_)
    print(result)

```

代码解释：

- 在上面的实现中，我们定义了一个 Context 类来表示解释器的运行环境，它存储解释器所需的一些全局信息。
- Expression 类是抽象表达式类，包含一个 interpret 方法用于解释表达式。VariableExpression 和 ConstantExpression 类是具体表达式类，用于解释变量和常量。
- AddExpression 和 SubtractExpression 类是具体表达式类，用于解释加法和减法表达式。

**补充说明：**

我不明白，这个代码示例没感觉到具体的作用。

#### ==迭代器模式==

> **迭代器模式**（Iterator）是一种行为型设计模式，它允许你在**不暴露集合底层实现的情况下遍历集合中的所有元素**。

实现思路：

- 在迭代器模式中，集合类（如列表、树等）将遍历操作委托给一个迭代器对象，而不是直接实现遍历操作。
- 迭代器对象负责实现遍历操作，以及保存当前遍历位置等状态。
- 这样，集合类就可以将遍历操作与集合底层实现解耦，从而使得集合类更加简单、灵活和易于维护。

迭代器模式通常由以下几个角色组成：

- **迭代器（Iterator）**：定义了迭代器的接口，包含用于遍历集合元素的方法，如 next()、has_next() 等。
- **具体迭代器（ConcreteIterator）**：实现了迭代器接口，负责实现迭代器的具体遍历逻辑，以及保存当前遍历位置等状态。
- **集合（Aggregate）**：定义了集合的接口，包含用于获取迭代器对象的方法，如 create_iterator() 等。
- **具体集合（ConcreteAggregate）**：实现了集合接口，负责创建具体迭代器对象，以便遍历集合中的元素。

迭代器模式的优缺点包括：

- 将遍历操作与集合底层实现解耦，使得集合类更加灵活和易于维护。
   简化了集合类的接口，使得集合类更加简单明了。
- 提供了对不同类型的集合统一遍历的机制，使得算法的复用性更加高。
- 迭代器模式的**缺点**是，由于迭代器对象需要保存遍历位置等状态，因此它可能会占用比较大的内存。此外，由于迭代器对象需要负责遍历逻辑，因此它可能会变得比较复杂。

以下是迭代器模式的一个简单示例，实现了一个列表类和一个列表迭代器类：

```python
from abc import ABC, abstractmethod


# 抽象迭代器类
class Iterator(ABC):
    @abstractmethod
    def has_next(self):
        pass

    @abstractmethod
    def next(self):
        pass


# 具体迭代器类
class ConcreteIterator(Iterator):
    def __init__(self, data):
        self.data = data
        self.index = 0

    def has_next(self):
        return self.index < len(self.data)

    def next(self):
        if self.has_next():
            value = self.data[self.index]
            self.index += 1
            return value


# 抽象聚合类
class Aggregate(ABC):
    @abstractmethod
    def create_iterator(self):
        pass


# 具体聚合类
class ConcreteAggregate(Aggregate):
    def __init__(self, data):
        self.data = data

    def create_iterator(self):
        return ConcreteIterator(self.data)


# 测试
if __name__ == "__main__":
    data = [1, 2, 3, 4, 5]
    aggregate = ConcreteAggregate(data)
    iterator = aggregate.create_iterator()
    while iterator.has_next():
        print(iterator.next())

```

代码解释：

- 以上代码中，我们首先定义了抽象迭代器类 Iterator，其中定义了两个抽象方法 has_next 和  next，分别用于判断是否还有下一个元素和返回下一个元素。然后，我们定义了具体迭代器类 ConcreteIterator，它包含了一个数据列表  data 和一个指针 index，它实现了 has_next 和 next 方法。
- 接着，我们定义了抽象聚合类 Aggregate，其中定义了一个抽象方法  create_iterator，用于创建迭代器对象。然后，我们定义了具体聚合类 ConcreteAggregate，它包含了一个数据列表  data，它实现了 create_iterator 方法，返回一个 ConcreteIterator 对象。
- 最后，在测试代码中，我们创建了一个数据列表 data，然后创建了一个具体聚合对象 aggregate，并通过  create_iterator 方法创建了一个具体迭代器对象 iterator，然后使用 while  循环遍历该聚合对象中的各个元素，打印出每个元素的值。

这样，迭代器模式的基本结构就完成了。我们可以通过定义不同的聚合类和迭代器类来实现不同的聚合对象和迭代方式。这样，迭代器模式可以提高程序的灵活性和可扩展性。

**补充说明：**

对于 Python 而言，`__iter__`等魔术方法的存在让迭代器模式随手即可实现。



#### 中介者模式

> **中介者模式**（Mediator）是一种行为型设计模式，它用于**将多个对象之间的交互解耦**，从而使得对象之间的通信更加简单和灵活。

实现思路：

- 在中介者模式中，多个对象之间不直接相互通信，而是通过一个中介者对象进行通信。
- 这样，**每个对象只需要和中介者对象通信，而不需要知道其他对象的存在**。
- **中介者对象负责协调各个对象之间的交互**，使得系统更加灵活和易于维护。

中介者模式通常由以下几个角色组成：

- **抽象中介者（Mediator）**：定义了各个同事对象之间交互的接口，它通常包含一个或多个抽象方法，用于定义各种交互操作。

  > 接口的作用是定义一些既定操作，其他对象可以面向接口编程（具体实现必定会实现接口定义的所有操作），其他对象只需要了解这些操作的语义并使用即可！

- **具体中介者（ConcreteMediator）**：实现了抽象中介者接口，负责协调各个同事对象之间的交互关系。

- **抽象同事类（Colleague）**：定义了各个同事对象的接口，包含一个指向中介者对象的引用，以便与中介者进行通信。

  > Q：

- **具体同事类（ConcreteColleague）**：实现了抽象同事类的接口，负责实现各自的行为，并且需要和中介者对象进行通信。

中介者模式的优缺点包括：

- **解耦**了各个对象之间的交互关系，使得系统更加灵活和易于维护。
- 降低了系统的复杂度，使得各个对象之间的交互变得简单明了。
- 可以集中管理各个对象之间的交互关系，从而提高系统的可维护性和可扩展性。
- 中介者模式的**缺点**是，由于中介者对象需要负责协调各个同事对象之间的交互关系，因此它的职责可能会变得非常复杂。另外，由于中介者对象需要了解各个同事对象之间的交互关系，因此它可能会变得比较庞大。

下面是一个简单的中介者模式的 Python 实现，该实现使用一个聊天室作为中介者，多个用户作为同事类：

> ChatRoom 作为中介者，多个 User 作为同事类

```python
from typing import List

class User:
    def __init__(self, name: str, mediator):
        self.name = name
        self.mediator = mediator

    def send_message(self, message: str):
        self.mediator.send_message(message, self)

    def receive_message(self, message: str):
        print(f"{self.name} received message: {message}")

class ChatRoom:
    def __init__(self):
        self.users: List[User] = []

    def add_user(self, user: User):
        self.users.append(user)

    def send_message(self, message: str, sender: User):
        for user in self.users:
            if user != sender:
                user.receive_message(f"{sender.name}: {message}")

if __name__ == '__main__':
    chat_room = ChatRoom()

    alice = User("Alice", chat_room)
    bob = User("Bob", chat_room)
    charlie = User("Charlie", chat_room)

    chat_room.add_user(alice)
    chat_room.add_user(bob)
    chat_room.add_user(charlie)

    alice.send_message("Hi everyone!")
    bob.send_message("Hello Alice!")
    charlie.send_message("Hey guys, what's up?")

```

代码解释：

- 在上面的示例中，User 类表示同事类，ChatRoom 类表示中介者。
- 每个 User 对象都有一个指向 ChatRoom 对象的引用，以便与中介者进行通信。
- 当一个用户发送消息时，它会将消息发送到中介者，然后中介者会将消息广播给其他用户。

这个简单的实现演示了中介者模式的基本思想，尽管它没有实现一个完整的中介者模式。实际上，中介者模式通常需要更复杂的实现，以便处理更复杂的交互关系。



#### 备忘录模式

#### 观察者模式

#### 状态模式

#### 策略模式

#### 模板方法模式

#### 访问者模式

