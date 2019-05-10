---
title: 'Procédure : obtenir des métriques de polices'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- fonts [Windows Forms], obtaining metrics
- font metrics [Windows Forms], obtaining
ms.assetid: ff7c0616-67f7-4fa2-84ee-b8d642f2b09b
ms.openlocfilehash: 438be2ffbff5c4f88ccfef4cad63dbfc71d132d5
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64648269"
---
# <a name="how-to-obtain-font-metrics"></a>Procédure : obtenir des métriques de polices
Le <xref:System.Drawing.FontFamily> classe fournit les méthodes suivantes qui récupèrent diverses métriques pour une combinaison famille/style particulière :  
  
- <xref:System.Drawing.FontFamily.GetEmHeight%2A>(FontStyle)  
  
- <xref:System.Drawing.FontFamily.GetCellAscent%2A>(FontStyle)  
  
- <xref:System.Drawing.FontFamily.GetCellDescent%2A>(FontStyle)  
  
- <xref:System.Drawing.FontFamily.GetLineSpacing%2A>(FontStyle)  
  
 Les nombres retournés par ces méthodes sont en unités de design de police, afin qu’ils soient indépendants de la taille et les unités d’un particulier <xref:System.Drawing.Font> objet.  
  
 L’illustration suivante montre les différentes mesures.  
  
 ![Polices du texte](./media/fontstext7a.png "fontstext7A")  
  
## <a name="example"></a>Exemple  
 L’exemple suivant affiche les métriques pour le style normal de la famille de polices Arial. Le code crée également un <xref:System.Drawing.Font> objet (basé sur la famille Arial) avec la taille de 16 pixels et affiche la métrique (en pixels) pour ce particulier <xref:System.Drawing.Font> objet.  
  
 L’illustration suivante montre la sortie de l’exemple de code.  
  
 ![Fonts Text](./media/csfontstext8.png "csFontsText8")  
  
 Notez les deux premières lignes de sortie dans l’illustration précédente. Le <xref:System.Drawing.Font> objet renvoie une taille de 16 et le <xref:System.Drawing.FontFamily> objet retourne une hauteur de 2 048. Ces deux nombres (16 et 2 048) sont la clé à la conversion entre les unités de design de police et les unités (dans ce cas des pixels) de la <xref:System.Drawing.Font> objet.  
  
 Par exemple, vous pouvez convertir le jambage ascendant à partir d’unités de design pixels comme suit :  
  
 ![Polices du texte](./media/fontstext9.png "FontsText9")  
  
 Le code suivant positionne le texte verticalement en définissant le <xref:System.Drawing.PointF.Y%2A> membre de données d’un <xref:System.Drawing.PointF> objet. La coordonnée y est augmentée `font.Height` pour chaque nouvelle ligne de texte. Le <xref:System.Drawing.Font.Height%2A> propriété d’un <xref:System.Drawing.Font> objet retourne l’interligne (en pixels) pour ce particulier <xref:System.Drawing.Font> objet. Dans cet exemple, le nombre retourné par <xref:System.Drawing.Font.Height%2A> est 19. Notez que cela est le même que le nombre (arrondi à un entier) obtenu en convertissant la métrique d’interligne en pixels.  
  
 Notez que la hauteur du carré cadratin (également appelée taille taille ou em) n’est pas la somme de la hauteur et de la profondeur. La somme de la hauteur et de la profondeur est appelée la hauteur de cellule. La hauteur de cellule moins l’espacement interne est égale à la hauteur du carré cadratin. La hauteur de cellule plus l’espacement externe est égale à l’interligne.  
  
 [!code-csharp[System.Drawing.FontsAndText#71](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.FontsAndText/CS/Class1.cs#71)]
 [!code-vb[System.Drawing.FontsAndText#71](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.FontsAndText/VB/Class1.vb#71)]  
  
## <a name="compiling-the-code"></a>Compilation du code  
 L’exemple précédent est conçu pour une utilisation avec Windows Forms et nécessite <xref:System.Windows.Forms.PaintEventArgs> `e`, qui est un paramètre de <xref:System.Windows.Forms.PaintEventHandler>.  
  
## <a name="see-also"></a>Voir aussi

- [Graphiques et dessins dans Windows Forms](graphics-and-drawing-in-windows-forms.md)
- [Utilisation de polices et de texte](using-fonts-and-text.md)
