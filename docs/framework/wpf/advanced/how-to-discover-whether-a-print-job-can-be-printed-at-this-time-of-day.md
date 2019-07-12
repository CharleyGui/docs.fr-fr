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
ms.openlocfilehash: ee38caedc5d5a29d2221d6e5a6bf6cf74617bf8c
ms.sourcegitcommit: 83ecdf731dc1920bca31f017b1556c917aafd7a0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/12/2019
ms.locfileid: "67859716"
---
# <a name="how-to-discover-whether-a-print-job-can-be-printed-at-this-time-of-day"></a>Procédure : Déterminer si un travail d’impression peut être imprimé à cette heure de la journée
Files d’attente ne concernent pas toujours disponibles 24 heures par jour. Ils ont des propriétés au moment de début et de fin qui peuvent être définies pour les rendre indisponibles à certains moments de la journée. Cette fonctionnalité peut être utilisée, par exemple, pour réserver une imprimante à l’usage exclusif d’un département après 17 h 00. Ce département aurait une autre file d’attente l’imprimante que les autres services à utiliser. La file d’attente pour les autres départements serait défini comme être indisponible après 17 h 00, tandis que la file d’attente pour le département privilégié peut être définie pour être disponible à tout moment.  
  
 En outre, les travaux d’impression eux-mêmes peuvent être définis pour être imprimables uniquement dans un intervalle de temps spécifié.  
  
 Le <xref:System.Printing.PrintQueue> et <xref:System.Printing.PrintSystemJobInfo> classes exposées dans l’API de Microsoft .NET Framework fournissent un moyen de vérifier à distance si un travail d’impression donné peut imprimer sur une file d’attente donnée à l’heure actuelle.  
  
## <a name="example"></a>Exemple  
 L’exemple ci-dessous est un exemple qui peut diagnostiquer les problèmes liés à un travail d’impression.  
  
 Il existe deux principales étapes de ce type de fonction comme suit.  
  
1. Lecture la <xref:System.Printing.PrintQueue.StartTimeOfDay%2A> et <xref:System.Printing.PrintQueue.UntilTimeOfDay%2A> propriétés de la <xref:System.Printing.PrintQueue> pour déterminer si l’heure actuelle est entre eux.  
  
2. Lecture la <xref:System.Printing.PrintSystemJobInfo.StartTimeOfDay%2A> et <xref:System.Printing.PrintSystemJobInfo.UntilTimeOfDay%2A> propriétés de la <xref:System.Printing.PrintSystemJobInfo> pour déterminer si l’heure actuelle est entre eux.  
  
 Mais les complications naissent du fait que ces propriétés ne sont pas <xref:System.DateTime> objets. Au lieu de cela, ils sont <xref:System.Int32> objets qui expriment l’heure du jour en tant que le nombre de minutes depuis minuit. En outre, cela n’est pas minuit dans le fuseau horaire actuel, mais minuit UTC (Coordinated Universal Time).  
  
 Le premier exemple de code présente la méthode statique **ReportQueueAndJobAvailability**, qui est transmis un <xref:System.Printing.PrintSystemJobInfo> et appelle les méthodes d’assistance pour déterminer si le travail peut être imprimé à l’heure actuelle et, si pas, quand elle peut imprimer. Notez qu’un <xref:System.Printing.PrintQueue> n’est pas passé à la méthode. Il s’agit, car le <xref:System.Printing.PrintSystemJobInfo> inclut une référence à la file d’attente dans son <xref:System.Printing.PrintSystemJobInfo.HostingPrintQueue%2A> propriété.  
  
 Les méthodes subordonnés sont surchargées **ReportAvailabilityAtThisTime** méthode qui peut prendre l’une un <xref:System.Printing.PrintQueue> ou un <xref:System.Printing.PrintSystemJobInfo> en tant que paramètre. Il existe également un **TimeConverter.ConvertToLocalHumanReadableTime**. Toutes ces méthodes sont décrites ci-dessous.  
  
 Le **ReportQueueAndJobAvailability** méthode commence par vérifier si la file d’attente ou le travail d’impression n’est pas disponible pour l’instant. Si un d’eux n’est pas disponible, il vérifie ensuite si la file d’attente est indisponible. S’il n’est pas disponible, la méthode signale ce fait et l’heure lorsque la file d’attente redeviennent disponible. Elle vérifie ensuite le travail et si elle n’est pas disponible, il signale au prochain intervalle pendant qu’elle peut imprimer. Enfin, la méthode signale la première heure lorsque le travail peut être imprimé. Il s’agit la plus récente de deux fois de suite.  
  
- L’heure auxquelles la file d’attente est ensuite disponible.  
  
