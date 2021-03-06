---
layout: post
category: پایتون, python, tips
title: کامپایلر مایکروسافت برای پایتون
---
#به نام خدا

##مقدمه
اخیراً شروع به کار با زبان پایتون کردم. خیلی سبک زبان رو نپسندیدم، بخصوص با dynamic بودن هنوز کامل کنار نیامده‌ام.
ولی زبان پایتون جامعه‌ی بسیار بزرگی دارد و نتیجه‌ی این جامعه‌ی بزرگ پروژه‌های باکیفیت و پرتعداد و پرکاربردی است که برای این زبان و با این زبان ایجاد شده‌اند. همین کتابخانه‌ها برنامه‌نویسی را برای انجام بسیاری از کارها آسان می‌کند. 

برای نصب کتابخانه‌های مختلف برای این زبان، راه‌های مختلفی وجود دارد. مشهورترین این راه‌ها `pip` و `easy_install` است. همچنین با استفاده از `conda` نیز می‌توان این کار را برای بعضی از کتابخانه‌ها انجام داد.

ولی راه اصلی نصب بسیاری از کتابخانه‌ها، استفاده از دستور زیر است:
	
	>> python setup.py install

فایل `setup.py` در همه‌ی پروژه‌ها وجود دارد، و در واقع این فایل توسط توسعه‌دهندگان هر کدام از این کتابخانه‌ها نوشته می‌شود. با استفاده از این دستور می‌توان کتابخانه‌ی مورد نظر را به لیست پایتون اضافه کرد. 

پایتون به زبان `C` نوشته شده است و برای سرعت‌گرفتن، قسمت‌هایی از کد را می‌توان به زبان `C` نوشت و در کد پایتون استفاده کرد. همچنین پروژه‌ای همانند `Cython`  می‌تواند کد پایتون را به کد `C` تبدیل کند.

##مشکل

در هنگام نصب بعضی از پروژه‌ها، لازم است قسمتی از کد توسط یک کامپایلر `C` کامپایل شود.  برای این کار باید پایتون بتواند کامپایلر درست نصب شده و تنظیمات مناسب را تشخیص دهد. اگر این مشکلی در این کار پیش بیاید، خطایی مانند زیر در هنگام نصب کتابخانه نمایش داده خواهد شد:

	Error:unable to find vcvarsall.bat
	
این خطا بخصوص در ویندوز احتمال ظهور بیشتری دارد! برای اینکار راه‌حلی پیشنهاد می‌شود که در ادامه توضیح آن را خواهم داد.

##راه‌حل

در مسیر زیر فایلی به نام `distutils.cfg` وجود دارد

	%PYTHONDIR%\Lib\distutils\

اگر هم این فایل موجود نباشد، آن را ایجاد کنید. محتویات آن را به صورت زیر تغییر دهید:

	[build]
	compiler=msvc
	
`%PYTHONDIR%` مسیر نصب پایتون می‌باشد. مسیر پیش‌فرض مسیر زیر می‌باشد:

	C:\Python27


تنظیمات بالا با فرض این است که کامپایلر مایکروسافت بر روی سیستم نصب باشد. اگر ویژوال استودیو داشته باشید کامپایلر نصب می‌باشد. اگر کامپایلر ویژوال استودیو ندارید می‌توانید نسخه‌ی [Express](http://www.visualstudio.com/en-us/downloads/download-visual-studio-vs.aspx) ویژوال استودیو را دریافت و نصب کنید.

حال به مسیر زیر بروید:

	%PYTHONDIR%\PCbuild\
	
در این پوشه فایل زیر را ایجاد کنید

	msvcr<num>.def

که منظور از `<num>` یک شماره است که بر اساس نسخه‌ی ویژوال استودیو تعیین می‌شود


- `Visual Studio 2008	->		90`
- `Visual Studio 2010	->		100`
- `Visual Studio 2012	->		110`
- `Visual Studio 2013	->		120`

حال در فایل ایجاد شده دو خط زیر را بنویسید:

	LIBRARY MSVCR<num>.dll
	EXPORTS
	
با انجام این کارها به احتمال زیادی مشکل کامپایل‌شدن کدهای `C` برای پایتون حل خواهد شد.