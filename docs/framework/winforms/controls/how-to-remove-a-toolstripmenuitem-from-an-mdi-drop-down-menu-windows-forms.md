---
title: 'Comment : supprimer un ToolStripMenuItem d’un menu déroulant MDI'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- menu items [Windows Forms], removing from MDI drop-down menus
- MenuStrip control [Windows Forms], merging
- MenuStrip control [Windows Forms], removing
- MDI [Windows Forms], merging menu items
ms.assetid: bdafe60d-82ee-45bc-97fe-eeefca6e54c1
ms.openlocfilehash: 3198195cf0991734826508aa65818505bf2038c8
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76735851"
---
# <a name="how-to-remove-a-toolstripmenuitem-from-an-mdi-drop-down-menu-windows-forms"></a>Comment : supprimer un ToolStripMenuItem d'un menu déroulant MDI (Windows Forms)
Dans certaines applications, le type d'une fenêtre enfant d'interface multidocument (MDI) peut être différent de celui de la fenêtre parente MDI. Par exemple, le parent MDI peut être une feuille de calcul et l'enfant MDI un graphique. Dans ce cas, vous souhaitez mettre à jour le contenu du menu du parent MDI avec le contenu du menu de l'enfant MDI à mesure que des fenêtres enfants MDI de types différents sont activées.  
  
 La procédure suivante utilise les propriétés <xref:System.Windows.Forms.Form.IsMdiContainer%2A>, <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A>, <xref:System.Windows.Forms.MergeAction>et <xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A> pour supprimer un élément de menu de la partie déroulante du menu MDI parent. La fermeture de la fenêtre enfant MDI restaure les éléments de menu supprimés dans le menu MDI parent.  
  
### <a name="to-remove-a-menustrip-from-an-mdi-drop-down-menu"></a>Pour supprimer un MenuStrip d’un menu déroulant MDI  
  
1. Créez un formulaire et affectez la valeur <xref:System.Windows.Forms.Form.IsMdiContainer%2A> à sa propriété `true`.  
  
2. Ajoutez un <xref:System.Windows.Forms.MenuStrip> à `Form1` et affectez la valeur <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A> à la propriété <xref:System.Windows.Forms.MenuStrip> du `true`.  
  
3. Ajoutez un élément de menu de niveau supérieur au `Form1` de <xref:System.Windows.Forms.MenuStrip> et affectez la valeur <xref:System.Windows.Forms.Control.Text%2A> à sa propriété `&File`.  
  
4. Ajoutez trois éléments de sous-menu à l’élément de menu `&File` et définissez leurs propriétés <xref:System.Windows.Forms.ToolStripItem.Text%2A> sur `&Open`, `&Import from`et `E&xit`.  
  
5. Ajoutez deux éléments de sous-menu à l’élément de sous-menu `&Import from` et définissez leurs propriétés <xref:System.Windows.Forms.ToolStripItem.Text%2A> sur `&Word` et `&Excel`.  
  
6. Ajoutez un formulaire au projet, ajoutez un <xref:System.Windows.Forms.MenuStrip> au formulaire et affectez la valeur <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A> à la propriété `Form2` du <xref:System.Windows.Forms.MenuStrip> de `true`.  
  
7. Ajoutez un élément de menu de niveau supérieur au `Form2` de <xref:System.Windows.Forms.MenuStrip> et affectez la valeur <xref:System.Windows.Forms.ToolStripItem.Text%2A> à sa propriété `&File`.  
  
8. Ajoutez un élément de sous-menu `&Import from` au menu `&File` de `Form2`et ajoutez un élément de sous-menu `&Word` au menu `&File`.  
  
9. Définissez les propriétés <xref:System.Windows.Forms.MergeAction> et <xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A> des éléments de menu `Form2` comme indiqué dans le tableau suivant.  
  
    |Élément de menu Form2|Valeur MergeAction|Valeur MergeIndex|  
    |---------------------|-----------------------|----------------------|  
    |Fichier|MatchOnly|-1|  
    |Importer à partir de|MatchOnly|-1|  
    |Word|Supprimer|-1|  
  
10. Dans `Form1`, créez un gestionnaire d’événements pour l’événement <xref:System.Windows.Forms.Control.Click> de l' <xref:System.Windows.Forms.ToolStripMenuItem>`&Open`.  
  
11. Dans le gestionnaire d’événements, insérez du code semblable à l’exemple de code suivant pour créer et afficher les nouvelles instances de `Form2` en tant qu’enfants MDI de `Form1`:  
  
    ```vb  
    Private Sub openToolStripMenuItem_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles openToolStripMenuItem.Click  
        Dim NewMDIChild As New Form2()  
        'Set the parent form of the child window.  
            NewMDIChild.MdiParent = Me  
        'Display the new form.  
            NewMDIChild.Show()  
    End Sub  
    ```  
  
    ```csharp  
    private void openToolStripMenuItem_Click(object sender, EventArgs e)  
    {  
        Form2 newMDIChild = new Form2();  
        // Set the parent form of the child window.  
            newMDIChild.MdiParent = this;  
        // Display the new form.  
            newMDIChild.Show();  
    }  
    ```  
  
12. Insérez du code similaire à l'exemple de code suivant dans le `&Open`<xref:System.Windows.Forms.ToolStripMenuItem> pour inscrire le gestionnaire d'événements.  
  
    ```vb  
    Private Sub openToolStripMenuItem_Click(sender As Object, e As _  
    EventArgs) Handles openToolStripMenuItem.Click  
    ```  
  
    ```csharp  
    this.openToolStripMenuItem.Click += new _  
    System.EventHandler(this.openToolStripMenuItem_Click);  
    ```  
  
## <a name="compiling-the-code"></a>Compilation du code  
 Cet exemple nécessite :  
  
- deux <xref:System.Windows.Forms.Form> contrôles nommés `Form1` et `Form2` ;  
  
- un contrôle <xref:System.Windows.Forms.MenuStrip> sur `Form1` nommé `menuStrip1` et un contrôle <xref:System.Windows.Forms.MenuStrip> sur `Form2` nommé `menuStrip2` ;  
  
- des références aux assemblys <xref:System?displayProperty=nameWithType> et <xref:System.Windows.Forms?displayProperty=nameWithType>.  
  
## <a name="see-also"></a>Voir aussi

- [Guide pratique pour créer des formulaires MDI parents](../advanced/how-to-create-mdi-parent-forms.md)
- [Guide pratique pour créer des formulaires MDI enfants](../advanced/how-to-create-mdi-child-forms.md)
- [Vue d'ensemble du contrôle MenuStrip](menustrip-control-overview-windows-forms.md)
