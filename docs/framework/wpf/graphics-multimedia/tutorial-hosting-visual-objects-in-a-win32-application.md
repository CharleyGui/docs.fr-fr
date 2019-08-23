---
title: 'Tutoriel : hébergement d’objets visuels dans une application Win32'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- visual objects in Win32 code [WPF]
- Win32 code [WPF], visual objects in
- hosting [WPF], visual objects in Win32 code
ms.assetid: f0e1600c-3217-43d5-875d-1864fa7fe628
ms.openlocfilehash: c8baefbf01467a65626a77f300f34a145d5c7281
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69962872"
---
# <a name="tutorial-hosting-visual-objects-in-a-win32-application"></a>Tutoriel : hébergement d’objets visuels dans une application Win32
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] propose un environnement de création d'applications élaboré. Toutefois, lorsque vous avez un investissement important dans [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] le code, il peut être plus efficace d' [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ajouter des fonctionnalités à votre application au lieu de réécrire votre code. Pour assurer la prise [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] en [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] charge des sous-systèmes et des sous-systèmes graphiques utilisés [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] simultanément dans une application, fournit un mécanisme [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] permettant d’héberger des objets dans une fenêtre.  
  
 Ce didacticiel explique comment écrire un exemple d’application, un [test de positionnement avec l’exemple](https://go.microsoft.com/fwlink/?LinkID=159995)d’interopérabilité [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Win32, qui héberge [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] des objets visuels dans une fenêtre.  

<a name="requirements"></a>   
## <a name="requirements"></a>Configuration requise  
 Ce didacticiel suppose que vous avez des connaissances de base en matière de programmation [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] et [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]. Pour une introduction à [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] la programmation de base, consultez [procédure pas à pas: Ma première application](../getting-started/walkthrough-my-first-wpf-desktop-application.md)de bureau WPF. Pour une présentation [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] de la programmation, consultez l’un des nombreux ouvrages sur le sujet, en particulier *Programming Windows* de Charles Petzold.  
  
> [!NOTE]
> Ce didacticiel comprend plusieurs exemples de code tirés de l'exemple associé. Cependant, pour une meilleure lecture, il n'inclut pas la totalité de l'exemple de code. Pour obtenir l’exemple de code complet, consultez [test de positionnement avec l’exemple d’interopérabilité Win32](https://go.microsoft.com/fwlink/?LinkID=159995).  
  
<a name="creating_the_host_win32_window"></a>   
## <a name="creating-the-host-win32-window"></a>Création de la fenêtre Win32 hôte  
 La clé pour héberger [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] des objets dans une [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] fenêtre <xref:System.Windows.Interop.HwndSource> est la classe. Cette classe encapsule les [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] objets dans une [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] fenêtre, ce qui leur permet d’être incorporés dans votre sous la [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] forme d’une fenêtre enfant.  
  
 L’exemple suivant montre le code permettant de créer <xref:System.Windows.Interop.HwndSource> l’objet [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] comme fenêtre de conteneur pour les objets visuels. Pour définir le style de la fenêtre, la position et d’autres [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] paramètres de la fenêtre <xref:System.Windows.Interop.HwndSourceParameters> , utilisez l’objet.  
  
 [!code-csharp[VisualsHitTesting#101](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsHitTesting/CSharp/MyWindow.cs#101)]
 [!code-vb[VisualsHitTesting#101](~/samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsHitTesting/VisualBasic/MyWindow.vb#101)]  
  
> [!NOTE]
> La valeur de la <xref:System.Windows.Interop.HwndSourceParameters.ExtendedWindowStyle%2A> propriété ne peut pas être définie sur WS_EX_TRANSPARENT. Cela signifie que la fenêtre [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] hôte ne peut pas être transparente. Pour cette raison, la couleur d’arrière-plan [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] de la fenêtre hôte est définie sur la même couleur d’arrière-plan que sa fenêtre parente.  
  
<a name="adding_visual_objects_to_the_host_win32_window"></a>   
## <a name="adding-visual-objects-to-the-host-win32-window"></a>Ajout d’objets visuels à la fenêtre Win32 hôte  
 Une fois que vous avez créé [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] une fenêtre de conteneur hôte pour les objets visuels, vous pouvez y ajouter des objets visuels. Vous souhaitez vous assurer que les transformations des objets visuels, telles que les animations, ne s’étendent pas au-delà des limites du [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] rectangle englobant de la fenêtre hôte.  
  
 L’exemple suivant montre le code permettant de créer <xref:System.Windows.Interop.HwndSource> l’objet et d’y ajouter des objets visuels.  
  
> [!NOTE]
> La <xref:System.Windows.Interop.HwndSource.RootVisual%2A> propriété de l' <xref:System.Windows.Interop.HwndSource> objet est définie sur le premier objet visuel ajouté à la fenêtre [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] hôte. L’objet visuel racine définit le nœud supérieur de l’arborescence des objets visuels. Tous les objets visuels suivants ajoutés à la [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] fenêtre hôte sont ajoutés en tant qu’objets enfants.  
  
 [!code-csharp[VisualsHitTesting#100](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsHitTesting/CSharp/MyWindow.cs#100)]
 [!code-vb[VisualsHitTesting#100](~/samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsHitTesting/VisualBasic/MyWindow.vb#100)]  
  
<a name="implementing_the_win32_message_filter"></a>   
## <a name="implementing-the-win32-message-filter"></a>Implémentation du filtre de messages Win32  
 La fenêtre [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] hôte pour les objets visuels nécessite une procédure de filtre de messages de fenêtre pour gérer les messages envoyés à la fenêtre à partir de la file d’attente de l’application. La procédure de fenêtre reçoit des messages [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] du système. Ces messages peuvent être des messages de gestion de fenêtre ou des messages de saisie. Vous pouvez choisir de gérer un message dans votre procédure de fenêtre ou de transférer le message au système de traitement par défaut.  
  
 L' <xref:System.Windows.Interop.HwndSource> objet que vous avez défini en tant que parent pour les objets visuels doit faire référence à la procédure de filtre de messages de fenêtre que vous fournissez. Lorsque vous créez l' <xref:System.Windows.Interop.HwndSource> objet, définissez la <xref:System.Windows.Interop.HwndSourceParameters.HwndSourceHook%2A> propriété pour qu’elle fasse référence à la procédure de fenêtre.  
  
 [!code-csharp[VisualsHitTesting#102](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsHitTesting/CSharp/MyWindow.cs#102)]
 [!code-vb[VisualsHitTesting#102](~/samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsHitTesting/VisualBasic/MyWindow.vb#102)]  
  
 L’exemple suivant montre le code permettant de gérer les messages lorsque les boutons gauche et droit de la souris sont relâchés. La valeur de coordonnée de la position de la souris est contenue `lParam` dans la valeur du paramètre.  
  
 [!code-csharp[VisualsHitTesting#103](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsHitTesting/CSharp/MyWindow.cs#103)]
 [!code-vb[VisualsHitTesting#103](~/samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsHitTesting/VisualBasic/MyWindow.vb#103)]  
  
<a name="processing_the_win32_messages"></a>   
## <a name="processing-the-win32-messages"></a>Traitement des messages Win32  
 Le code de l’exemple suivant montre comment un test de positionnement est effectué par rapport à la hiérarchie des objets visuels contenus [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] dans la fenêtre hôte. Vous pouvez déterminer si un point se trouve dans la géométrie d’un objet visuel, en utilisant <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> la méthode pour spécifier l’objet visuel racine et la valeur de coordonnée par rapport à laquelle effectuer le test de positionnement. Dans ce cas, l’objet visuel racine est la valeur de la <xref:System.Windows.Interop.HwndSource.RootVisual%2A> propriété de l' <xref:System.Windows.Interop.HwndSource> objet.  
  
 [!code-csharp[VisualsHitTesting#104](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsHitTesting/CSharp/MyCircle.cs#104)]
 [!code-vb[VisualsHitTesting#104](~/samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsHitTesting/VisualBasic/MyCircle.vb#104)]  
  
 Pour plus d’informations sur le test de positionnement sur des objets visuels, consultez [test de positionnement dans la couche visuelle](hit-testing-in-the-visual-layer.md).  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Interop.HwndSource>
- [Exemple d’interopérabilité de test de positionnement avec Win32](https://go.microsoft.com/fwlink/?LinkID=159995)
- [Test de positionnement dans la couche visuelle](hit-testing-in-the-visual-layer.md)
