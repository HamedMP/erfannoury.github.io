---
layout: post
category: Machine Learning, AI, Deep Learning, Python
title: نصب کتابخانه‌ی Theano در ویندوز (به‌روزرسانی)
---
به نام خدا
===========

بعد از پست قبلی در مورد نصب Theano بر روی ویندوز، تغییرات زیادی در این زمینه و کتابخانه‌های یادگیری عمیق و وضعیت نصب اونها روی ویندوز ایجاد شده. این پست به نوعی به‌روزرسانی بر روی موضوع نصب این کتابخانه‌ی پایه‌ای و بعد معرفی یک کتابخانه‌ی جدیده.

## نکات جدید برای نصب Theano
چند روز پیش می‌خواستم این کتابخانه رو روی یک کامپیوتر جدید نصب کنم.
اولین کاری که کردم دانلود کردن و نصب Anaconda Python، CUDA 7.0 و البته Visual Studio 2013 بود. بخاطر اینکه هنوز CUDA از Visual Studio 2015 پشتیبانی نمی‌کنه، سراغ نسخه‌ی جدیدش نرفتم.
بعد از اینکه اینا رو نصب کردم (اول ویژوال استودیو، بعد پایتون، در نهایت کودا) رفتم سراغ نصب gcc. درسته که برای کامپایل‌کردن قسمت اصلی کد Theano از کامپایلر مایکروسافت استفاده میشه، ولی بعضی از تیکه‌های کد نیاز به gcc دارن.
برای اینکار [TDM GCC](http://tdm-gcc.tdragon.net/) رو دانلود و نصب کردم. این نسخه از بقیه زودتر آپدیت میشه و چیز اضافی‌ای هم نصب نمی‌کنه.
بعد از اینکه همه‌ی اینها رو نصب کردم و مطمئن شدم که همه‌ی چیزهای لازم در مسیر سیستم قرار گرفتن رفتم سراغ نصب Theano.

اولین مشکلی که خوردم این بود که وقتی از gcc می‌خواست استفاده کنه خطای عدم وجود فایل‌های لازم برای پایتون رو میداد. رفتم خوب مسیر پایتون (پوشه‌ی libs) رو بررسی کردم. دیدم که همه چیز درسته.
بعد از کمی جستجو، فهمیدم که gcc نیاز به فایل‌های کتابخانه‌ای با فرمت `libpython27.a` داره، نه `python27.lib`. بنابراین باید اول این فایل رو پیدا (یا درست) می‌کردم و بعد در همون پوشه قرار میدادم. بعد از اینکار یکی از مشکلات کامپایل حل شد. 
برای حل مشکل به [این لینک](https://github.com/Theano/Theano/issues/2867) یه نگاهی بندازید.

مشکل دیگه یه مشکل خیلی عجیب بود. اینکه `C:\Windows\System32` تو مسیرهای سیستمی نبود. خیلی عجیب بود این موضوع برام و باعث ایجاد کلی مشکل و گرفتن کلی وقت شد. ولی بعد از اضافه کردن مسیر، کتابخانه به صورت کامل کامپایل شد.

بعد از این، نوبت درست کردن فایل تنظیمات کتابخانه، یعنی ` .theanorc` بود. این رو هم در مسیر کاربری قرار دادم و بعدش رفتم سراغ اجرای کتابخانه که بدون مشکل اجرا شد. اینجا به عنوان مرجع، محتوای فایل تنظیمات Theano رو میذارم.


	[blas]
	ldflags = 
	[nvcc]
	flags=-LC:\Anaconda\libs
	compiler_bindir=C:\Program Files (x86)\Microsoft Visual Studio 12.0\VC\bin
	optimizer_including=dnn
	fastmath = True
	[global]
	device = gpu
	floatX = float32
	[cuda]
	root=C:\Program Files\NVIDIA GPU Computing Toolkit\CUDA\v7.0


البته اگر خوب ببینید قسمت blas خالیه. برای اون قسمت هم کتابخانه‌ی OpenBLAS رو دانلود کردم و مسیر اون کتابخانه و همچنین اسم فایل کتابخانه‌ی OpenBLAS رو به عنوان ورودی دادم. 

بعد از این مراحل فکر نمی‌کنم مشکلی در نصب Theano پیش بیاد.

اون **dnn** هم که نوشتم همون cuDNN هست که انویدیا عرضه کرده تا محاسبات مرتبط با یادگیری عمیق سریعتر بشه. نصب اون هم راحته. بعد از اینکه فایل‌هاش رو دانلود کردید، تو پوشه‌های مرتبط توی محل نصب CUDA قرارشون بدید و اینجا هم اون خط رو به فایل تنظیمات اضافه کنید. cuDNN 2 روی ویندوز بدون مشکل کار می‌کنه، ولی cuDNN 3 رو هنوز امتحان نکردم.

## کتابخانه‌ی [Keras](https://github.com/fchollet/keras) 
کتابخانه‌ی یادگیری عمیق Keras یکی از اون کتابخانه‌های یادگیری عمیقه که به نظر میاد آینده‌ی بسیار درخشانی داشته باشه. این کتابخانه روی Theano ساخته شده، ولی API اون از Torch7 الهام گرفته شده و خیلی خوش‌دسته. برخلاف پیچیدگی‌های بالای کار با Theano، کد مربوط به این کتابخانه خیلی خوانا است و به راحتی می‌تونید توش به طراحی مدل و آموزش و تحلیل مدل بپردازید. واقعاً بین همه‌ی کتابخانه‌های یادگیری عمیقی که بررسی کردم (برای پایتون البته)، این بهترین گزینه برای شروع کاره. آموزش‌ها و راهنمایی‌های بسیار خوبی هم تو [این آدرس](http://keras.io/) گذاشتن. حتماً اگر تصمیم دارید کار روی یادگیری عمیق رو بدون مشکلات زیاد شروع کنید نگاهی به این کتابخانه بندازید.

در کل بخاطر اینکه افراد و شرکت‌های زیادی پشت کتابخانه‌های Caffe و Torch7 بودن بقیه‌ی کتابخانه‌ها تقریباً عقب مونده بودن. ولی اخیراً احساس می‌کنم که کتابخانه‌های مبتنی بر Theano دارن جایگاه خودشون رو قوی‌تر می‌کنن. خیلی از مقالات اخیر با این کتابخانه‌های پیاده‌سازی شدن و همچنین پیاده‌سازی مقالات زیادی توسط افراد ثالث برای این کتابخانه‌ها انجام می‌گیره. 

هر چقدر گزینه‌ها برای کار کردن زیاد باشن، بهتره. امیدوارم که روز به روز کتابخانه‌ها پیشرفته‌تر و البته ورود به اون‌ها ساده‌تر بشه.

فکر می‌کنم در روزهای آتی پست‌های متعددی داشته باشم.