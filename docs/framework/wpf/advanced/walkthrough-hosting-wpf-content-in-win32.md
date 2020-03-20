---
title: Contenu WPF hôte dans Win32
titleSuffix: ''
ms.date: 03/30/2017
dev_langs:
- cpp
helpviewer_keywords:
- hosting WPF content in Win32 window [WPF]
ms.assetid: 38ce284a-4303-46dd-b699-c9365b22a7dc
ms.openlocfilehash: 8a5d556abf49c9c1f49e7853e752ebc5248d1101
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186065"
---
# <a name="walkthrough-hosting-wpf-content-in-win32"></a>Procédure pas à pas : hébergement de contenu WPF dans Win32
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] propose un environnement de création d'applications élaboré. Toutefois, lorsque vous avez un investissement substantiel dans le code [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Win32, il pourrait être plus efficace d’ajouter des fonctionnalités à votre application plutôt que de réécrire votre code d’origine. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]fournit un mécanisme [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] simple pour héberger du contenu dans une fenêtre Win32.  
  
 Ce tutoriel décrit comment écrire une application d’échantillon, Hébergement du contenu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [WPF dans un échantillon de fenêtre Win32](https://github.com/Microsoft/WPF-Samples/tree/master/Migration%20and%20Interoperability/Win32HostingWPFPage), qui héberge le contenu dans une fenêtre Win32. Vous pouvez étendre cet échantillon pour héberger n’importe quelle fenêtre Win32. Parce qu’il s’agit de mélanger le code géré et non géré, l’application est écrite en CMD/CLI.  

<a name="requirements"></a>
## <a name="requirements"></a>Spécifications  
 Ce tutoriel suppose une familiarité [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] de base avec les deux et la programmation Win32. Pour une introduction [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] de base à la programmation, voir [Getting Started](../getting-started/index.md). Pour une introduction à la programmation Win32, vous devez faire référence à l’un des nombreux livres sur le sujet, en particulier *La programmation de Windows* par Charles Petzold.  
  
 Étant donné que l’échantillon qui accompagne ce tutoriel est mis en œuvre dans le CMD/CLI, ce tutoriel suppose une familiarité avec l’utilisation de CMD pour programmer l’API Windows ainsi qu’une compréhension de la programmation de code géré. La familiarité avec le CMD/CLI est utile mais pas essentielle.  
  
> [!NOTE]
> Ce didacticiel comprend plusieurs exemples de code tirés de l'exemple associé. Cependant, pour une meilleure lecture, il n'inclut pas la totalité de l'exemple de code. Pour le code complet de l’échantillon, voir [Le contenu D’hébergement WPF dans un échantillon de fenêtre Win32](https://github.com/Microsoft/WPF-Samples/tree/master/Migration%20and%20Interoperability/Win32HostingWPFPage).  
  
<a name="basic_procedure"></a>
## <a name="the-basic-procedure"></a>Procédure de base  
 Cette section décrit la procédure de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] base que vous utilisez pour héberger du contenu dans une fenêtre Win32. Les sections restantes décrivent chaque étape dans les détails.  
  
 La clé [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] pour héberger du contenu <xref:System.Windows.Interop.HwndSource> sur une fenêtre Win32 est la classe. Cette classe enveloppe [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] le contenu dans une fenêtre Win32, [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] ce qui lui permet d’être incorporé dans votre fenêtre d’enfant. L’approche suivante combine le [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Win32 et en une seule application.  
  
1. Implémentez votre [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] contenu en classe gérée.  
  
2. Implémentez une application Windows avec CMD/CLI. Si vous commencez avec une application existante et un code CMD non géré, vous pouvez généralement lui `/clr` permettre d’appeler le code géré en modifiant les paramètres de votre projet pour inclure le drapeau compilateur.  
  
3. Affectez au modèle de thread un thread unique cloisonné (STA, Single-Threaded Apartment).  
  
4. Gérez la notification [WM_CREATE](/windows/desktop/winmsg/wm-create)dans votre procédure de fenêtre et faites ce qui suit :  
  
    1. Créez un objet <xref:System.Windows.Interop.HwndSource> en faisant de la fenêtre parente son paramètre `parent`.  
  
    2. Créez une instance de la classe de contenu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
    3. Attribuer une référence [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] à l’objet de contenu à la <xref:System.Windows.Interop.HwndSource.RootVisual%2A> propriété de la <xref:System.Windows.Interop.HwndSource>.  
  
    4. Obtenez le HWND pour le contenu. La propriété <xref:System.Windows.Interop.HwndSource.Handle%2A> de l'objet <xref:System.Windows.Interop.HwndSource> contient le handle de fenêtre (HWND). Pour obtenir un HWND que vous pouvez utiliser dans la partie non managée de l'application, effectuez un cast de `Handle.ToPointer()` en HWND.  
  
5. Implémentez une classe managée qui contient un champ statique pour contenir une référence à votre contenu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Cette classe vous permet d’obtenir une référence au [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] contenu de votre code Win32.  
  
6. Assignez le contenu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] au champ statique.  
  
