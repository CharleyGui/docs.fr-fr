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
ms.openlocfilehash: b71783f2d061c9139de4449d8e0106eb00345894
ms.sourcegitcommit: 9a97c76e141333394676bc5d264c6624b6f45bcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2020
ms.locfileid: "75740177"
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
  
 Pour obtenir l’exemple complet sur les objets de test de positionnement à l’aide d’un conteneur hôte Win32, consultez [test de positionnement avec l’exemple d’interopérabilité Win32](https://go.microsoft.com/fwlink/?LinkID=159995).  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Interop.HwndSource>
- [Test de positionnement dans la couche visuelle](hit-testing-in-the-visual-layer.md)
- [Didacticiel : hébergement d’objets visuels dans une application Win32](tutorial-hosting-visual-objects-in-a-win32-application.md)
