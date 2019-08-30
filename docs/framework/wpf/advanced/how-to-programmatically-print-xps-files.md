---
title: 'Procédure : Imprimer des fichiers XPS par programmation'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- printing XPS files programmatically [WPF]
- XPS files [WPF], printing programmatically
ms.assetid: 0b1c0a3f-b19e-43d6-bcc9-eb3ec4e555ad
ms.openlocfilehash: 6642fad7d20e60a8b92e5860b763511f4fc0be72
ms.sourcegitcommit: 1b020356e421a9314dd525539da12463d980ce7a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/30/2019
ms.locfileid: "70169181"
---
# <a name="how-to-programmatically-print-xps-files"></a>Procédure : Imprimer des fichiers XPS par programmation
Vous pouvez utiliser une surcharge de la <xref:System.Printing.PrintQueue.AddJob%2A> méthode pour imprimer [!INCLUDE[TLA#tla_xps](../../../../includes/tlasharptla-xps-md.md)] des fichiers sans ouvrir <xref:System.Windows.Controls.PrintDialog> ou, en principe, tous [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] .  
  
 Vous pouvez également imprimer [!INCLUDE[TLA#tla_xps](../../../../includes/tlasharptla-xps-md.md)] des fichiers à l' <xref:System.Windows.Xps.XpsDocumentWriter.Write%2A> aide <xref:System.Windows.Xps.XpsDocumentWriter.WriteAsync%2A> des méthodes nombreuses <xref:System.Windows.Xps.XpsDocumentWriter>et du. Pour en savoir plus sur ce sujet, consultez l’article [Printing an XPS Document](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms771525(v=vs.90)) (Impression d’un document XPS).  
  
 Une autre façon d' [!INCLUDE[TLA#tla_xps](../../../../includes/tlasharptla-xps-md.md)] imprimer consiste à utiliser <xref:System.Windows.Controls.PrintDialog.PrintDocument%2A> les <xref:System.Windows.Controls.PrintDialog.PrintVisual%2A> méthodes ou du <xref:System.Windows.Controls.PrintDialog> contrôle. Consultez l’article [Appeler une boîte de dialogue Imprimer](how-to-invoke-a-print-dialog.md).  
  
## <a name="example"></a>Exemple  
 Les principales étapes à suivre pour utiliser la méthode <xref:System.Printing.PrintQueue.AddJob%28System.String%2CSystem.String%2CSystem.Boolean%29> à trois paramètres sont les suivantes. L’exemple ci-dessous donne des détails.  
  
1. Déterminez si l’imprimante est une imprimante XPSDrv. (Voir [Vue d’ensemble de l’impression](printing-overview.md) pour plus d’informations sur XPSDrv.)  
  
2. Si l’imprimante n’est pas une imprimante XPSDrv, définissez l’état de cloisonnement du thread sur Thread unique.  
  
3. Instanciez un serveur d’impression et un objet de file d’attente à l’impression.  
  
4. Appelez la méthode, en spécifiant un nom de travail, le fichier à imprimer et <xref:System.Boolean> un indicateur spécifiant si l’imprimante est une imprimante XPSDrv.  
  
 L’exemple ci-dessous montre comment imprimer par lot tous les fichiers [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] d’un répertoire. Bien que l’application invite l’utilisateur à spécifier le répertoire, la méthode à trois <xref:System.Printing.PrintQueue.AddJob%28System.String%2CSystem.String%2CSystem.Boolean%29> paramètres ne requiert pas de [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]. Elle peut être utilisée dans n’importe quel chemin d’accès de code où vous disposez d’un nom de fichier [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] et d’un chemin que vous pouvez lui transmettre.  
  
 La surcharge à trois <xref:System.Printing.PrintQueue.AddJob%28System.String%2CSystem.String%2CSystem.Boolean%29> paramètres de <xref:System.Printing.PrintQueue.AddJob%2A> doit s’exécuter dans un seul cloisonnement de threads chaque `false`fois que le <xref:System.Boolean> paramètre est, ce qui doit être lorsqu’une imprimante non-XPSDrv est utilisée. Toutefois, l’état de cloisonnement par défaut pour .NET est plusieurs threads. Cette valeur par défaut doit être modifiée puisque l’exemple utilise une imprimante non-XPSDrv.  
  
 Il existe deux moyens de modifier la valeur par défaut. L’une des méthodes consiste à ajouter <xref:System.STAThreadAttribute> simplement le (autrement dit`[System.STAThreadAttribute()]`, «») juste au-dessus de la première `Main` ligne de la méthode`static void Main(string[] args)`de l’application (généralement «»). Toutefois, de nombreuses applications requièrent `Main` que la méthode ait un état de cloisonnement multithread. il existe donc une deuxième méthode: Placez l’appel à <xref:System.Printing.PrintQueue.AddJob%28System.String%2CSystem.String%2CSystem.Boolean%29> dans un thread distinct dont l’état de cloisonnement est <xref:System.Threading.ApartmentState.STA> défini <xref:System.Threading.Thread.SetApartmentState%2A>sur avec. L’exemple suivant utilise cette deuxième technique.  
  
 En conséquence, l’exemple commence par instancier un <xref:System.Threading.Thread> objet et lui transmettre une méthode **PrintXPS** comme <xref:System.Threading.ThreadStart> paramètre. (La méthode **PrintXPS** est expliquée plus loin dans l’exemple.) Ensuite, le thread est défini sur un thread unique cloisonné. Le seul code restant de la méthode `Main` démarre le nouveau thread.  
  
 L’exemple se base principalement sur la méthode `static`**BatchXPSPrinter.PrintXPS**. Une fois que le serveur d’impression et la file d’attente ont été créés, la méthode invite l’utilisateur à spécifier un répertoire contenant les fichiers [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)]. Après la validation de l’existence du répertoire et de la présence \*de fichiers. XPS dans celui-ci, la méthode ajoute chacun de ces fichiers à la file d’attente à l’impression. L’exemple suppose que l’imprimante n’est pas XPSDrv, donc nous passons `false` au dernier paramètre de <xref:System.Printing.PrintQueue.AddJob%28System.String%2CSystem.String%2CSystem.Boolean%29> la méthode. Pour cette raison, la méthode validera le balisage [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] dans le fichier avant d’essayer de le convertir en langage de description de page de l’imprimante. Si la validation échoue, une exception est générée. L’exemple de code interceptera l’exception, en informera l’utilisateur et passera ensuite au fichier [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] suivant.  
  
 [!code-csharp[BatchPrintXPSFiles#BatchPrintXPSFiles](~/samples/snippets/csharp/VS_Snippets_Wpf/BatchPrintXPSFiles/CSharp/Program.cs#batchprintxpsfiles)]
 [!code-vb[BatchPrintXPSFiles#BatchPrintXPSFiles](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BatchPrintXPSFiles/visualbasic/program.vb#batchprintxpsfiles)]  
  
 Si vous utilisez une imprimante XPSDrv, vous pouvez définir le paramètre final sur `true`. Dans ce cas, puisque [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] est le langage de description de page de l’imprimante, la méthode enverra le fichier à l’imprimante sans le valider ou le convertir dans un autre langage de description de page. Si vous n’êtes pas certain au moment de la conception que l’application utilise une imprimante XPSDrv, vous pouvez modifier l’application pour qu’elle <xref:System.Printing.PrintQueue.IsXpsDevice%2A> Lise la propriété et crée la branche en fonction de ce qu’elle trouve.  
  
 Dans la mesure où il y aura au départ peu d’imprimantes XPSDrv disponibles [!INCLUDE[TLA#tla_winvista](../../../../includes/tlasharptla-winvista-md.md)] immédiatement après la publication de et Microsoft .NET Framework, vous devrez peut-être déguiser une imprimante non-XPSDrv en tant qu’imprimante XPSDrv. Pour ce faire, ajoutez le fichier Pipelineconfig.xml à la liste des fichiers dans la clé de Registre suivante de l’ordinateur qui exécute votre application :  
  
 HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Print\Environments\Windows NT x86\Drivers\Version-3\\ *\<PseudoXPSPrinter>* \DependentFiles  
  
 où *\<PseudoXPSPrinter>* est une file d’attente à l’impression. L’ordinateur doit ensuite être redémarré.  
  
 Ce déguisement vous permettra de `true` passer comme paramètre final de <xref:System.Printing.PrintQueue.AddJob%28System.String%2CSystem.String%2CSystem.Boolean%29> sans provoquer une exception, mais comme  *\<PseudoXPSPrinter >* n’est pas vraiment une imprimante XPSDrv, seul le garbage est imprimé.  
  
 **Remarque** Par souci de simplicité, l’exemple ci-dessus utilise \*la présence d’une extension. XPS comme test d' [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)]un fichier. Toutefois, les fichiers [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] n’ont pas obligatoirement cette extension. L’outil [isXPS.exe (isXPS Conformance Tool)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/aa348104(v=vs.100)) permet de tester la conformité d’un fichier aux normes [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)].  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Printing.PrintQueue>
- <xref:System.Printing.PrintQueue.AddJob%2A>
- <xref:System.Threading.ApartmentState>
- <xref:System.STAThreadAttribute>
- [Documents XPS](/windows/desktop/printdocs/documents)
- [Impression d’un document XPS](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms771525(v=vs.90))
- [Threads managés et non managés](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/5s8ee185(v=vs.100))
- [isXPS.exe (isXPS Conformance Tool)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/aa348104(v=vs.100))
- [Documents dans WPF](documents-in-wpf.md)
- [Vue d’ensemble de l’impression](printing-overview.md)
