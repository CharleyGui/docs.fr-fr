---
title: 'Comment : imprimer des fichiers XPS par programmation'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- printing XPS files programmatically [WPF]
- XPS files [WPF], printing programmatically
ms.assetid: 0b1c0a3f-b19e-43d6-bcc9-eb3ec4e555ad
ms.openlocfilehash: cc86a7e7c6a816af37c3d063825ed62583afa78a
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73966997"
---
# <a name="how-to-programmatically-print-xps-files"></a>Comment : imprimer des fichiers XPS par programmation

Vous pouvez utiliser une surcharge de la méthode <xref:System.Printing.PrintQueue.AddJob%2A> pour imprimer des fichiers XPS (XML Paper Specification) sans ouvrir de <xref:System.Windows.Controls.PrintDialog> ou, en principe, de [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)].

Vous pouvez également imprimer des fichiers XPS à l’aide des nombreuses méthodes <xref:System.Windows.Xps.XpsDocumentWriter.Write%2A?displayProperty=nameWithType> et <xref:System.Windows.Xps.XpsDocumentWriter.WriteAsync%2A?displayProperty=nameWithType>. Pour plus d’informations, consultez [impression d’un document XPS](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms771525(v=vs.90)).

Une autre façon d’imprimer XPS consiste à utiliser les méthodes <xref:System.Windows.Controls.PrintDialog.PrintDocument%2A?displayProperty=nameWithType> ou <xref:System.Windows.Controls.PrintDialog.PrintVisual%2A?displayProperty=nameWithType>. Consultez l’article [Appeler une boîte de dialogue Imprimer](how-to-invoke-a-print-dialog.md).

## <a name="example"></a>Exemple

Les principales étapes à suivre pour utiliser la méthode de <xref:System.Printing.PrintQueue.AddJob%28System.String%2CSystem.String%2CSystem.Boolean%29> à trois paramètres sont les suivantes. L’exemple ci-dessous donne des détails.

1. Déterminez si l’imprimante est une imprimante XPSDrv. Pour plus d’informations sur XPSDrv, consultez [vue d’ensemble de l’impression](printing-overview.md) .

2. Si l’imprimante n’est pas une imprimante XPSDrv, définissez l’état de cloisonnement du thread sur Thread unique.

3. Instanciez un serveur d’impression et un objet de file d’attente à l’impression.

4. Appelez la méthode, en spécifiant un nom de travail, le fichier à imprimer et un indicateur de <xref:System.Boolean> indiquant si l’imprimante est une imprimante XPSDrv ou non.

L’exemple ci-dessous montre comment imprimer tous les fichiers XPS dans un répertoire par lots. Bien que l’application invite l’utilisateur à spécifier le répertoire, la méthode de <xref:System.Printing.PrintQueue.AddJob%28System.String%2CSystem.String%2CSystem.Boolean%29> à trois paramètres ne nécessite pas de [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]. Il peut être utilisé dans n’importe quel chemin d’accès de code où vous disposez d’un nom de fichier XPS et d’un chemin d’accès que vous pouvez passer à celui-ci.

La surcharge de <xref:System.Printing.PrintQueue.AddJob%28System.String%2CSystem.String%2CSystem.Boolean%29> à trois paramètres de <xref:System.Printing.PrintQueue.AddJob%2A> doit s’exécuter dans un cloisonnement de thread unique chaque fois que le paramètre <xref:System.Boolean> est `false`, ce qui doit être lorsqu’une imprimante non-XPSDrv est utilisée. Toutefois, l’état de cloisonnement par défaut pour .NET est plusieurs threads. Cette valeur par défaut doit être modifiée puisque l’exemple utilise une imprimante non-XPSDrv.

Il existe deux moyens de modifier la valeur par défaut. L’une des méthodes consiste à ajouter simplement le <xref:System.STAThreadAttribute> (c’est-à-dire «`[System.STAThreadAttribute()]`») juste au-dessus de la première ligne de la méthode de `Main` de l’application (généralement «`static void Main(string[] args)`»). Toutefois, de nombreuses applications requièrent que la méthode `Main` ait un état de cloisonnement multithread. il existe donc une deuxième méthode : placer l’appel à <xref:System.Printing.PrintQueue.AddJob%28System.String%2CSystem.String%2CSystem.Boolean%29> dans un thread distinct dont l’état de cloisonnement est défini sur <xref:System.Threading.ApartmentState.STA> avec <xref:System.Threading.Thread.SetApartmentState%2A>. L’exemple suivant utilise cette deuxième technique.

