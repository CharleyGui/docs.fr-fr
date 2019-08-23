---
title: 'Procédure : Contrôler une horloge de façon interactive'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controlling clocks interactively [WPF]
- clocks [WPF], controlling interactively
ms.assetid: d0b520e0-2f18-4cef-977f-2909e709548a
ms.openlocfilehash: 2d18f395974750a6b85458f636a27f6101e7978f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69951347"
---
# <a name="how-to-interactively-control-a-clock"></a>Procédure : Contrôler une horloge de façon interactive
La <xref:System.Windows.Media.Animation.Clock> propriété d' <xref:System.Windows.Media.Animation.ClockController> un objet vous permet de démarrer, d’interrompre, de reprendre et de rechercher de manière interactive, d’avancer l’horloge à sa période de remplissage et d’arrêter l’horloge. Seule l’horloge racine d’une arborescence de minutage peut être contrôlée de manière interactive.  
  
> [!NOTE]
> Il existe d’autres façons de contrôler de manière interactive les animations qui ne nécessitent pas de travailler directement avec les horloges: vous pouvez également utiliser des storyboards. Les storyboards sont pris en charge dans le balisage et le code. Pour obtenir un exemple, consultez [animer une propriété à l’aide d’un Storyboard](how-to-animate-a-property-by-using-a-storyboard.md) ou [vue d’ensemble](animation-overview.md)de l’animation.  
  
 Dans l’exemple suivant, plusieurs boutons sont utilisés pour contrôler de manière interactive une horloge d’animation.  
  
## <a name="example"></a>Exemple  
 [!code-csharp[timingbehaviors_procedural_snip#GraphicsMMClockControllerExample](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_procedural_snip/CSharp/ClockControllerExample.cs#graphicsmmclockcontrollerexample)]
 [!code-vb[timingbehaviors_procedural_snip#GraphicsMMClockControllerExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_procedural_snip/visualbasic/clockcontrollerexample.vb#graphicsmmclockcontrollerexample)]  
  
## <a name="see-also"></a>Voir aussi

- [Animer une propriété à l’aide d’une table de montage séquentiel](how-to-animate-a-property-by-using-a-storyboard.md)
- [Vue d’ensemble de l’animation](animation-overview.md)
