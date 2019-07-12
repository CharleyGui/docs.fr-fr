---
title: 'Procédure : Diagnostiquer un travail d’impression problématique'
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
ms.openlocfilehash: d64e77b7fc6862eead3cb7e791b3a8f68ac52713
ms.sourcegitcommit: 83ecdf731dc1920bca31f017b1556c917aafd7a0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/12/2019
ms.locfileid: "67859731"
---
# <a name="how-to-diagnose-problematic-print-job"></a>Procédure : Diagnostiquer un travail d’impression problématique
Les administrateurs réseau reçoivent souvent des plaintes d’utilisateurs concernant des travaux d’impression qui échouent ou s’impriment lentement. L’ensemble des propriétés de travail d’impression exposées dans l’API de Microsoft .NET Framework fournissent un moyen pour effectuer un diagnostic rapide et à distance des travaux d’impression.  
  
## <a name="example"></a>Exemples  
 Voici les principales étapes à suivre pour créer ce type d’utilitaire.  
  
1. Identifiez le travail d’impression à l’origine de la plainte de l’utilisateur. Les utilisateurs sont rarement en mesure de l’identifier avec précision. Ils peuvent par exemple ne pas connaître les noms des serveurs d’impression ou des imprimantes. Ils peuvent décrire l’emplacement de l’imprimante avec une terminologie différente de celle utilisée dans le paramètre son <xref:System.Printing.PrintQueue.Location%2A> propriété. Par conséquent, il est judicieux de générer une liste des travaux envoyés par l’utilisateur. S’il y en a plusieurs, l’utilisateur peut contacter l’administrateur du système d’impression pour identifier le travail qui pose problème. La procédure est la suivante.  
  
    1. Répertoriez l’ensemble des serveurs d’impression.  
  
    2. Parcourez les serveurs en boucle pour interroger leurs files d’attente à l’impression.  
  
    3. À chaque étape de la boucle de serveur, parcourez en boucle toutes les files d’attente du serveur pour interroger les travaux associés.  
  
    4. À chaque étape de la boucle de file d’attente, parcourez les travaux associés et collectez les informations d’identification des travaux ayant été envoyés par l’utilisateur à l’origine de la plainte.  
  
