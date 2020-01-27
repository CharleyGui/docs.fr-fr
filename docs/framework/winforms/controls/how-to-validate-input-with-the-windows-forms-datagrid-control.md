---
title: Valider l’entrée avec le contrôle DataGrid
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGrid control [Windows Forms], examples
- user input [Windows Forms], validating
- examples [Windows Forms], DataGrid control
- DataGrid control [Windows Forms], validating input
- validation [Windows Forms], user input
ms.assetid: f1e9c3a0-d0a1-4893-a615-b4b0db046c63
ms.openlocfilehash: 3958089007401d2e977c9c96f07c9196e6216596
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76728299"
---
# <a name="how-to-validate-input-with-the-windows-forms-datagrid-control"></a>Comment : valider les entrées à l'aide du contrôle DataGrid Windows Forms

> [!NOTE]
> Le contrôle <xref:System.Windows.Forms.DataGridView> remplace le contrôle <xref:System.Windows.Forms.DataGrid> et lui ajoute des fonctionnalités ; toutefois, le contrôle <xref:System.Windows.Forms.DataGrid> est conservé pour la compatibilité descendante et l'utilisation future si tel est votre choix. Pour plus d’informations, consultez [Différences entre les contrôles DataGridView et DataGrid Windows Forms](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).

Deux types de validation d’entrée sont disponibles pour le contrôle <xref:System.Windows.Forms.DataGrid> Windows Forms. Si l’utilisateur tente d’entrer une valeur d’un type de données inacceptable pour la cellule, par exemple une chaîne dans un entier, la nouvelle valeur non valide est remplacée par l’ancienne valeur. Ce type de validation d’entrée est effectué automatiquement et ne peut pas être personnalisé.

L’autre type de validation d’entrée peut être utilisé pour refuser toutes les données inacceptables, par exemple une valeur 0 dans un champ qui doit être supérieure ou égale à 1, ou une chaîne inappropriée. Pour ce faire, dans le jeu de données, écrivez un gestionnaire d’événements pour l’événement <xref:System.Data.DataTable.ColumnChanging> ou <xref:System.Data.DataTable.RowChanging>. L’exemple ci-dessous utilise l’événement <xref:System.Data.DataTable.ColumnChanging>, car la valeur inacceptable n’est pas autorisée pour la colonne « Product » en particulier. Vous pouvez utiliser l’événement <xref:System.Data.DataTable.RowChanging> pour vérifier que la valeur d’une colonne « Date de fin » est postérieure à la colonne « Date de début » dans la même ligne.

## <a name="to-validate-user-input"></a>Pour valider l’entrée d’utilisateur

1. Écrivez du code pour gérer l’événement <xref:System.Data.DataTable.ColumnChanging> pour la table appropriée. Quand une entrée inappropriée est détectée, appelez la méthode <xref:System.Data.DataRow.SetColumnError%2A> de l’objet <xref:System.Data.DataRow>.

    ```vb
    Private Sub Customers_ColumnChanging(ByVal sender As Object, _
    ByVal e As System.Data.DataColumnChangeEventArgs)
       ' Only check for errors in the Product column
       If (e.Column.ColumnName.Equals("Product")) Then
          ' Do not allow "Automobile" as a product.
          If CType(e.ProposedValue, String) = "Automobile" Then
             Dim badValue As Object = e.ProposedValue
             e.ProposedValue = "Bad Data"
             e.Row.RowError = "The Product column contains an error"
             e.Row.SetColumnError(e.Column, "Product cannot be " & _
             CType(badValue, String))
          End If
       End If
    End Sub
    ```

    ```csharp
    //Handle column changing events on the Customers table
    private void Customers_ColumnChanging(object sender, System.Data.DataColumnChangeEventArgs e) {

       //Only check for errors in the Product column
       if (e.Column.ColumnName.Equals("Product")) {

          //Do not allow "Automobile" as a product
          if (e.ProposedValue.Equals("Automobile")) {
             object badValue = e.ProposedValue;
             e.ProposedValue = "Bad Data";
             e.Row.RowError = "The Product column contains an error";
             e.Row.SetColumnError(e.Column, "Product cannot be " + badValue);
          }
       }
    }
    ```

2. Connectez le gestionnaire d’événements à l’événement.

    Placez le code suivant dans l’événement <xref:System.Windows.Forms.Form.Load> du formulaire ou dans son constructeur.

    ```vb
    ' Assumes the grid is bound to a dataset called customersDataSet1
    ' with a table called Customers.
    ' Put this code in the form's Load event or its constructor.
    AddHandler customersDataSet1.Tables("Customers").ColumnChanging, AddressOf Customers_ColumnChanging
    ```

    ```csharp
    // Assumes the grid is bound to a dataset called customersDataSet1
    // with a table called Customers.
    // Put this code in the form's Load event or its constructor.
    customersDataSet1.Tables["Customers"].ColumnChanging += new DataColumnChangeEventHandler(this.Customers_ColumnChanging);
    ```

## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.DataGrid>
- <xref:System.Data.DataTable.ColumnChanging>
- <xref:System.Data.DataRow.SetColumnError%2A>
- [DataGrid, contrôle](datagrid-control-windows-forms.md)
