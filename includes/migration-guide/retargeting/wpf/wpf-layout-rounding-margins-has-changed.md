---
ms.openlocfilehash: 73096e5f61e5257e062df9743cae0f5464892357
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "67804591"
---
### <a name="wpf-layout-rounding-of-margins-has-changed"></a>L’arrondi des marges dans la disposition WPF a changé

|   |   |
|---|---|
|Détails|La façon dont les marges sont arrondies, les bordures et l'arrière-plan ont changé. Résultat de cette modification :<ul><li>La largeur ou la hauteur d'éléments peut croître ou diminuer d'un pixel au plus.</li><li>La position d'un objet peut se déplacer d'un pixel au plus.</li><li>Les éléments centrés peuvent être décalés verticalement ou horizontalement d'un pixel au plus.</li></ul>Par défaut, cette nouvelle disposition est activée uniquement pour les applications qui ciblent le .NET. Framework 4.6.|
|Suggestion|Dans la mesure où cette modification tend à éliminer le découpage droit ou inférieur des contrôles WPF dont le PPP est élevé, les applications qui ciblent les versions antérieures du .NET Framework, mais qui s'exécutent sur le .NET Framework 4.6, peuvent choisir ce nouveau comportement en ajoutant la ligne suivante à la section <code>&lt;runtime&gt;</code> du fichier app.config :<pre><code class="lang-xml">&lt;AppContextSwitchOverrides value=&quot;Switch.MS.Internal.DoNotApplyLayoutRoundingToMarginsAndBorderThickness=false&quot; /&gt;&#39;&#13;&#10;</code></pre>Les applications qui ciblent .NET Framework 4.6, mais veulent que les contrôles WPF soient rendus à l’aide de l’algorithme de disposition précédent peuvent y parvenir en ajoutant la ligne suivante à la section <code>&lt;runtime&gt;</code> du fichier app.config :<pre><code class="lang-xml">&lt;AppContextSwitchOverrides value=&quot;Switch.MS.Internal.DoNotApplyLayoutRoundingToMarginsAndBorderThickness=true&quot; /&gt;&#39;.&#13;&#10;</code></pre>|
|Étendue|Secondaire|
|Version|4.6|
|Type|Reciblage|
