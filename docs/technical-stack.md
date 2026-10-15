# Briefly — Technical Stack & Technology Decisions

> وضعیت این سند: **Proposed Technical Stack**
>
> وضعیت فعلی محصول هنوز **Product Discovery / Validation** است و این سند به معنی شروع ساخت کامل محصول نیست. هدف این است که اگر Validation موفق بود، از قبل بدانیم برای MVP فنی چه Stackی منطقی‌تر است و چرا.

---

## 1. Stack یعنی چه؟

یک Web Application معمولاً فقط با یک زبان یا یک تکنولوژی ساخته نمی‌شود.

برای مثال Briefly به بخش‌های مختلفی نیاز دارد:

- چیزی که کاربر در مرورگر می‌بیند
- بخشی که منطق اصلی برنامه را اجرا می‌کند
- جایی برای ذخیره اطلاعات
- Workerهایی برای کارهای پس‌زمینه
- سیستم Job Queue
- محل ذخیره فایل‌ها
- اتصال به AI
- Web Server
- Monitoring
- Deployment

مجموع تکنولوژی‌هایی که برای ساخت این بخش‌ها انتخاب می‌کنیم، **Technology Stack** نام دارد.

معماری ساده Briefly:

```text
User
  ↓
Frontend
  ↓
Backend API
  ↓
Database
  ↓
Jobs / Workers
  ↓
Telegram / RSS / Websites / AI
```

---

## 2. Stack پیشنهادی Briefly

| بخش | انتخاب پیشنهادی |
|---|---|
| Frontend | Next.js + TypeScript |
| UI | Tailwind CSS + shadcn/ui |
| Backend API | Go |
| Go HTTP Router | Chi |
| PostgreSQL Driver | pgx |
| SQL Layer | sqlc |
| Database | PostgreSQL |
| Vector Search | pgvector |
| Text Search | PostgreSQL Full Text Search + pg_trgm |
| Background Jobs | River + PostgreSQL |
| AI | Provider-agnostic AI layer |
| Object Storage | S3-compatible storage / MinIO |
| Reverse Proxy | Nginx |
| Deployment | Docker / Docker Compose |
| Metrics | Prometheus |
| Dashboard | Grafana |
| Logs | Structured JSON; Loki later if needed |

انتخاب کلی ما را می‌توان این‌طور خلاصه کرد:

> **Next.js + Go + PostgreSQL + Docker**

بقیه ابزارها در اطراف این هسته قرار می‌گیرند.

---

# 3. Frontend — Next.js + TypeScript

## Frontend چیست؟

Frontend همان بخشی از برنامه است که کاربر مستقیماً می‌بیند و با آن کار می‌کند.

در Briefly شامل بخش‌هایی مثل این است:

- Login
- Onboarding
- انتخاب Topic
- مدیریت Sourceها
- Daily Brief
- Story Page
- Saved Items
- Settings
- Feedback

---

## چرا Next.js؟

Next.js یک Framework بر پایه React است.

React ابزار بسیار قدرتمندی برای ساخت رابط کاربری است، اما Next.js امکانات بیشتری را به شکل آماده در اختیار پروژه قرار می‌دهد، مثل:

- Routing
- Server Rendering
- Layout management
- Data fetching
- Caching
- SEO support
- Image optimization
- Build tooling
- Server-side capabilities

به زبان ساده:

> React بیشتر ابزار ساخت UI است؛ Next.js یک ساختار کامل‌تر برای ساخت Web Application می‌دهد.

برای Briefly این مهم است چون می‌خواهیم Frontend را سریع بسازیم، اما ساختار پروژه از همان ابتدا قابل رشد باشد.

---

## چرا React خالی نه؟

با React خالی معمولاً باید تعداد بیشتری تصمیم و ابزار را خودمان انتخاب و ترکیب کنیم.

مثلاً:

- Router
- Build configuration
- Server rendering
- SEO strategy
- Project structure

این انعطاف بد نیست، اما برای Briefly ارزش اصلی در ساخت یک Frontend framework از صفر نیست.

ما می‌خواهیم زمان تیم بیشتر صرف خود Product شود.

---

## چرا Vue / Nuxt نه؟

Vue و Nuxt گزینه‌های بسیار خوبی هستند و انتخاب اشتباهی محسوب نمی‌شوند.

Nuxt تقریباً نقشی مشابه Next.js در دنیای Vue دارد.

دلایل ترجیح Next.js:

- اکوسیستم بزرگ React
- تعداد زیاد Component و Library
- Community بزرگ
- منابع آموزشی زیاد
- Integration مناسب با سرویس‌ها و ابزارهای جدید
- مناسب برای Dashboard و Product UI

نتیجه:

> **Nuxt می‌توانست انتخاب خوبی باشد، اما Next.js برای Briefly تعادل مناسبی بین اکوسیستم، سرعت توسعه و آینده پروژه دارد.**

