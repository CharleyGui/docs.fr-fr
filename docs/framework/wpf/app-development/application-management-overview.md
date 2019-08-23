---
title: Vue d'ensemble de la gestion d'applications
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- application management [WPF]
ms.assetid: 32b1c054-5aca-423b-b4b5-ed8dc4dc637d
ms.openlocfilehash: 448c212e4afe547dc6342b000fe06d5340db112c
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69958738"
---
# <a name="application-management-overview"></a>Vue d'ensemble de la gestion d'applications
Toutes les applications tendent à partager un jeu de fonctionnalités commun qui s’applique à l’implémentation et à la gestion. Cette rubrique fournit une vue d’ensemble des fonctionnalités de <xref:System.Windows.Application> la classe pour la création et la gestion d’applications.  

## <a name="the-application-class"></a>Classe Application  
 Dans WPF, les fonctionnalités communes de portée application sont encapsulées dans la <xref:System.Windows.Application> classe. La <xref:System.Windows.Application> classe comprend les fonctionnalités suivantes:  
  
- Suivi et interaction avec la durée de vie d’une application.  
  
- Récupération et traitement des paramètres de ligne de commande.  
  
- Détection et traitement des exceptions non gérées.  
  
- Partage des propriétés de portée application et des ressources.  
  
- Gestion des fenêtres dans des applications autonomes.  
  
- Suivi et gestion de la navigation.  
  
<a name="The_Application_Class"></a>   
## <a name="how-to-perform-common-tasks-using-the-application-class"></a>Comment effectuer des tâches courantes à l’aide de la classe Application  
 Si vous n’êtes pas intéressé par tous les détails de la <xref:System.Windows.Application> classe, le tableau suivant répertorie quelques-unes des tâches <xref:System.Windows.Application> courantes pour et comment les accomplir. En affichant l’API et les rubriques connexes, vous pouvez obtenir davantage d’informations et des exemples de code.  
  
|Tâche|Approche|  
|----------|--------------|  
|Obtenir un objet qui représente l’application actuelle|Utilisez la propriété <xref:System.Windows.Application.Current%2A?displayProperty=nameWithType>.|  
|Ajouter un écran de démarrage à une application|Consultez [Ajouter un écran de démarrage à une application WPF](how-to-add-a-splash-screen-to-a-wpf-application.md).|  
|Démarrer une application|Utilisez la méthode <xref:System.Windows.Application.Run%2A?displayProperty=nameWithType>.|  
|Arrêter une application|Utilisez la <xref:System.Windows.Application.Shutdown%2A> méthode de l' <xref:System.Windows.Application.Current%2A?displayProperty=nameWithType> objet.|  
|Obtenir des arguments de la ligne de commande|Gérez l' <xref:System.Windows.Application.Startup?displayProperty=nameWithType> événement et utilisez la <xref:System.Windows.StartupEventArgs.Args%2A?displayProperty=nameWithType> propriété. Pour obtenir un exemple, consultez <xref:System.Windows.Application.Startup?displayProperty=nameWithType> l’événement.|  
|Obtenir et définir le code de sortie d’application|Définissez la <xref:System.Windows.ExitEventArgs.ApplicationExitCode%2A?displayProperty=nameWithType> propriété dans le <xref:System.Windows.Application.Exit?displayProperty=nameWithType> gestionnaire d’événements ou appelez <xref:System.Windows.Application.Shutdown%2A> la méthode et transmettez un entier.|  
|Détecter et traiter des exceptions non gérées|Gérez l' <xref:System.Windows.Application.DispatcherUnhandledException> événement.|  
|Obtenir et définir des ressources de portée application|Utilisez la propriété <xref:System.Windows.Application.Resources%2A?displayProperty=nameWithType>.|  
|Utiliser un dictionnaire de ressources de portée application|Consultez [utiliser un dictionnaire de ressources de portée application](how-to-use-an-application-scope-resource-dictionary.md).|  
|Obtenir et définir les propriétés de portée application|Utilisez la propriété <xref:System.Windows.Application.Properties%2A?displayProperty=nameWithType>.|  
|Obtenir et enregistrer l’état d’une application|Consultez [conserver et restaurer les propriétés de portée application d’une session d’application à l’autre](persist-and-restore-application-scope-properties.md).|  
|Gérer les fichiers de données de non-code, dont les fichiers de ressources, les fichiers de contenu et les fichiers du site d’origine.|Consultez [fichiers de ressources, de contenu et de données d’une application WPF](wpf-application-resource-content-and-data-files.md).|  
|Gérer des fenêtres dans des applications autonomes|Consultez [Vue d’ensemble des fenêtres WPF](wpf-windows-overview.md).|  
|Suivre et gérer la navigation|Consultez [vue d’ensemble](navigation-overview.md)de la navigation.|  
  
