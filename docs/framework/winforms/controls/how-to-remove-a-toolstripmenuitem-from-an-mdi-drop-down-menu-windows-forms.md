---
title: 'Comment : supprimer un ToolStripMenuItem d’un menu déroulant MDI'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- menu items [Windows Forms], removing from MDI drop-down menus
- MenuStrip control [Windows Forms], merging
- MenuStrip control [Windows Forms], removing
- MDI [Windows Forms], merging menu items
ms.assetid: bdafe60d-82ee-45bc-97fe-eeefca6e54c1
ms.openlocfilehash: 3198195cf0991734826508aa65818505bf2038c8
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76735851"
---
# <a name="how-to-remove-a-toolstripmenuitem-from-an-mdi-drop-down-menu-windows-forms"></a><span data-ttu-id="a0e8b-102">Comment : supprimer un ToolStripMenuItem d'un menu déroulant MDI (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="a0e8b-102">How to: Remove a ToolStripMenuItem from an MDI Drop-Down Menu (Windows Forms)</span></span>
<span data-ttu-id="a0e8b-103">Dans certaines applications, le type d'une fenêtre enfant d'interface multidocument (MDI) peut être différent de celui de la fenêtre parente MDI.</span><span class="sxs-lookup"><span data-stu-id="a0e8b-103">In some applications, the kind of a multiple-document interface (MDI) child window can be different from the MDI parent window.</span></span> <span data-ttu-id="a0e8b-104">Par exemple, le parent MDI peut être une feuille de calcul et l'enfant MDI un graphique.</span><span class="sxs-lookup"><span data-stu-id="a0e8b-104">For example, the MDI parent might be a spreadsheet, and the MDI child might be a chart.</span></span> <span data-ttu-id="a0e8b-105">Dans ce cas, vous souhaitez mettre à jour le contenu du menu du parent MDI avec le contenu du menu de l'enfant MDI à mesure que des fenêtres enfants MDI de types différents sont activées.</span><span class="sxs-lookup"><span data-stu-id="a0e8b-105">In that case, you want to update the contents of the MDI parent's menu with the contents of the MDI child's menu as MDI child windows of different kinds are activated.</span></span>  
  
 <span data-ttu-id="a0e8b-106">La procédure suivante utilise les propriétés <xref:System.Windows.Forms.Form.IsMdiContainer%2A>, <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A>, <xref:System.Windows.Forms.MergeAction>et <xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A> pour supprimer un élément de menu de la partie déroulante du menu MDI parent.</span><span class="sxs-lookup"><span data-stu-id="a0e8b-106">The following procedure uses the <xref:System.Windows.Forms.Form.IsMdiContainer%2A>, <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A>, <xref:System.Windows.Forms.MergeAction>, and <xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A> properties to remove a menu item from the drop-down part of the MDI parent menu.</span></span> <span data-ttu-id="a0e8b-107">La fermeture de la fenêtre enfant MDI restaure les éléments de menu supprimés dans le menu MDI parent.</span><span class="sxs-lookup"><span data-stu-id="a0e8b-107">Closing the MDI child window restores the removed menu items to the MDI parent menu.</span></span>  
  
### <a name="to-remove-a-menustrip-from-an-mdi-drop-down-menu"></a><span data-ttu-id="a0e8b-108">Pour supprimer un MenuStrip d’un menu déroulant MDI</span><span class="sxs-lookup"><span data-stu-id="a0e8b-108">To remove a MenuStrip from an MDI drop-down menu</span></span>  
  
1. <span data-ttu-id="a0e8b-109">Créez un formulaire et affectez la valeur `true` à sa propriété <xref:System.Windows.Forms.Form.IsMdiContainer%2A>.</span><span class="sxs-lookup"><span data-stu-id="a0e8b-109">Create a form and set its <xref:System.Windows.Forms.Form.IsMdiContainer%2A> property to `true`.</span></span>  
  
2. <span data-ttu-id="a0e8b-110">Ajoutez un <xref:System.Windows.Forms.MenuStrip> à `Form1` et affectez la valeur `true` à la propriété <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A> du <xref:System.Windows.Forms.MenuStrip>.</span><span class="sxs-lookup"><span data-stu-id="a0e8b-110">Add a <xref:System.Windows.Forms.MenuStrip> to `Form1` and set the <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A> property of the <xref:System.Windows.Forms.MenuStrip> to `true`.</span></span>  
  
3. <span data-ttu-id="a0e8b-111">Ajoutez un élément de menu de niveau supérieur au <xref:System.Windows.Forms.MenuStrip> de `Form1` et affectez la valeur `&File` à sa propriété <xref:System.Windows.Forms.Control.Text%2A>.</span><span class="sxs-lookup"><span data-stu-id="a0e8b-111">Add a top-level menu item to the `Form1`<xref:System.Windows.Forms.MenuStrip> and set its <xref:System.Windows.Forms.Control.Text%2A> property to `&File`.</span></span>  
  
