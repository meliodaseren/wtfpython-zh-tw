[wtfpython English](https://github.com/satwikkansal/wtfpython)

[wtfpython 简体中文](https://github.com/leisurelicht/wtfpython-cn)

---

<p align="center"><img src="/images/logo.png" alt=""></p>
<h1 align="center">What the f*ck Python! 🐍</h1>
<p align="center">一些有趣且鮮為人知的 Python 特性.</p>

<p align="center">
<a href="https://github.com/satwikkansal/wtfpython">English</a>
| <a href="https://github.com/leisurelicht/wtfpython-cn">簡體中文</a>
</p>

[![WTFPL 2.0][license-image]][license-url] [![Commit id][commit-image]][commit-url]


Python，是一個設計優美的解釋型高級語言, 它提供了很多能讓程序員感到舒適的功能特性. 但有的時候, Python 的一些輸出結果對於初學者來說似乎並不是那麼一目了然.

這個有趣的項目意在收集 Python 中那些難以理解和反人類直覺的例子以及鮮為人知的功能特性, 並嘗試討論這些現像背後真正的原理!

雖然下面的有些例子並不一定會讓你覺得 WTFs, 但它們依然有可能會告訴你一些你所不知道的 Python 有趣特性.  我覺得這是一種學習編程語言內部原理的好辦法, 而且我相信你也會從中獲得樂趣!

如果您是一位經驗比較豐富的 Python 程序員, 你可以嘗試挑戰看是否能一次就找到例子的正確答案. 你可能對其中的一些例子已經比較熟悉了, 那這也許能喚起你當年踩這些坑時的甜蜜回憶 :sweat_smile:

PS: 如果你不是第一次讀了, 你可以在[這裡](https://github.com/satwikkansal/wtfpython/releases/)獲取變動內容.

那麼, 讓我們開始吧...

# Table of Contents/目錄
<!-- TOC -->

- [Table of Contents/目錄](#table-of-contents目錄)
- [Structure of the Examples/示例結構](#structure-of-the-examples示例結構)
- [Usage/用法](#usage用法)
- [👀 Examples/示例](#-examples示例)
    - [Section: Strain your brain!/大腦運動!](#section-strain-your-brain大腦運動)
        - [> Strings can be tricky sometimes/微妙的字串 *](#-strings-can-be-tricky-sometimes微妙的字串-)
        - [> Time for some hash brownies!/是時候來點蛋糕了!](#-time-for-some-hash-brownies是時候來點蛋糕了)
        - [> Return return everywhere!/到處返回！](#-return-return-everywhere到處返回)
        - [> Deep down, we're all the same./本質上,我們都一樣. *](#-deep-down-were-all-the-same本質上我們都一樣-)
        - [> For what?/為什麼?](#-for-what為什麼)
        - [> Evaluation time discrepancy/執行時機差異](#-evaluation-time-discrepancy執行時機差異)
        - [> `is` is not what it is!/出人意料的`is`!](#-is-is-not-what-it-is出人意料的is)
        - [> A tic-tac-toe where X wins in the first attempt!/一蹴即至!](#-a-tic-tac-toe-where-x-wins-in-the-first-attempt一蹴即至)
        - [> The sticky output function/麻煩的輸出](#-the-sticky-output-function麻煩的輸出)
        - [> `is not ...` is not `is (not ...)`/`is not ...` 不是 `is (not ...)`](#-is-not--is-not-is-not-is-not--不是-is-not-)
        - [> The surprising comma/意外的逗號](#-the-surprising-comma意外的逗號)
        - [> Backslashes at the end of string/字串末尾的反斜線](#-backslashes-at-the-end-of-string字串末尾的反斜線)
        - [> not knot!/別糾結!](#-not-knot別糾結)
        - [> Half triple-quoted strings/三個引號](#-half-triple-quoted-strings三個引號)
        - [> Midnight time doesn't exist?/不存在的午夜?](#-midnight-time-doesnt-exist不存在的午夜)
        - [> What's wrong with booleans?/布爾你怎麼了?](#-whats-wrong-with-booleans布爾你怎麼了)
        - [> Class attributes and instance attributes/類屬性和實例屬性](#-class-attributes-and-instance-attributes類屬性和實例屬性)
        - [> yielding None/生成 None](#-yielding-none生成-none)
        - [> Mutating the immutable!/強人所難](#-mutating-the-immutable強人所難)
        - [> The disappearing variable from outer scope/消失的外部變量](#-the-disappearing-variable-from-outer-scope消失的外部變量)
        - [> When True is actually False/真亦假](#-when-true-is-actually-false真亦假)
        - [> From filled to None in one instruction.../從有到無...](#-from-filled-to-none-in-one-instruction從有到無)
        - [> Subclass relationships/子類關系 *](#-subclass-relationships子類關系-)
        - [> The mysterious key type conversion/神秘的鍵型轉換 *](#-the-mysterious-key-type-conversion神秘的鍵型轉換-)
        - [> Let's see if you can guess this?/看看你能否猜到這一點?](#-lets-see-if-you-can-guess-this看看你能否猜到這一點)
    - [Section: Appearances are deceptive!/外表是靠不住的!](#section-appearances-are-deceptive外表是靠不住的)
        - [> Skipping lines?/跳過一行?](#-skipping-lines跳過一行)
        - [> Teleportation/空間移動 *](#-teleportation空間移動-)
        - [> Well, something is fishy.../嗯, 有些可疑...](#-well-something-is-fishy嗯有些可疑)
    - [Section: Watch out for the landmines!/小心地雷!](#section-watch-out-for-the-landmines小心地雷)
        - [> Modifying a dictionary while iterating over it/迭代字典時的修改](#-modifying-a-dictionary-while-iterating-over-it迭代字典時的修改)
        - [> Stubborn `del` operator/堅強的 `del` *](#-stubborn-del-operator堅強的-del-)
        - [> Deleting a list item while iterating/迭代列表時刪除元素](#-deleting-a-list-item-while-iterating迭代列表時刪除元素)
        - [> Loop variables leaking out!/循環變量泄漏!](#-loop-variables-leaking-out循環變量泄漏)
        - [> Beware of default mutable arguments!/當心默認的可變參數!](#-beware-of-default-mutable-arguments當心默認的可變參數)
        - [> Catching the Exceptions/捕獲異常](#-catching-the-exceptions捕獲異常)
        - [> Same operands, different story!/同人不同命!](#-same-operands-different-story同人不同命)
        - [> The out of scope variable/外部作用域變量](#-the-out-of-scope-variable外部作用域變量)
        - [> Be careful with chained operations/小心鏈式操作](#-be-careful-with-chained-operations小心鏈式操作)
        - [> Name resolution ignoring class scope/忽略類作用域的名稱解析](#-name-resolution-ignoring-class-scope忽略類作用域的名稱解析)
        - [> Needle in a Haystack/大海撈針](#-needle-in-a-haystack大海撈針)
    - [Section: The Hidden treasures!/隱藏的寶藏!](#section-the-hidden-treasures隱藏的寶藏)
        - [> Okay Python, Can you make me fly?/Python, 可否帶我飛? *](#-okay-python-can-you-make-me-flypython-可否帶我飛-)
        - [> `goto`, but why?/`goto`, 但為什麼? *](#-goto-but-whygoto-但為什麼-)
        - [> Brace yourself!/做好思想准備 *](#-brace-yourself做好思想准備-)
        - [> Let's meet Friendly Language Uncle For Life/讓生活更友好 *](#-lets-meet-friendly-language-uncle-for-life讓生活更友好-)
        - [> Even Python understands that love is complicated/連 Python 也知道愛是難言的 *](#-even-python-understands-that-love-is-complicated連-Python-也知道愛是難言的-)
        - [> Yes, it exists!/是的, 它存在!](#-yes-it-exists是的-它存在)
        - [> Inpinity/無限 *](#-inpinity無限-)
        - [> Mangling time!修飾時間! *](#-mangling-time修飾時間-)
    - [Section: Miscellaneous/雜項](#section-miscellaneous雜項)
        - [> `+=` is faster/更快的 `+=` ](#--is-faster更快的-)
        - [> Let's make a giant string!/來做個巨大的字串吧!](#-lets-make-a-giant-string來做個巨大的字串吧)
        - [> Explicit typecast of strings/字串的顯式類型轉換](#-explicit-typecast-of-strings字串的顯式類型轉換)
        - [> Minor Ones/小知識點](#-minor-ones小知識點)
- [Contributing/貢獻](#contributing貢獻)
- [Acknowledgements/致謝](#acknowledgements致謝)
- [🎓 License/許可](#-license許可)
    - [Help/幫助](#help幫助)
    - [Surprise your geeky pythonist friends?/想給你的極客朋友一個驚喜?](#surprise-your-geeky-pythonist-friends想給你的極客朋友一個驚喜)
    - [Need a pdf version?/需要來一份 pdf 版?](#need-a-pdf-version需要來一份-pdf-版)
    - [Follow Commit/追蹤 Commit](#follow-commit追蹤-Commit)

<!-- /TOC -->

# Structure of the Examples/示例結構

所有示例的結構都如下所示:

> ### > 一個精選的標題 *
> 標題末尾的星號表示該示例在第一版中不存在，是最近添加的.
>
> ```py
> # 准備代碼.
> # 釋放魔法...
> ```
>
> **Output (Python version):**
> ```py
> >>> 觸發語句
> 出乎意料的輸出結果
> ```
> (可選): 對意外輸出結果的簡短描述.
>
>
> #### 💡 說明:
>
> * 簡要說明發生了什麼以及為什麼會發生.
>   ```py
>   如有必要, 舉例說明
>   ```
>   **Output:**
>   ```py
>   >>> 觸發語句 # 一些讓魔法變得容易理解的例子
>   # 一些正常的輸入
>   ```

**注意:** 所有的示例都在 Python 3.5.2 版本的交互解釋器上測試過, 如果不特別說明應該適用於所有 Python 版本.

# Usage/用法

我個人建議, 最好依次閱讀下面的示例, 並對每個示例:
- 仔細閱讀設置例子最開始的代碼.  如果您是一位經驗豐富的 Python 程序員, 那麼大多數時候您都能成功預期到後面的結果.
- 閱讀輸出結果,
  + 確認結果是否如你所料.
  + 確認你是否知道這背後的原理.
    - 如果不知道, 深呼吸然後閱讀說明 (如果你還是看不明白, 別沉默! 可以在[這](https://github.com/satwikkansal/wtfPython)提個 issue).
    - 如果知道, 給自己點獎勵, 然後去看下一個例子.

PS: 你也可以在命令行閱讀 WTFpython. 我們有 pypi 包 和 npm 包(支持代碼高亮).(譯: 這兩個都是英文版的)

安裝 npm 包 [`wtfpython`](https://www.npmjs.com/package/wtfpython)
```sh
$ npm install -g wtfpython
```

或者, 安裝 pypi 包 [`wtfpython`](https://pypi.python.org/pypi/wtfpython)
```sh
$ pip install wtfpython -U
```

現在, 在命令行中運行 `wtfpython`, 你就可以開始瀏覽了.

---

# 👀 Examples/示例


## Section: Strain your brain!/大腦運動!

### > Strings can be tricky sometimes/微妙的字串 *

1\.
```py
>>> a = "some_string"
>>> id(a)
140420665652016
>>> id("some" + "_" + "string") # 注意兩個的id值是相同的.
140420665652016
```

2\.
```py
>>> a = "wtf"
>>> b = "wtf"
>>> a is b
True

>>> a = "wtf!"
>>> b = "wtf!"
>>> a is b
False

>>> a, b = "wtf!", "wtf!"
>>> a is b
True
```

3\.
```py
>>> 'a' * 20 is 'aaaaaaaaaaaaaaaaaaaa'
True
>>> 'a' * 21 is 'aaaaaaaaaaaaaaaaaaaaa'
False
```

很好理解, 對吧?

#### 💡 說明:
- 這些行為是由於 Cpython 在編譯優化時, 某些情況下會嘗試使用已經存在的不可變對像而不是每次都創建一個新對像. (這種行為被稱作字串的駐留 [string interning] )
- 發生駐留之後, 許多變量可能指向內存中的相同字串對像. (從而節省內存)
- 在上面的代碼中, 字串是隱式駐留的. 何時發生隱式駐留則取決於具體的實現. 這裡有一些方法可以用來猜測字串是否會被駐留:
  - 所有長度為 0 和長度為 1 的字串都被駐留.
  - 字串在編譯時被實現 (`'wtf'` 將被駐留, 但是 `''.join(['w', 't', 'f']` 將不會被駐留)
  - 字串中只包含字母，數字或下劃線時將會駐留. 所以 `'wtf!'` 由於包含 `!` 而未被駐留. 可以在[這裡](https://github.com/python/cpython/blob/3.6/Objects/codeobject.c#L19)找到 CPython 對此規則的實現.

    <img src="/images/string-intern/string_intern.png" alt="">

- 當在同一行將 `a` 和 `b` 的值設置為 `"wtf!"` 的時候, Python 解釋器會創建一個新對像, 然後同時引用第二個變量. 如果你在不同的行上進行賦值操作, 它就不會“知道”已經有一個 `wtf！` 對像 (因為 `"wtf!"` 不是按照上面提到的方式被隱式駐留的). 它是一種編譯器優化, 特別適用於交互式環境.
- 常量折疊 (constant folding) 是 Python 中的一種 [窺孔優化 (peephole optimization)](https://en.wikipedia.org/wiki/Peephole_optimization) 技術. 這意味著在編譯時表達式 `'a'*20` 會被替換為 `'aaaaaaaaaaaaaaaaaaaa'` 以減少運行時的時鐘周期. 只有長度小於 20 的字串才會發生常量折疊. (為啥? 想像一下由於表達式 `'a'*10**10` 而生成的 `.pyc` 文件的大小). 相關的源碼實現在[這裡](https://github.com/python/cpython/blob/3.6/Python/peephole.c#L288).


---

### > Time for some hash brownies!/是時候來點蛋糕了!
* hash brownie指一種含有大麻成分的蛋糕, 所以這裡是句雙關

1\.
```py
some_dict = {}
some_dict[5.5] = "Ruby"
some_dict[5.0] = "JavaScript"
some_dict[5] = "Python"
```

**Output:**
```py
>>> some_dict[5.5]
"Ruby"
>>> some_dict[5.0]
"Python"
>>> some_dict[5]
"Python"
```

"Python" 消除了 "JavaScript" 的存在 ?

#### 💡 說明:

* Python 字典通過檢查鍵值是否相等和比較哈希值來確定兩個鍵是否相同.
* 具有相同值的不可變對像在 Python 中始終具有相同的哈希值.
  ```py
  >>> 5 == 5.0
  True
  >>> hash(5) == hash(5.0)
  True
  ```
  **注意:** 具有不同值的對像也可能具有相同的哈希值（哈希衝突）.
* 當執行 `some_dict[5] = "Python"` 語句時, 因為Python將 `5` 和 `5.0` 識別為 `some_dict` 的同一個鍵, 所以已有值 "JavaScript" 就被 "Python" 覆蓋了.
* 這個 StackOverflow的[回答](https://stackoverflow.com/a/32211042/4354153)漂亮的解釋了這背後的基本原理.

---

### > Return return everywhere!/到處返回！

```py
def some_func():
    try:
        return 'from_try'
    finally:
        return 'from_finally'
```

**Output:**
```py
>>> some_func()
'from_finally'
```

#### 💡 說明:

- 當在 "try...finally" 語句的 `try` 中執行 `return`, `break` 或 `continue` 後, `finally` 子句依然會執行.
- 函數的返回值由最後執行的 `return` 語句決定. 由於 `finally` 子句一定會執行, 所以 `finally` 子句中的 `return` 將始終是最後執行的語句.

---

### > Deep down, we're all the same./本質上,我們都一樣. *

```py
class WTF:
  pass
```

**Output:**
```py
>>> WTF() == WTF() # 兩個不同的對像應該不相等
False
>>> WTF() is WTF() # 也不相同
False
>>> hash(WTF()) == hash(WTF()) # 哈希值也應該不同
True
>>> id(WTF()) == id(WTF())
True
```

#### 💡 說明:

* 當調用 `id` 函數時, Python 創建了一個 `WTF` 類的對像並傳給 `id` 函數. 然後 `id` 函數獲取其id值 (也就是內存地址), 然後丟棄該對像. 該對像就被銷毀了.
* 當我們連續兩次進行這個操作時, Python會將相同的內存地址分配給第二個對像. 因為 (在CPython中) `id` 函數使用對像的內存地址作為對像的id值, 所以兩個對像的id值是相同的.
* 綜上, 對像的id值僅僅在對像的生命周期內唯一. 在對像被銷毀之後, 或被創建之前, 其他對像可以具有相同的id值.
* 那為什麼 `is` 操作的結果為 `False` 呢? 讓我們看看這段代碼.
  ```py
  class WTF(object):
    def __init__(self): print("I")
    def __del__(self): print("D")
  ```

  **Output:**
  ```py
  >>> WTF() is WTF()
  I
  I
  D
  D
  False
  >>> id(WTF()) == id(WTF())
  I
  D
  I
  D
  True
  ```
  正如你所看到的, 對像銷毀的順序是造成所有不同之處的原因.

---

### > For what?/為什麼?

```py
some_string = "wtf"
some_dict = {}
for i, some_dict[i] in enumerate(some_string):
    pass
```

**Output:**
```py
>>> some_dict # 創建了索引字典.
{0: 'w', 1: 't', 2: 'f'}
```

####  💡 說明:

* [Python 語法](https://docs.python.org/3/reference/grammar.html) 中對 `for` 的定義是:
  ```
  for_stmt: 'for' exprlist 'in' testlist ':' suite ['else' ':' suite]
  ```
  其中 `exprlist` 指分配目標. 這意味著對可迭代對像中的**每一項都會執行**類似 `{exprlist} = {next_value}` 的操作.

  一個有趣的例子說明了這一點:
  ```py
  for i in range(4):
      print(i)
      i = 10
  ```

  **Output:**
  ```
  0
  1
  2
  3
  ```

  你可曾覺得這個循環只會運行一次?

  **💡 說明:**

  - 由於循環在Python中工作方式, 賦值語句 `i = 10` 並不會影響迭代循環, 在每次迭代開始之前, 迭代器(這裡指 `range(4)`) 生成的下一個元素就被解包並賦值給目標列表的變量(這裡指 `i`)了.

* 在每一次的迭代中, `enumerate(some_string)` 函數就生成一個新值 `i` (計數器增加) 並從 `some_string` 中獲取一個字符. 然後將字典 `some_dict` 鍵 `i` (剛剛分配的) 的值設為該字符. 本例中循環的展開可以簡化為:
  ```py
  >>> i, some_dict[i] = (0, 'w')
  >>> i, some_dict[i] = (1, 't')
  >>> i, some_dict[i] = (2, 'f')
  >>> some_dict
  ```

---

### > Evaluation time discrepancy/執行時機差異

1\.
```py
array = [1, 8, 15]
g = (x for x in array if array.count(x) > 0)
array = [2, 8, 22]
```

**Output:**
```py
>>> print(list(g))
[8]
```

2\.

```py
array_1 = [1,2,3,4]
g1 = (x for x in array_1)
array_1 = [1,2,3,4,5]

array_2 = [1,2,3,4]
g2 = (x for x in array_2)
array_2[:] = [1,2,3,4,5]
```

**Output:**
```py
>>> print(list(g1))
[1,2,3,4]

>>> print(list(g2))
[1,2,3,4,5]
```

#### 💡 說明

- 在[生成器](https://wiki.python.org/moin/Generators)表達式中, `in` 子句在聲明時執行, 而條件子句則是在運行時執行.
- 所以在運行前, `array` 已經被重新賦值為 `[2, 8, 22]`, 因此對於之前的 `1`, `8` 和 `15`, 只有 `count(8)` 的結果是大於 `0` 的, 所以生成器只會生成 `8`.
- 第二部分中 `g1` 和 `g2` 的輸出差異則是由於變量 `array_1` 和 `array_2` 被重新賦值的方式導致的.
- 在第一種情況下, `array_1` 被綁定到新對像 `[1,2,3,4,5]`, 因為 `in` 子句是在聲明時被執行的， 所以它仍然引用舊對像 `[1,2,3,4]`(並沒有被銷毀).
- 在第二種情況下, 對 `array_2` 的切片賦值將相同的舊對像 `[1,2,3,4]` 原地更新為 `[1,2,3,4,5]`. 因此 `g2` 和 `array_2` 仍然引用同一個對像(這個對像現在已經更新為 `[1,2,3,4,5]`).

---

### > `is` is not what it is!/出人意料的`is`!

下面是一個在互聯網上非常有名的例子.

```py
>>> a = 256
>>> b = 256
>>> a is b
True

>>> a = 257
>>> b = 257
>>> a is b
False

>>> a = 257; b = 257
>>> a is b
True
```

#### 💡 說明:

**`is` 和 `==` 的區別**

* `is` 運算符檢查兩個運算對像是否引用自同一對像 (即, 它檢查兩個預算對像是否相同).
* `==` 運算符比較兩個運算對像的值是否相等.
* 因此 `is` 代表引用相同, `==` 代表值相等. 下面的例子可以很好的說明這點,
  ```py
  >>> [] == []
  True
  >>> [] is [] # 這兩個空列表位於不同的內存地址.
  False
  ```

**`256` 是一個已經存在的對像, 而 `257` 不是**

當你啟動Python 的時候, `-5` 到 `256` 的數值就已經被分配好了. 這些數字因為經常使用所以適合被提前准備好.

引用自 https://docs.python.org/3/c-api/long.html
> 當前的實現為-5到256之間的所有整數保留一個整數對像數組, 當你創建了一個該範圍內的整數時, 你只需要返回現有對像的引用. 所以改變1的值是有可能的. 我懷疑這種行為在Python中是未定義行為. :-)

```py
>>> id(256)
10922528
>>> a = 256
>>> b = 256
>>> id(a)
10922528
>>> id(b)
10922528
>>> id(257)
140084850247312
>>> x = 257
>>> y = 257
>>> id(x)
140084850247440
>>> id(y)
140084850247344
```

這裡解釋器並沒有智能到能在執行 `y = 257` 時意識到我們已經創建了一個整數 `257`, 所以它在內存中又新建了另一個對像.

**當 `a` 和 `b` 在同一行中使用相同的值初始化時，會指向同一個對像.**

```py
>>> a, b = 257, 257
>>> id(a)
140640774013296
>>> id(b)
140640774013296
>>> a = 257
>>> b = 257
>>> id(a)
140640774013392
>>> id(b)
140640774013488
```

* 當 a 和 b 在同一行中被設置為 `257` 時, Python 解釋器會創建一個新對像, 然後同時引用第二個變量. 如果你在不同的行上進行, 它就不會 "知道" 已經存在一個 `257` 對像了.
* 這是一種特別為交互式環境做的編譯器優化. 當你在實時解釋器中輸入兩行的時候, 他們會單獨編譯, 因此也會單獨進行優化. 如果你在 `.py` 文件中嘗試這個例子, 則不會看到相同的行為, 因為文件是一次性編譯的.

---

### > A tic-tac-toe where X wins in the first attempt!/一蹴即至!

```py
# 我們先初始化一個變量row
row = [""]*3 #row i['', '', '']
# 並創建一個變量board
board = [row]*3
```

**Output:**
```py
>>> board
[['', '', ''], ['', '', ''], ['', '', '']]
>>> board[0]
['', '', '']
>>> board[0][0]
''
>>> board[0][0] = "X"
>>> board
[['X', '', ''], ['X', '', ''], ['X', '', '']]
```

我們有沒有賦值過3個 "X" 呢？

#### 💡 說明:

當我們初始化 `row` 變量時, 下面這張圖展示了內存中的情況。

![image](/images/tic-tac-toe/after_row_initialized.png)

而當通過對 `row` 做乘法來初始化 `board` 時, 內存中的情況則如下圖所示 (每個元素 `board[0]`, `board[1]` 和 `board[2]` 都和 `row` 一樣引用了同一列表.)

![image](/images/tic-tac-toe/after_board_initialized.png)

我們可以通過不使用變量 `row` 生成 `board` 來避免這種情況. ([這個](https://github.com/satwikkansal/wtfpython/issues/68)issue提出了這個需求.)

```py
>>> board = [['']*3 for _ in range(3)]
>>> board[0][0] = "X"
>>> board
[['X', '', ''], ['', '', ''], ['', '', '']]
```

---

### > The sticky output function/麻煩的輸出

```py
funcs = []
results = []
for x in range(7):
    def some_func():
        return x
    funcs.append(some_func)
    results.append(some_func()) # 注意這裡函數被執行了

funcs_results = [func() for func in funcs]
```

**Output:**
```py
>>> results
[0, 1, 2, 3, 4, 5, 6]
>>> funcs_results
[6, 6, 6, 6, 6, 6, 6]
```

即使每次在迭代中將 `some_func` 加入 `funcs` 前的 `x` 值都不相同, 所有的函數還是都返回6.

// 再換個例子

```py
>>> powers_of_x = [lambda x: x**i for i in range(10)]
>>> [f(2) for f in powers_of_x]
[512, 512, 512, 512, 512, 512, 512, 512, 512, 512]
```

#### 💡 說明:

- 當在循環內部定義一個函數時, 如果該函數在其主體中使用了循環變量, 則閉包函數將與循環變量綁定, 而不是它的值. 因此, 所有的函數都是使用最後分配給變量的值來進行計算的.

- 可以通過將循環變量作為命名變量傳遞給函數來獲得預期的結果. **為什麼這樣可行?** 因為這會在函數內再次定義一個局部變量.

    ```py
    funcs = []
    for x in range(7):
        def some_func(x=x):
            return x
        funcs.append(some_func)
    ```

    **Output:**
    ```py
    >>> funcs_results = [func() for func in funcs]
    >>> funcs_results
    [0, 1, 2, 3, 4, 5, 6]
    ```

---

### > `is not ...` is not `is (not ...)`/`is not ...` 不是 `is (not ...)`

```py
>>> 'something' is not None
True
>>> 'something' is (not None)
False
```

#### 💡 說明:

- `is not` 是個單獨的二元運算符, 與分別使用 `is` 和 `not` 不同.
-  如果操作符兩側的變量指向同一個對像, 則 `is not` 的結果為 `False`, 否則結果為 `True`.

---

### > The surprising comma/意外的逗號

**Output:**
```py
>>> def f(x, y,):
...     print(x, y)
...
>>> def g(x=4, y=5,):
...     print(x, y)
...
>>> def h(x, **kwargs,):
  File "<stdin>", line 1
    def h(x, **kwargs,):
                     ^
SyntaxError: invalid syntax
>>> def h(*args,):
  File "<stdin>", line 1
    def h(*args,):
                ^
SyntaxError: invalid syntax
```

#### 💡 說明:

- 在Python函數的形式參數列表中, 尾隨逗號並不一定是合法的.
- 在Python中, 參數列表部分用前置逗號定義, 部分用尾隨逗號定義. 這種衝突導致逗號被夾在中間, 沒有規則定義它.(譯:這一句看得我也很懵逼,只能強翻了.詳細解釋看下面的討論帖會一目了然.)
- **注意:** 尾隨逗號的問題已經在Python 3.6中被[修復](https://bugs.python.org/issue9232)了. 而這篇[帖子](https://bugs.python.org/issue9232#msg248399)中則簡要討論了Python中尾隨逗號的不同用法.
---

### > Backslashes at the end of string/字串末尾的反斜線

**Output:**
```
>>> print("\\ C:\\")
\ C:\
>>> print(r"\ C:")
\ C:
>>> print(r"\ C:\")

    File "<stdin>", line 1
      print(r"\ C:\")
                     ^
SyntaxError: EOL while scanning string literal
```

#### 💡 說明:

- 在以 `r` 開頭的原始字串中, 反斜線並沒有特殊含義.
  ```py
  >>> print(repr(r"wt\"f"))
  'wt\\"f'
  ```
- 解釋器所做的只是簡單的改變了反斜線的行為, 因此會直接放行反斜線及後一個的字符. 這就是反斜線在原始字串末尾不起作用的原因.

---

### > not knot!/別糾結!

```py
x = True
y = False
```

**Output:**
```py
>>> not x == y
True
>>> x == not y
  File "<input>", line 1
    x == not y
           ^
SyntaxError: invalid syntax
```

#### 💡 說明:

* 運算符的優先級會影響表達式的求值順序, 而在 Python 中 `==` 運算符的優先級要高於 `not` 運算符.
* 所以 `not x == y` 相當於 `not (x == y)`, 同時等價於 `not (True == False)`, 最後的運算結果就是 `True`.
* 之所以 `x == not y` 會拋一個 `SyntaxError` 異常, 是因為它會被認為等價於 `(x == not) y`, 而不是你一開始期望的 `x == (not y)`.
* 解釋器期望 `not` 標記是 `not in` 操作符的一部分 (因為 `==` 和 `not in` 操作符具有相同的優先級), 但是它在 `not` 標記後面找不到 `in` 標記, 所以會拋出 `SyntaxError` 異常.

---

### > Half triple-quoted strings/三個引號

**Output:**
```py
>>> print('wtfpython''')
wtfpython
>>> print("wtfpython""")
wtfpython
>>> # 下面的語句會拋出 `SyntaxError` 異常
>>> # print('''wtfpython')
>>> # print("""wtfpython")
```

#### 💡 說明:
+ Python 提供隱式的[字串鏈接](https://docs.python.org/2/reference/lexical_analysis.html#string-literal-concatenation), 例如,
  ```
  >>> print("wtf" "python")
  wtfpython
  >>> print("wtf" "") # or "wtf"""
  wtf
  ```
+ `'''` 和 `"""` 在 Python中也是字串定界符, Python 解釋器在先遇到三個引號的的時候會嘗試再尋找三個終止引號作為定界符, 如果不存在則會導致 `SyntaxError` 異常.

---

### > Midnight time doesn't exist?/不存在的午夜?

```py
from datetime import datetime

midnight = datetime(2018, 1, 1, 0, 0)
midnight_time = midnight.time()

noon = datetime(2018, 1, 1, 12, 0)
noon_time = noon.time()

if midnight_time:
    print("Time at midnight is", midnight_time)

if noon_time:
    print("Time at noon is", noon_time)
```

**Output:**
```sh
('Time at noon is', datetime.time(12, 0))
```

midnight_time 並沒有被輸出.

#### 💡 說明:

在Python 3.5之前, 如果 `datetime.time` 對像存儲的UTC的午夜時間(譯: 就是 `00:00`), 那麼它的布爾值會被認為是 `False`. 當使用 `if obj:` 語句來檢查 `obj` 是否為 `null` 或者某些“空”值的時候, 很容易出錯.

---

### > What's wrong with booleans?/布爾你怎麼了?

1\.
```py
# 一個簡單的例子, 統計下面可迭代對像中的布爾型值的個數和整型值的個數
mixed_list = [False, 1.0, "some_string", 3, True, [], False]
integers_found_so_far = 0
booleans_found_so_far = 0

for item in mixed_list:
    if isinstance(item, int):
        integers_found_so_far += 1
    elif isinstance(item, bool):
        booleans_found_so_far += 1
```

**Output:**
```py
>>> integers_found_so_far
4
>>> booleans_found_so_far
0
```

2\.
```py
another_dict = {}
another_dict[True] = "JavaScript"
another_dict[1] = "Ruby"
another_dict[1.0] = "Python"
```

**Output:**
```py
>>> another_dict[True]
"Python"
```

3\.
```py
>>> some_bool = True
>>> "wtf"*some_bool
'wtf'
>>> some_bool = False
>>> "wtf"*some_bool
''
```

#### 💡 說明:

* 布爾值是 `int` 的子類
  ```py
  >>> isinstance(True, int)
  True
  >>> isinstance(False, int)
  True
  ```

* 所以 `True` 的整數值是 `1`, 而 `False` 的整數值是 `0`.
  ```py
  >>> True == 1 == 1.0 and False == 0 == 0.0
  True
  ```

* 關於其背後的原理, 請看這個 StackOverflow 的[回答](https://stackoverflow.com/a/8169049/4354153).

---

### > Class attributes and instance attributes/類屬性和實例屬性

1\.
```py
class A:
    x = 1

class B(A):
    pass

class C(A):
    pass
```

**Output:**
```py
>>> A.x, B.x, C.x
(1, 1, 1)
>>> B.x = 2
>>> A.x, B.x, C.x
(1, 2, 1)
>>> A.x = 3
>>> A.x, B.x, C.x
(3, 2, 3)
>>> a = A()
>>> a.x, A.x
(3, 3)
>>> a.x += 1
>>> a.x, A.x
(4, 3)
```

2\.
```py
class SomeClass:
    some_var = 15
    some_list = [5]
    another_list = [5]
    def __init__(self, x):
        self.some_var = x + 1
        self.some_list = self.some_list + [x]
        self.another_list += [x]
```

**Output:**

```py
>>> some_obj = SomeClass(420)
>>> some_obj.some_list
[5, 420]
>>> some_obj.another_list
[5, 420]
>>> another_obj = SomeClass(111)
>>> another_obj.some_list
[5, 111]
>>> another_obj.another_list
[5, 420, 111]
>>> another_obj.another_list is SomeClass.another_list
True
>>> another_obj.another_list is some_obj.another_list
True
```

#### 💡 說明:

* 類變量和實例變量在內部是通過類對像的字典來處理(譯: 就是 `__dict__` 屬性). 如果在當前類的字典中找不到的話就去它的父類中尋找.
* `+=` 運算符會在原地修改可變對像, 而不是創建新對像. 因此, 修改一個實例的屬性會影響其他實例和類屬性.

---

### > yielding None/生成 None

```py
some_iterable = ('a', 'b')

def some_func(val):
    return "something"
```

**Output:**
```py
>>> [x for x in some_iterable]
['a', 'b']
>>> [(yield x) for x in some_iterable]
<generator object <listcomp> at 0x7f70b0a4ad58>
>>> list([(yield x) for x in some_iterable])
['a', 'b']
>>> list((yield x) for x in some_iterable)
['a', None, 'b', None]
>>> list(some_func((yield x)) for x in some_iterable)
['a', 'something', 'b', 'something']
```

#### 💡 說明:
- 來源和解釋可以在這裡找到: https://stackoverflow.com/questions/32139885/yield-in-list-comprehensions-and-generator-expressions
- 相關錯誤報告: http://bugs.python.org/issue10544

---

### > Mutating the immutable!/強人所難

```py
some_tuple = ("A", "tuple", "with", "values")
another_tuple = ([1, 2], [3, 4], [5, 6])
```

**Output:**
```py
>>> some_tuple[2] = "change this"
TypeError: 'tuple' object does not support item assignment
>>> another_tuple[2].append(1000) # 這裡不出現錯誤
>>> another_tuple
([1, 2], [3, 4], [5, 6, 1000])
>>> another_tuple[2] += [99, 999]
TypeError: 'tuple' object does not support item assignment
>>> another_tuple
([1, 2], [3, 4], [5, 6, 1000, 99, 999])
```

我還以為元組是不可變的呢...

#### 💡 說明:

* 引用 https://docs.python.org/2/reference/datamodel.html

    > 不可變序列
        不可變序列的對像一旦創建就不能再改變. (如果對像包含對其他對像的引用，則這些其他對像可能是可變的並且可能會被修改; 但是，由不可變對像直接引用的對像集合不能更改.)

* `+=` 操作符在原地修改了列表. 元素賦值操作並不工作, 但是當異常拋出時, 元素已經在原地被修改了.

(譯: 對於不可變對像, 這裡指tuple, `+=` 並不是原子操作, 而是 `extend` 和 `=` 兩個動作, 這裡 `=` 操作雖然會拋出異常, 但 `extend` 操作已經修改成功了. 詳細解釋可以看[這裡](https://segmentfault.com/a/1190000010767068))

---

### > The disappearing variable from outer scope/消失的外部變量

```py
e = 7
try:
    raise Exception()
except Exception as e:
    pass
```

**Output (Python 2.x):**
```py
>>> print(e)
# prints nothing
```

**Output (Python 3.x):**
```py
>>> print(e)
NameError: name 'e' is not defined
```

#### 💡 說明:

* 出處: https://docs.python.org/3/reference/compound_stmts.html#except

  當使用 `as` 為目標分配異常的時候, 將在except子句的末尾清除該異常.

  這就好像

  ```py
  except E as N:
      foo
  ```

  會被翻譯成

  ```py
  except E as N:
      try:
          foo
      finally:
          del N
  ```

  這意味著異常必須在被賦值給其他變量才能在 `except` 子句之後引用它. 而異常之所以會被清除, 則是由於上面附加的回溯信息(trackback)會和棧幀(stack frame)形成循環引用, 使得該棧幀中的所有本地變量在下一次垃圾回收發生之前都處於活動狀態.(譯: 也就是說不會被回收)

* 子句在 Python 中並沒有獨立的作用域. 示例中的所有內容都處於同一作用域內, 所以變量 `e` 會由於執行了 `except` 子句而被刪除. 而對於有獨立的內部作用域的函數來說情況就不一樣了. 下面的例子說明了這一點:

     ```py
     def f(x):
         del(x)
         print(x)

     x = 5
     y = [5, 4, 3]
     ```

     **Output:**
     ```py
     >>>f(x)
     UnboundLocalError: local variable 'x' referenced before assignment
     >>>f(y)
     UnboundLocalError: local variable 'x' referenced before assignment
     >>> x
     5
     >>> y
     [5, 4, 3]
     ```

* 在 Python 2.x 中, `Exception()` 實例被賦值給了變量 `e`, 所以當你嘗試打印結果的時候, 它的輸出為空.（譯: 正常的Exception實例打印出來就是空）

    **Output (Python 2.x):**
    ```py
    >>> e
    Exception()
    >>> print e
    # 沒有打印任何內容!
    ```

---

### > When True is actually False/真亦假

```py
True = False
if True == False:
    print("I've lost faith in truth!")
```

**Output:**
```
I've lost faith in truth!
```

#### 💡 說明:

- 最初, Python 並沒有 `bool` 型 (人們用0表示假值, 用非零值比如1作為真值). 後來他們添加了 `True`, `False`, 和 `bool` 型, 但是, 為了向後兼容, 他們沒法把 `True` 和 `False` 設置為常量, 只是設置成了內置變量.
- Python 3 由於不再需要向後兼容, 終於可以修復這個問題了, 所以這個例子無法在 Python 3.x 中執行!

---

### > From filled to None in one instruction.../從有到無...

```py
some_list = [1, 2, 3]
some_dict = {
  "key_1": 1,
  "key_2": 2,
  "key_3": 3
}

some_list = some_list.append(4)
some_dict = some_dict.update({"key_4": 4})
```

**Output:**
```py
>>> print(some_list)
None
>>> print(some_dict)
None
```

#### 💡 說明:

大多數修改序列/映射對像的方法, 比如 `list.append`, `dict.update`, `list.sort` 等等. 都是原地修改對像並返回 `None`. 這樣做的理由是, 如果操作可以原地完成, 就可以避免創建對像的副本來提高性能. (參考[這裡](http://docs.python.org/2/faq/design.html#why-doesn-t-list-sort-return-the-sorted-list))

---

### > Subclass relationships/子類關系 *

**Output:**
```py
>>> from collections import Hashable
>>> issubclass(list, object)
True
>>> issubclass(object, Hashable)
True
>>> issubclass(list, Hashable)
False
```

子類關系應該是可傳遞的, 對吧? (即, 如果 `A` 是 `B` 的子類, `B` 是 `C` 的子類, 那麼 `A` _應該_ 是 `C` 的子類.)

#### 💡 說明:

* Python 中的子類關系並不必須是傳遞的. 任何人都可以在元類中隨意定義 `__subclasscheck__`.
* 當 `issubclass(cls, Hashable)` 被調用時, 它只是在 `cls` 中尋找 "`__hash__`" 方法或繼承自"`__hash__`"的方法.
* 由於 `object` is 可散列的(hashable), 但是 `list` 是不可散列的, 所以它打破了這種傳遞關系.
* 在[這裡](https://www.naftaliharris.com/blog/python-subclass-intransitivity/)可以找到更詳細的解釋.

---

### > The mysterious key type conversion/神秘的鍵型轉換 *

```py
class SomeClass(str):
    pass

some_dict = {'s':42}
```

**Output:**
```py
>>> type(list(some_dict.keys())[0])
str
>>> s = SomeClass('s')
>>> some_dict[s] = 40
>>> some_dict # 預期: 兩個不同的鍵值對
{'s': 40}
>>> type(list(some_dict.keys())[0])
str
```

#### 💡 說明:

* 由於 `SomeClass` 會從 `str` 自動繼承 `__hash__` 方法, 所以 `s` 對像和 `"s"` 字串的哈希值是相同的.
* 而 `SomeClass("s") == "s"` 為 `True` 是因為 `SomeClass` 也繼承了 `str` 類 `__eq__` 方法.
* 由於兩者的哈希值相同且相等, 所以它們在字典中表示相同的鍵.
* 如果想要實現期望的功能, 我們可以重定義 `SomeClass` 的 `__eq__` 方法.
  ```py
  class SomeClass(str):
    def __eq__(self, other):
        return (
            type(self) is SomeClass
            and type(other) is SomeClass
            and super().__eq__(other)
        )

    # 當我們自定義 __eq__ 方法時, Python 不會再自動繼承 __hash__ 方法
    # 所以我們也需要定義它
    __hash__ = str.__hash__

  some_dict = {'s':42}
  ```

  **Output:**
  ```py
  >>> s = SomeClass('s')
  >>> some_dict[s] = 40
  >>> some_dict
  {'s': 40, 's': 42}
  >>> keys = list(some_dict.keys())
  >>> type(keys[0]), type(keys[1])
  (__main__.SomeClass, str)
  ```

---

### > Let's see if you can guess this?/看看你能否猜到這一點?

```py
a, b = a[b] = {}, 5
```

**Output:**
```py
>>> a
{5: ({...}, 5)}
```

#### 💡 說明:

* 根據 [Python 語言參考](https://docs.python.org/2/reference/simple_stmts.html#assignment-statements), 賦值語句的形式如下
  ```
  (target_list "=")+ (expression_list | yield_expression)
  ```

  > 賦值語句計算表達式列表(expression list)(牢記 這可以是單個表達式或以逗號分隔的列表, 後者返回元組)並將單個結果對像從左到右分配給目標列表中的每一項.

*  `(target_list "=")+` 中的 `+` 意味著可以有**一個或多個**目標列表. 在這個例子中, 目標列表是 `a, b` 和 `a[b]` (注意表達式列表只能有一個, 在我們的例子中是 `{}, 5`).

* 表達式列表計算結束後, 將其值自動解包後**從左到右**分配給目標列表(target list). 因此, 在我們的例子中, 首先將 `{}, 5` 元組並賦值給 `a, b`, 然後我們就可以得到 `a = {}` 且 `b = 5`.

* `a` 被賦值的 `{}` 是可變對像.

* 第二個目標列表是 `a[b]` (你可能覺得這裡會報錯, 因為在之前的語句中 `a` 和 `b` 都還沒有被定義. 但是別忘了, 我們剛剛將 `a` 賦值 `{}` 且將 `b` 賦值為 `5`).

* 現在, 我們將通過將字典中鍵 `5` 的值設置為元組 `({}, 5)` 來創建循環引用 (輸出中的 `{...}` 指與 `a` 引用了相同的對像). 下面是一個更簡單的循環引用的例子
  ```py
  >>> some_list = some_list[0] = [0]
  >>> some_list
  [[...]]
  >>> some_list[0]
  [[...]]
  >>> some_list is some_list[0]
  True
  >>> some_list[0][0][0][0][0][0] == some_list
  True
  ```
  我們的例子就是這種情況 (`a[b][0]` 與 `a` 是相同的對像)

* 總結一下, 你也可以把例子拆成
  ```py
  a, b = {}, 5
  a[b] = a, b
  ```
  並且可以通過 `a[b][0]` 與 `a` 是相同的對像來證明是循環引用
  ```py
  >>> a[b][0] is a
  True
  ```

---

---

## Section: Appearances are deceptive!/外表是靠不住的!

### > Skipping lines?/跳過一行?

**Output:**
```py
>>> value = 11
>>> valuｅ = 32
>>> value
11
```

什麼鬼?

**注意:** 如果你想要重現的話最簡單的方法是直接復制上面的代碼片段到你的文件或命令行裡.

#### 💡 說明:

一些非西方字符雖然看起來和英語字母相同, 但會被解釋器識別為不同的字母.

```py
>>> ord('ｅ') # 西裡爾語的 'e' (Ye)
1077
>>> ord('e') # 拉丁語的 'e', 用於英文並使用標准鍵盤輸入
101
>>> 'ｅ' == 'e'
False

>>> value = 42 # 拉丁語 e
>>> valuｅ = 23 # 西裡爾語 'e', Python 2.x 的解釋器在這會拋出 `SyntaxError` 異常
>>> value
42
```

內置的 `ord()` 函數可以返回一個字符的 Unicode [代碼點](https://en.wikipedia.org/wiki/Code_point), 這裡西裡爾語 'e' 和拉丁語 'e' 的代碼點不同證實了上述例子.

---

### > Teleportation/空間移動 *

```py
import numpy as np

def energy_send(x):
    # 初始化一個 numpy 數組
    np.array([float(x)])

def energy_receive():
    # 返回一個空的 numpy 數組
    return np.empty((), dtype=np.float).tolist()
```

**Output:**
```py
>>> energy_send(123.456)
>>> energy_receive()
123.456
```

誰來給我發個諾貝爾獎?

#### 💡 說明:

* 注意在 `energy_send` 函數中創建的 numpy 數組並沒有返回, 因此內存空間被釋放並可以被重新分配.
* `numpy.empty()` 直接返回下一段空閑內存，而不重新初始化. 而這個內存點恰好就是剛剛釋放的那個(通常情況下, 並不絕對).

---

### > Well, something is fishy.../嗯，有些可疑...

```py
def square(x):
    """
    一個通過加法計算平方的簡單函數.
    """
    sum_so_far = 0
    for counter in range(x):
        sum_so_far = sum_so_far + x
  return sum_so_far
```

**Output (Python 2.x):**

```py
>>> square(10)
10
```

難道不應該是100嗎?

**注意:** 如果你無法重現, 可以嘗試運行這個文件[mixed_tabs_and_spaces.py](/mixed_tabs_and_spaces.py).

#### 💡 說明:

* **不要混用制表符(tab)和空格(space)!** 在上面的例子中, return 的前面是"1個制表符", 而其他部分的代碼前面是 "4個空格".
* Python是這麼處理制表符的:
  > 首先, 制表符會從左到右依次被替換成8個空格, 直到被替換後的字符總數是八的倍數 <...>
* 因此, `square` 函數最後一行的制表符會被替換成8個空格, 導致return語句進入循環語句裡面.
* Python 3 很友好, 在這種情況下會自動拋出錯誤.

    **Output (Python 3.x):**
    ```py
    TabError: inconsistent use of tabs and spaces in indentation
    ```

---

---

## Section: Watch out for the landmines!/小心地雷!


### > Modifying a dictionary while iterating over it/迭代字典時的修改

```py
x = {0: None}

for i in x:
    del x[i]
    x[i+1] = None
    print(i)
```

**Output (Python 2.7- Python 3.5):**

```
0
1
2
3
4
5
6
7
```

是的, 它運行了**八次**然後才停下來.

#### 💡 說明:

* Python不支持對字典進行迭代的同時修改它.
* 它之所以運行8次, 是因為字典會自動擴容以容納更多鍵值(我們有8次刪除記錄, 因此需要擴容). 這實際上是一個實現細節. (譯: 應該是因為字典的初始最小值是8, 擴容會導致散列表地址發生變化而中斷循環.)
* 在不同的Python實現中刪除鍵的處理方式以及調整大小的時間可能會有所不同.(譯: 就是說什麼時候擴容在不同版本中可能是不同的, 在3.6及3.7的版本中到[5](https://github.com/python/cpython/blob/v3.6.1/Objects/dictobject.c#L103-L110)就會自動擴容了. 以後也有可能再次發生變化. 順帶一提,後面兩次擴容會擴展為32和256. 8->32->256)
* 更多的信息, 你可以參考這個StackOverflow的[回答](https://stackoverflow.com/questions/44763802/bug-in-python-dict), 它詳細的解釋一個類似的例子.

---

### > Stubborn `del` operator/堅強的 `del` *

```py
class SomeClass:
    def __del__(self):
        print("Deleted!")
```

**Output:**
1\.
```py
>>> x = SomeClass()
>>> y = x
>>> del x # 這裡應該會輸出 "Deleted!"
>>> del y
Deleted!
```

唷, 終於刪除了. 你可能已經猜到了在我們第一次嘗試刪除 `x` 時是什麼讓 `__del__` 免於被調用的. 那讓我們給這個例子增加點難度.

2\.
```py
>>> x = SomeClass()
>>> y = x
>>> del x
>>> y # 檢查一下y是否存在
<__main__.SomeClass instance at 0x7f98a1a67fc8>
>>> del y # 像之前一樣, 這裡應該會輸出 "Deleted!"
>>> globals() # 好吧, 並沒有. 讓我們看一下所有的全局變量
Deleted!
{'__builtins__': <module '__builtin__' (built-in)>, 'SomeClass': <class __main__.SomeClass at 0x7f98a1a5f668>, '__package__': None, '__name__': '__main__', '__doc__': None}
```

好了，現在它被刪除了 :confused:

#### 💡 說明:
+ `del x` 並不會立刻調用 `x.__del__()`.
+ 每當遇到 `del x`, Python 會將 `x` 的引用數減1, 當 `x` 的引用數減到0時就會調用 `x.__del__()`.
+ 在第二個例子中, `y.__del__()` 之所以未被調用, 是因為前一條語句 (`>>> y`) 對同一對像創建了另一個引用, 從而防止在執行 `del y` 後對像的引用數變為0.
+ 調用 `globals` 導致引用被銷毀, 因此我們可以看到 "Deleted!" 終於被輸出了.
+ (譯: 這其實是 Python 交互解釋器的特性, 它會自動讓 `_` 保存上一個表達式輸出的值, 詳細可以看[這裡](https://www.cnblogs.com/leisurelylicht/p/diao-pi-de-kong-zhi-tai.html).)

---

### > Deleting a list item while iterating/迭代列表時刪除元素

```py
list_1 = [1, 2, 3, 4]
list_2 = [1, 2, 3, 4]
list_3 = [1, 2, 3, 4]
list_4 = [1, 2, 3, 4]

for idx, item in enumerate(list_1):
    del item

for idx, item in enumerate(list_2):
    list_2.remove(item)

for idx, item in enumerate(list_3[:]):
    list_3.remove(item)

for idx, item in enumerate(list_4):
    list_4.pop(idx)
```

**Output:**
```py
>>> list_1
[1, 2, 3, 4]
>>> list_2
[2, 4]
>>> list_3
[]
>>> list_4
[2, 4]
```

你能猜到為什麼輸出是 `[2, 4]` 嗎?

#### 💡 說明:

* 在迭代時修改對像是一個很愚蠢的主意. 正確的做法是迭代對像的副本, `list_3[:]` 就是這麼做的.

     ```py
     >>> some_list = [1, 2, 3, 4]
     >>> id(some_list)
     139798789457608
     >>> id(some_list[:]) # 注意python為切片列表創建了新對像.
     139798779601192
     ```

**`del`, `remove` 和 `pop` 的不同:**
* `del var_name` 只是從本地或全局命名空間中刪除了 `var_name` (這就是為什麼 `list_1` 沒有受到影響).
* `remove` 會刪除第一個匹配到的指定值, 而不是特定的索引, 如果找不到值則拋出 `ValueError` 異常.
* `pop` 則會刪除指定索引處的元素並返回它, 如果指定了無效的索引則拋出 `IndexError` 異常.

**為什麼輸出是 `[2, 4]`?**
- 列表迭代是按索引進行的, 所以當我們從 `list_2` 或 `list_4` 中刪除 `1` 時, 列表的內容就變成了 `[2, 3, 4]`. 剩余元素會依次位移, 也就是說, `2` 的索引會變為 0, `3` 會變為 1. 由於下一次迭代將獲取索引為 1 的元素 (即 `3`), 因此 `2` 將被徹底的跳過. 類似的情況會交替發生在列表中的每個元素上.

* 參考這個StackOverflow的[回答](https://stackoverflow.com/questions/45946228/what-happens-when-you-try-to-delete-a-list-element-while-iterating-over-it)來解釋這個例子
* 關於Python中字典的類似例子, 可以參考這個Stackoverflow的[回答](https://stackoverflow.com/questions/45877614/how-to-change-all-the-dictionary-keys-in-a-for-loop-with-d-items).

---

### > Loop variables leaking out!/循環變量泄漏!

1\.
```py
for x in range(7):
    if x == 6:
        print(x, ': for x inside loop')
print(x, ': x in global')
```

**Output:**
```py
6 : for x inside loop
6 : x in global
```

但是 `x` 從未在循環外被定義...

2\.
```py
# 這次我們先初始化x
x = -1
for x in range(7):
    if x == 6:
        print(x, ': for x inside loop')
print(x, ': x in global')
```

**Output:**
```py
6 : for x inside loop
6 : x in global
```

3\.
```
x = 1
print([x for x in range(5)])
print(x, ': x in global')
```

**Output (on Python 2.x):**
```
[0, 1, 2, 3, 4]
(4, ': x in global')
```

**Output (on Python 3.x):**
```
[0, 1, 2, 3, 4]
1 : x in global
```

#### 💡 說明:

- 在 Python 中, for 循環使用所在作用域並在結束後保留定義的循環變量. 如果我們曾在全局命名空間中定義過循環變量. 在這種情況下, 它會重新綁定現有變量.

- Python 2.x 和 Python 3.x 解釋器在列表推導式示例中的輸出差異, 在文檔 [What’s New In Python 3.0](https://docs.python.org/3/whatsnew/3.0.html) 中可以找到相關的解釋:

    > "列表推導不再支持句法形式 `[... for var in item1, item2, ...]`. 取而代之的是 `[... for var in (item1, item2, ...)]`. 另外, 注意列表推導具有不同的語義: 它們更接近於 `list()` 構造函數中生成器表達式的語法糖(譯: 這一句我也不是很明白), 特別是循環控制變量不再泄漏到周圍的作用域中."

---

### > Beware of default mutable arguments!/當心默認的可變參數!

```py
def some_func(default_arg=[]):
    default_arg.append("some_string")
    return default_arg
```

**Output:**
```py
>>> some_func()
['some_string']
>>> some_func()
['some_string', 'some_string']
>>> some_func([])
['some_string']
>>> some_func()
['some_string', 'some_string', 'some_string']
```

#### 💡 說明:

- Python中函數的默認可變參數並不是每次調用該函數時都會被初始化. 相反, 它們會使用最近分配的值作為默認值. 當我們明確的將 `[]` 作為參數傳遞給 `some_func` 的時候, 就不會使用 `default_arg` 的默認值, 所以函數會返回我們所期望的結果.

    ```py
    def some_func(default_arg=[]):
        default_arg.append("some_string")
        return default_arg
    ```

    **Output:**
    ```py
    >>> some_func.__defaults__ # 這裡會顯示函數的默認參數的值
    ([],)
    >>> some_func()
    >>> some_func.__defaults__
    (['some_string'],)
    >>> some_func()
    >>> some_func.__defaults__
    (['some_string', 'some_string'],)
    >>> some_func([])
    >>> some_func.__defaults__
    (['some_string', 'some_string'],)
    ```

- 避免可變參數導致的錯誤的常見做法是將 `None` 指定為參數的默認值, 然後檢查是否有值傳給對應的參數. 例:

    ```py
    def some_func(default_arg=None):
        if not default_arg:
            default_arg = []
        default_arg.append("some_string")
        return default_arg
    ```

---

### > Catching the Exceptions/捕獲異常

```py
some_list = [1, 2, 3]
try:
    # 這裡會拋出異常 ``IndexError``
    print(some_list[4])
except IndexError, ValueError:
    print("Caught!")

try:
    # 這裡會拋出異常 ``ValueError``
    some_list.remove(4)
except IndexError, ValueError:
    print("Caught again!")
```

**Output (Python 2.x):**
```py
Caught!

ValueError: list.remove(x): x not in list
```

**Output (Python 3.x):**
```py
  File "<input>", line 3
    except IndexError, ValueError:
                     ^
SyntaxError: invalid syntax
```

#### 💡 說明:

* 如果你想要同時捕獲多個不同類型的異常時, 你需要將它們用括號包成一個元組作為第一個參數傳遞. 第二個參數是可選名稱, 如果你提供, 它將與被捕獲的異常實例綁定. 例,
  ```py
  some_list = [1, 2, 3]
  try:
     # 這裡會拋出異常 ``ValueError``
     some_list.remove(4)
  except (IndexError, ValueError), e:
     print("Caught again!")
     print(e)
  ```
  **Output (Python 2.x):**
  ```
  Caught again!
  list.remove(x): x not in list
  ```
  **Output (Python 3.x):**
  ```py
    File "<input>", line 4
      except (IndexError, ValueError), e:
                                       ^
  IndentationError: unindent does not match any outer indentation level
  ```

* 在 Python 3 中, 用逗號區分異常與可選名稱是無效的; 正確的做法是使用 `as` 關鍵字. 例,
  ```py
  some_list = [1, 2, 3]
  try:
      some_list.remove(4)

  except (IndexError, ValueError) as e:
      print("Caught again!")
      print(e)
  ```
  **Output:**
  ```
  Caught again!
  list.remove(x): x not in list
  ```

---

### > Same operands, different story!/同人不同命!

1\.
```py
a = [1, 2, 3, 4]
b = a
a = a + [5, 6, 7, 8]
```

**Output:**
```py
>>> a
[1, 2, 3, 4, 5, 6, 7, 8]
>>> b
[1, 2, 3, 4]
```

2\.
```py
a = [1, 2, 3, 4]
b = a
a += [5, 6, 7, 8]
```

**Output:**
```py
>>> a
[1, 2, 3, 4, 5, 6, 7, 8]
>>> b
[1, 2, 3, 4, 5, 6, 7, 8]
```

#### 💡 說明:

*  `a += b` 並不總是與 `a = a + b` 表現相同. 類實現 *`op=`* 運算符的方式 *也許* 是不同的, 列表就是這樣做的.

* 表達式 `a = a + [5,6,7,8]` 會生成一個新列表, 並讓 `a` 引用這個新列表, 同時保持 `b` 不變.

* 表達式 `a += [5,6,7,8]` 實際上是使用的是 "extend" 函數, 所以 `a` 和 `b` 仍然指向已被修改的同一列表.

---

### > The out of scope variable/外部作用域變量

```py
a = 1
def some_func():
    return a

def another_func():
    a += 1
    return a
```

**Output:**
```py
>>> some_func()
1
>>> another_func()
UnboundLocalError: local variable 'a' referenced before assignment
```

#### 💡 說明:
* 當你在作用域中對變量進行賦值時, 變量會變成該作用域內的局部變量. 因此 `a` 會變成 `another_func` 函數作用域中的局部變量, 但它在函數作用域中並沒有被初始化, 所以會引發錯誤.
* 可以閱讀[這個](http://sebastianraschka.com/Articles/2014_python_scope_and_namespaces.html)簡短卻很棒的指南, 了解更多關於 Python 中命名空間和作用域的工作原理.
* 想要在 `another_func` 中修改外部作用域變量 `a` 的話, 可以使用 `global` 關鍵字.
  ```py
  def another_func()
      global a
      a += 1
      return a
  ```

  **Output:**
  ```py
  >>> another_func()
  2
  ```

---

### > Be careful with chained operations/小心鏈式操作

```py
>>> (False == False) in [False] # 可以理解
False
>>> False == (False in [False]) # 可以理解
False
>>> False == False in [False] # 為毛?
True

>>> True is False == False
False
>>> False is False is False
True

>>> 1 > 0 < 1
True
>>> (1 > 0) < 1
False
>>> 1 > (0 < 1)
False
```

#### 💡 說明:

根據 https://docs.python.org/2/reference/expressions.html#not-in

> 形式上, 如果 a, b, c, ..., y, z 是表達式, 而 op1, op2, ..., opN 是比較運算符, 那麼除了每個表達式最多只出現一次以外 a op1 b op2 c ... y opN z 就等於 a op1 b and b op2 c and ... y opN z.

雖然上面的例子似乎很愚蠢, 但是像 `a == b == c` 或 `0 <= x <= 100` 就很棒了.

* `False is False is False` 相當於 `(False is False) and (False is False)`
* `True is False == False` 相當於 `True is False and False == False`, 由於語句的第一部分 (`True is False`) 等於 `False`, 因此整個表達式的結果為 `False`.
* `1 > 0 < 1` 相當於 `1 > 0 and 0 < 1`, 所以最終結果為 `True`.
* 表達式 `(1 > 0) < 1` 相當於 `True < 1` 且
  ```py
  >>> int(True)
  1
  >>> True + 1 # 與這個例子無關，只是好玩
  2
  ```
  所以, `1 < 1` 等於 `False`

---

### > Name resolution ignoring class scope/忽略類作用域的名稱解析

1\.
```py
x = 5
class SomeClass:
    x = 17
    y = (x for i in range(10))
```

**Output:**
```py
>>> list(SomeClass.y)[0]
5
```

2\.
```py
x = 5
class SomeClass:
    x = 17
    y = [x for i in range(10)]
```

**Output (Python 2.x):**
```py
>>> SomeClass.y[0]
17
```

**Output (Python 3.x):**
```py
>>> SomeClass.y[0]
5
```

#### 💡 說明:
- 類定義中嵌套的作用域會忽略類內的名稱綁定.
- 生成器表達式有它自己的作用域.
- 從 Python 3.X 開始, 列表推導式也有自己的作用域.

---

### > Needle in a Haystack/大海撈針

1\.
```py
x, y = (0, 1) if True else None, None
```

**Output:**
```
>>> x, y  # 期望的結果是 (0, 1)
((0, 1), None)
```

幾乎每個 Python 程序員都遇到過類似的情況.

2\.
```py
t = ('one', 'two')
for i in t:
    print(i)

t = ('one')
for i in t:
    print(i)

t = ()
print(t)
```

**Output:**
```py
one
two
o
n
e
tuple()
```

#### 💡 說明:
* 對於 1, 正確的語句是 `x, y = (0, 1) if True else (None, None)`.
* 對於 2, 正確的語句是 `t = ('one',)` 或者 `t = 'one',` (缺少逗號) 否則解釋器會認為 `t` 是一個字串, 並逐個字符對其進行迭代.
* `()` 是一個特殊的標記，表示空元組.

---

---


## Section: The Hidden treasures!/隱藏的寶藏!

This section contains few of the lesser-known interesting things about Python that most beginners like me are unaware of (well, not anymore).

### > Okay Python, Can you make me fly?/Python, 可否帶我飛? *

好, 去吧.

```py
import antigravity
```

**Output:**
噓.. 這是個超級秘密.

#### 💡 說明:
+ `antigravity` 模塊是 Python 開發人員發布的少數復活節彩蛋之一.
+ `import antigravity` 會打開一個 Python 的[經典 XKCD 漫畫](http://xkcd.com/353/)頁面.
+ 不止如此. 這個**復活節彩蛋裡還有一個復活節彩蛋**. 如果你看一下[代碼](https://github.com/python/cpython/blob/master/Lib/antigravity.py#L7-L17), 就會發現還有一個函數實現了 [XKCD's geohashing 算法](https://xkcd.com/426/).

---

### > `goto`, but why?/`goto`, 但為什麼? *

```py
from goto import goto, label
for i in range(9):
    for j in range(9):
        for k in range(9):
            print("I'm trapped, please rescue!")
            if k == 2:
                goto .breakout # 從多重循環中跳出
label .breakout
print("Freedom!")
```

**Output (Python 2.3):**
```py
I'm trapped, please rescue!
I'm trapped, please rescue!
Freedom!
```

#### 💡 說明:
- 2004年4月1日, Python [宣布](https://mail.python.org/pipermail/python-announce-list/2004-April/002982.html) 加入一個可用的 `goto` 作為愚人節禮物.
- 當前版本的 Python 並沒有這個模塊.
- 就算可以用, 也請不要使用它. 這裡是為什麼Python中沒有 `goto` 的[原因](https://docs.python.org/3/faq/design.html#why-is-there-no-goto).

---

### > Brace yourself!/做好思想准備 *

如果你不喜歡在Python中使用空格來表示作用域, 你可以導入 C 風格的 {},

```py
from __future__ import braces
```

**Output:**
```py
  File "some_file.py", line 1
    from __future__ import braces
SyntaxError: not a chance
```

想用大括號? 沒門! 覺得不爽, 請去用java.

#### 💡 說明:
+ 通常 `__future__` 會提供 Python 未來版本的功能. 然而，這裡的 “未來” 是一個諷刺.
+ 這是一個表達社區對此類問題態度的復活節彩蛋.

---

### > Let's meet Friendly Language Uncle For Life/讓生活更友好 *

**Output (Python 3.x)**
```py
>>> from __future__ import barry_as_FLUFL
>>> "Ruby" != "Python" # 這裡沒什麼疑問
  File "some_file.py", line 1
    "Ruby" != "Python"
              ^
SyntaxError: invalid syntax

>>> "Ruby" <> "Python"
True
```

這就對了.

#### 💡 說明:
- 相關的 [PEP-401](https://www.python.org/dev/peps/pep-0401/) 發布於 2009年4月1日 (所以你現在知道這意味著什麼了吧).
- 引用 PEP-401
  > 意識到 Python 3.0 裡的 != 運算符是一個會引起手指疼痛的恐怖錯誤, FLUFL 將 <> 運算符恢復為唯一寫法.
- Uncle Barry 在 PEP 中還分享了其他東西; 你可以在[這裡](https://www.python.org/dev/peps/pep-0401/)獲得他們.
- (譯: 雖然文檔中沒寫，但應該是只能在交互解釋器中使用.)
---

### > Even Python understands that love is complicated/連 Python 也知道愛是難言的 *

```py
import this
```

等等, **this** 是什麼? `this` 是愛 :heart:

**Output:**
```
The Zen of Python, by Tim Peters

Beautiful is better than ugly.
優美勝於醜陋（Python 以編寫優美的代碼為目標）
Explicit is better than implicit.
明了勝於晦澀（優美的代碼應當是明了的，命名規範，風格相似）
Simple is better than complex.
簡潔勝於復雜（優美的代碼應當是簡潔的，不要有復雜的內部實現）
Complex is better than complicated.
復雜勝於凌亂（如果復雜不可避免，那代碼間也不能有難懂的關系，要保持接口簡潔）
Flat is better than nested.
扁平勝於嵌套（優美的代碼應當是扁平的，不能有太多的嵌套）
Sparse is better than dense.
間隔勝於緊湊（優美的代碼有適當的間隔，不要奢望一行代碼解決問題）
Readability counts.
可讀性很重要（優美的代碼一定是可讀的）
Special cases aren't special enough to break the rules.
沒有特例特殊到需要違背這些規則（這些規則至高無上）
Although practicality beats purity.
盡管我們更傾向於實用性
Errors should never pass silently.
不要安靜的包容所有錯誤
Unless explicitly silenced.
除非你確定需要這樣做（精准地捕獲異常，不寫 except:pass 風格的代碼）
In the face of ambiguity, refuse the temptation to guess.
拒絕誘惑你去猜測的曖昧事物
There should be one-- and preferably only one --obvious way to do it.
而是盡量找一種，最好是唯一一種明顯的解決方案（如果不確定，就用窮舉法）
Although that way may not be obvious at first unless you're Dutch.
雖然這並不容易，因為你不是 Python 之父（這裡的 Dutch 是指 Guido ）
Now is better than never.
現在行動好過永遠不行動
Although never is often better than *right* now.
盡管不行動要好過魯莽行動
If the implementation is hard to explain, it's a bad idea.
如果你無法向人描述你的方案，那肯定不是一個好方案；
If the implementation is easy to explain, it may be a good idea.
如果你能輕松向人描述你的方案，那也許會是一個好方案（方案測評標准）
Namespaces are one honking great idea -- let's do more of those!
命名空間是一種絕妙的理念，我們應當多加利用（倡導與號召）
```

這是 Python 之禪!

```py
>>> love = this
>>> this is love
True
>>> love is True
False
>>> love is False
False
>>> love is not True or False
True
>>> love is not True or False; love is love  # 愛是難言的
True
```

#### 💡 說明:

* `this` 模塊是關於 Python 之禪的復活節彩蛋 ([PEP 20](https://www.python.org/dev/peps/pep-0020)).
* 如果你認為這已經夠有趣的了, 可以看看 [this.py](https://hg.python.org/cpython/file/c3896275c0f6/Lib/this.py) 的實現. 有趣的是, Python 之禪的實現代碼違反了他自己 (這可能是唯一會發生這種情況的地方).
*
至於 `love is not True or False; love is love`, 意外卻又不言而喻.

---

### > Yes, it exists!/是的, 它存在!

**循環的 `else`.** 一個典型的例子:

```py
  def does_exists_num(l, to_find):
      for num in l:
          if num == to_find:
              print("Exists!")
              break
      else:
          print("Does not exist")
```

**Output:**
```py
>>> some_list = [1, 2, 3, 4, 5]
>>> does_exists_num(some_list, 4)
Exists!
>>> does_exists_num(some_list, -1)
Does not exist
```

**異常的 `else` .** 例,

```py
try:
    pass
except:
    print("Exception occurred!!!")
else:
    print("Try block executed successfully...")
```

**Output:**
```py
Try block executed successfully...
```

#### 💡 說明:
- 循環後的 `else` 子句只會在循環沒有觸發 `break` 語句, 正常結束的情況下才會執行.
- try 之後的 `else` 子句也被稱為 "完成子句", 因為在 `try` 語句中到達 `else` 子句意味著try塊實際上已成功完成.

---

### > Inpinity/無限 *

英文拼寫是有意的, 請不要為此提交補丁.
(譯: 這裡是為了突出 Python 中無限的定義與[Pi](https://en.wikipedia.org/wiki/Pi)有關, 所以將兩個單詞拼接了.)

**Output (Python 3.x):**
```py
>>> infinity = float('infinity')
>>> hash(infinity)
314159
>>> hash(float('-inf'))
-314159
```

#### 💡 說明:
- infinity 的哈希值是 10⁵ x π.
- 有意思的是, `float('-inf')` 的哈希值在 Python 3 中是 "-10⁵ x π"  , 而在 Python 2 中是 "-10⁵ x e".

---

### > Mangling time!/修飾時間! *

```py
class Yo(object):
    def __init__(self):
        self.__honey = True
        self.bitch = True
```

**Output:**
```py
>>> Yo().bitch
True
>>> Yo().__honey
AttributeError: 'Yo' object has no attribute '__honey'
>>> Yo()._Yo__honey
True
```

為什麼 `Yo()._Yo__honey` 能運行? 只有印度人理解.(譯: 這個梗可能是指印度音樂人[Yo Yo Honey Singh](https://en.wikipedia.org/wiki/Yo_Yo_Honey_Singh))

#### 💡 說明:

* [名字修飾](https://en.wikipedia.org/wiki/Name_mangling) 用於避免不同命名空間之間名稱衝突.
* 在 Python 中, 解釋器會通過給類中以 `__` (雙下劃線)開頭且結尾最多只有一個下劃線的類成員名稱加上`_NameOfTheClass` 來修飾(mangles)名稱.
* 所以, 要訪問 `__honey` 對像,我們需要加上 `_Yo` 以防止與其他類中定義的相同名稱的屬性發生衝突.

---

---

## Section: Miscellaneous/雜項


### > `+=` is faster/更快的 `+=`

```py
# 用 "+" 連接三個字串:
>>> timeit.timeit("s1 = s1 + s2 + s3", setup="s1 = ' ' * 100000; s2 = ' ' * 100000; s3 = ' ' * 100000", number=100)
0.25748300552368164
# 用 "+=" 連接三個字串:
>>> timeit.timeit("s1 += s2 + s3", setup="s1 = ' ' * 100000; s2 = ' ' * 100000; s3 = ' ' * 100000", number=100)
0.012188911437988281
```

#### 💡 說明:
+ 連接兩個以上的字串時 `+=` 比 `+` 更快, 因為在計算過程中第一個字串 (例如, `s1 += s2 + s3` 中的 `s1`) 不會被銷毀.(譯: 就是 `+=` 執行的是追加操作，少了一個銷毀新建的動作.)

---

### > Let's make a giant string!/來做個巨大的字串吧！

```py
def add_string_with_plus(iters):
    s = ""
    for i in range(iters):
        s += "xyz"
    assert len(s) == 3*iters

def add_bytes_with_plus(iters):
    s = b""
    for i in range(iters):
        s += b"xyz"
    assert len(s) == 3*iters

def add_string_with_format(iters):
    fs = "{}"*iters
    s = fs.format(*(["xyz"]*iters))
    assert len(s) == 3*iters

def add_string_with_join(iters):
    l = []
    for i in range(iters):
        l.append("xyz")
    s = "".join(l)
    assert len(s) == 3*iters

def convert_list_to_string(l, iters):
    s = "".join(l)
    assert len(s) == 3*iters
```

**Output:**
```py
>>> timeit(add_string_with_plus(10000))
1000 loops, best of 3: 972 µs per loop
>>> timeit(add_bytes_with_plus(10000))
1000 loops, best of 3: 815 µs per loop
>>> timeit(add_string_with_format(10000))
1000 loops, best of 3: 508 µs per loop
>>> timeit(add_string_with_join(10000))
1000 loops, best of 3: 878 µs per loop
>>> l = ["xyz"]*10000
>>> timeit(convert_list_to_string(l, 10000))
10000 loops, best of 3: 80 µs per loop
```

讓我們將迭代次數增加10倍.

```py
>>> timeit(add_string_with_plus(100000)) # 執行時間線性增加
100 loops, best of 3: 9.75 ms per loop
>>> timeit(add_bytes_with_plus(100000)) # 二次增加
1000 loops, best of 3: 974 ms per loop
>>> timeit(add_string_with_format(100000)) # 線性增加
100 loops, best of 3: 5.25 ms per loop
>>> timeit(add_string_with_join(100000)) # 線性增加
100 loops, best of 3: 9.85 ms per loop
>>> l = ["xyz"]*100000
>>> timeit(convert_list_to_string(l, 100000)) # 線性增加
1000 loops, best of 3: 723 µs per loop
```

#### 💡 說明:
- 你可以在這獲得更多 [timeit](https://docs.python.org/3/library/timeit.html) 的相關信息. 它通常用於衡量代碼片段的執行時間.
- 不要用 `+` 去生成過長的字串, 在 Python 中, `str` 是不可變得, 所以在每次連接中你都要把左右兩個字串復制到新的字串中. 如果你連接四個長度為10的字串, 你需要拷貝 (10+10) + ((10+10)+10) + (((10+10)+10)+10) = 90 個字符而不是 40 個字符. 隨著字串的數量和大小的增加, 情況會變得越發的糟糕 (就像`add_bytes_with_plus` 函數的執行時間一樣)
- 因此, 更建議使用 `.format.` 或 `%` 語法 (但是, 對於短字串, 它們比 `+` 稍慢一點).
- 又或者, 如果你所需的內容已經以可迭代對像的形式提供了, 使用 `''.join(可迭代對像)` 要快多了.
- `add_string_with_plus` 的執行時間沒有像 `add_bytes_with_plus` 一樣出現二次增加是因為解釋器會如同上一個列子所討論的一樣優化 `+=`. 用 `s = s + "x" + "y" + "z"` 替代 `s += "xyz"` 的話, 執行時間就會二次增加了.
  ```py
  def add_string_with_plus(iters):
      s = ""
      for i in range(iters):
          s = s + "x" + "y" + "z"
      assert len(s) == 3*iters

  >>> timeit(add_string_with_plus(10000))
  100 loops, best of 3: 9.87 ms per loop
  >>> timeit(add_string_with_plus(100000)) # 執行時間二次增加
  1 loops, best of 3: 1.09 s per loop
  ```

---

### > Explicit typecast of strings/字串的顯式類型轉換

```py
a = float('inf')
b = float('nan')
c = float('-iNf')  # 這些字串不區分大小寫
d = float('nan')
```

**Output:**
```py
>>> a
inf
>>> b
nan
>>> c
-inf
>>> float('some_other_string')
ValueError: could not convert string to float: some_other_string
>>> a == -c #inf==inf
True
>>> None == None # None==None
True
>>> b == d #但是 nan!=nan
False
>>> 50/a
0.0
>>> a/a
nan
>>> 23 + b
nan
```

#### 💡 說明:

`'inf'` 和 `'nan'` 是特殊的字串(不區分大小寫), 當顯示轉換成 `float` 型時, 它們分別用於表示數學意義上的 "無窮大" 和 "非數字".

---

### > Minor Ones/小知識點

* `join()` 是一個字串操作而不是列表操作. (第一次接觸會覺得有點違反直覺)

  **💡 說明:**
  如果 `join()` 是字串方法 那麼它就可以處理任何可迭代的對像(列表，元組，迭代器). 如果它是列表方法, 則必須在每種類型中單獨實現. 另外, 在 `list` 對像的通用API中實現一個專用於字串的方法沒有太大的意義.

* 看著奇怪但能正確運行的語句:
  + `[] = ()` 語句在語義上是正確的 (解包一個空的 `tuple` 並賦值給 `list`)
  + `'a'[0][0][0][0][0]` 在語義上也是正確的, 因為在 Python 中字串同時也是[序列](https://docs.python.org/3/glossary.html#term-sequence)(可迭代對像支持使用整數索引訪問元素).
  + `3 --0-- 5 == 8` 和 `--5 == 5` 在語義上都是正確的, 且結果等於 `True`.(譯: 3減負0等於3，再減負5相當於加5等於8；負的負5等於5.)

* 鑒於 `a` 是一個數組, `++a` 和 `--a` 都是有效的 Python 語句, 但其效果與 C, C++ 或 Java 等不一樣.
  ```py
  >>> a = 5
  >>> a
  5
  >>> ++a
  5
  >>> --a
  5
  ```

  **💡 說明:**
  + python 裡沒有 `++` 操作符. 這其實是兩個 `+` 操作符.
  + `++a` 被解析為 `+(+a)` 最後等於 `a`. `--a` 同理.
  + 這個 StackOverflow [回答](https://stackoverflow.com/questions/3654830/why-are-there-no-and-operators-in-python) 討論了為什麼 Python 中缺少增量和減量運算符.

* Python 使用 2個字節存儲函數中的本地變量. 理論上, 這意味著函數中只能定義65536個變量. 但是，Python 內置了一個方便的解決方案，可用於存儲超過2^16個變量名. 下面的代碼演示了當定義了超過65536個局部變量時堆棧中發生的情況 (警告: 這段代碼會打印大約2^18行文本, 請做好准備!):
     ```py
     import dis
     exec("""
     def f():
         """ + """
         """.join(["X"+str(x)+"=" + str(x) for x in range(65539)]))

     f()

     print(dis.dis(f))
     ```

* 你的 *Python 代碼* 並不會多線程同時運行 (是的, 你沒聽錯!). 雖然你覺得會產生多個線程並讓它們同時執行你的代碼, 但是, 由於 [全局解釋鎖](https://wiki.python.org/moin/GlobalInterpreterLock)的存在, 你所做的只是讓你的線程依次在同一個核心上執行. Python 多線程適用於IO密集型的任務, 但如果想要並行處理CPU密集型的任務, 你應該會想使用 [multiprocessing](https://docs.python.org/2/library/multiprocessing.html) 模塊.

* 列表切片超出索引邊界而不引發任何錯誤
  ```py
  >>> some_list = [1, 2, 3, 4, 5]
  >>> some_list[111:]
  []
  ```

* `int('١٢٣٤٥٦٧٨٩')` 在 Python 3 中會返回 `123456789`. 在 Python 中, 十進制字符包括數字字符, 以及可用於形成十進制數字的所有字符, 例如: U+0660, ARABIC-INDIC DIGIT ZERO. 這有一個關於此的 [有趣故事](http://chris.improbable.org/2014/8/25/adventures-in-unicode-digits/).

* `'abc'.count('') == 4`. 這有一個 `count` 方法的相近實現, 能更好的說明問題
  ```py
  def count(s, sub):
      result = 0
      for i in range(len(s) + 1 - len(sub)):
          result += (s[i:i + len(sub)] == sub)
      return result
  ```
  這個行為是由於空子串(`''`)與原始字串中長度為0的切片相匹配導致的.

---

# Contributing/貢獻

歡迎各種補丁! 詳情請看[CONTRIBUTING.md](https://github.com/satwikkansal/wtfpython/blob/master/CONTRIBUTING.md).(譯: 這是給原庫提貢獻的要求模版)

你可以通過新建 [issue](https://github.com/satwikkansal/wtfpython/issues/new) 或者在上 [Gitter](https://gitter.im/wtfpython/Lobby) 與我們進行討論.

(譯: 如果你想對這個翻譯項目提供幫助, 請看[這裡](https://github.com/leisurelicht/wtfpython-cn/blob/master/CONTRIBUTING.md))

# Acknowledgements/致謝

這個系列最初的想法和設計靈感來自於 Denys Dovhan 的項目 [wtfjs](https://github.com/denysdovhan/wtfjs). 社區的強大支持讓它成長為現在的模樣.

#### Some nice Links!/一些不錯的資源
* https://www.youtube.com/watch?v=sH4XF6pKKmk
* https://www.reddit.com/r/Python/comments/3cu6ej/what_are_some_wtf_things_about_python
* https://sopython.com/wiki/Common_Gotchas_In_Python
* https://stackoverflow.com/questions/530530/python-2-x-gotchas-and-landmines
* https://stackoverflow.com/questions/1011431/common-pitfalls-in-python
* https://www.python.org/doc/humor/
* https://www.codementor.io/satwikkansal/python-practices-for-efficient-code-performance-memory-and-usability-aze6oiq65

# 🎓 License/許可

[![CC 4.0][license-image]][license-url]

&copy; [Satwik Kansal](https://satwikkansal.xyz)

[license-url]: http://www.wtfpl.net
[license-image]: https://img.shields.io/badge/License-WTFPL%202.0-lightgrey.svg?style=flat-square

## Help/幫助

如果您有任何想法或建議，歡迎分享.

## Surprise your geeky pythonist friends?/想給你的極客朋友一個驚喜?

您可以使用這些快鏈向 Twitter 和 Linkedin 上的朋友推薦 wtfpython,

[Twitter](https://twitter.com/intent/tweet?url=https://github.com/satwikkansal/wtfpython&hastags=python,wtfpython)
 | [Linkedin](https://www.linkedin.com/shareArticle?url=https://github.com/satwikkansal&title=What%20the%20f*ck%20Python!&summary=An%20interesting%20collection%20of%20subtle%20and%20tricky%20Python%20snippets.)

## Need a pdf version?/需要來一份 pdf 版?

我收到一些想要pdf版本的需求. 你可以快速在[這](https://satwikkansal.xyz/wtfpython-pdf/)獲得.

## Follow Commit/追蹤 Commit

這是中文版 fork 時所處的原庫 Commit, 當原庫更新時我會跟隨更新.

[![Commit id][commit-image]][commit-url]

[commit-url]: https://github.com/satwikkansal/wtfpython/commit/30e05a5973930c38cdb59f1c02b85b19b22ac531
[commit-image]: https://img.shields.io/badge/Commit-30e05a-yellow.svg
