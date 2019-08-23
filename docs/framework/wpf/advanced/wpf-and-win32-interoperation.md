---
title: Interopérabilité WPF et Win32
ms.date: 03/30/2017
helpviewer_keywords:
- hosting WPF content in Win32 window [WPF]
- HWND interop [WPF]
- Win32 code [WPF], WPF interoperation
- interoperability [WPF], Win32
ms.assetid: 0ffbde0d-701d-45a3-a6fa-dd71f4d9772e
ms.openlocfilehash: d13f4ce37dba45dc99f0481043d80640e73d833d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69917470"
---
# <a name="wpf-and-win32-interoperation"></a>Interopérabilité WPF et Win32
Cette rubrique fournit une vue d’ensemble de l’interopérabilité du code [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] et [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]. [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] propose un environnement de création d'applications élaboré. Toutefois, si vous avez déjà écrit beaucoup de code [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)], vous avez peut-être intérêt à réutiliser une partie de ce code.  

<a name="basics"></a>   
## <a name="wpf-and-win32-interoperation-basics"></a>Notions de base de l’interopérabilité WPF et Win32  
 Il existe deux techniques principales pour permettre l’interopérabilité du code [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] et [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)].  
  
- Hébergement de contenu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] dans une fenêtre [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]. Cette technique vous permet d’utiliser les fonctionnalités graphiques avancées de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] dans le framework d’une application et d’une fenêtre [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] standard.  
  
- Hébergement d’une fenêtre [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] dans du contenu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Grâce à cette technique, vous pouvez utiliser un contrôle [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] personnalisé existant dans un autre contenu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] et passer des données au-delà des limites.  
  
 Cette rubrique présente les concepts inhérents à chacune de ces techniques. Pour une illustration plus orientée code de l' [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] hébergement [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]dans, [consultez Procédure pas à pas: Hébergement du contenu WPF dans](walkthrough-hosting-wpf-content-in-win32.md)Win32. Pour une illustration plus orientée code de l' [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] hébergement [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]dans, [consultez Procédure pas à pas: Hébergement d’un contrôle Win32 dans](walkthrough-hosting-a-win32-control-in-wpf.md)WPF.  
  
<a name="projects"></a>   
## <a name="wpf-interoperation-projects"></a>Projets d’interopérabilité WPF  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]Les API sont du code managé, mais [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] la plupart des programmes existants sont écrits C++en non managés.  Vous ne pouvez [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] pas appeler d’API à partir d’un véritable programme non managé. Toutefois, à l’aide `/clr` de l’option [!INCLUDE[TLA#tla_visualcpp](../../../../includes/tlasharptla-visualcpp-md.md)] avec le compilateur, vous pouvez créer un programme managé non managé mixte dans lequel vous pouvez mélanger en toute transparence des appels d’API managés et non managés.  
  
 Une complication au niveau du projet est que vous ne [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] pouvez pas compiler C++ de fichiers dans un projet.  Il existe toutefois plusieurs techniques de division du projet qui permettent de contourner ce problème.  
  
- Créez une C# dll qui contient toutes vos [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] pages en tant qu’assembly compilé, puis faites C++ en sorte que votre exécutable inclue cette dll comme référence.  
  
- Créer un C# exécutable pour le [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] contenu et faire référence à une C++ dll qui contient le [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] contenu.  
  
- Utilisez <xref:System.Windows.Markup.XamlReader.Load%2A> pour charger au [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] moment de l’exécution, au lieu de [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]compiler votre.  
  
- N’utilisez [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] pas du tout et écrivez tout votre [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] dans le code, en développant l’arborescence d' <xref:System.Windows.Application>éléments à partir de.  
  
 Utilisez la technique qui vous convient le mieux.  
  
