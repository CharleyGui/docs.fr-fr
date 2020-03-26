---
title: 'Comment : Créer une scène 3D'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- scenes [WPF], 3D
- 3D scenes
ms.assetid: adb4a598-71a2-4dd5-b677-ea3fc11b78b2
ms.openlocfilehash: 36453894e06e7b59f339c21713449140c17f6851
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/21/2020
ms.locfileid: "80112100"
---
# <a name="how-to-create-a-3d-scene"></a>Comment : Créer une scène 3D
Cet exemple montre comment créer un objet 3D qui ressemble à une feuille de papier plate qui a été tourné. Un <xref:System.Windows.Controls.Viewport3D> avec les composants suivants sont utilisés pour créer cette scène 3D simple:  
  
- Un appareil photo <xref:System.Windows.Media.Media3D.PerspectiveCamera>est créé à l’aide d’un . La caméra précise quelle partie de la scène 3D est visible.  
  
- Un maillage est créé pour spécifier la forme de <xref:System.Windows.Media.Media3D.GeometryModel3D.Geometry%2A> l’objet 3D (feuille de papier) en utilisant la propriété de <xref:System.Windows.Media.Media3D.GeometryModel3D>.  
  
- Un matériau est spécifié pour être affiché sur la surface de l’objet (gradient linéaire dans cet échantillon) en utilisant la <xref:System.Windows.Media.Media3D.GeometryModel3D.Material%2A> propriété de <xref:System.Windows.Media.Media3D.GeometryModel3D>.  
  
- Une lumière est créée pour <xref:System.Windows.Media.Media3D.DirectionalLight>briller sur l’objet à l’aide de .  
  
## <a name="example"></a>Exemple  
 Le code ci-dessous montre comment créer une scène 3D dans XAML.  
  
 [!code-xaml[3DGallery_snip#Basic3DShapeExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/Basic3DShapeExample.xaml#basic3dshapeexamplewholepage)]  
  
## <a name="example"></a>Exemple  
 Le code ci-dessous montre comment créer la même scène 3D dans le code de procédure.  
  
 [!code-csharp[3DGallery_procedural_snip#Basic3DShapeCodeExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_procedural_snip/CSharp/Basic3DShapeExample.cs#basic3dshapecodeexamplewholepage)]
 [!code-vb[3DGallery_procedural_snip#Basic3DShapeCodeExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/3DGallery_procedural_snip/visualbasic/basic3dshapeexample.vb#basic3dshapecodeexamplewholepage)]  
  
## <a name="see-also"></a>Voir aussi

- [Aperçu graphique 3D](3-d-graphics-overview.md)
