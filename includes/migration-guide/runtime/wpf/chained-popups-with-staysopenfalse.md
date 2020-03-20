---
ms.openlocfilehash: 22c4b61b293ac2366cae1dc73e0f6805a4a5fb8b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "67857210"
---
### <a name="chained-popups-with-staysopenfalse"></a>Fenêtres contextuelles chaînées avec StaysOpen=False

|   |   |
|---|---|
|Détails|Une fenêtre contextuelle avec StaysOpen=False est supposée se fermer quand vous cliquez en dehors de la fenêtre contextuelle. Quand plusieurs de ces fenêtres contextuelles sont chaînées (c’est-à-dire quand une fenêtre en contient une autre), de nombreux problèmes apparaissaient, notamment :<ul><li>Ouvrez deux niveaux, cliquez en dehors de P2 mais à l’intérieur de P1.  Rien ne se produit.</li><li>Ouvrez deux niveaux, cliquez en dehors de P1.  Les deux fenêtres contextuelles se ferment.</li><li>Ouvrez et fermez les deux niveaux.  Essayez à nouveau d’ouvrir P2.  Rien ne se produit.</li><li>Essayez d’ouvrir trois niveaux.  Désolé... Cette migration est impossible.  (Soit rien ne se passe, soit les deux premiers niveaux se ferment, selon l’endroit où vous cliquez.) Ces cas (et d’autres variantes) fonctionnent maintenant comme prévu.</li></ul>|
|Étendue|Edge|
|Version|4.7.1|
|Type|Runtime|
|API affectées|<ul><li><xref:System.Windows.Controls.Primitives.Popup.StaysOpen?displayProperty=nameWithType></li></ul>|
