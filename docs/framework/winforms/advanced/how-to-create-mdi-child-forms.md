---
title: 'Procédure : créer des formulaires enfants MDI'
ms.date: 03/30/2017
dev_langs:
- CSharp
- CPP
- VB
helpviewer_keywords:
- MDI [Windows Forms], creating forms
- child forms
ms.assetid: 164b69bb-2eca-4339-ada3-0679eb2c6dda
ms.openlocfilehash: f5e8682caf658d159f044528f040b99676355448
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69040114"
---
# <a name="how-to-create-mdi-child-forms"></a>Procédure : Créer des formulaires MDI enfants

Les formulaires enfants MDI sont un élément essentiel des [applications d’interface multidocument (MDI, multiple-document interface)](multiple-document-interface-mdi-applications.md), car ces formulaires représentent le centre de l’interaction de l’utilisateur.

Dans la procédure suivante, vous allez utiliser Visual Studio pour créer un formulaire MDI enfant qui affiche un <xref:System.Windows.Forms.RichTextBox> contrôle, semblable à la plupart des applications de traitement de texte. En remplaçant le <xref:System.Windows.Forms> contrôle par d’autres contrôles, tels que le <xref:System.Windows.Forms.DataGridView> contrôle ou un mélange de contrôles, vous pouvez créer des fenêtres MDI enfants (et, par extension, des applications MDI) avec diverses possibilités.

## <a name="create-mdi-child-forms"></a>Créer des formulaires MDI enfants

1. Créez un nouveau Windows Forms projet d’application dans Visual Studio. Dans la fenêtre **Propriétés** du formulaire, affectez à <xref:System.Windows.Forms.Form.IsMdiContainer%2A> `true` sa propriété la valeur `WindowsState` et à `Maximized`sa propriété la valeur.

   Ainsi, vous désignez le formulaire comme le conteneur MDI des fenêtres enfants.

2. Faites glisser un contrôle <xref:System.Windows.Forms.MenuStrip> de la `Toolbox` vers le formulaire. Affectez `Text` à sa propriété la valeur **file**.

3. Cliquez sur les points de suspension (...) en regard de la propriété Items, puis cliquez sur **Ajouter** pour ajouter deux éléments de menu de la barre d’outils enfants. Définissez la `Text` propriété pour ces éléments sur **nouveau** et **fenêtre**.

4. Dans l’**Explorateur de solutions**, cliquez avec le bouton droit sur le projet, puis sélectionnez **Ajouter** > **Nouvel élément**.

