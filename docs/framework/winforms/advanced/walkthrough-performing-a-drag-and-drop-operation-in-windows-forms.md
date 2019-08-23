---
title: 'Procédure pas à pas : exécution d’une opération glisser-déplacer dans Windows Forms'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Windows Forms, drag and drop operations
- drag and drop [Windows Forms], Windows Forms
ms.assetid: eb66f6bf-4a7d-4c2d-b276-40fefb2d3b6c
ms.openlocfilehash: cda3e87a4b0eb680d374eb0419a6b6b3157dc4a7
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69957121"
---
# <a name="walkthrough-performing-a-drag-and-drop-operation-in-windows-forms"></a><span data-ttu-id="f8f56-102">Procédure pas à pas : exécution d’une opération glisser-déplacer dans Windows Forms</span><span class="sxs-lookup"><span data-stu-id="f8f56-102">Walkthrough: Performing a Drag-and-Drop Operation in Windows Forms</span></span>
<span data-ttu-id="f8f56-103">Pour effectuer des opérations de glisser-déplacer dans des applications Windows, vous devez gérer une série d’événements, notamment les <xref:System.Windows.Forms.Control.DragEnter>événements, <xref:System.Windows.Forms.Control.DragLeave>et. <xref:System.Windows.Forms.Control.DragDrop></span><span class="sxs-lookup"><span data-stu-id="f8f56-103">To perform drag-and-drop operations within Windows-based applications you must handle a series of events, most notably the <xref:System.Windows.Forms.Control.DragEnter>, <xref:System.Windows.Forms.Control.DragLeave>, and <xref:System.Windows.Forms.Control.DragDrop> events.</span></span> <span data-ttu-id="f8f56-104">En utilisant les informations disponibles dans les arguments de ces événements, vous pouvez faciliter les opérations de glisser-déplacer.</span><span class="sxs-lookup"><span data-stu-id="f8f56-104">By working with the information available in the event arguments of these events, you can easily facilitate drag-and-drop operations.</span></span>  
  
## <a name="dragging-data"></a><span data-ttu-id="f8f56-105">Faire glisser des données</span><span class="sxs-lookup"><span data-stu-id="f8f56-105">Dragging Data</span></span>  
 <span data-ttu-id="f8f56-106">Toutes les opérations de glisser-déplacer commencent par un glisser.</span><span class="sxs-lookup"><span data-stu-id="f8f56-106">All drag-and-drop operations begin with dragging.</span></span> <span data-ttu-id="f8f56-107">Les fonctionnalités permettant de collecter des données au début du glissement sont implémentées dans <xref:System.Windows.Forms.Control.DoDragDrop%2A> la méthode.</span><span class="sxs-lookup"><span data-stu-id="f8f56-107">The functionality to enable data to be collected when dragging begins is implemented in the <xref:System.Windows.Forms.Control.DoDragDrop%2A> method.</span></span>  
  
 <span data-ttu-id="f8f56-108">Dans l’exemple suivant, l' <xref:System.Windows.Forms.Control.MouseDown> événement est utilisé pour démarrer l’opération glisser, car il est le plus intuitif (la plupart des actions de glisser-déplacer commencent par le bouton de la souris qui est enfoncé).</span><span class="sxs-lookup"><span data-stu-id="f8f56-108">In the following example, the <xref:System.Windows.Forms.Control.MouseDown> event is used to start the drag operation because it is the most intuitive (most drag-and-drop actions begin with the mouse button being depressed).</span></span> <span data-ttu-id="f8f56-109">N’oubliez cependant pas que n’importe quel événement peut être utilisé pour lancer une procédure de glisser-déplacer.</span><span class="sxs-lookup"><span data-stu-id="f8f56-109">However, remember that any event could be used to initiate a drag-and-drop procedure.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f8f56-110">Certains contrôles ont des événements personnalisés spécifiques au glisser.</span><span class="sxs-lookup"><span data-stu-id="f8f56-110">Certain controls have custom drag-specific events.</span></span> <span data-ttu-id="f8f56-111">Par <xref:System.Windows.Forms.ListView> exemple <xref:System.Windows.Forms.TreeView> , les contrôles et ont un <xref:System.Windows.Forms.TreeView.ItemDrag> événement.</span><span class="sxs-lookup"><span data-stu-id="f8f56-111">The <xref:System.Windows.Forms.ListView> and <xref:System.Windows.Forms.TreeView> controls, for example, have an <xref:System.Windows.Forms.TreeView.ItemDrag> event.</span></span>  
  
