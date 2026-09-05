# 🌴 Sabah Trip Itinerary — KK & Kundasang

## 📌 Project Overview

请制作一个现代化、适合手机和电脑浏览的 **Sabah Trip 行程可视化 HTML 页面**。

旅行地点主要包括：

- Kota Kinabalu（亚庇）
- Tanjung Aru Beach
- Gaya Street
- Kundasang
- Sosodikon Hill
- Desa Dairy Farm
- Spring Garden
- 其他沿途美食地点

网页主要使用 **中文（简体中文）**，但保留餐厅、地点和品牌的原文名称，例如：

- Yee Fung Laksa
- Fatt Kee
- Tanjung Aru Beach
- Desa Dairy Farm
- Sosodikon Hill
- Anooh Coffee

---

# 🎯 Main Goals

网页必须让用户可以非常直观地查看：

1. 每一天的完整行程
2. 每个活动的时间
3. 活动地点
4. 活动说明
5. 每个地点的图片
6. 点击地点直接打开 Google Maps
7. 航班信息
8. 航班倒计时
9. 每日行程 Timeline
10. 行李 / 必带物品 Checklist
11. KK → Kundasang → KK 的旅行路线
12. 未确定的行程使用 `待定` 标记
13. 每个活动可以显示预算 / 备注（如果以后需要扩展）

---

# 🖥️ Page Structure

建议整个网站设计成 Single Page Application / Single HTML Page。

页面结构：

```text
┌─────────────────────────────────────┐
│          🌴 SABAH TRIP              │
│       KK • Kundasang                │
│                                     │
│     ✈️ Flight Countdown             │
└─────────────────────────────────────┘

        ↓

┌─────────────────────────────────────┐
│ ✈️ 航班信息                         │
│ Senai → Kota Kinabalu               │
│ 3:10 PM → 5:30 PM                   │
│ Countdown                           │
└─────────────────────────────────────┘

        ↓

┌─────────────────────────────────────┐
│ 🗺️ Trip Route                       │
│                                     │
│ Johor → KK → Kundasang → KK         │
└─────────────────────────────────────┘

        ↓

┌─────────────────────────────────────┐
│ Day 1                               │
│ Timeline                            │
└─────────────────────────────────────┘

        ↓

│ Day 2                               │
│ Timeline                            │

        ↓

│ Day 3                               │
│ Timeline                            │

        ↓

│ Day 4                               │
│ Timeline                            │

        ↓

│ Day 5                               │
│ Timeline                            │

        ↓

┌─────────────────────────────────────┐
│ 🎒 Packing Checklist                │
└─────────────────────────────────────┘
```

---

# 🎨 Design Requirements

整体风格：

- Tropical
- Sabah travel
- 清爽
- 年轻
- 高级但不要过度复杂
- Mobile-first
- 卡片式设计
- 大量使用照片
- 圆角卡片
- 微妙阴影
- Smooth animation

建议视觉元素：

- 🌴 棕榈树
- 🌄 山景
- 🌊 海边
- ☕ 咖啡
- 🍜 美食
- ✈️ 飞机
- 📍 Location
- 📸 Photo

颜色建议：

```text
Primary:
Deep Green

Secondary:
Sky Blue

Accent:
Sunset Orange

Background:
Warm White / Light Beige

Text:
Dark Green / Dark Gray
```

不要让网页看起来像企业 Dashboard。

应该更像：

```text
Travel Journal
+
Interactive Itinerary
+
Trip Planner
```

---

# 📱 Responsive Design

必须支持：

- Desktop
- Tablet
- Mobile

Mobile 页面尤其重要。

手机上：

```text
Day 1 (16/9)
│
├── 3:10 PM
│   ✈️ 出发
│
├── 5:30 PM
│   🛬 抵达 KK
│
├── 6:00 PM
│   🍜 Dinner
│
└── 7:30 PM
    🏠 Check-in
```

不要把 Timeline 做成需要横向滚动的巨大表格。

---

# ✈️ Flight Information

页面顶部需要有一个明显的 Flight Card。

目前已知：

### Departure

```text
Senai Airport
Johor Bahru

3:10 PM
```

### Arrival

```text
Kota Kinabalu International Airport Terminal 1

5:30 PM
```

Flight：

