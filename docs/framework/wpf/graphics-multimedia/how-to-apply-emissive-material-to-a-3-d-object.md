---
title: 'Comment : Appliquer le matériel d’émissive à un objet 3D'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- EmissiveMaterial [WPF], applying to 3D objects
- 3D objects [WPF], applying EmissiveMaterial
ms.assetid: fd442cc2-5adc-487a-ba70-e45ed54bb3b4
ms.openlocfilehash: bf32b41ec2410c01ad137ec0ca9311f7c2b70061
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/21/2020
ms.locfileid: "80112152"
---
# <a name="how-to-apply-emissive-material-to-a-3d-object"></a>Comment : Appliquer le matériel d’émissive à un objet 3D
L’exemple suivant montre <xref:System.Windows.Media.Media3D.EmissiveMaterial> comment utiliser pour ajouter de la couleur à un matériau existant égal à la couleur du pinceau de l’EmissiveMaterial. Le code <xref:System.Windows.Media.Media3D.DiffuseMaterial> ci-dessous affiche et <xref:System.Windows.Media.Media3D.EmissiveMaterial> appliqué en combinaison pour ajouter du bleu à l’apparence du DiffuseMaterial.  
  
 [!code-xaml[3DGallery_snip#EmmisiveMaterialAnimationExampleInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/EmissiveMaterialExample.xaml#emmisivematerialanimationexampleinline1)]  
  
 Dans le code de procédure :  
  
 [!code-csharp[3DGallery_procedural_snip#EmissiveMaterialCodeExampleInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_procedural_snip/CSharp/EmissiveMaterialExample.cs#emissivematerialcodeexampleinline1)]
 [!code-vb[3DGallery_procedural_snip#EmissiveMaterialCodeExampleInline1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/3DGallery_procedural_snip/visualbasic/emissivematerialexample.vb#emissivematerialcodeexampleinline1)]  
  
## <a name="example"></a>Exemple  
 Le code suivant affiche l’échantillon entier dans XAML.  
  
 [!code-xaml[3DGallery_snip#EmissiveMaterialExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/EmissiveMaterialExample.xaml#emissivematerialexamplewholepage)]  
  
## <a name="example"></a>Exemple  
 Voici l’échantillon entier du code de procédure.  
  
 [!code-csharp[3DGallery_procedural_snip#EmissiveMaterialCodeExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_procedural_snip/CSharp/EmissiveMaterialExample.cs#emissivematerialcodeexamplewholepage)]
 [!code-vb[3DGallery_procedural_snip#EmissiveMaterialCodeExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/3DGallery_procedural_snip/visualbasic/emissivematerialexample.vb#emissivematerialcodeexamplewholepage)]  
  
## <a name="see-also"></a>Voir aussi

- [Créer une scène 3D](how-to-create-a-3-d-scene.md)
- [Aperçu graphique 3D](3-d-graphics-overview.md)
- [Animer les propriétés matérielles dans une scène 3D](how-to-animate-material-properties-in-a-3-d-scene.md)
- [Appliquer du matériel à l’avant et au dos d’un objet 3D](how-to-apply-material-to-the-front-and-back-of-a-3-d-object.md)
