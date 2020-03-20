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
# <a name="how-to-remotely-survey-the-status-of-printers"></a><span data-ttu-id="2b23f-102">Comment : observer à distance l'état d'imprimantes</span><span class="sxs-lookup"><span data-stu-id="2b23f-102">How to: Remotely Survey the Status of Printers</span></span>
<span data-ttu-id="2b23f-103">Dans les moyennes et grandes entreprises, il peut arriver à tout moment que plusieurs imprimantes ne fonctionnent pas en raison d’un bourrage papier, d’un manque de papier ou d’un autre problème.</span><span class="sxs-lookup"><span data-stu-id="2b23f-103">At any given time at medium and large companies there may be multiple printers that are not working due to a paper jam or being out of paper or some other problematic situation.</span></span> <span data-ttu-id="2b23f-104">Le riche ensemble de propriétés d’imprimantes exposées dans les API de Microsoft .NET Framework fournissent un moyen d’effectuer une étude rapide des états des imprimantes.</span><span class="sxs-lookup"><span data-stu-id="2b23f-104">The rich set of printer properties exposed in the APIs of Microsoft .NET Framework provide a means for performing a rapid survey of the states of printers.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2b23f-105"> Exemple</span><span class="sxs-lookup"><span data-stu-id="2b23f-105">Example</span></span>  
 <span data-ttu-id="2b23f-106">Voici les principales étapes à suivre pour créer ce type d’utilitaire.</span><span class="sxs-lookup"><span data-stu-id="2b23f-106">The major steps for creating this kind of utility are as follows.</span></span>  
  
1. <span data-ttu-id="2b23f-107">Répertoriez l’ensemble des serveurs d’impression.</span><span class="sxs-lookup"><span data-stu-id="2b23f-107">Obtain a list of all print servers.</span></span>  
  
2. <span data-ttu-id="2b23f-108">Parcourez les serveurs en boucle pour interroger leurs files d’attente à l’impression.</span><span class="sxs-lookup"><span data-stu-id="2b23f-108">Loop through the servers to query their print queues.</span></span>  
  
3. <span data-ttu-id="2b23f-109">À chaque étape de la boucle de serveur, parcourez en boucle toutes les files d’attente du serveur et lisez chaque propriété pouvant indiquer que la file d’attente ne fonctionne pas actuellement.</span><span class="sxs-lookup"><span data-stu-id="2b23f-109">Within each pass of the server loop, loop through all the server's queues and read each property that might indicate that the queue is not currently working.</span></span>  
  
 <span data-ttu-id="2b23f-110">Le code ci-dessous est une série d’extraits de code.</span><span class="sxs-lookup"><span data-stu-id="2b23f-110">The code below is a series of snippets.</span></span> <span data-ttu-id="2b23f-111">Pour plus de simplicité, cet exemple suppose qu’il existe une liste de serveurs d’impression délimitée par des caractères CRLF (retour chariot-saut de ligne).</span><span class="sxs-lookup"><span data-stu-id="2b23f-111">For simplicity, this example assumes that there is a CRLF-delimited list of print servers.</span></span> <span data-ttu-id="2b23f-112">La `fileOfPrintServers` variable <xref:System.IO.StreamReader> est un objet pour ce fichier.</span><span class="sxs-lookup"><span data-stu-id="2b23f-112">The variable `fileOfPrintServers` is a <xref:System.IO.StreamReader> object for this file.</span></span> <span data-ttu-id="2b23f-113">Puisque chaque nom de serveur est sur <xref:System.IO.StreamReader.ReadLine%2A> sa propre ligne, n’importe quel appel de obtient le nom du serveur suivant et déplace le <xref:System.IO.StreamReader>curseur de 's au début de la ligne suivante.</span><span class="sxs-lookup"><span data-stu-id="2b23f-113">Since each server name is on its own line, any call of <xref:System.IO.StreamReader.ReadLine%2A> gets the name of the next server and moves the <xref:System.IO.StreamReader>'s cursor to the beginning of the next line.</span></span>  
  
 <span data-ttu-id="2b23f-114">Dans la boucle extérieure, <xref:System.Printing.PrintServer> le code crée un objet pour le dernier serveur d’impression et spécifie que l’application doit avoir des droits administratifs sur le serveur.</span><span class="sxs-lookup"><span data-stu-id="2b23f-114">Within the outer loop, the code creates a <xref:System.Printing.PrintServer> object for the latest print server and specifies that the application is to have administrative rights to the server.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2b23f-115">S’il ya beaucoup de serveurs, vous pouvez <xref:System.Printing.PrintServer.%23ctor%28System.String%2CSystem.String%5B%5D%2CSystem.Printing.PrintSystemDesiredAccess%29> améliorer les performances en utilisant les constructeurs qui ne sont que l’initialisation des propriétés dont vous allez avoir besoin.</span><span class="sxs-lookup"><span data-stu-id="2b23f-115">If there are a lot of servers, you can improve performance by using the <xref:System.Printing.PrintServer.%23ctor%28System.String%2CSystem.String%5B%5D%2CSystem.Printing.PrintSystemDesiredAccess%29> constructors that only initialize the properties you are going to need.</span></span>  
  
 <span data-ttu-id="2b23f-116">L’exemple <xref:System.Printing.PrintServer.GetPrintQueues%2A> sert ensuite à créer une collection de toutes les files d’attente du serveur et commence à boucler à travers eux.</span><span class="sxs-lookup"><span data-stu-id="2b23f-116">The example then uses <xref:System.Printing.PrintServer.GetPrintQueues%2A> to create a collection of all of the server's queues and begins to loop through them.</span></span> <span data-ttu-id="2b23f-117">La boucle interne contient une structure en branches correspondant aux deux méthodes de vérification de l’état de l’imprimante :</span><span class="sxs-lookup"><span data-stu-id="2b23f-117">This inner loop contains a branching structure corresponding to the two ways of checking a printer's status:</span></span>  
  
