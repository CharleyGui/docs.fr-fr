---
title: 'Procédure : Déterminer si un travail d’impression peut être imprimé à cette heure de la journée'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- print queues [WPF], timing
- printers [WPF], availability
- print jobs [WPF], timing
ms.assetid: 7e9c8ec1-abf6-4b3d-b1c6-33b35d3c4063
ms.openlocfilehash: 859dc75169e443d07361951692a428507886fa2e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69947808"
---
# <a name="how-to-discover-whether-a-print-job-can-be-printed-at-this-time-of-day"></a>Procédure : Déterminer si un travail d’impression peut être imprimé à cette heure de la journée
Les files d’attente à l’impression ne sont pas toujours disponibles pendant 24 heures par jour. Ils ont des propriétés d’heure de début et de fin qui peuvent être définies pour les rendre indisponibles à certaines heures de la journée. Cette fonctionnalité peut être utilisée, par exemple, pour réserver une imprimante à l’usage exclusif d’un certain service après 17h00. Ce service dispose d’une file d’attente différente de celle utilisée par les autres services. La file d’attente des autres services est définie pour être indisponible après 17h00, tandis que la file d’attente pour le service favorisé peut être configurée pour être disponible à tout moment.  
  
 En outre, les travaux d’impression peuvent être configurés pour être imprimables uniquement dans un intervalle de temps spécifié.  
  
 Les <xref:System.Printing.PrintQueue> classes <xref:System.Printing.PrintSystemJobInfo> et exposées dans les API de Microsoft .NET Framework fournissent un moyen de vérifier à distance si un travail d’impression donné peut imprimer sur une file d’attente donnée à l’heure actuelle.  
  
## <a name="example"></a>Exemple  
 L’exemple ci-dessous est un exemple qui peut diagnostiquer les problèmes liés à un travail d’impression.  
  
 Il existe deux étapes principales pour ce type de fonction, comme suit.  
  
1. Lisez les <xref:System.Printing.PrintQueue.StartTimeOfDay%2A> propriétés <xref:System.Printing.PrintQueue.UntilTimeOfDay%2A> et de l' <xref:System.Printing.PrintQueue> objet pour déterminer si l’heure actuelle est comprise entre ces deux éléments.  
  
2. Lisez les <xref:System.Printing.PrintSystemJobInfo.StartTimeOfDay%2A> propriétés <xref:System.Printing.PrintSystemJobInfo.UntilTimeOfDay%2A> et de l' <xref:System.Printing.PrintSystemJobInfo> objet pour déterminer si l’heure actuelle est comprise entre ces deux éléments.  
  
 Mais les complications proviennent du fait que ces propriétés ne sont <xref:System.DateTime> pas des objets. Au lieu de <xref:System.Int32> cela, il s’agit d’objets qui expriment l’heure de la journée comme nombre de minutes depuis minuit. En outre, ce n’est pas minuit dans le fuseau horaire actuel, mais minuit UTC (temps universel coordonné).  
  
 Le premier exemple de code présente la méthode statique **ReportQueueAndJobAvailability**, qui est passée <xref:System.Printing.PrintSystemJobInfo> à un et appelle les méthodes d’assistance pour déterminer si le travail peut imprimer à l’heure actuelle et, dans le cas contraire, s’il peut imprimer. Notez qu’un <xref:System.Printing.PrintQueue> n’est pas passé à la méthode. Cela est dû au <xref:System.Printing.PrintSystemJobInfo> fait que le comprend une référence à la <xref:System.Printing.PrintSystemJobInfo.HostingPrintQueue%2A> file d’attente dans sa propriété.  
  
 Les méthodes subordonnées incluent la méthode **ReportAvailabilityAtThisTime** surchargée qui peut accepter <xref:System.Printing.PrintQueue> un ou <xref:System.Printing.PrintSystemJobInfo> un comme paramètre. Il y a également un **TimeConverter. ConvertToLocalHumanReadableTime**. Toutes ces méthodes sont décrites ci-dessous.  
  
 La méthode **ReportQueueAndJobAvailability** commence par vérifier si la file d’attente ou le travail d’impression n’est pas disponible pour l’instant. Si l’un de ces éléments n’est pas disponible, il vérifie ensuite si la file d’attente n’est pas disponible. S’il n’est pas disponible, la méthode signale ce fait et l’heure à laquelle la file d’attente redevient disponible. Il vérifie ensuite la tâche et, si elle est indisponible, elle signale la prochaine période quand elle peut imprimer. Enfin, la méthode indique l’heure la plus proche à laquelle le travail peut imprimer. Il s’agit de la version la plus récente de deux fois.  
  
- Heure à laquelle la file d’attente à l’impression est ensuite disponible.  
  
