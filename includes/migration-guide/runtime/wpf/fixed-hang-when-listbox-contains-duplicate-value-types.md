---
ms.openlocfilehash: 5d5423d18091545ad9d50325900f5a9a4fff6dd9
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85622016"
---
### <a name="fixed-a-hang-when-listbox-contains-duplicate-value-types"></a>Correction d’un blocage quand ListBox contient des types valeur en double

#### <a name="details"></a>Détails

Correction d’un problème où un <xref:System.Windows.Controls.ItemsControl> de virtualisation peut se bloquer pendant le défilement quand sa collection Items contient des objets de type valeur en double.

| Nom    | Valeur       |
|:--------|:------------|
| Étendue   |Majeure|
|Version|4.8|
|Type|Runtime|
