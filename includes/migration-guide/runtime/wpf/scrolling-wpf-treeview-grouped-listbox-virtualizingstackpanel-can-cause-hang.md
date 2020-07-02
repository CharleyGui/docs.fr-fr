---
ms.openlocfilehash: 1be68c2968d0eaa9024007bcf37abf9e44c36f1c
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85622054"
---
### <a name="scrolling-a-wpf-treeview-or-grouped-listbox-in-a-virtualizingstackpanel-can-cause-a-hang"></a>Le défilement d’un TreeView ou d’une ListBox groupée WPF dans un VirtualizingStackPanel peut provoquer un blocage

#### <a name="details"></a>Détails

Dans le .NET Framework 4.5, le défilement d’un contrôle <xref:System.Windows.Controls.TreeView?displayProperty=fullName> WPF dans un panneau d’empilement virtualisé peut provoquer un blocage si la fenêtre d’affichage comporte des marges (par exemple entre les éléments du <xref:System.Windows.Controls.TreeView?displayProperty=fullName> ou sur un élément ItemsPresenter). En outre, dans certains cas, des éléments de taille différente dans une même vue peuvent causer une instabilité, même s’il n’y a pas de marges.

#### <a name="suggestion"></a>Suggestion

Vous pouvez éviter ce problème en effectuant une mise à niveau vers .NET Framework 4.5.1. Vous pouvez également supprimer les marges des collections de vue (comme les <xref:System.Windows.Controls.TreeView?displayProperty=fullName>s) dans les panneaux d’empilement virtualisés, si tous les éléments qu’ils contiennent sont de même taille.

| Nom    | Valeur       |
|:--------|:------------|
| Étendue   |Majeure|
|Version|4,5|
|Type|Runtime

#### <a name="affected-apis"></a>API affectées

-<xref:System.Windows.Controls.VirtualizingStackPanel.SetIsVirtualizing(System.Windows.DependencyObject,System.Boolean)?displayProperty=nameWithType></li></ul>|
