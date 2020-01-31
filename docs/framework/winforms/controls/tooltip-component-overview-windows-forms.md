---
title: Vue d'ensemble du composant ToolTip
ms.date: 03/30/2017
f1_keywords:
- ToolTip
helpviewer_keywords:
- tooltips [Windows Forms], about tooltips
- ToolTip component [Windows Forms], about ToolTip component
ms.assetid: 3fbc6f08-c882-4acd-a960-a08efe3c7e6e
ms.openlocfilehash: 731f7ad0ce6670000d8c3d3e901e1506f7ef470a
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76741905"
---
# <a name="tooltip-component-overview-windows-forms"></a>Vue d'ensemble du composant ToolTip (Windows Forms)
Le composant Windows Forms <xref:System.Windows.Forms.ToolTip> affiche du texte quand l'utilisateur pointe sur des contrôles. Une info-bulle peut être associée à n'importe quel contrôle. Exemple d’utilisation de ce composant : pour économiser de l’espace sur un formulaire, vous pouvez afficher une petite icône sur un bouton et utiliser une info-bulle pour expliquer la fonction du bouton.  
  
## <a name="working-with-the-tooltip-component"></a>Utilisation du composant ToolTip  
 Un composant <xref:System.Windows.Forms.ToolTip> fournit une propriété `ToolTip` à plusieurs contrôles sur un Windows Form ou un autre conteneur. Par exemple, si vous placez un composant <xref:System.Windows.Forms.ToolTip> sur un formulaire, vous pouvez afficher « tapez votre nom ici » pour un contrôle <xref:System.Windows.Forms.TextBox> et « cliquez ici pour enregistrer les modifications » pour un contrôle <xref:System.Windows.Forms.Button>.  
  
 Les principales méthodes du composant <xref:System.Windows.Forms.ToolTip> sont <xref:System.Windows.Forms.ToolTip.SetToolTip%2A> et <xref:System.Windows.Forms.ToolTip.GetToolTip%2A>. Vous pouvez utiliser la méthode <xref:System.Windows.Forms.ToolTip.SetToolTip%2A> pour définir les info-bulles affichées pour les contrôles. Pour plus d’informations, consultez [Comment : définir des info-bulles pour les contrôles d’un Windows Form au moment du design](how-to-set-tooltips-for-controls-on-a-windows-form-at-design-time.md). Les propriétés de clé sont <xref:System.Windows.Forms.ToolTip.Active%2A>, qui doivent avoir la valeur `true` pour que l’info-bulle s’affiche, et <xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A>, qui définit la durée d’affichage de la chaîne d’info-bulle, la durée pendant laquelle l’utilisateur doit pointer sur le contrôle pour que l’info-bulle s’affiche, et le temps nécessaire pour que les fenêtres d’info-bulle suivantes s’affichent. Pour plus d’informations, consultez [Comment : modifier le délai du composant Windows Forms info-bulle](how-to-change-the-delay-of-the-windows-forms-tooltip-component.md).  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.ToolTip>
- [Guide pratique pour définir des info-bulles pour les contrôles d'un Windows Form au moment du design](how-to-set-tooltips-for-controls-on-a-windows-form-at-design-time.md)
- [Guide pratique pour modifier la durée avant affichage du composant ToolTip Windows Forms](how-to-change-the-delay-of-the-windows-forms-tooltip-component.md)
