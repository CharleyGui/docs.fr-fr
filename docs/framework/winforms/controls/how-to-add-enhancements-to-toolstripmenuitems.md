---
title: 'Procédure : ajouter des améliorations aux ToolStripMenuItems'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- commands [Windows Forms], grouping on menus
- check marks [Windows Forms], adding to menus
- ToolStripMenuItems [Windows Forms], displaying access keys
- menus [Windows Forms], grouping commands
- menu items [Windows Forms], displaying shortcut keys
- ToolStripMenuItems
- separators [Windows Forms], displaying on menus
- menu items [Windows Forms], showing separators
- menu items [Windows Forms], adding check marks
- ToolStripMenuItems [Windows Forms], adding check marks
- menu items [Windows Forms], adding images
- ToolStripSeparators [Windows Forms], displaying on MenuStrips
- menu items [Windows Forms], displaying access keys
- ToolStripMenuItems [Windows Forms], displaying shortcut keys
- ToolStripMenuItems [Windows Forms], adding images
- keyboard shortcuts [Windows Forms], displaying on menus
- images [Windows Forms], adding to menus
- ToolStripMenuItems [Windows Forms], showing separator bars
ms.assetid: aa5f19bb-b545-4378-bfa6-36ba592f0d7c
ms.openlocfilehash: 9e95c3623bf9bad8395f586392a0557ad1cde880
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69912581"
---
# <a name="how-to-add-enhancements-to-toolstripmenuitems"></a>Procédure : ajouter des améliorations aux ToolStripMenuItems
Vous pouvez améliorer la facilité d' <xref:System.Windows.Forms.MenuStrip> utilisation <xref:System.Windows.Forms.ContextMenuStrip> des contrôles et des manières suivantes:  
  
- Ajoutez des coches pour indiquer si une fonctionnalité est activée ou désactivée, par exemple si une règle est affichée le long de la marge d’une application de traitement de texte, ou pour indiquer quel fichier dans une liste de fichiers est affiché, par exemple dans un menu **fenêtre** .  
  
- Ajoutez des images qui représentent visuellement des commandes de menu.  
  
- Affichez les touches de raccourci pour fournir une alternative clavier à la souris pour exécuter des commandes. Par exemple, si vous appuyez sur CTRL + C, la commande **copier** est exécutée.  
  
- Affichez les touches d’accès pour fournir une alternative clavier à la souris pour la navigation dans les menus. Par exemple, en appuyant sur ALT + F, vous choisissez le menu **fichier** .  
  
- Affichez les barres de séparation pour regrouper les commandes associées et rendre les menus plus lisibles.  
  
### <a name="to-display-a-check-mark-on-a-menu-command"></a>Pour afficher une coche sur une commande de menu  
  
- Affectez <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> à `true`sa propriété la valeur.  
  
     Cela affecte également à <xref:System.Windows.Forms.ToolStripMenuItem.CheckState%2A> la propriété `true`la valeur. Utilisez cette procédure uniquement si vous souhaitez que la commande de menu apparaisse comme étant activée par défaut, qu’elle soit ou non sélectionnée.  
  
### <a name="to-display-a-check-mark-that-changes-state-with-each-click"></a>Pour afficher une coche qui modifie l’État à chaque clic  
  
- Affectez à `true`la propriété <xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A> de la commande de menu la valeur.  
  
### <a name="to-add-an-image-to-a-menu-command"></a>Pour ajouter une image à une commande de menu  
  
- Définissez la <xref:System.Windows.Forms.ToolStripItem.Image%2A> propriété de la commande de menu sur le nom de l’image. Si la <xref:System.Windows.Forms.ToolStripItemDisplayStyle> propriété de cette commande de menu a la <xref:System.Windows.Forms.ToolStripItemDisplayStyle.Text> valeur <xref:System.Windows.Forms.ToolStripItemDisplayStyle.None>ou, l’image ne peut pas être affichée.  
  
> [!NOTE]
> La marge de l’image peut également afficher une coche si vous le souhaitez. En outre, vous pouvez affecter <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> à `true`la propriété de l’image la valeur, et l’image s’affichera avec une bordure hachurée autour de celle-ci au moment de l’exécution.  
  
### <a name="to-display-a-shortcut-key-for-a-menu-command"></a>Pour afficher une touche de raccourci pour une commande de menu  
  
