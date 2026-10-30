# سند مادر پرامپت‌ها و توسعهٔ افزونهٔ ZarinShopBot

**نسخهٔ مرجع این سند:** 1.8.43  
**زبان:** فارسی  
**کاربرد:** انتقال دانش پروژه، شروع کار توسعه‌دهنده/دستیار جدید، بازبینی تغییرات و آماده‌سازی انتشار.

> **دامنه و امانت‌داری تاریخی:** این سند از پرامپت نگه‌داری‌شدهٔ پروژه، READMEها، changelog انتشارها و گزارش‌های ممیزی داخل مخزن گردآوری شده است. این سند رونویسی کلمه‌به‌کلمهٔ همهٔ پیام‌های چت از آغاز پروژه نیست؛ متن پیام‌هایی که در مخزن یا فایل‌های پروژه نگه‌داری نشده‌اند قابل بازسازی دقیق نیستند. برای جلوگیری از ساختن تاریخچهٔ غیرواقعی، پیوست‌ها و تاریخچهٔ انتشار موجود به‌عنوان مرجع حفظ شده‌اند. فایل اولیهٔ `docs/PROJECT-PROMPT.fa.md` نیز حذف نشده و همراه این فایل باقی می‌ماند.

---

## ۱. پرامپت مادر قابل استفاده برای ادامهٔ پروژه

متن زیر را می‌توان برای ادامهٔ توسعه، بازبینی یا اصلاح نسخه‌های بعدی به توسعه‌دهنده/دستیار داد:

> تو توسعه‌دهنده و بازبین افزونهٔ WordPress/WooCommerce به نام ZarinShopBot هستی. فروشگاه WooCommerce را به ربات‌ها و تجربه‌های فروش در Telegram، Bale و Rubika متصل می‌کنی. ابتدا ساختار فعلی، قراردادهای API و تست‌های مربوط را بررسی کن؛ سپس تغییر کمینه و موضعی انجام بده. قابلیت‌های سالم، داده‌های ذخیره‌شده، تنظیمات مدیر، هویت برند، امنیت سفارش و رفتار سایر پیام‌رسان‌ها را بدون دلیل تغییر نده.
>
> ### قواعد غیرقابل‌مذاکره
> 1. شناسه‌های اصلی پنل/تنظیمات را حفظ کن: صفحهٔ تنظیمات `zarincode_zarinshopbot_setting`، option `zarincode_settings`، گروه `zarincode_settings_options` و dashboard slug `zarincode_zarinshopbot`. فقط با دلیل فنی و مهاجرت سازگار تغییرشان بده.
> 2. هیچ موردی از شناسهٔ برند بازنشسته در فایل‌ها، نام‌ها، کامنت‌ها، مستندات یا بستهٔ انتشار باقی نماند؛ جست‌وجو به‌شکل case-insensitive انجام شود.
> 3. فایل‌های prompt و مستندات پروژه را حذف نکن. اگر نیاز به تکمیل دارند، نسخهٔ جدید/بخش تکمیلی اضافه کن و منابع قبلی را حفظ کن.
> 4. از کاربر توکن، رمز، credential پیامک، کلید خصوصی، PAT یا پیوند سفارش/پرداخت دارای مجوز درخواست نکن. رازها فقط از تنظیمات امن مدیریت خوانده شوند؛ در HTML، پاسخ عمومی، log یا تست ثبت نشوند.
> 5. سیاست account/guest، یکتایی شمارهٔ تلفن، اتصال امن شماره به حساب و تأیید OTP را حفظ کن. Kavenegar و Melipayamak ارائه‌دهندگان OTP پشتیبانی‌شده‌اند و credential آن‌ها فقط از تنظیمات مدیریت خوانده شود. اگر حساب اجباری یا OTP تلفن را لازم می‌کند، هیچ گزینهٔ «عدم دریافت تلفن» نباید الزام امنیتی را دور بزند؛ توضیح UI نیز باید این قفل را روشن بیان کند.
> 6. PDF فاکتور و بارکد را با کد/دارایی محلی افزونه یا هاست تولید کن؛ CDN، سرویس، API یا فونت/آیکون خارجی اضافه نکن. مجوز دسترسی به فایل و PDF سفارش باید بر اساس مالکیت/اجازهٔ WooCommerce بررسی شود.
> 7. مبالغ و درآمد را مطابق مقدار و واحد/نماد ارز WooCommerce نمایش بده؛ ترتیب نامعتبر مانند `ریال0` نپذیرفتنی است.
> 8. خطاهای افزونه را از خطاهای WordPress/WooCommerce، شبکه/هاست و پاسخ provider جدا کن. رویدادی که ثبت نشده است را موفقیت یا شکست قطعی گزارش نکن. دادهٔ حساس را log نکن.
> 9. رابط باید برای کاربر غیرفنی روشن، فارسی‌پذیر، واکنش‌گرا و قابل استفاده با صفحه‌کلید باشد. در عرض 320px نیز متن، فرم، checkbox، دکمه و جدول نباید روی هم بیفتند.
> 10. درخواست‌های کاربر برای Telegram، Bale و Rubika را از هم تفکیک کن. شباهت نام متدها، نوع update یا پرداخت به معنی یکسان بودن قرارداد API نیست. تغییر مشترک باید تست پلتفرم‌های دیگر را هم بگذراند.
> 11. در هر دور اصلاح، نسخه و metadataهای انتشار را هماهنگ کن، ZIP تازه را از آخرین سورس بساز، ساختار و CRC آرشیو را بررسی کن و SHA-256 و آزمون‌های واقعاً اجراشده را گزارش بده. ZIP قدیمی جای ZIP تازه را نمی‌گیرد.
> 12. محدودیت‌های محیط را صریح بگو. اگر PHP CLI یا سایت staging موجود نیست، PHP lint/runtime یا آزمون زندهٔ WordPress/WooCommerce/API را انجام‌شده اعلام نکن.
>
> ### معیارهای پلتفرمی
> - **Telegram:** رفتار موجود Bot API، webhook/polling، payment و Mini App را تا زمانی که نقص مشخصی با آزمون مستقل نشان داده نشده تغییر نده. پاسخ‌های مربوط به UI تلگرام را با آزمون‌های آن پوشش بده.
> - **Bale:** قرارداد بازوی رسمی، webhook/polling، دکمه‌های Web App و callback را مستقل رعایت کن. رابط مدیریت باید نشانی HTTPS قابل‌کپی و پیوند مستقیم قابل کلیک داشته باشد. برای بازشدن معتبر Mini App، تنظیم Main Mini App در BotFather و `initData` امضاشده لازم است؛ بازکردن URL در مرورگر عادی احراز هویت Mini App محسوب نمی‌شود. محدودیت `localStorage` در WebView نباید کل برنامه را از کار بیندازد؛ fallback نشست‌محور امن داشته باش. telemetry callback را با telemetry بازشدن Mini App یکی ندان. کوتاه‌سازی Unicode باید حتی بدون `mbstring` امن باشد.
> - **Rubika:** قرارداد API، مدل update/chat، احراز هویت webhook و payloadهای Rubika مستقل‌اند. هیچ قابلیت پرداخت بومی یا فیلد/مدتی را که در مستند رسمی تضمین نشده ادعا نکن. اصلاحات دیگر پلتفرم نباید مسیر روبیکا را ناخواسته تغییر دهند.
>
> ### روش انجام کار
> 1. درخواست جاری و فایل‌های آن را مشخص کن؛ محدودیت‌ها و معیار پذیرش را بنویس.
> 2. جست‌وجوی هدفمند در PHP/JS/CSS/templates/tests/docs و مسیر بارگذاری assets انجام بده؛ کد موجود و تست‌های regression را بخوان.
> 3. محل کم‌ریسک اصلاح را انتخاب کن و قرارداد option/API/HTML را بی‌دلیل نشکن.
> 4. آزمون regression ایستا/واحد مناسب اضافه یا به‌روز کن؛ تست را به جزئیات پیاده‌سازی شکننده وابسته نکن.
> 5. همهٔ آزمون‌های موجود، `node --check` فایل‌های JS، `git diff --check`، اسکن brand، version metadata و ساختار ZIP را اجرا کن.
> 6. تغییر را مرور کن، release notes را بنویس، ZIP جدید و SHA-256 تولید کن. دقیقاً گزارش بده چه چیزهایی اجرا شده و چه چیزهایی به‌دلیل نبود PHP/staging انجام نشده است.

---

## ۲. هویت، هدف و مرز پروژه

ZarinShopBot افزونه‌ای چندکاناله برای WordPress و WooCommerce است. WooCommerce منبع اصلی محصولات، سفارش‌ها، موجودی، tax، حمل‌ونقل، currency و وضعیت پرداخت است. ربات‌ها و Mini Appها لایهٔ کانال/رابط هستند و نباید منطق کسب‌وکار فروشگاه را به منبع دوم و متناقض تبدیل کنند.

پلتفرم‌های فعال در دامنهٔ پروژه:
- **Telegram:** Bot API، webhook و Mini App مستقل.
- **Bale:** API و Mini App مستقل؛ پرداخت درون Mini App فقط مطابق جریان رسمی و تأیید سمت سرور.
- **Rubika:** Bot API مستقل، webhook و رابط/ارسال متناسب با قابلیت‌های مستندشده.

این سه کانال قراردادهای جدا دارند. مدل مشترک داخلی یا helper مشترک فقط وقتی مجاز است که اختلاف‌های واقعی request، auth، keyboard، update و response را پنهان نکند.

### اصول UX/برند
- برند افزونه و امضای پیش‌فرض: زرین‌کد / Zarincode.com. امضای سفارشی مدیر باید حفظ شود؛ مهاجرت فقط مقدار default شناخته‌شدهٔ قبلی را تغییر می‌دهد.
- assetهای لازم، فونت‌ها و SVGها داخل افزونه‌اند؛ آیکون/فونت به CDN یا لینک خارجی متکی نشود.
- متن فارسی و انگلیسی، جهت RTL/LTR، ترجمهٔ gettext، کنتراست، focus و breakpoints باید در کنار هم بررسی شوند.
- checkboxهای دارای توضیح باید به‌عنوان گزینه‌های جدا و خوانا چیده شوند؛ متن توضیح نباید به عنوان Bold بچسبد.

---

## ۳. قراردادهای پایدار ذخیره‌سازی و URL

موارد زیر API داخلیِ پنل/نصب محسوب می‌شوند و بدون برنامهٔ مهاجرت تغییر نکنند:

