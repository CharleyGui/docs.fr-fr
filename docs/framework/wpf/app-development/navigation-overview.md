---
title: Vue d'ensemble de la navigation
description: En savoir plus sur la prise en charge de la navigation de type navigateur utilisée dans les applications autonomes et les applications de navigateur XAML dans Windows Presentation Foundation (WPF).
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- loose XAML files [WPF]
- windows [WPF]
- Start page [WPF]
- HTML files [WPF]
- structured navigation [WPF]
- fragment navigation [WPF]
- URIs (Uniform Resource Identifiers)
- custom objects [WPF]
- Uniform Resource Identifiers (URIs)
- pages [WPF]
- frames [WPF]
- navigation hosts [WPF]
- journals [WPF]
- lifetimes [WPF]
- retaining content state [WPF]
- content state [WPF]
- programmatic navigation [WPF]
- hyperlinks [WPF]
ms.assetid: 86ad2143-606a-4e34-bf7e-51a2594248b8
ms.openlocfilehash: 2aac1b3a38b6240bfba1b90983fd9cbd18b31b6f
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621702"
---
# <a name="navigation-overview"></a>Vue d'ensemble de la navigation

Windows Presentation Foundation (WPF) prend en charge la navigation de style navigateur qui peut être utilisée dans deux types d’applications : les applications autonomes et les applications de navigateur XAML (XBAP). Pour empaqueter le contenu pour la navigation, WPF fournit la <xref:System.Windows.Controls.Page> classe. Vous pouvez naviguer de l’un <xref:System.Windows.Controls.Page> à l’autre de façon déclarative, en utilisant un <xref:System.Windows.Documents.Hyperlink> , ou par programme, à l’aide de <xref:System.Windows.Navigation.NavigationService> . WPF utilise le journal pour mémoriser les pages qui ont été parcourues et pour y revenir.

<xref:System.Windows.Controls.Page>, <xref:System.Windows.Documents.Hyperlink> , <xref:System.Windows.Navigation.NavigationService> et le journal forment le cœur de la prise en charge de la navigation offerte par WPF. Cette vue d’ensemble explore ces fonctionnalités en détail avant de couvrir la prise en charge de la navigation avancée qui comprend la navigation vers des [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] fichiers libres, des fichiers HTML et des objets.

> [!NOTE]
> Dans cette rubrique, le terme « navigateur » fait référence uniquement aux navigateurs qui peuvent héberger des applications WPF, qui incluent actuellement Microsoft Internet Explorer et Firefox. Lorsque des fonctionnalités WPF spécifiques sont prises en charge uniquement par un navigateur particulier, la version du navigateur est référencée.

## <a name="navigation-in-wpf-applications"></a>Navigation dans les applications WPF

Cette rubrique fournit une vue d’ensemble des principales fonctionnalités de navigation dans WPF. Ces fonctionnalités sont disponibles pour les applications autonomes et les applications XBAP, bien que cette rubrique les présente dans le contexte d’une application XBAP.

> [!NOTE]
> Cette rubrique n’explique pas comment créer et déployer des applications XBAP. Pour plus d’informations sur les XBAP, consultez [vue d’ensemble des applications de navigateur XAML WPF](wpf-xaml-browser-applications-overview.md).

Cette section explique et illustre les aspects suivants de la navigation :

