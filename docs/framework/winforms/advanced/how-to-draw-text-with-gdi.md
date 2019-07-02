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
ms.openlocfilehash: 3d5b79e82185c044314ff8807b86835ef6a87c45
ms.sourcegitcommit: b1cfd260928d464d91e20121f9bdba7611c94d71
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2019
ms.locfileid: "67505908"
---
# <a name="how-to-draw-text-with-gdi"></a>Procédure : dessiner du texte avec GDI
Avec le <xref:System.Windows.Forms.TextRenderer.DrawText%2A> méthode dans le <xref:System.Windows.Forms.TextRenderer> (classe), vous pouvez accéder à des fonctionnalités GDI pour dessiner du texte sur un formulaire ou contrôle. Rendu de texte GDI offre généralement de meilleures performances et plus précis mesure de texte que GDI +.  
  
> [!NOTE]
>  Le <xref:System.Windows.Forms.TextRenderer.DrawText%2A> méthodes de la <xref:System.Windows.Forms.TextRenderer> classe ne sont pas pris en charge pour l’impression. Lors de l’impression, utilisez toujours le <xref:System.Drawing.Graphics.DrawString%2A> méthodes de la <xref:System.Drawing.Graphics> classe.  
  
## <a name="example"></a>Exemple  
 L’exemple de code suivant montre comment dessiner du texte sur plusieurs lignes dans un rectangle à l’aide de la <xref:System.Windows.Forms.TextRenderer.DrawText%2A> (méthode).  
  
 [!code-csharp[System.Windows.Forms.TextRendererExamples#7](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.TextRendererExamples/CS/Form1.cs#7)]
 [!code-vb[System.Windows.Forms.TextRendererExamples#7](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.TextRendererExamples/VB/Form1.vb#7)]  
  
 Pour afficher le texte avec le <xref:System.Windows.Forms.TextRenderer> (classe), vous devez un <xref:System.Drawing.IDeviceContext>, comme un <xref:System.Drawing.Graphics> et un <xref:System.Drawing.Font>, un emplacement pour dessiner le texte et la couleur dans laquelle il doit être dessiné. Si vous le souhaitez, vous pouvez spécifier le texte à l’aide de la mise en forme le <xref:System.Windows.Forms.TextFormatFlags> énumération.  
  
 Pour plus d’informations sur l’obtention d’un <xref:System.Drawing.Graphics>, consultez [Comment : Créer des objets graphiques pour le dessin](how-to-create-graphics-objects-for-drawing.md). Pour plus d’informations sur la construction d’un <xref:System.Drawing.Font>, consultez [Comment : Construire des familles de polices et des polices](how-to-construct-font-families-and-fonts.md).  
  
## <a name="compiling-the-code"></a>Compilation du code  
 L’exemple de code précédent est conçu pour une utilisation avec Windows Forms et nécessite le <xref:System.Windows.Forms.PaintEventArgs> `e`, qui est un paramètre de <xref:System.Windows.Forms.PaintEventHandler>.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.TextRenderer>
- <xref:System.Drawing.Font>
- <xref:System.Drawing.Color>
- [Utilisation de polices et de texte](using-fonts-and-text.md)
