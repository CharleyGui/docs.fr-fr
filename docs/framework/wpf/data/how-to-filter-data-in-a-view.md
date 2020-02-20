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
ms.openlocfilehash: f15bcfd1e3c4175f8b4b97244f120d5edbdec9b8
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77453076"
---
# <a name="how-to-filter-data-in-a-view"></a><span data-ttu-id="77b63-102">Comment : filtrer les données d'une vue</span><span class="sxs-lookup"><span data-stu-id="77b63-102">How to: Filter Data in a View</span></span>
<span data-ttu-id="77b63-103">Cet exemple montre comment filtrer des données dans une vue.</span><span class="sxs-lookup"><span data-stu-id="77b63-103">This example shows how to filter data in a view.</span></span>  
  
## <a name="example"></a><span data-ttu-id="77b63-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="77b63-104">Example</span></span>  
 <span data-ttu-id="77b63-105">Pour créer un filtre, définissez une méthode qui fournit la logique de filtrage.</span><span class="sxs-lookup"><span data-stu-id="77b63-105">To create a filter, define a method that provides the filtering logic.</span></span> <span data-ttu-id="77b63-106">La méthode est utilisée comme rappel et accepte un paramètre de type `object`.</span><span class="sxs-lookup"><span data-stu-id="77b63-106">The method is used as a callback and accepts a parameter of type `object`.</span></span> <span data-ttu-id="77b63-107">La méthode suivante retourne tous les objets `Order` avec la propriété `filled` définie sur « no », en filtrant le reste des objets.</span><span class="sxs-lookup"><span data-stu-id="77b63-107">The following method returns all the `Order` objects with the `filled` property set to "No", filtering out the rest of the objects.</span></span>  
  
 [!code-csharp[SortFilter#2](~/samples/snippets/csharp/VS_Snippets_Wpf/SortFilter/CSharp/Page1.xaml.cs#2)]
 [!code-vb[SortFilter#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SortFilter/VisualBasic/Page1.xaml.vb#2)]  
  
 <span data-ttu-id="77b63-108">Vous pouvez ensuite appliquer le filtre, comme indiqué dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="77b63-108">You can then apply the filter, as shown in the following example.</span></span> <span data-ttu-id="77b63-109">Dans cet exemple, `myCollectionView` est un objet <xref:System.Windows.Data.ListCollectionView>.</span><span class="sxs-lookup"><span data-stu-id="77b63-109">In this example, `myCollectionView` is a <xref:System.Windows.Data.ListCollectionView> object.</span></span>  
  
 [!code-csharp[SortFilter#Filter](~/samples/snippets/csharp/VS_Snippets_Wpf/SortFilter/CSharp/Page1.xaml.cs#filter)]
 [!code-vb[SortFilter#Filter](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SortFilter/VisualBasic/Page1.xaml.vb#filter)]  
  
 <span data-ttu-id="77b63-110">Pour annuler le filtrage, vous pouvez définir la propriété <xref:System.Windows.Data.CollectionView.Filter%2A> sur `null`:</span><span class="sxs-lookup"><span data-stu-id="77b63-110">To undo filtering, you can set the <xref:System.Windows.Data.CollectionView.Filter%2A> property to `null`:</span></span>  
  
 [!code-csharp[SortFilter#Unfilter](~/samples/snippets/csharp/VS_Snippets_Wpf/SortFilter/CSharp/Page1.xaml.cs#unfilter)]
 [!code-vb[SortFilter#Unfilter](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SortFilter/VisualBasic/Page1.xaml.vb#unfilter)]  
  
 <span data-ttu-id="77b63-111">Pour plus d’informations sur la création ou l’obtention d’une vue, consultez [obtenir la vue par défaut d’une collection de données](how-to-get-the-default-view-of-a-data-collection.md).</span><span class="sxs-lookup"><span data-stu-id="77b63-111">For information about how to create or obtain a view, see [Get the Default View of a Data Collection](how-to-get-the-default-view-of-a-data-collection.md).</span></span> <span data-ttu-id="77b63-112">Pour obtenir un exemple complet, consultez [Tri et filtrage d’éléments dans un exemple d’affichage](https://github.com/Microsoft/WPF-Samples/tree/master/Data%20Binding/SortFilter).</span><span class="sxs-lookup"><span data-stu-id="77b63-112">For the complete example, see [Sorting and Filtering Items in a View Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Data%20Binding/SortFilter).</span></span>  
  
 <span data-ttu-id="77b63-113">Si votre objet de vue provient d’un objet <xref:System.Windows.Data.CollectionViewSource>, vous appliquez la logique de filtrage en définissant un gestionnaire d’événements pour l’événement <xref:System.Windows.Data.CollectionViewSource.Filter>.</span><span class="sxs-lookup"><span data-stu-id="77b63-113">If your view object comes from a <xref:System.Windows.Data.CollectionViewSource> object, you apply filtering logic by setting an event handler for the <xref:System.Windows.Data.CollectionViewSource.Filter> event.</span></span> <span data-ttu-id="77b63-114">Dans l’exemple suivant, `listingDataView` est une instance de <xref:System.Windows.Data.CollectionViewSource>.</span><span class="sxs-lookup"><span data-stu-id="77b63-114">In the following example, `listingDataView` is an instance of <xref:System.Windows.Data.CollectionViewSource>.</span></span>  
  
 [!code-csharp[DataBindingLab#10](~/samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/MainWindow.xaml.cs#10)]
 [!code-vb[DataBindingLab#10](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataBindingLab/VisualBasic/MainWindow.xaml.vb#10)]  
  
 <span data-ttu-id="77b63-115">L’exemple suivant illustre l’implémentation de l’exemple de gestionnaire d’événements `ShowOnlyBargainsFilter` Filter.</span><span class="sxs-lookup"><span data-stu-id="77b63-115">The following shows the implementation of the example `ShowOnlyBargainsFilter` filter event handler.</span></span> <span data-ttu-id="77b63-116">Ce gestionnaire d’événements utilise la propriété <xref:System.Windows.Data.FilterEventArgs.Accepted%2A> pour filtrer les objets `AuctionItem` ayant un `CurrentPrice` de $25 ou supérieur.</span><span class="sxs-lookup"><span data-stu-id="77b63-116">This event handler uses the <xref:System.Windows.Data.FilterEventArgs.Accepted%2A> property to filter out `AuctionItem` objects that have a `CurrentPrice` of $25 or greater.</span></span>  
  
 [!code-csharp[DataBindingLab#5](~/samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/MainWindow.xaml.cs#5)]
 [!code-vb[DataBindingLab#5](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataBindingLab/VisualBasic/MainWindow.xaml.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="77b63-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="77b63-117">See also</span></span>

- <xref:System.Windows.Data.CollectionView.CanFilter%2A>
- <xref:System.Windows.Data.BindingListCollectionView.CustomFilter%2A>
- [<span data-ttu-id="77b63-118">Vue d’ensemble de la liaison de données</span><span class="sxs-lookup"><span data-stu-id="77b63-118">Data Binding Overview</span></span>](../../../desktop-wpf/data/data-binding-overview.md)
- [<span data-ttu-id="77b63-119">Trier des données dans une vue</span><span class="sxs-lookup"><span data-stu-id="77b63-119">Sort Data in a View</span></span>](how-to-sort-data-in-a-view.md)
- [<span data-ttu-id="77b63-120">Rubriques Comment</span><span class="sxs-lookup"><span data-stu-id="77b63-120">How-to Topics</span></span>](data-binding-how-to-topics.md)
