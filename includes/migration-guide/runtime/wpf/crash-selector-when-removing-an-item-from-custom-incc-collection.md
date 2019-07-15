---
ms.openlocfilehash: 8f4ee44e8432bae3537c6f064f564b9f044a7c33
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/11/2019
ms.locfileid: "67802437"
---
### <a name="crash-in-selector-when-removing-an-item-from-a-custom-incc-collection"></a>Plantage dans le sélecteur lors de la suppression d’un élément d’une collection INCC personnalisée

|   |   |
|---|---|
|Détails|Une <code>T:System.InvalidOperationException</code> peut se produire dans les scénarios suivants :<ul><li>L’ItemsSource pour une collection <code>T:System.Windows.Controls.Primitives.Selector</code> est une collection avec une implémentation personnalisée de <code>T:System.Collections.Specialized.INotifyCollectionChanged</code>.</li><li>L’élément sélectionné est supprimé de la collection.</li><li>Le <code>T:System.Collections.Specialized.NotifyCollectionChangedEventArgs</code> a <code>P:System.Collections.Specialized.NotifyCollectionChangedEventArgs.OldStartingIndex</code> = -1 (indiquant une position inconnue).</li></ul>La pile des appels de l’exception commence à System.Windows.Threading.Dispatcher.VerifyAccess() à System.Windows.DependencyObject.GetValue(DependencyProperty dp) à System.Windows.Controls.Primitives.Selector.GetIsSelected(DependencyObject element). Cette exception peut se produire dans .NET Framework 4.5 si l’application a plusieurs threads de répartiteur. Dans .NET Framework 4.7, l’exception peut également se produire dans les applications avec un seul thread de répartiteur. Le problème est résolu dans .NET Framework 4.7.1.|
|Suggestion|Mettre à niveau vers .NET Framework 4.7.1.|
|Portée|Mineur|
|Version|4.7|
|Type|Runtime|

