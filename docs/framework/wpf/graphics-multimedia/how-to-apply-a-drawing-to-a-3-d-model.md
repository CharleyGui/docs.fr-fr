---
title: 'Comment : appliquer un dessin à un modèle 3D'
ms.date: 03/30/2017
helpviewer_keywords:
- drawings [WPF], applying to 3-D models
- 3-D models [WPF], applying drawings to
ms.assetid: 68357577-b7fc-446e-8be9-a8cc7df3a350
ms.openlocfilehash: 311a3ac1d9fa219a3a365d506d9d0c3e8b6bc229
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459370"
---
# <a name="how-to-apply-a-drawing-to-a-3-d-model"></a>Comment : appliquer un dessin à un modèle 3D

Cet exemple montre comment utiliser une <xref:System.Windows.Media.DrawingBrush> comme <xref:System.Windows.Media.Media3D.Material> appliquée à un modèle 3D.

Le code suivant définit une <xref:System.Windows.Media.DrawingGroup> comme contenu d’un <xref:System.Windows.Media.DrawingBrush>.  La <xref:System.Windows.Media.DrawingBrush> est définie comme <xref:System.Windows.Media.Media3D.DiffuseMaterial.Brush%2A> propriété de la <xref:System.Windows.Media.Media3D.DiffuseMaterial> appliquée à un plan 3D.

> [!NOTE]
> Il est souvent souhaitable de définir des objets et des valeurs complexes comme le dessin ci-dessous en tant que ressources qui peuvent être réutilisées et simplifier votre code. Pour plus d’informations, consultez [ressources XAML](../../../desktop-wpf/fundamentals/xaml-resources-define.md) .

[!code-xaml[3DGallery_snip#ApplyDrawingToMaterialInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/ApplyDrawingToMaterialExample.xaml#applydrawingtomaterialinline1)]

## <a name="example"></a>Exemple

Le code suivant illustre l’exemple complet.

[!code-xaml[3DGallery_snip#ApplyDrawingToMaterialExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/ApplyDrawingToMaterialExample.xaml#applydrawingtomaterialexamplewholepage)]

## <a name="see-also"></a>Voir aussi

- [Ressources XAML](../../../desktop-wpf/fundamentals/xaml-resources-define.md)
- [Créer une scène 3D](how-to-create-a-3-d-scene.md)
- [Vue d’ensemble des objets de dessin](drawing-objects-overview.md)
- [Vue d’ensemble des graphiques 3D](3-d-graphics-overview.md)
