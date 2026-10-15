# Briefly — Idea Red Team & Validation Plan

> وضعیت فعلی: **Product Discovery**
>
> حکم فعلی: **🟢 TEST — هنوز 🚀 BUILD نه**

این سند نتیجه بررسی ایده Briefly با رویکرد Idea Red Team است. هدف این تحلیل تایید ایده نیست؛ هدف این است که قبل از صرف زمان، هزینه و انرژی برای ساخت محصول، فرضیات خطرناک، شواهد گمشده، ریسک‌ها و ارزان‌ترین روش‌های آزمایش مشخص شوند.

---

## 1. خلاصه ایده

Briefly برای افرادی است که منابع خبری و اطلاعاتی متعددی مانند Telegram، وب‌سایت‌ها، RSS و منابع تخصصی را دنبال می‌کنند اما زمان کافی برای بررسی همه آن‌ها ندارند.

فرآیند پیشنهادی محصول:

**جمع‌آوری → فیلتر → حذف تکرار → تشخیص اهمیت → خلاصه‌سازی → شخصی‌سازی → نمایش**

هدف Briefly این نیست که خبر بیشتری به کاربر بدهد.

هدف اصلی:

> کاربر در زمان بسیار کمتر بفهمد چه اتفاقات مهمی افتاده است.

---

## 2. بازسازی مسئله

### Problem

مسئله فقط «زیاد بودن خبر» نیست.

تعریف دقیق‌تر:

> من چندین منبع مهم دارم که احساس می‌کنم باید آن‌ها را بررسی کنم، اما وقت ندارم همه آن‌ها را بخوانم.

### User

تعریف فعلی کاربران در Product Concept بسیار گسترده است:

- مدیران
- صاحبان کسب‌وکار
- متخصصان فناوری
- سرمایه‌گذاران
- پژوهشگران
- دانشجویان
- تولیدکنندگان محتوا

این دامنه برای شروع محصول بیش از حد بزرگ است.

### Beachhead User پیشنهادی

برای شروع بهتر است روی یک گروه کوچک و قابل دسترس تمرکز شود، مثلا:

> متخصصان و مدیران حوزه فناوری که روزانه چندین کانال Telegram و منبع تخصصی را برای کار خود بررسی می‌کنند.

یا محدودتر:

> مدیران IT و متخصصان AI که روزانه 5 تا 20 کانال Telegram یا منبع تخصصی را دنبال می‌کنند و از دست دادن یک خبر مهم می‌تواند روی کارشان تاثیر بگذارد.

### Situation

> کاربر زمان محدودی دارد، اما چندین منبع را مهم می‌داند و احساس می‌کند باید آن‌ها را مرتب بررسی کند.

### Current Solution

راه‌حل‌های فعلی احتمالی:

- اسکرول دستی Telegram
- Telegram Folder
- باز کردن سایت‌های خبری
- RSS Reader
- Newsletter
- Search
- Bookmark / Saved Messages
- نادیده گرفتن بخشی از اخبار

این موارد فعلا **فرضیه** هستند و باید با رفتار کاربران واقعی بررسی شوند.

### Desired Outcome

کاربر واقعا دنبال این نیست که «خلاصه خبر» دریافت کند.

نتیجه مطلوب:

> بدانم چه چیز مهمی تغییر کرده، بدون اینکه مجبور باشم همه منابع را بررسی کنم.

---

## 3. Job To Be Done

تعریف پیشنهادی:

> وقتی وقت ندارم همه منابع مهمم را بررسی کنم، کمکم کن سریع بفهمم چه اتفاقات مهمی افتاده است.

نسخه بسیار کوتاه:

> **What changed that I need to know?**

این Job از «News Aggregation» مهم‌تر است، چون Aggregation راه‌حل است نه نیاز واقعی کاربر.

---

## 4. Evidence Check

در حال حاضر مستندات محصول مناسب هستند، اما Evidence واقعی از رفتار کاربران هنوز ثبت نشده است.

