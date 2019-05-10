---
title: 'Procédure : vérifier que la ligne sélectionnée dans une table enfant reste à la bonne position'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- master-details view
- row position [Windows Forms]
- parent/child view [Windows Forms]
- resetting child position
- data binding [.NET Framework], row selection
- caching [.NET Framework], child position
- child position
- master/details view [Windows Forms]
- child tables row selection
- current child position
ms.assetid: c5fa2562-43a4-46fa-a604-52d8526a87bd
ms.openlocfilehash: bbebd9f040c60016305a861abee3723450a7456b
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64651979"
---
# <a name="how-to-ensure-the-selected-row-in-a-child-table-remains-at-the-correct-position"></a><span data-ttu-id="4d203-102">Procédure : vérifier que la ligne sélectionnée dans une table enfant reste à la bonne position</span><span class="sxs-lookup"><span data-stu-id="4d203-102">How to: Ensure the Selected Row in a Child Table Remains at the Correct Position</span></span>
<span data-ttu-id="4d203-103">Souvent, lors de l’utilisation de la liaison de données dans des Windows Forms, vous affichez des données dans ce que l’on appelle une vue parent/enfant ou maître/détails.</span><span class="sxs-lookup"><span data-stu-id="4d203-103">Oftentimes when you work with data binding in Windows Forms, you will display data in what is called a parent/child or master/details view.</span></span> <span data-ttu-id="4d203-104">Cela fait référence à un scénario de liaison de données où les données de la même source sont affichées dans deux contrôles.</span><span class="sxs-lookup"><span data-stu-id="4d203-104">This refers to a data-binding scenario where data from the same source is displayed in two controls.</span></span> <span data-ttu-id="4d203-105">La modification de la sélection dans un contrôle entraîne la modification des données affichées dans le deuxième contrôle.</span><span class="sxs-lookup"><span data-stu-id="4d203-105">Changing the selection in one control causes the data displayed in the second control to change.</span></span> <span data-ttu-id="4d203-106">Par exemple, le premier contrôle peut contenir une liste de clients et le second une liste de commandes associées au client sélectionné dans le premier contrôle.</span><span class="sxs-lookup"><span data-stu-id="4d203-106">For example, the first control might contain a list of customers and the second a list of orders related to the selected customer in the first control.</span></span>  
  
 <span data-ttu-id="4d203-107">À compter de .NET Framework version 2.0, quand vous affichez des données dans une vue parent/enfant, vous devrez peut-être effectuer des étapes supplémentaires pour vous assurer que la ligne actuellement sélectionnée dans la table enfant n'est pas réinitialisée à la première ligne de la table.</span><span class="sxs-lookup"><span data-stu-id="4d203-107">Starting with the .NET Framework version 2.0, when you display data in a parent/child view you might have to take extra steps to make sure that the currently selected row in the child table is not reset to the first row of the table.</span></span> <span data-ttu-id="4d203-108">Pour cela, vous devez mettre en cache la position de la table enfant et la réinitialiser une fois que la table parente a changé.</span><span class="sxs-lookup"><span data-stu-id="4d203-108">In order to do this, you will have to cache the child table position and reset it after the parent table changes.</span></span> <span data-ttu-id="4d203-109">En général, la réinitialisation de l'enfant se produit la première fois qu'un champ sur une ligne de la table parente change.</span><span class="sxs-lookup"><span data-stu-id="4d203-109">Typically the child reset occurs the first time a field in a row of the parent table changes.</span></span>  
  
### <a name="to-cache-the-current-child-position"></a><span data-ttu-id="4d203-110">Pour mettre en cache la position actuelle de l'enfant</span><span class="sxs-lookup"><span data-stu-id="4d203-110">To Cache the Current Child Position</span></span>  
  
