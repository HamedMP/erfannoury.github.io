---
layout: post
category: Computer Vision, OpenCV, Ceemple
title: OpenCV آسان در ویندوز با استفاده از Ceemple
---
به نام خدا
===========

## OpenCV

یکی از مهم‌ترین کتابخانه‌های پردازش تصویر و بینایی ماشین، کتابخانه‌ی [OpenCV](http://opencv.org) هست. این کتابخانه که با استفاده از C/C++ نوشته شده و بسیاری از الگوریتم‌های مورد نیاز برای پردازش تصویر، بینایی ماشین و یادگیری ماشین رو پیاده‌سازی کرده. این کتابخانه از بسیاری از سیستم‌های عامل و معماری‌های سخت‌افزاری پشتیبانی می‌کنه و تقریباً همه جا می‌تونید ازش استفاده بکنید. همچنین اگر با زبان C++ راحت نباشید، این کتابخانه رو میشه به راحتی از زبان‌های جاوا و پایتون هم صدا زد و استفاده کرد.

با توجه به اینکه این کتابخانه از نظر حجم کد و همچنین وابستگی‌های خارجی به کتابخانه‌های دیگه، یک کتابخانه‌ی بسیار بزرگ به حساب میاد، بنابراین آماده‌کردن اون برای استفاده کار نسبتاً سختیه. برای اینکه بتونید از این کتابخانه استفاده بکنید، لازمه که کد این کتابخانه، به همراه کتابخانه‌های خارجی دیگری که کد به اونها وابسته هست کامپایل بشن تا بعد بشه ازشون استفاده کرد. این کار، بخصوص بر روی ویندوز نسبتاً سخت و وقت‌گیر هست. در این پست قصد دارم راه‌حل آسانی رو برای حل این مشکل معرفی کنم. OpenCV سخت در ویندوز رو بعداً توضیح خواهم داد.


## Ceemple OpenCV for Visual Studio
### [دریافت این افزونه](http://www.ceemple.com/ceemple-opencv-visual-studio/)


![Ceemple OpenCV for Visual Studio](http://www.ceemple.com/wp-content/uploads/2015/01/Capture5-1024x555.png)

[Ceemple](http://ceemple.com) یک راه‌حل مناسب برای این مشکل ارائه داده. اونا یک extension برای ویژوال استودیو ارائه دادن که شامل OpenCV 3.0 کامپایل‌شده و آماده‌ی استفاده به همراه کتابخانه‌های جانبی مهمی مثل CUDA، OpenCL، OpenMP و IPP هست.
شاید اطلاع داشته باشید که خود OpenCV هم DLLهای از پیش‌ساخته‌شده‌ی کتابخانه رو برای ویندوز ارائه میده. ولی این فایل‌ها، با حداقل استفاده از کتابخانه‌های جانبی بخصوص CUDA و IPP ارائه میشن که این موضوع باعث میشه این کتابخانه از تمام امکانات سخت‌افزاری برای پردازش بهره نبره. ولی در نسخه‌ای که Ceemple ارائه میده، این کتابخانه‌های مهم جانبی وجود دارن و شما می‌تونید از سرعت بیشتر اجرای کد بر روی پردازنده‌ یا پردازنده‌ی گرافیکی خودتون استفاده کنید.

همچنین با نصب این افزونه، امکان ساخت پروژه‌های OpenCV به صورت مستقیم از درون ویژوال استودیو ایجاد میشه. به این ترتیب خیلی سریع و بدون نیاز به تنظیم دسترسی پروژه به فایل‌های header و dll و lib مربوط به OpenCV و کتابخانه‌های جانبی، می‌تونید شروع به کد زدن بکنید و به تولید برنامه بپردازید.

![New OpenCV project dialoge in VS](http://www.ceemple.com/wp-content/uploads/2015/01/Capture.png)

علاوه بر نکات مثبت گفته شده، با نصب این افزونه، افزونه‌ی [Image Watch](https://visualstudiogallery.msdn.microsoft.com/e682d542-7ef3-402c-b857-bbfba714f78d) هم بر روی ویژوال استودیو نصب میشه. این افزونه‌ی بسیار مفید به شما در هنگام debug کردن برنامه در ویژوال استودیو کمک می‌کنه. با استفاده از این افزونه، در هنگام debug کردن، می‌تونید تصاویری که در کدتون استفاده می‌کنید و بر روی حافظه هستن رو ببینید و به راحتی به جریان کدتون پی ببرید و مشکلات احتمالی رو به راحتی پیدا و رفع کنید. این افزونه بسیار افزونه‌ی مفیدیه و برای کارهای پردازش تصویر و بینایی ماشین بسیار توصیه میشه.
([توضیح بیشتر در مورد Image Watch](http://channel9.msdn.com/posts/Introducing-Image-Watch))

![Image Watch VS extension](http://www.ceemple.com/wp-content/uploads/2015/01/Capture7-1024x559.png)



__توجه__: _تصاویر برگرفته از سایت [ceemple](http://ceemple.com) هستند._

## به‌روزرسانی 1
با استفاده از biicode هم می‌تونید به سادگی از OpenCV استفاده کنید. در این
[لینک](http://docs.opencv.org/master/d3/d82/tutorial_biicode.html) در این مورد توضیح داده شده. 
