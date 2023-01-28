## MSquare Programing Fullstack Course
### Episode-21 *Summary*

ဒီနေ့သင်တန်းမှာတော့ 

 - **Promise chaining**
 - **Promise hell**
 - **fetch**
 
 <br>စတာတွေအကြောင်း လေ့လာသွားမှာပါ။
 ##
 
- Promise တစ်ခု resolve ဖြစ်တဲ့အခါ .then ထဲက callback function က အလုပ်လုပ်ပြီး promise တစ်ခုကို return ပြန်ထုတ်ပေးတယ်ဆိုပါစို့။
- ထို ပြန်ထုတ်ပေးတဲ့ promise ကို ဆက်ပြီး .then . catch နဲ့ ဆက်ပြီး ချိတ်ဆက်အသုံးပြုတာကို promise chaining လို့ ခေါ်ပါတယ်
>Enample
```js
new Promise((resolve,reject) =>{
  resolve("this is reslove 1")
}).then((data)=>{
  console.log(data)
  new Promise((resolve,reject) =>{
    resolve("this is reslove 2")
  }).then((data)=>{
    console.log(data)
    new Promise((resolve,reject) =>{
      resolve("this is reslove 3")
    }).then((data)=>{
      console.log(data)
      new Promise((resolve,reject) =>{
        resolve("this is reslove 4")
      }).then((data)=>{
        console.log(data)
      }).catch(error =>{
        console.log(error)
      })
    }).catch(error =>{
      console.log(error)
    })
  }).catch(error =>{
    console.log(error)
  })
}).catch(error =>{
  console.log(error)
})
//output 1: this is reslove 1
//output 2: this is reslove 2
//output 3: this is reslove 3
//output 4: this is reslove 4
```
- အထက်ပါ ကုဒ်ကို လေ့လာကြည့်ပါက ရှုပ်ထွေးနေပြီး နားလည်ရ ခက်စေပါတယ်။
ဒီလို .then .catch တွေနဲ့ ရှုပ်ထွေးနေတဲ့ promise  ကို **promise hell** လို့ ခေါ်ပါတယ်။
- coding မှာ promise hell, callback hell , if/esle hell တွေ ရှိနေရင် ကောင်းမွန်တဲ့ code တစ်ခုလို့
သတ်မှတ်လို့ မရပါဘူး။ Coding လုပ်သူကိုယ်တိုင် နားလည်ရခက်စေပြီး အခြားသူများလဲ ကြည့်ရှုစစ်ဆေးရန် အဆင်မပြေ ဖြစ်ရပါတယ်။ 
- ကောင်းမွန်တဲ့ code တစ်ခုဆိုတာ ယေဘုယျ အားဖြင့်
1. clean and clear ဖြစ်ရပါမယ်
2. code တွေ ထပ်နေတာမျိုး မဖြစ်သင့်ပါဘူး (***DRY***- **D**on't **R**epeat **Y**ourself)
3. မိမိကိုယ်တိုင်သာမက အခြားသူများလဲ နားလည်ရ လွယ်စေမယ့် ပုံစံမျိုးလဲ ဖြစ်ရပါမယ်
- Promise Hell ကို ဖြေရှင်းရန် async/await function ကို အသုံးပြုလေ့ရှိပါတယ်
>(မှတ်ချက် ။   ။ async/await function အသုံးပြုပုံကို နောက်သင်ခန်းစာတွင် မျှော်...)
## 
### fetch
### fetch ဆို javascript မှာ အသင့်ပါလာတဲ့ method တစ်ခုဖြစ်ပါတယ်
### fetch မှာ
- server  ကနေ data တွေ လှမ်းယူခြင်း (**GET** method)
- server  ဆီသို့ data အသစ်တွေ ပို့ခြင်း(**POST** method)
- server  က data တွေကို ပြင်ဆင်ခြင်း(**PUT** method)
- server  က data တွေကို ဖျက်ခြင်း(**DELETE** method)
- စတဲ့ အဓိက method တွေ အပြင် အခြား အသုံး၀င်တဲ့ method တွေ ပါ၀င်ပါတယ်။
#### `Ftech` ကို back-end server နဲ့ ချိတ်ဆက်ပြီး data တွေ request လုပ်တဲ့အခါ အသုံးပြုလေ့ရှိကြပါတယ်။

-**fetch() method** က **promise တစ်ခုကို return** ပြန်ပေးပါတယ်။<br>
-**promise တစ်ခုကို return** ပြန်ပေးတဲ့အခါ  ယေဘုယျ အနေနဲ့ **resolve ကို auto သတ်မှတ်**ပေးပါတယ်။


#### Syntax

    fetch(url,{method});

#### Usage
```js
const url ='https://fakestoreapi.com/products'
fetch(url)
  .then((response) => response.json())
  .then((data) => console.log(data));
  
  //(20) [{…}, {…}, {…}, {…}, {…}, {…}, {…}, {…}, {…}, {…}, {…}, {…}, {…}, {…}, {…}, {…}, {…}, {…}, {…}, {…}]
```
>  ရှင်းလင်းချက်
```js
const url ='https://fakestoreapi.com/products'
```
- api server တစ်ခုရဲ့ လိပ်စာကို url variable အနေနဲ့ သိမ်းလိုက်တာပါ။

```js
fetch(url)
```
- ခုနက သိမ်းထားတဲ့ url ကနေ GET methodနဲ့ data လှမ်းယူလိုက်တာပါ
( fetch မှာ method ကို မထည့်ထားဘူးဆိုရင် default အနေနဲ့ GET method ဖြစ်ပါတယ်)
- fetch က fulfill promise(`resolve`) တစ်ခု return ပြန်ပေးတာမလို့ `.then()` သုံးလို့ရပါပြီ
```js
.then((response) => response.json())
```
- fetch က return ပြန်လာတဲ့ promise(response) ကို  လက်ခံလိုက်ပြီး
ထို response ထဲမှာ ပါလာတဲ့ json() method ကို အသုံးပြုလိုက်တာပါ
- ဒီ `.then` ကလဲ promise တစ်ခုကို return ပြန်ထုတ်ပေးပါတယ်။
```js
.then((data) => console.log(data));
```
- အထက်က ( .then ) က return ပြန်လာတဲ့ promise(data) ကို  လက်ခံလိုက်ပြီး
ထို data ထဲမှာ ရလာတဲ့ အချက်အလက်တွေကို console log ထုတ်လိုက်တာဖြစ်ပါတယ်။
##
### Using fetch and thrown error

```js
const url ="https://fakestoreapi.com/productsdfdfdsafdsa";
 
 fetch(url)
 .then((response) => {
      response.json().then((data) => {
          console.log(data);
        }).catch((err) => {
          console.log("Inside catch...", err);
        });
    }).catch((err) => {
      console.log("Outside catch: ", err);
    });
```
>Try it

    
ကျနော်တို့က url link ကို အမှားကြီး ပေးထားပြီး 
1. catch() နှစ်ခုမှာ log နှစ်မျိုး ထုတ်ထားပါတယ်။
2. ပထမ console.log ကို .then တစ်ခုထဲ ထည့်ထားပါတယ်
3. ဒုတိယ console.log ကိုတော့ .then အနောက်မှာ လုပ်ထားပါတယ်

- အထက်ပါ code ကို စမ်းကြည့်တဲ့ အခါ 
မည်သည့် error (or) console.log ပေါ်လာမယ်လို့ သင်ထင်ပါလဲ။
- အရင်ဆုံး ကုဒ်ကို မစမ်းကြည့်ပဲ ဒီအတိုင်းစဥ်းစားပြီး အဖြေထုတ်ကြည့်ပါ။

