---
title: "Comment : dessiner du texte sur l'arrière-plan d'un contrôle"
ms.date: 03/30/2017
helpviewer_keywords:
- controls [WPF], drawing text to backgrounds
- text [WPF], drawing to control backgrounds
- drawing [WPF], text to control backgrounds
- backgrounds [WPF], drawing text to
- typography [WPF], drawing text to control backgrounds
ms.assetid: 686d8fba-f61c-4974-a871-c635d67a7f69
ms.openlocfilehash: 14300f763b67c6ac67ee408de2009c328d499c13
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73424369"
---
# <a name="how-to-draw-text-to-a-controls-background"></a>Comment : dessiner du texte sur l'arrière-plan d'un contrôle
Vous pouvez dessiner du texte directement à l’arrière-plan d’un contrôle en convertissant une chaîne de texte en objet <xref:System.Windows.Media.FormattedText>, puis en dessinant l’objet dans le <xref:System.Windows.Media.DrawingContext>du contrôle. Vous pouvez également utiliser cette technique pour dessiner sur l’arrière-plan des objets dérivés de <xref:System.Windows.Controls.Panel>, tels que <xref:System.Windows.Controls.Canvas> et <xref:System.Windows.Controls.StackPanel>.  
  
 ![Capture d’écran des contrôles affichant du texte comme arrière-plan.](./media/how-to-draw-text-to-a-control-background/draw-text-background.png "DrawText2Background01")  
Exemple de contrôles avec des arrière-plans de texte personnalisés  
  
## <a name="example"></a>Exemple  
 Pour dessiner sur l’arrière-plan d’un contrôle, créez un nouvel objet <xref:System.Windows.Media.DrawingBrush> et dessinez le texte converti dans le <xref:System.Windows.Media.DrawingContext>de l’objet. Ensuite, assignez le nouvel <xref:System.Windows.Media.DrawingBrush> à la propriété d’arrière-plan du contrôle.  
  
 L’exemple de code suivant montre comment créer un objet <xref:System.Windows.Media.FormattedText> et dessiner sur l’arrière-plan d’un objet <xref:System.Windows.Controls.Label> et <xref:System.Windows.Controls.Button>.  
  
 [!code-csharp[DrawTextToControlBackground#DrawTextToControlBackground1](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawTextToControlBackground/CSHARP/Window1.xaml.cs#drawtexttocontrolbackground1)]  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Media.FormattedText>
- [Dessin du texte mis en forme](drawing-formatted-text.md)
