---
title: 'Comment : créer une liste des fenêtres MDI avec MenuStrip'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- MDI [Windows Forms], creating window lists
- MenuStrip control [Windows Forms], creating window lists
ms.assetid: 04fb414b-811f-4a83-aab6-b4a24646dec5
ms.openlocfilehash: f013c3df2ab5783a22fe2c34402dc53a328cafa2
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76731006"
---
# <a name="how-to-create-an-mdi-window-list-with-menustrip-windows-forms"></a>Comment : créer une liste des fenêtres MDI avec MenuStrip (Windows Forms)
Utilisez l’interface multidocument (MDI) pour créer des applications qui peuvent ouvrir plusieurs documents en même temps et copier et coller du contenu d’un document à l’autre.  
  
 Cette procédure vous montre comment créer une liste de tous les formulaires enfants actifs dans le menu fenêtre du parent.  
  
### <a name="to-create-an-mdi-window-list-on-a-menustrip"></a>Pour créer une liste de fenêtres MDI sur un MenuStrip  
  
1. Créez un formulaire et affectez la valeur <xref:System.Windows.Forms.Form.IsMdiContainer%2A> à sa propriété `true`.  
  
2. Ajoutez un <xref:System.Windows.Forms.MenuStrip> au formulaire.  
  
3. Ajoutez deux éléments de menu de niveau supérieur au <xref:System.Windows.Forms.MenuStrip> et définissez leurs propriétés <xref:System.Windows.Forms.Control.Text%2A> sur `&File` et `&Window`.  
  
4. Ajoutez un élément de sous-menu à l'élément de menu `&File` et affectez la valeur <xref:System.Windows.Forms.ToolStripItem.Text%2A> à la propriété `&Open`.  
  
5. Définissez la propriété <xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A> du <xref:System.Windows.Forms.MenuStrip> sur le <xref:System.Windows.Forms.ToolStripMenuItem>`&Window`.  
  
6. Ajoutez un formulaire au projet et ajoutez le contrôle de votre choix, tel qu’un autre <xref:System.Windows.Forms.MenuStrip>.  
  
7. Créez un gestionnaire d'événements pour l'événement <xref:System.Windows.Forms.Control.Click> du `&New` de <xref:System.Windows.Forms.ToolStripMenuItem>.  
  
8. Dans le gestionnaire d’événements, insérez du code semblable au suivant pour créer et afficher les nouvelles instances de `Form2` en tant qu’enfants MDI de `Form1`.  
  
    ```vb  
    Private Sub openToolStripMenuItem_Click(ByVal sender As _  
    System.Object, ByVal e As System.EventArgs) Handles _  
    openToolStripMenuItem.Click  
        Dim NewMDIChild As New Form2()  
        'Set the parent form of the child window.  
            NewMDIChild.MdiParent = Me  
        'Display the new form.  
            NewMDIChild.Show()  
    End Sub  
    ```  
  
    ```csharp  
    private void newToolStripMenuItem_Click(object sender, EventArgs e)  
    {  
        Form2 newMDIChild = new Form2();  
        // Set the parent form of the child window.  
            newMDIChild.MdiParent = this;  
        // Display the new form.  
            newMDIChild.Show();  
    }  
    ```  
  
9. Placez le code comme suit dans le <xref:System.Windows.Forms.ToolStripMenuItem> `&New`pour inscrire le gestionnaire d’événements.  
  
    ```vb  
    Private Sub newToolStripMenuItem_Click(sender As Object, e As _  
    EventArgs) Handles newToolStripMenuItem.Click  
    ```  
  
    ```csharp  
    this.newToolStripMenuItem.Click += new System.EventHandler(this.newToolStripMenuItem_Click);  
    ```  
  
## <a name="compiling-the-code"></a>Compilation du code  
 Cet exemple nécessite :  
  
- deux <xref:System.Windows.Forms.Form> contrôles nommés `Form1` et `Form2` ;  
  
- un contrôle <xref:System.Windows.Forms.MenuStrip> sur `Form1` nommé `menuStrip1` et un contrôle <xref:System.Windows.Forms.MenuStrip> sur `Form2` nommé `menuStrip2` ;  
  
- des références aux assemblys <xref:System?displayProperty=nameWithType> et <xref:System.Windows.Forms?displayProperty=nameWithType>.  
  
## <a name="see-also"></a>Voir aussi

- [Guide pratique pour créer des formulaires MDI parents](../advanced/how-to-create-mdi-parent-forms.md)
- [Guide pratique pour créer des formulaires MDI enfants](../advanced/how-to-create-mdi-child-forms.md)
- [MenuStrip, contrôle](menustrip-control-windows-forms.md)
