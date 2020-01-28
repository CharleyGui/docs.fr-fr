---
title: Partage de boucles de messages entre Win32 et WPF
titleSuffix: ''
ms.date: 03/30/2017
helpviewer_keywords:
- Win32 code [WPF], sharing message loops
- message loops [WPF]
- sharing message loops [WPF]
- interoperability [WPF], Win32
ms.assetid: 39ee888c-e5ec-41c8-b11f-7b851a554442
ms.openlocfilehash: e1b96284d69645876d3e383beb03a2cc540d8b7b
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76731710"
---
# <a name="sharing-message-loops-between-win32-and-wpf"></a>Partage de boucles de messages entre Win32 et WPF
Cette rubrique explique comment implémenter une boucle de messages pour l’interopérabilité avec [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)], en utilisant l’exposition de la boucle de message existante dans <xref:System.Windows.Threading.Dispatcher> ou en créant une boucle de messages distincte sur le côté Win32 de votre code d’interopérabilité.  
  
## <a name="componentdispatcher-and-the-message-loop"></a>ComponentDispatcher et la boucle de message  
 Un scénario normal pour l’interopérabilité et la prise en charge des événements de clavier consiste à implémenter <xref:System.Windows.Interop.IKeyboardInputSink>ou à sous-classe à partir de classes qui implémentent déjà <xref:System.Windows.Interop.IKeyboardInputSink>, comme <xref:System.Windows.Interop.HwndSource> ou <xref:System.Windows.Interop.HwndHost>. Toutefois, la prise en charge du récepteur de clavier ne répond pas à tous les besoins de boucle de message possibles lors de l’envoi et de la réception de messages entre les limites d’interopérabilité. Pour faciliter la formalisation d’une architecture de boucle de messages d’application, [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] fournit la classe <xref:System.Windows.Interop.ComponentDispatcher>, qui définit un protocole simple à suivre pour une boucle de message.  
  
 <xref:System.Windows.Interop.ComponentDispatcher> est une classe statique qui expose plusieurs membres. La portée de chaque méthode est implicitement liée au thread appelant. Une boucle de messages doit appeler certaines de ces API à des moments critiques (comme défini dans la section suivante).  
  
 <xref:System.Windows.Interop.ComponentDispatcher> fournit des événements que d’autres composants (tels que le récepteur de clavier) peuvent écouter. La classe <xref:System.Windows.Threading.Dispatcher> appelle toutes les méthodes de <xref:System.Windows.Interop.ComponentDispatcher> appropriées dans une séquence appropriée. Si vous implémentez votre propre boucle de message, votre code est chargé d’appeler les méthodes <xref:System.Windows.Interop.ComponentDispatcher> de la même manière.  
  
 L’appel de méthodes <xref:System.Windows.Interop.ComponentDispatcher> sur un thread appellera uniquement les gestionnaires d’événements inscrits sur ce thread.  
  
## <a name="writing-message-loops"></a>Écriture de boucles de messages  
 Voici une liste de contrôle des membres de <xref:System.Windows.Interop.ComponentDispatcher> que vous allez utiliser si vous écrivez votre propre boucle de message :  
  
- <xref:System.Windows.Interop.ComponentDispatcher.PushModal%2A>: votre boucle de messages doit appeler This pour indiquer que le thread est modal.  
  
- <xref:System.Windows.Interop.ComponentDispatcher.PopModal%2A>: votre boucle de messages doit appeler This pour indiquer que le thread est rétabli en mode inmodal.  
  
- <xref:System.Windows.Interop.ComponentDispatcher.RaiseIdle%2A>: votre boucle de messages doit appeler This pour indiquer que <xref:System.Windows.Interop.ComponentDispatcher> doit déclencher l’événement <xref:System.Windows.Interop.ComponentDispatcher.ThreadIdle>. <xref:System.Windows.Interop.ComponentDispatcher> ne déclenchera pas <xref:System.Windows.Interop.ComponentDispatcher.ThreadIdle> si <xref:System.Windows.Interop.ComponentDispatcher.IsThreadModal%2A> est `true`, mais les boucles de messages peuvent choisir d’appeler <xref:System.Windows.Interop.ComponentDispatcher.RaiseIdle%2A> même si <xref:System.Windows.Interop.ComponentDispatcher> ne peut pas y répondre dans un État modal.  
  
- <xref:System.Windows.Interop.ComponentDispatcher.RaiseThreadMessage%2A>: votre boucle de messages doit l’appeler pour indiquer qu’un nouveau message est disponible. La valeur de retour indique si un écouteur d’un événement <xref:System.Windows.Interop.ComponentDispatcher> a géré le message. Si <xref:System.Windows.Interop.ComponentDispatcher.RaiseThreadMessage%2A> retourne `true` (géré), le répartiteur ne doit rien faire d’autre avec le message. Si la valeur de retour est `false`, le répartiteur est supposé appeler la fonction Win32 `TranslateMessage`, puis appeler `DispatchMessage`.  
  
## <a name="using-componentdispatcher-and-existing-message-handling"></a>Utilisation de ComponentDispatcher et gestion des messages existants  
 Voici une liste de contrôle des membres de <xref:System.Windows.Interop.ComponentDispatcher> que vous allez utiliser si vous vous fiez à la boucle de message [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] inhérente.  
  