1. <span data-ttu-id="4d203-111">Déclarez une variable entière pour stocker la position de liste de l'enfant et une variable booléenne pour stocker une valeur indiquant s'il faut mettre en cache la position de l'enfant.</span><span class="sxs-lookup"><span data-stu-id="4d203-111">Declare an integer variable to store the child list position and a Boolean variable to store whether to cache the child position.</span></span>  
  
     [!code-csharp[System.Windows.Forms.CurrencyManagerReset#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.CurrencyManagerReset/CS/Form1.cs#4)]
     [!code-vb[System.Windows.Forms.CurrencyManagerReset#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.CurrencyManagerReset/VB/Form1.vb#4)]  
  
2. <span data-ttu-id="4d203-112">Gérez l’événement <xref:System.Windows.Forms.CurrencyManager.ListChanged> pour le <xref:System.Windows.Forms.CurrencyManager> de la liaison et vérifiez s’il y a un <xref:System.ComponentModel.ListChangedType> égal à <xref:System.ComponentModel.ListChangedType.Reset>.</span><span class="sxs-lookup"><span data-stu-id="4d203-112">Handle the <xref:System.Windows.Forms.CurrencyManager.ListChanged> event for the binding's <xref:System.Windows.Forms.CurrencyManager> and check for a <xref:System.ComponentModel.ListChangedType> of <xref:System.ComponentModel.ListChangedType.Reset>.</span></span>  
  
3. <span data-ttu-id="4d203-113">Vérifiez la position actuelle du <xref:System.Windows.Forms.CurrencyManager>.</span><span class="sxs-lookup"><span data-stu-id="4d203-113">Check the current position of the <xref:System.Windows.Forms.CurrencyManager>.</span></span> <span data-ttu-id="4d203-114">Si elle est supérieure à la première entrée de la liste (en général 0), enregistrez-la dans une variable.</span><span class="sxs-lookup"><span data-stu-id="4d203-114">If it is greater than first entry in the list (typically 0), save it to a variable.</span></span>  
  
     [!code-csharp[System.Windows.Forms.CurrencyManagerReset#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.CurrencyManagerReset/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.CurrencyManagerReset#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.CurrencyManagerReset/VB/Form1.vb#2)]  
  
4. <span data-ttu-id="4d203-115">Gérez l'événement <xref:System.Windows.Forms.BindingManagerBase.CurrentChanged> de la liste parente pour le gestionnaire de devise parent.</span><span class="sxs-lookup"><span data-stu-id="4d203-115">Handle the parent list's <xref:System.Windows.Forms.BindingManagerBase.CurrentChanged> event for the parent currency manager.</span></span> <span data-ttu-id="4d203-116">Dans le gestionnaire, définissez la valeur booléenne pour indiquer qu'il ne s'agit pas d'un scénario de mise en cache.</span><span class="sxs-lookup"><span data-stu-id="4d203-116">In the handler, set the Boolean value to indicate it is not a caching scenario.</span></span> <span data-ttu-id="4d203-117">Si l'événement <xref:System.Windows.Forms.BindingManagerBase.CurrentChanged> se produit, la modification du parent est une modification de position dans la liste et non une modification de valeur d'élément.</span><span class="sxs-lookup"><span data-stu-id="4d203-117">If the <xref:System.Windows.Forms.BindingManagerBase.CurrentChanged> occurs, the change to the parent is a list position change and not an item value change.</span></span>  
  
     [!code-csharp[System.Windows.Forms.CurrencyManagerReset#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.CurrencyManagerReset/CS/Form1.cs#5)]
     [!code-vb[System.Windows.Forms.CurrencyManagerReset#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.CurrencyManagerReset/VB/Form1.vb#5)]  
  
### <a name="to-reset-the-child-position"></a><span data-ttu-id="4d203-118">Pour réinitialiser la position de l'enfant</span><span class="sxs-lookup"><span data-stu-id="4d203-118">To Reset the Child Position</span></span>  
  
1. <span data-ttu-id="4d203-119">Gérez l'événement <xref:System.Windows.Forms.BindingManagerBase.PositionChanged> pour le <xref:System.Windows.Forms.CurrencyManager> de la liaison enfant.</span><span class="sxs-lookup"><span data-stu-id="4d203-119">Handle the <xref:System.Windows.Forms.BindingManagerBase.PositionChanged> event for the child binding's <xref:System.Windows.Forms.CurrencyManager>.</span></span>  
  
2. <span data-ttu-id="4d203-120">Réinitialisez la position de la table enfant à la position mise en cache enregistrée lors de la procédure précédente.</span><span class="sxs-lookup"><span data-stu-id="4d203-120">Reset the child table position to the cached position saved in the previous procedure.</span></span>  
  
     [!code-csharp[System.Windows.Forms.CurrencyManagerReset#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.CurrencyManagerReset/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.CurrencyManagerReset#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.CurrencyManagerReset/VB/Form1.vb#3)]  
  
## <a name="example"></a><span data-ttu-id="4d203-121">Exemple</span><span class="sxs-lookup"><span data-stu-id="4d203-121">Example</span></span>  
 <span data-ttu-id="4d203-122">L'exemple suivant montre comment enregistrer la position actuelle sur le <xref:System.Windows.Forms.CurrencyManager> pour une table enfant et réinitialiser la position après qu'une modification a été effectuée sur la table parente.</span><span class="sxs-lookup"><span data-stu-id="4d203-122">The following example demonstrates how to save the current position on the <xref:System.Windows.Forms.CurrencyManager>.for a child table and reset the position after an edit is completed on the parent table.</span></span> <span data-ttu-id="4d203-123">Cet exemple contient deux contrôles <xref:System.Windows.Forms.DataGridView> liés à deux tables dans un <xref:System.Data.DataSet> à l'aide d'un composant <xref:System.Windows.Forms.BindingSource>.</span><span class="sxs-lookup"><span data-stu-id="4d203-123">This example contains two <xref:System.Windows.Forms.DataGridView> controls bound to two tables in a <xref:System.Data.DataSet> using a <xref:System.Windows.Forms.BindingSource> component.</span></span> <span data-ttu-id="4d203-124">Une relation est établie entre les deux tables et la relation est ajoutée au <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="4d203-124">A relation is established between the two tables and the relation is added to the <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="4d203-125">La position dans la table enfant est initialement définie sur la troisième ligne à des fins de démonstration.</span><span class="sxs-lookup"><span data-stu-id="4d203-125">The position in the child table is initially set to the third row for demonstration purposes.</span></span>  
  
 [!code-csharp[System.Windows.Forms.CurrencyManagerReset#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.CurrencyManagerReset/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.CurrencyManagerReset#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.CurrencyManagerReset/VB/Form1.vb#1)]  
  
 <span data-ttu-id="4d203-126">Pour tester l'exemple de code, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="4d203-126">To test the code example, perform the following steps:</span></span>  
  
1. <span data-ttu-id="4d203-127">Exécutez l'exemple.</span><span class="sxs-lookup"><span data-stu-id="4d203-127">Run the example.</span></span>  
  
2. <span data-ttu-id="4d203-128">Assurez-vous que la case **Cache et réinitialisation de position** est cochée.</span><span class="sxs-lookup"><span data-stu-id="4d203-128">Make sure the **Cache and reset position** check box is selected.</span></span>  
  
3. <span data-ttu-id="4d203-129">Cliquez sur le bouton **Effacer le champ parent** pour provoquer une modification dans un champ de la table parent.</span><span class="sxs-lookup"><span data-stu-id="4d203-129">Click the **Clear parent field** button to cause a change in a field of the parent table.</span></span> <span data-ttu-id="4d203-130">Notez que la ligne sélectionnée dans la table enfant ne change pas.</span><span class="sxs-lookup"><span data-stu-id="4d203-130">Notice that the selected row in the child table does not change.</span></span>  
  
4. <span data-ttu-id="4d203-131">Fermez puis réexécutez l'exemple.</span><span class="sxs-lookup"><span data-stu-id="4d203-131">Close and run the example again.</span></span> <span data-ttu-id="4d203-132">Cette opération est nécessaire car le comportement de réinitialisation se produit uniquement lors de la première modification sur la ligne parente.</span><span class="sxs-lookup"><span data-stu-id="4d203-132">You need to do this because the reset behavior occurs only on the first change in the parent row.</span></span>  
  
5. <span data-ttu-id="4d203-133">Décochez la case **Cache et réinitialisation de position**.</span><span class="sxs-lookup"><span data-stu-id="4d203-133">Clear the **Cache and reset position** check box.</span></span>  
  
6. <span data-ttu-id="4d203-134">Cliquez sur le bouton **Effacer le champ parent**.</span><span class="sxs-lookup"><span data-stu-id="4d203-134">Click the **Clear parent field** button.</span></span> <span data-ttu-id="4d203-135">Notez que la ligne sélectionnée dans la table enfant passe en première ligne.</span><span class="sxs-lookup"><span data-stu-id="4d203-135">Notice that the selected row in the child table changes to the first row.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="4d203-136">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="4d203-136">Compiling the Code</span></span>  
 <span data-ttu-id="4d203-137">Cet exemple nécessite :</span><span class="sxs-lookup"><span data-stu-id="4d203-137">This example requires:</span></span>  
  
- <span data-ttu-id="4d203-138">Références aux assemblys System, System.Data, System.Drawing, System.Windows.Forms et System.Xml.</span><span class="sxs-lookup"><span data-stu-id="4d203-138">References to the System, System.Data, System.Drawing, System.Windows.Forms, and System.XML assemblies.</span></span>  
  
 <span data-ttu-id="4d203-139">Pour plus d’informations sur la création de cet exemple à partir de la ligne de commande pour Visual Basic ou Visual c#, consultez [génération à partir de la ligne de commande](../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) ou [de ligne de commande avec csc.exe](../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="4d203-139">For information about how to build this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="4d203-140">Vous pouvez également créer cet exemple dans Visual Studio en collant le code dans un nouveau projet.</span><span class="sxs-lookup"><span data-stu-id="4d203-140">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4d203-141">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4d203-141">See also</span></span>

- [<span data-ttu-id="4d203-142">Guide pratique pour S’assurer que plusieurs contrôles liés à la même Source de données restent synchronisés</span><span class="sxs-lookup"><span data-stu-id="4d203-142">How to: Ensure Multiple Controls Bound to the Same Data Source Remain Synchronized</span></span>](multiple-controls-bound-to-data-source-synchronized.md)
- [<span data-ttu-id="4d203-143">BindingSource, composant</span><span class="sxs-lookup"><span data-stu-id="4d203-143">BindingSource Component</span></span>](./controls/bindingsource-component.md)
- [<span data-ttu-id="4d203-144">Liaison de données et Windows Forms</span><span class="sxs-lookup"><span data-stu-id="4d203-144">Data Binding and Windows Forms</span></span>](data-binding-and-windows-forms.md)
