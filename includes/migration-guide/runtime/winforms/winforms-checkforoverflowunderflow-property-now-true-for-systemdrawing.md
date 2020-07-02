---
ms.openlocfilehash: 4cd06fd02fadbaa9f74e40f850e688ee883454ed
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620443"
---
### <a name="winforms-checkforoverflowunderflow-property-is-now-true-for-systemdrawing"></a>La propriété CheckForOverflowUnderflow de WinForm est désormais true pour System.Drawing

#### <a name="details"></a>Détails

La propriété CheckForOverflowUnderflow pour l’assembly System.Drawing.dll est définie sur true.

#### <a name="suggestion"></a>Suggestion

Auparavant, en cas de dépassement de capacité, le résultat était tronqué automatiquement. Désormais, une exception <xref:System.OverflowException?displayProperty=fullName> est levée.

| Nom    | Valeur       |
|:--------|:------------|
| Étendue   |Edge|
|Version|4,5|
|Type|Runtime|
