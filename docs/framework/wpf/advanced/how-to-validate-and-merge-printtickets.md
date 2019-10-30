---
title: 'Comment : valider et fusionner des PrintTicket'
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
ms.openlocfilehash: 15e328729886e0f1efc3b47705fcb4ce13013137
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/29/2019
ms.locfileid: "73035579"
---
# <a name="how-to-validate-and-merge-printtickets"></a><span data-ttu-id="b3438-102">Comment : valider et fusionner des PrintTicket</span><span class="sxs-lookup"><span data-stu-id="b3438-102">How to: Validate and Merge PrintTickets</span></span>
<span data-ttu-id="b3438-103">Le schéma d' [impression](https://go.microsoft.com/fwlink/?LinkId=186397) Microsoft Windows comprend les éléments <xref:System.Printing.PrintCapabilities> et <xref:System.Printing.PrintTicket> flexibles et extensibles.</span><span class="sxs-lookup"><span data-stu-id="b3438-103">The Microsoft Windows [Print Schema](https://go.microsoft.com/fwlink/?LinkId=186397) includes the flexible and extensible <xref:System.Printing.PrintCapabilities> and <xref:System.Printing.PrintTicket> elements.</span></span> <span data-ttu-id="b3438-104">Le premier détaille les fonctionnalités d’un périphérique d’impression et le dernier spécifie comment l’appareil doit utiliser ces fonctionnalités en ce qui concerne une séquence particulière de documents, un document individuel ou une page individuelle.</span><span class="sxs-lookup"><span data-stu-id="b3438-104">The former itemizes the capabilities of a print device and the latter specifies how the device should use those capabilities with respect to a particular sequence of documents, individual document, or individual page.</span></span>  
  
 <span data-ttu-id="b3438-105">Voici une séquence classique de tâches pour une application qui prend en charge l’impression.</span><span class="sxs-lookup"><span data-stu-id="b3438-105">A typical sequence of tasks for an application that supports printing would be as follows.</span></span>  
  
1. <span data-ttu-id="b3438-106">Déterminez les fonctionnalités d’une imprimante.</span><span class="sxs-lookup"><span data-stu-id="b3438-106">Determine a printer's capabilities.</span></span>  
  
2. <span data-ttu-id="b3438-107">Configurez un <xref:System.Printing.PrintTicket> pour utiliser ces fonctionnalités.</span><span class="sxs-lookup"><span data-stu-id="b3438-107">Configure a <xref:System.Printing.PrintTicket> to use those capabilities.</span></span>  
  
3. <span data-ttu-id="b3438-108">Validez le <xref:System.Printing.PrintTicket>.</span><span class="sxs-lookup"><span data-stu-id="b3438-108">Validate the <xref:System.Printing.PrintTicket>.</span></span>  
  
 <span data-ttu-id="b3438-109">Cet article explique comment procéder.</span><span class="sxs-lookup"><span data-stu-id="b3438-109">This article shows how to do this.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b3438-110">Exemple</span><span class="sxs-lookup"><span data-stu-id="b3438-110">Example</span></span>  
 <span data-ttu-id="b3438-111">Dans l’exemple simple ci-dessous, nous nous intéressons uniquement si une imprimante peut prendre en charge l’impression recto-verso.</span><span class="sxs-lookup"><span data-stu-id="b3438-111">In the simple example below, we are interested only in whether a printer can support duplexing — two-sided printing.</span></span> <span data-ttu-id="b3438-112">Les étapes principales sont les suivantes.</span><span class="sxs-lookup"><span data-stu-id="b3438-112">The major steps are as follows.</span></span>  
  
1. <span data-ttu-id="b3438-113">Obtient un objet <xref:System.Printing.PrintCapabilities> avec la méthode <xref:System.Printing.PrintQueue.GetPrintCapabilities%2A>.</span><span class="sxs-lookup"><span data-stu-id="b3438-113">Get a <xref:System.Printing.PrintCapabilities> object with the <xref:System.Printing.PrintQueue.GetPrintCapabilities%2A> method.</span></span>  
  
