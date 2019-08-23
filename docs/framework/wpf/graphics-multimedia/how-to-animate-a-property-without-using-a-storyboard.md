---
title: 'Procédure : Animer une propriété sans utiliser de table de montage séquentiel'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- non-Storyboard animation
- local animation [WPF]
- animation [WPF], non-Storyboard (local)
ms.assetid: d411db70-4df7-487d-82bc-95a7c1b2e7f8
ms.openlocfilehash: 71711c0392576930e97986078ec5926ff6ca9813
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69963013"
---
# <a name="how-to-animate-a-property-without-using-a-storyboard"></a>Procédure : Animer une propriété sans utiliser de table de montage séquentiel
Cet exemple illustre une façon d’appliquer une animation à une propriété sans utiliser de <xref:System.Windows.Media.Animation.Storyboard>.  
  
> [!NOTE]
> La fonctionnalité n’est pas disponible en langage [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]. Pour plus d’informations sur l’animation d’une propriété en [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], consultez [Animer une propriété à l’aide d’un storyboard](how-to-animate-a-property-by-using-a-storyboard.md).  
  
 Pour appliquer une animation locale à une propriété, utilisez la <xref:System.Windows.UIElement.BeginAnimation%2A> méthode. Cette méthode accepte deux paramètres: un <xref:System.Windows.DependencyProperty> qui spécifie la propriété à animer et l’animation à appliquer à cette propriété.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment animer la largeur et la couleur d’arrière <xref:System.Windows.Controls.Button>-plan d’un.  
  
 [!code-cpp[animateproperty#11](~/samples/snippets/cpp/VS_Snippets_Wpf/animateproperty/CPP/LocalAnimationExample.cpp#11)]
 [!code-csharp[animateproperty#11](~/samples/snippets/csharp/VS_Snippets_Wpf/animateproperty/CSharp/LocalAnimationExample.cs#11)]
 [!code-vb[animateproperty#11](~/samples/snippets/visualbasic/VS_Snippets_Wpf/animateproperty/VisualBasic/LocalAnimationExample.vb#11)]  
  
 Plusieurs classes d’animation de l' <xref:System.Windows.Media.Animation> espace de noms existent pour animer différents types de propriétés. Pour plus d’informations sur l’animation de propriétés, consultez [Vue d’ensemble de l’animation](animation-overview.md). Pour plus d’informations sur les propriétés de dépendance (le type de propriétés présentées dans ces exemples) et leurs fonctionnalités, consultez [Vue d’ensemble des propriétés de dépendance](../advanced/dependency-properties-overview.md).  
  
 Il existe d’autres façons d’animer <xref:System.Windows.Media.Animation.Storyboard> sans utiliser d’objets. pour plus d’informations, consultez [vue d’ensemble des techniques d’animation de propriétés](property-animation-techniques-overview.md).  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Media.Animation.AnimationTimeline>
- <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A>
- <xref:System.Windows.Media.Animation>
- <xref:System.Windows.Media.Animation.Storyboard>
- [Vue d’ensemble des techniques d’animation de propriétés](property-animation-techniques-overview.md)
- [Vue d’ensemble de l’animation](animation-overview.md)
