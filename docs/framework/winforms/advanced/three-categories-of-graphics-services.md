---
title: Trois catégories de services graphiques
ms.date: 03/30/2017
helpviewer_keywords:
- imaging
- graphics [Windows Forms], categories
- 2-D vector graphics
- vector graphics
- typography
ms.assetid: 068c0ef3-f6ee-4d58-a7b6-eb2531ead408
ms.openlocfilehash: a69fa7a1ccad353c879731de05dc47f0d6ae8795
ms.sourcegitcommit: b1cfd260928d464d91e20121f9bdba7611c94d71
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2019
ms.locfileid: "67505231"
---
# <a name="three-categories-of-graphics-services"></a>Trois catégories de services graphiques
Les offres de graphiques dans les Windows Forms se répartissent en trois grandes catégories :  
  
- Graphiques vectoriels en deux dimensions (2D)  
  
- Création d’images  
  
- Typographie  
  
## <a name="2-d-vector-graphics"></a>Graphiques vectoriels en 2D  
 Les graphiques vectoriels en deux dimensions sont des primitives ; tels que des lignes, des courbes et des chiffres. qui sont spécifiées par les ensembles de points sur un système de coordonnées. Par exemple, une ligne droite est spécifiée par ses deux points de terminaison, et un rectangle est spécifié par un point indiquant l’emplacement de son coin supérieur gauche et une paire de valeurs indiquant sa largeur et sa hauteur. Un chemin d’accès simple est spécifié par un tableau de points reliés par des lignes droites. Une spline de Bézier est une courbe sophistiquée spécifiée par quatre points de contrôle.  
  
 GDI + fournit des classes et structures qui stockent des informations sur les primitives elles-mêmes, des classes qui stockent des informations sur la façon dont les primitives seront dessinées et des classes qui effectuent le dessin. Par exemple, le <xref:System.Drawing.Rectangle> structure stocke l’emplacement et la taille d’un rectangle ; le <xref:System.Drawing.Pen> classe stocke des informations sur la couleur de ligne, la largeur de ligne et le style de ligne ; et le <xref:System.Drawing.Graphics> classe a des méthodes pour dessiner des lignes, des rectangles, des chemins d’accès, et autres chiffres. Il existe également plusieurs <xref:System.Drawing.Brush> les classes qui stockent des informations sur la façon de figures fermées et chemins d’accès seront remplis avec les couleurs ou des motifs.  
  
 Vous pouvez enregistrer une image vectorielle, ce qui est une séquence de commandes graphiques, dans un métafichier. GDI + offre la <xref:System.Drawing.Imaging.Metafile> classe pour, afficher, enregistrer des métafichiers. Avec le <xref:System.Drawing.Imaging.MetafileHeader> et <xref:System.Drawing.Imaging.MetaHeader> classes, vous pouvez inspecter les données stockées dans un en-tête de métafichier.  
  
## <a name="imaging"></a>Création d’images  
 Certains types d’images sont difficiles ou impossibles à afficher avec les techniques de graphismes vectoriels. Par exemple, les images sur les boutons de barre d’outils et les images qui apparaissent sous forme d’icônes sont difficiles à spécifier en tant que collections de lignes et de courbes. Une photographie numérique haute résolution d’un stade de football est encore plus difficile de créer avec les techniques de vecteur. Images de ce type sont stockées comme des bitmaps, qui sont des tableaux de nombres qui représentent les couleurs de points individuels sur l’écran. GDI + offre la <xref:System.Drawing.Bitmap> classe pour l’affichage, la manipulation et l’enregistrement de bitmaps.  
  
## <a name="typography"></a>Typographie  
 Typographie est l’affichage du texte dans une variété de polices, tailles et des styles. GDI + fournit la prise en charge complète pour cette tâche complexe. Une des nouvelles fonctionnalités dans GDI + est l’anticrénelage, ce qui donne au texte restitué sur un écran LCD une apparence plus lisse.  
  
 En outre, Windows Forms offre une option permettant de dessiner du texte avec les fonctions GDI dans son <xref:System.Windows.Forms.TextRenderer> classe.  
  
## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble des graphismes](graphics-overview-windows-forms.md)
- [À propos du code managé GDI+](about-gdi-managed-code.md)
- [Utilisation de classes graphiques managées](using-managed-graphics-classes.md)