```text
Senai → Kota Kinabalu
```

航空公司和航班号码目前未知，因此不要自行编造。

可以预留：

```text
Airline: 待填写
Flight No.: 待填写
Booking Ref: 待填写
```

---

# ⏳ Flight Countdown

需要加入 Countdown Component。

用户可以填写：

```javascript
const flightDateTime = "YYYY-MM-DDTHH:MM:SS+08:00";
```

网页自动计算：

```text
距离出发还有

03
Days

12
Hours

45
Minutes

20
Seconds
```

倒计时需要每秒更新。

Flight Countdown Card 应该是页面最明显的视觉元素之一。

如果旅行日期尚未提供，不要假设日期。

显示：

```text
✈️ 航班日期
待填写

添加日期后即可启动倒计时
```

---

# 🗺️ Google Maps Integration

每一个有明确地点的活动都必须可以点击。

点击后：

```text
📍 在 Google Maps 中打开
```

打开 Google Maps 对应地点。

例如：

```text
Tanjung Aru Beach
```

应该可以直接打开：

```text
https://www.google.com/maps/search/?api=1&query=Tanjung+Aru+Beach+Sabah
```

对于餐厅：

```text
Yee Fung Laksa
```

打开：

```text
https://www.google.com/maps/search/?api=1&query=Yee+Fung+Laksa+Kota+Kinabalu
```

不要把 Google Maps iframe 强行嵌入每一个 Card。

优先使用：

```text
📍 Google Maps
```

按钮。

---

# 📸 Image Requirements

每一个主要活动都应该支持一/多張图片。

例如：

```javascript
{
    time: "6:00 PM",
    title: "Dinner",
    location: "Kota Kinabalu",
    image: "...",
}
```

Card 中显示：

```text
┌─────────────────────────┐
│                         │
│       Activity Image    │
│                         │
├─────────────────────────┤
│ 6:00 PM                 │
│ 🍤 晚餐                 │
│                         │
│ 煮炒 / 海鲜             │
│                         │
│ 📍 Google Maps          │
└─────────────────────────┘
```

图片需要：

- 圆角
- `object-fit: cover`
- Responsive
- Lazy loading
- 图片加载失败时显示 placeholder

可以设计成：

```text
🌴 Sabah
图片暂不可用
```

---

# 🗓️ Itinerary

## Day 1 — 抵达亚庇 ✈️

### 3:10 PM
**出发**

📍 Senai Airport

说明：

```text
从 Senai Airport 出发前往 Kota Kinabalu。
```

---

### 5:30 PM
**抵达 KK**

📍 Kota Kinabalu International Airport Terminal 1

---

### 6:00 PM
**晚餐 🍤**

📍 Kota Kinabalu

选择：

```text
煮炒 / 海鲜
```

地点目前未确定。

显示：

```text
📍 地点待定
```

---

### 7:30 PM
**Homestay Check-in 🏠**

📍 Homestay

然后：

```text
休息
```

Homestay 地址目前未知。

---

# Day 2 — Kota Kinabalu City 🌊

## 9:00 AM
### 早餐 🍜

**生肉面**

📍 Sinsuran

---

## 10:30 AM
### Kota Kinabalu City Walk 🚶

路线：

```text
粉色清真寺
↓
水上清真寺
↓
Gaya Street
```

每一个地点都应该是独立 Activity Card。

---

## 12:00 PM
### 午餐 🍜

📍 Yee Fung Laksa

食物：

```text
Laksa
牛杂
```

---

## 2:00 PM
### Continue Gaya Street 🚶

继续探索：

```text
Gaya Street
```

可以加入：

```text
📸 拍照
🛍️ 逛街
🍜 小吃
```

---

## 3:00 PM
### 下午茶 ☕

候选：

```text
Mizumizu
Woo! Cafe
```

由于尚未确定最终选择，显示为：

```text
☕ 下午茶
Mizumizu / Woo! Cafe
```

---

## 6:00 PM
### Sunset 🌅

📍 Tanjung Aru Beach

这是 Day 2 的重点活动。

Card 应该使用较大的照片。

可以显示：

```text
🌅 Sunset
Golden Hour
```

---

## 7:00 PM
### Dinner 🦐

📍 大茄来

类型：

