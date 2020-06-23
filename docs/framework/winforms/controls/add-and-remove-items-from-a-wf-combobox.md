---
title: Ajouter et supprimer des éléments d’un contrôle ComboBox, ListBox ou CheckedListBox
ms.date: 03/30/2017
description: Découvrez comment ajouter et supprimer des contrôles Windows Forms ComboBox, ListBox et CheckedListBox simplement et sans liaison de données.
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- combo boxes [Windows Forms], adding items
- list boxes [Windows Forms], removing items
- ComboBox control [Windows Forms], adding and removing items
- ListBox control [Windows Forms], adding and removing items
- list boxes [Windows Forms], adding items
- combo boxes [Windows Forms], removing items
- CheckedListBox control [Windows Forms], adding and removing items
ms.assetid: 7224c8d2-4118-443e-ae1e-d7c17d1e69ee
ms.openlocfilehash: f3701257bbe410bf03c4c21700705e87b581bf2e
ms.sourcegitcommit: 3824ff187947572b274b9715b60c11269335c181
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/17/2020
ms.locfileid: "84904440"
---
# <a name="how-to-add-and-remove-items-from-a-windows-forms-combobox-listbox-or-checkedlistbox-control"></a><span data-ttu-id="ce644-103">Comment : ajouter et supprimer des éléments d'un contrôle ComboBox, ListBox ou CheckedListBox Windows Forms</span><span class="sxs-lookup"><span data-stu-id="ce644-103">How to: Add and Remove Items from a Windows Forms ComboBox, ListBox, or CheckedListBox Control</span></span>
<span data-ttu-id="ce644-104">Les éléments peuvent être ajoutés à une zone de liste déroulante, Windows Forms une zone de liste ou une zone de liste de cases à cocher de plusieurs façons, car ces contrôles peuvent être liés à une variété de sources de données.</span><span class="sxs-lookup"><span data-stu-id="ce644-104">Items can be added to a Windows Forms combo box, list box, or checked list box in a variety of ways, because these controls can be bound to a variety of data sources.</span></span> <span data-ttu-id="ce644-105">Toutefois, cette rubrique illustre la méthode la plus simple et ne nécessite aucune liaison de données.</span><span class="sxs-lookup"><span data-stu-id="ce644-105">However, this topic demonstrates the simplest method and requires no data binding.</span></span> <span data-ttu-id="ce644-106">Les éléments affichés sont généralement des chaînes ; Toutefois, n’importe quel objet peut être utilisé.</span><span class="sxs-lookup"><span data-stu-id="ce644-106">The items displayed are usually strings; however, any object can be used.</span></span> <span data-ttu-id="ce644-107">Le texte affiché dans le contrôle est la valeur retournée par la méthode de l’objet `ToString` .</span><span class="sxs-lookup"><span data-stu-id="ce644-107">The text that is displayed in the control is the value returned by the object's `ToString` method.</span></span>  
  
### <a name="to-add-items"></a><span data-ttu-id="ce644-108">Pour ajouter des éléments</span><span class="sxs-lookup"><span data-stu-id="ce644-108">To add items</span></span>  
  
1. <span data-ttu-id="ce644-109">Ajoutez la chaîne ou l’objet à la liste à l’aide `Add` de la méthode de la `ObjectCollection` classe.</span><span class="sxs-lookup"><span data-stu-id="ce644-109">Add the string or object to the list by using the `Add` method of the `ObjectCollection` class.</span></span> <span data-ttu-id="ce644-110">La collection est référencée à l’aide de la `Items` propriété :</span><span class="sxs-lookup"><span data-stu-id="ce644-110">The collection is referenced using the `Items` property:</span></span>  
  
    ```vb  
    ComboBox1.Items.Add("Tokyo")  
    ```  
  
    ```csharp  
    comboBox1.Items.Add("Tokyo");  
    ```  
  
    ```cpp  
    comboBox1->Items->Add("Tokyo");  
    ```  
  
     - <span data-ttu-id="ce644-111">ou -</span><span class="sxs-lookup"><span data-stu-id="ce644-111">or -</span></span>  
  
2. <span data-ttu-id="ce644-112">Insérez la chaîne ou l’objet au point souhaité dans la liste avec la `Insert` méthode :</span><span class="sxs-lookup"><span data-stu-id="ce644-112">Insert the string or object at the desired point in the list with the `Insert` method:</span></span>  
  
    ```vb  
    CheckedListBox1.Items.Insert(0, "Copenhagen")  
    ```  
  
    ```csharp  
    checkedListBox1.Items.Insert(0, "Copenhagen");  
    ```  
  
    ```cpp  
    checkedListBox1->Items->Insert(0, "Copenhagen");  
    ```  
  
     - <span data-ttu-id="ce644-113">ou -</span><span class="sxs-lookup"><span data-stu-id="ce644-113">or -</span></span>  
  