| نوع | شناسهٔ پایدار |
|---|---|
| صفحهٔ تنظیمات اصلی | `zarincode_zarinshopbot_setting` |
| option تنظیمات اصلی | `zarincode_settings` |
| settings group | `zarincode_settings_options` |
| dashboard slug | `zarincode_zarinshopbot` |

تنظیمات مستقل پلتفرم‌ها، درگاه کارت‌به‌کارت، checkout و سایر ماژول‌ها ممکن است option اختصاصی داشته باشند؛ پیش از تغییر schema، registration، default، sanitize callback، migration و uninstall logic را بررسی کن. مقادیر سفارشی مدیر overwrite نشوند. برای افزودن یا حذف option، رفتار upgrade و uninstall را با آزمون پوشش بده.

---

## ۴. نمای معماری و نقشهٔ کد

> این نقشه برای یافتن محل کار است؛ قبل از هر تغییر، نام کلاس‌ها و پیاده‌سازی واقعی همان commit را از سورس بخوان.

- `zarinshopbot.php` — bootstrap افزونه، نسخه، enqueue/registration عمومی، hookها و مسیرهای آغازین.
- `defaults.php` — مقدارهای پیش‌فرض و migrationهای محافظ برای داده‌های قدیمی.
- `panel/` — رابط مدیریت؛ `panel/settings.php` پنل اصلی، `panel/main.php` داشبورد و `panel/partials/settings-save-bar.php` نوار ذخیرهٔ مشترک.
- `includes/` — منطق دامنه، یکپارچه‌سازی‌ها و adapterهای API؛ برای checkout، کانال‌ها، کارت‌به‌کارت، سفارش، Mini App و log اینجا را بر اساس کلاس مرتبط جست‌وجو کن.
- `assets/css/admin-settings.css` و `assets/css/admin-polish.css` — استایل‌های اصلی و polish مدیریت؛ selectorها را در scope افزونه محدود کن.
- `assets/js/` — رفتار پنل، Mini App و کد سمت کاربر؛ وابستگی شبکه‌ای مرورگر باید از URLهای نسبی/پلتفرمی معتبر باشد، نه localhost محیط توسعه.
- `languages/` — `.pot`, `.po`, `.mo`; gettext و metadata انتشار را هماهنگ نگه دار. `msgstr` خالی ناخواسته می‌تواند برچسب UI را پنهان کند.
- `tests/*.js` — آزمون‌های smoke/regression ایستا و JS؛ پوشش جدید متناسب با تغییر اضافه شود.
- `docs/` — prompt، مستندات توسعه، گزارش‌های ممیزی پلتفرم و راهنمای فارسی آفلاین.
- `vendor/` — وابستگی‌های همراه پروژه؛ قبل از افزودن/به‌روزرسانی dependency، مجوز، حجم، نسخه و آفلاین‌بودن را بررسی کن.

### مرزهای مسئولیت
- دادهٔ فروشگاهی، مبالغ، محصول، order و موجودی از WooCommerce خوانده شوند.
- adapter هر پلتفرم مسئول تبدیل payload و پاسخ مخصوص همان provider است.
- UI پنل فقط انتخاب/نمایش/ارسال تنظیمات معتبر را بر عهده دارد؛ رازها به خروجی عمومی منتقل نشوند.
- از تغییر در core WooCommerce یا plugin ثالث به‌عنوان راه‌حل افزونه‌ای پرهیز کن.

---

## ۵. امنیت حساب، تلفن، سفارش و پرداخت

### حساب و شماره تلفن
- سیاست account/guest باید از پنل و مطابق نیاز مدیر قابل انتخاب باشد.
- شمارهٔ تلفن برای هویت حساب یکتا بماند؛ شمارهٔ تأییدنشده نباید به حساب موجود دیگری متصل شود.
- OTP و تغییر تلفن با تأیید انجام شود؛ Kavenegar و Melipayamak از gatewayهای تنظیم‌شوندهٔ مدیریت‌اند.
- credentialهای OTP فقط از تنظیمات مدیریت خوانده شوند؛ داخل سورس، log، HTML، test fixture منتشرشده یا درخواست کاربر قرار نگیرند.
- اگر حساب اجباری یا OTP فعال است، انتخاب «عدم دریافت تلفن» برای عبور از الزام رد/قفل شود و UI چرایی آن را شفاف توضیح دهد.

### سفارش، موجودی و مالکیت
- سفارش Mini App قبل از انتقال به پرداخت باید آیتم‌ها و محاسبات معتبر WooCommerce داشته باشد. رزرو موجودی موقت با کاهش قطعی موجودی یکی نیست.
- کم‌شدن قطعی stock باید بر اساس جریان پرداخت/وضعیت معتبر WooCommerce انجام شود؛ مسیر `on-hold` کارت‌به‌کارت را از پرداخت تأییدشده جدا در نظر بگیر.
- آزمون چرخهٔ موجودی باید حداقل هم‌زمانی/رزرو، پرداخت موفق، لغو/انقضا و backorder را پوشش بدهد.
- لینک فایل دانلودی یا PDF باید با permission/order ownership کنترل شود؛ صرف دانستن یک شناسه/URL نباید دسترسی بسازد.

### PDF و بارکد
- تولید باید محلی باشد؛ هیچ سرویس PDF/Barcode بیرونی یا CDN اضافه نشود.
- barcode در صورت نیاز با library/کد همراه افزونه یا امکانات local ایجاد شود.
- خطا و fallback برای فایل مفقود/دسترسی ردشده روشن و بدون افشای مسیر حساس باشد.

### خطا و log
- حداقل چهار منشأ را از هم جدا کن: افزونه/کد PHP، WordPress/WooCommerce، شبکه/هاست، provider پیام‌رسان/OTP/پرداخت.
- telemetry زمان کل webhook یا API، موفقیت delivery، و بازشدن Mini App مفاهیم جدا هستند؛ عنوان اندازه‌گیری را دقیق نگه دار.
- token، OTP، secret، payment data و اطلاعات شناسایی غیرضروری در log ثبت نشوند.
- در retry و webhook، update تکراری را در صورت نیاز idempotent مدیریت کن؛ موفقیت API را از تحویل قطعی به کاربر متمایز کن.

---

## ۶. نکات مستقل هر پلتفرم

### Telegram
- Bot API نسخه/مستندات و فیلدهای واقعی update را بررسی کن؛ نوع chat یا فیلدی را که schema تضمین نمی‌کند از حدس نتیجه نگیر.
- webhook و long polling دو شیوهٔ دریافت جدا هستند؛ هم‌زمانی، offset، retry و duplicate update را در کد فعلی بررسی کن.
- Mini App authentication بر اساس `initData` معتبر سمت سرور است؛ فقط query یا `startapp` URL گواه اصالت نیست.
- command identifierها در UI/ترجمه به‌شکل literal باقی بمانند؛ توضیحات اطراف می‌توانند ترجمه شوند.

### Bale
- endpoint، متد، ساختار دکمه و callback را از مستند رسمی Bale بررسی کن و با Telegram یا Rubika یکی ندان.
- نشانی HTTPS وب‌اپ باید قابل کپی باشد؛ پیوند مستقیم در صورت پشتیبانی قابل کلیک نمایش داده شود.
- بازشدن Mini App در محیط عادی مرورگر به‌تنهایی احراز هویت `initData` نیست.
- رفتار `localStorage` در WebView ممکن است محدود باشد؛ fallback باید خطای storage را مهار کند، اما اعتبار نشست/پرداخت را جعل نکند.
- پرداخت Mini App فقط از مسیر رسمی پلتفرم و confirmation سمت سرور انجام شود؛ UI نباید صرفاً به callback مرورگر برای تسویه اعتماد کند.

### Rubika
- مدل‌های رسمی Chat/Update و schema متدها را از مستندات Rubika بخوان؛ `chat_type` یا مدت اعتبار `file_id` را بدون تضمین رسمی فرض نکن.
- cache شناسهٔ فایل باید scope امن (ربات/URL)، expiry/eviction و رفتار refresh پس از رد صریح API داشته باشد.
- دریافت webhook، ارسال پیام، keypad، attachment و پرداخت را مستقل بررسی کن؛ capability مستندنشده را در محصول وعده نده.

---

## ۷. قرارداد UI تنظیمات و ترجمه

- `.zarin-checkbox-row`: هر گزینه یک بلوک/ردیف مستقل؛ checkbox و متن در ستون‌های واضح؛ عنوان Bold و توضیح جدا و خوانا؛ wrap برای متن طولانی و breakpoint موبایل.
- `.zarin-checkbox-label`: label سادهٔ inline باید checkbox را با فاصله و هم‌ترازی صحیح نگه دارد؛ توضیح sibling باید از خود label تفکیک بصری داشته باشد.
- کلاس‌های toggle card مانند `.zarin-toggle-card-title` و `.zarin-toggle-card-desc` باید فاصله و line-height مناسب داشته باشند.
- فرم کانال‌ها در `.zarin-channel-content` نیز checkbox و `description` دارند؛ رفع فقط پنل اصلی کافی نیست.
- label کلیک‌پذیر، focus واضح، کنتراست، RTL/LTR، متن طولانی، zoom، viewport 320px و preference کاهش حرکت بررسی شوند.
- تغییر CSS در scope افزونه انجام شود تا WordPress admin و pluginهای ثالث آسیب نبینند.
- آیکون‌ها SVG محلی باشند؛ فونت متن را با فونت آیکون WordPress/TinyMCE اشتباه نگیر.
- زبان source و gettext catalogها هماهنگ باشد؛ placeholderهای positional (`%1$s`) با مقدارهای درست پر شوند؛ تست PO/POT/MO را اجرا کن.

---

## ۸. آزمون، تشخیص و معیار پذیرش

### بررسی‌های ایستا و محلی
- همهٔ `tests/*.js` را با Node اجرا کن.
- `node --check` را برای همهٔ فایل‌های JavaScript قابل‌حمل اجرا کن.
- در محیط Git: `git diff --check`.
- اسکن case-insensitive نام برند بازنشسته را روی کل پروژه، docs و بسته انجام بده.
- نسخه را بین plugin header/runtime، Composer، Stable tag، README، راهنمای آفلاین و آزمون release همگام کن؛ migration قدیمی را کورکورانه با تغییر version بازنویسی نکن.
- CSS/JSON/POT/PO و magic/header جدول MO را بررسی کن.
- ZIP را باز کن، `testzip()`/CRC، ریشهٔ پوشه، تعداد فایل‌ها و حضور فایل‌های الزامی را تأیید کن.

