---
title: "Comment : gérer l'événement MouseDoubleClick pour chaque élément d'un ListView"
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ListView controls [WPF], MouseDoubleClick event
ms.assetid: 81b39369-655a-4585-ac58-4640e5bb8fed
ms.openlocfilehash: 25308ee87fb387787e20c8a8887ae8e4e60742b9
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73460230"
---
# <a name="how-to-handle-the-mousedoubleclick-event-for-each-item-in-a-listview"></a><span data-ttu-id="6f0e6-102">Comment : gérer l'événement MouseDoubleClick pour chaque élément d'un ListView</span><span class="sxs-lookup"><span data-stu-id="6f0e6-102">How to: Handle the MouseDoubleClick Event for Each Item in a ListView</span></span>
<span data-ttu-id="6f0e6-103">Pour gérer un événement pour un élément dans un <xref:System.Windows.Controls.ListView>, vous devez ajouter un gestionnaire d’événements à chaque <xref:System.Windows.Controls.ListViewItem>.</span><span class="sxs-lookup"><span data-stu-id="6f0e6-103">To handle an event for an item in a <xref:System.Windows.Controls.ListView>, you need to add an event handler to each <xref:System.Windows.Controls.ListViewItem>.</span></span> <span data-ttu-id="6f0e6-104">Lorsqu’un <xref:System.Windows.Controls.ListView> est lié à une source de données, vous ne créez pas explicitement de <xref:System.Windows.Controls.ListViewItem>, mais vous pouvez gérer l’événement pour chaque élément en ajoutant un <xref:System.Windows.EventSetter> à un style de <xref:System.Windows.Controls.ListViewItem>.</span><span class="sxs-lookup"><span data-stu-id="6f0e6-104">When a <xref:System.Windows.Controls.ListView> is bound to a data source, you don't explicitly create a <xref:System.Windows.Controls.ListViewItem>, but you can handle the event for each item by adding an <xref:System.Windows.EventSetter> to a style of a <xref:System.Windows.Controls.ListViewItem>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6f0e6-105">Exemple</span><span class="sxs-lookup"><span data-stu-id="6f0e6-105">Example</span></span>  
 <span data-ttu-id="6f0e6-106">L’exemple suivant crée un <xref:System.Windows.Controls.ListView> lié aux données et crée un <xref:System.Windows.Style> pour ajouter un gestionnaire d’événements à chaque <xref:System.Windows.Controls.ListViewItem>.</span><span class="sxs-lookup"><span data-stu-id="6f0e6-106">The following example creates a data-bound <xref:System.Windows.Controls.ListView> and creates a <xref:System.Windows.Style> to add an event handler to each <xref:System.Windows.Controls.ListViewItem>.</span></span>  
  
 [!code-xaml[ListViewHowTos#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml#1)]  
[!code-xaml[ListViewHowTos#5](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml#5)]  
[!code-xaml[ListViewHowTos#2](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml#2)]  
  
 <span data-ttu-id="6f0e6-107">L’exemple suivant gère l’événement <xref:System.Windows.Controls.Control.MouseDoubleClick>.</span><span class="sxs-lookup"><span data-stu-id="6f0e6-107">The following example handles the <xref:System.Windows.Controls.Control.MouseDoubleClick> event.</span></span>  
  
 [!code-csharp[ListViewHowTos#6](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml.cs#6)]
 [!code-vb[ListViewHowTos#6](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ListViewHowTos/VisualBasic/Window1.xaml.vb#6)]  
  
> [!NOTE]
> <span data-ttu-id="6f0e6-108">Bien qu’il soit plus courant de lier un <xref:System.Windows.Controls.ListView> à une source de données, vous pouvez utiliser un style pour ajouter un gestionnaire d’événements à chaque <xref:System.Windows.Controls.ListViewItem> dans un <xref:System.Windows.Controls.ListView> non lié aux données, que vous ayez explicitement ou non créé un <xref:System.Windows.Controls.ListViewItem>.</span><span class="sxs-lookup"><span data-stu-id="6f0e6-108">Although it is most common to bind a <xref:System.Windows.Controls.ListView> to a data source, you can use a style to add an event handler to each <xref:System.Windows.Controls.ListViewItem> in a non-data-bound <xref:System.Windows.Controls.ListView> regardless of whether you explicitly create a <xref:System.Windows.Controls.ListViewItem>.</span></span>  <span data-ttu-id="6f0e6-109">Pour plus d’informations sur les contrôles <xref:System.Windows.Controls.ListViewItem> créés explicitement et implicitement, consultez <xref:System.Windows.Controls.ItemsControl>.</span><span class="sxs-lookup"><span data-stu-id="6f0e6-109">For more information about explicitly and implicitly created <xref:System.Windows.Controls.ListViewItem> controls, see <xref:System.Windows.Controls.ItemsControl>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6f0e6-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6f0e6-110">See also</span></span>

- <xref:System.Xml.XmlElement>
- [<span data-ttu-id="6f0e6-111">Vue d’ensemble de la liaison de données</span><span class="sxs-lookup"><span data-stu-id="6f0e6-111">Data Binding Overview</span></span>](../data/data-binding-overview.md)
- [<span data-ttu-id="6f0e6-112">Application d’un style et création de modèles</span><span class="sxs-lookup"><span data-stu-id="6f0e6-112">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="6f0e6-113">Effectuer une liaison à des données XML à l’aide d’un XMLDataProvider et de requêtes XPath</span><span class="sxs-lookup"><span data-stu-id="6f0e6-113">Bind to XML Data Using an XMLDataProvider and XPath Queries</span></span>](../data/how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md)
- [<span data-ttu-id="6f0e6-114">Vue d’ensemble de ListView</span><span class="sxs-lookup"><span data-stu-id="6f0e6-114">ListView Overview</span></span>](listview-overview.md)
