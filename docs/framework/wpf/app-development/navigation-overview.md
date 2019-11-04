---
title: Vue d'ensemble de la navigation
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
ms.openlocfilehash: 619dc101cd8851cee24651b7e3098ae12ef46259
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459772"
---
# <a name="navigation-overview"></a>Vue d'ensemble de la navigation

Windows Presentation Foundation (WPF) prend en charge la navigation de style navigateur qui peut être utilisée dans deux types d’applications : les applications autonomes et les applications de navigateur XAML (XBAP). Pour empaqueter le contenu pour la navigation, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] fournit la classe <xref:System.Windows.Controls.Page>. Vous pouvez naviguer d’une <xref:System.Windows.Controls.Page> à une autre de façon déclarative, à l’aide d’un <xref:System.Windows.Documents.Hyperlink> ou par programme, à l’aide de l' <xref:System.Windows.Navigation.NavigationService>. [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] utilise le journal pour se souvenir des pages visitées et y revenir.

<xref:System.Windows.Controls.Page>, <xref:System.Windows.Documents.Hyperlink>, <xref:System.Windows.Navigation.NavigationService>et le journal constituent le cœur de la prise en charge de la navigation offerte par [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]. Cette vue d’ensemble explore ces fonctionnalités en détail avant de couvrir la prise en charge de la navigation avancée qui comprend la navigation vers des fichiers [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], des fichiers HTML et des objets libres.

> [!NOTE]
> Dans cette rubrique, le terme « navigateur » fait référence uniquement aux navigateurs qui peuvent héberger des applications [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], qui incluent actuellement Microsoft Internet Explorer et Firefox. Lorsque des fonctionnalités [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] spécifiques sont prises en charge uniquement par un navigateur particulier, la version du navigateur est indiquée.

## <a name="navigation-in-wpf-applications"></a>Navigation dans les applications WPF

Cette rubrique fournit une vue d’ensemble des principales fonctionnalités de navigation dans [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]. Ces fonctionnalités sont disponibles pour les applications autonomes et les applications XBAP, bien que cette rubrique les présente dans le contexte d’une application XBAP.

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