### بررسی‌هایی که staging می‌خواهند
موارد زیر را صرفاً با smoke test ایستا «زنده» اعلام نکن:
- فعال‌سازی واقعی در WordPress/WooCommerce و سازگاری نسخه‌ها.
- webhook Telegram/Bale/Rubika، تنظیم secret، ارسال/دریافت واقعی و پاسخ provider.
- Mini App روی WebView واقعی و `initData`.
- پرداخت، callback و چرخهٔ موجودی واقعی.
- OTP واقعی Kavenegar/Melipayamak.
- permission سفارش/دانلود و تحویل PDF.

### محدودیت فعلی محیط انتشار 1.8.43
- در محیط فعلی PHP CLI نصب نیست؛ `php -l`، تست runtime PHP و اجرای WordPress زنده انجام نشده است.
- برای نسخهٔ 1.8.43، ۴۱ فایل smoke test جاوااسکریپت و `node --check` برای ۵۰ فایل JS با موفقیت اجرا شدند. `git diff --check`، تعادل brace در CSS، header/magic فایل MO، اسکن case-insensitive برند و اعتبار ZIP بررسی شدند.
- موفقیت آزمون‌های ایستا، معادل تست عملی محیط staging نیست.

---

## ۹. نسخه‌گذاری و انتشار

1. ابتدا تغییرات واقعی و scope درخواست را تثبیت کن؛ شمارهٔ patch/minor را مطابق اثر تغییر انتخاب کن.
2. metadataهای runtime، سربرگ افزونه، Composer، Stable tag، README، guide، کاتالوگ gettext و release smoke test را هماهنگ کن. فایل‌های migration نسخه‌ای را صرفاً برای یکسان‌سازی ظاهری دستکاری نکن.
3. release notes را با تغییر واقعی بنویس؛ موارد قبلی را به نام نسخهٔ جدید جا نزن.
4. از آخرین سورس، بستهٔ نصب افزونه با ساختار `ZarinShopBot/...` تولید کن؛ `.git`، credential و فایل‌های موقت را وارد نکن؛ فایل‌های prompt و docs لازم را نگه دار.
5. ZIP را باز و CRC، version، assets، tests/docs و مسیر نصب را بررسی کن؛ SHA-256 محاسبه شود.
6. بستهٔ قدیمی را به‌جای بستهٔ جدید ارائه نکن.
7. محدودیت تست و کارهای staging را کنار لینک فایل گزارش کن.

### بستهٔ فعلی
- آخرین ZIP افزونه: `ZarinShopBot-1.8.43.zip` (در workspace ریشهٔ `/home/user/`).
- فایل‌های پروژه را در GitHub کاربر از این محیط با SSH ذخیره نمی‌کنیم؛ برای بارگذاری، کاربر باید فایل ZIP را خودش دانلود و در مخزن خود commit/push کند. هیچ کلید یا credentialی نباید در گفتگو ارسال شود.

---

## ۱۰. نقشهٔ مستندات فنی نگه‌داری‌شده

مستندات زیر کنار سورس بمانند و پیش از تغییر مرتبط خوانده شوند:

- `docs/PROJECT-PROMPT.fa.md` — پرامپت نگه‌داری‌شده و قواعد جاری/یادداشت‌های درخواست‌های انتشار.
- `docs/bot-platform-architecture-research-fa.md` — پژوهش معماری، مرزبندی adapter، updateها، routing، retry، امنیت و عملیات.
- `docs/telegram-api-audit-10.3-fa.md` — ممیزی Telegram و Bot API مبنای آن سند.
- `docs/bale-integration-audit-fa.md` — ممیزی پیاده‌سازی و ماتریس قابلیت‌های Bale.
- `docs/rubika-integration-audit-fa.md` و `docs/rubika-bot-api-catalog-fa.md` — ممیزی افزونه و کاتالوگ API رسمی Rubika.
- `docs/platform-capability-audit-fa.md` — ماتریس قابلیت/محدودیت و پیگیری‌های احراز هویت/تنظیمات.
- `docs/woocommerce-multichannel-checkout-audit-fa.md` — checkout چندکاناله، سفارش، موجودی و مرزهای WooCommerce.
- `docs/settings-panel-audit-fa.md` — نقشه و اصول UI تنظیمات.
- `docs/free-download-display-delivery-fa.md` — متن دانلود رایگان و تحویل امن فایل.
- `docs/rubika-bale-incident-audit-fa.md` — تفکیک اختلال provider/Webhook/Mini App و عیب‌یابی.
- `docs/guide-fa.html` — راهنمای آفلاین کاربر/مدیر؛ باید version آن با release همگام بماند.
- `README.md` و `readme.txt` — معرفی، نصب، تنظیمات و changelog کامل انتشارهای ثبت‌شده.

گزارش‌های ممیزی snapshot هستند: پیش از اقدام بر اساس endpoint یا قابلیت، مستند رسمی جاری provider را دوباره بررسی کن و نتیجهٔ زمان بررسی را ثبت کن.

---

## ۱۱. تاریخچهٔ تغییرات از آغاز changelog ثبت‌شده

تاریخچهٔ کامل رسمیِ ثبت‌شده از نسخهٔ 1.1.0 تا نسخهٔ جاری، در پیوست این سند از بخش Changelog فایل `readme.txt` درج می‌شود. این بخش را هنگام ادامهٔ پروژه حفظ و فقط با افزودن نسخهٔ جدید به‌روز کن. نسخه‌های پیش از 1.1.0 یا گفت‌وگوهایی که در فایل‌های پروژه ثبت نشده‌اند در منابع حاضر موجود نیستند؛ برای آن‌ها رویداد یا درخواست ساختگی ننویس.

---

## پیوست A — متن پرامپت نگه‌داری‌شدهٔ پروژه

متن فعلی `docs/PROJECT-PROMPT.fa.md` در ادامه عیناً اضافه می‌شود تا نسخهٔ مادر هم در یک فایل مستقل قابل‌استفاده باشد؛ فایل اصلی نیز جداگانه حفظ می‌شود.

---


```markdown
# پرامپت کامل پروژهٔ ZarinShopBot

این سند، درخواست‌ها و معیارهای پذیرش ارائه‌شده برای توسعه و بازبینی ZarinShopBot را گردآوری می‌کند. این فایل فقط شرح نیازمندی‌های پروژه است و شامل هیچ راز، توکن، کلید خصوصی یا دستورالعمل محرمانهٔ سامانه نیست.

## نقش و هدف

به‌عنوان توسعه‌دهندهٔ افزونهٔ WordPress/WooCommerce، سورس ZarinShopBot را با حفظ قابلیت‌های موجود بررسی و اصلاح کن. این افزونه فروشگاه WooCommerce را به Telegram، Bale و Rubika وصل می‌کند. تفاوت‌ها و محدودیت‌های هر API را جداگانه رعایت کن؛ از تغییرات مشترک غیرضروری که ممکن است در یک کانال دیگر رگرسیون بسازند پرهیز کن.

## قواعد پایدار پروژه

1. این شناسه‌های تنظیمات بی‌دلیل عوض نشوند:
   - صفحهٔ تنظیمات: `zarincode_zarinshopbot_setting`
   - option: `zarincode_settings`
   - settings group: `zarincode_settings_options`
   - صفحهٔ داشبورد: `zarincode_zarinshopbot`
2. در کل پروژه هیچ شناسهٔ برند بازنشسته باقی نماند؛ جست‌وجو باید case-insensitive باشد.
3. فایل‌های prompt پروژه حذف یا بازنویسیِ ناخواسته نشوند.
4. credential پیامک، توکن یا رمز پلتفرم، یا پیوند سفارش دارای مجوز از کاربر درخواست نشود. رازها باید از تنظیمات مدیریت گرفته شوند و در لاگ/HTML افشا نشوند.
5. سیاست حساب/مهمان از پنل مدیریت قابل انتخاب بماند؛ شمارهٔ تلفن یکتا باشد و ورود/تغییر تلفن با OTP تأیید شود. درگاه‌های OTP شامل Kavenegar و Melipayamak باشند و credentialها فقط از تنظیمات مدیریت خوانده شوند.
6. PDF فاکتور و بارکد باید با کد/دارایی‌های محلی افزونه یا هاست ساخته شوند؛ از CDN، API یا سرویس PDF/بارکد خارجی استفاده نشود. مالکیت سفارش برای مشتری مهمان یا عضو امن بررسی شود و مشتری مجاز بتواند PDF را دریافت کند.
7. درآمد با مقدار عددی و سپس فاصله و واحد/نماد ارز WooCommerce نمایش داده شود؛ ترتیب وارونه مانند «ریال0» پذیرفته نیست.
8. بررسی لاگ باید کامل و کانال‌به‌کانال باشد. خطای افزونه، خطای پاسخ provider و خطای محیط/هاست را از هم جدا کن؛ رویدادهای ثبت‌نشده را به‌عنوان موفقیت یا شکست قطعی معرفی نکن.
9. رابط کارت‌به‌کارت و متن‌های مشتری باید برای کاربر غیرفنی روشن باشد. تنظیمات و پیام‌های خصوصی فعلی نباید پشت toggle بسته پنهان شوند.
10. طراحی موبایل از عرض 320px پشتیبانی کند.
11. آرشیوهای قدیمی انتشار نگه‌داری نشوند؛ فقط سورس پروژه و deliverable درخواستی باقی بمانند.
12. پس از هر رفع اشکال، نسخه و metadataها را هماهنگ کن، ZIP انتشار را از جدیدترین سورس بساز، آرشیو قدیمی را نگه ندار، محتویات ZIP را بررسی کن و SHA-256 و آزمون‌های واقعاً اجراشده را گزارش بده.

## معیارهای کانال‌ها

### Telegram
- پیاده‌سازی موجود، APIها، احراز هویت، Webhook، پرداخت و Mini App تلگرام بدون نیاز تغییر باقی بماند، مگر نقص مشخص و آزمون مستقل آن ثابت شود.
- تغییرات مشترک باید با آزمون‌های Telegram کنترل شوند.

### Bale
- دکمه‌های Web App و callback باید مطابق API رسمی بله کار کنند.
- نشانی HTTPS وب‌اپ در پنل قابل کپی باشد و پیوند مستقیم Mini App کلیک‌پذیر نمایش داده شود.
- رابط مدیریت صریحاً توضیح دهد که پیوند مستقیم `https://ble.ir/<bot_username>?startapp` به تنظیم Main Mini App در BotFather وابسته است؛ بازکردن صفحهٔ HTTPS در مرورگر معمولی به‌تنهایی `initData` امضاشده فراهم نمی‌کند.
- محدودیت یا خطای `localStorage` در WebView نباید کل JavaScript Mini App را متوقف کند؛ در نبود storage پایدار، برنامه با fallback نشست‌محور کار کند.
- کوتاه‌سازی عنوان فارسی دکمه، حتی بدون `mbstring`، نباید UTF-8 را وسط نویسه قطع کند.
- گزارش موفقیت callbackها را با telemetry بازشدن Mini App اشتباه نگیر.

