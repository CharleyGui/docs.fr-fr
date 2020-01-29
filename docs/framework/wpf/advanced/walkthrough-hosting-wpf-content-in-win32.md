---
title: Héberger du contenu WPF dans Win32
titleSuffix: ''
ms.date: 03/30/2017
dev_langs:
- cpp
helpviewer_keywords:
- hosting WPF content in Win32 window [WPF]
ms.assetid: 38ce284a-4303-46dd-b699-c9365b22a7dc
ms.openlocfilehash: ff95b330ff67e916a4d27ef841e757998d847c8b
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76735310"
---
# <a name="walkthrough-hosting-wpf-content-in-win32"></a>Procédure pas à pas : hébergement de contenu WPF dans Win32
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] propose un environnement de création d'applications élaboré. Toutefois, lorsque vous investissez dans du code Win32, il peut être plus efficace d’ajouter des fonctionnalités de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] à votre application que de réécrire votre code d’origine. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] fournit un mécanisme simple pour héberger du contenu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] dans une fenêtre Win32.  
  
 Ce didacticiel explique comment écrire un exemple d’application, [hébergeant du contenu WPF dans un exemple de fenêtre Win32](https://go.microsoft.com/fwlink/?LinkID=160004), qui héberge [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] contenu dans une fenêtre Win32. Vous pouvez étendre cet exemple pour héberger n’importe quelle fenêtre Win32. Étant donné qu’il implique la combinaison de code managé et non managé, l’application C++est écrite en/cli.  

<a name="requirements"></a>   
## <a name="requirements"></a>Configuration requise pour  
 Ce didacticiel suppose une connaissance de base des [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] et de la programmation Win32. Pour une présentation de base de la programmation de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], consultez [prise en main](../getting-started/index.md). Pour une introduction à la programmation Win32, vous devez référencer l’un des nombreux ouvrages sur le sujet, en particulier *Programming Windows* de Charles Petzold.  
  
 Étant donné que l’exemple qui accompagne ce didacticiel est implémenté C++en/CLI, ce didacticiel suppose que vous êtes familiarisé avec l' C++ utilisation de pour programmer l’API Windows, ainsi qu’une compréhension de la programmation de code managé. La connaissance de C++la fonction/CLI est utile, mais pas essentielle.  
  
> [!NOTE]
> Ce didacticiel comprend plusieurs exemples de code tirés de l'exemple associé. Cependant, pour une meilleure lecture, il n'inclut pas la totalité de l'exemple de code. Pour obtenir l’exemple de code complet, consultez [Hébergement de contenu WPF dans un exemple de fenêtre Win32](https://go.microsoft.com/fwlink/?LinkID=160004).  
  
<a name="basic_procedure"></a>   
## <a name="the-basic-procedure"></a>Procédure de base  
 Cette section décrit la procédure de base que vous utilisez pour héberger [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] contenu dans une fenêtre Win32. Les sections restantes décrivent chaque étape dans les détails.  
  
 La classe <xref:System.Windows.Interop.HwndSource> est la clé de l’hébergement de contenu de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] dans une fenêtre Win32. Cette classe encapsule le contenu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] dans une fenêtre Win32, ce qui lui permet d’être incorporé dans votre [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] en tant que fenêtre enfant. L’approche suivante combine les [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Win32 et dans une même application.  
  
1. Implémentez votre contenu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] en tant que classe managée.  
  
2. Implémenter une application Windows C++avec/CLI. Si vous démarrez avec une application existante et du C++ code non managé, vous pouvez généralement lui permettre d’appeler du code managé en modifiant les paramètres de votre projet de façon à inclure l’indicateur de compilateur `/clr`.  
  
3. Affectez au modèle de thread un thread unique cloisonné (STA, Single-Threaded Apartment).  
  
4. Gérez le [WM_CREATE](/windows/desktop/winmsg/wm-create)notification dans votre procédure de fenêtre et procédez comme suit :  
  
    1. Créez un objet <xref:System.Windows.Interop.HwndSource> en faisant de la fenêtre parente son paramètre `parent`.  
  
    2. Créez une instance de la classe de contenu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
    3. Assignez une référence à l’objet de contenu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] à la propriété <xref:System.Windows.Interop.HwndSource.RootVisual%2A> de l' <xref:System.Windows.Interop.HwndSource>.  
  
    4. Obtenez le HWND pour le contenu. La propriété <xref:System.Windows.Interop.HwndSource.Handle%2A> de l'objet <xref:System.Windows.Interop.HwndSource> contient le handle de fenêtre (HWND). Pour obtenir un HWND que vous pouvez utiliser dans la partie non managée de l'application, effectuez un cast de `Handle.ToPointer()` en HWND.  
  
