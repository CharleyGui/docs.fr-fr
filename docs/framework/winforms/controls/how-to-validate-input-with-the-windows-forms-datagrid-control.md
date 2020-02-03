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
# <a name="how-to-validate-input-with-the-windows-forms-datagrid-control"></a><span data-ttu-id="5cf1e-102">Comment : valider les entrées à l'aide du contrôle DataGrid Windows Forms</span><span class="sxs-lookup"><span data-stu-id="5cf1e-102">How to: Validate Input with the Windows Forms DataGrid Control</span></span>

> [!NOTE]
> <span data-ttu-id="5cf1e-103">Le contrôle <xref:System.Windows.Forms.DataGridView> remplace le contrôle <xref:System.Windows.Forms.DataGrid> et lui ajoute des fonctionnalités ; toutefois, le contrôle <xref:System.Windows.Forms.DataGrid> est conservé pour la compatibilité descendante et l'utilisation future si tel est votre choix.</span><span class="sxs-lookup"><span data-stu-id="5cf1e-103">The <xref:System.Windows.Forms.DataGridView> control replaces and adds functionality to the <xref:System.Windows.Forms.DataGrid> control; however, the <xref:System.Windows.Forms.DataGrid> control is retained for both backward compatibility and future use, if you choose.</span></span> <span data-ttu-id="5cf1e-104">Pour plus d’informations, consultez [Différences entre les contrôles DataGridView et DataGrid Windows Forms](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span><span class="sxs-lookup"><span data-stu-id="5cf1e-104">For more information, see [Differences Between the Windows Forms DataGridView and DataGrid Controls](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span></span>

<span data-ttu-id="5cf1e-105">Deux types de validation d’entrée sont disponibles pour le contrôle <xref:System.Windows.Forms.DataGrid> Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="5cf1e-105">There are two types of input validation available for the Windows Forms <xref:System.Windows.Forms.DataGrid> control.</span></span> <span data-ttu-id="5cf1e-106">Si l’utilisateur tente d’entrer une valeur d’un type de données inacceptable pour la cellule, par exemple une chaîne dans un entier, la nouvelle valeur non valide est remplacée par l’ancienne valeur.</span><span class="sxs-lookup"><span data-stu-id="5cf1e-106">If the user attempts to enter a value that is of an unacceptable data type for the cell, for example a string into an integer, the new invalid value is replaced with the old value.</span></span> <span data-ttu-id="5cf1e-107">Ce type de validation d’entrée est effectué automatiquement et ne peut pas être personnalisé.</span><span class="sxs-lookup"><span data-stu-id="5cf1e-107">This kind of input validation is done automatically and cannot be customized.</span></span>

<span data-ttu-id="5cf1e-108">L’autre type de validation d’entrée peut être utilisé pour refuser toutes les données inacceptables, par exemple une valeur 0 dans un champ qui doit être supérieure ou égale à 1, ou une chaîne inappropriée.</span><span class="sxs-lookup"><span data-stu-id="5cf1e-108">The other type of input validation can be used to reject any unacceptable data, for example a 0 value in a field that must be greater than or equal to 1, or an inappropriate string.</span></span> <span data-ttu-id="5cf1e-109">Pour ce faire, dans le jeu de données, écrivez un gestionnaire d’événements pour l’événement <xref:System.Data.DataTable.ColumnChanging> ou <xref:System.Data.DataTable.RowChanging>.</span><span class="sxs-lookup"><span data-stu-id="5cf1e-109">This is done in the dataset by writing an event handler for the <xref:System.Data.DataTable.ColumnChanging> or <xref:System.Data.DataTable.RowChanging> event.</span></span> <span data-ttu-id="5cf1e-110">L’exemple ci-dessous utilise l’événement <xref:System.Data.DataTable.ColumnChanging>, car la valeur inacceptable n’est pas autorisée pour la colonne « Product » en particulier.</span><span class="sxs-lookup"><span data-stu-id="5cf1e-110">The example below uses the <xref:System.Data.DataTable.ColumnChanging> event because the unacceptable value is disallowed for the "Product" column in particular.</span></span> <span data-ttu-id="5cf1e-111">Vous pouvez utiliser l’événement <xref:System.Data.DataTable.RowChanging> pour vérifier que la valeur d’une colonne « Date de fin » est postérieure à la colonne « Date de début » dans la même ligne.</span><span class="sxs-lookup"><span data-stu-id="5cf1e-111">You might use the <xref:System.Data.DataTable.RowChanging> event for checking that the value of an "End Date" column is later than the "Start Date" column in the same row.</span></span>

## <a name="to-validate-user-input"></a><span data-ttu-id="5cf1e-112">Pour valider l’entrée d’utilisateur</span><span class="sxs-lookup"><span data-stu-id="5cf1e-112">To validate user input</span></span>

1. <span data-ttu-id="5cf1e-113">Écrivez du code pour gérer l’événement <xref:System.Data.DataTable.ColumnChanging> pour la table appropriée.</span><span class="sxs-lookup"><span data-stu-id="5cf1e-113">Write code to handle the <xref:System.Data.DataTable.ColumnChanging> event for the appropriate table.</span></span> <span data-ttu-id="5cf1e-114">Quand une entrée inappropriée est détectée, appelez la méthode <xref:System.Data.DataRow.SetColumnError%2A> de l’objet <xref:System.Data.DataRow>.</span><span class="sxs-lookup"><span data-stu-id="5cf1e-114">When inappropriate input is detected, call the <xref:System.Data.DataRow.SetColumnError%2A> method of the <xref:System.Data.DataRow> object.</span></span>

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

2. <span data-ttu-id="5cf1e-115">Connectez le gestionnaire d’événements à l’événement.</span><span class="sxs-lookup"><span data-stu-id="5cf1e-115">Connect the event handler to the event.</span></span>

    <span data-ttu-id="5cf1e-116">Placez le code suivant dans l’événement <xref:System.Windows.Forms.Form.Load> du formulaire ou dans son constructeur.</span><span class="sxs-lookup"><span data-stu-id="5cf1e-116">Place the following code within either the form's <xref:System.Windows.Forms.Form.Load> event or its constructor.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="5cf1e-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5cf1e-117">See also</span></span>

- <xref:System.Windows.Forms.DataGrid>
- <xref:System.Data.DataTable.ColumnChanging>
- <xref:System.Data.DataRow.SetColumnError%2A>
- [<span data-ttu-id="5cf1e-118">DataGrid, contrôle</span><span class="sxs-lookup"><span data-stu-id="5cf1e-118">DataGrid Control</span></span>](datagrid-control-windows-forms.md)
