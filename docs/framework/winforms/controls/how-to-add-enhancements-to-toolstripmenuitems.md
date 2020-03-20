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
# <a name="how-to-add-enhancements-to-toolstripmenuitems"></a><span data-ttu-id="7afdd-102">Comment : ajouter des améliorations aux ToolStripMenuItems</span><span class="sxs-lookup"><span data-stu-id="7afdd-102">How to: Add Enhancements to ToolStripMenuItems</span></span>
<span data-ttu-id="7afdd-103">Vous pouvez améliorer la <xref:System.Windows.Forms.MenuStrip> <xref:System.Windows.Forms.ContextMenuStrip> facilité d’utilisation et les contrôles de la manière suivante :</span><span class="sxs-lookup"><span data-stu-id="7afdd-103">You can enhance the usability of <xref:System.Windows.Forms.MenuStrip> and <xref:System.Windows.Forms.ContextMenuStrip> controls in the following ways:</span></span>  
  
- <span data-ttu-id="7afdd-104">Ajoutez des points de contrôle pour indiquer si une fonctionnalité est activée ou désactivée, par exemple si une règle est affichée le long de la marge d’une application de traitement de texte, ou pour indiquer quel fichier dans une liste de fichiers est affiché, comme sur un menu **fenêtre.**</span><span class="sxs-lookup"><span data-stu-id="7afdd-104">Add check marks to designate whether a feature is turned on or off, such as whether a ruler is displayed along the margin of a word-processing application, or to indicate which file in a list of files is being displayed, such as on a **Window** menu.</span></span>  
  
- <span data-ttu-id="7afdd-105">Ajoutez des images qui représentent visuellement les commandes de menu.</span><span class="sxs-lookup"><span data-stu-id="7afdd-105">Add images that visually represent menu commands.</span></span>  
  
- <span data-ttu-id="7afdd-106">Affichez des touches de raccourci pour fournir une alternative de clavier à la souris pour effectuer des commandes.</span><span class="sxs-lookup"><span data-stu-id="7afdd-106">Display shortcut keys to provide a keyboard alternative to the mouse for performing commands.</span></span> <span data-ttu-id="7afdd-107">Par exemple, appuyer sur CTRL-C effectue la commande **Copy.**</span><span class="sxs-lookup"><span data-stu-id="7afdd-107">For example, pressing CTRL+C performs the **Copy** command.</span></span>  
  
- <span data-ttu-id="7afdd-108">Affichez les touches d’accès pour fournir une alternative de clavier à la souris pour la navigation de menu.</span><span class="sxs-lookup"><span data-stu-id="7afdd-108">Display access keys to provide a keyboard alternative to the mouse for menu navigation.</span></span> <span data-ttu-id="7afdd-109">Par exemple, appuyer sur ALT-F choisit le menu **Fichier.**</span><span class="sxs-lookup"><span data-stu-id="7afdd-109">For example, pressing ALT+F chooses the **File** menu.</span></span>  
  
- <span data-ttu-id="7afdd-110">Afficher les barres de séparateur aux commandes liées au groupe et rendre les menus plus lisibles.</span><span class="sxs-lookup"><span data-stu-id="7afdd-110">Show separator bars to group related commands and make menus more readable.</span></span>  
  
### <a name="to-display-a-check-mark-on-a-menu-command"></a><span data-ttu-id="7afdd-111">Pour afficher une marque de contrôle sur une commande de menu</span><span class="sxs-lookup"><span data-stu-id="7afdd-111">To display a check mark on a menu command</span></span>  
  
- <span data-ttu-id="7afdd-112">Définissez <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> sa `true`propriété à .</span><span class="sxs-lookup"><span data-stu-id="7afdd-112">Set its <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> property to `true`.</span></span>  
  
     <span data-ttu-id="7afdd-113">Cela définit <xref:System.Windows.Forms.ToolStripMenuItem.CheckState%2A> également `true`la propriété à .</span><span class="sxs-lookup"><span data-stu-id="7afdd-113">This also sets the <xref:System.Windows.Forms.ToolStripMenuItem.CheckState%2A> property to `true`.</span></span> <span data-ttu-id="7afdd-114">Utilisez cette procédure uniquement si vous souhaitez que la commande du menu s’affiche comme vérifiée par défaut, qu’elle soit sélectionnée ou non.</span><span class="sxs-lookup"><span data-stu-id="7afdd-114">Use this procedure only if you want the menu command to appear as checked by default, regardless of whether it is selected.</span></span>  
  
