---
title: Déterminer les éléments cochés dans le contrôle CheckedListBox
description: Découvrez comment déterminer les éléments cochés dans le contrôle Windows Forms CheckedListBox en effectuant une itération au sein de la collection stockée dans la propriété CheckedItems.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- check boxes [Windows Forms], determining checked state
- CheckedListBox control [Windows Forms], determining checked state
ms.assetid: 178b477d-27c9-489c-8914-44a9623a4d41
ms.openlocfilehash: fd8845ef83da7406ff4f1468506a23e3f4d386a0
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85618348"
---
# <a name="how-to-determine-checked-items-in-the-windows-forms-checkedlistbox-control"></a>Comment : déterminer des éléments cochés dans le contrôle CheckedListBox Windows Forms
Lors de la présentation de données dans un <xref:System.Windows.Forms.CheckedListBox> contrôle Windows Forms, vous pouvez itérer au sein de la collection stockée dans la <xref:System.Windows.Forms.CheckedListBox.CheckedItems%2A> propriété ou parcourir la liste à l’aide <xref:System.Windows.Forms.CheckedListBox.GetItemChecked%2A> de la méthode pour déterminer les éléments qui sont activés. La <xref:System.Windows.Forms.CheckedListBox.GetItemChecked%2A> méthode prend un numéro d’index d’élément comme argument et retourne `true` ou `false` . Contrairement à ce que vous pourriez espérer, <xref:System.Windows.Forms.ListBox.SelectedItems%2A> les <xref:System.Windows.Forms.ListBox.SelectedIndices%2A> Propriétés et ne déterminent pas les éléments qui sont activés ; ils déterminent les éléments qui sont mis en surbrillance.  
  
### <a name="to-determine-checked-items-in-a-checkedlistbox-control"></a>Pour déterminer les éléments activés dans un contrôle CheckedListBox  
  
1. Itère au sein de la <xref:System.Windows.Forms.CheckedListBox.CheckedItems%2A> collection, en commençant à 0, car la collection est de base zéro. Notez que cette méthode vous donnera le numéro d’élément dans la liste des éléments cochés, et non dans la liste globale. Par conséquent, si le premier élément de la liste n’est pas activé et que le deuxième élément est activé, le code ci-dessous affiche un texte tel que « élément activé 1 = MyListItem2 ».  
  
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
  
     - ou -  
  
2. Parcourez la <xref:System.Windows.Forms.CheckedListBox.Items%2A> collection, en commençant à 0 car la collection est de base zéro, puis appelez la <xref:System.Windows.Forms.CheckedListBox.GetItemChecked%2A> méthode pour chaque élément. Notez que cette méthode vous donnera le numéro de l’élément dans la liste globale. par conséquent, si le premier élément de la liste n’est pas activé et que le deuxième élément est activé, il affiche un résultat semblable à « Item 2 = MyListItem2 ».  
  
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

- [Contrôles Windows Forms utilisés pour l'affichage de listes d'options](windows-forms-controls-used-to-list-options.md)
