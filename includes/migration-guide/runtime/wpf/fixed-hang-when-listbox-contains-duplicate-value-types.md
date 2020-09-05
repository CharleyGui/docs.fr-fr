---
ms.openlocfilehash: 7637c2d96aef93b4cf8f2314c1dd1edba51d553c
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496388"
---
### <a name="fixed-a-hang-when-listbox-contains-duplicate-value-types"></a>Correction d’un blocage quand ListBox contient des types valeur en double

#### <a name="details"></a>Détails

Correction d’un problème où un <xref:System.Windows.Controls.ItemsControl> de virtualisation peut se bloquer pendant le défilement quand sa collection Items contient des objets de type valeur en double.

| Name    | Valeur       |
|:--------|:------------|
| Étendue   |Majeure|
|Version|4.8|
|Type|Runtime|

#### <a name="affected-apis"></a>API affectées

Non détectable via l’analyse des API.

<!--

#### Affected APIs

Not detectable via API analysis.

-->