### Rubika
- تغییرات بله نباید selector، payload، احراز هویت یا جریان webhook روبیکا را تغییر دهد.
- هر اصلاح مستقل روبیکا باید براساس API مستند و آزمون‌های خودش انجام شود.

## وضعیت اصلاحات این نسخه

نسخهٔ 1.8.38 شامل رفع خطای ترجمهٔ فارسی با `msgstr` خالی و نمایش آیکون‌های ویرایشگر با SVG محلی است:
- handler کپی اختصاصی `.zarin-copy-webapp-url` برای پنل تنظیمات بله، شامل Clipboard API و fallback.
- پیوند مستقیم بله به‌صورت anchor قابل کلیک و کپی‌پذیر؛ راهنمای Main Mini App در BotFather.
- wrapper امن برای خواندن/نوشتن/حذف `localStorage` و fallback حافظه‌ای/JSON معیوب در storefront Mini App.
- کوتاه‌سازی Unicode ایمن برای عنوان دکمهٔ Web App بله در محیط فاقد `mbstring`.
- بررسی لاگ نصب: خطاهای parse-time فایل‌های globally-required روی همهٔ کانال‌ها اثر می‌گذارند، نه فقط بله. در log مسیر نصب/شماره‌خط فایل‌ها با سورس فعلی منطبق نبود و نسخهٔ قدیمی/تکراری باید در هاست حذف یا غیرفعال شود.
- guard سفارش ماژول فاکتور با `is_a($order, 'WC_Order')` نوشته شده است تا تشخیص نوع سفارش به token کلاس fully-qualified وابسته نباشد؛ `manage_stock` و `$channel` نیز در سورس فعلی به‌صورت امن بررسی/مقداردهی می‌شوند.
- سفارش‌های سفارشی Telegram/Bale Mini App پس از ذخیرهٔ line itemها و پیش از انتقال به درگاه، از طریق `wc_reserve_stock_for_order` رزرو موجودی می‌شوند؛ اگر API رزرو موجودی برای کالای موجودی‌مدیریت‌شده و بدون backorder در دسترس نباشد، checkout fail-safe متوقف می‌شود. نتیجهٔ نهایی موجودی را از reservation موقت جدا کن: موجودی عددی پس از پرداخت تأییدشده یا مسیر on-hold کارت‌به‌کارت کاهش می‌یابد، نه صرفاً با ساخت سفارش pending.
- رفع Parse error تنظیمات با بستن هفت تگ PHP در فراخوانی‌های inline و افزودن smoke test بازگشتی.
- اصلاح deprecation `str_ireplace(null)` در `OrdersTrait::toPersian()` با محافظت از ورودی‌های غیر scalar.
- ارتقای نسخهٔ انتشار به 1.8.36 برای رفع parse و deprecation؛ سپس در 1.8.37 fallback عنوان/متن کارت‌به‌کارت برای ورودی‌های خالی، تعیین فونت `tinymce` برای آیکون‌های ویرایشگر، حفظ فونت رسمی Dashicons برای آیکون‌های نامنقشه‌شده، و اعمال کنتراست scoped اضافه شد.
- در 1.8.38، ۳۷ عبارت ترجمهٔ فارسی با `msgstr` خالی به متن مبدأ برگشتند، `.mo` بدون ترجمهٔ خالی بازساخته شد و فیلتر runtime برای کاتالوگ stale اضافه شد؛ toolbar از SVG محلی استفاده می‌کند تا مربع خالی وابسته به font glyph رخ ندهد.
- نسخهٔ 1.8.38 در سربرگ، runtime، Composer، Stable tag، README، راهنمای آفلاین، فایل‌های ترجمه، آزمون نسخه و ZIP همگام است.

## آزمون و انتشار

- آزمون‌های smoke JavaScript موجود، به‌ویژه `tests/bale-miniapp-controls-smoke.js`، `tests/telegram-miniapp-botfather-smoke.js`، `tests/rubika-start-routing-smoke.js`، `tests/platform-client-split-smoke.js` و `tests/release-version-smoke.js` را اجرا کن.
- برای فایل‌های JavaScript از `node --check` استفاده کن.
- آزمون چرخهٔ موجودی `tests/channel-stock-lifecycle-smoke.js` را همراه تست‌های هر سه پلتفرم اجرا کن.
- PHP CLI در محیط ساخت این انتشار موجود نیست؛ PHP lint یا آزمون اجرایی PHP را ادعا نکن.
- آزمون live بله، Telegram، Rubika، WordPress یا WooCommerce را فقط پس از اجرای واقعی staging اعلام کن.
- قبل از انتشار، `git diff --check`، بازبینی فهرست فایل‌های ZIP، هماهنگی شمارهٔ نسخه و اسکن case-insensitive شناسه‌های برند بازنشسته را انجام بده.
- هرگونه محدودیت آزمون و نیاز staging را در یادداشت انتشار شفاف بیان کن.


## یادداشت انتشار 1.8.39
- پیش‌نمایش منوی فروشگاه اکنون از ده SVG محلی افزونه استفاده می‌کند و تبدیل emoji وردپرس به تصویر Twemoji خارجی فقط در صفحهٔ تنظیمات افزونه متوقف شده است.
- ردیف‌های منو به Grid کلاس‌محور با نقاط شکست واکنش‌گرا تبدیل شدند.
- ZIP تازه باید از آخرین سورس با نام `ZarinShopBot-1.8.39.zip` ساخته و آزمون‌های استاتیک اجرا شوند؛ PHP CLI و WordPress زنده در دسترس نیستند.


## یادداشت انتشار 1.8.40
- تنظیم سراسری `zarincode_settings[register_req_phone]` فعال شد: موبایل/تلفن ثابت، فقط موبایل، فقط تلفن ثابت و عدم دریافت. پروفایل‌های فیزیکی و دانلودی امکان پیروی از گزینهٔ کلی یا override دارند.
- سیاست حساب اجباری و OTP دریافت موبایل را همچنان الزام می‌کند؛ حالت انتخابی مدیر در زمان قفل حفظ می‌شود و پس از برداشتن قفل قابل بازگشت است.
- ZIP تازه باید از آخرین سورس با نام `ZarinShopBot-1.8.40.zip` ساخته شود. PHP CLI و WordPress زنده در دسترس نیستند.


## یادداشت انتشار 1.8.41
- تب فرمان‌ها در `#tab=commands` بازآرایی شد: aliasها کنار فرمان اصلی، فرمان‌های تکمیلی جدا و بلوک کپی Telegram جمع‌شده است.
- شناسهٔ فنی فرمان‌ها در UI literal می‌مانند؛ msgidهای فرمان از PO/POT/MO حذف شدند و توکن‌های داخل پیام‌های ترجمه‌پذیر به placeholder تبدیل شدند.
- تفاوت ثبت منوی هر پیام‌رسان بدون ستون‌های تکراری توضیح داده شد و آزمون ایستا برای عدم تکرار/ترجمهٔ شناسه‌ها اضافه شد.
- ZIP تازه باید از آخرین سورس با نام `ZarinShopBot-1.8.41.zip` ساخته شود. PHP CLI و WordPress زنده در دسترس نیستند.


## یادداشت انتشار 1.8.43
- ردیف‌های `.zarin-checkbox-row` در پنل تنظیمات به‌صورت بلوک‌های مجزای واکنش‌گرا نمایش داده می‌شوند؛ عنوان Bold و متن توضیح فاصلهٔ خوانا دارند.
- `.zarin-checkbox-label` و چک‌باکس‌های فرم‌های مستقل Telegram/Bale/Rubika نیز هم‌تراز و با فاصلهٔ مناسب نمایش داده می‌شوند.
- نسخه و metadataها به 1.8.43 هماهنگ شدند؛ آزمون‌های smoke جاوااسکریپت و `node --check`، تعادل آکولاد CSS، اسکن برند و CRC/ساختار ZIP بررسی شدند. PHP CLI و WordPress زنده در دسترس نیستند.
- ZIP تازه باید `ZarinShopBot-1.8.43.zip` باشد؛ خروجی‌های قدیمی جای این بسته را نمی‌گیرند.

## یادداشت انتشار 1.8.42
- برای روبیکا `file_id` تصویر بر اساس bot token و URL تصویر cache می‌شود؛ cache hit درخواست upload و fetch را حذف می‌کند.
- رویدادهای ساختاریافته در shutdown batch می‌شوند و زمان کامل webhookهای Bale/Rubika ثبت می‌شود.
- امضای پیش‌فرض پیام شامل پیوند HTTPS زرین‌کد است؛ مهاجرت فقط مقدار قدیمیِ دست‌نخورده را تغییر می‌دهد.
- ZIP تازه باید `ZarinShopBot-1.8.42.zip` باشد. PHP CLI و WordPress زنده در دسترس نیستند.
```

## پیوست B — تاریخچهٔ کامل changelog ثبت‌شده

متن زیر از بخش changelog رسمی `readme.txt` این نسخه گرفته شده است؛ آن فایل همچنان منبع اصلی انتشار WordPress است.

```text
== Changelog ==

= 1.8.43 =
* Give checkbox settings with explanatory copy distinct responsive rows, clearly separate bold titles from helper text, and align checkbox labels in Telegram/Bale/Rubika channel settings.
* Reuse Rubika-uploaded image file IDs per bot and image URL, avoiding repeated image download and upload round-trips; expire cached IDs and refresh only after an explicit provider rejection.
* Batch structured activity-log writes at request shutdown and record total Bale/Rubika webhook durations alongside existing per-API timings.
* Set a professional default message signature with a clickable Zarincode.com link; migrate only the untouched previous default and preserve custom signatures. PHP CLI and live WordPress are unavailable in the build environment.

