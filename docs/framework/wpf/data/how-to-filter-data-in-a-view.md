---
title: "Comment : filtrer les données d'une vue"
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- views [WPF], filtering data
- filtering data in views [WPF]
- data binding [WPF], filtering data in views
ms.assetid: c76e8606-4cc4-45a8-9110-e2ec66dc6afd
ms.openlocfilehash: ea49897ca5e9cb6b639cf7d98ff05bd287c51761
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73453483"
---
# <a name="how-to-filter-data-in-a-view"></a>Comment : filtrer les données d'une vue
Cet exemple montre comment filtrer des données dans une vue.  
  
## <a name="example"></a>Exemple  
 Pour créer un filtre, définissez une méthode qui fournit la logique de filtrage. La méthode est utilisée comme rappel et accepte un paramètre de type `object`. La méthode suivante retourne tous les objets `Order` avec la propriété `filled` définie sur « no », en filtrant le reste des objets.  
  
 [!code-csharp[SortFilter#2](~/samples/snippets/csharp/VS_Snippets_Wpf/SortFilter/CSharp/Page1.xaml.cs#2)]
 [!code-vb[SortFilter#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SortFilter/VisualBasic/Page1.xaml.vb#2)]  
  
 Vous pouvez ensuite appliquer le filtre, comme indiqué dans l’exemple suivant. Dans cet exemple, `myCollectionView` est un objet <xref:System.Windows.Data.ListCollectionView>.  
  
 [!code-csharp[SortFilter#Filter](~/samples/snippets/csharp/VS_Snippets_Wpf/SortFilter/CSharp/Page1.xaml.cs#filter)]
 [!code-vb[SortFilter#Filter](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SortFilter/VisualBasic/Page1.xaml.vb#filter)]  
  
 Pour annuler le filtrage, vous pouvez définir la propriété <xref:System.Windows.Data.CollectionView.Filter%2A> sur `null`:  
  
 [!code-csharp[SortFilter#Unfilter](~/samples/snippets/csharp/VS_Snippets_Wpf/SortFilter/CSharp/Page1.xaml.cs#unfilter)]
 [!code-vb[SortFilter#Unfilter](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SortFilter/VisualBasic/Page1.xaml.vb#unfilter)]  
  
 Pour plus d’informations sur la création ou l’obtention d’une vue, consultez [obtenir la vue par défaut d’une collection de données](how-to-get-the-default-view-of-a-data-collection.md). Pour obtenir un exemple complet, consultez [Tri et filtrage d’éléments dans un exemple d’affichage](https://go.microsoft.com/fwlink/?LinkID=160040).  
  
 Si votre objet de vue provient d’un objet <xref:System.Windows.Data.CollectionViewSource>, vous appliquez la logique de filtrage en définissant un gestionnaire d’événements pour l’événement <xref:System.Windows.Data.CollectionViewSource.Filter>. Dans l’exemple suivant, `listingDataView` est une instance de <xref:System.Windows.Data.CollectionViewSource>.  
  
 [!code-csharp[DataBindingLab#10](~/samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/MainWindow.xaml.cs#10)]
 [!code-vb[DataBindingLab#10](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataBindingLab/VisualBasic/MainWindow.xaml.vb#10)]  
  
 L’exemple suivant illustre l’implémentation de l’exemple de gestionnaire d’événements `ShowOnlyBargainsFilter` Filter. Ce gestionnaire d’événements utilise la propriété <xref:System.Windows.Data.FilterEventArgs.Accepted%2A> pour filtrer les objets `AuctionItem` ayant un `CurrentPrice` de $25 ou supérieur.  
  
 [!code-csharp[DataBindingLab#5](~/samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/MainWindow.xaml.cs#5)]
 [!code-vb[DataBindingLab#5](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataBindingLab/VisualBasic/MainWindow.xaml.vb#5)]  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Data.CollectionView.CanFilter%2A>
- <xref:System.Windows.Data.BindingListCollectionView.CustomFilter%2A>
- [Vue d’ensemble de la liaison de données](../../../desktop-wpf/data/data-binding-overview.md)
- [Trier des données dans une vue](how-to-sort-data-in-a-view.md)
- [Rubriques de guide pratique](data-binding-how-to-topics.md)
