---
title: Vue d'ensemble de la gestion d'applications
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- application management [WPF]
ms.assetid: 32b1c054-5aca-423b-b4b5-ed8dc4dc637d
ms.openlocfilehash: c36de23a6a49e684330fc0f47fc46bd86c55e767
ms.sourcegitcommit: 34593b4d0be779699d38a9949d6aec11561657ec
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/11/2019
ms.locfileid: "66834072"
---
# <a name="application-management-overview"></a>Vue d'ensemble de la gestion d'applications
Toutes les applications tendent à partager un jeu de fonctionnalités commun qui s’applique à l’implémentation et à la gestion. Cette rubrique fournit une vue d’ensemble des fonctionnalités dans le <xref:System.Windows.Application> classe pour la création et la gestion des applications.  

## <a name="the-application-class"></a>Classe Application  
 Dans WPF, les fonctionnalités communes de portée application sont encapsulées dans le <xref:System.Windows.Application> classe. Le <xref:System.Windows.Application> classe inclut les fonctionnalités suivantes :  
  
- Suivi et interaction avec la durée de vie d’une application.  
  
- Récupération et traitement des paramètres de ligne de commande.  
  
- Détection et traitement des exceptions non gérées.  
  
- Partage des propriétés de portée application et des ressources.  
  
- Gestion des fenêtres dans des applications autonomes.  
  
- Suivi et gestion de la navigation.  
  
<a name="The_Application_Class"></a>   
## <a name="how-to-perform-common-tasks-using-the-application-class"></a>Comment effectuer des tâches courantes à l’aide de la classe Application  
 Si vous n’êtes pas intéressé par tous les détails de la <xref:System.Windows.Application> (classe), le tableau suivant dresse la liste des tâches courantes de <xref:System.Windows.Application> et comment les accomplir. En affichant l’API et les rubriques connexes, vous pouvez obtenir davantage d’informations et des exemples de code.  
  
|Tâche|Approche|  
|----------|--------------|  
|Obtenir un objet qui représente l’application actuelle|Utilisez la propriété <xref:System.Windows.Application.Current%2A?displayProperty=nameWithType>.|  
|Ajouter un écran de démarrage à une application|Consultez [ajouter un écran de démarrage dans une Application WPF](how-to-add-a-splash-screen-to-a-wpf-application.md).|  
|Démarrer une application|Utilisez la méthode <xref:System.Windows.Application.Run%2A?displayProperty=nameWithType>.|  
|Arrêter une application|Utilisez le <xref:System.Windows.Application.Shutdown%2A> méthode de la <xref:System.Windows.Application.Current%2A?displayProperty=nameWithType> objet.|  
|Obtenir des arguments de la ligne de commande|Gérer le <xref:System.Windows.Application.Startup?displayProperty=nameWithType> événement et utilisez le <xref:System.Windows.StartupEventArgs.Args%2A?displayProperty=nameWithType> propriété. Pour obtenir un exemple, consultez le <xref:System.Windows.Application.Startup?displayProperty=nameWithType> événement.|  
|Obtenir et définir le code de sortie d’application|Définir le <xref:System.Windows.ExitEventArgs.ApplicationExitCode%2A?displayProperty=nameWithType> propriété dans le <xref:System.Windows.Application.Exit?displayProperty=nameWithType> Gestionnaire d’événements ou l’appel de la <xref:System.Windows.Application.Shutdown%2A> (méthode) et passez un entier.|  
|Détecter et traiter des exceptions non gérées|Gérer le <xref:System.Windows.Application.DispatcherUnhandledException> événement.|  
|Obtenir et définir des ressources de portée application|Utilisez la propriété <xref:System.Windows.Application.Resources%2A?displayProperty=nameWithType>.|  
|Utiliser un dictionnaire de ressources de portée application|Consultez [utiliser un dictionnaire de ressources de portée Application](how-to-use-an-application-scope-resource-dictionary.md).|  
|Obtenir et définir les propriétés de portée application|Utilisez la propriété <xref:System.Windows.Application.Properties%2A?displayProperty=nameWithType>.|  
|Obtenir et enregistrer l’état d’une application|Consultez [rendre persistantes et restaurer les propriétés de portée Application entre les Sessions de l’Application](persist-and-restore-application-scope-properties.md).|  
|Gérer les fichiers de données de non-code, dont les fichiers de ressources, les fichiers de contenu et les fichiers du site d’origine.|Consultez [ressource d’Application WPF, de contenu et de fichiers de données](wpf-application-resource-content-and-data-files.md).|  
|Gérer des fenêtres dans des applications autonomes|Consultez [Vue d’ensemble des fenêtres WPF](wpf-windows-overview.md).|  
|Suivre et gérer la navigation|Consultez [vue d’ensemble de la Navigation](navigation-overview.md).|  
  
