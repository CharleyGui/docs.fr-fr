---
title: 'Procédure : Trouver un TreeViewItem dans un TreeView'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- TreeView control [WPF], finding a TreeViewItem
- TreeViewItem [WPF], finding
ms.assetid: 72ecd40c-3939-4e01-b617-5e9daa6074d9
ms.openlocfilehash: ad72c7a7fb11dfe605db4119dde831b47dd7c5a4
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69962092"
---
# <a name="how-to-find-a-treeviewitem-in-a-treeview"></a>Procédure : Trouver un TreeViewItem dans un TreeView
Le <xref:System.Windows.Controls.TreeView> contrôle offre un moyen pratique d’afficher des données hiérarchiques. Si votre <xref:System.Windows.Controls.TreeView> est lié à une source de données, <xref:System.Windows.Controls.TreeView.SelectedItem%2A> la propriété constitue un moyen pratique de récupérer rapidement l’objet de données sélectionné. Il est généralement préférable de travailler avec l’objet de données sous-jacent, mais il peut arriver que vous deviez manipuler par programmation <xref:System.Windows.Controls.TreeViewItem>les données contenant. Par exemple, vous devrez peut-être développer par programmation le <xref:System.Windows.Controls.TreeViewItem>ou sélectionner un autre élément dans le. <xref:System.Windows.Controls.TreeView>  
  
 Pour rechercher un <xref:System.Windows.Controls.TreeViewItem> qui contient un objet de données spécifique, vous devez parcourir chaque niveau <xref:System.Windows.Controls.TreeView>de. Les éléments d’un <xref:System.Windows.Controls.TreeView> peuvent également être virtualisés pour améliorer les performances. Dans le cas où les éléments peuvent être virtualisés, vous devez également vous <xref:System.Windows.Controls.TreeViewItem> rendre un pour vérifier s’il contient l’objet de données.  
  
## <a name="example"></a>Exemple  
  
## <a name="description"></a>Description  
 L’exemple suivant recherche un <xref:System.Windows.Controls.TreeView> objet spécifique et retourne le contenant <xref:System.Windows.Controls.TreeViewItem>de l’objet. L’exemple vérifie que chaque <xref:System.Windows.Controls.TreeViewItem> est instancié afin que ses éléments enfants puissent être recherchés. Cet exemple fonctionne également si le <xref:System.Windows.Controls.TreeView> n’utilise pas d’éléments virtualisés.  
  
> [!NOTE]
> L’exemple suivant fonctionne pour tout <xref:System.Windows.Controls.TreeView>, quel que soit le modèle de données sous-jacent <xref:System.Windows.Controls.TreeViewItem> , et effectue des recherches chaque fois que l’objet est trouvé. Une autre technique qui offre de meilleures performances consiste à Rechercher l’objet spécifié dans le modèle de données, à effectuer le suivi de son emplacement dans la hiérarchie de données <xref:System.Windows.Controls.TreeViewItem> , puis <xref:System.Windows.Controls.TreeView>à rechercher le correspondant dans le. Toutefois, la technique qui offre de meilleures performances nécessite une connaissance du modèle de données et ne peut pas être généralisée pour une donnée <xref:System.Windows.Controls.TreeView>.  
  
## <a name="code"></a>Code  
 [!code-csharp[TreeViewFindTVI#1](~/samples/snippets/csharp/VS_Snippets_Wpf/TreeViewFindTVI/CSharp/MainWindow.xaml.cs#1)]
 [!code-vb[TreeViewFindTVI#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TreeViewFindTVI/VisualBasic/MainWindow.xaml.vb#1)]  
  
 Le code précédent s’appuie sur un personnalisé <xref:System.Windows.Controls.VirtualizingStackPanel> qui expose une méthode nommée `BringIntoView`. Le code suivant définit le personnalisé <xref:System.Windows.Controls.VirtualizingStackPanel>.  
  
 [!code-csharp[TreeViewFindTVI#2](~/samples/snippets/csharp/VS_Snippets_Wpf/TreeViewFindTVI/CSharp/MainWindow.xaml.cs#2)]
 [!code-vb[TreeViewFindTVI#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TreeViewFindTVI/VisualBasic/MainWindow.xaml.vb#2)]  
  
 Le code XAML suivant montre comment créer un <xref:System.Windows.Controls.TreeView> qui utilise le personnalisé <xref:System.Windows.Controls.VirtualizingStackPanel>.  
  
 [!code-xaml[TreeViewFindTVI#3](~/samples/snippets/csharp/VS_Snippets_Wpf/TreeViewFindTVI/CSharp/MainWindow.xaml#3)]  
  
## <a name="see-also"></a>Voir aussi

- [Améliorer les performances d'un contrôle TreeView](how-to-improve-the-performance-of-a-treeview.md)
