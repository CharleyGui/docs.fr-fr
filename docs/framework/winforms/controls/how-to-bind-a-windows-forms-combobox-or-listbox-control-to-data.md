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
# <a name="how-to-bind-a-windows-forms-combobox-or-listbox-control-to-data"></a><span data-ttu-id="65d23-102">Comment : lier un contrôle ComboBox ou ListBox Windows Forms aux données</span><span class="sxs-lookup"><span data-stu-id="65d23-102">How to: Bind a Windows Forms ComboBox or ListBox Control to Data</span></span>
<span data-ttu-id="65d23-103">Vous pouvez lier les <xref:System.Windows.Forms.ComboBox> et les <xref:System.Windows.Forms.ListBox> aux données pour effectuer des tâches telles que l’exploration des données dans une base de données, l’entrée de nouvelles données ou la modification de données existantes.</span><span class="sxs-lookup"><span data-stu-id="65d23-103">You can bind the <xref:System.Windows.Forms.ComboBox> and <xref:System.Windows.Forms.ListBox> to data to perform tasks such as browsing data in a database, entering new data, or editing existing data.</span></span>  
  
### <a name="to-bind-a-combobox-or-listbox-control"></a><span data-ttu-id="65d23-104">Pour lier un contrôle ComboBox ou ListBox</span><span class="sxs-lookup"><span data-stu-id="65d23-104">To bind a ComboBox or ListBox control</span></span>  
  
1. <span data-ttu-id="65d23-105">Affectez à la propriété `DataSource` un objet de source de données.</span><span class="sxs-lookup"><span data-stu-id="65d23-105">Set the `DataSource` property to a data source object.</span></span> <span data-ttu-id="65d23-106">Les sources de données possibles incluent une <xref:System.Windows.Forms.BindingSource> liée aux données, à une table de données, à une vue de données, à un DataSet, à un gestionnaire d’affichage de données, à un tableau ou à toute autre classe qui implémente l’interface <xref:System.Collections.IList>.</span><span class="sxs-lookup"><span data-stu-id="65d23-106">Possible data sources include a <xref:System.Windows.Forms.BindingSource> bound to data, a data table, a data view, a dataset, a data view manager, an array, or any class that implements the <xref:System.Collections.IList> interface.</span></span> <span data-ttu-id="65d23-107">Pour plus d’informations, consultez [sources de données prises en charge par Windows Forms](../data-sources-supported-by-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="65d23-107">For more information, see [Data Sources Supported by Windows Forms](../data-sources-supported-by-windows-forms.md).</span></span>  
  
2. <span data-ttu-id="65d23-108">Si vous effectuez une liaison à une table, définissez la propriété `DisplayMember` sur le nom d’une colonne dans la source de données.</span><span class="sxs-lookup"><span data-stu-id="65d23-108">If you are binding to a table, set the `DisplayMember` property to the name of a column in the data source.</span></span>  
  
     <span data-ttu-id="65d23-109">\- ou -</span><span class="sxs-lookup"><span data-stu-id="65d23-109">\- or -</span></span>  
  
     <span data-ttu-id="65d23-110">Si vous effectuez une liaison à une <xref:System.Collections.IList>, définissez le membre d’affichage sur une propriété publique du type dans la liste.</span><span class="sxs-lookup"><span data-stu-id="65d23-110">If you are binding to an <xref:System.Collections.IList>, set the display member to a public property of the type in the list.</span></span>  
  
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
    > <span data-ttu-id="65d23-111">Si vous êtes lié à une source de données qui n’implémente pas l’interface <xref:System.ComponentModel.IBindingList>, telle qu’un <xref:System.Collections.ArrayList>, les données du contrôle lié ne sont pas mises à jour lorsque la source de données est mise à jour.</span><span class="sxs-lookup"><span data-stu-id="65d23-111">If you are bound to a data source that does not implement the <xref:System.ComponentModel.IBindingList> interface, such as an <xref:System.Collections.ArrayList>, the bound control's data will not be updated when the data source is updated.</span></span> <span data-ttu-id="65d23-112">Par exemple, si une zone de liste déroulante est liée à une <xref:System.Collections.ArrayList> et que des données sont ajoutées à la <xref:System.Collections.ArrayList>, ces nouveaux éléments n’apparaîtront pas dans la zone de liste déroulante.</span><span class="sxs-lookup"><span data-stu-id="65d23-112">For example, if you have a combo box bound to an <xref:System.Collections.ArrayList> and data is added to the <xref:System.Collections.ArrayList>, these new items will not appear in the combo box.</span></span> <span data-ttu-id="65d23-113">Toutefois, vous pouvez forcer la mise à jour de la zone de liste déroulante en appelant les méthodes <xref:System.Windows.Forms.BindingManagerBase.SuspendBinding%2A> et <xref:System.Windows.Forms.BindingManagerBase.ResumeBinding%2A> sur l’instance de la classe <xref:System.Windows.Forms.BindingContext> à laquelle le contrôle est lié.</span><span class="sxs-lookup"><span data-stu-id="65d23-113">However, you can force the combo box to be updated by calling the <xref:System.Windows.Forms.BindingManagerBase.SuspendBinding%2A> and <xref:System.Windows.Forms.BindingManagerBase.ResumeBinding%2A> methods on the instance of the <xref:System.Windows.Forms.BindingContext> class to which the control is bound.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="65d23-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="65d23-114">See also</span></span>

- <xref:System.Windows.Forms.ComboBox>
- <xref:System.Windows.Forms.ListBox>
- [<span data-ttu-id="65d23-115">Liaison de données Windows Forms</span><span class="sxs-lookup"><span data-stu-id="65d23-115">Windows Forms Data Binding</span></span>](../windows-forms-data-binding.md)
- [<span data-ttu-id="65d23-116">Liaison de données et Windows Forms</span><span class="sxs-lookup"><span data-stu-id="65d23-116">Data Binding and Windows Forms</span></span>](../data-binding-and-windows-forms.md)
- [<span data-ttu-id="65d23-117">Contrôles Windows Forms utilisés pour l’affichage de listes d’options</span><span class="sxs-lookup"><span data-stu-id="65d23-117">Windows Forms Controls Used to List Options</span></span>](windows-forms-controls-used-to-list-options.md)
