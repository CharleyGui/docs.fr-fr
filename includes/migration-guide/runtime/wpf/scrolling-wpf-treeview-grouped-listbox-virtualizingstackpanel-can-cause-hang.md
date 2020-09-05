---
ms.openlocfilehash: 31ada197db36be192317e32a37a353d375d9cc65
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497361"
---
### <a name="scrolling-a-wpf-treeview-or-grouped-listbox-in-a-virtualizingstackpanel-can-cause-a-hang"></a>Le défilement d’un TreeView ou d’une ListBox groupée WPF dans un VirtualizingStackPanel peut provoquer un blocage

#### <a name="details"></a>Détails

Dans le .NET Framework 4.5, le défilement d’un contrôle <xref:System.Windows.Controls.TreeView?displayProperty=fullName> WPF dans un panneau d’empilement virtualisé peut provoquer un blocage si la fenêtre d’affichage comporte des marges (par exemple entre les éléments du <xref:System.Windows.Controls.TreeView?displayProperty=fullName> ou sur un élément ItemsPresenter). En outre, dans certains cas, des éléments de taille différente dans une même vue peuvent causer une instabilité, même s’il n’y a pas de marges.

#### <a name="suggestion"></a>Suggestion

Vous pouvez éviter ce problème en effectuant une mise à niveau vers .NET Framework 4.5.1. Vous pouvez également supprimer les marges des collections de vue (comme les <xref:System.Windows.Controls.TreeView?displayProperty=fullName>s) dans les panneaux d’empilement virtualisés, si tous les éléments qu’ils contiennent sont de même taille.

| Name    | Valeur       |
|:--------|:------------|
| Étendue   |Majeure|
|Version|4,5|
|Type|Runtime|

#### <a name="affected-apis"></a>API affectées

- <xref:System.Windows.Controls.VirtualizingStackPanel.SetIsVirtualizing(System.Windows.DependencyObject,System.Boolean)?displayProperty=nameWithType>

<!--

#### Affected APIs

- `M:System.Windows.Controls.VirtualizingStackPanel.SetIsVirtualizing(System.Windows.DependencyObject,System.Boolean)`

-->
