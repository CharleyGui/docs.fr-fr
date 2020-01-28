---
title: Graphiques et dessin
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [Windows Forms]
- graphics [Windows Forms], using in Windows Forms
- GDI+, using in managed code
- drawing [Windows Forms]
ms.assetid: 362532c5-1a06-4257-bdc8-723461009ede
ms.openlocfilehash: 10ad18d38c84f6e447601ab6c8bf1a953dabb7cf
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746403"
---
# <a name="graphics-and-drawing-in-windows-forms"></a>Graphiques et dessins dans les Windows Forms
L’common language runtime utilise une implémentation avancée de l’Graphics Device Interface Windows (GDI) appelée GDI+. Avec GDI+, vous pouvez créer des graphiques, dessiner du texte et manipuler des images graphiques en tant qu’objets. GDI+ est conçu pour offrir des performances et une facilité d’utilisation. Vous pouvez utiliser GDI+ pour restituer des images graphiques sur des Windows Forms et des contrôles. Bien que vous ne puissiez pas utiliser GDI+ directement sur Web Forms, vous pouvez afficher des images graphiques via le contrôle serveur Web image.  
  
 Dans cette section, vous trouverez des rubriques qui présentent les notions de base de la programmation GDI+. Bien qu’il ne s’agisse pas d’une référence exhaustive, cette section comprend des informations sur les objets <xref:System.Drawing.Graphics>, <xref:System.Drawing.Pen>, <xref:System.Drawing.Brush>, et <xref:System.Drawing.Color> et explique comment effectuer des tâches telles que dessiner des formes et du texte ou afficher des images. Pour plus d’informations, consultez [référence GDI+](/windows/desktop/gdiplus/-gdiplus-class-gdi-reference).  
  
 Si vous voulez vous lancer et commencer immédiatement, consultez [Bien démarrer avec la programmation graphique](getting-started-with-graphics-programming.md). Elle comporte des rubriques sur l’utilisation de code pour dessiner des lignes, des formes, du texte et d’autres éléments sur les Windows Forms.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Vue d’ensemble des graphismes](graphics-overview-windows-forms.md)  
 Fournit une introduction aux classes managées graphiques.  
  
 [À propos du code managé GDI+](about-gdi-managed-code.md)  
 Fournit des informations sur les classes GDI+ managées.  
  
 [Utilisation de classes graphiques managées](using-managed-graphics-classes.md)  
 Montre comment effectuer diverses tâches à l’aide des classes managées GDI+.  
  
## <a name="reference"></a>Reference  
 <xref:System.Drawing>  
 Donne accès aux fonctionnalités graphiques de base de GDI+.  
  
 <xref:System.Drawing.Drawing2D>  
 Fournit des fonctionnalités graphiques vectorielles et à deux dimensions avancées.  
  
 <xref:System.Drawing.Imaging>  
 Fournit des fonctionnalités d’imagerie GDI+ avancées.  
  
 <xref:System.Drawing.Text>  
 Fournit des fonctionnalités de typographie GDI+ avancées. Les classes dans cet espace de noms peuvent être utilisées pour créer et utiliser des collections de polices.  
  
 <xref:System.Drawing.Printing>  
 Fournit des fonctionnalités d'impression.  
  
## <a name="related-sections"></a>Rubriques connexes  
 [Dessin et rendu personnalisés des contrôles](../controls/custom-control-painting-and-rendering.md)  
 Explique comment fournir du code pour des contrôles de dessin.