> [!NOTE]
> Si vous n’avez pas C++déjà utilisé/CLI, vous remarquerez peut-être des mots `gcnew` clés `nullptr` «nouveaux», tels que et dans les exemples de code d’interopérabilité. Ces mots clés remplacent l’ancienne syntaxe de double trait de`__gc`soulignement () et fournissent une syntaxe plus naturelle C++pour le code managé dans.  Pour en savoir plus sur C++les fonctionnalités managées/CLI, consultez [extensions de composant pour les plateformes Runtime](/cpp/windows/component-extensions-for-runtime-platforms) et [Hello, C++/CLI](https://go.microsoft.com/fwlink/?LinkId=98739).  
  
<a name="hwnds"></a>   
## <a name="how-wpf-uses-hwnds"></a>Utilisation des HWND par WPF  
 Pour tirer le meilleur parti de l’interopérabilité HWND dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], vous devez comprendre de quelle façon [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] utilise les HWND. Pour un HWND, vous ne pouvez [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] pas mélanger le rendu avec le rendu DirectX ou le rendu GDI/GDI+. Ceci a plusieurs implications. D’une part, pour pouvoir combiner ces modèles de rendu, vous devez créer une solution d’interopérabilité et utiliser les segments d’interopérabilité désignés pour chaque modèle de rendu à utiliser. D’autre part, le comportement de rendu crée une restriction d’« espace de rendu » (« airspace » en anglais) relative aux objectifs de la solution d’interopérabilité. Le concept d’« espace de rendu » est expliqué en détail dans la rubrique [Vue d’ensemble des régions de technologie](technology-regions-overview.md).  
  
 Tous les éléments [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] affichés sont stockés par un HWND. Quand vous créez un [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Window>, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] crée un HWND de niveau supérieur et utilise un <xref:System.Windows.Interop.HwndSource> pour placer le <xref:System.Windows.Window> et son [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] contenu dans le HWND.  Le reste du contenu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] dans l’application partage ce HWND spécifique. Les menus, les zones de liste déroulante et les autres menus contextuels constituent une exception à ce principe. Ces éléments créent leur propre fenêtre de niveau supérieur, ce qui explique pourquoi un menu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] peut potentiellement dépasser le bord du HWND de fenêtre qui le contient. Lorsque vous utilisez <xref:System.Windows.Interop.HwndHost> pour placer un HWND dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] indique comment positionner le nouveau HWND enfant par rapport au [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Window> HWND.  
  
 La transparence dans et entre les HWND est un concept connexe des HWND. Ceci est également expliqué dans la rubrique [Vue d’ensemble des régions de technologie](technology-regions-overview.md).  
  
<a name="hosting_a_wpf_page"></a>   
## <a name="hosting-wpf-content-in-a-microsoft-win32-window"></a>Hébergement de contenu WPF dans une fenêtre Microsoft Win32  
 La clé de l’hébergement [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] d’un [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] sur une fenêtre <xref:System.Windows.Interop.HwndSource> est la classe. Cette classe inclut le contenu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] dans un wrapper dans une fenêtre [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)], ce qui permet au contenu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] d’être incorporé dans votre [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] sous la forme d’une fenêtre enfant. L'approche suivante combine [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] et [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] dans une même application.  
  
1. Implémentez le contenu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] (l’élément racine du contenu) comme une classe managée. En règle générale, la classe hérite de l’une des classes pouvant contenir plusieurs éléments enfants et/ou utilisée en tant qu’élément racine, <xref:System.Windows.Controls.DockPanel> tel <xref:System.Windows.Controls.Page>que ou. Dans les étapes suivantes, cette classe est appelée « classe de contenu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] » et les instances de la classe sont appelées « objets de contenu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ».  
  
2. Implémenter une application Windows C++avec/CLI. Si vous démarrez avec une C++ application non managée existante, vous pouvez généralement lui permettre d’appeler du code managé en modifiant les paramètres de votre projet de `/clr` façon à inclure l’indicateur de compilateur (la portée complète de ce `/clr` qui peut être nécessaire à la prise en charge la compilation n’est pas décrite dans cette rubrique.  
  
3. Définissez le thread unique cloisonné (STA) comme modèle de thread. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] utilise ce modèle de thread.  
  
4. Gérez la notification WM_CREATE dans votre procédure de fenêtre.  
  
5. Dans le gestionnaire (ou une fonction appelée par le gestionnaire), effectuez les opérations suivantes :  
  
    1. Créez un <xref:System.Windows.Interop.HwndSource> objet avec le HWND de la fenêtre parente `parent` comme paramètre.  
  
    2. Créez une instance de la classe de contenu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
    3. Assignez une référence [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] à l’objet de <xref:System.Windows.Interop.HwndSource> contenu <xref:System.Windows.Interop.HwndSource.RootVisual%2A> à la propriété de l’objet.  
  
    4. La <xref:System.Windows.Interop.HwndSource> propriété <xref:System.Windows.Interop.HwndSource.Handle%2A> de l’objet contient le handle de fenêtre (HWND). Pour obtenir un HWND que vous pouvez utiliser dans la partie non managée de l'application, effectuez un cast de `Handle.ToPointer()` en HWND.  
  