#### <a name="to-start-a-drag-operation"></a><span data-ttu-id="f8f56-112">Pour démarrer une opération de glisser</span><span class="sxs-lookup"><span data-stu-id="f8f56-112">To start a drag operation</span></span>  
  
1. <span data-ttu-id="f8f56-113">Dans l' <xref:System.Windows.Forms.Control.MouseDown> événement pour le contrôle où l’opération glisser commence, utilisez la `DoDragDrop` méthode pour définir les données à faire glisser et l’effet autorisé à faire glisser.</span><span class="sxs-lookup"><span data-stu-id="f8f56-113">In the <xref:System.Windows.Forms.Control.MouseDown> event for the control where the drag will begin, use the `DoDragDrop` method to set the data to be dragged and the allowed effect dragging will have.</span></span> <span data-ttu-id="f8f56-114">Pour plus d’informations, consultez <xref:System.Windows.Forms.DragEventArgs.Data%2A> et <xref:System.Windows.Forms.DragEventArgs.AllowedEffect%2A>.</span><span class="sxs-lookup"><span data-stu-id="f8f56-114">For more information, see <xref:System.Windows.Forms.DragEventArgs.Data%2A> and <xref:System.Windows.Forms.DragEventArgs.AllowedEffect%2A>.</span></span>  
  
     <span data-ttu-id="f8f56-115">L’exemple suivant montre comment initier une opération glisser.</span><span class="sxs-lookup"><span data-stu-id="f8f56-115">The following example shows how to initiate a drag operation.</span></span> <span data-ttu-id="f8f56-116">Le contrôle où l’opération de glisser commence <xref:System.Windows.Forms.Button> est un contrôle, les données glissées sont la chaîne représentant <xref:System.Windows.Forms.Control.Text%2A> la propriété du <xref:System.Windows.Forms.Button> contrôle et les effets autorisés sont la copie ou le déplacement.</span><span class="sxs-lookup"><span data-stu-id="f8f56-116">The control where the drag begins is a <xref:System.Windows.Forms.Button> control, the data being dragged is the string representing the <xref:System.Windows.Forms.Control.Text%2A> property of the <xref:System.Windows.Forms.Button> control, and the allowed effects are either copying or moving.</span></span>  
  
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
    > <span data-ttu-id="f8f56-117">Toutes les données peuvent être utilisées en tant que paramètre `DoDragDrop` dans la méthode. dans l’exemple ci <xref:System.Windows.Forms.Control.Text%2A> -dessus, <xref:System.Windows.Forms.Button> la propriété du contrôle a été utilisée (au lieu de coder en dur une valeur ou de récupérer des données d’un DataSet), car la propriété a été associée au emplacement à partir duquel vous faites glisser <xref:System.Windows.Forms.Button> (le contrôle).</span><span class="sxs-lookup"><span data-stu-id="f8f56-117">Any data can be used as a parameter in the `DoDragDrop` method; in the example above, the <xref:System.Windows.Forms.Control.Text%2A> property of the <xref:System.Windows.Forms.Button> control was used (rather than hard-coding a value or retrieving data from a dataset) because the property was related to the location being dragged from (the <xref:System.Windows.Forms.Button> control).</span></span> <span data-ttu-id="f8f56-118">Gardez cela à l’esprit quand vous incorporez des opérations de glisser-déplacer dans vos applications Windows.</span><span class="sxs-lookup"><span data-stu-id="f8f56-118">Keep this in mind as you incorporate drag-and-drop operations into your Windows-based applications.</span></span>  
  
 <span data-ttu-id="f8f56-119">Pendant qu’une opération glisser est en vigueur, vous pouvez gérer <xref:System.Windows.Forms.Control.QueryContinueDrag> l’événement, qui «demande l’autorisation» du système pour poursuivre l’opération glisser.</span><span class="sxs-lookup"><span data-stu-id="f8f56-119">While a drag operation is in effect, you can handle the <xref:System.Windows.Forms.Control.QueryContinueDrag> event, which "asks permission" of the system to continue the drag operation.</span></span> <span data-ttu-id="f8f56-120">Lors de la gestion de cette méthode, il s’agit également du point approprié pour appeler des méthodes qui auront un effet sur l’opération glisser, par exemple <xref:System.Windows.Forms.TreeNode> le développement <xref:System.Windows.Forms.TreeView> d’un dans un contrôle lorsque le curseur pointe dessus.</span><span class="sxs-lookup"><span data-stu-id="f8f56-120">When handling this method, it is also the appropriate point for you to call methods that will have an effect on the drag operation, such as expanding a <xref:System.Windows.Forms.TreeNode> in a <xref:System.Windows.Forms.TreeView> control when the cursor hovers over it.</span></span>  
  
