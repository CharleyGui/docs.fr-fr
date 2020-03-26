---
title: 'Comment : Animer les propriétés matérielles dans une scène 3D'
ms.date: 03/30/2017
helpviewer_keywords:
- Material properties [WPF], animating in 3D scenes
- animation [WPF], Material properties in 3D scenes
- 3D scenes [WPF], animating Material properties
ms.assetid: 229fd6eb-7401-4992-b0c9-8b28de230c0f
ms.openlocfilehash: db59debcd7558cde52d8604cb04c8c4e68921825
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/21/2020
ms.locfileid: "80112191"
---
# <a name="how-to-animate-material-properties-in-a-3d-scene"></a>Comment : Animer les propriétés matérielles dans une scène 3D
Cet exemple montre comment animer <xref:System.Windows.Media.Brush.Opacity%2A> la <xref:System.Windows.Media.Media3D.Material> propriété de l’appliqué à un modèle 3D.  
  
 L’exemple de code <xref:System.Windows.Media.LinearGradientBrush> suivant <xref:System.Windows.Media.Media3D.Material> définit l’utilisé comme l’appliqué à l’objet 3D.  
  
 [!code-xaml[Animation3DGallery_snip#AnimateMaterialExampleInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/AnimateMaterialExample.xaml#animatematerialexampleinline1)]  
  
 La <xref:System.Windows.Media.Brush.Opacity%2A> propriété <xref:System.Windows.Media.LinearGradientBrush> de ceci est animée utilisant l’exemple de code ci-dessous.  
  
 [!code-xaml[Animation3DGallery_snip#AnimateMaterialExampleInline2](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/AnimateMaterialExample.xaml#animatematerialexampleinline2)]  
  
## <a name="example"></a>Exemple  
 Le code suivant affiche l’échantillon entier.  
  
 [!code-xaml[Animation3DGallery_snip#AnimateMaterialExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/AnimateMaterialExample.xaml#animatematerialexamplewholepage)]  
  
## <a name="see-also"></a>Voir aussi

- [Créer une scène 3D](how-to-create-a-3-d-scene.md)
- [Aperçu graphique 3D](3-d-graphics-overview.md)
