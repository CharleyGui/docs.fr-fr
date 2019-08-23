---
title: 'Procédure : Gérer l’événement MouseDoubleClick pour chaque élément d’un ListView'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ListView controls [WPF], MouseDoubleClick event
ms.assetid: 81b39369-655a-4585-ac58-4640e5bb8fed
ms.openlocfilehash: 7e51c810a2e1e4bf4157aa1311255c5547021b60
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69962060"
---
# <a name="how-to-handle-the-mousedoubleclick-event-for-each-item-in-a-listview"></a><span data-ttu-id="437f5-102">Procédure : Gérer l’événement MouseDoubleClick pour chaque élément d’un ListView</span><span class="sxs-lookup"><span data-stu-id="437f5-102">How to: Handle the MouseDoubleClick Event for Each Item in a ListView</span></span>
<span data-ttu-id="437f5-103">Pour gérer un événement pour un élément dans un <xref:System.Windows.Controls.ListView>, vous devez ajouter un gestionnaire d’événements à chacun <xref:System.Windows.Controls.ListViewItem>.</span><span class="sxs-lookup"><span data-stu-id="437f5-103">To handle an event for an item in a <xref:System.Windows.Controls.ListView>, you need to add an event handler to each <xref:System.Windows.Controls.ListViewItem>.</span></span> <span data-ttu-id="437f5-104">Quand un <xref:System.Windows.Controls.ListView> est lié à une source de données, vous ne créez pas <xref:System.Windows.Controls.ListViewItem>explicitement un, mais vous pouvez gérer l’événement pour chaque élément en <xref:System.Windows.EventSetter> ajoutant un à un style <xref:System.Windows.Controls.ListViewItem>de.</span><span class="sxs-lookup"><span data-stu-id="437f5-104">When a <xref:System.Windows.Controls.ListView> is bound to a data source, you don't explicitly create a <xref:System.Windows.Controls.ListViewItem>, but you can handle the event for each item by adding an <xref:System.Windows.EventSetter> to a style of a <xref:System.Windows.Controls.ListViewItem>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="437f5-105">Exemple</span><span class="sxs-lookup"><span data-stu-id="437f5-105">Example</span></span>  
 <span data-ttu-id="437f5-106">L’exemple suivant crée un lié <xref:System.Windows.Controls.ListView> aux données et crée un <xref:System.Windows.Style> pour ajouter un gestionnaire d’événements à chacun. <xref:System.Windows.Controls.ListViewItem></span><span class="sxs-lookup"><span data-stu-id="437f5-106">The following example creates a data-bound <xref:System.Windows.Controls.ListView> and creates a <xref:System.Windows.Style> to add an event handler to each <xref:System.Windows.Controls.ListViewItem>.</span></span>  
  
 [!code-xaml[ListViewHowTos#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml#1)]  
[!code-xaml[ListViewHowTos#5](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml#5)]  
[!code-xaml[ListViewHowTos#2](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml#2)]  
  
 <span data-ttu-id="437f5-107">L’exemple suivant gère l' <xref:System.Windows.Controls.Control.MouseDoubleClick> événement.</span><span class="sxs-lookup"><span data-stu-id="437f5-107">The following example handles the <xref:System.Windows.Controls.Control.MouseDoubleClick> event.</span></span>  
  
 [!code-csharp[ListViewHowTos#6](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml.cs#6)]
 [!code-vb[ListViewHowTos#6](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ListViewHowTos/VisualBasic/Window1.xaml.vb#6)]  
  
> [!NOTE]
> <span data-ttu-id="437f5-108">Bien qu’il soit plus courant de lier <xref:System.Windows.Controls.ListView> un à une source de données, vous pouvez utiliser un style pour ajouter un gestionnaire d' <xref:System.Windows.Controls.ListViewItem> événements à chaque dans un non lié <xref:System.Windows.Controls.ListView> aux données, que vous ayez ou <xref:System.Windows.Controls.ListViewItem>non explicitement créé un.</span><span class="sxs-lookup"><span data-stu-id="437f5-108">Although it is most common to bind a <xref:System.Windows.Controls.ListView> to a data source, you can use a style to add an event handler to each <xref:System.Windows.Controls.ListViewItem> in a non-data-bound <xref:System.Windows.Controls.ListView> regardless of whether you explicitly create a <xref:System.Windows.Controls.ListViewItem>.</span></span>  <span data-ttu-id="437f5-109">Pour plus d’informations sur les contrôles créés <xref:System.Windows.Controls.ListViewItem> explicitement et implicitement, consultez. <xref:System.Windows.Controls.ItemsControl></span><span class="sxs-lookup"><span data-stu-id="437f5-109">For more information about explicitly and implicitly created <xref:System.Windows.Controls.ListViewItem> controls, see <xref:System.Windows.Controls.ItemsControl>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="437f5-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="437f5-110">See also</span></span>

- <xref:System.Xml.XmlElement>
- [<span data-ttu-id="437f5-111">Vue d’ensemble de la liaison de données</span><span class="sxs-lookup"><span data-stu-id="437f5-111">Data Binding Overview</span></span>](../data/data-binding-overview.md)
- [<span data-ttu-id="437f5-112">Application d’un style et création de modèles</span><span class="sxs-lookup"><span data-stu-id="437f5-112">Styling and Templating</span></span>](styling-and-templating.md)
- [<span data-ttu-id="437f5-113">Effectuer une liaison à des données XML à l’aide d’un XMLDataProvider et de requêtes XPath</span><span class="sxs-lookup"><span data-stu-id="437f5-113">Bind to XML Data Using an XMLDataProvider and XPath Queries</span></span>](../data/how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md)
- [<span data-ttu-id="437f5-114">Vue d’ensemble de ListView</span><span class="sxs-lookup"><span data-stu-id="437f5-114">ListView Overview</span></span>](listview-overview.md)
