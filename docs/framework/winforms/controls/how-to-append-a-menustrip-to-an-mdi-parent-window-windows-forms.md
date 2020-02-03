---
title: 'Comment : ajouter un MenuStrip à une fenêtre parente MDI'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- MenuStrip control [Windows Forms], merging
- MenuStrip control [Windows Forms], appending
- MDI [Windows Forms], merging menu items
ms.assetid: ab70c936-b452-4653-b417-17be57bb795b
ms.openlocfilehash: 06e5c9daab8b7eb72024fff27d661c0eb3bf84c6
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76747157"
---
# <a name="how-to-append-a-menustrip-to-an-mdi-parent-window-windows-forms"></a>Comment : ajouter un MenuStrip à une fenêtre parente MDI (Windows Forms)
Dans certaines applications, le type d'une fenêtre enfant d'interface multidocument (MDI) peut être différent de celui de la fenêtre parente MDI. Par exemple, le parent MDI peut être une feuille de calcul et l'enfant MDI un graphique. Dans ce cas, vous souhaitez mettre à jour le contenu du menu du parent MDI avec le contenu du menu de l'enfant MDI à mesure que des fenêtres enfants MDI de types différents sont activées.  
  
 La procédure suivante utilise les propriétés <xref:System.Windows.Forms.Form.IsMdiContainer%2A>, <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A>, <xref:System.Windows.Forms.MergeAction> et <xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A> pour ajouter le menu MDI enfant au menu MDI parent. La fermeture de la fenêtre MDI enfant supprime le menu ajouté du MDI parent.  
  
 Consultez également [les applications d’interface multidocument (MDI, multiple-document interface)](../advanced/multiple-document-interface-mdi-applications.md).  
  
### <a name="to-append-a-menu-item-to-an-mdi-parent"></a>Pour ajouter un élément à un menu MDI parent  
  
1. Créez un formulaire et affectez la valeur <xref:System.Windows.Forms.Form.IsMdiContainer%2A> à sa propriété `true`.  
  
2. Ajoutez un <xref:System.Windows.Forms.MenuStrip> à `Form1` et affectez la valeur <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A> à la propriété <xref:System.Windows.Forms.MenuStrip> du `true`.  
  
3. Affectez la valeur <xref:System.Windows.Forms.ToolStripItem.Visible%2A> à la propriété `Form1` du <xref:System.Windows.Forms.MenuStrip> de `false`.  
  
4. Ajoutez un élément de menu de niveau supérieur au `Form1` de <xref:System.Windows.Forms.MenuStrip> et affectez la valeur <xref:System.Windows.Forms.Control.Text%2A> à sa propriété `&File`.  
  
5. Ajoutez un élément de sous-menu à l'élément de menu `&File` et affectez la valeur <xref:System.Windows.Forms.Form.Text%2A> à la propriété `&Open`.  
  
6. Ajoutez un formulaire au projet, ajoutez un <xref:System.Windows.Forms.MenuStrip> au formulaire et affectez la valeur <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A> à la propriété `Form2` du <xref:System.Windows.Forms.MenuStrip> de `true`.  
  
7. Ajoutez un élément de menu de niveau supérieur au `Form2` de <xref:System.Windows.Forms.MenuStrip> et affectez la valeur <xref:System.Windows.Forms.Form.Text%2A> à sa propriété `&Special`.  
  
8. Ajoutez deux éléments de sous-menu à l'élément de menu `&Special` et affectez respectivement les valeurs <xref:System.Windows.Forms.Form.Text%2A> et `Command&1` à leur propriété `Command&2`.  
  
9. Affectez la valeur <xref:System.Windows.Forms.MergeAction> à la propriété `&Special` des éléments de menu `Command&1`, `Command&2` et <xref:System.Windows.Forms.MergeAction.Append>.  
  
10. Créez un gestionnaire d’événements pour l’événement <xref:System.Windows.Forms.Control.Click> de l' <xref:System.Windows.Forms.ToolStripMenuItem>`&Open`.  
  
11. Dans le gestionnaire d'événements, insérez du code semblable à l'exemple de code suivant pour créer et afficher de nouvelles instances de `Form2` en tant qu'enfants MDI de `Form1`.  
  
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
    this.openToolStripMenuItem.Click += new System.EventHandler(this.openToolStripMenuItem_Click);  
    ```  
  
## <a name="compiling-the-code"></a>Compilation du code  
 Cet exemple nécessite :  
  
- deux <xref:System.Windows.Forms.Form> contrôles nommés `Form1` et `Form2` ;  
  
- un contrôle <xref:System.Windows.Forms.MenuStrip> sur `Form1` nommé `menuStrip1` et un contrôle <xref:System.Windows.Forms.MenuStrip> sur `Form2` nommé `menuStrip2` ;  
  
- des références aux assemblys <xref:System?displayProperty=nameWithType> et <xref:System.Windows.Forms?displayProperty=nameWithType>.
