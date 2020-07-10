---
title: Ajouter des boutons charger, enregistrer et annuler au contrôle BindingNavigator
description: Découvrez comment ajouter des boutons charger, enregistrer et annuler au contrôle Windows Forms BindingNavigator.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [Windows Forms], manipulating
- BindingNavigator control [Windows Forms], adding buttons
ms.assetid: faa33042-186e-4bb2-8798-17ceb987ec62
ms.openlocfilehash: d4db91b8cfaf2df253d0c4cf5d8a66e9157d4986
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/09/2020
ms.locfileid: "86173417"
---
# <a name="how-to-add-load-save-and-cancel-buttons-to-the-windows-forms-bindingnavigator-control"></a><span data-ttu-id="f11ee-103">Comment : ajouter des boutons Charger, Enregistrer et Annuler au contrôle BindingNavigator Windows Forms</span><span class="sxs-lookup"><span data-stu-id="f11ee-103">How to: Add Load, Save, and Cancel Buttons to the Windows Forms BindingNavigator Control</span></span>

<span data-ttu-id="f11ee-104">Le <xref:System.Windows.Forms.BindingNavigator> contrôle est un <xref:System.Windows.Forms.ToolStrip> contrôle spécial destiné à la navigation et à la manipulation de contrôles sur votre formulaire qui sont liés aux données.</span><span class="sxs-lookup"><span data-stu-id="f11ee-104">The <xref:System.Windows.Forms.BindingNavigator> control is a special-purpose <xref:System.Windows.Forms.ToolStrip> control that is intended for navigating and manipulating controls on your form that are bound to data.</span></span>

<span data-ttu-id="f11ee-105">Étant donné qu’il s’agit d’un <xref:System.Windows.Forms.ToolStrip> contrôle, le <xref:System.Windows.Forms.BindingNavigator> composant peut être facilement modifié pour inclure des commandes supplémentaires ou alternatives pour l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="f11ee-105">Because it's a <xref:System.Windows.Forms.ToolStrip> control, the <xref:System.Windows.Forms.BindingNavigator> component can be easily modified to include additional or alternative commands for the user.</span></span>

<span data-ttu-id="f11ee-106">Dans la procédure suivante, un <xref:System.Windows.Forms.TextBox> contrôle est lié aux données et le <xref:System.Windows.Forms.ToolStrip> contrôle ajouté au formulaire est modifié pour inclure les boutons charger, enregistrer et annuler.</span><span class="sxs-lookup"><span data-stu-id="f11ee-106">In the following procedure, a <xref:System.Windows.Forms.TextBox> control is bound to data, and the <xref:System.Windows.Forms.ToolStrip> control that is added to the form is modified to include load, save, and cancel buttons.</span></span>

## <a name="add-load-save-and-cancel-buttons-to-the-bindingnavigator-component"></a><span data-ttu-id="f11ee-107">Ajouter des boutons charger, enregistrer et annuler au composant BindingNavigator</span><span class="sxs-lookup"><span data-stu-id="f11ee-107">Add load, save, and cancel buttons to the BindingNavigator component</span></span>

1. <span data-ttu-id="f11ee-108">Dans Visual Studio, ajoutez un <xref:System.Windows.Forms.TextBox> contrôle à votre formulaire.</span><span class="sxs-lookup"><span data-stu-id="f11ee-108">In Visual Studio, add a <xref:System.Windows.Forms.TextBox> control to your form.</span></span>

2. <span data-ttu-id="f11ee-109">Liez-le à un <xref:System.Windows.Forms.BindingSource> , qui est lié à une source de données.</span><span class="sxs-lookup"><span data-stu-id="f11ee-109">Bind it to a <xref:System.Windows.Forms.BindingSource>, which is bound to a data source.</span></span> <span data-ttu-id="f11ee-110">Pour cet exemple, le <xref:System.Windows.Forms.BindingSource> est lié à une base de données.</span><span class="sxs-lookup"><span data-stu-id="f11ee-110">For this example, the <xref:System.Windows.Forms.BindingSource> is bound to a database.</span></span>

