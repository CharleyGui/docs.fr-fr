---
title: 'Comment : lier un TreeView à des données dont la profondeur ne peut pas être déterminée'
ms.date: 03/30/2017
helpviewer_keywords:
- TreeView control [WPF], binding to data of indeterminate depth
ms.assetid: daddcd74-1b0f-4ffd-baeb-ec934c5e0f53
ms.openlocfilehash: cd9a1ee015ebb707a7a06d1c062a1bb3003c96e8
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458617"
---
# <a name="how-to-bind-a-treeview-to-data-that-has-an-indeterminable-depth"></a>Comment : lier un TreeView à des données dont la profondeur ne peut pas être déterminée
Il peut arriver que vous souhaitiez lier un <xref:System.Windows.Controls.TreeView> à une source de données dont la profondeur n’est pas connue.  Cela peut se produire lorsque les données sont récursives par nature, comme un système de fichiers, où les dossiers peuvent contenir des dossiers ou la structure organisationnelle d’une société, où les employés ont d’autres employés comme des collaborateurs directs.  
  
 La source de données doit avoir un modèle d’objet hiérarchique. Par exemple, une classe `Employee` peut contenir une collection d’objets Employee qui sont les collaborateurs directs d’un employé. Si les données sont représentées d’une manière non hiérarchique, vous devez générer une représentation hiérarchique des données.  
  
 Lorsque vous définissez la propriété <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A?displayProperty=nameWithType> et si le <xref:System.Windows.Controls.ItemsControl> génère une <xref:System.Windows.Controls.ItemsControl> pour chaque élément enfant, le <xref:System.Windows.Controls.ItemsControl> enfant utilise le même <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> que le parent. Par exemple, si vous définissez la propriété <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> sur un <xref:System.Windows.Controls.TreeView>lié aux données, chaque <xref:System.Windows.Controls.TreeViewItem> générée utilise le <xref:System.Windows.DataTemplate> qui a été assigné à la propriété <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> de l' <xref:System.Windows.Controls.TreeView>.  
  
 Le <xref:System.Windows.HierarchicalDataTemplate> vous permet de spécifier le <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> pour un <xref:System.Windows.Controls.TreeViewItem>, ou n’importe quelle <xref:System.Windows.Controls.HeaderedItemsControl>, sur le modèle de données. Lorsque vous définissez la propriété <xref:System.Windows.HierarchicalDataTemplate.ItemsSource%2A?displayProperty=nameWithType>, cette valeur est utilisée lorsque la <xref:System.Windows.HierarchicalDataTemplate> est appliquée. À l’aide d’un <xref:System.Windows.HierarchicalDataTemplate>, vous pouvez définir de manière récursive la <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> pour chaque <xref:System.Windows.Controls.TreeViewItem> dans le <xref:System.Windows.Controls.TreeView>.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment lier un <xref:System.Windows.Controls.TreeView> à des données hiérarchiques et utiliser une <xref:System.Windows.HierarchicalDataTemplate> pour spécifier les <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> pour chaque <xref:System.Windows.Controls.TreeViewItem>.  Le <xref:System.Windows.Controls.TreeView> se lie aux données XML qui représentent les employés d’une société.  Chaque élément de `Employee` peut contenir d’autres éléments `Employee` pour indiquer les destinataires des rapports. Étant donné que les données sont récursives, le <xref:System.Windows.HierarchicalDataTemplate> peut être appliqué à chaque niveau.  
  
 [!code-xaml[TreeViewWithUnknownDepth#1](~/samples/snippets/csharp/VS_Snippets_Wpf/TreeViewWithUnknownDepth/CS/Window1.xaml#1)]  
  
## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble de la liaison de données](../../../desktop-wpf/data/data-binding-overview.md)
- [Vue d’ensemble des modèles de données](../data/data-templating-overview.md)