6. Implémentez une classe managée qui contient un champ statique comportant une référence à l’objet de contenu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Cette classe vous permet d’obtenir une référence à l' [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] objet de contenu à [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] partir de votre code, mais il est plus <xref:System.Windows.Interop.HwndSource> important d’éviter que votre garbage collection par inadvertance soit effectué par inadvertance.  
  
7. Recevez les notifications de l’objet de contenu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] en attachant un gestionnaire à un ou plusieurs événements de l’objet de contenu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
8. Communiquez avec l’objet de contenu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] en utilisant la référence que vous avez stockée dans le champ statique pour définir les propriétés, les méthodes d’appel, etc.  
  
> [!NOTE]
> Vous pouvez faire une partie ou la totalité de la définition de la classe de contenu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] de la première étape dans [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] à l’aide de la classe partielle par défaut de la classe de contenu, à condition de créer un assembly distinct et de le référencer. Bien que vous incluez <xref:System.Windows.Application> généralement un objet dans le cadre [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] de la compilation de dans un assembly, vous n' <xref:System.Windows.Application> avez pas à utiliser ce dernier dans le cadre de l’interopérabilité, vous utilisez simplement une [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ou plusieurs des classes racines pour les fichiers visés à par l’application et référencent leurs classes partielles. Le reste de la procédure est quasiment identique à celle présentée ci-dessus.  
>   
>  Chacune de ces étapes est illustrée par du code dans [la rubrique Procédure pas à pas: Hébergement du contenu WPF dans](walkthrough-hosting-wpf-content-in-win32.md)Win32.  
  
<a name="hosting_an_hwnd"></a>   
## <a name="hosting-a-microsoft-win32-window-in-wpf"></a>Hébergement d’une fenêtre Microsoft Win32 dans WPF  
 La clé de l’hébergement [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] d’une fenêtre [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] dans un autre <xref:System.Windows.Interop.HwndHost> contenu est la classe. Cette classe inclut la fenêtre dans un wrapper dans un élément [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] qui peut être ajouté à une arborescence d’éléments [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. <xref:System.Windows.Interop.HwndHost>prend également en charge les API qui vous permettent d’effectuer des tâches telles que le traitement des messages pour la fenêtre hébergée. La procédure de base est la suivante :  
  
1. Créez une arborescence d’éléments pour une application [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] (à l’aide de code ou de balises). Recherchez un point approprié et autorisé dans l’arborescence d’éléments où <xref:System.Windows.Interop.HwndHost> l’implémentation peut être ajoutée en tant qu’élément enfant. Dans les étapes suivantes, cet élément est appelé élément de réservation.  
  
2. Dérivez de <xref:System.Windows.Interop.HwndHost> pour créer un objet qui [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] contient votre contenu.  
  
3. Dans cette classe hôte, substituez la <xref:System.Windows.Interop.HwndHost> méthode <xref:System.Windows.Interop.HwndHost.BuildWindowCore%2A>. Retournez le HWND de la fenêtre hébergée. Vous pouvez inclure le ou les contrôles réels dans un wrapper comme une fenêtre enfant de la fenêtre retournée. L’inclusion des contrôles dans un wrapper dans une fenêtre hôte permet au contenu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] de recevoir facilement les notifications des contrôles. Cette technique permet d’éviter certains problèmes de [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] liés à la gestion des messages à la limite d’un contrôle hébergé.  
  
4. Substituez les <xref:System.Windows.Interop.HwndHost> méthodes <xref:System.Windows.Interop.HwndHost.DestroyWindowCore%2A> et <xref:System.Windows.Interop.HwndHost.WndProc%2A>. L’objectif est d’effectuer un nettoyage et de supprimer les références au contenu hébergé, en particulier si vous avez créé des références à des objets non managés.  
  
