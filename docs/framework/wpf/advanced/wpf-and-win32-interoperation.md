---
title: WPF et interopérabilité Win32
titleSuffix: ''
ms.date: 03/30/2017
helpviewer_keywords:
- hosting WPF content in Win32 window [WPF]
- HWND interop [WPF]
- Win32 code [WPF], WPF interoperation
- interoperability [WPF], Win32
ms.assetid: 0ffbde0d-701d-45a3-a6fa-dd71f4d9772e
ms.openlocfilehash: 7b7c3ed8f9833094ce1e836c11f84132ae84def2
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76735229"
---
# <a name="wpf-and-win32-interoperation"></a>Interopérabilité WPF et Win32

Cette rubrique fournit une vue d’ensemble de l’interopérabilité de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] et du code Win32. [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] propose un environnement de création d'applications élaboré. Toutefois, lorsque vous avez un investissement important dans du code Win32, il peut être plus efficace de réutiliser une partie de ce code.

<a name="basics"></a>

## <a name="wpf-and-win32-interoperation-basics"></a>Notions de base de l’interopérabilité WPF et Win32

Il existe deux techniques de base pour l’interopérabilité entre les [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] et le code Win32.

- Hébergez [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] contenu dans une fenêtre Win32. Grâce à cette technique, vous pouvez utiliser les fonctionnalités graphiques avancées de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] dans le cadre d’une application et d’une fenêtre Win32 standard.

- Hébergez une fenêtre Win32 dans le contenu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Avec cette technique, vous pouvez utiliser un contrôle Win32 personnalisé existant dans le contexte d’autres [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] du contenu, et passer des données entre les limites.

Cette rubrique présente les concepts inhérents à chacune de ces techniques. Pour une illustration plus orientée code de l’hébergement d' [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] dans Win32, consultez [procédure pas à pas : Hébergement de contenu WPF dans Win32](walkthrough-hosting-wpf-content-in-win32.md). Pour une illustration plus orientée code de l’hébergement de Win32 dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], consultez [procédure pas à pas : Hébergement d’un contrôle Win32 dans WPF](walkthrough-hosting-a-win32-control-in-wpf.md).

<a name="projects"></a>

## <a name="wpf-interoperation-projects"></a>Projets d’interopérabilité WPF

les API [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] sont du code managé, mais la plupart des programmes Win32 existants sont écrits C++en non managés.  Vous ne pouvez pas appeler des API [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] à partir d’un véritable programme non managé. Toutefois, à l’aide de l’option `/clr` avec le C++ compilateur Microsoft Visual, vous pouvez créer un programme managé non managé mixte dans lequel vous pouvez mélanger en toute transparence des appels d’API managés et non managés.

Une complication au niveau du projet est que vous ne pouvez pas compiler [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] C++ fichiers dans un projet.  Il existe toutefois plusieurs techniques de division du projet qui permettent de contourner ce problème.

- Créez une C# dll qui contient toutes vos pages [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] en tant qu’assembly compilé, puis faites C++ en sorte que votre exécutable inclue cette dll comme référence.

- Créer un C# exécutable pour le contenu de la [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] et faire référence à une C++ dll qui contient le contenu Win32.

- Utilisez <xref:System.Windows.Markup.XamlReader.Load%2A> pour charger des [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] au moment de l’exécution, au lieu de compiler votre [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].

- N’utilisez pas de [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], et écrivez toutes vos [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] dans le code, en créant l’arborescence d’éléments à partir de <xref:System.Windows.Application>.

Utilisez la technique qui vous convient le mieux.

> [!NOTE]
> Si vous n’avez pas C++déjà utilisé/CLI, vous remarquerez peut-être des mots clés « nouveaux », tels que `gcnew` et `nullptr` dans les exemples de code d’interopérabilité. Ces mots clés remplacent l’ancienne syntaxe de double trait de soulignement (`__gc`) et fournissent une syntaxe plus naturelle C++pour le code managé dans.  Pour en savoir plus sur C++les fonctionnalités managées/CLI, consultez [extensions de composant pour les plateformes Runtime](/cpp/windows/component-extensions-for-runtime-platforms).

