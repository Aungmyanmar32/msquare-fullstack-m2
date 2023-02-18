## MSquare Programing Fullstack Course
### Episode-*31* 
### Summary For `Room(1)` intermediate Class
##
### Connect Github Repo to  *`Cloud-base Virtual machines`* (Digital Ocean Droplet)
##
- အရင်ဆုံး GitHub repo ရဲ့ personal access token တစ်ခု generate လုပ်ပေးရပါမယ်။
- GitHub user profile ပုံ အောက်က setting ကို သွားပါ
- developer setting ထဲထပ်၀င်ပါ
- personal token မှာ token (classic) ကိုရွေးပါ။
- generate new token မှာ generate new token(classic) ကို ထပ်ရွေးပါ။
- Note မှာ တစ်ခုခုရေးထည့်ပြီး repo မှာ အကုန် ရွေးပေးကာ generateလုပ်ရင် token တစ်ခု ရလာမှာဖြစ်ပါတယ်။

![enter image description here](https://raw.githubusercontent.com/Aungmyanmar32/msquare-fullstack-m2/main/dodtoken.png)
- DOD server ထဲ SSH ဖြင့် ၀င်ပါ
- ### IP address and password ဆရာ့ဆီမှာ မေးပါ။
- မိမိရဲ့ folder ထဲ ထပ်၀င်ပါ
- github repo ကို personal token နဲ့ clone ရန် link ကို အောက်ပါအတိုင်း လုပ်ပေးပြီး DOD မှ မိမိရဲ့ folder ထဲ clone ထည့်ပေးပါ။
```properties
https://oauth2:<your-token>@github.com/<Username>/<repository-name>.git
```
##
### React ( intro)
### Create react project
- github repo တစ်ခုကို readme နဲ့ create လုပ်ပါ
- ထို repo ကို local ထဲ clone လိုက်ပါ.
- ရလာတဲ့ folder ထဲ မှာ react ကို ထည့်ပါမယ်
- ရလာတဲ့ folderကို vs cdoe မှာ ဖွင့်ထားပါ။
- new terminal ကို ဖွင်ပြီး 
```properties
npx create-react-app my-app
```
- ရိုက်ထည့်ပေးပါ
- my-app ဆိုတဲ့ နေရာမှာ မိမိစိတ်ကြိုက် project နာမည် ထည့်လို့ရပါတယ်
- အချိန်အနည်းငယ် စောင့်ပြီးပါက react ကို ထည့်လို့ပြီးပါပြီး။

![enter image description here](https://raw.githubusercontent.com/Aungmyanmar32/msquare-fullstack-m2/main/react1.png)
- react ကို browser ပေါ်မှာ ဖွင့်ရန်အတွက်  my-app folder ထဲ  သွားပါမယ်
```properties
cd my-app
```
- npm start ကို ထည့်ပြီး enter ခေါက်ပေးလိုက်ပါ။
```properties
npm start
```
![enter image description here](https://raw.githubusercontent.com/Aungmyanmar32/msquare-fullstack-m2/main/react2.png)
- browser က auto ပွင့်လာပြီး react logo ပြပေးနေပါက react project တစ်ခု စတင်တာ ပြီးပါပြီး။
