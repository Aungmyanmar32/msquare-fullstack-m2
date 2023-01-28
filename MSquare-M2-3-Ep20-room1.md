## MSquare Programing Fullstack Course
### Episode-*20* 
### Summary For `Room(1)` intermediate Class
##
### GET data from server and POST data to server (Using Postman)

- Postman ကို မိမိစက်ထဲ install လုပ်ထားပေးပါ။ (download Postman and install)
- Postman ကို ဖွင့်ထားပေးပါ။
- VS code မှာ server.js ထဲ sever တစ်ခု create လုပ်၊ allUsers array တစ်ခုလုပ်ပါ။
- `/allUsers`  route နဲ့  request တွေ method တွေကို  listen လုပ်ထားပါမယ်။
- node server.js ဖြင့် http serverကို run ပေးထားပါ။
### server.js
```js
const  fs = require("fs");
const  http = require("http");

const  allUsers = [
{
 id:  1,
 name:  "Aung Aung",
 email:  "aung1@web.de",
},
{
 id:  2,
 name:  "Ko Ko",
 email:  "koko2@web.de",
},
{
 id:  3,
 name:  "Bo Bo",
 email:  "bobo3@web.de",
},
];

const  server = http.createServer((req, res) => {
 if (req.url === "/allUsers") {
 const  method = req.method;
  if (method === "GET") {
//Get method
   res.writeHead(200, { "Content-Type":  "application/json" });
   res.write(JSON.stringify(allUsers));
   return  res.end();
  } else  if (method === "POST") {
//post method
//get data from front-end
   let  newData = "";
   req.on("data", (chunk) => {
    newData += chunk;
   });
   req.on("end", () => {
//push new-data to allUsers array
    allUsers.push(JSON.parse(newData));
//response updated allUsers array to front-end
    res.writeHead(200, { "Content-Type":  "application/json" });
    res.write(JSON.stringify(allUsers));
    return  res.end();
   });
  }
  } else {
   res.writeHead(404, { "Content-Type":  "text/plain" });
   res.write("404 | Page Not Found!");
   return res.end();
   }
});

server.listen(3000, () => {
 console.log("Server started: Listening on port 3000");
});
```
##
### GET data from server using *Postman*
- postman အထဲမှာ
1. method ကို GET
2. url မှာ localhost:3000/allUsers 
- request send လိုက်ရင် sever ကနေ response လုပ်ပေးတဲ့ Json string ကို body output မှာ ပြပေးတာ မြင်ရမှာပါ။
- 
![enter image description here](https://raw.githubusercontent.com/Aungmyanmar32/msquare-fullstack-m2/main/ep20-1-1.jpg)
##
### POST data to server using *Postman*
- postman အထဲမှာ
1. method ကို POST
2. url မှာ localhost:3000/allUsers 
3. အောက်မှာ body tabကိုရွေး
4. body အောက်မှာ raw ကို ရွေးပြီး text  မှာ JSON ပြောင်းပေးလိုက်ပါ
5. ပြီးရင် POST ချင်တဲ့ data ကို  အောက်က box ထဲမှာ ရေးထည့်ပေးပါ။
- request send လိုက်ရင် sever ကနေ response လုပ်ပေးတဲ့ Json string ကို body output မှာ ပြပေးတာ မြင်ရမှာပါ။ POST လိုက်တဲ့ JSON ကို အောက်ဆုံးမှာ ပြပေးနေပါလိမ့်မယ်။
![enter image description here](https://raw.githubusercontent.com/Aungmyanmar32/msquare-fullstack-m2/main/ep20-1-2.jpg)

##
### N*ode* P*ackage* M*anager* (or)  NPM  
#### (မိတ်ဆက်)
- NPM ဆိုတာက NodeJS ကို အသုံးပြုရေးသားထားတဲ့ package တွေကို စီမံခန့်ခွဲ ပေးတဲ့ အရာဖြစ်ပါတယ်။
- NodeJS ကို install   လုပ်လိုက်တာနဲ့ NPM ပါ တစ်ခါတည်းပါပီးသားဖြစ်ပါတယ်။
- NPM ရှိမရှိ ကို TERMINAL မှာ `npm -v` ဆိုပြီး စစ်ကြည့်နိုင်ပါတယ်။
အောက်မှာ 8.19...ဆိုပြီး ပြပေးရင် NPM install လုပ်ထားပြီးဖြစ်ပါတယ်။

##
### Nodemon ( Node package)


    Nodemon ဆိုတာက NodeJS ကို အသုံးပြုရေးသားထားတဲ့ package (Node Module) တစ်ခုဖြစ်ပါတယ်။

 - server.js မှာ code အသစ်ရေးလိုက်တိုင်း /တစ်ခုခုပြင်လိုက်တိုင်း run ထားတဲ့ node server ကို  restart (ပိတ်/ဖွင့်) ပြန်လုပ်ပေးရလေ့ရှိပါတယ်။
 - nodemon ကို အသုံးပြုလိုက်မယ်ဆိုရင် **server.js မှာ ပြောင်းလဲမှုရှိတိုင်း** server ကို **restart ပြန်လုပ်စရာမလိုတော့ပဲ** nodemon က ပြောင်းလဲမှုများကို **စောင့်ကြည့်ကာ auto restart လုပ်**ပေးနိုင်ပါတယ်။
### Install Nodemon  globally by using NPM
 - terminal ထဲမှာ `npm i -g nodemon` ဆိုတဲ့ command ကို run ပေးလိုက်ရုံနဲ့ nodemon ကို NodeJS မှာ အသုံးပြုလို့ ရပါပြီး။<br>( `i` = install , `-g` = install in globally (**can use any Dir** ) )
- nodemon ကို အသုံးပြုပြီး node sever run မယ်ဆိုရင် `node server.js` အစား `nodemon server.js` လို့ ပြောင်းရေးပေးရမှာ ဖြစ်ပါတယ်။
- ![enter image description here](https://raw.githubusercontent.com/Aungmyanmar32/msquare-fullstack-m2/main/ep20-1-3.jpg)
