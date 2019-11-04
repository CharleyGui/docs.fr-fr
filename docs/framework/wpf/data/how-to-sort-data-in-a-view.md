---
title: 'Comment : trier des données dans une vue'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data binding [WPF], sorting data in views
- data binding [WPF], grouping data in views
- grouping data in views [WPF]
- views [WPF], sorting data
- views [WPF], grouping data
- sorting data in views [WPF]
ms.assetid: f4c43578-01b7-4774-a953-acb95a13b94a
ms.openlocfilehash: 14314ed019f9194a657787bd767ae68615e94ac7
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73454827"
---
# <a name="how-to-sort-data-in-a-view"></a>Comment : trier des données dans une vue
Cet exemple décrit comment trier des données dans une vue.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant crée un <xref:System.Windows.Controls.ListBox> simple et un <xref:System.Windows.Controls.Button>:  
  
 [!code-xaml[ListBoxSort_snip#HowTo](~/samples/snippets/csharp/VS_Snippets_Wpf/ListBoxSort_snip/CSharp/Window1.xaml#howto)]  
  
 Le gestionnaire d’événements <xref:System.Windows.Controls.Primitives.ButtonBase.Click> du bouton contient une logique permettant de trier les éléments de l' <xref:System.Windows.Controls.ListBox> dans l’ordre décroissant. Vous pouvez effectuer cette opération, car l’ajout d’éléments à une <xref:System.Windows.Controls.ListBox> de cette manière les ajoute à la <xref:System.Windows.Controls.ItemCollection> du <xref:System.Windows.Controls.ListBox>et <xref:System.Windows.Controls.ItemCollection> dérive de la classe <xref:System.Windows.Data.CollectionView>. Si vous liez votre <xref:System.Windows.Controls.ListBox> à une collection à l’aide de la propriété <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>, vous pouvez utiliser la même technique pour le tri.  
  
 [!code-csharp[ListBoxSort_snip#HowToCode](~/samples/snippets/csharp/VS_Snippets_Wpf/ListBoxSort_snip/CSharp/Window1.xaml.cs#howtocode)]
 [!code-vb[ListBoxSort_snip#HowToCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ListBoxSort_snip/visualbasic/window1.xaml.vb#howtocode)]  
  
 Tant que vous disposez d’une référence à l’objet de vue, vous pouvez utiliser la même technique pour trier le contenu d’autres affichages de collection. Pour obtenir un exemple d’obtention d’une vue, consultez [obtenir la vue par défaut d’une collection de données](how-to-get-the-default-view-of-a-data-collection.md). Pour un autre exemple, consultez [Trier une colonne GridView lors d’un clic sur un en-tête](../controls/how-to-sort-a-gridview-column-when-a-header-is-clicked.md). Pour plus d’informations sur les affichages, consultez liaison à des collections dans [vue d’ensemble](../../../desktop-wpf/data/data-binding-overview.md)de la liaison de données.  
  
 Pour obtenir un exemple de la façon d’appliquer une logique de tri dans [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], consultez [Trier et grouper des données à l’aide d’une vue en XAML](how-to-sort-and-group-data-using-a-view-in-xaml.md).  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Data.ListCollectionView.CustomSort%2A>
- [Trier une colonne GridView lors d’un clic sur un en-tête](../controls/how-to-sort-a-gridview-column-when-a-header-is-clicked.md)
- [Vue d’ensemble de la liaison de données](../../../desktop-wpf/data/data-binding-overview.md)
- [Filtrer les données d’une vue](how-to-filter-data-in-a-view.md)
- [Rubriques de guide pratique](data-binding-how-to-topics.md)
