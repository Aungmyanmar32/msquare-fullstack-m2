## MSquare Programing Fullstack Course
### Episode-*19* Summary for (group 2) 

ဒီနေ့သင်တန်းမှာတော့ <br>
### classList.add()
### crateElement
### append
အကြောင်း လေ့လာသွားပါမယ်။
##
### အထက်ပါ အကြောင်းအရာတွေကို လေ့လာရင်း Google Meet UI လေး လုပ်ကြည့်သွားရအောင်

- အရင်ဆုံး html ဖိုင်တစ်ခု လုပ်ပါမယ်
### index.html
```html
<!DOCTYPE  html>
<html  lang="en">

<head>
 <meta charset="UTF-8"  />
 <meta http-equiv="X-UA-Compatible" content="IE=edge"  />
 <meta name="viewport" content="width=device-width, initial-scale=1.0"  />
 <link rel="stylesheet" href="style.css" />
 <title>Google Meet</title>
</head>

<body>
 <div class="usersDiv"></div>

 <script src="script.js"></script>
</body>

</html>
```
- head tag အထဲမှာ style.css ကို link ချိတ်ထားပါတယ်
- body tag  အထဲမှာတော့ usersDiv  ဆိုတဲ့ div  တစ်ခု လုပ်ထားပါတယ်။
- script.js  ဆိုတဲ့ javascript file ကိုလဲ ချိတ်ထည့်ထားပါတယ်။
## 
- ထပ်ပြီး script.js ဖိုင်တစ်ခု လုပ်ပါမယ်
- ပြီးရင် အောက်က ကုဒ်လေးရေးလိုက်ပါတယ်
### script.js
```js
const  usersDiv = document.querySelector(".usersDiv");
const  allUsers =[
{id:  1, name:"Aung"},
{id:  2, name:"Kyaw"},
{id:  3, name:"Maung"},
{id:  4, name:"Aye"},
{id:  5, name:"tun"},
]
```
> ရှင်းလင်းချက်
```js
const  usersDiv = document.querySelector(".usersDiv");
```
- ဒါကတော့ html ထဲက usersDiv ဆိုတဲ့ div ကို javascript ကနေ လှမ်းယူလိုက်တာပါ။
---
```js
const  allUsers =[
{id:  1, name:"Aung"},
{id:  2, name:"Kyaw"},
{id:  3, name:"Maung"},
{id:  4, name:"Aye"},
{id:  5, name:"tun"},
]
```
- array တစ်ခု လုပ်ပြီး allUsers ဆိုတဲ့ variable ထဲ သိမ်းထားတာပါ။
array ထဲ object  တွေမှာ id နဲ့ name ဆိုပြီး properties နှစ်ခု ပါပါတယ်

##
- အခု ကျနော်တို့က div တစ်ခု create လုပ်ပြီး allUsers Array  ထဲက name  တွေ ထည့်ကာ
လှမ်းယူထားတဲ့ html ဖိုင်ထဲက usersDiv ထဲ ပေါင်းထည့်ကြည့်ရအောင်..

### script.js
```js
const  usersDiv = document.querySelector(".usersDiv");
const  allUsers =[
{id:  1, name:"Aung"},
{id:  2, name:"Kyaw"},
{id:  3, name:"Maung"},
{id:  4, name:"Aye"},
{id:  5, name:"tun"},
]

//create new div and append to html
for (let  i = 0; i < allUser.length; i++) {
 const userDiv = document.createElement("div");
 userDiv.textContent = allUsers[i].name;
 
 usersDiv.append(userDiv);
 }
```
> ရှင်းလင်းချက်
```js
const userDiv = document.createElement("div");
```
- userDiv ဆိုတဲ့ div element အသစ်တစ်ခု ဖန်တီးလိုက်တာပါ
- ---
```js
userDiv.textContent = allUsers[i].name;
```
- အသစ်လုပ်ထားတဲ့ userDiv  ထဲ allUsers Array ထဲက name တွေကို စာအဖြစ်ထည့်ပေးလိုက်တာပါ။
---
```js
usersDiv.append(userDiv);
```

- အသစ်လုပ်ထားတဲ့ userDiv ကို  html က လှမ်းယူထားတဲ့ usersDiv ထဲ ထည့်ပေးလိုက်တာပါ
- ---
```js
for (let  i = 0; i < allUser.length; i++) {
 const userDiv = document.createElement("div");
 userDiv.textContent = allUsers[i].name;
 
 usersDiv.append(userDiv);
 }
```
- allUsers Array ထဲ ရှိသမျှ name တွေ လိုချင်တာမလို့ for loop ထဲ ထည့်ပြီး loop လုပ်ထားတာပါ
### index.html ကို Go live (live server) နဲ့ ဖွင့်ကြည့်တဲ့ အခါ အောက်ပါအတိုင်း မြင်ရမှာ ပါ။

