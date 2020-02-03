---
title: Supprimer ou masquer des colonnes dans le contrôle DataGrid
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data grids [Windows Forms], deleting columns
- DataGrid control [Windows Forms], deleting columns
- data grids [Windows Forms], hiding columns
- columns [Windows Forms], hiding
- columns [Windows Forms], deleting in data grids
- DataGrid control [Windows Forms], hiding columns
ms.assetid: bcd0dd96-6687-4c48-b0e1-d5287b93ac91
ms.openlocfilehash: c730be934e9b978bdaf09bc7e668b4318077fba5
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743298"
---
# <a name="how-to-delete-or-hide-columns-in-the-windows-forms-datagrid-control"></a><span data-ttu-id="cf582-102">Comment : supprimer ou masquer des colonnes dans le contrôle DataGrid Windows Forms</span><span class="sxs-lookup"><span data-stu-id="cf582-102">How to: Delete or Hide Columns in the Windows Forms DataGrid Control</span></span>
> [!NOTE]
> <span data-ttu-id="cf582-103">Le contrôle <xref:System.Windows.Forms.DataGridView> remplace le contrôle <xref:System.Windows.Forms.DataGrid> et lui ajoute des fonctionnalités ; toutefois, le contrôle <xref:System.Windows.Forms.DataGrid> est conservé pour la compatibilité descendante et l'utilisation future si tel est votre choix.</span><span class="sxs-lookup"><span data-stu-id="cf582-103">The <xref:System.Windows.Forms.DataGridView> control replaces and adds functionality to the <xref:System.Windows.Forms.DataGrid> control; however, the <xref:System.Windows.Forms.DataGrid> control is retained for both backward compatibility and future use, if you choose.</span></span> <span data-ttu-id="cf582-104">Pour plus d’informations, consultez [Différences entre les contrôles DataGridView et DataGrid Windows Forms](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span><span class="sxs-lookup"><span data-stu-id="cf582-104">For more information, see [Differences Between the Windows Forms DataGridView and DataGrid Controls](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span></span>  
  
 <span data-ttu-id="cf582-105">Vous pouvez supprimer ou masquer par programmation les colonnes du contrôle Windows Forms <xref:System.Windows.Forms.DataGrid> à l’aide des propriétés et des méthodes des objets <xref:System.Windows.Forms.GridColumnStylesCollection> et <xref:System.Windows.Forms.DataGridColumnStyle> (qui sont membres de la classe <xref:System.Windows.Forms.DataGridTableStyle>).</span><span class="sxs-lookup"><span data-stu-id="cf582-105">You can programmatically delete or hide columns in the Windows Forms <xref:System.Windows.Forms.DataGrid> control by using the properties and methods of the <xref:System.Windows.Forms.GridColumnStylesCollection> and <xref:System.Windows.Forms.DataGridColumnStyle> objects (which are members of the <xref:System.Windows.Forms.DataGridTableStyle> class).</span></span>  
  
 <span data-ttu-id="cf582-106">Les colonnes supprimées ou masquées existent toujours dans la source de données à laquelle la grille est liée, et sont toujours accessibles par programme.</span><span class="sxs-lookup"><span data-stu-id="cf582-106">The deleted or hidden columns still exist in the data source the grid is bound to, and can still be accessed programmatically.</span></span> <span data-ttu-id="cf582-107">Ils ne sont plus visibles dans le DataGrid.</span><span class="sxs-lookup"><span data-stu-id="cf582-107">They are just no longer visible in the datagrid.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="cf582-108">Si votre application n’accède pas à certaines colonnes de données et que vous ne souhaitez pas qu’elles s’affichent dans la grille de données, il n’est probablement pas nécessaire de les inclure dans la source de données en premier lieu.</span><span class="sxs-lookup"><span data-stu-id="cf582-108">If your application does not access certain columns of data, and you do not want them displayed in the datagrid, then it is probably not necessary to include them in the data source in the first place.</span></span>  
  
