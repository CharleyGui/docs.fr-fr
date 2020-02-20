---
title: Manipulation de données
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 51096a2e-8b38-4c4d-a523-799bfdb7ec69
ms.openlocfilehash: a84f74bde8da9ca7e40184b76efe51cea129b66a
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77451848"
---
# <a name="manipulating-data"></a><span data-ttu-id="d416f-102">Manipulation de données</span><span class="sxs-lookup"><span data-stu-id="d416f-102">Manipulating Data</span></span>
<span data-ttu-id="d416f-103">Avant l'introduction des ensembles de résultats actifs multiples (Multiple Active Result Sets, MARS), les développeurs devaient utiliser soit des connexions multiples, soit des curseurs côté serveur pour résoudre certains scénarios.</span><span class="sxs-lookup"><span data-stu-id="d416f-103">Before the introduction of Multiple Active Result Sets (MARS), developers had to use either multiple connections or server-side cursors to solve certain scenarios.</span></span> <span data-ttu-id="d416f-104">En outre, quand plusieurs connexions étaient utilisées dans une situation transactionnelle, des connexions liées (avec **sp_getbindtoken** et **sp_bindsession**) étaient requises.</span><span class="sxs-lookup"><span data-stu-id="d416f-104">In addition, when multiple connections were used in a transactional situation, bound connections (with **sp_getbindtoken** and **sp_bindsession**) were required.</span></span> <span data-ttu-id="d416f-105">Les scénarios suivants montrent comment utiliser une connexion de type MARS au lieu de connexions multiples.</span><span class="sxs-lookup"><span data-stu-id="d416f-105">The following scenarios show how to use a MARS-enabled connection instead of multiple connections.</span></span>  
  
## <a name="using-multiple-commands-with-mars"></a><span data-ttu-id="d416f-106">Utilisation de commandes multiples avec MARS</span><span class="sxs-lookup"><span data-stu-id="d416f-106">Using Multiple Commands with MARS</span></span>  
 <span data-ttu-id="d416f-107">L'application console suivante montre comment utiliser deux objets <xref:System.Data.SqlClient.SqlDataReader> avec deux objets <xref:System.Data.SqlClient.SqlCommand> et un objet <xref:System.Data.SqlClient.SqlConnection> lorsque MARS est activé.</span><span class="sxs-lookup"><span data-stu-id="d416f-107">The following Console application demonstrates how to use two <xref:System.Data.SqlClient.SqlDataReader> objects with two <xref:System.Data.SqlClient.SqlCommand> objects and a single <xref:System.Data.SqlClient.SqlConnection> object with MARS enabled.</span></span>  
  
### <a name="example"></a><span data-ttu-id="d416f-108">Exemple</span><span class="sxs-lookup"><span data-stu-id="d416f-108">Example</span></span>  
 <span data-ttu-id="d416f-109">L’exemple ouvre une connexion unique à la base de données **AdventureWorks**.</span><span class="sxs-lookup"><span data-stu-id="d416f-109">The example opens a single connection to the **AdventureWorks** database.</span></span> <span data-ttu-id="d416f-110">En utilisant un objet <xref:System.Data.SqlClient.SqlCommand>, un <xref:System.Data.SqlClient.SqlDataReader> est créé.</span><span class="sxs-lookup"><span data-stu-id="d416f-110">Using a <xref:System.Data.SqlClient.SqlCommand> object, a <xref:System.Data.SqlClient.SqlDataReader> is created.</span></span> <span data-ttu-id="d416f-111">Comme le lecteur est utilisé, un second <xref:System.Data.SqlClient.SqlDataReader> est ouvert, en utilisant les données du premier <xref:System.Data.SqlClient.SqlDataReader> comme entrée pour la clause WHERE du second lecteur.</span><span class="sxs-lookup"><span data-stu-id="d416f-111">As the reader is used, a second <xref:System.Data.SqlClient.SqlDataReader> is opened, using data from the first <xref:System.Data.SqlClient.SqlDataReader> as input to the WHERE clause for the second reader.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d416f-112">L’exemple suivant utilise l’exemple de base de données **AdventureWorks** inclus dans SQL Server.</span><span class="sxs-lookup"><span data-stu-id="d416f-112">The following example uses the sample **AdventureWorks** database included with SQL Server.</span></span> <span data-ttu-id="d416f-113">La chaîne de connexion fournie dans l'exemple de code suppose que la base de données est installée et disponible sur l'ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="d416f-113">The connection string provided in the sample code assumes that the database is installed and available on the local computer.</span></span> <span data-ttu-id="d416f-114">Si nécessaire, modifiez la chaîne de connexion en fonction de votre environnement.</span><span class="sxs-lookup"><span data-stu-id="d416f-114">Modify the connection string as necessary for your environment.</span></span>  
  
