---
title: 'Comment : utiliser SelectedValue, SelectedValuePath et SelectedItem'
description: Découvrez comment utiliser les propriétés SelectedValue et SelectedValuePath pour spécifier une valeur pour le SelectedItem d’un Windows Presentation Foundation TreeView.
ms.date: 03/30/2017
helpviewer_keywords:
- TreeView control [WPF], SelectedValue properties
- Control class [WPF], SelectedItem properties
- Control class [WPF], TreeView properties
- Control class [WPF], SelectedValue properties
- TreeView control [WPF], SelectedItem properties
- SelectedValue [WPF], SelectedValuePath properties
- TreeView control [WPF], SelectedValuePath properties
- Control class [WPF], SelectedValuePath properties
- SelectedValue [WPF], SelectedItem properties
ms.assetid: 2fc92ad4-f02c-4f89-bbe9-d4978a7af0db
ms.openlocfilehash: ddac2455dee0bf69d25307340eddd5364e43e823
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87166278"
---
# <a name="how-to-use-selectedvalue-selectedvaluepath-and-selecteditem"></a>Comment : utiliser SelectedValue, SelectedValuePath et SelectedItem
Cet exemple montre comment utiliser les <xref:System.Windows.Controls.TreeView.SelectedValue%2A> Propriétés et <xref:System.Windows.Controls.TreeView.SelectedValuePath%2A> pour spécifier une valeur pour le <xref:System.Windows.Controls.TreeView.SelectedItem%2A> d’un <xref:System.Windows.Controls.TreeView> .  
  
## <a name="example"></a>Exemple  
 La <xref:System.Windows.Controls.TreeView.SelectedValuePath%2A> propriété fournit un moyen de spécifier un <xref:System.Windows.Controls.TreeView.SelectedValue%2A> pour le <xref:System.Windows.Controls.TreeView.SelectedItem%2A> dans un <xref:System.Windows.Controls.TreeView> . Le <xref:System.Windows.Controls.TreeView.SelectedItem%2A> représente un objet dans la <xref:System.Windows.Controls.ItemsControl.Items%2A> collection et le <xref:System.Windows.Controls.TreeView> affiche la valeur d’une propriété unique de l’élément sélectionné. La <xref:System.Windows.Controls.TreeView.SelectedValuePath%2A> propriété spécifie le chemin d’accès à la propriété qui est utilisée pour déterminer la valeur de la <xref:System.Windows.Controls.TreeView.SelectedValue%2A> propriété. Les exemples de cette rubrique illustrent ce concept.  
  
 L’exemple suivant montre un <xref:System.Windows.Data.XmlDataProvider> qui contient des informations sur les employés.  
  
 [!code-xaml[TreeViewSelectedValue#XMLDataProvider](~/samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSelectedValue/CS/Window1.xaml#xmldataprovider)]  
  
 L’exemple suivant définit un <xref:System.Windows.HierarchicalDataTemplate> qui affiche les `EmployeeName` et `EmployeeWorkDay` de `Employee` . Notez que le <xref:System.Windows.HierarchicalDataTemplate> ne spécifie pas le dans le cadre `EmployeeNumber` du modèle.  
  
 [!code-xaml[TreeViewSelectedValue#HierarchicalDataTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSelectedValue/CS/Window1.xaml#hierarchicaldatatemplate)]  
  
 L’exemple suivant montre un <xref:System.Windows.Controls.TreeView> qui utilise le précédemment défini <xref:System.Windows.HierarchicalDataTemplate> et qui affecte <xref:System.Windows.Controls.TreeView.SelectedValue%2A> la valeur à la propriété `EmployeeNumber` . Lorsque vous sélectionnez un `EmployeeName` dans le <xref:System.Windows.Controls.TreeView> , la <xref:System.Windows.Controls.TreeView.SelectedItem%2A> propriété retourne l' `EmployeeInfo` élément de données qui correspond au sélectionné `EmployeeName` . Toutefois, étant donné que a la <xref:System.Windows.Controls.TreeView.SelectedValuePath%2A> <xref:System.Windows.Controls.TreeView> valeur `EmployeeNumber` , le a la <xref:System.Windows.Controls.TreeView.SelectedValue%2A> valeur `EmployeeNumber` .  
  
 [!code-xaml[TreeViewSelectedValue#SelectedValuePath](~/samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSelectedValue/CS/Window1.xaml#selectedvaluepath)]  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Controls.TreeView>
- <xref:System.Windows.Controls.TreeViewItem>
- [Vue d'ensemble de TreeView](treeview-overview.md)
- [Rubriques Comment](treeview-how-to-topics.md)
