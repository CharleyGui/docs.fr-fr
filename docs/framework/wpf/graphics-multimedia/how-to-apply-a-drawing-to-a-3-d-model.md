---
title: 'Procédure : Appliquer un dessin à un modèle 3D'
ms.date: 03/30/2017
helpviewer_keywords:
- drawings [WPF], applying to 3-D models
- 3-D models [WPF], applying drawings to
ms.assetid: 68357577-b7fc-446e-8be9-a8cc7df3a350
ms.openlocfilehash: 14470d0adeb948ea46a0720b5713c20fb7d8e6d8
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855884"
---
# <a name="how-to-apply-a-drawing-to-a-3-d-model"></a>Procédure : Appliquer un dessin à un modèle 3D

Cet exemple montre comment utiliser un <xref:System.Windows.Media.DrawingBrush> <xref:System.Windows.Media.Media3D.Material> comme appliqué à un modèle 3D.

Le code suivant définit un <xref:System.Windows.Media.DrawingGroup> comme le contenu d’un <xref:System.Windows.Media.DrawingBrush>.  Le <xref:System.Windows.Media.DrawingBrush> est défini <xref:System.Windows.Media.Media3D.DiffuseMaterial.Brush%2A> en tant que propriété du <xref:System.Windows.Media.Media3D.DiffuseMaterial> appliqué à un plan 3D.

> [!NOTE]
> Il est souvent souhaitable de définir des objets et des valeurs complexes comme le dessin ci-dessous en tant que ressources qui peuvent être réutilisées et simplifier votre code. Pour plus d’informations, consultez [ressources XAML](../advanced/xaml-resources.md) .

[!code-xaml[3DGallery_snip#ApplyDrawingToMaterialInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/ApplyDrawingToMaterialExample.xaml#applydrawingtomaterialinline1)]

## <a name="example"></a>Exemple

Le code suivant illustre l’exemple complet.

[!code-xaml[3DGallery_snip#ApplyDrawingToMaterialExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/ApplyDrawingToMaterialExample.xaml#applydrawingtomaterialexamplewholepage)]

## <a name="see-also"></a>Voir aussi

- [Ressources XAML](../advanced/xaml-resources.md)
- [Créer une scène 3D](how-to-create-a-3-d-scene.md)
- [Vue d’ensemble des objets de dessin](drawing-objects-overview.md)
- [Vue d’ensemble des graphiques 3D](3-d-graphics-overview.md)
