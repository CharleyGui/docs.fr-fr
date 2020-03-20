---
title: "Comment : observer à distance l'état d'imprimantes"
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- surveying printer status remotely [WPF]
- printer status [WPF], surveying remotely
- remotely surveying printer status [WPF]
- status [WPF], printers [WPF], surveying remotely
ms.assetid: d6324759-8292-4c23-9584-9c708887dc94
ms.openlocfilehash: 859ccb703c6c54c66d6ea7b433c67d156627e25b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187037"
---
# <a name="how-to-remotely-survey-the-status-of-printers"></a>Comment : observer à distance l'état d'imprimantes
Dans les moyennes et grandes entreprises, il peut arriver à tout moment que plusieurs imprimantes ne fonctionnent pas en raison d’un bourrage papier, d’un manque de papier ou d’un autre problème. Le riche ensemble de propriétés d’imprimantes exposées dans les API de Microsoft .NET Framework fournissent un moyen d’effectuer une étude rapide des états des imprimantes.  
  
## <a name="example"></a> Exemple  
 Voici les principales étapes à suivre pour créer ce type d’utilitaire.  
  
1. Répertoriez l’ensemble des serveurs d’impression.  
  
2. Parcourez les serveurs en boucle pour interroger leurs files d’attente à l’impression.  
  
3. À chaque étape de la boucle de serveur, parcourez en boucle toutes les files d’attente du serveur et lisez chaque propriété pouvant indiquer que la file d’attente ne fonctionne pas actuellement.  
  
 Le code ci-dessous est une série d’extraits de code. Pour plus de simplicité, cet exemple suppose qu’il existe une liste de serveurs d’impression délimitée par des caractères CRLF (retour chariot-saut de ligne). La `fileOfPrintServers` variable <xref:System.IO.StreamReader> est un objet pour ce fichier. Puisque chaque nom de serveur est sur <xref:System.IO.StreamReader.ReadLine%2A> sa propre ligne, n’importe quel appel de obtient le nom du serveur suivant et déplace le <xref:System.IO.StreamReader>curseur de 's au début de la ligne suivante.  
  
 Dans la boucle extérieure, <xref:System.Printing.PrintServer> le code crée un objet pour le dernier serveur d’impression et spécifie que l’application doit avoir des droits administratifs sur le serveur.  
  
> [!NOTE]
> S’il ya beaucoup de serveurs, vous pouvez <xref:System.Printing.PrintServer.%23ctor%28System.String%2CSystem.String%5B%5D%2CSystem.Printing.PrintSystemDesiredAccess%29> améliorer les performances en utilisant les constructeurs qui ne sont que l’initialisation des propriétés dont vous allez avoir besoin.  
  
 L’exemple <xref:System.Printing.PrintServer.GetPrintQueues%2A> sert ensuite à créer une collection de toutes les files d’attente du serveur et commence à boucler à travers eux. La boucle interne contient une structure en branches correspondant aux deux méthodes de vérification de l’état de l’imprimante :  
  
- Vous pouvez lire les <xref:System.Printing.PrintQueue.QueueStatus%2A> drapeaux de <xref:System.Printing.PrintQueueStatus>la propriété qui est de type .  
  
