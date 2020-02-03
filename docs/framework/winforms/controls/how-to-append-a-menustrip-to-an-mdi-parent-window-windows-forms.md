---
title: 'Comment : ajouter un MenuStrip à une fenêtre parente MDI'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- MenuStrip control [Windows Forms], merging
- MenuStrip control [Windows Forms], appending
- MDI [Windows Forms], merging menu items
ms.assetid: ab70c936-b452-4653-b417-17be57bb795b
ms.openlocfilehash: 06e5c9daab8b7eb72024fff27d661c0eb3bf84c6
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76747157"
---
# <a name="how-to-append-a-menustrip-to-an-mdi-parent-window-windows-forms"></a><span data-ttu-id="a8ea7-102">Comment : ajouter un MenuStrip à une fenêtre parente MDI (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="a8ea7-102">How to: Append a MenuStrip to an MDI Parent Window (Windows Forms)</span></span>
<span data-ttu-id="a8ea7-103">Dans certaines applications, le type d'une fenêtre enfant d'interface multidocument (MDI) peut être différent de celui de la fenêtre parente MDI.</span><span class="sxs-lookup"><span data-stu-id="a8ea7-103">In some applications, the kind of a multiple-document interface (MDI) child window can be different from the MDI parent window.</span></span> <span data-ttu-id="a8ea7-104">Par exemple, le parent MDI peut être une feuille de calcul et l'enfant MDI un graphique.</span><span class="sxs-lookup"><span data-stu-id="a8ea7-104">For example, the MDI parent might be a spreadsheet, and the MDI child might be a chart.</span></span> <span data-ttu-id="a8ea7-105">Dans ce cas, vous souhaitez mettre à jour le contenu du menu du parent MDI avec le contenu du menu de l'enfant MDI à mesure que des fenêtres enfants MDI de types différents sont activées.</span><span class="sxs-lookup"><span data-stu-id="a8ea7-105">In that case, you want to update the contents of the MDI parent's menu with the contents of the MDI child's menu as MDI child windows of different kinds are activated.</span></span>  
  
 <span data-ttu-id="a8ea7-106">La procédure suivante utilise les propriétés <xref:System.Windows.Forms.Form.IsMdiContainer%2A>, <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A>, <xref:System.Windows.Forms.MergeAction> et <xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A> pour ajouter le menu MDI enfant au menu MDI parent.</span><span class="sxs-lookup"><span data-stu-id="a8ea7-106">The following procedure uses the <xref:System.Windows.Forms.Form.IsMdiContainer%2A>, <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A>, <xref:System.Windows.Forms.MergeAction>, and <xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A> properties to append the MDI child menu to the MDI parent menu.</span></span> <span data-ttu-id="a8ea7-107">La fermeture de la fenêtre MDI enfant supprime le menu ajouté du MDI parent.</span><span class="sxs-lookup"><span data-stu-id="a8ea7-107">Closing the MDI child window removes the appended menu from the MDI parent.</span></span>  
  
 <span data-ttu-id="a8ea7-108">Consultez également [les applications d’interface multidocument (MDI, multiple-document interface)](../advanced/multiple-document-interface-mdi-applications.md).</span><span class="sxs-lookup"><span data-stu-id="a8ea7-108">Also see [Multiple-Document Interface (MDI) Applications](../advanced/multiple-document-interface-mdi-applications.md).</span></span>  
  
### <a name="to-append-a-menu-item-to-an-mdi-parent"></a><span data-ttu-id="a8ea7-109">Pour ajouter un élément à un menu MDI parent</span><span class="sxs-lookup"><span data-stu-id="a8ea7-109">To append a menu item to an MDI parent</span></span>  
  
1. <span data-ttu-id="a8ea7-110">Créez un formulaire et affectez la valeur <xref:System.Windows.Forms.Form.IsMdiContainer%2A> à sa propriété `true`.</span><span class="sxs-lookup"><span data-stu-id="a8ea7-110">Create a form and set its <xref:System.Windows.Forms.Form.IsMdiContainer%2A> property to `true`.</span></span>  
  
2. <span data-ttu-id="a8ea7-111">Ajoutez un <xref:System.Windows.Forms.MenuStrip> à `Form1` et affectez la valeur <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A> à la propriété <xref:System.Windows.Forms.MenuStrip> du `true`.</span><span class="sxs-lookup"><span data-stu-id="a8ea7-111">Add a <xref:System.Windows.Forms.MenuStrip> to `Form1` and set the <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A> property of the <xref:System.Windows.Forms.MenuStrip> to `true`.</span></span>  
  
3. <span data-ttu-id="a8ea7-112">Affectez la valeur <xref:System.Windows.Forms.ToolStripItem.Visible%2A> à la propriété `Form1` du <xref:System.Windows.Forms.MenuStrip> de `false`.</span><span class="sxs-lookup"><span data-stu-id="a8ea7-112">Set the <xref:System.Windows.Forms.ToolStripItem.Visible%2A> property of the `Form1`<xref:System.Windows.Forms.MenuStrip> to `false`.</span></span>  
  
4. <span data-ttu-id="a8ea7-113">Ajoutez un élément de menu de niveau supérieur au `Form1` de <xref:System.Windows.Forms.MenuStrip> et affectez la valeur <xref:System.Windows.Forms.Control.Text%2A> à sa propriété `&File`.</span><span class="sxs-lookup"><span data-stu-id="a8ea7-113">Add a top-level menu item to the `Form1`<xref:System.Windows.Forms.MenuStrip> and set its <xref:System.Windows.Forms.Control.Text%2A> property to `&File`.</span></span>  
  
