---
title: Méthode Load
ms.date: 03/30/2017
dev_langs:
- vb
ms.assetid: e22e5812-89c6-41f0-9302-bb899a46dbff
ms.openlocfilehash: ea437d1f8ed567934acafbd8db1f8dba8eb22bcc
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91177538"
---
# <a name="the-load-method"></a><span data-ttu-id="5e923-102">Méthode Load</span><span class="sxs-lookup"><span data-stu-id="5e923-102">The Load Method</span></span>

<span data-ttu-id="5e923-103">Vous pouvez utiliser la méthode <xref:System.Data.DataTable.Load%2A> pour charger un objet <xref:System.Data.DataTable> de lignes d'une source de données.</span><span class="sxs-lookup"><span data-stu-id="5e923-103">You can use the <xref:System.Data.DataTable.Load%2A> method to load a <xref:System.Data.DataTable> with rows from a data source.</span></span> <span data-ttu-id="5e923-104">Il s’agit d’une méthode surchargée qui, dans sa forme la plus simple, accepte un seul paramètre, **DataReader**.</span><span class="sxs-lookup"><span data-stu-id="5e923-104">This is an overloaded method which, in its simplest form, accepts a single parameter, a **DataReader**.</span></span> <span data-ttu-id="5e923-105">Dans cette forme, il charge simplement le **DataTable** avec des lignes.</span><span class="sxs-lookup"><span data-stu-id="5e923-105">In this form, it simply loads the **DataTable** with rows.</span></span> <span data-ttu-id="5e923-106">Si vous le souhaitez, vous pouvez spécifier le paramètre **LoadOption** pour contrôler la façon dont les données sont ajoutées au **DataTable**.</span><span class="sxs-lookup"><span data-stu-id="5e923-106">Optionally, you can specify the **LoadOption** parameter to control how data is added to the **DataTable**.</span></span>  
  
 <span data-ttu-id="5e923-107">Le paramètre **LoadOption** est particulièrement utile dans les cas où le **DataTable** contient déjà des lignes de données, car il décrit la façon dont les données entrantes de la source de données sont combinées avec les données déjà présentes dans la table.</span><span class="sxs-lookup"><span data-stu-id="5e923-107">The **LoadOption** parameter is particularly useful in cases where the **DataTable** already contains rows of data, because it describes how incoming data from the data source will be combined with the data already in the table.</span></span> <span data-ttu-id="5e923-108">Par exemple, **PreserveCurrentValues** (valeur par défaut) spécifie que dans les cas où une ligne est marquée comme **ajoutée** dans le **DataTable**, la valeur **d’origine** ou chaque colonne est définie sur le contenu de la ligne correspondante de la source de données.</span><span class="sxs-lookup"><span data-stu-id="5e923-108">For example, **PreserveCurrentValues** (the default) specifies that in cases where a row is marked as **Added** in the **DataTable**, the **Original** value or each column is set to the contents of the matching row from the data source.</span></span> <span data-ttu-id="5e923-109">La valeur **actuelle** conservera les valeurs assignées lors de l’ajout de la ligne et le **RowState** de la ligne aura la valeur **Changed**.</span><span class="sxs-lookup"><span data-stu-id="5e923-109">The **Current** value will retain the values assigned when the row was added, and the **RowState** of the row will be set to **Changed**.</span></span>  
  
 <span data-ttu-id="5e923-110">Le tableau suivant donne une brève description des valeurs d'énumération <xref:System.Data.LoadOption>.</span><span class="sxs-lookup"><span data-stu-id="5e923-110">The following table gives a short description of the <xref:System.Data.LoadOption> enumeration values.</span></span>  
  
