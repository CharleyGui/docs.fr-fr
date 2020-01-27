---
title: Vue d'ensemble des contrôles HScrollBar et VScrollBar
ms.date: 03/30/2017
f1_keywords:
- HScrollBar
- VScrollBar
helpviewer_keywords:
- ScrollBar control [Windows Forms]
- HScrollBar control [Windows Forms], about HScrollBar
- VScrollBar control [Windows Forms], about VScrollBar control
- ScrollBar control [Windows Forms], about ScrollBar control
- scroll bars [Windows Forms], about scroll bars
ms.assetid: 8b307679-1cae-41d8-99aa-3d1efd207cd6
ms.openlocfilehash: abe0c8da9723f17cb80715454f6ab7297724a21f
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76728159"
---
# <a name="hscrollbar-and-vscrollbar-controls-overview-windows-forms"></a>Vue d'ensemble des contrôles HScrollBar et VScrollBar (Windows Forms)
Les contrôles de <xref:System.Windows.Forms.ScrollBar> Windows Forms sont utilisés pour faciliter la navigation dans une longue liste d’éléments ou une grande quantité d’informations en faisant défiler horizontalement ou verticalement l’application ou le contrôle. Les barres de défilement étant un élément courant de l’interface Windows, le contrôle <xref:System.Windows.Forms.ScrollBar> est souvent utilisé avec les contrôles qui ne dérivent pas de la classe <xref:System.Windows.Forms.ScrollableControl>. De même, de nombreux développeurs choisissent d’incorporer le contrôle de <xref:System.Windows.Forms.ScrollBar> lors de la création de leurs propres contrôles utilisateur.  
  
 Les contrôles <xref:System.Windows.Forms.HScrollBar> (horizontal) et <xref:System.Windows.Forms.VScrollBar> (vertical) fonctionnent indépendamment des autres contrôles et ont leur propre ensemble d’événements, de propriétés et de méthodes. les contrôles <xref:System.Windows.Forms.ScrollBar> ne sont pas les mêmes que les barres de défilement intégrées attachées à des zones de texte, des zones de liste, des zones de liste modifiable ou des formulaires MDI (le contrôle <xref:System.Windows.Forms.TextBox> a une propriété <xref:System.Windows.Forms.TextBox.ScrollBars%2A> pour afficher ou masquer les barres de défilement attachées au contrôle).  
  
 Les contrôles <xref:System.Windows.Forms.ScrollBar> utilisent l’événement <xref:System.Windows.Forms.ScrollBar.Scroll> pour surveiller le mouvement de la case de défilement (parfois appelée curseur de défilement) le long de la barre de défilement. L’utilisation de l’événement <xref:System.Windows.Forms.ScrollBar.Scroll> permet d’accéder à la valeur de la barre de défilement au fur et à mesure de son déplacement.  
  
## <a name="value-property"></a>Propriété Value  
 La propriété <xref:System.Windows.Forms.ScrollBar.Value%2A> (qui, par défaut, est 0) est une `integer` valeur correspondant à la position de la case de défilement dans la barre de défilement. Lorsque la position de la case de défilement est à la valeur minimale, elle passe à la position la plus à gauche (pour les barres de défilement horizontales) ou à la position supérieure (pour les barres de défilement verticales). Lorsque la case de défilement est à la valeur maximale, la case de défilement se déplace vers la position la plus à droite ou la plus basse. De même, une valeur à mi-chemin entre le bas et le haut de la plage place le bord de tête de la case de défilement au milieu de la barre de défilement.  
  
 En plus d’utiliser des clics de souris pour modifier la valeur de la barre de défilement, un utilisateur peut également faire glisser la case de défilement jusqu’à n’importe quel point le long de la barre. La valeur résultante dépend de la position de la case de défilement, mais elle est toujours comprise dans la plage des <xref:System.Windows.Forms.ScrollBar.Minimum%2A> à <xref:System.Windows.Forms.ScrollBar.Maximum%2A> propriétés définies par l’utilisateur.  
  
## <a name="largechange-and-smallchange-properties"></a>Propriétés LargeChange et SmallChange  
 Quand l’utilisateur appuie sur la touche PG. suiv ou PG. suiv. ou clique sur le rail de la barre de défilement de chaque côté de la case de défilement, la propriété <xref:System.Windows.Forms.ScrollBar.Value%2A> change en fonction de la valeur définie dans la propriété <xref:System.Windows.Forms.ScrollBar.LargeChange%2A>.  
  
 Quand l’utilisateur appuie sur l’une des touches de direction ou clique sur l’un des boutons de la barre de défilement, la propriété <xref:System.Windows.Forms.ScrollBar.Value%2A> change en fonction de la valeur définie dans la propriété <xref:System.Windows.Forms.ScrollBar.SmallChange%2A>.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.HScrollBar>
- <xref:System.Windows.Forms.VScrollBar>
- [Contrôles à utiliser dans les Windows Forms](controls-to-use-on-windows-forms.md)
