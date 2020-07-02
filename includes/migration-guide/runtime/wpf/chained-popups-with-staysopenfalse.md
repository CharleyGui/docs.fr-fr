---
ms.openlocfilehash: 171b7a3a962f8259e64b88f1ae893e649b5f24bb
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621105"
---
### <a name="chained-popups-with-staysopenfalse"></a>Fenêtres contextuelles chaînées avec StaysOpen=False

#### <a name="details"></a>Détails

Une fenêtre contextuelle avec StaysOpen=False est supposée se fermer quand vous cliquez en dehors de la fenêtre contextuelle. Quand plusieurs de ces fenêtres contextuelles sont chaînées (c’est-à-dire quand une fenêtre en contient une autre), de nombreux problèmes apparaissaient, notamment :<ul><li>Ouvrez deux niveaux, cliquez en dehors de P2 mais à l’intérieur de P1.  Rien ne se produit.</li><li>Ouvrez deux niveaux, cliquez en dehors de P1.  Les deux fenêtres contextuelles se ferment.</li><li>Ouvrez et fermez les deux niveaux.  Essayez à nouveau d’ouvrir P2.  Rien ne se produit.</li><li>Essayez d’ouvrir trois niveaux.  Désolé... Cette migration est impossible.  (Rien ne se passe ou les deux premiers niveaux se ferment, en fonction de l’endroit où vous cliquez.) Ces cas (et autres variantes) fonctionnent à présent comme prévu.</li></ul>

| Nom    | Valeur       |
|:--------|:------------|
| Étendue   |Edge|
|Version|4.7.1|
|Type|Runtime

#### <a name="affected-apis"></a>API affectées

-<xref:System.Windows.Controls.Primitives.Popup.StaysOpen?displayProperty=nameWithType></li></ul>|
