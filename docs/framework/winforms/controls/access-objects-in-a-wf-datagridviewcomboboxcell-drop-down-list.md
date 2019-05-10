---
title: 'Procédure : accéder à des objets dans une liste déroulante DataGridViewComboBoxCell Windows Forms'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], accessing objects in combo box cells
- combo boxes [Windows Forms], in DataGridView control
- combo boxes [Windows Forms], accessing objects in DataGridViewComboBoxCell drop-down lists
ms.assetid: bcbe794a-d1fa-47f8-b5a3-5f085b32097d
ms.openlocfilehash: 8df9ef1c30704c8b0d0dc7bbec48e53252cf9ae6
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64665868"
---
# <a name="how-to-access-objects-in-a-windows-forms-datagridviewcomboboxcell-drop-down-list"></a><span data-ttu-id="c52c2-102">Procédure : accéder à des objets dans une liste déroulante DataGridViewComboBoxCell Windows Forms</span><span class="sxs-lookup"><span data-stu-id="c52c2-102">How to: Access Objects in a Windows Forms DataGridViewComboBoxCell Drop-Down List</span></span>
<span data-ttu-id="c52c2-103">Comme le <xref:System.Windows.Forms.ComboBox> contrôle, le <xref:System.Windows.Forms.DataGridViewComboBoxColumn> et <xref:System.Windows.Forms.DataGridViewComboBoxCell> types permettent d’ajouter des objets arbitraires à leurs listes déroulantes.</span><span class="sxs-lookup"><span data-stu-id="c52c2-103">Like the <xref:System.Windows.Forms.ComboBox> control, the <xref:System.Windows.Forms.DataGridViewComboBoxColumn> and <xref:System.Windows.Forms.DataGridViewComboBoxCell> types enable you to add arbitrary objects to their drop-down lists.</span></span> <span data-ttu-id="c52c2-104">Avec cette fonctionnalité, vous pouvez représenter des États complexes dans une liste déroulante, sans avoir à stocker des objets correspondants dans une collection distincte.</span><span class="sxs-lookup"><span data-stu-id="c52c2-104">With this feature, you can represent complex states in a drop-down list without having to store corresponding objects in a separate collection.</span></span>  
  
 <span data-ttu-id="c52c2-105">Contrairement à la <xref:System.Windows.Forms.ComboBox> contrôle, le <xref:System.Windows.Forms.DataGridView> types n’ont pas un <xref:System.Windows.Forms.ComboBox.SelectedItem%2A> propriété pour récupérer l’objet actuellement sélectionné.</span><span class="sxs-lookup"><span data-stu-id="c52c2-105">Unlike the <xref:System.Windows.Forms.ComboBox> control, the <xref:System.Windows.Forms.DataGridView> types do not have a <xref:System.Windows.Forms.ComboBox.SelectedItem%2A> property for retrieving the currently selected object.</span></span> <span data-ttu-id="c52c2-106">Au lieu de cela, vous devez définir le <xref:System.Windows.Forms.DataGridViewComboBoxColumn.ValueMember%2A?displayProperty=nameWithType> ou <xref:System.Windows.Forms.DataGridViewComboBoxCell.ValueMember%2A?displayProperty=nameWithType> propriété le nom d’une propriété de votre objet métier.</span><span class="sxs-lookup"><span data-stu-id="c52c2-106">Instead, you must set the <xref:System.Windows.Forms.DataGridViewComboBoxColumn.ValueMember%2A?displayProperty=nameWithType> or <xref:System.Windows.Forms.DataGridViewComboBoxCell.ValueMember%2A?displayProperty=nameWithType> property to the name of a property on your business object.</span></span> <span data-ttu-id="c52c2-107">Lorsque l’utilisateur effectue une sélection, la propriété indiquée de l’objet métier définit la cellule <xref:System.Windows.Forms.DataGridViewCell.Value%2A> propriété.</span><span class="sxs-lookup"><span data-stu-id="c52c2-107">When the user makes a selection, the indicated property of the business object sets the cell <xref:System.Windows.Forms.DataGridViewCell.Value%2A> property.</span></span>  
  
 <span data-ttu-id="c52c2-108">Pour récupérer l’objet métier via la valeur de cellule, le `ValueMember` propriété doit indiquer une propriété qui retourne une référence à l’objet métier lui-même.</span><span class="sxs-lookup"><span data-stu-id="c52c2-108">To retrieve the business object through the cell value, the `ValueMember` property must indicate a property that returns a reference to the business object itself.</span></span> <span data-ttu-id="c52c2-109">Par conséquent, si le type de l’objet métier n’est pas sous votre contrôle, vous devez ajouter une telle propriété en étendant le type via l’héritage.</span><span class="sxs-lookup"><span data-stu-id="c52c2-109">Therefore, if the type of the business object is not under your control, you must add such a property by extending the type through inheritance.</span></span>  
  
 <span data-ttu-id="c52c2-110">Les procédures suivantes montrent comment remplir une liste déroulante avec des objets métier et récupérer les objets via la cellule <xref:System.Windows.Forms.DataGridViewCell.Value%2A> propriété.</span><span class="sxs-lookup"><span data-stu-id="c52c2-110">The following procedures demonstrate how to populate a drop-down list with business objects and retrieve the objects through the cell <xref:System.Windows.Forms.DataGridViewCell.Value%2A> property.</span></span>  
  