- [Implémentation d’une page](#CreatingAXAMLPage)

- [Configuration d’une page de démarrage](#Configuring_a_Start_Page)

- [Configuration du titre, de la largeur et de la hauteur de la fenêtre hôte](#ConfiguringAXAMLPage)

- [Navigation par lien hypertexte](#NavigatingBetweenXAMLPages)

- [Navigation vers un fragment](#FragmentNavigation)

- [Service de navigation](#NavigationService)

- [Navigation par programmation avec le service de navigation](#Programmatic_Navigation_with_the_Navigation_Service)

- [Durée de vie de la navigation](#Navigation_Lifetime)

- [Mémorisation de la navigation avec le journal](#NavigationHistory)

- [Durée de vie d’une page et le journal](#PageLifetime)

- [Conservation de l’état du contenu avec l’historique de navigation](#RetainingContentStateWithNavigationHistory)

- [Internes](#Cookies)

- [Navigation structurée](#Structured_Navigation)

<a name="CreatingAXAMLPage"></a>

### <a name="implementing-a-page"></a>Implémentation d’une page

Dans WPF, vous pouvez accéder à plusieurs types de contenu qui incluent des objets .NET Framework, des objets personnalisés, des valeurs d’énumération, des contrôles utilisateur, des [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] fichiers et des fichiers html. Toutefois, vous constaterez que la méthode la plus courante et la plus pratique pour empaqueter le contenu consiste à utiliser <xref:System.Windows.Controls.Page> . En outre, <xref:System.Windows.Controls.Page> implémente des fonctionnalités spécifiques à la navigation pour améliorer leur apparence et simplifier le développement.

À l’aide de <xref:System.Windows.Controls.Page> , vous pouvez implémenter de manière déclarative une page navigable de [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] contenu à l’aide d’un balisage similaire à ce qui suit.

[!code-xaml[NavigationOverviewSnippets#Page1XAML](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/Page1.xaml#page1xaml)]

Un <xref:System.Windows.Controls.Page> implémenté dans [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] le balisage a `Page` comme son élément racine et requiert la déclaration d’espace de noms XML WPF. L' `Page` élément contient le contenu auquel vous souhaitez accéder et que vous souhaitez afficher. Vous ajoutez du contenu en définissant l' `Page.Content` élément de propriété, comme indiqué dans le balisage suivant.

[!code-xaml[NavigationOverviewSnippets#Page2XAML](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/Page2.xaml#page2xaml)]

`Page.Content` ne peut contenir qu’un seul élément enfant. Dans l’exemple précédent, le contenu est une chaîne unique, « Hello, Page! » Dans la pratique, vous utiliserez généralement un contrôle de disposition comme élément enfant (consultez [disposition](../advanced/layout.md)) pour contenir et composer votre contenu.

Les éléments enfants d’un `Page` élément sont considérés comme le contenu d’un <xref:System.Windows.Controls.Page> et, par conséquent, vous n’avez pas besoin d’utiliser la `Page.Content` déclaration explicite. Le balisage suivant est l’équivalent déclaratif de l’exemple précédent.

[!code-xaml[NavigationOverviewSnippets#Page3XAML](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/Page3.xaml#page3xaml)]

Dans ce cas, `Page.Content` est défini automatiquement avec les éléments enfants de l' `Page` élément. Pour plus d’informations, consultez [Modèle de contenu WPF](../controls/wpf-content-model.md).

Un balisage uniquement <xref:System.Windows.Controls.Page> est utile pour afficher le contenu. Toutefois, un <xref:System.Windows.Controls.Page> peut également afficher des contrôles qui permettent aux utilisateurs d’interagir avec la page, et il peut répondre à l’interaction de l’utilisateur en gérant les événements et en appelant la logique d’application. Une interactivité <xref:System.Windows.Controls.Page> est implémentée à l’aide d’une combinaison de balises et de code-behind, comme illustré dans l’exemple suivant.

[!code-xaml[XBAPAppDefSnippets#HomePageMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/XBAPAppDefSnippets/CSharp/HomePage.xaml#homepagemarkup)]

[!code-csharp[XBAPAppDefSnippets#HomePageCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/XBAPAppDefSnippets/CSharp/HomePage.xaml.cs#homepagecodebehind)]
[!code-vb[XBAPAppDefSnippets#HomePageCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/XBAPAppDefSnippets/VisualBasic/HomePage.xaml.vb#homepagecodebehind)]

Pour permettre à un fichier de balisage et un fichier code-behind de fonctionner ensemble, la configuration suivante est nécessaire :

- Dans le balisage, l' `Page` élément doit inclure l' `x:Class` attribut. Lorsque l’application est générée, l’existence de `x:Class` dans le fichier de balisage amène Microsoft Build Engine (MSBuild) à créer une `partial` classe qui dérive de <xref:System.Windows.Controls.Page> et qui porte le nom spécifié par l' `x:Class` attribut. Cela nécessite l’ajout d’une déclaration d’espace de noms XML pour le [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] schéma ( `xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"` ). La `partial` classe générée implémente `InitializeComponent` , qui est appelé pour inscrire les événements et définir les propriétés implémentées dans le balisage.

- Dans le code-behind, la classe doit être une `partial` classe portant le même nom que celui spécifié par l' `x:Class` attribut dans le balisage, et elle doit dériver de <xref:System.Windows.Controls.Page> . Cela permet au fichier code-behind d’être associé à la `partial` classe générée pour le fichier de balisage quand l’application est générée (consultez [génération d’une application WPF](building-a-wpf-application-wpf.md)).

- Dans le code-behind, la <xref:System.Windows.Controls.Page> classe doit implémenter un constructeur qui appelle la `InitializeComponent` méthode. `InitializeComponent`est implémenté par la classe générée du fichier de balisage `partial` pour inscrire les événements et définir les propriétés définies dans le balisage.

> [!NOTE]
> Lorsque vous ajoutez un nouveau <xref:System.Windows.Controls.Page> à votre projet à l’aide de Visual Studio, le <xref:System.Windows.Controls.Page> est implémenté à l’aide du balisage et du code-behind, et il comprend la configuration nécessaire pour créer l’association entre les fichiers de balisage et de code-behind, comme décrit ici.

Une fois que vous disposez d’un <xref:System.Windows.Controls.Page> , vous pouvez accéder à celui-ci. Pour spécifier le premier <xref:System.Windows.Controls.Page> vers lequel une application accède, vous devez configurer le démarrage <xref:System.Windows.Controls.Page> .

<a name="Configuring_a_Start_Page"></a>

### <a name="configuring-a-start-page"></a>Configuration d’une page de démarrage

Les applications XBAP requièrent l’hébergement d’une certaine quantité d’infrastructure d’application dans un navigateur. Dans WPF, la <xref:System.Windows.Application> classe fait partie d’une définition d’application qui établit l’infrastructure d’application requise (consultez [vue d’ensemble](application-management-overview.md)de la gestion des applications).

Une définition d’application est généralement implémentée à l’aide du balisage et du code-behind, avec le fichier de balisage configuré en tant qu' `ApplicationDefinition` élément MSBuild. Voici une définition d’application pour un XBAP.

[!code-xaml[XBAPAppDefSnippets#XBAPApplicationDefinitionMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/XBAPAppDefSnippets/CSharp/App.xaml#xbapapplicationdefinitionmarkup)]

[!code-csharp[XBAPAppDefSnippets#XBAPApplicationDefinitionCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/XBAPAppDefSnippets/CSharp/App.xaml.cs#xbapapplicationdefinitioncodebehind)]
[!code-vb[XBAPAppDefSnippets#XBAPApplicationDefinitionCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/XBAPAppDefSnippets/VisualBasic/Application.xaml.vb#xbapapplicationdefinitioncodebehind)]

Un XBAP peut utiliser sa définition d’application pour spécifier un démarrage <xref:System.Windows.Controls.Page> , qui est le <xref:System.Windows.Controls.Page> chargé automatiquement lors du lancement de l’application XBAP. Pour ce faire, définissez la <xref:System.Windows.Application.StartupUri%2A> propriété avec l’URI (Uniform Resource Identifier) pour le souhaité <xref:System.Windows.Controls.Page> .

> [!NOTE]
> Dans la plupart des cas, le <xref:System.Windows.Controls.Page> est soit compilé dans, soit déployé avec une application. Dans ce cas, l’URI qui identifie un <xref:System.Windows.Controls.Page> est un URI à en-tête pack, qui est un URI conforme au schéma *Pack* . Les URI à en-tête pack sont décrits plus en détail dans l’article [Pack URI dans WPF](pack-uris-in-wpf.md). Vous pouvez également naviguer vers du contenu à l’aide du schéma http, comme indiqué ci-dessous.

Vous pouvez définir <xref:System.Windows.Application.StartupUri%2A> de manière déclarative dans le balisage, comme indiqué dans l’exemple suivant.

[!code-xaml[NavigationOverviewSnippets#XBAPApplicationDefinitionMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/App.xaml#xbapapplicationdefinitionmarkup)]

Dans cet exemple, l' `StartupUri` attribut est défini avec un URI à en-tête pack relatif qui identifie HomePage. Xaml. Lorsque l’application XBAP est lancée, HomePage. Xaml accède automatiquement et s’affiche. Cela est illustré par la figure suivante, qui montre une application XBAP lancée à partir d’un serveur Web.

![Page XBAP](./media/navigation-overview/xbap-launched-from-a-web-server.png "Cela montre une application XBAP lancée à partir d’un serveur Web.")

> [!NOTE]
> Pour plus d’informations sur le développement et le déploiement de XBAP, consultez [vue d’ensemble des applications de navigateur XAML WPF](wpf-xaml-browser-applications-overview.md) et [déploiement d’une application WPF](deploying-a-wpf-application-wpf.md).

<a name="ConfiguringAXAMLPage"></a>

### <a name="configuring-the-host-windows-title-width-and-height"></a>Configuration du titre, de la largeur et de la hauteur de la fenêtre hôte

Vous avez peut-être remarqué à partir de l’illustration précédente que le titre du navigateur et du volet d’onglets est l’URI de l’application XBAP. En plus d’être long, le titre n’est ni attrayant, ni informatif. Pour cette raison, <xref:System.Windows.Controls.Page> vous offre un moyen de modifier le titre en définissant la <xref:System.Windows.Controls.Page.WindowTitle%2A> propriété. En outre, vous pouvez configurer la largeur et la hauteur de la fenêtre du navigateur en définissant <xref:System.Windows.Controls.Page.WindowWidth%2A> et <xref:System.Windows.Controls.Page.WindowHeight%2A> , respectivement.

<xref:System.Windows.Controls.Page.WindowTitle%2A>, <xref:System.Windows.Controls.Page.WindowWidth%2A> et <xref:System.Windows.Controls.Page.WindowHeight%2A> peuvent être définis de façon déclarative dans le balisage, comme indiqué dans l’exemple suivant.

[!code-xaml[NavigationOverviewSnippets#HomePageMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/HomePage.xaml#homepagemarkup)]

Le résultat est affiché dans l’illustration suivante.

![Titre de la fenêtre, hauteur, largeur](./media/navigation-overview/window-title-width-height.png "Cela indique le titre, la hauteur et la largeur de la fenêtre que vous pouvez configurer.")

<a name="NavigatingBetweenXAMLPages"></a>

### <a name="hyperlink-navigation"></a>Navigation par lien hypertexte

Une application XBAP classique comprend plusieurs pages. La façon la plus simple de naviguer d’une page à une autre consiste à utiliser un <xref:System.Windows.Documents.Hyperlink> . Vous pouvez ajouter de façon déclarative un <xref:System.Windows.Documents.Hyperlink> à un à <xref:System.Windows.Controls.Page> l’aide de l' `Hyperlink` élément, qui est illustré dans le balisage suivant.

[!code-xaml[NavigationOverviewSnippets#HyperlinkXAML1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithHyperlink.xaml#hyperlinkxaml1)]
[!code-xaml[NavigationOverviewSnippets#HyperlinkXAML2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithHyperlink.xaml#hyperlinkxaml2)]
[!code-xaml[NavigationOverviewSnippets#HyperlinkXAML3](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithHyperlink.xaml#hyperlinkxaml3)]

Un `Hyperlink` élément requiert les éléments suivants :

- URI à en-tête pack du <xref:System.Windows.Controls.Page> à atteindre, comme spécifié par l' `NavigateUri` attribut.

- Contenu sur lequel un utilisateur peut cliquer pour lancer la navigation, tel que le texte et les images (pour le contenu que l' `Hyperlink` élément peut contenir, consultez <xref:System.Windows.Documents.Hyperlink> ).

L’illustration suivante montre une application XBAP avec un <xref:System.Windows.Controls.Page> qui a un <xref:System.Windows.Documents.Hyperlink> .

![Page avec lien hypertexte](./media/navigation-overview/xbap-with-a-page-with-a-hyperlink.png "Cela montre une application XBAP avec une page avec un lien hypertexte.")

Comme vous pouvez vous y attendre, le fait de cliquer sur le <xref:System.Windows.Documents.Hyperlink> fait que l’application XBAP accède au <xref:System.Windows.Controls.Page> identifié par l' `NavigateUri` attribut. En outre, le XBAP ajoute une entrée pour le précédent <xref:System.Windows.Controls.Page> à la liste des pages récentes dans Internet Explorer. Ce cas est illustré dans la figure suivante.

![Boutons précédent et suivant](./media/navigation-overview/back-and-forward-navigation.png "Naviguez avec les boutons précédent et suivant.")

De même que la prise en charge de la navigation d’un <xref:System.Windows.Controls.Page> à un autre, <xref:System.Windows.Documents.Hyperlink> prend également en charge la navigation de fragments.

<a name="FragmentNavigation"></a>

### <a name="fragment-navigation"></a>Navigation vers un fragment

La navigation vers un *fragment* est la navigation vers un fragment de contenu dans le en cours <xref:System.Windows.Controls.Page> ou dans un autre <xref:System.Windows.Controls.Page> . Dans WPF, un fragment de contenu est le contenu qui est contenu dans un élément nommé. Un élément nommé est un élément dont l' `Name` attribut est défini. Le balisage suivant montre un `TextBlock` élément nommé qui contient un fragment de contenu.

[!code-xaml[NavigationOverviewSnippets#PageWithContentFragmentsMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithFragments.xaml#pagewithcontentfragmentsmarkup1)]
[!code-xaml[NavigationOverviewSnippets#PageWithContentFragmentsMARKUP2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithFragments.xaml#pagewithcontentfragmentsmarkup2)]
[!code-xaml[NavigationOverviewSnippets#PageWithContentFragmentsMARKUP3](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithFragments.xaml#pagewithcontentfragmentsmarkup3)]

Pour <xref:System.Windows.Documents.Hyperlink> qu’un accède à un fragment de contenu, l' `NavigateUri` attribut doit inclure les éléments suivants :

- URI du <xref:System.Windows.Controls.Page> avec le fragment de contenu vers lequel naviguer.

- un caractère "#" ;

- Nom de l’élément sur le <xref:System.Windows.Controls.Page> qui contient le fragment de contenu.

Un URI de fragment a le format suivant.

*URIPage* `#` *NomÉlément*

L’exemple suivant montre un `Hyperlink` qui est configuré pour naviguer vers un fragment de contenu.

[!code-xaml[NavigationOverviewSnippets#PageThatNavigatesXAML1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageThatNavigatesToFragment.xaml#pagethatnavigatesxaml1)]
[!code-xaml[NavigationOverviewSnippets#PageThatNavigatesXAML2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageThatNavigatesToFragment.xaml#pagethatnavigatesxaml2)]
[!code-xaml[NavigationOverviewSnippets#PageThatNavigatesXAML3](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageThatNavigatesToFragment.xaml#pagethatnavigatesxaml3)]

> [!NOTE]
> Cette section décrit l’implémentation de la navigation par fragment par défaut dans WPF. WPF vous permet également d’implémenter votre propre schéma de navigation de fragment qui, en partie, requiert la gestion de l' <xref:System.Windows.Navigation.NavigationService.FragmentNavigation?displayProperty=nameWithType> événement.

> [!IMPORTANT]
> Vous pouvez naviguer vers des fragments dans des [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] pages libres (fichiers de balisage uniquement [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] avec `Page` comme élément racine) uniquement si les pages peuvent être parcourues via http.
>
> Toutefois, une [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] page libre peut accéder à ses propres fragments.

<a name="NavigationService"></a>

### <a name="navigation-service"></a>Service de navigation

Alors que <xref:System.Windows.Documents.Hyperlink> permet à un utilisateur d’initier la navigation vers un particulier <xref:System.Windows.Controls.Page> , le travail de localisation et de téléchargement de la page est effectué par la <xref:System.Windows.Navigation.NavigationService> classe. Essentiellement, <xref:System.Windows.Navigation.NavigationService> offre la possibilité de traiter une demande de navigation pour le compte du code client, tel que <xref:System.Windows.Documents.Hyperlink> . En outre, <xref:System.Windows.Navigation.NavigationService> implémente une prise en charge de niveau supérieur pour le suivi et l’influence d’une demande de navigation.

Quand un <xref:System.Windows.Documents.Hyperlink> utilisateur clique sur un, WPF appelle <xref:System.Windows.Navigation.NavigationService.Navigate%2A?displayProperty=nameWithType> pour localiser et télécharger le <xref:System.Windows.Controls.Page> à l’URI à en-tête pack spécifié. Le téléchargé <xref:System.Windows.Controls.Page> est converti en une arborescence d’objets dont l’objet racine est une instance du téléchargé <xref:System.Windows.Controls.Page> . Une référence à l' <xref:System.Windows.Controls.Page> objet racine est stockée dans la <xref:System.Windows.Navigation.NavigationService.Content%2A?displayProperty=nameWithType> propriété. L’URI à en-tête pack pour le contenu cible de la navigation est stocké dans la <xref:System.Windows.Navigation.NavigationService.Source%2A?displayProperty=nameWithType> propriété, tandis que le <xref:System.Windows.Navigation.NavigationService.CurrentSource%2A?displayProperty=nameWithType> stocke l’URI à en-tête pack pour la dernière page vers laquelle la navigation a eu lieu.

> [!NOTE]
> Il est possible qu’une application WPF en ait plusieurs actuellement actives <xref:System.Windows.Navigation.NavigationService> . Pour plus d’informations, consultez la section [hôtes de navigation](#Navigation_Hosts) plus loin dans cette rubrique.

<a name="Programmatic_Navigation_with_the_Navigation_Service"></a>

### <a name="programmatic-navigation-with-the-navigation-service"></a>Navigation par programmation avec le service de navigation

Vous n’avez pas besoin de savoir <xref:System.Windows.Navigation.NavigationService> si la navigation est implémentée de façon déclarative dans le balisage à l’aide de <xref:System.Windows.Documents.Hyperlink> , car <xref:System.Windows.Documents.Hyperlink> utilise <xref:System.Windows.Navigation.NavigationService> en votre nom. Cela signifie que, tant que le parent direct ou indirect d’un <xref:System.Windows.Documents.Hyperlink> est un hôte de navigation (voir les [hôtes de navigation](#Navigation_Hosts)), est en <xref:System.Windows.Documents.Hyperlink> mesure de trouver et d’utiliser le service de navigation de l’hôte de navigation pour traiter une demande de navigation.

Toutefois, il existe des situations dans lesquelles vous devez utiliser <xref:System.Windows.Navigation.NavigationService> directement, y compris les éléments suivants :

- Lorsque vous devez instancier un <xref:System.Windows.Controls.Page> à l’aide d’un constructeur sans paramètre.

- Lorsque vous devez définir des propriétés sur le <xref:System.Windows.Controls.Page> avant d’accéder à celui-ci.

- Lorsque le <xref:System.Windows.Controls.Page> qui doit être parcouru sur ne peut être déterminé qu’au moment de l’exécution.

Dans ces situations, vous devez écrire du code pour lancer la navigation par programmation en appelant la <xref:System.Windows.Navigation.NavigationService.Navigate%2A> méthode de l' <xref:System.Windows.Navigation.NavigationService> objet. Cela nécessite l’obtention d’une référence à un <xref:System.Windows.Navigation.NavigationService> .

#### <a name="getting-a-reference-to-the-navigationservice"></a>Obtention d’une référence à NavigationService

Pour les raisons décrites dans la section [hôtes de navigation](#Navigation_Hosts) , une application WPF peut avoir plusieurs <xref:System.Windows.Navigation.NavigationService> . Cela signifie que votre code a besoin d’un moyen de trouver un <xref:System.Windows.Navigation.NavigationService> , qui est généralement le <xref:System.Windows.Navigation.NavigationService> qui a navigué vers le actuel <xref:System.Windows.Controls.Page> . Vous pouvez obtenir une référence à un <xref:System.Windows.Navigation.NavigationService> en appelant la `static` <xref:System.Windows.Navigation.NavigationService.GetNavigationService%2A?displayProperty=nameWithType> méthode. Pour obtenir le <xref:System.Windows.Navigation.NavigationService> qui a navigué vers un particulier <xref:System.Windows.Controls.Page> , vous passez une référence à <xref:System.Windows.Controls.Page> en tant qu’argument de la <xref:System.Windows.Navigation.NavigationService.GetNavigationService%2A> méthode. Le code suivant montre comment obtenir le <xref:System.Windows.Navigation.NavigationService> pour le actuel <xref:System.Windows.Controls.Page> .

[!code-csharp[NavigationOverviewSnippets#GetNSCODEBEHIND1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/GetNSPage.xaml.cs#getnscodebehind1)]
[!code-csharp[NavigationOverviewSnippets#GetNSCODEBEHIND2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/GetNSPage.xaml.cs#getnscodebehind2)]
[!code-vb[NavigationOverviewSnippets#GetNSCODEBEHIND2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/GetNSPage.xaml.vb#getnscodebehind2)]

Comme raccourci pour rechercher le <xref:System.Windows.Navigation.NavigationService> pour un <xref:System.Windows.Controls.Page> , <xref:System.Windows.Controls.Page> implémente la <xref:System.Windows.Controls.Page.NavigationService%2A> propriété. Cela est illustré par l'exemple suivant.

[!code-csharp[NavigationOverviewSnippets#GetNSShortcutCODEBEHIND1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/GetNSPageShortCut.xaml.cs#getnsshortcutcodebehind1)]
[!code-csharp[NavigationOverviewSnippets#GetNSShortcutCODEBEHIND2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/GetNSPageShortCut.xaml.cs#getnsshortcutcodebehind2)]
[!code-vb[NavigationOverviewSnippets#GetNSShortcutCODEBEHIND2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/GetNSPageShortCut.xaml.vb#getnsshortcutcodebehind2)]

> [!NOTE]
> Un <xref:System.Windows.Controls.Page> peut uniquement obtenir une référence à son <xref:System.Windows.Navigation.NavigationService> lorsqu’il <xref:System.Windows.Controls.Page> déclenche l' <xref:System.Windows.FrameworkElement.Loaded> événement.

#### <a name="programmatic-navigation-to-a-page-object"></a>Navigation par programmation vers un objet Page

L’exemple suivant montre comment utiliser <xref:System.Windows.Navigation.NavigationService> pour naviguer par programmation vers un <xref:System.Windows.Controls.Page> . La navigation par programmation est requise, car la <xref:System.Windows.Controls.Page> cible de la navigation peut uniquement être instanciée à l’aide d’un constructeur unique sans paramètre. Le <xref:System.Windows.Controls.Page> avec le constructeur sans paramètre est affiché dans le balisage et le code suivants.

[!code-xaml[NavigationOverviewSnippets#PageWithNonDefaultConstructorXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithNonDefaultConstructor.xaml#pagewithnondefaultconstructorxaml)]

[!code-csharp[NavigationOverviewSnippets#PageWithNonDefaultConstructorCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithNonDefaultConstructor.xaml.cs#pagewithnondefaultconstructorcodebehind)]
[!code-vb[NavigationOverviewSnippets#PageWithNonDefaultConstructorCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/PageWithNonDefaultConstructor.xaml.vb#pagewithnondefaultconstructorcodebehind)]

Le <xref:System.Windows.Controls.Page> qui navigue vers le <xref:System.Windows.Controls.Page> avec le constructeur sans paramètre est indiqué dans le balisage et le code suivants.

[!code-xaml[NavigationOverviewSnippets#NSNavigationPageXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NSNavigationPage.xaml#nsnavigationpagexaml)]

[!code-csharp[NavigationOverviewSnippets#NSNavigationPageCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NSNavigationPage.xaml.cs#nsnavigationpagecodebehind)]
[!code-vb[NavigationOverviewSnippets#NSNavigationPageCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/NSNavigationPage.xaml.vb#nsnavigationpagecodebehind)]

Quand l' <xref:System.Windows.Documents.Hyperlink> <xref:System.Windows.Controls.Page> utilisateur clique sur, la navigation est lancée en instanciant le <xref:System.Windows.Controls.Page> pour naviguer jusqu’à l’utilisation du constructeur sans paramètre et en appelant la <xref:System.Windows.Navigation.NavigationService.Navigate%2A?displayProperty=nameWithType> méthode. <xref:System.Windows.Navigation.NavigationService.Navigate%2A>accepte une référence à l’objet vers lequel <xref:System.Windows.Navigation.NavigationService> navigue, plutôt qu’un URI à en-tête pack.

#### <a name="programmatic-navigation-with-a-pack-uri"></a>Navigation par programmation avec un URI à en-tête pack

Si vous devez construire un URI à en-tête pack par programme (lorsque vous pouvez uniquement déterminer l’URI à en-tête pack au moment de l’exécution, par exemple), vous pouvez utiliser la <xref:System.Windows.Navigation.NavigationService.Navigate%2A?displayProperty=nameWithType> méthode. Cela est illustré par l'exemple suivant.

[!code-xaml[NavigationOverviewSnippets#NSUriNavigationPageXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NSUriNavigationPage.xaml#nsurinavigationpagexaml)]

[!code-csharp[NavigationOverviewSnippets#NSUriNavigationPageCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NSUriNavigationPage.xaml.cs#nsurinavigationpagecodebehind)]
[!code-vb[NavigationOverviewSnippets#NSUriNavigationPageCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/NSUriNavigationPage.xaml.vb#nsurinavigationpagecodebehind)]

#### <a name="refreshing-the-current-page"></a>Actualisation de la page active

Un <xref:System.Windows.Controls.Page> n’est pas téléchargé s’il a le même URI à en-tête pack que l’URI à en-tête pack stocké dans la <xref:System.Windows.Navigation.NavigationService.Source%2A?displayProperty=nameWithType> propriété. Pour forcer WPF à télécharger à nouveau la page actuelle, vous pouvez appeler la <xref:System.Windows.Navigation.NavigationService.Refresh%2A?displayProperty=nameWithType> méthode, comme indiqué dans l’exemple suivant.

[!code-xaml[NavigationOverviewSnippets#NSRefreshNavigationPageXAML1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NSRefreshNavigationPage.xaml#nsrefreshnavigationpagexaml1)]

[!code-csharp[NavigationOverviewSnippets#NSRefreshNavigationPageCODEBEHIND1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NSRefreshNavigationPage.xaml.cs#nsrefreshnavigationpagecodebehind1)]
[!code-vb[NavigationOverviewSnippets#NSRefreshNavigationPageCODEBEHIND1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/NSRefreshNavigationPage.xaml.vb#nsrefreshnavigationpagecodebehind1)]
[!code-csharp[NavigationOverviewSnippets#NSRefreshNavigationPageCODEBEHIND2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NSRefreshNavigationPage.xaml.cs#nsrefreshnavigationpagecodebehind2)]
[!code-vb[NavigationOverviewSnippets#NSRefreshNavigationPageCODEBEHIND2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/NSRefreshNavigationPage.xaml.vb#nsrefreshnavigationpagecodebehind2)]

<a name="Navigation_Lifetime"></a>

### <a name="navigation-lifetime"></a>Durée de vie de la navigation

Comme vous l’avez vu, il existe de nombreuses façons de démarrer la navigation. Lorsque la navigation est lancée et que la navigation est en cours, vous pouvez suivre et influencer la navigation à l’aide des événements suivants qui sont implémentés par <xref:System.Windows.Navigation.NavigationService> :

- <xref:System.Windows.Navigation.NavigationService.Navigating>. Se produit quand une nouvelle navigation est demandée. Permet d’annuler la navigation.

- <xref:System.Windows.Navigation.NavigationService.NavigationProgress>. Se produit périodiquement au cours d'un téléchargement, pour donner des informations sur la progression de la navigation.

- <xref:System.Windows.Navigation.NavigationService.Navigated>. Se produit quand la page a été localisée et téléchargée.

- <xref:System.Windows.Navigation.NavigationService.NavigationStopped>. Se produit lorsque la navigation est arrêtée (en appelant <xref:System.Windows.Navigation.NavigationService.StopLoading%2A> ) ou lorsqu’une nouvelle navigation est demandée alors qu’une navigation en cours est en cours.

- <xref:System.Windows.Navigation.NavigationService.NavigationFailed>. Se produit en cas d’erreur pendant la navigation vers le contenu demandé.

- <xref:System.Windows.Navigation.NavigationService.LoadCompleted>. Se produit quand le contenu cible de la navigation est chargé et analysé, et que son rendu a commencé.

- <xref:System.Windows.Navigation.NavigationService.FragmentNavigation>. Se produit au début de la navigation vers un fragment de contenu, c’est-à-dire :

  - immédiatement, si le fragment désiré est dans le contenu actuel ;

  - après le chargement du contenu source, si le fragment désiré est dans un autre contenu.

Les événements de navigation sont générés dans l’ordre indiqué sur la figure suivante.

![Organigramme de la navigation entre les pages](./media/navigation-overview/order-of-navigation-events.png "Organigramme des événements de navigation entre les pages")

En général, un <xref:System.Windows.Controls.Page> n’est pas concerné par ces événements. Il est plus probable qu’une application s’en préoccupe et, pour cette raison, ces événements sont également déclenchés par la <xref:System.Windows.Application> classe :

- <xref:System.Windows.Application.Navigating?displayProperty=nameWithType>

- <xref:System.Windows.Application.NavigationProgress?displayProperty=nameWithType>

- <xref:System.Windows.Application.Navigated?displayProperty=nameWithType>

- <xref:System.Windows.Application.NavigationFailed?displayProperty=nameWithType>

- <xref:System.Windows.Application.NavigationStopped?displayProperty=nameWithType>

- <xref:System.Windows.Application.LoadCompleted?displayProperty=nameWithType>

- <xref:System.Windows.Application.FragmentNavigation?displayProperty=nameWithType>

Chaque fois que <xref:System.Windows.Navigation.NavigationService> déclenche un événement, la <xref:System.Windows.Application> classe déclenche l’événement correspondant. <xref:System.Windows.Controls.Frame>et <xref:System.Windows.Navigation.NavigationWindow> offrent les mêmes événements pour détecter la navigation dans leurs étendues respectives.

Dans certains cas, un <xref:System.Windows.Controls.Page> peut s’intéresser à ces événements. Par exemple, un <xref:System.Windows.Controls.Page> peut gérer l' <xref:System.Windows.Navigation.NavigationService.Navigating?displayProperty=nameWithType> événement pour déterminer s’il faut ou non annuler la navigation à partir de lui-même. Cela est illustré par l'exemple suivant.

[!code-xaml[NavigationOverviewSnippets#CancelNavigationPageXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/CancelNavigationPage.xaml#cancelnavigationpagexaml)]

[!code-csharp[NavigationOverviewSnippets#CancelNavigationPageCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/CancelNavigationPage.xaml.cs#cancelnavigationpagecodebehind)]
[!code-vb[NavigationOverviewSnippets#CancelNavigationPageCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/CancelNavigationPage.xaml.vb#cancelnavigationpagecodebehind)]

Si vous inscrivez un gestionnaire avec un événement de navigation à partir d’un <xref:System.Windows.Controls.Page> , comme le fait l’exemple précédent, vous devez également annuler l’inscription du gestionnaire d’événements. Si ce n’est pas le cas, il peut y avoir des effets secondaires sur la façon dont la navigation WPF mémorise <xref:System.Windows.Controls.Page> la navigation à l’aide du journal.

<a name="NavigationHistory"></a>

### <a name="remembering-navigation-with-the-journal"></a>Mémorisation de la navigation avec le journal

WPF utilise deux piles pour se souvenir des pages à partir desquelles vous avez accédé : une pile Back et une pile Forward. Lorsque vous naviguez du actuel <xref:System.Windows.Controls.Page> vers un nouveau <xref:System.Windows.Controls.Page> ou que vous le transférez à un existant <xref:System.Windows.Controls.Page> , le actuel <xref:System.Windows.Controls.Page> est ajouté à la *pile de retour*. Lorsque vous naviguez du actuel <xref:System.Windows.Controls.Page> vers le précédent <xref:System.Windows.Controls.Page> , le actuel <xref:System.Windows.Controls.Page> est ajouté à la *pile Forward*. La pile Back, la pile Forward et les fonctionnalités qui permettent de les gérer représentent le journal. Chaque élément de la pile Back et de la pile Forward est une instance de la <xref:System.Windows.Navigation.JournalEntry> classe et est désigné sous le nom d' *entrée de journal*.

#### <a name="navigating-the-journal-from-internet-explorer"></a>Navigation dans le journal à partir d’Internet Explorer

D’un plan conceptuel, le journal fonctionne de la même façon que les boutons **précédent** et **suivant** dans Internet Explorer. Ces boutons sont représentés dans la figure suivante.

![Boutons précédent et suivant](./media/navigation-overview/back-and-forward-navigation.png "Naviguez avec les boutons précédent et suivant.")

Pour les applications XBAP hébergées par Internet Explorer, WPF intègre le journal dans la navigation [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] d’Internet Explorer. Cela permet aux utilisateurs de parcourir les pages d’une application XBAP à l’aide des boutons **précédent**, **suivant**et **pages récentes** dans Internet Explorer.

> [!IMPORTANT]
> Dans Internet Explorer, quand un utilisateur quitte et revient à une application XBAP, seules les entrées de journal pour les pages qui n’étaient pas gardées actives sont conservées dans le journal. Pour plus d’informations sur la conservation des pages actives, consultez [durée de vie de la page et le journal](#PageLifetime) plus loin dans cette rubrique.

Par défaut, le texte de chaque <xref:System.Windows.Controls.Page> qui apparaît dans la liste **pages récentes** d’Internet Explorer est l’URI du <xref:System.Windows.Controls.Page> . Dans de nombreux cas, cela n’est pas particulièrement explicite pour l’utilisateur. Heureusement, vous pouvez changer le texte à l’aide d’une des options suivantes :

1. Valeur de l' `JournalEntry.Name` attribut attaché.

2. Valeur de l' `Page.Title` attribut.

3. `Page.WindowTitle`Valeur de l’attribut et URI du actuel <xref:System.Windows.Controls.Page> .

4. URI du actuel <xref:System.Windows.Controls.Page> . (Par défaut)

L’ordre dans lequel les options sont listées correspond à l’ordre de priorité de recherche du texte. Par exemple, si `JournalEntry.Name` est défini, les autres valeurs sont ignorées.

L’exemple suivant utilise l' `Page.Title` attribut pour modifier le texte qui apparaît pour une entrée de journal.

[!code-xaml[NavigationOverviewSnippets#PageTitleMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithTitle.xaml#pagetitlemarkup1)]
[!code-xaml[NavigationOverviewSnippets#PageTitleMARKUP2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithTitle.xaml#pagetitlemarkup2)]

[!code-csharp[NavigationOverviewSnippets#PageTitleCODEBEHIND1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithTitle.xaml.cs#pagetitlecodebehind1)]
[!code-vb[NavigationOverviewSnippets#PageTitleCODEBEHIND1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/PageWithTitle.xaml.vb#pagetitlecodebehind1)]
[!code-csharp[NavigationOverviewSnippets#PageTitleCODEBEHIND2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithTitle.xaml.cs#pagetitlecodebehind2)]
[!code-vb[NavigationOverviewSnippets#PageTitleCODEBEHIND2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/PageWithTitle.xaml.vb#pagetitlecodebehind2)]

#### <a name="navigating-the-journal-using-wpf"></a>Navigation dans le journal à l’aide de WPF

Bien qu’un utilisateur puisse naviguer dans le journal à l’aide des pages **précédent**, **suivant**et **récent** dans Internet Explorer, vous pouvez également naviguer dans le journal à l’aide des mécanismes DÉCLARATIFS et de programmation fournis par WPF. L’une des raisons pour cela consiste à fournir des interfaces utilisateur de navigation personnalisées dans vos pages.

Vous pouvez ajouter de façon déclarative la prise en charge de la navigation dans le journal à l’aide des commandes de navigation exposées par <xref:System.Windows.Input.NavigationCommands> . L’exemple suivant montre comment utiliser la `BrowseBack` commande de navigation.

[!code-xaml[NavigationOverviewSnippets#NavigationCommandsPageXAML1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NavigationCommandsPage.xaml#navigationcommandspagexaml1)]
[!code-xaml[NavigationOverviewSnippets#NavigationCommandsPageXAML2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NavigationCommandsPage.xaml#navigationcommandspagexaml2)]
[!code-xaml[NavigationOverviewSnippets#NavigationCommandsPageXAML3](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NavigationCommandsPage.xaml#navigationcommandspagexaml3)]
[!code-xaml[NavigationOverviewSnippets#NavigationCommandsPageXAML4](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NavigationCommandsPage.xaml#navigationcommandspagexaml4)]

Vous pouvez parcourir le journal par programmation à l’aide de l’un des membres suivants de la <xref:System.Windows.Navigation.NavigationService> classe :

- <xref:System.Windows.Navigation.NavigationService.GoBack%2A>

- <xref:System.Windows.Navigation.NavigationService.GoForward%2A>

- <xref:System.Windows.Navigation.NavigationService.CanGoBack%2A>

- <xref:System.Windows.Navigation.NavigationService.CanGoForward%2A>

Le journal peut également être manipulé par programme, comme indiqué dans conservation de [l’état du contenu avec l’historique de navigation](#RetainingContentStateWithNavigationHistory) plus loin dans cette rubrique.

<a name="PageLifetime"></a>

### <a name="page-lifetime-and-the-journal"></a>Durée de vie d’une page et le journal

Considérez une application XBAP avec plusieurs pages qui contiennent du contenu riche, y compris des graphiques, des animations et des médias. L’encombrement mémoire de pages comme celles-ci peut être assez important, en particulier si des médias audio et vidéo sont utilisés. Étant donné que le journal « mémorise » les pages qui ont été parcourues, une telle application XBAP peut rapidement consommer une grande quantité de mémoire.

Pour cette raison, le comportement par défaut du journal est de stocker les <xref:System.Windows.Controls.Page> métadonnées dans chaque entrée du journal plutôt qu’une référence à un <xref:System.Windows.Controls.Page> objet. Lors de la navigation dans une entrée de journal, ses <xref:System.Windows.Controls.Page> métadonnées sont utilisées pour créer une nouvelle instance du spécifié <xref:System.Windows.Controls.Page> . Par conséquent, chaque <xref:System.Windows.Controls.Page> cible de navigation a la durée de vie illustrée par la figure suivante.

![Durée de vie de la page](./media/navigation-overview/navigated-page-lifetime.png "Indique la durée de vie lors de la navigation dans une page.")

Bien que l’utilisation du comportement de journalisation par défaut puisse économiser sur la consommation de mémoire, les performances de rendu par page peuvent être réduites ; réinstanciation a <xref:System.Windows.Controls.Page> peut prendre beaucoup de temps, en particulier s’il a beaucoup de contenu. Si vous devez conserver une <xref:System.Windows.Controls.Page> instance dans le journal, vous pouvez dessiner sur deux techniques pour effectuer cette tâche. Tout d’abord, vous pouvez naviguer par programmation vers un <xref:System.Windows.Controls.Page> objet en appelant la <xref:System.Windows.Navigation.NavigationService.Navigate%2A?displayProperty=nameWithType> méthode.

Deuxièmement, vous pouvez spécifier que WPF conserve une instance de <xref:System.Windows.Controls.Page> dans le journal en affectant <xref:System.Windows.Controls.Page.KeepAlive%2A> à la propriété la `true` valeur (la valeur par défaut est `false` ). Comme indiqué dans l’exemple suivant, vous pouvez définir <xref:System.Windows.Controls.Page.KeepAlive%2A> de manière déclarative dans le balisage.

[!code-xaml[NavigationOverviewSnippets#KeepAlivePageXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/KeepAlivePage.xaml#keepalivepagexaml)]

La durée de vie d’un <xref:System.Windows.Controls.Page> qui est gardé actif est légèrement différente de celle d’un qui n’est pas. La première fois <xref:System.Windows.Controls.Page> que vous accédez à un qui reste actif, il est instancié comme un <xref:System.Windows.Controls.Page> qui n’est pas gardé actif. Toutefois, étant donné qu’une instance du <xref:System.Windows.Controls.Page> est conservée dans le journal, elle n’est jamais instanciée à nouveau tant qu’elle reste dans le journal. Par conséquent, si un <xref:System.Windows.Controls.Page> a une logique d’initialisation qui doit être appelée chaque fois que le <xref:System.Windows.Controls.Page> est parcouru, vous devez le déplacer du constructeur vers un gestionnaire pour l' <xref:System.Windows.FrameworkElement.Loaded> événement. Comme indiqué dans l’illustration suivante, les <xref:System.Windows.FrameworkElement.Loaded> <xref:System.Windows.FrameworkElement.Unloaded> événements et sont toujours déclenchés chaque fois <xref:System.Windows.Controls.Page> qu’un est navigué vers et à partir de, respectivement.

![Lorsque les événements chargés et déchargés sont déclenchés](./media/navigation-overview/loaded-and-unloaded-events.png "Les événements chargés et déchargés sont déclenchés quand une page navigue vers et à partir de.")

Quand un <xref:System.Windows.Controls.Page> n’est pas gardé actif, vous ne devez pas effectuer l’une des opérations suivantes :

- stocker une référence le concernant, même partiellement ;

- inscrire des gestionnaires d’événements auprès d’événements qu’il n’implémente pas.

L’une ou l’autre d’entre elles créera des références qui obligeront <xref:System.Windows.Controls.Page> à conserver la mémoire, même après qu’elle a été supprimée du journal.

En général, vous devez préférer le comportement par défaut <xref:System.Windows.Controls.Page> de ne pas conserver un <xref:System.Windows.Controls.Page> actif. Toutefois, cela a des conséquences sur l’état, comme le décrit la section suivante.

<a name="RetainingContentStateWithNavigationHistory"></a>

### <a name="retaining-content-state-with-navigation-history"></a>Conservation de l’état du contenu avec l’historique de navigation

Si un <xref:System.Windows.Controls.Page> n’est pas gardé actif et qu’il contient des contrôles qui collectent des données de l’utilisateur, qu’arrive-t-il aux données si un utilisateur quitte et revient au <xref:System.Windows.Controls.Page> ? Du point de vue de l’expérience utilisateur, l’utilisateur s’attend à voir les données qu’il a entrées. Malheureusement, étant donné qu’une nouvelle instance de <xref:System.Windows.Controls.Page> est créée avec chaque navigation, les contrôles qui ont collecté les données sont réinstanciés et les données sont perdues.

Heureusement, le journal assure la prise en charge de la mémorisation des données entre les <xref:System.Windows.Controls.Page> navigations, y compris les données de contrôle. Plus précisément, l’entrée de journal pour chaque <xref:System.Windows.Controls.Page> agit comme un conteneur temporaire pour l' <xref:System.Windows.Controls.Page> État associé. Les étapes suivantes décrivent l’utilisation de cette prise en charge lors <xref:System.Windows.Controls.Page> de la navigation à partir de :

1. Une entrée pour le en cours <xref:System.Windows.Controls.Page> est ajoutée au journal.

2. L’état de <xref:System.Windows.Controls.Page> est stocké avec l’entrée de journal de cette page, qui est ajoutée à la pile de retour.

3. Le nouveau <xref:System.Windows.Controls.Page> est accédé à.

Lorsque <xref:System.Windows.Controls.Page> vous accédez à la page, à l’aide du journal, les étapes suivantes se produisent :

1. <xref:System.Windows.Controls.Page>(L’entrée de journal supérieure sur la pile Back) est instanciée.

2. Le <xref:System.Windows.Controls.Page> est actualisé avec l’État qui a été stocké avec l’entrée de journal pour le <xref:System.Windows.Controls.Page> .

3. Le <xref:System.Windows.Controls.Page> accède de nouveau à.

WPF utilise automatiquement cette prise en charge lorsque les contrôles suivants sont utilisés sur un <xref:System.Windows.Controls.Page> :

- <xref:System.Windows.Controls.CheckBox>

- <xref:System.Windows.Controls.ComboBox>

- <xref:System.Windows.Controls.Expander>

- <xref:System.Windows.Controls.Frame>

- <xref:System.Windows.Controls.ListBox>

- <xref:System.Windows.Controls.ListBoxItem>

- <xref:System.Windows.Controls.MenuItem>

- <xref:System.Windows.Controls.ProgressBar>

- <xref:System.Windows.Controls.RadioButton>

- <xref:System.Windows.Controls.Slider>

- <xref:System.Windows.Controls.TabControl>

- <xref:System.Windows.Controls.TabItem>

- <xref:System.Windows.Controls.TextBox>

Si un <xref:System.Windows.Controls.Page> utilise ces contrôles, les données qui y sont entrées sont mémorisées entre <xref:System.Windows.Controls.Page> les navigations, comme le montre la **couleur préférée** <xref:System.Windows.Controls.ListBox> dans la figure suivante.

![Page avec contrôles mémorisant l'état](./media/navigation-overview/data-remembered-across-page-navigations.png "Les données entrées sont mémorisées au fil des navigations dans les pages.")

Quand <xref:System.Windows.Controls.Page> a des contrôles autres que ceux de la liste précédente, ou lorsque l’État est stocké dans des objets personnalisés, vous devez écrire du code pour que le journal mémorise l’État dans les <xref:System.Windows.Controls.Page> navigations.

Si vous devez vous souvenir de petites parties d’État entre <xref:System.Windows.Controls.Page> les navigations, vous pouvez utiliser des propriétés de dépendance (consultez <xref:System.Windows.DependencyProperty> ) qui sont configurées avec l' <xref:System.Windows.FrameworkPropertyMetadata.Journal%2A?displayProperty=nameWithType> indicateur de métadonnées.

Si l’État dont vous avez <xref:System.Windows.Controls.Page> besoin dans les navigations comprend plusieurs éléments de données, il peut s’avérer moins gourmand en code d’encapsuler votre état dans une classe unique et d’implémenter l' <xref:System.Windows.Navigation.IProvideCustomContentState> interface.

Si vous devez naviguer dans les différents États d’un unique <xref:System.Windows.Controls.Page> , sans naviguer à partir de <xref:System.Windows.Controls.Page> lui-même, vous pouvez utiliser <xref:System.Windows.Navigation.IProvideCustomContentState> et <xref:System.Windows.Navigation.NavigationService.AddBackEntry%2A?displayProperty=nameWithType> .

<a name="Cookies"></a>

### <a name="cookies"></a>Cookies

Les applications WPF peuvent également stocker des données avec des cookies, qui sont créés, mis à jour et supprimés à l’aide des <xref:System.Windows.Application.SetCookie%2A> <xref:System.Windows.Application.GetCookie%2A> méthodes et. Les cookies que vous pouvez créer dans WPF sont les mêmes que ceux utilisés par les autres types d’applications Web. les cookies sont des éléments de données arbitraires stockés par une application sur un ordinateur client pendant ou à travers les sessions d’application. Les données de cookie prennent généralement la forme d’une paire nom/valeur au format suivant.

*Nom* `=` *Valeur*

Lorsque les données sont passées à <xref:System.Windows.Application.SetCookie%2A> , avec le <xref:System.Uri> de l’emplacement pour lequel le cookie doit être défini, un cookie est créé en mémoire et n’est disponible que pendant la durée de la session d’application actuelle. Ce type de cookie est appelé *cookie de session*.

Pour stocker un cookie dans des sessions d’application, vous devez lui ajouter une date d’expiration au format suivant.

*NOM* `=` *VALEUR* `; expires=DAY, DD-MMM-YYYY HH:MM:SS GMT`

Un cookie avec une date d’expiration est stocké dans le dossier fichiers Internet temporaires de l’installation Windows actuelle jusqu’à ce que le cookie expire. Un cookie de ce type est connu sous le nom de *cookie persistant* , car il persiste entre les sessions d’application.

Vous récupérez les cookies de session et les cookies persistants en appelant la <xref:System.Windows.Application.GetCookie%2A> méthode, en passant le <xref:System.Uri> de l’emplacement où le cookie a été défini avec la <xref:System.Windows.Application.SetCookie%2A> méthode.

Voici quelques-unes des façons dont les cookies sont pris en charge dans WPF :

- Les applications autonomes WPF et les applications XBAP peuvent créer et gérer des cookies.

- Les cookies créés par une application XBAP sont accessibles à partir du navigateur.

- Les applications XBAP du même domaine peuvent créer et partager des cookies.

- Les applications XBAP et les pages HTML du même domaine peuvent créer et partager des cookies.

- Les cookies sont distribués lorsque des applications XBAP et des [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] pages libres effectuent des requêtes Web.

- Les applications XBAP de niveau supérieur et les applications XBAP hébergées dans IFRAMEs peuvent accéder aux cookies.

- La prise en charge des cookies dans WPF est la même pour tous les navigateurs pris en charge.

- Dans Internet Explorer, la stratégie P3P relative aux cookies est respectée par WPF, en particulier en ce qui concerne les applications XBAP internes et tierces.

<a name="Structured_Navigation"></a>

### <a name="structured-navigation"></a>Navigation structurée

Si vous devez passer des données d’un <xref:System.Windows.Controls.Page> à un autre, vous pouvez passer les données en tant qu’arguments à un constructeur sans paramètre du <xref:System.Windows.Controls.Page> . Notez que si vous utilisez cette technique, vous devez garder l' <xref:System.Windows.Controls.Page> état actif ; dans le cas contraire, la prochaine fois que vous accédez à <xref:System.Windows.Controls.Page> , WPF réinstancie le <xref:System.Windows.Controls.Page> à l’aide du constructeur sans paramètre.

Vous <xref:System.Windows.Controls.Page> pouvez également implémenter des propriétés qui sont définies avec les données qui doivent être passées. Toutefois, les choses deviennent délicates lorsqu’un a <xref:System.Windows.Controls.Page> besoin de repasser des données au <xref:System.Windows.Controls.Page> qui y a accédé. Le problème est que la navigation ne prend pas en charge de manière native des mécanismes permettant de garantir qu’un <xref:System.Windows.Controls.Page> sera renvoyé à après sa navigation. Pour l’essentiel, la navigation ne prend pas en charge la sémantique d’appel/de retour. Pour résoudre ce problème, WPF fournit la <xref:System.Windows.Navigation.PageFunction%601> classe que vous pouvez utiliser pour vous assurer qu’un <xref:System.Windows.Controls.Page> est retourné à de manière prévisible et structurée. Pour plus d’informations, consultez [vue d’ensemble de la navigation structurée](structured-navigation-overview.md).

<a name="The_NavigationWindow_Class"></a>

## <a name="the-navigationwindow-class"></a>NavigationWindow, classe

À ce stade, vous avez découvert la gamme des services de navigation que vous êtes le plus susceptible d’utiliser pour générer des applications au contenu navigable. Ces services ont été abordés dans le contexte des applications XBAP, bien qu’elles ne soient pas limitées aux applications XBAP. Les systèmes d’exploitation modernes et les applications Windows tirent parti de l’expérience du navigateur des utilisateurs modernes pour incorporer la navigation de style navigateur dans des applications autonomes. Voici quelques exemples communs :

- **Dictionnaire des synonymes** : pour naviguer parmi des choix de mots.

- **Explorateur de fichiers** : pour naviguer parmi des fichiers et des dossiers.

- **Assistants** : pour décomposer une tâche complexe en plusieurs pages parmi lesquelles il est possible de naviguer. Par exemple, l’Assistant composants de Windows gère l’ajout et la suppression de fonctionnalités Windows.

Pour incorporer la navigation de style navigateur dans vos applications autonomes, vous pouvez utiliser la <xref:System.Windows.Navigation.NavigationWindow> classe. <xref:System.Windows.Navigation.NavigationWindow>dérive de <xref:System.Windows.Window> et l’étend avec la même prise en charge de la navigation fournie par les applications XBAP. Vous pouvez utiliser <xref:System.Windows.Navigation.NavigationWindow> la fenêtre principale de votre application autonome ou une fenêtre secondaire telle qu’une boîte de dialogue.

Pour implémenter un <xref:System.Windows.Navigation.NavigationWindow> , comme avec la plupart des classes de niveau supérieur dans WPF ( <xref:System.Windows.Window> , <xref:System.Windows.Controls.Page> , etc.), vous utilisez une combinaison de balisage et de code-behind. Cela est illustré par l'exemple suivant.

[!code-xaml[IntroToNavNavigationWindowSnippets#NavigationWindowMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/IntroToNavNavigationWindowSnippets/CSharp/MainWindow.xaml#navigationwindowmarkup)]

[!code-csharp[IntroToNavNavigationWindowSnippets#NavigationWindowCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/IntroToNavNavigationWindowSnippets/CSharp/MainWindow.xaml.cs#navigationwindowcodebehind)]
[!code-vb[IntroToNavNavigationWindowSnippets#NavigationWindowCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/IntroToNavNavigationWindowSnippets/VisualBasic/MainWindow.xaml.vb#navigationwindowcodebehind)]

Ce code crée un <xref:System.Windows.Navigation.NavigationWindow> qui navigue automatiquement vers un <xref:System.Windows.Controls.Page> (homepage. Xaml) lorsque le <xref:System.Windows.Navigation.NavigationWindow> est ouvert. Si <xref:System.Windows.Navigation.NavigationWindow> est la fenêtre d’application principale, vous pouvez utiliser l' `StartupUri` attribut pour le lancer. Ce cas de figure est illustré dans le balisage suivant.

[!code-xaml[IntroToNavNavigationWindowSnippets#AppLaunchNavWindow](~/samples/snippets/csharp/VS_Snippets_Wpf/IntroToNavNavigationWindowSnippets/CSharp/App.xaml#applaunchnavwindow)]

L’illustration suivante montre la <xref:System.Windows.Navigation.NavigationWindow> fenêtre principale d’une application autonome.

![Fenêtre principale](./media/navigation-overview/navigation-window-as-main-window.png "Fenêtre de navigation comme fenêtre principale")

À partir de la figure, vous pouvez voir que <xref:System.Windows.Navigation.NavigationWindow> a un titre, même s’il n’a pas été défini dans le <xref:System.Windows.Navigation.NavigationWindow> code d’implémentation de l’exemple précédent. Au lieu de cela, le titre est défini à l’aide de la <xref:System.Windows.Controls.Page.WindowTitle%2A> propriété, qui est illustrée dans le code suivant.

[!code-xaml[IntroToNavNavigationWindowSnippets#HomePageMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/IntroToNavNavigationWindowSnippets/CSharp/HomePage.xaml#homepagemarkup1)]
[!code-xaml[IntroToNavNavigationWindowSnippets#HomePageMARKUP2](~/samples/snippets/csharp/VS_Snippets_Wpf/IntroToNavNavigationWindowSnippets/CSharp/HomePage.xaml#homepagemarkup2)]

La définition <xref:System.Windows.Controls.Page.WindowWidth%2A> des <xref:System.Windows.Controls.Page.WindowHeight%2A> Propriétés et affecte également le <xref:System.Windows.Navigation.NavigationWindow> .

En général, vous implémentez le vôtre <xref:System.Windows.Navigation.NavigationWindow> lorsque vous avez besoin de personnaliser son comportement ou son apparence. Si vous ne faites ni l’un, ni l’autre, vous pouvez utiliser un raccourci. Si vous spécifiez l’URI à en-tête pack d’un <xref:System.Windows.Controls.Page> comme <xref:System.Windows.Application.StartupUri%2A> dans une application autonome, <xref:System.Windows.Application> crée automatiquement un <xref:System.Windows.Navigation.NavigationWindow> pour héberger <xref:System.Windows.Controls.Page> . Le balisage suivant montre comment y parvenir.

[!code-xaml[IntroToNavNavigationWindowSnippets#AppLaunchPage](~/samples/snippets/csharp/VS_Snippets_Wpf/IntroToNavNavigationWindowSnippets/CSharp/AnotherApp.xaml#applaunchpage)]

Si vous souhaitez qu’une fenêtre d’application secondaire telle qu’une boîte de dialogue soit un <xref:System.Windows.Navigation.NavigationWindow> , vous pouvez utiliser le code de l’exemple suivant pour l’ouvrir.

[!code-csharp[IntroToNavNavigationWindowSnippets#CreateNWDialogBox](~/samples/snippets/csharp/VS_Snippets_Wpf/IntroToNavNavigationWindowSnippets/CSharp/DialogOwnerWindow.xaml.cs#createnwdialogbox)]
[!code-vb[IntroToNavNavigationWindowSnippets#CreateNWDialogBox](~/samples/snippets/visualbasic/VS_Snippets_Wpf/IntroToNavNavigationWindowSnippets/VisualBasic/DialogOwnerWindow.xaml.vb#createnwdialogbox)]

L’illustration suivante affiche le résultat.

![Boîte de dialogue](./media/navigation-overview/navigation-window-as-dialog-box.png "Fenêtre de navigation en tant que boîte de dialogue")

Comme vous pouvez le voir, <xref:System.Windows.Navigation.NavigationWindow> affiche les boutons **précédent** et **suivant** de style Internet Explorer qui permettent aux utilisateurs de naviguer dans le journal. Ces boutons fournissent la même expérience utilisateur, comme le montre la figure suivante.

![Boutons Précédent et Suivant dans une fenêtre de navigation](./media/navigation-overview/back-and-forward-buttons-in-navigation-window.png "Boutons précédent et suivant dans une fenêtre de navigation")

Si vos pages fournissent leur propre prise en charge de la navigation dans le journal et l’interface utilisateur, vous pouvez masquer les boutons **précédent** et **suivant** affichés par <xref:System.Windows.Navigation.NavigationWindow> en affectant à la propriété la valeur <xref:System.Windows.Navigation.NavigationWindow.ShowsNavigationUI%2A> `false` .

Vous pouvez également utiliser la prise en charge de la personnalisation dans WPF pour remplacer le [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] du <xref:System.Windows.Navigation.NavigationWindow> lui-même.

<a name="Frame_in_Standalone_Applications"></a>

## <a name="the-frame-class"></a>Frame, classe

Le navigateur et <xref:System.Windows.Navigation.NavigationWindow> sont des fenêtres qui hébergent du contenu navigable. Dans certains cas, les applications ont un contenu qui n’a pas besoin d’être hébergé par une fenêtre entière. À la place, ce contenu est hébergé dans un autre contenu. Vous pouvez insérer du contenu navigable dans d’autres contenus à l’aide de la <xref:System.Windows.Controls.Frame> classe. <xref:System.Windows.Controls.Frame>fournit la même prise en charge que les <xref:System.Windows.Navigation.NavigationWindow> XBAP et.

L’exemple suivant montre comment ajouter un <xref:System.Windows.Controls.Frame> à un de <xref:System.Windows.Controls.Page> manière déclarative à l’aide de l' `Frame` élément.

[!code-xaml[NavigationOverviewSnippets#FrameHostPageXAML1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHostPage.xaml#framehostpagexaml1)]
[!code-xaml[NavigationOverviewSnippets#FrameHostPageXAML2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHostPage.xaml#framehostpagexaml2)]
[!code-xaml[NavigationOverviewSnippets#FrameHostPageXAML3](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHostPage.xaml#framehostpagexaml3)]

Ce balisage définit l' `Source` attribut de l' `Frame` élément avec un URI à en-tête pack pour le <xref:System.Windows.Controls.Page> auquel le <xref:System.Windows.Controls.Frame> doit naviguer initialement. L’illustration suivante montre une application XBAP avec un <xref:System.Windows.Controls.Page> qui a un <xref:System.Windows.Controls.Frame> qui a navigué entre plusieurs pages.

![Frame ayant subi une navigation entre plusieurs pages](./media/navigation-overview/frame-navigation-between-multiple-pages.png "Cela montre une navigation de frame entre plusieurs pages.")

Vous n’avez pas à utiliser <xref:System.Windows.Controls.Frame> dans le contenu d’un <xref:System.Windows.Controls.Page> . Il est également courant d’héberger un <xref:System.Windows.Controls.Frame> à l’intérieur du contenu d’un <xref:System.Windows.Window> .

Par défaut, <xref:System.Windows.Controls.Frame> utilise uniquement son propre journal en l’absence d’un autre journal. Si un <xref:System.Windows.Controls.Frame> fait partie du contenu hébergé à l’intérieur d’un <xref:System.Windows.Navigation.NavigationWindow> ou d’un XBAP, <xref:System.Windows.Controls.Frame> utilise le journal qui appartient au <xref:System.Windows.Navigation.NavigationWindow> ou à l’application XBAP. Parfois, il <xref:System.Windows.Controls.Frame> se peut que vous deviez être responsable de son propre journal. L’une des raisons à cela est d’autoriser la navigation dans les journaux dans les pages hébergées par un <xref:System.Windows.Controls.Frame> . Cela est illustré par la figure suivante.

![Diagramme de frame et de page](./media/navigation-overview/journal-navigation-within-pages-hosted-by-a-frame.png "Cela montre la navigation dans les journaux dans les pages hébergées par un frame.")

Dans ce cas, vous pouvez configurer <xref:System.Windows.Controls.Frame> pour utiliser son propre journal en affectant <xref:System.Windows.Controls.Frame.JournalOwnership%2A> à la propriété de la <xref:System.Windows.Controls.Frame> valeur <xref:System.Windows.Navigation.JournalOwnership.OwnsJournal> . Ce cas de figure est illustré dans le balisage suivant.

[!code-xaml[NavigationOverviewSnippets#FrameHostPageOwnJournalXAML1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHostPageOwnJournal.xaml#framehostpageownjournalxaml1)]
[!code-xaml[NavigationOverviewSnippets#FrameHostPageOwnJournalXAML2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHostPageOwnJournal.xaml#framehostpageownjournalxaml2)]
[!code-xaml[NavigationOverviewSnippets#FrameHostPageOwnJournalXAML3](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHostPageOwnJournal.xaml#framehostpageownjournalxaml3)]

L’illustration suivante montre l’effet de la navigation dans un <xref:System.Windows.Controls.Frame> qui utilise son propre journal.

![Frame utilisant son propre journal](./media/navigation-overview/frame-uses-its-own-journal.png "Cela montre l’effet de la navigation dans un frame qui utilise son propre journal.")

Notez que les entrées de journal sont affichées par la navigation [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] dans le <xref:System.Windows.Controls.Frame> , plutôt que par Internet Explorer.

> [!NOTE]
> Si un <xref:System.Windows.Controls.Frame> fait partie du contenu hébergé dans un <xref:System.Windows.Window> , <xref:System.Windows.Controls.Frame> utilise son propre journal et, par conséquent, affiche sa propre navigation [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] .

Si votre expérience utilisateur requiert un <xref:System.Windows.Controls.Frame> pour fournir son propre journal sans afficher la navigation [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] , vous pouvez masquer la navigation [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] en affectant <xref:System.Windows.Controls.Frame.NavigationUIVisibility%2A> à la valeur <xref:System.Windows.Visibility.Hidden> . Ce cas de figure est illustré dans le balisage suivant.

[!code-xaml[NavigationOverviewSnippets#FrameHostPageHidesUIXAML1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHostPageOwnHiddenJournal.xaml#framehostpagehidesuixaml1)]
[!code-xaml[NavigationOverviewSnippets#FrameHostPageHidesUIXAML2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHostPageOwnHiddenJournal.xaml#framehostpagehidesuixaml2)]
[!code-xaml[NavigationOverviewSnippets#FrameHostPageHidesUIXAML3](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHostPageOwnHiddenJournal.xaml#framehostpagehidesuixaml3)]

<a name="Navigation_Hosts"></a>

## <a name="navigation-hosts"></a>Hôtes de navigation

<xref:System.Windows.Controls.Frame>et <xref:System.Windows.Navigation.NavigationWindow> sont des classes connues comme hôtes de navigation. Un *hôte de navigation* est une classe qui peut accéder au contenu et l’afficher. Pour ce faire, chaque hôte de navigation utilise ses propres <xref:System.Windows.Navigation.NavigationService> et journal. La construction de base d’un hôte de navigation est illustrée dans la figure suivante.

![Diagrammes du navigateur](./media/navigation-overview/navigation-host-construction.png "Construction de base d’un hôte de navigation")

Fondamentalement, cela permet <xref:System.Windows.Navigation.NavigationWindow> <xref:System.Windows.Controls.Frame> à et de fournir la même prise en charge de navigation qu’une application XBAP lorsqu’elle est hébergée dans le navigateur.

Outre l’utilisation de <xref:System.Windows.Navigation.NavigationService> et d’un journal, les hôtes de navigation implémentent les mêmes membres que ceux qui <xref:System.Windows.Navigation.NavigationService> implémentent. Cela est illustré par la figure suivante.

![Journal dans un frame et dans une fenêtre de navigation](./media/navigation-overview/navigation-window-and-frame.png "Fenêtre et frame de navigation")

Cela vous permet de programmer la prise en charge de la navigation directement par rapport à eux. Vous pouvez envisager cela si vous devez fournir une navigation personnalisée [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] pour un <xref:System.Windows.Controls.Frame> qui est hébergé dans un <xref:System.Windows.Window> . En outre, les deux types implémentent des membres supplémentaires liés à la navigation, y compris `BackStack` ( <xref:System.Windows.Navigation.NavigationWindow.BackStack%2A?displayProperty=nameWithType> , <xref:System.Windows.Controls.Frame.BackStack%2A?displayProperty=nameWithType> ) et `ForwardStack` ( <xref:System.Windows.Navigation.NavigationWindow.ForwardStack%2A?displayProperty=nameWithType> , <xref:System.Windows.Controls.Frame.ForwardStack%2A?displayProperty=nameWithType> ), qui vous permettent d’énumérer les entrées de journal dans la pile Back et la pile Forward, respectivement.

Comme cela a déjà été mentionné, plusieurs journaux peuvent exister dans une application. L’exemple suivant illustre ce cas de figure.

![Plusieurs journaux au sein d'une application](./media/navigation-overview/multiple-journals-in-one-application.png "Il s’agit d’un exemple de plusieurs journaux dans une application.")

<a name="Navigating_to_Content_Other_than_Pages"></a>

## <a name="navigating-to-content-other-than-xaml-pages"></a>Navigation vers un autre contenu que des pages XAML

Tout au long de cette rubrique, <xref:System.Windows.Controls.Page> et les applications XBAP à en-tête pack ont été utilisées pour illustrer les diverses fonctionnalités de navigation de WPF. Toutefois, un <xref:System.Windows.Controls.Page> qui est compilé dans une application n’est pas le seul type de contenu vers lequel une navigation peut être établie, et les applications XBAP à en-tête pack ne sont pas le seul moyen d’identifier le contenu.

Comme le montre cette section, vous pouvez également naviguer vers des [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] fichiers libres, des fichiers HTML et des objets.

<a name="Navigating_to_Loose_XAML_Files"></a>

### <a name="navigating-to-loose-xaml-files"></a>Navigation vers des fichiers XAML libre

Un [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] fichier libre est un fichier avec les caractéristiques suivantes :

- Contient uniquement [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] (autrement dit, aucun code).

- Il a une déclaration d’espace de noms appropriée.

- Son nom de fichier porte l’extension .xaml.

Par exemple, considérez le contenu suivant qui est stocké en tant que [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] fichier libre, Person. Xaml.

[!code-xaml[NavigationOverviewSnippets#LooseXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/Person.xaml#loosexaml)]

Quand vous double-cliquez sur le fichier, le navigateur s’ouvre et navigue vers le contenu, qu’il affiche. Ce cas est illustré dans la figure suivante.

![Affichage du contenu du fichier Person.XAML](./media/navigation-overview/contents-of-person-xaml-file.png "Affiche le contenu du fichier Person. XAML.")

Vous pouvez afficher un [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] fichier libre à partir des éléments suivants :

- site web sur la machine locale, un intranet ou Internet ;

- Partage de fichiers UNC (Universal Naming Convention).

- disque local.

Un [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] fichier libre peut être ajouté aux favoris du navigateur, ou être la page d’hébergement du navigateur.

> [!NOTE]
> Pour plus d’informations sur la publication et le lancement de [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] pages libres, consultez [déploiement d’une application WPF](deploying-a-wpf-application-wpf.md).

L’une des limitations en matière de libre [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] est que vous ne pouvez héberger que du contenu sécurisé pour une exécution en confiance partielle. Par exemple, `Window` ne peut pas être l’élément racine d’un [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] fichier libre. Pour plus d’informations, consultez [Sécurité de confiance partielle de WPF](../wpf-partial-trust-security.md).

<a name="Navigating_to_HTML_Files_Using_Frame"></a>

### <a name="navigating-to-html-files-by-using-frame"></a>Navigation vers des fichiers HTML à l’aide d’un Frame

Comme vous pouvez vous y attendre, vous pouvez également accéder au code HTML. Vous devez simplement fournir un URI qui utilise le schéma http. Par exemple, le code suivant [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] montre un <xref:System.Windows.Controls.Frame> qui navigue vers une page html.

[!code-xaml[NavigationOverviewSnippets#FrameHtmlNavMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHTMLNavPage.xaml#framehtmlnavmarkup)]

La navigation vers le code HTML nécessite des autorisations spéciales. Par exemple, vous ne pouvez pas naviguer à partir d’une application XBAP qui s’exécute dans le bac à sable de sécurité de confiance partielle de la zone Internet. Pour plus d’informations, consultez [Sécurité de confiance partielle de WPF](../wpf-partial-trust-security.md).

<a name="Navigating_to_HTML_Files_Using_WebBrowser"></a>

### <a name="navigating-to-html-files-by-using-the-webbrowser-control"></a>Navigation vers des fichiers HTML à l’aide du contrôle WebBrowser

Le <xref:System.Windows.Controls.WebBrowser> contrôle prend en charge l’hébergement de documents html, la navigation et l’interopérabilité du code managé/de script. Pour plus d’informations sur le <xref:System.Windows.Controls.WebBrowser> contrôle, consultez <xref:System.Windows.Controls.WebBrowser> .

<xref:System.Windows.Controls.Frame>À l’instar de, la navigation vers HTML à l’aide de <xref:System.Windows.Controls.WebBrowser> requiert des autorisations spéciales. Par exemple, à partir d’une application de confiance partielle, vous pouvez naviguer uniquement jusqu’au code HTML situé sur le site d’origine. Pour plus d’informations, consultez [Sécurité de confiance partielle de WPF](../wpf-partial-trust-security.md).

<a name="Navigating_to_Objects"></a>

### <a name="navigating-to-custom-objects"></a>Navigation vers des objets personnalisés

Si vous avez des données qui sont stockées en tant qu’objets personnalisés, une façon d’afficher ces données consiste à créer un <xref:System.Windows.Controls.Page> avec le contenu lié à ces objets (consultez [vue d’ensemble](../../../desktop-wpf/data/data-binding-overview.md)de la liaison de données). En revanche, si vous n’avez pas besoin de la charge de traitement supplémentaire liée à la création d’une page entière juste pour afficher les objets, vous pouvez naviguer directement vers ces derniers.

Considérez la `Person` classe implémentée dans le code suivant.

[!code-csharp[NavigateToObjectSnippets#PersonClassCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigateToObjectSnippets/CSharp/Person.cs#personclasscode)]
[!code-vb[NavigateToObjectSnippets#PersonClassCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigateToObjectSnippets/VisualBasic/Person.vb#personclasscode)]

Pour y accéder, vous appelez la <xref:System.Windows.Navigation.NavigationWindow.Navigate%2A?displayProperty=nameWithType> méthode, comme le montre le code suivant.

[!code-xaml[NavigateToObjectSnippets#PageThatNavsToObject1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigateToObjectSnippets/CSharp/HomePage.xaml#pagethatnavstoobject1)]
[!code-xaml[NavigateToObjectSnippets#PageThatNavsToObject2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigateToObjectSnippets/CSharp/HomePage.xaml#pagethatnavstoobject2)]
[!code-xaml[NavigateToObjectSnippets#PageThatNavsToObject3](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigateToObjectSnippets/CSharp/HomePage.xaml#pagethatnavstoobject3)]

[!code-csharp[NavigateToObjectSnippets#PageThatNavsToObjectCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigateToObjectSnippets/CSharp/HomePage.xaml.cs#pagethatnavstoobjectcodebehind)]
[!code-vb[NavigateToObjectSnippets#PageThatNavsToObjectCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigateToObjectSnippets/VisualBasic/HomePage.xaml.vb#pagethatnavstoobjectcodebehind)]

L’illustration suivante affiche le résultat.

![Page de navigation vers une classe](./media/navigation-overview/page-navigates-to-an-object.png "Il s’agit d’un exemple de page qui navigue vers un objet.")

Dans cette illustration, vous pouvez voir que rien d’utile n’est affiché. En fait, la valeur affichée est la valeur de retour de la `ToString` méthode pour l’objet **Person** ; par défaut, il s’agit de la seule valeur que WPF peut utiliser pour représenter votre objet. Vous pouvez substituer la `ToString` méthode pour retourner des informations plus explicites, bien qu’il ne s’agisse toujours que d’une valeur de chaîne. L’une des techniques que vous pouvez utiliser pour tirer parti des fonctionnalités de présentation de WPF consiste à utiliser un modèle de données. Vous pouvez implémenter un modèle de données que WPF peut associer à un objet d’un type particulier. Le code suivant montre un modèle de données pour l' `Person` objet.

[!code-xaml[NavigateToObjectSnippets#DataTemplateMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigateToObjectSnippets/CSharp/App.xaml#datatemplatemarkup)]

Ici, le modèle de données est associé au `Person` type à l’aide `x:Type` de l’extension de balisage dans l' `DataType` attribut. Le modèle de données lie ensuite les `TextBlock` éléments (consultez <xref:System.Windows.Controls.TextBlock> ) aux propriétés de la `Person` classe. L’illustration suivante montre l’apparence mise à jour de l' `Person` objet.

![Navigation vers une classe comportant un modèle de données](./media/navigation-overview/navigating-to-a-class.png "Navigation vers une classe qui a un modèle de données.")

Cette technique présente un avantage, elle vous permet d’afficher vos objets de manière cohérente dans la totalité de votre application grâce à la réutilisation du modèle de données.

Pour plus d’informations sur les modèles de données, consultez [vue d’ensemble](../data/data-templating-overview.md)des modèles de données.

<a name="Security"></a>

## <a name="security"></a>Sécurité

La prise en charge de la navigation WPF permet d’accéder à des XBAP sur Internet et permet aux applications d’héberger du contenu tiers. Pour protéger les applications et les utilisateurs contre les comportements dangereux, WPF fournit une variété de fonctionnalités de sécurité qui sont abordées dans [sécurité](../security-wpf.md) et [sécurité de confiance partielle de WPF](../wpf-partial-trust-security.md).

## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Application.SetCookie%2A>
- <xref:System.Windows.Application.GetCookie%2A>
- [Vue d’ensemble de la gestion d’applications](application-management-overview.md)
- [URI à en-tête pack dans WPF](pack-uris-in-wpf.md)
- [Vue d’ensemble de la navigation structurée](structured-navigation-overview.md)
- [Vue d’ensemble des topologies de navigation](navigation-topologies-overview.md)
- [Rubriques de procédures](navigation-how-to-topics.md)
- [Déploiement d’une application WPF](deploying-a-wpf-application-wpf.md)
