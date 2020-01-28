---
title: Ajouter et supprimer des éléments d’un contrôle ComboBox, ListBox ou CheckedListBox
ms.date: 03/30/2017
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
ms.openlocfilehash: 3a83d98af42386b566b4af7bc11ff383dea8fd6b
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746306"
---
# <a name="how-to-add-and-remove-items-from-a-windows-forms-combobox-listbox-or-checkedlistbox-control"></a><span data-ttu-id="0667a-102">Comment : ajouter et supprimer des éléments d'un contrôle ComboBox, ListBox ou CheckedListBox Windows Forms</span><span class="sxs-lookup"><span data-stu-id="0667a-102">How to: Add and Remove Items from a Windows Forms ComboBox, ListBox, or CheckedListBox Control</span></span>
<span data-ttu-id="0667a-103">Les éléments peuvent être ajoutés à une zone de liste déroulante, Windows Forms une zone de liste ou une zone de liste de cases à cocher de plusieurs façons, car ces contrôles peuvent être liés à une variété de sources de données.</span><span class="sxs-lookup"><span data-stu-id="0667a-103">Items can be added to a Windows Forms combo box, list box, or checked list box in a variety of ways, because these controls can be bound to a variety of data sources.</span></span> <span data-ttu-id="0667a-104">Toutefois, cette rubrique illustre la méthode la plus simple et ne nécessite aucune liaison de données.</span><span class="sxs-lookup"><span data-stu-id="0667a-104">However, this topic demonstrates the simplest method and requires no data binding.</span></span> <span data-ttu-id="0667a-105">Les éléments affichés sont généralement des chaînes ; Toutefois, n’importe quel objet peut être utilisé.</span><span class="sxs-lookup"><span data-stu-id="0667a-105">The items displayed are usually strings; however, any object can be used.</span></span> <span data-ttu-id="0667a-106">Le texte affiché dans le contrôle correspond à la valeur retournée par la méthode `ToString` de l’objet.</span><span class="sxs-lookup"><span data-stu-id="0667a-106">The text that is displayed in the control is the value returned by the object's `ToString` method.</span></span>  
  
### <a name="to-add-items"></a><span data-ttu-id="0667a-107">Pour ajouter des éléments</span><span class="sxs-lookup"><span data-stu-id="0667a-107">To add items</span></span>  
  
1. <span data-ttu-id="0667a-108">Ajoutez la chaîne ou l’objet à la liste à l’aide de la méthode `Add` de la classe `ObjectCollection`.</span><span class="sxs-lookup"><span data-stu-id="0667a-108">Add the string or object to the list by using the `Add` method of the `ObjectCollection` class.</span></span> <span data-ttu-id="0667a-109">La collection est référencée à l’aide de la propriété `Items` :</span><span class="sxs-lookup"><span data-stu-id="0667a-109">The collection is referenced using the `Items` property:</span></span>  
  
    ```vb  
    ComboBox1.Items.Add("Tokyo")  
    ```  
  
    ```csharp  
    comboBox1.Items.Add("Tokyo");  
    ```  
  
    ```cpp  
    comboBox1->Items->Add("Tokyo");  
    ```  
  
     - <span data-ttu-id="0667a-110">ou</span><span class="sxs-lookup"><span data-stu-id="0667a-110">or -</span></span>  
  
2. <span data-ttu-id="0667a-111">Insérez la chaîne ou l’objet au point souhaité dans la liste à l’aide de la méthode `Insert` :</span><span class="sxs-lookup"><span data-stu-id="0667a-111">Insert the string or object at the desired point in the list with the `Insert` method:</span></span>  
  
    ```vb  
    CheckedListBox1.Items.Insert(0, "Copenhagen")  
    ```  
  
    ```csharp  
    checkedListBox1.Items.Insert(0, "Copenhagen");  
    ```  
  
    ```cpp  
    checkedListBox1->Items->Insert(0, "Copenhagen");  
    ```  
  
     - <span data-ttu-id="0667a-112">ou</span><span class="sxs-lookup"><span data-stu-id="0667a-112">or -</span></span>  
  
3. <span data-ttu-id="0667a-113">Assigner un tableau entier à la collection `Items` :</span><span class="sxs-lookup"><span data-stu-id="0667a-113">Assign an entire array to the `Items` collection:</span></span>  
  
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
  
### <a name="to-remove-an-item"></a><span data-ttu-id="0667a-114">Pour supprimer un élément</span><span class="sxs-lookup"><span data-stu-id="0667a-114">To remove an item</span></span>  
  
1. <span data-ttu-id="0667a-115">Appelez la méthode `Remove` ou `RemoveAt` pour supprimer des éléments.</span><span class="sxs-lookup"><span data-stu-id="0667a-115">Call the `Remove` or `RemoveAt` method to delete items.</span></span>  
  
     <span data-ttu-id="0667a-116">`Remove` possède un argument qui spécifie l’élément à supprimer.`RemoveAt`</span><span class="sxs-lookup"><span data-stu-id="0667a-116">`Remove` has one argument that specifies the item to remove.`RemoveAt`</span></span> <span data-ttu-id="0667a-117">supprime l’élément avec le numéro d’index spécifié.</span><span class="sxs-lookup"><span data-stu-id="0667a-117">removes the item with the specified index number.</span></span>  
  
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
  
### <a name="to-remove-all-items"></a><span data-ttu-id="0667a-118">Pour supprimer tous les éléments</span><span class="sxs-lookup"><span data-stu-id="0667a-118">To remove all items</span></span>  
  
1. <span data-ttu-id="0667a-119">Appelez la méthode `Clear` pour supprimer tous les éléments de la collection :</span><span class="sxs-lookup"><span data-stu-id="0667a-119">Call the `Clear` method to remove all items from the collection:</span></span>  
  
    ```vb  
    ListBox1.Items.Clear()  
    ```  
  
    ```csharp  
    listBox1.Items.Clear();  
    ```  
  
    ```cpp  
    listBox1->Items->Clear();  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="0667a-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0667a-120">See also</span></span>

- <xref:System.Windows.Forms.ComboBox>
- <xref:System.Windows.Forms.ListBox>
- <xref:System.Windows.Forms.CheckedListBox>
- [<span data-ttu-id="0667a-121">Guide pratique pour trier le contenu d'un contrôle ComboBox, CheckedListBox ou ListBox Windows Forms</span><span class="sxs-lookup"><span data-stu-id="0667a-121">How to: Sort the Contents of a Windows Forms ComboBox, ListBox, or CheckedListBox Control</span></span>](sort-the-contents-of-a-wf-combobox-listbox-or-checkedlistbox-control.md)
- [<span data-ttu-id="0667a-122">Utilisation d'un contrôle ComboBox Windows Forms à la place d'un contrôle ListBox</span><span class="sxs-lookup"><span data-stu-id="0667a-122">When to Use a Windows Forms ComboBox Instead of a ListBox</span></span>](when-to-use-a-windows-forms-combobox-instead-of-a-listbox.md)
- [<span data-ttu-id="0667a-123">Contrôles Windows Forms utilisés pour l’affichage de listes d’options</span><span class="sxs-lookup"><span data-stu-id="0667a-123">Windows Forms Controls Used to List Options</span></span>](windows-forms-controls-used-to-list-options.md)
