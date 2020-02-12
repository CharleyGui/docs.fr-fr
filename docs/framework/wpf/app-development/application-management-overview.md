---
title: Vue d'ensemble de la gestion d'applications
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- application management [WPF]
ms.assetid: 32b1c054-5aca-423b-b4b5-ed8dc4dc637d
ms.openlocfilehash: dbc5bd9f699415fb47f21c6a45b1c58cfcff0f33
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/11/2020
ms.locfileid: "77124518"
---
# <a name="application-management-overview"></a>Vue d'ensemble de la gestion d'applications

Toutes les applications tendent à partager un jeu de fonctionnalités commun qui s’applique à l’implémentation et à la gestion. Cette rubrique fournit une vue d’ensemble des fonctionnalités de la classe <xref:System.Windows.Application> pour la création et la gestion d’applications.

## <a name="the-application-class"></a>Classe Application

Dans WPF, les fonctionnalités communes de portée application sont encapsulées dans la classe <xref:System.Windows.Application>. La classe <xref:System.Windows.Application> comprend les fonctionnalités suivantes :

- Suivi et interaction avec la durée de vie d’une application.

- Récupération et traitement des paramètres de ligne de commande.

- Détection et traitement des exceptions non gérées.

- Partage des propriétés de portée application et des ressources.

- Gestion des fenêtres dans des applications autonomes.

- Suivi et gestion de la navigation.

<a name="The_Application_Class"></a>

## <a name="how-to-perform-common-tasks-using-the-application-class"></a>Comment effectuer des tâches courantes à l’aide de la classe Application

Si vous n’êtes pas intéressé par tous les détails de la classe <xref:System.Windows.Application>, le tableau suivant répertorie certaines des tâches courantes pour <xref:System.Windows.Application> et comment les accomplir. En affichant l’API et les rubriques connexes, vous pouvez obtenir davantage d’informations et des exemples de code.

|Tâche|Approche|
|----------|--------------|
|Obtenir un objet qui représente l’application actuelle|Utilisez la propriété <xref:System.Windows.Application.Current%2A?displayProperty=nameWithType>.|
|Ajouter un écran de démarrage à une application|Consultez [Ajouter un écran de démarrage à une application WPF](how-to-add-a-splash-screen-to-a-wpf-application.md).|
|Démarrer une application|Utilisez la méthode <xref:System.Windows.Application.Run%2A?displayProperty=nameWithType>.|
|Arrêter une application|Utilisez la méthode <xref:System.Windows.Application.Shutdown%2A> de l’objet <xref:System.Windows.Application.Current%2A?displayProperty=nameWithType>.|
|Obtenir des arguments de la ligne de commande|Gérez l’événement <xref:System.Windows.Application.Startup?displayProperty=nameWithType> et utilisez la propriété <xref:System.Windows.StartupEventArgs.Args%2A?displayProperty=nameWithType>. Pour obtenir un exemple, consultez l’événement <xref:System.Windows.Application.Startup?displayProperty=nameWithType>.|
|Obtenir et définir le code de sortie d’application|Définissez la propriété <xref:System.Windows.ExitEventArgs.ApplicationExitCode%2A?displayProperty=nameWithType> dans le gestionnaire d’événements <xref:System.Windows.Application.Exit?displayProperty=nameWithType> ou appelez la méthode <xref:System.Windows.Application.Shutdown%2A> et transmettez un entier.|
|Détecter et traiter des exceptions non gérées|Gérez l’événement <xref:System.Windows.Application.DispatcherUnhandledException>.|
|Obtenir et définir des ressources de portée application|Utilisez la propriété <xref:System.Windows.Application.Resources%2A?displayProperty=nameWithType>.|
|Utiliser un dictionnaire de ressources de portée application|Consultez [utiliser un dictionnaire de ressources de portée application](how-to-use-an-application-scope-resource-dictionary.md).|
|Obtenir et définir les propriétés de portée application|Utilisez la propriété <xref:System.Windows.Application.Properties%2A?displayProperty=nameWithType>.|
|Obtenir et enregistrer l’état d’une application|Consultez [conserver et restaurer les propriétés de portée application d’une session d’application à l’autre](persist-and-restore-application-scope-properties.md).|
|Gérer les fichiers de données de non-code, dont les fichiers de ressources, les fichiers de contenu et les fichiers du site d’origine.|Consultez [fichiers de ressources, de contenu et de données d’une application WPF](wpf-application-resource-content-and-data-files.md).|
|Gérer des fenêtres dans des applications autonomes|Consultez [Vue d’ensemble des fenêtres WPF](wpf-windows-overview.md).|
|Suivre et gérer la navigation|Consultez [vue d’ensemble](navigation-overview.md)de la navigation.|

