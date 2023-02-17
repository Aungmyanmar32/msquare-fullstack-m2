## MSquare Programing Fullstack Course
### Episode-*19* Summary for (group 2) 

ဒီနေ့သင်တန်းမှာတော့ <br>
### pull request ( PR) and Marge to mian on github repo
### npm 
### install express
အကြောင်း လေ့လာသွားပါမယ်။
##
### ပြီးခဲတဲ့ သင်ခန်းစာမှာ pull request (PR) လုပ်ပြီး reviewer တစ်ယောက် ကို add ခဲ့ပြီးပါပြီး
- reviewer က ကျနော်တို့ request လုပ်တဲ့repo မှာ စစ်ဆေးပြီး မှတ်ချက်ပေးလိုက်ပါတယ်။
- အဲ့ဒါကို ကြည့်ဖို့ မိမိရဲ့ Github repo ကိုသွားပါ။
- pull request ထဲ ၀င်ပါ
- မိမိ request  လုပ်ထားတဲ့ နေရာကို ထပ်၀င်ပါ

![enter image description here](https://raw.githubusercontent.com/Aungmyanmar32/msquare-fullstack-m2/main/pr1.png)
- ဆရာက မှတ်ချက်ပေးထားတာကို မြင်ရမှာပါ။
- ပုံထဲမှာတော့ line 7 က text ကို welcome to msquarefdcလို့ ပြောင်းလိုက်ပါလို့ မှတ်ချက်ပေးထားပါတယ်
- ဒါကြောင့်မလို့ မိမိရဲ့  vs code ထဲမှာ feat/sidebar branch ထဲကို သွားပြီး sidebar.html မှာ ဆရာခိုင်းတဲ့အတိုင်း ပြင်လိုက်ပါ
- git add/commit လုပ်ပြီး git push လုပ်လိုက်ပါ။
- ပြီးရင်တော့  ဆရာခိုင်းတဲ့အတိုင်း ပြင်လိုက်ပြီး ဖြစ်ကြောင်း Resolve conversation ကို နှိပ်ပေးလိုက်ပါ 
##
![enter image description here](https://raw.githubusercontent.com/Aungmyanmar32/msquare-fullstack-m2/main/pr2.png)
- reviewer က ထပ်မံစစ်ဆေးပြီး အဆင်ပြေကြောင်း ပြောလာပါက Marge လုပ်လို့ ရပါပြီး
- Marge pull request ကို အများအားဖြင့် reviewer ကပဲ နှိပ်ပေးလေ့ရှိပါတယ်
- ဒီနေ့သင်ခန်းစာမှာတော့  မိမိကိုယ်တိုင်ပဲ နှိပ်ပေးလိုက်ပါ။
- ဒါဆိုရင် feat/sidebar ဆိုတဲ့ branch ကို main ထဲ marge လုပ်လို့ ပြီးပါပြီး
##
### N*ode* P*ackage* M*anager* (or)  NPM  
#### (မိတ်ဆက်)
- NPM ဆိုတာက NodeJS ကို အသုံးပြုရေးသားထားတဲ့ package တွေကို စီမံခန့်ခွဲ ပေးတဲ့ အရာဖြစ်ပါတယ်။
- NodeJS ကို install   လုပ်လိုက်တာနဲ့ NPM ပါ တစ်ခါတည်းပါပီးသားဖြစ်ပါတယ်။
- NPM ရှိမရှိ ကို TERMINAL မှာ `npm -v` ဆိုပြီး စစ်ကြည့်နိုင်ပါတယ်။
အောက်မှာ 8.19...ဆိုပြီး ပြပေးရင် NPM install လုပ်ထားပြီးဖြစ်ပါတယ်။
##
### Setup NPM project
- မိမိရဲ့ project မှာ node package  တွေ သုံးနိုင်ဖို့ npm ကို initialize လုပ်ပေးရပါမယ်
- အရင်ဆုံး npm-express-project ဆိုတဲ့ folder တစ်ခု ဆောက်ပြီး vs code မှာ ဖွင့်ထားပေးပါ
- new terminal ကို ဖွင့်ပြီး `npm init` ကို ရိုက်ထည့်းပေးပါ။
```bash
Admin@MSquare MINGW64 ~/Desktop/ep31/npm-express-project
$ npm init
This utility will walk you through creating a package.json file.
It only covers the most common items, and tries to guess sensible defaults.

See `npm help init` for definitive documentation on these fields
and exactly what they do.

Use `npm install <pkg>` afterwards to install a package and
save it as a dependency in the package.json file.

Press ^C at any time to quit.
package name: (npm-express-project)
```
- package name ကို npm-express-project လို့ပေးမှာလားလို့ မေးတာပါ။( enter ခေါက်ပေးလိုက်ပါ)
- ဆက်ပြီးမေးလာသမျှ ကိုလဲ enter ခေါက်ပေးလိုက်ပါ။
```bash
author:                                                                                                                                                                                        
license: (ISC)                                                                                                                                                                                 
About to write to C:\Users\Admin\Desktop\ep31\npm-express-project\package.json:

{
  "name": "npm-express-project",
  "version": "1.0.0",
  "description": "",
  "main": "index.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "author": "",
  "license": "ISC"
}


Is this OK? (yes)

Admin@MSquare MINGW64 ~/Desktop/ep31/npm-express-project
$
```
- ဒီလိုပြလာပြီး ဆိုရင် npm init လုပ်လို့ပြီးပါပြီး
- ကိုယ့်ရဲ့ project folder ထဲမှာ package.json ဖိုင်တစ်ခု ရလာမှာဖြစ်ပါတယ်။
```properties
//package.json

{
"name": "npm-express-project",
"version": "1.0.0",
"description": "",
"main": "index.js",
"scripts": {
"test": "echo \"Error: no test specified\" && exit 1"
},

"author": "",
"license": "ISC"

}
```
##
### Express
- Express ဆိုတာ node server ကို အသုံးပြုရလွယ်ကူအောင် ပြုလုပ်ထားတဲ့ node package ( node module ) တစ်ခုဖြစ်ပါတယ်
- npm မှတဆင့် node package တွေကို မိမိ projetc ထဲ install လုပ်ပြီး အသုံးပြုနိုင်ပါတယ်
- expressကို install လုပ်ရန် termianl ထဲ `npm install express` လို့ ရိုက်ထည့်ပေးပါ။
```bash
Admin@MSquare MINGW64 ~/Desktop/ep31/npm-express-project
$ npm install express

added 57 packages, and audited 58 packages in 5s

7 packages are looking for funding
  run `npm fund` for details

found 0 vulnerabilities

Admin@MSquare MINGW64 ~/Desktop/ep31/npm-express-project
$
```
- express ကို install လုပ်လိုက်ပါက မိမိရဲ့ project folderထဲမှာ node_modules folder နဲ့ package_lock.json ဆိုပြီး နှစ်ခု ထပ်တိုးလားတာကိုမြင်ရမှာပါ။
- ဒါ့အပြင် package.json ထဲမှာလဲ dependencies object တစ်ခု တိုးလာပြီး သူ့အထဲမှာ ကျနော်တို့ install လုပ်လိုက်တဲ့ express ကို ပြပေးနေတာကို မြင်ရမှာပါ။
```properties
{
  "name": "npm-express-project",
  "version": "1.0.0",
  "description": "",
  "main": "index.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "author": "",
  "license": "ISC",
  "dependencies": {
    "express": "^4.18.2"
  }
}

```
-  ကျနော်တို့ install လုပ်လိုက်တဲ့ node module တွေကို အဆိုပါ dependencies object အထဲမှာ ၀င်ကြည့်နိုင်ပါတယ်။

![enter image description here](https://raw.githubusercontent.com/Aungmyanmar32/msquare-fullstack-m2/main/00exr21.png)

##
### Note
- npm init လုပ်တဲ့အခါ default အနေတဲ့ တစ်ခါတည်းလုပ်ချင်ပါက
**`npm init -y`** ကို အသုံးပြုနိုင်ပါတယ်။

