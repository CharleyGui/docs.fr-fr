---
title: Vue d’ensemble de Windows
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
ms.openlocfilehash: 17582192fabf85777bba250f6f53047a84f264b9
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742362"
---
# <a name="wpf-windows-overview"></a>Vue d'ensemble des fenêtres WPF
Les utilisateurs interagissent avec les applications autonomes de Windows Presentation Foundation (WPF) par le biais de Windows. L’objectif principal d’une fenêtre est d’héberger du contenu qui permet aux utilisateurs de visualiser les données et d’interagir avec celles-ci. Les applications WPF autonomes fournissent leurs propres fenêtres à l’aide de la classe <xref:System.Windows.Window>. Cette rubrique présente <xref:System.Windows.Window> avant de couvrir les notions de base de la création et de la gestion de Windows dans des applications autonomes.  
  
> [!NOTE]
> Les applications WPF hébergées par le navigateur, y compris les applications de navigateur XAML (XBAP) et les pages de [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] faible, ne fournissent pas leurs propres fenêtres. Au lieu de cela, ils sont hébergés dans Windows fourni par Windows Internet Explorer. Consultez [vue d’ensemble des applications de navigateur XAML WPF](wpf-xaml-browser-applications-overview.md).  

<a name="TheWindowClass"></a>   
## <a name="the-window-class"></a>Window, classe  
 L’illustration suivante montre les parties constitutives d’une fenêtre :  
  
 ![Capture d’écran montrant les éléments de la fenêtre.](./media/wpf-windows-overview/window-constituent-elements.png)  
  
 Une fenêtre est divisée en deux zones : la zone non cliente et la zone cliente.  
  
 La *zone non cliente* d’une fenêtre est implémentée par WPF et inclut les parties d’une fenêtre qui sont communes à la plupart des fenêtres, y compris les éléments suivants :  
  
- bordure ;  
  
- barre de titre ;  
  
- icône ;  
  
- boutons Réduire, Agrandir et Restaurer ;  
  
- bouton Fermer ;  
  
- menu système avec des éléments de menu qui permettent aux utilisateurs de réduire, agrandir, restaurer, déplacer, redimensionner et fermer une fenêtre.  
  
 La *zone cliente* d’une fenêtre est la zone dans la zone non cliente d’une fenêtre et est utilisée par les développeurs pour ajouter du contenu spécifique à l’application, comme des barres de menus, des barres d’outils et des contrôles.  
  
 Dans WPF, une fenêtre est encapsulée par la classe <xref:System.Windows.Window> que vous utilisez pour effectuer les opérations suivantes :  
  
- afficher une fenêtre ;  
  
- configurer la taille, la position et l’apparence d’une fenêtre ;  
  
- héberger un contenu spécifique à l’application ;  
  
- gérer la durée de vie d’une fenêtre.  
  