En conséquence, l’exemple commence par instanciation d’un objet <xref:System.Threading.Thread> et en lui passant une méthode **PrintXPS** comme paramètre <xref:System.Threading.ThreadStart>. (La méthode **PrintXPS** est définie ultérieurement dans l’exemple.) Le thread est ensuite défini sur un seul thread cloisonné. Le seul code restant de la méthode `Main` démarre le nouveau thread.

L’exemple se base principalement sur la méthode `static`**BatchXPSPrinter.PrintXPS**. Après avoir créé un serveur d’impression et une file d’attente, la méthode invite l’utilisateur à entrer un répertoire contenant des fichiers XPS. Après la validation de l’existence du répertoire et de la présence de fichiers \*. XPS dans celui-ci, la méthode ajoute chacun de ces fichiers à la file d’attente à l’impression. L’exemple suppose que l’imprimante n’est pas XPSDrv, donc nous passons `false` au dernier paramètre de <xref:System.Printing.PrintQueue.AddJob%28System.String%2CSystem.String%2CSystem.Boolean%29> méthode. C’est la raison pour laquelle la méthode valide le balisage XPS dans le fichier avant de tenter de la convertir dans le langage de description de page de l’imprimante. Si la validation échoue, une exception est générée. L’exemple de code intercepte l’exception, en informe l’utilisateur, puis passe au traitement du fichier XPS suivant.

[!code-csharp[BatchPrintXPSFiles#BatchPrintXPSFiles](~/samples/snippets/csharp/VS_Snippets_Wpf/BatchPrintXPSFiles/CSharp/Program.cs#batchprintxpsfiles)]
[!code-vb[BatchPrintXPSFiles#BatchPrintXPSFiles](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BatchPrintXPSFiles/visualbasic/program.vb#batchprintxpsfiles)]

Si vous utilisez une imprimante XPSDrv, vous pouvez définir le paramètre final sur `true`. Dans ce cas, étant donné que XPS est le langage de description de page de l’imprimante, la méthode envoie le fichier à l’imprimante sans le valider ou le convertir dans un autre langage de description de page. Si vous n’êtes pas certain, au moment du design, que l’application utilisera une imprimante XPSDrv, vous pouvez modifier l’application pour qu’elle lise les <xref:System.Printing.PrintQueue.IsXpsDevice%2A> propriété et branche en fonction de ce qu’elle trouve.

Dans la mesure où il y aura au départ peu d’imprimantes XPSDrv disponibles immédiatement après la sortie de Windows Vista et Microsoft .NET Framework, vous devrez peut-être déguiser une imprimante non-XPSDrv en tant qu’imprimante XPSDrv. Pour ce faire, ajoutez le fichier Pipelineconfig.xml à la liste des fichiers dans la clé de Registre suivante de l’ordinateur qui exécute votre application :

HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Print\Environments\Windows NT x86\Drivers\Version-3\\ *\<PseudoXPSPrinter>* \DependentFiles

où *\<PseudoXPSPrinter>* est une file d’attente à l’impression. L’ordinateur doit ensuite être redémarré.

Ce déguisement vous permettra de passer `true` comme paramètre final de <xref:System.Printing.PrintQueue.AddJob%28System.String%2CSystem.String%2CSystem.Boolean%29> sans générer d’exception, mais étant donné que *\<PseudoXPSPrinter >* n’est pas vraiment une imprimante XPSDrv, seul le garbage est imprimé.

> [!NOTE]
> Par souci de simplicité, l’exemple ci-dessus utilise la présence d’une extension \*. XPS comme test d’un fichier XPS. Toutefois, les fichiers XPS n’ont pas besoin d’avoir cette extension. [IsXPS. exe (outil de conformité isXPS)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/aa348104(v=vs.100)) est une façon de tester la validité d’un fichier XPS.

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