5. Dans votre fichier code-behind, créez une instance de la classe d’hébergement de contrôle et définissez-la comme enfant de l’élément de réservation. En général, vous utilisez un gestionnaire d’événements <xref:System.Windows.FrameworkElement.Loaded>tel que, ou vous utilisez le constructeur de classe partielle. Vous pouvez également ajouter le contenu d’interopérabilité via un comportement au moment de l’exécution.  
  
6. Traitez les messages de fenêtre sélectionnés, tels que les notifications de contrôle. Il y a deux approches possibles, qui fournissent un accès identique au flux de messages. Votre choix est donc essentiellement motivé par le côté pratique de la programmation.  
  
    - Implémentez le traitement des messages pour tous les messages (pas seulement les messages d’arrêt) <xref:System.Windows.Interop.HwndHost> dans <xref:System.Windows.Interop.HwndHost.WndProc%2A>votre substitution de la méthode.  
  
    - Faire en sorte [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] que l’élément d’hébergement traite les <xref:System.Windows.Interop.HwndHost.MessageHook> messages en gérant l’événement. Cet événement est déclenché pour chaque message qui est envoyé à la procédure de fenêtre principale de la fenêtre hébergée.  
  
    - Vous ne pouvez pas traiter les messages de Windows qui ne sont <xref:System.Windows.Interop.HwndHost.WndProc%2A>pas en cours d’utilisation à l’aide de.  
  
7. Communiquez avec la fenêtre hébergée en effectuant un appel de code non managé pour appeler la fonction `SendMessage` non managée.  
  
 L’exécution de ces étapes crée une application qui fonctionne avec des entrées de la souris. Vous pouvez ajouter la prise en charge de la tabulation pour la <xref:System.Windows.Interop.IKeyboardInputSink> fenêtre hébergée en implémentant l’interface.  
  
 Chacune de ces étapes est illustrée par du code dans [la rubrique Procédure pas à pas: Hébergement d’un contrôle Win32 dans](walkthrough-hosting-a-win32-control-in-wpf.md)WPF.  
  
### <a name="hwnds-inside-wpf"></a>HWND dans WPF  
 Vous pouvez considérer <xref:System.Windows.Interop.HwndHost> comme un contrôle spécial. (Techniquement, <xref:System.Windows.Interop.HwndHost> est une <xref:System.Windows.FrameworkElement> classe dérivée, et <xref:System.Windows.Controls.Control> non une classe dérivée, mais elle peut être considérée comme un contrôle à des fins d’interopérabilité.) soustrait la nature sous [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] -jacente du contenu hébergé de telle sorte que le [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] reste de considère le contenu hébergé comme un autre objet de contrôle, qui doit restituer et traiter l’entrée. <xref:System.Windows.Interop.HwndHost> <xref:System.Windows.Interop.HwndHost>se comporte généralement comme n’importe quel [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] autre <xref:System.Windows.FrameworkElement>, bien qu’il existe des différences importantes autour de la sortie (dessin et graphiques) et de l’entrée (souris et clavier) en fonction des limitations de ce que les HWND sous-jacents peuvent prendre en charge.  
  
#### <a name="notable-differences-in-output-behavior"></a>Principales différences dans le comportement de sortie  
  
- <xref:System.Windows.FrameworkElement>, qui est la <xref:System.Windows.Interop.HwndHost> classe de base, possède très peu de propriétés qui impliquent des modifications de l’interface utilisateur. Celles-ci incluent des <xref:System.Windows.FrameworkElement.FlowDirection%2A?displayProperty=nameWithType>propriétés telles que, qui modifie la disposition des éléments dans cet élément en tant que parent. Toutefois, la plupart des propriétés concernées ne sont pas mappées aux équivalents possibles de [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)], le cas échéant. Un trop grand nombre de ces propriétés et de leurs significations reposent essentiellement sur la technologie de rendu, ce qui rend les mappages difficiles à utiliser. Par conséquent, la définition de <xref:System.Windows.FrameworkElement.FlowDirection%2A> propriétés <xref:System.Windows.Interop.HwndHost> telles que on n’a aucun effet.  
  
- <xref:System.Windows.Interop.HwndHost>ne peut pas être pivotée, mise à l’échelle, inclinée ou affectée par une transformation.  
  
