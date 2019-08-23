---
title: 'Procédure : remplir une forme avec une texture d’image'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- images [Windows Forms], using with brushes
- bitmaps [Windows Forms], using texture
- shapes [Windows Forms], filling with images
ms.assetid: 508da5a6-2433-4d2b-9680-eaeae4e96e3b
ms.openlocfilehash: 42c456137f84c6fa657ba5a09727eae052a45376
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69911690"
---
# <a name="how-to-fill-a-shape-with-an-image-texture"></a>Procédure : remplir une forme avec une texture d’image
Vous pouvez remplir une forme fermée avec une texture à l’aide <xref:System.Drawing.Image> de la classe <xref:System.Drawing.TextureBrush> et de la classe.  
  
## <a name="example"></a>Exemples  
 L’exemple suivant remplit une ellipse avec une image. Le code construit un <xref:System.Drawing.Image> objet, puis passe l’adresse de cet <xref:System.Drawing.Image> objet en tant qu’argument à un <xref:System.Drawing.TextureBrush.%23ctor%2A> constructeur. La troisième instruction met à l’échelle l’image, et la quatrième instruction remplit l’ellipse avec des copies répétées de l’image mise à l’échelle.  
  
 Dans le code suivant, la <xref:System.Drawing.TextureBrush.Transform%2A> propriété contient la transformation qui est appliquée à l’image avant qu’elle ne soit dessinée. Supposons que l’image d’origine a une largeur de 640 pixels et une hauteur de 480 pixels. La transformation réduit l’image à 75 × 75 en définissant les valeurs de mise à l’échelle horizontale et verticale.  
  
> [!NOTE]
> Dans l’exemple suivant, la taille de l’image est de 75 × 75 et la taille de l’ellipse est 150 × 250. Étant donné que l’image est plus petite que l’ellipse qu’elle remplit, l’ellipse est en mosaïque avec l’image. La mosaïque signifie que l’image est répétée horizontalement et verticalement jusqu’à ce que la limite de la forme soit atteinte. Pour plus d’informations sur les mosaïques, consultez [procédure: Juxtaposer une forme avec une image](how-to-tile-a-shape-with-an-image.md).  
  
 [!code-csharp[System.Drawing.UsingABrush#21](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingABrush/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.UsingABrush#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingABrush/VB/Class1.vb#21)]  
  
## <a name="compiling-the-code"></a>Compilation du code  
 L’exemple précédent est conçu pour être utilisé avec Windows Forms, et il <xref:System.Windows.Forms.PaintEventArgs> nécessite `e`, qui <xref:System.Windows.Forms.Control.Paint> est un paramètre du gestionnaire d’événements.  
  
## <a name="see-also"></a>Voir aussi

- [Utilisation d'un pinceau pour remplir des formes](using-a-brush-to-fill-shapes.md)