= 1.8.41 =
* Reorganize the commands tab: list primary commands and aliases once, move extra commands to their own table, and collapse the Telegram copy block.
* Keep bot command identifiers literal in the UI and translation catalogs; preserve translatable descriptions with positional placeholders. Clarify platform-specific menu registration behavior without repeating support columns.
* Add static regression coverage for command-tab duplication, literal identifiers and gettext catalogs. PHP CLI and live WordPress are unavailable in the build environment.

= 1.8.40 =
* Make the store order phone mode administrator-configurable: mobile or landline, mobile only, landline only, or do not collect.
* Allow downloadable and physical/mixed bot checkout profiles to inherit the global phone mode or override it independently; sanitize all supported values.
* Keep a verified mobile mandatory when account-required or SMS OTP policies are enabled, without discarding the administrator’s saved preference while the mode is locked.
* Add regression smoke checks for phone mode selection, profile inheritance, and account/OTP safeguards. PHP CLI and live WordPress are unavailable in the build environment.

= 1.8.39 =
* Replace store-menu preview emoji with ten packaged local SVG icons and disable WordPress emoji-to-remote-image conversion on the plugin settings screen, preventing broken remote Twemoji images.
* Rebuild core menu setting rows with aligned CSS Grid columns and responsive tablet/mobile layouts for preview, Persian/English labels, enable checkbox and priority.
* Validate local icon mappings and responsive menu styling with static smoke checks; PHP CLI and a live WordPress site are not available in the build environment.

= 1.8.38 =
* Fix empty Persian gettext translations that erased card-transfer menu titles, gateway names, descriptions and the enabled-checkbox label; 37 untranslated entries now map to source text, the compiled MO catalog has no empty translations, and a runtime gettext guard protects against stale external catalogs.
* Render all configured message-editor toolbar glyphs with local SVG masks, independent of icon-font availability or theme overrides.
* Keep card-transfer title and customer instructions visible for empty saved values, and preserve readable labels/contrast.
* JavaScript/static checks pass; PHP CLI and live WordPress staging are unavailable. Validate the admin screen on staging before production.

= 1.8.37 =
* Restore the default card-transfer title and customer copy when saved values are empty, whitespace-only, or contain only empty editor markup.
* Protect card-transfer headings, labels and help text with scoped high-contrast styles so admin theme rules cannot make the text disappear.
* Preserve the correct TinyMCE `tinymce` icon font and WordPress Dashicons fallback; only explicitly mapped icons use local SVG masks.
* JavaScript/static smoke tests pass; PHP CLI and live WordPress staging are unavailable. Validate the PHP files and inspect the editor UI on staging before production.

= 1.8.36 =
* Close all seven inline PHP tags around message editor render calls in the settings panel, preventing the reported parse error when opening plugin settings.
* Make Persian digit conversion safe for null and non-scalar inputs, removing the reported PHP deprecation from OrdersTrait.
* Add regression smoke coverage for inline PHP boundaries and null-safe digit conversion.
* JavaScript/static smoke tests pass; PHP CLI and live WordPress staging are unavailable in the build environment. Verify PHP syntax and open the settings screen on staging before production.

= 1.8.35 =
* Reserve WooCommerce stock for custom Telegram/Bale Mini App orders after line items are saved and before payment handoff; fail safely when stock-managed, non-backorder items cannot be held.
* Preserve WooCommerce-native stock reduction on verified payment completion and the existing immediate reduction for card-transfer orders placed on hold.
* Add cross-platform stock lifecycle smoke checks for Telegram, Bale, Rubika, Mini Apps, native invoices, website gateways, free orders, and manual transfer.
* JavaScript/static checks pass; PHP CLI and live WooCommerce staging are unavailable, so validate PHP syntax and actual stock changes on staging before production.

= 1.8.34 =
* Trace the installation log: parse-time fatals occurred in plugin files loaded globally, so they can prevent all channels from booting; the error log showed different source paths/revisions, not a Bale API failure.
* Remove fully-qualified `instanceof` tokens from the invoice order guard; use a class-string check consistent with the website checkout guard.
* The current source retains safe guards for absent `manage_stock` and initializes the order channel before metadata use, eliminating the two reported PHP warnings.
* The log’s WP-Cron/Action Scheduler `could_not_set` entries are separate WordPress scheduling/storage failures and are not Bale webhook errors.
* JavaScript/static smoke tests pass; PHP CLI and live WordPress/Bale staging were not available. Run PHP lint and a single-copy activation test on staging before production.

= 1.8.33 =
* Repair Bale Mini App administration: delegated URL copying, a clickable direct-launch link, and explicit BotFather Main Mini App setup guidance.
* Keep the shared storefront responsive when WebView localStorage is blocked or contains invalid JSON, using an in-memory fallback.
* Truncate Bale menu button labels on UTF-8 character boundaries when mbstring is unavailable; Telegram and Rubika paths remain unchanged.
* JavaScript syntax checks and all 33 smoke suites pass. PHP CLI and live Bale/WordPress staging were not available; verify on staging before production.

= 1.8.32 =
* Correct the fatal checkout validation guard by using a guarded WooCommerce order-type check instead of a fragile fully-qualified token in the affected hooks.
* Initialize the channel platform before writing platform-specific order metadata, preventing an undefined-variable warning during Bale/Rubika checkout. The cart stock check uses safe absent-key handling.
* Keep the secure bot invoice PDF link, available only for the order owner chat.
* Verify the phone-index table after dbDelta before marking its schema ready; fail safely when unavailable and remove the index/schema marker during plugin uninstall.
* Use WordPress visual editors for bot messages, platform overrides, broadcasts, campaign text and card-transfer customer copy; show per-field dynamic variables and normalize rich formatting to each chat API's supported subset.
* Add the previously implemented chat ID and last-location placeholders to the message palette; correctly resolve bot signatures and register/translate platform-specific overrides through WPML. Remove the nonfunctional product-title/link chips from generic broadcasts; retain the real `%product%` token for product posts.
* JavaScript/static smoke tests pass; no PHP CLI or live WordPress/WooCommerce runtime was available, so site-side PHP execution still requires staging validation.

= 1.8.31 =
* Add a PDF invoice download link to each customer-owned Telegram, Bale and Rubika bot order card. The shared order view verifies the chat ID before showing the link; the generated PDF remains local to the plugin and the existing guest/order-key or account-owner download checks remain in force.
* The Rubika link is represented through its documented HTTPS Link metadata; Telegram and Bale use their supported URL buttons.
* JavaScript/static checks pass. PHP CLI and live platform/WooCommerce staging are unavailable in the build environment.

= 1.8.30 =
* Normalize sales/revenue amounts in the dashboard to render the localized amount first, followed by one space and the WooCommerce currency symbol, independent of the configured currency position.
* Apply the same formatter to platform revenue, today/month summaries and payment-method totals; isolate the amount in LTR layout while preserving surrounding spaces and WooCommerce number precision/separators.
* Add static regression checks for currency-position independence, multi-currency symbol selection and whitespace.
* JavaScript/static tests pass. PHP CLI and WordPress admin runtime are not available in the build environment.

= 1.8.29 =
* Add a customer-downloadable WooCommerce order invoice PDF, generated locally by bundled plugin code without a remote PDF/barcode service or CDN.
* Add a standard Code 128-B barcode containing a unique internal order reference and store-keyed signature, rendered as vector bars in the PDF.
* Embed the locally bundled DejaVu Sans font and glyph metrics for Persian/Arabic and Latin text; include the font license and PDF rendering assets inside the plugin.
* Expose a secured invoice download link on order details, customer order emails, and My Account order actions. Guest downloads require the order key; signed-in customers may download their own order invoice.
* JavaScript/static checks pass. PHP CLI and live WooCommerce rendering are unavailable in the build environment; test generated PDFs and barcode scanning on staging before production.

= 1.8.28 =
* Add administrator-controlled guest/optional/account checkout policy, configurable WooCommerce checkout field profiles, custom order fields for classic checkout and Mini App, and WooCommerce phone-login support.
* Add encrypted SMS provider credential settings for Kavenegar and Melipayamak, rate-limited OTP verification for web checkout, Mini App and bot order flows, and a unique phone ownership index for account linking.
* Add Mini App logo/color branding and shared message defaults with optional Telegram/Bale/Rubika overrides, including editable help and about pages.
* This release has static/JavaScript smoke coverage only in the build environment. Native chat receipt upload across Telegram/Bale/Rubika and complete custom-field parity for every bot flow still require staging validation and follow-up work; do not deploy without reviewing the platform caveats.

= 1.8.27 =
* Add a filter-aware, administrator-only TXT download to Activity Logs, using the same redacted records shown in the dashboard and nonce/capability checks.
* Diagnose Rubika no-reply evidence: webhook route authentication rejects mismatched URL secrets with 403; the Rubika settings page now warns when no registered route verifier exists or it differs from the current secret. Authentication remains fail-closed; register the Rubika webhook after deployment.
* Force Bale/Telegram Mini App AJAX and returned WooCommerce payment URLs to HTTPS, disable intermediary caching for catalog fetches, and add safe console/server diagnostics for catalog failures.
* Add regression smoke checks for TXT export, Rubika auth-state guidance and Bale Mini App HTTPS/payment flow. JavaScript/static tests pass; no live Rubika/Bale or WordPress staging was available.

= 1.8.26 =
* Fix a PHP parse error in the payment-redirect branch that prevented WordPress from activating the plugin. The nested ternary for selecting the redirect key had one extra closing parenthesis.
* Correct malformed fully-qualified namespace references in the bundled admin diagnostics PHP test suite.
* Validate all 91 bundled PHP files with a PHP grammar parser (zero syntax errors); PHP CLI and WordPress/WooCommerce runtime were unavailable.
* Carry forward the free-download display labels, named WooCommerce download links, platform audit and regression tests from 1.8.25.

= 1.8.25 =
* Display a Persian “دانلود رایگان” label for downloadable products whose current WooCommerce price is zero; variable products are labeled only when every purchasable variation is zero-priced. Product names in WooCommerce remain unchanged.
* Apply display-only titles across Telegram, Bale, Rubika, recommendations, cart and Mini App product views.
* Send authorized WooCommerce download URLs as clickable file-name links instead of printing raw URLs; suppress Telegram link previews. Actual file uploads/attachments are not implemented.
* Add static regression coverage and a platform delivery capability/security audit. JavaScript/static checks pass; PHP CLI and live platform staging are not available in the build environment.

