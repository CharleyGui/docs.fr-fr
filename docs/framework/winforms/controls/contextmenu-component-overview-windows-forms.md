---
title: Vue d'ensemble du composant ContextMenu (Windows Forms)
ms.date: 03/30/2017
f1_keywords:
- ContextMenu
helpviewer_keywords:
- ContextMenu component [Windows Forms], about ContextMenu component
- context menus [Windows Forms], ContextMenu component
- shortcut menus [Windows Forms], ContextMenu component
ms.assetid: 49d6398f-d3c4-4679-84fa-1de07b68b05e
ms.openlocfilehash: 6ae7817bc158f30fbf55b5f6228ecdf134d6657d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69962185"
---
# <a name="contextmenu-component-overview-windows-forms"></a>Vue d'ensemble du composant ContextMenu (Windows Forms)
> [!IMPORTANT]
> Bien <xref:System.Windows.Forms.MenuStrip> que <xref:System.Windows.Forms.ContextMenuStrip> et remplacent et ajoutent des <xref:System.Windows.Forms.ContextMenu> fonctionnalités aux contrôles et des <xref:System.Windows.Forms.MainMenu> versions <xref:System.Windows.Forms.ContextMenu> antérieures, et sont conservés pour la <xref:System.Windows.Forms.MainMenu> compatibilité descendante et l’utilisation future si tel est votre choix.  
  
 Avec le composant <xref:System.Windows.Forms.ContextMenu> Windows Forms, vous pouvez fournir aux utilisateurs un menu contextuel facilement accessible des commandes fréquemment utilisées qui sont associées à l’objet sélectionné. Les éléments d’un menu contextuel sont souvent un sous-ensemble des éléments des menus principaux qui apparaissent ailleurs dans l’application. Un utilisateur peut généralement accéder à un menu contextuel en cliquant avec le bouton droit de la souris. Sur Windows Forms, les menus contextuels sont associés à des contrôles.  
  
## <a name="key-properties"></a>Propriétés de clé  
 Vous pouvez associer un menu contextuel à un contrôle en affectant à <xref:System.Windows.Forms.Control.ContextMenu%2A> la propriété du <xref:System.Windows.Forms.ContextMenu> contrôle la valeur du composant. Un menu contextuel unique peut être associé à plusieurs contrôles, mais chaque contrôle ne peut avoir qu’un seul menu contextuel.  
  
 La propriété de clé du <xref:System.Windows.Forms.ContextMenu> composant est la <xref:System.Windows.Forms.Menu.MenuItems%2A> propriété. Vous pouvez ajouter <xref:System.Windows.Forms.MenuItem> <xref:System.Windows.Forms.Menu.MenuItemCollection> des éléments de menu en créant par programmation des objets et en les ajoutant au du menu contextuel. Étant donné que les éléments d’un menu contextuel sont généralement dessinés à partir d’autres menus, vous pouvez ajouter des éléments à un menu contextuel en les copiant le plus souvent.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.ContextMenu>
- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ContextMenuStrip>
