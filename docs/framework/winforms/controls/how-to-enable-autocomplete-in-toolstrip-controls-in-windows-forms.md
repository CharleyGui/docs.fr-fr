---
title: 'Comment : activer la saisie semi-automatique dans les contrôles ToolStrip'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- AutoComplete [Windows Forms], examples
- toolbars [Windows Forms], AutoComplete
- examples [Windows Forms], toolbars
- AutoComplete [Windows Forms], enabling in toolbars
- ToolStripComboBox class [Windows Forms], examples
- ToolStrip control [Windows Forms], AutoComplete
ms.assetid: fd66d085-1af1-45d4-930a-cde944da2e16
ms.openlocfilehash: 18b17aaea9d2354c03bb43f3fdd8d3779697cf58
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79142016"
---
# <a name="how-to-enable-autocomplete-in-toolstrip-controls-in-windows-forms"></a><span data-ttu-id="71f3a-102">Comment : activer la saisie semi-automatique dans les contrôles ToolStrip dans les Windows Forms</span><span class="sxs-lookup"><span data-stu-id="71f3a-102">How to: Enable AutoComplete in ToolStrip Controls in Windows Forms</span></span>
<span data-ttu-id="71f3a-103">La procédure suivante <xref:System.Windows.Forms.ToolStripLabel> combine <xref:System.Windows.Forms.ToolStripComboBox> un avec un qui peut être abandonné pour afficher une liste d’éléments, tels que les sites Web récemment visités.</span><span class="sxs-lookup"><span data-stu-id="71f3a-103">The following procedure combines a <xref:System.Windows.Forms.ToolStripLabel> with a <xref:System.Windows.Forms.ToolStripComboBox> that can be dropped down to show a list of items, such as recently visited Web sites.</span></span> <span data-ttu-id="71f3a-104">Si l’utilisateur tape un personnage qui correspond au premier caractère de l’un des éléments de la liste, l’élément est immédiatement affiché.</span><span class="sxs-lookup"><span data-stu-id="71f3a-104">If the user types a character that matches the first character of one of the items in the list, the item is immediately displayed.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="71f3a-105">L’achèvement `ToolStrip` automatique fonctionne avec des contrôles de la <xref:System.Windows.Forms.ComboBox> <xref:System.Windows.Forms.TextBox>même manière qu’il fonctionne avec des contrôles traditionnels tels que et .</span><span class="sxs-lookup"><span data-stu-id="71f3a-105">Automatic completion works with `ToolStrip` controls in the same way that it works with traditional controls such as <xref:System.Windows.Forms.ComboBox> and <xref:System.Windows.Forms.TextBox>.</span></span>  
  
### <a name="to-enable-autocomplete-in-a-toolstrip-control"></a><span data-ttu-id="71f3a-106">Pour activer AutoComplete dans un contrôle ToolStrip</span><span class="sxs-lookup"><span data-stu-id="71f3a-106">To enable AutoComplete in a ToolStrip control</span></span>  
  
1. <span data-ttu-id="71f3a-107">Créez <xref:System.Windows.Forms.ToolStrip> un contrôle et ajoutez des éléments.</span><span class="sxs-lookup"><span data-stu-id="71f3a-107">Create a <xref:System.Windows.Forms.ToolStrip> control and add items to it.</span></span>  
  
    ```vb  
    ToolStrip1 = New System.Windows.Forms.ToolStrip  
    ToolStrip1.Items.AddRange(New System.Windows.Forms.ToolStripItem()_  
        {ToolStripLabel1, ToolStripComboBox1})  
    ```  
  
    ```csharp  
    toolStrip1 = new System.Windows.Forms.ToolStrip();  
    toolStrip1.Items.AddRange(new System.Windows.Forms.ToolStripItem[]
        {toolStripLabel1, toolStripComboBox1});  
    ```  
  