```vb  
Option Strict On  
Option Explicit On  
  
Imports System  
Imports System.Data  
Imports System.Data.SqlClient  
Module Module1  
  Sub Main()  
    ' By default, MARS is disabled when connecting  
    ' to a MARS-enabled host.  
    ' It must be enabled in the connection string.  
    Dim connectionString As String = GetConnectionString()  
  
    Dim vendorID As Integer  
  
    Dim vendorCmd As SqlCommand  
    Dim productCmd As SqlCommand  
    Dim productReader As SqlDataReader  
  
    Dim vendorSQL As String = & _   
      "SELECT VendorId, Name FROM Purchasing.Vendor"  
    Dim productSQL As String = _  
        "SELECT Production.Product.Name FROM Production.Product " & _  
        "INNER JOIN Purchasing.ProductVendor " & _  
        "ON Production.Product.ProductID = " & _  
        "Purchasing.ProductVendor.ProductID " & _  
        "WHERE Purchasing.ProductVendor.VendorID = @VendorId"  
  
    Using awConnection As New SqlConnection(connectionString)  
      vendorCmd = New SqlCommand(vendorSQL, awConnection)  
      productCmd = New SqlCommand(productSQL, awConnection)  
      productCmd.Parameters.Add("@VendorId", SqlDbType.Int)  
  
      awConnection.Open()  
      Using vendorReader As SqlDataReader = vendorCmd.ExecuteReader()  
        While vendorReader.Read()  
          Console.WriteLine(vendorReader("Name"))  
  
          vendorID = CInt(vendorReader("VendorId"))  
  
          productCmd.Parameters("@VendorId").Value = vendorID  
  
          ' The following line of code requires  
          ' a MARS-enabled connection.  
          productReader = productCmd.ExecuteReader()  
          Using productReader  
            While productReader.Read()  
              Console.WriteLine("  " & CStr(productReader("Name")))  
            End While  
          End Using  
        End While  
      End Using  
    End Using  
  
    Console.WriteLine("Press any key to continue")  
    Console.ReadLine()  
  End Sub  
  
  Function GetConnectionString() As String  
    ' To avoid storing the connection string in your code,  
    ' you can retrieve it from a configuration file.  
    Return "Data Source=(local);Integrated Security=SSPI;" & _  
      "Initial Catalog=AdventureWorks; MultipleActiveResultSets=True"  
  End Function  
End Module  
```  
  
