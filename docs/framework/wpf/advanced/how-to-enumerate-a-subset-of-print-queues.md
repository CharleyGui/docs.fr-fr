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
# <a name="how-to-enumerate-a-subset-of-print-queues"></a>Comment : énumérer un sous-ensemble de files d'attente à l'impression
Une situation courante rencontrée par les professionnels de l’informatique qui gèrent un ensemble d’imprimantes à l’ensemble de l’entreprise consiste à générer une liste d’imprimantes présentant certaines caractéristiques. Cette fonctionnalité est fournie par la méthode <xref:System.Printing.PrintServer.GetPrintQueues%2A> d’un objet <xref:System.Printing.PrintServer> et de l’énumération <xref:System.Printing.EnumeratedPrintQueueTypes>.  
  
## <a name="example"></a>Exemple  
 Dans l’exemple ci-dessous, le code commence par créer un tableau d’indicateurs qui spécifient les caractéristiques des files d’attente à l’impression que vous souhaitez répertorier. Dans cet exemple, nous recherchons des files d’attente à l’impression qui sont installées localement sur le serveur d’impression et qui sont partagées. L’énumération <xref:System.Printing.EnumeratedPrintQueueTypes> offre de nombreuses autres possibilités.  
  
 Le code crée ensuite un objet <xref:System.Printing.LocalPrintServer>, une classe dérivée de <xref:System.Printing.PrintServer>. Le serveur d’impression local est l’ordinateur sur lequel l’application s’exécute.  
  
 La dernière étape importante consiste à passer le tableau à la méthode <xref:System.Printing.PrintServer.GetPrintQueues%2A>.  
  
 Enfin, les résultats sont présentés à l’utilisateur.  
  
 [!code-cpp[EnumerateSubsetOfPrintQueues#ListSubsetOfPrintQueues](~/samples/snippets/cpp/VS_Snippets_Wpf/EnumerateSubsetOfPrintQueues/CPP/Program.cpp#listsubsetofprintqueues)]
 [!code-csharp[EnumerateSubsetOfPrintQueues#ListSubsetOfPrintQueues](~/samples/snippets/csharp/VS_Snippets_Wpf/EnumerateSubsetOfPrintQueues/CSharp/Program.cs#listsubsetofprintqueues)]
 [!code-vb[EnumerateSubsetOfPrintQueues#ListSubsetOfPrintQueues](~/samples/snippets/visualbasic/VS_Snippets_Wpf/EnumerateSubsetOfPrintQueues/visualbasic/program.vb#listsubsetofprintqueues)]  
  
 Vous pouvez étendre cet exemple en faisant en sorte que la `foreach` boucle qui parcourt chaque file d’attente à l’impression effectue un filtrage supplémentaire. Par exemple, vous pouvez filtrer les imprimantes qui ne prennent pas en charge l’impression recto-verso en faisant appel à la boucle pour chaque méthode <xref:System.Printing.PrintQueue.GetPrintCapabilities%2A> de la file d’attente à l’impression et tester la valeur renvoyée pour la présence du duplex.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Printing.PrintServer.GetPrintQueues%2A>
- <xref:System.Printing.PrintServer>
- <xref:System.Printing.LocalPrintServer>
- <xref:System.Printing.EnumeratedPrintQueueTypes>
- <xref:System.Printing.PrintQueue>
- <xref:System.Printing.PrintQueue.GetPrintCapabilities%2A>
- [Documents dans WPF](documents-in-wpf.md)
- [Vue d’ensemble de l’impression](printing-overview.md)
- [Microsoft XPS document Writer](/windows/win32/printdocs/microsoft-xps-document-writer)
