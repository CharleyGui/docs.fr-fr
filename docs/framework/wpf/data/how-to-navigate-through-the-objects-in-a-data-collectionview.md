---
title: "Comment : naviguer dans les objets d'un CollectionView de données"
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- CollectionView [WPF], navigating through objects
- data binding [WPF], navigating through objects in data CollectionView
- navigating through objects in data CollectionView [WPF]
ms.assetid: fcd37590-bce1-4ac9-8b74-3b96c7458b8a
ms.openlocfilehash: 5ca386db89dcaa66d364d2ed7169c67393cebead
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459708"
---
# <a name="how-to-navigate-through-the-objects-in-a-data-collectionview"></a>Comment : naviguer dans les objets d'un CollectionView de données
Les vues permettent d’afficher la même collection de données de différentes façons, en fonction du tri, du filtrage ou du regroupement. Les vues fournissent également un concept de pointeur d’enregistrement actif et activent le déplacement du pointeur. Cet exemple montre comment obtenir l’objet actuel et parcourir les objets d’une collection de données à l’aide des fonctionnalités fournies dans la classe <xref:System.Windows.Data.CollectionView>.  
  
## <a name="example"></a>Exemple  
 Dans cet exemple, `myCollectionView` est un objet <xref:System.Windows.Data.CollectionView> qui est une vue sur une collection liée.  
  
 Dans l’exemple suivant, `OnButton` est un gestionnaire d’événements pour les boutons `Previous` et `Next` dans une application, qui sont des boutons qui permettent à l’utilisateur de naviguer dans la collection de données. Notez que les propriétés <xref:System.Windows.Data.CollectionView.IsCurrentBeforeFirst%2A> et <xref:System.Windows.Data.CollectionView.IsCurrentAfterLast%2A> indiquent si le pointeur d’enregistrement actuel est arrivé au début et à la fin de la liste, respectivement afin que <xref:System.Windows.Data.CollectionView.MoveCurrentToFirst%2A> et <xref:System.Windows.Data.CollectionView.MoveCurrentToLast%2A> puissent être appelées de manière appropriée.  
  
 La propriété <xref:System.Windows.Data.CollectionView.CurrentItem%2A> de la vue est convertie en `Order` pour retourner l’élément de commande actuel dans la collection.  
  
 [!code-csharp[CollectionView#OnButton](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionView/CSharp/Page1.xaml.cs#onbutton)]
 [!code-vb[CollectionView#OnButton](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CollectionView/VisualBasic/Page1.xaml.vb#onbutton)]  
  
## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble de la liaison de données](../../../desktop-wpf/data/data-binding-overview.md)
- [Trier des données dans une vue](how-to-sort-data-in-a-view.md)
- [Filtrer les données d’une vue](how-to-filter-data-in-a-view.md)
- [Trier et grouper des données à l'aide d'une vue en XAML](how-to-sort-and-group-data-using-a-view-in-xaml.md)
- [Rubriques de guide pratique](data-binding-how-to-topics.md)
