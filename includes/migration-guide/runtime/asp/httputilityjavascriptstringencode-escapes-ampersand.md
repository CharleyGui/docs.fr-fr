---
ms.openlocfilehash: d587e542a72d584502ac3ac892619cc38b88ef77
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619925"
---
### <a name="httputilityjavascriptstringencode-escapes-ampersand"></a>HttpUtility.JavaScriptStringEncode place le caractère esperluette (&) dans une séquence d’échappement

#### <a name="details"></a>Détails

Depuis .NET Framework 4.5, <xref:System.Web.HttpUtility.JavaScriptStringEncode(System.String)?displayProperty=fullName> place le caractère esperluette (&amp;) dans une séquence d’échappement.

#### <a name="suggestion"></a>Suggestion

Si votre application dépend du comportement précédent de cette méthode, vous pouvez ajouter un paramètre aspnet:JavaScriptDoNotEncodeAmpersand à l’[élément appSettings ASP.NET](https://docs.microsoft.com/previous-versions/aspnet/hh975440(v=vs.120)) dans votre fichier de configuration.

| Nom    | Valeur       |
|:--------|:------------|
| Étendue   |Secondaire|
|Version|4,5|
|Type|Runtime

#### <a name="affected-apis"></a>API affectées

-<xref:System.Web.HttpUtility.JavaScriptStringEncode(System.String)?displayProperty=nameWithType></li><li><xref:System.Web.HttpUtility.JavaScriptStringEncode(System.String,System.Boolean)?displayProperty=nameWithType></li></ul>|
