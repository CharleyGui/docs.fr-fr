---
title: 'Procédure pas à pas : utilisation du contrôle MaskedTextBox'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- input [Windows Forms], controlling to ensure validity
- MaskedTextBox control [Windows Forms], walkthroughs
- MaskedTextBox control [Windows Forms], validation
- user input [Windows Forms], controlling
- text [Windows Forms], controls for input
ms.assetid: df60565e-5447-4110-92a6-be1f6ff5faa3
ms.openlocfilehash: db32b3ec88a07747ea3e286af9f04edce3f1ba3b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182055"
---
# <a name="walkthrough-working-with-the-maskedtextbox-control"></a><span data-ttu-id="5b9ec-102">Procédure pas à pas : utilisation du contrôle MaskedTextBox</span><span class="sxs-lookup"><span data-stu-id="5b9ec-102">Walkthrough: Working with the MaskedTextBox Control</span></span>
<span data-ttu-id="5b9ec-103">Cette procédure pas à pas décrit notamment les tâches suivantes :</span><span class="sxs-lookup"><span data-stu-id="5b9ec-103">Tasks illustrated in this walkthrough include:</span></span>  
  
- <span data-ttu-id="5b9ec-104">Initialiser <xref:System.Windows.Forms.MaskedTextBox> le contrôle</span><span class="sxs-lookup"><span data-stu-id="5b9ec-104">Initializing the <xref:System.Windows.Forms.MaskedTextBox> control</span></span>  
  
- <span data-ttu-id="5b9ec-105">Utilisation <xref:System.Windows.Forms.MaskedTextBox.MaskInputRejected> du gestionnaire d’événements pour alerter l’utilisateur lorsqu’un personnage ne se conforme pas au masque</span><span class="sxs-lookup"><span data-stu-id="5b9ec-105">Using the <xref:System.Windows.Forms.MaskedTextBox.MaskInputRejected> event handler to alert the user when a character does not conform to the mask</span></span>  
  
- <span data-ttu-id="5b9ec-106">L’affectation d’un type à la <xref:System.Windows.Forms.MaskedTextBox.ValidatingType%2A> propriété et l’utilisation du <xref:System.Windows.Forms.MaskedTextBox.TypeValidationCompleted> gestionnaire d’événements pour alerter l’utilisateur lorsque la valeur qu’il tente de valider n’est pas valide pour le type</span><span class="sxs-lookup"><span data-stu-id="5b9ec-106">Assigning a type to the <xref:System.Windows.Forms.MaskedTextBox.ValidatingType%2A> property and using the <xref:System.Windows.Forms.MaskedTextBox.TypeValidationCompleted> event handler to alert the user when the value they're attempting to commit is not valid for the type</span></span>  
  
## <a name="creating-the-project-and-adding-a-control"></a><span data-ttu-id="5b9ec-107">Créer le projet et ajouter un contrôle</span><span class="sxs-lookup"><span data-stu-id="5b9ec-107">Creating the Project and Adding a Control</span></span>  
  
#### <a name="to-add-a-maskedtextbox-control-to-your-form"></a><span data-ttu-id="5b9ec-108">Pour ajouter un contrôle MaskedTextBox à votre formulaire</span><span class="sxs-lookup"><span data-stu-id="5b9ec-108">To add a MaskedTextBox control to your form</span></span>  
  
1. <span data-ttu-id="5b9ec-109">Ouvrez le formulaire sur lequel <xref:System.Windows.Forms.MaskedTextBox> vous voulez placer le contrôle.</span><span class="sxs-lookup"><span data-stu-id="5b9ec-109">Open the form on which you want to place the <xref:System.Windows.Forms.MaskedTextBox> control.</span></span>  
  
2. <span data-ttu-id="5b9ec-110">Faites <xref:System.Windows.Forms.MaskedTextBox> glisser un contrôle de la boîte à **outils** à votre formulaire.</span><span class="sxs-lookup"><span data-stu-id="5b9ec-110">Drag a <xref:System.Windows.Forms.MaskedTextBox> control from the **Toolbox** to your form.</span></span>  
  
3. <span data-ttu-id="5b9ec-111">Cliquez à droite sur le contrôle et choisissez **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="5b9ec-111">Right-click the control and choose **Properties**.</span></span> <span data-ttu-id="5b9ec-112">Dans la fenêtre **Propriétés,** sélectionnez la propriété **Masque** et cliquez sur le bouton **...** (ellipsis) à côté du nom de la propriété.</span><span class="sxs-lookup"><span data-stu-id="5b9ec-112">In the **Properties** window, select the **Mask** property and click the **...** (ellipsis) button next to the property name.</span></span>  
  