|<span data-ttu-id="5e923-111">Valeur LoadOption</span><span class="sxs-lookup"><span data-stu-id="5e923-111">LoadOption value</span></span>|<span data-ttu-id="5e923-112">Description</span><span class="sxs-lookup"><span data-stu-id="5e923-112">Description</span></span>|  
|----------------------|-----------------|  
|<span data-ttu-id="5e923-113">**OverwriteRow**</span><span class="sxs-lookup"><span data-stu-id="5e923-113">**OverwriteRow**</span></span>|<span data-ttu-id="5e923-114">Si les lignes entrantes ont la même valeur **PrimaryKey** qu’une ligne figurant déjà dans le **DataTable**, les valeurs **d’origine** et **actuelles** de chaque colonne sont remplacées par les valeurs de la ligne entrante et la propriété **RowState** est définie sur **Unchanged**.</span><span class="sxs-lookup"><span data-stu-id="5e923-114">If incoming rows have the same **PrimaryKey** value as a row already in the **DataTable**, the **Original** and **Current** values of each column are replaced with the values in the incoming row, and the **RowState** property is set to **Unchanged**.</span></span><br /><br /> <span data-ttu-id="5e923-115">Les lignes de la source de données qui n’existent pas encore dans le **DataTable** sont ajoutées avec une valeur **RowState** **inchangée**.</span><span class="sxs-lookup"><span data-stu-id="5e923-115">Rows from the data source that do not already exist in the **DataTable** are added with a **RowState** value of **Unchanged**.</span></span><br /><br /> <span data-ttu-id="5e923-116">Cette option permet d’actualiser le contenu du **DataTable** afin qu’il corresponde au contenu de la source de données.</span><span class="sxs-lookup"><span data-stu-id="5e923-116">This option in effect refreshes the contents of the **DataTable** so that it matches the contents of the data source.</span></span>|  
|<span data-ttu-id="5e923-117">**PreserveCurrentValues (par défaut)**</span><span class="sxs-lookup"><span data-stu-id="5e923-117">**PreserveCurrentValues (default)**</span></span>|<span data-ttu-id="5e923-118">Si les lignes entrantes ont la même valeur **PrimaryKey** qu’une ligne figurant déjà dans le **DataTable**, la valeur **d’origine** est définie sur le contenu de la ligne entrante et la valeur **actuelle** n’est pas modifiée.</span><span class="sxs-lookup"><span data-stu-id="5e923-118">If incoming rows have the same **PrimaryKey** value as a row already in the **DataTable**, the **Original** value is set to the contents of the incoming row, and the **Current** value is not changed.</span></span><br /><br /> <span data-ttu-id="5e923-119">Si le **RowState** est **ajouté** ou **modifié**, il est défini sur **modifié**.</span><span class="sxs-lookup"><span data-stu-id="5e923-119">If the **RowState** is **Added** or **Modified**, it is set to **Modified**.</span></span><br /><br /> <span data-ttu-id="5e923-120">Si le **RowState** a été **supprimé**, il reste **supprimé**.</span><span class="sxs-lookup"><span data-stu-id="5e923-120">If the **RowState** was **Deleted**, it remains **Deleted**.</span></span><br /><br /> <span data-ttu-id="5e923-121">Les lignes de la source de données qui n’existent pas encore dans le **DataTable** sont ajoutées, et **RowState** a la valeur **Unchanged**.</span><span class="sxs-lookup"><span data-stu-id="5e923-121">Rows from the data source that do not already exist in the **DataTable** are added, and the **RowState** is set to **Unchanged**.</span></span>|  
|<span data-ttu-id="5e923-122">**UpdateCurrentValues**</span><span class="sxs-lookup"><span data-stu-id="5e923-122">**UpdateCurrentValues**</span></span>|<span data-ttu-id="5e923-123">Si les lignes entrantes ont la même valeur **PrimaryKey** que la ligne qui se trouve déjà dans le **DataTable**, la valeur **actuelle** est copiée à la valeur **d’origine** , et la valeur **actuelle** est ensuite définie sur le contenu de la ligne entrante.</span><span class="sxs-lookup"><span data-stu-id="5e923-123">If incoming rows have the same **PrimaryKey** value as the row already in the **DataTable**, the **Current** value is copied to the **Original** value, and the **Current** value is then set to the contents of the incoming row.</span></span><br /><br /> <span data-ttu-id="5e923-124">Si le **RowState** dans le **DataTable** a été **ajouté**, le **RowState** reste **ajouté**.</span><span class="sxs-lookup"><span data-stu-id="5e923-124">If the **RowState** in the **DataTable** was **Added**, the **RowState** remains **Added**.</span></span> <span data-ttu-id="5e923-125">Pour les lignes marquées comme étant **modifiées** ou **supprimées**, le **RowState** est **modifié**.</span><span class="sxs-lookup"><span data-stu-id="5e923-125">For rows marked as **Modified** or **Deleted**, the **RowState** is **Modified**.</span></span><br /><br /> <span data-ttu-id="5e923-126">Les lignes de la source de données qui n’existent pas encore dans le **DataTable** sont ajoutées, et **RowState** a la valeur **added**.</span><span class="sxs-lookup"><span data-stu-id="5e923-126">Rows from the data source that do not already exist in the **DataTable** are added, and the **RowState** is set to **Added**.</span></span>|  
  
 <span data-ttu-id="5e923-127">L’exemple suivant utilise la méthode **Load** pour afficher une liste d’anniversaires pour les employés de la base de données **Northwind** .</span><span class="sxs-lookup"><span data-stu-id="5e923-127">The following sample uses the **Load** method to display a list of birthdays for the employees in the **Northwind** database.</span></span>  
  
