---
ms.openlocfilehash: 44cb833fc93caaa79000147421e1c013f755b9cb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "68238022"
---
### <a name="listboxitem-isselected-binding-issue-with-observablecollectionlttgtmove"></a>Problème de liaison ListBoxItem IsSelected avec ObservableCollection&lt;T&gt;.Move

|   |   |
|---|---|
|Détails|L’appel de <xref:System.Collections.ObjectModel.ObservableCollection%601.Move(System.Int32,System.Int32)> ou de <xref:System.Collections.ObjectModel.ObservableCollection%601.MoveItem(System.Int32,System.Int32)> sur une collection liée à un <xref:System.Windows.Controls.ListBox?displayProperty=name> avec des éléments sélectionnés peut entraîner un comportement imprévisible avec une sélection ultérieure ou la désélection d’éléments de <xref:System.Windows.Controls.ListBox?displayProperty=name>.|
|Suggestion|L’appel de <xref:System.Collections.ObjectModel.Collection%601.Remove(%600)?displayProperty=name> et de <xref:System.Collections.ObjectModel.Collection%601.Insert(System.Int32,%600)?displayProperty=name> au lieu de <xref:System.Collections.ObjectModel.ObservableCollection%601.Move(System.Int32,System.Int32)> permet de contourner ce problème. Étant donné que ce problème a été résolu dans le .NET Framework 4.6, vous pouvez également mettre à niveau votre version du .NET Framework.|
|Étendue|Secondaire|
|Version|4.5|
|Type|Runtime|
|API affectées|<ul><li><xref:System.Collections.ObjectModel.ObservableCollection%601.Move(System.Int32,System.Int32)?displayProperty=nameWithType></li><li><xref:System.Collections.ObjectModel.ObservableCollection%601.MoveItem(System.Int32,System.Int32)?displayProperty=nameWithType></li></ul>|
