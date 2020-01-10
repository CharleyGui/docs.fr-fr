---
title: "Didacticiel : hébergement d'objets visuels dans une application Win32"
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- visual objects in Win32 code [WPF]
- Win32 code [WPF], visual objects in
- hosting [WPF], visual objects in Win32 code
ms.assetid: f0e1600c-3217-43d5-875d-1864fa7fe628
ms.openlocfilehash: 621684e14f9d1b599c4ef60e3731f0f58f31aacd
ms.sourcegitcommit: 9a97c76e141333394676bc5d264c6624b6f45bcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2020
ms.locfileid: "75740163"
---
# <a name="tutorial-hosting-visual-objects-in-a-win32-application"></a>Didacticiel : hébergement d'objets visuels dans une application Win32
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] propose un environnement de création d'applications élaboré. Toutefois, lorsque vous avez un investissement important dans du code Win32, il peut être plus efficace d’ajouter des fonctionnalités de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] à votre application plutôt que de réécrire votre code. Pour assurer la prise en charge des sous-systèmes Win32 et [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Graphics utilisés simultanément dans une application, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] fournit un mécanisme permettant d’héberger des objets dans une fenêtre Win32.  
  
 Ce didacticiel explique comment écrire un exemple d’application, un [test de positionnement avec l’exemple d’interopérabilité Win32](https://go.microsoft.com/fwlink/?LinkID=159995), qui héberge [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] objets visuels dans une fenêtre Win32.  

<a name="requirements"></a>   
## <a name="requirements"></a>Configuration requise pour  
 Ce didacticiel suppose une connaissance de base des [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] et de la programmation Win32. Pour une introduction à la programmation [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] de base, consultez [procédure pas à pas : ma première application de bureau WPF](../getting-started/walkthrough-my-first-wpf-desktop-application.md). Pour une introduction à la programmation Win32, consultez l’un des nombreux ouvrages sur le sujet, en particulier *Programming Windows* de Charles Petzold.  
  
> [!NOTE]
> Ce didacticiel comprend plusieurs exemples de code tirés de l'exemple associé. Cependant, pour une meilleure lecture, il n'inclut pas la totalité de l'exemple de code. Pour obtenir l’exemple de code complet, consultez [test de positionnement avec l’exemple d’interopérabilité Win32](https://go.microsoft.com/fwlink/?LinkID=159995).  
  
<a name="creating_the_host_win32_window"></a>   
## <a name="creating-the-host-win32-window"></a>Création de la fenêtre Win32 hôte  
 La classe <xref:System.Windows.Interop.HwndSource> est la clé de l’hébergement des objets [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] dans une fenêtre Win32. Cette classe encapsule les objets [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] dans une fenêtre Win32, ce qui leur permet d’être incorporés dans votre [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] en tant que fenêtre enfant.  
  
 L’exemple suivant montre le code permettant de créer l’objet <xref:System.Windows.Interop.HwndSource> en tant que fenêtre de conteneur Win32 pour les objets visuels. Pour définir le style de la fenêtre, la position et d’autres paramètres pour la fenêtre Win32, utilisez l’objet <xref:System.Windows.Interop.HwndSourceParameters>.  
  
 [!code-csharp[VisualsHitTesting#101](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsHitTesting/CSharp/MyWindow.cs#101)]
 [!code-vb[VisualsHitTesting#101](~/samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsHitTesting/VisualBasic/MyWindow.vb#101)]  
  
> [!NOTE]
> La valeur de la propriété <xref:System.Windows.Interop.HwndSourceParameters.ExtendedWindowStyle%2A> ne peut pas être définie sur WS_EX_TRANSPARENT. Cela signifie que la fenêtre Win32 hôte ne peut pas être transparente. Pour cette raison, la couleur d’arrière-plan de la fenêtre hôte Win32 est définie sur la même couleur d’arrière-plan que sa fenêtre parente.  
  
<a name="adding_visual_objects_to_the_host_win32_window"></a>   
## <a name="adding-visual-objects-to-the-host-win32-window"></a>Ajout d’objets visuels à la fenêtre Win32 hôte  
 Une fois que vous avez créé une fenêtre de conteneur Win32 hôte pour les objets visuels, vous pouvez y ajouter des objets visuels. Vous souhaitez vous assurer que les transformations des objets visuels, telles que les animations, ne s’étendent pas au-delà des limites du rectangle englobant de la fenêtre Win32 hôte.  
  
 L’exemple suivant montre le code permettant de créer l’objet <xref:System.Windows.Interop.HwndSource> et d’y ajouter des objets visuels.  
  
> [!NOTE]
> La propriété <xref:System.Windows.Interop.HwndSource.RootVisual%2A> de l’objet <xref:System.Windows.Interop.HwndSource> est définie sur le premier objet visuel ajouté à la fenêtre hôte Win32. L’objet visuel racine définit le nœud supérieur de l’arborescence des objets visuels. Tous les objets visuels suivants ajoutés à la fenêtre hôte Win32 sont ajoutés en tant qu’objets enfants.  
  
 [!code-csharp[VisualsHitTesting#100](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsHitTesting/CSharp/MyWindow.cs#100)]
 [!code-vb[VisualsHitTesting#100](~/samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsHitTesting/VisualBasic/MyWindow.vb#100)]  
  
<a name="implementing_the_win32_message_filter"></a>   
## <a name="implementing-the-win32-message-filter"></a>Implémentation du filtre de messages Win32  
 La fenêtre Win32 hôte pour les objets visuels nécessite une procédure de filtre de messages de fenêtre pour gérer les messages envoyés à la fenêtre à partir de la file d’attente de l’application. La procédure de fenêtre reçoit des messages du système Win32. Ces messages peuvent être des messages de gestion de fenêtre ou des messages de saisie. Vous pouvez choisir de gérer un message dans votre procédure de fenêtre ou de transférer le message au système de traitement par défaut.  
  
 L’objet <xref:System.Windows.Interop.HwndSource> que vous avez défini comme parent des objets visuels doit faire référence à la procédure de filtre de messages de fenêtre que vous fournissez. Lorsque vous créez l’objet <xref:System.Windows.Interop.HwndSource>, définissez la propriété <xref:System.Windows.Interop.HwndSourceParameters.HwndSourceHook%2A> pour qu’elle fasse référence à la procédure de fenêtre.  
  
 [!code-csharp[VisualsHitTesting#102](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsHitTesting/CSharp/MyWindow.cs#102)]
 [!code-vb[VisualsHitTesting#102](~/samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsHitTesting/VisualBasic/MyWindow.vb#102)]  
  
 L’exemple suivant montre le code permettant de gérer les messages lorsque les boutons gauche et droit de la souris sont relâchés. La valeur de coordonnée de la position de la souris est contenue dans la valeur du paramètre `lParam`.  
  
 [!code-csharp[VisualsHitTesting#103](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsHitTesting/CSharp/MyWindow.cs#103)]
 [!code-vb[VisualsHitTesting#103](~/samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsHitTesting/VisualBasic/MyWindow.vb#103)]  
  
<a name="processing_the_win32_messages"></a>   
## <a name="processing-the-win32-messages"></a>Traitement des messages Win32  
 Le code de l’exemple suivant montre comment un test de positionnement est effectué par rapport à la hiérarchie des objets visuels contenus dans la fenêtre hôte Win32. Vous pouvez déterminer si un point se trouve dans la géométrie d’un objet visuel, en utilisant la méthode <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> pour spécifier l’objet visuel racine et la valeur de coordonnée sur laquelle effectuer le test de positionnement. Dans ce cas, l’objet visuel racine est la valeur de la propriété <xref:System.Windows.Interop.HwndSource.RootVisual%2A> de l’objet <xref:System.Windows.Interop.HwndSource>.  
  
 [!code-csharp[VisualsHitTesting#104](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsHitTesting/CSharp/MyCircle.cs#104)]
 [!code-vb[VisualsHitTesting#104](~/samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsHitTesting/VisualBasic/MyCircle.vb#104)]  
  
 Pour plus d’informations sur le test de positionnement sur des objets visuels, consultez [test de positionnement dans la couche visuelle](hit-testing-in-the-visual-layer.md).  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Interop.HwndSource>
- [Exemple d’interopérabilité de test de positionnement avec Win32](https://go.microsoft.com/fwlink/?LinkID=159995)
- [Test de positionnement dans la couche visuelle](hit-testing-in-the-visual-layer.md)
