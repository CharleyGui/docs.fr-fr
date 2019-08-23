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
# <a name="how-to-add-enhancements-to-toolstripmenuitems"></a><span data-ttu-id="8570a-102">Procédure : ajouter des améliorations aux ToolStripMenuItems</span><span class="sxs-lookup"><span data-stu-id="8570a-102">How to: Add Enhancements to ToolStripMenuItems</span></span>
<span data-ttu-id="8570a-103">Vous pouvez améliorer la facilité d' <xref:System.Windows.Forms.MenuStrip> utilisation <xref:System.Windows.Forms.ContextMenuStrip> des contrôles et des manières suivantes:</span><span class="sxs-lookup"><span data-stu-id="8570a-103">You can enhance the usability of <xref:System.Windows.Forms.MenuStrip> and <xref:System.Windows.Forms.ContextMenuStrip> controls in the following ways:</span></span>  
  
- <span data-ttu-id="8570a-104">Ajoutez des coches pour indiquer si une fonctionnalité est activée ou désactivée, par exemple si une règle est affichée le long de la marge d’une application de traitement de texte, ou pour indiquer quel fichier dans une liste de fichiers est affiché, par exemple dans un menu **fenêtre** .</span><span class="sxs-lookup"><span data-stu-id="8570a-104">Add check marks to designate whether a feature is turned on or off, such as whether a ruler is displayed along the margin of a word-processing application, or to indicate which file in a list of files is being displayed, such as on a **Window** menu.</span></span>  
  
- <span data-ttu-id="8570a-105">Ajoutez des images qui représentent visuellement des commandes de menu.</span><span class="sxs-lookup"><span data-stu-id="8570a-105">Add images that visually represent menu commands.</span></span>  
  
- <span data-ttu-id="8570a-106">Affichez les touches de raccourci pour fournir une alternative clavier à la souris pour exécuter des commandes.</span><span class="sxs-lookup"><span data-stu-id="8570a-106">Display shortcut keys to provide a keyboard alternative to the mouse for performing commands.</span></span> <span data-ttu-id="8570a-107">Par exemple, si vous appuyez sur CTRL + C, la commande **copier** est exécutée.</span><span class="sxs-lookup"><span data-stu-id="8570a-107">For example, pressing CTRL+C performs the **Copy** command.</span></span>  
  
- <span data-ttu-id="8570a-108">Affichez les touches d’accès pour fournir une alternative clavier à la souris pour la navigation dans les menus.</span><span class="sxs-lookup"><span data-stu-id="8570a-108">Display access keys to provide a keyboard alternative to the mouse for menu navigation.</span></span> <span data-ttu-id="8570a-109">Par exemple, en appuyant sur ALT + F, vous choisissez le menu **fichier** .</span><span class="sxs-lookup"><span data-stu-id="8570a-109">For example, pressing ALT+F chooses the **File** menu.</span></span>  
  
- <span data-ttu-id="8570a-110">Affichez les barres de séparation pour regrouper les commandes associées et rendre les menus plus lisibles.</span><span class="sxs-lookup"><span data-stu-id="8570a-110">Show separator bars to group related commands and make menus more readable.</span></span>  
  
### <a name="to-display-a-check-mark-on-a-menu-command"></a><span data-ttu-id="8570a-111">Pour afficher une coche sur une commande de menu</span><span class="sxs-lookup"><span data-stu-id="8570a-111">To display a check mark on a menu command</span></span>  
  
- <span data-ttu-id="8570a-112">Affectez <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> à `true`sa propriété la valeur.</span><span class="sxs-lookup"><span data-stu-id="8570a-112">Set its <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> property to `true`.</span></span>  
  
     <span data-ttu-id="8570a-113">Cela affecte également à <xref:System.Windows.Forms.ToolStripMenuItem.CheckState%2A> la propriété `true`la valeur.</span><span class="sxs-lookup"><span data-stu-id="8570a-113">This also sets the <xref:System.Windows.Forms.ToolStripMenuItem.CheckState%2A> property to `true`.</span></span> <span data-ttu-id="8570a-114">Utilisez cette procédure uniquement si vous souhaitez que la commande de menu apparaisse comme étant activée par défaut, qu’elle soit ou non sélectionnée.</span><span class="sxs-lookup"><span data-stu-id="8570a-114">Use this procedure only if you want the menu command to appear as checked by default, regardless of whether it is selected.</span></span>  
  
