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
# <a name="how-to-navigate-through-the-objects-in-a-data-collectionview"></a><span data-ttu-id="ab662-102">Comment : naviguer dans les objets d'un CollectionView de données</span><span class="sxs-lookup"><span data-stu-id="ab662-102">How to: Navigate Through the Objects in a Data CollectionView</span></span>
<span data-ttu-id="ab662-103">Les vues permettent d’afficher la même collection de données de différentes façons, en fonction du tri, du filtrage ou du regroupement.</span><span class="sxs-lookup"><span data-stu-id="ab662-103">Views allow the same data collection to be viewed in different ways, depending on sorting, filtering, or grouping.</span></span> <span data-ttu-id="ab662-104">Les vues fournissent également un concept de pointeur d’enregistrement actif et activent le déplacement du pointeur.</span><span class="sxs-lookup"><span data-stu-id="ab662-104">Views also provide a current record pointer concept and enable moving the pointer.</span></span> <span data-ttu-id="ab662-105">Cet exemple montre comment obtenir l’objet actuel et parcourir les objets d’une collection de données à l’aide des fonctionnalités fournies dans la classe <xref:System.Windows.Data.CollectionView>.</span><span class="sxs-lookup"><span data-stu-id="ab662-105">This example shows how to get the current object as well as navigate through the objects in a data collection using the functionality provided in the <xref:System.Windows.Data.CollectionView> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ab662-106">Exemple</span><span class="sxs-lookup"><span data-stu-id="ab662-106">Example</span></span>  
 <span data-ttu-id="ab662-107">Dans cet exemple, `myCollectionView` est un objet <xref:System.Windows.Data.CollectionView> qui est une vue sur une collection liée.</span><span class="sxs-lookup"><span data-stu-id="ab662-107">In this example, `myCollectionView` is a <xref:System.Windows.Data.CollectionView> object that is a view over a bound collection.</span></span>  
  
 <span data-ttu-id="ab662-108">Dans l’exemple suivant, `OnButton` est un gestionnaire d’événements pour les boutons `Previous` et `Next` dans une application, qui sont des boutons qui permettent à l’utilisateur de naviguer dans la collection de données.</span><span class="sxs-lookup"><span data-stu-id="ab662-108">In the following example, `OnButton` is an event handler for the `Previous` and `Next` buttons in an application, which are buttons that allow the user to navigate the data collection.</span></span> <span data-ttu-id="ab662-109">Notez que les propriétés <xref:System.Windows.Data.CollectionView.IsCurrentBeforeFirst%2A> et <xref:System.Windows.Data.CollectionView.IsCurrentAfterLast%2A> indiquent si le pointeur d’enregistrement actuel est arrivé au début et à la fin de la liste, respectivement afin que <xref:System.Windows.Data.CollectionView.MoveCurrentToFirst%2A> et <xref:System.Windows.Data.CollectionView.MoveCurrentToLast%2A> puissent être appelées de manière appropriée.</span><span class="sxs-lookup"><span data-stu-id="ab662-109">Note that the <xref:System.Windows.Data.CollectionView.IsCurrentBeforeFirst%2A> and <xref:System.Windows.Data.CollectionView.IsCurrentAfterLast%2A> properties report whether the current record pointer has come to the beginning and the end of the list respectively so that <xref:System.Windows.Data.CollectionView.MoveCurrentToFirst%2A> and <xref:System.Windows.Data.CollectionView.MoveCurrentToLast%2A> can be called as appropriately.</span></span>  
  
 <span data-ttu-id="ab662-110">La propriété <xref:System.Windows.Data.CollectionView.CurrentItem%2A> de la vue est convertie en `Order` pour retourner l’élément de commande actuel dans la collection.</span><span class="sxs-lookup"><span data-stu-id="ab662-110">The <xref:System.Windows.Data.CollectionView.CurrentItem%2A> property of the view is cast as an `Order` to return the current order item in the collection.</span></span>  
  
 [!code-csharp[CollectionView#OnButton](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionView/CSharp/Page1.xaml.cs#onbutton)]
 [!code-vb[CollectionView#OnButton](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CollectionView/VisualBasic/Page1.xaml.vb#onbutton)]  
  
## <a name="see-also"></a><span data-ttu-id="ab662-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ab662-111">See also</span></span>

- [<span data-ttu-id="ab662-112">Vue d’ensemble de la liaison de données</span><span class="sxs-lookup"><span data-stu-id="ab662-112">Data Binding Overview</span></span>](../../../desktop-wpf/data/data-binding-overview.md)
- [<span data-ttu-id="ab662-113">Trier des données dans une vue</span><span class="sxs-lookup"><span data-stu-id="ab662-113">Sort Data in a View</span></span>](how-to-sort-data-in-a-view.md)
- [<span data-ttu-id="ab662-114">Filtrer les données d’une vue</span><span class="sxs-lookup"><span data-stu-id="ab662-114">Filter Data in a View</span></span>](how-to-filter-data-in-a-view.md)
- [<span data-ttu-id="ab662-115">Trier et grouper des données à l'aide d'une vue en XAML</span><span class="sxs-lookup"><span data-stu-id="ab662-115">Sort and Group Data Using a View in XAML</span></span>](how-to-sort-and-group-data-using-a-view-in-xaml.md)
- [<span data-ttu-id="ab662-116">Rubriques de guide pratique</span><span class="sxs-lookup"><span data-stu-id="ab662-116">How-to Topics</span></span>](data-binding-how-to-topics.md)
