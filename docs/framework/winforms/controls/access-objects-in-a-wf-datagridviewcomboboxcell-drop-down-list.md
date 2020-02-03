---
title: Accéder aux objets dans la liste déroulante DataGridViewComboBoxCell
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], accessing objects in combo box cells
- combo boxes [Windows Forms], in DataGridView control
- combo boxes [Windows Forms], accessing objects in DataGridViewComboBoxCell drop-down lists
ms.assetid: bcbe794a-d1fa-47f8-b5a3-5f085b32097d
ms.openlocfilehash: 7e76ab1ac9089778e4371f4ee65b06d5ebc570bf
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746311"
---
# <a name="how-to-access-objects-in-a-windows-forms-datagridviewcomboboxcell-drop-down-list"></a><span data-ttu-id="454f4-102">Comment : accéder à des objets dans une liste déroulante DataGridViewComboBoxCell Windows Forms</span><span class="sxs-lookup"><span data-stu-id="454f4-102">How to: Access Objects in a Windows Forms DataGridViewComboBoxCell Drop-Down List</span></span>
<span data-ttu-id="454f4-103">À l’instar du contrôle <xref:System.Windows.Forms.ComboBox>, les types <xref:System.Windows.Forms.DataGridViewComboBoxColumn> et <xref:System.Windows.Forms.DataGridViewComboBoxCell> vous permettent d’ajouter des objets arbitraires à leurs listes déroulantes.</span><span class="sxs-lookup"><span data-stu-id="454f4-103">Like the <xref:System.Windows.Forms.ComboBox> control, the <xref:System.Windows.Forms.DataGridViewComboBoxColumn> and <xref:System.Windows.Forms.DataGridViewComboBoxCell> types enable you to add arbitrary objects to their drop-down lists.</span></span> <span data-ttu-id="454f4-104">Avec cette fonctionnalité, vous pouvez représenter des États complexes dans une liste déroulante sans avoir à stocker les objets correspondants dans une collection distincte.</span><span class="sxs-lookup"><span data-stu-id="454f4-104">With this feature, you can represent complex states in a drop-down list without having to store corresponding objects in a separate collection.</span></span>  
  
 <span data-ttu-id="454f4-105">Contrairement au contrôle <xref:System.Windows.Forms.ComboBox>, les types de <xref:System.Windows.Forms.DataGridView> n’ont pas de propriété <xref:System.Windows.Forms.ComboBox.SelectedItem%2A> pour récupérer l’objet actuellement sélectionné.</span><span class="sxs-lookup"><span data-stu-id="454f4-105">Unlike the <xref:System.Windows.Forms.ComboBox> control, the <xref:System.Windows.Forms.DataGridView> types do not have a <xref:System.Windows.Forms.ComboBox.SelectedItem%2A> property for retrieving the currently selected object.</span></span> <span data-ttu-id="454f4-106">Au lieu de cela, vous devez définir la propriété <xref:System.Windows.Forms.DataGridViewComboBoxColumn.ValueMember%2A?displayProperty=nameWithType> ou <xref:System.Windows.Forms.DataGridViewComboBoxCell.ValueMember%2A?displayProperty=nameWithType> sur le nom d’une propriété de votre objet métier.</span><span class="sxs-lookup"><span data-stu-id="454f4-106">Instead, you must set the <xref:System.Windows.Forms.DataGridViewComboBoxColumn.ValueMember%2A?displayProperty=nameWithType> or <xref:System.Windows.Forms.DataGridViewComboBoxCell.ValueMember%2A?displayProperty=nameWithType> property to the name of a property on your business object.</span></span> <span data-ttu-id="454f4-107">Lorsque l’utilisateur effectue une sélection, la propriété indiquée de l’objet métier définit la propriété de <xref:System.Windows.Forms.DataGridViewCell.Value%2A> de la cellule.</span><span class="sxs-lookup"><span data-stu-id="454f4-107">When the user makes a selection, the indicated property of the business object sets the cell <xref:System.Windows.Forms.DataGridViewCell.Value%2A> property.</span></span>  
  
 <span data-ttu-id="454f4-108">Pour récupérer l’objet métier à l’aide de la valeur de cellule, la propriété `ValueMember` doit indiquer une propriété qui retourne une référence à l’objet métier lui-même.</span><span class="sxs-lookup"><span data-stu-id="454f4-108">To retrieve the business object through the cell value, the `ValueMember` property must indicate a property that returns a reference to the business object itself.</span></span> <span data-ttu-id="454f4-109">Par conséquent, si le type de l’objet métier n’est pas sous votre contrôle, vous devez ajouter une telle propriété en étendant le type par héritage.</span><span class="sxs-lookup"><span data-stu-id="454f4-109">Therefore, if the type of the business object is not under your control, you must add such a property by extending the type through inheritance.</span></span>  
  
 <span data-ttu-id="454f4-110">Les procédures suivantes montrent comment remplir une liste déroulante avec des objets métier et récupérer les objets par le biais de la propriété <xref:System.Windows.Forms.DataGridViewCell.Value%2A> de la cellule.</span><span class="sxs-lookup"><span data-stu-id="454f4-110">The following procedures demonstrate how to populate a drop-down list with business objects and retrieve the objects through the cell <xref:System.Windows.Forms.DataGridViewCell.Value%2A> property.</span></span>  
  