- L’heure auxquelles le travail d’impression est ensuite disponible.  
  
 Lors du signalement des heures de la journée, la <xref:System.DateTime.ToShortTimeString%2A> méthode est également appelée car cette méthode supprime les années, les mois et jours de la sortie. Vous ne pouvez pas limiter la disponibilité d’une file d’attente à l’impression ou d’un travail d’impression à des années, mois ou jours.  
  
 [!code-cpp[DiagnoseProblematicPrintJob#ReportQueueAndJobAvailability](~/samples/snippets/cpp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CPP/Program.cpp#reportqueueandjobavailability)]
 [!code-csharp[DiagnoseProblematicPrintJob#ReportQueueAndJobAvailability](~/samples/snippets/csharp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CSharp/Program.cs#reportqueueandjobavailability)]
 [!code-vb[DiagnoseProblematicPrintJob#ReportQueueAndJobAvailability](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/visualbasic/program.vb#reportqueueandjobavailability)]  
  
 Les deux surcharges de la **ReportAvailabilityAtThisTime** méthode sont identiques à l’exception du type passé pour eux, afin que seuls les <xref:System.Printing.PrintQueue> version est présentée ci-dessous.  
  
> [!NOTE]
>  Le fait que les méthodes sont identiques à l’exception de type soulève la question de savoir pourquoi l’exemple ne crée pas une méthode générique **ReportAvailabilityAtThisTime\<T >** . La raison est qu’une telle méthode devrait être limité à une classe qui possède le **StartTimeOfDay** et **UntilTimeOfDay** propriétés qui appelle la méthode, mais une méthode générique peut uniquement être limité à un l’unique classe et la seule classe commune aux deux <xref:System.Printing.PrintQueue> et <xref:System.Printing.PrintSystemJobInfo> l’héritage arborescence est <xref:System.Printing.PrintSystemObject> n’ayant pas de propriétés.  
  
 Le **ReportAvailabilityAtThisTime** (méthode) (présenté dans l’exemple de code ci-dessous) commence par initialiser un <xref:System.Boolean> variable sentinel à `true`. Elle sera réinitialisée à `false`, si la file d’attente n’est pas disponible.  
  
 Ensuite, la méthode vérifie si le début et « until » heures sont identiques. S’ils sont, la file d’attente est toujours disponible, alors la méthode retourne `true`.  
  
 Si la file d’attente n’est pas disponible tout le temps, la méthode utilise la méthode statique <xref:System.DateTime.UtcNow%2A> propriété à obtenir l’heure actuelle comme un <xref:System.DateTime> objet. (Nous n’avez pas besoin de heure locale, car le <xref:System.Printing.PrintQueue.StartTimeOfDay%2A> et <xref:System.Printing.PrintQueue.UntilTimeOfDay%2A> propriétés sont elles-mêmes en heure UTC.)  
  
 Toutefois, ces deux propriétés ne sont pas <xref:System.DateTime> objets. Ils sont <xref:System.Int32>s exprimant le temps que le nombre de minutes après minuit UTC. Donc nous devons convertir notre <xref:System.DateTime> objet minutes après minuit. Lorsque cette opération effectuée, la méthode vérifie simplement pour voir si « maintenant » est entre le début de la file d’attente et les heures, définit la sentinelle sur false si « maintenant » n’est pas entre les deux heures et retourne la sentinelle « until ».  
  
 [!code-cpp[DiagnoseProblematicPrintJob#PrintQueueStartUntil](~/samples/snippets/cpp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CPP/Program.cpp#printqueuestartuntil)]
 [!code-csharp[DiagnoseProblematicPrintJob#PrintQueueStartUntil](~/samples/snippets/csharp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CSharp/Program.cs#printqueuestartuntil)]
 [!code-vb[DiagnoseProblematicPrintJob#PrintQueueStartUntil](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/visualbasic/program.vb#printqueuestartuntil)]  
  
 Le **TimeConverter.ConvertToLocalHumanReadableTime** (méthode) (présenté dans l’exemple de code ci-dessous) n’utilise pas toutes les méthodes introduites avec Microsoft .NET Framework, que la description est courte. La méthode a une double tâche de conversion : elle doit prendre un entier exprimant des minutes après minuit et le convertir en un temps lisible et il doit le convertir à l’heure locale. Cela, il en créant d’abord un <xref:System.DateTime> objet qui est définie à minuit UTC, puis il utilise le <xref:System.DateTime.AddMinutes%2A> méthode pour ajouter les minutes qui ont été passés à la méthode. Cela retourne un nouvel <xref:System.DateTime> exprimant l’heure d’origine qui a été passé à la méthode. Le <xref:System.DateTime.ToLocalTime%2A> méthode convertit ensuite cette heure locale.  
  
 [!code-cpp[DiagnoseProblematicPrintJob#TimeConverter](~/samples/snippets/cpp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CPP/Program.cpp#timeconverter)]
 [!code-csharp[DiagnoseProblematicPrintJob#TimeConverter](~/samples/snippets/csharp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CSharp/Program.cs#timeconverter)]
 [!code-vb[DiagnoseProblematicPrintJob#TimeConverter](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/visualbasic/program.vb#timeconverter)]  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.DateTime>
- <xref:System.Printing.PrintSystemJobInfo>
- <xref:System.Printing.PrintQueue>
- [Documents dans WPF](documents-in-wpf.md)
- [Vue d’ensemble de l’impression](printing-overview.md)
