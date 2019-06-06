---
ms.openlocfilehash: 53fc2a51a7995e9b6ad43e28429313d2aea9abf1
ms.sourcegitcommit: 4735bb7741555bcb870d7b42964d3774f4897a6e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/30/2019
ms.locfileid: "66379234"
---
### <a name="scrolling-a-wpf-treeview-or-grouped-listbox-in-a-virtualizingstackpanel-can-result-in-an-unresponsive-application"></a>Le défilement d’un TreeView ou d’une ListBox groupée WPF dans un VirtualizingStackPanel peut entraîner une absence de réponse de la part d’une application

|   |   |
|---|---|
|Détails|Dans .NET Framework 4.5, le défilement d’un contrôle <xref:System.Windows.Controls.TreeView?displayProperty=name> WPF dans un panneau d’empilement virtualisé peut entraîner une absence de réponse de la part d’une application si la fenêtre d’affichage comporte des marges (par exemple, entre les éléments du <xref:System.Windows.Controls.TreeView?displayProperty=name> ou sur un élément ItemsPresenter). En outre, dans certains cas, des éléments de taille différente dans une même vue peuvent causer une instabilité, même s’il n’y a pas de marges.|
|Suggestion|Vous pouvez éviter ce problème en effectuant une mise à niveau vers .NET Framework 4.5.1. Vous pouvez également supprimer les marges des collections de vue (comme les <xref:System.Windows.Controls.TreeView?displayProperty=name>s) dans les panneaux d’empilement virtualisés, si tous les éléments qu’ils contiennent sont de même taille.|
|Portée|Majeur|
|Version|4.5|
|Type|Runtime|
|API affectées|<ul><li><xref:System.Windows.Controls.VirtualizingStackPanel.SetIsVirtualizing(System.Windows.DependencyObject,System.Boolean)?displayProperty=nameWithType></li></ul>|
