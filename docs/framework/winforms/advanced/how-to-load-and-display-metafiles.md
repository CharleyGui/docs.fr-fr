---
title: 'Comment : charger et afficher des métafichiers'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- examples [Windows Forms], metafiles
- metafiles [Windows Forms], displaying
ms.assetid: 60af1714-f148-4d85-a739-0557965ffa73
ms.openlocfilehash: 6c17e0b2d023ccf80b0d32301b7ee6765edcae9f
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73424817"
---
# <a name="how-to-load-and-display-metafiles"></a>Comment : charger et afficher des métafichiers
La classe <xref:System.Drawing.Imaging.Metafile>, qui hérite de la classe <xref:System.Drawing.Image>, fournit des méthodes pour l’enregistrement, l’affichage et l’examen d’images vectorielles.  
  
## <a name="example"></a>Exemple  
 Pour afficher une image vectorielle (métafichier) sur l’écran, vous avez besoin d’un objet <xref:System.Drawing.Imaging.Metafile> et d’un objet <xref:System.Drawing.Graphics>. Transmettez le nom d’un fichier (ou d’un flux) à un constructeur <xref:System.Drawing.Imaging.Metafile>. Après avoir créé un objet <xref:System.Drawing.Imaging.Metafile>, transmettez cet objet <xref:System.Drawing.Imaging.Metafile> à la méthode <xref:System.Drawing.Graphics.DrawImage%2A> d’un objet <xref:System.Drawing.Graphics>.  
  
 L’exemple crée un objet <xref:System.Drawing.Imaging.Metafile> à partir d’un fichier EMF (métafichier amélioré), puis dessine l’image avec son angle supérieur gauche à (60, 10).  
  
 L’illustration suivante montre le métafichier dessiné à l’emplacement spécifié.  
  
 ![Capture d’écran montrant la position de l’image.](./media/how-to-load-and-display-metafiles/metafile-drawn-specified-location.png "imageposition2")  
  
 [!code-csharp[System.Drawing.WorkingWithImages#41](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/CS/Class1.cs#41)]
 [!code-vb[System.Drawing.WorkingWithImages#41](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/VB/Class1.vb#41)]  
  
## <a name="compiling-the-code"></a>Compilation du code  
 L’exemple précédent est conçu pour être utilisé avec Windows Forms, et il requiert <xref:System.Windows.Forms.PaintEventArgs> `e`, qui est un paramètre du gestionnaire d’événements <xref:System.Windows.Forms.Control.Paint>.  
  
## <a name="see-also"></a>Voir aussi

- [Utilisation des images, bitmaps, icônes et métafichiers](working-with-images-bitmaps-icons-and-metafiles.md)