| ادعا | وضعیت |
|---|---|
| کاربران منابع زیادی را دنبال می‌کنند | ASSUMPTION |
| بررسی منابع برای آن‌ها دردناک است | UNKNOWN |
| زمان قابل توجهی صرف این کار می‌کنند | UNKNOWN |
| خبرهای مهم را از دست می‌دهند | UNKNOWN |
| AI Summary می‌خواهند | ASSUMPTION |
| Personalized Feed می‌خواهند | ASSUMPTION |
| حاضرند Briefly را هر روز باز کنند | UNKNOWN |
| حاضرند بررسی مستقیم Telegram را کاهش دهند | UNKNOWN |
| به فیلتر و خلاصه Briefly اعتماد خواهند کرد | UNKNOWN |
| حاضرند برای سرویس پول بدهند | UNKNOWN |

### Strongest Evidence

در حال حاضر:

> **Evidence رفتاری قوی ثبت نشده است.**

این به معنی ضعیف بودن ایده نیست؛ به معنی این است که پروژه هنوز واقعا در Product Discovery قرار دارد.

---

## 5. مهم‌ترین سوال محصول

تمام مرحله Discovery باید فعلا حول این سوال بچرخد:

> آیا کسی حاضر است به جای 30 تا 60 دقیقه بررسی منابع مختلف، روزانه حدود 5 دقیقه Briefly را بررسی کند؟

و سوال مهم‌تر:

> آیا بعد از استفاده از Briefly، نیاز کاربر به بررسی مستقیم منابع اصلی واقعا کاهش پیدا می‌کند؟

اگر کاربر Briefly را بخواند و بعد دوباره تمام کانال‌ها و سایت‌ها را بررسی کند، محصول هنوز Core Value خود را ایجاد نکرده است.

---

## 6. Killer Assumption

مهم‌ترین فرض خطرناک:

> کاربران آن‌قدر به انتخاب، فیلتر و خلاصه‌سازی Briefly اعتماد می‌کنند که بررسی مستقیم منابع قبلی خود را کاهش دهند.

این فرض شامل دو بخش است:

1. **Efficiency** — Briefly واقعا زمان را کم کند.
2. **Trust** — کاربر نگران از دست دادن اطلاعات مهم نباشد.

اگر این فرض غلط باشد، بخش بزرگی از ارزش محصول از بین می‌رود.

---

## 7. رقیب اصلی

رقیب اصلی Briefly الزاما یک AI News Aggregator دیگر نیست.

برای اولین گروه پیشنهادی، رقیب اصلی احتمالا:

> **Telegram و عادت فعلی کاربر**

است.

Telegram از قبل دارد:

- منابع کاربر
- Notification
- Search
- Forward
- Share
- Folder
- عادت روزانه
- Learning Curve نزدیک به صفر

بنابراین Briefly نباید فقط کمی بهتر باشد.

باید بهبود قابل توجهی ایجاد کند، مثلا:

> **45 دقیقه → 5 دقیقه**

---

## 8. Red Team Attack

دلایل اصلی که ممکن است باعث شکست Briefly شوند:

| ریسک | شدت |
|---|---|
| کاربر بعد از Briefly همچنان تمام منابع اصلی را بررسی کند | 🔴 Critical |
| فیلتر اشتباه باعث مخفی شدن خبر مهم و از بین رفتن اعتماد شود | 🔴 Critical |
| کاربر به AI Summary اعتماد نکند | 🔴 Critical |
| پروژه قبل از Validation بیش از حد بزرگ شود | 🔴 Critical |
| تنظیم Source، Topic، Keyword و Priority پیچیده شود | 🟠 Important |
| Telegram Integration محدود یا ناپایدار باشد | 🟠 Important |
| Summarization به قابلیت Commodity تبدیل شود | 🟠 Important |
| هزینه پردازش AI در مقیاس بالا زیاد شود | 🟠 Important |
| Duplicate Detection کیفیت کافی نداشته باشد | 🟠 Important |
| مدل درآمدی مناسب پیدا نشود | 🟠 Important |