- <xref:System.Windows.Forms.ToolStripMenuItem.ShortcutKeys%2A> Définissez la propriété de la commande de menu sur la combinaison de touches souhaitée, telle que CTRL + O pour la commande de menu **ouvrir** , et affectez à <xref:System.Windows.Forms.ToolStripMenuItem.ShowShortcutKeys%2A> `true`la propriété la valeur.  
  
### <a name="to-display-custom-shortcut-keys-for-a-menu-command"></a>Pour afficher les touches de raccourci personnalisées pour une commande de menu  
  
- Définissez la propriété de <xref:System.Windows.Forms.ToolStripMenuItem.ShortcutKeyDisplayString%2A> la commande de menu sur la combinaison de touches souhaitée, telle que Ctrl + Maj + o plutôt que MAJ + CTRL + o, et affectez à `true`la propriété la <xref:System.Windows.Forms.ToolStripMenuItem.ShowShortcutKeys%2A> valeur.  
  
### <a name="to-display-an-access-key-for-a-menu-command"></a>Pour afficher une touche d’accès pour une commande de menu  
  
- Lorsque vous définissez la <xref:System.Windows.Forms.ToolStripItem.Text%2A> propriété de la commande de menu, entrez une esperluette (&) avant la lettre que vous souhaitez utiliser comme touche d’accès. Par exemple, `&Open` <u></u> <xref:System.Windows.Forms.ToolStripItem.Text%2A> si vous tapez comme propriété d’un élément de menu, une commande de menu s’affiche en tant que stylet.
  
     Pour accéder à cette commande de menu, appuyez sur ALT pour activer le <xref:System.Windows.Forms.MenuStrip>, puis appuyez sur la touche d’accès du nom de menu. Lorsque le menu s’ouvre et affiche des éléments avec des touches d’accès, vous devez simplement appuyer sur la touche d’accès pour sélectionner la commande de menu.  
  
> [!NOTE]
> Évitez de définir des clés d’accès en double, telles que la définition de ALT + F à deux reprises dans le même système de menu. L’ordre de sélection des clés d’accès en double ne peut pas être garanti.  
  
### <a name="to-display-a-separator-bar-between-menu-commands"></a>Pour afficher une barre de séparation entre les commandes de menu  
  
- Une fois que vous <xref:System.Windows.Forms.MenuStrip> avez défini et les éléments qu’il contiendra <xref:System.Windows.Forms.ToolStripItemCollection.AddRange%2A> , <xref:System.Windows.Forms.ToolStripItemCollection.Add%2A> utilisez la méthode ou pour <xref:System.Windows.Forms.MenuStrip> ajouter les <xref:System.Windows.Forms.ToolStripSeparator> commandes de menu et les contrôles au dans l’ordre de votre choix.  
  
    ```vb  
    ' This code adds a top-level File menu to the MenuStrip.  
    Me.menuStrip1.Items.Add(New ToolStripMenuItem() _  
    {Me.fileToolStripMenuItem})  
  
    ' This code adds the New and Open menu commands, a separator bar,   
    ' and the Save and Exit menu commands to the top-level File menu,   
    ' in that order.  
    Me.fileToolStripMenuItem.DropDownItems.AddRange(New _  
    ToolStripMenuItem() {Me.newToolStripMenuItem, _  
    Me.openToolStripMenuItem, Me.toolStripSeparator1, _  
    Me.saveToolStripMenuItem, Me.exitToolStripMenuItem})  
    ```  
  
    ```csharp  
    // This code adds a top-level File menu to the MenuStrip.  
    this.menuStrip1.Items.Add(new ToolStripItem[]_  
    {this.fileToolStripMenuItem});  
  
    // This code adds the New and Open menu commands, a separator bar,   
    // and the Save and Exit menu commands to the top-level File menu,   
    // in that order.  
    this.fileToolStripMenuItem.DropDownItems.AddRange(new _  
    ToolStripItem[] {  
    this.newToolStripMenuItem,  
    this.openToolStripMenuItem,  
    this.toolStripSeparator1,  
    this.saveToolStripMenuItem,  
    this.exitToolStripMenuItem});  
    ```  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStripMenuItem>
- [Vue d'ensemble du contrôle MenuStrip](menustrip-control-overview-windows-forms.md)