5. Implémentez une classe managée qui contient un champ statique pour contenir une référence à votre contenu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Cette classe vous permet d’obtenir une référence au contenu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] à partir de votre code Win32.  
  
6. Assignez le contenu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] au champ statique.  
  
7. Recevoir des notifications du contenu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] en attachant un gestionnaire à un ou plusieurs événements [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
8. Communiquez avec le contenu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] en utilisant la référence que vous avez stockée dans le champ statique pour définir les propriétés, etc.  
  
> [!NOTE]
> Vous pouvez également utiliser [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] pour implémenter votre contenu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Toutefois, vous devrez le compiler séparément en tant que bibliothèque de liens dynamiques (DLL) et référencer cette DLL à partir de votre application Win32. Le reste de la procédure est similaire à celle présentée ci-dessus.

<a name="implementing_the_application"></a>
## <a name="implementing-the-host-application"></a>Implémentation de l'application hôte.
 Cette section décrit comment héberger [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] contenu dans une application Win32 de base. Le contenu lui-même est C++implémenté dans/CLI en tant que classe managée. Pour l'essentiel, il s'agit d'une programmation [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] simple. Les aspects clés de l’implémentation de contenu sont décrits dans [implémentation du contenu WPF](#implementing_the_wpf_page).

- [Application de base](#the_basic_application)

- [Hébergement du contenu WPF](#hosting_the_wpf_page)

- [Stockage d’une référence au contenu WPF](#holding_a_reference)

- [Communication avec le contenu WPF](#communicating_with_the_page)

<a name="the_basic_application"></a>
### <a name="the-basic-application"></a>Application de base
 Le point de départ de l’application hôte consistait à créer un modèle Visual Studio 2005.

1. Ouvrez Visual Studio 2005, puis sélectionnez **nouveau projet** dans le menu **fichier** .

2. Sélectionnez **Win32** dans la liste des types C++ de projets visuels. Si votre langue par défaut n' C++est pas, vous trouverez ces types de projets dans d' **autres langues**.

3. Sélectionnez un modèle de **projet Win32** , attribuez un nom au projet et cliquez sur **OK** pour lancer l **'Assistant application Win32**.

4. Acceptez les paramètres par défaut de l’Assistant, puis cliquez sur **Terminer** pour démarrer le projet.

 Le modèle crée une application Win32 de base, notamment :

- Un point d'entrée pour l'application

- Une fenêtre avec une procédure de fenêtre associée (WndProc)

- Menu avec les en-têtes de **fichier** et **d’aide** . Le menu **fichier** comporte un élément **quitter** qui ferme l’application. Le menu **aide** contient un élément **à propos** de qui lance une boîte de dialogue simple.

 Avant de commencer à écrire du code pour héberger le contenu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], vous devez apporter deux modifications au modèle de base.

 La première consiste à compiler le projet sous forme de code managé. Par défaut, le projet se compile sous forme de code non managé. Cependant, comme [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] est implémenté en code managé, le projet doit être compilé en conséquence.

1. Dans **Explorateur de solutions** , cliquez avec le bouton droit sur le nom du projet, puis sélectionnez **Propriétés** dans le menu contextuel pour ouvrir la boîte de dialogue **pages de propriétés** .

2. Sélectionnez **Propriétés de configuration** dans l’arborescence dans le volet gauche.

3. Sélectionnez prise en charge du **Common Language Runtime** dans la liste **paramètres par défaut du projet** dans le volet droit.

4. Sélectionnez **prise en charge du Common Language Runtime (/CLR)** dans la zone de liste déroulante.

> [!NOTE]
> L'indicateur de ce compilateur vous permet d'utiliser du code managé dans votre application, mais la compilation de votre code non managé se fera toujours comme avant.

 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] utilise le modèle de thread unique cloisonné (STA). Pour fonctionner correctement avec le code de contenu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], vous devez définir le modèle de thread de l’application sur STA en appliquant un attribut au point d’entrée.

 [!code-cpp[Win32HostingWPFPage#WinMain](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/Win32HostingWPFPage.cpp#winmain)]

<a name="hosting_the_wpf_page"></a>
### <a name="hosting-the-wpf-content"></a>Hébergement du contenu WPF
 Le contenu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] est une application d’entrée d’adresse simple. Elle est constituée de plusieurs contrôles <xref:System.Windows.Controls.TextBox> destinés à recevoir le nom d'utilisateur, l'adresse et ainsi de suite. Il existe également deux contrôles de <xref:System.Windows.Controls.Button>, **OK** et **Annuler**. Quand l’utilisateur clique sur **OK**, le gestionnaire d’événements <xref:System.Windows.Controls.Primitives.ButtonBase.Click> du bouton collecte les données à partir des contrôles de <xref:System.Windows.Controls.TextBox>, les assigne aux propriétés correspondantes et déclenche un événement personnalisé, `OnButtonClicked`. Quand l’utilisateur clique sur **Annuler**, le gestionnaire déclenche simplement `OnButtonClicked`. L'objet d'argument d'événement pour `OnButtonClicked` contient un champ booléen qui indique le bouton sur lequel l'utilisateur a cliqué.

 Le code permettant d’héberger le contenu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] est implémenté dans un gestionnaire pour la notification [WM_CREATE](/windows/desktop/winmsg/wm-create) dans la fenêtre hôte.

 [!code-cpp[Win32HostingWPFPage#WMCreate](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/Win32HostingWPFPage.cpp#wmcreate)]

 La méthode `GetHwnd` prend les informations de taille et de position, ainsi que le handle de la fenêtre parente et retourne le handle de fenêtre du contenu de la [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] hébergée.

> [!NOTE]
> Vous ne pouvez pas utiliser de directive `#using` pour l'espace de noms `System::Windows::Interop`. Cela entraîne une collision de noms entre la structure <xref:System.Windows.Interop.MSG> de cet espace de noms et la structure MSG déclarée dans winuser.h. Vous devez à la place utiliser des noms qualifiés complets pour accéder au contenu de cet espace de noms.

 [!code-cpp[Win32HostingWPFPage#GetHwnd](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/Win32HostingWPFPage.cpp#gethwnd)]

 Vous ne pouvez pas héberger le contenu de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] directement dans la fenêtre de votre application. Vous devez plutôt commencer par créer un objet <xref:System.Windows.Interop.HwndSource> pour inclure le contenu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] dans un wrapper. Cet objet est fondamentalement une fenêtre conçue pour héberger un contenu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Vous hébergez l’objet <xref:System.Windows.Interop.HwndSource> dans la fenêtre parente en le créant en tant qu’enfant d’une fenêtre Win32 qui fait partie de votre application. Les paramètres du constructeur <xref:System.Windows.Interop.HwndSource> contiennent quasiment les mêmes informations que vous pouvez passer à CreateWindow lorsque vous créez une fenêtre enfant Win32.

 Vous allez ensuite créer une instance de l’objet de contenu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Dans ce cas, le contenu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] est implémenté en tant que classe distincte, `WPFPage`, C++à l’aide de/CLI. Vous pouvez aussi implémenter le contenu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] avec [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]. Toutefois, pour ce faire, vous devez configurer un projet distinct et générer le contenu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] en tant que DLL. Vous pouvez ajouter une référence à cette DLL à votre projet et utiliser cette référence pour créer une instance du contenu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].

 Vous affichez le contenu de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] dans votre fenêtre enfant en assignant une référence au contenu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] à la propriété <xref:System.Windows.Interop.HwndSource.RootVisual%2A> de l' <xref:System.Windows.Interop.HwndSource>.

 La ligne de code suivante attache un gestionnaire d'événements, `WPFButtonClicked`, à l'événement [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] du contenu `OnButtonClicked`. Ce gestionnaire est appelé quand l’utilisateur clique sur le bouton **OK** ou **Annuler** . Pour plus d’informations sur ce gestionnaire d’événements, consultez [communicating_with_the_WPF du contenu](#communicating_with_the_page) .

 La dernière ligne de code présentée retourne le handle de fenêtre (HWND) associé à l'objet <xref:System.Windows.Interop.HwndSource>. Vous pouvez utiliser ce handle à partir de votre code Win32 pour envoyer des messages à la fenêtre hébergée, même si l’exemple ne le fait pas. L'objet <xref:System.Windows.Interop.HwndSource> déclenche un événement chaque fois qu'il reçoit un message. Pour traiter les messages, appelez la méthode <xref:System.Windows.Interop.HwndSource.AddHook%2A> pour attacher un gestionnaire de messages et traiter ensuite les messages dans ce gestionnaire.

<a name="holding_a_reference"></a>
### <a name="holding-a-reference-to-the-wpf-content"></a>Stockage d'une référence au contenu WPF
 Pour de nombreuses applications, vous souhaiterez communiquer ultérieurement avec le contenu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Par exemple, vous pouvez souhaiter modifier les propriétés du contenu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ou éventuellement faire en sorte que l'objet <xref:System.Windows.Interop.HwndSource> héberge un contenu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] différent. Pour ce faire, vous avez besoin d'une référence à l'objet <xref:System.Windows.Interop.HwndSource> ou au contenu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. L'objet <xref:System.Windows.Interop.HwndSource> et son contenu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] associé restent en mémoire jusqu'à la destruction du handle de fenêtre. Cependant, la variable que vous assignez à l'objet <xref:System.Windows.Interop.HwndSource> sera hors de portée dès que vous retournerez de la procédure de fenêtre. Pour gérer ce problème avec les applications Win32, la méthode la plus simple consiste à utiliser une variable statique ou globale. Malheureusement, vous ne pouvez pas assigner un objet managé à ces types de variable. Vous pouvez assigner le handle de fenêtre associé à l'objet <xref:System.Windows.Interop.HwndSource> à une variable globale ou statique, mais cela ne permet pas d'accéder à l'objet proprement dit.

 La solution la plus simple à ce problème consiste à implémenter une classe managée qui contient un jeu de champs statiques pour stocker les références à tous les objets managés auxquels vous devez accéder. L'exemple utilise la classe `WPFPageHost` pour stocker une référence au contenu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], plus les valeurs initiales de plusieurs de ses propriétés qui peuvent être modifiées ultérieurement par l'utilisateur. Cette option est définie dans l'en-tête.

 [!code-cpp[Win32HostingWPFPage#WPFPageHost](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/Win32HostingWPFPage.h#wpfpagehost)]

 La dernière partie de la fonction `GetHwnd` assigne des valeurs à ces champs en vue d'une utilisation ultérieure pendant que `myPage` se trouve toujours dans la portée.

<a name="communicating_with_the_page"></a>
### <a name="communicating-with-the-wpf-content"></a>Communication avec le contenu WPF
 Il existe deux types de communication avec le contenu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. L’application reçoit des informations du contenu de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] lorsque l’utilisateur clique sur les boutons **OK** ou **Annuler** . L'application possède aussi une [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] qui permet à l'utilisateur de modifier différentes propriétés du contenu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], telles que la couleur d'arrière-plan ou la taille de police par défaut.

 Comme indiqué précédemment, quand l'utilisateur clique sur l'un des boutons, le contenu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] déclenche un événement `OnButtonClicked`. L'application attache un gestionnaire à cet événement pour recevoir ces notifications. Si vous avez cliqué sur le bouton **OK** , le gestionnaire obtient les informations utilisateur à partir du contenu de la [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] et les affiche dans un jeu de contrôles statiques.

 [!code-cpp[Win32HostingWPFPage#WPFButtonClicked](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/Win32HostingWPFPage.cpp#wpfbuttonclicked)]

 Le gestionnaire reçoit un objet d'argument d'événement personnalisé du contenu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], `MyPageEventArgs`. La propriété `IsOK` de l’objet a la valeur `true` si l’utilisateur a cliqué sur le bouton **OK** et `false` si l’utilisateur a cliqué sur le bouton **Annuler** .

 Si l’utilisateur a cliqué sur le bouton **OK** , le gestionnaire obtient une référence au contenu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] à partir de la classe de conteneur. Il recueille ensuite les informations utilisateur détenues par les propriété de contenu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] associées et utilise les contrôles statiques pour afficher les informations dans la fenêtre parente. Étant donné que les données de contenu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] se trouvent sous la forme d’une chaîne managée, elles doivent être marshalées pour être utilisées par un contrôle Win32. Si l’utilisateur a cliqué sur le bouton **Annuler** , le gestionnaire efface les données des contrôles statiques.

 L'application [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] fournit un ensemble de cases d'option qui permettent à l'utilisateur de modifier la couleur d'arrière-plan du contenu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], ainsi que plusieurs propriétés liées aux polices. L'exemple suivant est un extrait de la procédure de fenêtre (WndProc) de l'application et de son traitement des messages qui définit différentes propriétés sur différents messages, notamment la couleur d'arrière-plan. Les autres sont similaires et ne sont pas illustrées. Consultez l'exemple complet pour plus de détails et pour connaître le contexte.

 [!code-cpp[Win32HostingWPFPage#WMCommandToBG](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/Win32HostingWPFPage.cpp#wmcommandtobg)]

 Pour définir la couleur d'arrière-plan, obtenez une référence au contenu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] (`hostedPage`) à partir de `WPFPageHost` et affectez à la propriété de couleur d'arrière-plan la valeur appropriée. L'exemple utilise trois options de couleur : la couleur d'origine, du vert clair ou du saumon clair. La couleur d'arrière-plan d'origine est stockée en tant que champ statique dans la classe `WPFPageHost`. Pour définir les deux autres couleurs, vous devez créer un objet <xref:System.Windows.Media.SolidColorBrush> et transmettre au constructeur une valeur de couleur statique à partir de l'objet <xref:System.Windows.Media.Colors>.

<a name="implementing_the_wpf_page"></a>
## <a name="implementing-the-wpf-page"></a>Implémentation de la page WPF
 Vous pouvez héberger et utiliser le contenu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] sans avoir connaissance de l’implémentation réelle. Si le contenu de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] a été empaqueté dans une DLL distincte, il aurait pu être créé dans n’importe quel langage de common language runtime (CLR). Voici une brève procédure pas à pas C++de l’implémentation/CLI utilisée dans l’exemple. Cette section comprend les sous-sections suivantes.