## <a name="dropping-data"></a><span data-ttu-id="f8f56-121">Déposer des données</span><span class="sxs-lookup"><span data-stu-id="f8f56-121">Dropping Data</span></span>  
 <span data-ttu-id="f8f56-122">Une fois que vous avez commencé à faire glisser des données à partir d’un emplacement sur un Windows Form ou un contrôle, vous voulez naturellement les déposer quelque part.</span><span class="sxs-lookup"><span data-stu-id="f8f56-122">Once you have begun dragging data from a location on a Windows Form or control, you will naturally want to drop it somewhere.</span></span> <span data-ttu-id="f8f56-123">Le curseur change quand il passe sur une zone d’un formulaire ou d’un contrôle qui est correctement configuré pour le dépôt des données.</span><span class="sxs-lookup"><span data-stu-id="f8f56-123">The cursor will change when it crosses an area of a form or control that is correctly configured for dropping data.</span></span> <span data-ttu-id="f8f56-124">Toute zone d’un Windows Form ou d’un contrôle peut être rendue pour accepter les données déplacées en définissant <xref:System.Windows.Forms.Control.DragDrop> la <xref:System.Windows.Forms.Control.AllowDrop%2A> propriété et en gérant les <xref:System.Windows.Forms.Control.DragEnter> événements et.</span><span class="sxs-lookup"><span data-stu-id="f8f56-124">Any area within a Windows Form or control can be made to accept dropped data by setting the <xref:System.Windows.Forms.Control.AllowDrop%2A> property and handling the <xref:System.Windows.Forms.Control.DragEnter> and <xref:System.Windows.Forms.Control.DragDrop> events.</span></span>  
  
#### <a name="to-perform-a-drop"></a><span data-ttu-id="f8f56-125">Pour effectuer un dépôt</span><span class="sxs-lookup"><span data-stu-id="f8f56-125">To perform a drop</span></span>  
  
1. <span data-ttu-id="f8f56-126">Affectez <xref:System.Windows.Forms.Control.AllowDrop%2A> à la propriété la valeur true.</span><span class="sxs-lookup"><span data-stu-id="f8f56-126">Set the <xref:System.Windows.Forms.Control.AllowDrop%2A> property to true.</span></span>  
  
2. <span data-ttu-id="f8f56-127">Dans l' `DragEnter` événement pour le contrôle où le déplacement se produit, assurez-vous que les données glissées sont d’un type acceptable (dans ce <xref:System.Windows.Forms.Control.Text%2A>cas,).</span><span class="sxs-lookup"><span data-stu-id="f8f56-127">In the `DragEnter` event for the control where the drop will occur, ensure that the data being dragged is of an acceptable type (in this case, <xref:System.Windows.Forms.Control.Text%2A>).</span></span> <span data-ttu-id="f8f56-128">Le code définit ensuite l’effet qui se produit lorsque la suppression se produit dans une valeur de <xref:System.Windows.Forms.DragDropEffects> l’énumération.</span><span class="sxs-lookup"><span data-stu-id="f8f56-128">The code then sets the effect that will happen when the drop occurs to a value in the <xref:System.Windows.Forms.DragDropEffects> enumeration.</span></span> <span data-ttu-id="f8f56-129">Pour plus d'informations, consultez <xref:System.Windows.Forms.DragEventArgs.Effect%2A>.</span><span class="sxs-lookup"><span data-stu-id="f8f56-129">For more information, see <xref:System.Windows.Forms.DragEventArgs.Effect%2A>.</span></span>  
  
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
    > <span data-ttu-id="f8f56-130">Vous pouvez définir votre propre <xref:System.Windows.Forms.DataFormats> objet en spécifiant votre propre objet <xref:System.Object> comme paramètre de <xref:System.Windows.Forms.DataObject.SetData%2A> la méthode.</span><span class="sxs-lookup"><span data-stu-id="f8f56-130">You can define your own <xref:System.Windows.Forms.DataFormats> by specifying your own object as the <xref:System.Object> parameter of the <xref:System.Windows.Forms.DataObject.SetData%2A> method.</span></span> <span data-ttu-id="f8f56-131">Pour cela, vérifiez que l’objet spécifié est sérialisable.</span><span class="sxs-lookup"><span data-stu-id="f8f56-131">Be sure, when doing this, that the object specified is serializable.</span></span> <span data-ttu-id="f8f56-132">Pour plus d'informations, consultez <xref:System.Runtime.Serialization.ISerializable>.</span><span class="sxs-lookup"><span data-stu-id="f8f56-132">For more information, see <xref:System.Runtime.Serialization.ISerializable>.</span></span>  
  