<a name="hwnds"></a>

## <a name="how-wpf-uses-hwnds"></a>Utilisation des HWND par WPF

Pour tirer le meilleur parti de l’interopérabilité HWND dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], vous devez comprendre de quelle façon [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] utilise les HWND. Pour un HWND, vous ne pouvez pas mélanger [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] rendu avec le rendu DirectX ou le rendu GDI/GDI+. Ceci a plusieurs implications. D’une part, pour pouvoir combiner ces modèles de rendu, vous devez créer une solution d’interopérabilité et utiliser les segments d’interopérabilité désignés pour chaque modèle de rendu à utiliser. D’autre part, le comportement de rendu crée une restriction d’« espace de rendu » (« airspace » en anglais) relative aux objectifs de la solution d’interopérabilité. Le concept d’« espace de rendu » est expliqué en détail dans la rubrique [Vue d’ensemble des régions de technologie](technology-regions-overview.md).

Tous les éléments [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] affichés sont stockés par un HWND. Lorsque vous créez un [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Window>, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] crée un HWND de niveau supérieur et utilise une <xref:System.Windows.Interop.HwndSource> pour placer le <xref:System.Windows.Window> et son contenu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] dans le HWND.  Le reste du contenu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] dans l’application partage ce HWND spécifique. Les menus, les zones de liste déroulante et les autres menus contextuels constituent une exception à ce principe. Ces éléments créent leur propre fenêtre de niveau supérieur, ce qui explique pourquoi un menu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] peut potentiellement dépasser le bord du HWND de fenêtre qui le contient. Lorsque vous utilisez <xref:System.Windows.Interop.HwndHost> pour placer un HWND à l’intérieur d' [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] informe Win32 comment positionner le nouveau HWND enfant par rapport au [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Window> HWND.

La transparence dans et entre les HWND est un concept connexe des HWND. Ceci est également expliqué dans la rubrique [Vue d’ensemble des régions de technologie](technology-regions-overview.md).

<a name="hosting_a_wpf_page"></a>

## <a name="hosting-wpf-content-in-a-microsoft-win32-window"></a>Hébergement de contenu WPF dans une fenêtre Microsoft Win32

La clé de l’hébergement d’un [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] sur une fenêtre Win32 est la classe <xref:System.Windows.Interop.HwndSource>. Cette classe encapsule le contenu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] dans une fenêtre Win32, afin que le contenu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] puisse être incorporé dans votre [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] en tant que fenêtre enfant. L’approche suivante combine les [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Win32 et dans une même application.

1. Implémentez le contenu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] (l’élément racine du contenu) comme une classe managée. En règle générale, la classe hérite de l’une des classes pouvant contenir plusieurs éléments enfants et/ou utilisée en tant qu’élément racine, par exemple <xref:System.Windows.Controls.DockPanel> ou <xref:System.Windows.Controls.Page>. Dans les étapes suivantes, cette classe est appelée « classe de contenu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] » et les instances de la classe sont appelées « objets de contenu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ».

2. Implémenter une application Windows C++avec/CLI. Si vous démarrez avec une C++ application non managée existante, vous pouvez généralement lui permettre d’appeler du code managé en modifiant les paramètres de votre projet de façon à inclure l’indicateur `/clr` du compilateur (la portée complète de ce qui peut être nécessaire pour prendre en charge `/clr` compilation n’est pas décrite dans cette rubrique).

3. Définissez le thread unique cloisonné (STA) comme modèle de thread. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] utilise ce modèle de thread.

4. Gérez la notification WM_CREATE dans votre procédure de fenêtre.

5. Dans le gestionnaire (ou une fonction appelée par le gestionnaire), effectuez les opérations suivantes :

    1. Créez un objet <xref:System.Windows.Interop.HwndSource> avec le HWND de la fenêtre parente comme paramètre `parent`.

    2. Créez une instance de la classe de contenu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].

    3. Assignez une référence à l’objet de contenu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] à la propriété <xref:System.Windows.Interop.HwndSource.RootVisual%2A> de l’objet <xref:System.Windows.Interop.HwndSource>.

    4. La propriété <xref:System.Windows.Interop.HwndSource.Handle%2A> de l’objet <xref:System.Windows.Interop.HwndSource> contient le handle de fenêtre (HWND). Pour obtenir un HWND que vous pouvez utiliser dans la partie non managée de l'application, effectuez un cast de `Handle.ToPointer()` en HWND.

