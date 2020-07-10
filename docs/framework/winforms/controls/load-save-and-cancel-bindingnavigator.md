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
# <a name="how-to-add-load-save-and-cancel-buttons-to-the-windows-forms-bindingnavigator-control"></a>Comment : ajouter des boutons Charger, Enregistrer et Annuler au contrôle BindingNavigator Windows Forms

Le <xref:System.Windows.Forms.BindingNavigator> contrôle est un <xref:System.Windows.Forms.ToolStrip> contrôle spécial destiné à la navigation et à la manipulation de contrôles sur votre formulaire qui sont liés aux données.

Étant donné qu’il s’agit d’un <xref:System.Windows.Forms.ToolStrip> contrôle, le <xref:System.Windows.Forms.BindingNavigator> composant peut être facilement modifié pour inclure des commandes supplémentaires ou alternatives pour l’utilisateur.

Dans la procédure suivante, un <xref:System.Windows.Forms.TextBox> contrôle est lié aux données et le <xref:System.Windows.Forms.ToolStrip> contrôle ajouté au formulaire est modifié pour inclure les boutons charger, enregistrer et annuler.

## <a name="add-load-save-and-cancel-buttons-to-the-bindingnavigator-component"></a>Ajouter des boutons charger, enregistrer et annuler au composant BindingNavigator

1. Dans Visual Studio, ajoutez un <xref:System.Windows.Forms.TextBox> contrôle à votre formulaire.

2. Liez-le à un <xref:System.Windows.Forms.BindingSource> , qui est lié à une source de données. Pour cet exemple, le <xref:System.Windows.Forms.BindingSource> est lié à une base de données.

3. Une fois le DataSet et l’adaptateur de table générés, faites glisser un <xref:System.Windows.Forms.BindingNavigator> contrôle vers le formulaire.

4. Affectez à la <xref:System.Windows.Forms.BindingNavigator> propriété du contrôle <xref:System.Windows.Forms.BindingNavigator.BindingSource%2A> la valeur <xref:System.Windows.Forms.BindingSource> sur le formulaire qui est lié aux contrôles.

5. Sélectionnez le contrôle <xref:System.Windows.Forms.BindingNavigator>.

6. Cliquez sur le glyphe actions du concepteur ( ![ petite flèche noire ](./media/designer-actions-glyph.gif) ) pour afficher la boîte de dialogue **tâches BindingNavigator** et sélectionnez **modifier les éléments**.

     L **'éditeur de collections Items** s’affiche.

7. Dans l **'éditeur de collections Items**, procédez comme suit :

    1. Ajoutez un <xref:System.Windows.Forms.ToolStripSeparator> et trois <xref:System.Windows.Forms.ToolStripButton> éléments en sélectionnant le type approprié <xref:System.Windows.Forms.ToolStripItem> et en cliquant sur le bouton **Ajouter** .

    2. Définissez la <xref:System.Windows.Forms.ToolStripItem.Name%2A> propriété des boutons sur **LoadButton**, **SaveButton**et **CancelButton**, respectivement.

    3. Affectez <xref:System.Windows.Forms.ToolStripItem.Text%2A> à la propriété des boutons la valeur **Load**, **Save**et **Cancel**.

    4. Définissez la <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> propriété pour chacun des boutons sur **texte**. Vous pouvez également définir cette propriété sur **image** ou **ImageAndText**, et définir l’image à afficher dans la <xref:System.Windows.Forms.ToolStripItem.Image%2A> propriété.

    5. Cliquez sur **OK** pour fermer la boîte de dialogue. Les boutons sont ajoutés au <xref:System.Windows.Forms.ToolStrip> .

8. Cliquez avec le bouton droit sur le formulaire, puis choisissez **afficher le code**.

9. Dans l’éditeur de code, recherchez la ligne de code qui charge les données dans l’adaptateur de table. Ce code a été généré lors de la configuration de la liaison de données à l’étape 2. Le code doit ressembler à ce qui suit : `TableAdapterName.Fill(DataSetName.TableName)` . Il sera probablement dans l’événement du formulaire <xref:System.Windows.Forms.Form.Load> .

10. Créez un gestionnaire d’événements pour l' <xref:System.Windows.Forms.ToolStripItem.Click> événement de la **charge** <xref:System.Windows.Forms.ToolStripButton> que vous avez créée précédemment et déplacez-y ce code de chargement de données.

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

11. Créez un gestionnaire d’événements pour l' <xref:System.Windows.Forms.ToolStripItem.Click> événement de l' **enregistrement** <xref:System.Windows.Forms.ToolStripButton> que vous avez créé précédemment et écrivez du code pour mettre à jour les données dans la table à laquelle le contrôle est lié.

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
    > Dans certains cas, le <xref:System.Windows.Forms.BindingNavigator> composant a déjà un bouton **Enregistrer** , mais aucun code n’a été généré par la Concepteur Windows Forms. Dans ce cas, vous pouvez placer le code précédent dans le <xref:System.Windows.Forms.ToolStripItem.Click> Gestionnaire d’événements pour ce bouton, plutôt que de créer un bouton entièrement nouveau sur le <xref:System.Windows.Forms.ToolStrip> . Toutefois, le bouton est désactivé par défaut. vous devez donc définir la <xref:System.Windows.Forms.ToolBarButton.Enabled%2A> propriété du bouton sur `true` pour que le bouton fonctionne correctement.

12. Créez un gestionnaire d’événements pour l' <xref:System.Windows.Forms.ToolStripItem.Click> événement de l' **annulation** <xref:System.Windows.Forms.ToolStripButton> que vous avez créée précédemment et écrivez du code pour annuler les modifications apportées à l’enregistrement de données qui s’affiche.

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
    > La <xref:System.Windows.Forms.BindingSource.CancelEdit%2A> portée de la méthode est limitée à la ligne de données. Enregistrez les modifications apportées lors de l’affichage de cet enregistrement individuel avant de passer à l’enregistrement suivant.

## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.BindingNavigator>
- <xref:System.Windows.Forms.BindingSource>
- <xref:System.Windows.Forms.ToolStrip>
- [Contrôle BindingNavigator](bindingnavigator-control-windows-forms.md)
- [Vue d’ensemble du composant BindingSource](bindingsource-component-overview.md)
