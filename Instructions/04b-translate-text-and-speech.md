---
lab:
  title: استكشاف الترجمة
---

# <a name="explore-translation"></a>استكشاف الترجمة

> **ملاحظة** لإكمال هذا النشاط المعملي، ستحتاج إلى [اشتراك Azure](https://azure.microsoft.com/free?azure-portal=true) الذي لديك فيه حق الوصول الإداري.

إن إحدى القوى الدافعة التي مكنت الحضارة الإنسانية من التطور هي القدرة على التواصل مع بعضها البعض. في معظم المساعي البشرية، التواصل ضروري.

يمكن أن يساعد الذكاء الاصطناعي (AI) في تبسيط التواصل من خلال ترجمة النص أو الكلام بين اللغات، مما يساعد على إزالة الحواجز أمام التواصل عبر البلدان والثقافات.

لاختبار قدرات خدمة “Translator”، سنستخدم تطبيق سطر أوامر بسيطاً يتم تشغيله في Cloud Shell. تنطبق نفس المبادئ والوظائف في حلول العالم الحقيقي، مثل مواقع الويب أو تطبيقات الهاتف.

## <a name="create-a-cognitive-services-resource"></a>إنشاء مورد *الخدمات المعرفية*

يمكنك استخدام خدمة "Translator" عن طريق إنشاء إما مورد **Translator** أو مورد **Cognitive Services**.

إذا لم تكن قد فعلت ذلك بالفعل، قم بإنشاء مورد **الخدمات المعرفية** في اشتراك Azure.

1. في علامة تبويب مستعرض أخرى، افتح مدخل Azure في [https://portal.azure.com](https://portal.azure.com?azure-portal=true)، وقم بتسجيل الدخول باستخدام حساب Microsoft الخاص بك.

1. حدد زر **&#65291;Create a resource**، ثم ابحث عن *Cognitive Services*، وقم بإنشاء مورد**Cognitive Services** بالإعدادات التالية:
    - **الاشتراك**: *اشتراك Azure الخاص بك*.
    - **مجموعة الموارد**: *أنشئ مجموعة موارد جديدة ذات اسم فريد*.
    - **Region**: *اختر أي منطقة متوفرة*.
    - **الاسم**: *أدخل اسمًا مميزًا*.
    - **مستوى التسعير**: قياسي S0
    - **By checking this box I acknowledge that I have read and understood all the terms below**: محدد.

1. راجع المورد وأنشئه، وانتظر حتى يكتمل التوزيع. ثم انتقل إلى المورد الموزع.

1. عرض صفحة **Keys and Endpoint** لمورد الخدمات المعرفية. ستحتاج إلى المفاتيح والموقع للاتصال من تطبيقات العميل.

### <a name="get-the-key-and-location-for-your-cognitive-services-resource"></a>الحصول على المفتاح والموقع لمورد «الخدمات المعرفية»

1. يُرجى الانتظار لاكتمال التوزيع. ثم انتقل إلى مورد “Cognitive Services”، وفي الصفحة **Overview** انقر فوق الرابط لإدارة مفاتيح الخدمة. ستحتاج نقطة النهاية والمفاتيح للاتصال بمورد “Cognitive Services” من تطبيقات العميل.

1. عرض صفحة **Keys and Endpoint** لموردك. ستحتاج **location/region** و **key**للاتصال من تطبيقات العميل.

> **ملاحظة** لاستخدام خدمة Translator لا تحتاج إلى استخدام نقطة النهاية Cognitive Service. يتم توفير نقطة نهاية عمومية فقط لخدمة المترجم. 

## <a name="run-cloud-shell"></a>تشغيل Cloud Shell

لاختبار قدرات خدمة «الترجمة»، سنستخدم تطبيق سطر أوامر بسيط يعمل في Cloud Shell على Azure. 

1. في مدخل Azure، حدد زر **[>_]** *(Cloud Shell)* أعلى الصفحة يمين مربع البحث. يؤدي ذلك إلى فتح جزء Cloud Shell في أسفل المدخل.

    ![بدء تشغيل Cloud Shell بالنقر على الرمز الموجود على يمين مربع البحث العلوي](media/translate-text-and-speech/powershell-portal-guide-1.png)

1. في المرة الأولى التي تفتح فيها Cloud Shell، قد يُطلب منك اختيار نوع shell التي تريد استخدامها (*Bash* أو *PowerShell).* حدد **PowerShell**. إذا لم ترى هذا الخيار، تخطي الخطوة.  

1. إذا تمت مطالبتك بإنشاء سعة تخزينية لشركة Cloud Shell، فتأكد من تحديد اشتراكك وحدد **Create storage**. ثم انتظر دقيقة أو نحو ذلك لإنشاء التخزين.

    ![أنشئ التخزين بالنقر فوق «confirm».](media/translate-text-and-speech/powershell-portal-guide-2.png)

1. تأكد من تبديل نوع shell المشار إليه في أعلى يسار جزء Cloud Shell إلى *PowerShell*. إذا كان *Bash*، فقم بالتبديل إلى *PowerShell* باستخدام القائمة المنسدلة. 

    ![كيفية العثور على القائمة المنسدلة ناحية اليسار للتبديل إلى PowerShell](media/translate-text-and-speech/powershell-portal-guide-3.png) 

1. انتظر حتى يبدأ PowerShell. يجب أن ترى الشاشة التالية في مدخل Azure:  

    ![انتظر حتى يبدأ PowerShell.](media/translate-text-and-speech/powershell-prompt.png)

## <a name="configure-and-run-a-client-application"></a>كوّن تطبيق عميل وقم بتشغيله

الآن بعد أن أصبح لديك طراز مخصص، يمكنك تشغيل تطبيق عميل بسيط يستخدم خدمة «الترجمة».

1. في shell الأمر، أدخل الأمر التالي لتحميل نموذج التطبيق وحفظه إلى مجلد يسمى «ai-900».

    ```PowerShell
    git clone https://github.com/MicrosoftLearning/AI-900-AIFundamentals ai-900
    ```

    >**تلميح** إذا كنت قد استخدمت هذا الأمر بالفعل في نشاط معملي آخر لاستنساخ مستودع *ai-900*، فيمكنك تخطي هذه الخطوة.

1. يتم تحميل الملفات إلى مجلد يسمى **ai-900** نريد الآن رؤية جميع الملفات في تخزين Cloud Shell الخاص بك والعمل معهم. اكتب الأمر التالي في shell: 

     ```PowerShell
    code .
    ```

    لاحظ كيف يفتح هذا محررًا مثل المحرر الموجود في الصورة أدناه: 

    ![محرر التعليمات البرمجية.](media/translate-text-and-speech/powershell-portal-guide-4.png)

1. في جزء **Files** على اليسار، قم بتوسيع **ai-900** وحدد **translator.ps1**. يحتوي هذا الملف على بعض التعليمات البرمجية التي تستخدم خدمة «المترجم»:

    ![المحرر الذي يحتوي على تعليمات برمجية لاستخدام خدمة «المترجم»](media/translate-text-and-speech/translate-code.png)

1. لا تشغل بالك كثيرًا بشأن تفاصيل التعليمات البرمجية، ما يهم هو أنه يحتاج إلى «المنطقة/الموقع» وأي من مفاتيح مورد «الخدمات المعرفية» الخاص بك. انسخ هذه من صفحة **Keys and Endpoints** لموردك من مدخل Azure وألصقها في محرر التعليمات البرمجية، مستبدلاً قيم العنصر النائب **YOUR_KEY** و**YOUR_LOCATION** على التوالي.

    بعد لصق قيم المفتاح ونقطة الموقع، يجب أن تكون السطور الأولى من التعليمات البرمجية مشابهين لهذا:

    ```PowerShell
    $key="1a2b3c4d5e6f7g8h9i0j...."
    $location="somelocation"
    ```

1. في أعلى يمين جزء المحرر، استخدم الزر **...** لفتح القائمة ثم حدد **Save** لحفظ التغييرات. ثم افتح القائمة مرة أخرى وحدد **Close Editor**.

    سيتم استخدام تطبيق العميل النموذج لخدمة «المترجم» للقيام بمهام متعددة:
    - ترجمة النص من الإنجليزية إلى الفرنسية والإيطالية والصينية.
    - ترجمة الصوت من الإنجليزية إلى نص باللغة الفرنسية

    استخدم مشغل الفيديو أدناه لسماع صوت الإدخال الذي سيقوم التطبيق بمعالجته:

    <div class="embeddedvideo"><iframe src="https://www.microsoft.com/videoplayer/embed/RWORN0" frameborder="0" allowfullscreen="true" data-linktype="external"></iframe></div>


    > **ملاحظة** يمكن للتطبيق الحقيقي قبول الإدخال من ميكروفون وإرسال الاستجابة إلى مكبر الصوت، ولكن في هذا المثال البسيط، سنستخدم الإدخال المسجل مسبقًا في ملف صوتي.

1. في جزء Cloud Shell، أدخل الأمر التالي لتشغيل التعليمات البرمجية:

    ```PowerShell
    cd ai-900
    ./translator.ps1
    ```

1. راجع الإخراج. هل رأيت الترجمة من النص باللغة الإنجليزية إلى الفرنسية والإيطالية والصينية؟  هل رأيت الصوت الإنجليزي "hello" مترجماً إلى نص باللغة الفرنسية?

## <a name="learn-more"></a>معرفة المزيد

يظهر هذا التطبيق البسيط فقط بعض من قدرات خدمة «المترجم». لمعرفة المزيد حول ما يمكنك القيام به مع هذه الخدمة، راجع [صفحة Translator](https://docs.microsoft.com/azure/cognitive-services/translator/translator-overview).