- <xref:System.Windows.Interop.HwndHost>ne prend pas en <xref:System.Windows.UIElement.Opacity%2A> charge la propriété (fusion alpha). Si le contenu à <xref:System.Windows.Interop.HwndHost> l' <xref:System.Drawing> intérieur du effectue des opérations qui incluent des informations alpha, qui n’est lui <xref:System.Windows.Interop.HwndHost> -même pas une violation, mais dans son ensemble, prend uniquement en charge l’opacité = 1,0 (100%).  
  
- <xref:System.Windows.Interop.HwndHost>s’affiche au-dessus des [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] autres éléments dans la même fenêtre de niveau supérieur. Toutefois, un <xref:System.Windows.Controls.ToolTip> menu <xref:System.Windows.Controls.ContextMenu> généré par ou est une fenêtre de niveau supérieur distincte, ce qui se comportera correctement avec <xref:System.Windows.Interop.HwndHost>.  
  
- <xref:System.Windows.Interop.HwndHost>ne respecte pas la zone de découpage <xref:System.Windows.UIElement>de son parent. Cela peut poser problème si vous tentez de placer une <xref:System.Windows.Interop.HwndHost> classe à l’intérieur d’une zone <xref:System.Windows.Controls.Canvas>de défilement ou.  
  
#### <a name="notable-differences-in-input-behavior"></a>Principales différences dans le comportement d’entrée  
  
- En général, alors que les appareils d’entrée sont étendus [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] dans la région hébergée, les [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] <xref:System.Windows.Interop.HwndHost> événements d’entrée sont directement dirigés vers.  
  
- Lorsque la souris se trouve sur <xref:System.Windows.Interop.HwndHost>le, votre application ne reçoit [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] pas d’événements de souris et la valeur [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] `false`de <xref:System.Windows.UIElement.IsMouseOver%2A> la propriété est.  
  
- Si le <xref:System.Windows.Interop.HwndHost> a le focus clavier, votre application ne reçoit [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] pas d’événements de clavier et la [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] valeur <xref:System.Windows.UIElement.IsKeyboardFocusWithin%2A> `false`de la propriété est.  
  
- Lorsque le focus est dans <xref:System.Windows.Interop.HwndHost> le et que les modifications apportées à un autre contrôle à l' [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] intérieur <xref:System.Windows.UIElement.GotFocus> du <xref:System.Windows.UIElement.LostFocus> <xref:System.Windows.Interop.HwndHost>, votre application ne reçoit pas les événements ou.  
  
- Les propriétés et les événements de stylet associés sont analogues et ne signalent pas d’informations lorsque <xref:System.Windows.Interop.HwndHost>le stylet est sur.  
  
<a name="tabbing_mnemonics_accelerators"></a>   
## <a name="tabbing-mnemonics-and-accelerators"></a>Tabulation, mnémoniques et accélérateurs  
 Les <xref:System.Windows.Interop.IKeyboardInputSink> interfaces <xref:System.Windows.Interop.IKeyboardInputSite> et vous permettent de créer une expérience de clavier transparente pour [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] les [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] applications mixtes et:  
  
- Tabulation entre des composants [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] et [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
- Mnémoniques et accélérateurs fonctionnant quand le focus est sur un composant Win32 et sur un composant WPF.  
  
 Les <xref:System.Windows.Interop.HwndHost> classes <xref:System.Windows.Interop.HwndSource> et fournissent toutes deux des implémentations de <xref:System.Windows.Interop.IKeyboardInputSink>, mais elles peuvent ne pas gérer tous les messages d’entrée souhaités pour des scénarios plus avancés. Dans ce cas, substituez les méthodes appropriées pour obtenir le comportement de clavier souhaité.  
  
 Les interfaces assurent uniquement la prise en charge des événements qui ont lieu lors de la transition entre les zones [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] et [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]. Dans la zone [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)], le comportement de tabulation est entièrement déterminé par la logique [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] implémentée pour la tabulation, le cas échéant.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Interop.HwndHost>
- <xref:System.Windows.Interop.HwndSource>
- <xref:System.Windows.Interop>
- [Procédure pas à pas : Hébergement d’un contrôle Win32 dans WPF](walkthrough-hosting-a-win32-control-in-wpf.md)
- [Procédure pas à pas : Hébergement de contenu WPF dans Win32](walkthrough-hosting-wpf-content-in-win32.md)
