---
title: Génération et dessin de courbes
ms.date: 03/30/2017
helpviewer_keywords:
- drawing [Windows Forms], curves
- examples [Windows Forms], drawing curves
- curves [Windows Forms], drawing
ms.assetid: 76e92623-4130-4644-b867-faca58bdb3a2
ms.openlocfilehash: 4c1b0cc6c6f878569fcf0c392f1b6f9683ec8afc
ms.sourcegitcommit: b1cfd260928d464d91e20121f9bdba7611c94d71
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2019
ms.locfileid: "67506101"
---
# <a name="constructing-and-drawing-curves"></a>Génération et dessin de courbes
GDI + prend en charge plusieurs types de courbes : splines de Bézier, des splines cardinales, des arcs et des points de suspension. Une ellipse est définie par son rectangle englobant ; un arc est une partie d’une ellipse définie par un angle de départ et un angle de balayage. Une spline cardinale est définie par un tableau de points et un paramètre de tension, la courbe passe sans heurts par chaque point dans le tableau, et le paramètre tension influence la courbure de la courbe. Une spline de Bézier définie par deux points de terminaison et deux points de contrôle que la courbe ne passe pas par les points de contrôle, mais les points de contrôle influencent la direction et de pliage comme la courbe passe à partir d’un point de terminaison à l’autre.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Guide pratique pour Dessiner des splines cardinales](how-to-draw-cardinal-splines.md)  
 Décrit des splines cardinales et comment les dessiner.  
  
 [Guide pratique pour Dessiner une Spline de Bézier unique](how-to-draw-a-single-bezier-spline.md)  
 Décrit une spline de Bézier et comment dessiner un.  
  
 [Guide pratique pour Dessiner une séquence de Splines de Bézier](how-to-draw-a-sequence-of-bezier-splines.md)  
 Explique comment dessiner plusieurs splines de Bézier dans la séquence.