### <a name="to-delete-a-column-from-the-datagrid-programmatically"></a><span data-ttu-id="cf582-109">Pour supprimer une colonne de la grille de contrôle DataGrid par programmation</span><span class="sxs-lookup"><span data-stu-id="cf582-109">To delete a column from the DataGrid programmatically</span></span>  
  
1. <span data-ttu-id="cf582-110">Dans la zone déclarations de votre formulaire, déclarez une nouvelle instance de la classe <xref:System.Windows.Forms.DataGridTableStyle>.</span><span class="sxs-lookup"><span data-stu-id="cf582-110">In the declarations area of your form, declare a new instance of the <xref:System.Windows.Forms.DataGridTableStyle> class.</span></span>  
  
2. <span data-ttu-id="cf582-111">Affectez à la propriété <xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A?displayProperty=nameWithType> la table de votre source de données à laquelle vous souhaitez appliquer le style.</span><span class="sxs-lookup"><span data-stu-id="cf582-111">Set the <xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A?displayProperty=nameWithType> property to the table in your data source that you want to apply the style to.</span></span> <span data-ttu-id="cf582-112">L’exemple suivant utilise la propriété <xref:System.Windows.Forms.DataGrid.DataMember%2A?displayProperty=nameWithType>, qu’elle suppose comme étant déjà définie.</span><span class="sxs-lookup"><span data-stu-id="cf582-112">The following example uses the <xref:System.Windows.Forms.DataGrid.DataMember%2A?displayProperty=nameWithType> property, which it assumes is already set.</span></span>  
  
3. <span data-ttu-id="cf582-113">Ajoutez le nouvel objet <xref:System.Windows.Forms.DataGridTableStyle> à la collection de styles de table de DataGrid.</span><span class="sxs-lookup"><span data-stu-id="cf582-113">Add the new <xref:System.Windows.Forms.DataGridTableStyle> object to the datagrid's table styles collection.</span></span>  
  
4. <span data-ttu-id="cf582-114">Appelez la méthode <xref:System.Windows.Forms.GridColumnStylesCollection.RemoveAt%2A> de la collection de <xref:System.Windows.Forms.DataGridTableStyle.GridColumnStyles%2A> du <xref:System.Windows.Forms.DataGrid>, en spécifiant l’index de colonne de la colonne à supprimer.</span><span class="sxs-lookup"><span data-stu-id="cf582-114">Call the <xref:System.Windows.Forms.GridColumnStylesCollection.RemoveAt%2A> method of the <xref:System.Windows.Forms.DataGrid>'s <xref:System.Windows.Forms.DataGridTableStyle.GridColumnStyles%2A> collection, specifying the column index of the column to delete.</span></span>  
  
    ```vb  
    ' Declare a new DataGridTableStyle in the  
    ' declarations area of your form.  
    Dim ts As DataGridTableStyle = New DataGridTableStyle()  
  
    Sub DeleteColumn()  
       ' Set the DataGridTableStyle.MappingName property  
       ' to the table in the data source to map to.  
       ts.MappingName = DataGrid1.DataMember  
  
       ' Add it to the datagrid's TableStyles collection  
       DataGrid1.TableStyles.Add(ts)  
  
       ' Delete the first column (index 0)  
       DataGrid1.TableStyles(0).GridColumnStyles.RemoveAt(0)  
    End Sub  
    ```  
  
    ```csharp  
    // Declare a new DataGridTableStyle in the  
    // declarations area of your form.  
    DataGridTableStyle ts = new DataGridTableStyle();  
  
    private void deleteColumn()  
    {  
       // Set the DataGridTableStyle.MappingName property  
       // to the table in the data source to map to.  
       ts.MappingName = dataGrid1.DataMember;  
  
       // Add it to the datagrid's TableStyles collection  
       dataGrid1.TableStyles.Add(ts);  
  
       // Delete the first column (index 0)  
       dataGrid1.TableStyles[0].GridColumnStyles.RemoveAt(0);  
    }  
    ```  
  
### <a name="to-hide-a-column-in-the-datagrid-programmatically"></a><span data-ttu-id="cf582-115">Pour masquer une colonne dans la grille de contrôle DataGrid par programmation</span><span class="sxs-lookup"><span data-stu-id="cf582-115">To hide a column in the DataGrid programmatically</span></span>  
  