2. <span data-ttu-id="b3438-114">Testez la présence de la fonctionnalité de votre choix.</span><span class="sxs-lookup"><span data-stu-id="b3438-114">Test for the presence of the capability you want.</span></span> <span data-ttu-id="b3438-115">Dans l’exemple ci-dessous, nous testons la propriété <xref:System.Printing.PrintCapabilities.DuplexingCapability%2A> de l’objet <xref:System.Printing.PrintCapabilities> pour la présence de la possibilité d’imprimer sur les deux côtés d’une feuille de papier avec la « rotation de page » sur le côté long de la feuille.</span><span class="sxs-lookup"><span data-stu-id="b3438-115">In the example below, we test the <xref:System.Printing.PrintCapabilities.DuplexingCapability%2A> property of the <xref:System.Printing.PrintCapabilities> object for the presence of the capability of printing on both sides of a sheet of paper with the "page turning" along the long side of the sheet.</span></span> <span data-ttu-id="b3438-116">Étant donné que <xref:System.Printing.PrintCapabilities.DuplexingCapability%2A> est une collection, nous utilisons la méthode `Contains` de <xref:System.Collections.ObjectModel.ReadOnlyCollection%601>.</span><span class="sxs-lookup"><span data-stu-id="b3438-116">Since <xref:System.Printing.PrintCapabilities.DuplexingCapability%2A> is a collection, we use the `Contains` method of <xref:System.Collections.ObjectModel.ReadOnlyCollection%601>.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="b3438-117">Cette étape n’est pas strictement nécessaire.</span><span class="sxs-lookup"><span data-stu-id="b3438-117">This step is not strictly necessary.</span></span> <span data-ttu-id="b3438-118">La méthode <xref:System.Printing.PrintQueue.MergeAndValidatePrintTicket%2A> utilisée ci-dessous vérifie chaque demande dans la <xref:System.Printing.PrintTicket> par rapport aux fonctionnalités de l’imprimante.</span><span class="sxs-lookup"><span data-stu-id="b3438-118">The <xref:System.Printing.PrintQueue.MergeAndValidatePrintTicket%2A> method used below will check each request in the <xref:System.Printing.PrintTicket> against the capabilities of the printer.</span></span> <span data-ttu-id="b3438-119">Si la capacité demandée n’est pas prise en charge par l’imprimante, le pilote d’imprimante remplace une autre requête dans le <xref:System.Printing.PrintTicket> retourné par la méthode.</span><span class="sxs-lookup"><span data-stu-id="b3438-119">If the requested capability is not supported by printer, the printer driver will substitute an alternative request in the <xref:System.Printing.PrintTicket> returned by the method.</span></span>  
  
3. <span data-ttu-id="b3438-120">Si l’imprimante prend en charge l’impression recto-verso, l’exemple de code crée une <xref:System.Printing.PrintTicket> qui demande un duplex.</span><span class="sxs-lookup"><span data-stu-id="b3438-120">If the printer supports duplexing, the sample code creates a <xref:System.Printing.PrintTicket> that asks for duplexing.</span></span> <span data-ttu-id="b3438-121">Toutefois, l’application ne spécifie pas tous les paramètres d’imprimante possibles disponibles dans l’élément <xref:System.Printing.PrintTicket>.</span><span class="sxs-lookup"><span data-stu-id="b3438-121">But the application does not specify every possible printer setting available in the <xref:System.Printing.PrintTicket> element.</span></span> <span data-ttu-id="b3438-122">Cela serait gaspiller le programmeur et le temps de programmation.</span><span class="sxs-lookup"><span data-stu-id="b3438-122">That would be wasteful of both programmer and program time.</span></span> <span data-ttu-id="b3438-123">Au lieu de cela, le code définit uniquement la demande de duplexage, puis fusionne ce <xref:System.Printing.PrintTicket> avec une <xref:System.Printing.PrintTicket>existante, entièrement configurée et validée, dans ce cas, le <xref:System.Printing.PrintTicket>par défaut de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="b3438-123">Instead, the code sets only the duplexing request and then merges this <xref:System.Printing.PrintTicket> with an existing, fully configured and validated, <xref:System.Printing.PrintTicket>, in this case, the user's default <xref:System.Printing.PrintTicket>.</span></span>  
  
4. <span data-ttu-id="b3438-124">En conséquence, l’exemple appelle la méthode <xref:System.Printing.PrintQueue.MergeAndValidatePrintTicket%2A> pour fusionner le nouveau, minimal <xref:System.Printing.PrintTicket> avec le <xref:System.Printing.PrintTicket>par défaut de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="b3438-124">Accordingly, the sample calls the <xref:System.Printing.PrintQueue.MergeAndValidatePrintTicket%2A> method to merge the new, minimal, <xref:System.Printing.PrintTicket> with the user's default <xref:System.Printing.PrintTicket>.</span></span> <span data-ttu-id="b3438-125">Cela retourne un <xref:System.Printing.ValidationResult> qui comprend le nouveau <xref:System.Printing.PrintTicket> comme l’une de ses propriétés.</span><span class="sxs-lookup"><span data-stu-id="b3438-125">This returns a <xref:System.Printing.ValidationResult> that includes the new <xref:System.Printing.PrintTicket> as one of its properties.</span></span>  
  
