---
ms.openlocfilehash: 08a9292c5a41e7b9b7c1bcc18ec96460de19863f
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621069"
---
### <a name="support-special-relative-uri-notation-when-unicode-is-present"></a>Prise en charge d’une notation d’URI relatif spéciale quand des caractères Unicode sont présents

#### <a name="details"></a>Détails

<xref:System.Uri>ne lève plus d’exception <xref:System.NullReferenceException> lors de l’appel <xref:System.Uri.TryCreate%2A> de sur certains URI relatifs contenant du Unicode. La reproduction la plus simple du <xref:System.NullReferenceException> est ci-dessous, avec les deux instructions équivalentes :<pre><code class="lang-csharp">bool success = Uri.TryCreate(&quot;http:%C3%A8&quot;, UriKind.RelativeOrAbsolute, out Uri href);&#13;&#10;bool success = Uri.TryCreate(&quot;http:&#232;&quot;, UriKind.RelativeOrAbsolute, out Uri href);&#13;&#10;</code></pre><xref:System.NullReferenceException> ne peut être reproduite que si les conditions suivantes sont réunies :<ul><li>Vous devez spécifier l’URI comme étant relatif en le faisant précéder de « http: » sans le faire suivre de « // ».</li><li>L’URI doit contenir des symboles non réservés ou Unicode encodés en pourcentage.</li></ul>

#### <a name="suggestion"></a>Suggestion

Les utilisateurs qui dépendent de ce comportement pour interdire les URI relatifs doivent spécifier <xref:System.UriKind.Absolute?displayProperty=nameWithType> à la place quand ils créent un URI.

| Nom    | Valeur       |
|:--------|:------------|
| Étendue   |Edge|
|Version|4.7.2|
|Type|Runtime

#### <a name="affected-apis"></a>API affectées

-<xref:System.Uri.TryCreate(System.Uri,System.Uri,System.Uri@)?displayProperty=nameWithType></li><li><xref:System.Uri.TryCreate(System.String,System.UriKind,System.Uri@)?displayProperty=nameWithType></li><li><xref:System.Uri.TryCreate(System.Uri,System.String,System.Uri@)?displayProperty=nameWithType></li></ul>|
