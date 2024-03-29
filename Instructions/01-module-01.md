---
lab:
  title: استكشاف خدمات الذكاء الاصطناعي في Azure
---

> **هام**
> **لقد تم إهمال مختبر كاشف الشذوذات واستبداله بالتحديث أدناه.**

تساعد خدمات الذكاء الاصطناعي في Azure المستخدمين على إنشاء تطبيقات الذكاء الاصطناعي باستخدام واجهات برمجة التطبيقات المبتكرة والنماذج الجاهزة والمبنية مسبقًا والقابلة للتخصيص. في هذا التمرين، ستلقي نظرة على إحدى الخدمات، سلامة المحتوى بالذكاء الاصطناعي في Azure وكذلك استوديو سلامة المحتوى. 

يمكنك استوديو سلامة المحتوى من استكشاف كيفية إدارة محتوى النص والصورة. يمكنك تشغيل اختبارات على نموذج النص أو الصور والحصول على درجة خطورة تتراوح من آمنة إلى عالية الخطورة لكل فئة. في هذا التمرين المعملي، ستقوم بإنشاء مورد خدمة واحدة في استوديو سلامة المحتوى واختبار وظائفه. 

> **ملاحظه** الهدف من هذا التمرين هو تكوين فكرة عامة عن كيفية توفير خدمات Azure للذكاء الاصطناعي واستخدامها. يتم استخدام المحتوى السلامة كمثال، ولكن لا يتوقع منك اكتساب معرفة شاملة بسلامة المحتوى في هذا التمرين!

## التنقل في استوديو سلامة المحتوى 

![لقطة شاشة للصفحة المنتقل إليها في استوديو سلامة المحتوى.](./media/content-safety/content-safety-getting-started.png)


