---
ms.openlocfilehash: ad953a1562db407c04d7860c60eb5964fe6fe2ca
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620039"
---
### <a name="deserialization-of-mailmessage-objects-serialized-under-the-net-framework-45-may-fail"></a>La désérialisation des objets MailMessage sérialisés sous .NET Framework 4.5 peut échouer

#### <a name="details"></a>Détails

À compter de .NET Framework 4.5, les objets <xref:System.Web.Mail.MailMessage> peuvent inclure des caractères non-ASCII. Dans le .NET Framework 4, seuls les caractères ASCII sont pris en charge. Les objets <xref:System.Web.Mail.MailMessage> qui contiennent des caractères non-ASCII et qui sont sérialisés sous .NET Framework 4.5 ou ultérieur ne peuvent pas être désérialisés dans .NET Framework 4.

#### <a name="suggestion"></a>Suggestion

Vérifiez que votre code assure la gestion des exceptions lors de la désérialisation d’un objet <xref:System.Web.Mail.MailMessage>.

| Nom    | Valeur       |
|:--------|:------------|
| Étendue   |Secondaire|
|Version|4,5|
|Type|Runtime

#### <a name="affected-apis"></a>API affectées

-<xref:System.Web.Mail.MailMessage?displayProperty=nameWithType></li></ul>|
