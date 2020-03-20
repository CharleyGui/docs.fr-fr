---
title: "Comment : diagnostiquer un travail d'impression problématique"
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- troubleshooting print job problems [WPF]
- print jobs [WPF], troubleshooting
- print jobs [WPF], diagnosing problems
ms.assetid: b081a170-84c6-48f9-a487-5766a8d58a82
ms.openlocfilehash: 15de5d9ec8dc4016753b9d4cbed6fb0c64571774
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186047"
---
# <a name="how-to-diagnose-problematic-print-job"></a>Comment : diagnostiquer un travail d'impression problématique
Les administrateurs réseau reçoivent souvent des plaintes d’utilisateurs concernant des travaux d’impression qui échouent ou s’impriment lentement. Le riche ensemble de propriétés d’emploi d’impression exposées dans les API de Microsoft .NET Framework fournissent un moyen d’effectuer un diagnostic rapide à distance des travaux d’impression.  
  
## <a name="example"></a> Exemple  
 Voici les principales étapes à suivre pour créer ce type d’utilitaire.  
  
1. Identifiez le travail d’impression à l’origine de la plainte de l’utilisateur. Les utilisateurs sont rarement en mesure de l’identifier avec précision. Ils peuvent par exemple ne pas connaître les noms des serveurs d’impression ou des imprimantes. Ils peuvent décrire l’emplacement de l’imprimante dans <xref:System.Printing.PrintQueue.Location%2A> une terminologie différente de celle utilisée pour définir sa propriété. Par conséquent, il est judicieux de générer une liste des travaux envoyés par l’utilisateur. S’il y en a plusieurs, l’utilisateur peut contacter l’administrateur du système d’impression pour identifier le travail qui pose problème. La procédure est la suivante.  
  
    1. Répertoriez l’ensemble des serveurs d’impression.  
  
    2. Parcourez les serveurs en boucle pour interroger leurs files d’attente à l’impression.  
  
    3. À chaque étape de la boucle de serveur, parcourez en boucle toutes les files d’attente du serveur pour interroger les travaux associés.  
  
    4. À chaque étape de la boucle de file d’attente, parcourez les travaux associés et collectez les informations d’identification des travaux ayant été envoyés par l’utilisateur à l’origine de la plainte.  
  
