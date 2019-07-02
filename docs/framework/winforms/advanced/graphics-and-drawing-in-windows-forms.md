---
title: Graphiques et dessins dans les Windows Forms
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [Windows Forms]
- graphics [Windows Forms], using in Windows Forms
- GDI+, using in managed code
- drawing [Windows Forms]
ms.assetid: 362532c5-1a06-4257-bdc8-723461009ede
ms.openlocfilehash: e110203605c31f90f71c949f81c18ebf464d52eb
ms.sourcegitcommit: b1cfd260928d464d91e20121f9bdba7611c94d71
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2019
ms.locfileid: "67505542"
---
# <a name="graphics-and-drawing-in-windows-forms"></a>Graphiques et dessins dans les Windows Forms
Le common language runtime utilise une implémentation avancée de la Windows GDI Graphics Device Interface () appelée GDI +. Avec GDI +, vous pouvez créer des graphismes, dessiner du texte et manipuler des images graphiques comme des objets. GDI + est conçu pour offrir des performances et facilité d’utilisation. Vous pouvez utiliser GDI + pour restituer des images graphiques sur les Windows Forms et contrôles. Bien que vous ne pouvez pas utiliser GDI + directement sur des Web Forms, vous pouvez afficher des images graphiques via le contrôle serveur Web Image.  
  
 Dans cette section, vous trouverez des rubriques qui présentent les notions fondamentales de programmation GDI +. Bien qu’il ne s’agisse pas d’une référence exhaustive, cette section comprend des informations sur les objets <xref:System.Drawing.Graphics>, <xref:System.Drawing.Pen>, <xref:System.Drawing.Brush>, et <xref:System.Drawing.Color> et explique comment effectuer des tâches telles que dessiner des formes et du texte ou afficher des images. Pour plus d’informations, consultez [référence GDI +](/windows/desktop/gdiplus/-gdiplus-class-gdi-reference).  
  
 Si vous voulez vous lancer et commencer immédiatement, consultez [Bien démarrer avec la programmation graphique](getting-started-with-graphics-programming.md). Elle comporte des rubriques sur l’utilisation de code pour dessiner des lignes, des formes, du texte et d’autres éléments sur les Windows Forms.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Vue d’ensemble des graphiques](graphics-overview-windows-forms.md)  
 Fournit une introduction aux classes managées graphiques.  
  
 [À propos du code managé GDI+](about-gdi-managed-code.md)  
 Fournit des informations sur les classes managées GDI +.  
  
 [Utilisation de classes graphiques managées](using-managed-graphics-classes.md)  
 Montre comment à complète gérer un large éventail de tâches à l’aide de GDI + classes.  
  
## <a name="reference"></a>Référence  
 <xref:System.Drawing>  
 Fournit l’accès aux fonctionnalités graphiques de base GDI +.  
  
 <xref:System.Drawing.Drawing2D>  
 Fournit des fonctionnalités graphiques vectorielles et à deux dimensions avancées.  
  
 <xref:System.Drawing.Imaging>  
 Fournit une fonctionnalité d’image GDI + avancée.  
  
 <xref:System.Drawing.Text>  
 Fournit des fonctionnalités typographiques GDI + avancées. Les classes dans cet espace de noms peuvent être utilisées pour créer et utiliser des collections de polices.  
  
 <xref:System.Drawing.Printing>  
 Fournit des fonctionnalités d'impression.  
  
## <a name="related-sections"></a>Rubriques connexes  
 [Dessin et rendu personnalisés des contrôles](../controls/custom-control-painting-and-rendering.md)  
 Explique comment fournir du code pour des contrôles de dessin.
