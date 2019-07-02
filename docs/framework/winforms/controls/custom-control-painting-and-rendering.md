---
title: Peinture et rendu personnalisés des contrôles
ms.date: 03/30/2017
helpviewer_keywords:
- custom controls [Windows Forms], rendering
- custom controls [Windows Forms], painting
- user controls [Windows Forms], painting
ms.assetid: a09dbf76-0966-4cbf-a66a-2083ba98e068
ms.openlocfilehash: 14abac5678bfffa3cdb61307fd3cb54681c82a99
ms.sourcegitcommit: b1cfd260928d464d91e20121f9bdba7611c94d71
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2019
ms.locfileid: "67506085"
---
# <a name="custom-control-painting-and-rendering"></a>Peinture et rendu personnalisés des contrôles
La peinture personnalisée des contrôles est une des nombreuses tâches complexes facilitées par le .NET Framework. Lorsque vous créez un contrôle personnalisé, vous disposez de nombreuses options concernant l’aspect graphique de votre contrôle. Si vous créez un contrôle qui hérite de la `Control`, vous devez fournir du code qui permet à votre contrôle afficher sa représentation sous forme graphique. Si vous créez un contrôle utilisateur en héritant de la `UserControl`, ou à partir d’un des contrôles Windows Forms, vous pouvez substituer la représentation graphique standard et fournir votre propre code graphique. Si vous souhaitez fournir un rendu personnalisé pour les contrôles constitutifs d’un `UserControl` vous créez, vos options sont plus limitées, tout en autorisant un large éventail de possibilités de graphiques pour vos applications et de contrôles.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Rendu d'un contrôle Windows Forms](rendering-a-windows-forms-control.md)  
 Montre comment programmer la logique qui affiche un contrôle.  
  
 [Contrôles dessinés par l’utilisateur](user-drawn-controls.md)  
 Donne une vue d’ensemble des étapes impliquées dans l’écriture et en remplaçant le code de rendu de votre contrôle.  
  
 [Contrôles constitutifs](constituent-controls.md)  
 Décrit comment implémenter le code de rendu personnalisées pour des contrôles constitutifs dans vos formulaires et contrôles utilisateur.  
  
 [Guide pratique pour Rendre votre contrôle Invisible au moment de l’exécution](how-to-make-your-control-invisible-at-run-time.md)  
 Montre comment utiliser le <xref:System.Windows.Forms.Control.Visible%2A> propriété à masquer et afficher un contrôle.  
  
 [Guide pratique pour Affecter un arrière-plan Transparent à votre contrôle](how-to-give-your-control-a-transparent-background.md)  
 Montre comment utiliser le <xref:System.Windows.Forms.Control.SetStyle%2A> méthode pour créer une couleur d’arrière-plan qui est opaque, transparente ou partiellement transparents.  
  
 [Rendu des contrôles avec les styles visuels](rendering-controls-with-visual-styles.md)  
 Montre comment restituer les contrôles à l’aide de styles visuels dans les systèmes d’exploitation qui les prennent en charge.  
  
## <a name="reference"></a>Référence  
 <xref:System.Windows.Forms.Control>  
 Décrit cette classe et propose des liens vers tous ses membres.  
  
 <xref:System.Windows.Forms.UserControl>  
 Décrit cette classe et propose des liens vers tous ses membres.  
  
 <xref:System.Windows.Forms.Control.OnPaint%2A>  
 Décrit cette méthode.  
  
## <a name="related-sections"></a>Rubriques connexes  
 [Guide pratique pour Créer des objets graphiques pour le dessin](../advanced/how-to-create-graphics-objects-for-drawing.md)  
 Présente la fonctionnalité graphique GDI + dans Visual Studio et fournit des liens vers plus d’informations.  
  
 [Variétés de contrôles personnalisés](varieties-of-custom-controls.md)  
 Décrit les types de contrôles personnalisés que vous pouvez créer.
