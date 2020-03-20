---
title: Déterminer les articles vérifiés dans le contrôle checkedListBox
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- check boxes [Windows Forms], determining checked state
- CheckedListBox control [Windows Forms], determining checked state
ms.assetid: 178b477d-27c9-489c-8914-44a9623a4d41
ms.openlocfilehash: 5d93a63e9c1c6aae91ecfe83590c59450a565afe
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182191"
---
# <a name="how-to-determine-checked-items-in-the-windows-forms-checkedlistbox-control"></a><span data-ttu-id="84950-102">Comment : déterminer des éléments cochés dans le contrôle CheckedListBox Windows Forms</span><span class="sxs-lookup"><span data-stu-id="84950-102">How to: Determine Checked Items in the Windows Forms CheckedListBox Control</span></span>
<span data-ttu-id="84950-103">Lors de la présentation <xref:System.Windows.Forms.CheckedListBox> de données dans un contrôle des formulaires Windows, vous pouvez soit itérer à travers la collection stockée dans la <xref:System.Windows.Forms.CheckedListBox.CheckedItems%2A> propriété, ou passer par la liste en utilisant la <xref:System.Windows.Forms.CheckedListBox.GetItemChecked%2A> méthode pour déterminer quels éléments sont vérifiés.</span><span class="sxs-lookup"><span data-stu-id="84950-103">When presenting data in a Windows Forms <xref:System.Windows.Forms.CheckedListBox> control, you can either iterate through the collection stored in the <xref:System.Windows.Forms.CheckedListBox.CheckedItems%2A> property, or step through the list using the <xref:System.Windows.Forms.CheckedListBox.GetItemChecked%2A> method to determine which items are checked.</span></span> <span data-ttu-id="84950-104">La <xref:System.Windows.Forms.CheckedListBox.GetItemChecked%2A> méthode prend un numéro d’index d’article comme argument et retours `true` ou `false`.</span><span class="sxs-lookup"><span data-stu-id="84950-104">The <xref:System.Windows.Forms.CheckedListBox.GetItemChecked%2A> method takes an item index number as its argument and returns `true` or `false`.</span></span> <span data-ttu-id="84950-105">Contrairement à ce à <xref:System.Windows.Forms.ListBox.SelectedItems%2A> quoi <xref:System.Windows.Forms.ListBox.SelectedIndices%2A> vous pouvez vous attendre, les propriétés et les propriétés ne déterminent pas quels éléments sont vérifiés; ils déterminent quels éléments sont mis en évidence.</span><span class="sxs-lookup"><span data-stu-id="84950-105">Contrary to what you might expect, the <xref:System.Windows.Forms.ListBox.SelectedItems%2A> and <xref:System.Windows.Forms.ListBox.SelectedIndices%2A> properties do not determine which items are checked; they determine which items are highlighted.</span></span>  
  
### <a name="to-determine-checked-items-in-a-checkedlistbox-control"></a><span data-ttu-id="84950-106">Pour déterminer les articles vérifiés dans un contrôle CheckedListBox</span><span class="sxs-lookup"><span data-stu-id="84950-106">To determine checked items in a CheckedListBox control</span></span>  
  