---

## 9. Product Risk Review

### VALUE — 🟡 UNKNOWN

هنوز نمی‌دانیم Problem آن‌قدر مهم است که کاربر رفتار فعلی خود را تغییر دهد.

### USABILITY — 🟡 UNKNOWN

ممکن است تنظیم Topic، Keyword، Source، Block List و Priority برای کاربر بیش از حد پیچیده شود.

محصول باید بتواند با Minimum Configuration ارزش اولیه تولید کند.

### FEASIBILITY — 🟡 UNKNOWN / قابل بررسی

بخش‌های اصلی از نظر فنی قابل ساخت به نظر می‌رسند، اما ریسک‌هایی وجود دارد:

- Telegram ingestion
- Content extraction
- Duplicate detection
- Ranking
- Hallucination
- AI cost
- Source restrictions

در حال حاضر مانع فنی غیرقابل حل مشخصی دیده نشده است.

### BUSINESS VIABILITY — 🟡 UNKNOWN

هنوز مشخص نیست:

- چه کسی پول می‌دهد؟
- چرا پول می‌دهد؟
- چقدر حاضر است پرداخت کند؟
- هزینه پردازش هر کاربر چقدر است؟
- آیا حاشیه سود مناسب ایجاد می‌شود؟

این سوال‌ها در مرحله فعلی طبیعی هستند، اما نباید مثبت فرض شوند.

---

## 10. Assumption Map

| Assumption | Risk if Wrong | Current Evidence | How to Test |
|---|---|---|---|
| کاربران زمان زیادی صرف بررسی منابع می‌کنند | Critical | ندارد | Customer Interview + مشاهده رفتار |
| کاربران ترجیح می‌دهند خبرهای کمتر ولی مرتبط‌تر ببینند | High | ندارد | Manual Daily Brief |
| کاربران به AI Summary اعتماد می‌کنند | High | ندارد | Summary همراه Original Source |
| کاربران بررسی منابع اصلی را کاهش می‌دهند | Critical | ندارد | تست 7 تا 14 روزه |
| Personalization ارزش واقعی ایجاد می‌کند | High | ندارد | Brief شخصی در برابر Brief عمومی |
| Deduplication تجربه را بهتر می‌کند | Medium | ندارد | مقایسه Feed گروه‌بندی‌شده و عادی |
| کاربران هر روز برمی‌گردند | Critical | ندارد | Retention test |
| کاربران حاضرند پول بدهند | Critical | ندارد | Paid continuation / Pre-order |

اولویت تست با فرضیاتی است که:

> **Importance بالا + Evidence پایین**

دارند.

---

## 11. Problem Score

در حال حاضر امتیاز عددی واقعی نباید ساخته شود.

| Dimension | Result |
|---|---|
| Pain | NEEDS EVIDENCE |
| Frequency | NEEDS EVIDENCE |
| User Access | NEEDS EVIDENCE |
| Evidence | NEEDS EVIDENCE |
| Existing Effort | NEEDS EVIDENCE |
| Understanding | NEEDS EVIDENCE |

Score بدون Evidence واقعی فقط ظاهر علمی ایجاد می‌کند.

---

## 12. نقد MVP فعلی

MVP فعلی در Product Concept شامل تعداد زیادی قابلیت است:

- User Account
- Topic
- Source
- Data Collection
- Storage
- Classification
- AI Summarization
- Duplicate Detection
- Personalized Feed
- Original Link

این Scope بیشتر شبیه Version 1.0 است تا کوچک‌ترین MVP برای یادگیری.

ریسک:

> ممکن است چند ماه محصول ساخته شود و بعد مشخص شود کاربران آن را دوست دارند، اما استفاده روزانه ندارند.

بنابراین قبل از MVP فنی باید یک Pretotype اجرا شود.

---

## 13. کوچک کردن Scope

برای آزمایش اولیه بهتر است پشتیبانی همزمان از این موارد انجام نشود:

