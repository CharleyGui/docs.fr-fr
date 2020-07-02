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
# <a name="how-to-determine-checked-items-in-the-windows-forms-checkedlistbox-control"></a><span data-ttu-id="a3360-103">Comment : déterminer des éléments cochés dans le contrôle CheckedListBox Windows Forms</span><span class="sxs-lookup"><span data-stu-id="a3360-103">How to: Determine Checked Items in the Windows Forms CheckedListBox Control</span></span>
<span data-ttu-id="a3360-104">Lors de la présentation de données dans un <xref:System.Windows.Forms.CheckedListBox> contrôle Windows Forms, vous pouvez itérer au sein de la collection stockée dans la <xref:System.Windows.Forms.CheckedListBox.CheckedItems%2A> propriété ou parcourir la liste à l’aide <xref:System.Windows.Forms.CheckedListBox.GetItemChecked%2A> de la méthode pour déterminer les éléments qui sont activés.</span><span class="sxs-lookup"><span data-stu-id="a3360-104">When presenting data in a Windows Forms <xref:System.Windows.Forms.CheckedListBox> control, you can either iterate through the collection stored in the <xref:System.Windows.Forms.CheckedListBox.CheckedItems%2A> property, or step through the list using the <xref:System.Windows.Forms.CheckedListBox.GetItemChecked%2A> method to determine which items are checked.</span></span> <span data-ttu-id="a3360-105">La <xref:System.Windows.Forms.CheckedListBox.GetItemChecked%2A> méthode prend un numéro d’index d’élément comme argument et retourne `true` ou `false` .</span><span class="sxs-lookup"><span data-stu-id="a3360-105">The <xref:System.Windows.Forms.CheckedListBox.GetItemChecked%2A> method takes an item index number as its argument and returns `true` or `false`.</span></span> <span data-ttu-id="a3360-106">Contrairement à ce que vous pourriez espérer, <xref:System.Windows.Forms.ListBox.SelectedItems%2A> les <xref:System.Windows.Forms.ListBox.SelectedIndices%2A> Propriétés et ne déterminent pas les éléments qui sont activés ; ils déterminent les éléments qui sont mis en surbrillance.</span><span class="sxs-lookup"><span data-stu-id="a3360-106">Contrary to what you might expect, the <xref:System.Windows.Forms.ListBox.SelectedItems%2A> and <xref:System.Windows.Forms.ListBox.SelectedIndices%2A> properties do not determine which items are checked; they determine which items are highlighted.</span></span>  
  
### <a name="to-determine-checked-items-in-a-checkedlistbox-control"></a><span data-ttu-id="a3360-107">Pour déterminer les éléments activés dans un contrôle CheckedListBox</span><span class="sxs-lookup"><span data-stu-id="a3360-107">To determine checked items in a CheckedListBox control</span></span>  
  
1. <span data-ttu-id="a3360-108">Itère au sein de la <xref:System.Windows.Forms.CheckedListBox.CheckedItems%2A> collection, en commençant à 0, car la collection est de base zéro.</span><span class="sxs-lookup"><span data-stu-id="a3360-108">Iterate through the <xref:System.Windows.Forms.CheckedListBox.CheckedItems%2A> collection, starting at 0 since the collection is zero-based.</span></span> <span data-ttu-id="a3360-109">Notez que cette méthode vous donnera le numéro d’élément dans la liste des éléments cochés, et non dans la liste globale.</span><span class="sxs-lookup"><span data-stu-id="a3360-109">Note that this method will give you the item number in the list of checked items, not the overall list.</span></span> <span data-ttu-id="a3360-110">Par conséquent, si le premier élément de la liste n’est pas activé et que le deuxième élément est activé, le code ci-dessous affiche un texte tel que « élément activé 1 = MyListItem2 ».</span><span class="sxs-lookup"><span data-stu-id="a3360-110">So if the first item in the list is not checked and the second item is checked, the code below will display text like "Checked Item 1 = MyListItem2".</span></span>  
  
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
  
     - <span data-ttu-id="a3360-111">ou -</span><span class="sxs-lookup"><span data-stu-id="a3360-111">or -</span></span>  
  
2. <span data-ttu-id="a3360-112">Parcourez la <xref:System.Windows.Forms.CheckedListBox.Items%2A> collection, en commençant à 0 car la collection est de base zéro, puis appelez la <xref:System.Windows.Forms.CheckedListBox.GetItemChecked%2A> méthode pour chaque élément.</span><span class="sxs-lookup"><span data-stu-id="a3360-112">Step through the <xref:System.Windows.Forms.CheckedListBox.Items%2A> collection, starting at 0 since the collection is zero-based, and call the <xref:System.Windows.Forms.CheckedListBox.GetItemChecked%2A> method for each item.</span></span> <span data-ttu-id="a3360-113">Notez que cette méthode vous donnera le numéro de l’élément dans la liste globale. par conséquent, si le premier élément de la liste n’est pas activé et que le deuxième élément est activé, il affiche un résultat semblable à « Item 2 = MyListItem2 ».</span><span class="sxs-lookup"><span data-stu-id="a3360-113">Note that this method will give you the item number in the overall list, so if the first item in the list is not checked and the second item is checked, it will display something like "Item 2 = MyListItem2".</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="a3360-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a3360-114">See also</span></span>

- [<span data-ttu-id="a3360-115">Contrôles Windows Forms utilisés pour l'affichage de listes d'options</span><span class="sxs-lookup"><span data-stu-id="a3360-115">Windows Forms Controls Used to List Options</span></span>](windows-forms-controls-used-to-list-options.md)