### <a name="to-add-business-objects-to-the-drop-down-list"></a><span data-ttu-id="c52c2-111">Pour ajouter des objets métier à la liste déroulante</span><span class="sxs-lookup"><span data-stu-id="c52c2-111">To add business objects to the drop-down list</span></span>  
  
1. <span data-ttu-id="c52c2-112">Créer un nouveau <xref:System.Windows.Forms.DataGridViewComboBoxColumn> et remplir ses <xref:System.Windows.Forms.DataGridViewComboBoxColumn.Items%2A> collection.</span><span class="sxs-lookup"><span data-stu-id="c52c2-112">Create a new <xref:System.Windows.Forms.DataGridViewComboBoxColumn> and populate its <xref:System.Windows.Forms.DataGridViewComboBoxColumn.Items%2A> collection.</span></span> <span data-ttu-id="c52c2-113">Vous pouvez également définir la colonne <xref:System.Windows.Forms.DataGridViewComboBoxColumn.DataSource%2A> propriété à la collection d’objets métier.</span><span class="sxs-lookup"><span data-stu-id="c52c2-113">Alternatively, you can set the column <xref:System.Windows.Forms.DataGridViewComboBoxColumn.DataSource%2A> property to the collection of business objects.</span></span> <span data-ttu-id="c52c2-114">Dans ce cas, toutefois, vous ne pouvez pas ajouter « non attribués » à la liste déroulante sans provoquer la création d’un objet métier correspondant dans votre collection.</span><span class="sxs-lookup"><span data-stu-id="c52c2-114">In that case, however, you cannot add "unassigned" to the drop-down list without creating a corresponding business object in your collection.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewComboBoxObjectBinding#110](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/CS/form1.cs#110)]
     [!code-vb[System.Windows.Forms.DataGridViewComboBoxObjectBinding#110](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/vb/form1.vb#110)]  
  
2. <span data-ttu-id="c52c2-115">Définissez les propriétés <xref:System.Windows.Forms.DataGridViewComboBoxColumn.DisplayMember%2A> et <xref:System.Windows.Forms.DataGridViewComboBoxColumn.ValueMember%2A>.</span><span class="sxs-lookup"><span data-stu-id="c52c2-115">Set the <xref:System.Windows.Forms.DataGridViewComboBoxColumn.DisplayMember%2A> and <xref:System.Windows.Forms.DataGridViewComboBoxColumn.ValueMember%2A> properties.</span></span> <span data-ttu-id="c52c2-116"><xref:System.Windows.Forms.DataGridViewComboBoxColumn.DisplayMember%2A> Indique la propriété de l’objet métier à afficher dans la liste déroulante.</span><span class="sxs-lookup"><span data-stu-id="c52c2-116"><xref:System.Windows.Forms.DataGridViewComboBoxColumn.DisplayMember%2A> indicates the property of the business object to display in the drop-down list.</span></span> <span data-ttu-id="c52c2-117"><xref:System.Windows.Forms.DataGridViewComboBoxColumn.ValueMember%2A> Indique la propriété qui retourne une référence à l’objet métier.</span><span class="sxs-lookup"><span data-stu-id="c52c2-117"><xref:System.Windows.Forms.DataGridViewComboBoxColumn.ValueMember%2A> indicates the property that returns a reference to the business object.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewComboBoxObjectBinding#115](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/CS/form1.cs#115)]
     [!code-vb[System.Windows.Forms.DataGridViewComboBoxObjectBinding#115](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/vb/form1.vb#115)]  
  
3. <span data-ttu-id="c52c2-118">Assurez-vous que votre type d’objet métier contienne une propriété qui retourne une référence à l’instance actuelle.</span><span class="sxs-lookup"><span data-stu-id="c52c2-118">Make sure that your business object type contains a property that returns a reference to the current instance.</span></span> <span data-ttu-id="c52c2-119">Cette propriété doit être nommée avec la valeur affectée à <xref:System.Windows.Forms.DataGridViewComboBoxColumn.ValueMember%2A> à l’étape précédente.</span><span class="sxs-lookup"><span data-stu-id="c52c2-119">This property must be named with the value assigned to <xref:System.Windows.Forms.DataGridViewComboBoxColumn.ValueMember%2A> in the previous step.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewComboBoxObjectBinding#310](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/CS/form1.cs#310)]
     [!code-vb[System.Windows.Forms.DataGridViewComboBoxObjectBinding#310](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/vb/form1.vb#310)]  
  
### <a name="to-retrieve-the-currently-selected-business-object"></a><span data-ttu-id="c52c2-120">Pour récupérer l’objet métier actuellement sélectionné</span><span class="sxs-lookup"><span data-stu-id="c52c2-120">To retrieve the currently selected business object</span></span>  
  
- <span data-ttu-id="c52c2-121">Obtenir la cellule <xref:System.Windows.Forms.DataGridViewCell.Value%2A> propriété et les convertir en type d’objet métier.</span><span class="sxs-lookup"><span data-stu-id="c52c2-121">Get the cell <xref:System.Windows.Forms.DataGridViewCell.Value%2A> property and cast it to the business object type.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewComboBoxObjectBinding#120](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/CS/form1.cs#120)]
     [!code-vb[System.Windows.Forms.DataGridViewComboBoxObjectBinding#120](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/vb/form1.vb#120)]  
  
## <a name="example"></a><span data-ttu-id="c52c2-122">Exemple</span><span class="sxs-lookup"><span data-stu-id="c52c2-122">Example</span></span>  
 <span data-ttu-id="c52c2-123">L’exemple complet illustre l’utilisation d’objets d’entreprise dans une liste déroulante.</span><span class="sxs-lookup"><span data-stu-id="c52c2-123">The complete example demonstrates the use of business objects in a drop-down list.</span></span> <span data-ttu-id="c52c2-124">Dans l’exemple, un <xref:System.Windows.Forms.DataGridView> contrôle est lié à une collection de `Task` objets.</span><span class="sxs-lookup"><span data-stu-id="c52c2-124">In the example, a <xref:System.Windows.Forms.DataGridView> control is bound to a collection of `Task` objects.</span></span> <span data-ttu-id="c52c2-125">Chaque `Task` objet possède un `AssignedTo` propriété qui indique le `Employee` objet actuellement affecté à cette tâche.</span><span class="sxs-lookup"><span data-stu-id="c52c2-125">Each `Task` object has an `AssignedTo` property that indicates the `Employee` object currently assigned to that task.</span></span> <span data-ttu-id="c52c2-126">Le `Assigned To` colonne affiche la `Name` valeur de propriété pour chaque employé assigné, ou « non assigné » si le `Task.AssignedTo` valeur de propriété est `null`.</span><span class="sxs-lookup"><span data-stu-id="c52c2-126">The `Assigned To` column displays the `Name` property value for each assigned employee, or "unassigned" if the `Task.AssignedTo` property value is `null`.</span></span>  
  
 <span data-ttu-id="c52c2-127">Pour afficher le comportement de cet exemple, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="c52c2-127">To view the behavior of this example, perform the following steps:</span></span>  
  
1. <span data-ttu-id="c52c2-128">Modifier les affectations dans les `Assigned To` colonne en sélectionnant des valeurs différentes dans les listes déroulantes ou en appuyant sur CTRL + 0 dans une cellule de zone de liste déroulante.</span><span class="sxs-lookup"><span data-stu-id="c52c2-128">Change assignments in the `Assigned To` column by selecting different values from the drop-down lists or pressing CTRL+0 in a combo-box cell.</span></span>  
  
2. <span data-ttu-id="c52c2-129">Cliquez sur `Generate Report` pour afficher les affectations actuelles.</span><span class="sxs-lookup"><span data-stu-id="c52c2-129">Click `Generate Report` to display the current assignments.</span></span> <span data-ttu-id="c52c2-130">Cette procédure montre qu’une modification dans le `Assigned To` colonne met automatiquement à jour le `tasks` collection.</span><span class="sxs-lookup"><span data-stu-id="c52c2-130">This demonstrates that a change in the `Assigned To` column automatically updates the `tasks` collection.</span></span>  
  
3. <span data-ttu-id="c52c2-131">Cliquez sur un `Request Status` bouton pour appeler le `RequestStatus` méthode du courant `Employee` objet pour cette ligne.</span><span class="sxs-lookup"><span data-stu-id="c52c2-131">Click a `Request Status` button to call the `RequestStatus` method of the current `Employee` object for that row.</span></span> <span data-ttu-id="c52c2-132">Cet exemple montre que l’objet sélectionné a été récupéré avec succès.</span><span class="sxs-lookup"><span data-stu-id="c52c2-132">This demonstrates that the selected object has been successfully retrieved.</span></span>  
  
 [!code-csharp[System.Windows.Forms.DataGridViewComboBoxObjectBinding#000](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/CS/form1.cs#000)]
 [!code-vb[System.Windows.Forms.DataGridViewComboBoxObjectBinding#000](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/vb/form1.vb#000)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="c52c2-133">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="c52c2-133">Compiling the Code</span></span>  
 <span data-ttu-id="c52c2-134">Cet exemple nécessite :</span><span class="sxs-lookup"><span data-stu-id="c52c2-134">This example requires:</span></span>  
  
- <span data-ttu-id="c52c2-135">des références aux assemblys System et System.Windows.Forms ;</span><span class="sxs-lookup"><span data-stu-id="c52c2-135">References to the System and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c52c2-136">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c52c2-136">See also</span></span>

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
- [<span data-ttu-id="c52c2-137">Affichage des données dans le contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="c52c2-137">Displaying Data in the Windows Forms DataGridView Control</span></span>](displaying-data-in-the-windows-forms-datagridview-control.md)