3. <span data-ttu-id="ce644-114">Assigner un tableau entier à la `Items` collection :</span><span class="sxs-lookup"><span data-stu-id="ce644-114">Assign an entire array to the `Items` collection:</span></span>  
  
    ```vb  
    Dim ItemObject(9) As System.Object  
    Dim i As Integer  
       For i = 0 To 9  
       ItemObject(i) = "Item" & i  
    Next i  
    ListBox1.Items.AddRange(ItemObject)  
    ```  
  
    ```csharp  
    System.Object[] ItemObject = new System.Object[10];  
    for (int i = 0; i <= 9; i++)  
    {  
       ItemObject[i] = "Item" + i;  
    }  
    listBox1.Items.AddRange(ItemObject);  
    ```  
  
    ```cpp  
    Array<System::Object^>^ ItemObject = gcnew Array<System::Object^>(10);  
    for (int i = 0; i <= 9; i++)  
    {  
       ItemObject[i] = String::Concat("Item", i.ToString());  
    }  
    listBox1->Items->AddRange(ItemObject);  
    ```  
  
### <a name="to-remove-an-item"></a><span data-ttu-id="ce644-115">Pour supprimer un élément</span><span class="sxs-lookup"><span data-stu-id="ce644-115">To remove an item</span></span>  
  
1. <span data-ttu-id="ce644-116">Appelez la `Remove` `RemoveAt` méthode ou pour supprimer des éléments.</span><span class="sxs-lookup"><span data-stu-id="ce644-116">Call the `Remove` or `RemoveAt` method to delete items.</span></span>  
  
     <span data-ttu-id="ce644-117">`Remove`a un argument qui spécifie l’élément à supprimer.`RemoveAt`</span><span class="sxs-lookup"><span data-stu-id="ce644-117">`Remove` has one argument that specifies the item to remove.`RemoveAt`</span></span> <span data-ttu-id="ce644-118">supprime l’élément avec le numéro d’index spécifié.</span><span class="sxs-lookup"><span data-stu-id="ce644-118">removes the item with the specified index number.</span></span>  
  
    ```vb  
    ' To remove item with index 0:  
    ComboBox1.Items.RemoveAt(0)  
    ' To remove currently selected item:  
    ComboBox1.Items.Remove(ComboBox1.SelectedItem)  
    ' To remove "Tokyo" item:  
    ComboBox1.Items.Remove("Tokyo")  
    ```  
  
    ```csharp  
    // To remove item with index 0:  
    comboBox1.Items.RemoveAt(0);  
    // To remove currently selected item:  
    comboBox1.Items.Remove(comboBox1.SelectedItem);  
    // To remove "Tokyo" item:  
    comboBox1.Items.Remove("Tokyo");  
    ```  
  
    ```cpp  
    // To remove item with index 0:  
    comboBox1->Items->RemoveAt(0);  
    // To remove currently selected item:  
    comboBox1->Items->Remove(comboBox1->SelectedItem);  
    // To remove "Tokyo" item:  
    comboBox1->Items->Remove("Tokyo");  
    ```  
  
### <a name="to-remove-all-items"></a><span data-ttu-id="ce644-119">Pour supprimer tous les éléments</span><span class="sxs-lookup"><span data-stu-id="ce644-119">To remove all items</span></span>  
  
1. <span data-ttu-id="ce644-120">Appelez la `Clear` méthode pour supprimer tous les éléments de la collection :</span><span class="sxs-lookup"><span data-stu-id="ce644-120">Call the `Clear` method to remove all items from the collection:</span></span>  
  
    ```vb  
    ListBox1.Items.Clear()  
    ```  
  
    ```csharp  
    listBox1.Items.Clear();  
    ```  
  
    ```cpp  
    listBox1->Items->Clear();  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="ce644-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ce644-121">See also</span></span>

- <xref:System.Windows.Forms.ComboBox>
- <xref:System.Windows.Forms.ListBox>
- <xref:System.Windows.Forms.CheckedListBox>
- [<span data-ttu-id="ce644-122">Comment : trier le contenu d'un contrôle ComboBox, CheckedListBox ou ListBox Windows Forms</span><span class="sxs-lookup"><span data-stu-id="ce644-122">How to: Sort the Contents of a Windows Forms ComboBox, ListBox, or CheckedListBox Control</span></span>](sort-the-contents-of-a-wf-combobox-listbox-or-checkedlistbox-control.md)
- [<span data-ttu-id="ce644-123">Utilisation d'un contrôle ComboBox Windows Forms à la place d'un contrôle ListBox</span><span class="sxs-lookup"><span data-stu-id="ce644-123">When to Use a Windows Forms ComboBox Instead of a ListBox</span></span>](when-to-use-a-windows-forms-combobox-instead-of-a-listbox.md)
- [<span data-ttu-id="ce644-124">Contrôles Windows Forms utilisés pour l'affichage de listes d'options</span><span class="sxs-lookup"><span data-stu-id="ce644-124">Windows Forms Controls Used to List Options</span></span>](windows-forms-controls-used-to-list-options.md)
