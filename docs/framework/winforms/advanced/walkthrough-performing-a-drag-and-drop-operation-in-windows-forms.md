---
title: 'Procédure pas à pas : Effectuer une opération de drag-and-drop'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Windows Forms, drag and drop operations
- drag and drop [Windows Forms], Windows Forms
ms.assetid: eb66f6bf-4a7d-4c2d-b276-40fefb2d3b6c
ms.openlocfilehash: b5e4bf753733cb9bd010672f40e8fbeb0cf036bf
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182445"
---
# <a name="walkthrough-performing-a-drag-and-drop-operation-in-windows-forms"></a><span data-ttu-id="e7356-102">Procédure pas à pas : exécution d’opérations de glisser-déposer dans Windows Forms</span><span class="sxs-lookup"><span data-stu-id="e7356-102">Walkthrough: Performing a Drag-and-Drop Operation in Windows Forms</span></span>
<span data-ttu-id="e7356-103">Pour effectuer des opérations de drag-and-drop dans les applications Basées <xref:System.Windows.Forms.Control.DragEnter>sur <xref:System.Windows.Forms.Control.DragLeave>Windows, vous devez gérer une série d’événements, notamment le , , et <xref:System.Windows.Forms.Control.DragDrop> les événements.</span><span class="sxs-lookup"><span data-stu-id="e7356-103">To perform drag-and-drop operations within Windows-based applications you must handle a series of events, most notably the <xref:System.Windows.Forms.Control.DragEnter>, <xref:System.Windows.Forms.Control.DragLeave>, and <xref:System.Windows.Forms.Control.DragDrop> events.</span></span> <span data-ttu-id="e7356-104">En utilisant les informations disponibles dans les arguments de ces événements, vous pouvez faciliter les opérations de glisser-déplacer.</span><span class="sxs-lookup"><span data-stu-id="e7356-104">By working with the information available in the event arguments of these events, you can easily facilitate drag-and-drop operations.</span></span>  
  
## <a name="dragging-data"></a><span data-ttu-id="e7356-105">Faire glisser des données</span><span class="sxs-lookup"><span data-stu-id="e7356-105">Dragging Data</span></span>  
 <span data-ttu-id="e7356-106">Toutes les opérations de glisser-déplacer commencent par un glisser.</span><span class="sxs-lookup"><span data-stu-id="e7356-106">All drag-and-drop operations begin with dragging.</span></span> <span data-ttu-id="e7356-107">La fonctionnalité permettant de recueillir des données lorsque <xref:System.Windows.Forms.Control.DoDragDrop%2A> le drague commence est implémentée dans la méthode.</span><span class="sxs-lookup"><span data-stu-id="e7356-107">The functionality to enable data to be collected when dragging begins is implemented in the <xref:System.Windows.Forms.Control.DoDragDrop%2A> method.</span></span>  
  
 <span data-ttu-id="e7356-108">Dans l’exemple <xref:System.Windows.Forms.Control.MouseDown> suivant, l’événement est utilisé pour démarrer l’opération de traînée parce qu’il est le plus intuitif (la plupart des actions de drag-and-drop commencent avec le bouton de la souris étant déprimé).</span><span class="sxs-lookup"><span data-stu-id="e7356-108">In the following example, the <xref:System.Windows.Forms.Control.MouseDown> event is used to start the drag operation because it is the most intuitive (most drag-and-drop actions begin with the mouse button being depressed).</span></span> <span data-ttu-id="e7356-109">N’oubliez cependant pas que n’importe quel événement peut être utilisé pour lancer une procédure de glisser-déplacer.</span><span class="sxs-lookup"><span data-stu-id="e7356-109">However, remember that any event could be used to initiate a drag-and-drop procedure.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e7356-110">Certains contrôles ont des événements personnalisés spécifiques au glisser.</span><span class="sxs-lookup"><span data-stu-id="e7356-110">Certain controls have custom drag-specific events.</span></span> <span data-ttu-id="e7356-111">Les <xref:System.Windows.Forms.ListView> <xref:System.Windows.Forms.TreeView> contrôles et les commandes, par exemple, ont un <xref:System.Windows.Forms.TreeView.ItemDrag> événement.</span><span class="sxs-lookup"><span data-stu-id="e7356-111">The <xref:System.Windows.Forms.ListView> and <xref:System.Windows.Forms.TreeView> controls, for example, have an <xref:System.Windows.Forms.TreeView.ItemDrag> event.</span></span>  
  
#### <a name="to-start-a-drag-operation"></a><span data-ttu-id="e7356-112">Pour démarrer une opération de glisser</span><span class="sxs-lookup"><span data-stu-id="e7356-112">To start a drag operation</span></span>  
  
