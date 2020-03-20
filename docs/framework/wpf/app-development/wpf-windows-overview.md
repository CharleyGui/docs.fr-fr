---
title: Aperçu des fenêtres
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- XAML [WPF], displaying content via
- XAML pages [WPF], displaying
- content [WPF], displaying via XAML
- window objects [WPF]
- hosting [WPF], applications
- managing windows [WPF]
- dialog boxes [WPF]
- Page object [WPF]
- NavigationWindow objects [WPF]
- applications [WPF], hosting
- content [WPF], displaying
- events [WPF]
- content [WPF], displaying via procedural code
- modal windows [WPF]
- procedural code [WPF], displaying content via
- displaying content via procedural code [WPF]
- window management [WPF]
- displaying content [WPF]
- window events [WPF]
- windows [WPF]
- modal dialog boxes [WPF]
- displaying XAML pages [WPF]
ms.assetid: 737d04ec-8861-46c3-8d44-fa11d3528d23
ms.openlocfilehash: b06afb56f43a874815cf9f679f1f7fefbdfd4565
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79145538"
---
# <a name="wpf-windows-overview"></a>Vue d'ensemble des fenêtres WPF
Les utilisateurs interagissent avec les applications autonomes de la Windows Presentation Foundation (WPF) à travers les fenêtres. L’objectif principal d’une fenêtre est d’héberger du contenu qui permet aux utilisateurs de visualiser les données et d’interagir avec celles-ci. Les applications WPF autonomes fournissent leurs <xref:System.Windows.Window> propres fenêtres en utilisant la classe. Ce sujet <xref:System.Windows.Window> introduit avant de couvrir les principes fondamentaux de la création et de la gestion des fenêtres dans des applications autonomes.  
  
> [!NOTE]
> Les applications WPF hébergées par navigateur, y compris les [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] applications de navigateur XAML (XBAP) et les pages en vrac, ne fournissent pas leurs propres fenêtres. Au lieu de cela, ils sont hébergés dans les fenêtres fournies par Windows Internet Explorer. Voir [WPF XAML Browser Applications Aperçu](wpf-xaml-browser-applications-overview.md).  

<a name="TheWindowClass"></a>
## <a name="the-window-class"></a>Window, classe  
 Le chiffre suivant illustre les parties constitutives d’une fenêtre :  
  
 ![Capture d’écran qui montre des éléments de fenêtre.](./media/wpf-windows-overview/window-constituent-elements.png)  
  
 Une fenêtre est divisée en deux zones : la zone non cliente et la zone cliente.  
  
 La *zone non cliente* d’une fenêtre est implémentée par WPF et comprend les parties d’une fenêtre qui sont communes à la plupart des fenêtres, y compris les suivantes:  
  
- bordure ;  
  
- barre de titre ;  
  
- icône ;  
  
- boutons Réduire, Agrandir et Restaurer ;  
  
- bouton Fermer ;  
  
- menu système avec des éléments de menu qui permettent aux utilisateurs de réduire, agrandir, restaurer, déplacer, redimensionner et fermer une fenêtre.  
  
 La *zone client* d’une fenêtre est la zone située dans la zone non cliente d’une fenêtre et est utilisée par les développeurs pour ajouter du contenu spécifique à l’application, comme des barres de menu, des barres d’outils et des commandes.  
  
 Dans WPF, une fenêtre est encapsulée par la <xref:System.Windows.Window> classe que vous utilisez pour faire ce qui suit :  
  
- afficher une fenêtre ;  
  
- configurer la taille, la position et l’apparence d’une fenêtre ;  
  
- héberger un contenu spécifique à l’application ;  
  
- gérer la durée de vie d’une fenêtre.  
  
