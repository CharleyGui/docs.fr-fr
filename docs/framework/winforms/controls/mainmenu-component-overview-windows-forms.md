---
title: Vue d'ensemble du composant MainMenu
ms.date: 03/30/2017
f1_keywords:
- MenuItem
- MainMenu
helpviewer_keywords:
- MainMenu control [Windows Forms], about MainMenu control
- menus
ms.assetid: b41cc5a3-cc59-4996-aa3c-8dd9c17d3c90
ms.openlocfilehash: 8bc35de239429214d6b493b343d1dd6c898f4d37
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745115"
---
# <a name="mainmenu-component-overview-windows-forms"></a>Vue d'ensemble du composant MainMenu (Windows Forms)
> [!IMPORTANT]
> Bien que <xref:System.Windows.Forms.MenuStrip> et <xref:System.Windows.Forms.ContextMenuStrip> remplacent et ajoutent des fonctionnalités aux contrôles <xref:System.Windows.Forms.MainMenu> et <xref:System.Windows.Forms.ContextMenu> des versions précédentes, <xref:System.Windows.Forms.MainMenu> et les <xref:System.Windows.Forms.ContextMenu> sont conservés pour la compatibilité descendante et l’utilisation future si vous le souhaitez.  
  
 Le composant Windows Forms <xref:System.Windows.Forms.MainMenu> affiche un menu au moment de l’exécution. Tous les sous-menus du menu principal et les éléments individuels sont des objets <xref:System.Windows.Forms.MenuItem>.  
  
## <a name="key-properties"></a>Propriétés de clé  
 Un élément de menu peut être désigné comme élément par défaut en affectant à la propriété <xref:System.Windows.Forms.MenuItem.DefaultItem%2A> la valeur `true`. L’élément par défaut s’affiche en gras lorsque l’utilisateur clique sur le menu. La propriété <xref:System.Windows.Forms.MenuItem.Checked%2A> de l’élément de menu est `true` ou `false`, et indique si l’élément de menu est sélectionné. La propriété <xref:System.Windows.Forms.MenuItem.RadioCheck%2A> de l’élément de menu personnalise l’apparence de l’élément sélectionné : si <xref:System.Windows.Forms.MenuItem.RadioCheck%2A> a la valeur `true`, une case d’option apparaît en regard de l’élément. Si <xref:System.Windows.Forms.MenuItem.RadioCheck%2A> est défini sur `false`, une coche apparaît en regard de l’élément.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.MainMenu>
- <xref:System.Windows.Forms.Menu>
- <xref:System.Windows.Forms.MenuItem>
- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ContextMenuStrip>
- [Vue d'ensemble du contrôle MenuStrip](menustrip-control-overview-windows-forms.md)
