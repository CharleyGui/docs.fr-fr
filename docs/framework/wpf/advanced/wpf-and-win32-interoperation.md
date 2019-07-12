---
title: Interopérabilité WPF et Win32
ms.date: 03/30/2017
helpviewer_keywords:
- hosting WPF content in Win32 window [WPF]
- HWND interop [WPF]
- Win32 code [WPF], WPF interoperation
- interoperability [WPF], Win32
ms.assetid: 0ffbde0d-701d-45a3-a6fa-dd71f4d9772e
ms.openlocfilehash: c9e94eef6caf5b4c9a64623d5c578af89acc616a
ms.sourcegitcommit: 83ecdf731dc1920bca31f017b1556c917aafd7a0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/12/2019
ms.locfileid: "67859925"
---
# <a name="wpf-and-win32-interoperation"></a>Interopérabilité WPF et Win32
Cette rubrique fournit une vue d’ensemble de l’interopérabilité du code [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] et [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]. [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] propose un environnement de création d'applications élaboré. Toutefois, si vous avez déjà écrit beaucoup de code [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)], vous avez peut-être intérêt à réutiliser une partie de ce code.  

<a name="basics"></a>   
## <a name="wpf-and-win32-interoperation-basics"></a>Notions de base de l’interopérabilité WPF et Win32  
 Il existe deux techniques principales pour permettre l’interopérabilité du code [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] et [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)].  
  
- Hébergement de contenu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] dans une fenêtre [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]. Cette technique vous permet d’utiliser les fonctionnalités graphiques avancées de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] dans le framework d’une application et d’une fenêtre [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] standard.  
  
- Hébergement d’une fenêtre [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] dans du contenu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Grâce à cette technique, vous pouvez utiliser un contrôle [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] personnalisé existant dans un autre contenu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] et passer des données au-delà des limites.  
  
 Cette rubrique présente les concepts inhérents à chacune de ces techniques. Pour obtenir une illustration plus orientée code d’hébergement [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] dans [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)], consultez [procédure pas à pas : Hébergement de contenu WPF dans Win32](walkthrough-hosting-wpf-content-in-win32.md). Pour obtenir une illustration plus orientée code d’hébergement [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], consultez [procédure pas à pas : Hébergement d’un contrôle Win32 dans WPF](walkthrough-hosting-a-win32-control-in-wpf.md).  
  
