---
title: 'Procédure : remplir des figures ouvertes'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- open figures [Windows Forms], filling
- figures [Windows Forms], filling
ms.assetid: 5a36b0e4-f1f4-46c0-a85a-22ae98491950
ms.openlocfilehash: 6ecea7d3edb0c3e25fb4e69ff12b88019e530021
ms.sourcegitcommit: b1cfd260928d464d91e20121f9bdba7611c94d71
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2019
ms.locfileid: "67506074"
---
# <a name="how-to-fill-open-figures"></a>Procédure : remplir des figures ouvertes
Vous pouvez remplir un chemin d’accès en passant un <xref:System.Drawing.Drawing2D.GraphicsPath> de l’objet à le <xref:System.Drawing.Graphics.FillPath%2A> (méthode). Le <xref:System.Drawing.Graphics.FillPath%2A> méthode remplit le chemin d’accès selon le mode de remplissage (de substitution ou par balayage) actuellement défini pour le chemin d’accès. Si le chemin d’accès comporte des figures ouvertes, le chemin d’accès est rempli comme si ces figures étaient fermées. GDI + ferme une figure en dessinant une ligne droite de son point d’arrivée à son point de départ.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant crée un chemin d’accès qui a une figure ouverte (un arc) et une figure fermée (une ellipse). Le <xref:System.Drawing.Graphics.FillPath%2A> méthode remplit le chemin d’accès selon le mode de remplissage par défaut, qui est <xref:System.Drawing.Drawing2D.FillMode.Alternate>.  
  
 L’illustration suivante montre la sortie de l’exemple de code. Notez que le chemin d’accès est rempli (conformément à <xref:System.Drawing.Drawing2D.FillMode.Alternate>) comme si la figure ouverte était fermée par une ligne droite de son point d’arrivée à son point de départ.  
  
 ![Diagramme qui montre la sortie de la méthode FillPath](./media/how-to-fill-open-figures/fill-path-alternate-mode.png)  
  
 [!code-csharp[System.Drawing.ConstructingDrawingPaths#11](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingPaths/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.ConstructingDrawingPaths#11](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingPaths/VB/Class1.vb#11)]  
  
## <a name="compiling-the-code"></a>Compilation du code  
 L’exemple précédent est conçu pour une utilisation avec Windows Forms et nécessite <xref:System.Windows.Forms.PaintEventArgs> `e`, qui est un paramètre de la <xref:System.Windows.Forms.Control.Paint> Gestionnaire d’événements.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Drawing.Drawing2D.GraphicsPath>
- [Tracés graphiques dans GDI+](graphics-paths-in-gdi.md)