3. <span data-ttu-id="f11ee-111">Une fois le DataSet et l’adaptateur de table générés, faites glisser un <xref:System.Windows.Forms.BindingNavigator> contrôle vers le formulaire.</span><span class="sxs-lookup"><span data-stu-id="f11ee-111">After the dataset and table adapter are generated, drag a <xref:System.Windows.Forms.BindingNavigator> control to the form.</span></span>

4. <span data-ttu-id="f11ee-112">Affectez à la <xref:System.Windows.Forms.BindingNavigator> propriété du contrôle <xref:System.Windows.Forms.BindingNavigator.BindingSource%2A> la valeur <xref:System.Windows.Forms.BindingSource> sur le formulaire qui est lié aux contrôles.</span><span class="sxs-lookup"><span data-stu-id="f11ee-112">Set the <xref:System.Windows.Forms.BindingNavigator> control's <xref:System.Windows.Forms.BindingNavigator.BindingSource%2A> property to the <xref:System.Windows.Forms.BindingSource> on the form that is bound to the controls.</span></span>

5. <span data-ttu-id="f11ee-113">Sélectionnez le contrôle <xref:System.Windows.Forms.BindingNavigator>.</span><span class="sxs-lookup"><span data-stu-id="f11ee-113">Select the <xref:System.Windows.Forms.BindingNavigator> control.</span></span>

6. <span data-ttu-id="f11ee-114">Cliquez sur le glyphe actions du concepteur ( ![ petite flèche noire ](./media/designer-actions-glyph.gif) ) pour afficher la boîte de dialogue **tâches BindingNavigator** et sélectionnez **modifier les éléments**.</span><span class="sxs-lookup"><span data-stu-id="f11ee-114">Click the designer actions glyph (![Small black arrow](./media/designer-actions-glyph.gif)) so the **BindingNavigator Tasks** dialog appears and select **Edit Items**.</span></span>

     <span data-ttu-id="f11ee-115">L **'éditeur de collections Items** s’affiche.</span><span class="sxs-lookup"><span data-stu-id="f11ee-115">The **Items Collection Editor** appears.</span></span>

7. <span data-ttu-id="f11ee-116">Dans l **'éditeur de collections Items**, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="f11ee-116">In the **Items Collection Editor**, complete the following:</span></span>

    1. <span data-ttu-id="f11ee-117">Ajoutez un <xref:System.Windows.Forms.ToolStripSeparator> et trois <xref:System.Windows.Forms.ToolStripButton> éléments en sélectionnant le type approprié <xref:System.Windows.Forms.ToolStripItem> et en cliquant sur le bouton **Ajouter** .</span><span class="sxs-lookup"><span data-stu-id="f11ee-117">Add a <xref:System.Windows.Forms.ToolStripSeparator> and three <xref:System.Windows.Forms.ToolStripButton> items by selecting the appropriate type of <xref:System.Windows.Forms.ToolStripItem> and clicking the **Add** button.</span></span>

    2. <span data-ttu-id="f11ee-118">Définissez la <xref:System.Windows.Forms.ToolStripItem.Name%2A> propriété des boutons sur **LoadButton**, **SaveButton**et **CancelButton**, respectivement.</span><span class="sxs-lookup"><span data-stu-id="f11ee-118">Set the <xref:System.Windows.Forms.ToolStripItem.Name%2A> property of the buttons to **LoadButton**, **SaveButton**, and **CancelButton**, respectively.</span></span>

    3. <span data-ttu-id="f11ee-119">Affectez <xref:System.Windows.Forms.ToolStripItem.Text%2A> à la propriété des boutons la valeur **Load**, **Save**et **Cancel**.</span><span class="sxs-lookup"><span data-stu-id="f11ee-119">Set the <xref:System.Windows.Forms.ToolStripItem.Text%2A> property of the buttons to **Load**, **Save**, and **Cancel**.</span></span>

    4. <span data-ttu-id="f11ee-120">Définissez la <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> propriété pour chacun des boutons sur **texte**.</span><span class="sxs-lookup"><span data-stu-id="f11ee-120">Set the <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> property for each of the buttons to **Text**.</span></span> <span data-ttu-id="f11ee-121">Vous pouvez également définir cette propriété sur **image** ou **ImageAndText**, et définir l’image à afficher dans la <xref:System.Windows.Forms.ToolStripItem.Image%2A> propriété.</span><span class="sxs-lookup"><span data-stu-id="f11ee-121">Alternatively, you can set this property to **Image** or **ImageAndText**, and set the image to be displayed in the <xref:System.Windows.Forms.ToolStripItem.Image%2A> property.</span></span>

    5. <span data-ttu-id="f11ee-122">Cliquez sur **OK** pour fermer la boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="f11ee-122">Click **OK** to close the dialog box.</span></span> <span data-ttu-id="f11ee-123">Les boutons sont ajoutés au <xref:System.Windows.Forms.ToolStrip> .</span><span class="sxs-lookup"><span data-stu-id="f11ee-123">The buttons are added to the <xref:System.Windows.Forms.ToolStrip>.</span></span>

