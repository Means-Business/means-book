#### 

# Full Stack Web Developer

## JavaScript \| Create Models for noSQL \(mongoDB\)

![](/assets/sign in with google group.png)

ปุ่ม "Sign in with Google" ที่เห็นสวยๆนี้ มันมีการทำงานแยกได้เป็น 2 ส่วนคือ

1. Front-End
2. Back-End

ที่เราเห็นเป็นโลโก้ หรือสีพื้นเป็น สีฟ้า หรือสีขาว เป็นการทำงานในส่วนของ Front-End ซึ่งไม่ได้กล่าวถึงในที่นี้ แต่บทความนี้จะขอกล่าวถึงในส่วนของ Back-End เท่านั้นครับ

ในส่วนของ Back-End แยกย่อยได้ดังนี้

1. ส่วนที่จัดการกับ Database
2. ส่วนของการประมวลผล \(เอาโค๊ดไปใส่ใน app.js\)

ขอเริ่มในส่วนที่ 1 การจัดการ Database โดยมี Environment ดังนี้

* ใช้ Database แบบ noSQL
* ใช้ noSQL ยี่ห้อ MongoDB
* สร้างแบบจำลองบน MongoDB โดยใช้ตัวช่วยชื่อว่า "**mongoose**"

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
2. ในกล่องนั้นมีของเล่นอยู่ 2 ชิ้น สมมุติ ชิ้นที่ 1 เรียกว่า "**Schema**" ชิ้นที่ 2 เรียกว่า "**model**"

จากข้อมูลด้านบนเราพล็อตจากภาษามนุษย์ เป็นภาษา JavaScript ได้ดังนี้

```
mongoose.Schema;
mongoose.model;
```

สมมุติต่อ เราแกะกล่องที่ชื่อ "**mongoose**" และเอาของเล่นทั้ง 2 ชิ้นมาใส่กล่องเล็กๆ 2 ใบ พล็อตเป็นภาษา JavaScript ได้ดังนี้

```
import mongoose from "mongoose"; // นำกล่องที่ชื่อ "mongoose" มาไว้บนตัก
const Schema = mongoose.Schema; // นำของเล่นชื่อ "mongoose.Schema" มาใส่ในกล่องเล็กๆชื่อว่า "Schema"
const User = mongoose.model; // นำของเล่นชื่อ "mongoose.model" มาใส่ในกล่องเล็กๆชื่อว่า "User"
```

> หมายเหตุ: const Schema = mongoose.Schema; สามารถลดรูปเป็น const { Schema } = mongoose;

สมมุติต่อ เราหยิบของเล่นที่ชื่อ "**Schema**" มาเล่น วิธีเล่นคือเราเอามานั่งปั้นเหมือนปั้นดินน้ำมันให้เป็นรูปตามที่เราต้องการ ในกรณีนี้เราต้องการปั้นเป็นห้อง ๆ หนึ่งเอาไว้เก็บคุณสมบัติของ "**User**" โดยพล็อตเป็นภาษา JavaScript ได้ดังนี้

```
// ขอเรียก "ปั้น" ในภาษามนุษย์ว่า "new" ในภาษา JavaScript
new Schema({
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
```

พอปั้นเสร็จก็เอาไปเก็บในกล่องชื่อว่า "**mongoSchema**"

```
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
```

พอเขียนโค๊ดเสร็จเราก็จับแต่หลักการ โดยในหัวเราจะมีแค่ภาพนี้

```
// สร้างแบบจำลองให้ Database
// นำกล่อง mongoose มาไว้บนตัก
import mongoose from 'mongoose';


// เปิดกล่อง mongoose ออกมาแล้วหยิบของเล่น Schema ไปใส่ในกล่องย่อยที่ชื่อ Schema
const { Schema } = mongoose;


const mongoSchema = new Schema({...}); // นำกล่องย่อยมาปั้นเล่นให้เป็น mongoSchema

// นำไปใช้ใน app.js
const User = mongoose.model('User', mongoSchema); // เวลาจะนำไปใช้ก็เก็บทั้งหมดใส่ในกล่องอีกครั้งตั้งชื่อใหม่ว่า User

export default User; // ส่งมอบกล่องที่ชื่อ User ให้เพื่อนเราที่ชื่อ app.js นำไปใช้
```

อธิบายเป็นภาษามนุษย์ดังนี้

1. นำกล่อง mongoose มาไว้บนตัก
2. เปิดกล่อง mongoose ออกมาแล้วหยิบของเล่นชิ้นที่ 1 คือ Schema ไปใส่ในกล่องย่อยที่ชื่อ Schema
3. นำกล่องย่อยมาปั้นเล่น พอปั้นเสร็จให้ชื่อว่า mongoSchema
4. mongoSchema ต้องเล่นร่วมกันกับของเล่นชิ้นที่ 2 ที่ชื่อว่า model ซึ่งมันมีวิธีเล่นคือ 1. ต้องมีป้ายชื่อ 2. เอา mongoSchema ที่เราเพิ่งปั้นเสร็จมาใส่เข้าไปใน model
5. พอเราประกอบร่างของเล่น 2 ชิ้นเสร็จแล้ว ก็ส่งมอบให้ app.js ยืมไปเล่น



