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
# <a name="how-to-get-the-default-view-of-a-data-collection"></a><span data-ttu-id="f2ad7-102">Comment : obtenir la vue par défaut d'une collection de données</span><span class="sxs-lookup"><span data-stu-id="f2ad7-102">How to: Get the Default View of a Data Collection</span></span>
<span data-ttu-id="f2ad7-103">Les vues permettent d’afficher la même collection de données de différentes façons, en fonction du tri, du filtrage ou des critères de regroupement.</span><span class="sxs-lookup"><span data-stu-id="f2ad7-103">Views allow the same data collection to be viewed in different ways, depending on sorting, filtering, or grouping criteria.</span></span> <span data-ttu-id="f2ad7-104">Chaque collection possède une vue partagée par défaut, qui est utilisée comme source de liaison réelle lorsqu’une liaison spécifie une collection comme source.</span><span class="sxs-lookup"><span data-stu-id="f2ad7-104">Every collection has one shared default view, which is used as the actual binding source when a binding specifies a collection as its source.</span></span> <span data-ttu-id="f2ad7-105">Cet exemple montre comment obtenir la vue par défaut d’une collection.</span><span class="sxs-lookup"><span data-stu-id="f2ad7-105">This example shows how to get the default view of a collection.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f2ad7-106">Exemple</span><span class="sxs-lookup"><span data-stu-id="f2ad7-106">Example</span></span>  
 <span data-ttu-id="f2ad7-107">Pour créer la vue, vous avez besoin d’une référence d’objet à la collection.</span><span class="sxs-lookup"><span data-stu-id="f2ad7-107">To create the view, you need an object reference to the collection.</span></span> <span data-ttu-id="f2ad7-108">Cet objet de données peut être obtenu en référençant votre propre objet code-behind, en obtenant le contexte de données, en obtenant une propriété de la source de données ou en obtenant une propriété de la liaison.</span><span class="sxs-lookup"><span data-stu-id="f2ad7-108">This data object can be obtained by referencing your own code-behind object, by getting the data context, by getting a property of the data source, or by getting a property of the binding.</span></span> <span data-ttu-id="f2ad7-109">Cet exemple montre comment obtenir la <xref:System.Windows.FrameworkElement.DataContext%2A> d’un objet de données et l’utiliser pour obtenir directement la vue de collection par défaut pour cette collection.</span><span class="sxs-lookup"><span data-stu-id="f2ad7-109">This example shows how to get the <xref:System.Windows.FrameworkElement.DataContext%2A> of a data object and use it to directly obtain the default collection view for this collection.</span></span>  
  
 [!code-csharp[CollectionView#2](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionView/CSharp/Page1.xaml.cs#2)]
 [!code-vb[CollectionView#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CollectionView/VisualBasic/Page1.xaml.vb#2)]  
  
 <span data-ttu-id="f2ad7-110">Dans cet exemple, l’élément racine est un <xref:System.Windows.Controls.StackPanel>.</span><span class="sxs-lookup"><span data-stu-id="f2ad7-110">In this example, the root element is a <xref:System.Windows.Controls.StackPanel>.</span></span> <span data-ttu-id="f2ad7-111">La <xref:System.Windows.FrameworkElement.DataContext%2A> est définie sur *myDataSource*, qui fait référence à un fournisseur de données qui est un <xref:System.Collections.ObjectModel.ObservableCollection%601> d’objets de *commande* .</span><span class="sxs-lookup"><span data-stu-id="f2ad7-111">The <xref:System.Windows.FrameworkElement.DataContext%2A> is set to *myDataSource*, which refers to a data provider that is an <xref:System.Collections.ObjectModel.ObservableCollection%601> of *Order* objects.</span></span>  
  
 [!code-xaml[CollectionView#CollectionViewDataContext](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionView/CSharp/Page1.xaml#collectionviewdatacontext)]  
  
 <span data-ttu-id="f2ad7-112">Vous pouvez également instancier et lier votre propre vue de collection à l’aide de la classe <xref:System.Windows.Data.CollectionViewSource>.</span><span class="sxs-lookup"><span data-stu-id="f2ad7-112">Alternatively, you can instantiate and bind to your own collection view using the <xref:System.Windows.Data.CollectionViewSource> class.</span></span> <span data-ttu-id="f2ad7-113">Cette vue de collection est partagée uniquement par les contrôles qui y sont liés directement.</span><span class="sxs-lookup"><span data-stu-id="f2ad7-113">This collection view is only shared by controls that bind to it directly.</span></span> <span data-ttu-id="f2ad7-114">Pour obtenir un exemple, consultez la section How to Create a View dans la [vue d’ensemble](../../../desktop-wpf/data/data-binding-overview.md)de la liaison de données.</span><span class="sxs-lookup"><span data-stu-id="f2ad7-114">For an example, see the How to Create a View section in the [Data Binding Overview](../../../desktop-wpf/data/data-binding-overview.md).</span></span>  
  
 <span data-ttu-id="f2ad7-115">Pour obtenir des exemples des fonctionnalités offertes par une vue de collection, consultez [Trier des données dans une vue](how-to-sort-data-in-a-view.md), [Filtrer les données dans une vue](how-to-filter-data-in-a-view.md)et [naviguer parmi les objets dans un CollectionView de données](how-to-navigate-through-the-objects-in-a-data-collectionview.md).</span><span class="sxs-lookup"><span data-stu-id="f2ad7-115">For examples of the functionality provided by a collection view, see [Sort Data in a View](how-to-sort-data-in-a-view.md), [Filter Data in a View](how-to-filter-data-in-a-view.md), and [Navigate Through the Objects in a Data CollectionView](how-to-navigate-through-the-objects-in-a-data-collectionview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f2ad7-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f2ad7-116">See also</span></span>

- [<span data-ttu-id="f2ad7-117">Trier et grouper des données à l'aide d'une vue en XAML</span><span class="sxs-lookup"><span data-stu-id="f2ad7-117">Sort and Group Data Using a View in XAML</span></span>](how-to-sort-and-group-data-using-a-view-in-xaml.md)
- [<span data-ttu-id="f2ad7-118">Rubriques de guide pratique</span><span class="sxs-lookup"><span data-stu-id="f2ad7-118">How-to Topics</span></span>](data-binding-how-to-topics.md)