2. <span data-ttu-id="71f3a-108">Définissez <xref:System.Windows.Forms.ToolStripItem.Overflow%2A> la propriété de l’étiquette et la boîte combo pour <xref:System.Windows.Forms.ToolStripItemOverflow.Never> que la liste soit toujours disponible quelle que soit la taille du formulaire.</span><span class="sxs-lookup"><span data-stu-id="71f3a-108">Set the <xref:System.Windows.Forms.ToolStripItem.Overflow%2A> property of the label and the combo box to <xref:System.Windows.Forms.ToolStripItemOverflow.Never> so that the list is always available regardless of the form's size.</span></span>  
  
    ```vb  
    ToolStripLabel1.Overflow = _  
        System.Windows.Forms.ToolStripItemOverflow.Never  
    ToolStripComboBox1.Overflow = _  
        System.Windows.Forms.ToolStripItemOverflow.Never  
    ```  
  
    ```csharp  
    toolStripLabel1.Overflow = _  
        System.Windows.Forms.ToolStripItemOverflow.Never  
    toolStripComboBox1.Overflow = System.Windows.Forms.ToolStripItemOverflow.Never  
    ```  
  
3. <span data-ttu-id="71f3a-109">Ajoutez des mots à <xref:System.Windows.Forms.ToolStripComboBox> la collection d’objets du contrôle.</span><span class="sxs-lookup"><span data-stu-id="71f3a-109">Add words to the Items collection of the <xref:System.Windows.Forms.ToolStripComboBox> control.</span></span>  
  
    ```vb  
    ToolStripComboBox1.Items.AddRange(New Object() {"First Item", _  
        "Second Item", "Third Item"})  
    ```  
  
    ```csharp  
    toolStripComboBox1.Items.AddRange(new object[] {"First item", "Second item", "Third item"});  
    ```  
  
4. <span data-ttu-id="71f3a-110">Réglez la <xref:System.Windows.Forms.ComboBox.AutoCompleteMode%2A> propriété <xref:System.Windows.Forms.AutoCompleteMode.Append>de la boîte combo à .</span><span class="sxs-lookup"><span data-stu-id="71f3a-110">Set the <xref:System.Windows.Forms.ComboBox.AutoCompleteMode%2A> property of the combo box to <xref:System.Windows.Forms.AutoCompleteMode.Append>.</span></span>  
  
    ```vb  
    ToolStripComboBox1.AutoCompleteMode = _  
        System.Windows.Forms.AutoCompleteMode.Append  
    ```  
  
    ```csharp  
    toolStripComboBox1.AutoCompleteMode = System.Windows.Forms.AutoCompleteMode.Append;  
    ```  
  
5. <span data-ttu-id="71f3a-111">Réglez la <xref:System.Windows.Forms.ComboBox.AutoCompleteSource%2A> propriété <xref:System.Windows.Forms.AutoCompleteSource.ListItems>de la boîte combo à .</span><span class="sxs-lookup"><span data-stu-id="71f3a-111">Set the <xref:System.Windows.Forms.ComboBox.AutoCompleteSource%2A> property of the combo box to <xref:System.Windows.Forms.AutoCompleteSource.ListItems>.</span></span>  
  
    ```vb  
    ToolStripComboBox1.AutoCompleteSource = _  
        System.Windows.Forms.AutoCompleteSource.ListItems  
    ```  
  
    ```csharp  
    toolStripComboBox1.AutoCompleteSource = System.Windows.Forms.AutoCompleteSource.ListItems;  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="71f3a-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="71f3a-112">See also</span></span>

- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.ToolStripLabel>
- <xref:System.Windows.Forms.ToolStripComboBox>
- <xref:System.Windows.Forms.ToolStripComboBox.AutoCompleteMode%2A>
- <xref:System.Windows.Forms.ToolStripComboBox.AutoCompleteSource%2A>
- [<span data-ttu-id="71f3a-113">Vue d’ensemble du contrôle ToolStrip</span><span class="sxs-lookup"><span data-stu-id="71f3a-113">ToolStrip Control Overview</span></span>](toolstrip-control-overview-windows-forms.md)
- [<span data-ttu-id="71f3a-114">Architecture du contrôle ToolStrip</span><span class="sxs-lookup"><span data-stu-id="71f3a-114">ToolStrip Control Architecture</span></span>](toolstrip-control-architecture.md)
- [<span data-ttu-id="71f3a-115">Résumé de la technologie ToolStrip</span><span class="sxs-lookup"><span data-stu-id="71f3a-115">ToolStrip Technology Summary</span></span>](toolstrip-technology-summary.md)
