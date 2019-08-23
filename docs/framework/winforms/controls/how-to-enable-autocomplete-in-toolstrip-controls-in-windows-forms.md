---
title: 'Procédure : Activer la saisie semi-automatique dans les contrôles ToolStrip dans Windows Forms'
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
ms.openlocfilehash: 301f1b156bbaee5c5f7be95e972ee1ebaa83777f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69963614"
---
# <a name="how-to-enable-autocomplete-in-toolstrip-controls-in-windows-forms"></a>Procédure : Activer la saisie semi-automatique dans les contrôles ToolStrip dans Windows Forms
La procédure suivante combine un <xref:System.Windows.Forms.ToolStripLabel> avec un <xref:System.Windows.Forms.ToolStripComboBox> qui peut être supprimé pour afficher une liste d’éléments, tels que les sites Web récemment visités. Si l’utilisateur tape un caractère qui correspond au premier caractère de l’un des éléments de la liste, l’élément est immédiatement affiché.  
  
> [!NOTE]
> La saisie semi- `ToolStrip` automatique fonctionne avec les contrôles de la même façon qu’avec les contrôles <xref:System.Windows.Forms.ComboBox> traditionnels <xref:System.Windows.Forms.TextBox>, tels que et.  
  
### <a name="to-enable-autocomplete-in-a-toolstrip-control"></a>Pour activer la saisie semi-automatique dans un contrôle ToolStrip  
  
1. Créer un <xref:System.Windows.Forms.ToolStrip> contrôle et y ajouter des éléments.  
  
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
  
2. Affectez à la <xref:System.Windows.Forms.ToolStripItemOverflow.Never> propriétédel’étiquetteetàlazonedelistedéroulantelavaleurafinquelalistesoittoujoursdisponible,quellequesoitlatailleduformulaire.<xref:System.Windows.Forms.ToolStripItem.Overflow%2A>  
  
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
  
3. Ajoutez des mots à la collection d’éléments <xref:System.Windows.Forms.ToolStripComboBox> du contrôle.  
  
    ```vb  
    ToolStripComboBox1.Items.AddRange(New Object() {"First Item", _  
        "Second Item", "Third Item"})  
    ```  
  
    ```csharp  
    toolStripComboBox1.Items.AddRange(new object[] {"First item", "Second item", "Third item"});  
    ```  
  
4. Affectez <xref:System.Windows.Forms.ComboBox.AutoCompleteMode%2A> à <xref:System.Windows.Forms.AutoCompleteMode.Append>la propriété de la zone de liste déroulante la valeur.  
  
    ```vb  
    ToolStripComboBox1.AutoCompleteMode = _  
        System.Windows.Forms.AutoCompleteMode.Append  
    ```  
  
    ```csharp  
    toolStripComboBox1.AutoCompleteMode = System.Windows.Forms.AutoCompleteMode.Append;  
    ```  
  
5. Affectez <xref:System.Windows.Forms.ComboBox.AutoCompleteSource%2A> à <xref:System.Windows.Forms.AutoCompleteSource.ListItems>la propriété de la zone de liste déroulante la valeur.  
  
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