1. <span data-ttu-id="e7356-113">Dans <xref:System.Windows.Forms.Control.MouseDown> le cas où le contrôle où la traînée commencera, utilisez la `DoDragDrop` méthode pour définir les données à traîné et l’effet autorisé de traînage aura.</span><span class="sxs-lookup"><span data-stu-id="e7356-113">In the <xref:System.Windows.Forms.Control.MouseDown> event for the control where the drag will begin, use the `DoDragDrop` method to set the data to be dragged and the allowed effect dragging will have.</span></span> <span data-ttu-id="e7356-114">Pour plus d’informations, consultez <xref:System.Windows.Forms.DragEventArgs.Data%2A> et <xref:System.Windows.Forms.DragEventArgs.AllowedEffect%2A>.</span><span class="sxs-lookup"><span data-stu-id="e7356-114">For more information, see <xref:System.Windows.Forms.DragEventArgs.Data%2A> and <xref:System.Windows.Forms.DragEventArgs.AllowedEffect%2A>.</span></span>  
  
     <span data-ttu-id="e7356-115">L’exemple suivant montre comment initier une opération glisser.</span><span class="sxs-lookup"><span data-stu-id="e7356-115">The following example shows how to initiate a drag operation.</span></span> <span data-ttu-id="e7356-116">Le contrôle où la <xref:System.Windows.Forms.Button> traînée commence est un contrôle, les données étant traînées est la chaîne représentant la <xref:System.Windows.Forms.Control.Text%2A> propriété du <xref:System.Windows.Forms.Button> contrôle, et les effets autorisés sont soit copier ou se déplacer.</span><span class="sxs-lookup"><span data-stu-id="e7356-116">The control where the drag begins is a <xref:System.Windows.Forms.Button> control, the data being dragged is the string representing the <xref:System.Windows.Forms.Control.Text%2A> property of the <xref:System.Windows.Forms.Button> control, and the allowed effects are either copying or moving.</span></span>  
  
    ```vb  
    Private Sub Button1_MouseDown(ByVal sender As Object, ByVal e As System.Windows.Forms.MouseEventArgs) Handles Button1.MouseDown  
       Button1.DoDragDrop(Button1.Text, DragDropEffects.Copy Or DragDropEffects.Move)  
    End Sub  
    ```  
  
    ```csharp  
    private void button1_MouseDown(object sender,
    System.Windows.Forms.MouseEventArgs e)  
    {  
       button1.DoDragDrop(button1.Text, DragDropEffects.Copy |
          DragDropEffects.Move);  
    }  
    ```  
  
    > [!NOTE]
    > <span data-ttu-id="e7356-117">Toutes les données peuvent être `DoDragDrop` utilisées comme paramètre dans la méthode; dans l’exemple <xref:System.Windows.Forms.Control.Text%2A> ci-dessus, la propriété du <xref:System.Windows.Forms.Button> contrôle a été utilisée (plutôt que de coder une valeur ou de récupérer <xref:System.Windows.Forms.Button> des données à partir d’un jeu de données) parce que la propriété était liée à l’emplacement traîné (le contrôle).</span><span class="sxs-lookup"><span data-stu-id="e7356-117">Any data can be used as a parameter in the `DoDragDrop` method; in the example above, the <xref:System.Windows.Forms.Control.Text%2A> property of the <xref:System.Windows.Forms.Button> control was used (rather than hard-coding a value or retrieving data from a dataset) because the property was related to the location being dragged from (the <xref:System.Windows.Forms.Button> control).</span></span> <span data-ttu-id="e7356-118">Gardez cela à l’esprit quand vous incorporez des opérations de glisser-déplacer dans vos applications Windows.</span><span class="sxs-lookup"><span data-stu-id="e7356-118">Keep this in mind as you incorporate drag-and-drop operations into your Windows-based applications.</span></span>  
  
 <span data-ttu-id="e7356-119">Pendant qu’une opération de traînée <xref:System.Windows.Forms.Control.QueryContinueDrag> est en vigueur, vous pouvez gérer l’événement, qui « demande la permission » du système pour continuer le fonctionnement de la traînée.</span><span class="sxs-lookup"><span data-stu-id="e7356-119">While a drag operation is in effect, you can handle the <xref:System.Windows.Forms.Control.QueryContinueDrag> event, which "asks permission" of the system to continue the drag operation.</span></span> <span data-ttu-id="e7356-120">Lors de la manipulation de cette méthode, il est également le point approprié pour vous <xref:System.Windows.Forms.TreeNode> d’appeler des méthodes qui auront un effet sur le fonctionnement de la traînée, comme l’expansion d’un <xref:System.Windows.Forms.TreeView> contrôle lorsque le curseur plane sur elle.</span><span class="sxs-lookup"><span data-stu-id="e7356-120">When handling this method, it is also the appropriate point for you to call methods that will have an effect on the drag operation, such as expanding a <xref:System.Windows.Forms.TreeNode> in a <xref:System.Windows.Forms.TreeView> control when the cursor hovers over it.</span></span>  
  
