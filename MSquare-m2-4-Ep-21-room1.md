## MSquare Programing Fullstack Course

### Episode-21

### Summary For  `Room(1)`  intermediate Class
- ပြီးခဲ့တဲ့ သင်ခန်းစာမှာ GET နဲ့ POST method ကို လေ့လာခဲ့ကြပါတယ်
- ခုသင်ခန်းစာမှာတော့ PUT and DELETE method ကို လေ့လာသွားကြပါမယ်။
##


- အောက်မှာ အရင် postman သင်ခန်းစာက code တွေပြန်ပြထားတာဖြစ်ပါတယ်
- ### server.js
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
### PUT data to server( Using Postman)
- PUT method က ဆာဗာမှာ ရှိပြီးသားdata ကို ပြင်လိုတဲ့အခါ အသုံးပြုပါတယ်
- နမူနာမှာတော့ ဆာဗာမှာ ရှိပြီးသား user email နဲ့ request ကပို့လိုက်တဲ့ email တို့ 
တူမတူ တိုက်ဆိုင်စစ်ဆေးပြီး တူလာခဲ့ရင် request ကပို့လိုက်တဲ့ name ကို ဆာဗာ က
user name နေရာမှာ အစားထိုး ပြင်ဆင်တာကို လေ့လာရမှာ ဖြစ်ပါတယ်
- POST method ရဲ့ အဆုံးမှာ PUT method ကို ဆက်ရေးပါမယ်
### server.js
```js
else if (method === "PUT") {
      //PUT method

      //get data from front-end
      let updateData = "";
      req.on("data", (chunk) => {
        updateData += chunk;
      });

      req.on("end", () => {
        //push new-data to allUsers array
        const updateUser = JSON.parse(updateData);
        
        //get email from request
        const updateEmail = updateUser.email;
        
        //find this email is matching with allUsers array items
        const isEmailexit = allUsers.find((user) => user.email === updateEmail);

        if (isEmailexit) {
          //update new name
          isEmailexit.name = updateUser.name;
        }
        // response updated allUsers array to front-end
        res.writeHead(200, { "Content-Type": "application/json" });
        res.write(JSON.stringify(allUsers));
        return res.end();
      });
    }
```
 `else if (method === "PUT")`
- Put method ဖြစ်ခဲ့ရင် အထဲက ကုဒ်တွေ run ပေးပါလို့ သတ်မှတ်လိုက်တာပါ။
```js
  let updateData = "";
      req.on("data", (chunk) => {
        updateData += chunk;
      });

      req.on("end", () => {
        //push new-data to allUsers array
        const updateUser = JSON.parse(updateData);
        
        //get email from request
        const updateEmail = updateUser.email;
  ```
    
- request က ပို့လာတဲ့ data ကို updateUser အဖြစ်လက်ခံလိုက်ပြီး ရလာတဲ့ dataထဲက email ကို updateEmail ထဲ သိမ်းထားလိုက်တာပါ။
```js
const isEmailexit = allUsers.find((user) => user.email === updateEmail);
```
- updateEmail နဲ့ allUsers array ထဲရှိ email တူတဲ့ဟာ ရှိမရှိ `array.find()` method ကို သုံးပြီး ရှာလိုက်တာပါ
```js
 if (isEmailexit) {
          //update new name
          isEmailexit.name = updateUser.name;
        }
```
- updateEmail နဲ့ allUsers array ထဲရှိ email တူတဲ့ဟာ ရှိခဲ့ရင် ထို array item  ထဲက name property ရဲ့ value ကို updateUser ထဲက name property ရဲ့ value နဲ့ အစားထိုး ပြောင်းလဲသတ်မှတ်ခိုင်းလိုက်တာပါ
```js
     res.writeHead(200, { "Content-Type": "application/json" });
        res.write(JSON.stringify(allUsers));
        return res.end();
```
- ဒါကတော့ အစားထိုး ပြင်ဆင်ပြီးသား ဖြစ်တဲ့ data ကို response ပြန်ထုတ်ပေးလိုက်တာပါ
### PUT method အတွက်ဆာဗာမှာ ပြင်ဆင်ထားပြီးဖြစ်ပါတယ်
- ဆာဗာကို run ထားပေးပြီး postman ကို ဖွင့်ပါ
- အရင်ဆုံး GET request လုပ်ကြည့်ပါက ဆာဗာမှာ ရှိနေတဲ့ data ကို ပြပေးမှာ ဖြစ်ပါတယ်