- <span data-ttu-id="2b23f-118">Vous pouvez lire les <xref:System.Printing.PrintQueue.QueueStatus%2A> drapeaux de <xref:System.Printing.PrintQueueStatus>la propriété qui est de type .</span><span class="sxs-lookup"><span data-stu-id="2b23f-118">You can read the flags of the <xref:System.Printing.PrintQueue.QueueStatus%2A> property which is of type <xref:System.Printing.PrintQueueStatus>.</span></span>  
  
- <span data-ttu-id="2b23f-119">Vous pouvez lire chaque <xref:System.Printing.PrintQueue.IsOutOfPaper%2A>propriété <xref:System.Printing.PrintQueue.IsPaperJammed%2A>pertinente telle que , et .</span><span class="sxs-lookup"><span data-stu-id="2b23f-119">You can read each relevant property such as <xref:System.Printing.PrintQueue.IsOutOfPaper%2A>, and <xref:System.Printing.PrintQueue.IsPaperJammed%2A>.</span></span>  
  
 <span data-ttu-id="2b23f-120">Cet exemple montre les deux méthodes, de sorte que l’utilisateur a été précédemment invité à quelle <xref:System.Printing.PrintQueue.QueueStatus%2A> méthode à utiliser et a répondu avec "y" s’ils voulaient utiliser les drapeaux de la propriété.</span><span class="sxs-lookup"><span data-stu-id="2b23f-120">This example demonstrates both methods, so the user was previously prompted as to which method to use and responded with "y" if they wanted to use the flags of the <xref:System.Printing.PrintQueue.QueueStatus%2A> property.</span></span> <span data-ttu-id="2b23f-121">Voir ci-dessous pour obtenir des informations détaillées sur les deux méthodes.</span><span class="sxs-lookup"><span data-stu-id="2b23f-121">See below for the details of the two methods.</span></span>  
  
 <span data-ttu-id="2b23f-122">Enfin, les résultats sont présentés à l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="2b23f-122">Finally, the results are presented to the user.</span></span>  
  
 [!code-cpp[PrinterStatusSurvey#SurveyQueues](~/samples/snippets/cpp/VS_Snippets_Wpf/PrinterStatusSurvey/CPP/Program.cpp#surveyqueues)]
 [!code-csharp[PrinterStatusSurvey#SurveyQueues](~/samples/snippets/csharp/VS_Snippets_Wpf/PrinterStatusSurvey/CSharp/Program.cs#surveyqueues)]
 [!code-vb[PrinterStatusSurvey#SurveyQueues](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PrinterStatusSurvey/visualbasic/program.vb#surveyqueues)]  
  
 <span data-ttu-id="2b23f-123">Pour vérifier l’état de <xref:System.Printing.PrintQueue.QueueStatus%2A> l’imprimante à l’aide des drapeaux de la propriété, vous vérifiez chaque drapeau pertinent pour voir s’il est défini.</span><span class="sxs-lookup"><span data-stu-id="2b23f-123">To check printer status using the flags of the <xref:System.Printing.PrintQueue.QueueStatus%2A> property, you check each relevant flag to see if it is set.</span></span> <span data-ttu-id="2b23f-124">La méthode standard pour voir si un bit est défini dans un ensemble d’indicateurs binaires consiste à effectuer une opération AND logique en utilisant comme opérandes l’ensemble d’indicateurs et l’indicateur lui-même.</span><span class="sxs-lookup"><span data-stu-id="2b23f-124">The standard way to see if one bit is set in a set of bit flags is to perform a logical AND operation with the set of flags as one operand and the flag itself as the other.</span></span> <span data-ttu-id="2b23f-125">Étant donné que l’indicateur lui-même n’a qu’un seul bit de défini, l’opération AND logique ne peut pas trouver plus d’un même bit défini.</span><span class="sxs-lookup"><span data-stu-id="2b23f-125">Since the flag itself has only one bit set, the result of the logical AND is that, at most, that same bit is set.</span></span> <span data-ttu-id="2b23f-126">Pour savoir si c’est bien le cas, il suffit de comparer le résultat de l’opération AND logique avec l’indicateur lui-même.</span><span class="sxs-lookup"><span data-stu-id="2b23f-126">To find out whether it is or not, just compare the result of the logical AND with the flag itself.</span></span> <span data-ttu-id="2b23f-127">Pour plus d’informations, voir <xref:System.Printing.PrintQueueStatus>, [l’opérateur& (référence C)](../../../csharp/language-reference/operators/bitwise-and-shift-operators.md#logical-and-operator-), et <xref:System.FlagsAttribute>.</span><span class="sxs-lookup"><span data-stu-id="2b23f-127">For more information, see <xref:System.Printing.PrintQueueStatus>, the [& Operator (C# Reference)](../../../csharp/language-reference/operators/bitwise-and-shift-operators.md#logical-and-operator-), and <xref:System.FlagsAttribute>.</span></span>  
  
 <span data-ttu-id="2b23f-128">Pour chaque attribut dont le bit est défini, le code ajoute une note au rapport final qui sera présenté à l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="2b23f-128">For each attribute whose bit is set, the code adds a notice to the final report that will be presented to the user.</span></span> <span data-ttu-id="2b23f-129">(La méthode **ReportAvailabilityAtThisTime** qui est appelée à la fin du code est présentée ci-après.)</span><span class="sxs-lookup"><span data-stu-id="2b23f-129">(The **ReportAvailabilityAtThisTime** method that is called at the end of the code is discussed below.)</span></span>  
  
 [!code-cpp[PrinterStatusSurvey#SpotTroubleUsingQueueAttributes](~/samples/snippets/cpp/VS_Snippets_Wpf/PrinterStatusSurvey/CPP/Program.cpp#spottroubleusingqueueattributes)]
 [!code-csharp[PrinterStatusSurvey#SpotTroubleUsingQueueAttributes](~/samples/snippets/csharp/VS_Snippets_Wpf/PrinterStatusSurvey/CSharp/Program.cs#spottroubleusingqueueattributes)]
 [!code-vb[PrinterStatusSurvey#SpotTroubleUsingQueueAttributes](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PrinterStatusSurvey/visualbasic/program.vb#spottroubleusingqueueattributes)]  
  
 <span data-ttu-id="2b23f-130">Pour vérifier l’état de l’imprimante à l’aide de chaque propriété, il vous suffit de lire chaque propriété et d’ajouter une note au rapport final qui sera présenté à l’utilisateur si la propriété est `true`.</span><span class="sxs-lookup"><span data-stu-id="2b23f-130">To check printer status using each property, you simply read each property and add a note to the final report that will be presented to the user if the property is `true`.</span></span> <span data-ttu-id="2b23f-131">(La méthode **ReportAvailabilityAtThisTime** qui est appelée à la fin du code est présentée ci-après.)</span><span class="sxs-lookup"><span data-stu-id="2b23f-131">(The **ReportAvailabilityAtThisTime** method that is called at the end of the code is discussed below.)</span></span>  
  
 [!code-cpp[PrinterStatusSurvey#SpotTroubleUsingQueueProperties](~/samples/snippets/cpp/VS_Snippets_Wpf/PrinterStatusSurvey/CPP/Program.cpp#spottroubleusingqueueproperties)]
 [!code-csharp[PrinterStatusSurvey#SpotTroubleUsingQueueProperties](~/samples/snippets/csharp/VS_Snippets_Wpf/PrinterStatusSurvey/CSharp/Program.cs#spottroubleusingqueueproperties)]
 [!code-vb[PrinterStatusSurvey#SpotTroubleUsingQueueProperties](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PrinterStatusSurvey/visualbasic/program.vb#spottroubleusingqueueproperties)]  
  
 <span data-ttu-id="2b23f-132">La méthode **ReportAvailabilityAtThisTime** a été créée au cas où vous devriez déterminer si la file d’attente est disponible à l’heure actuelle.</span><span class="sxs-lookup"><span data-stu-id="2b23f-132">The **ReportAvailabilityAtThisTime** method was created in case you need to determine if the queue is available at the current time of day.</span></span>  
  
 <span data-ttu-id="2b23f-133">La méthode ne fera <xref:System.Printing.PrintQueue.StartTimeOfDay%2A> <xref:System.Printing.PrintQueue.UntilTimeOfDay%2A> rien si le et les propriétés sont égales; parce que dans ce cas, l’imprimante est disponible en tout temps.</span><span class="sxs-lookup"><span data-stu-id="2b23f-133">The method will do nothing if the <xref:System.Printing.PrintQueue.StartTimeOfDay%2A> and <xref:System.Printing.PrintQueue.UntilTimeOfDay%2A> properties are equal; because in that case the printer is available at all times.</span></span> <span data-ttu-id="2b23f-134">S’ils sont différents, la méthode obtient l’heure actuelle qui doit <xref:System.Printing.PrintQueue.StartTimeOfDay%2A> ensuite <xref:System.Printing.PrintQueue.UntilTimeOfDay%2A> être <xref:System.Int32>convertie en minutes totales après minuit parce que les propriétés et sont s représentant minutes-après-minuit, pas des <xref:System.DateTime> objets.</span><span class="sxs-lookup"><span data-stu-id="2b23f-134">If they are different, the method gets the current time which then has to be converted into total minutes past midnight because the <xref:System.Printing.PrintQueue.StartTimeOfDay%2A> and <xref:System.Printing.PrintQueue.UntilTimeOfDay%2A> properties are <xref:System.Int32>s representing minutes-after-midnight, not <xref:System.DateTime> objects.</span></span> <span data-ttu-id="2b23f-135">Enfin, la méthode vérifie si l’heure actuelle se situe entre les heures de début et de fin.</span><span class="sxs-lookup"><span data-stu-id="2b23f-135">Finally, the method checks to see if the current time is between the start and "until" times.</span></span>  
  
 [!code-cpp[PrinterStatusSurvey#UsingStartAndUntilTimes](~/samples/snippets/cpp/VS_Snippets_Wpf/PrinterStatusSurvey/CPP/Program.cpp#usingstartanduntiltimes)]
 [!code-csharp[PrinterStatusSurvey#UsingStartAndUntilTimes](~/samples/snippets/csharp/VS_Snippets_Wpf/PrinterStatusSurvey/CSharp/Program.cs#usingstartanduntiltimes)]
 [!code-vb[PrinterStatusSurvey#UsingStartAndUntilTimes](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PrinterStatusSurvey/visualbasic/program.vb#usingstartanduntiltimes)]  
  
## <a name="see-also"></a><span data-ttu-id="2b23f-136">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2b23f-136">See also</span></span>

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
- [<span data-ttu-id="2b23f-137">& opérateur (référence C)</span><span class="sxs-lookup"><span data-stu-id="2b23f-137">& Operator (C# Reference)</span></span>](../../../csharp/language-reference/operators/bitwise-and-shift-operators.md#logical-and-operator-)
- [<span data-ttu-id="2b23f-138">Documents dans WPF</span><span class="sxs-lookup"><span data-stu-id="2b23f-138">Documents in WPF</span></span>](documents-in-wpf.md)
- [<span data-ttu-id="2b23f-139">Vue d'ensemble de l'impression</span><span class="sxs-lookup"><span data-stu-id="2b23f-139">Printing Overview</span></span>](printing-overview.md)