<a name="The_Application_Definition"></a>

## <a name="the-application-definition"></a>Définition d’application

Pour utiliser les fonctionnalités de la classe <xref:System.Windows.Application>, vous devez implémenter une définition d’application. Une définition d’application WPF est une classe qui dérive de <xref:System.Windows.Application> et qui est configurée avec un paramètre MSBuild spécial.

### <a name="implementing-an-application-definition"></a>Implémentation d’une définition d’application

Une définition d’application WPF standard est implémentée à l’aide du balisage et du code-behind. Vous pouvez ainsi utiliser le balisage pour définir de façon déclarative les propriétés d’une application et les ressources ainsi que pour inscrire des événements, tout en gérant les événements et en implémentant le comportement spécifique à l’application dans un fichier code-behind.

L’exemple suivant montre comment implémenter une définition d’application à l’aide de balisage et de code-behind :

[!code-xaml[ApplicationSnippets#ApplicationXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationSnippets/CSharp/App.xaml#applicationxaml)]

[!code-csharp[ApplicationSnippets#ApplicationCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationSnippets/CSharp/App.xaml.cs#applicationcodebehind)]
[!code-vb[ApplicationSnippets#ApplicationCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationSnippets/visualbasic/application.xaml.vb#applicationcodebehind)]

Pour permettre l’interopérabilité d’un fichier de balisage et d’un fichier code-behind, les conditions suivantes doivent être satisfaites :

- Dans le balisage, l’élément `Application` doit inclure l’attribut `x:Class`. Lorsque l’application est générée, l’existence d' `x:Class` dans le fichier de balisage amène MSBuild à créer une classe `partial` qui dérive de <xref:System.Windows.Application> et qui porte le nom spécifié par l’attribut `x:Class`. Cela nécessite l’ajout d’une déclaration d’espace de noms XML pour le schéma XAML (`xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"`).

- Dans le code-behind, la classe doit être une classe `partial` portant le même nom que celui spécifié par l’attribut `x:Class` dans le balisage et doit dériver de <xref:System.Windows.Application>. Cela permet au fichier code-behind d’être associé à la classe `partial` générée pour le fichier de balisage quand l’application est générée (consultez [génération d’une application WPF](building-a-wpf-application-wpf.md)).

> [!NOTE]
> Quand vous créez un projet d’application WPF ou un projet d’application de navigateur WPF à l’aide de Visual Studio, une définition d’application est incluse par défaut et est définie à l’aide du balisage et du code-behind.

Ce code est le minimum requis pour implémenter une définition d’application. Toutefois, une configuration MSBuild supplémentaire doit être apportée à la définition de l’application avant de générer et d’exécuter l’application.

### <a name="configuring-the-application-definition-for-msbuild"></a>Configuration de la définition d’application pour MSBuild

Les applications autonomes et les applications de navigateur XAML (XBAP) requièrent l’implémentation d’un certain niveau d’infrastructure pour pouvoir s’exécuter. La partie la plus importante de cette infrastructure est le point d’entrée. Quand une application est lancée par un utilisateur, le système d’exploitation appelle le point d’entrée, qui est une fonction connue pour démarrer les applications.

En règle générale, les développeurs ont toujours dû écrire eux-mêmes une partie ou l’intégralité de ce code, selon la technologie employée. Toutefois, WPF génère ce code pour vous lorsque le fichier de balisage de votre définition d’application est configuré en tant qu’élément de `ApplicationDefinition` MSBuild, comme indiqué dans le fichier projet MSBuild suivant :

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

Étant donné que le fichier code-behind contient du code, il est marqué comme un élément `Compile` MSBuild, comme c’est normal.

L’application de ces configurations MSBuild aux fichiers de balisage et code-behind d’une définition d’application amène MSBuild à générer du code similaire à ce qui suit :

[!code-csharp[auto-generated-code](~/samples/snippets/csharp/VS_Snippets_Wpf/AppDefAugSnippets/CSharp/App.cs)]
[!code-vb[auto-generated-code](~/samples/snippets/visualbasic/VS_Snippets_Wpf/AppDefAugSnippets/VisualBasic/App.vb)]

Le code résultant augmente la définition de votre application avec un code d’infrastructure supplémentaire, qui comprend la méthode de point d’entrée `Main`. L’attribut <xref:System.STAThreadAttribute> est appliqué à la méthode `Main` pour indiquer que le thread d’interface utilisateur principal de l’application WPF est un thread STA, ce qui est requis pour les applications WPF. Quand elle est appelée, `Main` crée une nouvelle instance de `App` avant d’appeler la méthode `InitializeComponent` pour inscrire les événements et définir les propriétés qui sont implémentées dans le balisage. Étant donné que `InitializeComponent` est généré pour vous, vous n’avez pas besoin d’appeler explicitement `InitializeComponent` à partir d’une définition d’application comme vous le feriez pour des implémentations de <xref:System.Windows.Controls.Page> et de <xref:System.Windows.Window>. Enfin, la méthode <xref:System.Windows.Application.Run%2A> est appelée pour démarrer l’application.

<a name="Getting_the_Current_Application"></a>

## <a name="getting-the-current-application"></a>Obtention de l’application actuelle

Étant donné que les fonctionnalités de la classe <xref:System.Windows.Application> sont partagées entre une application, il ne peut y avoir qu’une seule instance de la classe <xref:System.Windows.Application> par <xref:System.AppDomain>. Pour appliquer cela, la classe <xref:System.Windows.Application> est implémentée en tant que classe singleton (consultez [Implementing Singleton in C# ](https://docs.microsoft.com/previous-versions/msp-n-p/ff650316(v=pandp.10))), qui crée une seule instance de elle-même et fournit un accès partagé à celle-ci avec la propriété `static`<xref:System.Windows.Application.Current%2A>.

Le code suivant montre comment acquérir une référence à l’objet <xref:System.Windows.Application> pour le <xref:System.AppDomain>actuel.

[!code-csharp[ApplicationManagementOverviewSnippets#GetCurrentAppCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationManagementOverviewSnippets/CSharp/MainWindow.xaml.cs#getcurrentappcode)]
[!code-vb[ApplicationManagementOverviewSnippets#GetCurrentAppCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationManagementOverviewSnippets/VisualBasic/MainWindow.xaml.vb#getcurrentappcode)]

<xref:System.Windows.Application.Current%2A> retourne une référence à une instance de la classe <xref:System.Windows.Application>. Si vous souhaitez une référence à votre classe dérivée <xref:System.Windows.Application> vous devez effectuer un cast de la valeur de la propriété <xref:System.Windows.Application.Current%2A>, comme indiqué dans l’exemple suivant.

[!code-csharp[ApplicationManagementOverviewSnippets#GetSTCurrentAppCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationManagementOverviewSnippets/CSharp/MainWindow.xaml.cs#getstcurrentappcode)]
[!code-vb[ApplicationManagementOverviewSnippets#GetSTCurrentAppCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationManagementOverviewSnippets/VisualBasic/MainWindow.xaml.vb#getstcurrentappcode)]

Vous pouvez inspecter la valeur de <xref:System.Windows.Application.Current%2A> à n’importe quel stade de la durée de vie d’un objet <xref:System.Windows.Application>. Toutefois, vous devez être vigilant. Après l’instanciation de la classe <xref:System.Windows.Application>, il existe un point pendant lequel l’état de l’objet <xref:System.Windows.Application> est incohérent. Au cours de cette période, <xref:System.Windows.Application> effectue les différentes tâches d’initialisation requises par votre code pour s’exécuter, y compris l’établissement de l’infrastructure de l’application, la définition des propriétés et l’inscription des événements. Si vous essayez d’utiliser l’objet <xref:System.Windows.Application> pendant cette période, votre code peut avoir des résultats inattendus, en particulier s’il dépend des différentes propriétés de <xref:System.Windows.Application> définies.

Lorsque <xref:System.Windows.Application> termine son travail d’initialisation, sa durée de vie commence véritablement.

<a name="Application_Lifetime"></a>

## <a name="application-lifetime"></a>Durée de vie d’une application

La durée de vie d’une application WPF est marquée par plusieurs événements déclenchés par <xref:System.Windows.Application> pour vous avertir lorsque votre application a démarré, qu’elle a été activée et désactivée et a été arrêtée.

<a name="Splash_Screen"></a>

### <a name="splash-screen"></a>Écran de démarrage

À partir de la .NET Framework 3,5 SP1, vous pouvez spécifier une image à utiliser dans une fenêtre de démarrage ou un *écran*de démarrage. La classe <xref:System.Windows.SplashScreen> permet d’afficher facilement une fenêtre de démarrage pendant le chargement de votre application. La fenêtre de <xref:System.Windows.SplashScreen> est créée et affichée avant l’appel de <xref:System.Windows.Application.Run%2A>. Pour plus d’informations, consultez [temps de démarrage](../advanced/application-startup-time.md) de l’application et [Ajouter un écran de démarrage à une application WPF](how-to-add-a-splash-screen-to-a-wpf-application.md).

<a name="Starting_an_Application"></a>

### <a name="starting-an-application"></a>Démarrage d’une application

Une fois que <xref:System.Windows.Application.Run%2A> est appelé et que l’application est initialisée, l’application est prête à s’exécuter. Ce moment est signifié lorsque l’événement <xref:System.Windows.Application.Startup> est déclenché :

[!code-csharp[Startup-event](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationStartupSnippets/CSharp/App.xaml.cs?range=3-11,31-33)]
[!code-vb[Startup-event](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationStartupSnippets/visualbasic/application.xaml.vb?range=5-11,30-32)]

À ce stade de la durée de vie d’une application, la chose la plus courante est d’afficher une interface utilisateur.

<a name="Showing_a_User_Interface"></a>

### <a name="showing-a-user-interface"></a>Affichage d’une interface utilisateur

La plupart des applications Windows autonomes ouvrent un <xref:System.Windows.Window> lorsqu’elles commencent à s’exécuter. Le gestionnaire d’événements <xref:System.Windows.Application.Startup> est un emplacement à partir duquel vous pouvez effectuer cette opération, comme le montre le code suivant.

[!code-xaml[AppShowWindowHardSnippets#StartupEventMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/AppShowWindowHardSnippets/CSharp/App.xaml#startupeventmarkup)]

[!code-csharp[AppShowWindowHardSnippets#StartupEventCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/AppShowWindowHardSnippets/CSharp/App.xaml.cs#startupeventcodebehind)]
[!code-vb[AppShowWindowHardSnippets#StartupEventCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/AppShowWindowHardSnippets/VisualBasic/Application.xaml.vb#startupeventcodebehind)]

> [!NOTE]
> La première <xref:System.Windows.Window> à instancier dans une application autonome devient la fenêtre d’application principale par défaut. Cet objet <xref:System.Windows.Window> est référencé par la propriété <xref:System.Windows.Application.MainWindow%2A?displayProperty=nameWithType>. La valeur de la propriété <xref:System.Windows.Application.MainWindow%2A> peut être modifiée par programme si une autre fenêtre que la première <xref:System.Windows.Window> instanciée doit être la fenêtre principale.

Quand un XBAP démarre pour la première fois, il accède très probablement à une <xref:System.Windows.Controls.Page>. Ceci est illustré dans le code suivant.

[!code-xaml[XBAPAppStartupSnippets#StartupXBAPMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/XBAPAppStartupSnippets/CSharp/App.xaml#startupxbapmarkup)]

[!code-csharp[XBAPAppStartupSnippets#StartupXBAPCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/XBAPAppStartupSnippets/CSharp/App.xaml.cs#startupxbapcodebehind)]
[!code-vb[XBAPAppStartupSnippets#StartupXBAPCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/XBAPAppStartupSnippets/VisualBasic/Application.xaml.vb#startupxbapcodebehind)]

Si vous gérez <xref:System.Windows.Application.Startup> pour ouvrir uniquement un <xref:System.Windows.Window> ou accéder à un <xref:System.Windows.Controls.Page>, vous pouvez définir l’attribut `StartupUri` dans le balisage à la place.

L’exemple suivant montre comment utiliser l' <xref:System.Windows.Application.StartupUri%2A> à partir d’une application autonome pour ouvrir une <xref:System.Windows.Window>.

[!code-xaml[ApplicationManagementOverviewSnippets#OverviewStartupUriMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationManagementOverviewSnippets/CSharp/App.xaml#overviewstartupurimarkup)]

L’exemple suivant montre comment utiliser <xref:System.Windows.Application.StartupUri%2A> à partir d’une application XBAP pour accéder à une <xref:System.Windows.Controls.Page>.

[!code-xaml[PageSnippets#XBAPStartupUriMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/PageSnippets/CSharp/App.xaml#xbapstartupurimarkup)]

Ce balisage a le même effet que le code précédent pour ouvrir une fenêtre.

> [!NOTE]
> Pour plus d’informations sur la navigation, consultez [vue d’ensemble](navigation-overview.md)de la navigation.

Vous devez gérer l’événement <xref:System.Windows.Application.Startup> pour ouvrir une <xref:System.Windows.Window> si vous devez l’instancier à l’aide d’un constructeur sans paramètre, ou si vous devez définir ses propriétés ou vous abonner à ses événements avant de l’afficher, ou vous devez traiter les arguments de ligne de commande fournis lors du lancement de l’application.

<a name="Processing_Command_Line_Arguments"></a>

### <a name="processing-command-line-arguments"></a>Traitement des arguments de ligne de commande

Dans Windows, les applications autonomes peuvent être lancées à partir d’une invite de commandes ou du bureau. Dans les deux cas, les arguments de ligne de commande peuvent être passés à l’application. L’exemple suivant montre une application qui est lancée avec un seul argument de ligne de commande, « /StartMinimized » :

`wpfapplication.exe /StartMinimized`

Pendant l’initialisation de l’application, WPF récupère les arguments de ligne de commande du système d’exploitation et les transmet au gestionnaire d’événements <xref:System.Windows.Application.Startup> via la propriété <xref:System.Windows.StartupEventArgs.Args%2A> du paramètre <xref:System.Windows.StartupEventArgs>. Vous pouvez récupérer et stocker les arguments de ligne de commande à l’aide de code similaire au suivant.

[!code-xaml[ApplicationStartupSnippets#HandleStartupXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationStartupSnippets/CSharp/App.xaml#handlestartupxaml)]

[!code-csharp[ApplicationStartupSnippets#HandleStartupCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationStartupSnippets/CSharp/App.xaml.cs#handlestartupcodebehind)]
[!code-vb[ApplicationStartupSnippets#HandleStartupCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationStartupSnippets/visualbasic/application.xaml.vb#handlestartupcodebehind)]

Le code gère <xref:System.Windows.Application.Startup> pour vérifier si l’argument de ligne de commande **/StartMinimized** a été fourni ; Si c’est le cas, elle ouvre la fenêtre principale avec un <xref:System.Windows.WindowState> de <xref:System.Windows.WindowState.Minimized>. Notez que, étant donné que la propriété <xref:System.Windows.Window.WindowState%2A> doit être définie par programmation, la <xref:System.Windows.Window> principale doit être ouverte explicitement dans le code.

Les XBAP ne peuvent pas récupérer et traiter les arguments de ligne de commande, car ils sont lancés à l’aide du déploiement ClickOnce (consultez [déploiement d’une application WPF](deploying-a-wpf-application-wpf.md)). En revanche, ils peuvent récupérer et traiter des paramètres de chaîne de requête à partir des URL servant à les lancer.

<a name="Application_Activation_and_Deactivation"></a>

### <a name="application-activation-and-deactivation"></a>Activation et désactivation d’une application

Windows permet aux utilisateurs de basculer entre les applications. La façon la plus courante consiste à utiliser la combinaison de touches ALT+TAB. Une application ne peut être basculée que si elle possède un <xref:System.Windows.Window> visible qu’un utilisateur peut sélectionner. La <xref:System.Windows.Window> actuellement sélectionnée est la *fenêtre active* (également appelée fenêtre de *premier plan*) et est la <xref:System.Windows.Window> qui reçoit l’entrée d’utilisateur. L’application avec la fenêtre active est l’application *active* (ou *application de premier plan*). Une application devient l’application active dans les circonstances suivantes :

- Elle est lancée et affiche un <xref:System.Windows.Window>.

- Un utilisateur passe d’une autre application en sélectionnant un <xref:System.Windows.Window> dans l’application.

Vous pouvez détecter qu’une application devient active en gérant l’événement <xref:System.Windows.Application.Activated?displayProperty=nameWithType>.

De même, une application peut devenir inactive dans les circonstances suivantes :

- Un utilisateur bascule vers une autre application à partir de l’application active.

- L’application s’arrête.

Vous pouvez détecter qu’une application devient inactive en gérant l’événement <xref:System.Windows.Application.Deactivated?displayProperty=nameWithType>.

Le code suivant montre comment gérer les événements <xref:System.Windows.Application.Activated> et <xref:System.Windows.Application.Deactivated> pour déterminer si une application est active.

[!code-xaml[ApplicationActivationSnippets#DetectActivationStateXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationActivationSnippets/CSharp/App.xaml#detectactivationstatexaml)]

[!code-csharp[ApplicationActivationSnippets#DetectActivationStateCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationActivationSnippets/CSharp/App.xaml.cs#detectactivationstatecodebehind)]
[!code-vb[ApplicationActivationSnippets#DetectActivationStateCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationActivationSnippets/visualbasic/application.xaml.vb#detectactivationstatecodebehind)]

Une <xref:System.Windows.Window> peut également être activée et désactivée. Pour plus d'informations, consultez <xref:System.Windows.Window.Activated?displayProperty=nameWithType> et <xref:System.Windows.Window.Deactivated?displayProperty=nameWithType>.

> [!NOTE]
> Ni <xref:System.Windows.Application.Activated?displayProperty=nameWithType> ni <xref:System.Windows.Application.Deactivated?displayProperty=nameWithType> ne sont déclenchés pour les applications XBAP.

<a name="Application_Shutdown"></a>

### <a name="application-shutdown"></a>Arrêt d’une application

La durée de vie d’une application s’achève quand elle est arrêtée, ce qui peut se produire pour les raisons suivantes :

- Un utilisateur ferme chaque <xref:System.Windows.Window>.

- Un utilisateur ferme le <xref:System.Windows.Window>principal.

- Un utilisateur met fin à la session Windows en se déconnectant ou en arrêtant.

- Une condition spécifique à l’application a été remplie.

Pour vous aider à gérer l’arrêt de l’application, <xref:System.Windows.Application> fournit la méthode <xref:System.Windows.Application.Shutdown%2A>, la propriété <xref:System.Windows.Application.ShutdownMode%2A> et les événements <xref:System.Windows.Application.SessionEnding> et <xref:System.Windows.Application.Exit>.

> [!NOTE]
> <xref:System.Windows.Application.Shutdown%2A> ne peut être appelé qu’à partir d’applications qui ont des <xref:System.Security.Permissions.UIPermission>. Les applications WPF autonomes disposent toujours de cette autorisation. Toutefois, les applications XBAP qui s’exécutent dans le bac à sable de sécurité de confiance partielle de la zone Internet ne le font pas.

#### <a name="shutdown-mode"></a>Mode d’arrêt

La plupart des applications s’arrêtent à la fermeture de toutes les fenêtres ou de la fenêtre principale. Toutefois, d’autres conditions spécifiques à l’application peuvent parfois déterminer l’arrêt d’une application. Vous pouvez spécifier les conditions dans lesquelles votre application s’arrêtera en définissant <xref:System.Windows.Application.ShutdownMode%2A> avec l’une des valeurs d’énumération <xref:System.Windows.ShutdownMode> suivantes :

- <xref:System.Windows.ShutdownMode.OnLastWindowClose>

- <xref:System.Windows.ShutdownMode.OnMainWindowClose>

- <xref:System.Windows.ShutdownMode.OnExplicitShutdown>

La valeur par défaut de <xref:System.Windows.Application.ShutdownMode%2A> est <xref:System.Windows.ShutdownMode.OnLastWindowClose>, ce qui signifie qu’une application s’arrête automatiquement lorsque la dernière fenêtre de l’application est fermée par l’utilisateur. Toutefois, si votre application doit être arrêtée lorsque la fenêtre principale est fermée, WPF le fait automatiquement si vous définissez <xref:System.Windows.Application.ShutdownMode%2A> sur <xref:System.Windows.ShutdownMode.OnMainWindowClose>. Cela est illustré par l'exemple suivant.

[!code-xaml[ApplicationShutdownModeSnippets#OnMainWindowCloseMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationShutdownModeSnippets/CS/Page1.xaml#onmainwindowclosemarkup)]

Lorsque vous avez des conditions d’arrêt spécifiques à l’application, vous définissez <xref:System.Windows.Application.ShutdownMode%2A> sur <xref:System.Windows.ShutdownMode.OnExplicitShutdown>. Dans ce cas, il vous incombe d’arrêter une application en appelant explicitement la méthode <xref:System.Windows.Application.Shutdown%2A> ; dans le cas contraire, votre application continuera de s’exécuter même si toutes les fenêtres sont fermées. Notez que <xref:System.Windows.Application.Shutdown%2A> est appelé implicitement lorsque la <xref:System.Windows.Application.ShutdownMode%2A> est <xref:System.Windows.ShutdownMode.OnLastWindowClose> ou <xref:System.Windows.ShutdownMode.OnMainWindowClose>.

> [!NOTE]
> <xref:System.Windows.Application.ShutdownMode%2A> peut être définie à partir d’une application XBAP, mais elle est ignorée ; une application XBAP est toujours arrêtée lorsqu’elle est quittée dans un navigateur ou lorsque le navigateur qui héberge l’application XBAP est fermé. Pour plus d’informations, consultez [Vue d’ensemble de la navigation](navigation-overview.md).

#### <a name="session-ending"></a>Fin de session

Les conditions d’arrêt décrites par la propriété <xref:System.Windows.Application.ShutdownMode%2A> sont spécifiques à une application. Dans certains cas, pourtant, une application peut s’arrêter à la suite d’une condition externe. La condition externe la plus courante se produit lorsqu’un utilisateur met fin à la session Windows par les actions suivantes :

- Déconnexion

- Arrêt

- Redémarrage

- Mise en veille prolongée

Pour détecter à quel moment une session Windows se termine, vous pouvez gérer l’événement <xref:System.Windows.Application.SessionEnding>, comme illustré dans l’exemple suivant.

[!code-xaml[ApplicationSessionEndingSnippets#HandlingSessionEndingXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationSessionEndingSnippets/CSharp/App.xaml#handlingsessionendingxaml)]

[!code-csharp[ApplicationSessionEndingSnippets#HandlingSessionEndingCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationSessionEndingSnippets/CSharp/App.xaml.cs#handlingsessionendingcodebehind)]
[!code-vb[ApplicationSessionEndingSnippets#HandlingSessionEndingCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationSessionEndingSnippets/visualbasic/application.xaml.vb#handlingsessionendingcodebehind)]

Dans cet exemple, le code inspecte la propriété <xref:System.Windows.SessionEndingCancelEventArgs.ReasonSessionEnding%2A> pour déterminer la façon dont la session Windows se termine. Il utilise cette valeur pour afficher un message de confirmation à l’attention de l’utilisateur. Si l’utilisateur ne souhaite pas que la session se termine, le code définit <xref:System.ComponentModel.CancelEventArgs.Cancel%2A> sur `true` pour empêcher la fin de la session Windows.

> [!NOTE]
> <xref:System.Windows.Application.SessionEnding> n’est pas déclenchée pour les applications XBAP.

#### <a name="exit"></a>Quitter

Quand une application s’arrête, il peut s’avérer nécessaire d’effectuer quelque traitement final, par exemple rendre persistant l’état de l’application. Dans ce cas, vous pouvez gérer l’événement <xref:System.Windows.Application.Exit>, comme le montre le gestionnaire d’événements `App_Exit` dans l’exemple suivant. Il est défini en tant que gestionnaire d’événements dans le fichier *app. Xaml* . Son implémentation est mise en surbrillance dans les fichiers *app.Xaml.cs* et *application. Xaml. vb* .

[!code-xaml[Defining-the-Exit-event-handler](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTOApplicationModelSnippets/CSharp/App.xaml?highlight=1-7)]

[!code-csharp[Handling-the-Exit-event](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTOApplicationModelSnippets/CSharp/App.xaml.cs?highlight=42-55)]
[!code-vb[Handling-the-Exit-event](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOApplicationModelSnippets/visualbasic/application.xaml.vb?highlight=34-45)]

Pour obtenir un exemple complet, consultez [rendre persistantes et restaurer les propriétés de portée application d’une session d’application à l’autre](persist-and-restore-application-scope-properties.md).

les <xref:System.Windows.Application.Exit> peuvent être gérées par des applications autonomes et des applications XBAP. Pour les applications XBAP, <xref:System.Windows.Application.Exit> est déclenché dans les circonstances suivantes :

- Une application XBAP est quittée.

- Dans Internet Explorer, lorsque l’onglet qui héberge le XBAP est fermé.

- Le navigateur est fermé.

#### <a name="exit-code"></a>Code de sortie

Les applications sont principalement lancées par le système d’exploitation en réponse à une requête de l’utilisateur. Toutefois, une application peut être lancée par une autre application pour effectuer une tâche spécifique. Quand l’application lancée s’arrête, il est possible que l’application de lancement souhaite connaître la condition dans laquelle s’est effectué cet arrêt. Dans ces situations, Windows permet aux applications de retourner un code de sortie d’application lors de l’arrêt. Par défaut, les applications WPF retournent une valeur de code de sortie de 0.

> [!NOTE]
> Quand vous déboguez à partir de Visual Studio, le code de sortie de l’application s’affiche dans la fenêtre **sortie** lorsque l’application s’arrête, dans un message similaire à ce qui suit :
>
> `The program '[5340] AWPFApp.vshost.exe: Managed' has exited with code 0 (0x0).`
>
> Pour ouvrir la fenêtre **sortie** , cliquez sur **sortie** dans le menu **affichage** .

Pour modifier le code de sortie, vous pouvez appeler la surcharge <xref:System.Windows.Application.Shutdown%28System.Int32%29>, qui accepte un argument entier comme code de sortie :

[!code-csharp[ApplicationExitSnippets#AppExitCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationExitSnippets/CSharp/MainWindow.xaml.cs#appexitcode)]
[!code-vb[ApplicationExitSnippets#AppExitCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationExitSnippets/visualbasic/mainwindow.xaml.vb#appexitcode)]

Vous pouvez détecter la valeur du code de sortie et la modifier, en gérant l’événement <xref:System.Windows.Application.Exit>. Un <xref:System.Windows.ExitEventArgs> qui fournit l’accès au code de sortie avec la propriété <xref:System.Windows.ExitEventArgs.ApplicationExitCode%2A> est passé au gestionnaire d’événements <xref:System.Windows.Application.Exit>. Pour plus d’informations, consultez <xref:System.Windows.Application.Exit>.

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

L’implémentation de cette prise en charge dépend de la capacité à détecter les exceptions non gérées, à savoir le déclenchement de l’événement <xref:System.Windows.Application.DispatcherUnhandledException>.

[!code-xaml[detecting-unhandled-exceptions](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationDispatcherUnhandledExceptionSnippets/CSharp/App.xaml#handledispatcherunhandledexceptionxaml)]

[!code-csharp[code-to-detect-unhandled-exceptions](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationDispatcherUnhandledExceptionSnippets/CSharp/App.xaml.cs)]
[!code-vb[code-to-detect-unhandled-exceptions](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationDispatcherUnhandledExceptionSnippets/visualbasic/application.xaml.vb)]

Un paramètre <xref:System.Windows.Threading.DispatcherUnhandledExceptionEventArgs> qui contient des informations contextuelles relatives à l’exception non gérée est passé au gestionnaire d’événements <xref:System.Windows.Application.DispatcherUnhandledException>, y compris l’exception elle-même (<xref:System.Windows.Threading.DispatcherUnhandledExceptionEventArgs.Exception%2A?displayProperty=nameWithType>). Vous pouvez utiliser ces informations pour déterminer comment gérer l’exception.

Lorsque vous gérez <xref:System.Windows.Application.DispatcherUnhandledException>, vous devez définir la propriété <xref:System.Windows.Threading.DispatcherUnhandledExceptionEventArgs.Handled%2A?displayProperty=nameWithType> sur `true`; dans le cas contraire, WPF considère toujours que l’exception est non gérée et revient au comportement par défaut décrit précédemment. Si une exception non gérée est déclenchée et que l’événement <xref:System.Windows.Application.DispatcherUnhandledException> n’est pas géré, que l’événement est géré et que <xref:System.Windows.Threading.DispatcherUnhandledExceptionEventArgs.Handled%2A> a la valeur `false`, l’application s’arrête immédiatement. En outre, aucun autre événement de <xref:System.Windows.Application> n’est déclenché. Par conséquent, vous devez gérer <xref:System.Windows.Application.DispatcherUnhandledException> si votre application a du code qui doit s’exécuter avant que l’application ne s’arrête.

Bien qu’une application puisse s’arrêter à la suite d’une exception non gérée, elle s’arrête habituellement en réponse à une requête de l’utilisateur, comme décrit dans la section suivante.

<a name="Application_Lifetime_Events"></a>

### <a name="application-lifetime-events"></a>Événements de durée de vie de l'application

Les applications autonomes et les XBAP n’ont pas exactement les mêmes durées de vie. La figure suivante illustre les principaux événements de la durée de vie d’une application autonome et indique l’ordre dans lequel ils sont déclenchés.

![&#45; Événements d’application d’application autonome](./media/applicationmodeloverview-applicationobjectevents.png "ApplicationModelOverview_ApplicationObjectEvents")

De même, la figure ci-dessous illustre les événements clés dans la durée de vie d’une application XBAP et montre l’ordre dans lequel ils sont déclenchés.

![Événements &#45; d’objets d’application XBAP](./media/applicationmodeloverview-applicationobjectevents-xbap.png "ApplicationModelOverview_ApplicationObjectEvents_xbap")

## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Application>
- [Vue d'ensemble des fenêtres WPF](wpf-windows-overview.md)
- [Vue d’ensemble de la navigation](navigation-overview.md)
- [Fichiers de ressources, de contenu et de données d’une application WPF](wpf-application-resource-content-and-data-files.md)
- [URI à en-tête pack dans WPF](pack-uris-in-wpf.md)
- [Modèle d’application : rubriques de procédures](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms749013(v=vs.100))
- [Développement d’applications](index.md)
