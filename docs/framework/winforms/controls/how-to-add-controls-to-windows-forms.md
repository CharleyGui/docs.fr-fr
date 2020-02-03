---
title: ajouter des contrôles
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Windows Forms controls, adding to form
- controls [Windows Forms], adding
ms.assetid: 2af86001-9d62-4154-87fb-66db2c3cd9fd
ms.openlocfilehash: 560089a23fbcccb0f0d5683a95ad06dd9c59556d
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743955"
---
# <a name="how-to-add-controls-to-windows-forms"></a>Comment : ajouter des contrôles à des Windows Forms

La plupart des formulaires sont conçus en ajoutant des contrôles à la surface du formulaire pour définir une interface utilisateur. Un *contrôle* est un composant d’un formulaire utilisé pour afficher des informations ou accepter une entrée d’utilisateur. Pour plus d’informations sur les contrôles, consultez [Windows Forms des contrôles](index.md).

## <a name="to-draw-a-control-on-a-form"></a>Pour dessiner un contrôle sur un formulaire

1. Ouvrez le formulaire. Pour plus d’informations, consultez [Comment : afficher des Windows Forms dans le concepteur](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/w5yd62ts(v=vs.100)).

2. Dans la **boîte à outils**, cliquez sur le contrôle que vous souhaitez ajouter à votre formulaire.

3. Dans le formulaire, cliquez à l’endroit où vous souhaitez placer l’angle supérieur gauche du contrôle, puis faites glisser le bouton vers l’emplacement où vous souhaitez placer le coin inférieur droit du contrôle.

    Le contrôle est ajouté au formulaire avec l’emplacement et la taille spécifiés.

    > [!NOTE]
    > Une taille par défaut est définie pour chaque contrôle. Vous pouvez ajouter un contrôle à votre formulaire à la taille par défaut du contrôle en le faisant glisser de la **boîte à outils** vers le formulaire.

## <a name="to-drag-a-control-to-a-form"></a>Pour faire glisser un contrôle vers un formulaire

1. Ouvrez le formulaire. Pour plus d’informations, consultez [Comment : afficher des Windows Forms dans le concepteur](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/w5yd62ts(v=vs.100)).

2. Dans la **boîte à outils**, cliquez sur le contrôle souhaité et faites-le glisser vers votre formulaire.

    Le contrôle est ajouté au formulaire à l’emplacement spécifié dans sa taille par défaut.

    > [!NOTE]
    > Vous pouvez double-cliquer sur un contrôle dans la **boîte à outils** pour l’ajouter dans le coin supérieur gauche du formulaire dans sa taille par défaut.

    Vous pouvez également ajouter dynamiquement des contrôles à un formulaire au moment de l’exécution. Dans l’exemple de code suivant, un contrôle de <xref:System.Windows.Forms.TextBox> est ajouté au formulaire lorsqu’un utilisateur clique sur un contrôle <xref:System.Windows.Forms.Button>.

    > [!NOTE]
    > La procédure suivante nécessite l’existence d’un formulaire avec un contrôle **Button** , `Button1`, déjà placé sur celui-ci.

## <a name="to-add-a-control-to-a-form-programmatically"></a>Pour ajouter par programmation un contrôle à un formulaire

1. Dans la méthode qui gère l’événement `Click` du bouton dans la classe de votre formulaire, insérez un code semblable au suivant pour ajouter une référence à votre variable de contrôle, définir le `Location`du contrôle et ajouter le contrôle.

    ```vb
    Private Sub Button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Button1.Click
       Dim MyText As New TextBox()
       MyText.Location = New Point(25, 25)
       Me.Controls.Add(MyText)
    End Sub
    ```

    ```csharp
    private void button1_Click(object sender, System.EventArgs e)
    {
       TextBox myText = new TextBox();
       myText.Location = new Point(25,25);
       this.Controls.Add (myText);
    }
    ```

    ```cpp
    private:
      System::Void button1_Click(System::Object ^  sender,
        System::EventArgs ^  e)
      {
        TextBox ^ myText = gcnew TextBox();
        myText->Location = Point(25,25);
        this->Controls->Add(myText);
      }
    ```

    > [!NOTE]
    > Vous pouvez également ajouter du code pour initialiser d’autres propriétés du contrôle.

    > [!IMPORTANT]
    > Vous pouvez exposer votre ordinateur local à un risque de sécurité sur le réseau en référençant un `UserControl`malveillant. Cela ne serait qu’une préoccupation dans le cas d’une personne malveillante qui crée un contrôle personnalisé nuisible, puis de l’ajouter par erreur à votre projet.

## <a name="see-also"></a>Voir aussi

- [Contrôles Windows Forms](index.md)
- [Guide pratique pour redimensionner des contrôles sur des Windows Forms](how-to-resize-controls-on-windows-forms.md)
- [Guide pratique pour définir le texte affiché par un contrôle Windows Forms](how-to-set-the-text-displayed-by-a-windows-forms-control.md)
- [Contrôles à utiliser dans les Windows Forms](controls-to-use-on-windows-forms.md)