### <a name="to-display-a-check-mark-that-changes-state-with-each-click"></a><span data-ttu-id="8570a-115">Pour afficher une coche qui modifie l’État à chaque clic</span><span class="sxs-lookup"><span data-stu-id="8570a-115">To display a check mark that changes state with each click</span></span>  
  
- <span data-ttu-id="8570a-116">Affectez à `true`la propriété <xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A> de la commande de menu la valeur.</span><span class="sxs-lookup"><span data-stu-id="8570a-116">Set the menu command's <xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A> property to `true`.</span></span>  
  
### <a name="to-add-an-image-to-a-menu-command"></a><span data-ttu-id="8570a-117">Pour ajouter une image à une commande de menu</span><span class="sxs-lookup"><span data-stu-id="8570a-117">To add an image to a menu command</span></span>  
  
- <span data-ttu-id="8570a-118">Définissez la <xref:System.Windows.Forms.ToolStripItem.Image%2A> propriété de la commande de menu sur le nom de l’image.</span><span class="sxs-lookup"><span data-stu-id="8570a-118">Set the menu command's <xref:System.Windows.Forms.ToolStripItem.Image%2A> property to the name of the image.</span></span> <span data-ttu-id="8570a-119">Si la <xref:System.Windows.Forms.ToolStripItemDisplayStyle> propriété de cette commande de menu a la <xref:System.Windows.Forms.ToolStripItemDisplayStyle.Text> valeur <xref:System.Windows.Forms.ToolStripItemDisplayStyle.None>ou, l’image ne peut pas être affichée.</span><span class="sxs-lookup"><span data-stu-id="8570a-119">If the <xref:System.Windows.Forms.ToolStripItemDisplayStyle> property of this menu command is set to <xref:System.Windows.Forms.ToolStripItemDisplayStyle.Text> or <xref:System.Windows.Forms.ToolStripItemDisplayStyle.None>, the image cannot be displayed.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8570a-120">La marge de l’image peut également afficher une coche si vous le souhaitez.</span><span class="sxs-lookup"><span data-stu-id="8570a-120">The image margin can also show a check mark if you so choose.</span></span> <span data-ttu-id="8570a-121">En outre, vous pouvez affecter <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> à `true`la propriété de l’image la valeur, et l’image s’affichera avec une bordure hachurée autour de celle-ci au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="8570a-121">Also, you can set the <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> property of the image to `true`, and the image will appear with a hatched border around it at run time.</span></span>  
  
### <a name="to-display-a-shortcut-key-for-a-menu-command"></a><span data-ttu-id="8570a-122">Pour afficher une touche de raccourci pour une commande de menu</span><span class="sxs-lookup"><span data-stu-id="8570a-122">To display a shortcut key for a menu command</span></span>  
  
- <span data-ttu-id="8570a-123"><xref:System.Windows.Forms.ToolStripMenuItem.ShortcutKeys%2A> Définissez la propriété de la commande de menu sur la combinaison de touches souhaitée, telle que CTRL + O pour la commande de menu **ouvrir** , et affectez à <xref:System.Windows.Forms.ToolStripMenuItem.ShowShortcutKeys%2A> `true`la propriété la valeur.</span><span class="sxs-lookup"><span data-stu-id="8570a-123">Set the menu command's <xref:System.Windows.Forms.ToolStripMenuItem.ShortcutKeys%2A> property to the desired keyboard combination, such as CTRL+O for the **Open** menu command, and set the <xref:System.Windows.Forms.ToolStripMenuItem.ShowShortcutKeys%2A> property to `true`.</span></span>  
  
### <a name="to-display-custom-shortcut-keys-for-a-menu-command"></a><span data-ttu-id="8570a-124">Pour afficher les touches de raccourci personnalisées pour une commande de menu</span><span class="sxs-lookup"><span data-stu-id="8570a-124">To display custom shortcut keys for a menu command</span></span>  
  
- <span data-ttu-id="8570a-125">Définissez la propriété de <xref:System.Windows.Forms.ToolStripMenuItem.ShortcutKeyDisplayString%2A> la commande de menu sur la combinaison de touches souhaitée, telle que Ctrl + Maj + o plutôt que MAJ + CTRL + o, et affectez à `true`la propriété la <xref:System.Windows.Forms.ToolStripMenuItem.ShowShortcutKeys%2A> valeur.</span><span class="sxs-lookup"><span data-stu-id="8570a-125">Set the menu command's <xref:System.Windows.Forms.ToolStripMenuItem.ShortcutKeyDisplayString%2A> property to the desired keyboard combination, such as CTRL+SHIFT+O rather than SHIFT+CTRL+O, and set the <xref:System.Windows.Forms.ToolStripMenuItem.ShowShortcutKeys%2A> property to `true`.</span></span>  
  