= 1.8.24 =
* Audit Rubika transport, webhook event mapping, commerce identity, inline/chat keypad, rich metadata, product image upload and WooCommerce checkout compatibility against the official API catalog.
* Convert URL buttons to documented HTTPS Link metadata for text/edit flows; keep safe visible URLs in file captions and never send an undocumented Button.url field.
* Preserve UTF-8 and UTF-16 metadata offsets, prioritize checkout links under the 30-part metadata limit, harden image upload validation, and fail explicitly for undocumented Rubika member lookup.
* Add a full integration coverage/limitations report. Runtime PHP and live Rubika/WordPress integration tests remain deployment checks.

= 1.8.23 =
* Render WooCommerce payment links in Rubika messages using documented Link metadata; reject non-HTTPS links and do not send the undocumented Button.url field.
* Native Rubika wallet payments remain unavailable until Rubika publishes/provides a merchant payment API and verification contract.
* PHP and live payment tests require an appropriate runtime and merchant credentials.


= 1.8.22 =
* Harden Rubika commerce identity: keep opaque string message IDs intact across the shared bot navigation/edit/delete flow.
* Bind Rubika cart and checkout session ownership to the message sender while preserving chat_id as the reply destination.
* Resolve chat type using the documented getChat method; block group/channel sales flows to avoid exposing private cart and checkout data.
* Ignore non-actionable Rubika lifecycle events and bot-originated messages; accept shared contact phone numbers in checkout.
* PHP/WordPress live tests were not run in the build environment.


= 1.8.21 =
* Avoid fatal errors in Telegram photo-caption truncation and subscriber avatar initials when optional mbstring is unavailable.
* Remove the unused PDO extension from the environment recommendation.
* Review Bale/Rubika reply destination handling; preserve Rubika chat_id routing and avoid exposing private commerce replies to Bale groups.
* Extend offline smoke coverage. PHP CLI and live WordPress/WooCommerce/channel credentials were unavailable for runtime integration tests.

= 1.8.20 =
* Remove obsolete product identifiers and compatibility shims from plugin source, assets, docs and tests; retain only current Zarincode routes and identifiers.
* Remove obsolete legacy migrations and fallback references; add a repository-wide branding smoke test.

= 1.8.19 =
* Namespace the settings admin page as `zarincode_zarinshopbot_setting` across menu registration, section/tab links, redirects, JavaScript and offline guide.
* Redirect old settings page URLs to the new slug while preserving tab/query state.
* Keep the WordPress option name `zarincode_settings` and settings group unchanged so saved configuration is preserved.

= 1.8.18 =
* Fix Rubika reply routing: preserve webhook chat_id separately from sender_id and send shared-engine replies to the correct conversation.
* Add regression coverage for StartedBot fallback, distinct sender/chat identifiers, and protection against redirecting unrelated admin destinations.

= 1.8.17 =
* Fixed Telegram menu synchronization so it no longer replaces a Mini App menu button with a commands-only button; when enabled, the plugin now registers its HTTPS Mini App URL through setChatMenuButton.
* Generated Telegram/Bale Mini App URLs now use HTTPS; menu configuration reruns when either commands or the Mini App setting changes.
* Improved BotFather setup instructions and getMe diagnostics to detect a mismatch between the saved bot username and the bot token.
* Added offline smoke coverage. PHP CLI, Telegram credentials and a live BotFather/API test were not available in the build environment.

= 1.8.16 =
* Fixed a PHP parse error in the Store API checkout validator so the plugin loads on supported PHP versions.
* Guarded the cart stock check against omitted stock metadata and added the WooCommerce CRUD `manage_stock` value to product data.
* Offline JavaScript/static checks are available; PHP CLI and live WordPress/WooCommerce verification were not available in the build environment.

= 1.8.15 =
* Made full name, mobile phone, and valid email mandatory in bot checkout, Mini App checkout, and WooCommerce website checkout for downloadable, physical, and mixed carts; stale/disabled options can no longer bypass the requirement.
* Kept validated email on downloadable WooCommerce orders instead of clearing it, including Mini App orders, so download permissions and order records retain the customer email.
* Made the Mini App email field visible and required even when shipping fields are hidden; added server-side validation to the endpoint and direct WooCommerce Store API checkout hooks.
* Updated admin controls to show these identity fields as mandatory and non-disableable; preserved configurable shipping/address fields and mixed-cart shipping behavior.
* Updated offline smoke tests and checkout guidance. JavaScript/static checks are available; PHP CLI and live WordPress/WooCommerce verification are not available in this environment.

= 1.8.14 =
* Changed the dashboard slug to zarincode_zarinshopbot and retained a query-preserving redirect from zarincode_main.
* Added guarded uninstall cleanup for plugin-owned options, transients, CPT data, metadata, scheduled events, Action Scheduler records, WPML strings and namespaced legacy tables; WooCommerce orders are retained.
* Updated the displayed plugin name to ربات زرین شاپ and set the product/developer URLs.
* Offline smoke checks pass; live WordPress/WooCommerce and PHP runtime verification was not available.

= 1.8.13 =
* Fixed the administrator diagnostics action by bundling its read-only suite.
* Added safe system checks for WooCommerce, REST, channel configuration, secret encryption, webhook scheme, and required assets.
* Escaped diagnostic result labels and details in the admin UI.
* Offline JavaScript smoke checks pass; live WordPress/WooCommerce/provider verification was not available.

= 1.8.12 =
* Fixed Telegram HTML parsing for photo captions and edited messages; escaped HTML entities are no longer decoded into active markup before sanitization.
* Converted shared HTML formatting to Bale's documented Markdown syntax across messages, media captions and edits; Telegram-only parse_mode is not sent to Bale.
* Prevented raw HTML from leaking into Rubika photo captions by sending plain text, without assuming undocumented sendFile caption metadata support.
* Normalized product names in channel product lists, cart messages and add-to-cart confirmations.
* Added offline per-adapter regression checks. No live Telegram, Bale or Rubika API test was available.

= 1.8.11 =
* Fixed escaped HTML tags leaking into Telegram product notifications; product names are normalized and escaped as plain text while the intended bold title remains formatted.
* Applied the same safe title handling to back-in-stock notifications and added regression coverage.

= 1.8.10 =
* Fixed Telegram inline callbacks by acknowledging callback queries at webhook ingress before database and WooCommerce work.
* Added a one-time upgrade webhook refresh for existing Telegram installations so callback_query is explicitly subscribed.
* Expanded webhook diagnostics to show whether callback_query is present in the live allowed_updates list.
* Added independent bot checkout-field profiles for downloadable products and physical/mixed carts. Name, mobile phone and valid email are mandatory for all order types; downloadable email is retained on the WooCommerce order. Shipping/address behavior remains based on cart type.
* Free downloadable orders now complete through WooCommerce and send permitted links; paid downloads are released only after WooCommerce confirms payment. Card-transfer downloads remain gated on manager approval.
* Prevented positive-total orders from being marked paid when no payment method is selected, and added idempotency for free/no-payment order creation.
* Fixed WooCommerce shipping-rate discovery so storefront shipping visibility does not suppress real rates; downloadable lines are excluded, cart/session state is restored, and invalid/missing rates fail closed.
* Offline PHP/JS smoke tests and syntax checks passed. No live WordPress/WooCommerce or gateway test was available.

= 1.8.8 =
* Consolidated Telegram connection, Mini App, alerts, proxy, native payments, and Telegram-only messaging features into one Telegram settings tab, using labeled groups and preserving existing option names.
* Kept all Bale settings in the Bale tab and all Rubika settings in the Rubika tab; moved cross-platform log controls into a separate shared diagnostics tab.
* Preserved old Telegram subsection links as aliases to the consolidated Telegram tab; shared WooCommerce settings remain in their own sections.
* Offline smoke tests, source scans, PHP parsing, and package checks passed. No live WordPress/WooCommerce or messaging API test was run.

= 1.8.7 =
* Finalized the shared save-bar partial for the main settings form and the independent Bale/Rubika option forms; the channel-only save scope remains explicit and the brand footer is identical.
* Clarified token status accurately: a stored token alone is not proof of a live connection; the channel's last explicit API-test result is shown separately.
* Added static checks for save-form IDs, Settings API option group/nonces, and cross-channel preservation; 8 JavaScript smoke suites, source parsing for 80 PHP files, and archive integrity passed. No live WordPress/WooCommerce/API test was run.

= 1.8.6 =
* Unified the sticky save-bar markup for the main settings, Bale, and Rubika through one reusable panel partial; each channel still submits only its own Settings API form and clearly explains its save scope.
* Kept channel forms, option group, nonce, sanitizer, and secret-preservation behavior independent; added an offline contract test for cross-channel settings preservation.
* Corrected token status copy so a saved token is not presented as proof of a live connection; the channel test result remains separately available.
* JavaScript static smoke tests and PHP source parsing passed. No live WordPress Settings API, WooCommerce, or messaging API test was run.

= 1.8.5 =
* Added a capability matrix based on the official Telegram, Bale, Rubika, WordPress, and WooCommerce documentation, with explicit limits for unsupported or unverified platform behavior.
* Separated Telegram-only invoices, Stars, rich messages, post-purchase rating, compact navigation, and the Telegram coupon from shared marketing and WooCommerce settings; moved the shared command-menu toggle to describe only platforms with implemented registration.
* Added clear shared WooCommerce checkout and download-policy guidance for free/paid digital products and mixed-cart shipping, without adding a bypass switch.
* Added offline smoke coverage for the capability matrix, platform scope, and the existing downloadable-product policy; PHP source parsing and JavaScript smoke tests passed. No live WordPress/WooCommerce or messaging API test was run.

= 1.8.4 =
* Added separate immediate-publish buttons for Telegram, Bale, and Rubika on the WooCommerce product editor; each button sends only to that platform's independently configured destination.
* Added capability, product-status, and per-product nonce checks to the authenticated AJAX publishing endpoint; success/failure feedback is shown in the editor.
* Preserved the on-save per-platform selection and the existing Telegram bot-audience notification as a clearly separate action.
* Added an independent product-editor publishing panel with responsive local styling and offline smoke coverage.
* JavaScript smoke tests and PHP syntax parsing passed; no live WordPress/WooCommerce or messaging API runtime test was available.

