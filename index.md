---
title: تعليمات مستضافة عبر الإنترنت
permalink: index.html
layout: home
ms.openlocfilehash: 86fa2da9bfa9e4d7edb0c853f77e95fe69e97411
ms.sourcegitcommit: 3fc8440b350b498c2f50ab4ce531a0f906792584
ms.translationtype: HT
ms.contentlocale: ar-SA
ms.lasthandoff: 09/08/2022
ms.locfileid: "147866000"
---
# <a name="azure-ai-fundamentals-exercises"></a>تمارين أساسيات Azure في الذكاء الاصطناعي

تم تصميم هذه التدريبات العملية لدعم محتوى التدريب على [Microsoft Learn](https://docs.microsoft.com/training/).

لإكمال هذه التمارين، ستحتاج إلى اشتراك Microsoft Azure. يمكنك التسجيل للحصول على نسخة تجريبية مجانية في [https://azure.microsoft.com](https://azure.microsoft.com).

{% assign labs = site.pages | where_exp:"page", "page.url contains '/instructions'" %}
| التمارين |
| ------- | 
{% for activity in labs  %}| [{{activity.lab.title}}]({{ site.github.url }}{{ activity.url }}) |
{% endfor %}
