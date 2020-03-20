---
title: 'Comment : ajouter des améliorations aux ToolStripMenuItems'
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
ms.openlocfilehash: 61a79b9bbe101d7bf694240bdffdecee5187adf2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182318"
---
# <a name="how-to-add-enhancements-to-toolstripmenuitems"></a>Comment : ajouter des améliorations aux ToolStripMenuItems
Vous pouvez améliorer la <xref:System.Windows.Forms.MenuStrip> <xref:System.Windows.Forms.ContextMenuStrip> facilité d’utilisation et les contrôles de la manière suivante :  
  
- Ajoutez des points de contrôle pour indiquer si une fonctionnalité est activée ou désactivée, par exemple si une règle est affichée le long de la marge d’une application de traitement de texte, ou pour indiquer quel fichier dans une liste de fichiers est affiché, comme sur un menu **fenêtre.**  
  
- Ajoutez des images qui représentent visuellement les commandes de menu.  
  
- Affichez des touches de raccourci pour fournir une alternative de clavier à la souris pour effectuer des commandes. Par exemple, appuyer sur CTRL-C effectue la commande **Copy.**  
  
- Affichez les touches d’accès pour fournir une alternative de clavier à la souris pour la navigation de menu. Par exemple, appuyer sur ALT-F choisit le menu **Fichier.**  
  
- Afficher les barres de séparateur aux commandes liées au groupe et rendre les menus plus lisibles.  
  
### <a name="to-display-a-check-mark-on-a-menu-command"></a>Pour afficher une marque de contrôle sur une commande de menu  
  
- Définissez <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> sa `true`propriété à .  
  
     Cela définit <xref:System.Windows.Forms.ToolStripMenuItem.CheckState%2A> également `true`la propriété à . Utilisez cette procédure uniquement si vous souhaitez que la commande du menu s’affiche comme vérifiée par défaut, qu’elle soit sélectionnée ou non.  
  
### <a name="to-display-a-check-mark-that-changes-state-with-each-click"></a>Pour afficher une marque de contrôle qui change d’état à chaque clic  
  
- Réglez la <xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A> propriété `true`de la commande du menu à .  
  
### <a name="to-add-an-image-to-a-menu-command"></a>Pour ajouter une image à une commande de menu  
  
- Définissez la propriété <xref:System.Windows.Forms.ToolStripItem.Image%2A> de la commande du menu au nom de l’image. Si <xref:System.Windows.Forms.ToolStripItemDisplayStyle> la propriété de cette <xref:System.Windows.Forms.ToolStripItemDisplayStyle.Text> commande <xref:System.Windows.Forms.ToolStripItemDisplayStyle.None>de menu est réglée ou, l’image ne peut pas être affichée.  
  
> [!NOTE]
> La marge d’image peut également afficher une marque de contrôle si vous le souhaitez. En outre, vous <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> pouvez définir `true`la propriété de l’image à , et l’image apparaîtra avec une bordure éclose autour d’elle au moment de l’exécution.  
  
### <a name="to-display-a-shortcut-key-for-a-menu-command"></a>Pour afficher une clé de raccourci pour une commande de menu  
  
- Réglez la <xref:System.Windows.Forms.ToolStripMenuItem.ShortcutKeys%2A> propriété de la commande du menu à la combinaison de clavier désirée, `true`telle que CTRL-O pour la commande de menu **ouvert,** et définissez la <xref:System.Windows.Forms.ToolStripMenuItem.ShowShortcutKeys%2A> propriété à .  
  
### <a name="to-display-custom-shortcut-keys-for-a-menu-command"></a>Pour afficher des touches de raccourci personnalisées pour une commande de menu  
  
- Réglez la <xref:System.Windows.Forms.ToolStripMenuItem.ShortcutKeyDisplayString%2A> propriété de la commande du menu à la combinaison de clavier désirée, comme CTRL-SHIFT-O plutôt que SHIFT-CTRL-O, et définissez la <xref:System.Windows.Forms.ToolStripMenuItem.ShowShortcutKeys%2A> propriété à `true`.  
  
### <a name="to-display-an-access-key-for-a-menu-command"></a>Pour afficher une clé d’accès pour une commande de menu  
  
- Lorsque vous <xref:System.Windows.Forms.ToolStripItem.Text%2A> définissez la propriété pour la commande du menu, entrez un ampersand (&) avant la lettre que vous souhaitez être souligné comme la clé d’accès. Par exemple, `&Open` la <xref:System.Windows.Forms.ToolStripItem.Text%2A> dactylographie comme propriété d’un élément de menu entraînera une commande de menu qui apparaît sous forme de stylo <u>O.</u>
  
     Pour naviguer jusqu’à cette commande de <xref:System.Windows.Forms.MenuStrip>menu, appuyez sur ALT pour mettre l’accent sur le , et appuyez sur la clé d’accès du nom du menu. Lorsque le menu s’ouvre et affiche des éléments avec des clés d’accès, vous n’avez qu’à appuyer sur la clé d’accès pour sélectionner la commande du menu.  
  
> [!NOTE]
> Évitez de définir les touches d’accès en double, telles que la définition d’ALT-F deux fois dans le même système de menu. L’ordre de sélection des clés d’accès en double ne peut être garanti.  
  
### <a name="to-display-a-separator-bar-between-menu-commands"></a>Pour afficher une barre de séparateur entre les commandes de menu  
  
- Après avoir <xref:System.Windows.Forms.MenuStrip> défini votre et les éléments <xref:System.Windows.Forms.ToolStripItemCollection.AddRange%2A> <xref:System.Windows.Forms.ToolStripItemCollection.Add%2A> qu’il contiendra, <xref:System.Windows.Forms.ToolStripSeparator> utilisez <xref:System.Windows.Forms.MenuStrip> la méthode ou la méthode pour ajouter les commandes et les commandes du menu à l’ordre que vous voulez.  
  
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
