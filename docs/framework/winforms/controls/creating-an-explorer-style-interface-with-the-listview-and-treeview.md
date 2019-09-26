---
title: 'Procédure pas à pas : création d’une interface de style explorateur avec les contrôles ListView et TreeView à l’aide du concepteur'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Explorer-style applications [Windows Forms], walkthroughs
- TreeView control [Windows Forms], ListView controls used with
- ListView control [Windows Forms], TreeView controls used with
- Explorer-style applications
- TreeView control [Windows Forms], using for explorer-style interface
- ListView control [Windows Forms], explorer style interface
- ListView control [Windows Forms], explorer-style interface
ms.assetid: 9e5e7721-19e2-4890-b273-a43589fe99ff
ms.openlocfilehash: d80f8e3bc729689b274af520bc37fda8417b0407
ms.sourcegitcommit: 56f1d1203d0075a461a10a301459d3aa452f4f47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/25/2019
ms.locfileid: "69658567"
---
# <a name="walkthrough-creating-an-explorer-style-interface-with-the-listview-and-treeview-controls-using-the-designer"></a><span data-ttu-id="b31e4-102">Procédure pas à pas : création d’une interface de style explorateur avec les contrôles ListView et TreeView à l’aide du concepteur</span><span class="sxs-lookup"><span data-stu-id="b31e4-102">Walkthrough: Creating an Explorer Style Interface with the ListView and TreeView Controls Using the Designer</span></span>

<span data-ttu-id="b31e4-103">L’un des avantages de Visual Studio est la possibilité de créer des applications de Windows Forms de qualité professionnelle dans un laps de temps limité.</span><span class="sxs-lookup"><span data-stu-id="b31e4-103">One of the benefits of Visual Studio is the ability to create professional-looking Windows Forms applications in a short of amount of time.</span></span> <span data-ttu-id="b31e4-104">Un scénario courant consiste à créer une interface utilisateur avec des contrôles <xref:System.Windows.Forms.ListView> et <xref:System.Windows.Forms.TreeView> qui ressemble à la fonctionnalité de l’Explorateur Windows des systèmes d’exploitation Windows.</span><span class="sxs-lookup"><span data-stu-id="b31e4-104">A common scenario is creating a user interface (UI) with <xref:System.Windows.Forms.ListView> and <xref:System.Windows.Forms.TreeView> controls that resembles the Windows Explorer feature of Windows operating systems.</span></span> <span data-ttu-id="b31e4-105">L’Explorateur Windows affiche une structure hiérarchique des fichiers et dossiers sur l’ordinateur d’un utilisateur.</span><span class="sxs-lookup"><span data-stu-id="b31e4-105">Windows Explorer displays a hierarchical structure of the files and folders on a user's computer.</span></span>

### <a name="to-create-the-form-containing-a-listview-and-treeview-control"></a><span data-ttu-id="b31e4-106">Pour créer le formulaire contenant un contrôle ListView et TreeView</span><span class="sxs-lookup"><span data-stu-id="b31e4-106">To create the form containing a ListView and TreeView control</span></span>

1. <span data-ttu-id="b31e4-107">Dans le menu **Fichier** , pointez sur **Nouveau**, puis cliquez sur **Projet**.</span><span class="sxs-lookup"><span data-stu-id="b31e4-107">On the **File** menu, point to **New**, and then click **Project**.</span></span>

2. <span data-ttu-id="b31e4-108">Dans la boîte de dialogue **nouveau projet** , procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="b31e4-108">In the **New Project** dialog box, do the following:</span></span>

    1. <span data-ttu-id="b31e4-109">Dans les catégories, choisissez **Visual Basic** ou **visuel C#** .</span><span class="sxs-lookup"><span data-stu-id="b31e4-109">In the categories, choose either **Visual Basic** or **Visual C#**.</span></span>

    2. <span data-ttu-id="b31e4-110">Dans la liste des modèles, choisissez **Windows Forms application**.</span><span class="sxs-lookup"><span data-stu-id="b31e4-110">In the list of templates, choose **Windows Forms Application**.</span></span>

3. <span data-ttu-id="b31e4-111">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="b31e4-111">Click **OK**.</span></span> <span data-ttu-id="b31e4-112">Un nouveau projet de Windows Forms est créé.</span><span class="sxs-lookup"><span data-stu-id="b31e4-112">A new Windows Forms project is created.</span></span>

4. <span data-ttu-id="b31e4-113">Ajoutez un <xref:System.Windows.Forms.SplitContainer> contrôle au formulaire et affectez à <xref:System.Windows.Forms.SplitContainer.Dock%2A> <xref:System.Windows.Forms.DockStyle.Fill>sa propriété la valeur.</span><span class="sxs-lookup"><span data-stu-id="b31e4-113">Add a <xref:System.Windows.Forms.SplitContainer> control to the form and set its <xref:System.Windows.Forms.SplitContainer.Dock%2A> property to <xref:System.Windows.Forms.DockStyle.Fill>.</span></span>

