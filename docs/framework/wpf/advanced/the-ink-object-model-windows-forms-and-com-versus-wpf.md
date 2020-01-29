---
title: Encre numérique-Windows Forms et COM ou WPF
titleSuffix: ''
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- enabling ink [WPF]
- InkCanvas control [WPF]
- ink object model [WPF]
- tablet pen [WPF], events [WPF]
- ink [WPF], enabling
- events [WPF], tablet pen
ms.assetid: 577835be-b145-4226-8570-1d309e9b3901
ms.openlocfilehash: 4a183bba2c5cfb2d12a9cf435ae1f92b4cf63948
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76737285"
---
# <a name="the-ink-object-model-windows-forms-and-com-versus-wpf"></a>Modèle objet encre : Windows Forms et COM ou WPF

Il existe essentiellement trois plateformes qui prennent en charge l’encre numérique : la plateforme de Windows Forms Tablet PC, la plate-forme COM Tablet PC et la plateforme Windows Presentation Foundation (WPF).  Les plateformes Windows Forms et COM partagent un modèle objet similaire, mais le modèle objet pour la plateforme WPF est fondamentalement différent.  Cette rubrique décrit les différences à un niveau élevé afin que les développeurs qui ont travaillé avec un modèle objet puissent mieux comprendre l’autre.  
  
## <a name="enabling-ink-in-an-application"></a>Activation de l’encre dans une application  
 Les trois plateformes expédient des objets et des contrôles qui permettent à une application de recevoir l’entrée d’un stylet de tablette.  Les plateformes Windows Forms et COM sont fournies avec les classes Microsoft. Ink. [InkPicture](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms583740(v=vs.90)), [Microsoft. Ink. InkEdit](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms552265(v=vs.90)), [Microsoft. Ink. InkOverlay](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms552322(v=vs.90)) et [Microsoft. Ink. InkCollector](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms583683(v=vs.90)) .  [Microsoft. Ink. InkPicture](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms583740(v=vs.90)) et [Microsoft. Ink. InkEdit](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms552265(v=vs.90)) sont des contrôles que vous pouvez ajouter à une application pour collecter l’encre.  [Microsoft. Ink. InkOverlay](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms552322(v=vs.90)) et [Microsoft. Ink. InkCollector](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms583683(v=vs.90)) peuvent être attachés à une fenêtre existante pour permettre l’activation des contrôles personnalisés et Windows par le biais de l’encre.  
  
 La plateforme WPF comprend le contrôle <xref:System.Windows.Controls.InkCanvas>.  Vous pouvez ajouter une <xref:System.Windows.Controls.InkCanvas> à votre application et commencer immédiatement à collecter l’encre. Avec la <xref:System.Windows.Controls.InkCanvas>, l’utilisateur peut copier, sélectionner et redimensionner l’encre.  Vous pouvez ajouter d’autres contrôles à la <xref:System.Windows.Controls.InkCanvas>et l’utilisateur peut également écrire sur ces contrôles.  Vous pouvez créer un contrôle personnalisé avec entrée manuscrite en lui ajoutant un <xref:System.Windows.Controls.InkPresenter> et en recueillant ses points de stylet.  
  
 Le tableau suivant répertorie les emplacements où vous pouvez en savoir plus sur l’activation de l’encre dans une application :  
  
|Pour effectuer cette opération...|Sur la plateforme WPF...|Sur les plateformes Windows Forms/COM...|  
|-----------------|--------------------------|------------------------------------------|  
|Ajouter un contrôle avec accès manuscrit à une application|Consultez [prise en main avec de l’encre](getting-started-with-ink.md).|Voir [exemple de formulaire de déclaration automatique](/windows/desktop/tablet/auto-claims-form-sample)|  
|Activer l’encre sur un contrôle personnalisé|Consultez [création d’un contrôle d’entrée d’encre](creating-an-ink-input-control.md).|Consultez [exemple de presse-papiers manuscrit](/windows/desktop/tablet/ink-clipboard-sample).|  
  