![enter image description here](https://raw.githubusercontent.com/Aungmyanmar32/msquare-fullstack-m2/main/ep19-1.jpg)
##
### Javascript ထဲမှ create လုပ်ထားသော html element များကို css ဖြင့် style လုပ်ခြင်း

- Javascript ထဲမှ create လုပ်ထားသော html element များကို css ဖြင့် style လုပ်ရန် class name ပေးရန် လိုအပ်ပါသည်။
### script.js
```js
const  usersDiv = document.querySelector(".usersDiv");
const  allUsers =[
{id:  1, name:"Aung"},
{id:  2, name:"Kyaw"},
{id:  3, name:"Maung"},
{id:  4, name:"Aye"},
{id:  5, name:"tun"},
]

//create new div and append to html
for (let  i = 0; i < allUser.length; i++) {
 const userDiv = document.createElement("div");
 userDiv.textContent = allUsers[i].name;
 //add class name
 userDiv.classList.add("userDiv");
 
 usersDiv.append(userDiv);
 }
```
> ရှင်းလင်းချက်
```js
userDiv.classList.add("userDiv");
```
- create လုပ်ထားတဲ့ userDiv ကို class = "userDiv" ဆိုပြီး ပေးလိုက်တာပါ
- အခုဆို css မှာ class name နဲ့ style ချလို့ ရပါပြီး
- ---
- style.css ဆိုတဲ့ ဖိုင်တစ်ခု လုပ်ပါ
- အောက်က ကုဒ်တွေ ရေးထည့်ပေးပါ။
### style.css
```css
.usersDiv {
width: 100vw;
display: flex;
justify-content: center;
flex-wrap: wrap;
}

.userDiv {
width: 200px;
height: 200px;
background-color: #0d1117;
color: aqua;
text-align: center;
margin: 5px;
}
```
![enter image description here](https://raw.githubusercontent.com/Aungmyanmar32/msquare-fullstack-m2/main/ep19-2.jpg)

- userDiv မှာ ဘေးအနားလေးတွေ လုံးလုံးလေးဖြစ်ချင်လို့ border-radius ထပ်ပေးပါမယ်။
### style.css
```css
.usersDiv {
width: 100vw;
display: flex;
justify-content: center;
flex-wrap: wrap;
}

.userDiv {
width: 200px;
height: 200px;
background-color: #0d1117;
color: aqua;
text-align: center;
margin: 5px;
border-radius: 10px; /*new code added*/
}
```
![enter image description here](https://raw.githubusercontent.com/Aungmyanmar32/msquare-fullstack-m2/main/ep19-3.jpg)

---
### create လုပ်ထားတဲ့ userDiv ထဲ ပုံ ထပ်ထည့်ကြည့်ရအောင်
### script.js
```js
const  usersDiv = document.querySelector(".usersDiv");
const  allUsers =[
{id:  1, name:"Aung"},
{id:  2, name:"Kyaw"},
{id:  3, name:"Maung"},
{id:  4, name:"Aye"},
{id:  5, name:"tun"},
]

//create new div and append to html
for (let  i = 0; i < allUser.length; i++) {
 const userDiv = document.createElement("div");
 userDiv.textContent = allUsers[i].name;
 //add class name
 userDiv.classList.add("userDiv");

const img = document.createElement("img");
img.src ="https://raw.githubusercontent.com/Aungmyanmar32/google-meet-exercises/main/img0.jpg";

userDiv.append(img);
 
 usersDiv.append(userDiv);
 }

```
>ရှင်းလင်းချက်
```js
const img = document.createElement("img");
img.src ="https://raw.githubusercontent.com/Aungmyanmar32/google-meet-exercises/main/img0.jpg";

```
-img element တစ်ခု အသစ်လုပ်လိုက်တာဖြစ်ပြီး  ထို img ရဲ့ source ကို ပုံတစ်ပုံထည့်ပေးလိုက်တာပါ

```js
userDiv.append(img);
```
- create လုပ်ထားတဲ့ img ကို userDiv ထဲ ထည့်ပေးလိုက်တာပါ

![enter image description here](https://raw.githubusercontent.com/Aungmyanmar32/msquare-fullstack-m2/main/ep19-4.jpg)
##
### Try it
အောက်ပါ ပုံမှာ css နဲ့ ရလာတဲ့ ရလဒ်ကို တွဲပြထားပါတယ်
- အသစ်ထည့်ထားသော css တွေကို လေ့လာကြည့်ပါ။
- css ကို အမျိုးမျိုး စမ်းကြည့်ပါ။
- ပုံတွေ ထည့်စမ်းကြည့်ပါ။
---
![enter image description here](https://raw.githubusercontent.com/Aungmyanmar32/msquare-fullstack-m2/main/ep19-5.jpg)

![enter image description here](https://raw.githubusercontent.com/Aungmyanmar32/msquare-fullstack-m2/main/ep19-6.jpg)
