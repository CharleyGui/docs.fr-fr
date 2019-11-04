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
# <a name="how-to-sort-data-in-a-view"></a><span data-ttu-id="87431-102">Comment : trier des données dans une vue</span><span class="sxs-lookup"><span data-stu-id="87431-102">How to: Sort Data in a View</span></span>
<span data-ttu-id="87431-103">Cet exemple décrit comment trier des données dans une vue.</span><span class="sxs-lookup"><span data-stu-id="87431-103">This example describes how to sort data in a view.</span></span>  
  
## <a name="example"></a><span data-ttu-id="87431-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="87431-104">Example</span></span>  
 <span data-ttu-id="87431-105">L’exemple suivant crée un <xref:System.Windows.Controls.ListBox> simple et un <xref:System.Windows.Controls.Button>:</span><span class="sxs-lookup"><span data-stu-id="87431-105">The following example creates a simple <xref:System.Windows.Controls.ListBox> and a <xref:System.Windows.Controls.Button>:</span></span>  
  
 [!code-xaml[ListBoxSort_snip#HowTo](~/samples/snippets/csharp/VS_Snippets_Wpf/ListBoxSort_snip/CSharp/Window1.xaml#howto)]  
  
 <span data-ttu-id="87431-106">Le gestionnaire d’événements <xref:System.Windows.Controls.Primitives.ButtonBase.Click> du bouton contient une logique permettant de trier les éléments de l' <xref:System.Windows.Controls.ListBox> dans l’ordre décroissant.</span><span class="sxs-lookup"><span data-stu-id="87431-106">The <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event handler of the button contains logic to sort the items in the <xref:System.Windows.Controls.ListBox> in the descending order.</span></span> <span data-ttu-id="87431-107">Vous pouvez effectuer cette opération, car l’ajout d’éléments à une <xref:System.Windows.Controls.ListBox> de cette manière les ajoute à la <xref:System.Windows.Controls.ItemCollection> du <xref:System.Windows.Controls.ListBox>et <xref:System.Windows.Controls.ItemCollection> dérive de la classe <xref:System.Windows.Data.CollectionView>.</span><span class="sxs-lookup"><span data-stu-id="87431-107">You can do this because adding items to a <xref:System.Windows.Controls.ListBox> this way adds them to the <xref:System.Windows.Controls.ItemCollection> of the <xref:System.Windows.Controls.ListBox>, and <xref:System.Windows.Controls.ItemCollection> derives from the <xref:System.Windows.Data.CollectionView> class.</span></span> <span data-ttu-id="87431-108">Si vous liez votre <xref:System.Windows.Controls.ListBox> à une collection à l’aide de la propriété <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>, vous pouvez utiliser la même technique pour le tri.</span><span class="sxs-lookup"><span data-stu-id="87431-108">If you are binding your <xref:System.Windows.Controls.ListBox> to a collection using the <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> property, you can use the same technique to sort.</span></span>  
  
 [!code-csharp[ListBoxSort_snip#HowToCode](~/samples/snippets/csharp/VS_Snippets_Wpf/ListBoxSort_snip/CSharp/Window1.xaml.cs#howtocode)]
 [!code-vb[ListBoxSort_snip#HowToCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ListBoxSort_snip/visualbasic/window1.xaml.vb#howtocode)]  
  
 <span data-ttu-id="87431-109">Tant que vous disposez d’une référence à l’objet de vue, vous pouvez utiliser la même technique pour trier le contenu d’autres affichages de collection.</span><span class="sxs-lookup"><span data-stu-id="87431-109">As long as you have a reference to the view object, you can use the same technique to sort the content of other collection views.</span></span> <span data-ttu-id="87431-110">Pour obtenir un exemple d’obtention d’une vue, consultez [obtenir la vue par défaut d’une collection de données](how-to-get-the-default-view-of-a-data-collection.md).</span><span class="sxs-lookup"><span data-stu-id="87431-110">For an example of how to obtain a view, see [Get the Default View of a Data Collection](how-to-get-the-default-view-of-a-data-collection.md).</span></span> <span data-ttu-id="87431-111">Pour un autre exemple, consultez [Trier une colonne GridView lors d’un clic sur un en-tête](../controls/how-to-sort-a-gridview-column-when-a-header-is-clicked.md).</span><span class="sxs-lookup"><span data-stu-id="87431-111">For another example, see [Sort a GridView Column When a Header Is Clicked](../controls/how-to-sort-a-gridview-column-when-a-header-is-clicked.md).</span></span> <span data-ttu-id="87431-112">Pour plus d’informations sur les affichages, consultez liaison à des collections dans [vue d’ensemble](../../../desktop-wpf/data/data-binding-overview.md)de la liaison de données.</span><span class="sxs-lookup"><span data-stu-id="87431-112">For more information about views, see Binding to Collections in [Data Binding Overview](../../../desktop-wpf/data/data-binding-overview.md).</span></span>  
  
 <span data-ttu-id="87431-113">Pour obtenir un exemple de la façon d’appliquer une logique de tri dans [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], consultez [Trier et grouper des données à l’aide d’une vue en XAML](how-to-sort-and-group-data-using-a-view-in-xaml.md).</span><span class="sxs-lookup"><span data-stu-id="87431-113">For an example of how to apply sorting logic in [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], see [Sort and Group Data Using a View in XAML](how-to-sort-and-group-data-using-a-view-in-xaml.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="87431-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="87431-114">See also</span></span>

- <xref:System.Windows.Data.ListCollectionView.CustomSort%2A>
- [<span data-ttu-id="87431-115">Trier une colonne GridView lors d’un clic sur un en-tête</span><span class="sxs-lookup"><span data-stu-id="87431-115">Sort a GridView Column When a Header Is Clicked</span></span>](../controls/how-to-sort-a-gridview-column-when-a-header-is-clicked.md)
- [<span data-ttu-id="87431-116">Vue d’ensemble de la liaison de données</span><span class="sxs-lookup"><span data-stu-id="87431-116">Data Binding Overview</span></span>](../../../desktop-wpf/data/data-binding-overview.md)
- [<span data-ttu-id="87431-117">Filtrer les données d’une vue</span><span class="sxs-lookup"><span data-stu-id="87431-117">Filter Data in a View</span></span>](how-to-filter-data-in-a-view.md)
- [<span data-ttu-id="87431-118">Rubriques de guide pratique</span><span class="sxs-lookup"><span data-stu-id="87431-118">How-to Topics</span></span>](data-binding-how-to-topics.md)