2. Une fois le travail d’impression problématique identifié, examinez les propriétés pertinentes pour tenter de trouver ce qui pose problème. Le travail affiche-t-il un état d’erreur ou l’imprimante qui traite la file d’attente a-t-elle été déconnectée avant l’impression du travail ?  
  
 Le code ci-dessous constitue une série d’exemples de code. Le premier exemple de code contient la boucle d’exécution des files d’attente à l’impression. (Étape 1c ci-dessus.) La variable `myPrintQueues` est le <xref:System.Printing.PrintQueueCollection> objet pour le serveur d’impression en cours.  
  
 L’exemple de code commence par actualiser l’objet actuel de la file d’attente avec <xref:System.Printing.PrintQueue.Refresh%2A?displayProperty=nameWithType>. Cela permet de s’assurer que les propriétés de l’objet représentent avec exactitude l’état de l’imprimante physique à laquelle l’objet est associé. Ensuite, l’application obtient la collection de travaux d’impression actuellement dans la file d’attente à l’aide de <xref:System.Printing.PrintQueue.GetPrintJobInfoCollection%2A>.  
  
 Ensuite l’application parcourt en boucle le <xref:System.Printing.PrintSystemJobInfo> collection et les compare <xref:System.Printing.PrintSystemJobInfo.Submitter%2A> propriété avec l’alias de l’utilisateur plainte. En cas de correspondance, l’application ajoute les informations d’identification sur le travail dans la chaîne qui s’affiche. (Les variables `userName` et `jobList` sont initialisées plus tôt dans l’application.)  
  
 [!code-cpp[DiagnoseProblematicPrintJob#EnumerateJobsInQueues](~/samples/snippets/cpp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CPP/Program.cpp#enumeratejobsinqueues)]
 [!code-csharp[DiagnoseProblematicPrintJob#EnumerateJobsInQueues](~/samples/snippets/csharp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CSharp/Program.cs#enumeratejobsinqueues)]
 [!code-vb[DiagnoseProblematicPrintJob#EnumerateJobsInQueues](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/visualbasic/program.vb#enumeratejobsinqueues)]  
  
 L’exemple de code suivant récupère l’application à l’étape 2. (Voir ci-dessus). Le travail problématique a été identifié et l’application demande les informations d’identification correspondantes. À partir de ces informations, il crée <xref:System.Printing.PrintServer>, <xref:System.Printing.PrintQueue>, et <xref:System.Printing.PrintSystemJobInfo> objets.  
  
 À ce stade, l’application contient une structure en branches correspondant aux deux méthodes de vérification de l’état du travail d’impression :  
  
- Vous pouvez lire les indicateurs de la <xref:System.Printing.PrintSystemJobInfo.JobStatus%2A> propriété qui est de type <xref:System.Printing.PrintJobStatus>.  
  
- Vous pouvez lire chaque propriété pertinente comme <xref:System.Printing.PrintSystemJobInfo.IsBlocked%2A> et <xref:System.Printing.PrintSystemJobInfo.IsInError%2A>.  
  
 Cet exemple illustre les deux méthodes, l’utilisateur a été auparavant invité à choisir la méthode à utiliser et a répondu par « Y » qu’il souhaitait utiliser les indicateurs de le <xref:System.Printing.PrintSystemJobInfo.JobStatus%2A> propriété. Voir ci-dessous pour obtenir des informations détaillées sur les deux méthodes. Enfin, l’application utilise une méthode appelée **ReportQueueAndJobAvailability** pour déterminer si le travail peut être imprimé à cette heure de la journée. Cette méthode est décrite dans l’article [Déterminer si un travail d’impression peut être imprimé à cette heure de la journée](how-to-discover-whether-a-print-job-can-be-printed-at-this-time-of-day.md).  
  
 [!code-cpp[DiagnoseProblematicPrintJob#IdentifyAndDiagnoseProblematicJob](~/samples/snippets/cpp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CPP/Program.cpp#identifyanddiagnoseproblematicjob)]
 [!code-csharp[DiagnoseProblematicPrintJob#IdentifyAndDiagnoseProblematicJob](~/samples/snippets/csharp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CSharp/Program.cs#identifyanddiagnoseproblematicjob)]
 [!code-vb[DiagnoseProblematicPrintJob#IdentifyAndDiagnoseProblematicJob](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/visualbasic/program.vb#identifyanddiagnoseproblematicjob)]  
  
 Pour vérifier l’état du travail d’impression à l’aide des indicateurs de le <xref:System.Printing.PrintSystemJobInfo.JobStatus%2A> propriété, vérifier chaque indicateur correspondant pour voir si elle est définie. La méthode standard pour voir si un bit est défini dans un ensemble d’indicateurs binaires consiste à effectuer une opération AND logique en utilisant comme opérandes l’ensemble d’indicateurs et l’indicateur lui-même. Étant donné que l’indicateur lui-même n’a qu’un seul bit de défini, l’opération AND logique ne peut pas trouver plus d’un même bit défini. Pour savoir si c’est bien le cas, il suffit de comparer le résultat de l’opération AND logique avec l’indicateur lui-même. Pour plus d’informations, consultez <xref:System.Printing.PrintJobStatus>, le [& opérateur (C# référence)](~/docs/csharp/language-reference/operators/bitwise-and-shift-operators.md#logical-and-operator-), et <xref:System.FlagsAttribute>.  
  
 Pour chaque attribut dont le bit est défini, le code l’indique sur l’écran de la console et propose parfois une réponse possible. (La méthode **HandlePausedJob** qui est appelée si le travail ou la file d’attente est suspendu(e) est décrite ci-après.)  
  
 [!code-cpp[DiagnoseProblematicPrintJob#SpotTroubleUsingJobAttributes](~/samples/snippets/cpp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CPP/Program.cpp#spottroubleusingjobattributes)]
 [!code-csharp[DiagnoseProblematicPrintJob#SpotTroubleUsingJobAttributes](~/samples/snippets/csharp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CSharp/Program.cs#spottroubleusingjobattributes)]
 [!code-vb[DiagnoseProblematicPrintJob#SpotTroubleUsingJobAttributes](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/visualbasic/program.vb#spottroubleusingjobattributes)]  
  
 Pour vérifier l’état du travail d’impression à l’aide de propriétés distinctes, il vous suffit de lire chaque propriété, et si la propriété est `true`, de l’indiquer sur l’écran de la console et de proposer éventuellement une réponse possible. (La méthode **HandlePausedJob** qui est appelée si le travail ou la file d’attente est suspendu(e) est décrite ci-après.)  
  
 [!code-cpp[DiagnoseProblematicPrintJob#SpotTroubleUsingJobProperties](~/samples/snippets/cpp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CPP/Program.cpp#spottroubleusingjobproperties)]
 [!code-csharp[DiagnoseProblematicPrintJob#SpotTroubleUsingJobProperties](~/samples/snippets/csharp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CSharp/Program.cs#spottroubleusingjobproperties)]
 [!code-vb[DiagnoseProblematicPrintJob#SpotTroubleUsingJobProperties](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/visualbasic/program.vb#spottroubleusingjobproperties)]  
  
 La méthode **HandlePausedJob** permet à l’utilisateur de l’application de relancer à distance des travaux suspendus. Les files d’attente à l’impression étant généralement interrompues pour une bonne raison, la méthode commence par demander à l’utilisateur s’il souhaite la relancer ou non. Si la réponse est « Y », puis le <xref:System.Printing.PrintQueue.Resume%2A?displayProperty=nameWithType> méthode est appelée.  
  
 Ensuite, l’utilisateur doit décider si le travail lui-même doit reprendre, au cas où il aurait été suspendu indépendamment de la file d’attente à l’impression. (Comparez <xref:System.Printing.PrintQueue.IsPaused%2A?displayProperty=nameWithType> et <xref:System.Printing.PrintSystemJobInfo.IsPaused%2A?displayProperty=nameWithType>.) Si la réponse est « Y », puis <xref:System.Printing.PrintSystemJobInfo.Resume%2A?displayProperty=nameWithType> est appelée ; sinon <xref:System.Printing.PrintSystemJobInfo.Cancel%2A> est appelée.  
  
 [!code-cpp[DiagnoseProblematicPrintJob#HandlePausedJob](~/samples/snippets/cpp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CPP/Program.cpp#handlepausedjob)]
 [!code-csharp[DiagnoseProblematicPrintJob#HandlePausedJob](~/samples/snippets/csharp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CSharp/Program.cs#handlepausedjob)]
 [!code-vb[DiagnoseProblematicPrintJob#HandlePausedJob](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/visualbasic/program.vb#handlepausedjob)]  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Printing.PrintJobStatus>
- <xref:System.Printing.PrintSystemJobInfo>
- <xref:System.FlagsAttribute>
- <xref:System.Printing.PrintQueue>
- [& Opérateur (C# référence)](~/docs/csharp/language-reference/operators/bitwise-and-shift-operators.md#logical-and-operator-)
- [Documents dans WPF](documents-in-wpf.md)
- [Vue d’ensemble de l’impression](printing-overview.md)
