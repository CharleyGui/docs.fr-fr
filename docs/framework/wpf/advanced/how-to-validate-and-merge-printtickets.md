---
title: 'Procédure : Valider et fusionner des PrintTicket'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- merging PrintTickets [WPF]
- PrintTicket [WPF], merging
- validation of PrintTickets [WPF]
- PrintTicket [WPF], validation
ms.assetid: 4fe2d501-d0b0-4fef-86af-6ffe6c162532
ms.openlocfilehash: 9e5242c07179501e6b39840a36f8dd6364d65b84
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69918345"
---
# <a name="how-to-validate-and-merge-printtickets"></a><span data-ttu-id="b7510-102">Procédure : Valider et fusionner des PrintTicket</span><span class="sxs-lookup"><span data-stu-id="b7510-102">How to: Validate and Merge PrintTickets</span></span>
<span data-ttu-id="b7510-103">Le [!INCLUDE[TLA#tla_win](../../../../includes/tlasharptla-win-md.md)] [schéma d’impression](https://go.microsoft.com/fwlink/?LinkId=186397) comprend les <xref:System.Printing.PrintCapabilities> <xref:System.Printing.PrintTicket> éléments flexibles et extensibles.</span><span class="sxs-lookup"><span data-stu-id="b7510-103">The [!INCLUDE[TLA#tla_win](../../../../includes/tlasharptla-win-md.md)] [Print Schema](https://go.microsoft.com/fwlink/?LinkId=186397) includes the flexible and extensible <xref:System.Printing.PrintCapabilities> and <xref:System.Printing.PrintTicket> elements.</span></span> <span data-ttu-id="b7510-104">Le premier détaille les fonctionnalités d’un périphérique d’impression et le dernier spécifie comment l’appareil doit utiliser ces fonctionnalités en ce qui concerne une séquence particulière de documents, un document individuel ou une page individuelle.</span><span class="sxs-lookup"><span data-stu-id="b7510-104">The former itemizes the capabilities of a print device and the latter specifies how the device should use those capabilities with respect to a particular sequence of documents, individual document, or individual page.</span></span>  
  
 <span data-ttu-id="b7510-105">Voici une séquence classique de tâches pour une application qui prend en charge l’impression.</span><span class="sxs-lookup"><span data-stu-id="b7510-105">A typical sequence of tasks for an application that supports printing would be as follows.</span></span>  
  
1. <span data-ttu-id="b7510-106">Déterminez les fonctionnalités d’une imprimante.</span><span class="sxs-lookup"><span data-stu-id="b7510-106">Determine a printer's capabilities.</span></span>  
  
2. <span data-ttu-id="b7510-107">Configurez un <xref:System.Printing.PrintTicket> pour utiliser ces fonctionnalités.</span><span class="sxs-lookup"><span data-stu-id="b7510-107">Configure a <xref:System.Printing.PrintTicket> to use those capabilities.</span></span>  
  
3. <span data-ttu-id="b7510-108">Validez <xref:System.Printing.PrintTicket>.</span><span class="sxs-lookup"><span data-stu-id="b7510-108">Validate the <xref:System.Printing.PrintTicket>.</span></span>  
  
 <span data-ttu-id="b7510-109">Cet article explique comment procéder.</span><span class="sxs-lookup"><span data-stu-id="b7510-109">This article shows how to do this.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b7510-110">Exemples</span><span class="sxs-lookup"><span data-stu-id="b7510-110">Example</span></span>  
 <span data-ttu-id="b7510-111">Dans l’exemple simple ci-dessous, nous nous intéressons uniquement si une imprimante peut prendre en charge l’impression recto-verso.</span><span class="sxs-lookup"><span data-stu-id="b7510-111">In the simple example below, we are interested only in whether a printer can support duplexing — two-sided printing.</span></span> <span data-ttu-id="b7510-112">Les étapes principales sont les suivantes.</span><span class="sxs-lookup"><span data-stu-id="b7510-112">The major steps are as follows.</span></span>  
  
1. <span data-ttu-id="b7510-113">Obtient un <xref:System.Printing.PrintCapabilities> objet avec la <xref:System.Printing.PrintQueue.GetPrintCapabilities%2A> méthode.</span><span class="sxs-lookup"><span data-stu-id="b7510-113">Get a <xref:System.Printing.PrintCapabilities> object with the <xref:System.Printing.PrintQueue.GetPrintCapabilities%2A> method.</span></span>  
  
2. <span data-ttu-id="b7510-114">Testez la présence de la fonctionnalité de votre choix.</span><span class="sxs-lookup"><span data-stu-id="b7510-114">Test for the presence of the capability you want.</span></span> <span data-ttu-id="b7510-115">Dans l’exemple ci-dessous, nous <xref:System.Printing.PrintCapabilities.DuplexingCapability%2A> testons la <xref:System.Printing.PrintCapabilities> propriété de l’objet pour la présence de la capacité d’impression des deux côtés d’une feuille de papier avec la «rotation de page» sur le côté long de la feuille.</span><span class="sxs-lookup"><span data-stu-id="b7510-115">In the example below, we test the <xref:System.Printing.PrintCapabilities.DuplexingCapability%2A> property of the <xref:System.Printing.PrintCapabilities> object for the presence of the capability of printing on both sides of a sheet of paper with the "page turning" along the long side of the sheet.</span></span> <span data-ttu-id="b7510-116">Étant <xref:System.Printing.PrintCapabilities.DuplexingCapability%2A> donné que est une collection, nous `Contains` utilisons la <xref:System.Collections.ObjectModel.ReadOnlyCollection%601>méthode de.</span><span class="sxs-lookup"><span data-stu-id="b7510-116">Since <xref:System.Printing.PrintCapabilities.DuplexingCapability%2A> is a collection, we use the `Contains` method of <xref:System.Collections.ObjectModel.ReadOnlyCollection%601>.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="b7510-117">Cette étape n’est pas strictement nécessaire.</span><span class="sxs-lookup"><span data-stu-id="b7510-117">This step is not strictly necessary.</span></span> <span data-ttu-id="b7510-118">La <xref:System.Printing.PrintQueue.MergeAndValidatePrintTicket%2A> méthode utilisée ci-dessous vérifie chaque requête dans <xref:System.Printing.PrintTicket> le par rapport aux fonctionnalités de l’imprimante.</span><span class="sxs-lookup"><span data-stu-id="b7510-118">The <xref:System.Printing.PrintQueue.MergeAndValidatePrintTicket%2A> method used below will check each request in the <xref:System.Printing.PrintTicket> against the capabilities of the printer.</span></span> <span data-ttu-id="b7510-119">Si la fonctionnalité demandée n’est pas prise en charge par l’imprimante, le pilote d’imprimante remplace une <xref:System.Printing.PrintTicket> autre requête dans le retourné par la méthode.</span><span class="sxs-lookup"><span data-stu-id="b7510-119">If the requested capability is not supported by printer, the printer driver will substitute an alternative request in the <xref:System.Printing.PrintTicket> returned by the method.</span></span>  
  
3. <span data-ttu-id="b7510-120">Si l’imprimante prend en charge l’impression recto-verso <xref:System.Printing.PrintTicket> , l’exemple de code crée un qui demande un duplex.</span><span class="sxs-lookup"><span data-stu-id="b7510-120">If the printer supports duplexing, the sample code creates a <xref:System.Printing.PrintTicket> that asks for duplexing.</span></span> <span data-ttu-id="b7510-121">Toutefois, l’application ne spécifie pas tous les paramètres d’imprimante <xref:System.Printing.PrintTicket> possibles disponibles dans l’élément.</span><span class="sxs-lookup"><span data-stu-id="b7510-121">But the application does not specify every possible printer setting available in the <xref:System.Printing.PrintTicket> element.</span></span> <span data-ttu-id="b7510-122">Cela serait gaspiller le programmeur et le temps de programmation.</span><span class="sxs-lookup"><span data-stu-id="b7510-122">That would be wasteful of both programmer and program time.</span></span> <span data-ttu-id="b7510-123">Au lieu de cela, le code définit uniquement la demande de duplexage, <xref:System.Printing.PrintTicket> puis fusionne avec un existant, entièrement configuré <xref:System.Printing.PrintTicket>et validé,, dans ce cas, la <xref:System.Printing.PrintTicket>valeur par défaut de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="b7510-123">Instead, the code sets only the duplexing request and then merges this <xref:System.Printing.PrintTicket> with an existing, fully configured and validated, <xref:System.Printing.PrintTicket>, in this case, the user's default <xref:System.Printing.PrintTicket>.</span></span>  
  
4. <span data-ttu-id="b7510-124">En conséquence, l’exemple appelle <xref:System.Printing.PrintQueue.MergeAndValidatePrintTicket%2A> la méthode pour fusionner le nouveau, <xref:System.Printing.PrintTicket> minimal, avec la valeur <xref:System.Printing.PrintTicket>par défaut de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="b7510-124">Accordingly, the sample calls the <xref:System.Printing.PrintQueue.MergeAndValidatePrintTicket%2A> method to merge the new, minimal, <xref:System.Printing.PrintTicket> with the user's default <xref:System.Printing.PrintTicket>.</span></span> <span data-ttu-id="b7510-125">Cela retourne un <xref:System.Printing.ValidationResult> qui comprend le nouveau <xref:System.Printing.PrintTicket> comme l’une de ses propriétés.</span><span class="sxs-lookup"><span data-stu-id="b7510-125">This returns a <xref:System.Printing.ValidationResult> that includes the new <xref:System.Printing.PrintTicket> as one of its properties.</span></span>  
  
5. <span data-ttu-id="b7510-126">L’exemple teste ensuite les nouvelles <xref:System.Printing.PrintTicket> demandes en duplex.</span><span class="sxs-lookup"><span data-stu-id="b7510-126">The sample then tests that the new <xref:System.Printing.PrintTicket> requests duplexing.</span></span> <span data-ttu-id="b7510-127">Si c’est le cas, l’exemple en fait le nouveau ticket d’impression par défaut pour l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="b7510-127">If it does, then the sample makes it the new default print ticket for the user.</span></span> <span data-ttu-id="b7510-128">Si l’étape 2 ci-dessus avait été omise et que l’imprimante ne prenait pas en charge le duplexeur sur le long terme, `false`le test aurait abouti.</span><span class="sxs-lookup"><span data-stu-id="b7510-128">If step 2 above had been left out and the printer did not support duplexing along the long side, then the test would have resulted in `false`.</span></span> <span data-ttu-id="b7510-129">(Voir la remarque ci-dessus.)</span><span class="sxs-lookup"><span data-stu-id="b7510-129">(See the note above.)</span></span>  
  
6. <span data-ttu-id="b7510-130">La dernière étape importante consiste à valider la modification apportée à <xref:System.Printing.PrintQueue.UserPrintTicket%2A> la <xref:System.Printing.PrintQueue> propriété de <xref:System.Printing.PrintQueue.Commit%2A> avec la méthode.</span><span class="sxs-lookup"><span data-stu-id="b7510-130">The last significant step is to commit the change to the <xref:System.Printing.PrintQueue.UserPrintTicket%2A> property of the <xref:System.Printing.PrintQueue> with the <xref:System.Printing.PrintQueue.Commit%2A> method.</span></span>  
  
 [!code-csharp[PrintTicketManagment#UsingMergeAndValidate](~/samples/snippets/csharp/VS_Snippets_Wpf/PrintTicketManagment/CSharp/printticket.cs#usingmergeandvalidate)]
 [!code-vb[PrintTicketManagment#UsingMergeAndValidate](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PrintTicketManagment/visualbasic/printticket.vb#usingmergeandvalidate)]  
  
 <span data-ttu-id="b7510-131">Pour que vous puissiez tester rapidement cet exemple, le reste de l’exemple est présenté ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="b7510-131">So that you can quickly test this example, the remainder of it is presented below.</span></span> <span data-ttu-id="b7510-132">Créez un projet et un espace de noms, puis collez les deux extraits de code dans cet article dans le bloc d’espace de noms.</span><span class="sxs-lookup"><span data-stu-id="b7510-132">Create a project and a namespace and then paste both the code snippets in this article into the namespace block.</span></span>  
  
 [!code-csharp[PrintTicketManagment#UIForMergeAndValidatePTUtility](~/samples/snippets/csharp/VS_Snippets_Wpf/PrintTicketManagment/CSharp/printticket.cs#uiformergeandvalidateptutility)]
 [!code-vb[PrintTicketManagment#UIForMergeAndValidatePTUtility](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PrintTicketManagment/visualbasic/printticket.vb#uiformergeandvalidateptutility)]  
  
## <a name="see-also"></a><span data-ttu-id="b7510-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b7510-133">See also</span></span>

- <xref:System.Printing.PrintCapabilities>
- <xref:System.Printing.PrintTicket>
- <xref:System.Printing.PrintServer.GetPrintQueues%2A>
- <xref:System.Printing.PrintServer>
- <xref:System.Printing.EnumeratedPrintQueueTypes>
- <xref:System.Printing.PrintQueue>
- <xref:System.Printing.PrintQueue.GetPrintCapabilities%2A>
- [<span data-ttu-id="b7510-134">Documents dans WPF</span><span class="sxs-lookup"><span data-stu-id="b7510-134">Documents in WPF</span></span>](documents-in-wpf.md)
- [<span data-ttu-id="b7510-135">Vue d’ensemble de l’impression</span><span class="sxs-lookup"><span data-stu-id="b7510-135">Printing Overview</span></span>](printing-overview.md)
- [<span data-ttu-id="b7510-136">Schéma d’impression</span><span class="sxs-lookup"><span data-stu-id="b7510-136">Print Schema</span></span>](https://go.microsoft.com/fwlink/?LinkId=186397)
