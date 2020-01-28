---
title: Concepts de base du développement de contrôles
ms.date: 03/30/2017
helpviewer_keywords:
- custom controls [Windows Forms], derivation types
- programming concepts [Windows Forms], Windows Forms controls
- controls [Windows Forms], creating
ms.assetid: 6277bb81-90f7-4c5b-9f4b-b02bb42dd316
ms.openlocfilehash: fab0a76e2f9fdb7e2f89e9d6a10dd9c522a6d8e1
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76739921"
---
# <a name="windows-forms-control-development-basics"></a>Concepts de base du développement de contrôles Windows Forms
Un contrôle de Windows Forms est une classe qui dérive directement ou indirectement de <xref:System.Windows.Forms.Control?displayProperty=nameWithType>. La liste suivante décrit des scénarios courants pour le développement de contrôles Windows Forms :  
  
- Combinaison de contrôles existants pour créer un contrôle composite.  
  
     Les contrôles composites encapsulent une interface utilisateur qui peut être réutilisée en tant que contrôle. Par exemple, un contrôle composite est un contrôle qui se compose d’une zone de texte et d’un bouton de réinitialisation. Les concepteurs visuels offrent une prise en charge enrichie de la création de contrôles composites. Pour créer un contrôle composite, dérivez de <xref:System.Windows.Forms.UserControl?displayProperty=nameWithType>. La classe de base <xref:System.Windows.Forms.UserControl> fournit le routage du clavier pour les contrôles enfants et permet aux contrôles enfants de fonctionner en tant que groupe. Pour plus d’informations, consultez l’article [Développement d’un contrôle Windows Forms composite](developing-a-composite-windows-forms-control.md).  
  
- Extension d’un contrôle existant pour le personnaliser ou l’ajouter à ses fonctionnalités.  
  
     Un bouton dont la couleur ne peut pas être modifiée et un bouton qui a une propriété supplémentaire qui effectue le suivi du nombre de clics effectués sont des exemples de contrôles étendus. Vous pouvez personnaliser n’importe quel contrôle Windows Forms en le dérivant et en substituant ou en ajoutant des propriétés, des méthodes et des événements.  
  
- Création d’un contrôle qui ne combine pas ou n’étend pas les contrôles existants.  
  
     Dans ce scénario, dérivez votre contrôle à partir de la classe de base <xref:System.Windows.Forms.Control>. Vous pouvez ajouter et remplacer des propriétés, des méthodes et des événements de la classe de base. Pour commencer, consultez [Comment : développer un contrôle de Windows Forms simple](how-to-develop-a-simple-windows-forms-control.md).  
  
 La classe de base pour les contrôles Windows Forms, <xref:System.Windows.Forms.Control>, fournit les éléments nécessaires à l’affichage visuel dans des applications Windows côté client. <xref:System.Windows.Forms.Control> fournit un handle de fenêtre, gère le routage des messages et fournit des événements de souris et de clavier, ainsi que de nombreux autres événements d’interface utilisateur. Il fournit une disposition avancée et possède des propriétés spécifiques à l’affichage visuel, telles que <xref:System.Windows.Forms.Control.ForeColor%2A>, <xref:System.Windows.Forms.Control.BackColor%2A>, <xref:System.Windows.Forms.Control.Height%2A>, <xref:System.Windows.Forms.Control.Width%2A>et bien d’autres. En outre, il assure la sécurité, la prise en charge des threads et l’interopérabilité avec les contrôles ActiveX. Étant donné que la majeure partie de l’infrastructure est fournie par la classe de base, il est relativement facile de développer vos propres contrôles Windows Forms.  
  
## <a name="see-also"></a>Voir aussi

- [Guide pratique pour développer un contrôle Windows Forms simple](how-to-develop-a-simple-windows-forms-control.md)
- [Développement d’un contrôle Windows Forms composite](developing-a-composite-windows-forms-control.md)
- [Guide pratique pour créer un contrôle Windows Forms qui affiche la progression](how-to-create-a-windows-forms-control-that-shows-progress.md)
- [Variétés de contrôles personnalisés](varieties-of-custom-controls.md)