= 1.8.3 =
* Reorganized settings into clearly marked Telegram-only, Bale-only, Rubika-only, and shared WooCommerce sections without changing saved option keys.
* Added a responsive three-platform control hub with per-channel setup status and direct links to each platform's settings.
* Clarified that Telegram alerts/Mini App/proxy settings are Telegram-specific, while Bale and Rubika retain their own independent settings, product-post destinations/titles, and order-notification switches.
* Kept digital-product checkout, mixed-cart shipping, and responsive RTL card-transfer behavior from 1.8.2.
* Offline JavaScript smoke tests and PHP syntax parsing passed; PHP CLI and live WordPress/WooCommerce/API runtime tests were unavailable in this environment.

= 1.8.2 =
* Added secure free and paid downloadable-product checkout for all three bot channels and the Mini App checkout routes.
* Added independent Telegram, Bale, and Rubika product-post destinations and title templates.
* Improved mobile/RTL card-transfer details.


= 1.8.1 =
* Fixed WooCommerce card-transfer review buttons: the form now renders outside the order editor form so approve/reject reaches the authenticated admin handler in classic and HPOS order screens.
* Added separate Bale and Rubika administrator chat IDs (Telegram continues using its existing Telegram admin chat setting). Receipt upload sends a signed approve/reject prompt to the buyer's own platform, with a protected link to the WooCommerce order/receipt.
* Bot-based review actions are HMAC-signed and restricted to that platform's configured admin identity. Approval calls WooCommerce payment_complete(), verifies the paid status, grants normal WooCommerce download permissions, and sends confirmation/download links to the buyer's originating platform; rejection keeps the order unpaid and prompts for a replacement receipt.
* Added safe diagnostics for receipt alerts, bot review, and WooCommerce payment completion without logging tokens, chat IDs, receipt contents, or request payloads.
* Offline/static review checks pass; live WordPress/WooCommerce and Telegram/Bale/Rubika APIs have not been tested in this environment.

= 1.8.0 =
* Downloadable WooCommerce products are excluded from bot and Mini App shipping requirements/rate packages even if Virtual is unchecked; mixed carts retain rates for physical items only.
* Telegram webhook registration explicitly subscribes to callback_query updates so Home/Cart inline callbacks are not lost through a previously restrictive allowed_updates filter.
* Rubika getMe now sends the documented no-parameter POST without an empty JSON array. On explicit invalid_input only, sendMessage safely retries without metadata and then with the official minimal text payload; no retry occurs after ambiguous transport/server failures.
* Added offline regression coverage for downloadable-only/mixed carts, Telegram callback subscription, Rubika API body and safe invalid_input fallbacks. Live WordPress/WooCommerce and messaging APIs were not available for runtime validation.

= 1.7.9 =
* اصلاح انتقال از Telegram Mini App به درگاه‌های وب ووکامرس با متد رسمی openLink تلگرام؛ درگاه Bale نیز فقط از متد مستند openLink خود Bale استفاده می‌کند و Rubika همچنان مسیر مستقل checkout وب را دارد.
* افزودن مهلت ۶۰ ثانیه‌ای برای درخواست ثبت سفارش و پیام بازیابی امن؛ اگر پاسخ دیر برسد، کاربر به سفارش‌هایش هدایت می‌شود و دربارهٔ احتمال ثبت سفارش و جلوگیری از تکرار هشدار می‌گیرد.
* افزودن ثبت مرحلهٔ checkout و خطاهای fatal بدون ذخیرهٔ شناسهٔ کاربر یا اطلاعات فرم، و تشخیص شکست واقعی پردازش پیام در ربات‌های بله/روبیکا.
* افزودن لاگ امن نتیجهٔ APIهای بله/روبیکا بدون توکن یا شناسهٔ گفتگو و آزمون آفلاین شکل وب‌هوک‌های رسمی Rubika و تحویل پیوند درگاه Mini App.
* اجرای lint و آزمون‌های آفلاین؛ آزمون runtime روی WordPress/WooCommerce واقعی و API زنده در این محیط انجام نشده است.

= 1.7.8 =
* رفع خطای ثبت سفارش در وب‌هوک بله هنگام درخواست نرخ ارسال: سبد ووکامرس در درخواست‌های REST به‌صورت امن و در صورت نیاز بارگذاری می‌شود؛ خطای شیء cart تهی دیگر به مرحلهٔ واردکردن کد پستی سرایت نمی‌کند.
* آماده‌سازی محافظت‌شدهٔ سرویس‌های مشتری، کشورها و ارسال ووکامرس؛ در صورت ناممکن‌بودن مقداردهی، خطا ثبت و مسیر بدون خطای fatal متوقف می‌شود.
* افزودن آزمون آفلاین بازگشت برای بارگذاری cart در وب‌هوک؛ runtime واقعی ووکامرس/API زنده در این محیط آزمایش نشده است.

= 1.7.7 =
* بازطراحی یکپارچهٔ تایپوگرافی، فاصله‌گذاری، کارت‌ها، فرم‌ها، جدول‌ها و واکنش‌گرایی در پنل مدیریت افزونه.
* همسان‌سازی نوار ذخیرهٔ بله و روبیکا با نوار تمام‌عرض ذخیرهٔ تنظیمات، با نمایش مستقل بر پایهٔ تب فعال.
* بهبود خوانایی داشبورد، گزارش‌ها، مخاطبان و ابزار ارسال همگانی.
* آزمون‌های آفلاین و lint اجرا شدند؛ این بسته به‌تنهایی آزمون runtime روی سایت واقعی یا API زنده محسوب نمی‌شود.

= 1.7.6 =
* Fixed the non-responsive Add Account button: enqueue the editor directly from the plugin admin bootstrap, independent of the WooCommerce gateway screen lifecycle.
* Reworked the editor initialization to use broadly supported DOM APIs, attach after document readiness, and retain the editable fallback if initialization fails.
* Added an executable JavaScript DOM smoke test for adding, editing, validating, saving and removing accounts.

= 1.7.5 =
* Move card-transfer enablement, destination accounts, customer instructions, receipt extensions and upload limits into the plugin’s own Settings panel. The WooCommerce gateway now links administrators back to that panel.
* Save into the existing WooCommerce gateway option to preserve previously configured accounts and order snapshots; register a dedicated sanitizer and maintain the legacy account-row format.
* Load the local account editor on the plugin settings page, including no-JavaScript editing fallback and panel-scoped validation; normalize Persian/Arabic digits before validating bank numbers.

= 1.7.4 =
* Fixed a fatal PHP signature incompatibility with current WooCommerce versions by matching the optional posted-data parameter in the payment gateway settings override.
* Added a WooCommerce-compatible parent-signature contract to the card-transfer smoke test to prevent regressions.

= 1.7.3 =
* Made the Telegram/Bale/Rubika channel save action sticky and consistent with the main Settings footer.
* Replaced the card-transfer account textarea with a structured, repeatable account editor for account label, bank, account holder, card number, account number, IBAN, and instructions. Existing six-column account rows continue to load.
* Added large, responsive bank-card details with a separate copy action for the account holder, card number, account number, and IBAN in website checkout/order views and the Telegram/Bale Mini App.
* Confirmed plugin icons are local; added no icon CDN dependencies.

= 1.7.2 =
* Fixed WooCommerce order creation: initialize and validate line-item counts, handle missing/unavailable products and return safe, actionable customer messages while retaining the cart.
* Localized order-creation failures and payment/receipt messages for Persian Mini App users, and applied the selected Mini App language to authenticated AJAX requests.
* Rebuilt the Persian gettext template/catalog from the current PHP sources, added legacy bot prompt strings, and compiled a fresh MO catalog.
* Removed release archives older than 1.7.0; kept the 1.7.0 and later archives unchanged.

= 1.7.1 =
* Resolve Mini App WooCommerce gateways by canonical ID as well as normalized ID; this fixes false “gateway no longer available” errors when an enabled gateway ID differs from the sanitized key.
* Check enabled status consistently from the gateway object/settings, preserve all enabled checkout methods, and report safe gateway-resolution diagnostics without exposing credentials.
* Add offline coverage for normalized IDs, boolean/string enabled values, and disabled gateways. No live WordPress/WooCommerce checkout or provider run is claimed.

= 1.7.0 =
* In Mini App checkout, use the configured native Bale/Telegram payment when available; otherwise show every enabled WooCommerce gateway and open the selected order-pay page in the same Mini App view.
* Add WooCommerce card-transfer gateway for normal checkout and Mini Apps, with multiple destination accounts, per-order account selection, configurable image/PDF receipt formats and a default 2 MB limit.
* Encrypt receipts in private order metadata (never public Media Library); validate upload size, extension and file signature/MIME. Orders stay on hold until an authorized manager reviews an uploaded receipt and approves payment.
* Add private admin receipt viewing and approve/reject controls; releasing payment through WooCommerce payment completion is the only route to fulfillment/download permissions.
* Add offline configuration/fallback smoke coverage. PHP/JS and package checks are offline; live WordPress, WooCommerce, wallet, gateway and provider runtime behavior is not claimed.

= 1.6.9 =
* Persist each registered-route HMAC verifier in a dedicated WordPress option separate from editable channel settings; verify the DB write before reporting success.
* Authentication reads that dedicated state (with compatibility fallback to 1.6.8 data), and registration logs explicitly report whether the verifier was saved. No raw route secret is duplicated.
* Add offline regression coverage for separate-option persistence, registered-route fallback, and rejection of unregistered paths. No live provider delivery is claimed.

= 1.6.8 =
* Fix the final authentication mismatch: after successful provider registration, retain a keyed full-length verifier for the exact registered route. Incoming webhooks are accepted only if they match either the current configured route secret or the last successfully registered route.
* Bale's registered route verifier is updated only after official getWebhookInfo confirms the URL/route. Rubika's verifier is updated only after both documented ReceiveUpdate and ReceiveInlineMessage endpoint updates are accepted.
* Keep the raw registered route secret out of the duplicate verifier; clear the verifier when the bot token is explicitly removed. Offline regression coverage added; no live API delivery is claimed.

= 1.6.7 =
* After Bale setWebhook, verify the active URL using the officially documented getWebhookInfo method; record only safe match flags and keyed route fingerprints, never the URL or secret.
* Log the accepted result and configured fingerprint separately for each documented Rubika ReceiveUpdate/ReceiveInlineMessage endpoint. Rubika's public method list does not document an endpoint-inspection getter, so the plugin does not claim remote read-back verification there.
* Add safe route-fingerprint tests for pretty and query-based WordPress REST URLs. Offline tests only; no live provider call is claimed.

