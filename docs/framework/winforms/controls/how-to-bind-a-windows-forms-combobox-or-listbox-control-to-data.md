---
title: Lier un contrôle ComboBox ou ListBox à des données
description: Découvrez comment lier la liste déroulante Windows Forms et la zone de liste aux données pour effectuer des tâches telles que l’exploration des données dans une base de données, l’entrée de nouvelles données ou la modification de données existantes.
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
ms.openlocfilehash: 0c07dc90ddc91061c5f34b5a237082cb444e89d9
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/24/2020
ms.locfileid: "85324068"
---
# <a name="how-to-bind-a-windows-forms-combobox-or-listbox-control-to-data"></a>Comment : lier un contrôle ComboBox ou ListBox Windows Forms aux données
Vous pouvez lier le <xref:System.Windows.Forms.ComboBox> et <xref:System.Windows.Forms.ListBox> aux données pour effectuer des tâches telles que l’exploration de données dans une base de données, l’entrée de nouvelles données ou la modification de données existantes.  
  
### <a name="to-bind-a-combobox-or-listbox-control"></a>Pour lier un contrôle ComboBox ou ListBox  
  
1. Affectez `DataSource` à la propriété un objet de source de données. Les sources de données possibles incluent une <xref:System.Windows.Forms.BindingSource> liée à des données, une table de données, une vue de données, un DataSet, un gestionnaire d’affichage de données, un tableau ou toute classe qui implémente l' <xref:System.Collections.IList> interface. Pour plus d’informations, consultez [sources de données prises en charge par Windows Forms](../data-sources-supported-by-windows-forms.md).  
  
2. Si vous effectuez une liaison à une table, définissez la `DisplayMember` propriété sur le nom d’une colonne dans la source de données.  
  
     \- ou -  
  
     Si vous effectuez une liaison à un <xref:System.Collections.IList> , définissez le membre d’affichage sur une propriété publique du type dans la liste.  
  
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
    > Si vous êtes lié à une source de données qui n’implémente pas l' <xref:System.ComponentModel.IBindingList> interface, telle que <xref:System.Collections.ArrayList> , les données du contrôle lié ne sont pas mises à jour lorsque la source de données est mise à jour. Par exemple, si une zone de liste déroulante est liée à un et que des <xref:System.Collections.ArrayList> données sont ajoutées au <xref:System.Collections.ArrayList> , ces nouveaux éléments n’apparaîtront pas dans la zone de liste déroulante. Toutefois, vous pouvez forcer la mise à jour de la zone de liste déroulante en appelant les <xref:System.Windows.Forms.BindingManagerBase.SuspendBinding%2A> <xref:System.Windows.Forms.BindingManagerBase.ResumeBinding%2A> méthodes et sur l’instance de la <xref:System.Windows.Forms.BindingContext> classe à laquelle le contrôle est lié.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.ComboBox>
- <xref:System.Windows.Forms.ListBox>
- [Liaison de données Windows Forms](../windows-forms-data-binding.md)
- [Liaison de données et Windows Forms](../data-binding-and-windows-forms.md)
- [Contrôles Windows Forms utilisés pour l'affichage de listes d'options](windows-forms-controls-used-to-list-options.md)
