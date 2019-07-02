---
title: Importance de l'ordre des transformations
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- transformations [Windows Forms], order significance
ms.assetid: 37d5f9dc-a5cf-4475-aa5d-34d714e808a9
ms.openlocfilehash: 08927ebaa460e19e558dce22f39c13c31f0e49d0
ms.sourcegitcommit: b1cfd260928d464d91e20121f9bdba7611c94d71
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2019
ms.locfileid: "67504909"
---
# <a name="why-transformation-order-is-significant"></a>Importance de l'ordre des transformations
Un seul <xref:System.Drawing.Drawing2D.Matrix> objet peut stocker une seule transformation ou une séquence de transformations. Celle-ci est appelée une transformation composite. La matrice d’une transformation composite est obtenue en multipliant les matrices des différentes transformations.  
  
## <a name="composite-transform-examples"></a>Exemples de transformations composites  
 Dans une transformation composite, l’ordre des diverses transformations est important. Par exemple, si vous tout d’abord faire pivoter, mettre à l’échelle, puis traduisez, vous obtenez un résultat différent que si vous convertissez tout d’abord, faire pivoter, puis mettre à l’échelle. Dans GDI +, les transformations composites sont construites de gauche à droite. Si S, R et T sont respectivement des matrices de mise à l’échelle, de rotation et de traduction, puis le produit SRT (dans cet ordre) est la matrice de la transformation composite qui s’adapte premier, puis fait pivoter, puis traduit. La matrice produite par le produit SRT est différente de la matrice produite par le produit TRS.  
  
 Un ordre est important parce que les transformations telles que rotation et mise à l’échelle sont effectuées par rapport à l’origine du système de coordonnées. Mise à l’échelle un objet qui est centré à l’origine de produit le même résultat que la mise à l’échelle un objet qui a été déplacé en dehors de l’origine. De même, la rotation d’un objet qui est centré à l’origine produit le même résultat que la rotation d’un objet qui a été déplacé en dehors de l’origine.  
  
 L’exemple suivant combine une mise à l’échelle, la rotation et la translation (dans cet ordre) pour former une transformation composite. L’argument <xref:System.Drawing.Drawing2D.MatrixOrder.Append> passé à la <xref:System.Drawing.Graphics.RotateTransform%2A> méthode indique que la rotation suivra la mise à l’échelle. De même, l’argument <xref:System.Drawing.Drawing2D.MatrixOrder.Append> passé à la <xref:System.Drawing.Graphics.TranslateTransform%2A> méthode indique que la traduction suivra la rotation. <xref:System.Drawing.Drawing2D.MatrixOrder.Append> et <xref:System.Drawing.Drawing2D.MatrixOrder.Prepend> sont membres de la <xref:System.Drawing.Drawing2D.MatrixOrder> énumération.  
  
 [!code-csharp[System.Drawing.MiscLegacyTopics#21](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.MiscLegacyTopics#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#21)]  
  
 L’exemple suivant effectue les appels de méthode de même que l’exemple précédent, mais l’ordre des appels est inversé. L’ordre des opérations est d’abord convertir, faire pivoter, puis mise à l’échelle, ce qui produit un résultat très différent à la première mise à l’échelle, puis de faire pivoter, puis traduire.  
  
 [!code-csharp[System.Drawing.MiscLegacyTopics#22](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#22)]
 [!code-vb[System.Drawing.MiscLegacyTopics#22](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#22)]  
  
 Une pour inverser l’ordre des transformations individuelles dans une transformation composite consiste à inverser l’ordre d’une séquence d’appels de méthode. Une deuxième méthode permettant de contrôler l’ordre des opérations consiste à modifier l’argument de commande de matrice. L’exemple suivant est identique à l’exemple précédent, à ceci près que <xref:System.Drawing.Drawing2D.MatrixOrder.Append> a été remplacé par <xref:System.Drawing.Drawing2D.MatrixOrder.Prepend>. La multiplication de matrice s’effectue dans l’ordre SRT, où S, R et T sont les matrices pour la mise à l’échelle, faire pivoter et traduire, respectivement. L’ordre de la transformation composite est la première échelle, faire pivoter, puis traduire.  
  
 [!code-csharp[System.Drawing.MiscLegacyTopics#23](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#23)]
 [!code-vb[System.Drawing.MiscLegacyTopics#23](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#23)]  
  
 Le résultat de l’exemple précédent est la même suite le premier exemple dans cette rubrique. Il s’agit, car nous avons inversé l’ordre des appels de méthode et l’ordre de la multiplication de matrice.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Drawing.Drawing2D.Matrix>
- [Systèmes de coordonnées et transformations](coordinate-systems-and-transformations.md)
- [Utilisation des transformations dans GDI+ managé](using-transformations-in-managed-gdi.md)