= 1.6.6 =
* Fix webhook secret rotation on settings saves: resubmitting an unchanged Bale/Rubika bot token no longer invalidates the already-registered webhook URL. A genuinely changed token still rotates the route secret and requires webhook registration again.
* Add regression coverage for stable webhook secrets on unchanged tokens and rotation after a token change.
* Offline contract smoke suites and PHP syntax checks passed; no live provider or WordPress/WooCommerce runtime is claimed.

= 1.6.5 =
* Read webhook credentials exclusively from the matched REST URL route parameter, preventing request-body/query values named `secret` from shadowing the registered path value.
* Enrich Bale/Rubika webhook authentication error logs with a non-sensitive reason, presence/length indicators, and keyed truncated fingerprints; never log raw credentials or webhook URLs.
* Add offline regression tests for credential mismatch diagnostics and route-parameter precedence. All 10 smoke suites and PHP syntax checks passed; no live WordPress/WooCommerce or provider webhook/API test is claimed.

= 1.6.4 =
* Split dashboard orders/revenue by source channel (Telegram, Bale, Rubika) using `_order_from`; include CPT and HPOS queries and present mixed currencies separately.
* Add independent Telegram enable/disable, explicit multi-platform broadcast selection, accurate queued/attempted wording, and per-platform audience links.
* Migrate Telegram, Bale, Rubika and Bale provider credentials to authenticated encryption at rest where OpenSSL/Sodium is available; blank secret fields keep current values.
* Offline verification: 9 contract smoke tests, PHP-WASM 8.5 syntax checks for 73 files, JavaScript syntax, gettext/MO and whitespace checks. Live WordPress/WooCommerce/provider delivery was not tested.

= 1.6.3 =
* Replaced WordPress Dashicons in plugin screens with a curated, bundled Lucide SVG subset; Mini App UI controls now use local vector masks and local Telegram/Bale/Rubika marks.
* Added unified Telegram, Bale, Rubika and plugin/system log filters with source counts and privacy-aware display of structured webhook diagnostics; legacy Telegram history remains visible.
* Refined Persian/English and 13-locale bot starter copy; only known untouched seed text and the untouched old divider signature migrate. The administrator-editable signature is appended to shared and direct channel replies and can be disabled by clearing it.
* Added static asset and syntax checks. No WordPress/WooCommerce runtime or live-provider test is claimed.

= 1.6.2 =
* Added privacy-safe, per-platform Bale/Rubika webhook ingress and dispatch diagnostics; shared update logs now identify their source channel.
* This diagnostic release does not claim live provider delivery or end-to-end testing.

= 1.6.1 =
* Expanded the gettext source catalog to 1,044 unique static strings and completed the Persian PO/MO catalog; preserved prior translations and contextual entries.
* Localized Mini App PHP/JavaScript labels, channel-panel feedback, command descriptions, bot chat replies, default greetings, and new settings placeholders.
* Migrated only untouched legacy English seed messages to Persian defaults; administrator-customized message text remains intact.
* Updated release metadata to 1.6.1. Static PHP parsing and JavaScript syntax checks passed; no live WordPress/WooCommerce/API runtime test is claimed.

= 1.6.0 =
* Added opt-in Telegram Rich Messages (Bot API 10.1+) with RTL metadata and conservative fallback only after explicit 400/404 API rejection.
* Recognize modern Telegram update envelopes and safely acknowledge/log update types without a commerce handler.
* Added Bale-native video/audio/document/animation/voice and media-group adapter mappings covered by offline contract tests.
* Reworked the Commands tab into common commands, shared optional aliases, and platform-specific menu setup; clarified Rubika payment and membership API limits.
* Added offline tests for Channel API (22), update idempotency (6), Telegram update envelope (6), Telegram Rich Message routing (8), and command consistency (4): 46 assertions total; added API audit notes for Telegram, Bale, and Rubika.

= 1.5.5 =
* Rename the first settings tab to Telegram and use the Telegram platform icon.
* Align the 11 common Telegram/store commands; sync Rubika's documented setCommands list when registering its webhook, while keeping Bale menu setup platform-specific.
* Preserve Rubika formatting metadata when editing messages and honor the global command-menu setting.
* Clarify that common store commands are shared where each platform API supports them; Telegram, Bale, and Rubika retain platform-specific payment, Mini App, membership, and command-menu behavior.


= 1.5.4 =
* Hardened Bale/Rubika API transport: provider allowlist, bounded TLS-verified requests, strict response-envelope validation, and sanitized transport errors.
* Routed channel storefront messages through the shared provider adapter for consistent button translation and response handling.
* Added webhook payload bounds, short duplicate suppression for event types without a stable provider ID, and privacy-safe delivery-failure logging.
* Persisted new webhook secrets before endpoint registration to prevent first-update authentication races.
* Replaced fatal duplicate-update termination and mutable post GUID usage with backward-compatible update-ID metadata and explicit duplicate acknowledgement.
* Added offline Channel API (14 assertions) and update-idempotency (6 assertions) smoke tests; static syntax/compatibility checks were run without claiming live provider delivery.

= 1.5.3 =
* Added a Bale storefront Mini App entry and responsive, theme-aware SDK integration with BackButton, QR scanning, contact-sharing prompt, and optional home-screen shortcut controls.
* Validate Bale initData server-side with the documented WebAppData HMAC scheme and keep Bale account IDs namespaced separately from Telegram IDs.
* Added native Bale Mini App checkout through createInvoiceLink/openInvoice; retain server-confirmed WooCommerce payment status and never redirect Mini App payments to website checkout.
* Preserve Telegram Mini App and normal WooCommerce behavior; align all release metadata with 1.5.3.
* Static JavaScript syntax and whitespace checks were run; PHP lint and runtime payment tests were not available in this build environment.

= 1.5.2 =
* Added responsive safe gutters around full-width admin panels so cards remain inset from the viewport edges.
* Replaced per-request asset file-stat cache keys with the release version, enabling long-lived browser caching until the next version bump.
* Added transient caching and WooCommerce-order invalidation for dashboard sales and top-product aggregates.
* Avoided repeating WPML dynamic-string registration work on every request when settings have not changed.
* Kept Bale/Rubika panel content lazy-loaded and independent from the main settings form.
* Bumped all current release metadata to 1.5.2.

= 1.5.1 =
* Fixed Bale/Rubika settings navigation so every settings section stays available after switching channels.
* Load channel settings on demand with a permission- and nonce-protected AJAX fragment instead of reloading the entire WordPress settings page.
* Keep independent channel forms outside the Telegram settings form and return to the selected channel after saving.
* Bumped the plugin release version to 1.5.1 across distribution metadata.

= 1.5.0 =
* Corrected the OrderFlowTrait.php parse error caused by a doubled namespace separator; bundled PHP files were checked with a PHP grammar parser.
* Replaced active legacy identifiers with Zarincode identifiers across routes, settings, actions, AJAX names, post types, taxonomy/meta keys, widget IDs and Mini App storage.
* Added one-time migration and compatibility bridges for earlier option names, metadata, posts, widgets, AJAX callers, hooks and settings integrations.
* Added Telegram provider invoice payments inside chat and a Telegram Mini App openInvoice flow; native Mini App mode does not redirect to the WooCommerce payment page.
* Chat checkout no longer presents website-gateway URLs when native payment is unavailable. Native Bale/Telegram configuration is required; Rubika native payment remains unavailable without a documented official flow.

= 1.3.0 =
* به‌روزرسانی نسخهٔ افزونه به 1.3.0 در سربرگ، ثابت اصلی، پنل، خروجی JSON، Composer، Stable tag و راهنما.
* افزودن فونت متغیر Exo 2 لاتین در کنار Vazirmatn؛ متن فارسی/عربی با Vazirmatn و نویسه‌های لاتین/انگلیسی با Exo 2 به‌صورت محلی و بر اساس Unicode fallback نمایش داده می‌شوند.
* اعمال فونت دوگانه در صفحه‌های مدیریت افزونه، ویرایش محصول/دسته، ابزارک Telegram، Mini App و راهنمای آفلاین؛ افزودن مجوز و انتساب Exo 2.
* گسترش راهنمای فارسی بر اساس صفحه‌ها و handlerهای واقعی افزونه؛ افزودن فرایند خرید گام‌به‌گام، صفحهٔ کانال‌ها، ابزارهای ووکامرس و توضیح محدودیت‌های پلتفرم/API.
* همگام‌سازی حداکثر تعداد محصولات هر صفحه در اعتبارسنجی سمت سرور با فرم (تا 50).
* اتصال کنترل‌های جست‌وجوی زنده، SKU، علاقه‌مندی و referral به رفتار بات؛ پایدارشدن گزینهٔ referral و توضیح دقیق محدودیت فیلتر بازهٔ قیمت.
* اصلاح توضیح یادآوری سبد برای اجرای Action Scheduler یا WP-Cron.
* پاک‌سازی قطعهٔ HTML/PHP تکراری و نامعتبر از انتهای stylesheet مربوط به Mini App؛ فایل اکنون فقط CSS دارد.

= 1.2.0 =
* افزایش نسخهٔ افزونه از 1.1.0 به 1.2.0 و همگام‌سازی شمارهٔ نسخه در سربرگ، پنل، خروجی پشتیبان، Composer و Stable tag.
* افزودن راهنمای کامل فارسی آفلاین به‌صورت HTML مستقل و زیرمنوی راهنمای افزونه در پیشخوان.
* افزودن فونت متغیر محلی Vazirmatn همراه با مجوز OFL و استفاده در پنل و Mini App.
* افزودن اردو به فهرست زبان‌های قابل انتخاب.
* بهبود دسترسی سریع به راهنما و اصلاح نسخه‌گذاری cache assetها.

= 1.1.0 =
* معرفی برند زرین‌کد و افزونه ZarinShopBot.
* افزودن آداپتور webhook/API برای Bale و Rubika v3 و هم‌راستاسازی جریان‌های مشترک هسته فروشگاه.
* افزودن سبدهای تفکیک‌شده، keypads بومی، لینک checkout ووکامرس و پرداخت در سایت.
* غیرفعال‌سازی وب‌هوک relay خارجی و اجبار به وب‌هوک مستقیم HTTPS.
* حفظ انتساب upstream و مجوز GPL.
```