---

## چرا Angular نه؟

Angular Framework بسیار قدرتمندی است، مخصوصاً برای پروژه‌های بزرگ Enterprise.

اما در Briefly فعلاً:

- تیم کوچک است
- MVP باید سریع ساخته شود
- نیاز به ساختار بسیار سنگین Enterprise نداریم

Angular امکانات زیادی را از ابتدا وارد پروژه می‌کند که فعلاً ممکن است بیشتر از نیاز ما باشد.

بنابراین:

> Angular بد نیست؛ برای Scope فعلی Briefly بیش از حد سنگین است.

---

# 4. TypeScript

JavaScript زبان اصلی Frontend وب است.

اما JavaScript بسیار آزاد است.

مثلاً ممکن است متغیری که قرار بوده Number باشد، اشتباهاً String شود و مشکل فقط هنگام اجرا دیده شود.

TypeScript به JavaScript سیستم Type اضافه می‌کند.

مثال:

```ts
let score: number = 10;
```

اگر بعداً اشتباهی بنویسیم:

```ts
score = "high";
```

TypeScript قبل از اجرا مشکل را پیدا می‌کند.

مزیت‌ها:

- خطاهای کمتر
- Refactoring امن‌تر
- خوانایی بهتر Code
- مناسب تیم
- IDE autocomplete بهتر
- قرارداد واضح‌تر بین Frontend و Backend

به زبان ساده:

> JavaScript آزادی بیشتری دارد؛ TypeScript همان JavaScript است، ولی با Guardrail بیشتر.

---

# 5. UI — Tailwind CSS + shadcn/ui

## Tailwind CSS چیست؟

CSS ظاهر صفحه را مشخص می‌کند:

- رنگ
- فاصله
- اندازه
- Layout
- Border
- Responsive behavior

Tailwind روش Utility-first برای نوشتن Style ارائه می‌دهد.

مزیت آن برای Briefly:

- توسعه سریع‌تر UI
- Consistency بهتر
- Responsive design ساده‌تر
- کاهش CSSهای پراکنده
- مناسب برای Product UI

---

## shadcn/ui چیست؟

shadcn/ui مجموعه‌ای از Componentهای قابل استفاده و قابل تغییر است، مثل:

- Button
- Dialog
- Dropdown
- Tabs
- Table
- Form
- Card
- Toast

مزیت مهمش این است که برخلاف بعضی Component Libraryها، کنترل Code و ظاهر Componentها تا حد زیادی دست خود پروژه باقی می‌ماند.

برای Briefly یعنی:

> می‌توانیم MVP را سریع بسازیم، بدون اینکه ظاهر محصول برای همیشه به یک UI Framework خاص قفل شود.

---

# 6. Backend — Go

## Backend چیست؟

Backend بخش پشت صحنه برنامه است.

کاربر مستقیماً آن را نمی‌بیند.

مثلاً وقتی کاربر یک Topic جدید Follow می‌کند:

```text
Frontend
   ↓
Backend API
   ↓
Validation
   ↓
Database
```

اما Backend در Briefly فقط CRUD نیست.

باید کارهایی مثل این انجام دهد:

- مدیریت User
- مدیریت Source
- دریافت محتوا
- Normalization
- اتصال به AI
- Classification
- Deduplication
- Story clustering
- Ranking
- ساخت Daily Brief
- اجرای Jobهای پس‌زمینه

---

## چرا Go؟

Go برای Backend، Network Services، Workerها و پردازش‌های Concurrent بسیار مناسب است.

Briefly ذاتاً تعداد زیادی کار مستقل و همزمان دارد.

مثال:

```text
RSS A       → Fetch
RSS B       → Fetch
Telegram C  → Fetch
Website D   → Fetch

Article 1 → Summarize
Article 2 → Embed
Article 3 → Classify
Article 4 → Deduplicate
```

Go برای این نوع workload مزیت‌های مهمی دارد:

- Concurrency قوی
- Goroutineهای سبک
- مصرف RAM مناسب
- Performance خوب
- اجرای مناسب Workerهای طولانی‌مدت
- Deployment ساده
- خروجی Single Binary
- Type system قوی
- Startup سریع
- استانداردهای خوب برای Network Programming

---

## چرا Node.js نه؟

Node.js انتخاب بسیار خوبی برای Backend وب است.

حتی یک مزیت مهم دارد:

> Frontend و Backend هر دو می‌توانند TypeScript باشند.

این کار Learning Curve و تعداد زبان‌های پروژه را کمتر می‌کند.

اما Briefly در صورت موفقیت احتمالاً Backendای خواهد داشت که حجم زیادی از کارهای زیر را انجام می‌دهد:

- Network I/O
- Worker processing
- Scheduled jobs
- Source ingestion
- concurrent API calls
- long-running services

