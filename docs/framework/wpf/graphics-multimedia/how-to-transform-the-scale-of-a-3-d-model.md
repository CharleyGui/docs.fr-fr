---
title: 'Comment : Transformer l’échelle d’un modèle 3D'
ms.date: 03/30/2017
helpviewer_keywords:
- scaling [WPF], 3D objects
- 3D objects [WPF], scaling
ms.assetid: f3fdfe33-f7dc-44b0-84a5-e43b89947f35
ms.openlocfilehash: be41a0e10929912c1b54bf7140d743d9453199bf
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/21/2020
ms.locfileid: "80111983"
---
# <a name="how-to-transform-the-scale-of-a-3d-model"></a>Comment : Transformer l’échelle d’un modèle 3D
Cet exemple montre comment mettre à l’échelle un objet 3D. Pour mettre à l’échelle <xref:System.Windows.Media.Media3D.ScaleTransform3D>un objet 3D, utilisez un . Les <xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleX%2A> <xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleY%2A>, <xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleZ%2A> , et les propriétés resize l’élément par le facteur que vous spécifiez. Par exemple, <xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleX%2A> une valeur de 1,5 étend un objet à 150 pour cent de sa largeur d’origine. Une <xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleY%2A> valeur de 0,5 réduit la hauteur d’un objet de 50 pour cent. Le code ci-dessous montre l’utilisation d’un <xref:System.Windows.Media.Media3D.ScaleTransform3D> comme transformation pour un <xref:System.Windows.Media.Media3D.GeometryModel3D>.  
  
 [!code-xaml[3DGallery_snip#ScaleTransform3DExampleInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/ScaleTransform3DExample.xaml#scaletransform3dexampleinline1)]  
  
## <a name="example"></a>Exemple  
 Le code suivant affiche l’échantillon entier.  
  
 [!code-xaml[3DGallery_snip#ScaleTransform3DExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/ScaleTransform3DExample.xaml#scaletransform3dexamplewholepage)]  
  
## <a name="see-also"></a>Voir aussi

- [Animation de traductions 3D](how-to-animate-3-d-translations.md)
- [Créer une scène 3D](how-to-create-a-3-d-scene.md)
- [Aperçu graphique 3D](3-d-graphics-overview.md)