```csharp  
using System;  
using System.Data;  
using System.Data.SqlClient;  
  
class Class1  
{  
static void Main()  
{  
  // By default, MARS is disabled when connecting  
  // to a MARS-enabled host.  
  // It must be enabled in the connection string.  
  string connectionString = GetConnectionString();  
  
  int vendorID;  
  SqlDataReader productReader = null;  
  string vendorSQL =   
    "SELECT VendorId, Name FROM Purchasing.Vendor";  
  string productSQL =   
    "SELECT Production.Product.Name FROM Production.Product " +  
    "INNER JOIN Purchasing.ProductVendor " +  
    "ON Production.Product.ProductID = " +   
    "Purchasing.ProductVendor.ProductID " +  
    "WHERE Purchasing.ProductVendor.VendorID = @VendorId";  
  
  using (SqlConnection awConnection =   
    new SqlConnection(connectionString))  
  {  
    SqlCommand vendorCmd = new SqlCommand(vendorSQL, awConnection);  
    SqlCommand productCmd =   
      new SqlCommand(productSQL, awConnection);  
  
    productCmd.Parameters.Add("@VendorId", SqlDbType.Int);  
  
    awConnection.Open();  
    using (SqlDataReader vendorReader = vendorCmd.ExecuteReader())  
    {  
      while (vendorReader.Read())  
      {  
        Console.WriteLine(vendorReader["Name"]);  
  
        vendorID = (int)vendorReader["VendorId"];  
  
        productCmd.Parameters["@VendorId"].Value = vendorID;  
        // The following line of code requires  
        // a MARS-enabled connection.  
        productReader = productCmd.ExecuteReader();  
        using (productReader)  
        {  
          while (productReader.Read())  
          {  
            Console.WriteLine("  " +  
              productReader["Name"].ToString());  
          }  
        }  
      }  
  }  
      Console.WriteLine("Press any key to continue");  
      Console.ReadLine();  
    }  
  }  
  private static string GetConnectionString()  
  {  
    // To avoid storing the connection string in your code,  
    // you can retrieve it from a configuration file.  
    return "Data Source=(local);Integrated Security=SSPI;" +   
      "Initial Catalog=AdventureWorks;MultipleActiveResultSets=True";  
  }  
}  
```  
  
## <a name="reading-and-updating-data-with-mars"></a><span data-ttu-id="d416f-115">Lecture et mise à jour des données avec MARS</span><span class="sxs-lookup"><span data-stu-id="d416f-115">Reading and Updating Data with MARS</span></span>  
 <span data-ttu-id="d416f-116">MARS permet d'utiliser une connexion pour les opérations de lecture et les opérations en langage DML (Data Manipulation Language) avec plusieurs opérations en attente.</span><span class="sxs-lookup"><span data-stu-id="d416f-116">MARS allows a connection to be used for both read operations and data manipulation language (DML) operations with more than one pending operation.</span></span> <span data-ttu-id="d416f-117">Cette fonctionnalité élimine la nécessité pour une application de gérer les erreurs en relation avec une connexion occupée.</span><span class="sxs-lookup"><span data-stu-id="d416f-117">This feature eliminates the need for an application to deal with connection-busy errors.</span></span> <span data-ttu-id="d416f-118">En outre, MARS peut remplacer l’utilisation de curseurs côté serveur, qui consomment généralement davantage de ressources.</span><span class="sxs-lookup"><span data-stu-id="d416f-118">In addition, MARS can replace the use of server-side cursors, which generally consume more resources.</span></span> <span data-ttu-id="d416f-119">Pour finir, comme plusieurs opérations peuvent opérer sur une seule connexion, elles peuvent partager le même contexte de transaction, en éliminant la nécessité d’utiliser les procédures stockées **système sp_getbindtoken** et **sp_bindsession**.</span><span class="sxs-lookup"><span data-stu-id="d416f-119">Finally, because multiple operations can operate on a single connection, they can share the same transaction context, eliminating the need to use **sp_getbindtoken** and **sp_bindsession** system stored procedures.</span></span>  
  
