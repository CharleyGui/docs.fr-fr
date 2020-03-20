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
# <a name="how-to-enable-autocomplete-in-toolstrip-controls-in-windows-forms"></a>Comment : activer la saisie semi-automatique dans les contrôles ToolStrip dans les Windows Forms
La procédure suivante <xref:System.Windows.Forms.ToolStripLabel> combine <xref:System.Windows.Forms.ToolStripComboBox> un avec un qui peut être abandonné pour afficher une liste d’éléments, tels que les sites Web récemment visités. Si l’utilisateur tape un personnage qui correspond au premier caractère de l’un des éléments de la liste, l’élément est immédiatement affiché.  
  
> [!NOTE]
> L’achèvement `ToolStrip` automatique fonctionne avec des contrôles de la <xref:System.Windows.Forms.ComboBox> <xref:System.Windows.Forms.TextBox>même manière qu’il fonctionne avec des contrôles traditionnels tels que et .  
  
### <a name="to-enable-autocomplete-in-a-toolstrip-control"></a>Pour activer AutoComplete dans un contrôle ToolStrip  
  
1. Créez <xref:System.Windows.Forms.ToolStrip> un contrôle et ajoutez des éléments.  
  
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
  
2. Définissez <xref:System.Windows.Forms.ToolStripItem.Overflow%2A> la propriété de l’étiquette et la boîte combo pour <xref:System.Windows.Forms.ToolStripItemOverflow.Never> que la liste soit toujours disponible quelle que soit la taille du formulaire.  
  
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
  
3. Ajoutez des mots à <xref:System.Windows.Forms.ToolStripComboBox> la collection d’objets du contrôle.  
  
    ```vb  
    ToolStripComboBox1.Items.AddRange(New Object() {"First Item", _  
        "Second Item", "Third Item"})  
    ```  
  
    ```csharp  
    toolStripComboBox1.Items.AddRange(new object[] {"First item", "Second item", "Third item"});  
    ```  
  
4. Réglez la <xref:System.Windows.Forms.ComboBox.AutoCompleteMode%2A> propriété <xref:System.Windows.Forms.AutoCompleteMode.Append>de la boîte combo à .  
  
    ```vb  
    ToolStripComboBox1.AutoCompleteMode = _  
        System.Windows.Forms.AutoCompleteMode.Append  
    ```  
  
    ```csharp  
    toolStripComboBox1.AutoCompleteMode = System.Windows.Forms.AutoCompleteMode.Append;  
    ```  
  
5. Réglez la <xref:System.Windows.Forms.ComboBox.AutoCompleteSource%2A> propriété <xref:System.Windows.Forms.AutoCompleteSource.ListItems>de la boîte combo à .  
  
    ```vb  
    ToolStripComboBox1.AutoCompleteSource = _  
        System.Windows.Forms.AutoCompleteSource.ListItems  
    ```  
  
    ```csharp  
    toolStripComboBox1.AutoCompleteSource = System.Windows.Forms.AutoCompleteSource.ListItems;  
    ```  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.ToolStripLabel>
- <xref:System.Windows.Forms.ToolStripComboBox>
- <xref:System.Windows.Forms.ToolStripComboBox.AutoCompleteMode%2A>
- <xref:System.Windows.Forms.ToolStripComboBox.AutoCompleteSource%2A>
- [Vue d’ensemble du contrôle ToolStrip](toolstrip-control-overview-windows-forms.md)
- [Architecture du contrôle ToolStrip](toolstrip-control-architecture.md)
- [Résumé de la technologie ToolStrip](toolstrip-technology-summary.md)
