---
ms.openlocfilehash: f4ff938b2d0e9ead481fdf239aed8a6b918a99b0
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620452"
---
### <a name="listboxitem-isselected-binding-issue-with-observablecollectionlttgtmove"></a>Problème de liaison ListBoxItem IsSelected avec ObservableCollection&lt;T&gt;.Move

#### <a name="details"></a>Détails

L’appel de <xref:System.Collections.ObjectModel.ObservableCollection%601.Move(System.Int32,System.Int32)> ou de <xref:System.Collections.ObjectModel.ObservableCollection%601.MoveItem(System.Int32,System.Int32)> sur une collection liée à un <xref:System.Windows.Controls.ListBox?displayProperty=fullName> avec des éléments sélectionnés peut entraîner un comportement imprévisible avec une sélection ultérieure ou la désélection d’éléments de <xref:System.Windows.Controls.ListBox?displayProperty=fullName>.

#### <a name="suggestion"></a>Suggestion

L’appel de <xref:System.Collections.ObjectModel.Collection%601.Remove(%600)?displayProperty=fullName> et de <xref:System.Collections.ObjectModel.Collection%601.Insert(System.Int32,%600)?displayProperty=fullName> au lieu de <xref:System.Collections.ObjectModel.ObservableCollection%601.Move(System.Int32,System.Int32)> permet de contourner ce problème. Étant donné que ce problème a été résolu dans le .NET Framework 4.6, vous pouvez également mettre à niveau votre version du .NET Framework.

| Nom    | Valeur       |
|:--------|:------------|
| Étendue   |Secondaire|
|Version|4,5|
|Type|Runtime

#### <a name="affected-apis"></a>API affectées

-<xref:System.Collections.ObjectModel.ObservableCollection%601.Move(System.Int32,System.Int32)?displayProperty=nameWithType></li><li><xref:System.Collections.ObjectModel.ObservableCollection%601.MoveItem(System.Int32,System.Int32)?displayProperty=nameWithType></li></ul>|