4. <span data-ttu-id="5b9ec-113">Dans la boîte de dialogue **de masque d’entrée,** sélectionnez le masque **Short Date** et cliquez **sur OK**.</span><span class="sxs-lookup"><span data-stu-id="5b9ec-113">In the **Input Mask** dialog box, select the **Short Date** mask and click **OK**.</span></span>  
  
5. <span data-ttu-id="5b9ec-114">Dans la fenêtre <xref:System.Windows.Forms.MaskedTextBox.BeepOnError%2A> **Propriétés** définir la propriété à `true`.</span><span class="sxs-lookup"><span data-stu-id="5b9ec-114">In the **Properties** window set the <xref:System.Windows.Forms.MaskedTextBox.BeepOnError%2A> property to `true`.</span></span> <span data-ttu-id="5b9ec-115">Cette propriété provoque un bip court de sonner chaque fois que l’utilisateur tente d’entrer un personnage qui viole la définition du masque.</span><span class="sxs-lookup"><span data-stu-id="5b9ec-115">This property causes a short beep to sound every time the user attempts to input a character that violates the mask definition.</span></span>  
  
 <span data-ttu-id="5b9ec-116">Pour un résumé des caractères que la propriété Masque <xref:System.Windows.Forms.MaskedTextBox.Mask%2A> prend en charge, voir la section Remarques de la propriété.</span><span class="sxs-lookup"><span data-stu-id="5b9ec-116">For a summary of the characters that the Mask property supports, see the Remarks section of the <xref:System.Windows.Forms.MaskedTextBox.Mask%2A> property.</span></span>  
  
## <a name="alert-the-user-to-input-errors"></a><span data-ttu-id="5b9ec-117">Alerter l’utilisateur des erreurs d’entrée</span><span class="sxs-lookup"><span data-stu-id="5b9ec-117">Alert the User to Input Errors</span></span>  
  
#### <a name="add-a-balloon-tip-for-rejected-mask-input"></a><span data-ttu-id="5b9ec-118">Ajouter une pointe de ballon pour l’entrée de masque rejeté</span><span class="sxs-lookup"><span data-stu-id="5b9ec-118">Add a balloon tip for rejected mask input</span></span>  
  
1. <span data-ttu-id="5b9ec-119">Retournez à la boîte <xref:System.Windows.Forms.ToolTip> à **outils** et ajoutez un à votre formulaire.</span><span class="sxs-lookup"><span data-stu-id="5b9ec-119">Return to the **Toolbox** and add a <xref:System.Windows.Forms.ToolTip> to your form.</span></span>  
  
2. <span data-ttu-id="5b9ec-120">Créez un gestionnaire <xref:System.Windows.Forms.MaskedTextBox.MaskInputRejected> d’événements <xref:System.Windows.Forms.ToolTip> pour l’événement qui soulève le moment où une erreur d’entrée se produit.</span><span class="sxs-lookup"><span data-stu-id="5b9ec-120">Create an event handler for the <xref:System.Windows.Forms.MaskedTextBox.MaskInputRejected> event that raises the <xref:System.Windows.Forms.ToolTip> when an input error occurs.</span></span> <span data-ttu-id="5b9ec-121">La pointe du ballon reste visible pendant cinq secondes, ou jusqu’à ce que l’utilisateur la clique.</span><span class="sxs-lookup"><span data-stu-id="5b9ec-121">The balloon tip remains visible for five seconds, or until the user clicks it.</span></span>  
  
    ```csharp  
    public void Form1_Load(Object sender, EventArgs e)
    {  
        ... // Other initialization code  
        maskedTextBox1.Mask = "00/00/0000";  
        maskedTextBox1.MaskInputRejected += new MaskInputRejectedEventHandler(maskedTextBox1_MaskInputRejected)  
    }  
  
    void maskedTextBox1_MaskInputRejected(object sender, MaskInputRejectedEventArgs e)  
    {  
        toolTip1.ToolTipTitle = "Invalid Input";  
        toolTip1.Show("We're sorry, but only digits (0-9) are allowed in dates.", maskedTextBox1, maskedTextBox1.Location, 5000);  
    }  
    ```  
  
    ```vb  
    Private Sub Form1_Load(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles MyBase.Load  
        Me.ToolTip1.IsBalloon = True  
        Me.MaskedTextBox1.Mask = "00/00/0000"  
    End Sub  
  
    Private Sub MaskedTextBox1_MaskInputRejected(sender as Object, e as MaskInputRejectedEventArgs) Handles MaskedTextBox1.MaskInputRejected  
        ToolTip1.ToolTipTitle = "Invalid Input"  
        ToolTip1.Show("We're sorry, but only digits (0-9) are allowed in dates.", MaskedTextBox1, 5000)  
    End Sub  
    ```  
  