5. <span data-ttu-id="b3438-126">L’exemple teste ensuite que la nouvelle <xref:System.Printing.PrintTicket> demande le duplexage.</span><span class="sxs-lookup"><span data-stu-id="b3438-126">The sample then tests that the new <xref:System.Printing.PrintTicket> requests duplexing.</span></span> <span data-ttu-id="b3438-127">Si c’est le cas, l’exemple en fait le nouveau ticket d’impression par défaut pour l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="b3438-127">If it does, then the sample makes it the new default print ticket for the user.</span></span> <span data-ttu-id="b3438-128">Si l’étape 2 ci-dessus avait été omise et que l’imprimante ne prenait pas en charge le duplexeur sur la longue partie, le test aurait abouti à `false`.</span><span class="sxs-lookup"><span data-stu-id="b3438-128">If step 2 above had been left out and the printer did not support duplexing along the long side, then the test would have resulted in `false`.</span></span> <span data-ttu-id="b3438-129">(Voir la remarque ci-dessus.)</span><span class="sxs-lookup"><span data-stu-id="b3438-129">(See the note above.)</span></span>  
  
6. <span data-ttu-id="b3438-130">La dernière étape importante consiste à valider la modification apportée à la propriété <xref:System.Printing.PrintQueue.UserPrintTicket%2A> du <xref:System.Printing.PrintQueue> avec la méthode <xref:System.Printing.PrintQueue.Commit%2A>.</span><span class="sxs-lookup"><span data-stu-id="b3438-130">The last significant step is to commit the change to the <xref:System.Printing.PrintQueue.UserPrintTicket%2A> property of the <xref:System.Printing.PrintQueue> with the <xref:System.Printing.PrintQueue.Commit%2A> method.</span></span>  
  
 [!code-csharp[PrintTicketManagment#UsingMergeAndValidate](~/samples/snippets/csharp/VS_Snippets_Wpf/PrintTicketManagment/CSharp/printticket.cs#usingmergeandvalidate)]
 [!code-vb[PrintTicketManagment#UsingMergeAndValidate](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PrintTicketManagment/visualbasic/printticket.vb#usingmergeandvalidate)]  
  
 <span data-ttu-id="b3438-131">Pour que vous puissiez tester rapidement cet exemple, le reste de l’exemple est présenté ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="b3438-131">So that you can quickly test this example, the remainder of it is presented below.</span></span> <span data-ttu-id="b3438-132">Créez un projet et un espace de noms, puis collez les deux extraits de code dans cet article dans le bloc d’espace de noms.</span><span class="sxs-lookup"><span data-stu-id="b3438-132">Create a project and a namespace and then paste both the code snippets in this article into the namespace block.</span></span>  
  
 [!code-csharp[PrintTicketManagment#UIForMergeAndValidatePTUtility](~/samples/snippets/csharp/VS_Snippets_Wpf/PrintTicketManagment/CSharp/printticket.cs#uiformergeandvalidateptutility)]
 [!code-vb[PrintTicketManagment#UIForMergeAndValidatePTUtility](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PrintTicketManagment/visualbasic/printticket.vb#uiformergeandvalidateptutility)]  
  
## <a name="see-also"></a><span data-ttu-id="b3438-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b3438-133">See also</span></span>

- <xref:System.Printing.PrintCapabilities>
- <xref:System.Printing.PrintTicket>
- <xref:System.Printing.PrintServer.GetPrintQueues%2A>
- <xref:System.Printing.PrintServer>
- <xref:System.Printing.EnumeratedPrintQueueTypes>
- <xref:System.Printing.PrintQueue>
- <xref:System.Printing.PrintQueue.GetPrintCapabilities%2A>
- [<span data-ttu-id="b3438-134">Documents dans WPF</span><span class="sxs-lookup"><span data-stu-id="b3438-134">Documents in WPF</span></span>](documents-in-wpf.md)
- [<span data-ttu-id="b3438-135">Vue d’ensemble de l’impression</span><span class="sxs-lookup"><span data-stu-id="b3438-135">Printing Overview</span></span>](printing-overview.md)
- [<span data-ttu-id="b3438-136">Schéma d’impression</span><span class="sxs-lookup"><span data-stu-id="b3438-136">Print Schema</span></span>](https://go.microsoft.com/fwlink/?LinkId=186397)
