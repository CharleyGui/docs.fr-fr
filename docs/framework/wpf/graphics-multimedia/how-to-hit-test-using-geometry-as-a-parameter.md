---
title: 'Procédure : Effectuer un test de positionnement avec Geometry comme paramètre'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hit tests [WPF], on visual objects using Geometry objects [WPF]
- visual objects [WPF], hit tests on
- Geometry objects [WPF], hit tests on visual objects [WPF]
ms.assetid: 6c8bdbf2-19e0-4fbb-bf89-c1252b2ebc61
ms.openlocfilehash: 8bed7784b00f49178c9a87def74b62f7ce620ec7
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69923403"
---
# <a name="how-to-hit-test-using-geometry-as-a-parameter"></a>Procédure : Effectuer un test de positionnement avec Geometry comme paramètre
Cet exemple montre comment effectuer un test de positionnement sur un objet visuel à l' <xref:System.Windows.Media.Geometry> aide d’un comme paramètre de test de positionnement.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment configurer un test de positionnement à l' <xref:System.Windows.Media.GeometryHitTestParameters> aide de <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> pour la méthode. La <xref:System.Windows.Point> valeur passée à la `OnMouseDown` méthode est utilisée pour créer un <xref:System.Windows.Media.Geometry> objet afin d’étendre la plage du test de positionnement.  
  
 [!code-csharp[HitTestingOverview#HitTestingOverviewSnippet10](~/samples/snippets/csharp/VS_Snippets_Wpf/HitTestingOverview/CSharp/GeometryHitTest.cs#hittestingoverviewsnippet10)]
 [!code-vb[HitTestingOverview#HitTestingOverviewSnippet10](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HitTestingOverview/visualbasic/geometryhittest.vb#hittestingoverviewsnippet10)]  
  
 La <xref:System.Windows.Media.GeometryHitTestResult.IntersectionDetail%2A> propriété de <xref:System.Windows.Media.GeometryHitTestResult> fournit des informations sur les résultats d’un test de positionnement qui <xref:System.Windows.Media.Geometry> utilise un comme paramètre de test de positionnement. L’illustration suivante montre la relation entre la géométrie du test de positionnement (le cercle bleu) et le contenu restitué de l’objet visuel cible (le carré rouge).  
  
 ![Diagramme qui montre IntersectionDetail utilisé dans le test de positionnement.](./media/how-to-hit-test-using-geometry-as-a-parameter/intersectiondetail-hit-test.png)  
  
 L’exemple suivant montre comment implémenter un rappel de test de positionnement <xref:System.Windows.Media.Geometry> quand un est utilisé comme paramètre de test de positionnement. Le `result` paramètre est casté en <xref:System.Windows.Media.GeometryHitTestResult> un afin de récupérer la valeur de la <xref:System.Windows.Media.GeometryHitTestResult.IntersectionDetail%2A> propriété. La valeur de propriété vous permet de déterminer si <xref:System.Windows.Media.Geometry> le paramètre de test de positionnement est entièrement ou partiellement contenu dans le contenu rendu de la cible du test d’atteinte. Dans ce cas, l’exemple de code ajoute à la liste les résultats du test de positionnement uniquement pour les objets visuels qui sont entièrement contenus dans les limites de la cible.  
  
 [!code-csharp[HitTestingOverview#HitTestingOverviewSnippet11](~/samples/snippets/csharp/VS_Snippets_Wpf/HitTestingOverview/CSharp/GeometryHitTest.cs#hittestingoverviewsnippet11)]
 [!code-vb[HitTestingOverview#HitTestingOverviewSnippet11](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HitTestingOverview/visualbasic/geometryhittest.vb#hittestingoverviewsnippet11)]  
  
> [!NOTE]
> Le <xref:System.Windows.Media.HitTestResult> rappel ne doit pas être appelé lorsque le détail de <xref:System.Windows.Media.IntersectionDetail.Empty>l’intersection est.  
  
## <a name="see-also"></a>Voir aussi

- [Test de positionnement dans la couche visuelle](hit-testing-in-the-visual-layer.md)
- [Effectuer un test de positionnement avec Geometry dans un Visual](how-to-hit-test-geometry-in-a-visual.md)