3. <span data-ttu-id="f8f56-133">Dans l' <xref:System.Windows.Forms.Control.DragDrop> événement pour le contrôle où le déplacement se produit, utilisez la <xref:System.Windows.Forms.DataObject.GetData%2A> méthode pour récupérer les données glissées.</span><span class="sxs-lookup"><span data-stu-id="f8f56-133">In the <xref:System.Windows.Forms.Control.DragDrop> event for the control where the drop will occur, use the <xref:System.Windows.Forms.DataObject.GetData%2A> method to retrieve the data being dragged.</span></span> <span data-ttu-id="f8f56-134">Pour plus d'informations, consultez <xref:System.Security.Cryptography.Xml.DataObject.Data%2A>.</span><span class="sxs-lookup"><span data-stu-id="f8f56-134">For more information, see <xref:System.Security.Cryptography.Xml.DataObject.Data%2A>.</span></span>  
  
     <span data-ttu-id="f8f56-135">Dans l’exemple ci-dessous <xref:System.Windows.Forms.TextBox> , un contrôle est le contrôle vers lequel le déplacement se produit.</span><span class="sxs-lookup"><span data-stu-id="f8f56-135">In the example below, a <xref:System.Windows.Forms.TextBox> control is the control being dragged to (where the drop will occur).</span></span> <span data-ttu-id="f8f56-136">Le code définit la <xref:System.Windows.Forms.Control.Text%2A> propriété <xref:System.Windows.Forms.TextBox> du contrôle comme étant égale aux données glissées.</span><span class="sxs-lookup"><span data-stu-id="f8f56-136">The code sets the <xref:System.Windows.Forms.Control.Text%2A> property of the <xref:System.Windows.Forms.TextBox> control equal to the data being dragged.</span></span>  
  
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
    > <span data-ttu-id="f8f56-137">En outre, vous pouvez utiliser la <xref:System.Windows.Forms.DragEventArgs.KeyState%2A> propriété, de sorte que, en fonction des touches enfoncées pendant l’opération de glisser-déplacer, certains effets se produisent (par exemple, il est standard de copier les données glissées lorsque la touche CTRL est enfoncée).</span><span class="sxs-lookup"><span data-stu-id="f8f56-137">Additionally, you can work with the <xref:System.Windows.Forms.DragEventArgs.KeyState%2A> property, so that, depending on keys depressed during the drag-and-drop operation, certain effects occur (for example, it is standard to copy the dragged data when the CTRL key is pressed).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f8f56-138">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f8f56-138">See also</span></span>

- [<span data-ttu-id="f8f56-139">Guide pratique : Ajouter des données au Presse-papiers</span><span class="sxs-lookup"><span data-stu-id="f8f56-139">How to: Add Data to the Clipboard</span></span>](how-to-add-data-to-the-clipboard.md)
- [<span data-ttu-id="f8f56-140">Guide pratique : Récupérer les données du presse-papiers</span><span class="sxs-lookup"><span data-stu-id="f8f56-140">How to: Retrieve Data from the Clipboard</span></span>](how-to-retrieve-data-from-the-clipboard.md)
- [<span data-ttu-id="f8f56-141">Opérations glisser-déposer et prise en charge du Presse-papiers</span><span class="sxs-lookup"><span data-stu-id="f8f56-141">Drag-and-Drop Operations and Clipboard Support</span></span>](drag-and-drop-operations-and-clipboard-support.md)