- Website
- RSS
- Newsletter
- APIs
- چندین Integration

### پیشنهاد اولیه

فقط:

> **Telegram**

کاربر مثلا 5 تا 15 کانال مهم را معرفی می‌کند.

خروجی:

> **Daily Brief**

مثلا 5 تا 10 مورد مهم روز.

هر مورد:

- عنوان
- خلاصه کوتاه
- چرا مهم است
- Source
- Original Link

هدف این نسخه اثبات Value است، نه اثبات معماری.

---

## 14. Pretotype پیشنهادی

قبل از نوشتن محصول کامل، سرویس برای حدود 10 کاربر به صورت Concierge / نیمه‌دستی اجرا شود.

از هر کاربر دریافت شود:

- 5 تا 15 Source مهم
- 3 تا 5 Topic مورد علاقه
- موضوعات کم‌اهمیت یا غیرمرتبط

سپس روزانه با ترکیب Automation، AI و کار دستی یک Brief تولید شود.

### نمونه خروجی

#### Briefly — Today

**7 خبر مهم برای شما**

برای هر مورد:

- Headline
- Summary
- Why it matters
- Source
- Original link

در این مرحله مهم نیست Recommendation Engine واقعی ساخته شده باشد.

هدف:

> **آیا خروجی برای کاربر آن‌قدر ارزش دارد که رفتار او را تغییر دهد؟**

---

## 15. Experiment 1 — Concierge Daily Brief

### Hypothesis

افرادی که منابع زیادی دنبال می‌کنند، Daily Brief را به بررسی دستی تمام منابع ترجیح می‌دهند.

### Experiment

- حدود 10 کاربر هدف
- مدت 7 تا 14 روز
- Daily Brief شخصی‌سازی‌شده
- ترجیحا یک زمان ثابت در روز

### Metrics

- چند روز Brief واقعا مصرف شد؟
- چند خبر باز شد؟
- چند مورد Relevant بود؟
- چند مورد Irrelevant بود؟
- آیا خبر مهمی Missing بود؟
- آیا بعد از Brief کاربر همچنان تمام منابع را بررسی کرد؟
- کاربر چقدر زمان صرفه‌جویی کرد؟

### Pass Condition پیشنهادی

مثلا:

> حداقل 6 نفر از 10 نفر، Brief را در حداقل 5 روز از 7 روز مصرف کنند.

و مهم‌تر:

> تعدادی از کاربران واقعا بررسی مستقیم منابع قبلی را کاهش دهند.

### Fail Condition

- کاربران بعد از چند روز Brief را باز نکنند.
- Brief خوانده شود اما رفتار قبلی بدون تغییر ادامه پیدا کند.
- Missing Story باعث شود اعتماد از بین برود.
- کاربران Brief را «جالب» بدانند ولی به آن وابسته نشوند.

---

## 16. Experiment 2 — Commitment Test

### Hypothesis

کاربر به اندازه کافی این Problem را احساس می‌کند که برای راه‌اندازی سرویس Effort صرف کند.

### Experiment

یک Landing Page ساده با پیام:

> خبرهای مهم منابع مورد اعتماد خودت را در چند دقیقه بخوان.

برای ثبت‌نام فقط Email دریافت نشود.

از کاربر خواسته شود:

1. Topic انتخاب کند.
2. حداقل 3 Source وارد کند.
3. Telegram / Email برای دریافت Brief بدهد.

### Metric

تعداد کاربرانی که Setup را واقعا کامل می‌کنند.

### چرا مهم است؟

صرف کردن زمان برای معرفی Source و Topic، Evidence قوی‌تری از Click یا Like است.

---

## 17. Experiment 3 — Willingness to Pay

این تست فقط بعد از تجربه واقعی محصول انجام شود.

سوال ضعیف:

> اگر این سرویس پولی باشد پول می‌دهی؟

تست قوی‌تر:

> دوره آزمایشی شما در تاریخ مشخص تمام می‌شود. برای ادامه سرویس باید مبلغ X پرداخت کنید.