![enter image description here](https://raw.githubusercontent.com/Aungmyanmar32/msquare-fullstack-m2/main/ep21-1-1.jpg)
- ပြင်ချင်တဲ့ user ရဲ့ email ကို request body မှာ မှန်အောင်ရေးပေးရပါမယ်
- name နေရာမှာတော့ ပြင်လိုတဲ့ နာမည် ရေးထည့်ပေးထားရပါမယ်

![enter image description here](https://raw.githubusercontent.com/Aungmyanmar32/msquare-fullstack-m2/main/ep21-1-2.jpg)
- method မှာ PUT ကိုရွေးထားပေးပြီး request send လိုက်တဲ့အခါမှာတော့ output မှာ ပြင်လိုက်တဲ့ name ကို မြင်ရရင် PUT  လုပ်ခြင်း အောင်မြင်ပါတယ်။

![enter image description here](https://raw.githubusercontent.com/Aungmyanmar32/msquare-fullstack-m2/main/ep21-1-3.jpg)

##
### DELETE data from server (using Postman)
- DELETE method က ဆာဗာမှာ ရှိပြီးသားdata ကို delete လိုတဲ့အခါ အသုံးပြုပါတယ်
- နမူနာမှာတော့ ဆာဗာမှာ ရှိပြီးသား user email နဲ့ request ကပို့လိုက်တဲ့ email တို့ 
တူမတူ တိုက်ဆိုင်စစ်ဆေးပြီး တူလာခဲ့ရင် request ကပို့လိုက်တဲ့ name ကို ဆာဗာ က
data ကို delete  လုပ်လိုက်မှာ ဖြစ်ပါတယ်
- PUT  method ရဲ့ အဆုံးမှာ DELETE method ကို ဆက်ရေးပါမယ်
### server.js
```js
else if (method === "DELETE") {
      //DELETE method

      //get data from front-end
      let updateData = "";
      req.on("data", (chunk) => {
        updateData += chunk;
      });

      req.on("end", () => {
        //push new-data to allUsers array
        const updateUser = JSON.parse(updateData);
        const updateEmail = updateUser.email;
        const isEmailexit = allUsers.find((user) => user.email === updateEmail);

        if (isEmailexit) {
          const deleteIndex = allUsers.indexOf(isEmailexit);
          allUsers.splice(deleteIndex, 1);
        }
        // response updated allUsers array to front-end
        res.writeHead(200, { "Content-Type": "application/json" });
        res.write(JSON.stringify(allUsers));
        return res.end();
      });
    }
```
 `else if (method === "DELETE")`
- DELETE method ဖြစ်ခဲ့ရင် အထဲက ကုဒ်တွေ run ပေးပါလို့ သတ်မှတ်လိုက်တာပါ။
```js
  let updateData = "";
      req.on("data", (chunk) => {
        updateData += chunk;
      });

      req.on("end", () => {
        //push new-data to allUsers array
        const updateUser = JSON.parse(updateData);
        
        //get email from request
        const updateEmail = updateUser.email;
  ```
    
- request က ပို့လာတဲ့ data ကို updateUser အဖြစ်လက်ခံလိုက်ပြီး ရလာတဲ့ dataထဲက email ကို updateEmail ထဲ သိမ်းထားလိုက်တာပါ။
```js
const isEmailexit = allUsers.find((user) => user.email === updateEmail);
```
- updateEmail နဲ့ allUsers array ထဲရှိ email တူတဲ့ဟာ ရှိမရှိ `array.find()` method ကို သုံးပြီး ရှာလိုက်တာပါ
```js
  if (isEmailexit) {
          const deleteIndex = allUsers.indexOf(isEmailexit);
          allUsers.splice(deleteIndex, 1);
        }
```
- updateEmail နဲ့ allUsers array ထဲရှိ email တူတဲ့ဟာ ရှိခဲ့ရင် ထို array item  ကို
array.splice() method နဲ့ remove လုပ်လိုက်တာဖြစ်ပါတယ်
```js
     res.writeHead(200, { "Content-Type": "application/json" });
        res.write(JSON.stringify(allUsers));
        return res.end();
```
- ဒါကတော့ removeလုပ်ပြီးသား ဖြစ်တဲ့ data ကို response ပြန်ထုတ်ပေးလိုက်တာပါ
### DELETE method အတွက်ဆာဗာမှာ ပြင်ဆင်ထားပြီးဖြစ်ပါတယ်

- ဖျက်ချင်တဲ့ user ရဲ့ email ကို request body မှာ မှန်အောင်ရေးပေးရပါမယ်
- koko2@web.de email ရှိတဲ့ user ကို ဖျက်ချင်တာမလို့ request body ထဲ အဆိုပါ emial ကို ထည့်ပေးလိုက်တာပါ။


![enter image description here](https://raw.githubusercontent.com/Aungmyanmar32/msquare-fullstack-m2/main/ep21-1-4.jpg)

- method မှာ DELETE ကို ရွေးပြီး request send လိုက်ပါက output မှာ ဖျက်လိုက်တဲ့ user မရှိတော့တာကို တွေ့ရမှာ ဖြစ်ပါတယ်။

![enter image description here](https://raw.githubusercontent.com/Aungmyanmar32/msquare-fullstack-m2/main/ep21-1-5.jpg)

##
### TRY THIS
-အခုဆိုရင် GET/POST/PUT/DELETE method ကို အသုံးချတက်ပြီမလို့  
1. Postman ကနေမဟုတ်ပဲ UI ( front-end) ကနေ GET/POST/PUT/DELETE method တွေကို fetch နဲ့ သုံးပြီး လုပ်ကြည့်ကြပါ။
2. ဆာဗာက data တွေကိုလဲ UI မှာ ပြပေးနိုင်အောင် လုပ်ကြည့်ကြပါ။

![enter image description here](https://raw.githubusercontent.com/Aungmyanmar32/msquare-fullstack-m2/main/ep21-1-res.png)

- [source code  for summary (server.js only)](https://github.com/Aungmyanmar32/msquare-fullstack-m2/blob/main/server.js)
