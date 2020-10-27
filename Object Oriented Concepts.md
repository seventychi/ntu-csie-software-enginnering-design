# Object-Oriented Concepts

## Identity

* 離散且可被區分識別的實體
* 每個實體皆為唯一，即便其所有的屬性皆相同

## Classification

* 每個 Object 皆為 Class 的實體（Instance）。

### Object

* Class 的實體。
* Instantiation（實例化）：建立 Class 的實體。

### Class

* 定義物件的行為

  * 變數
  * 操作行為
  * 存取的方式

* Class Notation

  <img src="https://raw.githubusercontent.com/seventychi/ntu-csie-software-enginnering-design/main/images/class%20notation.png" alt="class notation" style="zoom:50%;" />

  * Attribute

    * UML 格式：Visibility / name: type multiplicity = default value

      * Visibility

        +：public
        -：private
        #：protected
        ~：package

      * Type

        * Class
        * Interface
        * Int, Float, etc.

      * Multiplicity

        * 1 .. *
        * 0, 1 to N
        * *

    * Examples

      * +wheels: wheel[4]
      * -bumper stickers: sticker[*]
      * -passengers: person[1..5]

  * Static Attribute：屬於 Class 本身的屬性（不屬於 Instance），使用 Constant Values（常數）定義。

    * Examples

      * +BLACK: int = 0xFF000000

        ```java
        public class Color {
        	public static final int BLACK = 0xFF000000;
        }
        ```

  * Operation

    定義行為（A method is and **implementation** of an operation）

    * 格式：Visibility name (parameters): return-type {property}
    * Examples
      * +getSize(): Rectangle
      * +setSize(name: String): void
      * +getComponents(): Component[0..*]

  * Static Operation：屬於 Class 本身的行為，提供方便快速的方法

    * UML 格式：<u>Visibility name (parameters): return-type {property}</u>

      （註）加底線

### Abstract Class

* 必須包含至少一個抽象的方法
* 格式：類別名稱使用斜線

## Interface

* 提供屬性及方法但不提供實作

* UML 格式

  <img src="https://raw.githubusercontent.com/seventychi/ntu-csie-software-enginnering-design/main/images/interface.png" alt="interface" style="zoom:50%;" />

## Inheritance

* 繼承

* UML 格式

  <img src="https://raw.githubusercontent.com/seventychi/ntu-csie-software-enginnering-design/main/images/inheritance.png" alt="inheritance" style="zoom:50%;" />

* 多重繼承（Multi Inheritance）
  * 多重繼承的子類別又稱為 Join Class。
  * 實體在初始化或是呼叫方法時會有 Overlapping（多個父類別重複呼叫）的問題。
  * 解決多重繼承的方法：透過 Delegation 的方式設計；只繼承最重要的類別，其他的行為則呼叫 Delegate 進行處理。

## Polymorphism

* 同樣的 Operation（操作）有不同的行為（實作）或是不同的類別。
* Method = 針對 Operation 進行明確的實作。

### Static polymorphism

* Overloading：同一個 Operation 傳入不同的參數進行實作。

  <img src="https://raw.githubusercontent.com/seventychi/ntu-csie-software-enginnering-design/main/images/static%20polymorphism.png" alt="static polymorphism" style="zoom:50%;" />

### Dynamic polymorphism

* 相同的 Operation 藉由不同的 Class 進行實作。

  <img src="https://raw.githubusercontent.com/seventychi/ntu-csie-software-enginnering-design/main/images/dynamic%20polymorphism.png" alt="dynamic polymorphism" style="zoom:50%;" />

## Abstraction

* 只關注在必要的 Operation 跟 Attribute，忽略其他不影響 Entity 運作的內容。
* 通常應用在分析階段。

## Encapsulation

* 提供外部（External classes）可操作的 Attribute, Operations 等；將實際的實作封裝在自己的 Class 內。

## Relations

* 強弱關係：Dependency < Association < Aggregation < Composition < Generalization

|      | Dependency<br/>（依賴）                   | Association<br>（關聯）    | Aggregation<br/>（聚合）                                 | Composition<br/>（組合）   | Generalization<br/>（泛型） |
| ---- | ----------------------------------------- | -------------------------- | -------------------------------------------------------- | -------------------------- | --------------------------- |
| 概念 | A uses-a B                                | A has-a B                  | A owns-a B                                               | Ｂ is-part-of Ａ           | B is-a A                    |
| 說明 | A 使用 B。                                | A 有 B。                   | A 擁有 B                                                 | Ｂ 是 Ａ 的一部分          | B 是 A                      |
| UML  | 虛線箭頭                                  | 實線箭頭                   | 空心菱形（菱形放在主體邊）                               | 實心菱形（菱形放在主體邊） | 實線三角形箭頭              |
|      | Ａ -----> B                               | A ~~-----~~> B             | A ◇~~------~~> B                                         | A ◆~~-----~~> B            | A ◁~~------~~ B             |
| 範例 | Window（A）使用 Window Closing Event（B） | Window（A） 有 Cursor（B） | 車子（A）擁有輪子、引擎（B），但輪子跟引擎可以單獨存在。 | 手指（B）是手（A）的一部分 | Cat（B） 是 Animal（A）     |

## Role and Multiplicity

<img src="https://raw.githubusercontent.com/seventychi/ntu-csie-software-enginnering-design/main/images/role%20and%20multiplicity.png" alt="role and multiplicity" />

## Reference

李允中 教授，NTU Software Engineering Design Fall 2020