### <a name="to-add-business-objects-to-the-drop-down-list"></a><span data-ttu-id="454f4-111">Pour ajouter des objets métier à la liste déroulante</span><span class="sxs-lookup"><span data-stu-id="454f4-111">To add business objects to the drop-down list</span></span>  
  
1. <span data-ttu-id="454f4-112">Créer un <xref:System.Windows.Forms.DataGridViewComboBoxColumn> et remplir son <xref:System.Windows.Forms.DataGridViewComboBoxColumn.Items%2A> collection.</span><span class="sxs-lookup"><span data-stu-id="454f4-112">Create a new <xref:System.Windows.Forms.DataGridViewComboBoxColumn> and populate its <xref:System.Windows.Forms.DataGridViewComboBoxColumn.Items%2A> collection.</span></span> <span data-ttu-id="454f4-113">Vous pouvez également définir la propriété <xref:System.Windows.Forms.DataGridViewComboBoxColumn.DataSource%2A> de la colonne sur la collection d’objets métier.</span><span class="sxs-lookup"><span data-stu-id="454f4-113">Alternatively, you can set the column <xref:System.Windows.Forms.DataGridViewComboBoxColumn.DataSource%2A> property to the collection of business objects.</span></span> <span data-ttu-id="454f4-114">Dans ce cas, toutefois, vous ne pouvez pas ajouter « non assigné » à la liste déroulante sans créer un objet métier correspondant dans votre collection.</span><span class="sxs-lookup"><span data-stu-id="454f4-114">In that case, however, you cannot add "unassigned" to the drop-down list without creating a corresponding business object in your collection.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewComboBoxObjectBinding#110](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/CS/form1.cs#110)]
     [!code-vb[System.Windows.Forms.DataGridViewComboBoxObjectBinding#110](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/vb/form1.vb#110)]  
  
2. <span data-ttu-id="454f4-115">Définissez les propriétés <xref:System.Windows.Forms.DataGridViewComboBoxColumn.DisplayMember%2A> et <xref:System.Windows.Forms.DataGridViewComboBoxColumn.ValueMember%2A>.</span><span class="sxs-lookup"><span data-stu-id="454f4-115">Set the <xref:System.Windows.Forms.DataGridViewComboBoxColumn.DisplayMember%2A> and <xref:System.Windows.Forms.DataGridViewComboBoxColumn.ValueMember%2A> properties.</span></span> <span data-ttu-id="454f4-116"><xref:System.Windows.Forms.DataGridViewComboBoxColumn.DisplayMember%2A> indique la propriété de l’objet métier à afficher dans la liste déroulante.</span><span class="sxs-lookup"><span data-stu-id="454f4-116"><xref:System.Windows.Forms.DataGridViewComboBoxColumn.DisplayMember%2A> indicates the property of the business object to display in the drop-down list.</span></span> <span data-ttu-id="454f4-117"><xref:System.Windows.Forms.DataGridViewComboBoxColumn.ValueMember%2A> indique la propriété qui retourne une référence à l’objet métier.</span><span class="sxs-lookup"><span data-stu-id="454f4-117"><xref:System.Windows.Forms.DataGridViewComboBoxColumn.ValueMember%2A> indicates the property that returns a reference to the business object.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewComboBoxObjectBinding#115](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/CS/form1.cs#115)]
     [!code-vb[System.Windows.Forms.DataGridViewComboBoxObjectBinding#115](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/vb/form1.vb#115)]  
  
3. <span data-ttu-id="454f4-118">Assurez-vous que votre type d’objet métier contient une propriété qui retourne une référence à l’instance actuelle.</span><span class="sxs-lookup"><span data-stu-id="454f4-118">Make sure that your business object type contains a property that returns a reference to the current instance.</span></span> <span data-ttu-id="454f4-119">Cette propriété doit être nommée avec la valeur assignée à <xref:System.Windows.Forms.DataGridViewComboBoxColumn.ValueMember%2A> à l’étape précédente.</span><span class="sxs-lookup"><span data-stu-id="454f4-119">This property must be named with the value assigned to <xref:System.Windows.Forms.DataGridViewComboBoxColumn.ValueMember%2A> in the previous step.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewComboBoxObjectBinding#310](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/CS/form1.cs#310)]
     [!code-vb[System.Windows.Forms.DataGridViewComboBoxObjectBinding#310](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/vb/form1.vb#310)]  
  
### <a name="to-retrieve-the-currently-selected-business-object"></a><span data-ttu-id="454f4-120">Pour récupérer l’objet métier actuellement sélectionné</span><span class="sxs-lookup"><span data-stu-id="454f4-120">To retrieve the currently selected business object</span></span>  
  
- <span data-ttu-id="454f4-121">Récupérez la propriété <xref:System.Windows.Forms.DataGridViewCell.Value%2A> de la cellule et effectuez un cast de celle-ci vers le type d’objet métier.</span><span class="sxs-lookup"><span data-stu-id="454f4-121">Get the cell <xref:System.Windows.Forms.DataGridViewCell.Value%2A> property and cast it to the business object type.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewComboBoxObjectBinding#120](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/CS/form1.cs#120)]
     [!code-vb[System.Windows.Forms.DataGridViewComboBoxObjectBinding#120](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/vb/form1.vb#120)]  
  
## <a name="example"></a><span data-ttu-id="454f4-122">Exemple</span><span class="sxs-lookup"><span data-stu-id="454f4-122">Example</span></span>  
 <span data-ttu-id="454f4-123">L’exemple complet illustre l’utilisation des objets métier dans une liste déroulante.</span><span class="sxs-lookup"><span data-stu-id="454f4-123">The complete example demonstrates the use of business objects in a drop-down list.</span></span> <span data-ttu-id="454f4-124">Dans l’exemple, un contrôle de <xref:System.Windows.Forms.DataGridView> est lié à une collection d’objets `Task`.</span><span class="sxs-lookup"><span data-stu-id="454f4-124">In the example, a <xref:System.Windows.Forms.DataGridView> control is bound to a collection of `Task` objects.</span></span> <span data-ttu-id="454f4-125">Chaque objet `Task` a une propriété `AssignedTo` qui indique l’objet `Employee` actuellement assigné à cette tâche.</span><span class="sxs-lookup"><span data-stu-id="454f4-125">Each `Task` object has an `AssignedTo` property that indicates the `Employee` object currently assigned to that task.</span></span> <span data-ttu-id="454f4-126">La colonne `Assigned To` affiche la valeur de la propriété `Name` pour chaque employé affecté, ou « non assigné » si la valeur de la propriété `Task.AssignedTo` est `null`.</span><span class="sxs-lookup"><span data-stu-id="454f4-126">The `Assigned To` column displays the `Name` property value for each assigned employee, or "unassigned" if the `Task.AssignedTo` property value is `null`.</span></span>  
  
 <span data-ttu-id="454f4-127">Pour afficher le comportement de cet exemple, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="454f4-127">To view the behavior of this example, perform the following steps:</span></span>  
  
1. <span data-ttu-id="454f4-128">Modifiez les affectations dans la colonne `Assigned To` en sélectionnant des valeurs différentes dans les listes déroulantes ou en appuyant sur CTRL + 0 dans une cellule de zone de liste déroulante.</span><span class="sxs-lookup"><span data-stu-id="454f4-128">Change assignments in the `Assigned To` column by selecting different values from the drop-down lists or pressing CTRL+0 in a combo-box cell.</span></span>  
  
2. <span data-ttu-id="454f4-129">Cliquez sur `Generate Report` pour afficher les affectations actuelles.</span><span class="sxs-lookup"><span data-stu-id="454f4-129">Click `Generate Report` to display the current assignments.</span></span> <span data-ttu-id="454f4-130">Cela démontre qu’une modification de la colonne `Assigned To` met automatiquement à jour la collection de `tasks`.</span><span class="sxs-lookup"><span data-stu-id="454f4-130">This demonstrates that a change in the `Assigned To` column automatically updates the `tasks` collection.</span></span>  
  
3. <span data-ttu-id="454f4-131">Cliquez sur un bouton de `Request Status` pour appeler la méthode `RequestStatus` de l’objet `Employee` actif pour cette ligne.</span><span class="sxs-lookup"><span data-stu-id="454f4-131">Click a `Request Status` button to call the `RequestStatus` method of the current `Employee` object for that row.</span></span> <span data-ttu-id="454f4-132">Cela montre que l’objet sélectionné a été récupéré avec succès.</span><span class="sxs-lookup"><span data-stu-id="454f4-132">This demonstrates that the selected object has been successfully retrieved.</span></span>  
  
 [!code-csharp[System.Windows.Forms.DataGridViewComboBoxObjectBinding#000](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/CS/form1.cs#000)]
 [!code-vb[System.Windows.Forms.DataGridViewComboBoxObjectBinding#000](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/vb/form1.vb#000)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="454f4-133">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="454f4-133">Compiling the Code</span></span>  
 <span data-ttu-id="454f4-134">Cet exemple nécessite :</span><span class="sxs-lookup"><span data-stu-id="454f4-134">This example requires:</span></span>  
  
- <span data-ttu-id="454f4-135">des références aux assemblys System et System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="454f4-135">References to the System and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="454f4-136">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="454f4-136">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewComboBoxColumn>
- <xref:System.Windows.Forms.DataGridViewComboBoxColumn.Items%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewComboBoxColumn.DataSource%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewComboBoxColumn.ValueMember%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewComboBoxCell>
- <xref:System.Windows.Forms.DataGridViewComboBoxCell.Items%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewComboBoxCell.DataSource%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewComboBoxCell.ValueMember%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewCell.Value%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ComboBox>
- [<span data-ttu-id="454f4-137">Affichage des données dans le contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="454f4-137">Displaying Data in the Windows Forms DataGridView Control</span></span>](displaying-data-in-the-windows-forms-datagridview-control.md)
