---
title: Fusion alpha de lignes et de remplissages
ms.date: 03/30/2017
helpviewer_keywords:
- lines [Windows Forms], adding transparency
- examples [Windows Forms], alpha blending
- alpha blending [Windows Forms], using with lines
- alpha blending
- lines [Windows Forms], alpha blending
- fills [Windows Forms], alpha blending
- alpha blending [Windows Forms], using with fills
- shapes [Windows Forms], adding transparency
ms.assetid: 5440f48c-3ac9-44c3-b170-c1c110bdbab8
ms.openlocfilehash: 66061341ee6539e2172c537a0b2a6ec9ff87565c
ms.sourcegitcommit: b1cfd260928d464d91e20121f9bdba7611c94d71
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2019
ms.locfileid: "67506118"
---
# <a name="alpha-blending-lines-and-fills"></a>Fusion alpha de lignes et de remplissages
Dans GDI +, une couleur est une valeur 32 bits avec 8 bits pour chaque composant alpha, rouge, vert et bleu. La valeur alpha indique la transparence de la couleur, l’étendue à laquelle la couleur est fusionnée avec la couleur d’arrière-plan. Plage de valeurs alpha comprise entre 0 et 255, où 0 représente une couleur entièrement transparente, et 255 représente une couleur entièrement opaque.  
  
 Fusion alpha est un pixel par pixel de fusion de données de couleur source et d’arrière-plan. Chacun des trois composants (rouge, vert, bleu) d’une couleur de la source donnée est fusionnée avec le composant correspondant de la couleur d’arrière-plan selon la formule suivante :  
  
 displayColor = sourceColor × alpha / 255 + backgroundColor × (255 – alpha) / 255  
  
 Par exemple, supposons que le composant rouge de la couleur de la source est 150 et la composante rouge de la couleur d’arrière-plan est 100. Si la valeur alpha est de 200, le composant rouge de la couleur résultante est calculé comme suit :  
  
 150 × 200 / 255 + 100 × (255 – 200) / 255 = 139  
  
## <a name="in-this-section"></a>Dans cette section  
 [Guide pratique pour Dessiner des lignes opaques et translucides](how-to-draw-opaque-and-semitransparent-lines.md)  
 Montre comment dessiner des lignes à contrôle alpha.  
  
 [Guide pratique pour Dessiner avec des pinceaux opaques et translucides](how-to-draw-with-opaque-and-semitransparent-brushes.md)  
 Explique comment la fusion alpha avec des pinceaux.  
  
 [Guide pratique pour Utiliser le Mode de composition pour commander la fusion Alpha](how-to-use-compositing-mode-to-control-alpha-blending.md)  
 Décrit comment contrôler la fusion alpha utilisant <xref:System.Drawing.Drawing2D.CompositingMode>.  
  
 [Guide pratique pour Utiliser une matrice de couleurs pour définir des valeurs Alpha dans des Images](how-to-use-a-color-matrix-to-set-alpha-values-in-images.md)  
 Explique comment utiliser un <xref:System.Drawing.Imaging.ColorMatrix> objet fusion alpha.
