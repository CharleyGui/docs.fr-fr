---
title: "Comment : gérer l'événement MouseDoubleClick pour chaque élément d'un ListView"
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ListView controls [WPF], MouseDoubleClick event
ms.assetid: 81b39369-655a-4585-ac58-4640e5bb8fed
ms.openlocfilehash: 7bbc7bad36b3b1f2c92065e5f5699e5a86ac6189
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/20/2020
ms.locfileid: "81646112"
---
# <a name="how-to-handle-the-mousedoubleclick-event-for-each-item-in-a-listview"></a><span data-ttu-id="8d7ea-102">Comment : gérer l'événement MouseDoubleClick pour chaque élément d'un ListView</span><span class="sxs-lookup"><span data-stu-id="8d7ea-102">How to: Handle the MouseDoubleClick Event for Each Item in a ListView</span></span>
<span data-ttu-id="8d7ea-103">Pour gérer un événement pour <xref:System.Windows.Controls.ListView>un élément dans un , <xref:System.Windows.Controls.ListViewItem>vous devez ajouter un gestionnaire d’événement à chaque .</span><span class="sxs-lookup"><span data-stu-id="8d7ea-103">To handle an event for an item in a <xref:System.Windows.Controls.ListView>, you need to add an event handler to each <xref:System.Windows.Controls.ListViewItem>.</span></span> <span data-ttu-id="8d7ea-104">Lorsque <xref:System.Windows.Controls.ListView> l’a est lié à une source <xref:System.Windows.Controls.ListViewItem>de données, vous ne créez pas <xref:System.Windows.EventSetter> explicitement un , <xref:System.Windows.Controls.ListViewItem>mais vous pouvez gérer l’événement pour chaque élément en ajoutant un style d’un .</span><span class="sxs-lookup"><span data-stu-id="8d7ea-104">When a <xref:System.Windows.Controls.ListView> is bound to a data source, you don't explicitly create a <xref:System.Windows.Controls.ListViewItem>, but you can handle the event for each item by adding an <xref:System.Windows.EventSetter> to a style of a <xref:System.Windows.Controls.ListViewItem>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8d7ea-105">Exemple</span><span class="sxs-lookup"><span data-stu-id="8d7ea-105">Example</span></span>  
 <span data-ttu-id="8d7ea-106">L’exemple suivant crée <xref:System.Windows.Controls.ListView> une limite <xref:System.Windows.Style> de données et <xref:System.Windows.Controls.ListViewItem>crée un pour ajouter un gestionnaire d’événements à chacun .</span><span class="sxs-lookup"><span data-stu-id="8d7ea-106">The following example creates a data-bound <xref:System.Windows.Controls.ListView> and creates a <xref:System.Windows.Style> to add an event handler to each <xref:System.Windows.Controls.ListViewItem>.</span></span>  
  
 [!code-xaml[ListViewHowTos#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml#1)]  
[!code-xaml[ListViewHowTos#5](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml#5)]  
[!code-xaml[ListViewHowTos#2](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml#2)]  
  
 <span data-ttu-id="8d7ea-107">L’exemple suivant <xref:System.Windows.Controls.Control.MouseDoubleClick> traite de l’événement.</span><span class="sxs-lookup"><span data-stu-id="8d7ea-107">The following example handles the <xref:System.Windows.Controls.Control.MouseDoubleClick> event.</span></span>  
  
 [!code-csharp[ListViewHowTos#6](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml.cs#6)]
 [!code-vb[ListViewHowTos#6](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ListViewHowTos/VisualBasic/Window1.xaml.vb#6)]  
  
> [!NOTE]
> <span data-ttu-id="8d7ea-108">Bien qu’il soit <xref:System.Windows.Controls.ListView> plus courant de lier une source de données <xref:System.Windows.Controls.ListViewItem> à une source de <xref:System.Windows.Controls.ListView> données, vous pouvez <xref:System.Windows.Controls.ListViewItem>utiliser un style pour ajouter un gestionnaire d’événements à chacun dans un non-data-lié indépendamment du fait que vous créez explicitement un .</span><span class="sxs-lookup"><span data-stu-id="8d7ea-108">Although it is most common to bind a <xref:System.Windows.Controls.ListView> to a data source, you can use a style to add an event handler to each <xref:System.Windows.Controls.ListViewItem> in a non-data-bound <xref:System.Windows.Controls.ListView> regardless of whether you explicitly create a <xref:System.Windows.Controls.ListViewItem>.</span></span>  <span data-ttu-id="8d7ea-109">Pour plus d’informations sur <xref:System.Windows.Controls.ListViewItem> les <xref:System.Windows.Controls.ItemsControl>contrôles explicitement et implicitement créés, voir .</span><span class="sxs-lookup"><span data-stu-id="8d7ea-109">For more information about explicitly and implicitly created <xref:System.Windows.Controls.ListViewItem> controls, see <xref:System.Windows.Controls.ItemsControl>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8d7ea-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8d7ea-110">See also</span></span>

- <xref:System.Xml.XmlElement>
- [<span data-ttu-id="8d7ea-111">Aperçu de la liaison de données</span><span class="sxs-lookup"><span data-stu-id="8d7ea-111">Data Binding Overview</span></span>](../../../desktop-wpf/data/data-binding-overview.md)
- [<span data-ttu-id="8d7ea-112">Application d’un style et création de modèles</span><span class="sxs-lookup"><span data-stu-id="8d7ea-112">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="8d7ea-113">Lier aux données XML à l’aide d’un XMLDataProvider et XPath Requêtes</span><span class="sxs-lookup"><span data-stu-id="8d7ea-113">Bind to XML Data Using an XMLDataProvider and XPath Queries</span></span>](../data/how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md)
- [<span data-ttu-id="8d7ea-114">Vue d’ensemble de ListView</span><span class="sxs-lookup"><span data-stu-id="8d7ea-114">ListView Overview</span></span>](listview-overview.md)
