---
title: 'Procédure pas à pas : effectuer une opération de glisser-déplacer'
description: Apprenez à effectuer une opération de glisser-déplacer dans Windows Forms en gérant une série d’événements, notamment les événements DragEnter, DragLeave et DragDrop.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Windows Forms, drag and drop operations
- drag and drop [Windows Forms], Windows Forms
ms.assetid: eb66f6bf-4a7d-4c2d-b276-40fefb2d3b6c
ms.openlocfilehash: 83bfda875e2fdec3981bbcb8f8f7be00db342440
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/24/2020
ms.locfileid: "85325814"
---
# <a name="walkthrough-performing-a-drag-and-drop-operation-in-windows-forms"></a>Procédure pas à pas : exécution d’opérations de glisser-déposer dans Windows Forms
Pour effectuer des opérations de glisser-déplacer dans des applications Windows, vous devez gérer une série d’événements, notamment les <xref:System.Windows.Forms.Control.DragEnter> événements, <xref:System.Windows.Forms.Control.DragLeave> et <xref:System.Windows.Forms.Control.DragDrop> . En utilisant les informations disponibles dans les arguments de ces événements, vous pouvez faciliter les opérations de glisser-déplacer.  
  
## <a name="dragging-data"></a>Faire glisser des données  
 Toutes les opérations de glisser-déplacer commencent par un glisser. Les fonctionnalités permettant de collecter des données au début du glissement sont implémentées dans la <xref:System.Windows.Forms.Control.DoDragDrop%2A> méthode.  
  
 Dans l’exemple suivant, l' <xref:System.Windows.Forms.Control.MouseDown> événement est utilisé pour démarrer l’opération glisser, car il est le plus intuitif (la plupart des actions de glisser-déplacer commencent par le bouton de la souris qui est enfoncé). N’oubliez cependant pas que n’importe quel événement peut être utilisé pour lancer une procédure de glisser-déplacer.  
  
> [!NOTE]
> Certains contrôles ont des événements personnalisés spécifiques au glisser. <xref:System.Windows.Forms.ListView> <xref:System.Windows.Forms.TreeView> Par exemple, les contrôles et ont un <xref:System.Windows.Forms.TreeView.ItemDrag> événement.  
  
#### <a name="to-start-a-drag-operation"></a>Pour démarrer une opération de glisser  
  
1. Dans l' <xref:System.Windows.Forms.Control.MouseDown> événement pour le contrôle où l’opération glisser commence, utilisez la `DoDragDrop` méthode pour définir les données à faire glisser et l’effet autorisé à faire glisser. Pour plus d’informations, consultez <xref:System.Windows.Forms.DragEventArgs.Data%2A> et <xref:System.Windows.Forms.DragEventArgs.AllowedEffect%2A>.  
  
     L’exemple suivant montre comment initier une opération glisser. Le contrôle où l’opération de glisser commence est un <xref:System.Windows.Forms.Button> contrôle, les données glissées sont la chaîne représentant la <xref:System.Windows.Forms.Control.Text%2A> propriété du <xref:System.Windows.Forms.Button> contrôle et les effets autorisés sont la copie ou le déplacement.  
  
    ```vb  
    Private Sub Button1_MouseDown(ByVal sender As Object, ByVal e As System.Windows.Forms.MouseEventArgs) Handles Button1.MouseDown  
       Button1.DoDragDrop(Button1.Text, DragDropEffects.Copy Or DragDropEffects.Move)  
    End Sub  
    ```  
  
    ```csharp  
    private void button1_MouseDown(object sender,
    System.Windows.Forms.MouseEventArgs e)  
    {  
       button1.DoDragDrop(button1.Text, DragDropEffects.Copy |
          DragDropEffects.Move);  
    }  
    ```  
  
    > [!NOTE]
    > Toutes les données peuvent être utilisées en tant que paramètre dans la `DoDragDrop` méthode. dans l’exemple ci-dessus, la <xref:System.Windows.Forms.Control.Text%2A> propriété du <xref:System.Windows.Forms.Button> contrôle a été utilisée (au lieu de coder en dur une valeur ou de récupérer des données d’un DataSet), car la propriété était associée à l’emplacement à partir duquel vous avez fait glisser (le <xref:System.Windows.Forms.Button> contrôle). Gardez cela à l’esprit quand vous incorporez des opérations de glisser-déplacer dans vos applications Windows.  
  
 Pendant qu’une opération glisser est en vigueur, vous pouvez gérer l' <xref:System.Windows.Forms.Control.QueryContinueDrag> événement, qui « demande l’autorisation » du système pour poursuivre l’opération glisser. Lors de la gestion de cette méthode, il s’agit également du point approprié pour appeler des méthodes qui auront un effet sur l’opération glisser, par exemple le développement d’un <xref:System.Windows.Forms.TreeNode> dans un <xref:System.Windows.Forms.TreeView> contrôle lorsque le curseur pointe dessus.  
  