1. افتح [استوديو سلامة المحتوى](https://contentsafety.cognitive.azure.com?azure-portal=true). إذا لم تقم بتسجيل الدخول، فستحتاج إلى تسجيل الدخول. حدد **تسجيل الدخول** في الركن الأيمن العلوي من الشاشة. استخدم البريد الإلكتروني وكلمة المرور المرتبطين باشتراك Azure لتسجيل الدخول. 

1. تم إعداد استوديو سلامة المحتوى مثل العديد من الاستوديوهات الأخرى لخدمات الذكاء الاصطناعي في Azure. في القائمة في أعلى الشاشة، انقر فوق الأيقونة الموجودة على يسار *الذكاء الاصطناعي في Azure*. سترى قائمة منسدلة من الاستوديوهات الأخرى المصممة للتطوير باستخدام خدمات الذكاء الاصطناعي في Azure. يمكنك النقر فوق الأيقونة مرة أخرى لإخفاء القائمة.

![لقطة شاشة لقائمة استوديو سلامة المحتوى مع تحديد تبديل مفتوح للتبديل إلى استوديوهات أخرى.](./media/content-safety/studio-toggle-icon.png)  

## ربط مورد بالاستوديو 

قبل استخدام الاستوديو، تحتاج إلى ربط مورد خدمات الذكاء الاصطناعي في Azure بالاستوديو. اعتمادًا على الاستوديو، قد تجد أنك بحاجة إلى مورد خدمة واحدة محدد، أو يمكنك استخدام مورد عام متعدد الخدمات. في حالة استوديو سلامة المحتوى، يمكنك استخدام الخدمة عن طريق إنشاء مورد *سلامة محتوى* لخدمة واحدة أو مورد خدمات *الذكاء الاصطناعي في Azure* عام متعدد الخدمات. في الخطوات أدناه، سنقوم بإنشاء مورد سلامة محتوى لخدمة واحدة. 

1. انقر على أيقونة **الإعدادات** أعلى يمين الشاشة. 

![لقطة شاشة لأيقومة الإعدادات في الجزء العلوي الأيمن من الشاشة، بجوار أيقونات الجرس وعلامة الاستفهام والابتسامة.](./media/content-safety/settings-toggle.png)

1. في صفحة **لإعدادات**، سترى علامة تبويب *الدليل* وعلامة تبويب *المورد*. في علامة التبويب *المورد*، حدد **إنشاء مورد جديد**. ينقلك هذا إلى صفحة لإنشاء مورد في مدخل Microsoft Azure.

> **ملاحظة** تسمح علامة التبويب *الدليل* للمستخدمين بتحديد دلائل مختلفة لإنشاء الموارد منها. لا تحتاج إلى تغيير إعداداته إلا إذا كنت ترغب في استخدام دليل مختلف. 

![لقطة شاشة لمكان تحديد إنشاء مورد جديد من صفحة إعدادات استوديو سلامة المحتوى.](./media/content-safety/create-new-resource-from-studio.png)

1. في صفحة إنشاء *استوديو سلامة المحتوى* في [مدخل Microsoft Azure](https://portal.azure.com?auzre-portal=true)، تحتاج إلى تكوين العديد من التفاصيل لإنشاء موردك. قم بتكوينه بالإعدادات التالية:
    - **الاشتراك**: *اشتراك Azure الخاص بك*.
    - **مجموعة الموارد**: *أنشئ مجموعة موارد جديدة ذات اسم فريد*.
    - **Region**: *اختر أي منطقة متوفرة*.
    - **الاسم**: *أدخل اسمًا مميزًا*.
    - **مستوى التسعير**: مجاني (F0)

1. حدد **مراجعة + إنشاء** وراجع التكوين. ثم حدد **إنشاء**. ستشير الشاشة إلى وقت اكتمال النشر. 

*تهانينا! لقد قمت للتو بإنشاء مورد خدمات الذكاء الاصطناعي في Azure أو توفيره. المورد الذي قمت بتوفيره على وجه الخصوص هو مورد خدمة سلامة محتوى ذو خدمة واحدة.*

1. عند اكتمال النشر، افتح علامة تبويب جديدة وارجع إلى [استوديو سلامة المحتوى](https://contentsafety.cognitive.azure.com?azure-portal=true). 

1. حدد أيقونة **الإعدادات** في الجزء العلوي الأيمن من الشاشة مرة أخرى. هذه المرة يجب أن ترى أنه تمت إضافة المورد الذي تم إنشاؤه حديثًا إلى القائمة.  

1. في صفحة إعدادات استوديو سلامة المحتوى، حدد مورد خدمة الذكاء الاصطناعي في Azure الذي أنشأته للتو وانقر فوق **استخدم المورد** في أسفل الشاشة. سيتم نقلك مرة أخرى إلى الصفحة الرئيسية للاستوديو. الآن يمكنك البدء في استخدام الاستوديو مع المورد الذي تم إنشاؤه حديثًا.

## جرب الإشراف على النص في استوديو سلامة المحتوى

1. في الصفحة الرئيسية لاستوديو سلامة المحتوى، ضمن *تشغيل اختبارات الإشراف*، انتقل إلى **مربع الإشراف على المحتوى** وانقر على **جربه الآن**.
1. ضمن تشغيل اختبار بسيط، انقر فوق **سلامة المحتوى**. لاحظ أنه يتم عرض النص في المربع أدناه. 
1. انقر فوق **تشغيل الاختبار**. يؤدي تشغيل اختبار إلى استدعاء نموذج التعلم العميق لاستوديو سلامة المحتوى. تم بالفعل تدريب نموذج التعلم العميق على التعرف على المحتوى غير الآمن.
1. في لوحة *النتائج*، افحص النتائج. هناك أربعة مستويات خطورة من آمنة إلى عالية، وأربعة أنواع من المحتوى الضار. هل تعتبر خدمة سلامة المحتوى بالذكاء الاصطناعي أن هذه العينة مقبولة أم لا؟ ما يجب ملاحظته هو أن النتائج تقع ضمن نطاق الثقة. يمكن للنموذج المُدرب جيدًا، مثل أحد نماذج الذكاء الاصطناعي الجاهزة في Azure، إرجاع النتائج التي لديها احتمال كبير لمطابقة ما قد يصنفه الإنسان على النتيجة. في كل مرة تقوم فيها بتشغيل اختبار، يمكنك استدعاء النموذج مرة أخرى. 
1. الآن جرّب عينة أخرى. حدد النص ضمن المحتوى العنيف الذي به خطأ إملائي. تحقق من عرض المحتوى في المربع أدناه.
1. انقر فوق **تشغيل الاختبار** وافحص النتائج في لوحة النتائج مرة أخرى. 

يمكنك تشغيل الاختبارات على جميع العينات المقدمة، ثم فحص النتائج.

## تحقق من المفاتيح ونقطة النهاية

يمكن برمجة هذه القدرات التي اختبرتها في جميع أنواع التطبيقات. يمكن العثور على المفاتيح ونقطة النهاية المستخدمة لتطوير التطبيق في كل من استوديو سلامة المحتوى ومدخل Microsoft Azure. 

1. في استوديو سلامة المحتوى، انتقل مرة أخرى إلى صفحة **الإعدادات**، مع تحديد علامة التبويب *المواراد*. البحث عن المورد الذي استخدمته. مرر حتى ترى نقطة النهاية والمفتاح لموردك. 
1. في مدخل Microsoft Azure، سترى أن هذه هي *نفس* نقطة النهاية والمفاتيح *المختلفة* لموردك. للتحقق من ذلك، انتقل إلى [مدخل Microsoft Azure](https://portal.azure.com?auzre-portal=true). ابحث عن *سلامة المحتوى* في شريط البحث العلوي. ابحث عن موردك وانقر فوقه. في القائمة اليسرى، ابحث ضمن *إدارة الموارد* للـ *مفاتيح ونقاط النهاية*. حدد **المفتيح ونقطة النهاية** لعرض نقطة النهاية والمفاتيح لموردك. 

بعد الانتهاء، يمكنك حذف مورد سلامة المحتوى من مدخل Microsoft Azure. حذف المورد هو طريقة لتقليل التكاليف التي تتراكم عند وجود المورد في الاشتراك. للقيام بذلك، انتقل إلى صفحة **نظرة عامة** لموردك لسلامة المحتوى. حدد **حذف** في الجزء العلوي من الشاشة. 
