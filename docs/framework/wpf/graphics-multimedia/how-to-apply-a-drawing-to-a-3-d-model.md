---
title: 'Comment : Appliquer un dessin à un modèle 3D'
ms.date: 03/30/2017
helpviewer_keywords:
- drawings [WPF], applying to 3D models
- 3D models [WPF], applying drawings to
ms.assetid: 68357577-b7fc-446e-8be9-a8cc7df3a350
ms.openlocfilehash: 5b10630ab674fa9489cdf7ad53516a680f19da08
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/21/2020
ms.locfileid: "80112178"
---
# <a name="how-to-apply-a-drawing-to-a-3d-model"></a>Comment : Appliquer un dessin à un modèle 3D

Cet exemple montre comment <xref:System.Windows.Media.DrawingBrush> utiliser <xref:System.Windows.Media.Media3D.Material> un comme appliqué à un modèle 3D.

Le code suivant <xref:System.Windows.Media.DrawingGroup> définit un comme <xref:System.Windows.Media.DrawingBrush>le contenu d’un .  Le <xref:System.Windows.Media.DrawingBrush> est fixé <xref:System.Windows.Media.Media3D.DiffuseMaterial.Brush%2A> comme <xref:System.Windows.Media.Media3D.DiffuseMaterial> la propriété de l’appliqué à un avion 3D.

> [!NOTE]
> Il est souvent souhaitable de définir des objets et des valeurs complexes comme le dessin ci-dessous comme des ressources qui peuvent être réutilisées et simplifier votre code. Voir [XAML Resources](../../../desktop-wpf/fundamentals/xaml-resources-define.md) pour plus d’informations.

[!code-xaml[3DGallery_snip#ApplyDrawingToMaterialInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/ApplyDrawingToMaterialExample.xaml#applydrawingtomaterialinline1)]

## <a name="example"></a>Exemple

Le code suivant affiche l’échantillon entier.

[!code-xaml[3DGallery_snip#ApplyDrawingToMaterialExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/ApplyDrawingToMaterialExample.xaml#applydrawingtomaterialexamplewholepage)]

## <a name="see-also"></a>Voir aussi

- [Ressources XAML](../../../desktop-wpf/fundamentals/xaml-resources-define.md)
- [Créer une scène 3D](how-to-create-a-3-d-scene.md)
- [Vue d'ensemble des objets Drawing](drawing-objects-overview.md)
- [Aperçu graphique 3D](3-d-graphics-overview.md)