5. <span data-ttu-id="b31e4-114">Ajoutez un <xref:System.Windows.Forms.ImageList> nommé `imageList1` au formulaire et utilisez la fenêtre Propriétés pour ajouter deux images : une image de dossier et une image de document, dans cet ordre.</span><span class="sxs-lookup"><span data-stu-id="b31e4-114">Add an <xref:System.Windows.Forms.ImageList> named `imageList1` to the form and use the Properties window to add two images: a folder image and a document image, in that order.</span></span>

6. <span data-ttu-id="b31e4-115">Ajoutez un <xref:System.Windows.Forms.TreeView> contrôle nommé `treeview1` au formulaire et positionnez-le sur <xref:System.Windows.Forms.SplitContainer> le côté gauche du contrôle.</span><span class="sxs-lookup"><span data-stu-id="b31e4-115">Add a <xref:System.Windows.Forms.TreeView> control named `treeview1` to the form, and position it on the left side of the <xref:System.Windows.Forms.SplitContainer> control.</span></span> <span data-ttu-id="b31e4-116">Dans le fenêtre Propriétés pour `treeView1` , procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="b31e4-116">In the Properties window for `treeView1` do the following:</span></span>

    1. <span data-ttu-id="b31e4-117">Affectez à la propriété <xref:System.Windows.Forms.Control.Dock%2A> la valeur <xref:System.Windows.Forms.DockStyle.Fill>.</span><span class="sxs-lookup"><span data-stu-id="b31e4-117">Set the <xref:System.Windows.Forms.Control.Dock%2A> property to <xref:System.Windows.Forms.DockStyle.Fill>.</span></span>

    2. <span data-ttu-id="b31e4-118">Affectez à la propriété <xref:System.Windows.Forms.TreeView.ImageList%2A> la valeur `imagelist1.`</span><span class="sxs-lookup"><span data-stu-id="b31e4-118">Set the <xref:System.Windows.Forms.TreeView.ImageList%2A> property to `imagelist1.`</span></span>

7. <span data-ttu-id="b31e4-119">Ajoutez un <xref:System.Windows.Forms.ListView> contrôle nommé `listView1` au formulaire et positionnez-le sur <xref:System.Windows.Forms.SplitContainer> le côté droit du contrôle.</span><span class="sxs-lookup"><span data-stu-id="b31e4-119">Add a <xref:System.Windows.Forms.ListView> control named `listView1` to the form, and position it on the right side of the <xref:System.Windows.Forms.SplitContainer> control.</span></span> <span data-ttu-id="b31e4-120">Dans le fenêtre Propriétés pour `listview1` , procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="b31e4-120">In the Properties window for `listview1` do the following:</span></span>

    1. <span data-ttu-id="b31e4-121">Affectez à la propriété <xref:System.Windows.Forms.Control.Dock%2A> la valeur <xref:System.Windows.Forms.DockStyle.Fill>.</span><span class="sxs-lookup"><span data-stu-id="b31e4-121">Set the <xref:System.Windows.Forms.Control.Dock%2A> property to <xref:System.Windows.Forms.DockStyle.Fill>.</span></span>

    2. <span data-ttu-id="b31e4-122">Affectez à la propriété <xref:System.Windows.Forms.ListView.View%2A> la valeur <xref:System.Windows.Forms.View.Details>.</span><span class="sxs-lookup"><span data-stu-id="b31e4-122">Set the <xref:System.Windows.Forms.ListView.View%2A> property to <xref:System.Windows.Forms.View.Details>.</span></span>

    3. <span data-ttu-id="b31e4-123">Ouvrez l’éditeur de collections ColumnHeader en cliquant sur les points![de suspension (bouton de sélection (...) dans le fenêtre Propriétés de](./media/visual-studio-ellipsis-button.png)Visual Studio. <xref:System.Windows.Forms.ListView.Columns%2A> ) dans la propriété **.**</span><span class="sxs-lookup"><span data-stu-id="b31e4-123">Open the ColumnHeader Collection Editor by clicking the ellipses (![The Ellipsis button (...) in the Properties window of Visual Studio.](./media/visual-studio-ellipsis-button.png)) in the <xref:System.Windows.Forms.ListView.Columns%2A> property **.**</span></span> <span data-ttu-id="b31e4-124">Ajoutez trois colonnes et affectez <xref:System.Windows.Forms.ColumnHeader.Text%2A> à `Name`leur propriété `Type`la valeur `Last Modified`, et, respectivement.</span><span class="sxs-lookup"><span data-stu-id="b31e4-124">Add three columns and set their <xref:System.Windows.Forms.ColumnHeader.Text%2A> property to `Name`, `Type`, and `Last Modified`, respectively.</span></span> <span data-ttu-id="b31e4-125">Cliquez sur **OK** pour fermer la boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="b31e4-125">Click **OK** to close the dialog box.</span></span>

    4. <span data-ttu-id="b31e4-126">Affectez à la propriété <xref:System.Windows.Forms.ListView.SmallImageList%2A> la valeur `imageList1.`</span><span class="sxs-lookup"><span data-stu-id="b31e4-126">Set the <xref:System.Windows.Forms.ListView.SmallImageList%2A> property to `imageList1.`</span></span>

