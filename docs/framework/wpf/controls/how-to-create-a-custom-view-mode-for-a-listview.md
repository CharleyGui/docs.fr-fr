---
title: "Comment : créer un mode d'affichage personnalisé pour un ListView"
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ListView controls [WPF], creating custom View mode
ms.assetid: 71077349-eeb9-4344-ab29-b5df96df3314
ms.openlocfilehash: 3b9ca17bddcecb1895205fca76f0a489ecf25c4f
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/13/2020
ms.locfileid: "81243217"
---
# <a name="how-to-create-a-custom-view-mode-for-a-listview"></a><span data-ttu-id="43b23-102">Comment : Créer un mode de vue personnalisé pour un ListView</span><span class="sxs-lookup"><span data-stu-id="43b23-102">How to: Create a custom view mode for a ListView</span></span>

<span data-ttu-id="43b23-103">Cet exemple montre comment <xref:System.Windows.Controls.ListView.View%2A> créer un <xref:System.Windows.Controls.ListView> mode personnalisé pour un contrôle.</span><span class="sxs-lookup"><span data-stu-id="43b23-103">This example shows how to create a custom <xref:System.Windows.Controls.ListView.View%2A> mode for a <xref:System.Windows.Controls.ListView> control.</span></span>  
  
## <a name="example"></a><span data-ttu-id="43b23-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="43b23-104">Example</span></span>  
 <span data-ttu-id="43b23-105">Vous devez <xref:System.Windows.Controls.ViewBase> utiliser la classe lorsque vous <xref:System.Windows.Controls.ListView> créez une vue personnalisée pour le contrôle.</span><span class="sxs-lookup"><span data-stu-id="43b23-105">You must use the <xref:System.Windows.Controls.ViewBase> class when you create a custom view for the <xref:System.Windows.Controls.ListView> control.</span></span> <span data-ttu-id="43b23-106">L’exemple suivant montre `PlainView` un mode de <xref:System.Windows.Controls.ViewBase> vue appelé qui est dérivé de la classe.</span><span class="sxs-lookup"><span data-stu-id="43b23-106">The following example shows a view mode called `PlainView` that's derived from the <xref:System.Windows.Controls.ViewBase> class.</span></span>  
  
 [!code-csharp[ListViewCustomView#PlainView](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewCustomView/CSharp/PlainView.cs#plainview)]
 [!code-vb[ListViewCustomView#PlainView](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ListViewCustomView/visualbasic/plainview.vb#plainview)]  
  
 <span data-ttu-id="43b23-107">Pour appliquer un style à la <xref:System.Windows.Style> vue personnalisée, utilisez la classe.</span><span class="sxs-lookup"><span data-stu-id="43b23-107">To apply a style to the custom view, use the <xref:System.Windows.Style> class.</span></span> <span data-ttu-id="43b23-108">L’exemple suivant <xref:System.Windows.Style> définit `PlainView` un mode de vue pour le mode.</span><span class="sxs-lookup"><span data-stu-id="43b23-108">The following example defines a <xref:System.Windows.Style> for the `PlainView` view mode.</span></span> <span data-ttu-id="43b23-109">Dans l’exemple précédent, ce style est <xref:System.Windows.Controls.ViewBase.DefaultStyleKey%2A> défini comme la `PlainView`valeur de la propriété qui est définie pour .</span><span class="sxs-lookup"><span data-stu-id="43b23-109">In the previous example, this style is set as the value of the <xref:System.Windows.Controls.ViewBase.DefaultStyleKey%2A> property that's defined for `PlainView`.</span></span>  
  
 [!code-xaml[ListViewCustomView#PlainViewStyle](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewCustomView/CSharp/Themes/Generic.xaml#plainviewstyle)]  
  
 <span data-ttu-id="43b23-110">Pour définir la disposition des données dans <xref:System.Windows.DataTemplate> un mode de vue personnalisé, définissez un objet.</span><span class="sxs-lookup"><span data-stu-id="43b23-110">To define the layout of data in a custom view mode, define a <xref:System.Windows.DataTemplate> object.</span></span> <span data-ttu-id="43b23-111">L’exemple suivant <xref:System.Windows.DataTemplate> définit un qui peut être `PlainView` utilisé pour afficher les données en mode vue.</span><span class="sxs-lookup"><span data-stu-id="43b23-111">The following example defines a <xref:System.Windows.DataTemplate> that can be used to display data in the `PlainView` view mode.</span></span>  
  
 [!code-xaml[ListViewCustomView#PlainViewDataTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewCustomView/CSharp/Window1.xaml#plainviewdatatemplate)]  
  
 <span data-ttu-id="43b23-112">L’exemple suivant montre <xref:System.Windows.ResourceKey> comment `PlainView` définir un mode <xref:System.Windows.DataTemplate> de vue qui utilise celui qui est défini dans l’exemple précédent.</span><span class="sxs-lookup"><span data-stu-id="43b23-112">The following example shows how to define a <xref:System.Windows.ResourceKey> for the `PlainView` view mode that uses the <xref:System.Windows.DataTemplate> that is defined in the previous example.</span></span>  
  
 [!code-xaml[ListViewCustomView#PlainViewtileView](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewCustomView/CSharp/Window1.xaml#plainviewtileview)]  
  
 <span data-ttu-id="43b23-113">Un <xref:System.Windows.Controls.ListView> contrôle peut utiliser une vue <xref:System.Windows.Controls.ListView.View%2A> personnalisée si vous définissez la propriété à la clé de ressource.</span><span class="sxs-lookup"><span data-stu-id="43b23-113">A <xref:System.Windows.Controls.ListView> control can use a custom view if you set the <xref:System.Windows.Controls.ListView.View%2A> property to the resource key.</span></span> <span data-ttu-id="43b23-114">L’exemple suivant montre `PlainView` comment spécifier comme mode de vue pour un <xref:System.Windows.Controls.ListView>.</span><span class="sxs-lookup"><span data-stu-id="43b23-114">The following example shows how to specify `PlainView` as the view mode for a <xref:System.Windows.Controls.ListView>.</span></span>  
  
 [!code-csharp[ListViewCustomView#ListViewtileViewmode](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewCustomView/CSharp/Window1.xaml.cs#listviewtileviewmode)]
 [!code-vb[ListViewCustomView#ListViewtileViewmode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ListViewCustomView/visualbasic/window1.xaml.vb#listviewtileviewmode)]  
  
 <span data-ttu-id="43b23-115">Pour l’échantillon complet, voir [ListView with Multiple Views (C)](https://github.com/dotnet/docs/tree/master/samples/snippets/csharp/VS_Snippets_Wpf/ListViewCustomView/CSharp) ou [ListView with Multiple Views (Visual Basic)](https://github.com/dotnet/docs/tree/master/samples/snippets/visualbasic/VS_Snippets_Wpf/ListViewCustomView/visualbasic).</span><span class="sxs-lookup"><span data-stu-id="43b23-115">For the complete sample, see [ListView with Multiple Views (C#)](https://github.com/dotnet/docs/tree/master/samples/snippets/csharp/VS_Snippets_Wpf/ListViewCustomView/CSharp) or [ListView with Multiple Views (Visual Basic)](https://github.com/dotnet/docs/tree/master/samples/snippets/visualbasic/VS_Snippets_Wpf/ListViewCustomView/visualbasic).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="43b23-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="43b23-116">See also</span></span>

- <xref:System.Windows.Controls.ListView>
- <xref:System.Windows.Controls.GridView>
- [<span data-ttu-id="43b23-117">Rubriques de procédures</span><span class="sxs-lookup"><span data-stu-id="43b23-117">How-to Topics</span></span>](listview-how-to-topics.md)
- [<span data-ttu-id="43b23-118">Vue d’ensemble de ListView</span><span class="sxs-lookup"><span data-stu-id="43b23-118">ListView Overview</span></span>](listview-overview.md)
- [<span data-ttu-id="43b23-119">Vue d’ensemble de GridView</span><span class="sxs-lookup"><span data-stu-id="43b23-119">GridView Overview</span></span>](gridview-overview.md)