### <a name="to-display-an-access-key-for-a-menu-command"></a><span data-ttu-id="8570a-126">Pour afficher une touche d’accès pour une commande de menu</span><span class="sxs-lookup"><span data-stu-id="8570a-126">To display an access key for a menu command</span></span>  
  
- <span data-ttu-id="8570a-127">Lorsque vous définissez la <xref:System.Windows.Forms.ToolStripItem.Text%2A> propriété de la commande de menu, entrez une esperluette (&) avant la lettre que vous souhaitez utiliser comme touche d’accès.</span><span class="sxs-lookup"><span data-stu-id="8570a-127">When you set the <xref:System.Windows.Forms.ToolStripItem.Text%2A> property for the menu command, enter an ampersand (&) before the letter you want to be underlined as the access key.</span></span> <span data-ttu-id="8570a-128">Par exemple, `&Open` <u></u> <xref:System.Windows.Forms.ToolStripItem.Text%2A> si vous tapez comme propriété d’un élément de menu, une commande de menu s’affiche en tant que stylet.</span><span class="sxs-lookup"><span data-stu-id="8570a-128">For example, typing `&Open` as the <xref:System.Windows.Forms.ToolStripItem.Text%2A> property of a menu item will result in a menu command that appears as <u>O</u>pen.</span></span>
  
     <span data-ttu-id="8570a-129">Pour accéder à cette commande de menu, appuyez sur ALT pour activer le <xref:System.Windows.Forms.MenuStrip>, puis appuyez sur la touche d’accès du nom de menu.</span><span class="sxs-lookup"><span data-stu-id="8570a-129">To navigate to this menu command, press ALT to give focus to the <xref:System.Windows.Forms.MenuStrip>, and press the access key of the menu name.</span></span> <span data-ttu-id="8570a-130">Lorsque le menu s’ouvre et affiche des éléments avec des touches d’accès, vous devez simplement appuyer sur la touche d’accès pour sélectionner la commande de menu.</span><span class="sxs-lookup"><span data-stu-id="8570a-130">When the menu opens and shows items with access keys, you only need to press the access key to select the menu command.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8570a-131">Évitez de définir des clés d’accès en double, telles que la définition de ALT + F à deux reprises dans le même système de menu.</span><span class="sxs-lookup"><span data-stu-id="8570a-131">Avoid defining duplicate access keys, such as defining ALT+F twice in the same menu system.</span></span> <span data-ttu-id="8570a-132">L’ordre de sélection des clés d’accès en double ne peut pas être garanti.</span><span class="sxs-lookup"><span data-stu-id="8570a-132">The selection order of duplicate access keys cannot be guaranteed.</span></span>  
  
### <a name="to-display-a-separator-bar-between-menu-commands"></a><span data-ttu-id="8570a-133">Pour afficher une barre de séparation entre les commandes de menu</span><span class="sxs-lookup"><span data-stu-id="8570a-133">To display a separator bar between menu commands</span></span>  
  
- <span data-ttu-id="8570a-134">Une fois que vous <xref:System.Windows.Forms.MenuStrip> avez défini et les éléments qu’il contiendra <xref:System.Windows.Forms.ToolStripItemCollection.AddRange%2A> , <xref:System.Windows.Forms.ToolStripItemCollection.Add%2A> utilisez la méthode ou pour <xref:System.Windows.Forms.MenuStrip> ajouter les <xref:System.Windows.Forms.ToolStripSeparator> commandes de menu et les contrôles au dans l’ordre de votre choix.</span><span class="sxs-lookup"><span data-stu-id="8570a-134">After you define your <xref:System.Windows.Forms.MenuStrip> and the items it will contain, use the <xref:System.Windows.Forms.ToolStripItemCollection.AddRange%2A> or <xref:System.Windows.Forms.ToolStripItemCollection.Add%2A> method to add the menu commands and <xref:System.Windows.Forms.ToolStripSeparator> controls to the <xref:System.Windows.Forms.MenuStrip> in the order you want.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="8570a-135">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8570a-135">See also</span></span>

- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStripMenuItem>
- [<span data-ttu-id="8570a-136">Vue d'ensemble du contrôle MenuStrip</span><span class="sxs-lookup"><span data-stu-id="8570a-136">MenuStrip Control Overview</span></span>](menustrip-control-overview-windows-forms.md)