```vb  
Private Sub LoadBirthdays(ByVal connectionString As String)  
    ' Assumes that connectionString is a valid connection string  
    ' to the Northwind database on SQL Server.  
    Dim queryString As String = _  
    "SELECT LastName, FirstName, BirthDate " & _  
      " FROM dbo.Employees " & _  
      "ORDER BY BirthDate, LastName, FirstName"  
  
    ' Open and fill a DataSet.
    Dim adapter As SqlDataAdapter = New SqlDataAdapter( _  
        queryString, connectionString)  
    Dim employees As New DataSet  
    adapter.Fill(employees, "Employees")  
  
    ' Create a SqlDataReader for use with the Load Method.  
    Dim reader As DataTableReader = employees.GetDataReader()  
  
    ' Create an instance of DataTable and assign the first  
    ' DataTable in the DataSet.Tables collection to it.  
    Dim dataTableEmp As DataTable = employees.Tables(0)  
  
    ' Fill the DataTable with data by calling Load and  
    ' passing the SqlDataReader.  
    dataTableEmp.Load(reader, LoadOption.OverwriteRow)  
  
    ' Loop through the rows collection and display the values  
    ' in the console window.  
    Dim employeeRow As DataRow  
    For Each employeeRow In dataTableEmp.Rows  
        Console.WriteLine("{0:MM\\dd\\yyyy}" & ControlChars.Tab & _  
          "{1}, {2}", _  
          employeeRow("BirthDate"), _  
          employeeRow("LastName"), _  
          employeeRow("FirstName"))  
    Next employeeRow  
  
    ' Keep the window opened to view the contents.  
    Console.ReadLine()  
End Sub  
```  
  
## <a name="see-also"></a><span data-ttu-id="5e923-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5e923-128">See also</span></span>

- [<span data-ttu-id="5e923-129">Manipulation des données dans un DataTable</span><span class="sxs-lookup"><span data-stu-id="5e923-129">Manipulating Data in a DataTable</span></span>](manipulating-data-in-a-datatable.md)
- [<span data-ttu-id="5e923-130">Vue d'ensemble d’ADO.NET</span><span class="sxs-lookup"><span data-stu-id="5e923-130">ADO.NET Overview</span></span>](../ado-net-overview.md)
