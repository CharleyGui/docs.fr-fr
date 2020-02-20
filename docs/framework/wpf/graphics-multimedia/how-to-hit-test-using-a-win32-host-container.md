---
title: "Comment : effectuer un test de positionnement à l'aide d'un conteneur hôte Win32"
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hit tests [WPF], using Win32 host containers
- visual objects [WPF], hit tests on
- Win32 host containers [WPF], hit tests using
ms.assetid: 9491f7f3-d8ba-4573-a888-2f064d1349dc
ms.openlocfilehash: a86c1c36f75fa232d52731959371268a8b2593d7
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452803"
---
# <a name="how-to-hit-test-using-a-win32-host-container"></a>Comment : effectuer un test de positionnement à l'aide d'un conteneur hôte Win32
Vous pouvez créer des objets visuels dans une fenêtre Win32 en fournissant un conteneur de fenêtre hôte pour les objets visuels. Pour assurer la gestion des événements des objets visuels du conteneur, vous devez traiter les messages transmis à la boucle de filtre de messages du conteneur de fenêtre hôte. Reportez-vous au [Didacticiel : Hébergement d’objets visuels dans une application Win32](tutorial-hosting-visual-objects-in-a-win32-application.md) pour plus d’informations sur la façon d’héberger des objets visuels dans une fenêtre Win32.  
  
## <a name="example"></a>Exemple  
 Le code suivant montre comment configurer des gestionnaires d’événements de souris pour une fenêtre Win32 utilisée en tant que conteneur hôte pour les objets visuels.  
  
 [!code-csharp[VisualsHitTesting#103](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsHitTesting/CSharp/MyWindow.cs#103)]
 [!code-vb[VisualsHitTesting#103](~/samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsHitTesting/VisualBasic/MyWindow.vb#103)]  
  
 L’exemple suivant montre comment configurer un test de positionnement en réponse pour intercepter des événements de souris spécifiques.  
  
 [!code-csharp[VisualsHitTesting#104](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsHitTesting/CSharp/MyCircle.cs#104)]
 [!code-vb[VisualsHitTesting#104](~/samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsHitTesting/VisualBasic/MyCircle.vb#104)]  
  
 L’objet <xref:System.Windows.Interop.HwndSource> présente [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] contenu dans une fenêtre Win32. La valeur de la propriété <xref:System.Windows.Interop.HwndSource.RootVisual%2A> de l’objet <xref:System.Windows.Interop.HwndSource> représente le nœud supérieur dans la hiérarchie de l’arborescence d’éléments visuels.  
  
 Pour obtenir l’exemple complet sur les objets de test de positionnement à l’aide d’un conteneur hôte Win32, consultez [test de positionnement avec l’exemple d’interopérabilité Win32](https://github.com/microsoft/WPF-Samples/tree/master/Visual%20Layer/VisualsHitTesting).  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Interop.HwndSource>
- [Test de positionnement dans la couche visuelle](hit-testing-in-the-visual-layer.md)
- [Didacticiel : hébergement d’objets visuels dans une application Win32](tutorial-hosting-visual-objects-in-a-win32-application.md)
