---
title: 'Comment : Appliquer du matériel à l’avant et au dos d’un objet 3D'
ms.date: 03/30/2017
helpviewer_keywords:
- 3D objects [WPF], applying Material class
- Material class [WPF], applying to both sides of 3D object
- classes [WPF], Material
ms.assetid: d93c8ad6-4939-4d29-9544-4d16d98093c1
ms.openlocfilehash: 5c24879d97e7857fb07fcef4a9ba8efa901e4a39
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/21/2020
ms.locfileid: "80112139"
---
# <a name="how-to-apply-material-to-the-front-and-back-of-a-3d-object"></a>Comment : Appliquer du matériel à l’avant et au dos d’un objet 3D
L’exemple suivant montre <xref:System.Windows.Media.Media3D.Material> comment appliquer un à l’avant et à l’arrière d’un objet 3D et animer l’objet pour montrer les deux côtés de l’objet. La <xref:System.Windows.Media.Media3D.GeometryModel3D.Material%2A> propriété <xref:System.Windows.Media.Media3D.GeometryModel3D> d’un est <xref:System.Windows.Media.Brush> utilisée pour appliquer un rouge <xref:System.Windows.Media.Media3D.GeometryModel3D.BackMaterial%2A> sur <xref:System.Windows.Media.Media3D.GeometryModel3D> le côté avant <xref:System.Windows.Media.Brush> de l’objet et la propriété de l’est utilisé pour appliquer un bleu sur le côté arrière de l’objet. Le code ci-dessous affiche l’application des matériaux à l’objet :  
  
 [!code-xaml[Animation3DGallery_snip#BackMaterialAnimationExampleInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/BackMaterialAnimationExample.xaml#backmaterialanimationexampleinline1)]  
  
## <a name="example"></a>Exemple  
 Le code suivant affiche l’échantillon entier.  
  
 [!code-xaml[Animation3DGallery_snip#BackMaterialAnimationExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/BackMaterialAnimationExample.xaml#backmaterialanimationexamplewholepage)]  
  
## <a name="see-also"></a>Voir aussi

- [Créer une scène 3D](how-to-create-a-3-d-scene.md)
- [Aperçu graphique 3D](3-d-graphics-overview.md)
- [Animer les propriétés matérielles dans une scène 3D](how-to-animate-material-properties-in-a-3-d-scene.md)
- [Appliquer le matériel Emissive sur un objet 3D](how-to-apply-emissive-material-to-a-3-d-object.md)
