---
title: تعليمات مستضافة عبر الإنترنت
permalink: index.html
layout: home
---

# <a name="azure-ai-fundamentals-exercises"></a>تمارين أساسيات Azure في الذكاء الاصطناعي

تم تصميم هذه التدريبات العملية لدعم محتوى التدريب على [Microsoft Learn](https://docs.microsoft.com/training/).

لإكمال هذه التمارين، ستحتاج إلى اشتراك Microsoft Azure. يمكنك التسجيل للحصول على نسخة تجريبية مجانية في [https://azure.microsoft.com](https://azure.microsoft.com).


## <a name="labs"></a>Labs

{% assign labs = site.pages | where_exp:"page", "page.url contains '/instructions'" %}
| Title | Module |
| --- | --- | 
{% for activity in labs %}| {{ activity.lab.module }} | [{{ activity.lab.title }}{% if activity.lab.type %} - {{ activity.lab.type }}{% endif %}]({{ site.github.url }}{{ activity.url }}) |
{% endfor %}