4. <span data-ttu-id="a0e8b-112">Ajoutez trois éléments de sous-menu à l’élément de menu `&File` et définissez leurs propriétés <xref:System.Windows.Forms.ToolStripItem.Text%2A> sur `&Open`, `&Import from`et `E&xit`.</span><span class="sxs-lookup"><span data-stu-id="a0e8b-112">Add three submenu items to the `&File` menu item and set their <xref:System.Windows.Forms.ToolStripItem.Text%2A> properties to `&Open`, `&Import from`, and `E&xit`.</span></span>  
  
5. <span data-ttu-id="a0e8b-113">Ajoutez deux éléments de sous-menu à l’élément de sous-menu `&Import from` et définissez leurs propriétés <xref:System.Windows.Forms.ToolStripItem.Text%2A> sur `&Word` et `&Excel`.</span><span class="sxs-lookup"><span data-stu-id="a0e8b-113">Add two submenu items to the `&Import from` submenu item and set their <xref:System.Windows.Forms.ToolStripItem.Text%2A> properties to `&Word` and `&Excel`.</span></span>  
  
6. <span data-ttu-id="a0e8b-114">Ajoutez un formulaire au projet, ajoutez un <xref:System.Windows.Forms.MenuStrip> au formulaire et affectez la valeur `true` à la propriété <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A> du <xref:System.Windows.Forms.MenuStrip> de `Form2`.</span><span class="sxs-lookup"><span data-stu-id="a0e8b-114">Add a form to the project, add a <xref:System.Windows.Forms.MenuStrip> to the form, and set the <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A> property of the `Form2`<xref:System.Windows.Forms.MenuStrip> to `true`.</span></span>  
  
7. <span data-ttu-id="a0e8b-115">Ajoutez un élément de menu de niveau supérieur au <xref:System.Windows.Forms.MenuStrip> de `Form2` et affectez la valeur `&File` à sa propriété <xref:System.Windows.Forms.ToolStripItem.Text%2A>.</span><span class="sxs-lookup"><span data-stu-id="a0e8b-115">Add a top-level menu item to the `Form2`<xref:System.Windows.Forms.MenuStrip> and set its <xref:System.Windows.Forms.ToolStripItem.Text%2A> property to `&File`.</span></span>  
  
8. <span data-ttu-id="a0e8b-116">Ajoutez un élément de sous-menu `&Import from` au menu `&File` de `Form2`et ajoutez un élément de sous-menu `&Word` au menu `&File`.</span><span class="sxs-lookup"><span data-stu-id="a0e8b-116">Add an `&Import from` submenu item to the `&File` menu of `Form2`, and add an `&Word` submenu item to the `&File` menu.</span></span>  
  
9. <span data-ttu-id="a0e8b-117">Définissez les propriétés <xref:System.Windows.Forms.MergeAction> et <xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A> des éléments de menu `Form2` comme indiqué dans le tableau suivant.</span><span class="sxs-lookup"><span data-stu-id="a0e8b-117">Set the <xref:System.Windows.Forms.MergeAction> and <xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A> properties of the `Form2` menu items as shown in the following table.</span></span>  
  
    |<span data-ttu-id="a0e8b-118">Élément de menu Form2</span><span class="sxs-lookup"><span data-stu-id="a0e8b-118">Form2 menu item</span></span>|<span data-ttu-id="a0e8b-119">Valeur MergeAction</span><span class="sxs-lookup"><span data-stu-id="a0e8b-119">MergeAction value</span></span>|<span data-ttu-id="a0e8b-120">Valeur MergeIndex</span><span class="sxs-lookup"><span data-stu-id="a0e8b-120">MergeIndex value</span></span>|  
    |---------------------|-----------------------|----------------------|  
    |<span data-ttu-id="a0e8b-121">File</span><span class="sxs-lookup"><span data-stu-id="a0e8b-121">File</span></span>|<span data-ttu-id="a0e8b-122">MatchOnly</span><span class="sxs-lookup"><span data-stu-id="a0e8b-122">MatchOnly</span></span>|<span data-ttu-id="a0e8b-123">-1</span><span class="sxs-lookup"><span data-stu-id="a0e8b-123">-1</span></span>|  
    |<span data-ttu-id="a0e8b-124">Importer à partir de</span><span class="sxs-lookup"><span data-stu-id="a0e8b-124">Import from</span></span>|<span data-ttu-id="a0e8b-125">MatchOnly</span><span class="sxs-lookup"><span data-stu-id="a0e8b-125">MatchOnly</span></span>|<span data-ttu-id="a0e8b-126">-1</span><span class="sxs-lookup"><span data-stu-id="a0e8b-126">-1</span></span>|  
    |<span data-ttu-id="a0e8b-127">Word</span><span class="sxs-lookup"><span data-stu-id="a0e8b-127">Word</span></span>|<span data-ttu-id="a0e8b-128">Remove</span><span class="sxs-lookup"><span data-stu-id="a0e8b-128">Remove</span></span>|<span data-ttu-id="a0e8b-129">-1</span><span class="sxs-lookup"><span data-stu-id="a0e8b-129">-1</span></span>|  
  
