---
title: 'Procédure : Supprimer un ToolStripMenuItem d’un Menu du menu déroulant MDI (Windows Forms)'
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
ms.openlocfilehash: 378410977c31a446b34bf907dfd438a2a799c84a
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64662287"
---
# <a name="how-to-remove-a-toolstripmenuitem-from-an-mdi-drop-down-menu-windows-forms"></a>Procédure : Supprimer un ToolStripMenuItem d’un Menu du menu déroulant MDI (Windows Forms)
Dans certaines applications, le type d'une fenêtre enfant d'interface multidocument (MDI) peut être différent de celui de la fenêtre parente MDI. Par exemple, le parent MDI peut être une feuille de calcul et l'enfant MDI un graphique. Dans ce cas, vous souhaitez mettre à jour le contenu du menu du parent MDI avec le contenu du menu de l'enfant MDI à mesure que des fenêtres enfants MDI de types différents sont activées.  
  
 La procédure suivante utilise le <xref:System.Windows.Forms.Form.IsMdiContainer%2A>, <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A>, <xref:System.Windows.Forms.MergeAction>, et <xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A> propriétés à supprimer un élément de menu à partir de la partie déroulante du menu MDI parent. Fermeture de la fenêtre MDI enfant restaure les éléments de menu supprimé au menu MDI parent.  
  
### <a name="to-remove-a-menustrip-from-an-mdi-drop-down-menu"></a>Pour supprimer un MenuStrip dans le menu déroulant MDI  
  
1. Créez un formulaire et affectez la valeur `true` à sa propriété <xref:System.Windows.Forms.Form.IsMdiContainer%2A>.  
  
2. Ajoutez un <xref:System.Windows.Forms.MenuStrip> à `Form1` et affectez la valeur `true` à la propriété <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A> du <xref:System.Windows.Forms.MenuStrip>.  
  
3. Ajoutez un élément de menu de niveau supérieur au <xref:System.Windows.Forms.MenuStrip> de `Form1` et affectez la valeur `&File` à sa propriété <xref:System.Windows.Forms.Control.Text%2A>.  
  
4. Ajoutez trois éléments de sous-menu à la `&File` élément de menu et définissez leurs <xref:System.Windows.Forms.ToolStripItem.Text%2A> propriétés à `&Open`, `&Import from`, et `E&xit`.  
  
5. Ajoutez deux éléments de sous-menu à la `&Import from` élément de sous-menu et définissez leurs <xref:System.Windows.Forms.ToolStripItem.Text%2A> propriétés à `&Word` et `&Excel`.  
  
6. Ajoutez un formulaire au projet, ajoutez un <xref:System.Windows.Forms.MenuStrip> au formulaire et affectez la valeur `true` à la propriété <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A> du <xref:System.Windows.Forms.MenuStrip> de `Form2`.  
  
7. Ajoutez un élément de menu de niveau supérieur au <xref:System.Windows.Forms.MenuStrip> de `Form2` et affectez la valeur `&File` à sa propriété <xref:System.Windows.Forms.ToolStripItem.Text%2A>.  
  
8. Ajouter un `&Import from` élément de sous-menu à la `&File` menu de `Form2`et ajoutez un `&Word` élément de sous-menu à le `&File` menu.  
  
9. Définir le <xref:System.Windows.Forms.MergeAction> et <xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A> propriétés de la `Form2` les éléments de menu comme indiqué dans le tableau suivant.  
  
    |Élément de menu Form2|Valeur MergeAction|Valeur MergeIndex|  
    |---------------------|-----------------------|----------------------|  
    |Fichier|MatchOnly|-1|  
    |Importer à partir de|MatchOnly|-1|  
    |Word|Remove|-1|  
  
10. Dans `Form1`, créez un gestionnaire d’événements pour le <xref:System.Windows.Forms.Control.Click> événements de la `&Open` <xref:System.Windows.Forms.ToolStripMenuItem>.  
  
11. Dans le Gestionnaire d’événements, insérez du code semblable à l’exemple de code suivant pour créer et afficher les nouvelles instances de `Form2` en tant qu’enfants MDI de `Form1`:  
  
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
 Cet exemple nécessite :  
  
- deux <xref:System.Windows.Forms.Form> contrôles nommés `Form1` et `Form2` ;  
  
- un contrôle <xref:System.Windows.Forms.MenuStrip> sur `Form1` nommé `menuStrip1` et un contrôle <xref:System.Windows.Forms.MenuStrip> sur `Form2` nommé `menuStrip2` ;  
  
- des références aux assemblys <xref:System?displayProperty=nameWithType> et <xref:System.Windows.Forms?displayProperty=nameWithType>.  
  
## <a name="see-also"></a>Voir aussi

- [Guide pratique pour Créer des formulaires MDI parents](../advanced/how-to-create-mdi-parent-forms.md)
- [Guide pratique pour Créer des formulaires MDI enfants](../advanced/how-to-create-mdi-child-forms.md)
- [Vue d'ensemble du contrôle MenuStrip](menustrip-control-overview-windows-forms.md)