## <a name="dropping-data"></a><span data-ttu-id="e7356-121">Déposer des données</span><span class="sxs-lookup"><span data-stu-id="e7356-121">Dropping Data</span></span>  
 <span data-ttu-id="e7356-122">Une fois que vous avez commencé à faire glisser des données à partir d’un emplacement sur un Windows Form ou un contrôle, vous voulez naturellement les déposer quelque part.</span><span class="sxs-lookup"><span data-stu-id="e7356-122">Once you have begun dragging data from a location on a Windows Form or control, you will naturally want to drop it somewhere.</span></span> <span data-ttu-id="e7356-123">Le curseur change quand il passe sur une zone d’un formulaire ou d’un contrôle qui est correctement configuré pour le dépôt des données.</span><span class="sxs-lookup"><span data-stu-id="e7356-123">The cursor will change when it crosses an area of a form or control that is correctly configured for dropping data.</span></span> <span data-ttu-id="e7356-124">Toute zone dans un formulaire ou un contrôle Windows peut <xref:System.Windows.Forms.Control.AllowDrop%2A> être faite <xref:System.Windows.Forms.Control.DragEnter> <xref:System.Windows.Forms.Control.DragDrop> pour accepter les données abandonnées en définissant la propriété et en manipulant le et les événements.</span><span class="sxs-lookup"><span data-stu-id="e7356-124">Any area within a Windows Form or control can be made to accept dropped data by setting the <xref:System.Windows.Forms.Control.AllowDrop%2A> property and handling the <xref:System.Windows.Forms.Control.DragEnter> and <xref:System.Windows.Forms.Control.DragDrop> events.</span></span>  
  
#### <a name="to-perform-a-drop"></a><span data-ttu-id="e7356-125">Pour effectuer un dépôt</span><span class="sxs-lookup"><span data-stu-id="e7356-125">To perform a drop</span></span>  
  
1. <span data-ttu-id="e7356-126">Définissez <xref:System.Windows.Forms.Control.AllowDrop%2A> la propriété pour vrai.</span><span class="sxs-lookup"><span data-stu-id="e7356-126">Set the <xref:System.Windows.Forms.Control.AllowDrop%2A> property to true.</span></span>  
  
2. <span data-ttu-id="e7356-127">Dans `DragEnter` le cas pour le contrôle où la goutte se produira, assurez-vous <xref:System.Windows.Forms.Control.Text%2A>que les données traînées est d’un type acceptable (dans ce cas, ).</span><span class="sxs-lookup"><span data-stu-id="e7356-127">In the `DragEnter` event for the control where the drop will occur, ensure that the data being dragged is of an acceptable type (in this case, <xref:System.Windows.Forms.Control.Text%2A>).</span></span> <span data-ttu-id="e7356-128">Le code définit ensuite l’effet qui se produira <xref:System.Windows.Forms.DragDropEffects> lorsque la baisse se produit à une valeur dans le recensement.</span><span class="sxs-lookup"><span data-stu-id="e7356-128">The code then sets the effect that will happen when the drop occurs to a value in the <xref:System.Windows.Forms.DragDropEffects> enumeration.</span></span> <span data-ttu-id="e7356-129">Pour plus d’informations, consultez <xref:System.Windows.Forms.DragEventArgs.Effect%2A>.</span><span class="sxs-lookup"><span data-stu-id="e7356-129">For more information, see <xref:System.Windows.Forms.DragEventArgs.Effect%2A>.</span></span>  
  
    ```vb  
    Private Sub TextBox1_DragEnter(ByVal sender As Object, ByVal e As System.Windows.Forms.DragEventArgs) Handles TextBox1.DragEnter  
       If (e.Data.GetDataPresent(DataFormats.Text)) Then  
         e.Effect = DragDropEffects.Copy  
       Else  
         e.Effect = DragDropEffects.None  
       End If  
    End Sub  
    ```  
  
    ```csharp  
    private void textBox1_DragEnter(object sender,
    System.Windows.Forms.DragEventArgs e)  
    {  
       if (e.Data.GetDataPresent(DataFormats.Text))
          e.Effect = DragDropEffects.Copy;  
       else  
          e.Effect = DragDropEffects.None;  
    }  
    ```  
  
    > [!NOTE]
    > <span data-ttu-id="e7356-130">Vous pouvez définir <xref:System.Windows.Forms.DataFormats> le vôtre en spécifiant votre propre objet comme le <xref:System.Object> paramètre de la <xref:System.Windows.Forms.DataObject.SetData%2A> méthode.</span><span class="sxs-lookup"><span data-stu-id="e7356-130">You can define your own <xref:System.Windows.Forms.DataFormats> by specifying your own object as the <xref:System.Object> parameter of the <xref:System.Windows.Forms.DataObject.SetData%2A> method.</span></span> <span data-ttu-id="e7356-131">Pour cela, vérifiez que l’objet spécifié est sérialisable.</span><span class="sxs-lookup"><span data-stu-id="e7356-131">Be sure, when doing this, that the object specified is serializable.</span></span> <span data-ttu-id="e7356-132">Pour plus d’informations, consultez <xref:System.Runtime.Serialization.ISerializable>.</span><span class="sxs-lookup"><span data-stu-id="e7356-132">For more information, see <xref:System.Runtime.Serialization.ISerializable>.</span></span>  
  
