---
title: 'Comment : altérer des couleurs'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- colors [Windows Forms], transforming with color matrices
- colors [Windows Forms], shearing
ms.assetid: 0a424171-5b8b-45c4-afef-e9720a6c3e22
ms.openlocfilehash: 825e5a90ebb0d9df3b894ce7bd353e917b676939
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79142392"
---
# <a name="how-to-shear-colors"></a>Comment : altérer des couleurs
La tonte augmente ou diminue un composant de couleur d’une quantité proportionnelle à un autre composant de couleur. Par exemple, considérez la transformation où la composante rouge est augmentée de la moitié de la valeur du composant bleu. Dans le cadre d’une telle transformation, la couleur (0,2, 0,5, 1) deviendrait (0,7, 0,5, 1). Le nouveau composant rouge est de 0,2 euro (1/2)(1) à 0,7.  
  
## <a name="example"></a> Exemple  
 L’exemple suivant <xref:System.Drawing.Image> construit un objet à partir du fichier ColorBars4.bmp. Ensuite, le code applique la transformation de cisaillement décrite dans le paragraphe précédent à chaque pixel de l’image.  
  
 L’illustration suivante montre l’image originale à gauche et l’image cisaillement à droite :
  
 ![Deux carrés avec des rayures colorées côte à côte illustrant l’image originale et l’image cisaillement.](./media/how-to-shear-colors/original-image-sheared-image.png)  
  
 Le tableau suivant répertorie les vecteurs de couleur des quatre barres avant et après la transformation de tonte.  
  
|Original|Cisaillée|  
|--------------|-------------|  
|(0, 0, 1, 1)|(0.5, 0, 1, 1)|  
|(0.5, 1, 0.5, 1)|(0.75, 1, 0.5, 1)|  
|(1, 1, 0, 1)|(1, 1, 0, 1)|  
|(0.4, 0.4, 0.4, 1)|(0.6, 0.4, 0.4, 1)|  
  
 [!code-csharp[System.Drawing.Misc3#9](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Misc3/CS/Form1.cs#9)]
 [!code-vb[System.Drawing.Misc3#9](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Misc3/VB/Form1.vb#9)]  
  
## <a name="compiling-the-code"></a>Compilation du code  
 L’exemple précédent est conçu pour une <xref:System.Windows.Forms.PaintEventArgs> `e`utilisation avec Windows Forms, et il nécessite , qui est un paramètre du gestionnaire d’événements. <xref:System.Windows.Forms.Control.Paint> Remplacez-le par `ColorBars.bmp` un nom d’image et un chemin valables sur votre système.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Drawing.Imaging.ColorMatrix>
- <xref:System.Drawing.Imaging.ImageAttributes>
- [Graphiques et dessins dans les Windows Forms](graphics-and-drawing-in-windows-forms.md)
- [Recoloriage des images](recoloring-images.md)
