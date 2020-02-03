---
title: Lier un contrôle ComboBox ou ListBox à des données
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data [Windows Forms], binding to controls
- list boxes [Windows Forms], data binding
- ComboBox control [Windows Forms], data binding
- data binding [Windows Forms], combo boxes
- ListBox control [Windows Forms], data binding
- combo boxes [Windows Forms], data binding
- bound controls [Windows Forms], combo boxes
- Windows Forms controls, data binding
- data-bound controls [Windows Forms], Windows Forms
ms.assetid: dfd7f081-8bea-4a41-86a3-86a1934828ef
ms.openlocfilehash: 99d9b53b32d6faae888b134d4ed486980c05a75b
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742037"
---
# <a name="how-to-bind-a-windows-forms-combobox-or-listbox-control-to-data"></a>Comment : lier un contrôle ComboBox ou ListBox Windows Forms aux données
Vous pouvez lier les <xref:System.Windows.Forms.ComboBox> et les <xref:System.Windows.Forms.ListBox> aux données pour effectuer des tâches telles que l’exploration des données dans une base de données, l’entrée de nouvelles données ou la modification de données existantes.  
  
### <a name="to-bind-a-combobox-or-listbox-control"></a>Pour lier un contrôle ComboBox ou ListBox  
  
1. Affectez à la propriété `DataSource` un objet de source de données. Les sources de données possibles incluent une <xref:System.Windows.Forms.BindingSource> liée aux données, à une table de données, à une vue de données, à un DataSet, à un gestionnaire d’affichage de données, à un tableau ou à toute autre classe qui implémente l’interface <xref:System.Collections.IList>. Pour plus d’informations, consultez [sources de données prises en charge par Windows Forms](../data-sources-supported-by-windows-forms.md).  
  
2. Si vous effectuez une liaison à une table, définissez la propriété `DisplayMember` sur le nom d’une colonne dans la source de données.  
  
     \- ou -  
  
     Si vous effectuez une liaison à une <xref:System.Collections.IList>, définissez le membre d’affichage sur une propriété publique du type dans la liste.  
  
    ```vb  
    Private Sub BindComboBox()  
      ComboBox1.DataSource = DataSet1.Tables("Suppliers")  
      ComboBox1.DisplayMember = "ProductName"  
    End Sub  
    ```  
  
    ```csharp  
    private void BindComboBox()  
    {  
      comboBox1.DataSource = dataSet1.Tables["Suppliers"];  
      comboBox1.DisplayMember = "ProductName";  
    }  
    ```  
  
    > [!NOTE]
    > Si vous êtes lié à une source de données qui n’implémente pas l’interface <xref:System.ComponentModel.IBindingList>, telle qu’un <xref:System.Collections.ArrayList>, les données du contrôle lié ne sont pas mises à jour lorsque la source de données est mise à jour. Par exemple, si une zone de liste déroulante est liée à une <xref:System.Collections.ArrayList> et que des données sont ajoutées à la <xref:System.Collections.ArrayList>, ces nouveaux éléments n’apparaîtront pas dans la zone de liste déroulante. Toutefois, vous pouvez forcer la mise à jour de la zone de liste déroulante en appelant les méthodes <xref:System.Windows.Forms.BindingManagerBase.SuspendBinding%2A> et <xref:System.Windows.Forms.BindingManagerBase.ResumeBinding%2A> sur l’instance de la classe <xref:System.Windows.Forms.BindingContext> à laquelle le contrôle est lié.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.ComboBox>
- <xref:System.Windows.Forms.ListBox>
- [Liaison de données Windows Forms](../windows-forms-data-binding.md)
- [Liaison de données et Windows Forms](../data-binding-and-windows-forms.md)
- [Contrôles Windows Forms utilisés pour l’affichage de listes d’options](windows-forms-controls-used-to-list-options.md)
