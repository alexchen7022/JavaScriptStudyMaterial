# Windows javascript 開發環境 安裝基礎
##1.Git
git是目前流行的版本控制程式，許多lib都存放於github這個網路服務網站上，
因此需要先安裝這個git的程式讓npm可以抓的到他所需要的lib.
**在安裝的過程中，要選擇Use Git from the windows command prompt讓windows的command line可以執行Git 不然其他軟體會抓不到。**  
https://git-scm.com/download/win
### 如果是在網管嚴格的環境，必須設定git proxy  
E.g.  
**git config --global http.proxy http://proxy.chu.edu.tw:3128**  
**git config --global https.proxy http://proxy.chu.edu.tw:3128**  

### git 預設port 為9418 但是被擋下來，因此把default的協定從git換成https  
**git config --global url."https://".insteadOf git://**  

##2.python 與 windows SDK
一些nodejs 的lib需要用到 npm-gyp這個lib來進行編譯，可以參考他的說明
https://github.com/nodejs/node-gyp
因此必須安裝**python 2.7.3** 並且安裝windows SDK，如果是64位元的環境要安裝64位元的SDK.
直接安裝visual studio 也可以，不過至少要開過一個C++的專案，他才會開始下載C++的編譯器。
記得確認python與C++的編譯器都存在於PATH的系統變數，E.g.可以在命令列下面確認，是否可以執行python.

# 安裝nodejs
https://nodejs.org/en/  
javascript serverside 的lib。
>Node.js® is a JavaScript runtime built on Chrome's V8 JavaScript engine. 
>Node.js uses an event-driven, non-blocking I/O model that makes it lightweight and efficient.
>Node.js' package ecosystem, npm, is the largest ecosystem of open source libraries in the world.

## 1.對 npm 設定proxy  
如果網路有限制必須透過proxy的話，除了git，npm也必須要設定
E.g.  
npm config set proxy http://proxy.chu.edu.tw:3128  
npm config set https-proxy http://proxy.chu.edu.tw:3128  

## 2.設定npm module路徑
在命令列的狀況下打輸入下列指令，  
**npm config set prefix "你想要的模組安裝路徑" -g**  
e.g. npm config set prefix "C:\npm" -g  
變更有兩個好處，第一個避免安裝路徑過長，第二個可以讓不同的帳號使用相同的npm模組，
如果windows使用習慣是一開始只用user的帳號登入，有需要時再用admin登入時，在run as administrator的狀況下，
有時候會安裝到admin的預設資料夾，這樣子整個npm安裝的node module會變的怪怪的。  
設定結束之後，記得將npm module的路徑加入system path，讓命令列下可以直接執行global的指令。  
參考資料:http://blog.miniasp.com/post/2015/09/02/Change-npm-default-global-installation-directory-for-nodejs-modules-in-Windows.aspx

## 3.更新npm 
npm為node module的管理程式，更新npm可以避免過深的巢狀參考，但是nodejs很奇妙，
在預設安裝的時候，並不會自行安裝新版的npm，而是需要自行更新  
**npm install -g npm**  

# 安裝bower
bower 為 web lib的管理程式，透過bower可以做版本控管   
**npm install -g bower**  
http://bower.io/
## 如果網路有限制的話，必須設定proxy
http://bower.io/docs/config/

# 安裝gulp
gulp 為 自動化工具，透過gulp可以將常用的命令打包並且串流執行。  
**npm install -g gulp**  
http://gulpjs.com/

# 安裝鷹架軟體
萬事起頭難，如果能有一個鷹架先搭起來，這樣子在開發上面就會先有一個統一的依循。 
目前我們使用的是 *Yeoman (THE WEB'S SCAFFOLDING TOOL FOR MODERN WEBAPPS)*  
http://yeoman.io/   
**npm install -g yo**

## 安裝參考的鷹架
我們會使用gulp-webapp這個樣板來進行開發  
**npm install -g generator-gulp-webapp**

# 建立專案資料夾，並使用鷹架初始化
先建立一個workspace與專案資料夾，E.g. D:\workspace\project1  
接著進入這個資料夾 cd  D:\workspace\project1  
最後執行 **yo gulp-webapp**  




