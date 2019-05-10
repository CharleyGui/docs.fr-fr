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
ms.openlocfilehash: 7f25e21008c77ebf5e55e7affbb4cf07db377c5d
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64623271"
---
# <a name="walkthrough-working-with-the-maskedtextbox-control"></a><span data-ttu-id="7791b-102">Procédure pas à pas : utilisation du contrôle MaskedTextBox</span><span class="sxs-lookup"><span data-stu-id="7791b-102">Walkthrough: Working with the MaskedTextBox Control</span></span>
<span data-ttu-id="7791b-103">Cette procédure pas à pas décrit notamment les tâches suivantes :</span><span class="sxs-lookup"><span data-stu-id="7791b-103">Tasks illustrated in this walkthrough include:</span></span>  
  
- <span data-ttu-id="7791b-104">L’initialisation du <xref:System.Windows.Forms.MaskedTextBox> contrôle</span><span class="sxs-lookup"><span data-stu-id="7791b-104">Initializing the <xref:System.Windows.Forms.MaskedTextBox> control</span></span>  
  
- <span data-ttu-id="7791b-105">À l’aide de la <xref:System.Windows.Forms.MaskedTextBox.MaskInputRejected> Gestionnaire d’événements pour avertir l’utilisateur lorsqu’un caractère n’est pas conforme au masque</span><span class="sxs-lookup"><span data-stu-id="7791b-105">Using the <xref:System.Windows.Forms.MaskedTextBox.MaskInputRejected> event handler to alert the user when a character does not conform to the mask</span></span>  
  
- <span data-ttu-id="7791b-106">Affecter un type à la <xref:System.Windows.Forms.MaskedTextBox.ValidatingType%2A> propriété et à l’aide de la <xref:System.Windows.Forms.MaskedTextBox.TypeValidationCompleted> pour avertir l’utilisateur lorsque la valeur qu’il essaie de valider n’est pas valide pour le type de gestionnaire d’événements</span><span class="sxs-lookup"><span data-stu-id="7791b-106">Assigning a type to the <xref:System.Windows.Forms.MaskedTextBox.ValidatingType%2A> property and using the <xref:System.Windows.Forms.MaskedTextBox.TypeValidationCompleted> event handler to alert the user when the value they're attempting to commit is not valid for the type</span></span>  
  
## <a name="creating-the-project-and-adding-a-control"></a><span data-ttu-id="7791b-107">Création du projet et l’ajout d’un contrôle</span><span class="sxs-lookup"><span data-stu-id="7791b-107">Creating the Project and Adding a Control</span></span>  
  
#### <a name="to-add-a-maskedtextbox-control-to-your-form"></a><span data-ttu-id="7791b-108">Pour ajouter un contrôle MaskedTextBox à votre formulaire</span><span class="sxs-lookup"><span data-stu-id="7791b-108">To add a MaskedTextBox control to your form</span></span>  
  
1. <span data-ttu-id="7791b-109">Ouvrez le formulaire sur lequel vous souhaitez placer le <xref:System.Windows.Forms.MaskedTextBox> contrôle.</span><span class="sxs-lookup"><span data-stu-id="7791b-109">Open the form on which you want to place the <xref:System.Windows.Forms.MaskedTextBox> control.</span></span>  
  
2. <span data-ttu-id="7791b-110">Faites glisser un <xref:System.Windows.Forms.MaskedTextBox> contrôle depuis la **boîte à outils** à votre formulaire.</span><span class="sxs-lookup"><span data-stu-id="7791b-110">Drag a <xref:System.Windows.Forms.MaskedTextBox> control from the **Toolbox** to your form.</span></span>  
  
3. <span data-ttu-id="7791b-111">Cliquez sur le contrôle et choisissez **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="7791b-111">Right-click the control and choose **Properties**.</span></span> <span data-ttu-id="7791b-112">Dans le **propriétés** fenêtre, sélectionnez le **masque** propriété et cliquez sur le **...**  (suspension) en regard du nom de propriété.</span><span class="sxs-lookup"><span data-stu-id="7791b-112">In the **Properties** window, select the **Mask** property and click the **...** (ellipsis) button next to the property name.</span></span>  
  
4. <span data-ttu-id="7791b-113">Dans le **masque d’entrée** boîte de dialogue, sélectionnez le **Date courte** masquer et cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="7791b-113">In the **Input Mask** dialog box, select the **Short Date** mask and click **OK**.</span></span>  
  
