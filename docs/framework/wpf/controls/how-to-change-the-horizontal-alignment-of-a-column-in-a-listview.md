---
title: "Comment : modifier l'alignement horizontal d'une colonne dans un ListView"
ms.date: 03/30/2017
helpviewer_keywords:
- ListView controls [WPF], horizontal alignment [WPF]
ms.assetid: b9573e44-9dad-4d14-939c-7859ca372758
ms.openlocfilehash: 5447f1a73b008b2ed4f345eba00f4d631e11e257
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458606"
---
# <a name="how-to-change-the-horizontal-alignment-of-a-column-in-a-listview"></a>Comment : modifier l'alignement horizontal d'une colonne dans un ListView
Par défaut, le contenu de chaque colonne d’un <xref:System.Windows.Controls.ListViewItem> est aligné à gauche. Vous pouvez modifier l’alignement de chaque colonne en fournissant une <xref:System.Windows.DataTemplate> et en définissant la propriété <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> sur l’élément dans le <xref:System.Windows.DataTemplate>. Cette rubrique montre comment un <xref:System.Windows.Controls.ListView> aligne son contenu par défaut et comment modifier l’alignement d’une colonne dans une <xref:System.Windows.Controls.ListView>.  
  
## <a name="example"></a>Exemple  
 Dans l’exemple suivant, les données des colonnes `Title` et `ISBN` sont alignées à gauche.  
  
 [!code-xaml[ListViewHowTos#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml#1)]  
[!code-xaml[ListViewHowTos#2](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml#2)]  
  
 Pour modifier l’alignement de la colonne `ISBN`, vous devez spécifier que la propriété <xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A> de chaque <xref:System.Windows.Controls.ListViewItem> est <xref:System.Windows.HorizontalAlignment.Stretch>, afin que les éléments de chaque <xref:System.Windows.Controls.ListViewItem> puissent s’étendre ou être positionnés sur toute la largeur de chaque colonne. Étant donné que le <xref:System.Windows.Controls.ListView> est lié à une source de données, vous devez créer un style qui définit le <xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A>. Ensuite, vous devez utiliser un <xref:System.Windows.DataTemplate> pour afficher le contenu au lieu d’utiliser la propriété <xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A>. Pour afficher les `ISBN` de chaque modèle, le <xref:System.Windows.DataTemplate> peut simplement contenir un <xref:System.Windows.Controls.TextBlock> dont la propriété <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> a la valeur <xref:System.Windows.HorizontalAlignment.Right>.  
  
 L’exemple suivant définit le style et <xref:System.Windows.DataTemplate> nécessaire pour aligner la colonne `ISBN` à droite, et modifie le <xref:System.Windows.Controls.GridViewColumn> pour référencer le <xref:System.Windows.DataTemplate>.  
  
 [!code-xaml[ListViewHowTos#3](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml#3)]  
[!code-xaml[ListViewHowTos#4](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml#4)]  
  
## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble de la liaison de données](../../../desktop-wpf/data/data-binding-overview.md)
- [Vue d’ensemble des modèles de données](../data/data-templating-overview.md)
- [Effectuer une liaison à des données XML à l’aide d’un XMLDataProvider et de requêtes XPath](../data/how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md)
- [Vue d’ensemble de ListView](listview-overview.md)
