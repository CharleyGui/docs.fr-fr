---
ms.openlocfilehash: 841cb06bf94844d9f4da9dc33e60bad0d43dcd84
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "70997604"
---
### <a name="support-special-relative-uri-notation-when-unicode-is-present"></a>Prise en charge d’une notation d’URI relatif spéciale quand des caractères Unicode sont présents

|   |   |
|---|---|
|Détails|<xref:System.Uri>ne lancera <xref:System.NullReferenceException> plus <xref:System.Uri.TryCreate%2A> de jet d’url lors de l’appel de certaines URL relatives contenant Unicode. La reproduction la <xref:System.NullReferenceException> plus simple de l’est ci-dessous, avec les deux déclarations étant équivalentes:<pre><code class="lang-csharp">bool success = Uri.TryCreate(&quot;http:%C3%A8&quot;, UriKind.RelativeOrAbsolute, out Uri href);&#13;&#10;bool success = Uri.TryCreate(&quot;http:&#232;&quot;, UriKind.RelativeOrAbsolute, out Uri href);&#13;&#10;</code></pre><xref:System.NullReferenceException> ne peut être reproduite que si les conditions suivantes sont réunies :<ul><li>Vous devez spécifier l’URI comme étant relatif en le faisant précéder de « http: » sans le faire suivre de « // ».</li><li>L’URI doit contenir des symboles non réservés ou Unicode encodés en pourcentage.</li></ul>|
|Suggestion|Les utilisateurs qui dépendent de ce comportement pour interdire les URI relatifs doivent spécifier <xref:System.UriKind.Absolute?displayProperty=nameWithType> à la place quand ils créent un URI.|
|Étendue|Edge|
|Version|4.7.2|
|Type|Runtime|
|API affectées|<ul><li><xref:System.Uri.TryCreate(System.Uri,System.Uri,System.Uri@)?displayProperty=nameWithType></li><li><xref:System.Uri.TryCreate(System.String,System.UriKind,System.Uri@)?displayProperty=nameWithType></li><li><xref:System.Uri.TryCreate(System.Uri,System.String,System.Uri@)?displayProperty=nameWithType></li></ul>|
