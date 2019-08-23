---
title: 'Procédure : dessiner du texte avec GDI'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- GDI [Windows Forms], drawing text [Windows Forms]
- text [Windows Forms], drawing with TextRenderer
- drawing [Windows Forms], text
- Windows Forms, drawing text with GDI
ms.assetid: 2a19fe5d-2ace-451c-94db-01cb1118ef7b
ms.openlocfilehash: 3ed2b5c94e4a38a5873a34e61287c4038cab5cbb
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69956540"
---
# <a name="how-to-draw-text-with-gdi"></a>Procédure : dessiner du texte avec GDI
Avec la <xref:System.Windows.Forms.TextRenderer.DrawText%2A> méthode de la <xref:System.Windows.Forms.TextRenderer> classe, vous pouvez accéder à la fonctionnalité GDI pour dessiner du texte sur un formulaire ou un contrôle. Le rendu de texte GDI offre généralement de meilleures performances et une mesure de texte plus précise que GDI+.  
  
> [!NOTE]
> Les <xref:System.Windows.Forms.TextRenderer.DrawText%2A> méthodes de la <xref:System.Windows.Forms.TextRenderer> classe ne sont pas prises en charge pour l’impression. Lors de l’impression, utilisez <xref:System.Drawing.Graphics.DrawString%2A> toujours les méthodes <xref:System.Drawing.Graphics> de la classe.  
  
## <a name="example"></a>Exemple  
 L’exemple de code suivant montre comment dessiner du texte sur plusieurs lignes au sein d’un <xref:System.Windows.Forms.TextRenderer.DrawText%2A> rectangle à l’aide de la méthode.  
  
 [!code-csharp[System.Windows.Forms.TextRendererExamples#7](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.TextRendererExamples/CS/Form1.cs#7)]
 [!code-vb[System.Windows.Forms.TextRendererExamples#7](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.TextRendererExamples/VB/Form1.vb#7)]  
  
 Pour restituer le texte <xref:System.Windows.Forms.TextRenderer> avec la classe, vous <xref:System.Drawing.IDeviceContext>avez besoin d’un <xref:System.Drawing.Graphics> , <xref:System.Drawing.Font>tel que et un, d’un emplacement pour dessiner le texte et de la couleur dans laquelle il doit être dessiné. Si vous le souhaitez, vous pouvez spécifier la mise en forme du <xref:System.Windows.Forms.TextFormatFlags> texte à l’aide de l’énumération.  
  
 Pour plus d’informations sur l' <xref:System.Drawing.Graphics>obtention d' [un, consultez Procédure: Créez des objets graphiques pour](how-to-create-graphics-objects-for-drawing.md)le dessin. Pour plus d’informations sur la construction <xref:System.Drawing.Font>d’un [, consultez Procédure: Construisez des familles de](how-to-construct-font-families-and-fonts.md)polices et des polices.  
  
## <a name="compiling-the-code"></a>Compilation du code  
 L’exemple de code précédent est conçu pour être utilisé avec Windows Forms, et il <xref:System.Windows.Forms.PaintEventArgs> requiert `e`, qui est un paramètre <xref:System.Windows.Forms.PaintEventHandler>de.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.TextRenderer>
- <xref:System.Drawing.Font>
- <xref:System.Drawing.Color>
- [Utilisation de polices et de texte](using-fonts-and-text.md)
