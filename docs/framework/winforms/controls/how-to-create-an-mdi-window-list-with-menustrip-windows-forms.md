---
title: 'Comment : créer une liste des fenêtres MDI avec MenuStrip'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- MDI [Windows Forms], creating window lists
- MenuStrip control [Windows Forms], creating window lists
ms.assetid: 04fb414b-811f-4a83-aab6-b4a24646dec5
ms.openlocfilehash: f013c3df2ab5783a22fe2c34402dc53a328cafa2
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76731006"
---
# <a name="how-to-create-an-mdi-window-list-with-menustrip-windows-forms"></a><span data-ttu-id="fd058-102">Comment : créer une liste des fenêtres MDI avec MenuStrip (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="fd058-102">How to: Create an MDI Window List with MenuStrip (Windows Forms)</span></span>
<span data-ttu-id="fd058-103">Utilisez l’interface multidocument (MDI) pour créer des applications qui peuvent ouvrir plusieurs documents en même temps et copier et coller du contenu d’un document à l’autre.</span><span class="sxs-lookup"><span data-stu-id="fd058-103">Use the multiple-document interface (MDI) to create applications that can open several documents at the same time and copy and paste content from one document to the other.</span></span>  
  
 <span data-ttu-id="fd058-104">Cette procédure vous montre comment créer une liste de tous les formulaires enfants actifs dans le menu fenêtre du parent.</span><span class="sxs-lookup"><span data-stu-id="fd058-104">This procedure shows you how to create a list of all the active child forms on the parent's Window menu.</span></span>  
  
### <a name="to-create-an-mdi-window-list-on-a-menustrip"></a><span data-ttu-id="fd058-105">Pour créer une liste de fenêtres MDI sur un MenuStrip</span><span class="sxs-lookup"><span data-stu-id="fd058-105">To create an MDI Window list on a MenuStrip</span></span>  
  
1. <span data-ttu-id="fd058-106">Créez un formulaire et affectez la valeur `true` à sa propriété <xref:System.Windows.Forms.Form.IsMdiContainer%2A>.</span><span class="sxs-lookup"><span data-stu-id="fd058-106">Create a form and set its <xref:System.Windows.Forms.Form.IsMdiContainer%2A> property to `true`.</span></span>  
  
2. <span data-ttu-id="fd058-107">Ajoutez un <xref:System.Windows.Forms.MenuStrip> au formulaire.</span><span class="sxs-lookup"><span data-stu-id="fd058-107">Add a <xref:System.Windows.Forms.MenuStrip> to the form.</span></span>  
  
3. <span data-ttu-id="fd058-108">Ajoutez deux éléments de menu de niveau supérieur au <xref:System.Windows.Forms.MenuStrip> et définissez leurs propriétés <xref:System.Windows.Forms.Control.Text%2A> sur `&File` et `&Window`.</span><span class="sxs-lookup"><span data-stu-id="fd058-108">Add two top-level menu items to the <xref:System.Windows.Forms.MenuStrip> and set their <xref:System.Windows.Forms.Control.Text%2A> properties to `&File` and `&Window`.</span></span>  
  
4. <span data-ttu-id="fd058-109">Ajoutez un élément de sous-menu à l'élément de menu `&File` et affectez la valeur `&Open` à la propriété <xref:System.Windows.Forms.ToolStripItem.Text%2A>.</span><span class="sxs-lookup"><span data-stu-id="fd058-109">Add a submenu item to the `&File` menu item and set its <xref:System.Windows.Forms.ToolStripItem.Text%2A> property to `&Open`.</span></span>  
  
5. <span data-ttu-id="fd058-110">Définissez la propriété <xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A> du <xref:System.Windows.Forms.MenuStrip> sur le <xref:System.Windows.Forms.ToolStripMenuItem>`&Window`.</span><span class="sxs-lookup"><span data-stu-id="fd058-110">Set the <xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A> property of the <xref:System.Windows.Forms.MenuStrip> to the `&Window`<xref:System.Windows.Forms.ToolStripMenuItem>.</span></span>  
  
6. <span data-ttu-id="fd058-111">Ajoutez un formulaire au projet et ajoutez le contrôle de votre choix, tel qu’un autre <xref:System.Windows.Forms.MenuStrip>.</span><span class="sxs-lookup"><span data-stu-id="fd058-111">Add a form to the project and add the control you want to it, such as another <xref:System.Windows.Forms.MenuStrip>.</span></span>  
  