10. <span data-ttu-id="a0e8b-130">Dans `Form1`, créez un gestionnaire d’événements pour l’événement <xref:System.Windows.Forms.Control.Click> de l' <xref:System.Windows.Forms.ToolStripMenuItem>`&Open`.</span><span class="sxs-lookup"><span data-stu-id="a0e8b-130">In `Form1`, create an event handler for the <xref:System.Windows.Forms.Control.Click> event of the `&Open`<xref:System.Windows.Forms.ToolStripMenuItem>.</span></span>  
  
11. <span data-ttu-id="a0e8b-131">Dans le gestionnaire d’événements, insérez du code semblable à l’exemple de code suivant pour créer et afficher les nouvelles instances de `Form2` en tant qu’enfants MDI de `Form1`:</span><span class="sxs-lookup"><span data-stu-id="a0e8b-131">Within the event handler, insert code similar to the following code example to create and display new instances of `Form2` as MDI children of `Form1`:</span></span>  
  
    ```vb  
    Private Sub openToolStripMenuItem_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles openToolStripMenuItem.Click  
        Dim NewMDIChild As New Form2()  
        'Set the parent form of the child window.  
            NewMDIChild.MdiParent = Me  
        'Display the new form.  
            NewMDIChild.Show()  
    End Sub  
    ```  
  
    ```csharp  
    private void openToolStripMenuItem_Click(object sender, EventArgs e)  
    {  
        Form2 newMDIChild = new Form2();  
        // Set the parent form of the child window.  
            newMDIChild.MdiParent = this;  
        // Display the new form.  
            newMDIChild.Show();  
    }  
    ```  
  
12. <span data-ttu-id="a0e8b-132">Insérez du code similaire à l'exemple de code suivant dans le `&Open`<xref:System.Windows.Forms.ToolStripMenuItem> pour inscrire le gestionnaire d'événements.</span><span class="sxs-lookup"><span data-stu-id="a0e8b-132">Place code similar to the following code example in the `&Open`<xref:System.Windows.Forms.ToolStripMenuItem> to register the event handler.</span></span>  
  
    ```vb  
    Private Sub openToolStripMenuItem_Click(sender As Object, e As _  
    EventArgs) Handles openToolStripMenuItem.Click  
    ```  
  
    ```csharp  
    this.openToolStripMenuItem.Click += new _  
    System.EventHandler(this.openToolStripMenuItem_Click);  
    ```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="a0e8b-133">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="a0e8b-133">Compiling the Code</span></span>  
 <span data-ttu-id="a0e8b-134">Cet exemple nécessite :</span><span class="sxs-lookup"><span data-stu-id="a0e8b-134">This example requires:</span></span>  
  
- <span data-ttu-id="a0e8b-135">deux <xref:System.Windows.Forms.Form> contrôles nommés `Form1` et `Form2` ;</span><span class="sxs-lookup"><span data-stu-id="a0e8b-135">Two <xref:System.Windows.Forms.Form> controls named `Form1` and `Form2`.</span></span>  
  
- <span data-ttu-id="a0e8b-136">un contrôle <xref:System.Windows.Forms.MenuStrip> sur `Form1` nommé `menuStrip1` et un contrôle <xref:System.Windows.Forms.MenuStrip> sur `Form2` nommé `menuStrip2` ;</span><span class="sxs-lookup"><span data-stu-id="a0e8b-136">A <xref:System.Windows.Forms.MenuStrip> control on `Form1` named `menuStrip1`, and a <xref:System.Windows.Forms.MenuStrip> control on `Form2` named `menuStrip2`.</span></span>  
  
- <span data-ttu-id="a0e8b-137">des références aux assemblys <xref:System?displayProperty=nameWithType> et <xref:System.Windows.Forms?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="a0e8b-137">References to the <xref:System?displayProperty=nameWithType> and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a0e8b-138">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a0e8b-138">See also</span></span>

- [<span data-ttu-id="a0e8b-139">Guide pratique pour créer des formulaires MDI parents</span><span class="sxs-lookup"><span data-stu-id="a0e8b-139">How to: Create MDI Parent Forms</span></span>](../advanced/how-to-create-mdi-parent-forms.md)
- [<span data-ttu-id="a0e8b-140">Guide pratique pour créer des formulaires MDI enfants</span><span class="sxs-lookup"><span data-stu-id="a0e8b-140">How to: Create MDI Child Forms</span></span>](../advanced/how-to-create-mdi-child-forms.md)
- [<span data-ttu-id="a0e8b-141">Vue d'ensemble du contrôle MenuStrip</span><span class="sxs-lookup"><span data-stu-id="a0e8b-141">MenuStrip Control Overview</span></span>](menustrip-control-overview-windows-forms.md)
