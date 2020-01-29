---
title: Créer une table de recherche pour un contrôle ComboBox, ListBox ou CheckedListBox
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- CheckedListBox control [Windows Forms], creating lookup tables
- lookup tables
- list boxes [Windows Forms], lookup tables
- ListBox control [Windows Forms], lookup tables
- ComboBox control [Windows Forms], lookup table
- lookup tables [Windows Forms], creating for controls
- combo boxes [Windows Forms], lookup tables
- ListBox control [Windows Forms], creating lookup tables
ms.assetid: 4ce35f12-1f4e-4317-92d1-af8686a8cfaa
ms.openlocfilehash: 4bbbc66a56c7ce269c2dabd593db88f96907d755
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76737372"
---
# <a name="how-to-create-a-lookup-table-for-a-windows-forms-combobox-listbox-or-checkedlistbox-control"></a>Comment : créer une table de correspondance pour un contrôle ComboBox, ListBox ou CheckedListBox Windows Forms
Il est parfois utile d'afficher les données dans un format convivial dans un Windows Form, mais de les stocker dans un format plus pertinent pour votre programme. Par exemple, un formulaire de commande de produits alimentaires peut présenter les éléments de menu par leur nom dans une zone de liste. Toutefois, la table de données dans laquelle la commande est enregistrée contient alors les numéros d'ID uniques représentant les produits alimentaires. Les tableaux ci-dessous montrent un exemple de stockage et d’affichage des données du formulaire de commande des produits alimentaires.  
  
### <a name="orderdetailstable"></a>OrderDetailsTable  
  
|OrderID|ItemID|Quantité|  
|-------------|------------|--------------|  
|4085|12|1|  
|4086|13|3|  
  
### <a name="itemtable"></a>ItemTable  
  
|Id|Name|  
|--------|----------|  
|12|Pomme de terre|  
|13|Poulet|  
  
 Dans ce scénario, une table, **OrderDetailsTable**, stocke les informations réelles que vous êtes préoccupé par l’affichage et l’enregistrement. Cependant, pour économiser de l'espace, elle procède d’une façon plutôt insolite. L’autre table, **ItemTable**, contient uniquement des informations relatives à l’apparence concernant le numéro d’ID qui est équivalent au nom de la nourriture, et rien sur les bons de commande réels.  
  
 Le **ItemTable** est connecté au contrôle <xref:System.Windows.Forms.ComboBox>, <xref:System.Windows.Forms.ListBox>ou <xref:System.Windows.Forms.CheckedListBox> par le biais de trois propriétés. La propriété `DataSource` contient le nom de cette table. La propriété `DisplayMember` contient la colonne de données de la table que vous souhaitez afficher dans le contrôle (nom de la Food). La propriété `ValueMember` contient la colonne de données de cette table avec les informations stockées (numéro d’ID).  
  
 **OrderDetailsTable** est connectée au contrôle par sa collection de liaisons, accessible via la propriété <xref:System.Windows.Forms.Control.DataBindings%2A>. Lorsque vous ajoutez un objet de liaison à la collection, vous connectez une propriété de contrôle à un membre de données spécifique (la colonne de numéros d’identification) dans une source de données ( **OrderDetailsTable**). Quand une sélection est effectuée dans le contrôle, c’est dans cette table que l'entrée du formulaire est enregistrée.  
  
### <a name="to-create-a-lookup-table"></a>Pour créer une table de choix  
  
1. Ajoutez un contrôle <xref:System.Windows.Forms.ComboBox>, <xref:System.Windows.Forms.ListBox> ou <xref:System.Windows.Forms.CheckedListBox> au formulaire.  
  
2. Connectez-vous à la source de données.  
  
3. Établissez une relation de données entre les deux tables. Consultez [Introduction aux objets DataRelation](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/0k21zcyx(v=vs.120)).  
  
4. Définissez les propriétés ci-dessous. Elles peuvent être définies dans le code ou dans le concepteur.  
  
    |Les|Paramètre|  
    |--------------|-------------|  
    |<xref:System.Windows.Forms.ListControl.DataSource%2A>|Table qui contient des informations sur les équivalences entre les numéros d’ID et les articles. Dans le scénario précédent, il s’agit de `ItemTable`.|  
    |<xref:System.Windows.Forms.ListControl.DisplayMember%2A>|Colonne de la table de source de données que vous souhaitez afficher dans le contrôle. Dans le scénario précédent, il s’agit de `"Name"` (à définir dans le code, utilisez des guillemets).|  
    |<xref:System.Windows.Forms.ListControl.ValueMember%2A>|Colonne de la table de source de données qui contient les informations stockées. Dans le scénario précédent, il s’agit de `"ID"` (à définir dans le code, utilisez des guillemets).|  
  
5. Dans une procédure, appelez la méthode <xref:System.Windows.Forms.ControlBindingsCollection.Add%2A> de la classe <xref:System.Windows.Forms.ControlBindingsCollection> pour lier la ppropriété <xref:System.Windows.Forms.ListControl.SelectedValue%2A> du contrôle à la table d'enregistrement de l'entrée du formulaire. Vous pouvez également effectuer cette opération dans le concepteur plutôt que dans le code, en accédant à la propriété <xref:System.Windows.Forms.Control.DataBindings%2A> du contrôle dans la fenêtre **Propriétés** . Dans le scénario précédent, il s’agit de `OrderDetailsTable`, et la colonne est `"ItemID"`.  
  
    ```vb  
    ListBox1.DataBindings.Add("SelectedValue", OrderDetailsTable, "ItemID")  
    ```  
  
    ```csharp  
    listBox1.DataBindings.Add("SelectedValue", OrderDetailsTable, "ItemID");  
    ```  
  
## <a name="see-also"></a>Voir aussi

- [Liaison de données et Windows Forms](../data-binding-and-windows-forms.md)
- [Vue d'ensemble du contrôle ListBox](listbox-control-overview-windows-forms.md)
- [Vue d'ensemble du contrôle ComboBox](combobox-control-overview-windows-forms.md)
- [Vue d'ensemble du contrôle CheckedListBox](checkedlistbox-control-overview-windows-forms.md)
- [Contrôles Windows Forms utilisés pour l’affichage de listes d’options](windows-forms-controls-used-to-list-options.md)