### <a name="to-display-a-check-mark-that-changes-state-with-each-click"></a><span data-ttu-id="7afdd-115">Pour afficher une marque de contrôle qui change d’état à chaque clic</span><span class="sxs-lookup"><span data-stu-id="7afdd-115">To display a check mark that changes state with each click</span></span>  
  
- <span data-ttu-id="7afdd-116">Réglez la <xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A> propriété `true`de la commande du menu à .</span><span class="sxs-lookup"><span data-stu-id="7afdd-116">Set the menu command's <xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A> property to `true`.</span></span>  
  
### <a name="to-add-an-image-to-a-menu-command"></a><span data-ttu-id="7afdd-117">Pour ajouter une image à une commande de menu</span><span class="sxs-lookup"><span data-stu-id="7afdd-117">To add an image to a menu command</span></span>  
  
- <span data-ttu-id="7afdd-118">Définissez la propriété <xref:System.Windows.Forms.ToolStripItem.Image%2A> de la commande du menu au nom de l’image.</span><span class="sxs-lookup"><span data-stu-id="7afdd-118">Set the menu command's <xref:System.Windows.Forms.ToolStripItem.Image%2A> property to the name of the image.</span></span> <span data-ttu-id="7afdd-119">Si <xref:System.Windows.Forms.ToolStripItemDisplayStyle> la propriété de cette <xref:System.Windows.Forms.ToolStripItemDisplayStyle.Text> commande <xref:System.Windows.Forms.ToolStripItemDisplayStyle.None>de menu est réglée ou, l’image ne peut pas être affichée.</span><span class="sxs-lookup"><span data-stu-id="7afdd-119">If the <xref:System.Windows.Forms.ToolStripItemDisplayStyle> property of this menu command is set to <xref:System.Windows.Forms.ToolStripItemDisplayStyle.Text> or <xref:System.Windows.Forms.ToolStripItemDisplayStyle.None>, the image cannot be displayed.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7afdd-120">La marge d’image peut également afficher une marque de contrôle si vous le souhaitez.</span><span class="sxs-lookup"><span data-stu-id="7afdd-120">The image margin can also show a check mark if you so choose.</span></span> <span data-ttu-id="7afdd-121">En outre, vous <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> pouvez définir `true`la propriété de l’image à , et l’image apparaîtra avec une bordure éclose autour d’elle au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="7afdd-121">Also, you can set the <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> property of the image to `true`, and the image will appear with a hatched border around it at run time.</span></span>  
  
### <a name="to-display-a-shortcut-key-for-a-menu-command"></a><span data-ttu-id="7afdd-122">Pour afficher une clé de raccourci pour une commande de menu</span><span class="sxs-lookup"><span data-stu-id="7afdd-122">To display a shortcut key for a menu command</span></span>  
  
- <span data-ttu-id="7afdd-123">Réglez la <xref:System.Windows.Forms.ToolStripMenuItem.ShortcutKeys%2A> propriété de la commande du menu à la combinaison de clavier désirée, `true`telle que CTRL-O pour la commande de menu **ouvert,** et définissez la <xref:System.Windows.Forms.ToolStripMenuItem.ShowShortcutKeys%2A> propriété à .</span><span class="sxs-lookup"><span data-stu-id="7afdd-123">Set the menu command's <xref:System.Windows.Forms.ToolStripMenuItem.ShortcutKeys%2A> property to the desired keyboard combination, such as CTRL+O for the **Open** menu command, and set the <xref:System.Windows.Forms.ToolStripMenuItem.ShowShortcutKeys%2A> property to `true`.</span></span>  
  
### <a name="to-display-custom-shortcut-keys-for-a-menu-command"></a><span data-ttu-id="7afdd-124">Pour afficher des touches de raccourci personnalisées pour une commande de menu</span><span class="sxs-lookup"><span data-stu-id="7afdd-124">To display custom shortcut keys for a menu command</span></span>  
  
- <span data-ttu-id="7afdd-125">Réglez la <xref:System.Windows.Forms.ToolStripMenuItem.ShortcutKeyDisplayString%2A> propriété de la commande du menu à la combinaison de clavier désirée, comme CTRL-SHIFT-O plutôt que SHIFT-CTRL-O, et définissez la <xref:System.Windows.Forms.ToolStripMenuItem.ShowShortcutKeys%2A> propriété à `true`.</span><span class="sxs-lookup"><span data-stu-id="7afdd-125">Set the menu command's <xref:System.Windows.Forms.ToolStripMenuItem.ShortcutKeyDisplayString%2A> property to the desired keyboard combination, such as CTRL+SHIFT+O rather than SHIFT+CTRL+O, and set the <xref:System.Windows.Forms.ToolStripMenuItem.ShowShortcutKeys%2A> property to `true`.</span></span>  
  
