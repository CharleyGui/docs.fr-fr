---
ms.openlocfilehash: f50022d9a7bacd7be40fe3050ced26e7c25cf7aa
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496149"
---
### <a name="crash-in-selector-when-removing-an-item-from-a-custom-incc-collection"></a>Plantage dans le sélecteur lors de la suppression d’un élément d’une collection INCC personnalisée

#### <a name="details"></a>Détails

Une <code>T:System.InvalidOperationException</code> peut se produire dans les scénarios suivants :<ul><li>L’ItemsSource pour une collection <code>T:System.Windows.Controls.Primitives.Selector</code> est une collection avec une implémentation personnalisée de <code>T:System.Collections.Specialized.INotifyCollectionChanged</code>.</li><li>L’élément sélectionné est supprimé de la collection.</li><li>Le <code>T:System.Collections.Specialized.NotifyCollectionChangedEventArgs</code> a <code>P:System.Collections.Specialized.NotifyCollectionChangedEventArgs.OldStartingIndex</code> = -1 (indiquant une position inconnue).</li></ul>La pile des appels de l’exception commence à System.Windows.Threading.Dispatcher.VerifyAccess() à System.Windows.DependencyObject.GetValue(DependencyProperty dp) à System.Windows.Controls.Primitives.Selector.GetIsSelected(DependencyObject element). Cette exception peut se produire dans .NET Framework 4.5 si l’application a plusieurs threads de répartiteur. Dans .NET Framework 4.7, l’exception peut également se produire dans les applications avec un seul thread de répartiteur. Le problème est résolu dans .NET Framework 4.7.1.

#### <a name="suggestion"></a>Suggestion

Mettre à niveau vers .NET Framework 4.7.1.

| Name    | Valeur       |
|:--------|:------------|
| Étendue   |Secondaire|
|Version|4,7|
|Type|Runtime|

#### <a name="affected-apis"></a>API affectées

Non détectable via l’analyse des API.

<!--

#### Affected APIs

Not detectable via API analysis.

-->