- <xref:System.Windows.Interop.ComponentDispatcher.IsThreadModal%2A>: retourne une valeur indiquant si l’application est devenue modale (par exemple, une boucle de messages modale a fait l’objet d’un push). <xref:System.Windows.Interop.ComponentDispatcher> pouvez suivre cet État, car la classe maintient un nombre d’appels de <xref:System.Windows.Interop.ComponentDispatcher.PushModal%2A> et de <xref:System.Windows.Interop.ComponentDispatcher.PopModal%2A> à partir de la boucle de message.  
  
- les événements <xref:System.Windows.Interop.ComponentDispatcher.ThreadFilterMessage> et <xref:System.Windows.Interop.ComponentDispatcher.ThreadPreprocessMessage> suivent les règles standard pour les appels de délégué. Les délégués sont appelés dans un ordre non spécifié, et tous les délégués sont appelés même si le premier marque le message comme étant géré.  
  
- <xref:System.Windows.Interop.ComponentDispatcher.ThreadIdle>: indique une durée appropriée et efficace pour le traitement inactif (il n’y a pas d’autres messages en attente pour le thread). <xref:System.Windows.Interop.ComponentDispatcher.ThreadIdle> n’est pas déclenché si le thread est modal.  
  
- <xref:System.Windows.Interop.ComponentDispatcher.ThreadFilterMessage>: déclenché pour tous les messages traités par la pompe de messages.  
  
- <xref:System.Windows.Interop.ComponentDispatcher.ThreadPreprocessMessage>: déclenché pour tous les messages qui n’ont pas été gérés pendant la <xref:System.Windows.Interop.ComponentDispatcher.ThreadFilterMessage>.  
  
 Un message est considéré comme géré si, après l’événement <xref:System.Windows.Interop.ComponentDispatcher.ThreadFilterMessage> ou <xref:System.Windows.Interop.ComponentDispatcher.ThreadPreprocessMessage> événement, le paramètre `handled` passé par référence dans les données d’événement est `true`. Les gestionnaires d’événements doivent ignorer le message si `handled` est `true`, car cela signifie que le gestionnaire différent gérait d’abord le message. Les gestionnaires d’événements pour les deux événements peuvent modifier le message. Le répartiteur doit distribuer le message modifié et non le message non modifié d’origine. <xref:System.Windows.Interop.ComponentDispatcher.ThreadPreprocessMessage> est remis à tous les écouteurs, mais l’objectif architectural est que seule la fenêtre de niveau supérieur contenant le HWND à partir duquel les messages ciblés doivent appeler du code en réponse au message.  
  
## <a name="how-hwndsource-treats-componentdispatcher-events"></a>Comment HwndSource traite les événements ComponentDispatcher  
 Si la <xref:System.Windows.Interop.HwndSource> est une fenêtre de niveau supérieur (sans HWND parent), elle s’inscrit avec <xref:System.Windows.Interop.ComponentDispatcher>. Si <xref:System.Windows.Interop.ComponentDispatcher.ThreadPreprocessMessage> est déclenchée et si le message est destiné aux fenêtres <xref:System.Windows.Interop.HwndSource> ou enfants, <xref:System.Windows.Interop.HwndSource> appelle son <xref:System.Windows.Interop.HwndSource.System%23Windows%23Interop%23IKeyboardInputSink%23TranslateAccelerator%2A>, <xref:System.Windows.Interop.IKeyboardInputSink.TranslateChar%2A>, <xref:System.Windows.Interop.IKeyboardInputSink.OnMnemonic%2A> séquence du récepteur du clavier.  
  
 Si la <xref:System.Windows.Interop.HwndSource> n’est pas une fenêtre de niveau supérieur (a un HWND parent), il n’y aura aucune gestion. Seule la fenêtre de niveau supérieur est supposée effectuer la gestion, et il est supposé qu’il s’agit d’une fenêtre de niveau supérieur avec prise en charge du récepteur de clavier dans le cadre d’un scénario d’interopérabilité.  
  
 Si <xref:System.Windows.Interop.HwndHost.WndProc%2A> sur un <xref:System.Windows.Interop.HwndSource> est appelé sans qu’une méthode de récepteur de clavier appropriée ne soit appelée en premier, votre application recevra les événements de clavier de niveau supérieur tels que <xref:System.Windows.UIElement.KeyDown>. Toutefois, aucune méthode de récepteur de clavier n’est appelée, ce qui contourne les fonctionnalités de modèle d’entrée de clavier souhaitables, telles que la prise en charge des clés d’accès. Cela peut se produire si la boucle de message n’a pas correctement notifié le thread pertinent sur le <xref:System.Windows.Interop.ComponentDispatcher>ou parce que le HWND parent n’a pas appelé les réponses appropriées du récepteur de clavier.  
  
 Un message qui accède au récepteur de clavier ne peut pas être envoyé au HWND si vous avez ajouté des hooks pour ce message à l’aide de la méthode <xref:System.Windows.Interop.HwndSource.AddHook%2A>. Le message a peut-être été traité directement au niveau de la pompe de messages et n’est pas soumis à la fonction `DispatchMessage`.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Interop.ComponentDispatcher>
- <xref:System.Windows.Interop.IKeyboardInputSink>
- [Interopérabilité WPF et Win32](wpf-and-win32-interoperation.md)
- [Modèle de thread](threading-model.md)
- [Vue d’ensemble des entrées](input-overview.md)