برای این نوع workload، Go انتخاب جذابی است.

مقایسه ساده:

| موضوع | Go | Node.js |
|---|---|---|
| Web API | عالی | عالی |
| Concurrency | عالی | عالی برای I/O |
| Workerهای دائمی | بسیار مناسب | مناسب |
| مصرف Memory | معمولاً پایین‌تر | معمولاً بالاتر |
| Deployment | بسیار ساده | ساده |
| Ecosystem Web | خوب | بسیار بزرگ |
| یک زبان برای کل Stack | خیر | بله |
| Compile-time type safety | قوی | با TypeScript |

نتیجه:

> Node.js انتخاب بدی نیست، اما Go برای ماهیت processing-heavy احتمالی Briefly انتخاب بلندمدت جذاب‌تری است.

---

## چرا Laravel / PHP نه؟

Laravel یکی از بهترین Frameworkها برای ساخت سریع Web Applicationهای Business-oriented است.

برای سیستم‌هایی مثل:

- CRM
- Admin Panel
- Accounting
- CMS
- E-commerce
- CRUD-heavy applications

Laravel می‌تواند انتخاب فوق‌العاده‌ای باشد.

اما بخش مهمی از Briefly این‌ها خواهد بود:

- Content ingestion
- Background processing
- Network calls
- AI calls
- Queue processing
- Source polling

Go برای این بخش‌ها بسیار طبیعی است.

اگر Briefly یک CRM یا پنل مدیریتی معمولی بود، Laravel می‌توانست حتی انتخاب اول باشد.

---

## چرا Python نه؟

Briefly از AI استفاده می‌کند، اما این به معنی نیاز قطعی به Python نیست.

اگر فعلاً از API مدل‌ها استفاده کنیم:

```text
Briefly
   ↓
AI API
   ↓
Summary / Classification / Embedding
```

Go به راحتی می‌تواند AI API را صدا بزند.

Python زمانی اهمیت بیشتری پیدا می‌کند که خودمان وارد این حوزه‌ها شویم:

- Machine Learning
- PyTorch
- Transformers
- Custom NLP models
- Local inference
- Model training
- Data Science pipelines

اگر بعدها نیاز شد، می‌توانیم یک سرویس جدا اضافه کنیم:

```text
Go Backend
    ↓
Python AI Service
```

بنابراین از روز اول کل Backend را Python نمی‌کنیم فقط چون پروژه از AI استفاده می‌کند.

---

# 7. Chi

Chi یک Router سبک برای Go است.

مثلاً مشخص می‌کند:

```text
GET  /api/briefs
GET  /api/stories/:id
POST /api/sources
POST /api/feedback
```

هر درخواست باید به کدام Handler برود.

دلایل انتخاب:

- سبک
- ساده
- نزدیک به استانداردهای خود Go
- Magic کم
- مناسب API service

ما فعلاً Framework بسیار بزرگ برای Go نیاز نداریم.

---

# 8. pgx و sqlc

## pgx

pgx Driver و Toolkit بسیار مناسب PostgreSQL در Go است.

Backend برای ارتباط با PostgreSQL به چنین Driverی نیاز دارد.

---

## sqlc

sqlc اجازه می‌دهد SQL واقعی بنویسیم و از روی آن Code تایپ‌شده Go تولید شود.

مثلاً ما SQL را واضح می‌بینیم:

```sql
SELECT id, title
FROM stories
WHERE id = $1;
```

و sqlc برای استفاده از آن Code مناسب Go تولید می‌کند.

مزایا:

- کنترل کامل روی SQL
- Performance قابل پیش‌بینی
- Compile-time checking بهتر
- Magic کمتر نسبت به ORMهای سنگین
- مناسب Queryهای جدی‌تر

برای Briefly که ممکن است Queryهای Ranking و Feed پیچیده داشته باشد، SQL شفاف مزیت مهمی است.

---

# 9. Database — PostgreSQL

## Database چیست؟

Database حافظه دائمی سیستم است.

مثلاً Briefly باید اطلاعات زیر را نگه دارد:

- Users
- Topics
- Sources
- Articles
- Stories
- Summaries
- Feedback
- Briefs
- Jobs

بدون Database اطلاعات با Restart شدن برنامه از بین می‌روند.

---

## چرا PostgreSQL؟

PostgreSQL یک Relational Database قدرتمند و Mature است.

Briefly داده‌های Relation-heavy زیادی دارد:

```text
User ↔ Topic
User ↔ Source
Story ↔ Article
Article ↔ Source
Brief ↔ Story
```

این مدل برای PostgreSQL بسیار مناسب است.

مزیت‌های دیگر:

- Transaction
- Indexing قوی
- JSON support
- Full Text Search
- Extension ecosystem
- Advanced queries
- Reliability
- pgvector
- pg_trgm