```text
海鲜
```

---

## 8:30 PM
### Shopping / Steamboat 🛍️🍲

活动：

```text
Shopping
Steamboat
```

地点：

```text
待定
```

---

# Day 3 — Kota Kinabalu → Kundasang 🏔️

## 10:00 AM
### Breakfast / Brunch 🍜

📍 Fatt Kee

食物：

```text
鱼肉粉
```

---

## 11:30 AM
### 前往 Kundasang 🚗

路线：

```text
Kota Kinabalu
        ↓
Tamparuli
        ↓
Kundasang
```

这是一个 Road Trip Segment。

可以显示：

```text
🚗 Road Trip
KK → Kundasang
```

---

# 🍮 Along the Way — Food Stops

沿途可以有多个可选停靠点。

### 椰子布丁 🥥

状态：

```text
沿途候选
```

---

### Tamparuli Mee 🍜

状态：

```text
沿途候选
```

---

### 烤山猪肉 + 木薯糕 🍖

状态：

```text
沿途候选
```

这些不要强制放入固定 Timeline。

可以设计为：

```text
🚗 沿途美食候选

[椰子布丁]
[Tamparuli Mee]
[烤山猪肉 + 木薯糕]
```

---

## 3:00 PM
### Desa Dairy Farm / Spring Garden 🌄

候选：

```text
Desa Dairy Farm
Spring Garden
```

备注：

```text
下午不一定可以看到神山。
```

这个备注需要明显显示，例如：

```text
⚠️ 温馨提醒
下午不一定能看到神山，
视天气及能见度而定。
```

---

## 6:00 PM
### Check-in 🏠

然后：

### Dinner 🍲

```text
火锅
```

📍 Homestay

---

# Day 4 — Kundasang Sunrise 🌄

## 5:30 AM
### Wake Up & 出发 🚗

---

## 6:00 AM
### 日出 🌅

📍 Sosodikon Hill

这是 Day 4 的重点活动。

使用大图片。

显示：

```text
🌄 Sunrise
Sosodikon Hill
```

---

## 8:00 AM
### Breakfast ☕

📍 Anooh Coffee

---

## 10:00 AM
### Desa Dairy Farm / Spring Garden 🐄🌸

候选地点：

```text
Desa Dairy Farm
Spring Garden
```

---

## 12:00 PM
### Lunch 🍴

📍 Rusa Selera

---

## 2:00 PM
### Afternoon Activity ❓

状态：

```text
待定
```

设计成一个可编辑的 Placeholder Card。

例如：

```text
┌────────────────────────┐
│ ❓ 下午行程            │
│                        │
│ 地点：待定             │
│ 活动：待定             │
│                        │
│ ✏️ 稍后补充            │
└────────────────────────┘
```

---

## 6:00 PM
### Dinner 🍴

地点：

```text
待定
```

---

# Day 5 — Return to KK ✈️

## 6:00 AM
### Homestay Sunrise + Breakfast 🌅

活动：

```text
日出
早餐
```

地点：

```text
Homestay
```

---

## 10:00 AM
### Check-out 🧳

---

## 12:30 PM
### Lunch 🍜

地点：

```text
待定
```

---

## 2:00 PM
### Afternoon Activity ❓

状态：

```text
待定
```

---

## 3:00 PM
### 前往机场 ✈️

Route：

```text
Kundasang / Kota Kinabalu
        ↓
Kota Kinabalu International Airport
```

---

# 🧭 Trip Route Visualization

需要有一个简化路线图。

不需要做真正的 GIS 地图。

可以使用：

```text
📍 Senai
   │
   ✈️
   ↓
📍 Kota Kinabalu
   │
   🚗
   ↓
📍 Tamparuli
   │
   ↓
📍 Kundasang
   │
   🚗
   ↓
📍 Kota Kinabalu Airport
```

可以使用 CSS / SVG 制作视觉化路线。

---

# 🗓️ Day Navigation

页面顶部或固定位置加入：

```text
[Day 1] [Day 2] [Day 3] [Day 4] [Day 5]
```

点击后自动滚动到对应日期。

Mobile 上可以使用 horizontal scrolling tabs。

例如：

```text
← Day 1 | Day 2 | Day 3 | Day 4 | Day 5 →
```