8. <span data-ttu-id="f11ee-124">Cliquez avec le bouton droit sur le formulaire, puis choisissez **afficher le code**.</span><span class="sxs-lookup"><span data-stu-id="f11ee-124">Right-click the form and choose **View Code**.</span></span>

9. <span data-ttu-id="f11ee-125">Dans l’éditeur de code, recherchez la ligne de code qui charge les données dans l’adaptateur de table.</span><span class="sxs-lookup"><span data-stu-id="f11ee-125">In the Code Editor, find the line of code that loads data into the table adapter.</span></span> <span data-ttu-id="f11ee-126">Ce code a été généré lors de la configuration de la liaison de données à l’étape 2.</span><span class="sxs-lookup"><span data-stu-id="f11ee-126">This code was generated when you set up the data binding in step 2.</span></span> <span data-ttu-id="f11ee-127">Le code doit ressembler à ce qui suit : `TableAdapterName.Fill(DataSetName.TableName)` .</span><span class="sxs-lookup"><span data-stu-id="f11ee-127">The code should be similar to the following: `TableAdapterName.Fill(DataSetName.TableName)`.</span></span> <span data-ttu-id="f11ee-128">Il sera probablement dans l’événement du formulaire <xref:System.Windows.Forms.Form.Load> .</span><span class="sxs-lookup"><span data-stu-id="f11ee-128">It will most likely be in the form's <xref:System.Windows.Forms.Form.Load> event.</span></span>

10. <span data-ttu-id="f11ee-129">Créez un gestionnaire d’événements pour l' <xref:System.Windows.Forms.ToolStripItem.Click> événement de la **charge** <xref:System.Windows.Forms.ToolStripButton> que vous avez créée précédemment et déplacez-y ce code de chargement de données.</span><span class="sxs-lookup"><span data-stu-id="f11ee-129">Create an event handler for the <xref:System.Windows.Forms.ToolStripItem.Click> event of the **Load** <xref:System.Windows.Forms.ToolStripButton> you created earlier and move this data-loading code into it.</span></span>

     <span data-ttu-id="f11ee-130">Votre code doit maintenant ressembler à ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="f11ee-130">Your code should now look similar to the following:</span></span>

    ```vb
    Private Sub LoadButton_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles LoadButton.Click
        TableAdapterName.Fill(DataSetName.TableName)
    End Sub
    ```

    ```csharp
    private void LoadButton_Click(System.Object sender,
        System.EventArgs e)
    {
        TableAdapterName.Fill(DataSetName.TableName);
    }
    ```

