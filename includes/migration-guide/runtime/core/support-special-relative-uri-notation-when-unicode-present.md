---
ms.openlocfilehash: c8a6870a9d34889dd8f5305035744bfc63be6af6
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/11/2019
ms.locfileid: "67856997"
---
### <a name="support-special-relative-uri-notation-when-unicode-is-present"></a>Prise en charge d’une notation d’URI relatif spéciale quand des caractères Unicode sont présents

|   |   |
|---|---|
|Détails|<xref:System.Uri> ne lève plus une <xref:System.NullReferenceException> quand il appelle <xref:System.Uri.TryCreate%2A> sur certains URI relatifs contenant des caractères Unicode. La reproduction la plus simple du <xref:System.NullReferenceException> est indiquée ci-dessous, où les deux instructions sont équivalentes :<pre><code class="lang-csharp">bool success = Uri.TryCreate(&quot;http:%C3%A8&quot;, UriKind.RelativeOrAbsolute, out Uri href);&#13;&#10;bool success = Uri.TryCreate(&quot;http:&#232;&quot;, UriKind.RelativeOrAbsolute, out Uri href);&#13;&#10;</code></pre><xref:System.NullReferenceException> ne peut être reproduite que si les conditions suivantes sont réunies :<ul><li>Vous devez spécifier l’URI comme étant relatif en le faisant précéder de « http: » sans le faire suivre de « // ».</li><li>L’URI doit contenir des symboles non réservés ou Unicode encodés en pourcentage.</li></ul>|
|Suggestion|Les utilisateurs qui dépendent de ce comportement pour interdire les URI relatifs doivent spécifier <xref:System.UriKind.Absolute?displayProperty=nameWithType> à la place quand ils créent un URI.|
|Portée|Microsoft Edge|
|Version|4.7.2|
|Type|Runtime|
|API affectées|<ul><li><xref:System.Uri.TryCreate(System.Uri,System.Uri,System.Uri@)?displayProperty=nameWithType></li><li><xref:System.Uri.TryCreate(System.String,System.UriKind,System.Uri@)?displayProperty=nameWithType></li><li><xref:System.Uri.TryCreate(System.Uri,System.String,System.Uri@)?displayProperty=nameWithType></li></ul>|

