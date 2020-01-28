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
# <a name="how-to-add-load-save-and-cancel-buttons-to-the-windows-forms-bindingnavigator-control"></a>Comment : ajouter des boutons Charger, Enregistrer et Annuler au contrôle BindingNavigator Windows Forms

Le contrôle <xref:System.Windows.Forms.BindingNavigator> est un contrôle <xref:System.Windows.Forms.ToolStrip> spécial destiné à la navigation et à la manipulation de contrôles sur votre formulaire qui sont liés aux données.

Étant donné qu’il s’agit d’un contrôle <xref:System.Windows.Forms.ToolStrip>, le composant <xref:System.Windows.Forms.BindingNavigator> peut être facilement modifié pour inclure des commandes supplémentaires ou alternatives pour l’utilisateur.

Dans la procédure suivante, un contrôle <xref:System.Windows.Forms.TextBox> est lié aux données et le contrôle <xref:System.Windows.Forms.ToolStrip> ajouté au formulaire est modifié pour inclure les boutons charger, enregistrer et annuler.

## <a name="add-load-save-and-cancel-buttons-to-the-bindingnavigator-component"></a>Ajouter des boutons charger, enregistrer et annuler au composant BindingNavigator

1. Dans Visual Studio, ajoutez un contrôle <xref:System.Windows.Forms.TextBox> à votre formulaire.

2. Liez-le à un <xref:System.Windows.Forms.BindingSource>, qui est lié à une source de données. Pour cet exemple, le <xref:System.Windows.Forms.BindingSource> est lié à une base de données.

3. Une fois le DataSet et l’adaptateur de table générés, faites glisser un contrôle <xref:System.Windows.Forms.BindingNavigator> vers le formulaire.

4. Affectez à la propriété <xref:System.Windows.Forms.BindingNavigator.BindingSource%2A> du contrôle <xref:System.Windows.Forms.BindingNavigator> la <xref:System.Windows.Forms.BindingSource> sur le formulaire lié aux contrôles.

5. Sélectionnez le contrôle <xref:System.Windows.Forms.BindingNavigator>.

6. Cliquez sur le glyphe de balise active (![glyphe de balise active](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) pour afficher la boîte de dialogue **tâches BindingNavigator** et sélectionner **modifier les éléments**.

     L **'éditeur de collections Items** s’affiche.

7. Dans l **'éditeur de collections Items**, procédez comme suit :

    1. Ajoutez un <xref:System.Windows.Forms.ToolStripSeparator> et trois éléments <xref:System.Windows.Forms.ToolStripButton> en sélectionnant le type de <xref:System.Windows.Forms.ToolStripItem> approprié et en cliquant sur le bouton **Ajouter** .

    2. Affectez à la propriété <xref:System.Windows.Forms.ToolStripItem.Name%2A> des boutons la valeur **LoadButton**, **SaveButton**et **CancelButton**, respectivement.

    3. Affectez la valeur **Load**, **Save**et **Cancel**à la propriété <xref:System.Windows.Forms.ToolStripItem.Text%2A> des boutons.

    4. Définissez la propriété <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> pour chacun des boutons sur **texte**. Vous pouvez également définir cette propriété sur **image** ou **ImageAndText**, et définir l’image à afficher dans la propriété <xref:System.Windows.Forms.ToolStripItem.Image%2A>.

    5. Cliquez sur **OK** pour fermer la boîte de dialogue. Les boutons sont ajoutés au <xref:System.Windows.Forms.ToolStrip>.

8. Cliquez avec le bouton droit sur le formulaire, puis choisissez **afficher le code**.

9. Dans l’éditeur de code, recherchez la ligne de code qui charge les données dans l’adaptateur de table. Ce code a été généré lors de la configuration de la liaison de données à l’étape 2. Le code doit ressembler à ce qui suit : `TableAdapterName.Fill(DataSetName.TableName)`. Il se trouve très probablement dans l’événement <xref:System.Windows.Forms.Form.Load> du formulaire.

10. Créez un gestionnaire d’événements pour l’événement <xref:System.Windows.Forms.ToolStripItem.Click> du <xref:System.Windows.Forms.ToolStripButton> de **charge** que vous avez créé précédemment et déplacez-y ce code de chargement de données.

     Votre code doit maintenant ressembler à ce qui suit :

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

11. Créez un gestionnaire d’événements pour l’événement <xref:System.Windows.Forms.ToolStripItem.Click> de l'<xref:System.Windows.Forms.ToolStripButton> d' **enregistrement** que vous avez créé précédemment et écrivez le code pour mettre à jour les données dans la table à laquelle le contrôle est lié.

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
    > Dans certains cas, le composant <xref:System.Windows.Forms.BindingNavigator> a déjà un bouton **Enregistrer** , mais aucun code n’a été généré par le Concepteur Windows Forms. Dans ce cas, vous pouvez placer le code précédent dans le gestionnaire d’événements <xref:System.Windows.Forms.ToolStripItem.Click> pour ce bouton, plutôt que de créer un bouton entièrement nouveau sur l' <xref:System.Windows.Forms.ToolStrip>. Toutefois, le bouton est désactivé par défaut. vous devez donc définir la propriété <xref:System.Windows.Forms.ToolBarButton.Enabled%2A> du bouton sur `true` pour que le bouton fonctionne correctement.

12. Créez un gestionnaire d’événements pour l’événement <xref:System.Windows.Forms.ToolStripItem.Click> du <xref:System.Windows.Forms.ToolStripButton> d' **annulation** que vous avez créé précédemment et écrivez du code pour annuler les modifications apportées à l’enregistrement de données qui s’affiche.

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
    > La méthode <xref:System.Windows.Forms.BindingSource.CancelEdit%2A> est limitée à la ligne de données. Enregistrez les modifications apportées lors de l’affichage de cet enregistrement individuel avant de passer à l’enregistrement suivant.

## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.BindingNavigator>
- <xref:System.Windows.Forms.BindingSource>
- <xref:System.Windows.Forms.ToolStrip>
- [BindingNavigator, contrôle](bindingnavigator-control-windows-forms.md)
- [Vue d'ensemble du composant BindingSource](bindingsource-component-overview.md)