5. Dans la boîte de dialogue **Ajouter un nouvel élément** , sélectionnez **Windows Form** (en Visual Basic ou C#en visuel) ou **Windows Forms application (.net)** ( C++en visuel) à partir du volet **modèles** . Dans la zone **nom** , nommez le formulaire **Form2**. Sélectionnez **ouvrir** pour ajouter le formulaire au projet.

    > [!NOTE]
    > Le formulaire MDI enfant que vous avez créé lors de cette étape est un Windows Form standard. Il a donc une propriété <xref:System.Windows.Forms.Form.Opacity%2A>, ce qui vous permet de contrôler la transparence du formulaire. Cependant, la propriété <xref:System.Windows.Forms.Form.Opacity%2A> a été conçue pour les fenêtres de niveau supérieur. Ne l'utilisez pas avec des formulaires MDI enfants, car des problèmes de peinture peuvent survenir.

     Ce formulaire sera le modèle pour vos formulaires MDI enfants.

     Le **Concepteur Windows Forms** s’ouvre et affiche **Form2**.

6. À partir de la **boîte à outils**, faites glisser un contrôle **RichTextBox** vers le formulaire.

7. Dans la fenêtre **Propriétés** , affectez `Anchor` à la propriété la valeur **Top, à gauche** et à la propriété la `Dock` valeur **Fill**.

   Ainsi, le contrôle <xref:System.Windows.Forms.RichTextBox> remplit complètement la zone de formulaire MDI enfant, même quand le formulaire est redimensionné.

8. Double-cliquez sur l’élément de menu nouveau <xref:System.Windows.Forms.Control.Click> pour créer un gestionnaire d’événements pour celui-ci.

9. Insérez un code semblable au suivant pour créer un nouveau formulaire MDI enfant lorsque l’utilisateur clique sur l’élément **de menu nouveau** .

   > [!NOTE]
   > Dans l'exemple suivant, le gestionnaire d'événements gère l'événement <xref:System.Windows.Forms.Control.Click> pour `MenuItem2`. Notez que, selon les spécificités de votre architecture d’application, votre **nouvel** élément de menu peut ne pas être `MenuItem2`.

    ```vb
    Protected Sub MDIChildNew_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles MenuItem2.Click
       Dim NewMDIChild As New Form2()
       'Set the Parent Form of the Child window.
       NewMDIChild.MdiParent = Me
       'Display the new form.
       NewMDIChild.Show()
    End Sub
    ```

    ```csharp
    protected void MDIChildNew_Click(object sender, System.EventArgs e){
       Form2 newMDIChild = new Form2();
       // Set the Parent Form of the Child window.
       newMDIChild.MdiParent = this;
       // Display the new form.
       newMDIChild.Show();
    }
    ```

    ```cpp
    private:
       void menuItem2_Click(System::Object ^ sender,
          System::EventArgs ^ e)
       {
          Form2^ newMDIChild = gcnew Form2();
          // Set the Parent Form of the Child window.
          newMDIChild->MdiParent = this;
          // Display the new form.
          newMDIChild->Show();
       }
    ```

   Dans C++, ajoutez la directive `#include` suivante en haut de Form1. h:

   ```cpp
   #include "Form2.h"
   ```

10. Dans la liste déroulante en haut de la fenêtre **Propriétés** , sélectionnez la bande de menus qui correspond à la bande de menu **fichier** , puis <xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A> affectez à la <xref:System.Windows.Forms.ToolStripMenuItem>propriété la valeur de la fenêtre.

    Cela permet au menu **fenêtre** de conserver une liste des fenêtres MDI enfants ouvertes avec une coche en regard de la fenêtre enfant active.

11. Appuyez sur **F5** pour exécuter l’application. En sélectionnant **nouveau** dans le menu **fichier** , vous pouvez créer des formulaires enfants MDI, qui sont suivis de dans l’élément de menu **fenêtre** .

    > [!NOTE]
    > Quand un formulaire MDI enfant a un composant <xref:System.Windows.Forms.MainMenu> (avec, généralement, une structure d'éléments de menu) et qu'il est ouvert dans un formulaire MDI parent qui a un composant <xref:System.Windows.Forms.MainMenu> (avec, généralement, une structure d'éléments de menu), les éléments de menu fusionnent automatiquement si vous avez défini la propriété <xref:System.Windows.Forms.MenuItem.MergeType%2A> (et, éventuellement, la propriété <xref:System.Windows.Forms.MenuItem.MergeOrder%2A>). Affectez la valeur <xref:System.Windows.Forms.MenuMerge.MergeItems> à la propriété <xref:System.Windows.Forms.MenuItem.MergeType%2A> des deux composants <xref:System.Windows.Forms.MainMenu> et à tous les éléments de menu du formulaire enfant. Définissez aussi la propriété <xref:System.Windows.Forms.MenuItem.MergeOrder%2A> pour que les éléments de menu des deux menus apparaissent dans l'ordre souhaité. De plus, sachez que quand vous fermez un formulaire MDI parent, chaque formulaire MDI enfant déclenche un événement <xref:System.Windows.Forms.Form.Closing> avant que l'événement <xref:System.Windows.Forms.Form.Closing> pour le parent MDI soit déclenché. L'annulation de l'événement <xref:System.Windows.Forms.Form.Closing>  d'un enfant MDI n'empêchera pas le déclenchement de l'événement <xref:System.Windows.Forms.Form.Closing> du MDI parent. Toutefois, l'argument <xref:System.ComponentModel.CancelEventArgs> pour l'événement <xref:System.Windows.Forms.Form.Closing> du MDI parent prendra la valeur `true`. Vous pouvez forcer la fermeture du MDI parent et de tous les formulaires MDI enfants en affectant la valeur `false` à l'argument <xref:System.ComponentModel.CancelEventArgs>.

## <a name="see-also"></a>Voir aussi

- [Applications d’interface multidocument (MDI, Multiple Document Interface)](multiple-document-interface-mdi-applications.md)
- [Guide pratique pour Créer des formulaires MDI parents](how-to-create-mdi-parent-forms.md)
- [Guide pratique pour Déterminer l’enfant MDI actif](how-to-determine-the-active-mdi-child.md)
- [Guide pratique pour Envoyer des données à l’enfant MDI actif](how-to-send-data-to-the-active-mdi-child.md)
- [Guide pratique pour Réorganiser les formulaires enfants MDI](how-to-arrange-mdi-child-forms.md)