### <a name="example"></a><span data-ttu-id="d416f-120">Exemple</span><span class="sxs-lookup"><span data-stu-id="d416f-120">Example</span></span>  
 <span data-ttu-id="d416f-121">L'application console suivante montre comment utiliser deux objets <xref:System.Data.SqlClient.SqlDataReader> avec trois objets <xref:System.Data.SqlClient.SqlCommand> et un objet <xref:System.Data.SqlClient.SqlConnection> lorsque MARS est activé.</span><span class="sxs-lookup"><span data-stu-id="d416f-121">The following Console application demonstrates how to use two <xref:System.Data.SqlClient.SqlDataReader> objects with three <xref:System.Data.SqlClient.SqlCommand> objects and a single <xref:System.Data.SqlClient.SqlConnection> object with MARS enabled.</span></span> <span data-ttu-id="d416f-122">Le premier objet de commande extrait une liste de fournisseurs dont le taux de crédit est 5.</span><span class="sxs-lookup"><span data-stu-id="d416f-122">The first command object retrieves a list of vendors whose credit rating is 5.</span></span> <span data-ttu-id="d416f-123">Le second objet de commande utilise l'ID du fournisseur fourni par un <xref:System.Data.SqlClient.SqlDataReader> pour charger le second <xref:System.Data.SqlClient.SqlDataReader> avec tous les produits du fournisseur en question.</span><span class="sxs-lookup"><span data-stu-id="d416f-123">The second command object uses the vendor ID provided from a <xref:System.Data.SqlClient.SqlDataReader> to load the second <xref:System.Data.SqlClient.SqlDataReader> with all of the products for the particular vendor.</span></span> <span data-ttu-id="d416f-124">Chaque enregistrement de produit est consulté par le second <xref:System.Data.SqlClient.SqlDataReader>.</span><span class="sxs-lookup"><span data-stu-id="d416f-124">Each product record is visited by the second <xref:System.Data.SqlClient.SqlDataReader>.</span></span> <span data-ttu-id="d416f-125">Un calcul est effectué afin de déterminer ce que doit être le nouveau **OnOrderQty**.</span><span class="sxs-lookup"><span data-stu-id="d416f-125">A calculation is performed to determine what the new **OnOrderQty** should be.</span></span> <span data-ttu-id="d416f-126">Le troisième objet de commande est ensuite utilisé pour mettre à jour la table **ProductVendor** avec la nouvelle valeur.</span><span class="sxs-lookup"><span data-stu-id="d416f-126">The third command object is then used to update the **ProductVendor** table with the new value.</span></span> <span data-ttu-id="d416f-127">Tout ce processus se déroule dans le cadre d'une seule transaction, qui est annulée à la fin.</span><span class="sxs-lookup"><span data-stu-id="d416f-127">This entire process takes place within a single transaction, which is rolled back at the end.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d416f-128">L’exemple suivant utilise l’exemple de base de données **AdventureWorks** inclus dans SQL Server.</span><span class="sxs-lookup"><span data-stu-id="d416f-128">The following example uses the sample **AdventureWorks** database included with SQL Server.</span></span> <span data-ttu-id="d416f-129">La chaîne de connexion fournie dans l'exemple de code suppose que la base de données est installée et disponible sur l'ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="d416f-129">The connection string provided in the sample code assumes that the database is installed and available on the local computer.</span></span> <span data-ttu-id="d416f-130">Si nécessaire, modifiez la chaîne de connexion en fonction de votre environnement.</span><span class="sxs-lookup"><span data-stu-id="d416f-130">Modify the connection string as necessary for your environment.</span></span>  
  
