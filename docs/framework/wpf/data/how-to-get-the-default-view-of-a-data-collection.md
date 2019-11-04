---
title: "Comment : obtenir la vue par défaut d'une collection de données"
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data collections [WPF], creating views of
- data binding [WPF], creating views of data collections
ms.assetid: b641e96c-c2f6-42ea-9c5d-bac81176ad65
ms.openlocfilehash: e82d252ed82e4d2e6d641e8b60e890cc93bb0427
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459120"
---
# <a name="how-to-get-the-default-view-of-a-data-collection"></a>Comment : obtenir la vue par défaut d'une collection de données
Les vues permettent d’afficher la même collection de données de différentes façons, en fonction du tri, du filtrage ou des critères de regroupement. Chaque collection possède une vue partagée par défaut, qui est utilisée comme source de liaison réelle lorsqu’une liaison spécifie une collection comme source. Cet exemple montre comment obtenir la vue par défaut d’une collection.  
  
## <a name="example"></a>Exemple  
 Pour créer la vue, vous avez besoin d’une référence d’objet à la collection. Cet objet de données peut être obtenu en référençant votre propre objet code-behind, en obtenant le contexte de données, en obtenant une propriété de la source de données ou en obtenant une propriété de la liaison. Cet exemple montre comment obtenir la <xref:System.Windows.FrameworkElement.DataContext%2A> d’un objet de données et l’utiliser pour obtenir directement la vue de collection par défaut pour cette collection.  
  
 [!code-csharp[CollectionView#2](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionView/CSharp/Page1.xaml.cs#2)]
 [!code-vb[CollectionView#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CollectionView/VisualBasic/Page1.xaml.vb#2)]  
  
 Dans cet exemple, l’élément racine est un <xref:System.Windows.Controls.StackPanel>. La <xref:System.Windows.FrameworkElement.DataContext%2A> est définie sur *myDataSource*, qui fait référence à un fournisseur de données qui est un <xref:System.Collections.ObjectModel.ObservableCollection%601> d’objets de *commande* .  
  
 [!code-xaml[CollectionView#CollectionViewDataContext](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionView/CSharp/Page1.xaml#collectionviewdatacontext)]  
  
 Vous pouvez également instancier et lier votre propre vue de collection à l’aide de la classe <xref:System.Windows.Data.CollectionViewSource>. Cette vue de collection est partagée uniquement par les contrôles qui y sont liés directement. Pour obtenir un exemple, consultez la section How to Create a View dans la [vue d’ensemble](../../../desktop-wpf/data/data-binding-overview.md)de la liaison de données.  
  
 Pour obtenir des exemples des fonctionnalités offertes par une vue de collection, consultez [Trier des données dans une vue](how-to-sort-data-in-a-view.md), [Filtrer les données dans une vue](how-to-filter-data-in-a-view.md)et [naviguer parmi les objets dans un CollectionView de données](how-to-navigate-through-the-objects-in-a-data-collectionview.md).  
  
## <a name="see-also"></a>Voir aussi

- [Trier et grouper des données à l'aide d'une vue en XAML](how-to-sort-and-group-data-using-a-view-in-xaml.md)
- [Rubriques de guide pratique](data-binding-how-to-topics.md)
