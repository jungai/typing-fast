## I Got Wrong TZ
---

### keywords
- datetime
- timezone tz
- json date
- mysql date
- mysql timestamp
- mysqljs

### question
เรื่องมีอยู่ว่า ผู้ใช้งานแจ้งผู้พัฒนาโปรแกรมว่า เจอ buggg แก้ให้หน่อย ทำไมเวลามันเพี้ยนนน จบ

เข้าเรื่อง เรามีตัวละครคือ client หรือ client browser ผู้ซึ่งอยู่ทั่วโลก แน่นอนว่าแต่ละพื้นที่ หรือแต่ละประเทศอยู่คนละ time zone กัน และเราก็มี server ผู้ที่เป็นคนเก็บข้อมูลของ client เอาไว้ ซึ่ง server นี้แม้ตัวจะอยู่ที่ไหนไม่สำคัญแต่เราตั้งเวลา GMT+7 เอาไว้ 

ปัญหา 
client บอกผู้พัฒนาโปรแกรมว่า นายๆ ทำไมเราเห็นเวลาอนาคตอ่ะ เรามั่นใจว่าเวลาที่เราส่งให้นาย มันเป็นเวลา "17.00" ตามเวลา 24hr ทำไมตอนนายตอบกลับเรามาทำไมเป็น "00.00" ของอีกวันอ่ะ

ที่นี้เรามาดูสิ่งที่ client กับ server คุยกัน

preset:
client timezone = Asia/Bangkok (GMT+7)
server timezone = Asia/Bangkok (GMT+7)
server mysql client timezone = Z
mysql database timezone = Asia/Bangkok (GMT+7)

case 1: display 
```bash
# client make GET http request to server

# server response
echo {
    "created_dt": "2021-04-19T17:00:00.000Z"
}

# client display date with new Date(response.created_dt) = 2021-04-20T00:00:00.000+07:00
```

จากปัญหานี้ เราอยากให้อธิบายว่าปัญหานี้ข้อผิดพลาดเกิดจากอะไร เพราะอะไร แล้วเราควรจะแก้ไขแบบไหนดี 