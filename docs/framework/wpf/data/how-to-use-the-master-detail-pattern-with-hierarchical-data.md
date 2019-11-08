---
title: 'Comment : utiliser le modèle maître/détail avec des données hiérarchiques'
ms.date: 03/30/2017
helpviewer_keywords:
- data binding [WPF], Master-Detail data paradigm
- Master-Detail data paradigm
ms.assetid: 11429b9e-058d-4084-bfb6-2cf209c8ddf7
ms.openlocfilehash: e4183ddc3868a1568662853b46e05348df129092
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73733485"
---
# <a name="how-to-use-the-master-detail-pattern-with-hierarchical-data"></a><span data-ttu-id="1d621-102">Comment : utiliser le modèle maître/détail avec des données hiérarchiques</span><span class="sxs-lookup"><span data-stu-id="1d621-102">How to: Use the Master-Detail Pattern with Hierarchical Data</span></span>
<span data-ttu-id="1d621-103">Cet exemple montre comment implémenter le scénario maître/détail.</span><span class="sxs-lookup"><span data-stu-id="1d621-103">This example shows how to implement the master-detail scenario.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1d621-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="1d621-104">Example</span></span>  
 <span data-ttu-id="1d621-105">Dans cet exemple, `LeagueList` est une collection de `Leagues`.</span><span class="sxs-lookup"><span data-stu-id="1d621-105">In this example, `LeagueList` is a collection of `Leagues`.</span></span> <span data-ttu-id="1d621-106">Chaque `League` a un `Name` et une collection d' `Divisions`, et chaque `Division` a un nom et une collection d' `Teams`.</span><span class="sxs-lookup"><span data-stu-id="1d621-106">Each `League` has a `Name` and a collection of `Divisions`, and each `Division` has a name and a collection of `Teams`.</span></span> <span data-ttu-id="1d621-107">Chaque `Team` a un nom d’équipe.</span><span class="sxs-lookup"><span data-stu-id="1d621-107">Each `Team` has a team name.</span></span>  
  
 [!code-xaml[MasterDetail#HowTo1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MasterDetail/VisualBasic/Page1.xaml#howto1)]  
[!code-xaml[MasterDetail#HowTo2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MasterDetail/VisualBasic/Page1.xaml#howto2)]  
  
 <span data-ttu-id="1d621-108">Voici une capture d’écran de l’exemple.</span><span class="sxs-lookup"><span data-stu-id="1d621-108">The following is a screenshot of the example.</span></span> <span data-ttu-id="1d621-109">Le `Divisions` <xref:System.Windows.Controls.ListBox> effectue automatiquement le suivi des sélections dans le <xref:System.Windows.Controls.ListBox> de `Leagues` et affiche les données correspondantes.</span><span class="sxs-lookup"><span data-stu-id="1d621-109">The `Divisions` <xref:System.Windows.Controls.ListBox> automatically tracks selections in the `Leagues` <xref:System.Windows.Controls.ListBox> and display the corresponding data.</span></span> <span data-ttu-id="1d621-110">Le `Teams` <xref:System.Windows.Controls.ListBox> effectue le suivi des sélections dans les deux autres contrôles <xref:System.Windows.Controls.ListBox>.</span><span class="sxs-lookup"><span data-stu-id="1d621-110">The `Teams` <xref:System.Windows.Controls.ListBox> tracks selections in the other two <xref:System.Windows.Controls.ListBox> controls.</span></span>  
  
 ![Capture d’écran montrant un&#45;exemple de scénario maître détaillé.](./media/how-to-use-the-master-detail-pattern-with-hierarchical-data/databinding-master-detail-scenario.png)  
  
 <span data-ttu-id="1d621-112">Les deux points à noter dans cet exemple sont les suivants :</span><span class="sxs-lookup"><span data-stu-id="1d621-112">The two things to notice in this example are:</span></span>  
  
1. <span data-ttu-id="1d621-113">Les trois contrôles <xref:System.Windows.Controls.ListBox> sont liés à la même source.</span><span class="sxs-lookup"><span data-stu-id="1d621-113">The three <xref:System.Windows.Controls.ListBox> controls bind to the same source.</span></span> <span data-ttu-id="1d621-114">Vous définissez la propriété <xref:System.Windows.Data.Binding.Path%2A> de la liaison pour spécifier le niveau de données que vous souhaitez que le <xref:System.Windows.Controls.ListBox> affiche.</span><span class="sxs-lookup"><span data-stu-id="1d621-114">You set the <xref:System.Windows.Data.Binding.Path%2A> property of the binding to specify which level of data you want the <xref:System.Windows.Controls.ListBox> to display.</span></span>  
  
2. <span data-ttu-id="1d621-115">Vous devez définir la propriété <xref:System.Windows.Controls.Primitives.Selector.IsSynchronizedWithCurrentItem%2A> sur `true` sur les contrôles <xref:System.Windows.Controls.ListBox> dont vous effectuez le suivi.</span><span class="sxs-lookup"><span data-stu-id="1d621-115">You must set the <xref:System.Windows.Controls.Primitives.Selector.IsSynchronizedWithCurrentItem%2A> property to `true` on the <xref:System.Windows.Controls.ListBox> controls of which the selection you are tracking.</span></span> <span data-ttu-id="1d621-116">La définition de cette propriété permet de s’assurer que l’élément sélectionné est toujours défini en tant que <xref:System.Windows.Controls.ItemCollection.CurrentItem%2A>.</span><span class="sxs-lookup"><span data-stu-id="1d621-116">Setting this property ensures that the selected item is always set as the <xref:System.Windows.Controls.ItemCollection.CurrentItem%2A>.</span></span> <span data-ttu-id="1d621-117">Sinon, si le <xref:System.Windows.Controls.ListBox> obtient des données à partir d’un <xref:System.Windows.Data.CollectionViewSource>, il synchronise automatiquement la sélection et la devise.</span><span class="sxs-lookup"><span data-stu-id="1d621-117">Alternatively, if the <xref:System.Windows.Controls.ListBox> gets it data from a <xref:System.Windows.Data.CollectionViewSource>, it synchronizes selection and currency automatically.</span></span>  
  
 <span data-ttu-id="1d621-118">La technique est légèrement différente quand vous utilisez des données XML.</span><span class="sxs-lookup"><span data-stu-id="1d621-118">The technique is slightly different when you are using XML data.</span></span> <span data-ttu-id="1d621-119">Pour obtenir un exemple, consultez [utiliser le modèle maître/détail avec des données XML hiérarchiques](how-to-use-the-master-detail-pattern-with-hierarchical-xml-data.md).</span><span class="sxs-lookup"><span data-stu-id="1d621-119">For an example, see [Use the Master-Detail Pattern with Hierarchical XML Data](how-to-use-the-master-detail-pattern-with-hierarchical-xml-data.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1d621-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1d621-120">See also</span></span>

- <xref:System.Windows.HierarchicalDataTemplate>
- [<span data-ttu-id="1d621-121">Effectuer une liaison à une collection et afficher des informations basées sur la sélection</span><span class="sxs-lookup"><span data-stu-id="1d621-121">Bind to a Collection and Display Information Based on Selection</span></span>](how-to-bind-to-a-collection-and-display-information-based-on-selection.md)
- [<span data-ttu-id="1d621-122">Vue d’ensemble de la liaison de données</span><span class="sxs-lookup"><span data-stu-id="1d621-122">Data Binding Overview</span></span>](../../../desktop-wpf/data/data-binding-overview.md)
- [<span data-ttu-id="1d621-123">Vue d’ensemble des modèles de données</span><span class="sxs-lookup"><span data-stu-id="1d621-123">Data Templating Overview</span></span>](data-templating-overview.md)
- [<span data-ttu-id="1d621-124">Rubriques de guide pratique</span><span class="sxs-lookup"><span data-stu-id="1d621-124">How-to Topics</span></span>](data-binding-how-to-topics.md)