6. Implémentez une classe managée qui contient un champ statique comportant une référence à l’objet de contenu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Cette classe vous permet d’obtenir une référence à l’objet de contenu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] à partir de votre code Win32, mais plus important encore, il empêche vos <xref:System.Windows.Interop.HwndSource> de faire l’objet d’un garbage collection par inadvertance.

7. Recevez les notifications de l’objet de contenu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] en attachant un gestionnaire à un ou plusieurs événements de l’objet de contenu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].

8. Communiquez avec l’objet de contenu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] en utilisant la référence que vous avez stockée dans le champ statique pour définir les propriétés, les méthodes d’appel, etc.

> [!NOTE]
> Vous pouvez faire une partie ou la totalité de la définition de la classe de contenu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] de la première étape dans [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] à l’aide de la classe partielle par défaut de la classe de contenu, à condition de créer un assembly distinct et de le référencer. Même si vous incluez généralement un objet <xref:System.Windows.Application> dans le cadre de la compilation du [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] dans un assembly, vous n’utilisez pas ce <xref:System.Windows.Application> dans le cadre de l’interopérabilité, vous utilisez simplement une ou plusieurs des classes racine pour les fichiers [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] référencés par l’application et référencent leurs classes partielles. Le reste de la procédure est quasiment identique à celle présentée ci-dessus.
>
> Chacune de ces étapes est illustrée par du code dans la rubrique [Procédure pas à pas : hébergement de contenu WPF dans Win32](walkthrough-hosting-wpf-content-in-win32.md).

<a name="hosting_an_hwnd"></a>

## <a name="hosting-a-microsoft-win32-window-in-wpf"></a>Hébergement d’une fenêtre Microsoft Win32 dans WPF

La clé de l’hébergement d’une fenêtre Win32 dans d’autres [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] contenu est la classe <xref:System.Windows.Interop.HwndHost>. Cette classe inclut la fenêtre dans un wrapper dans un élément [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] qui peut être ajouté à une arborescence d’éléments [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. <xref:System.Windows.Interop.HwndHost> prend également en charge les API qui vous permettent d’effectuer des tâches telles que traiter des messages pour la fenêtre hébergée. La procédure de base est la suivante :

1. Créez une arborescence d’éléments pour une application [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] (à l’aide de code ou de balises). Recherchez un point approprié et autorisé dans l’arborescence d’éléments où l’implémentation de <xref:System.Windows.Interop.HwndHost> peut être ajoutée en tant qu’élément enfant. Dans les étapes suivantes, cet élément est appelé élément de réservation.

2. Dérivez de <xref:System.Windows.Interop.HwndHost> pour créer un objet qui contient votre contenu Win32.

3. Dans cette classe hôte, substituez la méthode <xref:System.Windows.Interop.HwndHost> <xref:System.Windows.Interop.HwndHost.BuildWindowCore%2A>. Retournez le HWND de la fenêtre hébergée. Vous pouvez inclure le ou les contrôles réels dans un wrapper comme une fenêtre enfant de la fenêtre retournée. L’inclusion des contrôles dans un wrapper dans une fenêtre hôte permet au contenu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] de recevoir facilement les notifications des contrôles. Cette technique permet de corriger certains problèmes Win32 relatifs à la gestion des messages au niveau de la limite du contrôle hébergé.

4. Substituez les méthodes de <xref:System.Windows.Interop.HwndHost> <xref:System.Windows.Interop.HwndHost.DestroyWindowCore%2A> et <xref:System.Windows.Interop.HwndHost.WndProc%2A>. L’objectif est d’effectuer un nettoyage et de supprimer les références au contenu hébergé, en particulier si vous avez créé des références à des objets non managés.