5. <span data-ttu-id="7791b-114">Dans le **propriétés** fenêtre, définissez la <xref:System.Windows.Forms.MaskedTextBox.BeepOnError%2A> propriété `true`.</span><span class="sxs-lookup"><span data-stu-id="7791b-114">In the **Properties** window set the <xref:System.Windows.Forms.MaskedTextBox.BeepOnError%2A> property to `true`.</span></span> <span data-ttu-id="7791b-115">Cette propriété provoque un court signal sonore est déclenché chaque fois que l’utilisateur tente d’entrer un caractère qui ne respecte pas la définition de masque.</span><span class="sxs-lookup"><span data-stu-id="7791b-115">This property causes a short beep to sound every time the user attempts to input a character that violates the mask definition.</span></span>  
  
 <span data-ttu-id="7791b-116">Pour obtenir un résumé des caractères qui prend en charge de la propriété Mask, consultez la section Notes de la <xref:System.Windows.Forms.MaskedTextBox.Mask%2A> propriété.</span><span class="sxs-lookup"><span data-stu-id="7791b-116">For a summary of the characters that the Mask property supports, see the Remarks section of the <xref:System.Windows.Forms.MaskedTextBox.Mask%2A> property.</span></span>  
  
## <a name="alert-the-user-to-input-errors"></a><span data-ttu-id="7791b-117">Alerter l’utilisateur pour les erreurs d’entrée</span><span class="sxs-lookup"><span data-stu-id="7791b-117">Alert the User to Input Errors</span></span>  
  
#### <a name="add-a-balloon-tip-for-rejected-mask-input"></a><span data-ttu-id="7791b-118">Ajouter une info-bulle pour l’entrée de masque rejetés</span><span class="sxs-lookup"><span data-stu-id="7791b-118">Add a balloon tip for rejected mask input</span></span>  
  
1. <span data-ttu-id="7791b-119">Retour à la **boîte à outils** et ajoutez un <xref:System.Windows.Forms.ToolTip> à votre formulaire.</span><span class="sxs-lookup"><span data-stu-id="7791b-119">Return to the **Toolbox** and add a <xref:System.Windows.Forms.ToolTip> to your form.</span></span>  
  
2. <span data-ttu-id="7791b-120">Créer un gestionnaire d’événements pour le <xref:System.Windows.Forms.MaskedTextBox.MaskInputRejected> événement qui déclenche le <xref:System.Windows.Forms.ToolTip> lorsque se produit une erreur d’entrée.</span><span class="sxs-lookup"><span data-stu-id="7791b-120">Create an event handler for the <xref:System.Windows.Forms.MaskedTextBox.MaskInputRejected> event that raises the <xref:System.Windows.Forms.ToolTip> when an input error occurs.</span></span> <span data-ttu-id="7791b-121">L’info-bulle reste visible pendant cinq secondes, ou jusqu'à ce que l’utilisateur clique dessus.</span><span class="sxs-lookup"><span data-stu-id="7791b-121">The balloon tip remains visible for five seconds, or until the user clicks it.</span></span>  
  
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
  
## <a name="alert-the-user-to-a-type-that-is-not-valid"></a><span data-ttu-id="7791b-122">Avertir l’utilisateur à un Type qui n’est pas valide</span><span class="sxs-lookup"><span data-stu-id="7791b-122">Alert the User to a Type that Is Not Valid</span></span>  
  
#### <a name="add-a-balloon-tip-for-invalid-data-types"></a><span data-ttu-id="7791b-123">Ajouter une info-bulle pour les types de données non valides</span><span class="sxs-lookup"><span data-stu-id="7791b-123">Add a balloon tip for invalid data types</span></span>  
  
1. <span data-ttu-id="7791b-124">Dans votre formulaire <xref:System.Windows.Forms.Form.Load> Gestionnaire d’événements, affecter un <xref:System.Type> objet représentant le <xref:System.DateTime> type à la <xref:System.Windows.Forms.MaskedTextBox> du contrôle <xref:System.Windows.Forms.MaskedTextBox.ValidatingType%2A> propriété :</span><span class="sxs-lookup"><span data-stu-id="7791b-124">In your form's <xref:System.Windows.Forms.Form.Load> event handler, assign a <xref:System.Type> object representing the <xref:System.DateTime> type to the <xref:System.Windows.Forms.MaskedTextBox> control's <xref:System.Windows.Forms.MaskedTextBox.ValidatingType%2A> property:</span></span>  
  
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
  
2. <span data-ttu-id="7791b-125">Ajoutez un gestionnaire d'événements pour l'événement <xref:System.Windows.Forms.MaskedTextBox.TypeValidationCompleted> :</span><span class="sxs-lookup"><span data-stu-id="7791b-125">Add an event handler for the <xref:System.Windows.Forms.MaskedTextBox.TypeValidationCompleted> event:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="7791b-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7791b-126">See also</span></span>

- <xref:System.Windows.Forms.MaskedTextBox>
- [<span data-ttu-id="7791b-127">MaskedTextBox, contrôle</span><span class="sxs-lookup"><span data-stu-id="7791b-127">MaskedTextBox Control</span></span>](maskedtextbox-control-windows-forms.md)