3. <span data-ttu-id="e7356-133">Dans <xref:System.Windows.Forms.Control.DragDrop> le cas pour le contrôle où <xref:System.Windows.Forms.DataObject.GetData%2A> la goutte se produira, utilisez la méthode pour récupérer les données étant traînées.</span><span class="sxs-lookup"><span data-stu-id="e7356-133">In the <xref:System.Windows.Forms.Control.DragDrop> event for the control where the drop will occur, use the <xref:System.Windows.Forms.DataObject.GetData%2A> method to retrieve the data being dragged.</span></span> <span data-ttu-id="e7356-134">Pour plus d’informations, consultez <xref:System.Security.Cryptography.Xml.DataObject.Data%2A>.</span><span class="sxs-lookup"><span data-stu-id="e7356-134">For more information, see <xref:System.Security.Cryptography.Xml.DataObject.Data%2A>.</span></span>  
  
     <span data-ttu-id="e7356-135">Dans l’exemple <xref:System.Windows.Forms.TextBox> ci-dessous, un contrôle est le contrôle étant traîné à (où la goutte se produira).</span><span class="sxs-lookup"><span data-stu-id="e7356-135">In the example below, a <xref:System.Windows.Forms.TextBox> control is the control being dragged to (where the drop will occur).</span></span> <span data-ttu-id="e7356-136">Le code <xref:System.Windows.Forms.Control.Text%2A> définit la <xref:System.Windows.Forms.TextBox> propriété du contrôle égale aux données traînées.</span><span class="sxs-lookup"><span data-stu-id="e7356-136">The code sets the <xref:System.Windows.Forms.Control.Text%2A> property of the <xref:System.Windows.Forms.TextBox> control equal to the data being dragged.</span></span>  
  
    ```vb  
    Private Sub TextBox1_DragDrop(ByVal sender As Object, ByVal e As System.Windows.Forms.DragEventArgs) Handles TextBox1.DragDrop  
       TextBox1.Text = e.Data.GetData(DataFormats.Text).ToString  
    End Sub  
    ```  
  
    ```csharp  
    private void textBox1_DragDrop(object sender,
    System.Windows.Forms.DragEventArgs e)  
    {  
       textBox1.Text = e.Data.GetData(DataFormats.Text).ToString();  
    }  
    ```  
  
    > [!NOTE]
    > <span data-ttu-id="e7356-137">En outre, vous <xref:System.Windows.Forms.DragEventArgs.KeyState%2A> pouvez travailler avec la propriété, de sorte que, en fonction des clés décanches pendant l’opération de drag-and-drop, certains effets se produisent (par exemple, il est standard de copier les données traînées lorsque la clé CTRL est pressé).</span><span class="sxs-lookup"><span data-stu-id="e7356-137">Additionally, you can work with the <xref:System.Windows.Forms.DragEventArgs.KeyState%2A> property, so that, depending on keys depressed during the drag-and-drop operation, certain effects occur (for example, it is standard to copy the dragged data when the CTRL key is pressed).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e7356-138">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e7356-138">See also</span></span>

- [<span data-ttu-id="e7356-139">Guide pratique pour ajouter des données au Presse-papiers</span><span class="sxs-lookup"><span data-stu-id="e7356-139">How to: Add Data to the Clipboard</span></span>](how-to-add-data-to-the-clipboard.md)
- [<span data-ttu-id="e7356-140">Guide pratique pour récupérer des données du Presse-papiers</span><span class="sxs-lookup"><span data-stu-id="e7356-140">How to: Retrieve Data from the Clipboard</span></span>](how-to-retrieve-data-from-the-clipboard.md)
- [<span data-ttu-id="e7356-141">Opérations glisser-déposer et prise en charge du Presse-papiers</span><span class="sxs-lookup"><span data-stu-id="e7356-141">Drag-and-Drop Operations and Clipboard Support</span></span>](drag-and-drop-operations-and-clipboard-support.md)