<a name="projects"></a>   
## <a name="wpf-interoperation-projects"></a>Projets d’interopérabilité WPF  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] API sont gérées code, mais la plupart des existant [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] programmes sont écrits en non managé [!INCLUDE[TLA2#tla_cpp](../../../../includes/tla2sharptla-cpp-md.md)].  Vous ne pouvez pas appeler [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] API à partir d’un véritable non managée du programme. Toutefois, en utilisant le `/clr` option avec la [!INCLUDE[TLA#tla_visualcpp](../../../../includes/tlasharptla-visualcpp-md.md)] compilateur, vous pouvez créer un programme/non managé mixte dans lequel vous pouvez combiner des appels d’API managées et en toute transparence.  
  
 L’un des problèmes au niveau du projet est l’impossibilité de compiler des fichiers [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] dans un projet [!INCLUDE[TLA2#tla_cpp](../../../../includes/tla2sharptla-cpp-md.md)].  Il existe toutefois plusieurs techniques de division du projet qui permettent de contourner ce problème.  
  
- Créer une DLL c# qui contient tous les votre [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] pages comme un assembly compilé, puis demandez à votre [!INCLUDE[TLA2#tla_cpp](../../../../includes/tla2sharptla-cpp-md.md)] exécutable inclure [!INCLUDE[TLA2#tla_dll](../../../../includes/tla2sharptla-dll-md.md)] en tant que référence.  
  
- Créer un c# exécutable pour le [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] de contenu, et de référencer un [!INCLUDE[TLA2#tla_cpp](../../../../includes/tla2sharptla-cpp-md.md)] [!INCLUDE[TLA2#tla_dll](../../../../includes/tla2sharptla-dll-md.md)] qui contient le [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] contenu.  
  
- Utilisez <xref:System.Windows.Markup.XamlReader.Load%2A> charge tous [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] au moment de l’exécution, au lieu de compiler votre [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].  
  
- N’utilisez pas [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] du tout et écrire toutes vos [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] dans le code, la création de l’arborescence d’éléments à partir de <xref:System.Windows.Application>.  
  
 Utilisez la technique qui vous convient le mieux.  
  
> [!NOTE]
>  Si vous n’avez pas utilisé [!INCLUDE[TLA#tla_cppcli](../../../../includes/tlasharptla-cppcli-md.md)] auparavant, vous remarquerez peut-être la présence de « nouveaux » mots clés, comme `gcnew` et `nullptr`, dans les exemples de code d’interopérabilité. Ces mots clés remplacent l’ancienne syntaxe avec un double trait de soulignement (`__gc`) et constituent une syntaxe plus naturelle pour le code managé dans [!INCLUDE[TLA2#tla_cpp](../../../../includes/tla2sharptla-cpp-md.md)].  Pour en savoir plus sur les fonctionnalités managées de [!INCLUDE[TLA#tla_cppcli](../../../../includes/tlasharptla-cppcli-md.md)], consultez [Extensions de composant pour les plateformes d’exécution](/cpp/windows/component-extensions-for-runtime-platforms) et [Hello, C++/CLI](https://go.microsoft.com/fwlink/?LinkId=98739).  
  
<a name="hwnds"></a>   
## <a name="how-wpf-uses-hwnds"></a>Utilisation des HWND par WPF  
 Pour tirer le meilleur parti de l’interopérabilité HWND dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], vous devez comprendre de quelle façon [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] utilise les HWND. Pour un HWND, vous ne pouvez pas combiner du rendu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] avec du rendu [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)] ou [!INCLUDE[TLA2#tla_gdi](../../../../includes/tla2sharptla-gdi-md.md)] / [!INCLUDE[TLA2#tla_gdiplus](../../../../includes/tla2sharptla-gdiplus-md.md)]. Ceci a plusieurs implications. D’une part, pour pouvoir combiner ces modèles de rendu, vous devez créer une solution d’interopérabilité et utiliser les segments d’interopérabilité désignés pour chaque modèle de rendu à utiliser. D’autre part, le comportement de rendu crée une restriction d’« espace de rendu » (« airspace » en anglais) relative aux objectifs de la solution d’interopérabilité. Le concept d’« espace de rendu » est expliqué en détail dans la rubrique [Vue d’ensemble des régions de technologie](technology-regions-overview.md).  
  
 Tous les éléments [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] affichés sont stockés par un HWND. Lorsque vous créez un [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Window>, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] crée un HWND de niveau supérieur et utilise un <xref:System.Windows.Interop.HwndSource> pour placer le <xref:System.Windows.Window> et son [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] contenu dans le HWND.  Le reste du contenu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] dans l’application partage ce HWND spécifique. Les menus, les zones de liste déroulante et les autres menus contextuels constituent une exception à ce principe. Ces éléments créent leur propre fenêtre de niveau supérieur, ce qui explique pourquoi un menu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] peut potentiellement dépasser le bord du HWND de fenêtre qui le contient. Lorsque vous utilisez <xref:System.Windows.Interop.HwndHost> pour placer un HWND dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] informe [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] comment positionner le nouveau HWND enfant par rapport à la [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Window> HWND.  
  
 La transparence dans et entre les HWND est un concept connexe des HWND. Ceci est également expliqué dans la rubrique [Vue d’ensemble des régions de technologie](technology-regions-overview.md).  
  
<a name="hosting_a_wpf_page"></a>   
## <a name="hosting-wpf-content-in-a-microsoft-win32-window"></a>Hébergement de contenu WPF dans une fenêtre Microsoft Win32  
 La clé à l’hébergement d’un [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] sur un [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] fenêtre est la <xref:System.Windows.Interop.HwndSource> classe. Cette classe inclut le contenu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] dans un wrapper dans une fenêtre [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)], ce qui permet au contenu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] d’être incorporé dans votre [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] sous la forme d’une fenêtre enfant. L'approche suivante combine [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] et [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] dans une même application.  
  
1. Implémentez le contenu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] (l’élément racine du contenu) comme une classe managée. En règle générale, la classe hérite d’une des classes qui peuvent contenir plusieurs éléments enfants et/ou être utilisée comme un élément racine, tel que <xref:System.Windows.Controls.DockPanel> ou <xref:System.Windows.Controls.Page>. Dans les étapes suivantes, cette classe est appelée « classe de contenu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] » et les instances de la classe sont appelées « objets de contenu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ».  
  