### Metric

پرداخت واقعی یا شروع واقعی فرایند خرید.

رفتار مالی Evidence بسیار قوی‌تری از نظر کاربر است.

---

## 18. Customer Discovery

اولین مصاحبه‌ها باید با افرادی انجام شود که واقعا منابع زیادی را دنبال می‌کنند.

### سوال‌های پیشنهادی

1. آخرین بار که مجبور شدی چند منبع خبری یا تخصصی را بررسی کنی چه اتفاقی افتاد؟
2. دقیقا چطور این کار را انجام دادی؟
3. تقریبا چقدر زمان برد؟
4. سخت‌ترین یا آزاردهنده‌ترین قسمت این فرایند چه بود؟
5. قبلا برای بهتر کردن این فرایند چه چیزی امتحان کرده‌ای؟

### سوال‌هایی که نباید پرسیده شوند

مثلا:

> اگر برنامه‌ای بسازیم که خبرها را برایت خلاصه کند استفاده می‌کنی؟

این نوع سوال Future Prediction است و Evidence ضعیفی تولید می‌کند.

هدف مصاحبه:

> کشف رفتار واقعی گذشته، نه گرفتن تایید برای ایده.

---

## 19. Idea Court

### Paul Graham — 🟡 INVESTIGATE

Problem قابل باور است، اما User فعلی بیش از حد گسترده است. شروع باید با گروه کوچک‌تری انجام شود که Problem را شدیدتر تجربه می‌کند.

### Rob Fitzpatrick — 🟡 INVESTIGATE

Evidence رفتاری کافی وجود ندارد. تعریف کردن کاربران از ایده نباید Validation محسوب شود.

### Clayton Christensen — 🟡 INVESTIGATE

Job To Be Done امیدوارکننده است، اما Trigger، Situation، Switching Forces و Alternatives هنوز باید بررسی شوند.

### Alberto Savoia — 🟢 TEST

ایده را می‌توان بدون ساخت سیستم کامل و با یک Pretotype ارزان آزمایش کرد.

### Marty Cagan — 🟡 INVESTIGATE

Feasibility اولیه مناسب به نظر می‌رسد، اما Value و Business Viability هنوز Unknown هستند.

---

## 20. MVP پس از Validation

اگر Pretotype و Experimentها موفق باشند، MVP فنی می‌تواند کوچک باشد.

### Core User

فرد پرمشغله‌ای که چندین Source مهم را برای کار دنبال می‌کند.

### Core Situation

هر روز باید بفهمد چه اتفاقات مهمی افتاده است.

### Core Problem

Noise، Duplicate و محدودیت زمان.

### Core Job

سریع بفهمد چه چیز مهمی تغییر کرده است.

### Core Action

باز کردن Daily Brief.

### Core Value

در چند دقیقه از اتفاقات مهم باخبر شود و نیازش به بررسی مستقیم همه منابع کاهش پیدا کند.

### MVP Features

حداکثر:

1. انتخاب Source و Topic
2. جمع‌آوری محتوا
3. Filter + Deduplicate
4. Summary
5. Daily Personalized Brief + Original Link

---

## 21. NOT IN MVP

تا زمانی که Core Value اثبات نشده، این قابلیت‌ها نباید وارد Scope اولیه شوند:

- Mobile App
- Real-time Personalized Feed
- Advanced Recommendation Engine
- Automatic Interest Learning
- Sentiment Analysis
- Fact Checking
- Audio Brief
- Story Timeline
- Team Feed
- Advanced Push Notification
- Multi-language Translation
- Advanced Source Reputation
- چند سطح Summary
- Arbitrary Website Ingestion
- Newsletter Integration
- Trending Detection
- Vector Database مگر اینکه نیاز فنی واقعی ایجاد شود

Feature بیشتر نباید جای Evidence را بگیرد.

---

## 22. Product Positioning پیشنهادی برای تست

تعریف فنی فعلی:

> Personalized AI News Aggregator

