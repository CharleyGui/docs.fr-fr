---
ms.openlocfilehash: 8b2a01eb6dfdd5bd2bcbef6014d4edeb3ec82ac1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "66379700"
---
### <a name="winforms-checkforoverflowunderflow-property-is-now-true-for-systemdrawing"></a>La propriété CheckForOverflowUnderflow de WinForm est désormais true pour System.Drawing

|   |   |
|---|---|
|Détails|La propriété CheckForOverflowUnderflow pour l’assembly System.Drawing.dll est définie sur true.|
|Suggestion|Auparavant, en cas de dépassement de capacité, le résultat était tronqué automatiquement. Désormais, une exception <xref:System.OverflowException?displayProperty=name> est levée.|
|Portée|Microsoft Edge|
|Version|4.5|
|Type|Runtime|
