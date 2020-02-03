---
title: Ajouter des boutons charger, enregistrer et annuler au contrôle BindingNavigator
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [Windows Forms], manipulating
- BindingNavigator control [Windows Forms], adding buttons
ms.assetid: faa33042-186e-4bb2-8798-17ceb987ec62
ms.openlocfilehash: ac862d163f1bd8b66f29160d836bc459e4bf4081
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745129"
---
# <a name="how-to-add-load-save-and-cancel-buttons-to-the-windows-forms-bindingnavigator-control"></a><span data-ttu-id="ff3e1-102">Comment : ajouter des boutons Charger, Enregistrer et Annuler au contrôle BindingNavigator Windows Forms</span><span class="sxs-lookup"><span data-stu-id="ff3e1-102">How to: Add Load, Save, and Cancel Buttons to the Windows Forms BindingNavigator Control</span></span>

<span data-ttu-id="ff3e1-103">Le contrôle <xref:System.Windows.Forms.BindingNavigator> est un contrôle <xref:System.Windows.Forms.ToolStrip> spécial destiné à la navigation et à la manipulation de contrôles sur votre formulaire qui sont liés aux données.</span><span class="sxs-lookup"><span data-stu-id="ff3e1-103">The <xref:System.Windows.Forms.BindingNavigator> control is a special-purpose <xref:System.Windows.Forms.ToolStrip> control that is intended for navigating and manipulating controls on your form that are bound to data.</span></span>

<span data-ttu-id="ff3e1-104">Étant donné qu’il s’agit d’un contrôle <xref:System.Windows.Forms.ToolStrip>, le composant <xref:System.Windows.Forms.BindingNavigator> peut être facilement modifié pour inclure des commandes supplémentaires ou alternatives pour l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="ff3e1-104">Because it is a <xref:System.Windows.Forms.ToolStrip> control, the <xref:System.Windows.Forms.BindingNavigator> component can be easily modified to include additional or alternative commands for the user.</span></span>

<span data-ttu-id="ff3e1-105">Dans la procédure suivante, un contrôle <xref:System.Windows.Forms.TextBox> est lié aux données et le contrôle <xref:System.Windows.Forms.ToolStrip> ajouté au formulaire est modifié pour inclure les boutons charger, enregistrer et annuler.</span><span class="sxs-lookup"><span data-stu-id="ff3e1-105">In the following procedure, a <xref:System.Windows.Forms.TextBox> control is bound to data, and the <xref:System.Windows.Forms.ToolStrip> control that is added to the form is modified to include load, save, and cancel buttons.</span></span>

## <a name="add-load-save-and-cancel-buttons-to-the-bindingnavigator-component"></a><span data-ttu-id="ff3e1-106">Ajouter des boutons charger, enregistrer et annuler au composant BindingNavigator</span><span class="sxs-lookup"><span data-stu-id="ff3e1-106">Add load, save, and cancel buttons to the BindingNavigator component</span></span>

1. <span data-ttu-id="ff3e1-107">Dans Visual Studio, ajoutez un contrôle <xref:System.Windows.Forms.TextBox> à votre formulaire.</span><span class="sxs-lookup"><span data-stu-id="ff3e1-107">In Visual Studio, add a <xref:System.Windows.Forms.TextBox> control to your form.</span></span>

2. <span data-ttu-id="ff3e1-108">Liez-le à un <xref:System.Windows.Forms.BindingSource>, qui est lié à une source de données.</span><span class="sxs-lookup"><span data-stu-id="ff3e1-108">Bind it to a <xref:System.Windows.Forms.BindingSource>, which is bound to a data source.</span></span> <span data-ttu-id="ff3e1-109">Pour cet exemple, le <xref:System.Windows.Forms.BindingSource> est lié à une base de données.</span><span class="sxs-lookup"><span data-stu-id="ff3e1-109">For this example, the <xref:System.Windows.Forms.BindingSource> is bound to a database.</span></span>

