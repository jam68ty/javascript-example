# JavaSrcipt Example Project

## 建立專案
1. 先在本地端建立一個資料夾作為專案位置
![](https://i.imgur.com/czsa0bS.png)
2. 開啟VS Code File - Open Folder，開啟剛剛建立的資料夾
3. New Ternminal，在下方terminal輸入`touch README.md`(使用指令建立檔案)
![](https://i.imgur.com/w5bMY4p.png)
> 若無touch，則輸入`npm install touch-cli -g`安裝touch的套件
> ![](https://i.imgur.com/ZaV3Pi5.png)

## 建立Node.js的package

1. 檢查node js的version：`node --version`
2. 初始化node js專案所需的package：`node init`
![](https://i.imgur.com/IDLDHG4.png)
3. 完成後目錄下會自動出現`package.json`紀錄此專案的基本訊息
![](https://i.imgur.com/EDyKFSd.png)

## 安裝別人寫好的套件

1. 在terminal輸入`npm install lodash --save`
![](https://i.imgur.com/H70jxhK.png)
2. 完成後在這個專案中就會外來套件的相關檔案
![](https://i.imgur.com/Nh0C8Io.png)
3. 並且在`package.json`裡也會出現dependency
![](https://i.imgur.com/rHV157x.png)

> 下載測試用的套件(會自動去找測試的程式執行)：
> `npm install jest -g`

## 執行第一個腳本

可以看到在之前的`npm init`的步驟裡，我們選擇了預設的`index.js`作為專案的entry point，因此我們要在專案裡新增一個`index.js`
![](https://i.imgur.com/aehXObX.png)
1. 建立`index.js`的檔案，並且輸入`console.log('Hello world!');`
![](https://i.imgur.com/MgvdS7a.png)
2. 執行
(1) 可以選擇使用terminal輸入`node index.js`
![](https://i.imgur.com/oYdi1vr.png)
(2) 建立腳本：在`package.json`裡建立腳本
("Script Name"："Script Content")
![](https://i.imgur.com/t22uPTK.png)
並在terminal中執行`npm run test`
![](https://i.imgur.com/CpMaS1W.png)
(3) 使用VS Code的Debug
第一次使用會需要安裝套件
![](https://i.imgur.com/LAQ9qoK.png)
完成之後他會自動執行該專案的程式，程式會從前面`package.json`所設定的進入點開始跑
![](https://i.imgur.com/3jybPxf.png)


## 雜筆記

### VS Code偵錯模式
> 此篇為另建立的專案，專案名稱改為`hello-es6`，除此外皆相同

* 使用Chrome Debug會自動在專案下建立一個`.vscode`的資料夾
![](https://i.imgur.com/9xcRLY5.png)

* 裡面會有一個叫做`launch.json`的檔案存放可執行的組態
![](https://i.imgur.com/vH4S3jv.png)

* 我們也可以自行新增新的組態
![](https://i.imgur.com/MHKbGa1.png)

* 並把執行的腳本名稱換成前在`package.json`裡設定的腳本名稱
![](https://i.imgur.com/01KzMin.png)

* 此時再進行Debug，那麼他的執行效果就等同於`npm run test`
![](https://i.imgur.com/B1VNynI.png)

### VSCode 中斷點測試
* 按該行程式前面就可以設定中斷點。
* 可以看到只執行了line 6，因為中斷點設在line 7，因此最終只印出了a is: 1
![](https://i.imgur.com/LUr4w4S.png)

* 可以利用上方浮動的工具跳中斷點，完整執行此程式
![](https://i.imgur.com/0AxOCmx.png)

### ES6是什麼?

* JavaScript規範的版本之一，全名是ECMAScript 6
* 一些簡單的介紹可以看：https://ithelp.ithome.com.tw/articles/10200007

* 跟ES5比較明顯的差別舉例來說：
```javascript=
// es5 需要分開打用+串接
var name = ‘Name ‘ + first + ‘ ‘ + last + ‘.’
// es6 可以使用${}直接放變數
var name = `Name is ${first} ${last}.`
-----------------------------------
// es5 多行必須分開
var name = ‘first line’
 + ‘second line’
// es6 多行可以用一個「`」代替(markdown語法裡的顯示程式碼的標記)
var name = `first line
second line`
```
* 在ES6後出現了一個叫做Arrow function(fat arrow function)的功能(個人覺得有點像python裡的lambda function)
* 簡單來說就是讓function變得更簡短，比如：
```javascript=
const fun = function(x) { return x + 1 }
```
可以寫成
```javascript=
const fun = (x) => x + 1
```


---

* 但是若今天function沒有return value(void)，就要加上{}。比如：
```javascript=
const fun = function(x) { x + 3 }
```
可以寫成
```javascript=
const fun = (x) => { x + 3 }
```

---

#### 常用的ES6語法

* 引入package
    * require: Node.js 和 ES6 都支援的引入
    * export / import : 只有ES6 支援的導出引入
    * module.exports / exports: 只有 Node.js 支援的導出

* 解構賦值
```javascript=
//es5
const p = {name: 'Amy'};
const name = p.name // Amy
const id = p.id || 'no ID' //no ID
// es6
const p = {name: 'Amy'};
const {name, id = 'no ID'} = p
```

參考：https://ithelp.ithome.com.tw/articles/10200290

## Coding Style - ESLint

為了維持一定的coding style，也為了團隊合作時不要看別人的程式看到瘋掉(或讓人瘋掉)，有一些套件工具可以使用，這邊使用ESLint。

1. 安裝ESLint：`npm install -g eslint`
2. 在專案內產生套件執行檔`eslintrc.js`：`eslint --init`，他會問你一些關於程式碼的規範問題想怎麼設定
3. 設定一些規定的coding style
![](https://i.imgur.com/9FrieNP.png)
4. 創一個`badcod.js`，裡面的程式雖然都可以執行，但是對於維護或是開發都不太友善
![](https://i.imgur.com/ZO30p9O.png)
5. 執行`eslint badcode.js`，他會幫你挑出錯誤
![](https://i.imgur.com/KmKHjXu.png)
6. 可選擇手動修正或是自動修正：`eslint badcode.js --fix`
![](https://i.imgur.com/9be3czU.png)

> 當然，好的編譯器肯定都幫你做好了，只要去裝好套件，就算不像上面那樣執行、他也能幫你維持你的coding style
![](https://i.imgur.com/g21MkKH.png)
像是我用了""和我所設定的coding style不合，他就會幫我報錯
![](https://i.imgur.com/cBZXH53.png)