2. Implémentez une application [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] avec [!INCLUDE[TLA2#tla_cppcli](../../../../includes/tla2sharptla-cppcli-md.md)]. Si vous démarrez avec une application [!INCLUDE[TLA2#tla_cpp](../../../../includes/tla2sharptla-cpp-md.md)] non managée existante, vous pouvez généralement lui permettre d’appeler du code managé en modifiant les paramètres du projet pour inclure l’indicateur de compilateur `/clr` (cette rubrique ne décrit pas de façon exhaustive les éléments potentiellement nécessaires pour la prise en charge de la compilation `/clr`).  
  
3. Définissez le thread unique cloisonné (STA) comme modèle de thread. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] utilise ce modèle de thread.  
  
4. Gérez la notification WM_CREATE dans votre procédure de fenêtre.  
  
5. Dans le gestionnaire (ou une fonction appelée par le gestionnaire), effectuez les opérations suivantes :  
  
    1. Créer un nouveau <xref:System.Windows.Interop.HwndSource> objet avec le HWND de fenêtre parente en tant que son `parent` paramètre.  
  
    2. Créez une instance de la classe de contenu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
    3. Assignez une référence à la [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] objet de contenu pour le <xref:System.Windows.Interop.HwndSource> objet <xref:System.Windows.Interop.HwndSource.RootVisual%2A> propriété.  
  
    4. Le <xref:System.Windows.Interop.HwndSource> objet <xref:System.Windows.Interop.HwndSource.Handle%2A> propriété contient le handle de fenêtre (HWND). Pour obtenir un HWND que vous pouvez utiliser dans la partie non managée de l'application, effectuez un cast de `Handle.ToPointer()` en HWND.  
  
6. Implémentez une classe managée qui contient un champ statique comportant une référence à l’objet de contenu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Cette classe vous permet d’obtenir une référence à la [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] objet de contenu à partir de votre [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] code, mais plus important encore, il empêche votre <xref:System.Windows.Interop.HwndSource> ne soient pas par inadvertance par le garbage collecté.  
  
7. Recevez les notifications de l’objet de contenu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] en attachant un gestionnaire à un ou plusieurs événements de l’objet de contenu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
8. Communiquez avec l’objet de contenu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] en utilisant la référence que vous avez stockée dans le champ statique pour définir les propriétés, les méthodes d’appel, etc.  
  
> [!NOTE]
>  Vous pouvez faire une partie ou la totalité de la définition de la classe de contenu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] de la première étape dans [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] à l’aide de la classe partielle par défaut de la classe de contenu, à condition de créer un assembly distinct et de le référencer. Bien que vous incluez généralement un <xref:System.Windows.Application> objet dans le cadre de la compilation le [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] dans un assembly, vous n’arrivent pas à les utiliser <xref:System.Windows.Application> dans le cadre de l’interopérabilité, vous utilisez simplement une ou plusieurs des classes racine pour [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] les fichiers référencés à l’application et référencez leurs classes partielles. Le reste de la procédure est quasiment identique à celle présentée ci-dessus.  
>   
>  Chacune de ces étapes est illustrée par du code dans la rubrique [procédure pas à pas : Hébergement de contenu WPF dans Win32](walkthrough-hosting-wpf-content-in-win32.md).  
  
<a name="hosting_an_hwnd"></a>   
## <a name="hosting-a-microsoft-win32-window-in-wpf"></a>Hébergement d’une fenêtre Microsoft Win32 dans WPF  
 La clé à l’hébergement d’un [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] fenêtre dans les autres [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] le contenu est le <xref:System.Windows.Interop.HwndHost> classe. Cette classe inclut la fenêtre dans un wrapper dans un élément [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] qui peut être ajouté à une arborescence d’éléments [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. <xref:System.Windows.Interop.HwndHost> prend également en charge les API qui vous permettent d’effectuer des tâches telles que le traitement des messages de la fenêtre hébergée. La procédure de base est la suivante :  
  
1. Créez une arborescence d’éléments pour une application [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] (à l’aide de code ou de balises). Rechercher un point approprié et autorisé dans l’arborescence d’éléments où les <xref:System.Windows.Interop.HwndHost> implémentation peut être ajoutée comme un élément enfant. Dans les étapes suivantes, cet élément est appelé élément de réservation.  
  
2. Dériver de <xref:System.Windows.Interop.HwndHost> pour créer un objet qui contient votre [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] contenu.  
  
3. Dans cette classe hôte, substituez le <xref:System.Windows.Interop.HwndHost> méthode <xref:System.Windows.Interop.HwndHost.BuildWindowCore%2A>. Retournez le HWND de la fenêtre hébergée. Vous pouvez inclure le ou les contrôles réels dans un wrapper comme une fenêtre enfant de la fenêtre retournée. L’inclusion des contrôles dans un wrapper dans une fenêtre hôte permet au contenu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] de recevoir facilement les notifications des contrôles. Cette technique permet d’éviter certains problèmes de [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] liés à la gestion des messages à la limite d’un contrôle hébergé.  
  