## <a name="ink-data"></a>Données manuscrites  
 Sur les plateformes Windows Forms et COM, Microsoft. Ink [. InkCollector](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms583683(v=vs.90)), [Microsoft. Ink. InkOverlay](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms552322(v=vs.90)), [Microsoft. Ink. InkEdit](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms552265(v=vs.90))et [Microsoft. Ink. InkPicture](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms583740(v=vs.90)) exposent chacun un objet [Microsoft. Ink. Ink](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms583670(v=vs.90)) . L’objet [Microsoft. Ink. Ink](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms583670(v=vs.90)) contient les données d’un ou plusieurs objets [Microsoft. Ink. Stroke](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms552692(v=vs.90)) et expose des méthodes et des propriétés communes pour gérer et manipuler ces traits.  L’objet [Microsoft. Ink. Ink](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms583670(v=vs.90)) gère la durée de vie des traits qu’il contient ; l’objet [Microsoft. Ink. Ink](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms583670(v=vs.90)) crée et supprime les traits qu’il possède.  Chaque [Microsoft. Ink. Stroke](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms552692(v=vs.90)) possède un identificateur unique au sein de son objet [Microsoft. Ink. Ink](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms583670(v=vs.90)) parent.  
  
 Sur la plateforme WPF, la classe <xref:System.Windows.Ink.Stroke?displayProperty=nameWithType> possède et gère sa propre durée de vie. Un groupe d’objets <xref:System.Windows.Ink.Stroke> peut être collecté ensemble dans une <xref:System.Windows.Ink.StrokeCollection>, qui fournit des méthodes pour les opérations courantes de gestion des données d’entrée, telles que le test de positionnement, l’effacement, la transformation et la sérialisation de l’encre. Un <xref:System.Windows.Ink.Stroke> peut appartenir à zéro, un ou plusieurs objets <xref:System.Windows.Ink.StrokeCollection> à un moment donné.  Au lieu d’avoir un objet [Microsoft. Ink. Ink](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms583670(v=vs.90)) , les <xref:System.Windows.Controls.InkCanvas> et <xref:System.Windows.Controls.InkPresenter> contiennent un <xref:System.Windows.Ink.StrokeCollection?displayProperty=nameWithType>.  
  
 Les deux illustrations suivantes comparent les modèles d’objets de données d’encre.  Sur les plateformes Windows Forms et COM, l’objet [Microsoft. Ink. Ink](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms583670(v=vs.90)) limite la durée de vie des objets [Microsoft. Ink. Stroke](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms552692(v=vs.90)) , et les paquets du stylet appartiennent aux traits individuels.  Au moins deux traits peuvent référencer le même objet [Microsoft. Ink. DrawingAttributes](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms583636(v=vs.90)) , comme indiqué dans l’illustration suivante.  
  
 ![Diagramme du modèle d’objet Ink pour COM&#47;WinForms.](./media/ink-inkownsstrokes.png "Ink_InkOwnsStrokes")  
  
 Sur la [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], chaque <xref:System.Windows.Ink.Stroke?displayProperty=nameWithType> est un objet common language runtime qui existe tant qu’un objet y fait référence.  Chaque <xref:System.Windows.Ink.Stroke> fait référence à un objet <xref:System.Windows.Input.StylusPointCollection> et <xref:System.Windows.Ink.DrawingAttributes?displayProperty=nameWithType>, qui sont également common language runtime objets.  
  
 ![Diagramme du modèle d’objet Ink pour WPF.](./media/ink-wpfinkobjectmodel.png "Ink_WPFInkObjectModel")  
  
 Le tableau suivant compare comment accomplir certaines tâches courantes sur la plateforme WPF et les plateformes Windows Forms et COM.  
  
|Tâche|Windows Presentation Foundation|Windows Forms et COM|  
|----------|-------------------------------------|---------------------------|  
|Enregistrer l’encre|<xref:System.Windows.Ink.StrokeCollection.Save%2A>|[Microsoft.Ink.Ink.Save](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms571335(v=vs.90))|  
|Charger l’encre|Créez un <xref:System.Windows.Ink.StrokeCollection> avec le constructeur <xref:System.Windows.Ink.StrokeCollection.%23ctor%2A>.|[Microsoft.Ink.Ink.Load](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms569609(v=vs.90))|  
|Test de positionnement|<xref:System.Windows.Ink.StrokeCollection.HitTest%2A>|[Microsoft.Ink.Ink.HitTest](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms571330(v=vs.90))|  
|Copier l’encre|<xref:System.Windows.Controls.InkCanvas.CopySelection%2A>|[Microsoft.Ink.Ink.ClipboardCopy](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms571316(v=vs.90))|  
|Coller l’encre|<xref:System.Windows.Controls.InkCanvas.Paste%2A>|[Microsoft.Ink.Ink.ClipboardPaste](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms571318(v=vs.90))|  
|Accéder aux propriétés personnalisées d’une collection de traits|<xref:System.Windows.Ink.StrokeCollection.AddPropertyData%2A> (les propriétés sont stockées en interne et accessibles via <xref:System.Windows.Ink.StrokeCollection.AddPropertyData%2A>, <xref:System.Windows.Ink.StrokeCollection.RemovePropertyData%2A>et <xref:System.Windows.Ink.StrokeCollection.ContainsPropertyData%2A>)|Utiliser [Microsoft. Ink. Ink. ExtendedProperties](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms582214(v=vs.90))|  
  
### <a name="sharing-ink-between-platforms"></a>Partage d’encre entre plateformes  
 Bien que les plateformes aient des modèles d’objets différents pour les données d’encre, le partage des données entre les plateformes est très facile. Les exemples suivants enregistrent de l’encre à partir d’une application Windows Forms et chargent l’encre dans une application Windows Presentation Foundation.  
  
 [!code-csharp[WinFormWPFInk#UsingWinforms](~/samples/snippets/csharp/VS_Snippets_Wpf/WinformWPFInk/CSharp/Program.cs#usingwinforms)]
 [!code-vb[WinFormWPFInk#UsingWinforms](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WinformWPFInk/VisualBasic/Module1.vb#usingwinforms)]  
[!code-csharp[WinFormWPFInk#SaveWinforms](~/samples/snippets/csharp/VS_Snippets_Wpf/WinformWPFInk/CSharp/Program.cs#savewinforms)]
[!code-vb[WinFormWPFInk#SaveWinforms](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WinformWPFInk/VisualBasic/Module1.vb#savewinforms)]  
  
 [!code-csharp[WinFormWPFInk#UsingWPF](~/samples/snippets/csharp/VS_Snippets_Wpf/WinformWPFInk/CSharp/Program.cs#usingwpf)]
 [!code-vb[WinFormWPFInk#UsingWPF](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WinformWPFInk/VisualBasic/Module1.vb#usingwpf)]  
[!code-csharp[WinFormWPFInk#LoadWPF](~/samples/snippets/csharp/VS_Snippets_Wpf/WinformWPFInk/CSharp/Program.cs#loadwpf)]
[!code-vb[WinFormWPFInk#LoadWPF](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WinformWPFInk/VisualBasic/Module1.vb#loadwpf)]  
  
 Les exemples suivants enregistrent de l’encre à partir d’une application Windows Presentation Foundation et chargent l’encre dans une application Windows Forms.  
  
 [!code-csharp[WinFormWPFInk#UsingWPF](~/samples/snippets/csharp/VS_Snippets_Wpf/WinformWPFInk/CSharp/Program.cs#usingwpf)]
 [!code-vb[WinFormWPFInk#UsingWPF](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WinformWPFInk/VisualBasic/Module1.vb#usingwpf)]  
[!code-csharp[WinFormWPFInk#SaveWPF](~/samples/snippets/csharp/VS_Snippets_Wpf/WinformWPFInk/CSharp/Program.cs#savewpf)]
[!code-vb[WinFormWPFInk#SaveWPF](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WinformWPFInk/VisualBasic/Module1.vb#savewpf)]  
  
 [!code-csharp[WinFormWPFInk#UsingWinforms](~/samples/snippets/csharp/VS_Snippets_Wpf/WinformWPFInk/CSharp/Program.cs#usingwinforms)]
 [!code-vb[WinFormWPFInk#UsingWinforms](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WinformWPFInk/VisualBasic/Module1.vb#usingwinforms)]  
[!code-csharp[WinFormWPFInk#LoadWinforms](~/samples/snippets/csharp/VS_Snippets_Wpf/WinformWPFInk/CSharp/Program.cs#loadwinforms)]
[!code-vb[WinFormWPFInk#LoadWinforms](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WinformWPFInk/VisualBasic/Module1.vb#loadwinforms)]
## <a name="events-from-the-tablet-pen"></a>Événements du stylet du Tablet PC  

 [Microsoft. Ink. InkOverlay](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms552322(v=vs.90)), [Microsoft. Ink. InkCollector](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms583683(v=vs.90))et [Microsoft. Ink. InkPicture](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms583740(v=vs.90)) sur les plateformes Windows Forms et com reçoivent des événements lorsque l’utilisateur entre des données de stylet. [Microsoft. Ink. InkOverlay](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms552322(v=vs.90)) ou [Microsoft. Ink. InkCollector](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms583683(v=vs.90)) est attaché à une fenêtre ou à un contrôle et peut s’abonner aux événements déclenchés par les données d’entrée de tablette. Le thread sur lequel ces événements se produisent varie selon que les événements sont déclenchés à l’aide d’un stylet, d’une souris ou d’un programme. Pour plus d’informations sur les threads par rapport à ces événements, consultez [Considérations générales sur les threads](/windows/desktop/tablet/general-threading-considerations) et [threads sur lesquels un événement peut se déclencher](/windows/desktop/tablet/threads-on-which-an-event-can-fire).  
  
 Sur la plateforme Windows Presentation Foundation, la classe <xref:System.Windows.UIElement> a des événements pour l’entrée de stylet. Cela signifie que chaque contrôle expose le jeu complet d’événements de stylet.  Les événements de stylet ont des paires d’événements de tunneling/propagation et se produisent toujours sur le thread d’application.  Pour plus d’informations, consultez [vue d’ensemble des événements routés](routed-events-overview.md).  
  
 Le diagramme suivant montre comment comparer les modèles objet pour les classes qui déclenchent des événements de stylet. Le modèle objet Windows Presentation Foundation affiche uniquement les événements de propagation, pas les équivalents d’événement de tunneling.  
  
 ![Diagramme des événements de stylet dans WPF et WinForms.](./media/ink-stylusevents.png "Ink_StylusEvents")  
  
## <a name="pen-data"></a>Données de stylet  
 Les trois plateformes vous permettent d’intercepter et de manipuler les données qui proviennent d’un stylet.  Sur les plateformes Windows Forms et COM, cela est possible en créant un [Microsoft. StylusInput. RealTimeStylus](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms585724(v=vs.90)), en attachant une fenêtre ou un contrôle à celui-ci et en créant une classe qui implémente l’interface [Microsoft. StylusInput. IStylusSyncPlugin](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms575201(v=vs.90)) ou [Microsoft. StylusInput. IStylusAsyncPlugin](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms575194(v=vs.90)) . Le plug-in personnalisé est ensuite ajouté à la collection de plug-ins de [Microsoft. StylusInput. RealTimeStylus](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms585724(v=vs.90)). Pour plus d’informations sur ce modèle objet, consultez [architecture des API StylusInput](/windows/desktop/tablet/architecture-of-the-stylusinput-apis).  
  
 Sur la plateforme WPF, la classe <xref:System.Windows.UIElement> expose une collection de plug-ins, de la même façon que [Microsoft. StylusInput. RealTimeStylus](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms585724(v=vs.90)).  Pour intercepter des données de stylet, créez une classe qui hérite de <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> et ajoutez l’objet à la collection de <xref:System.Windows.UIElement.StylusPlugIns%2A> du <xref:System.Windows.UIElement>. Pour plus d’informations sur cette interaction, consultez [interception de l’entrée à partir du stylet](intercepting-input-from-the-stylus.md).  
  
 Sur toutes les plateformes, un pool de threads reçoit les données d’encre via des événements de stylet et les envoie au thread d’application.  Pour plus d’informations sur les threads sur les plateformes COM et Windows, consultez Considérations sur les [threads pour les API StylusInput](/windows/desktop/tablet/threading-considerations-for-the-stylusinput-apis).  Pour plus d’informations sur les threads sur le logiciel de présentation Windows, consultez [modèle de thread](the-ink-threading-model.md)de l’encre.  
  
 L’illustration suivante compare les modèles objet pour les classes qui reçoivent des données de stylet sur le pool de threads de stylet.  
  
 ![Diagramme du modèle StylusPlugin WPF vs WinForms.](./media/ink-stylusplugins.png "Ink_StylusPlugins")