5. Dans votre fichier code-behind, créez une instance de la classe d’hébergement de contrôle et définissez-la comme enfant de l’élément de réservation. En général, vous utilisez un gestionnaire d’événements tel que <xref:System.Windows.FrameworkElement.Loaded>, ou vous utilisez le constructeur de classe partielle. Vous pouvez également ajouter le contenu d’interopérabilité via un comportement au moment de l’exécution.

6. Traitez les messages de fenêtre sélectionnés, tels que les notifications de contrôle. Il y a deux approches possibles, qui fournissent un accès identique au flux de messages. Votre choix est donc essentiellement motivé par le côté pratique de la programmation.

    - Implémentez le traitement des messages pour tous les messages (pas seulement les messages d’arrêt) dans votre remplacement de la méthode <xref:System.Windows.Interop.HwndHost> <xref:System.Windows.Interop.HwndHost.WndProc%2A>.

    - Faire en sorte que l’élément [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] d’hébergement traite les messages en gérant l’événement <xref:System.Windows.Interop.HwndHost.MessageHook>. Cet événement est déclenché pour chaque message qui est envoyé à la procédure de fenêtre principale de la fenêtre hébergée.

    - Vous ne pouvez pas traiter les messages de Windows qui sont en dehors du processus à l’aide de <xref:System.Windows.Interop.HwndHost.WndProc%2A>.

7. Communiquez avec la fenêtre hébergée en effectuant un appel de code non managé pour appeler la fonction `SendMessage` non managée.

L’exécution de ces étapes crée une application qui fonctionne avec des entrées de la souris. Vous pouvez ajouter la prise en charge de la tabulation pour la fenêtre hébergée en implémentant l’interface <xref:System.Windows.Interop.IKeyboardInputSink>.

Chacune de ces étapes est illustrée par du code dans la rubrique [Procédure pas à pas : hébergement d’un contrôle Win32 dans WPF](walkthrough-hosting-a-win32-control-in-wpf.md).

### <a name="hwnds-inside-wpf"></a>HWND dans WPF