2. Une fois le travail d’impression problématique identifié, examinez les propriétés pertinentes pour tenter de trouver ce qui pose problème. Le travail affiche-t-il un état d’erreur ou l’imprimante qui traite la file d’attente a-t-elle été déconnectée avant l’impression du travail ?  
  
 Le code ci-dessous constitue une série d’exemples de code. Le premier exemple de code contient la boucle d’exécution des files d’attente à l’impression. (Étape 1c ci-dessus.) La `myPrintQueues` variable <xref:System.Printing.PrintQueueCollection> est l’objet pour le serveur d’impression actuel.  
  
 L’exemple de code commence par <xref:System.Printing.PrintQueue.Refresh%2A?displayProperty=nameWithType>rafraîchir l’objet actuel de file d’attente d’impression avec . Cela permet de s’assurer que les propriétés de l’objet représentent avec exactitude l’état de l’imprimante physique à laquelle l’objet est associé. Ensuite, l’application obtient la collection de travaux <xref:System.Printing.PrintQueue.GetPrintJobInfoCollection%2A>d’impression actuellement dans la file d’attente d’impression en utilisant .  
  
 Ensuite, l’application <xref:System.Printing.PrintSystemJobInfo> boucle à travers <xref:System.Printing.PrintSystemJobInfo.Submitter%2A> la collection et compare chaque propriété avec le pseudonyme de l’utilisateur plaignant. En cas de correspondance, l’application ajoute les informations d’identification sur le travail dans la chaîne qui s’affiche. (Les variables `userName` et `jobList` sont initialisées plus tôt dans l’application.)  
  
 [!code-cpp[DiagnoseProblematicPrintJob#EnumerateJobsInQueues](~/samples/snippets/cpp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CPP/Program.cpp#enumeratejobsinqueues)]
 [!code-csharp[DiagnoseProblematicPrintJob#EnumerateJobsInQueues](~/samples/snippets/csharp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CSharp/Program.cs#enumeratejobsinqueues)]
 [!code-vb[DiagnoseProblematicPrintJob#EnumerateJobsInQueues](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/visualbasic/program.vb#enumeratejobsinqueues)]  
  
 L’exemple de code suivant récupère l’application à l’étape 2. (Voir ci-dessus.) Le travail problématique a été identifié et la demande invite à l’information qui l’identifiera. A partir de <xref:System.Printing.PrintServer> <xref:System.Printing.PrintQueue>cette <xref:System.Printing.PrintSystemJobInfo> information, il crée , , et des objets.  
  
 À ce stade, l’application contient une structure en branches correspondant aux deux méthodes de vérification de l’état du travail d’impression :  
  
- Vous pouvez lire les <xref:System.Printing.PrintSystemJobInfo.JobStatus%2A> drapeaux de <xref:System.Printing.PrintJobStatus>la propriété qui est de type .  
  
- Vous pouvez lire chaque <xref:System.Printing.PrintSystemJobInfo.IsBlocked%2A> propriété <xref:System.Printing.PrintSystemJobInfo.IsInError%2A>pertinente telle que et .  
  
 Cet exemple montre les deux méthodes, de sorte que l’utilisateur a été précédemment invité à quelle <xref:System.Printing.PrintSystemJobInfo.JobStatus%2A> méthode à utiliser et a répondu avec "Y" s’ils voulaient utiliser les drapeaux de la propriété. Voir ci-dessous pour obtenir des informations détaillées sur les deux méthodes. Enfin, l’application utilise une méthode appelée **ReportQueueAndJobAvailability** pour déterminer si le travail peut être imprimé à cette heure de la journée. Cette méthode est décrite dans l’article [Déterminer si un travail d’impression peut être imprimé à cette heure de la journée](how-to-discover-whether-a-print-job-can-be-printed-at-this-time-of-day.md).  
  
 [!code-cpp[DiagnoseProblematicPrintJob#IdentifyAndDiagnoseProblematicJob](~/samples/snippets/cpp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CPP/Program.cpp#identifyanddiagnoseproblematicjob)]
 [!code-csharp[DiagnoseProblematicPrintJob#IdentifyAndDiagnoseProblematicJob](~/samples/snippets/csharp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CSharp/Program.cs#identifyanddiagnoseproblematicjob)]
 [!code-vb[DiagnoseProblematicPrintJob#IdentifyAndDiagnoseProblematicJob](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/visualbasic/program.vb#identifyanddiagnoseproblematicjob)]  
  
 Pour vérifier l’état d’impression de travail en utilisant les drapeaux de la <xref:System.Printing.PrintSystemJobInfo.JobStatus%2A> propriété, vous vérifiez chaque drapeau pertinent pour voir si elle est définie. La méthode standard pour voir si un bit est défini dans un ensemble d’indicateurs binaires consiste à effectuer une opération AND logique en utilisant comme opérandes l’ensemble d’indicateurs et l’indicateur lui-même. Étant donné que l’indicateur lui-même n’a qu’un seul bit de défini, l’opération AND logique ne peut pas trouver plus d’un même bit défini. Pour savoir si c’est bien le cas, il suffit de comparer le résultat de l’opération AND logique avec l’indicateur lui-même. Pour plus d’informations, voir <xref:System.Printing.PrintJobStatus>, [l’opérateur& (référence C)](../../../csharp/language-reference/operators/bitwise-and-shift-operators.md#logical-and-operator-), et <xref:System.FlagsAttribute>.  
  
 Pour chaque attribut dont le bit est défini, le code l’indique sur l’écran de la console et propose parfois une réponse possible. (La méthode **HandlePausedJob** qui est appelée si le travail ou la file d’attente est suspendu(e) est décrite ci-après.)  
  
 [!code-cpp[DiagnoseProblematicPrintJob#SpotTroubleUsingJobAttributes](~/samples/snippets/cpp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CPP/Program.cpp#spottroubleusingjobattributes)]
 [!code-csharp[DiagnoseProblematicPrintJob#SpotTroubleUsingJobAttributes](~/samples/snippets/csharp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CSharp/Program.cs#spottroubleusingjobattributes)]
 [!code-vb[DiagnoseProblematicPrintJob#SpotTroubleUsingJobAttributes](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/visualbasic/program.vb#spottroubleusingjobattributes)]  
  
 Pour vérifier l’état du travail d’impression à l’aide de propriétés distinctes, il vous suffit de lire chaque propriété, et si la propriété est `true`, de l’indiquer sur l’écran de la console et de proposer éventuellement une réponse possible. (La méthode **HandlePausedJob** qui est appelée si le travail ou la file d’attente est suspendu(e) est décrite ci-après.)  
  
 [!code-cpp[DiagnoseProblematicPrintJob#SpotTroubleUsingJobProperties](~/samples/snippets/cpp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CPP/Program.cpp#spottroubleusingjobproperties)]
 [!code-csharp[DiagnoseProblematicPrintJob#SpotTroubleUsingJobProperties](~/samples/snippets/csharp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CSharp/Program.cs#spottroubleusingjobproperties)]
 [!code-vb[DiagnoseProblematicPrintJob#SpotTroubleUsingJobProperties](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/visualbasic/program.vb#spottroubleusingjobproperties)]  
  
 La méthode **HandlePausedJob** permet à l’utilisateur de l’application de relancer à distance des travaux suspendus. Les files d’attente à l’impression étant généralement interrompues pour une bonne raison, la méthode commence par demander à l’utilisateur s’il souhaite la relancer ou non. Si la réponse est "Y", alors la <xref:System.Printing.PrintQueue.Resume%2A?displayProperty=nameWithType> méthode est appelée.  
  
 Ensuite, l’utilisateur doit décider si le travail lui-même doit reprendre, au cas où il aurait été suspendu indépendamment de la file d’attente à l’impression. (Comparer <xref:System.Printing.PrintQueue.IsPaused%2A?displayProperty=nameWithType> <xref:System.Printing.PrintSystemJobInfo.IsPaused%2A?displayProperty=nameWithType>et .) Si la réponse est <xref:System.Printing.PrintSystemJobInfo.Resume%2A?displayProperty=nameWithType> "Y", alors est appelé; autrement <xref:System.Printing.PrintSystemJobInfo.Cancel%2A> est appelé.  
  
 [!code-cpp[DiagnoseProblematicPrintJob#HandlePausedJob](~/samples/snippets/cpp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CPP/Program.cpp#handlepausedjob)]
 [!code-csharp[DiagnoseProblematicPrintJob#HandlePausedJob](~/samples/snippets/csharp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CSharp/Program.cs#handlepausedjob)]
 [!code-vb[DiagnoseProblematicPrintJob#HandlePausedJob](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/visualbasic/program.vb#handlepausedjob)]  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Printing.PrintJobStatus>
- <xref:System.Printing.PrintSystemJobInfo>
- <xref:System.FlagsAttribute>
- <xref:System.Printing.PrintQueue>
- [& opérateur (référence C)](../../../csharp/language-reference/operators/bitwise-and-shift-operators.md#logical-and-operator-)
- [Documents dans WPF](documents-in-wpf.md)
- [Vue d'ensemble de l'impression](printing-overview.md)