---

## چرا MySQL نه؟

MySQL هم Database بسیار خوبی است و برای بسیاری از پروژه‌ها انتخاب کاملاً منطقی است.

اما PostgreSQL برای Briefly چند مزیت جذاب دارد:

- Query capabilities قوی
- Extensionها
- pgvector
- Full Text Search
- Data typeهای پیشرفته
- قابلیت مناسب برای Queryهای پیچیده

تفاوت این دو همیشه تعیین‌کننده نیست، اما برای نیازهای احتمالی Briefly PostgreSQL Fit بهتری دارد.

---

## چرا MongoDB نه؟

MongoDB Document Database است و داده را شبیه Documentهای JSON نگهداری می‌کند.

برای برخی پروژه‌ها بسیار مناسب است.

اما Briefly Relationهای زیادی دارد.

مثلاً یک Story ممکن است چند Article داشته باشد و هر Article یک Source داشته باشد؛ Userها هم Topic و Sourceهای مختلفی Follow می‌کنند.

این Relationshipها در PostgreSQL طبیعی و قابل کنترل هستند.

بنابراین:

> MongoDB مشکلی را حل نمی‌کند که در MVP Briefly از PostgreSQL بهتر حل شود.

---

# 10. Article و Story را جدا می‌کنیم

این تصمیم Data Model مهمی است.

**Article** یعنی یک محتوای منتشرشده توسط یک Source.

مثلاً:

```text
Reuters Article
BBC Article
Telegram Post
TechCrunch Article
```

اما چند Article ممکن است درباره یک اتفاق واقعی باشند.

آن اتفاق را **Story** می‌نامیم.

مثال:

```text
Reuters ─────┐
BBC ─────────┤
Telegram ────┼──> Story
TechCrunch ──┘

"Company X releases Product Y"
```

این مدل کمک می‌کند Duplicate News را به جای چند کارت جدا، به یک Story واحد تبدیل کنیم.

---

# 11. Vector Search — pgvector

## Vector چیست؟

مدل‌های AI می‌توانند معنی یک متن را به مجموعه‌ای از عددها تبدیل کنند.

مثلاً:

```text
"OpenAI released a new model"

↓

[0.21, -0.94, 0.11, 0.65, ...]
```

به این Representation معمولاً Embedding گفته می‌شود.

متن‌هایی که معنای نزدیک دارند، Vectorهای نزدیک‌تری خواهند داشت.

---

## Briefly چرا Vector نیاز دارد؟

یکی از کاربردهای مهم:

**Duplicate / Similar Story Detection**

مثلاً:

```text
OpenAI launches Model X

OpenAI announces its new X model

مدل جدید X شرکت OpenAI معرفی شد
```

عبارت‌ها متفاوت‌اند، ولی ممکن است درباره یک Story باشند.

Vector similarity می‌تواند به تشخیص این شباهت کمک کند.

کاربردهای آینده:

- Semantic Search
- Story clustering
- User ↔ Story relevance
- Recommendation
- Similar articles

---

## چرا pgvector؟

pgvector قابلیت Vector را مستقیماً به PostgreSQL اضافه می‌کند.

یعنی به جای داشتن:

```text
PostgreSQL
+
Vector Database
```

فعلاً داریم:

```text
PostgreSQL
+
pgvector
```

مزایا:

- Infrastructure کمتر
- Backup ساده‌تر
- Deployment ساده‌تر
- Data consistency بهتر
- هزینه عملیاتی کمتر

---

## چرا Qdrant / Pinecone / Weaviate نه؟

این ابزارها Vector Databaseهای تخصصی و قدرتمندی هستند.

ممکن است در Scale بالا یا Use Caseهای خاص به آن‌ها نیاز پیدا کنیم.

اما شروع با آن‌ها یعنی یک سرویس جدید برای:

- Deployment
- Monitoring
- Backup
- Security
- Networking
- Synchronization

اصل ما:

> تا وقتی PostgreSQL + pgvector نیاز واقعی را پوشش می‌دهد، Vector Database جدا اضافه نمی‌کنیم.

---

# 12. Text Search — PostgreSQL Full Text Search + pg_trgm

کاربر ممکن است دنبال عبارت‌هایی مثل این بگردد:

```text
OpenAI
Iran economy
Cybersecurity attack
```

برای MVP، PostgreSQL ابزارهای Search خوبی دارد.

Full Text Search برای جستجوی متن و pg_trgm برای Matching و Similarity مفید است.

---

## چرا Elasticsearch / OpenSearch نه؟

Elasticsearch و OpenSearch Search Engineهای بسیار قدرتمندی هستند.

اما اضافه شدن آن‌ها یعنی:

```text
PostgreSQL
+
Search Cluster
+
Data Synchronization
```

این Complexity فعلاً توجیه ندارد.

اگر در آینده:

- حجم Articleها بسیار بالا شد
- Search پیچیده شد
- Analytics/Search workload سنگین شد

می‌توانیم Elasticsearch یا OpenSearch را اضافه کنیم.

ولی نه قبل از نیاز واقعی.

---

# 13. Background Jobs

بسیاری از کارهای Briefly نباید داخل یک HTTP Request انجام شوند.

فرض کنیم یک Article وارد سیستم می‌شود.

ممکن است لازم باشد:

```text
Extract
↓
Normalize
↓
Classify
↓
Generate embedding
↓
Detect duplicates
↓
Summarize
↓
Rank
```

اگر همه این مراحل را هنگام درخواست کاربر اجرا کنیم، ممکن است Request بسیار طولانی شود یا Fail شود.

به جای آن، کارها را به **Job** تبدیل می‌کنیم.

مثلاً:

```text
Job #1044
Summarize Article 849
```

Worker Job را از Queue می‌گیرد و در پس‌زمینه انجام می‌دهد.

---

# 14. River + PostgreSQL

River یک Job Queue مناسب Go است که می‌تواند روی PostgreSQL کار کند.

Jobهای احتمالی:

```text
fetch_source
extract_article
classify_article
generate_embedding
detect_duplicates
summarize_story
calculate_relevance
generate_daily_brief
```

مزیت مهم:

> برای MVP مجبور نیستیم Redis یا RabbitMQ فقط برای Queue اضافه کنیم.

PostgreSQL هم Data اصلی را نگه می‌دارد و هم Jobها را.

---

## چرا Redis + BullMQ نه؟

Redis و BullMQ ترکیب محبوب و خوبی هستند، مخصوصاً در Node.js.

اما در Architecture فعلی یعنی سرویس جدید:

```text
PostgreSQL
Redis
API
Workers
```

در حالی که فعلاً می‌توانیم داشته باشیم:

```text
PostgreSQL
API
Workers
```

اگر بعداً Load یا نوع Queue تغییر کرد، می‌توان Redis/RabbitMQ/Kafka را اضافه کرد.

---

## چرا RabbitMQ یا Kafka نه؟

این ابزارها بسیار قدرتمندند.

اما برای MVP به احتمال زیاد Overengineering هستند.

Kafka زمانی بسیار ارزشمند می‌شود که معماری Event-driven بزرگ، حجم Event بسیار بالا و چند Consumer مستقل داشته باشیم.

RabbitMQ برای Messaging و Queueهای جدی عالی است.

اما اصل فعلی:

> ابتدا ساده‌ترین سیستم قابل اعتماد را استفاده می‌کنیم و Complexity را فقط با Evidence اضافه می‌کنیم.

---

# 15. Worker چیست؟

Worker یک Process پشت صحنه است که Jobها را اجرا می‌کند.

مثال:

```text
Database Job
    ↓
Worker
    ↓
AI Provider
    ↓
Summary
    ↓
Database
```

می‌توانیم چند Worker داشته باشیم تا همزمان Jobهای مختلف را اجرا کنند.

این دقیقاً یکی از نقاط قوت Go است.

---

# 16. Source Adapter Architecture

Briefly باید از Sourceهای مختلف محتوا دریافت کند.

مثلاً:

- RSS
- Telegram
- Websites
- APIs

بهتر است برای Sourceها یک Interface مشترک داشته باشیم.

مفهومی شبیه:

```text
SourceProvider

Fetch()
Parse()
Normalize()
```

سپس:

```text
RSSProvider
TelegramProvider
WebsiteProvider
APIProvider
```

مزیت:

> اضافه کردن Source جدید نباید Core سیستم را خراب یا پیچیده کند.

ساختار احتمالی:

```text
internal/
  sources/
    rss/
    telegram/
    website/
```

---

# 17. Telegram ممکن است استثنا باشد

Telegram ingestion یکی از ریسک‌های فنی مهم Briefly است.

اگر روش Integration مورد نیاز ما با Go مناسب نبود، لازم نیست کل Backend را تغییر دهیم.

می‌توان یک Collector جدا ساخت.

مثلاً:

```text
Telegram Collector
Python + Telethon
       ↓
Normalized Content
       ↓
Go Backend
```

بنابراین Architecture باید اجازه دهد یک Source Adapter در صورت لزوم با تکنولوژی متفاوت ساخته شود.

---

# 18. AI Provider Abstraction

یکی از تصمیم‌های مهم این است که Business Logic مستقیماً به یک شرکت AI قفل نشود.

بد:

```text
Everywhere in code
→ OpenAI-specific logic
```

بهتر:

```text
AIProvider

Summarize()
Classify()
Embed()
```

و سپس Adapterهای مختلف:

```text
OpenAIProvider
GeminiProvider
AnthropicProvider
LocalProvider
```

---

