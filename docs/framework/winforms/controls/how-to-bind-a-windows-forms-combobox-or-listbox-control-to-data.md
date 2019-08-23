---
title: 'Procédure : lier un contrôle ComboBox ou ListBox Windows Forms à des données'
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
ms.openlocfilehash: f361526c44f8fbb9ab282fe15ae109b67e8f01dd
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69922753"
---
# <a name="how-to-bind-a-windows-forms-combobox-or-listbox-control-to-data"></a>Procédure : lier un contrôle ComboBox ou ListBox Windows Forms à des données
Vous pouvez lier le <xref:System.Windows.Forms.ComboBox> et <xref:System.Windows.Forms.ListBox> aux données pour effectuer des tâches telles que l’exploration de données dans une base de données, l’entrée de nouvelles données ou la modification de données existantes.  
  
### <a name="to-bind-a-combobox-or-listbox-control"></a>Pour lier un contrôle ComboBox ou ListBox  
  
1. Affectez `DataSource` à la propriété un objet de source de données. Les sources de données possibles <xref:System.Windows.Forms.BindingSource> incluent une liée à des données, une table de données, une vue de données, un DataSet, un gestionnaire d’affichage de données, un tableau ou <xref:System.Collections.IList> toute classe qui implémente l’interface. Pour plus d’informations, consultez [sources de données prises en charge par Windows Forms](../data-sources-supported-by-windows-forms.md).  
  
2. Si vous effectuez une liaison à une table, définissez `DisplayMember` la propriété sur le nom d’une colonne dans la source de données.  
  
     \- ou -  
  
     Si vous effectuez une liaison à <xref:System.Collections.IList>un, définissez le membre d’affichage sur une propriété publique du type dans la liste.  
  
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
    > Si vous êtes lié à une source de données qui n’implémente <xref:System.ComponentModel.IBindingList> pas l’interface, telle <xref:System.Collections.ArrayList>que, les données du contrôle lié ne sont pas mises à jour lorsque la source de données est mise à jour. Par exemple, si une zone de liste déroulante est <xref:System.Collections.ArrayList> liée à un et que des <xref:System.Collections.ArrayList>données sont ajoutées au, ces nouveaux éléments n’apparaîtront pas dans la zone de liste déroulante. Toutefois, vous pouvez forcer la mise à jour de la zone de liste <xref:System.Windows.Forms.BindingManagerBase.SuspendBinding%2A> déroulante en appelant les méthodes <xref:System.Windows.Forms.BindingContext> et <xref:System.Windows.Forms.BindingManagerBase.ResumeBinding%2A> sur l’instance de la classe à laquelle le contrôle est lié.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.ComboBox>
- <xref:System.Windows.Forms.ListBox>
- [Liaison de données Windows Forms](../windows-forms-data-binding.md)
- [Liaison de données et Windows Forms](../data-binding-and-windows-forms.md)
- [Contrôles Windows Forms utilisés pour l’affichage de listes d’options](windows-forms-controls-used-to-list-options.md)
