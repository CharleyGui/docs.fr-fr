---
title: 'Procédure : afficher les erreurs au sein d’un jeu de données avec le composant ErrorProvider Windows Forms'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- errors [Windows Forms], dataset errors
- error messages [Windows Forms], viewing in datasets
- ErrorProvider component [Windows Forms], dataset errors
ms.assetid: cbae023f-d651-4210-bdea-bcc5f037e321
ms.openlocfilehash: 3dbd2ccca607869a6f28bc5b3bd1c9f0769db9f5
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69950083"
---
# <a name="how-to-view-errors-within-a-dataset-with-the-windows-forms-errorprovider-component"></a>Procédure : afficher les erreurs au sein d’un jeu de données avec le composant ErrorProvider Windows Forms
Vous pouvez utiliser le composant <xref:System.Windows.Forms.ErrorProvider> Windows Forms pour afficher les erreurs de colonne au sein d’un DataSet ou d’une autre source de données. Pour qu' <xref:System.Windows.Forms.ErrorProvider> un composant affiche des erreurs de données sur un formulaire, il n’est pas nécessaire qu’il soit directement associé à un contrôle. Une fois lié à une source de données, il peut afficher une icône d’erreur en regard de tout contrôle lié à la même source de données.  
  
> [!NOTE]
> Si vous modifiez les propriétés et <xref:System.Windows.Forms.ErrorProvider.DataSource%2A> <xref:System.Windows.Forms.ErrorProvider.DataMember%2A> du fournisseur d’erreur au moment de l’exécution, vous <xref:System.Windows.Forms.ErrorProvider.BindToDataAndErrors%2A> devez utiliser la méthode pour éviter les conflits.  
  
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
  
2. Définissez la <xref:System.Windows.Forms.ErrorProvider.ContainerControl%2A> propriété sur le formulaire.  
  
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
- [Guide pratique pour Afficher les icônes d’erreur pour la validation de formulaire avec le composant ErrorProvider Windows Forms](display-error-icons-for-form-validation-with-wf-errorprovider.md)
