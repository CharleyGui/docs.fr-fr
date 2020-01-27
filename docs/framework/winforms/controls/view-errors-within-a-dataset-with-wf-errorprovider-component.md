---
title: Afficher les erreurs dans un DataSet à l’aide du composant ErrorProvider
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- errors [Windows Forms], dataset errors
- error messages [Windows Forms], viewing in datasets
- ErrorProvider component [Windows Forms], dataset errors
ms.assetid: cbae023f-d651-4210-bdea-bcc5f037e321
ms.openlocfilehash: 8c2155bf288db89b5d53567738fd399b915d50b6
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745455"
---
# <a name="how-to-view-errors-within-a-dataset-with-the-windows-forms-errorprovider-component"></a>Comment : afficher des erreurs d'un groupe de données à l'aide du composant ErrorProvider Windows Forms
Vous pouvez utiliser le composant Windows Forms <xref:System.Windows.Forms.ErrorProvider> pour afficher les erreurs de colonne au sein d’un DataSet ou d’une autre source de données. Pour qu’un composant <xref:System.Windows.Forms.ErrorProvider> affiche des erreurs de données sur un formulaire, il n’est pas nécessaire qu’il soit directement associé à un contrôle. Une fois lié à une source de données, il peut afficher une icône d’erreur en regard de tout contrôle lié à la même source de données.  
  
> [!NOTE]
> Si vous modifiez les propriétés <xref:System.Windows.Forms.ErrorProvider.DataSource%2A> et <xref:System.Windows.Forms.ErrorProvider.DataMember%2A> du fournisseur d’erreur au moment de l’exécution, vous devez utiliser la méthode <xref:System.Windows.Forms.ErrorProvider.BindToDataAndErrors%2A> pour éviter les conflits.  
  
### <a name="to-display-data-errors"></a>Pour afficher les erreurs de données  
  
1. Liez le composant à une colonne spécifique dans une table de données.  
  
    ```vb  
    ' Assumes existence of DataSet1, DataTable1  
    TextBox1.DataBindings.Add("Text", DataSet1, "Customers.Name")  
    ErrorProvider1.DataSource = DataSet1  
    ErrorProvider1.DataMember = "Customers"  
    ```  
  
    ```csharp  
    // Assumes existence of DataSet1, DataTable1  
    textBox1.DataBindings.Add("Text", DataSet1, "Customers.Name");  
    errorProvider1.DataSource = DataSet1;  
    errorProvider1.DataMember = "Customers";  
    ```  
  
2. Définissez la propriété <xref:System.Windows.Forms.ErrorProvider.ContainerControl%2A> sur le formulaire.  
  
    ```vb  
    ErrorProvider1.ContainerControl = Me  
    ```  
  
    ```csharp  
    errorProvider1.ContainerControl = this;  
    ```  
  
3. Définit la position de l’enregistrement actuel sur une ligne qui contient une erreur de colonne.  
  
    ```vb  
    DataTable1.Rows(5).SetColumnError("Name", "Bad data in this row.")  
    Me.BindingContext(DataTable1).Position = 5  
    ```  
  
    ```csharp  
    DataTable1.Rows[5].SetColumnError("Name", "Bad data in this row.");  
    this.BindingContext [DataTable1].Position = 5;  
    ```  
  
## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble du composant ErrorProvider](errorprovider-component-overview-windows-forms.md)
- [Guide pratique pour afficher des icônes d’erreur pour la validation de formulaire à l’aide du composant ErrorProvider Windows Forms](display-error-icons-for-form-validation-with-wf-errorprovider.md)