برای داخل تیم مفید است، اما لزوما بهترین Positioning برای کاربر نیست.

گزینه قابل آزمایش:

> **خلاصه 5 دقیقه‌ای شما از منابعی که به آن‌ها اعتماد دارید.**

یا:

> **مهم‌ترین چیزهایی که امروز باید بدانید، در چند دقیقه.**

Positioning باید Outcome را بفروشد، نه Technology را.

---

## 23. معیارهای اولیه موفقیت

در مرحله Discovery تعداد خبر جمع‌آوری‌شده Metric مهمی نیست.

Metricهای مهم‌تر:

- Daily Brief Consumption
- 7-day Retention
- Relevant Story Rate
- Irrelevant Story Rate
- Missing Important Story Rate
- Reduction in Direct Source Checking
- Estimated Time Saved
- Original Link Open Rate
- Setup Completion Rate
- Paid Conversion بعد از Trial

### Metric بسیار مهم

> **Reduction in Direct Source Checking**

چون این Metric مستقیما نشان می‌دهد آیا Briefly واقعا جایگزین بخشی از Workflow قبلی شده است یا خیر.

---

## 24. Final Red Team Report

### IDEA

تبدیل منابع خبری شلوغ و پراکنده به یک Brief کوتاه، مرتبط و شخصی‌سازی‌شده.

### USER

تعریف فعلی گسترده است.

Beachhead پیشنهادی:

> متخصصان و مدیران پرمشغله‌ای که تعداد زیادی Source حرفه‌ای را به صورت مداوم بررسی می‌کنند.

### JOB TO BE DONE

> سریع بفهمم چه اتفاقات مهمی افتاده بدون اینکه مجبور باشم تک‌تک منابع را بررسی کنم.

### BIGGEST PROBLEM

اطلاعات زیاد؛ زمان و توجه محدود.

### CURRENT ALTERNATIVE

بررسی دستی Telegram، وب‌سایت‌ها و سایر منابع.

### STRONGEST EVIDENCE

> فعلا Evidence رفتاری قوی ثبت نشده است.

### BIGGEST UNKNOWN

> آیا Problem آن‌قدر دردناک است که کاربر رفتار فعلی خود را تغییر دهد؟

### KILLER ASSUMPTION

> کاربر به Briefly آن‌قدر اعتماد خواهد کرد که بررسی منابع اصلی را کاهش دهد.

### MAIN RISK

> ساخت یک Aggregator پیشرفته قبل از اثبات Usage و Retention واقعی.

### MVP

> Daily Personalized Brief از تعداد محدودی Source.

### NEXT EXPERIMENT

> اجرای Concierge Daily Brief برای حدود 10 کاربر به مدت 7 تا 14 روز.

### VERDICT

> **🟢 TEST**

هنوز:

> **🚀 BUILD — NO**

---

## 25. Next Steps

ترتیب پیشنهادی ادامه پروژه:

1. تعریف دقیق Beachhead User
2. پیدا کردن 10 کاربر واقعی
3. اجرای Customer Interview
4. ثبت Evidence و Current Behavior
5. اجرای Concierge Daily Brief
6. اندازه‌گیری Retention و Behavior Change
7. بررسی Trust و Missing Story
8. تست Commitment
9. تست Willingness to Pay
10. تصمیم: PERSEVERE / PIVOT / STOP / MORE EVIDENCE
11. در صورت Validation، تعریف MVP فنی
12. بعد از آن انتخاب Stack و Architecture

---

## تصمیم فعلی

فعلا نباید تمرکز پروژه روی انتخاب Frontend، Backend، Database یا AI Provider باشد.

اول باید این فرض اثبات شود:

> **Briefly می‌تواند زمان بررسی منابع را به شکل معناداری کاهش دهد، بدون اینکه کاربر احساس کند اطلاعات مهمی را از دست می‌دهد.**

اگر این فرض با رفتار واقعی کاربران تایید شود، آن وقت پروژه آماده ورود از **Product Discovery** به **MVP Engineering** است.
