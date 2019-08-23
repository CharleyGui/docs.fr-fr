---
title: Vue d'ensemble du composant MainMenu (Windows Forms)
ms.date: 03/30/2017
f1_keywords:
- MenuItem
- MainMenu
helpviewer_keywords:
- MainMenu control [Windows Forms], about MainMenu control
- menus
ms.assetid: b41cc5a3-cc59-4996-aa3c-8dd9c17d3c90
ms.openlocfilehash: fe46683faee13bad951d5a7185aad8a687c290ef
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69952133"
---
# <a name="mainmenu-component-overview-windows-forms"></a>Vue d'ensemble du composant MainMenu (Windows Forms)
> [!IMPORTANT]
> Bien <xref:System.Windows.Forms.MenuStrip> que <xref:System.Windows.Forms.ContextMenuStrip> et remplacent et ajoutent des <xref:System.Windows.Forms.ContextMenu> fonctionnalités aux contrôles et des <xref:System.Windows.Forms.MainMenu> versions <xref:System.Windows.Forms.ContextMenu> antérieures, et sont conservés pour la <xref:System.Windows.Forms.MainMenu> compatibilité descendante et l’utilisation future si tel est votre choix.  
  
 Le composant <xref:System.Windows.Forms.MainMenu> Windows Forms affiche un menu au moment de l’exécution. Tous les sous-menus du menu principal et les éléments individuels <xref:System.Windows.Forms.MenuItem> sont des objets.  
  
## <a name="key-properties"></a>Propriétés de clé  
 Un élément de menu peut être désigné comme élément par défaut en affectant <xref:System.Windows.Forms.MenuItem.DefaultItem%2A> à `true`la propriété la valeur. L’élément par défaut s’affiche en gras lorsque l’utilisateur clique sur le menu. La propriété de l' <xref:System.Windows.Forms.MenuItem.Checked%2A> élément de menu `true` a `false`la valeur ou, et indique si l’élément de menu est sélectionné. <xref:System.Windows.Forms.MenuItem.RadioCheck%2A> La propriété de l’élément de menu personnalise l’apparence de l’élément sélectionné <xref:System.Windows.Forms.MenuItem.RadioCheck%2A> : si a `true`la valeur, une case d’option apparaît en regard `false`de <xref:System.Windows.Forms.MenuItem.RadioCheck%2A> l’élément; si a la valeur, une coche apparaît en regard de l’élément.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.MainMenu>
- <xref:System.Windows.Forms.Menu>
- <xref:System.Windows.Forms.MenuItem>
- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ContextMenuStrip>
- [Vue d'ensemble du contrôle MenuStrip](menustrip-control-overview-windows-forms.md)
