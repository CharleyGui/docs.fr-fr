---
title: 'Procédure pas à pas : hébergement de contenu WPF dans Win32'
ms.date: 03/30/2017
dev_langs:
- cpp
helpviewer_keywords:
- hosting WPF content in Win32 window [WPF]
ms.assetid: 38ce284a-4303-46dd-b699-c9365b22a7dc
ms.openlocfilehash: 02f0831b46b8087c48b86e83a4b20f94bf3b79d0
ms.sourcegitcommit: 24a4a8eb6d8cfe7b8549fb6d823076d7c697e0c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/23/2019
ms.locfileid: "68401579"
---
# <a name="walkthrough-hosting-wpf-content-in-win32"></a>Procédure pas à pas : hébergement de contenu WPF dans Win32
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] propose un environnement de création d'applications élaboré. Cependant, si vous avez écrit une bonne partie du code [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)], il est peut-être plus judicieux d'ajouter la fonctionnalité [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] à votre application plutôt que de réécrire le code d'origine. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]fournit un mécanisme simple pour héberger [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] le contenu dans une [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] fenêtre.  
  
 Ce didacticiel explique comment écrire un exemple d’application, [hébergeant du contenu WPF dans un exemple de fenêtre Win32](https://go.microsoft.com/fwlink/?LinkID=160004), qui [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] héberge [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] du contenu dans une fenêtre. Vous pouvez étendre cet exemple pour héberger n'importe quelle fenêtre [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]. Compte tenu de la présence de code managé et non managé dans l'application, celle-ci est écrite en [!INCLUDE[TLA#tla_cppcli](../../../../includes/tlasharptla-cppcli-md.md)].  

<a name="requirements"></a>   
## <a name="requirements"></a>Configuration requise  
 Ce didacticiel suppose que vous avez des connaissances de base en matière de programmation [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] et [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]. Pour une introduction à [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] la programmation de base, consultez [prise en main](../getting-started/index.md). Pour une introduction à [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] la programmation, vous devez référencer l’un des nombreux livres sur le sujet, en particulier *Programming Windows* de Charles Petzold.  
  
 Étant donné que l’exemple qui accompagne ce didacticiel est implémenté [!INCLUDE[TLA#tla_cppcli](../../../../includes/tlasharptla-cppcli-md.md)]dans, ce didacticiel suppose que vous êtes familiarisé avec l' [!INCLUDE[TLA#tla_cpp](../../../../includes/tlasharptla-cpp-md.md)] utilisation de pour [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]programmer l’API plus une compréhension de la programmation de code managé. Il est également souhaitable de connaître [!INCLUDE[TLA#tla_cppcli](../../../../includes/tlasharptla-cppcli-md.md)], même si cela n'est pas indispensable.  
  
> [!NOTE]
>  Ce didacticiel comprend plusieurs exemples de code tirés de l'exemple associé. Cependant, pour une meilleure lecture, il n'inclut pas la totalité de l'exemple de code. Pour obtenir l’exemple de code complet, consultez [Hébergement de contenu WPF dans un exemple de fenêtre Win32](https://go.microsoft.com/fwlink/?LinkID=160004).  
  
<a name="basic_procedure"></a>   
## <a name="the-basic-procedure"></a>Procédure de base  
 Cette section décrit la procédure de base que vous utilisez pour héberger [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] du contenu dans une [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] fenêtre. Les sections restantes décrivent chaque étape dans les détails.  
  
 La clé de l' [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Hébergement de contenu [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] dans une fenêtre <xref:System.Windows.Interop.HwndSource> est la classe. Cette classe encapsule le [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] contenu dans une [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] fenêtre, ce qui lui permet d’être incorporé dans votre [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] sous forme de fenêtre enfant. L'approche suivante combine [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] et [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] dans une même application.  
  
1. Implémentez [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] votre contenu en tant que classe managée.  
  
2. Implémentez une application [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] avec [!INCLUDE[TLA#tla_cppcli](../../../../includes/tlasharptla-cppcli-md.md)]. Si vous partez d'une application existante et de code [!INCLUDE[TLA#tla_cpp](../../../../includes/tlasharptla-cpp-md.md)] non managé, vous pouvez généralement faire en sorte qu'il puisse appeler du code managé en modifiant les paramètres de votre projet de manière à inclure l'indicateur du compilateur `/clr`.  
  
3. Affectez au modèle de thread un thread unique cloisonné (STA, Single-Threaded Apartment).  
  
4. Gérez la notification [WM_CREATE](/windows/desktop/winmsg/wm-create)dans votre procédure de fenêtre et procédez comme suit:  
  
    1. Créez un objet <xref:System.Windows.Interop.HwndSource> en faisant de la fenêtre parente son paramètre `parent`.  
  
    2. Créez une instance de la classe de contenu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
    3. Assignez une référence [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] à l’objet de <xref:System.Windows.Interop.HwndSource.RootVisual%2A> contenu à la <xref:System.Windows.Interop.HwndSource>propriété de.  
  
    4. Obtenez le HWND pour le contenu. La propriété <xref:System.Windows.Interop.HwndSource.Handle%2A> de l'objet <xref:System.Windows.Interop.HwndSource> contient le handle de fenêtre (HWND). Pour obtenir un HWND que vous pouvez utiliser dans la partie non managée de l'application, effectuez un cast de `Handle.ToPointer()` en HWND.  
  
5. Implémentez une classe managée qui contient un champ statique pour contenir une référence à votre contenu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Cette classe vous permet d'obtenir une référence au contenu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] à partir de votre code [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)].  
  
6. Assignez le contenu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] au champ statique.  
  
7. Recevoir des notifications [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] du contenu en attachant un gestionnaire à un ou plusieurs [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] événements.  
  
8. Communiquez avec le contenu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] en utilisant la référence que vous avez stockée dans le champ statique pour définir les propriétés, etc.  
  
> [!NOTE]
>  Vous pouvez également utiliser [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] pour implémenter [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] votre contenu. Toutefois, vous devrez le compiler séparément comme une [!INCLUDE[TLA#tla_dll](../../../../includes/tlasharptla-dll-md.md)] et référencer cette [!INCLUDE[TLA2#tla_dll](../../../../includes/tla2sharptla-dll-md.md)] à partir de votre application [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]. Le reste de la procédure est similaire à celle présentée ci-dessus.

<a name="implementing_the_application"></a>
## <a name="implementing-the-host-application"></a>Implémentation de l'application hôte.
 Cette section décrit comment héberger [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] du contenu dans une [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] application de base. Le contenu proprement dit est implémenté dans [!INCLUDE[TLA#tla_cppcli](../../../../includes/tlasharptla-cppcli-md.md)] en tant que classe managée. Pour l'essentiel, il s'agit d'une programmation [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] simple. Les aspects clés de l’implémentation de contenu sont décrits dans [implémentation du contenu WPF](#implementing_the_wpf_page).

<a name="autoNestedSectionsOUTLINE1"></a>
- [Application de base](#the_basic_application)

- [Hébergement du contenu WPF](#hosting_the_wpf_page)

- [Stockage d’une référence au contenu WPF](#holding_a_reference)

- [Communication avec le contenu WPF](#communicating_with_the_page)

<a name="the_basic_application"></a>
### <a name="the-basic-application"></a>Application de base
 Le point de départ de l’application hôte consistait à créer un modèle Visual Studio 2005.

1. Ouvrez Visual Studio 2005, puis sélectionnez **nouveau projet** dans le menu **fichier** .

2. Sélectionnez **Win32** dans la liste des [!INCLUDE[TLA2#tla_visualcpp](../../../../includes/tla2sharptla-visualcpp-md.md)] types de projets. Si votre langue par défaut n' [!INCLUDE[TLA2#tla_cpp](../../../../includes/tla2sharptla-cpp-md.md)]est pas, vous trouverez ces types de projets dans d' **autres langues**.

3. Sélectionnez un modèle de **projet Win32** , attribuez un nom au projet et cliquez sur **OK** pour lancer l **'Assistant application Win32**.

4. Acceptez les paramètres par défaut de l’Assistant, puis cliquez sur **Terminer** pour démarrer le projet.

 Le modèle crée une application [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] de base avec les éléments suivants :

- Un point d'entrée pour l'application

- Une fenêtre avec une procédure de fenêtre associée (WndProc)

- Menu avec les en-têtes de **fichier** et **d’aide** . Le menu **fichier** comporte un élément **quitter** qui ferme l’application. Le menu **aide** contient un élément **à propos** de qui lance une boîte de dialogue simple.

 Avant de commencer à écrire du code pour [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] héberger le contenu, vous devez apporter deux modifications au modèle de base.

 La première consiste à compiler le projet sous forme de code managé. Par défaut, le projet se compile sous forme de code non managé. Cependant, comme [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] est implémenté en code managé, le projet doit être compilé en conséquence.

1. Dans **Explorateur de solutions** , cliquez avec le bouton droit sur le nom du projet, puis sélectionnez **Propriétés** dans le menu contextuel pour ouvrir la boîte de dialogue **pages de propriétés** .

2. Sélectionnez **Propriétés de configuration** dans l’arborescence dans le volet gauche.

3. Sélectionnez prise en charge du **Common Language Runtime** dans la liste **paramètres par défaut du projet** dans le volet droit.

4. Sélectionnez **prise en charge du Common Language Runtime (/CLR)** dans la zone de liste déroulante.

> [!NOTE]
>  L'indicateur de ce compilateur vous permet d'utiliser du code managé dans votre application, mais la compilation de votre code non managé se fera toujours comme avant.

 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] utilise le modèle de thread unique cloisonné (STA). Pour fonctionner correctement avec le [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] code de contenu, vous devez définir le modèle de thread de l’application sur STA en appliquant un attribut au point d’entrée.

 [!code-cpp[Win32HostingWPFPage#WinMain](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/Win32HostingWPFPage.cpp#winmain)]

<a name="hosting_the_wpf_page"></a>
### <a name="hosting-the-wpf-content"></a>Hébergement du contenu WPF
 Le [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] contenu est une application d’entrée d’adresse simple. Elle est constituée de plusieurs contrôles <xref:System.Windows.Controls.TextBox> destinés à recevoir le nom d'utilisateur, l'adresse et ainsi de suite. Il existe également deux <xref:System.Windows.Controls.Button> contrôles: **OK** et **Annuler**. Quand l’utilisateur clique sur **OK**, le <xref:System.Windows.Controls.Primitives.ButtonBase.Click> gestionnaire d’événements du bouton collecte <xref:System.Windows.Controls.TextBox> les données à partir des contrôles, les assigne aux propriétés correspondantes et déclenche un `OnButtonClicked`événement personnalisé. Quand l’utilisateur clique sur **Annuler**, le gestionnaire `OnButtonClicked`déclenche simplement. L'objet d'argument d'événement pour `OnButtonClicked` contient un champ booléen qui indique le bouton sur lequel l'utilisateur a cliqué.

 Le code permettant d’héberger le [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] contenu est implémenté dans un gestionnaire pour la notification [WM_CREATE](/windows/desktop/winmsg/wm-create) dans la fenêtre hôte.

 [!code-cpp[Win32HostingWPFPage#WMCreate](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/Win32HostingWPFPage.cpp#wmcreate)]

 La `GetHwnd` méthode prend les informations de taille et de position, ainsi que le handle de fenêtre parente et [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] retourne le handle de fenêtre du contenu hébergé.

> [!NOTE]
>  Vous ne pouvez pas utiliser de directive `#using` pour l'espace de noms `System::Windows::Interop`. Cela entraîne une collision de noms entre la structure <xref:System.Windows.Interop.MSG> de cet espace de noms et la structure MSG déclarée dans winuser.h. Vous devez à la place utiliser des noms qualifiés complets pour accéder au contenu de cet espace de noms.

 [!code-cpp[Win32HostingWPFPage#GetHwnd](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/Win32HostingWPFPage.cpp#gethwnd)]

 Vous ne pouvez pas [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] héberger le contenu directement dans la fenêtre de votre application. Vous devez plutôt commencer par créer un objet <xref:System.Windows.Interop.HwndSource> pour inclure le contenu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] dans un wrapper. Cet objet est fondamentalement une fenêtre conçue pour héberger un [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] contenu. Vous hébergez <xref:System.Windows.Interop.HwndSource> l’objet dans la fenêtre parente en le créant en tant qu' [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] enfant d’une fenêtre qui fait partie de votre application. Les paramètres de constructeur <xref:System.Windows.Interop.HwndSource> contiennent quasiment les mêmes informations que vous transmettriez à CreateWindow au moment de créer une fenêtre enfant [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)].

 Vous allez ensuite créer une instance de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] l’objet de contenu. Dans ce cas, le contenu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] est implémenté en tant que classe distincte, `WPFPage`, à l'aide de [!INCLUDE[TLA#tla_cppcli](../../../../includes/tlasharptla-cppcli-md.md)]. Vous pouvez aussi implémenter le contenu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] avec [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]. Toutefois, pour ce faire, vous devez configurer un projet distinct et générer le contenu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] sous la forme [!INCLUDE[TLA2#tla_dll](../../../../includes/tla2sharptla-dll-md.md)]d’un. Vous pouvez ajouter une référence à cette [!INCLUDE[TLA2#tla_dll](../../../../includes/tla2sharptla-dll-md.md)] à votre projet et utiliser cette référence pour créer une instance du contenu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].

 Vous affichez [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] le contenu dans votre fenêtre enfant en assignant une référence [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] au contenu <xref:System.Windows.Interop.HwndSource>à <xref:System.Windows.Interop.HwndSource.RootVisual%2A> la propriété de.

 La ligne de code suivante attache un gestionnaire d'événements, `WPFButtonClicked`, à l'événement [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] du contenu `OnButtonClicked`. Ce gestionnaire est appelé quand l’utilisateur clique sur le bouton **OK** ou **Annuler** . Pour plus d’informations sur ce gestionnaire d’événements, consultez le [contenu communicating_with_the_WPF](#communicating_with_the_page) .

 La dernière ligne de code présentée retourne le handle de fenêtre (HWND) associé à l'objet <xref:System.Windows.Interop.HwndSource>. Vous pouvez utiliser ce handle à partir de votre code [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] pour envoyer des messages à la fenêtre hébergée, même si l'exemple ne le fait pas. L'objet <xref:System.Windows.Interop.HwndSource> déclenche un événement chaque fois qu'il reçoit un message. Pour traiter les messages, appelez la méthode <xref:System.Windows.Interop.HwndSource.AddHook%2A> pour attacher un gestionnaire de messages et traiter ensuite les messages dans ce gestionnaire.

<a name="holding_a_reference"></a>
### <a name="holding-a-reference-to-the-wpf-content"></a>Stockage d'une référence au contenu WPF
 Pour de nombreuses applications, vous souhaiterez communiquer ultérieurement avec le contenu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Par exemple, vous pouvez souhaiter modifier les propriétés du contenu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ou éventuellement faire en sorte que l'objet <xref:System.Windows.Interop.HwndSource> héberge un contenu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] différent. Pour ce faire, vous avez besoin d'une référence à l'objet <xref:System.Windows.Interop.HwndSource> ou au contenu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. L'objet <xref:System.Windows.Interop.HwndSource> et son contenu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] associé restent en mémoire jusqu'à la destruction du handle de fenêtre. Cependant, la variable que vous assignez à l'objet <xref:System.Windows.Interop.HwndSource> sera hors de portée dès que vous retournerez de la procédure de fenêtre. La méthode courante employée pour gérer ce problème avec les applications [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] consiste à utiliser une variable statique ou globale. Malheureusement, vous ne pouvez pas assigner un objet managé à ces types de variable. Vous pouvez assigner le handle de fenêtre associé à l'objet <xref:System.Windows.Interop.HwndSource> à une variable globale ou statique, mais cela ne permet pas d'accéder à l'objet proprement dit.

 La solution la plus simple à ce problème consiste à implémenter une classe managée qui contient un jeu de champs statiques pour stocker les références à tous les objets managés auxquels vous devez accéder. L'exemple utilise la classe `WPFPageHost` pour stocker une référence au contenu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], plus les valeurs initiales de plusieurs de ses propriétés qui peuvent être modifiées ultérieurement par l'utilisateur. Cette option est définie dans l'en-tête.

 [!code-cpp[Win32HostingWPFPage#WPFPageHost](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/Win32HostingWPFPage.h#wpfpagehost)]

 La dernière partie de la fonction `GetHwnd` assigne des valeurs à ces champs en vue d'une utilisation ultérieure pendant que `myPage` se trouve toujours dans la portée.

<a name="communicating_with_the_page"></a>
### <a name="communicating-with-the-wpf-content"></a>Communication avec le contenu WPF
 Il existe deux types de communication avec le contenu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. L’application reçoit des informations du [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] contenu quand l’utilisateur clique sur les boutons **OK** ou **Annuler** . L'application possède aussi une [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] qui permet à l'utilisateur de modifier différentes propriétés du contenu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], telles que la couleur d'arrière-plan ou la taille de police par défaut.

 Comme indiqué précédemment, quand l'utilisateur clique sur l'un des boutons, le contenu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] déclenche un événement `OnButtonClicked`. L'application attache un gestionnaire à cet événement pour recevoir ces notifications. Si l’utilisateur a cliqué sur le bouton **OK** , le gestionnaire obtient les informations utilisateur [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] du contenu et les affiche dans un jeu de contrôles statiques.

 [!code-cpp[Win32HostingWPFPage#WPFButtonClicked](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/Win32HostingWPFPage.cpp#wpfbuttonclicked)]

 Le gestionnaire reçoit un objet d'argument d'événement personnalisé du contenu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], `MyPageEventArgs`. La propriété de `IsOK` l’objet a la `true` valeur si  l’utilisateur a cliqué sur le bouton `false` OK et si l’utilisateur a cliqué sur le bouton **Annuler** .

 Si l’utilisateur a cliqué sur le bouton **OK** , le gestionnaire obtient une référence [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] au contenu à partir de la classe de conteneur. Il recueille ensuite les informations utilisateur détenues par les propriété de contenu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] associées et utilise les contrôles statiques pour afficher les informations dans la fenêtre parente. Étant donné que les données de contenu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] se présentent sous la forme d'une chaîne managée, elles doivent être marshalées pour être utilisées par un contrôle [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]. Si l’utilisateur a cliqué sur le bouton **Annuler** , le gestionnaire efface les données des contrôles statiques.

 L'application [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] fournit un ensemble de cases d'option qui permettent à l'utilisateur de modifier la couleur d'arrière-plan du contenu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], ainsi que plusieurs propriétés liées aux polices. L'exemple suivant est un extrait de la procédure de fenêtre (WndProc) de l'application et de son traitement des messages qui définit différentes propriétés sur différents messages, notamment la couleur d'arrière-plan. Les autres sont similaires et ne sont pas illustrées. Consultez l'exemple complet pour plus de détails et pour connaître le contexte.

 [!code-cpp[Win32HostingWPFPage#WMCommandToBG](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/Win32HostingWPFPage.cpp#wmcommandtobg)]

 Pour définir la couleur d'arrière-plan, obtenez une référence au contenu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] (`hostedPage`) à partir de `WPFPageHost` et affectez à la propriété de couleur d'arrière-plan la valeur appropriée. L'exemple utilise trois options de couleur : la couleur d'origine, du vert clair ou du saumon clair. La couleur d'arrière-plan d'origine est stockée en tant que champ statique dans la classe `WPFPageHost`. Pour définir les deux autres couleurs, vous devez créer un objet <xref:System.Windows.Media.SolidColorBrush> et transmettre au constructeur une valeur de couleur statique à partir de l'objet <xref:System.Windows.Media.Colors>.

<a name="implementing_the_wpf_page"></a>
## <a name="implementing-the-wpf-page"></a>Implémentation de la page WPF
 Vous pouvez héberger et utiliser [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] le contenu sans connaître l’implémentation réelle. Si le [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] contenu a été empaqueté dans un package [!INCLUDE[TLA2#tla_dll](../../../../includes/tla2sharptla-dll-md.md)]distinct, il aurait pu être créé dans n’importe quel langage de Common Language Runtime (CLR). Voici une brève procédure pas à pas de l'implémentation [!INCLUDE[TLA#tla_cppcli](../../../../includes/tlasharptla-cppcli-md.md)] utilisée dans l'exemple. Cette section comprend les sous-sections suivantes.

<a name="autoNestedSectionsOUTLINE2"></a>
- [Disposition](#page_layout)

- [Retour des données à la fenêtre hôte](#returning_data_to_window)

- [Définition des propriétés WPF](#set_page_properties)

<a name="page_layout"></a>
### <a name="layout"></a>Mise en page
 Les [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] éléments <xref:System.Windows.Controls.TextBox> <xref:System.Windows.Controls.Label> du contenu se composent de cinq contrôles, avec des contrôles associés: [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Nom, adresse, ville, État et code postal. Il existe également deux <xref:System.Windows.Controls.Button> contrôles: **OK** et **Annuler**

 Le contenu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] est implémenté dans la classe `WPFPage`. La disposition est gérée avec un élément de disposition <xref:System.Windows.Controls.Grid>. La classe hérite de <xref:System.Windows.Controls.Grid>, qui en fait effectivement l'élément racine du contenu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].

 Le [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] constructeur de contenu prend la largeur et la hauteur requises et dimensionne <xref:System.Windows.Controls.Grid> le en conséquence. Il définit ensuite la disposition de base en créant un ensemble <xref:System.Windows.Controls.ColumnDefinition> d' <xref:System.Windows.Controls.RowDefinition> objets et et en les ajoutant <xref:System.Windows.Controls.Grid> à la <xref:System.Windows.Controls.Grid.ColumnDefinitions%2A> base <xref:System.Windows.Controls.Grid.RowDefinitions%2A> d’objet et aux collections, respectivement. Une grille contenant cinq lignes et sept colonnes est ainsi définie et ses dimensions sont déterminées par le contenu des cellules.

 [!code-cpp[Win32HostingWPFPage#WPFPageCtorToGridDef](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/WPFPage.cpp#wpfpagectortogriddef)]

 Ensuite, le constructeur ajoute les éléments [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] au <xref:System.Windows.Controls.Grid>. Le premier élément est le texte du titre, qui est un contrôle <xref:System.Windows.Controls.Label> centré dans la première ligne de la grille.

 [!code-cpp[Win32HostingWPFPage#WPFPageCtorTitle](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/WPFPage.cpp#wpfpagectortitle)]

 La ligne suivante contient le contrôle <xref:System.Windows.Controls.Label> Name (nom) et le contrôle <xref:System.Windows.Controls.TextBox> qui lui est associé. Comme le même code est utilisé pour chaque paire label/textbox, il est placé dans une paire de méthodes privées et est utilisé pour les cinq paires label/textbox. Les méthodes créent le contrôle approprié et appellent les méthodes statiques <xref:System.Windows.Controls.Grid> et <xref:System.Windows.Controls.Grid.SetColumn%2A> de la classe <xref:System.Windows.Controls.Grid.SetRow%2A> pour placer les contrôles dans la bonne cellule. Une fois le contrôle créé, l'exemple appelle la méthode <xref:System.Windows.Controls.UIElementCollection.Add%2A> sur la propriété <xref:System.Windows.Controls.Panel.Children%2A> du <xref:System.Windows.Controls.Grid> pour ajouter le contrôle à la grille. Le code permettant d'ajouter les paires label/texbox restantes est similaire. Consultez l'exemple de code pour plus d'informations.

 [!code-cpp[Win32HostingWPFPage#WPFPageCtorName](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/WPFPage.cpp#wpfpagectorname)]

 Les deux méthodes sont implémentées comme suit :

 [!code-cpp[Win32HostingWPFPage#WPFPageCreateHelpers](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/WPFPage.cpp#wpfpagecreatehelpers)]

 Enfin, l’exemple ajoute les boutons **OK** et **Annuler** et attache un gestionnaire d’événements à leurs <xref:System.Windows.Controls.Primitives.ButtonBase.Click> événements.

 [!code-cpp[Win32HostingWPFPage#WPFPageCtorButtonsEvents](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/WPFPage.cpp#wpfpagectorbuttonsevents)]

<a name="returning_data_to_window"></a>
### <a name="returning-the-data-to-the-host-window"></a>Retour des données à la fenêtre hôte
 Quand l'utilisateur clique sur l'un de ces boutons, l'événement <xref:System.Windows.Controls.Primitives.ButtonBase.Click> correspondant est déclenché. La fenêtre hôte peut attacher simplement des gestionnaires à ces événements et obtenir directement les données des contrôles <xref:System.Windows.Controls.TextBox>. L'exemple utilise une approche un peu moins directe. Il gère le <xref:System.Windows.Controls.Primitives.ButtonBase.Click> dans le [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] contenu, puis déclenche un événement `OnButtonClicked`personnalisé pour notifier le [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] contenu. Cela permet au [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] contenu de valider des paramètres avant de notifier l’hôte. Le gestionnaire obtient le texte des contrôles <xref:System.Windows.Controls.TextBox> et l'assigne aux propriétés publiques, à partir desquelles l'hôte peut extraire les informations.

 La déclaration event dans WPFPage.h :

 [!code-cpp[Win32HostingWPFPage#WPFPageEventDecl](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/WPFPage.h#wpfpageeventdecl)]

 Le gestionnaire d'événements <xref:System.Windows.Controls.Primitives.ButtonBase.Click> dans WPFPage.cpp :

 [!code-cpp[Win32HostingWPFPage#WPFPageButtonClicked](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/WPFPage.cpp#wpfpagebuttonclicked)]

<a name="set_page_properties"></a>
### <a name="setting-the-wpf-properties"></a>Définition des propriétés WPF
 L' [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] hôte permet à l’utilisateur de modifier [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] plusieurs propriétés de contenu. Du côté de [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)], il suffit de modifier des propriétés. L'implémentation dans la classe de contenu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] est plus complexe, car il n'existe aucune propriété globale unique qui contrôle les polices pour tous les contrôles. Au lieu de cela, la propriété appropriée de chaque contrôle est modifiée dans les accesseurs set des propriétés. L’exemple suivant montre le code de la `DefaultFontFamily` propriété. La définition de la propriété appelle une méthode privée qui, à son tour, définit les propriétés <xref:System.Windows.Controls.Control.FontFamily%2A> de plusieurs contrôles.

 À partir de WPFPage.h :

 [!code-cpp[Win32HostingWPFPage#WPFPageFontFamilyProperty](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/WPFPage.h#wpfpagefontfamilyproperty)]

 À partir de WPFPage.ccp :

 [!code-cpp[Win32HostingWPFPage#WPFPageSetFontFamily](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/WPFPage.cpp#wpfpagesetfontfamily)]

## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Interop.HwndSource>
- [Interopérabilité WPF et Win32](wpf-and-win32-interoperation.md)
