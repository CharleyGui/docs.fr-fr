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
ms.openlocfilehash: d04357e0770bbf8eebe8f40a86a19ddc9baae3ab
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187428"
---
# <a name="tutorial-hosting-visual-objects-in-a-win32-application"></a>Didacticiel : hébergement d'objets visuels dans une application Win32
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] propose un environnement de création d'applications élaboré. Toutefois, lorsque vous avez un investissement substantiel dans le code [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Win32, il pourrait être plus efficace d’ajouter des fonctionnalités à votre application plutôt que de réécrire votre code. Pour prendre en charge [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Win32 et les sous-systèmes [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] graphiques utilisés simultanément dans une application, fournit un mécanisme pour héberger des objets dans une fenêtre Win32.  
  
 Ce tutoriel décrit comment écrire une application [d’échantillon, Hit Test avec Win32 Interoperation Sample](https://github.com/microsoft/WPF-Samples/tree/master/Visual%20Layer/VisualsHitTesting), qui héberge des [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] objets visuels dans une fenêtre Win32.  

<a name="requirements"></a>
## <a name="requirements"></a>Spécifications  
 Ce tutoriel suppose une familiarité [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] de base avec les deux et la programmation Win32. Pour une introduction [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] de base à la programmation, voir [Procédure pas à pas: Ma première application de bureau WPF](../getting-started/walkthrough-my-first-wpf-desktop-application.md). Pour une introduction à la programmation Win32, voir l’un des nombreux livres sur le sujet, en particulier *La programmation de Windows* par Charles Petzold.  
  
> [!NOTE]
> Ce didacticiel comprend plusieurs exemples de code tirés de l'exemple associé. Cependant, pour une meilleure lecture, il n'inclut pas la totalité de l'exemple de code. Pour le code complet de l’échantillon, voir [Hit Test avec Win32 Interoperation Sample](https://github.com/microsoft/WPF-Samples/tree/master/Visual%20Layer/VisualsHitTesting).  
  
<a name="creating_the_host_win32_window"></a>
## <a name="creating-the-host-win32-window"></a>Création de la fenêtre Win32 hôte  
 La clé [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] pour héberger des objets <xref:System.Windows.Interop.HwndSource> dans une fenêtre Win32 est la classe. Cette classe enveloppe [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] les objets dans une fenêtre Win32, [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] ce qui leur permet d’être incorporés dans votre fenêtre d’enfant.  
  
 L’exemple suivant montre le <xref:System.Windows.Interop.HwndSource> code pour créer l’objet comme la fenêtre de conteneur Win32 pour les objets visuels. Pour définir le style de fenêtre, la position et d’autres paramètres pour la fenêtre Win32, utilisez l’objet. <xref:System.Windows.Interop.HwndSourceParameters>  
  
 [!code-csharp[VisualsHitTesting#101](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsHitTesting/CSharp/MyWindow.cs#101)]
 [!code-vb[VisualsHitTesting#101](~/samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsHitTesting/VisualBasic/MyWindow.vb#101)]  
  
> [!NOTE]
> La valeur <xref:System.Windows.Interop.HwndSourceParameters.ExtendedWindowStyle%2A> de la propriété ne peut pas être réglée pour WS_EX_TRANSPARENT. Cela signifie que la fenêtre Win32 hôte ne peut pas être transparente. Pour cette raison, la couleur de fond de la fenêtre Win32 hôte est réglé à la même couleur de fond que sa fenêtre parente.  
  
<a name="adding_visual_objects_to_the_host_win32_window"></a>
## <a name="adding-visual-objects-to-the-host-win32-window"></a>Ajout d’objets visuels à la fenêtre Win32 hôte  
 Une fois que vous avez créé une fenêtre de conteneur Win32 hôte pour les objets visuels, vous pouvez y ajouter des objets visuels. Vous voudrez vous assurer que toute transformation des objets visuels, telles que les animations, ne s’étend pas au-delà des limites du rectangle de délimitation de la fenêtre Win32 hôte.  
  
 L’exemple suivant montre le <xref:System.Windows.Interop.HwndSource> code pour créer l’objet et y ajouter des objets visuels.  
  
> [!NOTE]
> La <xref:System.Windows.Interop.HwndSource.RootVisual%2A> propriété <xref:System.Windows.Interop.HwndSource> de l’objet est réglée sur le premier objet visuel ajouté à la fenêtre Win32 hôte. L’objet visuel racine définit le nœud supérieur de l’arborescence des objets visuels. Tous les objets visuels ultérieurs ajoutés à la fenêtre Win32 hôte sont ajoutés comme objets pour enfants.  
  
 [!code-csharp[VisualsHitTesting#100](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsHitTesting/CSharp/MyWindow.cs#100)]
 [!code-vb[VisualsHitTesting#100](~/samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsHitTesting/VisualBasic/MyWindow.vb#100)]  
  
<a name="implementing_the_win32_message_filter"></a>
## <a name="implementing-the-win32-message-filter"></a>Implémentation du filtre de messages Win32  
 La fenêtre Win32 de l’hôte pour les objets visuels nécessite une procédure de filtre de message de fenêtre pour gérer les messages qui sont envoyés à la fenêtre de la file d’attente d’application. La procédure de fenêtre reçoit des messages du système Win32. Ces messages peuvent être des messages de gestion de fenêtre ou des messages de saisie. Vous pouvez choisir de gérer un message dans votre procédure de fenêtre ou de transférer le message au système de traitement par défaut.  
  
 L’objet <xref:System.Windows.Interop.HwndSource> que vous avez défini comme le parent pour les objets visuels doit faire référence à la procédure de filtre de message de fenêtre que vous fournissez. Lorsque vous <xref:System.Windows.Interop.HwndSource> créez l’objet, définissez la <xref:System.Windows.Interop.HwndSourceParameters.HwndSourceHook%2A> propriété pour référencer la procédure de fenêtre.  
  
 [!code-csharp[VisualsHitTesting#102](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsHitTesting/CSharp/MyWindow.cs#102)]
 [!code-vb[VisualsHitTesting#102](~/samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsHitTesting/VisualBasic/MyWindow.vb#102)]  
  
 L’exemple suivant montre le code permettant de gérer les messages lorsque les boutons gauche et droit de la souris sont relâchés. La valeur de coordonnées de la position de `lParam` frappe de la souris est contenue dans la valeur du paramètre.  
  
 [!code-csharp[VisualsHitTesting#103](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsHitTesting/CSharp/MyWindow.cs#103)]
 [!code-vb[VisualsHitTesting#103](~/samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsHitTesting/VisualBasic/MyWindow.vb#103)]  
  
<a name="processing_the_win32_messages"></a>
## <a name="processing-the-win32-messages"></a>Traitement des messages Win32  
 Le code dans l’exemple suivant montre comment un test à succès est effectué contre la hiérarchie des objets visuels contenus dans la fenêtre Win32 hôte. Vous pouvez identifier si un point est dans la géométrie <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> d’un objet visuel, en utilisant la méthode pour spécifier l’objet visuel racine et la valeur de coordonnées pour frapper le test contre. Dans ce cas, l’objet visuel <xref:System.Windows.Interop.HwndSource.RootVisual%2A> racine est <xref:System.Windows.Interop.HwndSource> la valeur de la propriété de l’objet.  
  
 [!code-csharp[VisualsHitTesting#104](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsHitTesting/CSharp/MyCircle.cs#104)]
 [!code-vb[VisualsHitTesting#104](~/samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsHitTesting/VisualBasic/MyCircle.vb#104)]  
  
 Pour plus d’informations sur les tests à succès contre des objets visuels, voir [Hit Testing in the Visual Layer](hit-testing-in-the-visual-layer.md).  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Interop.HwndSource>
- [Hit Test with Win32 Interoperation Sample](https://github.com/microsoft/WPF-Samples/tree/master/Visual%20Layer/VisualsHitTesting) (Exemple de test de positionnement avec interopérabilité Win32)
- [Test de positionnement dans la couche visuelle](hit-testing-in-the-visual-layer.md)
