---
tags: DD技術讀書會
---
> DD技術讀書會 
> # SOLID design principles 
> [原文出處](https://https://clouding.city/php/solid/)
> [name=Kelly] [time=Fri, Feb 22, 2019] [color=#907bf7]

---
<i class="fa fa-file-text"></i> 目錄：
- [Reference](#Reference)
- [導讀](#導讀)
----
## Reference

| 成員 | Reference | 語言 |
| ------ | ----------- | ----------------- |
| Ada   | [http://www.cnblogs.com/TomXu/archive/2012/01/06/2305513.html](http://www.cnblogs.com/TomXu/archive/2012/01/06/2305513.html) | javascript |
| 成員2 |  |  |
| 成員3 |  |  |
| 成員4 |  |  |
| 成員5 |  |  |
| 成員6 |  |  |
| 成員7 |  |  |


----
## 導讀

[原文出處](https://https://clouding.city/php/solid/)

**1. Single Responsibility Principle 單一職責原則**
＊只做一件事／分離與簡化邏輯
=>SRP: 降低單一類別被「改變」所影響的機會

範例討論 哪裡違反原則了？
    
*    Bad:
```php=    
class UserSettings
{
    private $user;

    public function __construct(User $user)
    {
        $this->user = $user;
    }

     public function changeSettings(array $settings): void
    {
        if ($this->verifyCredentials()) {
            // ...
        }
    }

    private function verifyCredentials(): bool
    {
        // ...
    }
}
```
*    Good:
```php= 
    class UserAuth
    {
        private $user;

        public function __construct(User $user)
        {
            $this->user = $user;
        }

        public function verifyCredentials(): bool
        {
            // ...
        }
    }

    class UserSettings
    {
        private $user;
        private $auth;

        public function __construct(User $user)
        {
            $this->user = $user;
            $this->auth = new UserAuth($user);
        }

        public function changeSettings(array $settings): void
        {
            if ($this->auth->verifyCredentials()) {
                // ...
            }
        }
    }
```
----
**2. Open Closed Principle 開放封閉原則**
＊將改變開放出去，找出通版封裝起來
=>OCP: 讓主類別不會因為新增需求而改變

範例討論 哪裡違反原則了？

* Bad:
```php= 
    abstract class Adapter
    {
        protected $name;

        public function getName(): string
        {
            return $this->name;
        }
    }

    class AjaxAdapter extends Adapter
    {
        public function __construct()
        {
            parent::__construct();

            $this->name = 'ajaxAdapter';
        }
    }

    class NodeAdapter extends Adapter
    {
        public function __construct()
        {
            parent::__construct();

            $this->name = 'nodeAdapter';
        }
    }

    class HttpRequester
    {
        private $adapter;

        public function __construct(Adapter $adapter)
        {
            $this->adapter = $adapter;
        }

        public function fetch(string $url): Promise
        {
            $adapterName = $this->adapter->getName();

            if ($adapterName === 'ajaxAdapter') {
                return $this->makeAjaxCall($url);
            } elseif ($adapterName === 'httpNodeAdapter') {
                return $this->makeHttpCall($url);
            }
        }

        private function makeAjaxCall(string $url): Promise
        {
            // request and return promise
        }

        private function makeHttpCall(string $url): Promise
        {
            // request and return promise
        }
    }
```
* Good:
```php= 
    interface Adapter
    {
        public function request(string $url): Promise;
    }

    class AjaxAdapter implements Adapter
    {
        public function request(string $url): Promise
        {
            // request and return promise
        }
    }

    class NodeAdapter implements Adapter
    {
        public function request(string $url): Promise
        {
            // request and return promise
        }
    }

    class HttpRequester
    {
        private $adapter;

        public function __construct(Adapter $adapter)
        {
            $this->adapter = $adapter;
        }

        public function fetch(string $url): Promise
        {
            return $this->adapter->request($url);
        }
    }
```
----
**3. Liskov Substitution Principle 里氏替換原則**
＊爸爸會修車，子承父業，我要修車找兒子也要可以！
=>LSP: 避免繼承時子類別所造成的「行為改變」

範例討論 哪裡違反原則了？

* Bad:
```php=
class Rectangle
{
    protected $width = 0;
    protected $height = 0;

    public function setWidth(int $width): void
    {
        $this->width = $width;
    }

    public function setHeight(int $height): void
    {
        $this->height = $height;
    }

    public function getArea(): int
    {
        return $this->width * $this->height;
    }
}

class Square extends Rectangle
{
    public function setWidth(int $width): void
    {
        $this->width = $this->height = $width;
    }

    public function setHeight(int $height): void
    {
        $this->width = $this->height = $height;
    }
}

function printArea(Rectangle $rectangle): void
{
    $rectangle->setWidth(4);
    $rectangle->setHeight(5);

    // BAD: Will return 25 for Square. Should be 20.
    echo sprintf('%s has area %d.', get_class($rectangle), $rectangle->getArea()).PHP_EOL;
}

$rectangles = [new Rectangle(), new Square()];

foreach ($rectangles as $rectangle) {
    printArea($rectangle);
}
```
* Good:
```php=
interface Shape
{
    public function getArea(): int;
}

class Rectangle implements Shape
{
    private $width = 0;
    private $height = 0;

    public function __construct(int $width, int $height)
    {
        $this->width = $width;
        $this->height = $height;
    }

    public function getArea(): int
    {
        return $this->width * $this->height;
    }
}

class Square implements Shape
{
    private $length = 0;

    public function __construct(int $length)
    {
        $this->length = $length;
    }

    public function getArea(): int
    {
        return $this->length ** 2;
    }
}

function printArea(Shape $shape): void
{
    echo sprintf('%s has area %d.', get_class($shape), $shape->getArea()).PHP_EOL;
}

$shapes = [new Rectangle(4, 5), new Square(5)];

foreach ($shapes as $shape) {
    printArea($shape);
}
```
----
**4. Least Knowledge Principle 最小知識原則**
＊把做一件事封裝，別人不需要知道實際上的細節！
=>LKP: 避免暴露過多資訊造成用戶端因流程調整而改變

----
**5. Interface Segregation Principle 介面隔離原則**
＊不需要用到的不應被依賴
=>ISP: 降低用戶端因為不相關介面而被改變

範例討論 哪裡違反原則了？
* Bad:
```php=
interface Employee
{
    public function work(): void;

    public function eat(): void;
}

class Human implements Employee
{
    public function work(): void
    {
        // ....working
    }

    public function eat(): void
    {
        // ...... eating in lunch break
    }
}

class Robot implements Employee
{
    public function work(): void
    {
        //.... working much more
    }

    public function eat(): void
    {
        //.... robot can't eat, but it must implement this method
    }
}
```
* Good:
```php=
interface Workable
{
    public function work(): void;
}

interface Feedable
{
    public function eat(): void;
}

interface Employee extends Feedable, Workable
{
}

class Human implements Employee
{
    public function work(): void
    {
        // ....working
    }

    public function eat(): void
    {
        //.... eating in lunch break
    }
}

// robot can only work
class Robot implements Workable
{
    public function work(): void
    {
        // ....working
    }
}
```
----
**6. Dependency Inversion Principle 依賴反轉原則**
＊把細節用注入的方式，去確保相依的流程是單向性
觀察程式碼相依流程會形成反向
=>DIP: 避免高階程式因為低階程式改變而被迫改變


範例討論 哪裡違反原則了？
* Bad:
```php=
class Employee
{
    public function work(): void
    {
        // ....working
    }
}

class Robot extends Employee
{
    public function work(): void
    {
        //.... working much more
    }
}

class Manager
{
    private $employee;

    public function __construct(Employee $employee)
    {
        $this->employee = $employee;
    }

    public function manage(): void
    {
        $this->employee->work();
    }
}
```
* Good:
```php=
interface Employee
{
    public function work(): void;
}

class Human implements Employee
{
    public function work(): void
    {
        // ....working
    }
}

class Robot implements Employee
{
    public function work(): void
    {
        //.... working much more
    }
}

class Manager
{
    private $employee;

    public function __construct(Employee $employee)
    {
        $this->employee = $employee;
    }

    public function manage(): void
    {
        $this->employee->work();
    }
}
```

   
   
   