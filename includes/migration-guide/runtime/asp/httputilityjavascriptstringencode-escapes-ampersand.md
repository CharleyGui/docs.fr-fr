---
ms.openlocfilehash: b648aee35ff44730f545f0fa06f4e0a86615dece
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90606851"
---
### <a name="httputilityjavascriptstringencode-escapes-ampersand"></a>HttpUtility.JavaScriptStringEncode place le caractère esperluette (&) dans une séquence d’échappement

#### <a name="details"></a>Détails

Depuis .NET Framework 4.5, <xref:System.Web.HttpUtility.JavaScriptStringEncode(System.String)?displayProperty=fullName> place le caractère esperluette (&amp;) dans une séquence d’échappement.

#### <a name="suggestion"></a>Suggestion

Si votre application dépend du comportement précédent de cette méthode, vous pouvez ajouter un paramètre aspnet:JavaScriptDoNotEncodeAmpersand à l’[élément appSettings ASP.NET](/previous-versions/aspnet/hh975440(v=vs.120)) dans votre fichier de configuration.

| Name    | Valeur       |
|:--------|:------------|
| Étendue   |Secondaire|
|Version|4.5|
|Type|Runtime|

#### <a name="affected-apis"></a>API affectées

- <xref:System.Web.HttpUtility.JavaScriptStringEncode(System.String)?displayProperty=nameWithType>
- <xref:System.Web.HttpUtility.JavaScriptStringEncode(System.String,System.Boolean)?displayProperty=nameWithType>

<!--

#### Affected APIs

- `M:System.Web.HttpUtility.JavaScriptStringEncode(System.String)`
- `M:System.Web.HttpUtility.JavaScriptStringEncode(System.String,System.Boolean)`

-->
