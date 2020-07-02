---
ms.openlocfilehash: 86169b5c9a20678647153c951550e590a5bce588
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85622241"
---
### <a name="resizing-a-grid-can-hang"></a>Le redimensionnement d’une grille peut se bloquer

#### <a name="details"></a>Détails

Une boucle infinie peut se produire lors de la présentation d’une <code>T:System.Windows.Controls.Grid</code> dans les circonstances suivantes :<ul><li>Les définitions de ligne contiennent deux \* lignes, déclarant une MinHeight et une MaxHeight.</li><li>Le contenu des \* lignes ne dépasse pas le MaxHeight correspondant</li><li>La hauteur disponible de la grille est dépassée par le premier MinHeight (plus les autres lignes fixes ou automatiques)</li><li>L’application cible .NET Framework 4.7 ou adhère à l’algorithme d’allocation de 4.7 en définissant <code>Switch.System.Windows.Controls.Grid.StarDefinitionsCanExceedAvailableSpace=false</code></li></ul>La boucle se produit également avec plus de deux lignes, ou dans le cas analogue pour les colonnes. Le problème est résolu dans .NET Framework 4.7.1.

#### <a name="suggestion"></a>Suggestion

Mettre à niveau vers .NET Framework 4.7.1.  Si vous n’avez pas besoin de l’algorithme d’allocation de 4.7, vous pouvez aussi utiliser le paramètre de configuration suivant :<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Controls.Grid.StarDefinitionsCanExceedAvailableSpace=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>

| Nom    | Valeur       |
|:--------|:------------|
| Étendue   |Edge|
|Version|4,7|
|Type|Runtime|
