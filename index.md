---
title: تعليمات مستضافة عبر الإنترنت
permalink: index.html
layout: home
ms.openlocfilehash: b85af520a10e63a2f9a5696db03bfd946aff968f
ms.sourcegitcommit: 1ef64e3008a439d0d0bb3d93a27d3df68d3d64a9
ms.translationtype: HT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/17/2022
ms.locfileid: "140688686"
---
# <a name="azure-ai-fundamentals-exercises"></a>تمارين أساسيات Azure في الذكاء الاصطناعي

استخدم الروابط أدناه لإكمال التدريبات المعملية العملية لدورة Microsoft التدريبية [AI-900 *أساسيات الذكاء الاصطناعي في Microsoft Azure*](https://docs.microsoft.com/learn/certifications/courses/ai-900t00).

لإكمال هذه التمارين، ستحتاج إلى اشتراك Microsoft Azure. إذا لم يزودك مدربك بواحد، فيمكنك التسجيل للحصول على نسخة تجريبية مجانية على [https://azure.microsoft.com](https://azure.microsoft.com).

{% assign labs = site.pages | where_exp:"page", "page.url contains '/instructions'" %}
| التمارين |
| ------- | 
{% for activity in labs  %}| [{{activity.lab.title}}]({{ site.github.url }}{{ activity.url }}) |
{% endfor %}