4. Remplacer le <xref:System.Windows.Interop.HwndHost> méthodes <xref:System.Windows.Interop.HwndHost.DestroyWindowCore%2A> et <xref:System.Windows.Interop.HwndHost.WndProc%2A>. L’objectif est d’effectuer un nettoyage et de supprimer les références au contenu hébergé, en particulier si vous avez créé des références à des objets non managés.  
  
5. Dans votre fichier code-behind, créez une instance de la classe d’hébergement de contrôle et définissez-la comme enfant de l’élément de réservation. En général, vous utiliseriez un gestionnaire d’événements tel que <xref:System.Windows.FrameworkElement.Loaded>, ou utilisez le constructeur de classe partielle. Vous pouvez également ajouter le contenu d’interopérabilité via un comportement au moment de l’exécution.  
  
6. Traitez les messages de fenêtre sélectionnés, tels que les notifications de contrôle. Il y a deux approches possibles, qui fournissent un accès identique au flux de messages. Votre choix est donc essentiellement motivé par le côté pratique de la programmation.  
  
    - Implémentez traitement des messages pour tous les messages (pas seulement les messages d’arrêt) dans la substitution de la <xref:System.Windows.Interop.HwndHost> méthode <xref:System.Windows.Interop.HwndHost.WndProc%2A>.  
  
    - Hébergement [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] élément traiter les messages en gérant la <xref:System.Windows.Interop.HwndHost.MessageHook> événement. Cet événement est déclenché pour chaque message qui est envoyé à la procédure de fenêtre principale de la fenêtre hébergée.  
  
    - Vous ne pouvez pas traiter les messages à partir de windows qui sont hors processus à l’aide <xref:System.Windows.Interop.HwndHost.WndProc%2A>.  
  
7. Communiquez avec la fenêtre hébergée en effectuant un appel de code non managé pour appeler la fonction `SendMessage` non managée.  
  
 L’exécution de ces étapes crée une application qui fonctionne avec des entrées de la souris. Vous pouvez ajouter la prise en charge pour la fenêtre hébergée en implémentant le <xref:System.Windows.Interop.IKeyboardInputSink> interface.  
  
 Chacune de ces étapes est illustrée par du code dans la rubrique [procédure pas à pas : Hébergement d’un contrôle Win32 dans WPF](walkthrough-hosting-a-win32-control-in-wpf.md).  
  
### <a name="hwnds-inside-wpf"></a>HWND dans WPF  
 Vous pouvez considérer <xref:System.Windows.Interop.HwndHost> comme un contrôle spécial. (Techniquement, <xref:System.Windows.Interop.HwndHost> est un <xref:System.Windows.FrameworkElement> classe dérivée, pas un <xref:System.Windows.Controls.Control> classe dérivée, mais il peut être considéré comme un contrôle à des fins d’interopérabilité.) <xref:System.Windows.Interop.HwndHost> effectue l’abstraction sous-jacent [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] nature du contenu hébergé telles que le reste de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] considère le contenu hébergé comme un autre objet de contrôle, qui doit restituer et traiter l’entrée. <xref:System.Windows.Interop.HwndHost> se comporte généralement comme tout autre [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.FrameworkElement>, bien qu’il existe certaines différences importantes autour de sortie (dessin et graphiques) et entrées (souris et clavier) dues aux limitations de HWND sous-jacents peuvent prendre en charge.  
  
#### <a name="notable-differences-in-output-behavior"></a>Principales différences dans le comportement de sortie  
  
- <xref:System.Windows.FrameworkElement>, qui est la <xref:System.Windows.Interop.HwndHost> classe de base, a de nombreuses propriétés qui impliquent la modification de l’interface utilisateur. Ceux-ci incluent des propriétés comme <xref:System.Windows.FrameworkElement.FlowDirection%2A?displayProperty=nameWithType>, ce qui modifie la disposition des éléments au sein de cet élément en tant que parent. Toutefois, la plupart des propriétés concernées ne sont pas mappées aux équivalents possibles de [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)], le cas échéant. Un trop grand nombre de ces propriétés et de leurs significations reposent essentiellement sur la technologie de rendu, ce qui rend les mappages difficiles à utiliser. Par conséquent, définissant les propriétés telles que <xref:System.Windows.FrameworkElement.FlowDirection%2A> sur <xref:System.Windows.Interop.HwndHost> n’a aucun effet.  
  
