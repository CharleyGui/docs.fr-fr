---
title: Trois catégories de services graphiques
ms.date: 03/30/2017
helpviewer_keywords:
- imaging
- graphics [Windows Forms], categories
- 2D vector graphics
- vector graphics
- typography
ms.assetid: 068c0ef3-f6ee-4d58-a7b6-eb2531ead408
ms.openlocfilehash: fa7391ef0f7170ddb9d9d24aa5a1a03635bf46e0
ms.sourcegitcommit: e48a54ebe62e874500a7043f6ee0b77a744d55b4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/26/2020
ms.locfileid: "80291726"
---
# <a name="three-categories-of-graphics-services"></a>Trois catégories de services graphiques
Les offres graphiques dans Windows Forms se divisent en trois grandes catégories suivantes :  
  
- Graphiques vectoriels bidimensionnels (2-D)  
  
- Images  
  
- Typographie  
  
## <a name="2d-vector-graphics"></a>Graphiques vectoriels 2D  
 Les graphiques vectoriels bidimensionnels, tels que les lignes, les courbes et les figures, sont des primitifs qui sont spécifiés par des ensembles de points sur un système de coordonnées. Par exemple, une ligne droite est spécifiée par ses deux points de terminaison, et un rectangle est spécifié par un point donnant l’emplacement de son coin supérieur gauche et une paire de nombres donnant sa largeur et sa hauteur. Un chemin simple est spécifié par un tableau de points qui sont reliés par des lignes droites. Un éclat bézier est une courbe sophistiquée spécifiée par quatre points de contrôle.  
  
 GDIMD fournit des classes et des structures qui stockent des informations sur les primitifs eux-mêmes, des classes qui stockent des informations sur la façon dont les primitifs seront dessinés, et des classes qui font réellement le dessin. Par exemple, <xref:System.Drawing.Rectangle> la structure stocke l’emplacement et la taille d’un rectangle; la <xref:System.Drawing.Pen> classe stocke des informations sur la couleur de la ligne, la largeur de la ligne et le style de ligne; et <xref:System.Drawing.Graphics> la classe a des méthodes pour dessiner des lignes, des rectangles, des chemins, et d’autres figures. Il ya <xref:System.Drawing.Brush> aussi plusieurs classes qui stockent des informations sur la façon dont les chiffres fermés et les chemins seront remplis de couleurs ou de motifs.  
  
 Vous pouvez enregistrer une image vectorielle, qui est une séquence de commandes graphiques, dans un métaafile. GDIMD fournit <xref:System.Drawing.Imaging.Metafile> la classe pour l’enregistrement, l’affichage et l’enregistrement des métafiles. Avec <xref:System.Drawing.Imaging.MetafileHeader> les <xref:System.Drawing.Imaging.MetaHeader> classes et les classes, vous pouvez inspecter les données stockées dans un en-tête métaafile.  
  
## <a name="imaging"></a>Images  
 Certains types d’images sont difficiles ou impossibles à afficher avec les techniques de graphiques vectoriels. Par exemple, les images sur les boutons de la barre d’outils et les images qui apparaissent sous forme d’icônes sont difficiles à spécifier en tant que collections de lignes et de courbes. Une photographie numérique haute résolution d’un stade de baseball bondé est encore plus difficile à créer avec des techniques vectorielles. Les images de ce type sont stockées sous forme de bitmaps, qui sont des tableaux de nombres qui représentent les couleurs des points individuels à l’écran. GDIMD fournit <xref:System.Drawing.Bitmap> la classe pour l’affichage, la manipulation et l’économie de bitmaps.  
  
## <a name="typography"></a>Typographie  
 La typographie est l’affichage du texte dans une variété de polices, de tailles et de styles. GDIMD apporte un soutien important à cette tâche complexe. L’une des nouvelles fonctionnalités de GDI EST l’antialiasing sous-pixel, qui donne au texte rendu sur un écran LCD une apparence plus lisse.  
  
 En outre, Windows Forms offre la possibilité de <xref:System.Windows.Forms.TextRenderer> dessiner du texte avec des capacités GDI dans sa catégorie.  
  
## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble des graphismes](graphics-overview-windows-forms.md)
- [À propos du code managé GDI+](about-gdi-managed-code.md)
- [Utilisation de classes graphiques managées](using-managed-graphics-classes.md)