```vb  
Option Strict On  
Option Explicit On  
  
Imports System  
Imports System.Data  
Imports System.Data.SqlClient  
  
Module Module1  
  
  Sub Main()  
    ' By default, MARS is disabled when connecting  
    ' to a MARS-enabled host.  
    ' It must be enabled in the connection string.  
    Dim connectionString As String = GetConnectionString()  
  
    Dim updateTx As SqlTransaction  
    Dim vendorCmd As SqlCommand  
    Dim prodVendCmd As SqlCommand  
    Dim updateCmd As SqlCommand  
  
    Dim prodVendReader As SqlDataReader  
  
    Dim vendorID As Integer  
    Dim productID As Integer  
    Dim minOrderQty As Integer  
    Dim maxOrderQty As Integer  
    Dim onOrderQty As Integer  
    Dim recordsUpdated As Integer  
    Dim totalRecordsUpdated As Integer  
  
    Dim vendorSQL As String = _  
        "SELECT VendorID, Name FROM Purchasing.Vendor " & _  
        "WHERE CreditRating = 5"  
    Dim prodVendSQL As String = _  
        "SELECT ProductID, MaxOrderQty, MinOrderQty, OnOrderQty " & _  
        "FROM Purchasing.ProductVendor " & _  
        "WHERE VendorID = @VendorID"  
    Dim updateSQL As String = _  
        "UPDATE Purchasing.ProductVendor " & _   
        "SET OnOrderQty = @OrderQty " & _  
        "WHERE ProductID = @ProductID AND VendorID = @VendorID"  
  
    Using awConnection As New SqlConnection(connectionString)  
      awConnection.Open()  
      updateTx = awConnection.BeginTransaction()  
  
      vendorCmd = New SqlCommand(vendorSQL, awConnection)  
      vendorCmd.Transaction = updateTx  
  
      prodVendCmd = New SqlCommand(prodVendSQL, awConnection)  
      prodVendCmd.Transaction = updateTx  
      prodVendCmd.Parameters.Add("@VendorId", SqlDbType.Int)  
  
      updateCmd = New SqlCommand(updateSQL, awConnection)  
      updateCmd.Transaction = updateTx  
      updateCmd.Parameters.Add("@OrderQty", SqlDbType.Int)  
      updateCmd.Parameters.Add("@ProductID", SqlDbType.Int)  
      updateCmd.Parameters.Add("@VendorID", SqlDbType.Int)  
  
      Using vendorReader As SqlDataReader = vendorCmd.ExecuteReader()  
        While vendorReader.Read()  
          Console.WriteLine(vendorReader("Name"))  
  
          vendorID = CInt(vendorReader("VendorID"))  
          prodVendCmd.Parameters("@VendorID").Value = vendorID  
          prodVendReader = prodVendCmd.ExecuteReader()  
  
          Using prodVendReader  
            While (prodVendReader.Read)  
              productID = CInt(prodVendReader("ProductID"))  
  
              If IsDBNull(prodVendReader("OnOrderQty")) Then  
                minOrderQty = CInt(prodVendReader("MinOrderQty"))  
                onOrderQty = minOrderQty  
              Else  
                maxOrderQty = CInt(prodVendReader("MaxOrderQty"))  
                onOrderQty = CInt(maxOrderQty / 2)  
              End If  
  
              updateCmd.Parameters("@OrderQty").Value = onOrderQty  
              updateCmd.Parameters("@ProductID").Value = productID  
              updateCmd.Parameters("@VendorID").Value = vendorID  
  
              recordsUpdated = updateCmd.ExecuteNonQuery()  
              totalRecordsUpdated += recordsUpdated  
            End While  
          End Using  
        End While  
      End Using  
  
      Console.WriteLine("Total Records Updated: " & _   
        CStr(totalRecordsUpdated))  
      updateTx.Rollback()  
      Console.WriteLine("Transaction Rolled Back")  
    End Using  
  
    Console.WriteLine("Press any key to continue")  
    Console.ReadLine()  
  
  End Sub  
  
  Function GetConnectionString() As String  
    ' To avoid storing the connection string in your code,  
    ' you can retrieve it from a configuration file.  
    Return "Data Source=(local);Integrated Security=SSPI;" & _  
      "Initial Catalog=AdventureWorks;MultipleActiveResultSets=True"  
  End Function  
End Module  
```  
  
