---
title: Architecture d’entrée Windows Forms et WPF Interop
titleSuffix: ''
ms.date: 03/30/2017
helpviewer_keywords:
- input architecture [WPF interoperability]
- messages [WPF]
- Windows Forms [WPF], interoperability with
- Windows Forms [WPF], WPF interoperation
- interoperability [WPF], Windows Forms
- modeless forms [WPF]
- ElementHost keyboard and messages [WPF]
- keyboard interoperation [WPF]
- WindowsFormsHost keyboard and messages [WPF]
- modeless dialog boxes [WPF]
ms.assetid: 0eb6f137-f088-4c5e-9e37-f96afd28f235
ms.openlocfilehash: 1c7027947d24c847ee298022344e02ce0bbff764
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76794091"
---
# <a name="windows-forms-and-wpf-interoperability-input-architecture"></a>Architecture d'entrée pour l'interopérabilité entre Windows Forms et WPF
L’interopérabilité entre les [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] et Windows Forms requiert que les deux technologies aient le traitement d’entrée de clavier approprié. Cette rubrique décrit comment ces technologies implémentent le traitement du clavier et des messages pour permettre une interopérabilité fluide dans des applications hybrides.  
  
 Cette rubrique contient les sous-sections suivantes :  
  
- Formulaires et boîtes de dialogue non modals  
  
- Clavier WindowsFormsHost et traitement des messages  
  
- Clavier ElementHost et traitement des messages  
  
