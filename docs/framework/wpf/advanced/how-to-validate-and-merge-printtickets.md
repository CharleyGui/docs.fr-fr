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
ms.openlocfilehash: bd7f399555b343a52ec6f36aa3b8c706747d8b06
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/09/2020
ms.locfileid: "77094525"
---
# <a name="how-to-validate-and-merge-printtickets"></a>Comment : valider et fusionner des PrintTicket
Le schéma d' [impression](/windows/win32/printdocs/printschema) Microsoft Windows comprend les éléments <xref:System.Printing.PrintCapabilities> et <xref:System.Printing.PrintTicket> flexibles et extensibles. Le premier détaille les fonctionnalités d’un périphérique d’impression et le dernier spécifie comment l’appareil doit utiliser ces fonctionnalités en ce qui concerne une séquence particulière de documents, un document individuel ou une page individuelle.  
  
 Voici une séquence classique de tâches pour une application qui prend en charge l’impression.  
  
1. Déterminez les fonctionnalités d’une imprimante.  
  
2. Configurez un <xref:System.Printing.PrintTicket> pour utiliser ces fonctionnalités.  
  
3. Validez le <xref:System.Printing.PrintTicket>.  
  
 Cet article explique comment procéder.  
  
## <a name="example"></a>Exemple  
 Dans l’exemple simple ci-dessous, nous nous intéressons uniquement si une imprimante peut prendre en charge l’impression recto-verso. Les étapes principales sont les suivantes.  
  
1. Obtient un objet <xref:System.Printing.PrintCapabilities> avec la méthode <xref:System.Printing.PrintQueue.GetPrintCapabilities%2A>.  
  
2. Testez la présence de la fonctionnalité de votre choix. Dans l’exemple ci-dessous, nous testons la propriété <xref:System.Printing.PrintCapabilities.DuplexingCapability%2A> de l’objet <xref:System.Printing.PrintCapabilities> pour la présence de la possibilité d’imprimer sur les deux côtés d’une feuille de papier avec la « rotation de page » sur le côté long de la feuille. Étant donné que <xref:System.Printing.PrintCapabilities.DuplexingCapability%2A> est une collection, nous utilisons la méthode `Contains` de <xref:System.Collections.ObjectModel.ReadOnlyCollection%601>.  
  
    > [!NOTE]
    > Cette étape n’est pas strictement nécessaire. La méthode <xref:System.Printing.PrintQueue.MergeAndValidatePrintTicket%2A> utilisée ci-dessous vérifie chaque demande dans la <xref:System.Printing.PrintTicket> par rapport aux fonctionnalités de l’imprimante. Si la capacité demandée n’est pas prise en charge par l’imprimante, le pilote d’imprimante remplace une autre requête dans le <xref:System.Printing.PrintTicket> retourné par la méthode.  
  
3. Si l’imprimante prend en charge l’impression recto-verso, l’exemple de code crée une <xref:System.Printing.PrintTicket> qui demande un duplex. Toutefois, l’application ne spécifie pas tous les paramètres d’imprimante possibles disponibles dans l’élément <xref:System.Printing.PrintTicket>. Cela serait gaspiller le programmeur et le temps de programmation. Au lieu de cela, le code définit uniquement la demande de duplexage, puis fusionne ce <xref:System.Printing.PrintTicket> avec une <xref:System.Printing.PrintTicket>existante, entièrement configurée et validée, dans ce cas, le <xref:System.Printing.PrintTicket>par défaut de l’utilisateur.  
  
4. En conséquence, l’exemple appelle la méthode <xref:System.Printing.PrintQueue.MergeAndValidatePrintTicket%2A> pour fusionner le nouveau, minimal <xref:System.Printing.PrintTicket> avec le <xref:System.Printing.PrintTicket>par défaut de l’utilisateur. Cela retourne un <xref:System.Printing.ValidationResult> qui comprend le nouveau <xref:System.Printing.PrintTicket> comme l’une de ses propriétés.  
  
5. L’exemple teste ensuite que la nouvelle <xref:System.Printing.PrintTicket> demande le duplexage. Si c’est le cas, l’exemple en fait le nouveau ticket d’impression par défaut pour l’utilisateur. Si l’étape 2 ci-dessus avait été omise et que l’imprimante ne prenait pas en charge le duplexeur sur la longue partie, le test aurait abouti à `false`. (Voir la remarque ci-dessus.)  
  
6. La dernière étape importante consiste à valider la modification apportée à la propriété <xref:System.Printing.PrintQueue.UserPrintTicket%2A> du <xref:System.Printing.PrintQueue> avec la méthode <xref:System.Printing.PrintQueue.Commit%2A>.  
  
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
- [Schéma d’impression](/windows/win32/printdocs/printschema)
