## My fit gallery
---

### keywords
- frontend
- dom inspector
- html
- basic javascript

### question
ลองหาวิธีดึง image url ที่อยู่ในหน้า index ของ https://unsplash.com/ ขึ้นมาโดย
- หาวิธีในการ inspect ดูว่า url ของรูปถูกเก็บไว้แบบไหน จากหน้าจอเราจะดึง url ของรูปได้ยังไง ให้เขียนอธิบายวิธีการ inspect มาแบบพออ่านเข้าใจครับ
- เขียน javascript อย่างง่ายเพื่อหา source url ของรูปในหน้า index และแสดงผลตาม example หรือใกล้เคียง โดยพิจารณาจาก code 2 function
  - function ในการ query dom เพื่อหา source set
  - function ในการ normalize result เพื่อให้ผลลัพธ์ตามที่โจทย์ต้องการ (ดูจากตัวอย่าง result ด้านล่าง) (+3)
- ใน 1 รูปจะมีรูปที่มีความละเอียดต่างกัน ลองหาวิธีในการเขียนเงื่อนไขในการ เลือกรูปที่เหมาะกับหน้าจอ (+3) 
  - เช่น เมื่อใช้หน้าจอ desktop mode ที่มี width = 1080p ความละเอียดรูปที่เหมาะสมคือ 1080w หรือใกล้เคียงเช่น 1000w, หรือ 1200w ก็ได้ถ้าหาก source นั้นไม่มี width ที่ใกล้เคียง 


### example result
query all image from index page:
```javascript
[
  [
    'photo-1618411474625-4d1f95265202',
    [
      { 100w: 'https://images.unsplash.com/photo-1618411474625-4d1f95265202?ixid=MnwxMjA3fDB8MHxlZGl0b3JpYWwtZmVlZHw5MXx8fGVufDB8fHx8&ixlib=rb-1.2.1&auto=format&fit=crop&w=100&q=60' },
      { 200w: 'https://images.unsplash.com/photo-1618411474625-4d1f95265202?ixid=MnwxMjA3fDB8MHxlZGl0b3JpYWwtZmVlZHw5MXx8fGVufDB8fHx8&ixlib=rb-1.2.1&auto=format&fit=crop&w=200&q=60' },
      { 300w: 'https://images.unsplash.com/photo-1618411474625-4d1f95265202?ixid=MnwxMjA3fDB8MHxlZGl0b3JpYWwtZmVlZHw5MXx8fGVufDB8fHx8&ixlib=rb-1.2.1&auto=format&fit=crop&w=300&q=60' },
      { 400w: 'https://images.unsplash.com/photo-1618411474625-4d1f95265202?ixid=MnwxMjA3fDB8MHxlZGl0b3JpYWwtZmVlZHw5MXx8fGVufDB8fHx8&ixlib=rb-1.2.1&auto=format&fit=crop&w=400&q=60' },
      ...
    ]
  ],
  [
    'photo-1618411474625-4d1f9526...',
    [...]
  ]
]
```

query only window.width = '320px'
```javascript
[
  [
    'photo-1618411474625-4d1f95265202',
    [
      { 300w: 'https://images.unsplash.com/photo-1618411474625-4d1f95265202?ixid=MnwxMjA3fDB8MHxlZGl0b3JpYWwtZmVlZHw5MXx8fGVufDB8fHx8&ixlib=rb-1.2.1&auto=format&fit=crop&w=300&q=60' },
      ...
    ]
  ],
  [
    'photo-1618411474625-4d1f9526...',
    [...]
  ]
]
```