7. <span data-ttu-id="fd058-112">Créez un gestionnaire d'événements pour l'événement <xref:System.Windows.Forms.Control.Click> du <xref:System.Windows.Forms.ToolStripMenuItem> de `&New`.</span><span class="sxs-lookup"><span data-stu-id="fd058-112">Create an event handler for the <xref:System.Windows.Forms.Control.Click> event of the `&New`<xref:System.Windows.Forms.ToolStripMenuItem>.</span></span>  
  
8. <span data-ttu-id="fd058-113">Dans le gestionnaire d’événements, insérez du code semblable au suivant pour créer et afficher les nouvelles instances de `Form2` en tant qu’enfants MDI de `Form1`.</span><span class="sxs-lookup"><span data-stu-id="fd058-113">Within the event handler, insert code similar to the following to create and display new instances of `Form2` as MDI children of `Form1`.</span></span>  
  
    ```vb  
    Private Sub openToolStripMenuItem_Click(ByVal sender As _  
    System.Object, ByVal e As System.EventArgs) Handles _  
    openToolStripMenuItem.Click  
        Dim NewMDIChild As New Form2()  
        'Set the parent form of the child window.  
            NewMDIChild.MdiParent = Me  
        'Display the new form.  
            NewMDIChild.Show()  
    End Sub  
    ```  
  
    ```csharp  
    private void newToolStripMenuItem_Click(object sender, EventArgs e)  
    {  
        Form2 newMDIChild = new Form2();  
        // Set the parent form of the child window.  
            newMDIChild.MdiParent = this;  
        // Display the new form.  
            newMDIChild.Show();  
    }  
    ```  
  
9. <span data-ttu-id="fd058-114">Placez le code comme suit dans le <xref:System.Windows.Forms.ToolStripMenuItem> `&New`pour inscrire le gestionnaire d’événements.</span><span class="sxs-lookup"><span data-stu-id="fd058-114">Place code like the following in the `&New`<xref:System.Windows.Forms.ToolStripMenuItem> to register the event handler.</span></span>  
  
    ```vb  
    Private Sub newToolStripMenuItem_Click(sender As Object, e As _  
    EventArgs) Handles newToolStripMenuItem.Click  
    ```  
  
    ```csharp  
    this.newToolStripMenuItem.Click += new System.EventHandler(this.newToolStripMenuItem_Click);  
    ```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="fd058-115">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="fd058-115">Compiling the Code</span></span>  
 <span data-ttu-id="fd058-116">Cet exemple nécessite :</span><span class="sxs-lookup"><span data-stu-id="fd058-116">This example requires:</span></span>  
  
- <span data-ttu-id="fd058-117">deux <xref:System.Windows.Forms.Form> contrôles nommés `Form1` et `Form2` ;</span><span class="sxs-lookup"><span data-stu-id="fd058-117">Two <xref:System.Windows.Forms.Form> controls named `Form1` and `Form2`.</span></span>  
  
- <span data-ttu-id="fd058-118">un contrôle <xref:System.Windows.Forms.MenuStrip> sur `Form1` nommé `menuStrip1` et un contrôle <xref:System.Windows.Forms.MenuStrip> sur `Form2` nommé `menuStrip2` ;</span><span class="sxs-lookup"><span data-stu-id="fd058-118">A <xref:System.Windows.Forms.MenuStrip> control on `Form1` named `menuStrip1`, and a <xref:System.Windows.Forms.MenuStrip> control on `Form2` named `menuStrip2`.</span></span>  
  
- <span data-ttu-id="fd058-119">des références aux assemblys <xref:System?displayProperty=nameWithType> et <xref:System.Windows.Forms?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="fd058-119">References to the <xref:System?displayProperty=nameWithType> and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fd058-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fd058-120">See also</span></span>

- [<span data-ttu-id="fd058-121">Guide pratique pour créer des formulaires MDI parents</span><span class="sxs-lookup"><span data-stu-id="fd058-121">How to: Create MDI Parent Forms</span></span>](../advanced/how-to-create-mdi-parent-forms.md)
- [<span data-ttu-id="fd058-122">Guide pratique pour créer des formulaires MDI enfants</span><span class="sxs-lookup"><span data-stu-id="fd058-122">How to: Create MDI Child Forms</span></span>](../advanced/how-to-create-mdi-child-forms.md)
- [<span data-ttu-id="fd058-123">MenuStrip, contrôle</span><span class="sxs-lookup"><span data-stu-id="fd058-123">MenuStrip Control</span></span>](menustrip-control-windows-forms.md)