- Vous pouvez lire chaque <xref:System.Printing.PrintQueue.IsOutOfPaper%2A>propriété <xref:System.Printing.PrintQueue.IsPaperJammed%2A>pertinente telle que , et .  
  
 Cet exemple montre les deux méthodes, de sorte que l’utilisateur a été précédemment invité à quelle <xref:System.Printing.PrintQueue.QueueStatus%2A> méthode à utiliser et a répondu avec "y" s’ils voulaient utiliser les drapeaux de la propriété. Voir ci-dessous pour obtenir des informations détaillées sur les deux méthodes.  
  
 Enfin, les résultats sont présentés à l’utilisateur.  
  
 [!code-cpp[PrinterStatusSurvey#SurveyQueues](~/samples/snippets/cpp/VS_Snippets_Wpf/PrinterStatusSurvey/CPP/Program.cpp#surveyqueues)]
 [!code-csharp[PrinterStatusSurvey#SurveyQueues](~/samples/snippets/csharp/VS_Snippets_Wpf/PrinterStatusSurvey/CSharp/Program.cs#surveyqueues)]
 [!code-vb[PrinterStatusSurvey#SurveyQueues](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PrinterStatusSurvey/visualbasic/program.vb#surveyqueues)]  
  
 Pour vérifier l’état de <xref:System.Printing.PrintQueue.QueueStatus%2A> l’imprimante à l’aide des drapeaux de la propriété, vous vérifiez chaque drapeau pertinent pour voir s’il est défini. La méthode standard pour voir si un bit est défini dans un ensemble d’indicateurs binaires consiste à effectuer une opération AND logique en utilisant comme opérandes l’ensemble d’indicateurs et l’indicateur lui-même. Étant donné que l’indicateur lui-même n’a qu’un seul bit de défini, l’opération AND logique ne peut pas trouver plus d’un même bit défini. Pour savoir si c’est bien le cas, il suffit de comparer le résultat de l’opération AND logique avec l’indicateur lui-même. Pour plus d’informations, voir <xref:System.Printing.PrintQueueStatus>, [l’opérateur& (référence C)](../../../csharp/language-reference/operators/bitwise-and-shift-operators.md#logical-and-operator-), et <xref:System.FlagsAttribute>.  
  
 Pour chaque attribut dont le bit est défini, le code ajoute une note au rapport final qui sera présenté à l’utilisateur. (La méthode **ReportAvailabilityAtThisTime** qui est appelée à la fin du code est présentée ci-après.)  
  
 [!code-cpp[PrinterStatusSurvey#SpotTroubleUsingQueueAttributes](~/samples/snippets/cpp/VS_Snippets_Wpf/PrinterStatusSurvey/CPP/Program.cpp#spottroubleusingqueueattributes)]
 [!code-csharp[PrinterStatusSurvey#SpotTroubleUsingQueueAttributes](~/samples/snippets/csharp/VS_Snippets_Wpf/PrinterStatusSurvey/CSharp/Program.cs#spottroubleusingqueueattributes)]
 [!code-vb[PrinterStatusSurvey#SpotTroubleUsingQueueAttributes](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PrinterStatusSurvey/visualbasic/program.vb#spottroubleusingqueueattributes)]  
  
 Pour vérifier l’état de l’imprimante à l’aide de chaque propriété, il vous suffit de lire chaque propriété et d’ajouter une note au rapport final qui sera présenté à l’utilisateur si la propriété est `true`. (La méthode **ReportAvailabilityAtThisTime** qui est appelée à la fin du code est présentée ci-après.)  
  
 [!code-cpp[PrinterStatusSurvey#SpotTroubleUsingQueueProperties](~/samples/snippets/cpp/VS_Snippets_Wpf/PrinterStatusSurvey/CPP/Program.cpp#spottroubleusingqueueproperties)]
 [!code-csharp[PrinterStatusSurvey#SpotTroubleUsingQueueProperties](~/samples/snippets/csharp/VS_Snippets_Wpf/PrinterStatusSurvey/CSharp/Program.cs#spottroubleusingqueueproperties)]
 [!code-vb[PrinterStatusSurvey#SpotTroubleUsingQueueProperties](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PrinterStatusSurvey/visualbasic/program.vb#spottroubleusingqueueproperties)]  
  
 La méthode **ReportAvailabilityAtThisTime** a été créée au cas où vous devriez déterminer si la file d’attente est disponible à l’heure actuelle.  
  
 La méthode ne fera <xref:System.Printing.PrintQueue.StartTimeOfDay%2A> <xref:System.Printing.PrintQueue.UntilTimeOfDay%2A> rien si le et les propriétés sont égales; parce que dans ce cas, l’imprimante est disponible en tout temps. S’ils sont différents, la méthode obtient l’heure actuelle qui doit <xref:System.Printing.PrintQueue.StartTimeOfDay%2A> ensuite <xref:System.Printing.PrintQueue.UntilTimeOfDay%2A> être <xref:System.Int32>convertie en minutes totales après minuit parce que les propriétés et sont s représentant minutes-après-minuit, pas des <xref:System.DateTime> objets. Enfin, la méthode vérifie si l’heure actuelle se situe entre les heures de début et de fin.  
  
 [!code-cpp[PrinterStatusSurvey#UsingStartAndUntilTimes](~/samples/snippets/cpp/VS_Snippets_Wpf/PrinterStatusSurvey/CPP/Program.cpp#usingstartanduntiltimes)]
 [!code-csharp[PrinterStatusSurvey#UsingStartAndUntilTimes](~/samples/snippets/csharp/VS_Snippets_Wpf/PrinterStatusSurvey/CSharp/Program.cs#usingstartanduntiltimes)]
 [!code-vb[PrinterStatusSurvey#UsingStartAndUntilTimes](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PrinterStatusSurvey/visualbasic/program.vb#usingstartanduntiltimes)]  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Printing.PrintQueue.StartTimeOfDay%2A>
- <xref:System.Printing.PrintQueue.UntilTimeOfDay%2A>
- <xref:System.DateTime>
- <xref:System.Printing.PrintQueueStatus>
- <xref:System.FlagsAttribute>
- <xref:System.Printing.PrintServer.GetPrintQueues%2A>
- <xref:System.Printing.PrintServer>
- <xref:System.Printing.LocalPrintServer>
- <xref:System.Printing.EnumeratedPrintQueueTypes>
- <xref:System.Printing.PrintQueue>
- [& opérateur (référence C)](../../../csharp/language-reference/operators/bitwise-and-shift-operators.md#logical-and-operator-)
- [Documents dans WPF](documents-in-wpf.md)
- [Vue d'ensemble de l'impression](printing-overview.md)