### <a name="to-display-an-access-key-for-a-menu-command"></a><span data-ttu-id="7afdd-126">Pour afficher une clé d’accès pour une commande de menu</span><span class="sxs-lookup"><span data-stu-id="7afdd-126">To display an access key for a menu command</span></span>  
  
- <span data-ttu-id="7afdd-127">Lorsque vous <xref:System.Windows.Forms.ToolStripItem.Text%2A> définissez la propriété pour la commande du menu, entrez un ampersand (&) avant la lettre que vous souhaitez être souligné comme la clé d’accès.</span><span class="sxs-lookup"><span data-stu-id="7afdd-127">When you set the <xref:System.Windows.Forms.ToolStripItem.Text%2A> property for the menu command, enter an ampersand (&) before the letter you want to be underlined as the access key.</span></span> <span data-ttu-id="7afdd-128">Par exemple, `&Open` la <xref:System.Windows.Forms.ToolStripItem.Text%2A> dactylographie comme propriété d’un élément de menu entraînera une commande de menu qui apparaît sous forme de stylo <u>O.</u></span><span class="sxs-lookup"><span data-stu-id="7afdd-128">For example, typing `&Open` as the <xref:System.Windows.Forms.ToolStripItem.Text%2A> property of a menu item will result in a menu command that appears as <u>O</u>pen.</span></span>
  
     <span data-ttu-id="7afdd-129">Pour naviguer jusqu’à cette commande de <xref:System.Windows.Forms.MenuStrip>menu, appuyez sur ALT pour mettre l’accent sur le , et appuyez sur la clé d’accès du nom du menu.</span><span class="sxs-lookup"><span data-stu-id="7afdd-129">To navigate to this menu command, press ALT to give focus to the <xref:System.Windows.Forms.MenuStrip>, and press the access key of the menu name.</span></span> <span data-ttu-id="7afdd-130">Lorsque le menu s’ouvre et affiche des éléments avec des clés d’accès, vous n’avez qu’à appuyer sur la clé d’accès pour sélectionner la commande du menu.</span><span class="sxs-lookup"><span data-stu-id="7afdd-130">When the menu opens and shows items with access keys, you only need to press the access key to select the menu command.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7afdd-131">Évitez de définir les touches d’accès en double, telles que la définition d’ALT-F deux fois dans le même système de menu.</span><span class="sxs-lookup"><span data-stu-id="7afdd-131">Avoid defining duplicate access keys, such as defining ALT+F twice in the same menu system.</span></span> <span data-ttu-id="7afdd-132">L’ordre de sélection des clés d’accès en double ne peut être garanti.</span><span class="sxs-lookup"><span data-stu-id="7afdd-132">The selection order of duplicate access keys cannot be guaranteed.</span></span>  
  
### <a name="to-display-a-separator-bar-between-menu-commands"></a><span data-ttu-id="7afdd-133">Pour afficher une barre de séparateur entre les commandes de menu</span><span class="sxs-lookup"><span data-stu-id="7afdd-133">To display a separator bar between menu commands</span></span>  
  
- <span data-ttu-id="7afdd-134">Après avoir <xref:System.Windows.Forms.MenuStrip> défini votre et les éléments <xref:System.Windows.Forms.ToolStripItemCollection.AddRange%2A> <xref:System.Windows.Forms.ToolStripItemCollection.Add%2A> qu’il contiendra, <xref:System.Windows.Forms.ToolStripSeparator> utilisez <xref:System.Windows.Forms.MenuStrip> la méthode ou la méthode pour ajouter les commandes et les commandes du menu à l’ordre que vous voulez.</span><span class="sxs-lookup"><span data-stu-id="7afdd-134">After you define your <xref:System.Windows.Forms.MenuStrip> and the items it will contain, use the <xref:System.Windows.Forms.ToolStripItemCollection.AddRange%2A> or <xref:System.Windows.Forms.ToolStripItemCollection.Add%2A> method to add the menu commands and <xref:System.Windows.Forms.ToolStripSeparator> controls to the <xref:System.Windows.Forms.MenuStrip> in the order you want.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="7afdd-135">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7afdd-135">See also</span></span>

- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStripMenuItem>
- [<span data-ttu-id="7afdd-136">Vue d'ensemble du contrôle MenuStrip</span><span class="sxs-lookup"><span data-stu-id="7afdd-136">MenuStrip Control Overview</span></span>](menustrip-control-overview-windows-forms.md)
