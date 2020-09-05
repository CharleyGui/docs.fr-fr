---
ms.openlocfilehash: 7bf5f7e8a49acc2918dd0d68a1c54a5c277091b0
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496574"
---
### <a name="chained-popups-with-staysopenfalse"></a>Fenêtres contextuelles chaînées avec StaysOpen=False

#### <a name="details"></a>Détails

Une fenêtre contextuelle avec StaysOpen=False est supposée se fermer quand vous cliquez en dehors de la fenêtre contextuelle. Quand plusieurs de ces fenêtres contextuelles sont chaînées (c’est-à-dire quand une fenêtre en contient une autre), de nombreux problèmes apparaissaient, notamment :<ul><li>Ouvrez deux niveaux, cliquez en dehors de P2 mais à l’intérieur de P1.  Il ne se passe rien.</li><li>Ouvrez deux niveaux, cliquez en dehors de P1.  Les deux fenêtres contextuelles se ferment.</li><li>Ouvrez et fermez les deux niveaux.  Essayez à nouveau d’ouvrir P2.  Il ne se passe rien.</li><li>Essayez d’ouvrir trois niveaux.  Vous ne le pouvez pas.  (Rien ne se passe ou les deux premiers niveaux se ferment, en fonction de l’endroit où vous cliquez.) Ces cas (et autres variantes) fonctionnent à présent comme prévu.</li></ul>

| Name    | Valeur       |
|:--------|:------------|
| Étendue   |Edge|
|Version|4.7.1|
|Type|Runtime|

#### <a name="affected-apis"></a>API affectées

- <xref:System.Windows.Controls.Primitives.Popup.StaysOpen?displayProperty=nameWithType>

<!--

#### Affected APIs

- `P:System.Windows.Controls.Primitives.Popup.StaysOpen`

-->