- Heure à laquelle le travail d’impression est disponible.  
  
 Lors du signalement des heures de <xref:System.DateTime.ToShortTimeString%2A> la journée, la méthode est également appelée car cette méthode supprime les années, les mois et les jours de la sortie. Vous ne pouvez pas limiter la disponibilité d’une file d’attente à l’impression ou d’un travail d’impression à des années, des mois ou des jours spécifiques.  
  
 [!code-cpp[DiagnoseProblematicPrintJob#ReportQueueAndJobAvailability](~/samples/snippets/cpp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CPP/Program.cpp#reportqueueandjobavailability)]
 [!code-csharp[DiagnoseProblematicPrintJob#ReportQueueAndJobAvailability](~/samples/snippets/csharp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CSharp/Program.cs#reportqueueandjobavailability)]
 [!code-vb[DiagnoseProblematicPrintJob#ReportQueueAndJobAvailability](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/visualbasic/program.vb#reportqueueandjobavailability)]  
  
 Les deux surcharges de la méthode **ReportAvailabilityAtThisTime** sont identiques, à l’exception du type qui leur est passé, <xref:System.Printing.PrintQueue> c’est pourquoi seule la version est présentée ci-dessous.  
  
> [!NOTE]
> Le fait que les méthodes soient identiques à l’exception du type soulève la question de la raison pour laquelle l’exemple ne crée pas de méthode générique **\<ReportAvailabilityAtThisTime T >** . En effet, une telle méthode devrait être restreinte à une classe qui a les propriétés **StartTimeOfDay** et **UntilTimeOfDay** que la méthode appelle, mais une méthode générique ne peut être limitée qu’à une seule classe et la seule classe commune aux deux et, dans l’arborescence d' <xref:System.Printing.PrintSystemObject> héritage, n’a pas de propriétés de ce type. <xref:System.Printing.PrintSystemJobInfo> <xref:System.Printing.PrintQueue>  
  
 La méthode **ReportAvailabilityAtThisTime** (présentée dans l’exemple de code ci-dessous) commence par <xref:System.Boolean> initialiser une `true`variable Sentinel à. Elle est réinitialisée `false`à, si la file d’attente n’est pas disponible.  
  
 Ensuite, la méthode vérifie si les heures de début et de fin sont identiques. Si c’est le cas, la file d’attente est toujours disponible, `true`de sorte que la méthode retourne.  
  
 Si la file d’attente n’est pas disponible tout le temps, la méthode <xref:System.DateTime.UtcNow%2A> utilise la propriété statique pour obtenir l’heure <xref:System.DateTime> actuelle en tant qu’objet. (L’heure locale n’est pas nécessaire, <xref:System.Printing.PrintQueue.StartTimeOfDay%2A> car <xref:System.Printing.PrintQueue.UntilTimeOfDay%2A> les propriétés et sont elles-mêmes en heure UTC.)  
  
 Toutefois, ces deux propriétés ne sont <xref:System.DateTime> pas des objets. Il s' <xref:System.Int32>agit de s exprimant le temps en tant que nombre de minutes-après l’heure UTC-minuit. Nous devons donc convertir notre <xref:System.DateTime> objet en minutes-après-minuit. Lorsque cela est fait, la méthode vérifie simplement si «Now» se trouve entre les heures de début et de fin de la file d’attente, définit la sentinelle sur false si «Now» n’est pas entre les deux fois, et retourne la sentinelle.  
  
 [!code-cpp[DiagnoseProblematicPrintJob#PrintQueueStartUntil](~/samples/snippets/cpp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CPP/Program.cpp#printqueuestartuntil)]
 [!code-csharp[DiagnoseProblematicPrintJob#PrintQueueStartUntil](~/samples/snippets/csharp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CSharp/Program.cs#printqueuestartuntil)]
 [!code-vb[DiagnoseProblematicPrintJob#PrintQueueStartUntil](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/visualbasic/program.vb#printqueuestartuntil)]  
  
 La méthode **TimeConverter. ConvertToLocalHumanReadableTime** (présentée dans l’exemple de code ci-dessous) n’utilise aucune des méthodes introduites avec Microsoft .NET Framework. la discussion est donc brève. La méthode a une tâche de conversion double: elle doit prendre un entier exprimant minutes-après-minuit et la convertir en heure explicite et elle doit être convertie en heure locale. Pour ce faire, il commence par créer <xref:System.DateTime> un objet qui a la valeur UTC minuit, puis il utilise <xref:System.DateTime.AddMinutes%2A> la méthode pour ajouter les minutes passées à la méthode. Cela retourne un nouveau <xref:System.DateTime> exprimant l’heure d’origine passée à la méthode. La <xref:System.DateTime.ToLocalTime%2A> méthode convertit ensuite ce en heure locale.  
  
 [!code-cpp[DiagnoseProblematicPrintJob#TimeConverter](~/samples/snippets/cpp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CPP/Program.cpp#timeconverter)]
 [!code-csharp[DiagnoseProblematicPrintJob#TimeConverter](~/samples/snippets/csharp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CSharp/Program.cs#timeconverter)]
 [!code-vb[DiagnoseProblematicPrintJob#TimeConverter](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/visualbasic/program.vb#timeconverter)]  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.DateTime>
- <xref:System.Printing.PrintSystemJobInfo>
- <xref:System.Printing.PrintQueue>
- [Documents dans WPF](documents-in-wpf.md)
- [Vue d’ensemble de l’impression](printing-overview.md)