11. <span data-ttu-id="f11ee-131">Créez un gestionnaire d’événements pour l' <xref:System.Windows.Forms.ToolStripItem.Click> événement de l' **enregistrement** <xref:System.Windows.Forms.ToolStripButton> que vous avez créé précédemment et écrivez du code pour mettre à jour les données dans la table à laquelle le contrôle est lié.</span><span class="sxs-lookup"><span data-stu-id="f11ee-131">Create an event handler for the <xref:System.Windows.Forms.ToolStripItem.Click> event of the **Save**<xref:System.Windows.Forms.ToolStripButton> you created earlier and write code to update the data within the table the control is bound to.</span></span>

    ```vb
    Private Sub SaveButton_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles SaveButton.Click
        TableAdapterName.Update(DataSetName.TableName)
    End Sub
    ```

    ```csharp
    private void SaveButton_Click(System.Object sender,
        System.EventArgs e)
    {
        TableAdapterName.Update(DataSetName.TableName);
    }
    ```

    > [!NOTE]
    > <span data-ttu-id="f11ee-132">Dans certains cas, le <xref:System.Windows.Forms.BindingNavigator> composant a déjà un bouton **Enregistrer** , mais aucun code n’a été généré par la Concepteur Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="f11ee-132">In some cases, the <xref:System.Windows.Forms.BindingNavigator> component already has a **Save** button, but no code has been generated by the Windows Forms Designer.</span></span> <span data-ttu-id="f11ee-133">Dans ce cas, vous pouvez placer le code précédent dans le <xref:System.Windows.Forms.ToolStripItem.Click> Gestionnaire d’événements pour ce bouton, plutôt que de créer un bouton entièrement nouveau sur le <xref:System.Windows.Forms.ToolStrip> .</span><span class="sxs-lookup"><span data-stu-id="f11ee-133">In this case, you can place the preceding code in the <xref:System.Windows.Forms.ToolStripItem.Click> event handler for that button, rather than creating an entirely new button on the <xref:System.Windows.Forms.ToolStrip>.</span></span> <span data-ttu-id="f11ee-134">Toutefois, le bouton est désactivé par défaut. vous devez donc définir la <xref:System.Windows.Forms.ToolBarButton.Enabled%2A> propriété du bouton sur `true` pour que le bouton fonctionne correctement.</span><span class="sxs-lookup"><span data-stu-id="f11ee-134">However, the button is disabled by default, so you must set the <xref:System.Windows.Forms.ToolBarButton.Enabled%2A> property of the button to `true` to have the button function correctly.</span></span>

12. <span data-ttu-id="f11ee-135">Créez un gestionnaire d’événements pour l' <xref:System.Windows.Forms.ToolStripItem.Click> événement de l' **annulation** <xref:System.Windows.Forms.ToolStripButton> que vous avez créée précédemment et écrivez du code pour annuler les modifications apportées à l’enregistrement de données qui s’affiche.</span><span class="sxs-lookup"><span data-stu-id="f11ee-135">Create an event handler for the <xref:System.Windows.Forms.ToolStripItem.Click> event of the **Cancel** <xref:System.Windows.Forms.ToolStripButton> you created earlier and write code to cancel any changes to the data record that is displayed.</span></span>

    ```vb
    Private Sub CancelButton_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles CancelButton.Click
        BindingSourceName.CancelEdit()
    End Sub
    ```

    ```csharp
    private void CancelButton_Click(System.Object sender, System.EventArgs e)
    {
        BindingSourceName.CancelEdit();
    }
    ```

    > [!NOTE]
    > <span data-ttu-id="f11ee-136">La <xref:System.Windows.Forms.BindingSource.CancelEdit%2A> portée de la méthode est limitée à la ligne de données.</span><span class="sxs-lookup"><span data-stu-id="f11ee-136">The <xref:System.Windows.Forms.BindingSource.CancelEdit%2A> method is scoped to the row of data.</span></span> <span data-ttu-id="f11ee-137">Enregistrez les modifications apportées lors de l’affichage de cet enregistrement individuel avant de passer à l’enregistrement suivant.</span><span class="sxs-lookup"><span data-stu-id="f11ee-137">Save any changes you make while viewing that individual record before navigating to the next record.</span></span>

## <a name="see-also"></a><span data-ttu-id="f11ee-138">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f11ee-138">See also</span></span>

- <xref:System.Windows.Forms.BindingNavigator>
- <xref:System.Windows.Forms.BindingSource>
- <xref:System.Windows.Forms.ToolStrip>
- [<span data-ttu-id="f11ee-139">Contrôle BindingNavigator</span><span class="sxs-lookup"><span data-stu-id="f11ee-139">BindingNavigator Control</span></span>](bindingnavigator-control-windows-forms.md)
- [<span data-ttu-id="f11ee-140">Vue d’ensemble du composant BindingSource</span><span class="sxs-lookup"><span data-stu-id="f11ee-140">BindingSource Component Overview</span></span>](bindingsource-component-overview.md)