5. <span data-ttu-id="a8ea7-114">Ajoutez un élément de sous-menu à l'élément de menu `&File` et affectez la valeur <xref:System.Windows.Forms.Form.Text%2A> à la propriété `&Open`.</span><span class="sxs-lookup"><span data-stu-id="a8ea7-114">Add a submenu item to the `&File` menu item and set its <xref:System.Windows.Forms.Form.Text%2A> property to `&Open`.</span></span>  
  
6. <span data-ttu-id="a8ea7-115">Ajoutez un formulaire au projet, ajoutez un <xref:System.Windows.Forms.MenuStrip> au formulaire et affectez la valeur <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A> à la propriété `Form2` du <xref:System.Windows.Forms.MenuStrip> de `true`.</span><span class="sxs-lookup"><span data-stu-id="a8ea7-115">Add a form to the project, add a <xref:System.Windows.Forms.MenuStrip> to the form, and set the <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A> property of the `Form2`<xref:System.Windows.Forms.MenuStrip> to `true`.</span></span>  
  
7. <span data-ttu-id="a8ea7-116">Ajoutez un élément de menu de niveau supérieur au `Form2` de <xref:System.Windows.Forms.MenuStrip> et affectez la valeur <xref:System.Windows.Forms.Form.Text%2A> à sa propriété `&Special`.</span><span class="sxs-lookup"><span data-stu-id="a8ea7-116">Add a top-level menu item to the `Form2`<xref:System.Windows.Forms.MenuStrip> and set its <xref:System.Windows.Forms.Form.Text%2A> property to `&Special`.</span></span>  
  
8. <span data-ttu-id="a8ea7-117">Ajoutez deux éléments de sous-menu à l'élément de menu `&Special` et affectez respectivement les valeurs <xref:System.Windows.Forms.Form.Text%2A> et `Command&1` à leur propriété `Command&2`.</span><span class="sxs-lookup"><span data-stu-id="a8ea7-117">Add two submenu items to the `&Special` menu item and set their <xref:System.Windows.Forms.Form.Text%2A> properties to `Command&1` and `Command&2`, respectively.</span></span>  
  
9. <span data-ttu-id="a8ea7-118">Affectez la valeur <xref:System.Windows.Forms.MergeAction> à la propriété `&Special` des éléments de menu `Command&1`, `Command&2` et <xref:System.Windows.Forms.MergeAction.Append>.</span><span class="sxs-lookup"><span data-stu-id="a8ea7-118">Set the <xref:System.Windows.Forms.MergeAction> property of the `&Special`, `Command&1`, and `Command&2` menu items to <xref:System.Windows.Forms.MergeAction.Append>.</span></span>  
  
10. <span data-ttu-id="a8ea7-119">Créez un gestionnaire d’événements pour l’événement <xref:System.Windows.Forms.Control.Click> de l' <xref:System.Windows.Forms.ToolStripMenuItem>`&Open`.</span><span class="sxs-lookup"><span data-stu-id="a8ea7-119">Create an event handler for the <xref:System.Windows.Forms.Control.Click> event of the `&Open` <xref:System.Windows.Forms.ToolStripMenuItem>.</span></span>  
  
11. <span data-ttu-id="a8ea7-120">Dans le gestionnaire d'événements, insérez du code semblable à l'exemple de code suivant pour créer et afficher de nouvelles instances de `Form2` en tant qu'enfants MDI de `Form1`.</span><span class="sxs-lookup"><span data-stu-id="a8ea7-120">Within the event handler, insert code similar to the following code example to create and display new instances of `Form2` as MDI children of `Form1`.</span></span>  
  
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
  
12. <span data-ttu-id="a8ea7-121">Insérez du code similaire à l'exemple de code suivant dans le `&Open`<xref:System.Windows.Forms.ToolStripMenuItem> pour inscrire le gestionnaire d'événements.</span><span class="sxs-lookup"><span data-stu-id="a8ea7-121">Place code similar to the following code example in the `&Open`<xref:System.Windows.Forms.ToolStripMenuItem> to register the event handler.</span></span>  
  
    ```vb  
    Private Sub openToolStripMenuItem_Click(sender As Object, e As _  
    EventArgs) Handles openToolStripMenuItem.Click  
    ```  
  
    ```csharp  
    this.openToolStripMenuItem.Click += new System.EventHandler(this.openToolStripMenuItem_Click);  
    ```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="a8ea7-122">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="a8ea7-122">Compiling the Code</span></span>  
 <span data-ttu-id="a8ea7-123">Cet exemple nécessite :</span><span class="sxs-lookup"><span data-stu-id="a8ea7-123">This example requires:</span></span>  
  
- <span data-ttu-id="a8ea7-124">deux <xref:System.Windows.Forms.Form> contrôles nommés `Form1` et `Form2` ;</span><span class="sxs-lookup"><span data-stu-id="a8ea7-124">Two <xref:System.Windows.Forms.Form> controls named `Form1` and `Form2`.</span></span>  
  
- <span data-ttu-id="a8ea7-125">un contrôle <xref:System.Windows.Forms.MenuStrip> sur `Form1` nommé `menuStrip1` et un contrôle <xref:System.Windows.Forms.MenuStrip> sur `Form2` nommé `menuStrip2` ;</span><span class="sxs-lookup"><span data-stu-id="a8ea7-125">A <xref:System.Windows.Forms.MenuStrip> control on `Form1` named `menuStrip1`, and a <xref:System.Windows.Forms.MenuStrip> control on `Form2` named `menuStrip2`.</span></span>  
  
- <span data-ttu-id="a8ea7-126">des références aux assemblys <xref:System?displayProperty=nameWithType> et <xref:System.Windows.Forms?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="a8ea7-126">References to the <xref:System?displayProperty=nameWithType> and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>