当前日期需要有明显 active state。

---

# 🎒 Packing Checklist

加入一个完整的：

# 🎒 Sabah Trip Packing List

使用 Checkbox。

---

## 📱 Important

- [ ] 手机
- [ ] 手机充电器
- [ ] Power Bank
- [ ] 充电线
- [ ] 耳机
- [ ] 身份证 / Passport
- [ ] 航班资料
- [ ] Homestay 资料
- [ ] 钱包
- [ ] 银行卡
- [ ] 现金

---

## 👕 Clothing

- [ ] T-shirt
- [ ] 长裤
- [ ] 短裤
- [ ] 内衣裤
- [ ] 睡衣
- [ ] 外套
- [ ] 薄长袖
- [ ] Socks
- [ ] Comfortable Shoes
- [ ] Slippers

---

## 🌄 Kundasang

因为 Kundasang 气温可能比 KK 低，需要特别提醒：

- [ ] 外套
- [ ] 长裤
- [ ] 保暖衣物
- [ ] Comfortable Shoes
- [ ] Socks

---

## 🌧️ Weather

- [ ] Umbrella
- [ ] Raincoat
- [ ] Waterproof bag
- [ ] Plastic bags

---

## 🧴 Personal Care

- [ ] Toothbrush
- [ ] Toothpaste
- [ ] Facial cleanser
- [ ] Shampoo
- [ ] Body wash
- [ ] Sunscreen
- [ ] Lip balm
- [ ] Tissue
- [ ] Wet tissue

---

## 📷 Travel

- [ ] Camera
- [ ] Camera battery
- [ ] Memory card
- [ ] Tripod
- [ ] Sunglasses
- [ ] Cap
- [ ] Reusable water bottle

---

# 💰 Optional Budget Section

可以预留一个 Budget Tracker。

例如：

```text
💰 Trip Budget

Flight          RM xxx
Homestay        RM xxx
Food            RM xxx
Transport       RM xxx
Activities      RM xxx
Shopping        RM xxx

Total           RM xxx
```

目前如果没有金额，不要自行填写。

---

# 📝 Notes

每一天都应该允许加入 Notes。

例如：

```text
📝 Day 2 Notes

________________________________

________________________________
```

如果使用 JavaScript，可以将 Notes 存储到：

```text
localStorage
```

这样用户刷新网页之后内容不会消失。

---

# 🧩 Activity Card Data Structure

建议所有行程使用统一的数据结构。

例如：

```javascript
const itinerary = [
  {
    day: 1,
    date: null,
    activities: [
      {
        time: "15:10",
        title: "出发",
        type: "flight",
        location: "Senai Airport",
        description: "从 Senai Airport 出发前往 Kota Kinabalu",
        image: null,
        mapsQuery: "Senai Airport"
      },
      {
        time: "17:30",
        title: "抵达 KK",
        type: "flight",
        location: "Kota Kinabalu International Airport Terminal 1",
        description: "抵达亚庇",
        image: null,
        mapsQuery: "Kota Kinabalu International Airport Terminal 1"
      }
    ]
  }
]
```

---

# 🖼️ Image Architecture

图片路径建议统一：

```text
/assets/images/
```

例如：

```text
/assets/images/day1/senai-airport.jpg
/assets/images/day2/gaya-street.jpg
/assets/images/day2/tanjung-aru.jpg
/assets/images/day3/kundasang.jpg
/assets/images/day4/sosodikon-hill.jpg
/assets/images/day4/desa-dairy-farm.jpg
```

如果图片不存在：

```javascript
onerror
```

显示 placeholder。

---

# 📍 Google Maps Helper

建议建立：

