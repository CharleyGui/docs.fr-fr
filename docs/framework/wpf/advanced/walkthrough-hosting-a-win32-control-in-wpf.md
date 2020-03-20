---
title: Organiser un contrôle Win32 dans WPF
titleSuffix: ''
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hosting Win32 control in WPF [WPF]
- Win32 code [WPF], WPF interoperation
ms.assetid: a676b1eb-fc55-4355-93ab-df840c41cea0
ms.openlocfilehash: 5185e60640c652b79bd105db54830ac3acc57129
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186741"
---
# <a name="walkthrough-host-a-win32-control-in-wpf"></a>Procédure pas à pas: accueillir un contrôle Win32 dans WPF
Windows Presentation Foundation (WPF) offre un environnement riche pour créer des applications. Toutefois, lorsque vous avez un investissement substantiel dans le code Win32, il peut être plus efficace de réutiliser au moins une partie de ce code dans votre application WPF plutôt que de le réécrire complètement. WPF fournit un mécanisme simple pour héberger une fenêtre Win32, sur une page WPF.  
  
 Ce sujet vous guide à travers une application, [l’hébergement d’un contrôle Win32 ListBox dans L’échantillon WPF](https://github.com/Microsoft/WPF-Samples/tree/master/Migration%20and%20Interoperability/WPFHostingWin32Control), qui héberge un contrôle de la boîte de liste Win32. Cette procédure générale peut être étendue à l’hébergement de n’importe quelle fenêtre Win32.  

<a name="requirements"></a>
## <a name="requirements"></a>Spécifications  
 Ce sujet suppose une familiarité de base avec la programmation WPF et Windows API. Pour une introduction de base à la programmation WPF, voir [Getting Started](../getting-started/index.md). Pour une introduction à la programmation de Windows API, voir l’un des nombreux livres sur le sujet, en particulier *La programmation de Windows* par Charles Petzold.  
  
 Étant donné que l’échantillon qui accompagne ce sujet est mis en œuvre dans le C, il utilise platform Invocation Services (PInvoke) pour accéder à l’API Windows. Une certaine familiarité avec PInvoke est utile, mais pas essentiel.  
  
> [!NOTE]
> Cette rubrique comprend plusieurs exemples de code tirés de l'exemple associé. Cependant, pour une meilleure lecture, il n'inclut pas la totalité de l'exemple de code. Vous pouvez obtenir ou afficher le code complet de [l’hébergement d’un contrôle Win32 ListBox dans l’échantillon WPF](https://github.com/Microsoft/WPF-Samples/tree/master/Migration%20and%20Interoperability/WPFHostingWin32Control).  
  
<a name="basic_procedure"></a>
## <a name="the-basic-procedure"></a>Procédure de base  
 Cette section décrit la procédure de base pour l’hébergement d’une fenêtre Win32 sur une page WPF. Les sections restantes décrivent chaque étape en détails.  
  
 La procédure d’hébergement de base est la suivante :  
  
1. Implémenter une page WPF pour héberger la fenêtre. Une technique consiste <xref:System.Windows.Controls.Border> à créer un élément pour réserver une section de la page pour la fenêtre hébergée.  
  
2. Mettre en œuvre une classe <xref:System.Windows.Interop.HwndHost>pour accueillir le contrôle qui hérite de .  
  
3. Dans cette classe, <xref:System.Windows.Interop.HwndHost> remplacez <xref:System.Windows.Interop.HwndHost.BuildWindowCore%2A>le membre de la classe .  
  
4. Créez la fenêtre hébergée comme un enfant de la fenêtre qui contient la page WPF. Bien que la programmation WPF conventionnelle n’ait pas besoin de s’en servir explicitement, la page d’hébergement est une fenêtre avec une poignée (HWND). Vous recevez la page HWND à travers le `hwndParent` paramètre de la <xref:System.Windows.Interop.HwndHost.BuildWindowCore%2A> méthode. La fenêtre hébergée doit être créée comme un enfant de ce HWND.  
  
5. Une fois que vous avez créé la fenêtre hôte, retournez le HWND de la fenêtre hébergée. Si vous souhaitez héberger un ou plusieurs contrôles Win32, vous créez généralement une fenêtre d’accueil comme un enfant de la HWND et faire les contrôles enfants de cette fenêtre hôte. L’emballage des commandes dans une fenêtre d’hôte fournit un moyen simple pour votre page WPF de recevoir des notifications des contrôles, qui traite de certains problèmes Win32 particuliers avec des notifications à travers la limite HWND.  
  
6. Gérez les messages sélectionnés envoyés à la fenêtre hôte, comme les notifications des contrôles enfants. Il existe deux façons d'effectuer cette opération.  
  
    - Si vous préférez gérer des messages dans <xref:System.Windows.Interop.HwndHost.WndProc%2A> votre classe <xref:System.Windows.Interop.HwndHost> d’hébergement, remplacez la méthode de la classe.  
  
    - Si vous préférez que le WPF gère <xref:System.Windows.Interop.HwndHost> <xref:System.Windows.Interop.HwndHost.MessageHook> les messages, gérez l’événement de classe dans votre code-derrière. Cet événement se produit pour chaque message reçu par la fenêtre hébergée. Si vous choisissez cette option, <xref:System.Windows.Interop.HwndHost.WndProc%2A>vous devez toujours passer outre, mais vous n’avez besoin que d’une implémentation minimale.  
  
7. Remplacer les <xref:System.Windows.Interop.HwndHost.DestroyWindowCore%2A> <xref:System.Windows.Interop.HwndHost.WndProc%2A> méthodes <xref:System.Windows.Interop.HwndHost>et les méthodes de . Vous devez passer outre à <xref:System.Windows.Interop.HwndHost> ces méthodes pour satisfaire le contrat, mais vous n’aurez peut-être qu’à fournir une mise en œuvre minimale.  
  
8. Dans votre fichier de code,derrière, créez un exemple de la <xref:System.Windows.Controls.Border> classe d’hébergement de contrôle et faites-en un enfant de l’élément qui est destiné à héberger la fenêtre.  
  
9. Communiquez avec la fenêtre hébergée en lui envoyant des messages Microsoft Windows et en manipulant des messages à partir de ses fenêtres d’enfants, telles que les notifications envoyées par les contrôles.  
  
<a name="page_layout"></a>
## <a name="implement-the-page-layout"></a>Implémenter la disposition de la page  
 La mise en page de la page WPF qui héberge le contrôle ListBox se compose de deux régions. Le côté gauche de la page héberge [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] plusieurs contrôles WPF qui fournissent un qui vous permet de manipuler le contrôle Win32. Le coin en haut à droite de la page contient une zone carrée pour le contrôle ListBox hébergé.  
  
 Le code pour implémenter cette mise en page est assez simple. L’élément racine <xref:System.Windows.Controls.DockPanel> est un qui a deux éléments enfant. Le premier <xref:System.Windows.Controls.Border> est un élément qui héberge le contrôle ListBox. Il occupe un carré de 200 x 200 en haut à droite de la page. Le second <xref:System.Windows.Controls.StackPanel> est un élément qui contient un ensemble de contrôles WPF qui affichent des informations et vous permettent de manipuler le contrôle ListBox en définissant les propriétés d’interopération exposées. Pour chacun des éléments qui <xref:System.Windows.Controls.StackPanel>sont des enfants de la , voir le matériel de référence pour les différents éléments utilisés pour les détails sur ce que ces éléments sont ou ce qu’ils font, ceux-ci sont énumérés dans le code de l’exemple ci-dessous, mais ne seront pas expliqués ici (le modèle d’interopération de base ne nécessite aucun d’entre eux, ils sont fournis pour ajouter une certaine interactivité à l’échantillon).  
  
 [!code-xaml[WPFHostingWin32Control#WPFUI](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/Page1.xaml#wpfui)]  
  
<a name="host_class"></a>
## <a name="implement-a-class-to-host-the-microsoft-win32-control"></a>Implémenter une classe pour héberger le contrôle Microsoft Win32  
 Le cœur de cet exemple est la classe qui héberge réellement le contrôle, ControlHost.cs. Hérite de <xref:System.Windows.Interop.HwndHost>. Le constructeur prend deux paramètres, la hauteur et la largeur, <xref:System.Windows.Controls.Border> qui correspondent à la hauteur et la largeur de l’élément qui héberge le contrôle ListBox. Ces valeurs sont utilisées plus tard pour s’assurer que la taille du contrôle correspond à l’élément. <xref:System.Windows.Controls.Border>  
  
 [!code-csharp[WPFHostingWin32Control#ControlHostClass](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/ControlHost.cs#controlhostclass)]
 [!code-vb[WPFHostingWin32Control#ControlHostClass](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/ControlHost.vb#controlhostclass)]  
  
 Il existe également un ensemble de constantes. Ces constantes sont en grande partie prises de Winuser.h, et vous permettent d’utiliser des noms conventionnels lors de l’appel Win32 fonctions.  
  
 [!code-csharp[WPFHostingWin32Control#ControlHostConstants](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/ControlHost.cs#controlhostconstants)]
 [!code-vb[WPFHostingWin32Control#ControlHostConstants](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/ControlHost.vb#controlhostconstants)]  
  
<a name="buildwindowcore"></a>
### <a name="override-buildwindowcore-to-create-the-microsoft-win32-window"></a>Substituer BuildWindowCore pour créer la fenêtre Microsoft Win32  
 Vous remplacez cette méthode pour créer la fenêtre Win32 qui sera hébergée par la page, et faire la connexion entre la fenêtre et la page. Comme cet exemple implique l’hébergement d’un contrôle ListBox, deux fenêtres sont créées. La première est la fenêtre qui est effectivement hébergée par la page WPF. Le contrôle ListBox est créé comme un enfant de cette fenêtre.  
  
 Cette approche a pour but de simplifier le processus de réception des notifications du contrôle. Le <xref:System.Windows.Interop.HwndHost> cours vous permet de traiter les messages envoyés à la fenêtre qu’il héberge. Si vous hébergez directement un contrôle Win32, vous recevez les messages envoyés à la boucle de message interne du contrôle. Vous pouvez afficher le contrôle et lui envoyer des messages, mais vous ne recevez pas les notifications que le contrôle envoie à sa fenêtre parente. Cela signifie, entre autres, que vous n’avez aucun moyen de détecter quand l’utilisateur interagit avec le contrôle. Au lieu de cela, créez une fenêtre hôte et définissez le contrôle comme un enfant de cette fenêtre. Cela vous permet de traiter les messages de la fenêtre hôte, y compris les notifications que le contrôle lui envoie. Pour des raisons pratiques, comme la fenêtre hôte n’est guère plus qu’un simple wrapper pour le contrôle, le package est un contrôle ListBox.  
  
<a name="create_the_window_and_listbox"></a>
#### <a name="create-the-host-window-and-listbox-control"></a>Créer la fenêtre hôte et un contrôle ListBox  
 Vous pouvez utiliser PInvoke pour créer une fenêtre hôte pour le contrôle en créant et en enregistrant une classe de fenêtre, et ainsi de suite. Toutefois, vous pouvez, beaucoup plus simplement, créer une fenêtre avec la classe de fenêtre « statique » prédéfinie. Cela vous fournit la procédure de fenêtre dont vous avez besoin pour recevoir les notifications du contrôle et nécessite un minimum de codage.  
  
 Le HWND du contrôle est exposé au moyen d’une propriété en lecture seule, de sorte que la page hôte peut l’utiliser pour envoyer des messages au contrôle.  
  
 [!code-csharp[WPFHostingWin32Control#IntPtrProperty](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/ControlHost.cs#intptrproperty)]
 [!code-vb[WPFHostingWin32Control#IntPtrProperty](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/ControlHost.vb#intptrproperty)]  
  
 Le contrôle ListBox est créé comme un enfant de la fenêtre hébergée. La hauteur et la largeur des deux fenêtres sont définies sur les valeurs passées au constructeur, comme décrit ci-dessus. Cela garantit que la taille de la fenêtre hôte et du contrôle est identique à la zone réservée dans la page.  Une fois les fenêtres créées, <xref:System.Runtime.InteropServices.HandleRef> l’échantillon renvoie un objet qui contient le HWND de la fenêtre hôte.  
  
 [!code-csharp[WPFHostingWin32Control#BuildWindowCore](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/ControlHost.cs#buildwindowcore)]
 [!code-vb[WPFHostingWin32Control#BuildWindowCore](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/ControlHost.vb#buildwindowcore)]  
  
 [!code-csharp[WPFHostingWin32Control#BuildWindowCoreHelper](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/ControlHost.cs#buildwindowcorehelper)]
 [!code-vb[WPFHostingWin32Control#BuildWindowCoreHelper](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/ControlHost.vb#buildwindowcorehelper)]  
  
<a name="destroywindow_wndproc"></a>
### <a name="implement-destroywindow-and-wndproc"></a>Implémenter DestroyWindow et WndProc  
 En plus <xref:System.Windows.Interop.HwndHost.BuildWindowCore%2A>de , vous <xref:System.Windows.Interop.HwndHost.WndProc%2A> devez <xref:System.Windows.Interop.HwndHost.DestroyWindowCore%2A> également <xref:System.Windows.Interop.HwndHost>remplacer le et les méthodes de la . Dans cet exemple, les messages pour le <xref:System.Windows.Interop.HwndHost.MessageHook> contrôle sont manipulés <xref:System.Windows.Interop.HwndHost.DestroyWindowCore%2A> par le gestionnaire, donc la mise en œuvre et <xref:System.Windows.Interop.HwndHost.WndProc%2A> est minime. Dans le <xref:System.Windows.Interop.HwndHost.WndProc%2A>cas `handled` de `false` , pour indiquer que le message n’a pas été manipulé et retour 0. Pour <xref:System.Windows.Interop.HwndHost.DestroyWindowCore%2A>, il suffit de détruire la fenêtre.  
  
 [!code-csharp[WPFHostingWin32Control#WndProcDestroy](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/ControlHost.cs#wndprocdestroy)]
 [!code-vb[WPFHostingWin32Control#WndProcDestroy](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/ControlHost.vb#wndprocdestroy)]  
  
 [!code-csharp[WPFHostingWin32Control#WndProcDestroyHelper](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/ControlHost.cs#wndprocdestroyhelper)]
 [!code-vb[WPFHostingWin32Control#WndProcDestroyHelper](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/ControlHost.vb#wndprocdestroyhelper)]  
  
<a name="host_the_control"></a>
## <a name="host-the-control-on-the-page"></a>Héberger le contrôle dans la page  
 Pour héberger le contrôle sur la page, `ControlHost` vous créez d’abord une nouvelle instance de la classe. Passer la hauteur et la largeur de l’élément frontière qui contient le contrôle ()`ControlHostElement`au `ControlHost` constructeur. Cela garantit que la taille du ListBox est correcte. Vous hébergez ensuite le contrôle sur `ControlHost` la <xref:System.Windows.Controls.Decorator.Child%2A> page en <xref:System.Windows.Controls.Border>assignant l’objet à la propriété de l’hôte .  
  
 L’échantillon attache un <xref:System.Windows.Interop.HwndHost.MessageHook> gestionnaire à `ControlHost` l’événement de la pour recevoir des messages du contrôle. Cet événement est déclenché pour chaque message envoyé à la fenêtre hébergée. Dans ce cas, il s’agit des messages envoyés à la fenêtre qui encapsule le contrôle ListBox réel, y compris les notifications du contrôle. L’exemple appelle SendMessage pour obtenir des informations du contrôle et modifier son contenu. Les détails sur la façon dont la page communique avec le contrôle sont décrits dans la section suivante.  
  
> [!NOTE]
> Notez qu’il y a deux déclarations PInvoke pour SendMessage. Ceci est nécessaire parce `wParam` que l’on utilise le paramètre pour passer une ficelle et l’autre l’utilise pour passer un intégrer. Vous avez besoin d’une déclaration distincte pour chaque signature afin de garantir que les données sont correctement marshalées.  
  
 [!code-csharp[WPFHostingWin32Control#HostWindowClass](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/Page1.xaml.cs#hostwindowclass)]
 [!code-vb[WPFHostingWin32Control#HostWindowClass](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/Page1.xaml.vb#hostwindowclass)]  
  
 [!code-csharp[WPFHostingWin32Control#ControlMsgFilterSendMessage](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/Page1.xaml.cs#controlmsgfiltersendmessage)]
 [!code-vb[WPFHostingWin32Control#ControlMsgFilterSendMessage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/Page1.xaml.vb#controlmsgfiltersendmessage)]  
  
<a name="communication"></a>
## <a name="implement-communication-between-the-control-and-the-page"></a>Implémenter une communication entre le contrôle et la page  
 Vous manipulez le contrôle en lui envoyant des messages Windows. Le contrôle vous notifie quand l’utilisateur interagit avec lui en envoyant des notifications à sa fenêtre hôte. [L’hébergement d’un contrôle Win32 ListBox dans l’échantillon WPF](https://github.com/Microsoft/WPF-Samples/tree/master/Migration%20and%20Interoperability/WPFHostingWin32Control) comprend une interface utilisateur qui fournit plusieurs exemples de la façon dont cela fonctionne:  
  
- Ajouter un élément à la liste.  
  
- Supprimez l'élément sélectionné de la liste.  
  
- Afficher le texte de l'élément actuellement sélectionné.  
  
- Afficher le nombre d’éléments de la liste.  
  
 L’utilisateur peut également sélectionner un élément dans la boîte de liste en cliquant dessus, tout comme il le ferait pour une application Win32 classique. Les données affichées sont mises à jour chaque fois que l’utilisateur change l’état de la zone de liste en sélectionnant ou ajoutant un élément.  
  
 Pour ajouter des éléments, envoyez [ `LB_ADDSTRING` ](/windows/desktop/Controls/lb-addstring)à la boîte de liste un message . Pour supprimer les [`LB_GETCURSEL`](/windows/desktop/Controls/lb-getcursel) éléments, envoyez-le pour [`LB_DELETESTRING`](/windows/desktop/Controls/lb-deletestring) obtenir l’index de la sélection actuelle, puis supprimer l’élément. L’échantillon [`LB_GETCOUNT`](/windows/desktop/Controls/lb-getcount)envoie également , et utilise la valeur retournée pour mettre à jour l’affichage qui montre le nombre d’éléments. Ces deux [`SendMessage`](/windows/desktop/api/winuser/nf-winuser-sendmessage) cas d’utilisation l’une des déclarations PInvoke discutées dans la section précédente.  
  
 [!code-csharp[WPFHostingWin32Control#AppendDeleteText](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/Page1.xaml.cs#appenddeletetext)]
 [!code-vb[WPFHostingWin32Control#AppendDeleteText](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/Page1.xaml.vb#appenddeletetext)]  
  
 Lorsque l’utilisateur sélectionne un élément ou modifie sa sélection, le contrôle avertit la <xref:System.Windows.Interop.HwndHost.MessageHook> fenêtre d’hôte en lui envoyant un [ `WM_COMMAND` message,](/windows/desktop/menurc/wm-command)ce qui soulève l’événement pour la page. Le gestionnaire reçoit les mêmes informations que la procédure de fenêtre principale de la fenêtre hôte. Il passe également une référence à `handled`une valeur Boolean, . Vous `handled` définissez pour `true` indiquer que vous avez traité le message et qu’aucun autre traitement n’est nécessaire.  
  
 [`WM_COMMAND`](/windows/desktop/menurc/wm-command)est envoyé pour une variété de raisons, de sorte que vous devez examiner l’ID de notification pour déterminer si c’est un événement que vous souhaitez gérer. L’ID est contenu dans `wParam` le mot élevé du paramètre. L’échantillon utilise des opérateurs bitwise pour extraire l’ID. Si l’utilisateur a fait ou changé [`LBN_SELCHANGE`](/windows/desktop/Controls/lbn-selchange)sa sélection, l’ID sera .  
  
 Lorsqu’il [`LBN_SELCHANGE`](/windows/desktop/Controls/lbn-selchange) est reçu, l’échantillon obtient l’index [ `LB_GETCURSEL` ](/windows/desktop/Controls/lb-getcursel)de l’élément sélectionné en envoyant le contrôle d’un message . Pour obtenir le texte, <xref:System.Text.StringBuilder>vous créez d’abord un . Vous envoyez ensuite [ `LB_GETTEXT` ](/windows/desktop/Controls/lb-gettext)au contrôle un message . Passer l’objet <xref:System.Text.StringBuilder> vide `wParam` comme paramètre. Lors [`SendMessage`](/windows/desktop/api/winuser/nf-winuser-sendmessage) de <xref:System.Text.StringBuilder> la déclaration, le contiendra le texte de l’élément sélectionné. Cette utilisation [`SendMessage`](/windows/desktop/api/winuser/nf-winuser-sendmessage) de nécessite encore une autre déclaration PInvoke.  
  
 Enfin, `handled` définissez pour `true` indiquer que le message a été manipulé.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Interop.HwndHost>
- [Interopérabilité WPF et Win32](wpf-and-win32-interoperation.md)
- [Procédure pas à pas : ma première application de bureau WPF](../getting-started/walkthrough-my-first-wpf-desktop-application.md)
