---
title: 'Procédure pas à pas : Effectuer une opération de drag-and-drop'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Windows Forms, drag and drop operations
- drag and drop [Windows Forms], Windows Forms
ms.assetid: eb66f6bf-4a7d-4c2d-b276-40fefb2d3b6c
ms.openlocfilehash: b5e4bf753733cb9bd010672f40e8fbeb0cf036bf
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182445"
---
# <a name="walkthrough-performing-a-drag-and-drop-operation-in-windows-forms"></a>Procédure pas à pas : exécution d’opérations de glisser-déposer dans Windows Forms
Pour effectuer des opérations de drag-and-drop dans les applications Basées <xref:System.Windows.Forms.Control.DragEnter>sur <xref:System.Windows.Forms.Control.DragLeave>Windows, vous devez gérer une série d’événements, notamment le , , et <xref:System.Windows.Forms.Control.DragDrop> les événements. En utilisant les informations disponibles dans les arguments de ces événements, vous pouvez faciliter les opérations de glisser-déplacer.  
  
## <a name="dragging-data"></a>Faire glisser des données  
 Toutes les opérations de glisser-déplacer commencent par un glisser. La fonctionnalité permettant de recueillir des données lorsque <xref:System.Windows.Forms.Control.DoDragDrop%2A> le drague commence est implémentée dans la méthode.  
  
 Dans l’exemple <xref:System.Windows.Forms.Control.MouseDown> suivant, l’événement est utilisé pour démarrer l’opération de traînée parce qu’il est le plus intuitif (la plupart des actions de drag-and-drop commencent avec le bouton de la souris étant déprimé). N’oubliez cependant pas que n’importe quel événement peut être utilisé pour lancer une procédure de glisser-déplacer.  
  
> [!NOTE]
> Certains contrôles ont des événements personnalisés spécifiques au glisser. Les <xref:System.Windows.Forms.ListView> <xref:System.Windows.Forms.TreeView> contrôles et les commandes, par exemple, ont un <xref:System.Windows.Forms.TreeView.ItemDrag> événement.  
  
#### <a name="to-start-a-drag-operation"></a>Pour démarrer une opération de glisser  
  
1. Dans <xref:System.Windows.Forms.Control.MouseDown> le cas où le contrôle où la traînée commencera, utilisez la `DoDragDrop` méthode pour définir les données à traîné et l’effet autorisé de traînage aura. Pour plus d’informations, consultez <xref:System.Windows.Forms.DragEventArgs.Data%2A> et <xref:System.Windows.Forms.DragEventArgs.AllowedEffect%2A>.  
  
     L’exemple suivant montre comment initier une opération glisser. Le contrôle où la <xref:System.Windows.Forms.Button> traînée commence est un contrôle, les données étant traînées est la chaîne représentant la <xref:System.Windows.Forms.Control.Text%2A> propriété du <xref:System.Windows.Forms.Button> contrôle, et les effets autorisés sont soit copier ou se déplacer.  
  
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
    > Toutes les données peuvent être `DoDragDrop` utilisées comme paramètre dans la méthode; dans l’exemple <xref:System.Windows.Forms.Control.Text%2A> ci-dessus, la propriété du <xref:System.Windows.Forms.Button> contrôle a été utilisée (plutôt que de coder une valeur ou de récupérer <xref:System.Windows.Forms.Button> des données à partir d’un jeu de données) parce que la propriété était liée à l’emplacement traîné (le contrôle). Gardez cela à l’esprit quand vous incorporez des opérations de glisser-déplacer dans vos applications Windows.  
  
 Pendant qu’une opération de traînée <xref:System.Windows.Forms.Control.QueryContinueDrag> est en vigueur, vous pouvez gérer l’événement, qui « demande la permission » du système pour continuer le fonctionnement de la traînée. Lors de la manipulation de cette méthode, il est également le point approprié pour vous <xref:System.Windows.Forms.TreeNode> d’appeler des méthodes qui auront un effet sur le fonctionnement de la traînée, comme l’expansion d’un <xref:System.Windows.Forms.TreeView> contrôle lorsque le curseur plane sur elle.  
  
## <a name="dropping-data"></a>Déposer des données  
 Une fois que vous avez commencé à faire glisser des données à partir d’un emplacement sur un Windows Form ou un contrôle, vous voulez naturellement les déposer quelque part. Le curseur change quand il passe sur une zone d’un formulaire ou d’un contrôle qui est correctement configuré pour le dépôt des données. Toute zone dans un formulaire ou un contrôle Windows peut <xref:System.Windows.Forms.Control.AllowDrop%2A> être faite <xref:System.Windows.Forms.Control.DragEnter> <xref:System.Windows.Forms.Control.DragDrop> pour accepter les données abandonnées en définissant la propriété et en manipulant le et les événements.  
  
#### <a name="to-perform-a-drop"></a>Pour effectuer un dépôt  
  
1. Définissez <xref:System.Windows.Forms.Control.AllowDrop%2A> la propriété pour vrai.  
  
2. Dans `DragEnter` le cas pour le contrôle où la goutte se produira, assurez-vous <xref:System.Windows.Forms.Control.Text%2A>que les données traînées est d’un type acceptable (dans ce cas, ). Le code définit ensuite l’effet qui se produira <xref:System.Windows.Forms.DragDropEffects> lorsque la baisse se produit à une valeur dans le recensement. Pour plus d’informations, consultez <xref:System.Windows.Forms.DragEventArgs.Effect%2A>.  
  
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
    > Vous pouvez définir <xref:System.Windows.Forms.DataFormats> le vôtre en spécifiant votre propre objet comme le <xref:System.Object> paramètre de la <xref:System.Windows.Forms.DataObject.SetData%2A> méthode. Pour cela, vérifiez que l’objet spécifié est sérialisable. Pour plus d’informations, consultez <xref:System.Runtime.Serialization.ISerializable>.  
  
3. Dans <xref:System.Windows.Forms.Control.DragDrop> le cas pour le contrôle où <xref:System.Windows.Forms.DataObject.GetData%2A> la goutte se produira, utilisez la méthode pour récupérer les données étant traînées. Pour plus d’informations, consultez <xref:System.Security.Cryptography.Xml.DataObject.Data%2A>.  
  
     Dans l’exemple <xref:System.Windows.Forms.TextBox> ci-dessous, un contrôle est le contrôle étant traîné à (où la goutte se produira). Le code <xref:System.Windows.Forms.Control.Text%2A> définit la <xref:System.Windows.Forms.TextBox> propriété du contrôle égale aux données traînées.  
  
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
    > En outre, vous <xref:System.Windows.Forms.DragEventArgs.KeyState%2A> pouvez travailler avec la propriété, de sorte que, en fonction des clés décanches pendant l’opération de drag-and-drop, certains effets se produisent (par exemple, il est standard de copier les données traînées lorsque la clé CTRL est pressé).  
  
## <a name="see-also"></a>Voir aussi

- [Guide pratique pour ajouter des données au Presse-papiers](how-to-add-data-to-the-clipboard.md)
- [Guide pratique pour récupérer des données du Presse-papiers](how-to-retrieve-data-from-the-clipboard.md)
- [Opérations glisser-déposer et prise en charge du Presse-papiers](drag-and-drop-operations-and-clipboard-support.md)