## چرا این مهم است؟

AI Providerها ممکن است از نظر این موارد تغییر کنند:

- Price
- Quality
- Latency
- Persian support
- Context size
- Rate limits
- Availability

مثلاً ممکن است یک مدل ارزان برای Classification مناسب باشد و مدل دیگری برای Summary.

معماری بهتر:

```text
Classification → Cheap Model
Embedding      → Embedding Model
Summarization  → Better Model
Critical Story → Premium Model
```

این کار AI Cost را هم بهتر کنترل می‌کند.

---

# 19. Object Storage — S3 / MinIO

Database جای مناسبی برای نگهداری فایل‌های بزرگ نیست.

اگر بعدها Briefly فایل‌هایی مثل این داشته باشد:

- Images
- Audio
- Documents
- Generated podcast
- Attachments

بهتر است آن‌ها در Object Storage ذخیره شوند.

Database فقط Metadata و آدرس فایل را نگه می‌دارد.

---

## چرا S3-compatible؟

S3 به یک Standard بسیار رایج برای Object Storage تبدیل شده است.

اگر برنامه بر اساس API سازگار با S3 نوشته شود، Storage backend را راحت‌تر می‌توان تغییر داد.

---

## MinIO چیست؟

MinIO یک Object Storage سازگار با S3 است که می‌توانیم خودمان Host کنیم.

این برای محیط‌های Self-hosted یا Development مفید است.

---

# 20. Docker

Briefly احتمالاً چند Process خواهد داشت:

```text
Next.js
Go API
Go Worker
PostgreSQL
Nginx
```

Docker هر بخش را در محیط مشخص خودش اجرا می‌کند.

مزایا:

- Environment قابل تکرار
- Deployment ساده‌تر
- Dependency conflict کمتر
- Development و Production نزدیک‌تر
- Rollback ساده‌تر
- Isolation بهتر

---

# 21. Docker Compose

Docker Compose مشخص می‌کند Containerهای پروژه چطور با هم اجرا شوند.

مثلاً:

```text
web
api
worker
postgres
nginx
```

با یک Configuration می‌توان کل Stack را بالا آورد.

برای MVP و حتی Production کوچک/متوسط، Docker Compose می‌تواند کاملاً کافی باشد.

---

## چرا Kubernetes نه؟

Kubernetes سیستم بسیار قدرتمندی برای Orchestration است.

برای شرایطی مثل:

- تعداد زیاد Server
- تعداد زیاد Service
- Auto scaling پیچیده
- Self-healing
- Large infrastructure

بسیار مفید است.

اما اگر MVP روی یک یا چند Server اجرا شود، Kubernetes Complexity زیادی اضافه می‌کند.

تشبیه ساده:

> استفاده از Kubernetes برای MVP کوچک می‌تواند شبیه خریدن هواپیمای مسافربری برای رفتن تا سوپرمارکت باشد.

اگر Scale واقعاً نیاز ایجاد کرد، آن زمان Kubernetes را بررسی می‌کنیم.

---

# 22. Nginx

Nginx جلوی سرویس‌های برنامه قرار می‌گیرد.

مثلاً:

```text
Internet
   ↓
Nginx
   ├── /      → Next.js
   └── /api   → Go API
```

می‌تواند مسئول این موارد هم باشد:

- HTTPS
- Reverse Proxy
- Compression
- Redirect
- Security headers
- Routing

این باعث می‌شود سرویس‌های داخلی مستقیماً در معرض Internet قرار نگیرند.

---

# 23. Monitoring — Prometheus + Grafana

اگر Briefly در Production مشکل پیدا کند، فقط دانستن اینکه «سایت کند شده» کافی نیست.

باید بتوانیم بفهمیم:

- CPU چقدر مصرف می‌شود؟
- RAM چقدر است؟
- چند Job در Queue داریم؟
- چند Job Fail شده؟
- API latency چقدر است؟
- چند Source Fail شده؟
- AI Provider چقدر کند است؟
- روزانه چند Article پردازش می‌شود؟

Prometheus Metrics را جمع می‌کند.

Grafana آن‌ها را به Dashboard و نمودار تبدیل می‌کند.

---

# 24. Logs

در مرحله اول Application باید Logهای Structured تولید کند.

مثلاً:

```json
{
  "level": "error",
  "source_id": 145,
  "operation": "fetch",
  "error": "timeout"
}
```

این Log بسیار قابل جستجوتر از متن‌های تصادفی است.

در آینده در صورت نیاز Loki می‌تواند برای جمع‌آوری و Search کردن Logها اضافه شود.

اما Loki برای MVP الزام نیست.

---

# 25. چرا Redis را فعلاً اضافه نمی‌کنیم؟

Redis ابزار بسیار خوبی است.

کاربردهای رایج:

- Cache
- Rate limiting
- Queue
- Session
- Distributed locks
- Pub/Sub