- <xref:System.Windows.Interop.HwndHost> ne peut pas être pivotée, à l’échelle, inclinée ou sinon affectées par une transformation.  
  
- <xref:System.Windows.Interop.HwndHost> ne prend pas en charge le <xref:System.Windows.UIElement.Opacity%2A> propriété (fusion alpha). Si le contenu de la <xref:System.Windows.Interop.HwndHost> effectue <xref:System.Drawing> opérations qui incluent des informations alpha, qui n’est lui-même pas une violation, mais la <xref:System.Windows.Interop.HwndHost> comme ensemble prend uniquement en charge l’opacité = 1.0 (100 %).  
  
- <xref:System.Windows.Interop.HwndHost> s’affiche au-dessus des autres [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] éléments dans la même fenêtre de niveau supérieur. Toutefois, un <xref:System.Windows.Controls.ToolTip> ou <xref:System.Windows.Controls.ContextMenu> menu généré est une fenêtre de niveau supérieur distincte et il se comporte correctement avec <xref:System.Windows.Interop.HwndHost>.  
  
- <xref:System.Windows.Interop.HwndHost> ne respecte pas la zone de découpage de son parent <xref:System.Windows.UIElement>. Il s’agit potentiellement d’un problème si vous tentez de placer un <xref:System.Windows.Interop.HwndHost> classe à l’intérieur d’une zone de défilement ou <xref:System.Windows.Controls.Canvas>.  
  
#### <a name="notable-differences-in-input-behavior"></a>Principales différences dans le comportement d’entrée  
  
- En règle générale, tandis que les périphériques d’entrée sont délimitées au sein de la <xref:System.Windows.Interop.HwndHost> hébergé [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] région, les événements d’entrée accéder directement à [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)].  
  
- Alors que la souris est sur le <xref:System.Windows.Interop.HwndHost>, votre application ne reçoit pas [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] événements de souris et la valeur de la [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] propriété <xref:System.Windows.UIElement.IsMouseOver%2A> sera `false`.  
  
- Bien que le <xref:System.Windows.Interop.HwndHost> a le focus clavier, votre application ne reçoit pas [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] événements de clavier et la valeur de la [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] propriété <xref:System.Windows.UIElement.IsKeyboardFocusWithin%2A> sera `false`.  
  
- Lorsque le focus se trouve dans le <xref:System.Windows.Interop.HwndHost> et modifications apportées à un autre contrôle à l’intérieur de la <xref:System.Windows.Interop.HwndHost>, votre application ne reçoit pas les [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] événements <xref:System.Windows.UIElement.GotFocus> ou <xref:System.Windows.UIElement.LostFocus>.  
  
- Liés des événements et propriétés de stylet sont semblables et ne signalent pas d’informations lorsque le stylet est sur <xref:System.Windows.Interop.HwndHost>.  
  
<a name="tabbing_mnemonics_accelerators"></a>   
## <a name="tabbing-mnemonics-and-accelerators"></a>Tabulation, mnémoniques et accélérateurs  
 Le <xref:System.Windows.Interop.IKeyboardInputSink> et <xref:System.Windows.Interop.IKeyboardInputSite> interfaces permettent de créer une expérience de clavier transparente pour mixte [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] et [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] applications :  
  
- Tabulation entre des composants [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] et [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
- Mnémoniques et accélérateurs fonctionnant quand le focus est sur un composant Win32 et sur un composant WPF.  
  
 Le <xref:System.Windows.Interop.HwndHost> et <xref:System.Windows.Interop.HwndSource> les classes fournissent des implémentations de <xref:System.Windows.Interop.IKeyboardInputSink>, mais ils ne peuvent pas gérer tous les messages d’entrée que vous souhaitez pour des scénarios plus avancés. Dans ce cas, substituez les méthodes appropriées pour obtenir le comportement de clavier souhaité.  
  
 Les interfaces assurent uniquement la prise en charge des événements qui ont lieu lors de la transition entre les zones [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] et [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]. Dans la zone [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)], le comportement de tabulation est entièrement déterminé par la logique [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] implémentée pour la tabulation, le cas échéant.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Interop.HwndHost>
- <xref:System.Windows.Interop.HwndSource>
- <xref:System.Windows.Interop>
- [Procédure pas à pas : Hébergement d’un contrôle Win32 dans WPF](walkthrough-hosting-a-win32-control-in-wpf.md)
- [Procédure pas à pas : Hébergement de contenu WPF dans Win32](walkthrough-hosting-wpf-content-in-win32.md)
