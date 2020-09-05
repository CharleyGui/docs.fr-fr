---
ms.openlocfilehash: 2ae17e0823ec2fa064c948d9ea7bd19cbd34cb6a
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496344"
---
### <a name="horizontal-scrolling-and-virtualization"></a>Défilement horizontal et virtualisation

#### <a name="details"></a>Détails

Cette modification s’applique à un <xref:System.Windows.Controls.ItemsControl?displayProperty=fullName> qui fait sa propre virtualisation dans le sens orthogonal vers la direction de défilement principale (l’exemple classique est <xref:System.Windows.Controls.DataGrid?displayProperty=fullName> avec EnableColumnVirtualization=&quot;True&quot;).  Le résultat de certaines opérations de défilement horizontal a été changé afin de produire des résultats qui sont plus intuitifs et plus analogues par rapport aux résultats des opérations verticales comparables.<p/>Les opérations comprennent &quot;Défilement ici&quot; et &quot;Bord droit&quot; (il s’agit là des noms mentionnés dans le menu obtenu en double-cliquant sur une barre de défilement horizontale).  Toutes deux calculent un décalage candidat et appellent <xref:System.Windows.Controls.Primitives.IScrollInfo.SetHorizontalOffset(System.Double)>.<p/>Après le défilement vers le nouveau décalage, la notion de &quot;ici&quot; ou &quot;bord droit&quot; peut avoir changé, car le nouveau contenu dévirtualisé a changé la valeur de <xref:System.Windows.Controls.Primitives.IScrollInfo.ExtentWidth?displayProperty=fullName>.<p/>Avant .NET Framework 4.6.2, l’opération de défilement utilisait simplement le décalage final, même si ce n’est plus &quot;ici&quot; ou le &quot;bord droit&quot;.  Ceci entraîne des effets comme un « rebondissement » du curseur de défilement, comme illustré dans l’exemple. Supposons qu’un <xref:System.Windows.Controls.DataGrid?displayProperty=fullName> a ExtentWidth=1000 et Width=200.  Un défilement vers « Bord droit » utilise un décalage candidat de 1000-200 = 800.  Lors du défilement jusqu’à ce décalage, les nouvelles colonnes sont dévirtualisées. Supposons qu’elles sont très larges, de sorte que <xref:System.Windows.Controls.Primitives.IScrollInfo.ExtentWidth?displayProperty=fullName> passe à 2000.  Le défilement se termine avec HorizontalOffset=800, et le curseur &quot;rebondit&quot; à proximité du centre de la barre de défilement (précisément à 800/2000 = 40 %).<p/>Le changement consiste à recalculer un nouveau décalage candidat quand cette situation se produit, puis à réessayer. (C’est déjà comme cela que le défilement vertical fonctionne.) <p/>Le changement génère une expérience plus prévisible et intuitive pour l’utilisateur final, mais il peut aussi affecter toute application qui dépend de la valeur exacte de <xref:System.Windows.Controls.Primitives.IScrollInfo.HorizontalOffset?displayProperty=fullName> après un défilement horizontal, qu’il s’agisse d’un appel explicite à <xref:System.Windows.Controls.Primitives.IScrollInfo.SetHorizontalOffset(System.Double)> ou d’un appel effectué par l’utilisateur final.

#### <a name="suggestion"></a>Suggestion

Une application qui utilise une valeur prédite pour <xref:System.Windows.Controls.Primitives.IScrollInfo.HorizontalOffset?displayProperty=fullName> doit être changée afin de récupérer la valeur réelle (et la valeur de <xref:System.Windows.Controls.Primitives.IScrollInfo.ExtentWidth?displayProperty=fullName>) après un défilement horizontal susceptible de modifier <xref:System.Windows.Controls.Primitives.IScrollInfo.ExtentWidth?displayProperty=fullName> en raison de la dévirtualisation.

| Name    | Valeur       |
|:--------|:------------|
| Étendue   |Secondaire|
|Version|4.6.2|
|Type|Runtime|

#### <a name="affected-apis"></a>API affectées

- <xref:System.Windows.Controls.Primitives.IScrollInfo?displayProperty=nameWithType>

<!--

#### Affected APIs

- `T:System.Windows.Controls.Primitives.IScrollInfo`

-->
