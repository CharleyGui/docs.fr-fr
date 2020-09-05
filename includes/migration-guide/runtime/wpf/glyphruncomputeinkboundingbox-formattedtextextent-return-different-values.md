---
ms.openlocfilehash: d9e1624bbeb91db63bc284b8eb52643938eb42e5
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496985"
---
### <a name="glyphruncomputeinkboundingbox-and-formattedtextextent-return-different-values-beginning-in-net-framework-45"></a>GlyphRun.ComputeInkBoundingBox() et FormattedText.Extent retournent des valeurs différentes à compter de .NET Framework 4.5

#### <a name="details"></a>Détails

Des améliorations ont été apportées à <xref:System.Windows.Media.GlyphRun.ComputeInkBoundingBox> et à <xref:System.Windows.Media.FormattedText.Extent> dans .NET Framework 4.5 pour résoudre les problèmes où la taille des rectangles pour les glyphes qu’ils contenaient était parfois trop petite dans .NET Framework 4.0. Dans le .NET Framework 4.5, certains rectangles englobants sont désormais plus grands, ce qui entraîne des différences subtiles dans la disposition de l’interface utilisateur.

#### <a name="suggestion"></a>Suggestion

Notez que la taille de certains rectangles englobants de glyphes a été augmentée. Ces modifications sont censées améliorer la présentation et les tests hitbox. Toutefois, si vous souhaitez utiliser l’ancien comportement (versions antérieures au .NET 4.5), ajoutez l’entrée suivante au fichier app.config :<pre><code class="lang-xml">&lt;appsettings&gt;&#13;&#10;&lt;add key=&quot;IncludeAllInkInBoundingBox&quot; value=&quot;false&quot;&gt;&#13;&#10;&lt;/appsettings&gt;&#13;&#10;</code></pre>

| Name    | Valeur       |
|:--------|:------------|
| Étendue   |Edge|
|Version|4,5|
|Type|Runtime|

#### <a name="affected-apis"></a>API affectées

- <xref:System.Windows.Media.GlyphRun.ComputeInkBoundingBox?displayProperty=nameWithType>
- <xref:System.Windows.Media.FormattedText.Extent?displayProperty=nameWithType>

<!--

#### Affected APIs

- `M:System.Windows.Media.GlyphRun.ComputeInkBoundingBox`
- `P:System.Windows.Media.FormattedText.Extent`

-->