8. <span data-ttu-id="b31e4-127">Implémentez le code pour remplir <xref:System.Windows.Forms.TreeView> le avec des nœuds et des sous-nœuds.</span><span class="sxs-lookup"><span data-stu-id="b31e4-127">Implement the code to populate the <xref:System.Windows.Forms.TreeView> with nodes and subnodes.</span></span> <span data-ttu-id="b31e4-128">Ajoutez ce code à la `Form1` classe.</span><span class="sxs-lookup"><span data-stu-id="b31e4-128">Add this code to the `Form1` class.</span></span>

     [!code-csharp[System.Windows.Forms.ExplorerStyleInterface#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/CS/Form1.cs#1)]
     [!code-vb[System.Windows.Forms.ExplorerStyleInterface#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/VB/Form1.vb#1)]

9. <span data-ttu-id="b31e4-129">Étant donné que le code précédent utilise l’espace de noms System.IO, ajoutez l’instruction using ou import appropriée en haut du formulaire.</span><span class="sxs-lookup"><span data-stu-id="b31e4-129">Since the previous code uses the System.IO namespace, add the appropriate using or import statement at the top of the form.</span></span>

     [!code-csharp[System.Windows.Forms.ExplorerStyleInterface#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/CS/Form1.cs#4)]
     [!code-vb[System.Windows.Forms.ExplorerStyleInterface#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/VB/Form1.vb#4)]

10. <span data-ttu-id="b31e4-130">Appelez la méthode de configuration à partir de l’étape précédente dans le constructeur du formulaire <xref:System.Windows.Forms.Form.Load> ou la méthode de gestion d’événements.</span><span class="sxs-lookup"><span data-stu-id="b31e4-130">Call the set-up method from the previous step in the form's constructor or <xref:System.Windows.Forms.Form.Load> event-handling method.</span></span> <span data-ttu-id="b31e4-131">Ajoutez ce code au constructeur de formulaire.</span><span class="sxs-lookup"><span data-stu-id="b31e4-131">Add this code to the form constructor.</span></span>

     [!code-csharp[System.Windows.Forms.ExplorerStyleInterface#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.ExplorerStyleInterface#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/VB/Form1.vb#2)]

11. <span data-ttu-id="b31e4-132">Gérez l' <xref:System.Windows.Forms.TreeView.NodeMouseClick> événement pour `treeview1`et implémentez le **code pour** remplir `listview1` le contenu d’un nœud lorsqu’un utilisateur clique sur un nœud.</span><span class="sxs-lookup"><span data-stu-id="b31e4-132">Handle the <xref:System.Windows.Forms.TreeView.NodeMouseClick> event for `treeview1`**,** and implement the code to populate `listview1` with a node's contents when a node is clicked.</span></span> <span data-ttu-id="b31e4-133">Ajoutez ce code à la `Form1` classe.</span><span class="sxs-lookup"><span data-stu-id="b31e4-133">Add this code to the `Form1` class.</span></span>

     [!code-csharp[System.Windows.Forms.ExplorerStyleInterface#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.ExplorerStyleInterface#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/VB/Form1.vb#3)]

     <span data-ttu-id="b31e4-134">Si vous utilisez C#, assurez-vous que l' <xref:System.Windows.Forms.TreeView.NodeMouseClick> événement est associé à sa méthode de gestion d’événements.</span><span class="sxs-lookup"><span data-stu-id="b31e4-134">If you are using C#, make sure you have the <xref:System.Windows.Forms.TreeView.NodeMouseClick> event associated with its event-handling method.</span></span> <span data-ttu-id="b31e4-135">Ajoutez ce code au constructeur de formulaire.</span><span class="sxs-lookup"><span data-stu-id="b31e4-135">Add this code to the form constructor.</span></span>

     [!code-csharp[System.Windows.Forms.ExplorerStyleInterface#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/CS/Form1.cs#5)]

## <a name="testing-the-application"></a><span data-ttu-id="b31e4-136">Test de l'application</span><span class="sxs-lookup"><span data-stu-id="b31e4-136">Testing the Application</span></span>

<span data-ttu-id="b31e4-137">Vous pouvez maintenant tester le formulaire pour vous assurer qu’il se comporte comme prévu.</span><span class="sxs-lookup"><span data-stu-id="b31e4-137">You can now test the form to make sure it behaves as expected.</span></span>

#### <a name="to-test-the-form"></a><span data-ttu-id="b31e4-138">Pour tester le formulaire</span><span class="sxs-lookup"><span data-stu-id="b31e4-138">To test the form</span></span>

- <span data-ttu-id="b31e4-139">Appuyez sur F5 pour exécuter l'application.</span><span class="sxs-lookup"><span data-stu-id="b31e4-139">Press F5 to run the application.</span></span>

     <span data-ttu-id="b31e4-140">Vous verrez un formulaire fractionné contenant un <xref:System.Windows.Forms.TreeView> contrôle qui affiche le répertoire de votre projet sur le côté gauche, <xref:System.Windows.Forms.ListView> et un contrôle situé à droite avec trois colonnes.</span><span class="sxs-lookup"><span data-stu-id="b31e4-140">You will see a split form containing a <xref:System.Windows.Forms.TreeView> control that displays your project directory on the left side, and a <xref:System.Windows.Forms.ListView> control on the right side with three columns.</span></span> <span data-ttu-id="b31e4-141">Vous pouvez parcourir le <xref:System.Windows.Forms.TreeView> en sélectionnant des nœuds de répertoire, et le <xref:System.Windows.Forms.ListView> est rempli avec le contenu du répertoire sélectionné.</span><span class="sxs-lookup"><span data-stu-id="b31e4-141">You can traverse the <xref:System.Windows.Forms.TreeView> by selecting directory nodes, and the <xref:System.Windows.Forms.ListView> is populated with the contents of the selected directory.</span></span>

## <a name="next-steps"></a><span data-ttu-id="b31e4-142">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="b31e4-142">Next Steps</span></span>

<span data-ttu-id="b31e4-143">Cette application vous donne un exemple de la façon dont vous pouvez <xref:System.Windows.Forms.TreeView> utiliser <xref:System.Windows.Forms.ListView> et les contrôles ensemble.</span><span class="sxs-lookup"><span data-stu-id="b31e4-143">This application gives you an example of a way you can use <xref:System.Windows.Forms.TreeView> and <xref:System.Windows.Forms.ListView> controls together.</span></span> <span data-ttu-id="b31e4-144">Pour plus d’informations sur ces contrôles, consultez les rubriques suivantes :</span><span class="sxs-lookup"><span data-stu-id="b31e4-144">For more information on these controls, see the following topics:</span></span>

- [<span data-ttu-id="b31e4-145">Guide pratique pour Ajouter des informations personnalisées à un contrôle TreeView ou ListView (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="b31e4-145">How to: Add Custom Information to a TreeView or ListView Control (Windows Forms)</span></span>](add-custom-information-to-a-treeview-or-listview-control-wf.md)

- [<span data-ttu-id="b31e4-146">Guide pratique pour Ajouter des fonctionnalités de recherche à un contrôle ListView</span><span class="sxs-lookup"><span data-stu-id="b31e4-146">How to: Add Search Capabilities to a ListView Control</span></span>](how-to-add-search-capabilities-to-a-listview-control.md)

- [<span data-ttu-id="b31e4-147">Guide pratique pour Attacher un menu contextuel à un nœud TreeView</span><span class="sxs-lookup"><span data-stu-id="b31e4-147">How to: Attach a ShortCut Menu to a TreeView Node</span></span>](how-to-attach-a-shortcut-menu-to-a-treeview-node.md)

## <a name="see-also"></a><span data-ttu-id="b31e4-148">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b31e4-148">See also</span></span>

- <xref:System.Windows.Forms.ListView>
- <xref:System.Windows.Forms.TreeView>
- [<span data-ttu-id="b31e4-149">Contrôle ListView</span><span class="sxs-lookup"><span data-stu-id="b31e4-149">ListView Control</span></span>](listview-control-windows-forms.md)
- [<span data-ttu-id="b31e4-150">Guide pratique pour Ajouter et supprimer des nœuds avec le contrôle TreeView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b31e4-150">How to: Add and Remove Nodes with the Windows Forms TreeView Control</span></span>](how-to-add-and-remove-nodes-with-the-windows-forms-treeview-control.md)
- [<span data-ttu-id="b31e4-151">Guide pratique pour Ajouter et supprimer des éléments avec le contrôle ListView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b31e4-151">How to: Add and Remove Items with the Windows Forms ListView Control</span></span>](how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)
- [<span data-ttu-id="b31e4-152">Guide pratique pour Ajouter des colonnes au contrôle ListView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b31e4-152">How to: Add Columns to the Windows Forms ListView Control</span></span>](how-to-add-columns-to-the-windows-forms-listview-control.md)