- [Disposition](#page_layout)

- [Retour des données à la fenêtre hôte](#returning_data_to_window)

- [Définition des propriétés WPF](#set_page_properties)

<a name="page_layout"></a>
### <a name="layout"></a>Mise en page
 Les éléments [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] dans le contenu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] se composent de cinq contrôles <xref:System.Windows.Controls.TextBox>, avec des contrôles <xref:System.Windows.Controls.Label> associés : nom, adresse, ville, État et code postal. Il existe également deux contrôles de <xref:System.Windows.Controls.Button>, **OK** et **Annuler**

 Le contenu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] est implémenté dans la classe `WPFPage`. La disposition est gérée avec un élément de disposition <xref:System.Windows.Controls.Grid>. La classe hérite de <xref:System.Windows.Controls.Grid>, qui en fait effectivement l'élément racine du contenu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].

 Le constructeur de contenu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] prend la largeur et la hauteur requises et dimensionne le <xref:System.Windows.Controls.Grid> en conséquence. Il définit ensuite la disposition de base en créant un ensemble de <xref:System.Windows.Controls.ColumnDefinition> et <xref:System.Windows.Controls.RowDefinition> objets et en les ajoutant aux collections <xref:System.Windows.Controls.Grid.ColumnDefinitions%2A> et <xref:System.Windows.Controls.Grid.RowDefinitions%2A> <xref:System.Windows.Controls.Grid> de base d’objet, respectivement. Une grille contenant cinq lignes et sept colonnes est ainsi définie et ses dimensions sont déterminées par le contenu des cellules.

 [!code-cpp[Win32HostingWPFPage#WPFPageCtorToGridDef](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/WPFPage.cpp#wpfpagectortogriddef)]

 Ensuite, le constructeur ajoute les éléments [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] au <xref:System.Windows.Controls.Grid>. Le premier élément est le texte du titre, qui est un contrôle <xref:System.Windows.Controls.Label> centré dans la première ligne de la grille.

 [!code-cpp[Win32HostingWPFPage#WPFPageCtorTitle](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/WPFPage.cpp#wpfpagectortitle)]

 La ligne suivante contient le contrôle <xref:System.Windows.Controls.Label> Name (nom) et le contrôle <xref:System.Windows.Controls.TextBox> qui lui est associé. Comme le même code est utilisé pour chaque paire label/textbox, il est placé dans une paire de méthodes privées et est utilisé pour les cinq paires label/textbox. Les méthodes créent le contrôle approprié et appellent les méthodes statiques <xref:System.Windows.Controls.Grid> et <xref:System.Windows.Controls.Grid.SetColumn%2A> de la classe <xref:System.Windows.Controls.Grid.SetRow%2A> pour placer les contrôles dans la bonne cellule. Une fois le contrôle créé, l'exemple appelle la méthode <xref:System.Windows.Controls.UIElementCollection.Add%2A> sur la propriété <xref:System.Windows.Controls.Panel.Children%2A> du <xref:System.Windows.Controls.Grid> pour ajouter le contrôle à la grille. Le code permettant d'ajouter les paires label/texbox restantes est similaire. Consultez l'exemple de code pour plus d'informations.

 [!code-cpp[Win32HostingWPFPage#WPFPageCtorName](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/WPFPage.cpp#wpfpagectorname)]

 Les deux méthodes sont implémentées comme suit :

 [!code-cpp[Win32HostingWPFPage#WPFPageCreateHelpers](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/WPFPage.cpp#wpfpagecreatehelpers)]

 Enfin, l’exemple ajoute les boutons **OK** et **Annuler** et attache un gestionnaire d’événements à leurs événements <xref:System.Windows.Controls.Primitives.ButtonBase.Click>.

 [!code-cpp[Win32HostingWPFPage#WPFPageCtorButtonsEvents](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/WPFPage.cpp#wpfpagectorbuttonsevents)]

<a name="returning_data_to_window"></a>
### <a name="returning-the-data-to-the-host-window"></a>Retour des données à la fenêtre hôte
 Quand l'utilisateur clique sur l'un de ces boutons, l'événement <xref:System.Windows.Controls.Primitives.ButtonBase.Click> correspondant est déclenché. La fenêtre hôte peut attacher simplement des gestionnaires à ces événements et obtenir directement les données des contrôles <xref:System.Windows.Controls.TextBox>. L'exemple utilise une approche un peu moins directe. Il gère les <xref:System.Windows.Controls.Primitives.ButtonBase.Click> au sein du contenu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], puis déclenche un `OnButtonClicked`d’événements personnalisé pour notifier le contenu de l' [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Cela permet au contenu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] de procéder à une validation de paramètre avant de notifier l’hôte. Le gestionnaire obtient le texte des contrôles <xref:System.Windows.Controls.TextBox> et l'assigne aux propriétés publiques, à partir desquelles l'hôte peut extraire les informations.

 La déclaration event dans WPFPage.h :

 [!code-cpp[Win32HostingWPFPage#WPFPageEventDecl](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/WPFPage.h#wpfpageeventdecl)]

 Le gestionnaire d'événements <xref:System.Windows.Controls.Primitives.ButtonBase.Click> dans WPFPage.cpp :

 [!code-cpp[Win32HostingWPFPage#WPFPageButtonClicked](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/WPFPage.cpp#wpfpagebuttonclicked)]

<a name="set_page_properties"></a>
### <a name="setting-the-wpf-properties"></a>Définition des propriétés WPF
 L’hôte Win32 permet à l’utilisateur de modifier plusieurs propriétés de contenu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Du côté Win32, il suffit de modifier les propriétés. L'implémentation dans la classe de contenu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] est plus complexe, car il n'existe aucune propriété globale unique qui contrôle les polices pour tous les contrôles. Au lieu de cela, la propriété appropriée de chaque contrôle est modifiée dans les accesseurs set des propriétés. L’exemple suivant montre le code de la propriété `DefaultFontFamily`. La définition de la propriété appelle une méthode privée qui, à son tour, définit les propriétés <xref:System.Windows.Controls.Control.FontFamily%2A> de plusieurs contrôles.

 À partir de WPFPage.h :

 [!code-cpp[Win32HostingWPFPage#WPFPageFontFamilyProperty](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/WPFPage.h#wpfpagefontfamilyproperty)]

 À partir de WPFPage.ccp :

 [!code-cpp[Win32HostingWPFPage#WPFPageSetFontFamily](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/WPFPage.cpp#wpfpagesetfontfamily)]

## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Interop.HwndSource>
- [Interopérabilité WPF et Win32](wpf-and-win32-interoperation.md)