<a name="The_Application_Definition"></a>   
## <a name="the-application-definition"></a>Définition d’application  
 Pour utiliser les fonctionnalités de la <xref:System.Windows.Application> classe, vous devez implémenter une définition d’application. Une définition d’application WPF est une classe qui dérive <xref:System.Windows.Application> de et qui est configurée avec un paramètre MSBuild spécial.  

### <a name="implementing-an-application-definition"></a>Implémentation d’une définition d’application  
 Une définition d’application WPF standard est implémentée à l’aide du balisage et du code-behind. Vous pouvez ainsi utiliser le balisage pour définir de façon déclarative les propriétés d’une application et les ressources ainsi que pour inscrire des événements, tout en gérant les événements et en implémentant le comportement spécifique à l’application dans un fichier code-behind.  
  
 L’exemple suivant montre comment implémenter une définition d’application à l’aide de balisage et de code-behind :  
  
 [!code-xaml[ApplicationSnippets#ApplicationXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationSnippets/CSharp/App.xaml#applicationxaml)]  
  
 [!code-csharp[ApplicationSnippets#ApplicationCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationSnippets/CSharp/App.xaml.cs#applicationcodebehind)]
 [!code-vb[ApplicationSnippets#ApplicationCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationSnippets/visualbasic/application.xaml.vb#applicationcodebehind)]  
  
 Pour permettre l’interopérabilité d’un fichier de balisage et d’un fichier code-behind, les conditions suivantes doivent être satisfaites :  
  
- Dans le balisage `Application` , l’élément doit `x:Class` inclure l’attribut. Lorsque l’application est générée, l’existence de `x:Class` dans le fichier de balisage amène MSBuild à `partial` créer une classe qui dérive de <xref:System.Windows.Application> et qui porte le nom spécifié par `x:Class` l’attribut. Cela nécessite l’ajout d’une déclaration d’espace de noms XML pour le`xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"`schéma XAML ().
  
- Dans le code-behind, la classe doit être `partial` une classe portant le même nom que celui spécifié par `x:Class` l’attribut dans le balisage et <xref:System.Windows.Application>doit dériver de. Cela permet au fichier code-behind d’être associé à la `partial` classe générée pour le fichier de balisage quand l’application est générée (consultez [génération d’une application WPF](building-a-wpf-application-wpf.md)).  
  
> [!NOTE]
> Quand vous créez un projet d’application WPF ou un projet d’application de navigateur WPF à l’aide de Visual Studio, une définition d’application est incluse par défaut et est définie à l’aide du balisage et du code-behind.  
  
 Ce code est le minimum requis pour implémenter une définition d’application. Toutefois, une configuration MSBuild supplémentaire doit être apportée à la définition de l’application avant de générer et d’exécuter l’application.  
  
### <a name="configuring-the-application-definition-for-msbuild"></a>Configuration de la définition d’application pour MSBuild  
 Les applications autonomes et les applications de navigateur XAML (XBAP) requièrent l’implémentation d’un certain niveau d’infrastructure pour pouvoir s’exécuter. La partie la plus importante de cette infrastructure est le point d’entrée. Quand une application est lancée par un utilisateur, le système d’exploitation appelle le point d’entrée, qui est une fonction connue pour démarrer les applications.  
  
 En règle générale, les développeurs ont toujours dû écrire eux-mêmes une partie ou l’intégralité de ce code, selon la technologie employée. Toutefois, WPF génère ce code pour vous lorsque le fichier de balisage de votre définition d’application est configuré `ApplicationDefinition` en tant qu’élément MSBuild, comme indiqué dans le fichier projet MSBuild suivant:  
  
```xml  
<Project   
  DefaultTargets="Build"  
                        xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  ...  
  <ApplicationDefinition Include="App.xaml" />  
  <Compile Include="App.xaml.cs" />  
  ...  
</Project>  
```  
  
 Étant donné que le fichier code-behind contient du code, il est marqué `Compile` comme un élément MSBuild, comme c’est normal.  
  
 L’application de ces configurations MSBuild aux fichiers de balisage et code-behind d’une définition d’application amène MSBuild à générer du code similaire à ce qui suit:  
  
 [!code-csharp[auto-generated-code](~/samples/snippets/csharp/VS_Snippets_Wpf/AppDefAugSnippets/CSharp/App.cs)]
 [!code-vb[auto-generated-code](~/samples/snippets/visualbasic/VS_Snippets_Wpf/AppDefAugSnippets/VisualBasic/App.vb)]  
  
 Le code résultant augmente la définition de votre application avec un code d’infrastructure supplémentaire, qui comprend la méthode `Main`de point d’entrée. L' <xref:System.STAThreadAttribute> attribut est appliqué à la `Main` méthode pour indiquer que le thread d’interface utilisateur principal de l’application WPF est un thread STA, ce qui est requis pour les applications WPF. Quand elle est `Main` appelée, crée une nouvelle `App` instance de avant `InitializeComponent` d’appeler la méthode pour inscrire les événements et définir les propriétés implémentées dans le balisage. Étant `InitializeComponent` donné que est généré pour vous, vous n’avez pas `InitializeComponent` besoin d’appeler explicitement à partir d’une <xref:System.Windows.Controls.Page> définition <xref:System.Windows.Window> d’application comme vous le feriez pour les implémentations et. Enfin, la <xref:System.Windows.Application.Run%2A> méthode est appelée pour démarrer l’application.  
  
<a name="Getting_the_Current_Application"></a>   
## <a name="getting-the-current-application"></a>Obtention de l’application actuelle  
 Étant donné que les fonctionnalités <xref:System.Windows.Application> de la classe sont partagées dans une application, il ne peut y avoir <xref:System.Windows.Application> qu’une <xref:System.AppDomain>seule instance de la classe par. Pour appliquer cela, la <xref:System.Windows.Application> classe est implémentée en tant que classe singleton (consultez [Implementing Singleton in C# ](https://go.microsoft.com/fwlink/?LinkId=100567)), qui crée une seule instance de elle-même et fournit un `static` accès partagé à celle-ci avec la <xref:System.Windows.Application.Current%2A> propriété.  
  
 Le code suivant montre comment acquérir une référence à l' <xref:System.Windows.Application> objet pour le actuel. <xref:System.AppDomain>  
  
 [!code-csharp[ApplicationManagementOverviewSnippets#GetCurrentAppCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationManagementOverviewSnippets/CSharp/MainWindow.xaml.cs#getcurrentappcode)]
 [!code-vb[ApplicationManagementOverviewSnippets#GetCurrentAppCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationManagementOverviewSnippets/VisualBasic/MainWindow.xaml.vb#getcurrentappcode)]  
  
 <xref:System.Windows.Application.Current%2A>retourne une référence à une instance de la <xref:System.Windows.Application> classe. Si vous souhaitez une référence à votre <xref:System.Windows.Application> classe dérivée, vous devez effectuer un cast <xref:System.Windows.Application.Current%2A> de la valeur de la propriété, comme indiqué dans l’exemple suivant.  
  
 [!code-csharp[ApplicationManagementOverviewSnippets#GetSTCurrentAppCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationManagementOverviewSnippets/CSharp/MainWindow.xaml.cs#getstcurrentappcode)]
 [!code-vb[ApplicationManagementOverviewSnippets#GetSTCurrentAppCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationManagementOverviewSnippets/VisualBasic/MainWindow.xaml.vb#getstcurrentappcode)]  
  
 Vous pouvez inspecter la valeur <xref:System.Windows.Application.Current%2A> de à n’importe quel stade de la <xref:System.Windows.Application> durée de vie d’un objet. Toutefois, vous devez être vigilant. Après l' <xref:System.Windows.Application> instanciation de la classe, il existe un point pendant lequel l’état de <xref:System.Windows.Application> l’objet est incohérent. Pendant cette période, <xref:System.Windows.Application> effectue les différentes tâches d’initialisation requises par votre code pour s’exécuter, y compris l’établissement de l’infrastructure d’application, la définition des propriétés et l’inscription des événements. Si vous essayez d’utiliser l' <xref:System.Windows.Application> objet pendant cette période, votre code peut avoir des résultats inattendus, en particulier s’il <xref:System.Windows.Application> dépend des différentes propriétés définies.  
  
 Lorsque <xref:System.Windows.Application> termine son travail d’initialisation, sa durée de vie commence véritablement.  
  
<a name="Application_Lifetime"></a>   
## <a name="application-lifetime"></a>Durée de vie d’une application  
 La durée de vie d’une application WPF est marquée par plusieurs événements déclenchés <xref:System.Windows.Application> par pour vous avertir lorsque votre application a démarré, a été activée et désactivée et a été arrêtée.  

<a name="Splash_Screen"></a>   
### <a name="splash-screen"></a>Écran de démarrage  
 À partir de la .NET Framework 3,5 SP1, vous pouvez spécifier une image à utiliser dans une fenêtre de démarrage ou un *écran*de démarrage. La <xref:System.Windows.SplashScreen> classe permet d’afficher facilement une fenêtre de démarrage pendant le chargement de votre application. La <xref:System.Windows.SplashScreen> fenêtre est créée et affichée avant <xref:System.Windows.Application.Run%2A> l’appel de. Pour plus d’informations, consultez [temps de démarrage](../advanced/application-startup-time.md) de l’application et [Ajouter un écran de démarrage à une application WPF](how-to-add-a-splash-screen-to-a-wpf-application.md).  
  
<a name="Starting_an_Application"></a>   
### <a name="starting-an-application"></a>Démarrage d’une application  
 Une <xref:System.Windows.Application.Run%2A> fois que est appelé et que l’application est initialisée, l’application est prête à s’exécuter. Ce moment est signifié lorsque l' <xref:System.Windows.Application.Startup> événement est déclenché:  
  
[!code-csharp[Startup-event](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationStartupSnippets/CSharp/App.xaml.cs?range=3-11,31-33)]
[!code-vb[Startup-event](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationStartupSnippets/visualbasic/application.xaml.vb?range=5-11,30-32)]
  
 À ce stade de la durée de vie d’une application, la chose la plus courante est d’afficher une interface utilisateur.  
  
<a name="Showing_a_User_Interface"></a>
### <a name="showing-a-user-interface"></a>Affichage d’une interface utilisateur  
 La plupart des applications Windows autonomes ouvrent un <xref:System.Windows.Window> lorsqu’elles commencent à s’exécuter. Le <xref:System.Windows.Application.Startup> gestionnaire d’événements est un emplacement à partir duquel vous pouvez effectuer cette opération, comme le montre le code suivant.  
  
 [!code-xaml[AppShowWindowHardSnippets#StartupEventMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/AppShowWindowHardSnippets/CSharp/App.xaml#startupeventmarkup)]  
  
 [!code-csharp[AppShowWindowHardSnippets#StartupEventCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/AppShowWindowHardSnippets/CSharp/App.xaml.cs#startupeventcodebehind)]
 [!code-vb[AppShowWindowHardSnippets#StartupEventCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/AppShowWindowHardSnippets/VisualBasic/Application.xaml.vb#startupeventcodebehind)]  
  
> [!NOTE]
> Le premier <xref:System.Windows.Window> à être instancié dans une application autonome devient la fenêtre d’application principale par défaut. Cet <xref:System.Windows.Window> objet est référencé par la <xref:System.Windows.Application.MainWindow%2A?displayProperty=nameWithType> propriété. La valeur de la <xref:System.Windows.Application.MainWindow%2A> propriété peut être modifiée par programme si une autre fenêtre que la première <xref:System.Windows.Window> instanciée doit être la fenêtre principale.  
  
 Quand un XBAP démarre pour la première fois, il accède très probablement <xref:System.Windows.Controls.Page>à un. Ceci est illustré dans le code suivant.  
  
 [!code-xaml[XBAPAppStartupSnippets#StartupXBAPMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/XBAPAppStartupSnippets/CSharp/App.xaml#startupxbapmarkup)]  
  
 [!code-csharp[XBAPAppStartupSnippets#StartupXBAPCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/XBAPAppStartupSnippets/CSharp/App.xaml.cs#startupxbapcodebehind)]
 [!code-vb[XBAPAppStartupSnippets#StartupXBAPCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/XBAPAppStartupSnippets/VisualBasic/Application.xaml.vb#startupxbapcodebehind)]  
  
 Si vous gérez <xref:System.Windows.Application.Startup> uniquement pour <xref:System.Windows.Window> ouvrir ou accéder à un <xref:System.Windows.Controls.Page>, vous pouvez définir l’attribut `StartupUri` dans le balisage à la place.  
  
 L’exemple suivant montre comment utiliser <xref:System.Windows.Application.StartupUri%2A> à partir d’une application autonome pour ouvrir un. <xref:System.Windows.Window>  
  
 [!code-xaml[ApplicationManagementOverviewSnippets#OverviewStartupUriMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationManagementOverviewSnippets/CSharp/App.xaml#overviewstartupurimarkup)]  
  
 L’exemple suivant montre comment utiliser <xref:System.Windows.Application.StartupUri%2A> à partir d’une application XBAP pour naviguer jusqu’à un. <xref:System.Windows.Controls.Page>  
  
 [!code-xaml[PageSnippets#XBAPStartupUriMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/PageSnippets/CSharp/App.xaml#xbapstartupurimarkup)]  
  
 Ce balisage a le même effet que le code précédent pour ouvrir une fenêtre.  
  
> [!NOTE]
> Pour plus d’informations sur la navigation, consultez [vue d’ensemble](navigation-overview.md)de la navigation.  
  
 Vous devez gérer l' <xref:System.Windows.Application.Startup> événement pour ouvrir un <xref:System.Windows.Window> si vous devez l’instancier à l’aide d’un constructeur sans paramètre, ou vous devez définir ses propriétés ou vous abonner à ses événements avant de l’afficher, ou vous devez traiter les arguments de ligne de commande. qui ont été fournies lors du lancement de l’application.  
  
<a name="Processing_Command_Line_Arguments"></a>   
### <a name="processing-command-line-arguments"></a>Traitement des arguments de ligne de commande  
 Dans Windows, les applications autonomes peuvent être lancées à partir d’une invite de commandes ou du bureau. Dans les deux cas, les arguments de ligne de commande peuvent être passés à l’application. L’exemple suivant montre une application qui est lancée avec un seul argument de ligne de commande, « /StartMinimized » :  
  
 `wpfapplication.exe /StartMinimized`  
  
 Pendant l’initialisation de l’application, WPF récupère les arguments de ligne de commande du système d’exploitation et les transmet <xref:System.Windows.Application.Startup> au gestionnaire d’événements <xref:System.Windows.StartupEventArgs.Args%2A> via la propriété <xref:System.Windows.StartupEventArgs> du paramètre. Vous pouvez récupérer et stocker les arguments de ligne de commande à l’aide de code similaire au suivant.  
  
 [!code-xaml[ApplicationStartupSnippets#HandleStartupXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationStartupSnippets/CSharp/App.xaml#handlestartupxaml)]  
  
 [!code-csharp[ApplicationStartupSnippets#HandleStartupCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationStartupSnippets/CSharp/App.xaml.cs#handlestartupcodebehind)]
 [!code-vb[ApplicationStartupSnippets#HandleStartupCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationStartupSnippets/visualbasic/application.xaml.vb#handlestartupcodebehind)]  
  
 Handles <xref:System.Windows.Application.Startup> de code permettant de vérifier si l’argument de ligne de commande **/StartMinimized** a été fourni; si c’est le cas, <xref:System.Windows.WindowState> il <xref:System.Windows.WindowState.Minimized>ouvre la fenêtre principale avec un de. Notez que, étant <xref:System.Windows.Window.WindowState%2A> donné que la propriété doit être définie par programme, <xref:System.Windows.Window> la main doit être ouverte explicitement dans le code.  
  
 Les XBAP ne peuvent pas récupérer et traiter les arguments de ligne de commande, car ils sont lancés à l’aide du déploiement ClickOnce (consultez [déploiement d’une application WPF](deploying-a-wpf-application-wpf.md)). En revanche, ils peuvent récupérer et traiter des paramètres de chaîne de requête à partir des URL servant à les lancer.  
  
<a name="Application_Activation_and_Deactivation"></a>   
### <a name="application-activation-and-deactivation"></a>Activation et désactivation d’une application  
 Windows permet aux utilisateurs de basculer entre les applications. La façon la plus courante consiste à utiliser la combinaison de touches ALT+TAB. Une application ne peut être basculée que si elle dispose d' <xref:System.Windows.Window> un visible qu’un utilisateur peut sélectionner. Le actuellement sélectionné <xref:System.Windows.Window> est la *fenêtre active* (également appelée fenêtre de *premier plan*) et est le <xref:System.Windows.Window> qui reçoit l’entrée d’utilisateur. L’application avec la fenêtre active est l’application *active* (ou *application de premier plan*). Une application devient l’application active dans les circonstances suivantes :  
  
- Elle est lancée et affiche <xref:System.Windows.Window>un.  
  
- Un utilisateur passe d’une autre application en sélectionnant un <xref:System.Windows.Window> dans l’application.  
  
 Vous pouvez détecter qu’une application devient active en gérant l' <xref:System.Windows.Application.Activated?displayProperty=nameWithType> événement.  
  
 De même, une application peut devenir inactive dans les circonstances suivantes :  
  
- Un utilisateur bascule vers une autre application à partir de l’application active.  
  
- L’application s’arrête.  
  
 Vous pouvez détecter qu’une application devient inactive en gérant l' <xref:System.Windows.Application.Deactivated?displayProperty=nameWithType> événement.  
  
 Le code suivant montre comment gérer les <xref:System.Windows.Application.Activated> événements et <xref:System.Windows.Application.Deactivated> pour déterminer si une application est active.  
  
 [!code-xaml[ApplicationActivationSnippets#DetectActivationStateXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationActivationSnippets/CSharp/App.xaml#detectactivationstatexaml)]  
  
 [!code-csharp[ApplicationActivationSnippets#DetectActivationStateCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationActivationSnippets/CSharp/App.xaml.cs#detectactivationstatecodebehind)]
 [!code-vb[ApplicationActivationSnippets#DetectActivationStateCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationActivationSnippets/visualbasic/application.xaml.vb#detectactivationstatecodebehind)]  
  
 Un <xref:System.Windows.Window> peut également être activé et désactivé. Pour plus d'informations, consultez <xref:System.Windows.Window.Activated?displayProperty=nameWithType> et <xref:System.Windows.Window.Deactivated?displayProperty=nameWithType>.  
  
> [!NOTE]
> Ni <xref:System.Windows.Application.Activated?displayProperty=nameWithType> ni<xref:System.Windows.Application.Deactivated?displayProperty=nameWithType> n’est déclenché pour les XBAP.  
  
<a name="Application_Shutdown"></a>   
### <a name="application-shutdown"></a>Arrêt d’une application  
 La durée de vie d’une application s’achève quand elle est arrêtée, ce qui peut se produire pour les raisons suivantes :  
  
- Un utilisateur ferme tous <xref:System.Windows.Window>les.  
  
- Un utilisateur ferme le principal <xref:System.Windows.Window>.  
  
- Un utilisateur met fin à la session Windows en se déconnectant ou en arrêtant.  
  
- Une condition spécifique à l’application a été remplie.  
  
 Pour vous aider à gérer l’arrêt <xref:System.Windows.Application> de l' <xref:System.Windows.Application.Shutdown%2A> application, fournit <xref:System.Windows.Application.ShutdownMode%2A> la méthode, la <xref:System.Windows.Application.SessionEnding> propriété <xref:System.Windows.Application.Exit> et les événements et.  
  
> [!NOTE]
> <xref:System.Windows.Application.Shutdown%2A>peut uniquement être appelé à partir d’applications <xref:System.Security.Permissions.UIPermission>qui ont. Les applications WPF autonomes disposent toujours de cette autorisation. Toutefois, les applications XBAP qui s’exécutent dans le bac à sable de sécurité de confiance partielle de la zone Internet ne le font pas.  
  
#### <a name="shutdown-mode"></a>Mode d’arrêt  
 La plupart des applications s’arrêtent à la fermeture de toutes les fenêtres ou de la fenêtre principale. Toutefois, d’autres conditions spécifiques à l’application peuvent parfois déterminer l’arrêt d’une application. Vous pouvez spécifier les conditions dans lesquelles votre application s’arrêtera en définissant <xref:System.Windows.Application.ShutdownMode%2A> avec l’une des valeurs <xref:System.Windows.ShutdownMode> d’énumération suivantes:  
  
- <xref:System.Windows.ShutdownMode.OnLastWindowClose>  
  
- <xref:System.Windows.ShutdownMode.OnMainWindowClose>  
  
- <xref:System.Windows.ShutdownMode.OnExplicitShutdown>  
  
 La valeur par défaut <xref:System.Windows.Application.ShutdownMode%2A> de <xref:System.Windows.ShutdownMode.OnLastWindowClose>est, ce qui signifie qu’une application s’arrête automatiquement lorsque la dernière fenêtre de l’application est fermée par l’utilisateur. Toutefois, si votre application doit être arrêtée lorsque la fenêtre principale est fermée, WPF le fait automatiquement si vous définissez <xref:System.Windows.Application.ShutdownMode%2A> sur <xref:System.Windows.ShutdownMode.OnMainWindowClose>. L'exemple suivant le démontre.  
  
 [!code-xaml[ApplicationShutdownModeSnippets#OnMainWindowCloseMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationShutdownModeSnippets/CS/Page1.xaml#onmainwindowclosemarkup)]  
  
 Lorsque vous avez des conditions d’arrêt spécifiques à l’application <xref:System.Windows.Application.ShutdownMode%2A> , <xref:System.Windows.ShutdownMode.OnExplicitShutdown>vous affectez à la valeur. Dans ce cas, il vous incombe d’arrêter une application en appelant explicitement la <xref:System.Windows.Application.Shutdown%2A> méthode; sinon, votre application continue de s’exécuter même si toutes les fenêtres sont fermées. Notez que <xref:System.Windows.Application.Shutdown%2A> est appelé implicitement lorsque a <xref:System.Windows.Application.ShutdownMode%2A> <xref:System.Windows.ShutdownMode.OnLastWindowClose> la valeur ou <xref:System.Windows.ShutdownMode.OnMainWindowClose>.  
  
> [!NOTE]
> <xref:System.Windows.Application.ShutdownMode%2A>peut être défini à partir d’une application XBAP, mais il est ignoré; une application XBAP est toujours arrêtée lorsqu’elle est quittée dans un navigateur ou lorsque le navigateur qui héberge l’application XBAP est fermé. Pour plus d’informations, consultez [Vue d’ensemble de la navigation](navigation-overview.md).  
  
#### <a name="session-ending"></a>Fin de session  
 Les conditions d’arrêt décrites par la <xref:System.Windows.Application.ShutdownMode%2A> propriété sont spécifiques à une application. Dans certains cas, pourtant, une application peut s’arrêter à la suite d’une condition externe. La condition externe la plus courante se produit lorsqu’un utilisateur met fin à la session Windows par les actions suivantes:  
  
- Déconnexion  
  
- Arrêt  
  
- Redémarrage  
  
- Mise en veille prolongée  
  
 Pour détecter à quel moment une session Windows se termine, <xref:System.Windows.Application.SessionEnding> vous pouvez gérer l’événement, comme illustré dans l’exemple suivant.  
  
 [!code-xaml[ApplicationSessionEndingSnippets#HandlingSessionEndingXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationSessionEndingSnippets/CSharp/App.xaml#handlingsessionendingxaml)]  
  
 [!code-csharp[ApplicationSessionEndingSnippets#HandlingSessionEndingCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationSessionEndingSnippets/CSharp/App.xaml.cs#handlingsessionendingcodebehind)]
 [!code-vb[ApplicationSessionEndingSnippets#HandlingSessionEndingCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationSessionEndingSnippets/visualbasic/application.xaml.vb#handlingsessionendingcodebehind)]  
  
 Dans cet exemple, le code inspecte la <xref:System.Windows.SessionEndingCancelEventArgs.ReasonSessionEnding%2A> propriété pour déterminer la façon dont la session Windows se termine. Il utilise cette valeur pour afficher un message de confirmation à l’attention de l’utilisateur. Si l’utilisateur ne souhaite pas que la session se termine, le <xref:System.ComponentModel.CancelEventArgs.Cancel%2A> code `true` définit sur pour empêcher la fermeture de la session Windows.  
  
> [!NOTE]
> <xref:System.Windows.Application.SessionEnding>n’est pas déclenché pour les XBAP.

#### <a name="exit"></a>Exit  
 Quand une application s’arrête, il peut s’avérer nécessaire d’effectuer quelque traitement final, par exemple rendre persistant l’état de l’application. Dans ce cas, vous pouvez gérer l' <xref:System.Windows.Application.Exit> événement, comme le `App_Exit` montre le gestionnaire d’événements dans l’exemple suivant. Il est défini en tant que gestionnaire d’événements dans le fichier *app. Xaml* . Son implémentation est mise en surbrillance dans les fichiers *app.Xaml.cs* et *application. Xaml. vb* .
  
[!code-xaml[Defining-the-Exit-event-handler](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTOApplicationModelSnippets/CSharp/App.xaml?highlight=1-7)]  
  
 [!code-csharp[Handling-the-Exit-event](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTOApplicationModelSnippets/CSharp/App.xaml.cs?highlight=42-55)]
 [!code-vb[Handling-the-Exit-event](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOApplicationModelSnippets/visualbasic/application.xaml.vb?highlight=34-45)]  
  
 Pour obtenir un exemple complet, consultez [rendre persistantes et restaurer les propriétés de portée application d’une session d’application à l’autre](persist-and-restore-application-scope-properties.md).  
  
 <xref:System.Windows.Application.Exit>peut être géré par les applications autonomes et les applications XBAP. Pour les applications <xref:System.Windows.Application.Exit> XBAP, est déclenché dans les circonstances suivantes:  
  
- Une application XBAP est quittée.  
  
- Dans Internet Explorer, lorsque l’onglet qui héberge le XBAP est fermé.  
  
- Le navigateur est fermé.  
  
#### <a name="exit-code"></a>Code de sortie  
 Les applications sont principalement lancées par le système d’exploitation en réponse à une requête de l’utilisateur. Toutefois, une application peut être lancée par une autre application pour effectuer une tâche spécifique. Quand l’application lancée s’arrête, il est possible que l’application de lancement souhaite connaître la condition dans laquelle s’est effectué cet arrêt. Dans ces situations, Windows permet aux applications de retourner un code de sortie d’application lors de l’arrêt. Par défaut, les applications WPF retournent une valeur de code de sortie de 0.  
  
> [!NOTE]
> Quand vous déboguez à partir de Visual Studio, le code de sortie de l’application s’affiche dans la fenêtre **sortie** lorsque l’application s’arrête, dans un message similaire à ce qui suit:  
>   
>  `The program '[5340] AWPFApp.vshost.exe: Managed' has exited with code 0 (0x0).`  
>   
>  Pour ouvrir la fenêtre **sortie** , cliquez sur **sortie** dans le menu **affichage** .  
  
 Pour modifier le code de sortie, vous pouvez appeler <xref:System.Windows.Application.Shutdown%28System.Int32%29> la surcharge, qui accepte un argument entier comme code de sortie:  
  
 [!code-csharp[ApplicationExitSnippets#AppExitCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationExitSnippets/CSharp/MainWindow.xaml.cs#appexitcode)]
 [!code-vb[ApplicationExitSnippets#AppExitCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationExitSnippets/visualbasic/mainwindow.xaml.vb#appexitcode)]  
  
 Vous pouvez détecter la valeur du code de sortie et la modifier en gérant l' <xref:System.Windows.Application.Exit> événement. Le <xref:System.Windows.Application.Exit> gestionnaire d’événements reçoit un <xref:System.Windows.ExitEventArgs> qui fournit l’accès au code de sortie avec <xref:System.Windows.ExitEventArgs.ApplicationExitCode%2A> la propriété. Pour plus d'informations, consultez <xref:System.Windows.Application.Exit>.  
  
> [!NOTE]
> Vous pouvez définir le code de sortie dans les applications autonomes et les applications XBAP. Toutefois, la valeur du code de sortie est ignorée pour les XBAP.  
  
<a name="Unhandled_Exceptions"></a>   
### <a name="unhandled-exceptions"></a>Exceptions non gérées  
 Il peut parfois arriver qu’une application s’arrête anormalement, par exemple en cas d’exception inattendue. Dans ce cas, il est possible qu’elle n’ait pas le code nécessaire à la détection et au traitement de l’exception. Ce type d’exception est une exception non gérée ; une notification similaire à celle illustrée dans la figure ci-dessous s’affiche avant la fermeture de l’application.  
  
 ![Capture d’écran montrant une notification d’exception non gérée.](./media/application-management-overview/unhandled-exception-notification.png)  
  
 Du point de vue de l’expérience utilisateur, il est préférable pour une application d’éviter ce comportement par défaut en effectuant certaines ou l’ensemble des opérations suivantes :  
  
- Affichage d’informations conviviales.  
  
- Tentative de maintenir une application en cours d’exécution.  
  
- Enregistrement d’informations d’exception détaillées et conviviales pour les développeurs dans le journal des événements Windows.  
  
 L’implémentation de cette prise en charge dépend de la capacité à détecter les exceptions non gérées <xref:System.Windows.Application.DispatcherUnhandledException> , à laquelle l’événement est déclenché.  
  
[!code-xaml[detecting-unhandled-exceptions](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationDispatcherUnhandledExceptionSnippets/CSharp/App.xaml#handledispatcherunhandledexceptionxaml)]  
  
[!code-csharp[code-to-detect-unhandled-exceptions](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationDispatcherUnhandledExceptionSnippets/CSharp/App.xaml.cs)]
[!code-vb[code-to-detect-unhandled-exceptions](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationDispatcherUnhandledExceptionSnippets/visualbasic/application.xaml.vb)]  
  
 Un <xref:System.Windows.Application.DispatcherUnhandledException> paramètre qui contient des informations <xref:System.Windows.Threading.DispatcherUnhandledExceptionEventArgs> contextuelles relatives à l’exception non gérée, y compris l’exception elle-<xref:System.Windows.Threading.DispatcherUnhandledExceptionEventArgs.Exception%2A?displayProperty=nameWithType>même (), est passé au gestionnaire d’événements. Vous pouvez utiliser ces informations pour déterminer comment gérer l’exception.  
  
 Lorsque vous gérez <xref:System.Windows.Application.DispatcherUnhandledException>, vous devez affecter à <xref:System.Windows.Threading.DispatcherUnhandledExceptionEventArgs.Handled%2A?displayProperty=nameWithType> `true`la propriété la valeur; sinon, WPF considère toujours l’exception comme non gérée et revient au comportement par défaut décrit précédemment. Si une exception non gérée est levée et que l' <xref:System.Windows.Application.DispatcherUnhandledException> événement n’est pas géré, ou si l’événement est <xref:System.Windows.Threading.DispatcherUnhandledExceptionEventArgs.Handled%2A> géré et a `false`la valeur, l’application s’arrête immédiatement. En outre, aucun <xref:System.Windows.Application> autre événement n’est déclenché. Par conséquent, vous devez gérer <xref:System.Windows.Application.DispatcherUnhandledException> si votre application a du code qui doit s’exécuter avant que l’application ne s’arrête.  
  
 Bien qu’une application puisse s’arrêter à la suite d’une exception non gérée, elle s’arrête habituellement en réponse à une requête de l’utilisateur, comme décrit dans la section suivante.  
  
<a name="Application_Lifetime_Events"></a>   
### <a name="application-lifetime-events"></a>Événements de durée de vie de l'application  
 Les applications autonomes et les XBAP n’ont pas exactement les mêmes durées de vie. La figure suivante illustre les principaux événements de la durée de vie d’une application autonome et indique l’ordre dans lequel ils sont déclenchés.  
  
 ![Application autonome &#45; Événements d’objets d’application](./media/applicationmodeloverview-applicationobjectevents.png "ApplicationModelOverview_ApplicationObjectEvents")  
  
 De même, la figure ci-dessous illustre les événements clés dans la durée de vie d’une application XBAP et montre l’ordre dans lequel ils sont déclenchés.  
  
 ![XBAP &#45; Événements d’objets d’application](./media/applicationmodeloverview-applicationobjectevents-xbap.png "ApplicationModelOverview_ApplicationObjectEvents_xbap")  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Application>
- [Vue d'ensemble des fenêtres WPF](wpf-windows-overview.md)
- [Vue d’ensemble de la navigation](navigation-overview.md)
- [Fichiers de ressources, de contenu et de données d’une application WPF](wpf-application-resource-content-and-data-files.md)
- [URI à en-tête pack dans WPF](pack-uris-in-wpf.md)
- [Modèle d’application: Rubriques de procédures](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms749013(v=vs.100))
- [Développement de l’application](index.md)
