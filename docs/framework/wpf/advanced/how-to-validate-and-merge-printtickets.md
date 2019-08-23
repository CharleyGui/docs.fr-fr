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
# <a name="how-to-validate-and-merge-printtickets"></a>Procédure : Valider et fusionner des PrintTicket
Le [!INCLUDE[TLA#tla_win](../../../../includes/tlasharptla-win-md.md)] [schéma d’impression](https://go.microsoft.com/fwlink/?LinkId=186397) comprend les <xref:System.Printing.PrintCapabilities> <xref:System.Printing.PrintTicket> éléments flexibles et extensibles. Le premier détaille les fonctionnalités d’un périphérique d’impression et le dernier spécifie comment l’appareil doit utiliser ces fonctionnalités en ce qui concerne une séquence particulière de documents, un document individuel ou une page individuelle.  
  
 Voici une séquence classique de tâches pour une application qui prend en charge l’impression.  
  
1. Déterminez les fonctionnalités d’une imprimante.  
  
2. Configurez un <xref:System.Printing.PrintTicket> pour utiliser ces fonctionnalités.  
  
3. Validez <xref:System.Printing.PrintTicket>.  
  
 Cet article explique comment procéder.  
  
## <a name="example"></a>Exemples  
 Dans l’exemple simple ci-dessous, nous nous intéressons uniquement si une imprimante peut prendre en charge l’impression recto-verso. Les étapes principales sont les suivantes.  
  
1. Obtient un <xref:System.Printing.PrintCapabilities> objet avec la <xref:System.Printing.PrintQueue.GetPrintCapabilities%2A> méthode.  
  
2. Testez la présence de la fonctionnalité de votre choix. Dans l’exemple ci-dessous, nous <xref:System.Printing.PrintCapabilities.DuplexingCapability%2A> testons la <xref:System.Printing.PrintCapabilities> propriété de l’objet pour la présence de la capacité d’impression des deux côtés d’une feuille de papier avec la «rotation de page» sur le côté long de la feuille. Étant <xref:System.Printing.PrintCapabilities.DuplexingCapability%2A> donné que est une collection, nous `Contains` utilisons la <xref:System.Collections.ObjectModel.ReadOnlyCollection%601>méthode de.  
  
    > [!NOTE]
    > Cette étape n’est pas strictement nécessaire. La <xref:System.Printing.PrintQueue.MergeAndValidatePrintTicket%2A> méthode utilisée ci-dessous vérifie chaque requête dans <xref:System.Printing.PrintTicket> le par rapport aux fonctionnalités de l’imprimante. Si la fonctionnalité demandée n’est pas prise en charge par l’imprimante, le pilote d’imprimante remplace une <xref:System.Printing.PrintTicket> autre requête dans le retourné par la méthode.  
  
3. Si l’imprimante prend en charge l’impression recto-verso <xref:System.Printing.PrintTicket> , l’exemple de code crée un qui demande un duplex. Toutefois, l’application ne spécifie pas tous les paramètres d’imprimante <xref:System.Printing.PrintTicket> possibles disponibles dans l’élément. Cela serait gaspiller le programmeur et le temps de programmation. Au lieu de cela, le code définit uniquement la demande de duplexage, <xref:System.Printing.PrintTicket> puis fusionne avec un existant, entièrement configuré <xref:System.Printing.PrintTicket>et validé,, dans ce cas, la <xref:System.Printing.PrintTicket>valeur par défaut de l’utilisateur.  
  
4. En conséquence, l’exemple appelle <xref:System.Printing.PrintQueue.MergeAndValidatePrintTicket%2A> la méthode pour fusionner le nouveau, <xref:System.Printing.PrintTicket> minimal, avec la valeur <xref:System.Printing.PrintTicket>par défaut de l’utilisateur. Cela retourne un <xref:System.Printing.ValidationResult> qui comprend le nouveau <xref:System.Printing.PrintTicket> comme l’une de ses propriétés.  
  
5. L’exemple teste ensuite les nouvelles <xref:System.Printing.PrintTicket> demandes en duplex. Si c’est le cas, l’exemple en fait le nouveau ticket d’impression par défaut pour l’utilisateur. Si l’étape 2 ci-dessus avait été omise et que l’imprimante ne prenait pas en charge le duplexeur sur le long terme, `false`le test aurait abouti. (Voir la remarque ci-dessus.)  
  
6. La dernière étape importante consiste à valider la modification apportée à <xref:System.Printing.PrintQueue.UserPrintTicket%2A> la <xref:System.Printing.PrintQueue> propriété de <xref:System.Printing.PrintQueue.Commit%2A> avec la méthode.  
  
 [!code-csharp[PrintTicketManagment#UsingMergeAndValidate](~/samples/snippets/csharp/VS_Snippets_Wpf/PrintTicketManagment/CSharp/printticket.cs#usingmergeandvalidate)]
 [!code-vb[PrintTicketManagment#UsingMergeAndValidate](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PrintTicketManagment/visualbasic/printticket.vb#usingmergeandvalidate)]  
  
 Pour que vous puissiez tester rapidement cet exemple, le reste de l’exemple est présenté ci-dessous. Créez un projet et un espace de noms, puis collez les deux extraits de code dans cet article dans le bloc d’espace de noms.  
  
 [!code-csharp[PrintTicketManagment#UIForMergeAndValidatePTUtility](~/samples/snippets/csharp/VS_Snippets_Wpf/PrintTicketManagment/CSharp/printticket.cs#uiformergeandvalidateptutility)]
 [!code-vb[PrintTicketManagment#UIForMergeAndValidatePTUtility](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PrintTicketManagment/visualbasic/printticket.vb#uiformergeandvalidateptutility)]  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Printing.PrintCapabilities>
- <xref:System.Printing.PrintTicket>
- <xref:System.Printing.PrintServer.GetPrintQueues%2A>
- <xref:System.Printing.PrintServer>
- <xref:System.Printing.EnumeratedPrintQueueTypes>
- <xref:System.Printing.PrintQueue>
- <xref:System.Printing.PrintQueue.GetPrintCapabilities%2A>
- [Documents dans WPF](documents-in-wpf.md)
- [Vue d’ensemble de l’impression](printing-overview.md)
- [Schéma d’impression](https://go.microsoft.com/fwlink/?LinkId=186397)