3. <span data-ttu-id="ff3e1-110">Une fois le DataSet et l’adaptateur de table générés, faites glisser un contrôle <xref:System.Windows.Forms.BindingNavigator> vers le formulaire.</span><span class="sxs-lookup"><span data-stu-id="ff3e1-110">After the dataset and table adapter are generated, drag a <xref:System.Windows.Forms.BindingNavigator> control to the form.</span></span>

4. <span data-ttu-id="ff3e1-111">Affectez à la propriété <xref:System.Windows.Forms.BindingNavigator.BindingSource%2A> du contrôle <xref:System.Windows.Forms.BindingNavigator> la <xref:System.Windows.Forms.BindingSource> sur le formulaire lié aux contrôles.</span><span class="sxs-lookup"><span data-stu-id="ff3e1-111">Set the <xref:System.Windows.Forms.BindingNavigator> control's <xref:System.Windows.Forms.BindingNavigator.BindingSource%2A> property to the <xref:System.Windows.Forms.BindingSource> on the form that is bound to the controls.</span></span>

5. <span data-ttu-id="ff3e1-112">Sélectionnez le contrôle <xref:System.Windows.Forms.BindingNavigator>.</span><span class="sxs-lookup"><span data-stu-id="ff3e1-112">Select the <xref:System.Windows.Forms.BindingNavigator> control.</span></span>

