---
ms.openlocfilehash: 841cb06bf94844d9f4da9dc33e60bad0d43dcd84
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/14/2019
ms.locfileid: "70997604"
---
### <a name="support-special-relative-uri-notation-when-unicode-is-present"></a>Prise en charge d’une notation d’URI relatif spéciale quand des caractères Unicode sont présents

|   |   |
|---|---|
|Détails|<xref:System.Uri>ne lève plus d' <xref:System.NullReferenceException> exception lors de l’appel <xref:System.Uri.TryCreate%2A> de sur certains URI relatifs contenant du Unicode. La reproduction la plus simple du <xref:System.NullReferenceException> est ci-dessous, avec les deux instructions équivalentes :<pre><code class="lang-csharp">bool success = Uri.TryCreate(&quot;http:%C3%A8&quot;, UriKind.RelativeOrAbsolute, out Uri href);&#13;&#10;bool success = Uri.TryCreate(&quot;http:&#232;&quot;, UriKind.RelativeOrAbsolute, out Uri href);&#13;&#10;</code></pre><xref:System.NullReferenceException> ne peut être reproduite que si les conditions suivantes sont réunies :<ul><li>Vous devez spécifier l’URI comme étant relatif en le faisant précéder de « http: » sans le faire suivre de « // ».</li><li>L’URI doit contenir des symboles non réservés ou Unicode encodés en pourcentage.</li></ul>|
|Suggestion|Les utilisateurs qui dépendent de ce comportement pour interdire les URI relatifs doivent spécifier <xref:System.UriKind.Absolute?displayProperty=nameWithType> à la place quand ils créent un URI.|
|`Scope`|Microsoft Edge|
|Version|4.7.2|
|Type|Runtime|
|API affectées|<ul><li><xref:System.Uri.TryCreate(System.Uri,System.Uri,System.Uri@)?displayProperty=nameWithType></li><li><xref:System.Uri.TryCreate(System.String,System.UriKind,System.Uri@)?displayProperty=nameWithType></li><li><xref:System.Uri.TryCreate(System.Uri,System.String,System.Uri@)?displayProperty=nameWithType></li></ul>|