- [Cookies](#Cookies)

- [Navigation structurée](#Structured_Navigation)

<a name="CreatingAXAMLPage"></a>

### <a name="implementing-a-page"></a>Implémentation d’une page

Dans [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], vous pouvez accéder à plusieurs types de contenu qui incluent des objets .NET Framework, des objets personnalisés, des valeurs d’énumération, des contrôles utilisateur, des fichiers [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] et des fichiers HTML. Toutefois, vous constaterez que la méthode la plus courante et la plus pratique pour empaqueter le contenu consiste à utiliser <xref:System.Windows.Controls.Page>. En outre, <xref:System.Windows.Controls.Page> implémente des fonctionnalités spécifiques à la navigation pour améliorer leur apparence et simplifier le développement.

À l’aide de <xref:System.Windows.Controls.Page>, vous pouvez implémenter de manière déclarative une page navigable de contenu [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] à l’aide d’un balisage similaire à ce qui suit.

[!code-xaml[NavigationOverviewSnippets#Page1XAML](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/Page1.xaml#page1xaml)]

Une <xref:System.Windows.Controls.Page> implémentée dans [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] balisage a `Page` comme élément racine et requiert la déclaration d’espace de noms [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)][!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)]. L’élément `Page` contient le contenu auquel vous souhaitez accéder et que vous souhaitez afficher. Vous ajoutez du contenu en définissant l’élément de propriété `Page.Content`, comme indiqué dans le balisage suivant.

[!code-xaml[NavigationOverviewSnippets#Page2XAML](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/Page2.xaml#page2xaml)]

`Page.Content` ne peut contenir qu’un seul élément enfant. Dans l’exemple précédent, le contenu est une chaîne unique, « Hello, Page! » Dans la pratique, vous utiliserez généralement un contrôle de disposition comme élément enfant (consultez [disposition](../advanced/layout.md)) pour contenir et composer votre contenu.

Les éléments enfants d’un élément `Page` sont considérés comme le contenu d’un <xref:System.Windows.Controls.Page> et, par conséquent, vous n’avez pas besoin d’utiliser la déclaration d' `Page.Content` explicite. Le balisage suivant est l’équivalent déclaratif de l’exemple précédent.

[!code-xaml[NavigationOverviewSnippets#Page3XAML](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/Page3.xaml#page3xaml)]

Dans ce cas, `Page.Content` est défini automatiquement avec les éléments enfants de l’élément `Page`. Pour plus d’informations, consultez [Modèle de contenu WPF](../controls/wpf-content-model.md).

Une <xref:System.Windows.Controls.Page> de balisage uniquement est utile pour afficher du contenu. Toutefois, un <xref:System.Windows.Controls.Page> peut également afficher des contrôles qui permettent aux utilisateurs d’interagir avec la page, et il peut répondre à l’interaction de l’utilisateur en gérant les événements et en appelant la logique d’application. Une <xref:System.Windows.Controls.Page> interactive est implémentée à l’aide d’une combinaison de balises et de code-behind, comme illustré dans l’exemple suivant.

[!code-xaml[XBAPAppDefSnippets#HomePageMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/XBAPAppDefSnippets/CSharp/HomePage.xaml#homepagemarkup)]

[!code-csharp[XBAPAppDefSnippets#HomePageCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/XBAPAppDefSnippets/CSharp/HomePage.xaml.cs#homepagecodebehind)]
[!code-vb[XBAPAppDefSnippets#HomePageCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/XBAPAppDefSnippets/VisualBasic/HomePage.xaml.vb#homepagecodebehind)]

Pour permettre à un fichier de balisage et un fichier code-behind de fonctionner ensemble, la configuration suivante est nécessaire :

- Dans le balisage, l’élément `Page` doit inclure l’attribut `x:Class`. Lorsque l’application est générée, l’existence d' `x:Class` dans le fichier de balisage permet à Microsoft Build Engine (MSBuild) de créer une classe `partial` qui dérive de <xref:System.Windows.Controls.Page> et qui porte le nom spécifié par l’attribut `x:Class`. Cela nécessite l’ajout d’une déclaration d’espace de noms [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] pour le schéma de [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] (`xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"`). La classe `partial` générée implémente `InitializeComponent`, qui est appelé pour inscrire les événements et définir les propriétés implémentées dans le balisage.

- Dans le code-behind, la classe doit être une classe `partial` portant le même nom que celui spécifié par l’attribut `x:Class` dans le balisage, et elle doit dériver de <xref:System.Windows.Controls.Page>. Cela permet au fichier code-behind d’être associé à la classe `partial` générée pour le fichier de balisage quand l’application est générée (consultez [génération d’une application WPF](building-a-wpf-application-wpf.md)).

- Dans le code-behind, la classe <xref:System.Windows.Controls.Page> doit implémenter un constructeur qui appelle la méthode `InitializeComponent`. `InitializeComponent` est implémenté par la classe `partial` générée du fichier de balisage pour inscrire les événements et définir les propriétés définies dans le balisage.

> [!NOTE]
> Lorsque vous ajoutez un nouveau <xref:System.Windows.Controls.Page> à votre projet à l’aide de Visual Studio, le <xref:System.Windows.Controls.Page> est implémenté à l’aide du balisage et du code-behind, et il comprend la configuration nécessaire pour créer l’association entre les fichiers de balisage et de code-behind, comme décrit ici.

Une fois que vous disposez d’un <xref:System.Windows.Controls.Page>, vous pouvez accéder à celui-ci. Pour spécifier la première <xref:System.Windows.Controls.Page> à laquelle une application accède, vous devez configurer le <xref:System.Windows.Controls.Page> de démarrage.

<a name="Configuring_a_Start_Page"></a>

### <a name="configuring-a-start-page"></a>Configuration d’une page de démarrage

Les applications XBAP requièrent l’hébergement d’une certaine quantité d’infrastructure d’application dans un navigateur. Dans [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], la classe <xref:System.Windows.Application> fait partie d’une définition d’application qui établit l’infrastructure d’application requise (consultez [vue d’ensemble](application-management-overview.md)de la gestion des applications).

Une définition d’application est généralement implémentée à l’aide du balisage et du code-behind, avec le fichier de balisage configuré en tant qu’élément de `ApplicationDefinition` MSBuild. Voici une définition d’application pour un XBAP.

[!code-xaml[XBAPAppDefSnippets#XBAPApplicationDefinitionMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/XBAPAppDefSnippets/CSharp/App.xaml#xbapapplicationdefinitionmarkup)]

[!code-csharp[XBAPAppDefSnippets#XBAPApplicationDefinitionCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/XBAPAppDefSnippets/CSharp/App.xaml.cs#xbapapplicationdefinitioncodebehind)]
[!code-vb[XBAPAppDefSnippets#XBAPApplicationDefinitionCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/XBAPAppDefSnippets/VisualBasic/Application.xaml.vb#xbapapplicationdefinitioncodebehind)]

Une application XBAP peut utiliser sa définition d’application pour spécifier un <xref:System.Windows.Controls.Page>de démarrage, qui est le <xref:System.Windows.Controls.Page> chargé automatiquement lors du lancement de l’application XBAP. Pour ce faire, définissez la propriété <xref:System.Windows.Application.StartupUri%2A> avec l’URI (Uniform Resource Identifier) pour le <xref:System.Windows.Controls.Page>souhaité.

> [!NOTE]
> Dans la plupart des cas, le <xref:System.Windows.Controls.Page> est compilé dans ou déployé avec une application. Dans ce cas, l’URI qui identifie un <xref:System.Windows.Controls.Page> est un URI à en-tête pack, qui est un URI conforme au schéma *Pack* . Les URI à en-tête pack sont décrits plus en détail dans l’article [Pack URI dans WPF](pack-uris-in-wpf.md). Vous pouvez également naviguer vers du contenu à l’aide du schéma http, comme indiqué ci-dessous.

Vous pouvez définir <xref:System.Windows.Application.StartupUri%2A> de façon déclarative dans le balisage, comme indiqué dans l’exemple suivant.

[!code-xaml[NavigationOverviewSnippets#XBAPApplicationDefinitionMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/App.xaml#xbapapplicationdefinitionmarkup)]

Dans cet exemple, l’attribut `StartupUri` est défini avec un URI à en-tête pack relatif qui identifie HomePage. Xaml. Lorsque l’application XBAP est lancée, HomePage. Xaml accède automatiquement et s’affiche. Cela est illustré par la figure suivante, qui montre une application XBAP lancée à partir d’un serveur Web.

![Page XBAP](./media/navigation-overview/xbap-launched-from-a-web-server.png "Cela montre une application XBAP lancée à partir d’un serveur Web.")

> [!NOTE]
> Pour plus d’informations sur le développement et le déploiement de XBAP, consultez [vue d’ensemble des applications de navigateur XAML WPF](wpf-xaml-browser-applications-overview.md) et [déploiement d’une application WPF](deploying-a-wpf-application-wpf.md).

<a name="ConfiguringAXAMLPage"></a>

### <a name="configuring-the-host-windows-title-width-and-height"></a>Configuration du titre, de la largeur et de la hauteur de la fenêtre hôte

Vous avez peut-être remarqué à partir de l’illustration précédente que le titre du navigateur et du volet d’onglets est l’URI de l’application XBAP. En plus d’être long, le titre n’est ni attrayant, ni informatif. C’est la raison pour laquelle <xref:System.Windows.Controls.Page> offre un moyen de modifier le titre en définissant la propriété <xref:System.Windows.Controls.Page.WindowTitle%2A>. En outre, vous pouvez configurer la largeur et la hauteur de la fenêtre du navigateur en définissant <xref:System.Windows.Controls.Page.WindowWidth%2A> et <xref:System.Windows.Controls.Page.WindowHeight%2A>, respectivement.

<xref:System.Windows.Controls.Page.WindowTitle%2A>, <xref:System.Windows.Controls.Page.WindowWidth%2A>et <xref:System.Windows.Controls.Page.WindowHeight%2A> peuvent être définis de façon déclarative dans le balisage, comme indiqué dans l’exemple suivant.

[!code-xaml[NavigationOverviewSnippets#HomePageMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/HomePage.xaml#homepagemarkup)]

Le résultat est affiché dans l’illustration suivante.

![Titre de la fenêtre, hauteur, largeur](./media/navigation-overview/window-title-width-height.png "Cela indique le titre, la hauteur et la largeur de la fenêtre que vous pouvez configurer.")

<a name="NavigatingBetweenXAMLPages"></a>

### <a name="hyperlink-navigation"></a>Navigation par lien hypertexte

Une application XBAP classique comprend plusieurs pages. La façon la plus simple de naviguer d’une page à une autre consiste à utiliser un <xref:System.Windows.Documents.Hyperlink>. Vous pouvez ajouter de façon déclarative un <xref:System.Windows.Documents.Hyperlink> à un <xref:System.Windows.Controls.Page> à l’aide de l’élément `Hyperlink`, qui est indiqué dans le balisage suivant.

[!code-xaml[NavigationOverviewSnippets#HyperlinkXAML1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithHyperlink.xaml#hyperlinkxaml1)]
[!code-xaml[NavigationOverviewSnippets#HyperlinkXAML2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithHyperlink.xaml#hyperlinkxaml2)]
[!code-xaml[NavigationOverviewSnippets#HyperlinkXAML3](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithHyperlink.xaml#hyperlinkxaml3)]

Un élément `Hyperlink` requiert les éléments suivants :

- URI à en-tête pack du <xref:System.Windows.Controls.Page> vers lequel naviguer, comme spécifié par l’attribut `NavigateUri`.

- Contenu sur lequel un utilisateur peut cliquer pour lancer la navigation, par exemple le texte et les images (pour le contenu que l’élément `Hyperlink` peut contenir, consultez <xref:System.Windows.Documents.Hyperlink>).

L’illustration suivante montre une application XBAP avec un <xref:System.Windows.Controls.Page> qui a un <xref:System.Windows.Documents.Hyperlink>.

![Page avec lien hypertexte](./media/navigation-overview/xbap-with-a-page-with-a-hyperlink.png "Cela montre une application XBAP avec une page avec un lien hypertexte.")

Comme vous pouvez vous y attendre, le fait de cliquer sur le <xref:System.Windows.Documents.Hyperlink> amène l’application XBAP à accéder au <xref:System.Windows.Controls.Page> identifié par l’attribut `NavigateUri`. En outre, l’application XBAP ajoute une entrée pour le <xref:System.Windows.Controls.Page> précédent à la liste des pages récentes dans Internet Explorer. Ce cas est illustré dans la figure suivante.

![Boutons précédent et suivant](./media/navigation-overview/back-and-forward-navigation.png "Naviguez avec les boutons précédent et suivant.")

De même que la prise en charge de la navigation d’un <xref:System.Windows.Controls.Page> à un autre, <xref:System.Windows.Documents.Hyperlink> prend également en charge la navigation de fragments.

<a name="FragmentNavigation"></a>

### <a name="fragment-navigation"></a>Navigation vers un fragment

La navigation vers un *fragment* est la navigation vers un fragment de contenu dans le <xref:System.Windows.Controls.Page> actuel ou dans un autre <xref:System.Windows.Controls.Page>. Dans [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], un fragment de contenu est le contenu qui est contenu dans un élément nommé. Un élément nommé est un élément dont l’attribut `Name` est défini. Le balisage suivant montre un élément `TextBlock` nommé qui contient un fragment de contenu.

[!code-xaml[NavigationOverviewSnippets#PageWithContentFragmentsMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithFragments.xaml#pagewithcontentfragmentsmarkup1)]
[!code-xaml[NavigationOverviewSnippets#PageWithContentFragmentsMARKUP2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithFragments.xaml#pagewithcontentfragmentsmarkup2)]
[!code-xaml[NavigationOverviewSnippets#PageWithContentFragmentsMARKUP3](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithFragments.xaml#pagewithcontentfragmentsmarkup3)]

Pour qu’un <xref:System.Windows.Documents.Hyperlink> accède à un fragment de contenu, l’attribut `NavigateUri` doit inclure les éléments suivants :

- URI du <xref:System.Windows.Controls.Page> avec le fragment de contenu vers lequel naviguer.

- un caractère "#" ;

- Nom de l’élément sur la <xref:System.Windows.Controls.Page> qui contient le fragment de contenu.

Un URI de fragment a le format suivant.

*URIPage* `#` *NomÉlément*

L’exemple suivant illustre un `Hyperlink` configuré pour naviguer vers un fragment de contenu.

[!code-xaml[NavigationOverviewSnippets#PageThatNavigatesXAML1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageThatNavigatesToFragment.xaml#pagethatnavigatesxaml1)]
[!code-xaml[NavigationOverviewSnippets#PageThatNavigatesXAML2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageThatNavigatesToFragment.xaml#pagethatnavigatesxaml2)]
[!code-xaml[NavigationOverviewSnippets#PageThatNavigatesXAML3](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageThatNavigatesToFragment.xaml#pagethatnavigatesxaml3)]

> [!NOTE]
> Cette section décrit l’implémentation de la navigation par fragment par défaut dans [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]. [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] vous permet également d’implémenter votre propre schéma de navigation de fragment qui, en partie, requiert la gestion de l’événement <xref:System.Windows.Navigation.NavigationService.FragmentNavigation?displayProperty=nameWithType>.

> [!IMPORTANT]
> Vous pouvez naviguer vers des fragments dans des pages libres [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] (fichiers de balisage uniquement [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] avec `Page` comme élément racine) uniquement si les pages peuvent être parcourues via HTTP.
>
> Toutefois, une page de [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] faible peut accéder à ses propres fragments.

<a name="NavigationService"></a>

### <a name="navigation-service"></a>Service de navigation

Même si <xref:System.Windows.Documents.Hyperlink> permet à un utilisateur d’initier la navigation vers une <xref:System.Windows.Controls.Page> particulière, le travail de localisation et de téléchargement de la page est effectué par la classe <xref:System.Windows.Navigation.NavigationService>. En fait, <xref:System.Windows.Navigation.NavigationService> permet de traiter une demande de navigation pour le compte du code client, comme le <xref:System.Windows.Documents.Hyperlink>. En outre, <xref:System.Windows.Navigation.NavigationService> implémente une prise en charge de niveau supérieur pour le suivi et l’influence d’une demande de navigation.

Lorsqu’un utilisateur clique sur un <xref:System.Windows.Documents.Hyperlink>, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] appelle <xref:System.Windows.Navigation.NavigationService.Navigate%2A?displayProperty=nameWithType> pour rechercher et télécharger les <xref:System.Windows.Controls.Page> à l’URI à en-tête pack spécifié. Le <xref:System.Windows.Controls.Page> téléchargé est converti en une arborescence d’objets dont l’objet racine est une instance du <xref:System.Windows.Controls.Page> téléchargé. Une référence à l’objet racine <xref:System.Windows.Controls.Page> est stockée dans la propriété <xref:System.Windows.Navigation.NavigationService.Content%2A?displayProperty=nameWithType>. L’URI à en-tête pack pour le contenu cible de la navigation est stocké dans la propriété <xref:System.Windows.Navigation.NavigationService.Source%2A?displayProperty=nameWithType>, tandis que le <xref:System.Windows.Navigation.NavigationService.CurrentSource%2A?displayProperty=nameWithType> stocke l’URI à en-tête pack pour la dernière page vers laquelle la navigation a eu lieu.

> [!NOTE]
> Il est possible qu’une application [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] ait plusieurs <xref:System.Windows.Navigation.NavigationService>actuellement actives. Pour plus d’informations, consultez la section [hôtes de navigation](#Navigation_Hosts) plus loin dans cette rubrique.

<a name="Programmatic_Navigation_with_the_Navigation_Service"></a>

### <a name="programmatic-navigation-with-the-navigation-service"></a>Navigation par programmation avec le service de navigation

Vous n’avez pas besoin de connaître les <xref:System.Windows.Navigation.NavigationService> si la navigation est implémentée de façon déclarative dans le balisage à l’aide de <xref:System.Windows.Documents.Hyperlink>, car <xref:System.Windows.Documents.Hyperlink> utilise les <xref:System.Windows.Navigation.NavigationService> en votre nom. Cela signifie que, tant que le parent direct ou indirect d’un <xref:System.Windows.Documents.Hyperlink> est un hôte de navigation (voir les [hôtes de navigation](#Navigation_Hosts)), <xref:System.Windows.Documents.Hyperlink> sera en mesure de trouver et d’utiliser le service de navigation de l’hôte de navigation pour traiter une demande de navigation.

Toutefois, il existe des situations dans lesquelles vous devez utiliser <xref:System.Windows.Navigation.NavigationService> directement, y compris les éléments suivants :

- Lorsque vous devez instancier un <xref:System.Windows.Controls.Page> à l’aide d’un constructeur sans paramètre.

- Lorsque vous devez définir des propriétés sur la <xref:System.Windows.Controls.Page> avant d’y accéder.

- Lorsque l' <xref:System.Windows.Controls.Page> à laquelle la navigation doit être effectuée ne peut être déterminée qu’au moment de l’exécution.

Dans ces situations, vous devez écrire du code pour lancer la navigation par programmation en appelant la méthode <xref:System.Windows.Navigation.NavigationService.Navigate%2A> de l’objet <xref:System.Windows.Navigation.NavigationService>. Cela nécessite l’obtention d’une référence à un <xref:System.Windows.Navigation.NavigationService>.

#### <a name="getting-a-reference-to-the-navigationservice"></a>Obtention d’une référence à NavigationService

Pour les raisons décrites dans la section [hôtes de navigation](#Navigation_Hosts) , une application [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] peut avoir plusieurs <xref:System.Windows.Navigation.NavigationService>. Cela signifie que votre code a besoin d’un moyen de trouver un <xref:System.Windows.Navigation.NavigationService>, qui est généralement le <xref:System.Windows.Navigation.NavigationService> ayant navigué vers le <xref:System.Windows.Controls.Page> actuel. Vous pouvez obtenir une référence à une <xref:System.Windows.Navigation.NavigationService> en appelant la méthode `static`<xref:System.Windows.Navigation.NavigationService.GetNavigationService%2A?displayProperty=nameWithType>. Pour obtenir les <xref:System.Windows.Navigation.NavigationService> qui naviguent vers une <xref:System.Windows.Controls.Page>particulière, vous passez une référence au <xref:System.Windows.Controls.Page> en tant qu’argument de la méthode <xref:System.Windows.Navigation.NavigationService.GetNavigationService%2A>. Le code suivant montre comment obtenir le <xref:System.Windows.Navigation.NavigationService> pour le <xref:System.Windows.Controls.Page> actuel.

[!code-csharp[NavigationOverviewSnippets#GetNSCODEBEHIND1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/GetNSPage.xaml.cs#getnscodebehind1)]
[!code-csharp[NavigationOverviewSnippets#GetNSCODEBEHIND2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/GetNSPage.xaml.cs#getnscodebehind2)]
[!code-vb[NavigationOverviewSnippets#GetNSCODEBEHIND2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/GetNSPage.xaml.vb#getnscodebehind2)]

En guise de raccourci pour rechercher les <xref:System.Windows.Navigation.NavigationService> pour un <xref:System.Windows.Controls.Page>, <xref:System.Windows.Controls.Page> implémente la propriété <xref:System.Windows.Controls.Page.NavigationService%2A>. L'exemple suivant le démontre.

[!code-csharp[NavigationOverviewSnippets#GetNSShortcutCODEBEHIND1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/GetNSPageShortCut.xaml.cs#getnsshortcutcodebehind1)]
[!code-csharp[NavigationOverviewSnippets#GetNSShortcutCODEBEHIND2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/GetNSPageShortCut.xaml.cs#getnsshortcutcodebehind2)]
[!code-vb[NavigationOverviewSnippets#GetNSShortcutCODEBEHIND2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/GetNSPageShortCut.xaml.vb#getnsshortcutcodebehind2)]

> [!NOTE]
> Une <xref:System.Windows.Controls.Page> peut uniquement obtenir une référence à son <xref:System.Windows.Navigation.NavigationService> quand <xref:System.Windows.Controls.Page> déclenche l’événement <xref:System.Windows.FrameworkElement.Loaded>.

#### <a name="programmatic-navigation-to-a-page-object"></a>Navigation par programmation vers un objet Page

L’exemple suivant montre comment utiliser la <xref:System.Windows.Navigation.NavigationService> pour naviguer par programmation vers une <xref:System.Windows.Controls.Page>. La navigation par programmation est requise, car la <xref:System.Windows.Controls.Page> vers laquelle la navigation est effectuée ne peut être instanciée qu’à l’aide d’un constructeur unique sans paramètre. Le <xref:System.Windows.Controls.Page> avec le constructeur sans paramètre est indiqué dans le balisage et le code suivants.

[!code-xaml[NavigationOverviewSnippets#PageWithNonDefaultConstructorXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithNonDefaultConstructor.xaml#pagewithnondefaultconstructorxaml)]

[!code-csharp[NavigationOverviewSnippets#PageWithNonDefaultConstructorCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithNonDefaultConstructor.xaml.cs#pagewithnondefaultconstructorcodebehind)]
[!code-vb[NavigationOverviewSnippets#PageWithNonDefaultConstructorCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/PageWithNonDefaultConstructor.xaml.vb#pagewithnondefaultconstructorcodebehind)]

Le <xref:System.Windows.Controls.Page> qui accède au <xref:System.Windows.Controls.Page> avec le constructeur sans paramètre est indiqué dans le balisage et le code suivants.

[!code-xaml[NavigationOverviewSnippets#NSNavigationPageXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NSNavigationPage.xaml#nsnavigationpagexaml)]

[!code-csharp[NavigationOverviewSnippets#NSNavigationPageCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NSNavigationPage.xaml.cs#nsnavigationpagecodebehind)]
[!code-vb[NavigationOverviewSnippets#NSNavigationPageCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/NSNavigationPage.xaml.vb#nsnavigationpagecodebehind)]

Quand l’utilisateur clique sur l' <xref:System.Windows.Documents.Hyperlink> sur cet <xref:System.Windows.Controls.Page>, la navigation est lancée en instanciant le <xref:System.Windows.Controls.Page> pour accéder à à l’aide du constructeur sans paramètre et en appelant la méthode <xref:System.Windows.Navigation.NavigationService.Navigate%2A?displayProperty=nameWithType>. <xref:System.Windows.Navigation.NavigationService.Navigate%2A> accepte une référence à l’objet auquel le <xref:System.Windows.Navigation.NavigationService> accède, plutôt qu’à un URI à en-tête pack.

#### <a name="programmatic-navigation-with-a-pack-uri"></a>Navigation par programmation avec un URI à en-tête pack

Si vous devez construire un URI à en-tête pack par programme (lorsque vous pouvez uniquement déterminer l’URI à en-tête pack au moment de l’exécution, par exemple), vous pouvez utiliser la méthode <xref:System.Windows.Navigation.NavigationService.Navigate%2A?displayProperty=nameWithType>. L'exemple suivant le démontre.

[!code-xaml[NavigationOverviewSnippets#NSUriNavigationPageXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NSUriNavigationPage.xaml#nsurinavigationpagexaml)]

[!code-csharp[NavigationOverviewSnippets#NSUriNavigationPageCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NSUriNavigationPage.xaml.cs#nsurinavigationpagecodebehind)]
[!code-vb[NavigationOverviewSnippets#NSUriNavigationPageCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/NSUriNavigationPage.xaml.vb#nsurinavigationpagecodebehind)]

#### <a name="refreshing-the-current-page"></a>Actualisation de la page active

Un <xref:System.Windows.Controls.Page> n’est pas téléchargé s’il a le même URI à en-tête pack que l’URI à en-tête pack stocké dans la propriété <xref:System.Windows.Navigation.NavigationService.Source%2A?displayProperty=nameWithType>. Pour forcer [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] à télécharger à nouveau la page actuelle, vous pouvez appeler la méthode <xref:System.Windows.Navigation.NavigationService.Refresh%2A?displayProperty=nameWithType>, comme indiqué dans l’exemple suivant.

[!code-xaml[NavigationOverviewSnippets#NSRefreshNavigationPageXAML1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NSRefreshNavigationPage.xaml#nsrefreshnavigationpagexaml1)]

[!code-csharp[NavigationOverviewSnippets#NSRefreshNavigationPageCODEBEHIND1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NSRefreshNavigationPage.xaml.cs#nsrefreshnavigationpagecodebehind1)]
[!code-vb[NavigationOverviewSnippets#NSRefreshNavigationPageCODEBEHIND1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/NSRefreshNavigationPage.xaml.vb#nsrefreshnavigationpagecodebehind1)]
[!code-csharp[NavigationOverviewSnippets#NSRefreshNavigationPageCODEBEHIND2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NSRefreshNavigationPage.xaml.cs#nsrefreshnavigationpagecodebehind2)]
[!code-vb[NavigationOverviewSnippets#NSRefreshNavigationPageCODEBEHIND2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/NSRefreshNavigationPage.xaml.vb#nsrefreshnavigationpagecodebehind2)]

<a name="Navigation_Lifetime"></a>

### <a name="navigation-lifetime"></a>Durée de vie de la navigation

Comme vous l’avez vu, il existe de nombreuses façons de démarrer la navigation. Lorsque la navigation est lancée et que la navigation est en cours, vous pouvez suivre et influencer la navigation à l’aide des événements suivants qui sont implémentés par <xref:System.Windows.Navigation.NavigationService> :

- <xref:System.Windows.Navigation.NavigationService.Navigating>., Se produit quand une nouvelle navigation est demandée. Permet d’annuler la navigation.

- <xref:System.Windows.Navigation.NavigationService.NavigationProgress>., Se produit périodiquement au cours d'un téléchargement, pour donner des informations sur la progression de la navigation.

- <xref:System.Windows.Navigation.NavigationService.Navigated>., Se produit quand la page a été localisée et téléchargée.

- <xref:System.Windows.Navigation.NavigationService.NavigationStopped>., Se produit lorsque la navigation est arrêtée (en appelant <xref:System.Windows.Navigation.NavigationService.StopLoading%2A>) ou lorsqu’une nouvelle navigation est demandée alors qu’une navigation en cours est en cours.

- <xref:System.Windows.Navigation.NavigationService.NavigationFailed>., Se produit en cas d’erreur pendant la navigation vers le contenu demandé.

- <xref:System.Windows.Navigation.NavigationService.LoadCompleted>., Se produit quand le contenu cible de la navigation est chargé et analysé, et que son rendu a commencé.

- <xref:System.Windows.Navigation.NavigationService.FragmentNavigation>., Se produit au début de la navigation vers un fragment de contenu, c’est-à-dire :

  - immédiatement, si le fragment désiré est dans le contenu actuel ;

  - après le chargement du contenu source, si le fragment désiré est dans un autre contenu.

Les événements de navigation sont générés dans l’ordre indiqué sur la figure suivante.

![Organigramme de navigation entre les pages](./media/navigation-overview/order-of-navigation-events.png "Organigramme des événements de navigation entre les pages")

En général, un <xref:System.Windows.Controls.Page> n’est pas concerné par ces événements. Il est plus probable qu’une application s’en préoccupe et, pour cette raison, ces événements sont également déclenchés par la classe <xref:System.Windows.Application> :

- <xref:System.Windows.Application.Navigating?displayProperty=nameWithType>

- <xref:System.Windows.Application.NavigationProgress?displayProperty=nameWithType>

- <xref:System.Windows.Application.Navigated?displayProperty=nameWithType>

- <xref:System.Windows.Application.NavigationFailed?displayProperty=nameWithType>

- <xref:System.Windows.Application.NavigationStopped?displayProperty=nameWithType>

- <xref:System.Windows.Application.LoadCompleted?displayProperty=nameWithType>

- <xref:System.Windows.Application.FragmentNavigation?displayProperty=nameWithType>

Chaque fois que <xref:System.Windows.Navigation.NavigationService> déclenche un événement, la classe <xref:System.Windows.Application> déclenche l’événement correspondant. <xref:System.Windows.Controls.Frame> et <xref:System.Windows.Navigation.NavigationWindow> offrent les mêmes événements pour détecter la navigation dans leurs étendues respectives.

Dans certains cas, un <xref:System.Windows.Controls.Page> peut être intéressé par ces événements. Par exemple, un <xref:System.Windows.Controls.Page> peut gérer l’événement <xref:System.Windows.Navigation.NavigationService.Navigating?displayProperty=nameWithType> pour déterminer s’il faut ou non annuler la navigation à partir de lui-même. L'exemple suivant le démontre.

[!code-xaml[NavigationOverviewSnippets#CancelNavigationPageXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/CancelNavigationPage.xaml#cancelnavigationpagexaml)]

[!code-csharp[NavigationOverviewSnippets#CancelNavigationPageCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/CancelNavigationPage.xaml.cs#cancelnavigationpagecodebehind)]
[!code-vb[NavigationOverviewSnippets#CancelNavigationPageCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/CancelNavigationPage.xaml.vb#cancelnavigationpagecodebehind)]

Si vous inscrivez un gestionnaire avec un événement de navigation à partir d’un <xref:System.Windows.Controls.Page>, comme le fait l’exemple précédent, vous devez également annuler l’inscription du gestionnaire d’événements. Si ce n’est pas le cas, il peut y avoir des effets secondaires sur la façon dont la navigation [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] se souvient <xref:System.Windows.Controls.Page> la navigation à l’aide du journal.

<a name="NavigationHistory"></a>

### <a name="remembering-navigation-with-the-journal"></a>Mémorisation de la navigation avec le journal

[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] utilise deux piles pour mémoriser les pages à partir desquelles vous avez navigué : une pile Back et une pile Forward. Lorsque vous naviguez de la <xref:System.Windows.Controls.Page> actuelle vers une nouvelle <xref:System.Windows.Controls.Page> ou vers une <xref:System.Windows.Controls.Page> existante, le <xref:System.Windows.Controls.Page> actuel est ajouté à la *pile de retour*. Lorsque vous naviguez du <xref:System.Windows.Controls.Page> actuel vers le <xref:System.Windows.Controls.Page> précédent, le <xref:System.Windows.Controls.Page> actuel est ajouté à la *pile avant*. La pile Back, la pile Forward et les fonctionnalités qui permettent de les gérer représentent le journal. Chaque élément de la pile Back et de la pile Forward est une instance de la classe <xref:System.Windows.Navigation.JournalEntry>, et est désigné sous le nom d' *entrée de journal*.

#### <a name="navigating-the-journal-from-internet-explorer"></a>Navigation dans le journal à partir d’Internet Explorer

D’un plan conceptuel, le journal fonctionne de la même façon que les boutons **précédent** et **suivant** dans Internet Explorer. Ces boutons sont représentés dans la figure suivante.

![Boutons précédent et suivant](./media/navigation-overview/back-and-forward-navigation.png "Naviguez avec les boutons précédent et suivant.")

Pour les applications XBAP hébergées par Internet Explorer, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] intègre le journal dans le [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] de navigation d’Internet Explorer. Cela permet aux utilisateurs de parcourir les pages d’une application XBAP à l’aide des boutons **précédent**, **suivant**et **pages récentes** dans Internet Explorer.

> [!IMPORTANT]
> Dans Internet Explorer, quand un utilisateur quitte et revient à une application XBAP, seules les entrées de journal pour les pages qui n’étaient pas gardées actives sont conservées dans le journal. Pour plus d’informations sur la conservation des pages actives, consultez [durée de vie de la page et le journal](#PageLifetime) plus loin dans cette rubrique.

Par défaut, le texte de chaque <xref:System.Windows.Controls.Page> qui apparaît dans la liste **pages récentes** d’Internet Explorer est l’URI du <xref:System.Windows.Controls.Page>. Dans de nombreux cas, cela n’est pas particulièrement explicite pour l’utilisateur. Heureusement, vous pouvez changer le texte à l’aide d’une des options suivantes :

1. Valeur de l’attribut `JournalEntry.Name` jointe.

2. Valeur de l’attribut `Page.Title`.

3. Valeur de l’attribut `Page.WindowTitle` et l’URI du <xref:System.Windows.Controls.Page> en cours.

4. URI du <xref:System.Windows.Controls.Page> actuel. (Default)

L’ordre dans lequel les options sont listées correspond à l’ordre de priorité de recherche du texte. Par exemple, si `JournalEntry.Name` est définie, les autres valeurs sont ignorées.

L’exemple suivant utilise l’attribut `Page.Title` pour modifier le texte qui s’affiche pour une entrée de journal.

[!code-xaml[NavigationOverviewSnippets#PageTitleMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithTitle.xaml#pagetitlemarkup1)]
[!code-xaml[NavigationOverviewSnippets#PageTitleMARKUP2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithTitle.xaml#pagetitlemarkup2)]

[!code-csharp[NavigationOverviewSnippets#PageTitleCODEBEHIND1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithTitle.xaml.cs#pagetitlecodebehind1)]
[!code-vb[NavigationOverviewSnippets#PageTitleCODEBEHIND1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/PageWithTitle.xaml.vb#pagetitlecodebehind1)]
[!code-csharp[NavigationOverviewSnippets#PageTitleCODEBEHIND2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithTitle.xaml.cs#pagetitlecodebehind2)]
[!code-vb[NavigationOverviewSnippets#PageTitleCODEBEHIND2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/PageWithTitle.xaml.vb#pagetitlecodebehind2)]

#### <a name="navigating-the-journal-using-wpf"></a>Navigation dans le journal à l’aide de WPF

Bien qu’un utilisateur puisse naviguer dans le journal à l’aide des pages **précédent**, **suivant**et **récent** dans Internet Explorer, vous pouvez également naviguer dans le journal à l’aide des mécanismes déclaratifs et de programmation fournis par [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]. L’une des raisons pour cela consiste à fournir des interfaces utilisateur de navigation personnalisées dans vos pages.

Vous pouvez ajouter de façon déclarative la prise en charge de la navigation dans le journal à l’aide des commandes de navigation exposées par <xref:System.Windows.Input.NavigationCommands>. L’exemple suivant montre comment utiliser la commande de navigation `BrowseBack`.

[!code-xaml[NavigationOverviewSnippets#NavigationCommandsPageXAML1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NavigationCommandsPage.xaml#navigationcommandspagexaml1)]
[!code-xaml[NavigationOverviewSnippets#NavigationCommandsPageXAML2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NavigationCommandsPage.xaml#navigationcommandspagexaml2)]
[!code-xaml[NavigationOverviewSnippets#NavigationCommandsPageXAML3](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NavigationCommandsPage.xaml#navigationcommandspagexaml3)]
[!code-xaml[NavigationOverviewSnippets#NavigationCommandsPageXAML4](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NavigationCommandsPage.xaml#navigationcommandspagexaml4)]

Vous pouvez parcourir le journal par programmation en utilisant l’un des membres suivants de la classe <xref:System.Windows.Navigation.NavigationService> :

- <xref:System.Windows.Navigation.NavigationService.GoBack%2A>

- <xref:System.Windows.Navigation.NavigationService.GoForward%2A>

- <xref:System.Windows.Navigation.NavigationService.CanGoBack%2A>

- <xref:System.Windows.Navigation.NavigationService.CanGoForward%2A>

Le journal peut également être manipulé par programme, comme indiqué dans conservation de [l’état du contenu avec l’historique de navigation](#RetainingContentStateWithNavigationHistory) plus loin dans cette rubrique.

<a name="PageLifetime"></a>

### <a name="page-lifetime-and-the-journal"></a>Durée de vie d’une page et le journal

Considérez une application XBAP avec plusieurs pages qui contiennent du contenu riche, y compris des graphiques, des animations et des médias. L’encombrement mémoire de pages comme celles-ci peut être assez important, en particulier si des médias audio et vidéo sont utilisés. Étant donné que le journal « mémorise » les pages qui ont été parcourues, une telle application XBAP peut rapidement consommer une grande quantité de mémoire.

Pour cette raison, le comportement par défaut du journal est de stocker les métadonnées <xref:System.Windows.Controls.Page> dans chaque entrée du journal plutôt qu’une référence à un objet <xref:System.Windows.Controls.Page>. Lors de la navigation dans une entrée de journal, ses <xref:System.Windows.Controls.Page> métadonnées sont utilisées pour créer une nouvelle instance du <xref:System.Windows.Controls.Page> spécifié. Par conséquent, chaque <xref:System.Windows.Controls.Page> de navigation a la durée de vie illustrée dans la figure suivante.

![Durée de vie de la page](./media/navigation-overview/navigated-page-lifetime.png "Indique la durée de vie lors de la navigation dans une page.")

Bien que l’utilisation du comportement de journalisation par défaut puisse économiser sur la consommation de mémoire, les performances de rendu par page peuvent être réduites ; réinstanciation un <xref:System.Windows.Controls.Page> peut prendre beaucoup de temps, en particulier s’il a beaucoup de contenu. Si vous devez conserver une instance de <xref:System.Windows.Controls.Page> dans le journal, vous pouvez dessiner sur deux techniques pour effectuer cette tâche. Tout d’abord, vous pouvez naviguer par programmation vers un objet <xref:System.Windows.Controls.Page> en appelant la méthode <xref:System.Windows.Navigation.NavigationService.Navigate%2A?displayProperty=nameWithType>.

Deuxièmement, vous pouvez spécifier que [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] conserver une instance d’une <xref:System.Windows.Controls.Page> dans le journal en affectant à la propriété <xref:System.Windows.Controls.Page.KeepAlive%2A> la valeur `true` (la valeur par défaut est `false`). Comme indiqué dans l’exemple suivant, vous pouvez définir <xref:System.Windows.Controls.Page.KeepAlive%2A> de façon déclarative dans le balisage.

[!code-xaml[NavigationOverviewSnippets#KeepAlivePageXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/KeepAlivePage.xaml#keepalivepagexaml)]

La durée de vie d’un <xref:System.Windows.Controls.Page> maintenu actif est légèrement différente de celle d’une qui n’est pas. La première fois qu’une <xref:System.Windows.Controls.Page> qui est gardée actif est parcourue, elle est instanciée comme un <xref:System.Windows.Controls.Page> qui n’est pas gardé actif. Toutefois, étant donné qu’une instance du <xref:System.Windows.Controls.Page> est conservée dans le journal, elle n’est jamais instanciée à nouveau tant qu’elle reste dans le journal. Par conséquent, si une <xref:System.Windows.Controls.Page> a une logique d’initialisation qui doit être appelée à chaque fois que l' <xref:System.Windows.Controls.Page> accède à, vous devez la déplacer du constructeur dans un gestionnaire pour l’événement <xref:System.Windows.FrameworkElement.Loaded>. Comme indiqué dans l’illustration suivante, les événements <xref:System.Windows.FrameworkElement.Loaded> et <xref:System.Windows.FrameworkElement.Unloaded> sont toujours déclenchés chaque fois qu’un <xref:System.Windows.Controls.Page> navigue vers et à partir de, respectivement.

![Lorsque les événements chargés et déchargés sont déclenchés](./media/navigation-overview/loaded-and-unloaded-events.png "Les événements chargés et déchargés sont déclenchés quand une page navigue vers et à partir de.")

Quand un <xref:System.Windows.Controls.Page> n’est pas gardé actif, vous ne devez pas effectuer l’une des opérations suivantes :

- stocker une référence le concernant, même partiellement ;

- inscrire des gestionnaires d’événements auprès d’événements qu’il n’implémente pas.

L’une ou l’autre d’entre elles créera des références qui forceront la conservation de la <xref:System.Windows.Controls.Page> dans la mémoire, même après sa suppression du journal.

En général, vous devez préférer le comportement par défaut <xref:System.Windows.Controls.Page> de ne pas conserver un <xref:System.Windows.Controls.Page> actif. Toutefois, cela a des conséquences sur l’état, comme le décrit la section suivante.

<a name="RetainingContentStateWithNavigationHistory"></a>

### <a name="retaining-content-state-with-navigation-history"></a>Conservation de l’état du contenu avec l’historique de navigation

Si un <xref:System.Windows.Controls.Page> n’est pas gardé actif et qu’il contient des contrôles qui collectent les données de l’utilisateur, qu’arrive-t-il aux données si un utilisateur quitte le <xref:System.Windows.Controls.Page> et revient à ce dernier ? Du point de vue de l’expérience utilisateur, l’utilisateur s’attend à voir les données qu’il a entrées. Malheureusement, étant donné qu’une nouvelle instance de l' <xref:System.Windows.Controls.Page> est créée avec chaque navigation, les contrôles qui ont collecté les données sont réinstanciés et les données sont perdues.

Heureusement, le journal assure la prise en charge de la mémorisation des données dans <xref:System.Windows.Controls.Page> les navigations, y compris les données de contrôle. Plus précisément, l’entrée de journal pour chaque <xref:System.Windows.Controls.Page> agit comme un conteneur temporaire pour l’état de <xref:System.Windows.Controls.Page> associé. Les étapes suivantes décrivent l’utilisation de cette prise en charge lors de la navigation dans un <xref:System.Windows.Controls.Page> :

1. Une entrée pour le <xref:System.Windows.Controls.Page> actuel est ajoutée au journal.

2. L’état de la <xref:System.Windows.Controls.Page> est stocké avec l’entrée de journal de cette page, qui est ajoutée à la pile de retour.

3. Le nouveau <xref:System.Windows.Controls.Page> est accédé.

Lorsque vous accédez à la page <xref:System.Windows.Controls.Page>, à l’aide du journal, les étapes suivantes se produisent :

1. Le <xref:System.Windows.Controls.Page> (l’entrée de journal supérieure sur la pile Back) est instancié.

2. Le <xref:System.Windows.Controls.Page> est actualisé avec l’État qui a été stocké avec l’entrée de journal pour le <xref:System.Windows.Controls.Page>.

3. Le <xref:System.Windows.Controls.Page> accède à nouveau à.

[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] utilise automatiquement cette prise en charge lorsque les contrôles suivants sont utilisés sur un <xref:System.Windows.Controls.Page>:

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

Si un <xref:System.Windows.Controls.Page> utilise ces contrôles, les données qui y sont entrées sont mémorisées sur <xref:System.Windows.Controls.Page> navigations, comme le montre la **couleur préférée** <xref:System.Windows.Controls.ListBox> dans la figure suivante.

![Page avec des contrôles qui mémorisent l’État](./media/navigation-overview/data-remembered-across-page-navigations.png "Les données entrées sont mémorisées au fil des navigations dans les pages.")

Lorsqu’un <xref:System.Windows.Controls.Page> a des contrôles autres que ceux de la liste précédente, ou lorsque l’État est stocké dans des objets personnalisés, vous devez écrire du code pour que le journal mémorise l’État dans <xref:System.Windows.Controls.Page> navigations.

Si vous avez besoin de mémoriser de petits éléments d’État entre les <xref:System.Windows.Controls.Page> les navigations, vous pouvez utiliser des propriétés de dépendance (consultez <xref:System.Windows.DependencyProperty>) qui sont configurées avec l’indicateur de métadonnées <xref:System.Windows.FrameworkPropertyMetadata.Journal%2A?displayProperty=nameWithType>.

Si l’état que votre <xref:System.Windows.Controls.Page> doit mémoriser entre les navigations comprend plusieurs éléments de données, il peut s’avérer moins gourmand en code pour encapsuler votre état dans une seule classe et implémenter l’interface <xref:System.Windows.Navigation.IProvideCustomContentState>.

Si vous devez naviguer dans les différents États d’un <xref:System.Windows.Controls.Page>unique, sans naviguer à partir de la <xref:System.Windows.Controls.Page> elle-même, vous pouvez utiliser <xref:System.Windows.Navigation.IProvideCustomContentState> et <xref:System.Windows.Navigation.NavigationService.AddBackEntry%2A?displayProperty=nameWithType>.

<a name="Cookies"></a>

### <a name="cookies"></a>Cookies

[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] applications peuvent également stocker des données avec des cookies, qui sont créés, mis à jour et supprimés à l’aide des méthodes <xref:System.Windows.Application.SetCookie%2A> et <xref:System.Windows.Application.GetCookie%2A>. Les cookies que vous pouvez créer dans [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] sont les mêmes que ceux utilisés par les autres types d’applications Web. les cookies sont des éléments de données arbitraires stockés par une application sur un ordinateur client pendant ou à travers les sessions d’application. Les données de cookie prennent généralement la forme d’une paire nom/valeur au format suivant.

*Nom* `=` *Valeur*

Lorsque les données sont passées à <xref:System.Windows.Application.SetCookie%2A>, ainsi que la <xref:System.Uri> de l’emplacement pour lequel le cookie doit être défini, un cookie est créé en mémoire et n’est disponible que pendant la durée de la session d’application actuelle. Ce type de cookie est appelé *cookie de session*.

Pour stocker un cookie dans des sessions d’application, vous devez lui ajouter une date d’expiration au format suivant.

*NOM* `=` *VALEUR* `; expires=DAY, DD-MMM-YYYY HH:MM:SS GMT`

Un cookie avec une date d’expiration est stocké dans le dossier fichiers Internet temporaires de l’installation Windows actuelle jusqu’à ce que le cookie expire. Un cookie de ce type est connu sous le nom de *cookie persistant* , car il persiste entre les sessions d’application.

Vous récupérez les cookies de session et les cookies persistants en appelant la méthode <xref:System.Windows.Application.GetCookie%2A>, en passant le <xref:System.Uri> de l’emplacement où le cookie a été défini avec la méthode <xref:System.Windows.Application.SetCookie%2A>.

Voici quelques-unes des façons dont les cookies sont pris en charge dans [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]:

- [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] applications autonomes et les applications XBAP peuvent créer et gérer des cookies.

- Les cookies créés par une application XBAP sont accessibles à partir du navigateur.

- Les applications XBAP du même domaine peuvent créer et partager des cookies.

- Les applications XBAP et les pages HTML du même domaine peuvent créer et partager des cookies.

- Les cookies sont distribués lorsque des applications XBAP et des pages [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] libres effectuent des requêtes Web.

- Les applications XBAP de niveau supérieur et les applications XBAP hébergées dans IFRAMEs peuvent accéder aux cookies.

- La prise en charge des cookies dans [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] est identique pour tous les navigateurs pris en charge.

- Dans Internet Explorer, la stratégie P3P relative aux cookies est respectée par [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], en particulier en ce qui concerne les applications XBAP internes et tierces.

<a name="Structured_Navigation"></a>

### <a name="structured-navigation"></a>Navigation structurée

Si vous avez besoin de passer des données d’un <xref:System.Windows.Controls.Page> à un autre, vous pouvez passer les données en tant qu’arguments à un constructeur sans paramètre du <xref:System.Windows.Controls.Page>. Notez que si vous utilisez cette technique, vous devez garder le <xref:System.Windows.Controls.Page> actif ; Si ce n’est pas le cas, la prochaine fois que vous accédez à la <xref:System.Windows.Controls.Page>, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] réinstancie le <xref:System.Windows.Controls.Page> à l’aide du constructeur sans paramètre.

Votre <xref:System.Windows.Controls.Page> peut également implémenter des propriétés qui sont définies avec les données qui doivent être passées. Toutefois, les choses deviennent délicates quand un <xref:System.Windows.Controls.Page> doit renvoyer des données au <xref:System.Windows.Controls.Page> qui y a accédé. Le problème est que la navigation ne prend pas en charge de manière native des mécanismes permettant de garantir qu’un <xref:System.Windows.Controls.Page> sera renvoyé à après la navigation. Pour l’essentiel, la navigation ne prend pas en charge la sémantique d’appel/de retour. Pour résoudre ce problème, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] fournit la classe <xref:System.Windows.Navigation.PageFunction%601> que vous pouvez utiliser pour vous assurer qu’un <xref:System.Windows.Controls.Page> est retourné à de manière prévisible et structurée. Pour plus d’informations, consultez [vue d’ensemble de la navigation structurée](structured-navigation-overview.md).

<a name="The_NavigationWindow_Class"></a>

## <a name="the-navigationwindow-class"></a>NavigationWindow, classe

À ce stade, vous avez découvert la gamme des services de navigation que vous êtes le plus susceptible d’utiliser pour générer des applications au contenu navigable. Ces services ont été abordés dans le contexte des applications XBAP, bien qu’elles ne soient pas limitées aux applications XBAP. Les systèmes d’exploitation modernes et les applications Windows tirent parti de l’expérience du navigateur des utilisateurs modernes pour incorporer la navigation de style navigateur dans des applications autonomes. Voici quelques exemples usuels :

- **Dictionnaire des synonymes** : pour naviguer parmi des choix de mots.

- **Explorateur de fichiers** : pour naviguer parmi des fichiers et des dossiers.

- **Assistants** : pour décomposer une tâche complexe en plusieurs pages parmi lesquelles il est possible de naviguer. Par exemple, l’Assistant composants de Windows gère l’ajout et la suppression de fonctionnalités Windows.

Pour incorporer la navigation de style navigateur dans vos applications autonomes, vous pouvez utiliser la classe <xref:System.Windows.Navigation.NavigationWindow>. <xref:System.Windows.Navigation.NavigationWindow> dérive de <xref:System.Windows.Window> et l’étend avec la même prise en charge de la navigation fournie par les applications XBAP. Vous pouvez utiliser <xref:System.Windows.Navigation.NavigationWindow> en tant que fenêtre principale de votre application autonome ou en tant que fenêtre secondaire telle qu’une boîte de dialogue.

Pour implémenter un <xref:System.Windows.Navigation.NavigationWindow>, comme avec la plupart des classes de niveau supérieur dans [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] (<xref:System.Windows.Window>, <xref:System.Windows.Controls.Page>, etc.), vous utilisez une combinaison de balisage et de code-behind. L'exemple suivant le démontre.

[!code-xaml[IntroToNavNavigationWindowSnippets#NavigationWindowMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/IntroToNavNavigationWindowSnippets/CSharp/MainWindow.xaml#navigationwindowmarkup)]

[!code-csharp[IntroToNavNavigationWindowSnippets#NavigationWindowCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/IntroToNavNavigationWindowSnippets/CSharp/MainWindow.xaml.cs#navigationwindowcodebehind)]
[!code-vb[IntroToNavNavigationWindowSnippets#NavigationWindowCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/IntroToNavNavigationWindowSnippets/VisualBasic/MainWindow.xaml.vb#navigationwindowcodebehind)]

Ce code crée une <xref:System.Windows.Navigation.NavigationWindow> qui navigue automatiquement vers un <xref:System.Windows.Controls.Page> (HomePage. Xaml) lors de l’ouverture de l' <xref:System.Windows.Navigation.NavigationWindow>. Si le <xref:System.Windows.Navigation.NavigationWindow> est la fenêtre d’application principale, vous pouvez utiliser l’attribut `StartupUri` pour le lancer. Ce cas de figure est illustré dans le balisage suivant.

[!code-xaml[IntroToNavNavigationWindowSnippets#AppLaunchNavWindow](~/samples/snippets/csharp/VS_Snippets_Wpf/IntroToNavNavigationWindowSnippets/CSharp/App.xaml#applaunchnavwindow)]

L’illustration suivante montre les <xref:System.Windows.Navigation.NavigationWindow> en tant que fenêtre principale d’une application autonome.

![Fenêtre principale](./media/navigation-overview/navigation-window-as-main-window.png "Fenêtre de navigation comme fenêtre principale")

À partir de la figure, vous pouvez voir que le <xref:System.Windows.Navigation.NavigationWindow> a un titre, même s’il n’a pas été défini dans le code d’implémentation <xref:System.Windows.Navigation.NavigationWindow> de l’exemple précédent. Au lieu de cela, le titre est défini à l’aide de la propriété <xref:System.Windows.Controls.Page.WindowTitle%2A>, qui est illustrée dans le code suivant.

[!code-xaml[IntroToNavNavigationWindowSnippets#HomePageMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/IntroToNavNavigationWindowSnippets/CSharp/HomePage.xaml#homepagemarkup1)]
[!code-xaml[IntroToNavNavigationWindowSnippets#HomePageMARKUP2](~/samples/snippets/csharp/VS_Snippets_Wpf/IntroToNavNavigationWindowSnippets/CSharp/HomePage.xaml#homepagemarkup2)]

La définition des propriétés <xref:System.Windows.Controls.Page.WindowWidth%2A> et <xref:System.Windows.Controls.Page.WindowHeight%2A> affecte également le <xref:System.Windows.Navigation.NavigationWindow>.

En général, vous implémentez votre propre <xref:System.Windows.Navigation.NavigationWindow> lorsque vous devez personnaliser son comportement ou son apparence. Si vous ne faites ni l’un, ni l’autre, vous pouvez utiliser un raccourci. Si vous spécifiez l’URI à en-tête pack d’un <xref:System.Windows.Controls.Page> comme <xref:System.Windows.Application.StartupUri%2A> dans une application autonome, <xref:System.Windows.Application> crée automatiquement une <xref:System.Windows.Navigation.NavigationWindow> pour héberger le <xref:System.Windows.Controls.Page>. Le balisage suivant montre comment y parvenir.

[!code-xaml[IntroToNavNavigationWindowSnippets#AppLaunchPage](~/samples/snippets/csharp/VS_Snippets_Wpf/IntroToNavNavigationWindowSnippets/CSharp/AnotherApp.xaml#applaunchpage)]

Si vous souhaitez qu’une fenêtre d’application secondaire telle qu’une boîte de dialogue soit une <xref:System.Windows.Navigation.NavigationWindow>, vous pouvez utiliser le code de l’exemple suivant pour l’ouvrir.

[!code-csharp[IntroToNavNavigationWindowSnippets#CreateNWDialogBox](~/samples/snippets/csharp/VS_Snippets_Wpf/IntroToNavNavigationWindowSnippets/CSharp/DialogOwnerWindow.xaml.cs#createnwdialogbox)]
[!code-vb[IntroToNavNavigationWindowSnippets#CreateNWDialogBox](~/samples/snippets/visualbasic/VS_Snippets_Wpf/IntroToNavNavigationWindowSnippets/VisualBasic/DialogOwnerWindow.xaml.vb#createnwdialogbox)]

L’illustration suivante affiche le résultat.

![Boîte de dialogue](./media/navigation-overview/navigation-window-as-dialog-box.png "Fenêtre de navigation en tant que boîte de dialogue")

Comme vous pouvez le voir, <xref:System.Windows.Navigation.NavigationWindow> affiche les boutons **précédent** et **suivant** de style Internet Explorer qui permettent aux utilisateurs de naviguer dans le journal. Ces boutons fournissent la même expérience utilisateur, comme le montre la figure suivante.

![Boutons précédent et suivant dans une NavigationWindow](./media/navigation-overview/back-and-forward-buttons-in-navigation-window.png "Boutons précédent et suivant dans une fenêtre de navigation")

Si vos pages fournissent leur propre prise en charge de la navigation dans le journal et l’interface utilisateur, vous pouvez masquer les boutons **précédent** et **suivant** affichés par <xref:System.Windows.Navigation.NavigationWindow> en affectant à la propriété <xref:System.Windows.Navigation.NavigationWindow.ShowsNavigationUI%2A> la valeur `false`.

Vous pouvez également utiliser la prise en charge de la personnalisation dans [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] pour remplacer le [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] du <xref:System.Windows.Navigation.NavigationWindow> lui-même.

<a name="Frame_in_Standalone_Applications"></a>

## <a name="the-frame-class"></a>Frame, classe

Le navigateur et les <xref:System.Windows.Navigation.NavigationWindow> sont des fenêtres qui hébergent du contenu navigable. Dans certains cas, les applications ont un contenu qui n’a pas besoin d’être hébergé par une fenêtre entière. À la place, ce contenu est hébergé dans un autre contenu. Vous pouvez insérer du contenu navigable dans d’autres contenus à l’aide de la classe <xref:System.Windows.Controls.Frame>. <xref:System.Windows.Controls.Frame> fournit la même prise en charge que les <xref:System.Windows.Navigation.NavigationWindow> et les XBAP.

L’exemple suivant montre comment ajouter une <xref:System.Windows.Controls.Frame> à un <xref:System.Windows.Controls.Page> de manière déclarative à l’aide de l’élément `Frame`.

[!code-xaml[NavigationOverviewSnippets#FrameHostPageXAML1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHostPage.xaml#framehostpagexaml1)]
[!code-xaml[NavigationOverviewSnippets#FrameHostPageXAML2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHostPage.xaml#framehostpagexaml2)]
[!code-xaml[NavigationOverviewSnippets#FrameHostPageXAML3](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHostPage.xaml#framehostpagexaml3)]

Ce balisage définit l’attribut `Source` de l’élément `Frame` avec un URI à en-tête pack pour le <xref:System.Windows.Controls.Page> auquel le <xref:System.Windows.Controls.Frame> doit accéder initialement. L’illustration suivante montre une application XBAP avec un <xref:System.Windows.Controls.Page> avec une <xref:System.Windows.Controls.Frame> qui a navigué entre plusieurs pages.

![Frame qui a navigué entre plusieurs pages](./media/navigation-overview/frame-navigation-between-multiple-pages.png "Cela montre une navigation de frame entre plusieurs pages.")

Vous n’avez pas à utiliser <xref:System.Windows.Controls.Frame> à l’intérieur du contenu d’une <xref:System.Windows.Controls.Page>. Il est également courant d’héberger un <xref:System.Windows.Controls.Frame> à l’intérieur du contenu d’un <xref:System.Windows.Window>.

Par défaut, <xref:System.Windows.Controls.Frame> utilise uniquement son propre journal en l’absence d’un autre journal. Si un <xref:System.Windows.Controls.Frame> fait partie du contenu hébergé à l’intérieur d’un <xref:System.Windows.Navigation.NavigationWindow> ou d’une application XBAP, <xref:System.Windows.Controls.Frame> utilise le journal qui appartient au <xref:System.Windows.Navigation.NavigationWindow> ou à l’application XBAP. Parfois, il est possible qu’un <xref:System.Windows.Controls.Frame> doive être responsable de son propre journal. L’une des raisons à cela est d’autoriser la navigation dans les journaux dans les pages hébergées par un <xref:System.Windows.Controls.Frame>. Cela est illustré par la figure suivante.

![Diagramme de frame et de page](./media/navigation-overview/journal-navigation-within-pages-hosted-by-a-frame.png "Cela montre la navigation dans les journaux dans les pages hébergées par un frame.")

Dans ce cas, vous pouvez configurer la <xref:System.Windows.Controls.Frame> pour utiliser son propre journal en affectant à la propriété <xref:System.Windows.Controls.Frame.JournalOwnership%2A> de la <xref:System.Windows.Controls.Frame> la valeur <xref:System.Windows.Navigation.JournalOwnership.OwnsJournal>. Ce cas de figure est illustré dans le balisage suivant.

[!code-xaml[NavigationOverviewSnippets#FrameHostPageOwnJournalXAML1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHostPageOwnJournal.xaml#framehostpageownjournalxaml1)]
[!code-xaml[NavigationOverviewSnippets#FrameHostPageOwnJournalXAML2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHostPageOwnJournal.xaml#framehostpageownjournalxaml2)]
[!code-xaml[NavigationOverviewSnippets#FrameHostPageOwnJournalXAML3](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHostPageOwnJournal.xaml#framehostpageownjournalxaml3)]

L’illustration suivante montre l’effet de la navigation dans un <xref:System.Windows.Controls.Frame> qui utilise son propre journal.

![Frame qui utilise son propre journal](./media/navigation-overview/frame-uses-its-own-journal.png "Cela montre l’effet de la navigation dans un frame qui utilise son propre journal.")

Notez que les entrées de journal sont affichées par le [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] de navigation dans la <xref:System.Windows.Controls.Frame>, plutôt que par Internet Explorer.

> [!NOTE]
> Si un <xref:System.Windows.Controls.Frame> fait partie du contenu hébergé dans une <xref:System.Windows.Window>, <xref:System.Windows.Controls.Frame> utilise son propre journal et, par conséquent, affiche sa propre [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]de navigation.

Si vous avez besoin d’un <xref:System.Windows.Controls.Frame> pour fournir son propre journal sans afficher les [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]de navigation, vous pouvez masquer le [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] de navigation en affectant à la <xref:System.Windows.Controls.Frame.NavigationUIVisibility%2A> la valeur <xref:System.Windows.Visibility.Hidden>. Ce cas de figure est illustré dans le balisage suivant.

[!code-xaml[NavigationOverviewSnippets#FrameHostPageHidesUIXAML1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHostPageOwnHiddenJournal.xaml#framehostpagehidesuixaml1)]
[!code-xaml[NavigationOverviewSnippets#FrameHostPageHidesUIXAML2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHostPageOwnHiddenJournal.xaml#framehostpagehidesuixaml2)]
[!code-xaml[NavigationOverviewSnippets#FrameHostPageHidesUIXAML3](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHostPageOwnHiddenJournal.xaml#framehostpagehidesuixaml3)]

<a name="Navigation_Hosts"></a>

## <a name="navigation-hosts"></a>Hôtes de navigation

<xref:System.Windows.Controls.Frame> et <xref:System.Windows.Navigation.NavigationWindow> sont des classes qui sont appelées des hôtes de navigation. Un *hôte de navigation* est une classe qui peut accéder au contenu et l’afficher. Pour ce faire, chaque hôte de navigation utilise son propre <xref:System.Windows.Navigation.NavigationService> et son propre journal. La construction de base d’un hôte de navigation est illustrée dans la figure suivante.

![Diagrammes du navigateur](./media/navigation-overview/navigation-host-construction.png "Construction de base d’un hôte de navigation")

Fondamentalement, cela permet à <xref:System.Windows.Navigation.NavigationWindow> et à <xref:System.Windows.Controls.Frame> d’offrir la même prise en charge de navigation qu’une application XBAP fournit lorsqu’elle est hébergée dans le navigateur.

Outre l’utilisation de <xref:System.Windows.Navigation.NavigationService> et d’un journal, les hôtes de navigation implémentent les mêmes membres que <xref:System.Windows.Navigation.NavigationService> implémente. Cela est illustré par la figure suivante.

![Journal dans un frame et dans un NavigationWindow](./media/navigation-overview/navigation-window-and-frame.png "Fenêtre et frame de navigation")

Cela vous permet de programmer la prise en charge de la navigation directement par rapport à eux. Vous pouvez envisager cela si vous devez fournir une [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] de navigation personnalisée pour un <xref:System.Windows.Controls.Frame> hébergé dans un <xref:System.Windows.Window>. En outre, les deux types implémentent des membres supplémentaires liés à la navigation, y compris `BackStack` (<xref:System.Windows.Navigation.NavigationWindow.BackStack%2A?displayProperty=nameWithType>, <xref:System.Windows.Controls.Frame.BackStack%2A?displayProperty=nameWithType>) et `ForwardStack` (<xref:System.Windows.Navigation.NavigationWindow.ForwardStack%2A?displayProperty=nameWithType>, <xref:System.Windows.Controls.Frame.ForwardStack%2A?displayProperty=nameWithType>), qui vous permettent d’énumérer les entrées de journal dans la pile Back et la pile Forward, respectivement.

Comme cela a déjà été mentionné, plusieurs journaux peuvent exister dans une application. L’exemple suivant illustre ce cas de figure.

![Plusieurs journaux au sein d’une même application](./media/navigation-overview/multiple-journals-in-one-application.png "Il s’agit d’un exemple de plusieurs journaux dans une application.")

<a name="Navigating_to_Content_Other_than_Pages"></a>

## <a name="navigating-to-content-other-than-xaml-pages"></a>Navigation vers un autre contenu que des pages XAML

Tout au long de cette rubrique, les applications XBAP <xref:System.Windows.Controls.Page> et Pack ont été utilisées pour illustrer les différentes fonctionnalités de navigation de [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]. Toutefois, une <xref:System.Windows.Controls.Page> qui est compilée dans une application n’est pas le seul type de contenu vers lequel une navigation peut être établie, et les applications XBAP à en-tête pack ne sont pas le seul moyen d’identifier le contenu.

Comme le montre cette section, vous pouvez également accéder à des fichiers [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], des fichiers HTML et des objets libres.

<a name="Navigating_to_Loose_XAML_Files"></a>

### <a name="navigating-to-loose-xaml-files"></a>Navigation vers des fichiers XAML libre

Un fichier [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] libre est un fichier ayant les caractéristiques suivantes :

- Contient uniquement [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] (autrement dit, aucun code).

- Il a une déclaration d’espace de noms appropriée.

- Son nom de fichier porte l’extension .xaml.

Par exemple, considérez le contenu suivant qui est stocké en tant que fichier [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] libre, Person. Xaml.

[!code-xaml[NavigationOverviewSnippets#LooseXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/Person.xaml#loosexaml)]

Quand vous double-cliquez sur le fichier, le navigateur s’ouvre et navigue vers le contenu, qu’il affiche. Ce cas est illustré dans la figure suivante.

![Affichage du contenu dans le fichier Person. XAML](./media/navigation-overview/contents-of-person-xaml-file.png "Affiche le contenu du fichier Person. XAML.")

Vous pouvez afficher un fichier [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] libre à partir des éléments suivants :

- site web sur la machine locale, un intranet ou Internet ;

- Partage de fichiers UNC (Universal Naming Convention).

- disque local.

Un fichier de [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] libre peut être ajouté aux favoris du navigateur, ou être la page d’hébergement du navigateur.

> [!NOTE]
> Pour plus d’informations sur la publication et le lancement de pages [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] libres, consultez [déploiement d’une application WPF](deploying-a-wpf-application-wpf.md).

L’une des limitations par rapport au [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] faible est que vous pouvez uniquement héberger du contenu qui peut être exécuté en toute sécurité avec une confiance partielle. Par exemple, `Window` ne peut pas être l’élément racine d’un fichier de [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] libre. Pour plus d’informations, consultez [Sécurité de confiance partielle de WPF](../wpf-partial-trust-security.md).

<a name="Navigating_to_HTML_Files_Using_Frame"></a>

### <a name="navigating-to-html-files-by-using-frame"></a>Navigation vers des fichiers HTML à l’aide d’un Frame

Comme vous pouvez vous y attendre, vous pouvez également accéder au code HTML. Vous devez simplement fournir un URI qui utilise le schéma http. Par exemple, la [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] suivante montre une <xref:System.Windows.Controls.Frame> qui accède à une page HTML.

[!code-xaml[NavigationOverviewSnippets#FrameHtmlNavMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHTMLNavPage.xaml#framehtmlnavmarkup)]

La navigation vers le code HTML nécessite des autorisations spéciales. Par exemple, vous ne pouvez pas naviguer à partir d’une application XBAP qui s’exécute dans le bac à sable de sécurité de confiance partielle de la zone Internet. Pour plus d’informations, consultez [Sécurité de confiance partielle de WPF](../wpf-partial-trust-security.md).

<a name="Navigating_to_HTML_Files_Using_WebBrowser"></a>

### <a name="navigating-to-html-files-by-using-the-webbrowser-control"></a>Navigation vers des fichiers HTML à l’aide du contrôle WebBrowser

Le contrôle <xref:System.Windows.Controls.WebBrowser> prend en charge l’hébergement de documents HTML, la navigation et l’interopérabilité du code managé/de script. Pour plus d’informations sur le contrôle de <xref:System.Windows.Controls.WebBrowser>, consultez <xref:System.Windows.Controls.WebBrowser>.

Comme <xref:System.Windows.Controls.Frame>, accéder au code HTML à l’aide de <xref:System.Windows.Controls.WebBrowser> nécessite des autorisations spéciales. Par exemple, à partir d’une application de confiance partielle, vous pouvez naviguer uniquement jusqu’au code HTML situé sur le site d’origine. Pour plus d’informations, consultez [Sécurité de confiance partielle de WPF](../wpf-partial-trust-security.md).

<a name="Navigating_to_Objects"></a>

### <a name="navigating-to-custom-objects"></a>Navigation vers des objets personnalisés

Si vous avez des données qui sont stockées en tant qu’objets personnalisés, une façon d’afficher ces données consiste à créer un <xref:System.Windows.Controls.Page> avec le contenu lié à ces objets (consultez [vue d’ensemble](../../../desktop-wpf/data/data-binding-overview.md)de la liaison de données). En revanche, si vous n’avez pas besoin de la charge de traitement supplémentaire liée à la création d’une page entière juste pour afficher les objets, vous pouvez naviguer directement vers ces derniers.

Considérez la classe `Person` qui est implémentée dans le code suivant.

[!code-csharp[NavigateToObjectSnippets#PersonClassCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigateToObjectSnippets/CSharp/Person.cs#personclasscode)]
[!code-vb[NavigateToObjectSnippets#PersonClassCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigateToObjectSnippets/VisualBasic/Person.vb#personclasscode)]

Pour y accéder, vous appelez la méthode <xref:System.Windows.Navigation.NavigationWindow.Navigate%2A?displayProperty=nameWithType>, comme le montre le code suivant.

[!code-xaml[NavigateToObjectSnippets#PageThatNavsToObject1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigateToObjectSnippets/CSharp/HomePage.xaml#pagethatnavstoobject1)]
[!code-xaml[NavigateToObjectSnippets#PageThatNavsToObject2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigateToObjectSnippets/CSharp/HomePage.xaml#pagethatnavstoobject2)]
[!code-xaml[NavigateToObjectSnippets#PageThatNavsToObject3](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigateToObjectSnippets/CSharp/HomePage.xaml#pagethatnavstoobject3)]

[!code-csharp[NavigateToObjectSnippets#PageThatNavsToObjectCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigateToObjectSnippets/CSharp/HomePage.xaml.cs#pagethatnavstoobjectcodebehind)]
[!code-vb[NavigateToObjectSnippets#PageThatNavsToObjectCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigateToObjectSnippets/VisualBasic/HomePage.xaml.vb#pagethatnavstoobjectcodebehind)]

L’illustration suivante affiche le résultat.

![Page qui navigue vers une classe](./media/navigation-overview/page-navigates-to-an-object.png "Il s’agit d’un exemple de page qui navigue vers un objet.")

Dans cette illustration, vous pouvez voir que rien d’utile n’est affiché. En fait, la valeur affichée est la valeur de retour de la méthode `ToString` pour l’objet **Person** ; par défaut, il s’agit de la seule valeur que [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] pouvez utiliser pour représenter votre objet. Vous pouvez substituer la méthode `ToString` pour retourner des informations plus explicites, bien qu’il ne s’agisse toujours que d’une valeur de chaîne. L’une des techniques que vous pouvez utiliser pour tirer parti des fonctionnalités de présentation de [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] consiste à utiliser un modèle de données. Vous pouvez implémenter un modèle de données que [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] pouvez associer à un objet d’un type particulier. Le code suivant montre un modèle de données pour l’objet `Person`.

[!code-xaml[NavigateToObjectSnippets#DataTemplateMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigateToObjectSnippets/CSharp/App.xaml#datatemplatemarkup)]

Ici, le modèle de données est associé au type de `Person` à l’aide de l’extension de balisage `x:Type` dans l’attribut `DataType`. Le modèle de données lie ensuite les éléments `TextBlock` (consultez <xref:System.Windows.Controls.TextBlock>) aux propriétés de la classe `Person`. L’illustration suivante montre l’apparence mise à jour de l’objet `Person`.

![Navigation vers une classe qui a un modèle de données](./media/navigation-overview/navigating-to-a-class.png "Navigation vers une classe qui a un modèle de données.")

Cette technique présente un avantage, elle vous permet d’afficher vos objets de manière cohérente dans la totalité de votre application grâce à la réutilisation du modèle de données.

Pour plus d’informations sur les modèles de données, consultez [vue d’ensemble](../data/data-templating-overview.md)des modèles de données.

<a name="Security"></a>

## <a name="security"></a>Sécurité

[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] la prise en charge de la navigation permet de naviguer sur Internet et permet aux applications d’héberger du contenu tiers. Pour protéger les applications et les utilisateurs contre les comportements dangereux, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] fournit une variété de [fonctionnalités de sécurité](../security-wpf.md) qui sont abordées dans sécurité et [sécurité de confiance partielle de WPF](../wpf-partial-trust-security.md).

## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Application.SetCookie%2A>
- <xref:System.Windows.Application.GetCookie%2A>
- [Vue d’ensemble de la gestion d’applications](application-management-overview.md)
- [URI à en-tête pack dans WPF](pack-uris-in-wpf.md)
- [Vue d’ensemble de la navigation structurée](structured-navigation-overview.md)
- [Vue d’ensemble des topologies de navigation](navigation-topologies-overview.md)
- [Rubriques de guide pratique](navigation-how-to-topics.md)
- [Déploiement d’une application WPF](deploying-a-wpf-application-wpf.md)
