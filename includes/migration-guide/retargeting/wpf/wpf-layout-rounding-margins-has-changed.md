---
ms.openlocfilehash: f907cb1939e111c586d68243e6b8a8e291974e36
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85615719"
---
### <a name="wpf-layout-rounding-of-margins-has-changed"></a>L’arrondi des marges dans la disposition WPF a changé

#### <a name="details"></a>Détails

La façon dont les marges sont arrondies, les bordures et l'arrière-plan ont changé. Résultat de cette modification :

- La largeur ou la hauteur d'éléments peut croître ou diminuer d'un pixel au plus.
- La position d'un objet peut se déplacer d'un pixel au plus.
- Les éléments centrés peuvent être décalés verticalement ou horizontalement d'un pixel au plus.
Par défaut, cette nouvelle disposition est activée uniquement pour les applications qui ciblent le .NET. Framework 4.6.

#### <a name="suggestion"></a>Suggestion

Dans la mesure où cette modification tend à éliminer le découpage droit ou inférieur des contrôles WPF dont le PPP est élevé, les applications qui ciblent les versions antérieures du .NET Framework, mais qui s'exécutent sur le .NET Framework 4.6, peuvent choisir ce nouveau comportement en ajoutant la ligne suivante à la section `<runtime>` du fichier app.config :

<pre><code class="lang-xml">&lt;AppContextSwitchOverrides value=&quot;Switch.MS.Internal.DoNotApplyLayoutRoundingToMarginsAndBorderThickness=false&quot; /&gt;&#39;&#13;&#10;</code></pre>

Les applications qui ciblent .NET Framework 4.6, mais veulent que les contrôles WPF soient rendus à l’aide de l’algorithme de disposition précédent peuvent y parvenir en ajoutant la ligne suivante à la section `<runtime>` du fichier app.config :

<pre><code class="lang-xml">&lt;AppContextSwitchOverrides value=&quot;Switch.MS.Internal.DoNotApplyLayoutRoundingToMarginsAndBorderThickness=true&quot; /&gt;&#39;.&#13;&#10;</code></pre>

| Nom    | Valeur       |
|:--------|:------------|
| Étendue   | Secondaire       |
| Version | 4.6         |
| Type    | Reciblage |