<a name="DefiningAWindow"></a>
## <a name="implementing-a-window"></a>Implémentation d’une fenêtre  
 La mise en œuvre d’une fenêtre typique comprend à la fois l’apparence et le comportement, où *l’apparence* définit comment une fenêtre regarde les utilisateurs et le *comportement* définit la façon dont une fenêtre fonctionne que les utilisateurs interagissent avec elle. Dans WPF, vous pouvez implémenter l’apparence [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] et le comportement d’une fenêtre en utilisant soit le code ou le balisage.  
  
 En général, cependant, l’apparition d’une fenêtre est implémentée à l’aide [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] de balisage, et son comportement est implémenté en utilisant le code-derrière, comme le montre l’exemple suivant.  
  
 [!code-xaml[WindowsOverviewSnippets#MarkupAndCodeBehindWindowMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/MarkupAndCodeBehindWindow.xaml#markupandcodebehindwindowmarkup)]  
  
 [!code-csharp[WindowsOverviewSnippets#MarkupAndCodeBehindWindowCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/MarkupAndCodeBehindWindow.xaml.cs#markupandcodebehindwindowcodebehind)]
 [!code-vb[WindowsOverviewSnippets#MarkupAndCodeBehindWindowCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WindowsOverviewSnippets/VisualBasic/MarkupAndCodeBehindWindow.xaml.vb#markupandcodebehindwindowcodebehind)]  
  
 Pour permettre [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] à un fichier de balisage et à un fichier de code de travailler ensemble, ce qui suit est requis :  
  
- Dans le balisage, `Window` `x:Class` l’élément doit inclure l’attribut. Lorsque `x:Class` l’application est construite, l’existence de dans le fichier de balisage provoque moteur de construction Microsoft (MSBuild) pour créer une `partial` classe qui dérive et <xref:System.Windows.Window> a le nom qui est spécifié par l’attribut. `x:Class` Cela nécessite l’ajout d’une déclaration [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] D’espace de nom XML pour le schéma ( `xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"` ). La `partial` classe générée `InitializeComponent` implémente la méthode, qui est appelée à enregistrer les événements et à définir les propriétés qui sont mises en œuvre en majoration.  
  
- En vertu du code, la `partial` classe doit être une classe `x:Class` avec le même nom qui <xref:System.Windows.Window>est spécifiée par l’attribut dans la majoration, et il doit dériver de . Cela permet au fichier de code-derrière d’être associé à la `partial` classe qui est générée pour le fichier de balisage lorsque l’application est construite (voir Construire une application [WPF](building-a-wpf-application-wpf.md)).  
  
- En retard de <xref:System.Windows.Window> code, la classe doit `InitializeComponent` implémenter un constructeur qui appelle la méthode. `InitializeComponent`est implémenté par la `partial` classe générée par le fichier de balisage pour enregistrer les événements et définir les propriétés qui sont définies dans le balisage.  
  
> [!NOTE]
> Lorsque vous ajoutez <xref:System.Windows.Window> un nouveau à votre <xref:System.Windows.Window> projet en utilisant Visual Studio, le est implémenté à l’aide de balisage et de code-derrière, et comprend la configuration nécessaire pour créer l’association entre le balisage et les fichiers de code-derrière comme décrit ici.  
  
 Avec cette configuration en place, vous pouvez vous [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] concentrer sur la définition de l’apparence de la fenêtre dans le balisage et la mise en œuvre de son comportement dans le code-derrière. L’exemple suivant montre une fenêtre [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] avec un bouton, implémenté <xref:System.Windows.Controls.Primitives.ButtonBase.Click> en balisage, et un gestionnaire d’événements pour l’événement du bouton, implémenté en code derrière.  
  
 [!code-xaml[WindowsOverviewWindowWithButtonSnippets#MarkupAndCodeBehindWindowMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewWindowWithButtonSnippets/CSharp/MarkupAndCodeBehindWindow.xaml#markupandcodebehindwindowmarkup)]  
  
 [!code-csharp[WindowsOverviewWindowWithButtonSnippets#MarkupAndCodeBehindWindowCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewWindowWithButtonSnippets/CSharp/MarkupAndCodeBehindWindow.xaml.cs#markupandcodebehindwindowcodebehind)]
 [!code-vb[WindowsOverviewWindowWithButtonSnippets#MarkupAndCodeBehindWindowCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WindowsOverviewWindowWithButtonSnippets/VisualBasic/MarkupAndCodeBehindWindow.xaml.vb#markupandcodebehindwindowcodebehind)]  
  
<a name="ConfiguringWindowForMSBuild"></a>
## <a name="configuring-a-window-definition-for-msbuild"></a>Configuration d’une définition de fenêtre pour MSBuild  
 La façon dont vous implémentez votre fenêtre détermine comment elle est configurée pour MSBuild. Pour une fenêtre qui [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] est définie à l’aide de balisage et de code-derrière:  
  
- Les fichiers de balisage XAML `Page` sont configurés sous forme d’éléments MSBuild.  
  
- Les fichiers de code sont configurés sous forme d’éléments MSBuild. `Compile`  
  
 Ceci est indiqué dans le fichier de projet MSBuild suivant.  
  
```xml  
<Project ...  
                xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    ...  
    <Page Include="MarkupAndCodeBehindWindow.xaml" />  
    <Compile Include=" MarkupAndCodeBehindWindow.xaml.cs" />  
    ...  
</Project>  
```  
  
 Pour plus d’informations sur la construction d’applications WPF, voir [Construire une application WPF](building-a-wpf-application-wpf.md).  
  
<a name="WindowLifetime"></a>
## <a name="window-lifetime"></a>Durée de vie d'une fenêtre  
 Comme pour toute classe, une fenêtre a une durée de vie qui commence quand elle est instanciée pour la première fois. Elle est ensuite ouverte, activée et désactivée, et finalement fermée.  

<a name="Opening_a_Window"></a>
### <a name="opening-a-window"></a>Ouverture d’une fenêtre  
 Pour ouvrir une fenêtre, commencez par créer une instance de celle-ci, comme le montre l’exemple suivant.  
  
 [!code-xaml[WindowsOverviewStartupEventSnippets#AppMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewStartupEventSnippets/CSharp/App.xaml#appmarkup)]  
  
 [!code-csharp[WindowsOverviewStartupEventSnippets#AppCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewStartupEventSnippets/CSharp/App.xaml.cs#appcodebehind)]  
  
 Dans cet exemple, l’est `MarkupAndCodeBehindWindow` instantané lorsque l’application <xref:System.Windows.Application.Startup> commence, ce qui se produit lorsque l’événement est soulevé.  
  
 Lorsqu’une fenêtre est instantanée, une référence est automatiquement ajoutée à une <xref:System.Windows.Application> liste de <xref:System.Windows.Application.Windows%2A?displayProperty=nameWithType>fenêtres gérées par l’objet (voir ). En outre, la première fenêtre à être instantanée <xref:System.Windows.Application> est, par défaut, <xref:System.Windows.Application.MainWindow%2A?displayProperty=nameWithType>définie par la fenêtre d’application principale (voir ).  
  
 La fenêtre est enfin <xref:System.Windows.Window.Show%2A> ouverte en appelant la méthode; le résultat est indiqué dans le chiffre suivant.  
  
 ![Une fenêtre ouverte en appelant Window.Show](./media/wpf-windows-overview//window-opened-show-method.png)  
  
 Une fenêtre qui est <xref:System.Windows.Window.Show%2A> ouverte par l’appel est une fenêtre sans mode, ce qui signifie que l’application fonctionne dans un mode qui permet aux utilisateurs d’activer d’autres fenêtres dans la même application.  
  
> [!NOTE]
> <xref:System.Windows.Window.ShowDialog%2A>est appelé à ouvrir des fenêtres telles que les boîtes de dialogue modally. Voir [Dialog Boxes Aperçu](dialog-boxes-overview.md) pour plus d’informations.  
  
 Lorsqu’elle <xref:System.Windows.Window.Show%2A> est appelée, une fenêtre effectue des travaux d’initialisation avant qu’il ne soit montré pour établir l’infrastructure qui lui permet de recevoir l’entrée de l’utilisateur. Lorsque la fenêtre est <xref:System.Windows.Window.SourceInitialized> parascée, l’événement est soulevé et la fenêtre est affichée.  
  
 En tant que <xref:System.Windows.Application.StartupUri%2A> raccourci, peut être défini pour spécifier la première fenêtre qui est ouverte automatiquement quand une application démarre.  
  
 [!code-xaml[WindowsOverviewSnippets#ApplicationStartupUriMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/App.xaml#applicationstartupurimarkup)]  
  
 Lorsque l’application démarre, la fenêtre <xref:System.Windows.Application.StartupUri%2A> spécifiée par la valeur de est ouverte sans mode; en interne, la fenêtre <xref:System.Windows.Window.Show%2A> est ouverte en appelant sa méthode.  
  
<a name="Ownership"></a>
#### <a name="window-ownership"></a>Propriété de la fenêtre  
 Une fenêtre qui est <xref:System.Windows.Window.Show%2A> ouverte en utilisant la méthode n’a pas de relation implicite avec la fenêtre qui l’a créée; les utilisateurs peuvent interagir avec l’une ou l’autre fenêtre indépendamment de l’autre, ce qui signifie que l’une ou l’autre fenêtre peut faire ce qui suit:  
  
- Couvrez l’autre (sauf si <xref:System.Windows.Window.Topmost%2A> l’une des fenêtres a sa propriété réglée à `true`).  
  
- être réduite, agrandie et restaurée sans affecter l’autre fenêtre.  
  
 Certaines fenêtres nécessitent une relation avec la fenêtre qui les ouvre. Par exemple, une application intégrée de développement (IDE) peut ouvrir des fenêtres de propriété et des fenêtres d’outils dont le comportement typique est de couvrir la fenêtre qui les crée. De plus, ces fenêtres doivent toujours se fermer, se réduire, s’agrandir et se restaurer conjointement avec la fenêtre qui les a créées. Une telle relation peut être *own* établie en faisant une fenêtre <xref:System.Windows.Window.Owner%2A> propre une autre, et est atteint en fixant la propriété de la *fenêtre possédée* avec une référence à la fenêtre du *propriétaire*. Cela est illustré par l'exemple suivant.  
  
 [!code-csharp[WindowOwnerOwnedWindowsSnippets#SetWindowOwnerCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowOwnerOwnedWindowsSnippets/CSharp/MainWindow.xaml.cs#setwindowownercode)]
 [!code-vb[WindowOwnerOwnedWindowsSnippets#SetWindowOwnerCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WindowOwnerOwnedWindowsSnippets/visualbasic/mainwindow.xaml.vb#setwindowownercode)]  
  
 Une fois la propriété établie :  
  
- La fenêtre possédée peut faire référence à <xref:System.Windows.Window.Owner%2A> sa fenêtre propriétaire en inspectant la valeur de sa propriété.  
  
- La fenêtre du propriétaire peut découvrir toutes les fenêtres <xref:System.Windows.Window.OwnedWindows%2A> qu’il possède en inspectant la valeur de sa propriété.  
  
<a name="Preventing"></a>
#### <a name="preventing-window-activation"></a>Blocage de l’activation de la fenêtre  
 Il existe des scénarios où les fenêtres ne doivent pas être activées lorsqu’elles sont affichées, telles que les fenêtres de conversation d’une application de type messager Internet ou les fenêtres de notification d’une application de messagerie.  
  
 Si votre application dispose d’une fenêtre qui ne devrait <xref:System.Windows.Window.ShowActivated%2A> pas `false` être <xref:System.Windows.Window.Show%2A> activée lorsqu’elle est indiquée, vous pouvez définir sa propriété avant d’appeler la méthode pour la première fois. En conséquence :  
  
- La fenêtre n’est pas activée.  
  
- L’événement <xref:System.Windows.Window.Activated> de la fenêtre n’est pas soulevé.  
  
- La fenêtre déjà activée reste activée.  
  
 Toutefois, la fenêtre est activée dès que l’utilisateur clique sur la zone cliente ou non cliente. Dans ce cas :  
  
- La fenêtre est activée.  
  
- L’événement <xref:System.Windows.Window.Activated> de la fenêtre est soulevé.  
  
- La fenêtre qui était activée est désactivée.  
  
- La fenêtre <xref:System.Windows.Window.Deactivated> et <xref:System.Windows.Window.Activated> les événements sont ensuite soulevés comme prévu en réponse aux actions des utilisateurs.  
  
<a name="Window_Activation"></a>
### <a name="window-activation"></a>Activation de la fenêtre  
 Quand une fenêtre est ouverte pour la première fois, <xref:System.Windows.Window.ShowActivated%2A> elle `false`devient la fenêtre active (sauf si elle est affichée avec un set to ). La *fenêtre active* est la fenêtre qui capte actuellement l’entrée de l’utilisateur, comme les traits clés et les clics de souris. Lorsqu’une fenêtre devient active, elle soulève l’événement. <xref:System.Windows.Window.Activated>  
  
> [!NOTE]
> Lorsqu’une fenêtre est <xref:System.Windows.FrameworkElement.Loaded> ouverte <xref:System.Windows.Window.ContentRendered> pour la première <xref:System.Windows.Window.Activated> fois, les événements et les événements ne sont soulevés qu’après l’événement. Dans cet esprit, une fenêtre peut <xref:System.Windows.Window.ContentRendered> effectivement être considérée comme ouverte lorsqu’elle est soulevée.  
  
 Une fois qu’une fenêtre est active, un utilisateur peut activer une autre fenêtre de la même application ou activer une autre application. Lorsque cela se produit, la fenêtre actuellement <xref:System.Windows.Window.Deactivated> active devient désactivée et soulève l’événement. De même, lorsque l’utilisateur choisit une fenêtre actuellement désactivée, la fenêtre redevient active et <xref:System.Windows.Window.Activated> est soulevée.  
  
 Une raison commune <xref:System.Windows.Window.Activated> <xref:System.Windows.Window.Deactivated> à manipuler et est d’activer et désactiver les fonctionnalités qui ne peuvent s’exécuter que lorsqu’une fenêtre est active. Par exemple, certaines fenêtres affichent du contenu interactif qui nécessite en permanence l’attention de l’utilisateur ou une entrée de sa part, notamment les jeux et les lecteurs vidéo. L’exemple suivant est un lecteur vidéo <xref:System.Windows.Window.Activated> simplifié <xref:System.Windows.Window.Deactivated> qui démontre comment gérer et implémenter ce comportement.  
  
 [!code-xaml[WindowsOverviewSnippets#ActivationDeactivationMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/CustomMediaPlayerWindow.xaml#activationdeactivationmarkup)]  
  
 [!code-csharp[WindowsOverviewSnippets#ActivationDeactivationCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/CustomMediaPlayerWindow.xaml.cs#activationdeactivationcodebehind)]
 [!code-vb[WindowsOverviewSnippets#ActivationDeactivationCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WindowsOverviewSnippets/VisualBasic/CustomMediaPlayerWindow.xaml.vb#activationdeactivationcodebehind)]  
  
 D’autres types d’application peuvent toujours exécuter du code en arrière-plan quand une fenêtre est désactivée. Par exemple, un client d’e-mail peut continuer à interroger le serveur d’e-mail pendant que l’utilisateur utilise d’autres applications. Les applications de ce type ont souvent un comportement différent ou supplémentaire pendant que la fenêtre principale est désactivée. En ce qui concerne le programme d’e-mail, cela peut signifier l’ajout du nouvel élément d’e-mail à la boîte de réception, ainsi que l’ajout d’une icône de notification à la zone de notification. Une icône de notification n’a besoin d’être affichée que lorsque <xref:System.Windows.Window.IsActive%2A> la fenêtre de courrier n’est pas active, ce qui peut être déterminé en inspectant la propriété.  
  
 Si une tâche d’arrière-plan se termine, une fenêtre <xref:System.Windows.Window.Activate%2A> peut vouloir avertir l’utilisateur plus de toute urgence en appelant la méthode. Si l’utilisateur interagit avec <xref:System.Windows.Window.Activate%2A> une autre application activée lorsqu’elle est appelée, le bouton de la barre des tâches de la fenêtre clignote. Si un utilisateur interagit avec <xref:System.Windows.Window.Activate%2A> l’application actuelle, l’appel mettra la fenêtre au premier plan.  
  
> [!NOTE]
> Vous pouvez gérer l’activation <xref:System.Windows.Application.Activated?displayProperty=nameWithType> <xref:System.Windows.Application.Deactivated?displayProperty=nameWithType> de portée d’application à l’aide de l’application et des événements.  
  
<a name="Closing_a_Window"></a>
### <a name="closing-a-window"></a>Fermeture d’une fenêtre  
 Quand un utilisateur ferme une fenêtre, celle-ci cesse d’exister. Vous pouvez fermer une fenêtre à l’aide d’éléments de la zone non cliente, notamment :  
  
- **L’élément Close** du menu **Système.**  
  
- en appuyant sur Alt+F4 ;  
  
- Appuyez sur le bouton **Close.**  
  
 Vous pouvez fournir des mécanismes supplémentaires à la zone cliente pour fermer une fenêtre, notamment :  
  
- Un élément **de sortie** dans le menu **Fichier,** généralement pour les fenêtres d’application principales.  
  
- Un élément **proche** dans le menu **De fichier,** généralement sur une fenêtre d’application secondaire.  
  
- Un bouton **Annuler,** généralement sur une boîte de dialogue modal.  
  
- Un bouton **Close,** généralement sur une boîte de dialogue sans mode.  
  
 Pour fermer une fenêtre en réponse à l’un <xref:System.Windows.Window.Close%2A> de ces mécanismes personnalisés, vous devez appeler la méthode. L’exemple suivant met en œuvre la possibilité de fermer une fenêtre en choisissant la **sortie** sur le menu **Fichier.**  
  
 [!code-xaml[WindowsOverviewSnippets#WindowWithFileExitMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/WindowWithFileExit.xaml#windowwithfileexitmarkup)]  
  
 [!code-csharp[WindowsOverviewSnippets#WindowWithFileExitCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/WindowWithFileExit.xaml.cs#windowwithfileexitcodebehind)]
 [!code-vb[WindowsOverviewSnippets#WindowWithFileExitCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WindowsOverviewSnippets/VisualBasic/WindowWithFileExit.xaml.vb#windowwithfileexitcodebehind)]  
  
 Quand une fenêtre se ferme, <xref:System.Windows.Window.Closing> elle <xref:System.Windows.Window.Closed>soulève deux événements : et .  
  
 <xref:System.Windows.Window.Closing>est soulevée avant la fermeture de la fenêtre, et il fournit un mécanisme par lequel la fermeture de fenêtre peut être évitée. Bien souvent, la fermeture d’une fenêtre est nécessaire si elle contient des données qui ont été modifiées. Dans cette situation, l’événement peut être géré pour déterminer si les <xref:System.Windows.Window.Closing> données sont sales et, dans l’affirmative, de demander à l’utilisateur de continuer à fermer la fenêtre sans enregistrer les données ou d’annuler la fermeture de fenêtre. L’exemple suivant montre les <xref:System.Windows.Window.Closing>aspects clés de la manipulation .  
  
 [!code-csharp[WindowClosingSnippets](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowClosingSnippets/CSharp/DataWindow.xaml.cs)]
 [!code-vb[WindowClosingSnippets](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WindowClosingSnippets/visualbasic/datawindow.xaml.vb)]  

 Le <xref:System.Windows.Window.Closing> gestionnaire de <xref:System.ComponentModel.CancelEventArgs>l’événement est `Boolean` <xref:System.ComponentModel.CancelEventArgs.Cancel%2A> passé un `true` , qui met en œuvre la propriété que vous avez mis à empêcher une fenêtre de fermer.  
  
 Si <xref:System.Windows.Window.Closing> elle n’est pas manipulée ou s’il est manipulé mais non annulé, la fenêtre se fermera. Juste avant qu’une <xref:System.Windows.Window.Closed> fenêtre ne ferme, est soulevée. À ce stade, il est impossible d’empêcher une fenêtre de se fermer.  
  
> [!NOTE]
> Une application peut être configurée pour s’arrêter automatiquement <xref:System.Windows.Application.MainWindow%2A>lorsque la fenêtre d’application principale se ferme (voir ) ou que la dernière fenêtre se ferme. Pour plus d'informations, consultez <xref:System.Windows.Application.ShutdownMode%2A>.  
  
 Bien qu’une fenêtre puisse être explicitement fermée par le biais de mécanismes fournis dans les zones non clientes et clientes, une fenêtre peut également être implicitement fermée en raison d’un comportement dans d’autres parties de l’application ou de Windows, y compris ce qui suit :  
  
- Un utilisateur se connecte ou éteint Windows.  
  
- Le propriétaire d’une fenêtre <xref:System.Windows.Window.Owner%2A>se ferme (voir ).  
  
- La fenêtre d’application <xref:System.Windows.Application.ShutdownMode%2A> <xref:System.Windows.ShutdownMode.OnMainWindowClose>principale est fermée et est .  
  
- <xref:System.Windows.Application.Shutdown%2A> est appelée.  
  
> [!NOTE]
> Une fenêtre ne peut pas être rouverte après sa fermeture.  
  
<a name="Window_Lifetime_Events"></a>
### <a name="window-lifetime-events"></a>Événements de la durée de vie d’une fenêtre  
 L’illustration suivante montre la séquence des principaux événements dans la durée de vie d’une fenêtre :  
  
 ![Diagramme qui montre les événements dans la vie d’une fenêtre.](./media/wpf-windows-overview/window-lifetime-events.png)  
  
 L’illustration suivante montre la séquence des principaux événements dans la<xref:System.Windows.Window.ShowActivated%2A> durée de `false` vie d’une fenêtre qui est montrée sans activation (est réglée avant que la fenêtre soit montrée) :  
  
 ![Diagramme qui montre les événements dans la vie d’une fenêtre sans activation.](./media/wpf-windows-overview/window-lifetime-no-activation.png)  
  
<a name="WindowLocation"></a>
## <a name="window-location"></a>Emplacement d’une fenêtre  
 Quand une fenêtre est ouverte, elle dispose d’un emplacement dans les dimensions x et y du Bureau. Cet emplacement peut être déterminé <xref:System.Windows.Window.Left%2A> <xref:System.Windows.Window.Top%2A> en inspectant le et les propriétés, respectivement. Vous pouvez définir ces propriétés pour changer l’emplacement de la fenêtre.  
  
 Vous pouvez également spécifier l’emplacement initial d’un <xref:System.Windows.Window> moment où il apparaît pour la première fois en définissant la <xref:System.Windows.Window.WindowStartupLocation%2A> propriété avec l’une des valeurs de recensement suivantes <xref:System.Windows.WindowStartupLocation> :  
  
- <xref:System.Windows.WindowStartupLocation.CenterOwner> (par défaut)  
  
- <xref:System.Windows.WindowStartupLocation.CenterScreen>  
  
- <xref:System.Windows.WindowStartupLocation.Manual>  
  
 Si l’emplacement de <xref:System.Windows.WindowStartupLocation.Manual>démarrage <xref:System.Windows.Window.Left%2A> est <xref:System.Windows.Window.Top%2A> spécifié comme, <xref:System.Windows.Window> et le et les propriétés n’ont pas été définies, demandera à Windows pour un emplacement d’apparaître dans.  
  
<a name="Topmost_Windows_and_Z_Order"></a>
### <a name="topmost-windows-and-z-order"></a>Fenêtres au premier plan et ordre de plan  
 Outre un emplacement dans les dimensions x et y, une fenêtre a également un emplacement dans la dimension z, qui détermine sa position verticale par rapport à d’autres fenêtres. Il s’agit de l’ordre de plan de la fenêtre. Il en existe deux types : l’ordre de plan normal et l’ordre de plan le plus haut. L’emplacement d’une fenêtre dans *l’ordre z normal* est déterminé par si elle est actuellement active ou non. Par défaut, une fenêtre est située dans l’ordre de plan normal. L’emplacement d’une fenêtre dans *l’ordre z le plus élevé* est également déterminé par si elle est actuellement active ou non. De plus, les fenêtres dans l’ordre de plan le plus haut sont toujours situées au-dessus des fenêtres dans l’ordre de plan normal. Une fenêtre est située dans l’ordre <xref:System.Windows.Window.Topmost%2A> z `true`le plus haut en fixant sa propriété à .  
  
 [!code-xaml[WindowsOverviewSnippets#TopmostWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/TopmostWindow.xaml#topmostwindowmarkup1)]  
  
 Dans chaque ordre de plan, la fenêtre active apparaît au-dessus de toutes les autres fenêtres du même ordre de plan.  
  
<a name="WindowSize"></a>
## <a name="window-size"></a>Taille de la fenêtre  
 En plus d’avoir un emplacement de bureau, une fenêtre a une taille <xref:System.Windows.Window.SizeToContent%2A>qui est déterminée par plusieurs propriétés, y compris les différentes largeurs et propriétés de hauteur et .  
  
 <xref:System.Windows.FrameworkElement.MinWidth%2A>, <xref:System.Windows.FrameworkElement.Width%2A>et <xref:System.Windows.FrameworkElement.MaxWidth%2A> sont utilisés pour gérer la gamme de largeurs qu’une fenêtre peut avoir au cours de sa vie, et sont configurés comme indiqué dans l’exemple suivant.  
  
 [!code-xaml[WindowsOverviewSnippets#WidthWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/WidthWindow.xaml#widthwindowmarkup1)]  
  
 La hauteur de <xref:System.Windows.FrameworkElement.MinHeight%2A> <xref:System.Windows.FrameworkElement.Height%2A>fenêtre <xref:System.Windows.FrameworkElement.MaxHeight%2A>est gérée par, , et , et sont configurées comme indiqué dans l’exemple suivant.  
  
 [!code-xaml[WindowsOverviewSnippets#HeightWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/HeightWindow.xaml#heightwindowmarkup1)]  
  
 Comme les diverses valeurs de largeur et de hauteur spécifient chacune une plage, il est possible pour la largeur et la hauteur d’une fenêtre redimensionnable de se situer n’importe où dans la plage spécifiée pour la dimension respective. Pour détecter sa largeur et <xref:System.Windows.FrameworkElement.ActualWidth%2A> <xref:System.Windows.FrameworkElement.ActualHeight%2A>sa hauteur actuelles, inspectez et, respectivement.  
  
 Si vous souhaitez que la largeur et la hauteur de votre fenêtre aient une taille qui <xref:System.Windows.Window.SizeToContent%2A> correspond à la taille du contenu de la fenêtre, vous pouvez utiliser la propriété, qui a les valeurs suivantes :  
  
- <xref:System.Windows.SizeToContent.Manual>. Aucun effet (par défaut).  
  
- <xref:System.Windows.SizeToContent.Width>. Ajustement à la largeur de contenu, <xref:System.Windows.FrameworkElement.MinWidth%2A> qui <xref:System.Windows.FrameworkElement.MaxWidth%2A> a le même effet que la mise à la fois et à la largeur du contenu.  
  
- <xref:System.Windows.SizeToContent.Height>. Ajustement à la hauteur de contenu, <xref:System.Windows.FrameworkElement.MinHeight%2A> qui <xref:System.Windows.FrameworkElement.MaxHeight%2A> a le même effet que la définition à la fois et à la hauteur du contenu.  
  
- <xref:System.Windows.SizeToContent.WidthAndHeight>. Ajustement à la largeur de contenu et la <xref:System.Windows.FrameworkElement.MinHeight%2A> <xref:System.Windows.FrameworkElement.MaxHeight%2A> hauteur, qui a le même <xref:System.Windows.FrameworkElement.MinWidth%2A> <xref:System.Windows.FrameworkElement.MaxWidth%2A> effet que la mise à la fois et à la hauteur du contenu, et la définition à la fois et à la largeur du contenu.  
  
 L’exemple suivant montre une fenêtre qui s’ajuste automatiquement en fonction de son contenu, verticalement et horizontalement, au moment où elle s’affiche pour la première fois.  
  
 [!code-xaml[WindowsOverviewSnippets#SizeToContentWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/SizeToContentWindow.xaml#sizetocontentwindowmarkup1)]  
  
 L’exemple suivant montre <xref:System.Windows.Window.SizeToContent%2A> comment définir la propriété en code pour spécifier comment une fenêtre resizes pour s’adapter à son contenu .
  
 [!code-csharp[HOWTOWindowManagementSnippets#SetWindowSizeToContentPropertyCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/CSharp/MainWindow.xaml.cs#setwindowsizetocontentpropertycode)]
 [!code-vb[HOWTOWindowManagementSnippets#SetWindowSizeToContentPropertyCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/visualbasic/mainwindow.xaml.vb#setwindowsizetocontentpropertycode)]  
  
<a name="OrderOfPrecedence"></a>
## <a name="order-of-precedence-for-sizing-properties"></a>Ordre de priorité des propriétés de dimensionnement  
 Pour l’essentiel, les diverses propriétés de dimensionnement d’une fenêtre se combinent pour définir la plage de largeur et de hauteur d’une fenêtre redimensionnable. Pour s’assurer qu’une <xref:System.Windows.Window> plage valide est maintenue, évalue les valeurs des propriétés de taille en utilisant les ordres de préséance suivants.  
  
 **Pour les propriétés de hauteur :**  
  
1. <xref:System.Windows.FrameworkElement.MinHeight%2A?displayProperty=nameWithType>
  
2. <xref:System.Windows.FrameworkElement.MaxHeight%2A?displayProperty=nameWithType>
  
3. <xref:System.Windows.SizeToContent.Height?displayProperty=nameWithType>/<xref:System.Windows.SizeToContent.WidthAndHeight?displayProperty=nameWithType>
  
4. <xref:System.Windows.FrameworkElement.Height%2A?displayProperty=nameWithType>  
  
 **Pour les propriétés de largeur :**  
  
1. <xref:System.Windows.FrameworkElement.MinWidth%2A?displayProperty=nameWithType>
  
2. <xref:System.Windows.FrameworkElement.MaxWidth%2A?displayProperty=nameWithType>
  
3. <xref:System.Windows.SizeToContent.Width?displayProperty=nameWithType>/<xref:System.Windows.SizeToContent.WidthAndHeight?displayProperty=nameWithType>
  
4. <xref:System.Windows.FrameworkElement.Width%2A?displayProperty=nameWithType>  
  
 L’ordre de préséance peut également déterminer la taille d’une <xref:System.Windows.Window.WindowState%2A> fenêtre lorsqu’elle est maximisée, qui est gérée avec la propriété.  
  
<a name="WindowState"></a>
## <a name="window-state"></a>État de la fenêtre  
 Au cours de sa durée de vie, une fenêtre redimensionnable peut avoir trois états : normal, réduit et agrandi. Une fenêtre avec un état *normal* est l’état par défaut d’une fenêtre. Quand une fenêtre est dans cet état, l’utilisateur peut la déplacer et la redimensionner à l’aide d’une poignée de redimensionnement ou de la bordure, si elle est redimensionnable.  
  
 Une fenêtre avec un état *minimisé* s’effondre <xref:System.Windows.Window.ShowInTaskbar%2A> à `true`son bouton de barre de tâche si elle est réglée à ; sinon, il s’effondre à la plus petite taille possible, il peut être et se déplace dans le coin inférieur gauche du bureau. Aucun type de fenêtre réduite ne peut être redimensionné à l’aide d’une bordure ou d’une poignée de redimensionnement. Toutefois, une fenêtre réduite qui n’est pas affichée dans la barre des tâches peut être déplacée partout sur le Bureau.  
  
 Une fenêtre avec un état *maximisé* s’étend à la taille maximale <xref:System.Windows.FrameworkElement.MaxWidth%2A>qu’il peut être, qui ne sera aussi grande que son , <xref:System.Windows.FrameworkElement.MaxHeight%2A>, et <xref:System.Windows.Window.SizeToContent%2A> les propriétés dictent. Comme pour une fenêtre réduite, vous ne pouvez pas redimensionner une fenêtre agrandie à l’aide d’une poignée de redimensionnement ou en faisant glisser sa bordure.  
  
> [!NOTE]
> Les valeurs <xref:System.Windows.Window.Top%2A>de <xref:System.Windows.Window.Left%2A> <xref:System.Windows.FrameworkElement.Width%2A>la <xref:System.Windows.FrameworkElement.Height%2A> , , et les propriétés d’une fenêtre représentent toujours les valeurs pour l’état normal, même lorsque la fenêtre est actuellement maximisée ou minimisée.  
  
 L’état d’une fenêtre peut <xref:System.Windows.Window.WindowState%2A> être configuré en définissant sa propriété, qui peut avoir l’une des valeurs d’énumération suivantes <xref:System.Windows.WindowState> :  
  
- <xref:System.Windows.WindowState.Normal> (par défaut)  
  
- <xref:System.Windows.WindowState.Maximized>  
  
- <xref:System.Windows.WindowState.Minimized>  
  
 L’exemple suivant montre comment créer une fenêtre agrandie quand elle s’ouvre.  
  
 [!code-xaml[WindowsOverviewSnippets#WindowStateWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/WindowStateWindow.xaml#windowstatewindowmarkup1)]  
  
 En général, vous <xref:System.Windows.Window.WindowState%2A> devez configurer l’état initial d’une fenêtre. Une fois qu’une fenêtre redimensionnable est affichée, les utilisateurs peuvent cliquer dans la barre de titre de la fenêtre sur les boutons de réduction, d’agrandissement et de restauration pour changer son état.  
  
<a name="WindowAppearance"></a>
## <a name="window-appearance"></a>Apparence de la fenêtre  
 Vous pouvez changer l’apparence de la zone cliente d’une fenêtre en lui ajoutant un contenu spécifique, par exemple des boutons, des étiquettes et des zones de texte. Pour configurer la zone <xref:System.Windows.Window> non cliente, <xref:System.Windows.Window.Icon%2A> fournit plusieurs propriétés, <xref:System.Windows.Window.Title%2A> qui comprennent pour définir l’icône d’une fenêtre et de définir son titre.  
  
 Vous pouvez également changer l’apparence et le comportement d’une bordure de zone non cliente en configurant le mode de redimensionnement d’une fenêtre, le style de fenêtre, ainsi que son affichage ou non sous forme de bouton dans la barre des tâches du Bureau.  

<a name="Resize_Mode"></a>
### <a name="resize-mode"></a>Mode de redimensionnement  
 Selon la <xref:System.Windows.Window.WindowStyle%2A> propriété, vous pouvez contrôler comment (et si) les utilisateurs peuvent resize la fenêtre. Le choix du style de fenêtre influe sur la question de savoir si un utilisateur peut redimensionner la fenêtre en faisant glisser sa bordure avec la souris, si les boutons **Minimize,** **Maximisent**et **redimensionnent** apparaissent sur la zone non cliente et, s’ils apparaissent, s’ils sont activés.  
  
 Vous pouvez configurer comment une fenêtre <xref:System.Windows.Window.ResizeMode%2A> resizes en définissant <xref:System.Windows.ResizeMode> sa propriété, qui peut être l’une des valeurs de recensement suivantes:  
  
- <xref:System.Windows.ResizeMode.NoResize>  
  
- <xref:System.Windows.ResizeMode.CanMinimize>  
  
- <xref:System.Windows.ResizeMode.CanResize> (par défaut)  
  
- <xref:System.Windows.ResizeMode.CanResizeWithGrip>  
  
 Comme <xref:System.Windows.Window.WindowStyle%2A>avec, le mode de resize d’une fenêtre est peu susceptible de changer [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] au cours de sa vie, ce qui signifie que vous aurez très probablement le définir à partir de balisage.  
  
 [!code-xaml[WindowsOverviewSnippets#ResizeModeWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/ResizeModeWindow.xaml#resizemodewindowmarkup1)]  
  
 Notez que vous pouvez détecter si une fenêtre est maximisée, minimisée ou restaurée en inspectant la <xref:System.Windows.Window.WindowState%2A> propriété.  
  
<a name="Window_Style"></a>
### <a name="window-style"></a>Style de la fenêtre  
 La bordure exposée à partir de la zone non cliente d’une fenêtre convient à la plupart des applications. Toutefois, selon les circonstances, il arrive que d’autres types de bordure (voire aucune bordure) soient nécessaires, en fonction du type de fenêtre.  
  
 Pour contrôler le type de bordure d’une fenêtre, vous définissez sa <xref:System.Windows.Window.WindowStyle%2A> propriété avec l’une des valeurs suivantes de l’énumération <xref:System.Windows.WindowStyle> :  
  
- <xref:System.Windows.WindowStyle.None>  
  
- <xref:System.Windows.WindowStyle.SingleBorderWindow> (par défaut)  
  
- <xref:System.Windows.WindowStyle.ThreeDBorderWindow>  
  
- <xref:System.Windows.WindowStyle.ToolWindow>  
  
 L’effet de ces styles de fenêtre est illustré dans la figure suivante :  
  
 ![Illustration des styles de bordure de fenêtre.](./media/wpf-windows-overview/window-border-styles.png)  
  
 Vous pouvez <xref:System.Windows.Window.WindowStyle%2A> définir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] en utilisant le balisage ou le code; parce qu’il est peu probable de changer au cours de [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] la durée de vie d’une fenêtre, vous serez très probablement le configurer en utilisant le balisage.  
  
 [!code-xaml[WindowsOverviewSnippets#WindowStyleWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/WindowStyleWindow.xaml#windowstylewindowmarkup1)]  
  
#### <a name="non-rectangular-window-style"></a>Style de fenêtre non rectangulaire  
 Il ya aussi des situations <xref:System.Windows.Window.WindowStyle%2A> où les styles de frontière qui vous permet d’avoir ne sont pas suffisants. Par exemple, vous pouvez créer une application avec une bordure non rectangulaire, comme Microsoft Windows Media Player utilise.  
  
 Par exemple, considérez la fenêtre de bulle de discours indiquée dans la figure suivante :  
  
 ![Une fenêtre de bulle de la parole qui dit Drag Me.](./media/wpf-windows-overview/non-rectangular-window-figure.png)  
  
 Ce type de fenêtre peut <xref:System.Windows.Window.WindowStyle%2A> être <xref:System.Windows.WindowStyle.None>créé en définissant <xref:System.Windows.Window> la propriété à , et en utilisant un soutien spécial qui a pour la transparence.  
  
 [!code-xaml[WindowsOverviewSnippets#TransparentWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/TransparentWindow.xaml#transparentwindowmarkup1)]  
  
 Cette combinaison de valeurs indique à la fenêtre de s’afficher de manière totalement transparente. Dans cet état, les ornements de la zone non cliente (menu Fermer, boutons Réduire, Agrandir, Restaurer, etc.) de la fenêtre ne peuvent pas être utilisés. Vous devez donc fournir vos propres ornements.  
  
<a name="Task_Bar_Presence"></a>
### <a name="task-bar-presence"></a>Présence de la barre des tâches  

L’apparence par défaut d’une fenêtre comprend un bouton de barre des tâches, comme celui indiqué dans la figure suivante :

 ![Capture d’écran qui montre une fenêtre avec un bouton de barre des tâches.](./media/wpf-windows-overview/window-taskbar-button.png)  
  
 Certains types de fenêtres n’ont pas de bouton de barre de tâche, comme des boîtes de message et des boîtes de dialogue (voir [Dialog Boxes Overview](dialog-boxes-overview.md)). Vous pouvez contrôler si le bouton de barre <xref:System.Windows.Window.ShowInTaskbar%2A> de`true` tâche pour une fenêtre est affiché en définissant la propriété (par défaut).  
  
 [!code-xaml[WindowsOverviewSnippets#ShowInTaskbarWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/ShowInTaskbarWindow.xaml#showintaskbarwindowmarkup1)]  
  
<a name="SecurityConsiderations"></a>
## <a name="security-considerations"></a>Considérations relatives à la sécurité  
 <xref:System.Windows.Window>exige `UnmanagedCode` l’autorisation de sécurité pour être instantanée. Pour les applications installées sur la machine locale et lancées à partir de celle-ci, cette autorisation fait partie du jeu d’autorisations accordé à l’application.  
  
 Toutefois, cela ne relève pas de l’ensemble des autorisations accordées aux applications qui sont lancées à partir de la zone intranet d’Internet ou locale à l’aide de ClickOnce. Par conséquent, les utilisateurs recevront un avertissement de sécurité ClickOnce et devront élever l’autorisation définie pour l’application à pleine confiance.  
  
 En outre, les XAP ne peuvent pas afficher les fenêtres ou les boîtes de dialogue par défaut. Pour une discussion sur les considérations de sécurité d’application autonomes, voir [WPF Security Strategy - Platform Security](../wpf-security-strategy-platform-security.md).  
  
<a name="Other_Types_of_Windows"></a>
## <a name="other-types-of-windows"></a>Autres types de fenêtre  
 <xref:System.Windows.Navigation.NavigationWindow>est une fenêtre conçue pour héberger du contenu navigable. Pour plus d’informations, voir [Aperçu de la navigation](navigation-overview.md)).  
  
 Les boîtes de dialogue sont des fenêtres souvent utilisées pour rassembler des informations fournies par un utilisateur afin d’exécuter une fonction. Par exemple, lorsqu’un utilisateur souhaite ouvrir un fichier, la boîte de dialogue **Open File** est généralement affichée par une application pour obtenir le nom du fichier de l’utilisateur. Pour plus d’informations, consultez [Vue d’ensemble des boîtes de dialogue](dialog-boxes-overview.md).  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Window>
- <xref:System.Windows.MessageBox>
- <xref:System.Windows.Navigation.NavigationWindow>
- <xref:System.Windows.Application>
- [Vue d'ensemble des boîtes de dialogue](dialog-boxes-overview.md)
- [Génération d'une application WPF](building-a-wpf-application-wpf.md)