## <a name="modeless-forms-and-dialog-boxes"></a>Formulaires et boîtes de dialogue non modals  
 Appelez la méthode <xref:System.Windows.Forms.Integration.WindowsFormsHost.EnableWindowsFormsInterop%2A> sur l’élément <xref:System.Windows.Forms.Integration.WindowsFormsHost> pour ouvrir un formulaire ou une boîte de dialogue non modale à partir d’une application basée sur [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
 Appelez la méthode <xref:System.Windows.Forms.Integration.ElementHost.EnableModelessKeyboardInterop%2A> sur le contrôle <xref:System.Windows.Forms.Integration.ElementHost> pour ouvrir une page [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] non modale dans une application basée sur des Windows Forms.  
  
## <a name="windowsformshost-keyboard-and-message-processing"></a>Clavier WindowsFormsHost et traitement des messages  
 Lorsqu’elle est hébergée par une application basée sur [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], Windows Forms le traitement du clavier et des messages se compose des éléments suivants :  
  
- La classe <xref:System.Windows.Forms.Integration.WindowsFormsHost> acquiert des messages à partir de la boucle de message [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], qui est implémentée par la classe <xref:System.Windows.Interop.ComponentDispatcher>.  
  
- La classe <xref:System.Windows.Forms.Integration.WindowsFormsHost> crée une boucle de messages Windows Forms de substitution pour s’assurer que le traitement du clavier de Windows Forms ordinaire se produit.  
  
- La classe <xref:System.Windows.Forms.Integration.WindowsFormsHost> implémente l’interface <xref:System.Windows.Interop.IKeyboardInputSink> pour coordonner la gestion du focus avec [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
- Les contrôles <xref:System.Windows.Forms.Integration.WindowsFormsHost> s’inscrivent et démarrent leurs boucles de messages.  
  
 Les sections suivantes décrivent ces parties du processus plus en détail.  
  
### <a name="acquiring-messages-from-the-wpf-message-loop"></a>Acquisition de messages à partir de la boucle de message WPF  
 La classe <xref:System.Windows.Interop.ComponentDispatcher> implémente le gestionnaire de boucles de messages pour [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. La classe <xref:System.Windows.Interop.ComponentDispatcher> fournit des hooks pour permettre aux clients externes de filtrer des messages avant que [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] les traite.  
  
 L’implémentation de l’interopérabilité gère l’événement <xref:System.Windows.Interop.ComponentDispatcher.ThreadFilterMessage?displayProperty=nameWithType>, qui permet aux contrôles Windows Forms de traiter les messages avant les contrôles [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
### <a name="surrogate-windows-forms-message-loop"></a>Boucle de messages de Windows Forms de substitution  
 Par défaut, la classe <xref:System.Windows.Forms.Application?displayProperty=nameWithType> contient la boucle de messages principale pour les applications Windows Forms. Pendant l’interopérabilité, la boucle de message Windows Forms ne traite pas les messages. Par conséquent, cette logique doit être reproduite. Le gestionnaire de l’événement <xref:System.Windows.Interop.ComponentDispatcher.ThreadFilterMessage?displayProperty=nameWithType> effectue les étapes suivantes :  
  
1. Filtre le message à l’aide de l’interface <xref:System.Windows.Forms.IMessageFilter>.  
  
2. Appelle la méthode <xref:System.Windows.Forms.Control.PreProcessMessage%2A?displayProperty=nameWithType>.  
  
3. Traduit et distribue le message, si nécessaire.  
  
4. Transmet le message au contrôle d’hébergement, si aucun autre contrôle ne traite le message.  
  
### <a name="ikeyboardinputsink-implementation"></a>Implémentation de IKeyboardInputSink  
 La boucle de message de substitution gère la gestion du clavier. Par conséquent, la méthode <xref:System.Windows.Interop.IKeyboardInputSink.TabInto%2A?displayProperty=nameWithType> est la seule <xref:System.Windows.Interop.IKeyboardInputSink> membre qui requiert une implémentation dans la classe <xref:System.Windows.Forms.Integration.WindowsFormsHost>.  
  
 Par défaut, la classe <xref:System.Windows.Interop.HwndHost> retourne `false` pour son implémentation <xref:System.Windows.Interop.HwndHost.System%23Windows%23Interop%23IKeyboardInputSink%23TabInto%2A>. Cela empêche la tabulation d’un contrôle de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] à un contrôle de Windows Forms.  
  
 L’implémentation <xref:System.Windows.Forms.Integration.WindowsFormsHost> de la méthode <xref:System.Windows.Interop.IKeyboardInputSink.TabInto%2A?displayProperty=nameWithType> effectue les étapes suivantes :  
  
1. Recherche le premier ou le dernier contrôle de Windows Forms contenu dans le contrôle <xref:System.Windows.Forms.Integration.WindowsFormsHost> et qui peut recevoir le focus. Le choix du contrôle dépend des informations de parcours.  
  
2. Définit le focus sur le contrôle et retourne `true`.  
  
3. Si aucun contrôle ne peut recevoir le focus, retourne `false`.  
  
### <a name="windowsformshost-registration"></a>Inscription WindowsFormsHost  
 Quand le handle de fenêtre d’un contrôle de <xref:System.Windows.Forms.Integration.WindowsFormsHost> est créé, le contrôle <xref:System.Windows.Forms.Integration.WindowsFormsHost> appelle une méthode statique interne qui enregistre sa présence pour la boucle de message.  
  
 Pendant l’inscription, le contrôle <xref:System.Windows.Forms.Integration.WindowsFormsHost> examine la boucle de message. Si la boucle de message n’a pas été démarrée, le gestionnaire d’événements <xref:System.Windows.Interop.ComponentDispatcher.ThreadFilterMessage?displayProperty=nameWithType> est créé. La boucle de message est considérée comme étant en cours d’exécution lorsque le gestionnaire d’événements <xref:System.Windows.Interop.ComponentDispatcher.ThreadFilterMessage?displayProperty=nameWithType> est attaché.  
  
 Quand le handle de fenêtre est détruit, le contrôle <xref:System.Windows.Forms.Integration.WindowsFormsHost> se supprime lui-même de l’inscription.  
  
## <a name="elementhost-keyboard-and-message-processing"></a>Clavier ElementHost et traitement des messages  
 Lorsqu’ils sont hébergés par une application Windows Forms, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] le traitement du clavier et des messages se compose des éléments suivants :  
  
- implémentations d’interface <xref:System.Windows.Interop.HwndSource>, <xref:System.Windows.Interop.IKeyboardInputSink>et <xref:System.Windows.Interop.IKeyboardInputSite>.  
  
- Touches de tabulation et de direction.  
  
- Clés de commande et clés de boîte de dialogue.  
  
- Windows Forms le traitement des accélérateurs.  
  
 Les sections suivantes décrivent ces parties plus en détail.  
  
### <a name="interface-implementations"></a>Implémentations d’interface  
 Dans Windows Forms, les messages de clavier sont acheminés vers le handle de fenêtre du contrôle qui a le focus. Dans le contrôle <xref:System.Windows.Forms.Integration.ElementHost>, ces messages sont routés vers l’élément hébergé. Pour ce faire, le contrôle <xref:System.Windows.Forms.Integration.ElementHost> fournit une instance <xref:System.Windows.Interop.HwndSource>. Si le contrôle de <xref:System.Windows.Forms.Integration.ElementHost> a le focus, l’instance de <xref:System.Windows.Interop.HwndSource> route la plupart des entrées au clavier afin qu’elles puissent être traitées par la classe <xref:System.Windows.Input.InputManager> [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
 La classe <xref:System.Windows.Interop.HwndSource> implémente les interfaces <xref:System.Windows.Interop.IKeyboardInputSink> et <xref:System.Windows.Interop.IKeyboardInputSite>.  
  
 L’interopérabilité du clavier repose sur l’implémentation de la méthode <xref:System.Windows.Interop.IKeyboardInputSite.OnNoMoreTabStops%2A> pour gérer l’entrée de la touche TAB et de la touche de direction qui déplace le focus hors des éléments hébergés.  
  
### <a name="tabbing-and-arrow-keys"></a>Touches de tabulation et de direction  
 La logique de sélection de Windows Forms est mappée aux méthodes de <xref:System.Windows.Interop.HwndSource.System%23Windows%23Interop%23IKeyboardInputSink%23TabInto%2A> et de <xref:System.Windows.Interop.IKeyboardInputSite.OnNoMoreTabStops%2A> pour implémenter la navigation par TABULATIONs et les touches de direction. La substitution de la méthode <xref:System.Windows.Forms.Integration.ElementHost.Select%2A> effectue ce mappage.  
  
### <a name="command-keys-and-dialog-box-keys"></a>Clés de commande et clés de boîte de dialogue  
 Pour permettre à [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] la première possibilité de traiter les touches de commande et les touches de boîte de dialogue, Windows Forms le prétraitement des commandes est connecté à la méthode <xref:System.Windows.Interop.IKeyboardInputSink.TranslateAccelerator%2A>. La substitution de la méthode <xref:System.Windows.Forms.Control.ProcessCmdKey%2A?displayProperty=nameWithType> connecte les deux technologies.  
  
 Avec la méthode <xref:System.Windows.Interop.IKeyboardInputSink.TranslateAccelerator%2A>, les éléments hébergés peuvent gérer n’importe quel message de touche, comme WM_KEYDOWN, WM_KEYUP, WM_SYSKEYDOWN ou WM_SYSKEYUP, y compris les touches de commande, telles que TAB, entrée, ÉCHAP et les touches de direction. Si un message de clé n’est pas géré, il est envoyé vers le haut de la hiérarchie d’ancêtre Windows Forms pour la gestion.  
  
### <a name="accelerator-processing"></a>Traitement des accélérateurs  
 Pour traiter correctement les accélérateurs, Windows Forms traitement des accélérateurs doit être connecté à la classe <xref:System.Windows.Input.AccessKeyManager> [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. En outre, tous les messages WM_CHAR doivent être routés correctement vers les éléments hébergés.  
  
 Étant donné que l’implémentation par défaut <xref:System.Windows.Interop.HwndSource> de la méthode <xref:System.Windows.Interop.IKeyboardInputSink.TranslateChar%2A> retourne `false`, les messages WM_CHAR sont traités à l’aide de la logique suivante :  
  
- La méthode <xref:System.Windows.Forms.Control.IsInputChar%2A?displayProperty=nameWithType> est substituée pour garantir que tous les messages WM_CHAR sont transférés aux éléments hébergés.  
  
- Si la touche ALT est enfoncée, le message est WM_SYSCHAR. Windows Forms ne prétraite pas ce message via la méthode <xref:System.Windows.Forms.Control.IsInputChar%2A>. Par conséquent, la méthode <xref:System.Windows.Forms.Control.ProcessMnemonic%2A> est substituée pour interroger le <xref:System.Windows.Input.AccessKeyManager> [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] pour un accélérateur inscrit. Si un accélérateur inscrit est trouvé, <xref:System.Windows.Input.AccessKeyManager> le traite.  
  
- Si la touche ALT n’est pas enfoncée, la classe [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Input.InputManager> traite l’entrée non gérée. Si l’entrée est un accélérateur, le <xref:System.Windows.Input.AccessKeyManager> le traite. L’événement <xref:System.Windows.Input.InputManager.PostProcessInput> est géré pour les messages WM_CHAR qui n’ont pas été traités.  
  
 Quand l’utilisateur appuie sur la touche ALT, les signaux visuels des accélérateurs s’affichent sur l’ensemble du formulaire. Pour prendre en charge ce comportement, tous les contrôles <xref:System.Windows.Forms.Integration.ElementHost> du formulaire actif reçoivent des messages WM_SYSKEYDOWN, quel que soit le contrôle ayant le focus.  
  
 Les messages sont envoyés uniquement aux contrôles de <xref:System.Windows.Forms.Integration.ElementHost> dans le formulaire actif.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.Integration.WindowsFormsHost.EnableWindowsFormsInterop%2A>
- <xref:System.Windows.Forms.Integration.ElementHost.EnableModelessKeyboardInterop%2A>
- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [Procédure pas à pas : hébergement d'un contrôle composite Windows Forms dans WPF](walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)
- [Procédure pas à pas : Hébergement d'un contrôle composite WPF dans Windows Forms](walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
- [Interopérabilité WPF et Win32](wpf-and-win32-interoperation.md)