```csharp  
using System;  
using System.Collections.Generic;  
using System.Text;  
using System.Data;  
using System.Data.SqlClient;  
  
class Program  
{  
static void Main()  
{  
  // By default, MARS is disabled when connecting  
  // to a MARS-enabled host.  
  // It must be enabled in the connection string.  
  string connectionString = GetConnectionString();  
  
  SqlTransaction updateTx = null;  
  SqlCommand vendorCmd = null;  
  SqlCommand prodVendCmd = null;  
  SqlCommand updateCmd = null;  
  
  SqlDataReader prodVendReader = null;  
  
  int vendorID = 0;  
  int productID = 0;  
  int minOrderQty = 0;  
  int maxOrderQty = 0;  
  int onOrderQty = 0;  
  int recordsUpdated = 0;  
  int totalRecordsUpdated = 0;  
  
  string vendorSQL =  
      "SELECT VendorID, Name FROM Purchasing.Vendor " +   
      "WHERE CreditRating = 5";  
  string prodVendSQL =  
      "SELECT ProductID, MaxOrderQty, MinOrderQty, OnOrderQty " +  
      "FROM Purchasing.ProductVendor " +   
      "WHERE VendorID = @VendorID";  
  string updateSQL =  
      "UPDATE Purchasing.ProductVendor " +   
      "SET OnOrderQty = @OrderQty " +  
      "WHERE ProductID = @ProductID AND VendorID = @VendorID";  
  
  using (SqlConnection awConnection =   
    new SqlConnection(connectionString))  
  {  
    awConnection.Open();  
    updateTx = awConnection.BeginTransaction();  
  
    vendorCmd = new SqlCommand(vendorSQL, awConnection);  
    vendorCmd.Transaction = updateTx;  
  
    prodVendCmd = new SqlCommand(prodVendSQL, awConnection);  
    prodVendCmd.Transaction = updateTx;  
    prodVendCmd.Parameters.Add("@VendorId", SqlDbType.Int);  
  
    updateCmd = new SqlCommand(updateSQL, awConnection);  
    updateCmd.Transaction = updateTx;  
    updateCmd.Parameters.Add("@OrderQty", SqlDbType.Int);  
    updateCmd.Parameters.Add("@ProductID", SqlDbType.Int);  
    updateCmd.Parameters.Add("@VendorID", SqlDbType.Int);  
  
    using (SqlDataReader vendorReader = vendorCmd.ExecuteReader())  
    {  
      while (vendorReader.Read())  
      {  
        Console.WriteLine(vendorReader["Name"]);  
  
        vendorID = (int) vendorReader["VendorID"];  
        prodVendCmd.Parameters["@VendorID"].Value = vendorID;  
        prodVendReader = prodVendCmd.ExecuteReader();  
  
        using (prodVendReader)  
        {  
          while (prodVendReader.Read())  
          {  
            productID = (int) prodVendReader["ProductID"];  
  
            if (prodVendReader["OnOrderQty"] == DBNull.Value)  
            {  
              minOrderQty = (int) prodVendReader["MinOrderQty"];  
              onOrderQty = minOrderQty;  
            }  
            else  
            {  
              maxOrderQty = (int) prodVendReader["MaxOrderQty"];  
              onOrderQty = (int)(maxOrderQty / 2);  
            }  
  
            updateCmd.Parameters["@OrderQty"].Value = onOrderQty;  
            updateCmd.Parameters["@ProductID"].Value = productID;  
            updateCmd.Parameters["@VendorID"].Value = vendorID;  
  
            recordsUpdated = updateCmd.ExecuteNonQuery();  
            totalRecordsUpdated += recordsUpdated;  
          }  
        }  
      }  
    }  
    Console.WriteLine("Total Records Updated: " +   
      totalRecordsUpdated.ToString());  
    updateTx.Rollback();  
    Console.WriteLine("Transaction Rolled Back");  
  }  
  
  Console.WriteLine("Press any key to continue");  
  Console.ReadLine();  
}  
private static string GetConnectionString()  
{  
  // To avoid storing the connection string in your code,  
  // you can retrieve it from a configuration file.  
  return "Data Source=(local);Integrated Security=SSPI;" +   
    "Initial Catalog=AdventureWorks;" +   
    "MultipleActiveResultSets=True";  
  }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="d416f-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d416f-131">See also</span></span>

- [<span data-ttu-id="d416f-132">MARS (Multiple Active Result Sets)</span><span class="sxs-lookup"><span data-stu-id="d416f-132">Multiple Active Result Sets (MARS)</span></span>](multiple-active-result-sets-mars.md)
- [<span data-ttu-id="d416f-133">Vue d’ensemble d’ADO.NET</span><span class="sxs-lookup"><span data-stu-id="d416f-133">ADO.NET Overview</span></span>](../ado-net-overview.md)