<a name="DefiningAWindow"></a>   
## <a name="implementing-a-window"></a>Implémentation d’une fenêtre  
 L’implémentation d’une fenêtre classique comprend à la fois l’apparence et le comportement, où l' *apparence* définit la façon dont une fenêtre se présente aux utilisateurs et le *comportement* définit la façon dont une fenêtre fonctionne comme les utilisateurs interagissent avec elle. Dans WPF, vous pouvez implémenter l’apparence et le comportement d’une fenêtre à l’aide d’un code ou d’un balisage [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].  
  
 En général, toutefois, l’apparence d’une fenêtre est implémentée à l’aide d' [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] balisage, et son comportement est implémenté à l’aide de code-behind, comme indiqué dans l’exemple suivant.  
  
 [!code-xaml[WindowsOverviewSnippets#MarkupAndCodeBehindWindowMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/MarkupAndCodeBehindWindow.xaml#markupandcodebehindwindowmarkup)]  
  
 [!code-csharp[WindowsOverviewSnippets#MarkupAndCodeBehindWindowCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/MarkupAndCodeBehindWindow.xaml.cs#markupandcodebehindwindowcodebehind)]
 [!code-vb[WindowsOverviewSnippets#MarkupAndCodeBehindWindowCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WindowsOverviewSnippets/VisualBasic/MarkupAndCodeBehindWindow.xaml.vb#markupandcodebehindwindowcodebehind)]  
  
 Pour permettre à un fichier de balisage [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] et à un fichier code-behind de fonctionner ensemble, les conditions suivantes sont requises :  
  
- Dans le balisage, l’élément `Window` doit inclure l’attribut `x:Class`. Lorsque l’application est générée, l’existence d' `x:Class` dans le fichier de balisage permet à Microsoft Build Engine (MSBuild) de créer une classe `partial` qui dérive de <xref:System.Windows.Window> et qui porte le nom spécifié par l’attribut `x:Class`. Cela nécessite l’ajout d’une déclaration d’espace de noms XML pour le schéma de [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] (`xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"`). La classe `partial` générée implémente la méthode `InitializeComponent`, qui est appelée pour inscrire les événements et définir les propriétés implémentées dans le balisage.  
  
- Dans le code-behind, la classe doit être une classe `partial` portant le même nom que celui spécifié par l’attribut `x:Class` dans le balisage, et elle doit dériver de <xref:System.Windows.Window>. Cela permet au fichier code-behind d’être associé à la classe `partial` générée pour le fichier de balisage quand l’application est générée (consultez [génération d’une application WPF](building-a-wpf-application-wpf.md)).  
  
- Dans le code-behind, la classe <xref:System.Windows.Window> doit implémenter un constructeur qui appelle la méthode `InitializeComponent`. `InitializeComponent` est implémenté par la classe `partial` générée du fichier de balisage pour inscrire les événements et définir les propriétés définies dans le balisage.  
  
> [!NOTE]
> Lorsque vous ajoutez un nouveau <xref:System.Windows.Window> à votre projet à l’aide de Visual Studio, le <xref:System.Windows.Window> est implémenté à l’aide du balisage et du code-behind, et comprend la configuration nécessaire pour créer l’association entre les fichiers de balisage et code-behind, comme décrit ici.  
  
 Une fois cette configuration en place, vous pouvez vous concentrer sur la définition de l’apparence de la fenêtre dans [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] le balisage et l’implémentation de son comportement dans du code-behind. L’exemple suivant montre une fenêtre avec un bouton, implémentée dans [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] balisage, et un gestionnaire d’événements pour l’événement <xref:System.Windows.Controls.Primitives.ButtonBase.Click> du bouton, implémenté dans le code-behind.  
  
 [!code-xaml[WindowsOverviewWindowWithButtonSnippets#MarkupAndCodeBehindWindowMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewWindowWithButtonSnippets/CSharp/MarkupAndCodeBehindWindow.xaml#markupandcodebehindwindowmarkup)]  
  
 [!code-csharp[WindowsOverviewWindowWithButtonSnippets#MarkupAndCodeBehindWindowCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewWindowWithButtonSnippets/CSharp/MarkupAndCodeBehindWindow.xaml.cs#markupandcodebehindwindowcodebehind)]
 [!code-vb[WindowsOverviewWindowWithButtonSnippets#MarkupAndCodeBehindWindowCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WindowsOverviewWindowWithButtonSnippets/VisualBasic/MarkupAndCodeBehindWindow.xaml.vb#markupandcodebehindwindowcodebehind)]  
  
<a name="ConfiguringWindowForMSBuild"></a>   
## <a name="configuring-a-window-definition-for-msbuild"></a>Configuration d’une définition de fenêtre pour MSBuild  
 La façon dont vous implémentez votre fenêtre détermine son mode de configuration pour MSBuild. Pour une fenêtre définie à l’aide du balisage [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] et du code-behind :  
  
- Les fichiers de balisage XAML sont configurés en tant qu’éléments `Page` MSBuild.  
  
- Les fichiers code-behind sont configurés en tant qu’éléments `Compile` MSBuild.  
  
 Cela est illustré dans le fichier projet MSBuild suivant.  
  
```xml  
<Project ...  
                xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    ...  
    <Page Include="MarkupAndCodeBehindWindow.xaml" />  
    <Compile Include=" MarkupAndCodeBehindWindow.xaml.cs" />  
    ...  
</Project>  
```  
  
 Pour plus d’informations sur la création d’applications WPF, consultez [génération d’une application WPF](building-a-wpf-application-wpf.md).  
  
<a name="WindowLifetime"></a>   
## <a name="window-lifetime"></a>Durée de vie d'une fenêtre  
 Comme pour toute classe, une fenêtre a une durée de vie qui commence quand elle est instanciée pour la première fois. Elle est ensuite ouverte, activée et désactivée, et finalement fermée.  

<a name="Opening_a_Window"></a>   
### <a name="opening-a-window"></a>Ouverture d’une fenêtre  
 Pour ouvrir une fenêtre, commencez par créer une instance de celle-ci, comme le montre l’exemple suivant.  
  
 [!code-xaml[WindowsOverviewStartupEventSnippets#AppMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewStartupEventSnippets/CSharp/App.xaml#appmarkup)]  
  
 [!code-csharp[WindowsOverviewStartupEventSnippets#AppCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewStartupEventSnippets/CSharp/App.xaml.cs#appcodebehind)]  
  
 Dans cet exemple, le `MarkupAndCodeBehindWindow` est instancié au démarrage de l’application, ce qui se produit lorsque l’événement <xref:System.Windows.Application.Startup> est déclenché.  
  
 Quand une fenêtre est instanciée, une référence à celle-ci est automatiquement ajoutée à une liste de fenêtres gérée par l’objet <xref:System.Windows.Application> (consultez <xref:System.Windows.Application.Windows%2A?displayProperty=nameWithType>). En outre, la première fenêtre à instancier est, par défaut, définie par <xref:System.Windows.Application> comme fenêtre d’application principale (consultez <xref:System.Windows.Application.MainWindow%2A?displayProperty=nameWithType>).  
  
 La fenêtre est enfin ouverte en appelant la méthode <xref:System.Windows.Window.Show%2A> ; le résultat est illustré dans la figure suivante.  
  
 ![Fenêtre ouverte en appelant Window. Show](./media/wpf-windows-overview//window-opened-show-method.png)  
  
 Une fenêtre ouverte en appelant <xref:System.Windows.Window.Show%2A> est une fenêtre non modale, ce qui signifie que l’application fonctionne dans un mode qui permet aux utilisateurs d’activer d’autres fenêtres dans la même application.  
  
> [!NOTE]
> <xref:System.Windows.Window.ShowDialog%2A> est appelée pour ouvrir des fenêtres, telles que des boîtes de dialogue modales. Pour plus d’informations, consultez [vue d’ensemble des boîtes de dialogue](dialog-boxes-overview.md) .  
  
 Lorsque <xref:System.Windows.Window.Show%2A> est appelée, une fenêtre effectue un travail d’initialisation avant de l’afficher pour établir l’infrastructure qui lui permet de recevoir des entrées utilisateur. Lorsque la fenêtre est initialisée, l’événement <xref:System.Windows.Window.SourceInitialized> est déclenché et la fenêtre est affichée.  
  
 En guise de raccourci, <xref:System.Windows.Application.StartupUri%2A> peut être définie pour spécifier la première fenêtre qui s’ouvre automatiquement au démarrage d’une application.  
  
 [!code-xaml[WindowsOverviewSnippets#ApplicationStartupUriMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/App.xaml#applicationstartupurimarkup)]  
  
 Lorsque l’application démarre, la fenêtre spécifiée par la valeur de <xref:System.Windows.Application.StartupUri%2A> s’ouvre de façon non modale ; en interne, la fenêtre est ouverte en appelant sa méthode <xref:System.Windows.Window.Show%2A>.  
  
<a name="Ownership"></a>   
#### <a name="window-ownership"></a>Propriété de la fenêtre  
 Une fenêtre ouverte à l’aide de la méthode <xref:System.Windows.Window.Show%2A> n’a pas de relation implicite avec la fenêtre qui l’a créée. les utilisateurs peuvent interagir avec l’une ou l’autre des fenêtres indépendamment les unes des autres, ce qui signifie que les deux fenêtres peuvent effectuer les opérations suivantes :  
  
- Couvrir l’autre (sauf si la propriété <xref:System.Windows.Window.Topmost%2A> de l’une des fenêtres est définie sur `true`).  
  
- être réduite, agrandie et restaurée sans affecter l’autre fenêtre.  
  
 Certaines fenêtres nécessitent une relation avec la fenêtre qui les ouvre. Par exemple, une application d’environnement de développement intégré (IDE) peut ouvrir des fenêtres de propriétés et des fenêtres outil dont le comportement standard consiste à couvrir la fenêtre qui les crée. De plus, ces fenêtres doivent toujours se fermer, se réduire, s’agrandir et se restaurer conjointement avec la fenêtre qui les a créées. Une telle relation peut être établie en faisant en sorte qu’une fenêtre en *possède* une autre et est obtenue en définissant la propriété <xref:System.Windows.Window.Owner%2A> de la *fenêtre possédée* avec une référence à la *fenêtre propriétaire*. L'exemple suivant le démontre.  
  
 [!code-csharp[WindowOwnerOwnedWindowsSnippets#SetWindowOwnerCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowOwnerOwnedWindowsSnippets/CSharp/MainWindow.xaml.cs#setwindowownercode)]
 [!code-vb[WindowOwnerOwnedWindowsSnippets#SetWindowOwnerCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WindowOwnerOwnedWindowsSnippets/visualbasic/mainwindow.xaml.vb#setwindowownercode)]  
  
 Une fois la propriété établie :  
  
- La fenêtre possédée peut faire référence à sa fenêtre propriétaire en inspectant la valeur de sa propriété <xref:System.Windows.Window.Owner%2A>.  
  
- La fenêtre propriétaire peut découvrir toutes les fenêtres qu’elle possède en inspectant la valeur de sa propriété <xref:System.Windows.Window.OwnedWindows%2A>.  
  
<a name="Preventing"></a>   
#### <a name="preventing-window-activation"></a>Blocage de l’activation de la fenêtre  
 Il existe des scénarios dans lesquels les fenêtres ne doivent pas être activées quand elles sont affichées, telles que les fenêtres de conversation d’une application de style Messenger Internet ou les fenêtres de notification d’une application de messagerie.  
  
 Si votre application a une fenêtre qui ne doit pas être activée quand elle est affichée, vous pouvez définir sa propriété <xref:System.Windows.Window.ShowActivated%2A> sur `false` avant d’appeler la méthode <xref:System.Windows.Window.Show%2A> pour la première fois. En conséquence :  
  
- La fenêtre n’est pas activée.  
  
- L’événement <xref:System.Windows.Window.Activated> de la fenêtre n’est pas déclenché.  
  
- La fenêtre déjà activée reste activée.  
  
 Toutefois, la fenêtre est activée dès que l’utilisateur clique sur la zone cliente ou non cliente. Dans ce cas :  
  
- La fenêtre est activée.  
  
- L’événement <xref:System.Windows.Window.Activated> de la fenêtre est déclenché.  
  
- La fenêtre qui était activée est désactivée.  
  
- Les événements <xref:System.Windows.Window.Deactivated> et <xref:System.Windows.Window.Activated> de la fenêtre sont ensuite déclenchés comme prévu en réponse aux actions de l’utilisateur.  
  
<a name="Window_Activation"></a>   
### <a name="window-activation"></a>Activation de la fenêtre  
 Quand une fenêtre est ouverte pour la première fois, elle devient la fenêtre active (à moins qu’elle ne soit affichée avec <xref:System.Windows.Window.ShowActivated%2A> défini sur `false`). La *fenêtre active* est la fenêtre qui capture actuellement les entrées d’utilisateur, telles que les frappes de touche et les clics de souris. Quand une fenêtre devient active, elle déclenche l’événement <xref:System.Windows.Window.Activated>.  
  
> [!NOTE]
> Quand une fenêtre est ouverte pour la première fois, les événements <xref:System.Windows.FrameworkElement.Loaded> et <xref:System.Windows.Window.ContentRendered> sont déclenchés uniquement après le déclenchement de l’événement <xref:System.Windows.Window.Activated>. En tenant compte de cela, une fenêtre peut être considérée comme ouverte lorsque <xref:System.Windows.Window.ContentRendered> est déclenchée.  
  
 Une fois qu’une fenêtre est active, un utilisateur peut activer une autre fenêtre de la même application ou activer une autre application. Lorsque cela se produit, la fenêtre actuellement active est désactivée et déclenche l’événement <xref:System.Windows.Window.Deactivated>. De même, lorsque l’utilisateur sélectionne une fenêtre actuellement désactivée, la fenêtre redevient active et <xref:System.Windows.Window.Activated> est déclenchée.  
  
 Une des raisons courantes pour gérer les <xref:System.Windows.Window.Activated> et les <xref:System.Windows.Window.Deactivated> consiste à activer et désactiver les fonctionnalités qui ne peuvent s’exécuter que lorsqu’une fenêtre est active. Par exemple, certaines fenêtres affichent du contenu interactif qui nécessite en permanence l’attention de l’utilisateur ou une entrée de sa part, notamment les jeux et les lecteurs vidéo. L’exemple suivant est un lecteur vidéo simplifié qui montre comment gérer <xref:System.Windows.Window.Activated> et <xref:System.Windows.Window.Deactivated> pour implémenter ce comportement.  
  
 [!code-xaml[WindowsOverviewSnippets#ActivationDeactivationMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/CustomMediaPlayerWindow.xaml#activationdeactivationmarkup)]  
  
 [!code-csharp[WindowsOverviewSnippets#ActivationDeactivationCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/CustomMediaPlayerWindow.xaml.cs#activationdeactivationcodebehind)]
 [!code-vb[WindowsOverviewSnippets#ActivationDeactivationCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WindowsOverviewSnippets/VisualBasic/CustomMediaPlayerWindow.xaml.vb#activationdeactivationcodebehind)]  
  
 D’autres types d’application peuvent toujours exécuter du code en arrière-plan quand une fenêtre est désactivée. Par exemple, un client d’e-mail peut continuer à interroger le serveur d’e-mail pendant que l’utilisateur utilise d’autres applications. Les applications de ce type ont souvent un comportement différent ou supplémentaire pendant que la fenêtre principale est désactivée. En ce qui concerne le programme d’e-mail, cela peut signifier l’ajout du nouvel élément d’e-mail à la boîte de réception, ainsi que l’ajout d’une icône de notification à la zone de notification. Une icône de notification ne doit être affichée que lorsque la fenêtre de messagerie n’est pas active, ce qui peut être déterminé en examinant la propriété <xref:System.Windows.Window.IsActive%2A>.  
  
 Si une tâche en arrière-plan se termine, une fenêtre peut souhaiter notifier l’utilisateur de façon plus urgente en appelant <xref:System.Windows.Window.Activate%2A> méthode. Si l’utilisateur interagit avec une autre application activée lorsque <xref:System.Windows.Window.Activate%2A> est appelé, le bouton de la barre des tâches de la fenêtre clignote. Si un utilisateur interagit avec l’application actuelle, l’appel de <xref:System.Windows.Window.Activate%2A> place la fenêtre au premier plan.  
  
> [!NOTE]
> Vous pouvez gérer l’activation de l’étendue de l’application à l’aide des événements <xref:System.Windows.Application.Activated?displayProperty=nameWithType> et <xref:System.Windows.Application.Deactivated?displayProperty=nameWithType>.  
  
<a name="Closing_a_Window"></a>   
### <a name="closing-a-window"></a>Fermeture d’une fenêtre  
 Quand un utilisateur ferme une fenêtre, celle-ci cesse d’exister. Vous pouvez fermer une fenêtre à l’aide d’éléments de la zone non cliente, notamment :  
  
- Élément de **fermeture** du menu **système** .  
  
- Un appui sur Alt+F4  
  
- Appuyant sur le bouton **Fermer** .  
  
 Vous pouvez fournir des mécanismes supplémentaires à la zone cliente pour fermer une fenêtre, notamment :  
  
- Un élément de **sortie** dans le menu **fichier** , généralement pour les fenêtres d’application principales.  
  
- Élément **Fermer** dans le menu **fichier** , généralement dans une fenêtre d’application secondaire.  
  
- Bouton **Annuler** , généralement dans une boîte de dialogue modale.  
  
- Bouton **Fermer** , généralement dans une boîte de dialogue non modale.  
  
 Pour fermer une fenêtre en réponse à l’un de ces mécanismes personnalisés, vous devez appeler la méthode <xref:System.Windows.Window.Close%2A>. L’exemple suivant implémente la possibilité de fermer une fenêtre en choisissant **quitter** dans le menu **fichier** .  
  
 [!code-xaml[WindowsOverviewSnippets#WindowWithFileExitMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/WindowWithFileExit.xaml#windowwithfileexitmarkup)]  
  
 [!code-csharp[WindowsOverviewSnippets#WindowWithFileExitCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/WindowWithFileExit.xaml.cs#windowwithfileexitcodebehind)]
 [!code-vb[WindowsOverviewSnippets#WindowWithFileExitCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WindowsOverviewSnippets/VisualBasic/WindowWithFileExit.xaml.vb#windowwithfileexitcodebehind)]  
  
 Quand une fenêtre se ferme, elle déclenche deux événements : <xref:System.Windows.Window.Closing> et <xref:System.Windows.Window.Closed>.  
  
 <xref:System.Windows.Window.Closing> est déclenché avant la fermeture de la fenêtre et fournit un mécanisme qui permet d’empêcher la fermeture de la fenêtre. Bien souvent, la fermeture d’une fenêtre est nécessaire si elle contient des données qui ont été modifiées. Dans ce cas, l’événement <xref:System.Windows.Window.Closing> peut être géré pour déterminer si les données sont modifiées et, le cas échéant, pour demander à l’utilisateur s’il doit continuer à fermer la fenêtre sans enregistrer les données ou pour annuler la fermeture de la fenêtre. L’exemple suivant illustre les principaux aspects de la gestion des <xref:System.Windows.Window.Closing>.  
  
 [!code-csharp[WindowClosingSnippets](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowClosingSnippets/CSharp/DataWindow.xaml.cs)]
 [!code-vb[WindowClosingSnippets](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WindowClosingSnippets/visualbasic/datawindow.xaml.vb)]  

 Un <xref:System.ComponentModel.CancelEventArgs>, qui implémente la propriété de <xref:System.ComponentModel.CancelEventArgs.Cancel%2A> `Boolean`que vous affectez à `true`, est passé au gestionnaire d’événements <xref:System.Windows.Window.Closing> pour empêcher la fermeture d’une fenêtre.  
  
 Si <xref:System.Windows.Window.Closing> n’est pas gérée ou si elle est gérée mais pas annulée, la fenêtre se ferme. Juste avant la fermeture d’une fenêtre, <xref:System.Windows.Window.Closed> est déclenché. À ce stade, il est impossible d’empêcher une fenêtre de se fermer.  
  
> [!NOTE]
> Une application peut être configurée pour s’arrêter automatiquement à la fermeture de la fenêtre principale de l’application (voir <xref:System.Windows.Application.MainWindow%2A>) ou la dernière fenêtre se ferme. Pour plus d'informations, consultez <xref:System.Windows.Application.ShutdownMode%2A>.  
  
 Bien qu’une fenêtre puisse être fermée explicitement par le biais de mécanismes fournis dans les zones non client et client, une fenêtre peut également être fermée implicitement en raison d’un comportement dans d’autres parties de l’application ou de Windows, y compris les éléments suivants :  
  
- Un utilisateur se déconnecte ou arrête Windows.  
  
- Le propriétaire d’une fenêtre se ferme (voir <xref:System.Windows.Window.Owner%2A>).  
  
- La fenêtre d’application principale est fermée et <xref:System.Windows.Application.ShutdownMode%2A> est <xref:System.Windows.ShutdownMode.OnMainWindowClose>.  
  
- La méthode <xref:System.Windows.Application.Shutdown%2A> est appelée.  
  
> [!NOTE]
> Une fenêtre ne peut pas être rouverte après sa fermeture.  
  
<a name="Window_Lifetime_Events"></a>   
### <a name="window-lifetime-events"></a>Événements de la durée de vie d’une fenêtre  
 L’illustration suivante montre la séquence des événements principaux dans la durée de vie d’une fenêtre :  
  
 ![Diagramme qui affiche les événements dans la durée de vie d’une fenêtre.](./media/wpf-windows-overview/window-lifetime-events.png)  
  
 L’illustration suivante montre la séquence des événements principaux dans la durée de vie d’une fenêtre affichée sans activation (<xref:System.Windows.Window.ShowActivated%2A> a la valeur `false` avant l’affichage de la fenêtre) :  
  
 ![Diagramme qui affiche les événements dans la durée de vie d’une fenêtre sans activation.](./media/wpf-windows-overview/window-lifetime-no-activation.png)  
  
<a name="WindowLocation"></a>   
## <a name="window-location"></a>Emplacement d’une fenêtre  
 Quand une fenêtre est ouverte, elle dispose d’un emplacement dans les dimensions x et y du Bureau. Cet emplacement peut être déterminé en inspectant les propriétés <xref:System.Windows.Window.Left%2A> et <xref:System.Windows.Window.Top%2A>, respectivement. Vous pouvez définir ces propriétés pour changer l’emplacement de la fenêtre.  
  
 Vous pouvez également spécifier l’emplacement initial d’un <xref:System.Windows.Window> lorsqu’il apparaît pour la première fois en affectant à la propriété <xref:System.Windows.Window.WindowStartupLocation%2A> l’une des valeurs d’énumération <xref:System.Windows.WindowStartupLocation> suivantes :  
  
- <xref:System.Windows.WindowStartupLocation.CenterOwner> (valeur par défaut)  
  
- <xref:System.Windows.WindowStartupLocation.CenterScreen>  
  
- <xref:System.Windows.WindowStartupLocation.Manual>  
  
 Si l’emplacement de démarrage est spécifié en tant que <xref:System.Windows.WindowStartupLocation.Manual>et que les propriétés <xref:System.Windows.Window.Left%2A> et <xref:System.Windows.Window.Top%2A> n’ont pas été définies, <xref:System.Windows.Window> demande à Windows d’afficher un emplacement dans.  
  
<a name="Topmost_Windows_and_Z_Order"></a>   
### <a name="topmost-windows-and-z-order"></a>Fenêtres au premier plan et ordre de plan  
 Outre un emplacement dans les dimensions x et y, une fenêtre a également un emplacement dans la dimension z, qui détermine sa position verticale par rapport à d’autres fenêtres. Il s’agit de l’ordre de plan de la fenêtre. Il en existe deux types : l’ordre de plan normal et l’ordre de plan le plus haut. L’emplacement d’une fenêtre dans l' *ordre de plan normal* est déterminé par s’il est actuellement actif ou non. Par défaut, une fenêtre est située dans l’ordre de plan normal. L’emplacement d’une fenêtre dans l' *ordre de plan le plus haut* est également déterminé par le fait qu’elle est actuellement active ou non. De plus, les fenêtres dans l’ordre de plan le plus haut sont toujours situées au-dessus des fenêtres dans l’ordre de plan normal. Une fenêtre se trouve dans l’ordre de plan le plus haut en affectant à sa propriété <xref:System.Windows.Window.Topmost%2A> la valeur `true`.  
  
 [!code-xaml[WindowsOverviewSnippets#TopmostWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/TopmostWindow.xaml#topmostwindowmarkup1)]  
  
 Dans chaque ordre de plan, la fenêtre active apparaît au-dessus de toutes les autres fenêtres du même ordre de plan.  
  
<a name="WindowSize"></a>   
## <a name="window-size"></a>Taille de la fenêtre  
 Outre l’existence d’un emplacement de bureau, une fenêtre a une taille déterminée par plusieurs propriétés, y compris les propriétés Width et Height, ainsi que les <xref:System.Windows.Window.SizeToContent%2A>.  
  
 <xref:System.Windows.FrameworkElement.MinWidth%2A>, <xref:System.Windows.FrameworkElement.Width%2A>et <xref:System.Windows.FrameworkElement.MaxWidth%2A> sont utilisés pour gérer la plage de largeurs qu’une fenêtre peut avoir pendant sa durée de vie, et sont configurés comme indiqué dans l’exemple suivant.  
  
 [!code-xaml[WindowsOverviewSnippets#WidthWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/WidthWindow.xaml#widthwindowmarkup1)]  
  
 La hauteur de la fenêtre est gérée par <xref:System.Windows.FrameworkElement.MinHeight%2A>, <xref:System.Windows.FrameworkElement.Height%2A>et <xref:System.Windows.FrameworkElement.MaxHeight%2A>, et est configurée comme indiqué dans l’exemple suivant.  
  
 [!code-xaml[WindowsOverviewSnippets#HeightWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/HeightWindow.xaml#heightwindowmarkup1)]  
  
 Comme les diverses valeurs de largeur et de hauteur spécifient chacune une plage, il est possible pour la largeur et la hauteur d’une fenêtre redimensionnable de se situer n’importe où dans la plage spécifiée pour la dimension respective. Pour détecter la largeur et la hauteur actuelles, inspectez <xref:System.Windows.FrameworkElement.ActualWidth%2A> et <xref:System.Windows.FrameworkElement.ActualHeight%2A>, respectivement.  
  
 Si vous souhaitez que la largeur et la hauteur de votre fenêtre aient une taille adaptée à la taille du contenu de la fenêtre, vous pouvez utiliser la propriété <xref:System.Windows.Window.SizeToContent%2A>, qui a les valeurs suivantes :  
  
- <xref:System.Windows.SizeToContent.Manual>. Aucun effet (par défaut).  
  
- <xref:System.Windows.SizeToContent.Width>. Ajuster à la largeur du contenu, ce qui a le même effet que la définition des <xref:System.Windows.FrameworkElement.MinWidth%2A> et des <xref:System.Windows.FrameworkElement.MaxWidth%2A> à la largeur du contenu.  
  
- <xref:System.Windows.SizeToContent.Height>. Ajuster à la hauteur du contenu, qui a le même effet que la définition des <xref:System.Windows.FrameworkElement.MinHeight%2A> et des <xref:System.Windows.FrameworkElement.MaxHeight%2A> à la hauteur du contenu.  
  
- <xref:System.Windows.SizeToContent.WidthAndHeight>. Ajuster à la largeur et à la hauteur du contenu, ce qui équivaut à définir les <xref:System.Windows.FrameworkElement.MinHeight%2A> et à <xref:System.Windows.FrameworkElement.MaxHeight%2A> à la hauteur du contenu, et à définir à la fois <xref:System.Windows.FrameworkElement.MinWidth%2A> et <xref:System.Windows.FrameworkElement.MaxWidth%2A> sur la largeur du contenu.  
  
 L’exemple suivant montre une fenêtre qui s’ajuste automatiquement en fonction de son contenu, verticalement et horizontalement, au moment où elle s’affiche pour la première fois.  
  
 [!code-xaml[WindowsOverviewSnippets#SizeToContentWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/SizeToContentWindow.xaml#sizetocontentwindowmarkup1)]  
  
 L’exemple suivant montre comment définir la propriété <xref:System.Windows.Window.SizeToContent%2A> dans le code pour spécifier le mode de redimensionnement d’une fenêtre en fonction de son contenu.
  
 [!code-csharp[HOWTOWindowManagementSnippets#SetWindowSizeToContentPropertyCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/CSharp/MainWindow.xaml.cs#setwindowsizetocontentpropertycode)]
 [!code-vb[HOWTOWindowManagementSnippets#SetWindowSizeToContentPropertyCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/visualbasic/mainwindow.xaml.vb#setwindowsizetocontentpropertycode)]  
  
<a name="OrderOfPrecedence"></a>   
## <a name="order-of-precedence-for-sizing-properties"></a>Ordre de priorité des propriétés de dimensionnement  
 Pour l’essentiel, les diverses propriétés de dimensionnement d’une fenêtre se combinent pour définir la plage de largeur et de hauteur d’une fenêtre redimensionnable. Pour garantir la conservation d’une plage valide, <xref:System.Windows.Window> évalue les valeurs des propriétés de taille à l’aide des ordres de priorité suivants.  
  
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
  
 L’ordre de priorité peut également déterminer la taille d’une fenêtre lorsqu’elle est agrandie, qui est gérée avec la propriété <xref:System.Windows.Window.WindowState%2A>.  
  
<a name="WindowState"></a>   
## <a name="window-state"></a>État de la fenêtre  
 Au cours de sa durée de vie, une fenêtre redimensionnable peut avoir trois états : normal, réduit et agrandi. Une fenêtre avec un état *normal* est l’État par défaut d’une fenêtre. Quand une fenêtre est dans cet état, l’utilisateur peut la déplacer et la redimensionner à l’aide d’une poignée de redimensionnement ou de la bordure, si elle est redimensionnable.  
  
 Une fenêtre avec un état *réduit* est réduite à son bouton de barre des tâches si <xref:System.Windows.Window.ShowInTaskbar%2A> a la valeur `true`; dans le cas contraire, elle est réduite à la plus petite taille possible et se déplace vers l’angle inférieur gauche du bureau. Aucun type de fenêtre réduite ne peut être redimensionné à l’aide d’une bordure ou d’une poignée de redimensionnement. Toutefois, une fenêtre réduite qui n’est pas affichée dans la barre des tâches peut être déplacée partout sur le Bureau.  
  
 Une fenêtre avec un état *agrandi* s’agrandit jusqu’à la taille maximale possible, ce qui n’est pas aussi important que son <xref:System.Windows.FrameworkElement.MaxWidth%2A>, <xref:System.Windows.FrameworkElement.MaxHeight%2A>et <xref:System.Windows.Window.SizeToContent%2A> propriétés. Comme pour une fenêtre réduite, vous ne pouvez pas redimensionner une fenêtre agrandie à l’aide d’une poignée de redimensionnement ou en faisant glisser sa bordure.  
  
> [!NOTE]
> Les valeurs des propriétés <xref:System.Windows.Window.Top%2A>, <xref:System.Windows.Window.Left%2A>, <xref:System.Windows.FrameworkElement.Width%2A>et <xref:System.Windows.FrameworkElement.Height%2A> d’une fenêtre représentent toujours les valeurs de l’état normal, même lorsque la fenêtre est actuellement agrandie ou réduite.  
  
 L’état d’une fenêtre peut être configuré en définissant sa propriété <xref:System.Windows.Window.WindowState%2A>, qui peut avoir l’une des valeurs d’énumération <xref:System.Windows.WindowState> suivantes :  
  
- <xref:System.Windows.WindowState.Normal> (valeur par défaut)  
  
- <xref:System.Windows.WindowState.Maximized>  
  
- <xref:System.Windows.WindowState.Minimized>  
  
 L’exemple suivant montre comment créer une fenêtre agrandie quand elle s’ouvre.  
  
 [!code-xaml[WindowsOverviewSnippets#WindowStateWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/WindowStateWindow.xaml#windowstatewindowmarkup1)]  
  
 En général, vous devez définir <xref:System.Windows.Window.WindowState%2A> pour configurer l’état initial d’une fenêtre. Une fois qu’une fenêtre redimensionnable est affichée, les utilisateurs peuvent cliquer dans la barre de titre de la fenêtre sur les boutons de réduction, d’agrandissement et de restauration pour changer son état.  
  
<a name="WindowAppearance"></a>   
## <a name="window-appearance"></a>Apparence de la fenêtre  
 Vous pouvez changer l’apparence de la zone cliente d’une fenêtre en lui ajoutant un contenu spécifique, par exemple des boutons, des étiquettes et des zones de texte. Pour configurer la zone non cliente, <xref:System.Windows.Window> fournit plusieurs propriétés, qui incluent <xref:System.Windows.Window.Icon%2A> pour définir l’icône d’une fenêtre et <xref:System.Windows.Window.Title%2A> pour définir son titre.  
  
 Vous pouvez également changer l’apparence et le comportement d’une bordure de zone non cliente en configurant le mode de redimensionnement d’une fenêtre, le style de fenêtre, ainsi que son affichage ou non sous forme de bouton dans la barre des tâches du Bureau.  

<a name="Resize_Mode"></a>   
### <a name="resize-mode"></a>Mode de redimensionnement  
 En fonction de la propriété <xref:System.Windows.Window.WindowStyle%2A>, vous pouvez contrôler la façon dont les utilisateurs peuvent redimensionner la fenêtre. Le choix du style de fenêtre affecte si un utilisateur peut redimensionner la fenêtre en faisant glisser sa bordure avec la souris, que les boutons **réduire**, **agrandir**et **Redimensionner** apparaissent sur la zone non cliente et, s’ils apparaissent, s’ils sont activés.  
  
 Vous pouvez configurer le mode de redimensionnement d’une fenêtre en définissant sa propriété <xref:System.Windows.Window.ResizeMode%2A>, qui peut être l’une des <xref:System.Windows.ResizeMode> valeurs d’énumération suivantes :  
  
- <xref:System.Windows.ResizeMode.NoResize>  
  
- <xref:System.Windows.ResizeMode.CanMinimize>  
  
- <xref:System.Windows.ResizeMode.CanResize> (valeur par défaut)  
  
- <xref:System.Windows.ResizeMode.CanResizeWithGrip>  
  
 Comme avec <xref:System.Windows.Window.WindowStyle%2A>, le mode de redimensionnement d’une fenêtre est peu susceptible de changer pendant sa durée de vie, ce qui signifie que vous le définirez très probablement à partir du balisage [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].  
  
 [!code-xaml[WindowsOverviewSnippets#ResizeModeWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/ResizeModeWindow.xaml#resizemodewindowmarkup1)]  
  
 Notez que vous pouvez détecter si une fenêtre est agrandie, réduite ou restaurée en inspectant la propriété <xref:System.Windows.Window.WindowState%2A>.  
  
<a name="Window_Style"></a>   
### <a name="window-style"></a>Style de la fenêtre  
 La bordure exposée à partir de la zone non cliente d’une fenêtre convient à la plupart des applications. Toutefois, selon les circonstances, il arrive que d’autres types de bordure (voire aucune bordure) soient nécessaires, en fonction du type de fenêtre.  
  
 Pour contrôler le type de bordure qu’une fenêtre obtient, vous devez définir sa propriété <xref:System.Windows.Window.WindowStyle%2A> avec l’une des valeurs suivantes de l’énumération <xref:System.Windows.WindowStyle> :  
  
- <xref:System.Windows.WindowStyle.None>  
  
- <xref:System.Windows.WindowStyle.SingleBorderWindow> (valeur par défaut)  
  
- <xref:System.Windows.WindowStyle.ThreeDBorderWindow>  
  
- <xref:System.Windows.WindowStyle.ToolWindow>  
  
 L’effet de ces styles de fenêtre est illustré dans la figure suivante :  
  
 ![Illustration de styles de bordure de fenêtre.](./media/wpf-windows-overview/window-border-styles.png)  
  
 Vous pouvez définir <xref:System.Windows.Window.WindowStyle%2A> à l’aide du balisage ou du code [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ; comme il est peu probable qu’il soit modifié pendant la durée de vie d’une fenêtre, vous le configurerez très probablement à l’aide du balisage [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].  
  
 [!code-xaml[WindowsOverviewSnippets#WindowStyleWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/WindowStyleWindow.xaml#windowstylewindowmarkup1)]  
  
#### <a name="non-rectangular-window-style"></a>Style de fenêtre non rectangulaire  
 Il existe également des situations dans lesquelles les styles de bordure qui <xref:System.Windows.Window.WindowStyle%2A> vous permettent d’avoir n’est pas suffisant. Par exemple, vous souhaiterez peut-être créer une application avec une bordure non rectangulaire, comme Microsoft Windows Media Player.  
  
 Par exemple, considérez la fenêtre de bulle de parole présentée dans la figure suivante :  
  
 ![Une fenêtre de bulle de parole indiquant glisser-moi.](./media/wpf-windows-overview/non-rectangular-window-figure.png)  
  
 Ce type de fenêtre peut être créé en affectant à la propriété <xref:System.Windows.Window.WindowStyle%2A> la valeur <xref:System.Windows.WindowStyle.None>et en utilisant une prise en charge spéciale de la transparence par <xref:System.Windows.Window>.  
  
 [!code-xaml[WindowsOverviewSnippets#TransparentWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/TransparentWindow.xaml#transparentwindowmarkup1)]  
  
 Cette combinaison de valeurs indique à la fenêtre de s’afficher de manière totalement transparente. Dans cet état, les ornements de la zone non cliente (menu Fermer, boutons Réduire, Agrandir, Restaurer, etc.) de la fenêtre ne peuvent pas être utilisés. Vous devez donc fournir vos propres ornements.  
  
<a name="Task_Bar_Presence"></a>   
### <a name="task-bar-presence"></a>Présence de la barre des tâches  

L’apparence par défaut d’une fenêtre comprend un bouton de barre des tâches, comme celui illustré dans la figure suivante :

 ![Capture d’écran montrant une fenêtre avec un bouton de barre des tâches.](./media/wpf-windows-overview/window-taskbar-button.png)  
  
 Certains types de fenêtres n’ont pas de bouton de barre des tâches, comme des boîtes de message et des boîtes de dialogue (consultez [vue d’ensemble des boîtes de dialogue](dialog-boxes-overview.md)). Vous pouvez contrôler si le bouton de barre des tâches d’une fenêtre s’affiche en définissant la propriété <xref:System.Windows.Window.ShowInTaskbar%2A> (`true` par défaut).  
  
 [!code-xaml[WindowsOverviewSnippets#ShowInTaskbarWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/ShowInTaskbarWindow.xaml#showintaskbarwindowmarkup1)]  
  
<a name="SecurityConsiderations"></a>   
## <a name="security-considerations"></a>Considérations relatives à la sécurité  
 <xref:System.Windows.Window> nécessite l’instanciation d' `UnmanagedCode` autorisation de sécurité. Pour les applications installées sur la machine locale et lancées à partir de celle-ci, cette autorisation fait partie du jeu d’autorisations accordé à l’application.  
  
 Toutefois, cela se situe en dehors de l’ensemble des autorisations accordées aux applications qui sont lancées à partir de la zone Internet ou Intranet local à l’aide de ClickOnce. Par conséquent, les utilisateurs recevront un avertissement de sécurité ClickOnce et devront élever le jeu d’autorisations pour l’application à confiance totale.  
  
 En outre, les XBAP ne peuvent pas afficher les fenêtres ou les boîtes de dialogue par défaut. Pour une discussion sur les considérations relatives à la sécurité des applications autonomes, consultez [stratégie de sécurité de WPF-sécurité de la plateforme](../wpf-security-strategy-platform-security.md).  
  
<a name="Other_Types_of_Windows"></a>   
## <a name="other-types-of-windows"></a>Autres types de fenêtre  
 <xref:System.Windows.Navigation.NavigationWindow> est une fenêtre conçue pour héberger du contenu navigable. Pour plus d’informations, consultez [vue d’ensemble](navigation-overview.md)de la navigation).  
  
 Les boîtes de dialogue sont des fenêtres souvent utilisées pour rassembler des informations fournies par un utilisateur afin d’exécuter une fonction. Par exemple, lorsqu’un utilisateur souhaite ouvrir un fichier, la boîte de dialogue **ouvrir un fichier** s’affiche généralement par une application pour obtenir le nom de fichier de l’utilisateur. Pour plus d’informations, consultez [Vue d’ensemble des boîtes de dialogue](dialog-boxes-overview.md).  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Window>
- <xref:System.Windows.MessageBox>
- <xref:System.Windows.Navigation.NavigationWindow>
- <xref:System.Windows.Application>
- [Vue d’ensemble des boîtes de dialogue](dialog-boxes-overview.md)
- [Génération d’une application WPF](building-a-wpf-application-wpf.md)