Vous pouvez considérer <xref:System.Windows.Interop.HwndHost> comme un contrôle spécial. (Techniquement, <xref:System.Windows.Interop.HwndHost> est une <xref:System.Windows.FrameworkElement> classe dérivée, et non une classe dérivée <xref:System.Windows.Controls.Control>, mais elle peut être considérée comme un contrôle à des fins d’interopérabilité.) <xref:System.Windows.Interop.HwndHost> soustrait la nature Win32 sous-jacente du contenu hébergé de telle sorte que le reste de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] considère le contenu hébergé comme un autre objet de contrôle, qui doit afficher et traiter l’entrée. <xref:System.Windows.Interop.HwndHost> se comporte généralement comme tout autre [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.FrameworkElement>, bien qu’il existe des différences importantes entre la sortie (dessin et graphiques) et l’entrée (souris et clavier) en fonction des limitations de ce que les HWND sous-jacents peuvent prendre en charge.

#### <a name="notable-differences-in-output-behavior"></a>Principales différences dans le comportement de sortie

- <xref:System.Windows.FrameworkElement>, qui est la classe de base <xref:System.Windows.Interop.HwndHost>, a de nombreuses propriétés qui impliquent des modifications apportées à l’interface utilisateur. Celles-ci incluent des propriétés telles que <xref:System.Windows.FrameworkElement.FlowDirection%2A?displayProperty=nameWithType>, qui modifie la disposition des éléments dans cet élément en tant que parent. Toutefois, la plupart de ces propriétés ne sont pas mappées à des équivalents Win32 possibles, même si ces équivalents peuvent exister. Un trop grand nombre de ces propriétés et de leurs significations reposent essentiellement sur la technologie de rendu, ce qui rend les mappages difficiles à utiliser. Par conséquent, la définition de propriétés telles que <xref:System.Windows.FrameworkElement.FlowDirection%2A> sur <xref:System.Windows.Interop.HwndHost> n’a aucun effet.

- les <xref:System.Windows.Interop.HwndHost> ne peuvent pas être pivotées, mises à l’échelle, inclinées ou affectées par une transformation.

- <xref:System.Windows.Interop.HwndHost> ne prend pas en charge la propriété <xref:System.Windows.UIElement.Opacity%2A> (fusion alpha). Si le contenu à l’intérieur du <xref:System.Windows.Interop.HwndHost> effectue des opérations <xref:System.Drawing> qui incluent des informations alpha, qui n’est pas une violation, mais le <xref:System.Windows.Interop.HwndHost> dans son ensemble prend uniquement en charge l’opacité = 1,0 (100%).

- <xref:System.Windows.Interop.HwndHost> s’affiche au-dessus des autres éléments [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] dans la même fenêtre de niveau supérieur. Toutefois, un menu <xref:System.Windows.Controls.ToolTip> ou <xref:System.Windows.Controls.ContextMenu> généré est une fenêtre de niveau supérieur distincte, ce qui se comportera correctement avec <xref:System.Windows.Interop.HwndHost>.

- <xref:System.Windows.Interop.HwndHost> ne respecte pas la zone de découpage de son <xref:System.Windows.UIElement>parent. Cela peut poser problème si vous tentez de placer une classe <xref:System.Windows.Interop.HwndHost> à l’intérieur d’une zone de défilement ou d' <xref:System.Windows.Controls.Canvas>.

#### <a name="notable-differences-in-input-behavior"></a>Principales différences dans le comportement d’entrée

- En général, alors que les appareils d’entrée sont étendus dans la région Win32 hébergée <xref:System.Windows.Interop.HwndHost>, les événements d’entrée sont directement dirigés vers Win32.

- Lorsque la souris se trouve sur le <xref:System.Windows.Interop.HwndHost>, votre application ne reçoit pas d’événements de souris [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] et la valeur de la propriété [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.UIElement.IsMouseOver%2A> est `false`.

- Si le <xref:System.Windows.Interop.HwndHost> a le focus clavier, votre application ne recevra pas d’événements de clavier [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] et la valeur de la propriété [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.UIElement.IsKeyboardFocusWithin%2A> sera `false`.

- Lorsque le focus se trouve dans le <xref:System.Windows.Interop.HwndHost> et que les modifications apportées à un autre contrôle à l’intérieur du <xref:System.Windows.Interop.HwndHost>, votre application ne reçoit pas les événements [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.UIElement.GotFocus> ou <xref:System.Windows.UIElement.LostFocus>.

- Les propriétés et les événements de stylet associés sont analogues et ne signalent pas d’informations lorsque le stylet se trouve sur <xref:System.Windows.Interop.HwndHost>.

<a name="tabbing_mnemonics_accelerators"></a>

## <a name="tabbing-mnemonics-and-accelerators"></a>Tabulation, mnémoniques et accélérateurs

Les interfaces <xref:System.Windows.Interop.IKeyboardInputSink> et <xref:System.Windows.Interop.IKeyboardInputSite> vous permettent de créer une expérience clavier transparente pour les applications mixtes [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] et Win32 :

- Tabulation entre les composants Win32 et [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]

- Mnémoniques et accélérateurs fonctionnant quand le focus est sur un composant Win32 et sur un composant WPF.

Les classes <xref:System.Windows.Interop.HwndHost> et <xref:System.Windows.Interop.HwndSource> fournissent toutes deux des implémentations de <xref:System.Windows.Interop.IKeyboardInputSink>, mais elles peuvent ne pas gérer tous les messages d’entrée souhaités pour des scénarios plus avancés. Dans ce cas, substituez les méthodes appropriées pour obtenir le comportement de clavier souhaité.

Les interfaces assurent uniquement la prise en charge de ce qui se passe sur la transition entre les [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] et les régions Win32. Dans la région Win32, le comportement de tabulation est entièrement contrôlé par la logique Win32 implémentée pour la tabulation, le cas échéant.

## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Interop.HwndHost>
- <xref:System.Windows.Interop.HwndSource>
- <xref:System.Windows.Interop>
- [Procédure pas à pas : hébergement d'un contrôle Win32 dans WPF](walkthrough-hosting-a-win32-control-in-wpf.md)
- [Procédure pas à pas : hébergement de contenu WPF dans Win32](walkthrough-hosting-wpf-content-in-win32.md)