1. <span data-ttu-id="cf582-116">Dans la zone déclarations de votre formulaire, déclarez une nouvelle instance de la classe <xref:System.Windows.Forms.DataGridTableStyle>.</span><span class="sxs-lookup"><span data-stu-id="cf582-116">In the declarations area of your form, declare a new instance of the <xref:System.Windows.Forms.DataGridTableStyle> class.</span></span>  
  
2. <span data-ttu-id="cf582-117">Définissez la propriété <xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A> du <xref:System.Windows.Forms.DataGridTableStyle> sur la table de votre source de données à laquelle vous souhaitez appliquer le style.</span><span class="sxs-lookup"><span data-stu-id="cf582-117">Set the <xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A> property of the <xref:System.Windows.Forms.DataGridTableStyle> to the table in your data source that you want to apply the style to.</span></span> <span data-ttu-id="cf582-118">L’exemple de code suivant utilise la propriété <xref:System.Windows.Forms.DataGrid.DataMember%2A?displayProperty=nameWithType>, qu’il suppose comme étant déjà définie.</span><span class="sxs-lookup"><span data-stu-id="cf582-118">The following code example uses the <xref:System.Windows.Forms.DataGrid.DataMember%2A?displayProperty=nameWithType> property, which it assumes is already set.</span></span>  
  
3. <span data-ttu-id="cf582-119">Ajoutez le nouvel objet <xref:System.Windows.Forms.DataGridTableStyle> à la collection de styles de table de DataGrid.</span><span class="sxs-lookup"><span data-stu-id="cf582-119">Add the new <xref:System.Windows.Forms.DataGridTableStyle> object to the datagrid's table styles collection.</span></span>  
  
4. <span data-ttu-id="cf582-120">Masquez la colonne en affectant à sa propriété `Width` la valeur 0, en spécifiant l’index de colonne de la colonne à masquer.</span><span class="sxs-lookup"><span data-stu-id="cf582-120">Hide the column by setting its `Width` property to 0, specifying the column index of the column to hide.</span></span>  
  
    ```vb  
    ' Declare a new DataGridTableStyle in the  
    ' declarations area of your form.  
    Dim ts As DataGridTableStyle = New DataGridTableStyle()  
  
    Sub HideColumn()  
       ' Set the DataGridTableStyle.MappingName property  
       ' to the table in the data source to map to.  
       ts.MappingName = DataGrid1.DataMember  
  
       ' Add it to the datagrid's TableStyles collection  
       DataGrid1.TableStyles.Add(ts)  
  
       ' Hide the first column (index 0)  
       DataGrid1.TableStyles(0).GridColumnStyles(0).Width = 0  
    End Sub  
    ```  
  
    ```csharp  
    // Declare a new DataGridTableStyle in the  
    // declarations area of your form.  
    DataGridTableStyle ts = new DataGridTableStyle();  
  
    private void hideColumn()  
    {  
       // Set the DataGridTableStyle.MappingName property  
       // to the table in the data source to map to.  
       ts.MappingName = dataGrid1.DataMember;  
  
       // Add it to the datagrid's TableStyles collection  
       dataGrid1.TableStyles.Add(ts);  
  
       // Hide the first column (index 0)  
       dataGrid1.TableStyles[0].GridColumnStyles[0].Width = 0;  
    }  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="cf582-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="cf582-121">See also</span></span>

- [<span data-ttu-id="cf582-122">Guide pratique pour modifier des données affichées dans le contrôle DataGrid Windows Forms au moment de l’exécution</span><span class="sxs-lookup"><span data-stu-id="cf582-122">How to: Change Displayed Data at Run Time in the Windows Forms DataGrid Control</span></span>](change-displayed-data-at-run-time-wf-datagrid-control.md)
- [<span data-ttu-id="cf582-123">Guide pratique pour ajouter des tables et des colonnes au contrôle DataGrid Windows Forms</span><span class="sxs-lookup"><span data-stu-id="cf582-123">How to: Add Tables and Columns to the Windows Forms DataGrid Control</span></span>](how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control.md)