6. <span data-ttu-id="ff3e1-113">Cliquez sur le glyphe de balise active (![glyphe de balise active](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) pour afficher la boîte de dialogue **tâches BindingNavigator** et sélectionner **modifier les éléments**.</span><span class="sxs-lookup"><span data-stu-id="ff3e1-113">Click the smart tag glyph (![Smart Tag Glyph](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) so the **BindingNavigator Tasks** dialog appears and select **Edit Items**.</span></span>

     <span data-ttu-id="ff3e1-114">L **'éditeur de collections Items** s’affiche.</span><span class="sxs-lookup"><span data-stu-id="ff3e1-114">The **Items Collection Editor** appears.</span></span>

7. <span data-ttu-id="ff3e1-115">Dans l **'éditeur de collections Items**, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="ff3e1-115">In the **Items Collection Editor**, complete the following:</span></span>

    1. <span data-ttu-id="ff3e1-116">Ajoutez un <xref:System.Windows.Forms.ToolStripSeparator> et trois éléments <xref:System.Windows.Forms.ToolStripButton> en sélectionnant le type de <xref:System.Windows.Forms.ToolStripItem> approprié et en cliquant sur le bouton **Ajouter** .</span><span class="sxs-lookup"><span data-stu-id="ff3e1-116">Add a <xref:System.Windows.Forms.ToolStripSeparator> and three <xref:System.Windows.Forms.ToolStripButton> items by selecting the appropriate type of <xref:System.Windows.Forms.ToolStripItem> and clicking the **Add** button.</span></span>

    2. <span data-ttu-id="ff3e1-117">Affectez à la propriété <xref:System.Windows.Forms.ToolStripItem.Name%2A> des boutons la valeur **LoadButton**, **SaveButton**et **CancelButton**, respectivement.</span><span class="sxs-lookup"><span data-stu-id="ff3e1-117">Set the <xref:System.Windows.Forms.ToolStripItem.Name%2A> property of the buttons to **LoadButton**, **SaveButton**, and **CancelButton**, respectively.</span></span>

    3. <span data-ttu-id="ff3e1-118">Affectez la valeur **Load**, **Save**et **Cancel**à la propriété <xref:System.Windows.Forms.ToolStripItem.Text%2A> des boutons.</span><span class="sxs-lookup"><span data-stu-id="ff3e1-118">Set the <xref:System.Windows.Forms.ToolStripItem.Text%2A> property of the buttons to **Load**, **Save**, and **Cancel**.</span></span>

    4. <span data-ttu-id="ff3e1-119">Définissez la propriété <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> pour chacun des boutons sur **texte**.</span><span class="sxs-lookup"><span data-stu-id="ff3e1-119">Set the <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> property for each of the buttons to **Text**.</span></span> <span data-ttu-id="ff3e1-120">Vous pouvez également définir cette propriété sur **image** ou **ImageAndText**, et définir l’image à afficher dans la propriété <xref:System.Windows.Forms.ToolStripItem.Image%2A>.</span><span class="sxs-lookup"><span data-stu-id="ff3e1-120">Alternatively, you can set this property to **Image** or **ImageAndText**, and set the image to be displayed in the <xref:System.Windows.Forms.ToolStripItem.Image%2A> property.</span></span>

    5. <span data-ttu-id="ff3e1-121">Cliquez sur **OK** pour fermer la boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="ff3e1-121">Click **OK** to close the dialog box.</span></span> <span data-ttu-id="ff3e1-122">Les boutons sont ajoutés au <xref:System.Windows.Forms.ToolStrip>.</span><span class="sxs-lookup"><span data-stu-id="ff3e1-122">The buttons are added to the <xref:System.Windows.Forms.ToolStrip>.</span></span>

8. <span data-ttu-id="ff3e1-123">Cliquez avec le bouton droit sur le formulaire, puis choisissez **afficher le code**.</span><span class="sxs-lookup"><span data-stu-id="ff3e1-123">Right-click the form and choose **View Code**.</span></span>

9. <span data-ttu-id="ff3e1-124">Dans l’éditeur de code, recherchez la ligne de code qui charge les données dans l’adaptateur de table.</span><span class="sxs-lookup"><span data-stu-id="ff3e1-124">In the Code Editor, find the line of code that loads data into the table adapter.</span></span> <span data-ttu-id="ff3e1-125">Ce code a été généré lors de la configuration de la liaison de données à l’étape 2.</span><span class="sxs-lookup"><span data-stu-id="ff3e1-125">This code was generated when you set up the data binding in step 2.</span></span> <span data-ttu-id="ff3e1-126">Le code doit ressembler à ce qui suit : `TableAdapterName.Fill(DataSetName.TableName)`.</span><span class="sxs-lookup"><span data-stu-id="ff3e1-126">The code should be similar to the following: `TableAdapterName.Fill(DataSetName.TableName)`.</span></span> <span data-ttu-id="ff3e1-127">Il se trouve très probablement dans l’événement <xref:System.Windows.Forms.Form.Load> du formulaire.</span><span class="sxs-lookup"><span data-stu-id="ff3e1-127">It will most likely be in the form's <xref:System.Windows.Forms.Form.Load> event.</span></span>

10. <span data-ttu-id="ff3e1-128">Créez un gestionnaire d’événements pour l’événement <xref:System.Windows.Forms.ToolStripItem.Click> du <xref:System.Windows.Forms.ToolStripButton> de **charge** que vous avez créé précédemment et déplacez-y ce code de chargement de données.</span><span class="sxs-lookup"><span data-stu-id="ff3e1-128">Create an event handler for the <xref:System.Windows.Forms.ToolStripItem.Click> event of the **Load** <xref:System.Windows.Forms.ToolStripButton> you created earlier and move this data-loading code into it.</span></span>

     <span data-ttu-id="ff3e1-129">Votre code doit maintenant ressembler à ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="ff3e1-129">Your code should now look similar to the following:</span></span>

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

11. <span data-ttu-id="ff3e1-130">Créez un gestionnaire d’événements pour l’événement <xref:System.Windows.Forms.ToolStripItem.Click> de l'<xref:System.Windows.Forms.ToolStripButton> d' **enregistrement** que vous avez créé précédemment et écrivez le code pour mettre à jour les données dans la table à laquelle le contrôle est lié.</span><span class="sxs-lookup"><span data-stu-id="ff3e1-130">Create an event handler for the <xref:System.Windows.Forms.ToolStripItem.Click> event of the **Save**<xref:System.Windows.Forms.ToolStripButton> you created earlier and write code to update the data within the table the control is bound to.</span></span>

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
    > <span data-ttu-id="ff3e1-131">Dans certains cas, le composant <xref:System.Windows.Forms.BindingNavigator> a déjà un bouton **Enregistrer** , mais aucun code n’a été généré par le Concepteur Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="ff3e1-131">In some cases, the <xref:System.Windows.Forms.BindingNavigator> component already has a **Save** button, but no code has been generated by the Windows Forms Designer.</span></span> <span data-ttu-id="ff3e1-132">Dans ce cas, vous pouvez placer le code précédent dans le gestionnaire d’événements <xref:System.Windows.Forms.ToolStripItem.Click> pour ce bouton, plutôt que de créer un bouton entièrement nouveau sur l' <xref:System.Windows.Forms.ToolStrip>.</span><span class="sxs-lookup"><span data-stu-id="ff3e1-132">In this case, you can place the preceding code in the <xref:System.Windows.Forms.ToolStripItem.Click> event handler for that button, rather than creating an entirely new button on the <xref:System.Windows.Forms.ToolStrip>.</span></span> <span data-ttu-id="ff3e1-133">Toutefois, le bouton est désactivé par défaut. vous devez donc définir la propriété <xref:System.Windows.Forms.ToolBarButton.Enabled%2A> du bouton sur `true` pour que le bouton fonctionne correctement.</span><span class="sxs-lookup"><span data-stu-id="ff3e1-133">However, the button is disabled by default, so you must set the <xref:System.Windows.Forms.ToolBarButton.Enabled%2A> property of the button to `true` to have the button function correctly.</span></span>

12. <span data-ttu-id="ff3e1-134">Créez un gestionnaire d’événements pour l’événement <xref:System.Windows.Forms.ToolStripItem.Click> du <xref:System.Windows.Forms.ToolStripButton> d' **annulation** que vous avez créé précédemment et écrivez du code pour annuler les modifications apportées à l’enregistrement de données qui s’affiche.</span><span class="sxs-lookup"><span data-stu-id="ff3e1-134">Create an event handler for the <xref:System.Windows.Forms.ToolStripItem.Click> event of the **Cancel** <xref:System.Windows.Forms.ToolStripButton> you created earlier and write code to cancel any changes to the data record that is displayed.</span></span>

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
    > <span data-ttu-id="ff3e1-135">La méthode <xref:System.Windows.Forms.BindingSource.CancelEdit%2A> est limitée à la ligne de données.</span><span class="sxs-lookup"><span data-stu-id="ff3e1-135">The <xref:System.Windows.Forms.BindingSource.CancelEdit%2A> method is scoped to the row of data.</span></span> <span data-ttu-id="ff3e1-136">Enregistrez les modifications apportées lors de l’affichage de cet enregistrement individuel avant de passer à l’enregistrement suivant.</span><span class="sxs-lookup"><span data-stu-id="ff3e1-136">Save any changes you make while viewing that individual record before navigating to the next record.</span></span>

## <a name="see-also"></a><span data-ttu-id="ff3e1-137">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ff3e1-137">See also</span></span>

- <xref:System.Windows.Forms.BindingNavigator>
- <xref:System.Windows.Forms.BindingSource>
- <xref:System.Windows.Forms.ToolStrip>
- [<span data-ttu-id="ff3e1-138">BindingNavigator, contrôle</span><span class="sxs-lookup"><span data-stu-id="ff3e1-138">BindingNavigator Control</span></span>](bindingnavigator-control-windows-forms.md)
- [<span data-ttu-id="ff3e1-139">Vue d'ensemble du composant BindingSource</span><span class="sxs-lookup"><span data-stu-id="ff3e1-139">BindingSource Component Overview</span></span>](bindingsource-component-overview.md)
