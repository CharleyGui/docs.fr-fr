---
title: Déterminer les éléments cochés dans le contrôle CheckedListBox
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- check boxes [Windows Forms], determining checked state
- CheckedListBox control [Windows Forms], determining checked state
ms.assetid: 178b477d-27c9-489c-8914-44a9623a4d41
ms.openlocfilehash: 5854f7e6be759daeb604458ea8554d3c98ed39c2
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743240"
---
# <a name="how-to-determine-checked-items-in-the-windows-forms-checkedlistbox-control"></a>Comment : déterminer des éléments cochés dans le contrôle CheckedListBox Windows Forms
Lors de la présentation de données dans un contrôle Windows Forms <xref:System.Windows.Forms.CheckedListBox>, vous pouvez itérer au sein de la collection stockée dans la propriété <xref:System.Windows.Forms.CheckedListBox.CheckedItems%2A> ou parcourir la liste à l’aide de la méthode <xref:System.Windows.Forms.CheckedListBox.GetItemChecked%2A> pour déterminer les éléments qui sont activés. La méthode <xref:System.Windows.Forms.CheckedListBox.GetItemChecked%2A> prend un numéro d’index d’élément comme argument et retourne `true` ou `false`. Contrairement à ce que vous pourriez espérer, les propriétés <xref:System.Windows.Forms.ListBox.SelectedItems%2A> et <xref:System.Windows.Forms.ListBox.SelectedIndices%2A> ne déterminent pas les éléments qui sont activés ; ils déterminent quels éléments sont mis en surbrillance.  
  
### <a name="to-determine-checked-items-in-a-checkedlistbox-control"></a>Pour déterminer les éléments activés dans un contrôle CheckedListBox  
  
1. Itérez au sein de la collection <xref:System.Windows.Forms.CheckedListBox.CheckedItems%2A>, en démarrant à 0, car la collection est de base zéro. Notez que cette méthode vous donnera le numéro d’élément dans la liste des éléments cochés, et non dans la liste globale. Par conséquent, si le premier élément de la liste n’est pas activé et que le deuxième élément est activé, le code ci-dessous affiche un texte tel que « élément activé 1 = MyListItem2 ».  
  
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
  
     - ou  
  
2. Parcourez la collection <xref:System.Windows.Forms.CheckedListBox.Items%2A>, en commençant à 0, car la collection est de base zéro, puis appelez la méthode <xref:System.Windows.Forms.CheckedListBox.GetItemChecked%2A> pour chaque élément. Notez que cette méthode vous donnera le numéro de l’élément dans la liste globale. par conséquent, si le premier élément de la liste n’est pas activé et que le deuxième élément est activé, il affiche un résultat semblable à « Item 2 = MyListItem2 ».  
  
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
  
## <a name="see-also"></a>Voir aussi

- [Contrôles Windows Forms utilisés pour l’affichage de listes d’options](windows-forms-controls-used-to-list-options.md)