اما وجود یک تکنولوژی خوب به معنی این نیست که حتماً از روز اول باید آن را اضافه کنیم.

اگر بعداً Measurement نشان داد Database یا API به Cache نیاز دارد، Redis اضافه می‌شود.

اصل:

> **No technology without a job.**

---

# 26. چرا Microservice از روز اول نمی‌سازیم؟

Microservice Architecture برای سیستم‌های بزرگ مزایایی دارد، اما هزینه هم دارد:

- Network complexity
- Deployment بیشتر
- Monitoring بیشتر
- Authentication بین سرویس‌ها
- Distributed tracing
- Data consistency challenges
- Development overhead

برای Briefly بهتر است ابتدا یک **Modular Monolith** یا تعداد بسیار کمی Service داشته باشیم.

مثلاً:

```text
Web
API
Worker
Database
```

اما داخل Code مرز Moduleها واضح باشد.

اگر یک Module در آینده واقعاً نیاز به Scale یا Deployment مستقل داشت، آن را Service جدا می‌کنیم.

---

# 27. Monorepo پیشنهادی

ساختار احتمالی:

```text
briefly/

├── apps/
│   └── web/
│       └── Next.js
│
├── services/
│   └── api/
│       └── Go
│
├── workers/
│   └── processor/
│       └── Go
│
├── packages/
│   ├── contracts/
│   └── prompts/
│
├── migrations/
│
├── docs/
│
├── deployments/
│   ├── docker/
│   └── nginx/
│
├── docker-compose.yml
└── README.md
```

ممکن است API و Worker بخشی از Codebase مشترک Go را استفاده کنند و فقط Executable متفاوت داشته باشند.

---

# 28. معماری پیشنهادی

```text
                         Internet
                            │
                            ▼
                         Nginx
                            │
             ┌──────────────┴──────────────┐
             │                             │
             ▼                             ▼
        Next.js Web                     Go API
                                             │
                                   ┌─────────┴─────────┐
                                   │                   │
                                   ▼                   ▼
                              PostgreSQL           S3/MinIO
                              + pgvector
                              + Job Queue
                                   │
                                   ▼
                               Go Workers
                                   │
                   ┌───────────────┼───────────────┐
                   ▼               ▼               ▼
                  RSS          Telegram          Websites
                                   │
                                   ▼
                              AI Providers
```

---

# 29. جریان پردازش محتوا

Core pipeline پیشنهادی:

```text
Source
  ↓
Fetch
  ↓
Extract
  ↓
Normalize
  ↓
Noise Filtering
  ↓
Duplicate Detection
  ↓
Classification
  ↓
Embedding
  ↓
Story Clustering
  ↓
Relevance Ranking
  ↓
Summarization
  ↓
Daily Brief
```

این Pipeline دلیل اصلی بسیاری از انتخاب‌های Backend است.

---

# 30. Deduplication Strategy

در نسخه اول لازم نیست یک سیستم بسیار پیچیده Machine Learning بسازیم.

می‌توانیم مرحله‌ای جلو برویم:

```text
URL normalization
        ↓
Exact fingerprint
        ↓
Title similarity
        ↓
Content similarity
        ↓
Embedding similarity
        ↓
Story clustering
```

یعنی اول روش‌های ارزان و سریع اجرا می‌شوند و فقط در صورت نیاز سراغ پردازش گران‌تر می‌رویم.

این رویکرد برای کنترل AI Cost هم مهم است.

---

# 31. تکنولوژی‌هایی که عمداً فعلاً انتخاب نمی‌کنیم

برای MVP اولیه فعلاً این‌ها را لازم نمی‌دانیم:

- Kubernetes
- Kafka
- RabbitMQ
- Elasticsearch
- OpenSearch
- MongoDB
- Dedicated Vector Database
- Redis
- Large Microservice Architecture

این به معنی بد بودن آن‌ها نیست.

معنی تصمیم ما این است:

> هنوز Problemی نداریم که وجود این تکنولوژی‌ها را توجیه کند.

---

# 32. اصل معماری Briefly

هدف پیدا کردن «قوی‌ترین تکنولوژی دنیا» برای هر بخش نیست.

هدف این است:

```text
کمترین تعداد Moving Parts
+
تکنولوژی‌های Mature
+
Performance کافی
+
Development سریع
+
Operational Complexity پایین
+
مسیر Scale مناسب
```

برای همین PostgreSQL در MVP چند مسئولیت را پوشش می‌دهد:

```text
PostgreSQL
   ├── Relational Database
   ├── Full Text Search
   ├── Vector Search
   └── Job Queue storage
```

این سادگی یک ضعف نیست.

> **Simplicity is an architectural advantage.**

---

# 33. آیا این بهترین Stack دنیاست؟

نه.