1. <span data-ttu-id="84950-107">Itérer à <xref:System.Windows.Forms.CheckedListBox.CheckedItems%2A> travers la collection, à partir de 0 puisque la collection est basée sur zéro.</span><span class="sxs-lookup"><span data-stu-id="84950-107">Iterate through the <xref:System.Windows.Forms.CheckedListBox.CheckedItems%2A> collection, starting at 0 since the collection is zero-based.</span></span> <span data-ttu-id="84950-108">Notez que cette méthode vous donnera le numéro d’article dans la liste des éléments vérifiés, et non la liste globale.</span><span class="sxs-lookup"><span data-stu-id="84950-108">Note that this method will give you the item number in the list of checked items, not the overall list.</span></span> <span data-ttu-id="84950-109">Donc, si le premier élément de la liste n’est pas vérifié et que le deuxième élément est vérifié, le code ci-dessous affichera du texte comme "Article vérifié 1 - MyListItem2".</span><span class="sxs-lookup"><span data-stu-id="84950-109">So if the first item in the list is not checked and the second item is checked, the code below will display text like "Checked Item 1 = MyListItem2".</span></span>  
  
    ```vb  
    ' Determine if there are any items checked.  
    If CheckedListBox1.CheckedItems.Count <> 0 Then  
       ' If so, loop through all checked items and print results.  
       Dim x As Integer  
       Dim s As String = ""  
       For x = 0 To CheckedListBox1.CheckedItems.Count - 1  
          s = s & "Checked Item " & (x + 1).ToString & " = " & CheckedListBox1.CheckedItems(x).ToString & ControlChars.CrLf  
       Next x  
       MessageBox.Show(s)  
    End If  
    ```  
  
    ```csharp  
    // Determine if there are any items checked.  
    if(checkedListBox1.CheckedItems.Count != 0)  
    {  
       // If so, loop through all checked items and print results.  
       string s = "";  
       for(int x = 0; x < checkedListBox1.CheckedItems.Count ; x++)  
       {  
          s = s + "Checked Item " + (x+1).ToString() + " = " + checkedListBox1.CheckedItems[x].ToString() + "\n";  
       }  
       MessageBox.Show(s);  
    }  
    ```  
  
    ```cpp  
    // Determine if there are any items checked.  
    if(checkedListBox1->CheckedItems->Count != 0)  
    {  
       // If so, loop through all checked items and print results.  
       String ^ s = "";  
       for(int x = 0; x < checkedListBox1->CheckedItems->Count; x++)  
       {  
          s = String::Concat(s, "Checked Item ", (x+1).ToString(),  
             " = ", checkedListBox1->CheckedItems[x]->ToString(),  
             "\n");  
       }  
       MessageBox::Show(s);  
    }  
    ```  
  
     - <span data-ttu-id="84950-110">ou -</span><span class="sxs-lookup"><span data-stu-id="84950-110">or -</span></span>  
  
2. <span data-ttu-id="84950-111">Passez par <xref:System.Windows.Forms.CheckedListBox.Items%2A> la collection, à partir de 0 puisque <xref:System.Windows.Forms.CheckedListBox.GetItemChecked%2A> la collection est basée sur zéro, et appelez la méthode pour chaque élément.</span><span class="sxs-lookup"><span data-stu-id="84950-111">Step through the <xref:System.Windows.Forms.CheckedListBox.Items%2A> collection, starting at 0 since the collection is zero-based, and call the <xref:System.Windows.Forms.CheckedListBox.GetItemChecked%2A> method for each item.</span></span> <span data-ttu-id="84950-112">Notez que cette méthode vous donnera le numéro d’élément dans la liste globale, donc si le premier élément de la liste n’est pas vérifié et le deuxième élément est vérifié, il affichera quelque chose comme "Article 2 - MyListItem2".</span><span class="sxs-lookup"><span data-stu-id="84950-112">Note that this method will give you the item number in the overall list, so if the first item in the list is not checked and the second item is checked, it will display something like "Item 2 = MyListItem2".</span></span>  
  
    ```vb  
    Dim i As Integer  
    Dim s As String  
    s = "Checked Items:" & ControlChars.CrLf  
    For i = 0 To (CheckedListBox1.Items.Count - 1)  
       If CheckedListBox1.GetItemChecked(i) = True Then  
          s = s & "Item " & (i + 1).ToString & " = " & CheckedListBox1.Items(i).ToString & ControlChars.CrLf  
       End If  
    Next  
    MessageBox.Show(s)  
    ```  
  
    ```csharp  
    int i;  
    string s;
    s = "Checked items:\n" ;  
    for (i = 0; i <= (checkedListBox1.Items.Count-1); i++)  
    {  
       if (checkedListBox1.GetItemChecked(i))  
       {  
          s = s + "Item " + (i+1).ToString() + " = " + checkedListBox1.Items[i].ToString() + "\n";  
       }  
    }  
    MessageBox.Show (s);  
    ```  
  
    ```cpp  
    int i;  
    String ^ s;
    s = "Checked items:\n" ;  
    for (i = 0; i <= (checkedListBox1->Items->Count-1); i++)  
    {  
       if (checkedListBox1->GetItemChecked(i))  
       {  
          s = String::Concat(s, "Item ", (i+1).ToString(), " = ",  
             checkedListBox1->Item[i]->ToString(), "\n");  
       }  
    }  
    MessageBox::Show(s);  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="84950-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="84950-113">See also</span></span>

- [<span data-ttu-id="84950-114">Contrôles Windows Forms utilisés pour l'affichage de listes d'options</span><span class="sxs-lookup"><span data-stu-id="84950-114">Windows Forms Controls Used to List Options</span></span>](windows-forms-controls-used-to-list-options.md)
