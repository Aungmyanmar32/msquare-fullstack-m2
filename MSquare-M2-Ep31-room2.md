
## MSquare Programing Fullstack Course
### Episode-*31* Summary for (group 2) 

ဒီနေ့သင်တန်းမှာတော့ <br>
### git & github

အကြောင်း ပြန်လေ့လာသွားပါမယ်။
##

1. node-tutorial ဆိုတဲ့ github repo တစ်ခုကို readme file ထည့်ပြီး createလုပ်ပါ။
2. SSH link ကို copy  ယူပါ။
3. create လုပ်ထားတဲ့ repo ကို SSH link ကို သုံးပြီး local ထဲ clone လုပ်ပါ 
4. clone လို့ ရလာတဲ့ folder ထဲမှာ index.html style.css script.js server.js ဖိုင်များ create လုပ်ပါ။

![enter image description here](https://raw.githubusercontent.com/Aungmyanmar32/msquare-fullstack-m2/main/ep31g21.png)
##
### node http server တစ်ခု create ပြန်လုပ်ကြည့်ပါ။

```properties
<!-- index.html -->
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta http-equiv="X-UA-Compatible" content="IE=edge" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Document</title>
  </head>
  <body>
    <h1>NODE server Restart</h1>
    <script src="script.js"></script>
  </body>
</html>
```
```js
// script.js
console.log("hello");
```
```js
// server.js
const http = require("http");
const fs = require("fs");

const server = http.createServer((request, response) => {
  const method = request.method;
  const route = request.url;
  if (route === "/") {
    fs.readFile("./index.html", (err, data) => {
      response.writeHead(200, { "Content-Type": "text/html" });
      response.write(data);
      response.end();
    });
  } else if (route === "/script.js") {
    fs.readFile("./script.js", (err, data) => {
      response.writeHead(200, { "Content-Type": "text/javascript" });
      response.write(data);
      response.end();
    });
  } else if (route === "/style.css") {
    fs.readFile("./style.css", (err, data) => {
      response.writeHead(200, { "Content-Type": "text/css" });
      response.write(data);
      response.end();
    });
  } else {
    response.writeHead(200, { "Content-Type": "text/plain" });
    response.write(`404 | Page not found!`);
    response.end();
  }
});

server.listen(3000, () => {
  console.log("Server Runnig on Port 3000");
});

```
- server.js ထဲမှာ http server တစ်ခု create လုပ်ထားပြီး port 3000မှာ listen ထားပါတယ်
- server  ထဲမှာ  request ၀င်လာခဲ့ရင် သက်ဆိုင်ရာ route တွေနဲ့ စစ်ဆေးပြီး   သက်ဆိုင်ရာ file တွေကို  ဖတ်ပြီး response လုပ်ထားပါတယ်။
##
### ဆာဗာ start လို့ရပြီး ဆိုရင် 
- git add / git commit လုပ်ပြီး GitHub မှာ push ပြန်လုပ်ပေးပါ။
##
##
### pull request and add reviewers
- feat/sidebar ဆိုတဲ့ branch  တစ်ခု လုပ်ပါ
- feat/sidebar branch မှာ sidebar.html ဖိုင်တစ်ခုလုပ်ပါ။
```properties
Admin@MSquare MINGW64 ~/Desktop/exercises/node-tutorial (main)
$ git switch -c feat/sidebar
Switched to a new branch 'feat/sidebar'

Admin@MSquare MINGW64 ~/Desktop/exercises/node-tutorial (feat/sidebar)
$ touch sidebar.html

```
- sidebar.html ထဲမှာ codeတစ်ိချု့ရေးပါမယ်
```html
<!-- sidebar.html -->
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta http-equiv="X-UA-Compatible" content="IE=edge" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Document</title>
  </head>
  <body>
    <h1>This is sidebar</h1>  
  </body>
</html>
```
- git add / git commit လုပ်ပြီး GitHub  ဆီကို push ပေးပါ
```properties
Admin@MSquare MINGW64 ~/Desktop/exercises/node-tutorial (feat/sidebar)
$ git add .

Admin@MSquare MINGW64 ~/Desktop/exercises/node-tutorial (feat/sidebar)
$ git commit -m "feat/sidebar branch & sidebar html added"
[feat/sidebar d8955f6] feat/sidebar branch & sidebar html added
 2 files changed, 15 insertions(+)
 create mode 100644 sidebar.html

Admin@MSquare MINGW64 ~/Desktop/exercises/node-tutorial (feat/sidebar)
$ git push --set-upstream origin feat/sidebar
Enumerating objects: 5, done.
Counting objects: 100% (5/5), done.
Delta compression using up to 16 threads
Compressing objects: 100% (3/3), done.
Writing objects: 100% (3/3), 341 bytes | 341.00 KiB/s, done.
Total 3 (delta 2), reused 0 (delta 0), pack-reused 0
remote: Resolving deltas: 100% (2/2), completed with 2 local objects.
remote: 
remote: Create a pull request for 'feat/sidebar' on GitHub by visiting:
remote:      https://github.com/Aungmyanmar32/node-tutorial/pull/new/feat/sidebar
remote:
To github.com:Aungmyanmar32/node-tutorial.git
 * [new branch]      feat/sidebar -> feat/sidebar
branch 'feat/sidebar' set up to track 'origin/feat/sidebar'.

Admin@MSquare MINGW64 ~/Desktop/exercises/node-tutorial (feat/sidebar)
$
``` 
- အခုဆို github repo မှာ  branch နှစ်ခု ရှိနေပါပြီး
- main branch မှာ feat/sidebarကို ပေါင်းထည့်ဖို့  pull request လုပ်ပါမယ်။

![enter image description here](https://raw.githubusercontent.com/Aungmyanmar32/msquare-fullstack-m2/main/ep31g22.png)
- ကုဒ်တွေ စစ်ဆေးပေးဖို့ reviewer ထည့်ပါမယ်
- reviewer မထည့်ခင် ကိုယ်ထည့်ချင်တဲ့ reviewer ကို invite အရင် လုပ်ပေးရပါမယ်
- setting > collaborators ထဲ ၀င်ပြီး Add people ကို နှိပ်ပါ
![enter image description here](https://raw.githubusercontent.com/Aungmyanmar32/msquare-fullstack-m2/main/ep31g23.png)

-ပေါ်လာတဲ့ box ထဲမှာ ဆရာ့ github username ဖြစ်တဲ့ msquareprograming ကို ရိုက်ထည့်ပီး ရွေးပေးကာ add ပေးပါ

![enter image description here](https://raw.githubusercontent.com/Aungmyanmar32/msquare-fullstack-m2/main/ep31g24.png)

- invite လုပ်ပြီးပါက pending invite လို့ပြနေပါမယ်
- ဆရာလက်ခံလိုက်ပါက ဆရာ့ကို reviewer အနေနဲ့ pull request မှာ ထားလို့ရပါပြီး 
![enter image description here](https://raw.githubusercontent.com/Aungmyanmar32/msquare-fullstack-m2/main/ep31g25.png)

- pull request ထဲ ၀င်ပြီး  ခနက create လုပ်ထားတဲ့ request ထဲ ထပ်၀င်ကာ reviewer ဘေးက စက်သွားပုံကို နှိပ်ပြီး reviewer  ထည့်လို့ရပါပြီး
![enter image description here](https://raw.githubusercontent.com/Aungmyanmar32/msquare-fullstack-m2/main/ep31g26.png)