چیزی به نام «بهترین Stack برای همه پروژه‌ها» وجود ندارد.

Stack باید بر اساس Problem انتخاب شود.

مثلاً:

### یک CMS یا CRM

```text
Laravel + PostgreSQL
```

ممکن است انتخاب عالی باشد.

### یک SaaS ساده

```text
Next.js + Node.js
```

ممکن است بسیار منطقی باشد.

### یک Data Science Platform

```text
Python + FastAPI
```

ممکن است انتخاب بهتری باشد.

اما Briefly در صورت Validation قرار است کارهایی مثل این انجام دهد:

- Source ingestion
- concurrent network requests
- Background jobs
- Content processing
- AI calls
- Duplicate detection
- Ranking
- Daily Brief generation

به همین دلیل ترکیب زیر Fit مناسبی دارد:

> **Next.js + Go + PostgreSQL**

---

# 34. چه زمانی Stack را تغییر می‌دهیم؟

Stack یک قرارداد مقدس نیست.

Technology باید وقتی اضافه یا تغییر کند که Evidence فنی وجود داشته باشد.

مثال:

### Redis اضافه می‌کنیم اگر:

- Cache واقعاً لازم شود
- Database تحت فشار Hot Read قرار گیرد
- Distributed lock یا fast shared state نیاز داشته باشیم

### Elasticsearch/OpenSearch اضافه می‌کنیم اگر:

- Search PostgreSQL دیگر کافی نباشد
- حجم Search بسیار بالا رود
- Queryهای Search پیچیده شوند

### Qdrant یا Vector DB جدا اضافه می‌کنیم اگر:

- Scale برداری از توان یا Convenience pgvector فراتر رود
- Vector workload مستقل و سنگین شود

### Kafka اضافه می‌کنیم اگر:

- Event volume بسیار زیاد شود
- چند Consumer مستقل داشته باشیم
- Event replay و streaming architecture ارزش واقعی ایجاد کند

### Kubernetes اضافه می‌کنیم اگر:

- تعداد Service و Serverها آن‌قدر زیاد شود که Docker Compose دیگر Operationally مناسب نباشد

اصل تصمیم:

> **Scale based on measurements, not imagination.**

---

# 35. تصمیم نهایی پیشنهادی

برای MVP فنی Briefly:

```text
Frontend
Next.js + TypeScript
        ↓
Backend
Go
        ↓
Database
PostgreSQL
   ├── pgvector
   ├── Full Text Search
   └── River Jobs
        ↓
Workers
Go
        ↓
Sources + AI Providers
```

Deployment:

```text
Docker
+
Docker Compose
+
Nginx
```

Observability:

```text
Structured Logs
+
Prometheus
+
Grafana
```

---

# 36. مهم‌ترین نکته Product

این Stack فعلاً **پیشنهاد فنی** است، نه مجوز شروع Build کامل.

طبق Product Validation Plan، Briefly هنوز باید ابتدا ثابت کند که:

> کاربر بعد از استفاده از Briefly واقعاً زمان کمتری برای بررسی منابع اصلی صرف می‌کند و احساس نمی‌کند خبرهای مهم را از دست داده است.

بنابراین ترتیب همچنان این است:

```text
Product Discovery
        ↓
Validation
        ↓
MVP Scope
        ↓
Technical Architecture
        ↓
Build
```

اگر Validation شکست بخورد، بهترین Stack دنیا هم محصول را نجات نمی‌دهد.

---

## خلاصه تصمیم

**Next.js** را برای Frontend انتخاب می‌کنیم چون ساخت Web Application مدرن را سریع می‌کند.

**TypeScript** خطاهای بیشتری را قبل از اجرا پیدا می‌کند و نگهداری Code را ساده‌تر می‌کند.

**Go** برای Backend و Workerها مناسب است چون Briefly تعداد زیادی Network Request و Background Job خواهد داشت.

**PostgreSQL** Database اصلی است چون Relationهای پروژه را خوب مدیریت می‌کند و با Extensionهایی مثل pgvector چند نیاز دیگر را هم پوشش می‌دهد.

**pgvector** باعث می‌شود برای MVP مجبور به راه‌اندازی Vector Database جدا نباشیم.

**River** Queue را با PostgreSQL ساده نگه می‌دارد و نیاز اولیه به Redis/RabbitMQ را حذف می‌کند.

**Docker + Docker Compose** Development و Deployment را قابل تکرار و ساده می‌کند.

**Nginx** ورودی امن و کنترل‌شده سرویس‌ها را فراهم می‌کند.

**Prometheus + Grafana** در Production کمک می‌کنند بفهمیم سیستم واقعاً چه وضعیتی دارد.

و مهم‌تر از همه:

> **هر تکنولوژی جدید فقط وقتی وارد Stack می‌شود که یک نیاز واقعی برای آن وجود داشته باشد.**