## <a name="alert-the-user-to-a-type-that-is-not-valid"></a><span data-ttu-id="5b9ec-122">Alerter l’utilisateur d’un type qui n’est pas valide</span><span class="sxs-lookup"><span data-stu-id="5b9ec-122">Alert the User to a Type that Is Not Valid</span></span>  
  
#### <a name="add-a-balloon-tip-for-invalid-data-types"></a><span data-ttu-id="5b9ec-123">Ajouter une pointe de ballon pour les types de données non valides</span><span class="sxs-lookup"><span data-stu-id="5b9ec-123">Add a balloon tip for invalid data types</span></span>  
  
1. <span data-ttu-id="5b9ec-124">Dans le gestionnaire <xref:System.Windows.Forms.Form.Load> d’événements <xref:System.Type> de votre <xref:System.DateTime> formulaire, <xref:System.Windows.Forms.MaskedTextBox> assignez <xref:System.Windows.Forms.MaskedTextBox.ValidatingType%2A> un objet représentant le type à la propriété du contrôle :</span><span class="sxs-lookup"><span data-stu-id="5b9ec-124">In your form's <xref:System.Windows.Forms.Form.Load> event handler, assign a <xref:System.Type> object representing the <xref:System.DateTime> type to the <xref:System.Windows.Forms.MaskedTextBox> control's <xref:System.Windows.Forms.MaskedTextBox.ValidatingType%2A> property:</span></span>  
  
    ```csharp  
    private void Form1_Load(Object sender, EventArgs e)  
    {  
        // Other code  
        maskedTextBox1.ValidatingType = typeof(System.DateTime);  
        maskedTextBox1.TypeValidationCompleted += new TypeValidationEventHandler(maskedTextBox1_TypeValidationCompleted);  
    }  
    ```  
  
    ```vb  
    Private Sub Form1_Load(sender as Object, e as EventArgs)  
        // Other code  
        MaskedTextBox1.ValidatingType = GetType(System.DateTime)  
    End Sub  
    ```  
  
2. <span data-ttu-id="5b9ec-125">Ajoutez un gestionnaire d'événements pour l'événement <xref:System.Windows.Forms.MaskedTextBox.TypeValidationCompleted> :</span><span class="sxs-lookup"><span data-stu-id="5b9ec-125">Add an event handler for the <xref:System.Windows.Forms.MaskedTextBox.TypeValidationCompleted> event:</span></span>  
  
    ```csharp  
    public void maskedTextBox1_TypeValidationCompleted(object sender, TypeValidationEventArgs e)  
    {  
        if (!e.IsValidInput)  
        {  
           toolTip1.ToolTipTitle = "Invalid Date Value";  
           toolTip1.Show("We're sorry, but the value you entered is not a valid date. Please change the value.", maskedTextBox1, 5000);  
           e.Cancel = true;  
        }  
    }  
    ```  
  
    ```vb  
    Public Sub MaskedTextBox1_TypeValidationCompleted(sender as Object, e as TypeValidationEventArgs)  
        If Not e.IsValidInput Then  
           ToolTip1.ToolTipTitle = "Invalid Date Value"  
           ToolTip1.Show("We're sorry, but the value you entered is not a valid date. Please change the value.", maskedTextBox1, 5000)  
           e.Cancel = True  
        End If  
    End Sub  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="5b9ec-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5b9ec-126">See also</span></span>

- <xref:System.Windows.Forms.MaskedTextBox>
- [<span data-ttu-id="5b9ec-127">MaskedTextBox, contrôle</span><span class="sxs-lookup"><span data-stu-id="5b9ec-127">MaskedTextBox Control</span></span>](maskedtextbox-control-windows-forms.md)
