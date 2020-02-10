---
title: "Comment : énumérer un sous-ensemble de files d'attente à l'impression"
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- enumerating [WPF], subset of print queues
- print queues [WPF], enumerating subset of
ms.assetid: cc4a1b5b-d46f-4c5e-bc26-22c226e4bee0
ms.openlocfilehash: aae41931f012f6d34fc057fdd6ee9fc9baab6e7b
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/09/2020
ms.locfileid: "77094538"
---
# <a name="how-to-enumerate-a-subset-of-print-queues"></a><span data-ttu-id="17d7c-102">Comment : énumérer un sous-ensemble de files d'attente à l'impression</span><span class="sxs-lookup"><span data-stu-id="17d7c-102">How to: Enumerate a Subset of Print Queues</span></span>
<span data-ttu-id="17d7c-103">Une situation courante rencontrée par les professionnels de l’informatique qui gèrent un ensemble d’imprimantes à l’ensemble de l’entreprise consiste à générer une liste d’imprimantes présentant certaines caractéristiques.</span><span class="sxs-lookup"><span data-stu-id="17d7c-103">A common situation faced by information technology (IT) professionals managing a company-wide set of printers is to generate a list of printers having certain characteristics.</span></span> <span data-ttu-id="17d7c-104">Cette fonctionnalité est fournie par la méthode <xref:System.Printing.PrintServer.GetPrintQueues%2A> d’un objet <xref:System.Printing.PrintServer> et de l’énumération <xref:System.Printing.EnumeratedPrintQueueTypes>.</span><span class="sxs-lookup"><span data-stu-id="17d7c-104">This functionality is provided by the <xref:System.Printing.PrintServer.GetPrintQueues%2A> method of a <xref:System.Printing.PrintServer> object and the <xref:System.Printing.EnumeratedPrintQueueTypes> enumeration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="17d7c-105">Exemple</span><span class="sxs-lookup"><span data-stu-id="17d7c-105">Example</span></span>  
 <span data-ttu-id="17d7c-106">Dans l’exemple ci-dessous, le code commence par créer un tableau d’indicateurs qui spécifient les caractéristiques des files d’attente à l’impression que vous souhaitez répertorier.</span><span class="sxs-lookup"><span data-stu-id="17d7c-106">In the example below, the code begins by creating an array of flags that specify the characteristics of the print queues we want to list.</span></span> <span data-ttu-id="17d7c-107">Dans cet exemple, nous recherchons des files d’attente à l’impression qui sont installées localement sur le serveur d’impression et qui sont partagées.</span><span class="sxs-lookup"><span data-stu-id="17d7c-107">In this example, we are looking for print queues that are installed locally on the print server and are shared.</span></span> <span data-ttu-id="17d7c-108">L’énumération <xref:System.Printing.EnumeratedPrintQueueTypes> offre de nombreuses autres possibilités.</span><span class="sxs-lookup"><span data-stu-id="17d7c-108">The <xref:System.Printing.EnumeratedPrintQueueTypes> enumeration provides many other possibilities.</span></span>  
  
 <span data-ttu-id="17d7c-109">Le code crée ensuite un objet <xref:System.Printing.LocalPrintServer>, une classe dérivée de <xref:System.Printing.PrintServer>.</span><span class="sxs-lookup"><span data-stu-id="17d7c-109">The code then creates a <xref:System.Printing.LocalPrintServer> object, a class derived from <xref:System.Printing.PrintServer>.</span></span> <span data-ttu-id="17d7c-110">Le serveur d’impression local est l’ordinateur sur lequel l’application s’exécute.</span><span class="sxs-lookup"><span data-stu-id="17d7c-110">The local print server is the computer on which the application is running.</span></span>  
  
 <span data-ttu-id="17d7c-111">La dernière étape importante consiste à passer le tableau à la méthode <xref:System.Printing.PrintServer.GetPrintQueues%2A>.</span><span class="sxs-lookup"><span data-stu-id="17d7c-111">The last significant step is to pass the array to the <xref:System.Printing.PrintServer.GetPrintQueues%2A> method.</span></span>  
  
 <span data-ttu-id="17d7c-112">Enfin, les résultats sont présentés à l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="17d7c-112">Finally, the results are presented to the user.</span></span>  
  
 [!code-cpp[EnumerateSubsetOfPrintQueues#ListSubsetOfPrintQueues](~/samples/snippets/cpp/VS_Snippets_Wpf/EnumerateSubsetOfPrintQueues/CPP/Program.cpp#listsubsetofprintqueues)]
 [!code-csharp[EnumerateSubsetOfPrintQueues#ListSubsetOfPrintQueues](~/samples/snippets/csharp/VS_Snippets_Wpf/EnumerateSubsetOfPrintQueues/CSharp/Program.cs#listsubsetofprintqueues)]
 [!code-vb[EnumerateSubsetOfPrintQueues#ListSubsetOfPrintQueues](~/samples/snippets/visualbasic/VS_Snippets_Wpf/EnumerateSubsetOfPrintQueues/visualbasic/program.vb#listsubsetofprintqueues)]  
  
 <span data-ttu-id="17d7c-113">Vous pouvez étendre cet exemple en faisant en sorte que la `foreach` boucle qui parcourt chaque file d’attente à l’impression effectue un filtrage supplémentaire.</span><span class="sxs-lookup"><span data-stu-id="17d7c-113">You could extend this example by having the `foreach` loop that steps through each print queue do further screening.</span></span> <span data-ttu-id="17d7c-114">Par exemple, vous pouvez filtrer les imprimantes qui ne prennent pas en charge l’impression recto-verso en faisant appel à la boucle pour chaque méthode <xref:System.Printing.PrintQueue.GetPrintCapabilities%2A> de la file d’attente à l’impression et tester la valeur renvoyée pour la présence du duplex.</span><span class="sxs-lookup"><span data-stu-id="17d7c-114">For example, you could screen out printers that do not support two-sided printing by having the loop call each print queue's <xref:System.Printing.PrintQueue.GetPrintCapabilities%2A> method and test the returned value for the presence of duplexing.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="17d7c-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="17d7c-115">See also</span></span>

- <xref:System.Printing.PrintServer.GetPrintQueues%2A>
- <xref:System.Printing.PrintServer>
- <xref:System.Printing.LocalPrintServer>
- <xref:System.Printing.EnumeratedPrintQueueTypes>
- <xref:System.Printing.PrintQueue>
- <xref:System.Printing.PrintQueue.GetPrintCapabilities%2A>
- [<span data-ttu-id="17d7c-116">Documents dans WPF</span><span class="sxs-lookup"><span data-stu-id="17d7c-116">Documents in WPF</span></span>](documents-in-wpf.md)
- [<span data-ttu-id="17d7c-117">Vue d’ensemble de l’impression</span><span class="sxs-lookup"><span data-stu-id="17d7c-117">Printing Overview</span></span>](printing-overview.md)
- [<span data-ttu-id="17d7c-118">Microsoft XPS document Writer</span><span class="sxs-lookup"><span data-stu-id="17d7c-118">Microsoft XPS Document Writer</span></span>](/windows/win32/printdocs/microsoft-xps-document-writer)