## <a name="dropping-data"></a>Déposer des données  
 Une fois que vous avez commencé à faire glisser des données à partir d’un emplacement sur un Windows Form ou un contrôle, vous voulez naturellement les déposer quelque part. Le curseur change quand il passe sur une zone d’un formulaire ou d’un contrôle qui est correctement configuré pour le dépôt des données. Toute zone d’un Windows Form ou d’un contrôle peut être rendue pour accepter les données déplacées en définissant la <xref:System.Windows.Forms.Control.AllowDrop%2A> propriété et en gérant les <xref:System.Windows.Forms.Control.DragEnter> <xref:System.Windows.Forms.Control.DragDrop> événements et.  
  
#### <a name="to-perform-a-drop"></a>Pour effectuer un dépôt  
  
1. Affectez <xref:System.Windows.Forms.Control.AllowDrop%2A> à la propriété la valeur true.  
  
2. Dans l' `DragEnter` événement pour le contrôle où le déplacement se produit, assurez-vous que les données glissées sont d’un type acceptable (dans ce cas, <xref:System.Windows.Forms.Control.Text%2A> ). Le code définit ensuite l’effet qui se produit lorsque la suppression se produit dans une valeur de l' <xref:System.Windows.Forms.DragDropEffects> énumération. Pour plus d’informations, consultez <xref:System.Windows.Forms.DragEventArgs.Effect%2A>.  
  
    ```vb  
    Private Sub TextBox1_DragEnter(ByVal sender As Object, ByVal e As System.Windows.Forms.DragEventArgs) Handles TextBox1.DragEnter  
       If (e.Data.GetDataPresent(DataFormats.Text)) Then  
         e.Effect = DragDropEffects.Copy  
       Else  
         e.Effect = DragDropEffects.None  
       End If  
    End Sub  
    ```  
  
    ```csharp  
    private void textBox1_DragEnter(object sender,
    System.Windows.Forms.DragEventArgs e)  
    {  
       if (e.Data.GetDataPresent(DataFormats.Text))
          e.Effect = DragDropEffects.Copy;  
       else  
          e.Effect = DragDropEffects.None;  
    }  
    ```  
  
    > [!NOTE]
    > Vous pouvez définir votre propre <xref:System.Windows.Forms.DataFormats> objet en spécifiant votre propre objet comme <xref:System.Object> paramètre de la <xref:System.Windows.Forms.DataObject.SetData%2A> méthode. Pour cela, vérifiez que l’objet spécifié est sérialisable. Pour plus d’informations, consultez <xref:System.Runtime.Serialization.ISerializable>.  
  
3. Dans l' <xref:System.Windows.Forms.Control.DragDrop> événement pour le contrôle où le déplacement se produit, utilisez la <xref:System.Windows.Forms.DataObject.GetData%2A> méthode pour récupérer les données glissées. Pour plus d’informations, consultez <xref:System.Security.Cryptography.Xml.DataObject.Data%2A>.  
  
     Dans l’exemple ci-dessous, un <xref:System.Windows.Forms.TextBox> contrôle est le contrôle vers lequel le déplacement se produit. Le code définit la <xref:System.Windows.Forms.Control.Text%2A> propriété du <xref:System.Windows.Forms.TextBox> contrôle comme étant égale aux données glissées.  
  
    ```vb  
    Private Sub TextBox1_DragDrop(ByVal sender As Object, ByVal e As System.Windows.Forms.DragEventArgs) Handles TextBox1.DragDrop  
       TextBox1.Text = e.Data.GetData(DataFormats.Text).ToString  
    End Sub  
    ```  
  
    ```csharp  
    private void textBox1_DragDrop(object sender,
    System.Windows.Forms.DragEventArgs e)  
    {  
       textBox1.Text = e.Data.GetData(DataFormats.Text).ToString();  
    }  
    ```  
  
    > [!NOTE]
    > En outre, vous pouvez utiliser la <xref:System.Windows.Forms.DragEventArgs.KeyState%2A> propriété, de sorte que, en fonction des touches enfoncées pendant l’opération de glisser-déplacer, certains effets se produisent (par exemple, il est standard de copier les données glissées lorsque la touche CTRL est enfoncée).  
  
## <a name="see-also"></a>Voir aussi

- [Guide pratique pour ajouter des données au Presse-papiers](how-to-add-data-to-the-clipboard.md)
- [Guide pratique pour récupérer des données du Presse-papiers](how-to-retrieve-data-from-the-clipboard.md)
- [Opérations glisser-déposer et prise en charge du Presse-papiers](drag-and-drop-operations-and-clipboard-support.md)