```javascript
function openGoogleMaps(query) {
    const url =
      `https://www.google.com/maps/search/?api=1&query=${encodeURIComponent(query)}`;

    window.open(url, "_blank");
}
```

Activity Card 统一使用：

```text
📍 在 Google Maps 中打开
```

---

# ⏱️ Countdown Implementation

建立独立：

```javascript
startCountdown(targetDate)
```

显示：

```text
DD : HH : MM : SS
```

当 Countdown 完成：

```text
✈️ 旅程开始！
```

---

# ✨ Animations

可以加入轻微动画：

- Card fade-in
- Timeline slide-in
- Hover effect
- Image zoom on hover
- Smooth scrolling
- Countdown number transition
- Checkbox animation

但不要使用过度复杂的动画。

---

# 🌐 Technology

如果没有特殊限制，建议：

```text
HTML
CSS
JavaScript
```

优先制作成可以直接打开的：

```text
index.html
```

不要要求 backend。

可以使用：

```text
HTML
CSS
Vanilla JavaScript
SVG
LocalStorage
```

如果使用 framework，则优先：

```text
React / Next.js
```

但项目应该保持简单。

---

# 📁 Suggested Project Structure

```text
sabah-trip/
│
├── index.html
│
├── css/
│   └── style.css
│
├── js/
│   ├── itinerary.js
│   ├── countdown.js
│   ├── maps.js
│   └── checklist.js
│
├── assets/
│   └── images/
│       ├── day1/
│       ├── day2/
│       ├── day3/
│       ├── day4/
│       └── day5/
│
└── README.md
```

---

# ⚠️ Important Rules

1. **不要自行编造航班号码**
2. **不要自行编造旅行日期**
3. **不要自行编造 Homestay 地址**
4. 未确定的活动显示为 `待定`
5. 未确定的餐厅不要假装已经确认
6. 所有明确地点都提供 Google Maps 按钮
7. 每个 Activity 都支持图片
8. 图片不存在时必须有 placeholder
9. Mobile layout 必须优先考虑
10. 所有 UI 文案以中文为主
11. 餐厅、地点、品牌名称保留英文 / 原名
12. 页面应该可以直接部署到 GitHub Pages / Vercel / Netlify
13. 不需要 Backend
14. Countdown 必须根据用户填写的真实日期计算
15. 不要把 `?` 直接作为正式活动名称，使用 `待定`
16. Day 3 的沿途美食应该显示为 **候选停靠点**，而不是强制固定行程
17. Day 3 / Day 4 的 Desa Dairy Farm 与 Spring Garden 需要允许用户选择
18. `下午不一定看到神山` 必须作为天气/能见度提醒显示

---

# 🌟 Desired User Experience

打开网页后，用户应该马上看到：

```text
🌴 SABAH TRIP

KK • Kundasang

✈️ 距离出发还有
03 DAYS
12 HOURS
45 MINUTES

[查看行程]
```

往下：

```text
🗺️ TRIP ROUTE

Senai
 ↓ ✈️
Kota Kinabalu
 ↓ 🚗
Tamparuli
 ↓
Kundasang
 ↓ 🚗
KK Airport
```

然后：

```text
DAY 1
抵达亚庇

15:10 ✈️
出发

17:30 🛬
抵达 KK

18:00 🍤
晚餐

19:30 🏠
Check-in
```

然后用户可以继续滑动查看：

```text
DAY 2
🌊 Kota Kinabalu

DAY 3
🏔️ KK → Kundasang

DAY 4
🌄 Kundasang Sunrise

DAY 5
✈️ Return
```

最后：

```text
🎒 PACKING CHECKLIST

☐ 手机
☐ Power Bank
☐ 外套
☐ 雨伞
☐ 防晒
☐ 相机
...
```

整体应该让用户感觉像一个：

**🌴 中文 Sabah 旅游 Interactive Itinerary Website**

而不是普通的文字行程表。

---

# 🚀 Future Enhancements

预留未来扩展：

- [ ] 每日天气
- [ ] 实际驾驶时间
- [ ] Fuel Cost
- [ ] Trip Budget
- [ ] Restaurant reservation
- [ ] Hotel / Homestay information
- [ ] Photo Gallery
- [ ] Trip Notes
- [ ] Share Trip
- [ ] Export PDF
- [ ] Add to Google Calendar
- [ ] PWA / Add to Home Screen
- [ ] Offline mode

---

# ✅ Final Deliverable

最终请生成：

```text
1. 完整 HTML 页面
2. CSS
3. JavaScript
4. 图片资源结构
5. Responsive Mobile Design
6. Interactive Timeline
7. Flight Countdown
8. Google Maps Links
9. Packing Checklist
10. Day Navigation
11. Route Visualization
```

最终效果应该是一个：

**🌴 中文 Sabah 旅游 Interactive Itinerary Website**
