## MSquare Programing Fullstack Course
### Episode-*30* 
### Summary For `Room(1)` intermediate Class
##
### Upload file on Digital ocean
##
### Agriculture
- အပြင် လက်တွေ့မှာ project တစ်ခုကို web ပေါ်တင်တဲ့ အခါ
- - server တစ်ခုထဲမှာပဲ code တွေ file(image/video/music etc...) အကုန်လုံးကို စုပြုံတင်လေ့မရှိပဲ text  ( code/link etc..) သီးသန့် ကို server တစ်ခု ၊ file သီးသန့်ကို server တစ်ခု ခွဲတင်လေ့ရှိပါတယ်။
-  ခုလို ခွဲတင်လိုက်ခြင်းအားဖြင့် မိမိရေးလိုက်တဲ့ web app/site ကို ပိုမိုမြန်ဆန်စွာ manage လုပ်နိုင်ပြီး user များ အဆင်ပြေပြေ အသုံး'ပြုနိုင်မှာ ဖြစ်ပါတယ်
- file သီသန်းတင်တဲ့ server မှာ file တစ်ခုကို တင်လိုက်တာနဲ့ ထိုဖိုင်အတွက် link တစ်ခုကို ပြန်ထုတ်ပေးတာကြောင့် code သီးသန့် တင်တဲ့ ဆာဗာမှာ text အနေနဲ့ ထိုဖိုင်ကို ထည့်သွင်းအသုံးပြုနိုင်တာမလို့ loading time ကို သိသိသာသာ မြန်ဆန်စေမှာ ဖြစ်ပါတယ်

![enter image description here](https://raw.githubusercontent.com/Aungmyanmar32/msquare-fullstack-m2/main/digitaloce1.png)

##
### Using digital ocean space ( file upload server )
-  digital ocean space ဆိုတာ file upload service ပေးတဲ့ server တွေထဲက တစ်ခု ဖြစ်ပါတယ်။
- free ရတဲ့ service မဟုတ်ပဲ paid service တစ်ခုဖြစ်ပါတယ်
- အောက်က link က tutorial ကို ဖတ်ကြည့်ပြီး file upload အတွက် ကိုယ်တိုင်ရေးသားကြည့်ပါ။
https://www.digitalocean.com/community/tutorials/how-to-upload-a-file-to-object-storage-with-node-js
- tutorial ထဲမှာ ထည့်ပေးရမယ့် key တွေကို အောက်မှာ ရယူပါ
```properties
aws_access_key_id
aws_secret_access_key
bucket name တွေ ရယူရန် ကိုအောင်မြန်မာ (သို့မဟုတ်) ဆရာ့ဆီ ဆက်သွယ်ပါ
```
မှတ်ချက် ။   ။  tutorial ကို ဖတ်ကြည့်ပြီး file upload အတွက် ကိုယ်တိုင်ရေးသားရမှာဖြစ်လို့ ကြိုးစားပြီး ရေးကြည့်ကြပါ။
## အဆင်မပြေတဲ့ သူများ [ဒီမှာ](https://node-express-tuto.vercel.app/) ကြည့်ပါ
### [Source Code](https://github.com/Aungmyanmar32/space-node-app)
