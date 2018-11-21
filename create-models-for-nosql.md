#### 

# Full Stack Web Developer

## JavaScript \| Create Models for noSQL \(mongoDB\)

![](/assets/sign in with google group.png)

ปุ่ม "Sign in with Google" ที่เห็นสวยๆนี้ แยกการทำงานออกเป็น 2 ส่วนคือ

1. Front-End
2. Back-End

ที่เราเห็นเป็นโลโก้ หรือสีพื้นเป็น สีฟ้า หรือสีขาว เป็นการทำงานในส่วนของ Front-End ซึ่งไม่ได้กล่าวถึงในที่นี้ แต่บทความนี้จะขอกล่าวถึงในส่วนของ Back-End เท่านั้นก่อนครับ

ในส่วนของ Back-End แยกย่อยได้ดังนี้

1. ส่วนที่จัดการกับ Database
2. ส่วนของการประมวลผล \(เอาโค๊ดไปใส่ใน app.js\)

ขอเริ่มในส่วนที่ 1 การจัดการ Database โดยมี Environment ดังนี้

* ใช้ Database แบบ noSQL
* ใช้ noSQL ยี่ห้อ MongoDB

ลองดูโค๊ดนี้

```
import mongoose from 'mongoose';

const { Schema } = mongoose;

const mongoSchema = new Schema({
  googleId: {
    type: String,
    required: true,
    unique: true,
  },
  googleToken: {
    access_token: String,
    refresh_token: String,
    token_type: String,
    expiry_date: Number,
  },
  slug: {
    type: String,
    required: true,
    unique: true,
  },
  createdAt: {
    type: Date,
    required: true,
  },
  email: {
    type: String,
    required: true,
    unique: true,
  },
  isAdmin: {
    type: Boolean,
    default: false,
  },
  displayName: String,
  avatarUrl: String,

  isGithubConnected: {
    type: Boolean,
    default: false,
  },
  githubAccessToken: {
    type: String,
  },
});

const User = mongoose.model('User', mongoSchema);

export default User;
```

โค๊ดด้านบน ถ้านั่งดูเผินๆ มันดูเยอะไปหมด แล้วจะจำได้มั๊ยเนี่ย วิธีดูให้ดูแบบนี้

สมมุติเราซื้อสินค้ามาชิ้นหนึ่ง จำนวน 1 กล่อง 

1. ป้ายที่กล่องเขียนว่า "**mongoose**"
2. ในกล่องนั้นมีของเล่นอยู่ 2 ชิ้น ชิ้นที่ 1 เรียกว่า "**Schema**" ชิ้นที่ 2 เรียกว่า "**model**"

จากข้อมูลด้านบนเราพล็อตจากภาษามนุษย์ เป็นภาษา JavaScript ได้ดังนี้

```
mongoose.Schema;
mongoose.model;
```