<a name="The_Application_Definition"></a>   
## <a name="the-application-definition"></a>Définition d’application  
 Pour utiliser les fonctionnalités de la <xref:System.Windows.Application> (classe), vous devez implémenter une définition d’application. Une définition d’application WPF est une classe qui dérive de <xref:System.Windows.Application> et est configuré avec un paramètre MSBuild.  

### <a name="implementing-an-application-definition"></a>Implémentation d’une définition d’application  
 Une définition d’application WPF typique est implémentée à l’aide de balisage et code-behind. Vous pouvez ainsi utiliser le balisage pour définir de façon déclarative les propriétés d’une application et les ressources ainsi que pour inscrire des événements, tout en gérant les événements et en implémentant le comportement spécifique à l’application dans un fichier code-behind.  
  
 L’exemple suivant montre comment implémenter une définition d’application à l’aide de balisage et de code-behind :  
  
 [!code-xaml[ApplicationSnippets#ApplicationXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationSnippets/CSharp/App.xaml#applicationxaml)]  
  
 [!code-csharp[ApplicationSnippets#ApplicationCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationSnippets/CSharp/App.xaml.cs#applicationcodebehind)]
 [!code-vb[ApplicationSnippets#ApplicationCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationSnippets/visualbasic/application.xaml.vb#applicationcodebehind)]  
  
 Pour permettre l’interopérabilité d’un fichier de balisage et d’un fichier code-behind, les conditions suivantes doivent être satisfaites :  
  
- Dans le balisage, la `Application` élément doit inclure le `x:Class` attribut. Lorsque l’application est générée, l’existence de `x:Class` dans le balisage fichier amène MSBuild créer un `partial` classe qui dérive de <xref:System.Windows.Application> et porte le nom spécifié par le `x:Class` attribut. Cela nécessite l’ajout d’une déclaration d’espace de noms XML pour le schéma XAML (`xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"`).
  
- Dans le code-behind, la classe doit être un `partial` classe portant le même nom que celui qui est spécifié par le `x:Class` d’attribut dans le balisage et doit dériver de <xref:System.Windows.Application>. Cela permet au fichier code-behind à associer à la `partial` classe qui est généré pour le fichier de balisage quand l’application est générée (consultez [création d’une Application WPF](building-a-wpf-application-wpf.md)).  
  
> [!NOTE]
>  Lorsque vous créez un nouveau projet d’Application WPF ou un projet d’Application de navigateur WPF à l’aide de Visual Studio, une définition d’application est incluse par défaut et est définie à l’aide de balisage et code-behind.  
  
 Ce code est le minimum requis pour implémenter une définition d’application. Toutefois, une configuration supplémentaire de MSBuild doit être apportées à la définition de l’application avant de générer et exécuter l’application.  
  
### <a name="configuring-the-application-definition-for-msbuild"></a>Configuration de la définition d’application pour MSBuild  
 Les applications autonomes et des applications de navigateur XAML (XBAP) requièrent l’implémentation d’un certain niveau d’infrastructure avant de pouvoir exécuter. La partie la plus importante de cette infrastructure est le point d’entrée. Quand une application est lancée par un utilisateur, le système d’exploitation appelle le point d’entrée, qui est une fonction connue pour démarrer les applications.  
  
 En règle générale, les développeurs ont toujours dû écrire eux-mêmes une partie ou l’intégralité de ce code, selon la technologie employée. Toutefois, WPF génère automatiquement ce code pour vous lorsque le fichier de balisage de votre définition d’application est configuré en tant que MSBuild `ApplicationDefinition` de l’élément, comme indiqué dans le fichier de projet MSBuild suivant :  
  
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
  
 Étant donné que le fichier code-behind contient du code, il est marqué comme MSBuild `Compile` de l’élément, comme cela est normal.  
  
 L’application de ces configurations de MSBuild pour les fichiers de balisage et code-behind d’une définition d’application entraîne MSBuild générer du code semblable au suivant :  
  
 [!code-csharp[auto-generated-code](~/samples/snippets/csharp/VS_Snippets_Wpf/AppDefAugSnippets/CSharp/App.cs)]
 [!code-vb[auto-generated-code](~/samples/snippets/visualbasic/VS_Snippets_Wpf/AppDefAugSnippets/VisualBasic/App.vb)]  
  
 Le code résultant ajoute à votre définition d’application avec le code d’infrastructure supplémentaire, qui inclut la méthode de point d’entrée `Main`. Le <xref:System.STAThreadAttribute> l’attribut est appliqué à la `Main` méthode pour indiquer que le thread d’interface utilisateur pour l’application WPF est un thread STA, qui est requis pour les applications WPF. Lorsqu’elle est appelée, `Main` crée une nouvelle instance de `App` avant d’appeler le `InitializeComponent` méthode pour inscrire les événements et définir les propriétés qui sont implémentées dans le balisage. Étant donné que `InitializeComponent` est généré pour vous, vous n’avez pas besoin d’appeler explicitement `InitializeComponent` à partir d’une définition d’application comme vous le feriez pour <xref:System.Windows.Controls.Page> et <xref:System.Windows.Window> implémentations. Enfin, le <xref:System.Windows.Application.Run%2A> méthode est appelée pour démarrer l’application.  
  
<a name="Getting_the_Current_Application"></a>   
## <a name="getting-the-current-application"></a>Obtention de l’application actuelle  
 Étant donné que les fonctionnalités de la <xref:System.Windows.Application> classe sont partagés dans une application, il peut y avoir qu’une seule instance de la <xref:System.Windows.Application> classe par <xref:System.AppDomain>. Pour cela, appliquer la <xref:System.Windows.Application> classe est implémentée comme une classe singleton (consultez [implémentation de Singleton en c#](https://go.microsoft.com/fwlink/?LinkId=100567)), qui crée une seule instance d’elle-même et fournit un accès partagé à avec le `static` <xref:System.Windows.Application.Current%2A> propriété.  
  
 Le code suivant montre comment acquérir une référence à la <xref:System.Windows.Application> objet actif <xref:System.AppDomain>.  
  
 [!code-csharp[ApplicationManagementOverviewSnippets#GetCurrentAppCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationManagementOverviewSnippets/CSharp/MainWindow.xaml.cs#getcurrentappcode)]
 [!code-vb[ApplicationManagementOverviewSnippets#GetCurrentAppCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationManagementOverviewSnippets/VisualBasic/MainWindow.xaml.vb#getcurrentappcode)]  
  
 <xref:System.Windows.Application.Current%2A> Retourne une référence à une instance de la <xref:System.Windows.Application> classe. Si vous souhaitez une référence à votre <xref:System.Windows.Application> dérivée de classe, vous devez caster la valeur de la <xref:System.Windows.Application.Current%2A> propriété, comme indiqué dans l’exemple suivant.  
  
 [!code-csharp[ApplicationManagementOverviewSnippets#GetSTCurrentAppCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationManagementOverviewSnippets/CSharp/MainWindow.xaml.cs#getstcurrentappcode)]
 [!code-vb[ApplicationManagementOverviewSnippets#GetSTCurrentAppCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationManagementOverviewSnippets/VisualBasic/MainWindow.xaml.vb#getstcurrentappcode)]  
  
 Vous pouvez inspecter la valeur de <xref:System.Windows.Application.Current%2A> à tout moment dans la durée de vie d’un <xref:System.Windows.Application> objet. Toutefois, vous devez être vigilant. Après le <xref:System.Windows.Application> classe est instanciée, il existe une période pendant laquelle l’état de la <xref:System.Windows.Application> objet n’est pas cohérente. Pendant cette période, <xref:System.Windows.Application> effectue diverses tâches d’initialisation qui sont requis par votre code à exécuter, notamment l’établissement de l’infrastructure d’application, définition des propriétés et l’inscription des événements. Si vous essayez d’utiliser le <xref:System.Windows.Application> de l’objet pendant cette période, votre code peut avoir des résultats inattendus, en particulier si elle varie selon les différents <xref:System.Windows.Application> définition des propriétés.  
  
 Lorsque <xref:System.Windows.Application> achève son initialisation, sa durée de vie commence véritablement.  
  
<a name="Application_Lifetime"></a>   
## <a name="application-lifetime"></a>Durée de vie d’une application  
 La durée de vie d’une application WPF est marquée par plusieurs événements déclenchés par <xref:System.Windows.Application> pour vous informer lorsque votre application a démarré, a été activée et désactivée et a été arrêté.  

<a name="Splash_Screen"></a>   
### <a name="splash-screen"></a>Écran de démarrage  
 À compter de .NET Framework 3.5 SP1, vous pouvez spécifier une image à utiliser dans une fenêtre de démarrage, ou *écran de démarrage*. Le <xref:System.Windows.SplashScreen> classe rend plus facile d’afficher une fenêtre de démarrage pendant le chargement de votre application. Le <xref:System.Windows.SplashScreen> fenêtre est créée et affichée avant <xref:System.Windows.Application.Run%2A> est appelée. Pour plus d’informations, consultez [temps de démarrage d’Application](../advanced/application-startup-time.md) et [ajouter un écran de démarrage dans une Application WPF](how-to-add-a-splash-screen-to-a-wpf-application.md).  
  
<a name="Starting_an_Application"></a>   
### <a name="starting-an-application"></a>Démarrage d’une application  
 Après avoir <xref:System.Windows.Application.Run%2A> est appelée et l’application est initialisée, l’application est prête à exécuter. Ce moment est signifié le <xref:System.Windows.Application.Startup> événement est déclenché :  
  
[!code-csharp[Startup-event](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationStartupSnippets/CSharp/App.xaml.cs?range=3-11,31-33)]
[!code-vb[Startup-event](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationStartupSnippets/visualbasic/application.xaml.vb?range=5-11,30-32)]
  
 À ce stade de durée de vie d’une application, la plus courante consiste à afficher une interface utilisateur.  
  
<a name="Showing_a_User_Interface"></a>
### <a name="showing-a-user-interface"></a>Affichage d’une interface utilisateur  
 La plupart des applications de Windows autonome ouvrir un <xref:System.Windows.Window> lorsqu’il démarre en cours d’exécution. Le <xref:System.Windows.Application.Startup> Gestionnaire d’événements est un emplacement à partir duquel ce faire, comme illustré par le code suivant.  
  
 [!code-xaml[AppShowWindowHardSnippets#StartupEventMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/AppShowWindowHardSnippets/CSharp/App.xaml#startupeventmarkup)]  
  
 [!code-csharp[AppShowWindowHardSnippets#StartupEventCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/AppShowWindowHardSnippets/CSharp/App.xaml.cs#startupeventcodebehind)]
 [!code-vb[AppShowWindowHardSnippets#StartupEventCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/AppShowWindowHardSnippets/VisualBasic/Application.xaml.vb#startupeventcodebehind)]  
  
> [!NOTE]
>  La première <xref:System.Windows.Window> à instancier dans une autonome application devenue la fenêtre principale de l’application par défaut. Cela <xref:System.Windows.Window> objet est référencé par le <xref:System.Windows.Application.MainWindow%2A?displayProperty=nameWithType> propriété. La valeur de la <xref:System.Windows.Application.MainWindow%2A> propriété peut être modifiée par programmation si une fenêtre différente de la première instancié <xref:System.Windows.Window> doit être la fenêtre principale.  
  
 Premier démarrage d’une application XBAP, il permet d’accéder très probablement à un <xref:System.Windows.Controls.Page>. Ceci est illustré dans le code suivant.  
  
 [!code-xaml[XBAPAppStartupSnippets#StartupXBAPMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/XBAPAppStartupSnippets/CSharp/App.xaml#startupxbapmarkup)]  
  
 [!code-csharp[XBAPAppStartupSnippets#StartupXBAPCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/XBAPAppStartupSnippets/CSharp/App.xaml.cs#startupxbapcodebehind)]
 [!code-vb[XBAPAppStartupSnippets#StartupXBAPCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/XBAPAppStartupSnippets/VisualBasic/Application.xaml.vb#startupxbapcodebehind)]  
  
 Si vous gérez <xref:System.Windows.Application.Startup> à ouvrir uniquement un <xref:System.Windows.Window> ou accédez à un <xref:System.Windows.Controls.Page>, vous pouvez définir le `StartupUri` à la place l’attribut dans le balisage.  
  
 L’exemple suivant montre comment utiliser le <xref:System.Windows.Application.StartupUri%2A> à partir d’une application autonome pour ouvrir une <xref:System.Windows.Window>.  
  
 [!code-xaml[ApplicationManagementOverviewSnippets#OverviewStartupUriMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationManagementOverviewSnippets/CSharp/App.xaml#overviewstartupurimarkup)]  
  
 L’exemple suivant montre comment utiliser <xref:System.Windows.Application.StartupUri%2A> à partir d’une application XBAP pour accéder à un <xref:System.Windows.Controls.Page>.  
  
 [!code-xaml[PageSnippets#XBAPStartupUriMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/PageSnippets/CSharp/App.xaml#xbapstartupurimarkup)]  
  
 Ce balisage a le même effet que le code précédent pour ouvrir une fenêtre.  
  
> [!NOTE]
>  Pour plus d’informations sur la navigation, consultez [vue d’ensemble de la Navigation](navigation-overview.md).  
  
 Vous devez gérer le <xref:System.Windows.Application.Startup> pour ouvrir un <xref:System.Windows.Window> si vous devez instancier à l’aide d’un constructeur non défini par défaut, ou vous devez définir ses propriétés ou vous abonner à ses événements avant de les afficher, ou vous devez traiter tous les arguments de ligne de commande qui a été fourni lorsque l’application a été lancée.  
  
<a name="Processing_Command_Line_Arguments"></a>   
### <a name="processing-command-line-arguments"></a>Traitement des arguments de ligne de commande  
 Dans Windows, les applications autonomes peuvent être lancées à partir d’une invite de commandes ou le bureau. Dans les deux cas, les arguments de ligne de commande peuvent être passés à l’application. L’exemple suivant montre une application qui est lancée avec un seul argument de ligne de commande, « /StartMinimized » :  
  
 `wpfapplication.exe /StartMinimized`  
  
 Pendant l’initialisation d’application, WPF récupère les arguments de ligne de commande du système d’exploitation et les transmet à la <xref:System.Windows.Application.Startup> Gestionnaire d’événements via le <xref:System.Windows.StartupEventArgs.Args%2A> propriété de le <xref:System.Windows.StartupEventArgs> paramètre. Vous pouvez récupérer et stocker les arguments de ligne de commande à l’aide de code similaire au suivant.  
  
 [!code-xaml[ApplicationStartupSnippets#HandleStartupXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationStartupSnippets/CSharp/App.xaml#handlestartupxaml)]  
  
 [!code-csharp[ApplicationStartupSnippets#HandleStartupCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationStartupSnippets/CSharp/App.xaml.cs#handlestartupcodebehind)]
 [!code-vb[ApplicationStartupSnippets#HandleStartupCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationStartupSnippets/visualbasic/application.xaml.vb#handlestartupcodebehind)]  
  
 Le code gère <xref:System.Windows.Application.Startup> pour vérifier si le **/StartMinimized** argument de ligne de commande a été fournie ; dans ce cas, il ouvre la fenêtre principale avec un <xref:System.Windows.WindowState> de <xref:System.Windows.WindowState.Minimized>. Notez que, comme le <xref:System.Windows.Window.WindowState%2A> propriété doit être définie par programme, les principaux <xref:System.Windows.Window> doit être ouverte explicitement dans le code.  
  
 Les applications XBAP ne peut pas récupérer et traiter des arguments de ligne de commande, car elles sont lancées à l’aide du déploiement ClickOnce (consultez [déploiement d’une Application WPF](deploying-a-wpf-application-wpf.md)). En revanche, ils peuvent récupérer et traiter des paramètres de chaîne de requête à partir des URL servant à les lancer.  
  
<a name="Application_Activation_and_Deactivation"></a>   
### <a name="application-activation-and-deactivation"></a>Activation et désactivation d’une application  
 Windows permet aux utilisateurs de basculer entre les applications. La façon la plus courante consiste à utiliser la combinaison de touches ALT+TAB. Peut uniquement être basculer vers une application si elle a un visible <xref:System.Windows.Window> qu’un utilisateur peut sélectionner. Actuellement sélectionné <xref:System.Windows.Window> est la *fenêtre active* (également connu sous le *fenêtre de premier plan*) et est le <xref:System.Windows.Window> qui reçoit l’entrée de l’utilisateur. L’application avec la fenêtre active est la *application active* (ou *application de premier plan*). Une application devient l’application active dans les circonstances suivantes :  
  
- Elle est lancée et affiche un <xref:System.Windows.Window>.  
  
- Un utilisateur y bascule depuis une autre application en sélectionnant un <xref:System.Windows.Window> dans l’application.  
  
 Vous pouvez détecter qu’une application est devenue active en gérant la <xref:System.Windows.Application.Activated?displayProperty=nameWithType> événement.  
  
 De même, une application peut devenir inactive dans les circonstances suivantes :  
  
- Un utilisateur bascule vers une autre application à partir de l’application active.  
  
- L’application s’arrête.  
  
 Vous pouvez détecter qu’une application est devenue inactive en gérant la <xref:System.Windows.Application.Deactivated?displayProperty=nameWithType> événement.  
  
 Le code suivant montre comment gérer les <xref:System.Windows.Application.Activated> et <xref:System.Windows.Application.Deactivated> événements afin de déterminer si une application est active.  
  
 [!code-xaml[ApplicationActivationSnippets#DetectActivationStateXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationActivationSnippets/CSharp/App.xaml#detectactivationstatexaml)]  
  
 [!code-csharp[ApplicationActivationSnippets#DetectActivationStateCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationActivationSnippets/CSharp/App.xaml.cs#detectactivationstatecodebehind)]
 [!code-vb[ApplicationActivationSnippets#DetectActivationStateCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationActivationSnippets/visualbasic/application.xaml.vb#detectactivationstatecodebehind)]  
  
 Un <xref:System.Windows.Window> peut également être activée et désactivée. Pour plus d'informations, consultez <xref:System.Windows.Window.Activated?displayProperty=nameWithType> et <xref:System.Windows.Window.Deactivated?displayProperty=nameWithType>.  
  
> [!NOTE]
>  Ni <xref:System.Windows.Application.Activated?displayProperty=nameWithType> ni <xref:System.Windows.Application.Deactivated?displayProperty=nameWithType> est déclenché pour les applications XBAP.  
  
<a name="Application_Shutdown"></a>   
### <a name="application-shutdown"></a>Arrêt d’une application  
 La durée de vie d’une application s’achève quand elle est arrêtée, ce qui peut se produire pour les raisons suivantes :  
  
- Un utilisateur ferme chaque <xref:System.Windows.Window>.  
  
- Un utilisateur ferme la main <xref:System.Windows.Window>.  
  
- Un utilisateur met fin à la session Windows en se déconnectant ou en cours d’arrêt.  
  
- Une condition spécifique à l’application a été remplie.  
  
 Pour vous aider à gérer l’arrêt de l’application, <xref:System.Windows.Application> fournit le <xref:System.Windows.Application.Shutdown%2A> (méthode), le <xref:System.Windows.Application.ShutdownMode%2A> propriété et le <xref:System.Windows.Application.SessionEnding> et <xref:System.Windows.Application.Exit> événements.  
  
> [!NOTE]
>  <xref:System.Windows.Application.Shutdown%2A> peut uniquement être appelée à partir d’applications qui ont <xref:System.Security.Permissions.UIPermission>. Les applications WPF de Standalone ont toujours cette autorisation. Toutefois, les applications XBAP exécutées dans le bac à sable de sécurité de confiance partielle de la zone Internet ne peuvent pas.  
  
#### <a name="shutdown-mode"></a>Mode d’arrêt  
 La plupart des applications s’arrêtent à la fermeture de toutes les fenêtres ou de la fenêtre principale. Toutefois, d’autres conditions spécifiques à l’application peuvent parfois déterminer l’arrêt d’une application. Vous pouvez spécifier les conditions sous lesquelles votre application s’arrêtera en définissant <xref:System.Windows.Application.ShutdownMode%2A> avec l’une des opérations suivantes <xref:System.Windows.ShutdownMode> valeurs d’énumération :  
  
- <xref:System.Windows.ShutdownMode.OnLastWindowClose>  
  
- <xref:System.Windows.ShutdownMode.OnMainWindowClose>  
  
- <xref:System.Windows.ShutdownMode.OnExplicitShutdown>  
  
 La valeur par défaut <xref:System.Windows.Application.ShutdownMode%2A> est <xref:System.Windows.ShutdownMode.OnLastWindowClose>, ce qui signifie qu’une application s’arrête automatiquement lorsque la dernière fenêtre de l’application est fermée par l’utilisateur. Toutefois, si votre application doit s’arrêter lorsque la fenêtre principale est fermée, WPF arrête automatiquement si vous définissez <xref:System.Windows.Application.ShutdownMode%2A> à <xref:System.Windows.ShutdownMode.OnMainWindowClose>. L'exemple suivant le démontre.  
  
 [!code-xaml[ApplicationShutdownModeSnippets#OnMainWindowCloseMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationShutdownModeSnippets/CS/Page1.xaml#onmainwindowclosemarkup)]  
  
 Lorsque vous avez des conditions d’arrêt spécifiques à l’application, vous définissez <xref:System.Windows.Application.ShutdownMode%2A> à <xref:System.Windows.ShutdownMode.OnExplicitShutdown>. Dans ce cas, il vous incombe d’arrêter une application en appelant explicitement la <xref:System.Windows.Application.Shutdown%2A> méthode ; sinon, votre application continue à s’exécuter même si toutes les fenêtres sont fermées. Notez que <xref:System.Windows.Application.Shutdown%2A> est appelée implicitement quand le <xref:System.Windows.Application.ShutdownMode%2A> est soit <xref:System.Windows.ShutdownMode.OnLastWindowClose> ou <xref:System.Windows.ShutdownMode.OnMainWindowClose>.  
  
> [!NOTE]
>  <xref:System.Windows.Application.ShutdownMode%2A> peut être définie à partir d’une application XBAP, mais il est ignoré ; une application XBAP est toujours arrêté quand il quitte dans un navigateur ou lorsque le navigateur qui héberge l’application XBAP est fermé. Pour plus d’informations, consultez [Vue d’ensemble de la navigation](navigation-overview.md).  
  
#### <a name="session-ending"></a>Fin de session  
 Les conditions d’arrêt décrites par la <xref:System.Windows.Application.ShutdownMode%2A> propriété sont spécifiques à une application. Dans certains cas, pourtant, une application peut s’arrêter à la suite d’une condition externe. La condition externe la plus courante se produit lorsqu’un utilisateur met fin à la session de Windows par les actions suivantes :  
  
- Déconnexion  
  
- Arrêt  
  
- Redémarrage  
  
- Mise en veille prolongée  
  
 Pour détecter si une session Windows se termine, vous pouvez gérer le <xref:System.Windows.Application.SessionEnding> événement, comme illustré dans l’exemple suivant.  
  
 [!code-xaml[ApplicationSessionEndingSnippets#HandlingSessionEndingXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationSessionEndingSnippets/CSharp/App.xaml#handlingsessionendingxaml)]  
  
 [!code-csharp[ApplicationSessionEndingSnippets#HandlingSessionEndingCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationSessionEndingSnippets/CSharp/App.xaml.cs#handlingsessionendingcodebehind)]
 [!code-vb[ApplicationSessionEndingSnippets#HandlingSessionEndingCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationSessionEndingSnippets/visualbasic/application.xaml.vb#handlingsessionendingcodebehind)]  
  
 Dans cet exemple, le code inspecte le <xref:System.Windows.SessionEndingCancelEventArgs.ReasonSessionEnding%2A> propriété afin de déterminer la façon dont la session Windows se termine. Il utilise cette valeur pour afficher un message de confirmation à l’attention de l’utilisateur. Si l’utilisateur ne souhaite pas fin à la session, le code définit <xref:System.ComponentModel.CancelEventArgs.Cancel%2A> à `true` empêcher la session Windows de se terminer.  
  
> [!NOTE]
>  <xref:System.Windows.Application.SessionEnding> n’est pas déclenché pour les applications XBAP.

#### <a name="exit"></a>Exit  
 Quand une application s’arrête, il peut s’avérer nécessaire d’effectuer quelque traitement final, par exemple rendre persistant l’état de l’application. Pour ces situations, vous pouvez gérer le <xref:System.Windows.Application.Exit> événement, comme le `App_Exit` Gestionnaire d’événements s’effectue dans l’exemple suivant. Il est défini comme un gestionnaire d’événements dans le *App.xaml* fichier. Son implémentation est mis en surbrillance dans le *App.xaml.cs* et *Application.xaml.vb* fichiers.
  
[!code-xaml[Defining-the-Exit-event-handler](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTOApplicationModelSnippets/CSharp/App.xaml?highlight=1-7)]  
  
 [!code-csharp[Handling-the-Exit-event](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTOApplicationModelSnippets/CSharp/App.xaml.cs?highlight=42-55)]
 [!code-vb[Handling-the-Exit-event](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOApplicationModelSnippets/visualbasic/application.xaml.vb?highlight=34-45)]  
  
 Pour obtenir un exemple complet, consultez [rendre persistantes et restaurer de portée Application propriétés entre les Sessions de l’Application](persist-and-restore-application-scope-properties.md).  
  
 <xref:System.Windows.Application.Exit> peut être gérée par les applications autonomes et les applications XBAP. Pour les applications XBAP, <xref:System.Windows.Application.Exit> est déclenché dans les circonstances suivantes :  
  
- Une application XBAP est quitté.  
  
- Dans [!INCLUDE[TLA2#tla_ie7](../../../../includes/tla2sharptla-ie7-md.md)], lorsque l’onglet qui héberge l’application XBAP est fermé.  
  
- Le navigateur est fermé.  
  
#### <a name="exit-code"></a>Code de sortie  
 Les applications sont principalement lancées par le système d’exploitation en réponse à une requête de l’utilisateur. Toutefois, une application peut être lancée par une autre application pour effectuer une tâche spécifique. Quand l’application lancée s’arrête, il est possible que l’application de lancement souhaite connaître la condition dans laquelle s’est effectué cet arrêt. Dans ces situations, Windows permet aux applications retourner un code de sortie d’application lors de l’arrêt. Par défaut, les applications WPF retournent une valeur de code de sortie de 0.  
  
> [!NOTE]
>  Lorsque vous déboguez à partir de Visual Studio, le code de sortie d’application s’affiche dans le **sortie** fenêtre lorsque l’application s’arrête, dans un message qui ressemble à ce qui suit :  
>   
>  `The program '[5340] AWPFApp.vshost.exe: Managed' has exited with code 0 (0x0).`  
>   
>  Vous ouvrez le **sortie** fenêtre en cliquant sur **sortie** sur le **vue** menu.  
  
 Pour modifier le code de sortie, vous pouvez appeler la <xref:System.Windows.Application.Shutdown%28System.Int32%29> surcharge, qui accepte un argument entier soit le code de sortie :  
  
 [!code-csharp[ApplicationExitSnippets#AppExitCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationExitSnippets/CSharp/MainWindow.xaml.cs#appexitcode)]
 [!code-vb[ApplicationExitSnippets#AppExitCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationExitSnippets/visualbasic/mainwindow.xaml.vb#appexitcode)]  
  
 Vous pouvez détecter la valeur du code de sortie et modifier, en gérant la <xref:System.Windows.Application.Exit> événement. Le <xref:System.Windows.Application.Exit> est transmis au gestionnaire d’événements un <xref:System.Windows.ExitEventArgs> qui fournit l’accès au code de sortie avec le <xref:System.Windows.ExitEventArgs.ApplicationExitCode%2A> propriété. Pour plus d'informations, consultez <xref:System.Windows.Application.Exit>.  
  
> [!NOTE]
>  Vous pouvez définir le code de sortie dans les applications autonomes et les applications XBAP. Toutefois, la valeur de code de sortie est ignorée pour les applications XBAP.  
  
<a name="Unhandled_Exceptions"></a>   
### <a name="unhandled-exceptions"></a>Exceptions non gérées  
 Il peut parfois arriver qu’une application s’arrête anormalement, par exemple en cas d’exception inattendue. Dans ce cas, il est possible qu’elle n’ait pas le code nécessaire à la détection et au traitement de l’exception. Ce type d’exception est une exception non gérée ; une notification similaire à celle illustrée dans la figure ci-dessous s’affiche avant la fermeture de l’application.  
  
 ![Capture d’écran montrant une notification d’exception non gérée.](./media/application-management-overview/unhandled-exception-notification.png)  
  
 Du point de vue de l’expérience utilisateur, il est préférable pour une application d’éviter ce comportement par défaut en effectuant certaines ou l’ensemble des opérations suivantes :  
  
- Affichage d’informations conviviales.  
  
- Tentative de maintenir une application en cours d’exécution.  
  
- Enregistrement détaillé, informations sur l’exception de la convivialité pour les développeurs dans le journal des événements Windows.  
  
 Implémentation de cette prise en charge dépend en mesure de détecter les exceptions non gérées, qui est ce que le <xref:System.Windows.Application.DispatcherUnhandledException> événement est déclenché pour.  
  
[!code-xaml[detecting-unhandled-exceptions](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationDispatcherUnhandledExceptionSnippets/CSharp/App.xaml#handledispatcherunhandledexceptionxaml)]  
  
[!code-csharp[code-to-detect-unhandled-exceptions](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationDispatcherUnhandledExceptionSnippets/CSharp/App.xaml.cs)]
[!code-vb[code-to-detect-unhandled-exceptions](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationDispatcherUnhandledExceptionSnippets/visualbasic/application.xaml.vb)]  
  
 Le <xref:System.Windows.Application.DispatcherUnhandledException> est transmis au gestionnaire d’événements un <xref:System.Windows.Threading.DispatcherUnhandledExceptionEventArgs> paramètre qui contient des informations contextuelles concernant l’exception non gérée, y compris l’exception proprement dite (<xref:System.Windows.Threading.DispatcherUnhandledExceptionEventArgs.Exception%2A?displayProperty=nameWithType>). Vous pouvez utiliser ces informations pour déterminer comment gérer l’exception.  
  
 Lorsque vous gérez <xref:System.Windows.Application.DispatcherUnhandledException>, vous devez définir le <xref:System.Windows.Threading.DispatcherUnhandledExceptionEventArgs.Handled%2A?displayProperty=nameWithType> propriété `true`; sinon, WPF toujours considère que l’exception non gérée et rétablit le comportement par défaut décrit précédemment. Si une exception non gérée est levée et la valeur la <xref:System.Windows.Application.DispatcherUnhandledException> événement n’est pas géré, ou l’événement est géré et <xref:System.Windows.Threading.DispatcherUnhandledExceptionEventArgs.Handled%2A> a la valeur `false`, l’application s’arrête immédiatement. En outre, aucun autre <xref:System.Windows.Application> événements sont déclenchés. Par conséquent, vous devez gérer <xref:System.Windows.Application.DispatcherUnhandledException> si votre application comporte du code qui doit s’exécuter avant l’arrêt de l’application.  
  
 Bien qu’une application puisse s’arrêter à la suite d’une exception non gérée, elle s’arrête habituellement en réponse à une requête de l’utilisateur, comme décrit dans la section suivante.  
  
<a name="Application_Lifetime_Events"></a>   
### <a name="application-lifetime-events"></a>Événements de durée de vie de l'application  
 Les applications autonomes et des applications XBAP n’ont pas exactement les mêmes durées de vie. La figure suivante illustre les principaux événements de la durée de vie d’une application autonome et indique l’ordre dans lequel ils sont déclenchés.  
  
 ![Application autonome &#45; Événements d’objets d’application](./media/applicationmodeloverview-applicationobjectevents.png "ApplicationModelOverview_ApplicationObjectEvents")  
  
 De même, la figure suivante illustre les principaux événements de la durée de vie d’une application XBAP et indique l’ordre dans lequel ils sont déclenchés.  
  
 ![XBAP &#45; Événements d’objets d’application](./media/applicationmodeloverview-applicationobjectevents-xbap.png "ApplicationModelOverview_ApplicationObjectEvents_xbap")  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Application>
- [Vue d'ensemble des fenêtres WPF](wpf-windows-overview.md)
- [Vue d’ensemble de la navigation](navigation-overview.md)
- [Fichiers de ressources, de contenu et de données d’une application WPF](wpf-application-resource-content-and-data-files.md)
- [URI à en-tête pack dans WPF](pack-uris-in-wpf.md)
- [Modèle d’application : Rubriques de procédures](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms749013(v=vs.100))
- [Développement de l’application](index.md)
