---
title: Comment animer dans un style
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], properties [WPF], within styles
- styles [WPF], animating properties within
ms.assetid: 6a791f3d-6b1f-4972-a2f9-35880bcfd954
ms.openlocfilehash: 0b29648bf15f0046adcdee610f9565f7deb24972
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744877"
---
# <a name="how-to-animate-in-a-style"></a>Comment animer dans un style

Cet exemple montre comment animer des propriétés dans un style. Lors de l’animation dans un style, seul l’élément de Framework pour lequel le style est défini peut être ciblé directement. Pour cibler un objet Freezable, vous devez « pointer vers le dessous » à partir d’une propriété de l’élément stylisé.

Dans l’exemple suivant, plusieurs animations sont définies dans un style et appliquées à un <xref:System.Windows.Controls.Button>. Lorsque l’utilisateur déplace la souris sur le bouton, il passe d’un fondu opaque à un semi-transparent partiel, et de nouveau, de manière répétée. Lorsque l’utilisateur déplace la souris en dehors du bouton, il devient complètement opaque. Lorsque l’utilisateur clique sur le bouton, sa couleur d’arrière-plan passe de orange à blanc, puis de nouveau. Étant donné que le <xref:System.Windows.Media.SolidColorBrush> utilisé pour peindre le bouton ne peut pas être ciblé directement, il est accessible en pointillés à partir de la propriété <xref:System.Windows.Controls.Control.Background%2A> du bouton.

## <a name="example"></a>Exemple

[!code-xaml[timingbehaviors_snip#21](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/StyleStoryboardsExample.xaml#21)]

Notez que lors de l’animation dans un style, il est possible de cibler des objets qui n’existent pas. Par exemple, supposons que votre style utilise un <xref:System.Windows.Media.SolidColorBrush> pour définir la propriété d’arrière-plan d’un bouton, mais à un moment donné, le style est substitué et l’arrière-plan du bouton est défini avec une <xref:System.Windows.Media.LinearGradientBrush>.  La tentative d’animer le <xref:System.Windows.Media.SolidColorBrush> ne lèvera pas d’exception. l’animation échouera tout simplement en silence.

Pour plus d’informations sur la syntaxe de ciblage des storyboards, consultez [vue d’ensemble des storyboards](storyboards-overview.md). Pour plus d’informations sur l’animation, consultez [vue d’ensemble](animation-overview.md)de l’animation. Pour plus d’informations sur les styles, consultez [style et création de modèles](../../../desktop-wpf/fundamentals/styles-templates-overview.md).
