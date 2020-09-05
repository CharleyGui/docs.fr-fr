---
ms.openlocfilehash: 2c44c2e1658f8de556d3f7222de3fa6d4594163a
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497147"
---
### <a name="deserialization-of-mailmessage-objects-serialized-under-the-net-framework-45-may-fail"></a>La désérialisation des objets MailMessage sérialisés sous .NET Framework 4.5 peut échouer

#### <a name="details"></a>Détails

À compter de .NET Framework 4.5, les objets <xref:System.Web.Mail.MailMessage> peuvent inclure des caractères non-ASCII. Dans le .NET Framework 4, seuls les caractères ASCII sont pris en charge. Les objets <xref:System.Web.Mail.MailMessage> qui contiennent des caractères non-ASCII et qui sont sérialisés sous .NET Framework 4.5 ou ultérieur ne peuvent pas être désérialisés dans .NET Framework 4.

#### <a name="suggestion"></a>Suggestion

Vérifiez que votre code assure la gestion des exceptions lors de la désérialisation d’un objet <xref:System.Web.Mail.MailMessage>.

| Name    | Valeur       |
|:--------|:------------|
| Étendue   |Secondaire|
|Version|4,5|
|Type|Runtime|

#### <a name="affected-apis"></a>API affectées

- <xref:System.Web.Mail.MailMessage?displayProperty=nameWithType>

<!--

#### Affected APIs

- `T:System.Web.Mail.MailMessage`

-->
