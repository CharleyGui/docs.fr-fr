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
# <a name="how-to-draw-text-to-a-controls-background"></a><span data-ttu-id="bb100-102">Comment : dessiner du texte sur l'arrière-plan d'un contrôle</span><span class="sxs-lookup"><span data-stu-id="bb100-102">How to: Draw Text to a Control's Background</span></span>
<span data-ttu-id="bb100-103">Vous pouvez dessiner du texte directement à l’arrière-plan d’un contrôle en convertissant une chaîne de texte en objet <xref:System.Windows.Media.FormattedText>, puis en dessinant l’objet dans le <xref:System.Windows.Media.DrawingContext>du contrôle.</span><span class="sxs-lookup"><span data-stu-id="bb100-103">You can draw text directly to the background of a control by converting a text string to a <xref:System.Windows.Media.FormattedText> object, and then drawing the object to the control's <xref:System.Windows.Media.DrawingContext>.</span></span> <span data-ttu-id="bb100-104">Vous pouvez également utiliser cette technique pour dessiner sur l’arrière-plan des objets dérivés de <xref:System.Windows.Controls.Panel>, tels que <xref:System.Windows.Controls.Canvas> et <xref:System.Windows.Controls.StackPanel>.</span><span class="sxs-lookup"><span data-stu-id="bb100-104">You can also use this technique for drawing to the background of objects derived from <xref:System.Windows.Controls.Panel>, such as <xref:System.Windows.Controls.Canvas> and <xref:System.Windows.Controls.StackPanel>.</span></span>  
  
 <span data-ttu-id="bb100-105">![Capture d’écran des contrôles affichant du texte comme arrière-plan.](./media/how-to-draw-text-to-a-control-background/draw-text-background.png "DrawText2Background01")</span><span class="sxs-lookup"><span data-stu-id="bb100-105">![Screenshot of controls displaying text as background.](./media/how-to-draw-text-to-a-control-background/draw-text-background.png "DrawText2Background01")</span></span>  
<span data-ttu-id="bb100-106">Exemple de contrôles avec des arrière-plans de texte personnalisés</span><span class="sxs-lookup"><span data-stu-id="bb100-106">Example of controls with custom text backgrounds</span></span>  
  
## <a name="example"></a><span data-ttu-id="bb100-107">Exemple</span><span class="sxs-lookup"><span data-stu-id="bb100-107">Example</span></span>  
 <span data-ttu-id="bb100-108">Pour dessiner sur l’arrière-plan d’un contrôle, créez un nouvel objet <xref:System.Windows.Media.DrawingBrush> et dessinez le texte converti dans le <xref:System.Windows.Media.DrawingContext>de l’objet.</span><span class="sxs-lookup"><span data-stu-id="bb100-108">To draw to the background of a control, create a new <xref:System.Windows.Media.DrawingBrush> object and draw the converted text to the object's <xref:System.Windows.Media.DrawingContext>.</span></span> <span data-ttu-id="bb100-109">Ensuite, assignez le nouvel <xref:System.Windows.Media.DrawingBrush> à la propriété d’arrière-plan du contrôle.</span><span class="sxs-lookup"><span data-stu-id="bb100-109">Then, assign the new <xref:System.Windows.Media.DrawingBrush> to the control's background property.</span></span>  
  
 <span data-ttu-id="bb100-110">L’exemple de code suivant montre comment créer un objet <xref:System.Windows.Media.FormattedText> et dessiner sur l’arrière-plan d’un objet <xref:System.Windows.Controls.Label> et <xref:System.Windows.Controls.Button>.</span><span class="sxs-lookup"><span data-stu-id="bb100-110">The following code example shows how to create a <xref:System.Windows.Media.FormattedText> object and draw to the background of a <xref:System.Windows.Controls.Label> and <xref:System.Windows.Controls.Button> object.</span></span>  
  
 [!code-csharp[DrawTextToControlBackground#DrawTextToControlBackground1](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawTextToControlBackground/CSHARP/Window1.xaml.cs#drawtexttocontrolbackground1)]  
  
## <a name="see-also"></a><span data-ttu-id="bb100-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bb100-111">See also</span></span>

- <xref:System.Windows.Media.FormattedText>
- [<span data-ttu-id="bb100-112">Dessin du texte mis en forme</span><span class="sxs-lookup"><span data-stu-id="bb100-112">Drawing Formatted Text</span></span>](drawing-formatted-text.md)