7. Recevez des notifications du [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] contenu en attachant un [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] gestionnaire à un ou plusieurs des événements.  
  
8. Communiquez avec le contenu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] en utilisant la référence que vous avez stockée dans le champ statique pour définir les propriétés, etc.  
  
> [!NOTE]
> Vous pouvez [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] également utiliser [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] pour implémenter votre contenu. Cependant, vous devrez le compiler séparément en tant que bibliothèque à liaison dynamique (DLL) et référencer celui DLL de votre application Win32. Le reste de la procédure est similaire à celle présentée ci-dessus.

<a name="implementing_the_application"></a>
## <a name="implementing-the-host-application"></a>Implémentation de l'application hôte.
 Cette section décrit comment [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] héberger le contenu dans une application de base Win32. Le contenu lui-même est implémenté dans la catégorie CMD/CLI en tant que classe gérée. Pour l'essentiel, il s'agit d'une programmation [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] simple. Les aspects clés de l’implémentation du contenu sont discutés dans [la mise en œuvre du contenu WPF](#implementing_the_wpf_page).

- [Application de base](#the_basic_application)

- [Hébergement du contenu WPF](#hosting_the_wpf_page)

- [Stockage d'une référence au contenu WPF](#holding_a_reference)

- [Communication avec le contenu WPF](#communicating_with_the_page)

<a name="the_basic_application"></a>
### <a name="the-basic-application"></a>Application de base
 Le point de départ de l’application hôte était de créer un modèle Visual Studio 2005.

1. Ouvrez Visual Studio 2005 et sélectionnez **New Project** dans le menu **File.**

2. Sélectionnez **Win32** dans la liste des types de projets Visual CMD. Si votre langue par défaut n’est pas C, vous trouverez ces types de projets sous **d’autres langues**.

3. Sélectionnez un modèle **de projet Win32,** attribuez un nom au projet et cliquez **sur OK** pour lancer **l’assistant d’application Win32**.

4. Acceptez les paramètres par défaut de l’assistant et cliquez sur **Finition** pour démarrer le projet.

 Le modèle crée une application de base Win32, y compris:

- Un point d'entrée pour l'application

- Une fenêtre avec une procédure de fenêtre associée (WndProc)

- Un menu avec **des rubriques** et des rubriques **d’aide.** Le menu **Fichier** dispose d’un élément **de sortie** qui ferme l’application. Le menu **Aide** dispose **d’un** article About qui lance une simple boîte de dialogue.

 Avant de commencer à [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] écrire du code pour héberger le contenu, vous devez apporter deux modifications au modèle de base.

 La première consiste à compiler le projet sous forme de code managé. Par défaut, le projet se compile sous forme de code non managé. Cependant, comme [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] est implémenté en code managé, le projet doit être compilé en conséquence.

1. Cliquez à droite sur le nom du projet dans **Solution Explorer** et sélectionnez **les propriétés** du menu contextuelle pour lancer la boîte de dialogue **des Pages de propriété.**

2. Sélectionnez **les propriétés** de configuration de la vue de l’arbre dans la vitre gauche.

3. Sélectionnez le support **Common Language Runtime** de la liste **des défauts de projet** dans le bon volet.

4. Sélectionnez **Common Language Runtime Support (/clr)** dans la case liste d’abandon.

> [!NOTE]
> L'indicateur de ce compilateur vous permet d'utiliser du code managé dans votre application, mais la compilation de votre code non managé se fera toujours comme avant.

 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] utilise le modèle de thread unique cloisonné (STA). Afin de fonctionner correctement [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] avec le code de contenu, vous devez définir le modèle de threading de l’application à STA en appliquant un attribut au point d’entrée.

 [!code-cpp[Win32HostingWPFPage#WinMain](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/Win32HostingWPFPage.cpp#winmain)]

<a name="hosting_the_wpf_page"></a>
### <a name="hosting-the-wpf-content"></a>Hébergement du contenu WPF
 Le [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] contenu est une simple application d’entrée d’adresse. Elle est constituée de plusieurs contrôles <xref:System.Windows.Controls.TextBox> destinés à recevoir le nom d'utilisateur, l'adresse et ainsi de suite. Il ya <xref:System.Windows.Controls.Button> aussi deux contrôles, **OK** et **Annuler**. Lorsque l’utilisateur clique **sur OK,** le gestionnaire d’événements du <xref:System.Windows.Controls.Primitives.ButtonBase.Click> bouton recueille les données des contrôles, les <xref:System.Windows.Controls.TextBox> attribue aux propriétés correspondantes, et soulève un événement personnalisé, `OnButtonClicked`. Lorsque l’utilisateur clique **Annuler**, `OnButtonClicked`le gestionnaire soulève simplement . L'objet d'argument d'événement pour `OnButtonClicked` contient un champ booléen qui indique le bouton sur lequel l'utilisateur a cliqué.

 Le code pour [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] héberger le contenu est implémenté dans un gestionnaire pour la notification [WM_CREATE](/windows/desktop/winmsg/wm-create) sur la fenêtre d’hôte.

 [!code-cpp[Win32HostingWPFPage#WMCreate](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/Win32HostingWPFPage.cpp#wmcreate)]

 La `GetHwnd` méthode prend des informations de taille et de position ainsi [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] que la poignée de fenêtre parente et renvoie la poignée de fenêtre du contenu hébergé.

> [!NOTE]
> Vous ne pouvez pas utiliser de directive `#using` pour l'espace de noms `System::Windows::Interop`. Cela entraîne une collision de noms entre la structure <xref:System.Windows.Interop.MSG> de cet espace de noms et la structure MSG déclarée dans winuser.h. Vous devez à la place utiliser des noms qualifiés complets pour accéder au contenu de cet espace de noms.

 [!code-cpp[Win32HostingWPFPage#GetHwnd](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/Win32HostingWPFPage.cpp#gethwnd)]

 Vous ne [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] pouvez pas héberger le contenu directement dans votre fenêtre d’application. Vous devez plutôt commencer par créer un objet <xref:System.Windows.Interop.HwndSource> pour inclure le contenu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] dans un wrapper. Cet objet est essentiellement une fenêtre [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] qui est conçu pour héberger un contenu. Vous hébergez l’objet <xref:System.Windows.Interop.HwndSource> dans la fenêtre parent en le créant comme un enfant d’une fenêtre Win32 qui fait partie de votre application. Les <xref:System.Windows.Interop.HwndSource> paramètres du constructeur contiennent à peu près les mêmes informations que vous passeriez à CreateWindow lorsque vous créez une fenêtre Pour enfants Win32.

 Vous créez ensuite une [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] instance de l’objet de contenu. Dans ce cas, le [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] contenu est `WPFPage`implémenté en tant que classe distincte, en utilisant CMD/CLI. Vous pouvez aussi implémenter le contenu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] avec [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]. Toutefois, pour ce faire, vous devez configurer [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] un projet distinct et construire le contenu en tant que DLL. Vous pouvez ajouter une référence à ce DLL à votre projet, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] et utiliser cette référence pour créer une instance du contenu.

 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Vous affichez le contenu dans la fenêtre [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] de votre <xref:System.Windows.Interop.HwndSource.RootVisual%2A> enfant en assignant une référence au contenu à la propriété de la <xref:System.Windows.Interop.HwndSource>.

 La ligne de code suivante attache un gestionnaire d'événements, `WPFButtonClicked`, à l'événement [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] du contenu `OnButtonClicked`. Ce gestionnaire est appelé lorsque l’utilisateur clique sur le bouton **OK** ou **Annuler.** Consultez [communicating_with_the_WPF contenu](#communicating_with_the_page) pour une discussion plus approfondie sur ce gestionnaire d’événements.

 La dernière ligne de code présentée retourne le handle de fenêtre (HWND) associé à l'objet <xref:System.Windows.Interop.HwndSource>. Vous pouvez utiliser cette poignée à partir de votre code Win32 pour envoyer des messages à la fenêtre hébergée, bien que l’échantillon ne le fasse pas. L'objet <xref:System.Windows.Interop.HwndSource> déclenche un événement chaque fois qu'il reçoit un message. Pour traiter les messages, appelez la méthode <xref:System.Windows.Interop.HwndSource.AddHook%2A> pour attacher un gestionnaire de messages et traiter ensuite les messages dans ce gestionnaire.

<a name="holding_a_reference"></a>
### <a name="holding-a-reference-to-the-wpf-content"></a>Stockage d'une référence au contenu WPF
 Pour de nombreuses applications, vous souhaiterez communiquer ultérieurement avec le contenu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Par exemple, vous pouvez souhaiter modifier les propriétés du contenu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ou éventuellement faire en sorte que l'objet <xref:System.Windows.Interop.HwndSource> héberge un contenu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] différent. Pour ce faire, vous avez besoin d'une référence à l'objet <xref:System.Windows.Interop.HwndSource> ou au contenu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. L'objet <xref:System.Windows.Interop.HwndSource> et son contenu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] associé restent en mémoire jusqu'à la destruction du handle de fenêtre. Cependant, la variable que vous assignez à l'objet <xref:System.Windows.Interop.HwndSource> sera hors de portée dès que vous retournerez de la procédure de fenêtre. La façon habituelle de gérer ce problème avec les applications Win32 est d’utiliser une variable statique ou globale. Malheureusement, vous ne pouvez pas assigner un objet managé à ces types de variable. Vous pouvez assigner le handle de fenêtre associé à l'objet <xref:System.Windows.Interop.HwndSource> à une variable globale ou statique, mais cela ne permet pas d'accéder à l'objet proprement dit.

 La solution la plus simple à ce problème consiste à implémenter une classe managée qui contient un jeu de champs statiques pour stocker les références à tous les objets managés auxquels vous devez accéder. L'exemple utilise la classe `WPFPageHost` pour stocker une référence au contenu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], plus les valeurs initiales de plusieurs de ses propriétés qui peuvent être modifiées ultérieurement par l'utilisateur. Cette option est définie dans l'en-tête.

 [!code-cpp[Win32HostingWPFPage#WPFPageHost](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/Win32HostingWPFPage.h#wpfpagehost)]

 La dernière partie de la fonction `GetHwnd` assigne des valeurs à ces champs en vue d'une utilisation ultérieure pendant que `myPage` se trouve toujours dans la portée.

<a name="communicating_with_the_page"></a>
### <a name="communicating-with-the-wpf-content"></a>Communication avec le contenu WPF
 Il existe deux types de communication avec le contenu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. L’application reçoit [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] des informations du contenu lorsque l’utilisateur clique sur les boutons **OK** ou **Annuler.** L'application possède aussi une [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] qui permet à l'utilisateur de modifier différentes propriétés du contenu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], telles que la couleur d'arrière-plan ou la taille de police par défaut.

 Comme indiqué précédemment, quand l'utilisateur clique sur l'un des boutons, le contenu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] déclenche un événement `OnButtonClicked`. L'application attache un gestionnaire à cet événement pour recevoir ces notifications. Si le bouton **OK** a été cliqué, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] le gestionnaire obtient les informations utilisateur du contenu et les affiche dans un ensemble de contrôles statiques.

 [!code-cpp[Win32HostingWPFPage#WPFButtonClicked](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/Win32HostingWPFPage.cpp#wpfbuttonclicked)]

 Le gestionnaire reçoit un objet d'argument d'événement personnalisé du contenu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], `MyPageEventArgs`. La propriété `IsOK` de l’objet est réglée `true` à si `false` le bouton **OK** a été cliqué, et si le bouton **Annuler** a été cliqué.

 Si le bouton **OK** a été cliqué, le gestionnaire obtient une référence au [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] contenu de la classe de conteneurs. Il recueille ensuite les informations utilisateur détenues par les propriété de contenu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] associées et utilise les contrôles statiques pour afficher les informations dans la fenêtre parente. Étant [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] donné que les données de contenu sont sous la forme d’une chaîne gérée, elles doivent être mobilisées pour être utilisées par un contrôle Win32. Si le bouton **Annuler** a été cliqué, le gestionnaire efface les données des commandes statiques.

 L'application [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] fournit un ensemble de cases d'option qui permettent à l'utilisateur de modifier la couleur d'arrière-plan du contenu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], ainsi que plusieurs propriétés liées aux polices. L'exemple suivant est un extrait de la procédure de fenêtre (WndProc) de l'application et de son traitement des messages qui définit différentes propriétés sur différents messages, notamment la couleur d'arrière-plan. Les autres sont similaires et ne sont pas illustrées. Consultez l'exemple complet pour plus de détails et pour connaître le contexte.

 [!code-cpp[Win32HostingWPFPage#WMCommandToBG](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/Win32HostingWPFPage.cpp#wmcommandtobg)]

 Pour définir la couleur d'arrière-plan, obtenez une référence au contenu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] (`hostedPage`) à partir de `WPFPageHost` et affectez à la propriété de couleur d'arrière-plan la valeur appropriée. L'exemple utilise trois options de couleur : la couleur d'origine, du vert clair ou du saumon clair. La couleur d'arrière-plan d'origine est stockée en tant que champ statique dans la classe `WPFPageHost`. Pour définir les deux autres couleurs, vous devez créer un objet <xref:System.Windows.Media.SolidColorBrush> et transmettre au constructeur une valeur de couleur statique à partir de l'objet <xref:System.Windows.Media.Colors>.

<a name="implementing_the_wpf_page"></a>
## <a name="implementing-the-wpf-page"></a>Implémentation de la page WPF
 Vous pouvez héberger [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] et utiliser le contenu sans aucune connaissance de la mise en œuvre réelle. Si [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] le contenu avait été emballé dans un DLL distinct, il aurait pu être construit dans n’importe quelle langue commune runtime (CLR) langue. Voici une brève procédure pas à pas de la mise en œuvre de l’IMC et de l’IMC qui est utilisée dans l’échantillon. Cette section comprend les sous-sections suivantes.

- [Disposition](#page_layout)

- [Retour des données à la fenêtre hôte](#returning_data_to_window)

- [Définition des propriétés WPF](#set_page_properties)

<a name="page_layout"></a>
### <a name="layout"></a>Disposition
 Les [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] éléments [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] du contenu <xref:System.Windows.Controls.TextBox> sont composés <xref:System.Windows.Controls.Label> de cinq contrôles, avec les contrôles associés: Nom, Adresse, Ville, État et Zip. Il ya <xref:System.Windows.Controls.Button> aussi deux contrôles, **OK** et **Annuler**

 Le contenu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] est implémenté dans la classe `WPFPage`. La disposition est gérée avec un élément de disposition <xref:System.Windows.Controls.Grid>. La classe hérite de <xref:System.Windows.Controls.Grid>, qui en fait effectivement l'élément racine du contenu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].

 Le [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] constructeur de contenu prend la largeur et <xref:System.Windows.Controls.Grid> la hauteur requises, et taille en conséquence. Il définit ensuite la mise en <xref:System.Windows.Controls.ColumnDefinition> page <xref:System.Windows.Controls.RowDefinition> de base en <xref:System.Windows.Controls.Grid> créant <xref:System.Windows.Controls.Grid.ColumnDefinitions%2A> <xref:System.Windows.Controls.Grid.RowDefinitions%2A> un ensemble et des objets et en les ajoutant à la base d’objets et aux collections, respectivement. Une grille contenant cinq lignes et sept colonnes est ainsi définie et ses dimensions sont déterminées par le contenu des cellules.

 [!code-cpp[Win32HostingWPFPage#WPFPageCtorToGridDef](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/WPFPage.cpp#wpfpagectortogriddef)]

 Ensuite, le constructeur ajoute les éléments [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] au <xref:System.Windows.Controls.Grid>. Le premier élément est le texte du titre, qui est un contrôle <xref:System.Windows.Controls.Label> centré dans la première ligne de la grille.

 [!code-cpp[Win32HostingWPFPage#WPFPageCtorTitle](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/WPFPage.cpp#wpfpagectortitle)]

 La ligne suivante contient le contrôle <xref:System.Windows.Controls.Label> Name (nom) et le contrôle <xref:System.Windows.Controls.TextBox> qui lui est associé. Comme le même code est utilisé pour chaque paire label/textbox, il est placé dans une paire de méthodes privées et est utilisé pour les cinq paires label/textbox. Les méthodes créent le contrôle approprié et appellent les méthodes statiques <xref:System.Windows.Controls.Grid> et <xref:System.Windows.Controls.Grid.SetColumn%2A> de la classe <xref:System.Windows.Controls.Grid.SetRow%2A> pour placer les contrôles dans la bonne cellule. Une fois le contrôle créé, l'exemple appelle la méthode <xref:System.Windows.Controls.UIElementCollection.Add%2A> sur la propriété <xref:System.Windows.Controls.Panel.Children%2A> du <xref:System.Windows.Controls.Grid> pour ajouter le contrôle à la grille. Le code permettant d'ajouter les paires label/texbox restantes est similaire. Consultez l'exemple de code pour plus d'informations.

 [!code-cpp[Win32HostingWPFPage#WPFPageCtorName](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/WPFPage.cpp#wpfpagectorname)]

 Les deux méthodes sont implémentées comme suit :

 [!code-cpp[Win32HostingWPFPage#WPFPageCreateHelpers](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/WPFPage.cpp#wpfpagecreatehelpers)]

 Enfin, l’échantillon ajoute les boutons **OK** et **Annuler** <xref:System.Windows.Controls.Primitives.ButtonBase.Click> et attache un gestionnaire d’événements à leurs événements.

 [!code-cpp[Win32HostingWPFPage#WPFPageCtorButtonsEvents](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/WPFPage.cpp#wpfpagectorbuttonsevents)]

<a name="returning_data_to_window"></a>
### <a name="returning-the-data-to-the-host-window"></a>Retour des données à la fenêtre hôte
 Quand l'utilisateur clique sur l'un de ces boutons, l'événement <xref:System.Windows.Controls.Primitives.ButtonBase.Click> correspondant est déclenché. La fenêtre hôte peut attacher simplement des gestionnaires à ces événements et obtenir directement les données des contrôles <xref:System.Windows.Controls.TextBox>. L'exemple utilise une approche un peu moins directe. Il gère <xref:System.Windows.Controls.Primitives.ButtonBase.Click> le [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] contenu dans le contenu, `OnButtonClicked`puis soulève [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] un événement personnalisé , pour informer le contenu. Cela permet [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] au contenu de faire une certaine validation des paramètres avant d’aviser l’hôte. Le gestionnaire obtient le texte des contrôles <xref:System.Windows.Controls.TextBox> et l'assigne aux propriétés publiques, à partir desquelles l'hôte peut extraire les informations.

 La déclaration event dans WPFPage.h :

 [!code-cpp[Win32HostingWPFPage#WPFPageEventDecl](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/WPFPage.h#wpfpageeventdecl)]

 Le gestionnaire d'événements <xref:System.Windows.Controls.Primitives.ButtonBase.Click> dans WPFPage.cpp :

 [!code-cpp[Win32HostingWPFPage#WPFPageButtonClicked](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/WPFPage.cpp#wpfpagebuttonclicked)]

<a name="set_page_properties"></a>
### <a name="setting-the-wpf-properties"></a>Définition des propriétés WPF
 L’hôte Win32 permet à [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] l’utilisateur de modifier plusieurs propriétés de contenu. Du côté win32, il s’agit simplement de changer les propriétés. L'implémentation dans la classe de contenu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] est plus complexe, car il n'existe aucune propriété globale unique qui contrôle les polices pour tous les contrôles. Au lieu de cela, la propriété appropriée de chaque contrôle est modifiée dans les accesseurs set des propriétés. L’exemple suivant montre `DefaultFontFamily` le code de la propriété. La définition de la propriété appelle une méthode privée qui, à son tour, définit les propriétés <xref:System.Windows.Controls.Control.FontFamily%2A> de plusieurs contrôles.

 À partir de WPFPage.h :

 [!code-cpp[Win32HostingWPFPage#WPFPageFontFamilyProperty](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/WPFPage.h#wpfpagefontfamilyproperty)]

 À partir de WPFPage.ccp :

 [!code-cpp[Win32HostingWPFPage#WPFPageSetFontFamily](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/WPFPage.cpp#wpfpagesetfontfamily)]

## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Interop.HwndSource>
- [Interopérabilité WPF et Win32](wpf-and-win32-interoperation.md)
