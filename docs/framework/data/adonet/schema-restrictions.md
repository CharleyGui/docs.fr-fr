---
title: Restrictions de schéma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 73d2980e-e73c-4987-913a-8ddc93d09144
ms.openlocfilehash: 1a2c32d133799ee5338c18d0f51bced49cb3dc4b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69963173"
---
# <a name="schema-restrictions"></a><span data-ttu-id="72b78-102">Restrictions de schéma</span><span class="sxs-lookup"><span data-stu-id="72b78-102">Schema Restrictions</span></span>
<span data-ttu-id="72b78-103">Le deuxième paramètre facultatif de la méthode **GetSchema** correspond aux restrictions utilisées pour limiter la quantité d’informations de schéma retournées, et il est passé à la méthode **GetSchema** sous la forme d’un tableau de chaînes.</span><span class="sxs-lookup"><span data-stu-id="72b78-103">The second optional parameter of the **GetSchema** method is the restrictions that are used to limit the amount of schema information returned, and it is passed to the **GetSchema** method as an array of strings.</span></span> <span data-ttu-id="72b78-104">La position dans le tableau détermine les valeurs que vous pouvez passer et équivaut au numéro de restriction.</span><span class="sxs-lookup"><span data-stu-id="72b78-104">The position in the array determines the values that you can pass, and this is equivalent to the restriction number.</span></span>  
  
 <span data-ttu-id="72b78-105">Par exemple, le tableau suivant décrit les restrictions prises en charge par la collection de schémas « Tables » utilisant le fournisseur de données .NET Framework pour SQL Server.</span><span class="sxs-lookup"><span data-stu-id="72b78-105">For example, the following table describes the restrictions supported by the "Tables" schema collection using the .NET Framework Data Provider for SQL Server.</span></span> <span data-ttu-id="72b78-106">Des restrictions supplémentaires pour les collections de schémas SQL Server figurent à la fin de cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="72b78-106">Additional restrictions for SQL Server schema collections are listed at the end of this topic.</span></span>  
  
|<span data-ttu-id="72b78-107">Nom de restriction</span><span class="sxs-lookup"><span data-stu-id="72b78-107">Restriction Name</span></span>|<span data-ttu-id="72b78-108">nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="72b78-108">Parameter Name</span></span>|<span data-ttu-id="72b78-109">Valeur par défaut de la restriction</span><span class="sxs-lookup"><span data-stu-id="72b78-109">Restriction Default</span></span>|<span data-ttu-id="72b78-110">Numéro de restriction</span><span class="sxs-lookup"><span data-stu-id="72b78-110">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="72b78-111">Catalogue</span><span class="sxs-lookup"><span data-stu-id="72b78-111">Catalog</span></span>|@Catalog|<span data-ttu-id="72b78-112">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="72b78-112">TABLE_CATALOG</span></span>|<span data-ttu-id="72b78-113">1</span><span class="sxs-lookup"><span data-stu-id="72b78-113">1</span></span>|  
|<span data-ttu-id="72b78-114">Propriétaire</span><span class="sxs-lookup"><span data-stu-id="72b78-114">Owner</span></span>|@Owner|<span data-ttu-id="72b78-115">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="72b78-115">TABLE_SCHEMA</span></span>|<span data-ttu-id="72b78-116">2</span><span class="sxs-lookup"><span data-stu-id="72b78-116">2</span></span>|  
|<span data-ttu-id="72b78-117">Table</span><span class="sxs-lookup"><span data-stu-id="72b78-117">Table</span></span>|@Name|<span data-ttu-id="72b78-118">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="72b78-118">TABLE_NAME</span></span>|<span data-ttu-id="72b78-119">3</span><span class="sxs-lookup"><span data-stu-id="72b78-119">3</span></span>|  
|<span data-ttu-id="72b78-120">TableType</span><span class="sxs-lookup"><span data-stu-id="72b78-120">TableType</span></span>|@TableType|<span data-ttu-id="72b78-121">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="72b78-121">TABLE_TYPE</span></span>|<span data-ttu-id="72b78-122">4</span><span class="sxs-lookup"><span data-stu-id="72b78-122">4</span></span>|  
  
## <a name="specifying-restriction-values"></a><span data-ttu-id="72b78-123">Spécification des valeurs de restriction</span><span class="sxs-lookup"><span data-stu-id="72b78-123">Specifying Restriction Values</span></span>  
 <span data-ttu-id="72b78-124">Pour utiliser l’une des restrictions de la collection de schémas « Tables », créez simplement un tableau de chaînes contenant quatre éléments, puis placez une valeur dans l’élément correspondant au numéro de restriction.</span><span class="sxs-lookup"><span data-stu-id="72b78-124">To use one of the restrictions of the "Tables" schema collection, simply create an array of strings with four elements, then place a value in the element that matches the restriction number.</span></span> <span data-ttu-id="72b78-125">Par exemple, pour restreindre les tables retournées par la méthode **GetSchema** aux seules tables du schéma «Sales», définissez le deuxième élément du tableau sur «sales» avant de le passer à la méthode **GetSchema** .</span><span class="sxs-lookup"><span data-stu-id="72b78-125">For example, to restrict the tables returned by the **GetSchema** method to only those tables in the "Sales" schema, set the second element of the array to "Sales" before passing it to the **GetSchema** method.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="72b78-126">Les collections de restrictions pour `SqlClient` et `OracleClient` comportent une colonne `ParameterName` supplémentaire.</span><span class="sxs-lookup"><span data-stu-id="72b78-126">The restrictions collections for `SqlClient` and `OracleClient` have an additional `ParameterName` column.</span></span> <span data-ttu-id="72b78-127">La colonne par défaut de la restriction est encore là pour la compatibilité ascendante, mais est désormais ignorée.</span><span class="sxs-lookup"><span data-stu-id="72b78-127">The restriction default column is still there for backwards compatibility, but is currently ignored.</span></span> <span data-ttu-id="72b78-128">Il convient d'utiliser des requêtes paramétrées plutôt qu'un remplacement de chaîne afin de minimiser le risque d'attaque par injection SQL lors de la spécification de valeurs de restriction.</span><span class="sxs-lookup"><span data-stu-id="72b78-128">Parameterized queries rather than string replacement should be used to minimize the risk of an SQL injection attack when specifying restriction values.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="72b78-129">Le nombre d'éléments du tableau doit être inférieur ou égal au nombre de restrictions prises en charge pour la collection de schémas spécifiée, sans quoi une exception <xref:System.ArgumentException> est levée.</span><span class="sxs-lookup"><span data-stu-id="72b78-129">The number of elements in the array must be less than or equal to the number of restrictions supported for the specified schema collection else an <xref:System.ArgumentException> will be thrown.</span></span> <span data-ttu-id="72b78-130">Il peut y avoir moins de restrictions que le nombre maximal de restrictions.</span><span class="sxs-lookup"><span data-stu-id="72b78-130">There can be fewer than the maximum number of restrictions.</span></span> <span data-ttu-id="72b78-131">Les restrictions manquantes sont supposées avoir la valeur null (aucune restriction).</span><span class="sxs-lookup"><span data-stu-id="72b78-131">The missing restrictions are assumed to be null (unrestricted).</span></span>  
  
 <span data-ttu-id="72b78-132">Vous pouvez interroger un fournisseur managé .NET Framework pour déterminer la liste des restrictions prises en charge en appelant la méthode **GetSchema** avec le nom de la collection de schémas de restrictions, qui est «restrictions».</span><span class="sxs-lookup"><span data-stu-id="72b78-132">You can query a .NET Framework managed provider to determine the list of supported restrictions by calling the **GetSchema** method with the name of the restrictions schema collection, which is "Restrictions".</span></span> <span data-ttu-id="72b78-133">Cette opération retourne un <xref:System.Data.DataTable> contenant une liste des noms de collections, des noms de restriction, des valeurs de restriction par défaut et des numéros de restriction.</span><span class="sxs-lookup"><span data-stu-id="72b78-133">This will return a <xref:System.Data.DataTable> with a list of the collection names, the restriction names, the default restriction values, and the restriction numbers.</span></span>  
  
### <a name="example"></a><span data-ttu-id="72b78-134">Exemples</span><span class="sxs-lookup"><span data-stu-id="72b78-134">Example</span></span>  
 <span data-ttu-id="72b78-135">Les exemples suivants montrent comment utiliser la <xref:System.Data.SqlClient.SqlConnection.GetSchema%2A> méthode de la .NET Framework fournisseur de données pour la classe SQL Server <xref:System.Data.SqlClient.SqlConnection> pour récupérer des informations de schéma sur toutes les tables contenues dans l’exemple de base de données **AdventureWorks** , et pour limiter les informations retournées aux seules tables du schéma «Sales»:</span><span class="sxs-lookup"><span data-stu-id="72b78-135">The following examples demonstrate how to use the <xref:System.Data.SqlClient.SqlConnection.GetSchema%2A> method of the .NET Framework Data Provider for the SQL Server <xref:System.Data.SqlClient.SqlConnection> class to retrieve schema information about all of the tables contained in the **AdventureWorks** sample database, and to restrict the information returned to only those tables in the "Sales" schema:</span></span>  
  
```vb  
Imports System.Data.SqlClient  
  
Module Module1  
Sub Main()  
  Dim connectionString As String = _  
    "Data Source=(local);Database=AdventureWorks;" & _  
       "Integrated Security=true;";  
  
  Dim restrictions(3) As String  
  Using connection As New SqlConnection(connectionString)  
    connection.Open()  
  
    'Specify the restrictions.  
    restrictions(1) = "Sales"  
    Dim table As DataTable = connection.GetSchema("Tables", _  
       restrictions)  
  
    ' Display the contents of the table.  
      For Each row As DataRow In table.Rows  
         For Each col As DataColumn In table.Columns  
            Console.WriteLine("{0} = {1}", col.ColumnName, row(col))  
         Next  
         Console.WriteLine("============================")  
      Next  
    Console.WriteLine("Press any key to continue.")  
    Console.ReadKey()  
  End Using  
End Sub  
End Module  
```  
  
```csharp  
using System;  
using System.Data;  
using System.Data.SqlClient;  
  
class Program  
{  
  static void Main()  
  {  
    string connectionString =   
       "Data Source=(local);Database=AdventureWorks;" +  
       "Integrated Security=true;";  
    using (SqlConnection connection =  
       new SqlConnection(connectionString))  
    {  
        connection.Open();  
  
        // Specify the restrictions.  
        string[] restrictions = new string[4];  
        restrictions[1] = "Sales";  
        System.Data.DataTable table = connection.GetSchema(  
          "Tables", restrictions);  
  
        // Display the contents of the table.  
        foreach (System.Data.DataRow row in table.Rows)  
        {  
            foreach (System.Data.DataColumn col in table.Columns)  
            {  
                Console.WriteLine("{0} = {1}",   
                  col.ColumnName, row[col]);  
            }  
            Console.WriteLine("============================");  
        }  
        Console.WriteLine("Press any key to continue.");  
        Console.ReadKey();  
    }  
  }  
  
  private static string GetConnectionString()  
  {  
     // To avoid storing the connection string in your code,  
     // you can retrieve it from a configuration file.  
     return "Data Source=(local);Database=AdventureWorks;" +  
        "Integrated Security=true;";  
  }  
  
  private static void DisplayData(System.Data.DataTable table)  
  {  
     foreach (System.Data.DataRow row in table.Rows)  
     {  
        foreach (System.Data.DataColumn col in table.Columns)  
        {  
           Console.WriteLine("{0} = {1}", col.ColumnName, row[col]);  
        }  
     Console.WriteLine("============================");  
     }  
  }  
}  
```  
  
## <a name="sql-server-schema-restrictions"></a><span data-ttu-id="72b78-136">Restrictions de schéma SQL Server</span><span class="sxs-lookup"><span data-stu-id="72b78-136">SQL Server Schema Restrictions</span></span>  
 <span data-ttu-id="72b78-137">Les tableaux suivants énumèrent les restrictions pour les collections de schémas SQL Server.</span><span class="sxs-lookup"><span data-stu-id="72b78-137">The following tables list the restrictions for SQL Server schema collections.</span></span>  
  
### <a name="users"></a><span data-ttu-id="72b78-138">Utilisateurs</span><span class="sxs-lookup"><span data-stu-id="72b78-138">Users</span></span>  
  
|<span data-ttu-id="72b78-139">Nom de restriction</span><span class="sxs-lookup"><span data-stu-id="72b78-139">Restriction Name</span></span>|<span data-ttu-id="72b78-140">nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="72b78-140">Parameter Name</span></span>|<span data-ttu-id="72b78-141">Valeur par défaut de la restriction</span><span class="sxs-lookup"><span data-stu-id="72b78-141">Restriction Default</span></span>|<span data-ttu-id="72b78-142">Numéro de restriction</span><span class="sxs-lookup"><span data-stu-id="72b78-142">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="72b78-143">User_Name</span><span class="sxs-lookup"><span data-stu-id="72b78-143">User_Name</span></span>|@Name|<span data-ttu-id="72b78-144">name</span><span class="sxs-lookup"><span data-stu-id="72b78-144">name</span></span>|<span data-ttu-id="72b78-145">1</span><span class="sxs-lookup"><span data-stu-id="72b78-145">1</span></span>|  
  
### <a name="databases"></a><span data-ttu-id="72b78-146">Bases de données</span><span class="sxs-lookup"><span data-stu-id="72b78-146">Databases</span></span>  
  
|<span data-ttu-id="72b78-147">Nom de restriction</span><span class="sxs-lookup"><span data-stu-id="72b78-147">Restriction Name</span></span>|<span data-ttu-id="72b78-148">nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="72b78-148">Parameter Name</span></span>|<span data-ttu-id="72b78-149">Valeur par défaut de la restriction</span><span class="sxs-lookup"><span data-stu-id="72b78-149">Restriction Default</span></span>|<span data-ttu-id="72b78-150">Numéro de restriction</span><span class="sxs-lookup"><span data-stu-id="72b78-150">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="72b78-151">Nom</span><span class="sxs-lookup"><span data-stu-id="72b78-151">Name</span></span>|@Name|<span data-ttu-id="72b78-152">Nom</span><span class="sxs-lookup"><span data-stu-id="72b78-152">Name</span></span>|<span data-ttu-id="72b78-153">1</span><span class="sxs-lookup"><span data-stu-id="72b78-153">1</span></span>|  
  
### <a name="tables"></a><span data-ttu-id="72b78-154">Tables</span><span class="sxs-lookup"><span data-stu-id="72b78-154">Tables</span></span>  
  
|<span data-ttu-id="72b78-155">Nom de restriction</span><span class="sxs-lookup"><span data-stu-id="72b78-155">Restriction Name</span></span>|<span data-ttu-id="72b78-156">nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="72b78-156">Parameter Name</span></span>|<span data-ttu-id="72b78-157">Valeur par défaut de la restriction</span><span class="sxs-lookup"><span data-stu-id="72b78-157">Restriction Default</span></span>|<span data-ttu-id="72b78-158">Numéro de restriction</span><span class="sxs-lookup"><span data-stu-id="72b78-158">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="72b78-159">Catalogue</span><span class="sxs-lookup"><span data-stu-id="72b78-159">Catalog</span></span>|@Catalog|<span data-ttu-id="72b78-160">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="72b78-160">TABLE_CATALOG</span></span>|<span data-ttu-id="72b78-161">1</span><span class="sxs-lookup"><span data-stu-id="72b78-161">1</span></span>|  
|<span data-ttu-id="72b78-162">Propriétaire</span><span class="sxs-lookup"><span data-stu-id="72b78-162">Owner</span></span>|@Owner|<span data-ttu-id="72b78-163">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="72b78-163">TABLE_SCHEMA</span></span>|<span data-ttu-id="72b78-164">2</span><span class="sxs-lookup"><span data-stu-id="72b78-164">2</span></span>|  
|<span data-ttu-id="72b78-165">Table</span><span class="sxs-lookup"><span data-stu-id="72b78-165">Table</span></span>|@Name|<span data-ttu-id="72b78-166">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="72b78-166">TABLE_NAME</span></span>|<span data-ttu-id="72b78-167">3</span><span class="sxs-lookup"><span data-stu-id="72b78-167">3</span></span>|  
|<span data-ttu-id="72b78-168">TableType</span><span class="sxs-lookup"><span data-stu-id="72b78-168">TableType</span></span>|@TableType|<span data-ttu-id="72b78-169">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="72b78-169">TABLE_TYPE</span></span>|<span data-ttu-id="72b78-170">4</span><span class="sxs-lookup"><span data-stu-id="72b78-170">4</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="72b78-171">Colonnes</span><span class="sxs-lookup"><span data-stu-id="72b78-171">Columns</span></span>  
  
|<span data-ttu-id="72b78-172">Nom de restriction</span><span class="sxs-lookup"><span data-stu-id="72b78-172">Restriction Name</span></span>|<span data-ttu-id="72b78-173">nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="72b78-173">Parameter Name</span></span>|<span data-ttu-id="72b78-174">Valeur par défaut de la restriction</span><span class="sxs-lookup"><span data-stu-id="72b78-174">Restriction Default</span></span>|<span data-ttu-id="72b78-175">Numéro de restriction</span><span class="sxs-lookup"><span data-stu-id="72b78-175">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="72b78-176">Catalogue</span><span class="sxs-lookup"><span data-stu-id="72b78-176">Catalog</span></span>|@Catalog|<span data-ttu-id="72b78-177">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="72b78-177">TABLE_CATALOG</span></span>|<span data-ttu-id="72b78-178">1</span><span class="sxs-lookup"><span data-stu-id="72b78-178">1</span></span>|  
|<span data-ttu-id="72b78-179">Propriétaire</span><span class="sxs-lookup"><span data-stu-id="72b78-179">Owner</span></span>|@Owner|<span data-ttu-id="72b78-180">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="72b78-180">TABLE_SCHEMA</span></span>|<span data-ttu-id="72b78-181">2</span><span class="sxs-lookup"><span data-stu-id="72b78-181">2</span></span>|  
|<span data-ttu-id="72b78-182">Table</span><span class="sxs-lookup"><span data-stu-id="72b78-182">Table</span></span>|@Table|<span data-ttu-id="72b78-183">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="72b78-183">TABLE_NAME</span></span>|<span data-ttu-id="72b78-184">3</span><span class="sxs-lookup"><span data-stu-id="72b78-184">3</span></span>|  
|<span data-ttu-id="72b78-185">Colonne</span><span class="sxs-lookup"><span data-stu-id="72b78-185">Column</span></span>|@Column|<span data-ttu-id="72b78-186">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="72b78-186">COLUMN_NAME</span></span>|<span data-ttu-id="72b78-187">4</span><span class="sxs-lookup"><span data-stu-id="72b78-187">4</span></span>|  
  
### <a name="structuredtypemembers"></a><span data-ttu-id="72b78-188">StructuredTypeMembers</span><span class="sxs-lookup"><span data-stu-id="72b78-188">StructuredTypeMembers</span></span>  
  
|<span data-ttu-id="72b78-189">Nom de restriction</span><span class="sxs-lookup"><span data-stu-id="72b78-189">Restriction Name</span></span>|<span data-ttu-id="72b78-190">nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="72b78-190">Parameter Name</span></span>|<span data-ttu-id="72b78-191">Valeur par défaut de la restriction</span><span class="sxs-lookup"><span data-stu-id="72b78-191">Restriction Default</span></span>|<span data-ttu-id="72b78-192">Numéro de restriction</span><span class="sxs-lookup"><span data-stu-id="72b78-192">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="72b78-193">Catalogue</span><span class="sxs-lookup"><span data-stu-id="72b78-193">Catalog</span></span>|@Catalog|<span data-ttu-id="72b78-194">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="72b78-194">TABLE_CATALOG</span></span>|<span data-ttu-id="72b78-195">1</span><span class="sxs-lookup"><span data-stu-id="72b78-195">1</span></span>|  
|<span data-ttu-id="72b78-196">Propriétaire</span><span class="sxs-lookup"><span data-stu-id="72b78-196">Owner</span></span>|@Owner|<span data-ttu-id="72b78-197">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="72b78-197">TABLE_SCHEMA</span></span>|<span data-ttu-id="72b78-198">2</span><span class="sxs-lookup"><span data-stu-id="72b78-198">2</span></span>|  
|<span data-ttu-id="72b78-199">Table</span><span class="sxs-lookup"><span data-stu-id="72b78-199">Table</span></span>|@Table|<span data-ttu-id="72b78-200">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="72b78-200">TABLE_NAME</span></span>|<span data-ttu-id="72b78-201">3</span><span class="sxs-lookup"><span data-stu-id="72b78-201">3</span></span>|  
|<span data-ttu-id="72b78-202">Colonne</span><span class="sxs-lookup"><span data-stu-id="72b78-202">Column</span></span>|@Column|<span data-ttu-id="72b78-203">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="72b78-203">COLUMN_NAME</span></span>|<span data-ttu-id="72b78-204">4</span><span class="sxs-lookup"><span data-stu-id="72b78-204">4</span></span>|  
  
### <a name="views"></a><span data-ttu-id="72b78-205">Affichages</span><span class="sxs-lookup"><span data-stu-id="72b78-205">Views</span></span>  
  
|<span data-ttu-id="72b78-206">Nom de restriction</span><span class="sxs-lookup"><span data-stu-id="72b78-206">Restriction Name</span></span>|<span data-ttu-id="72b78-207">nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="72b78-207">Parameter Name</span></span>|<span data-ttu-id="72b78-208">Valeur par défaut de la restriction</span><span class="sxs-lookup"><span data-stu-id="72b78-208">Restriction Default</span></span>|<span data-ttu-id="72b78-209">Numéro de restriction</span><span class="sxs-lookup"><span data-stu-id="72b78-209">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="72b78-210">Catalogue</span><span class="sxs-lookup"><span data-stu-id="72b78-210">Catalog</span></span>|@Catalog|<span data-ttu-id="72b78-211">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="72b78-211">TABLE_CATALOG</span></span>|<span data-ttu-id="72b78-212">1</span><span class="sxs-lookup"><span data-stu-id="72b78-212">1</span></span>|  
|<span data-ttu-id="72b78-213">Propriétaire</span><span class="sxs-lookup"><span data-stu-id="72b78-213">Owner</span></span>|@Owner|<span data-ttu-id="72b78-214">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="72b78-214">TABLE_SCHEMA</span></span>|<span data-ttu-id="72b78-215">2</span><span class="sxs-lookup"><span data-stu-id="72b78-215">2</span></span>|  
|<span data-ttu-id="72b78-216">Table</span><span class="sxs-lookup"><span data-stu-id="72b78-216">Table</span></span>|@Table|<span data-ttu-id="72b78-217">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="72b78-217">TABLE_NAME</span></span>|<span data-ttu-id="72b78-218">3</span><span class="sxs-lookup"><span data-stu-id="72b78-218">3</span></span>|  
  
### <a name="viewcolumns"></a><span data-ttu-id="72b78-219">ViewColumns</span><span class="sxs-lookup"><span data-stu-id="72b78-219">ViewColumns</span></span>  
  
|<span data-ttu-id="72b78-220">Nom de restriction</span><span class="sxs-lookup"><span data-stu-id="72b78-220">Restriction Name</span></span>|<span data-ttu-id="72b78-221">nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="72b78-221">Parameter Name</span></span>|<span data-ttu-id="72b78-222">Valeur par défaut de la restriction</span><span class="sxs-lookup"><span data-stu-id="72b78-222">Restriction Default</span></span>|<span data-ttu-id="72b78-223">Numéro de restriction</span><span class="sxs-lookup"><span data-stu-id="72b78-223">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="72b78-224">Catalogue</span><span class="sxs-lookup"><span data-stu-id="72b78-224">Catalog</span></span>|@Catalog|<span data-ttu-id="72b78-225">VIEW_CATALOG</span><span class="sxs-lookup"><span data-stu-id="72b78-225">VIEW_CATALOG</span></span>|<span data-ttu-id="72b78-226">1</span><span class="sxs-lookup"><span data-stu-id="72b78-226">1</span></span>|  
|<span data-ttu-id="72b78-227">Propriétaire</span><span class="sxs-lookup"><span data-stu-id="72b78-227">Owner</span></span>|@Owner|<span data-ttu-id="72b78-228">VIEW_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="72b78-228">VIEW_SCHEMA</span></span>|<span data-ttu-id="72b78-229">2</span><span class="sxs-lookup"><span data-stu-id="72b78-229">2</span></span>|  
|<span data-ttu-id="72b78-230">Table</span><span class="sxs-lookup"><span data-stu-id="72b78-230">Table</span></span>|@Table|<span data-ttu-id="72b78-231">VIEW_NAME</span><span class="sxs-lookup"><span data-stu-id="72b78-231">VIEW_NAME</span></span>|<span data-ttu-id="72b78-232">3</span><span class="sxs-lookup"><span data-stu-id="72b78-232">3</span></span>|  
|<span data-ttu-id="72b78-233">Colonne</span><span class="sxs-lookup"><span data-stu-id="72b78-233">Column</span></span>|@Column|<span data-ttu-id="72b78-234">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="72b78-234">COLUMN_NAME</span></span>|<span data-ttu-id="72b78-235">4</span><span class="sxs-lookup"><span data-stu-id="72b78-235">4</span></span>|  
  
### <a name="procedureparameters"></a><span data-ttu-id="72b78-236">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="72b78-236">ProcedureParameters</span></span>  
  
|<span data-ttu-id="72b78-237">Nom de restriction</span><span class="sxs-lookup"><span data-stu-id="72b78-237">Restriction Name</span></span>|<span data-ttu-id="72b78-238">nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="72b78-238">Parameter Name</span></span>|<span data-ttu-id="72b78-239">Valeur par défaut de la restriction</span><span class="sxs-lookup"><span data-stu-id="72b78-239">Restriction Default</span></span>|<span data-ttu-id="72b78-240">Numéro de restriction</span><span class="sxs-lookup"><span data-stu-id="72b78-240">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="72b78-241">Catalogue</span><span class="sxs-lookup"><span data-stu-id="72b78-241">Catalog</span></span>|@Catalog|<span data-ttu-id="72b78-242">SPECIFIC_CATALOG</span><span class="sxs-lookup"><span data-stu-id="72b78-242">SPECIFIC_CATALOG</span></span>|<span data-ttu-id="72b78-243">1</span><span class="sxs-lookup"><span data-stu-id="72b78-243">1</span></span>|  
|<span data-ttu-id="72b78-244">Propriétaire</span><span class="sxs-lookup"><span data-stu-id="72b78-244">Owner</span></span>|@Owner|<span data-ttu-id="72b78-245">SPECIFIC_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="72b78-245">SPECIFIC_SCHEMA</span></span>|<span data-ttu-id="72b78-246">2</span><span class="sxs-lookup"><span data-stu-id="72b78-246">2</span></span>|  
|<span data-ttu-id="72b78-247">Name</span><span class="sxs-lookup"><span data-stu-id="72b78-247">Name</span></span>|@Name|<span data-ttu-id="72b78-248">SPECIFIC_NAME</span><span class="sxs-lookup"><span data-stu-id="72b78-248">SPECIFIC_NAME</span></span>|<span data-ttu-id="72b78-249">3</span><span class="sxs-lookup"><span data-stu-id="72b78-249">3</span></span>|  
|<span data-ttu-id="72b78-250">Paramètre</span><span class="sxs-lookup"><span data-stu-id="72b78-250">Parameter</span></span>|@Parameter|<span data-ttu-id="72b78-251">PARAMETER_NAME</span><span class="sxs-lookup"><span data-stu-id="72b78-251">PARAMETER_NAME</span></span>|<span data-ttu-id="72b78-252">4</span><span class="sxs-lookup"><span data-stu-id="72b78-252">4</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="72b78-253">Procédures</span><span class="sxs-lookup"><span data-stu-id="72b78-253">Procedures</span></span>  
  
|<span data-ttu-id="72b78-254">Nom de restriction</span><span class="sxs-lookup"><span data-stu-id="72b78-254">Restriction Name</span></span>|<span data-ttu-id="72b78-255">nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="72b78-255">Parameter Name</span></span>|<span data-ttu-id="72b78-256">Valeur par défaut de la restriction</span><span class="sxs-lookup"><span data-stu-id="72b78-256">Restriction Default</span></span>|<span data-ttu-id="72b78-257">Numéro de restriction</span><span class="sxs-lookup"><span data-stu-id="72b78-257">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="72b78-258">Catalogue</span><span class="sxs-lookup"><span data-stu-id="72b78-258">Catalog</span></span>|@Catalog|<span data-ttu-id="72b78-259">SPECIFIC_CATALOG</span><span class="sxs-lookup"><span data-stu-id="72b78-259">SPECIFIC_CATALOG</span></span>|<span data-ttu-id="72b78-260">1</span><span class="sxs-lookup"><span data-stu-id="72b78-260">1</span></span>|  
|<span data-ttu-id="72b78-261">Propriétaire</span><span class="sxs-lookup"><span data-stu-id="72b78-261">Owner</span></span>|@Owner|<span data-ttu-id="72b78-262">SPECIFIC_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="72b78-262">SPECIFIC_SCHEMA</span></span>|<span data-ttu-id="72b78-263">2</span><span class="sxs-lookup"><span data-stu-id="72b78-263">2</span></span>|  
|<span data-ttu-id="72b78-264">Nom</span><span class="sxs-lookup"><span data-stu-id="72b78-264">Name</span></span>|@Name|<span data-ttu-id="72b78-265">SPECIFIC_NAME</span><span class="sxs-lookup"><span data-stu-id="72b78-265">SPECIFIC_NAME</span></span>|<span data-ttu-id="72b78-266">3</span><span class="sxs-lookup"><span data-stu-id="72b78-266">3</span></span>|  
|<span data-ttu-id="72b78-267">Type</span><span class="sxs-lookup"><span data-stu-id="72b78-267">Type</span></span>|@Type|<span data-ttu-id="72b78-268">ROUTINE_TYPE</span><span class="sxs-lookup"><span data-stu-id="72b78-268">ROUTINE_TYPE</span></span>|<span data-ttu-id="72b78-269">4</span><span class="sxs-lookup"><span data-stu-id="72b78-269">4</span></span>|  
  
### <a name="indexcolumns"></a><span data-ttu-id="72b78-270">IndexColumns</span><span class="sxs-lookup"><span data-stu-id="72b78-270">IndexColumns</span></span>  
  
|<span data-ttu-id="72b78-271">Nom de restriction</span><span class="sxs-lookup"><span data-stu-id="72b78-271">Restriction Name</span></span>|<span data-ttu-id="72b78-272">nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="72b78-272">Parameter Name</span></span>|<span data-ttu-id="72b78-273">Valeur par défaut de la restriction</span><span class="sxs-lookup"><span data-stu-id="72b78-273">Restriction Default</span></span>|<span data-ttu-id="72b78-274">Numéro de restriction</span><span class="sxs-lookup"><span data-stu-id="72b78-274">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="72b78-275">Catalogue</span><span class="sxs-lookup"><span data-stu-id="72b78-275">Catalog</span></span>|@Catalog|<span data-ttu-id="72b78-276">db_name()</span><span class="sxs-lookup"><span data-stu-id="72b78-276">db_name()</span></span>|<span data-ttu-id="72b78-277">1</span><span class="sxs-lookup"><span data-stu-id="72b78-277">1</span></span>|  
|<span data-ttu-id="72b78-278">Propriétaire</span><span class="sxs-lookup"><span data-stu-id="72b78-278">Owner</span></span>|@Owner|<span data-ttu-id="72b78-279">user_name()</span><span class="sxs-lookup"><span data-stu-id="72b78-279">user_name()</span></span>|<span data-ttu-id="72b78-280">2</span><span class="sxs-lookup"><span data-stu-id="72b78-280">2</span></span>|  
|<span data-ttu-id="72b78-281">Table</span><span class="sxs-lookup"><span data-stu-id="72b78-281">Table</span></span>|@Table|<span data-ttu-id="72b78-282">o.name</span><span class="sxs-lookup"><span data-stu-id="72b78-282">o.name</span></span>|<span data-ttu-id="72b78-283">3</span><span class="sxs-lookup"><span data-stu-id="72b78-283">3</span></span>|  
|<span data-ttu-id="72b78-284">ConstraintName</span><span class="sxs-lookup"><span data-stu-id="72b78-284">ConstraintName</span></span>|@ConstraintName|<span data-ttu-id="72b78-285">x.name</span><span class="sxs-lookup"><span data-stu-id="72b78-285">x.name</span></span>|<span data-ttu-id="72b78-286">4</span><span class="sxs-lookup"><span data-stu-id="72b78-286">4</span></span>|  
|<span data-ttu-id="72b78-287">Colonne</span><span class="sxs-lookup"><span data-stu-id="72b78-287">Column</span></span>|@Column|<span data-ttu-id="72b78-288">c.name</span><span class="sxs-lookup"><span data-stu-id="72b78-288">c.name</span></span>|<span data-ttu-id="72b78-289">5\.</span><span class="sxs-lookup"><span data-stu-id="72b78-289">5</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="72b78-290">Index</span><span class="sxs-lookup"><span data-stu-id="72b78-290">Indexes</span></span>  
  
|<span data-ttu-id="72b78-291">Nom de restriction</span><span class="sxs-lookup"><span data-stu-id="72b78-291">Restriction Name</span></span>|<span data-ttu-id="72b78-292">nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="72b78-292">Parameter Name</span></span>|<span data-ttu-id="72b78-293">Valeur par défaut de la restriction</span><span class="sxs-lookup"><span data-stu-id="72b78-293">Restriction Default</span></span>|<span data-ttu-id="72b78-294">Numéro de restriction</span><span class="sxs-lookup"><span data-stu-id="72b78-294">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="72b78-295">Catalogue</span><span class="sxs-lookup"><span data-stu-id="72b78-295">Catalog</span></span>|@Catalog|<span data-ttu-id="72b78-296">db_name()</span><span class="sxs-lookup"><span data-stu-id="72b78-296">db_name()</span></span>|<span data-ttu-id="72b78-297">1</span><span class="sxs-lookup"><span data-stu-id="72b78-297">1</span></span>|  
|<span data-ttu-id="72b78-298">Propriétaire</span><span class="sxs-lookup"><span data-stu-id="72b78-298">Owner</span></span>|@Owner|<span data-ttu-id="72b78-299">user_name()</span><span class="sxs-lookup"><span data-stu-id="72b78-299">user_name()</span></span>|<span data-ttu-id="72b78-300">2</span><span class="sxs-lookup"><span data-stu-id="72b78-300">2</span></span>|  
|<span data-ttu-id="72b78-301">Table</span><span class="sxs-lookup"><span data-stu-id="72b78-301">Table</span></span>|@Table|<span data-ttu-id="72b78-302">o.name</span><span class="sxs-lookup"><span data-stu-id="72b78-302">o.name</span></span>|<span data-ttu-id="72b78-303">3</span><span class="sxs-lookup"><span data-stu-id="72b78-303">3</span></span>|  
  
### <a name="userdefinedtypes"></a><span data-ttu-id="72b78-304">UserDefinedTypes</span><span class="sxs-lookup"><span data-stu-id="72b78-304">UserDefinedTypes</span></span>  
  
|<span data-ttu-id="72b78-305">Nom de restriction</span><span class="sxs-lookup"><span data-stu-id="72b78-305">Restriction Name</span></span>|<span data-ttu-id="72b78-306">nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="72b78-306">Parameter Name</span></span>|<span data-ttu-id="72b78-307">Valeur par défaut de la restriction</span><span class="sxs-lookup"><span data-stu-id="72b78-307">Restriction Default</span></span>|<span data-ttu-id="72b78-308">Numéro de restriction</span><span class="sxs-lookup"><span data-stu-id="72b78-308">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="72b78-309">assembly_name</span><span class="sxs-lookup"><span data-stu-id="72b78-309">assembly_name</span></span>|@AssemblyName|<span data-ttu-id="72b78-310">assemblies.name</span><span class="sxs-lookup"><span data-stu-id="72b78-310">assemblies.name</span></span>|<span data-ttu-id="72b78-311">1</span><span class="sxs-lookup"><span data-stu-id="72b78-311">1</span></span>|  
|<span data-ttu-id="72b78-312">udt_name</span><span class="sxs-lookup"><span data-stu-id="72b78-312">udt_name</span></span>|@UDTName|<span data-ttu-id="72b78-313">types.assembly_class</span><span class="sxs-lookup"><span data-stu-id="72b78-313">types.assembly_class</span></span>|<span data-ttu-id="72b78-314">2</span><span class="sxs-lookup"><span data-stu-id="72b78-314">2</span></span>|  
  
### <a name="foreignkeys"></a><span data-ttu-id="72b78-315">ForeignKeys</span><span class="sxs-lookup"><span data-stu-id="72b78-315">ForeignKeys</span></span>  
  
|<span data-ttu-id="72b78-316">Nom de restriction</span><span class="sxs-lookup"><span data-stu-id="72b78-316">Restriction Name</span></span>|<span data-ttu-id="72b78-317">nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="72b78-317">Parameter Name</span></span>|<span data-ttu-id="72b78-318">Valeur par défaut de la restriction</span><span class="sxs-lookup"><span data-stu-id="72b78-318">Restriction Default</span></span>|<span data-ttu-id="72b78-319">Numéro de restriction</span><span class="sxs-lookup"><span data-stu-id="72b78-319">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="72b78-320">Catalogue</span><span class="sxs-lookup"><span data-stu-id="72b78-320">Catalog</span></span>|@Catalog|<span data-ttu-id="72b78-321">CONSTRAINT_CATALOG</span><span class="sxs-lookup"><span data-stu-id="72b78-321">CONSTRAINT_CATALOG</span></span>|<span data-ttu-id="72b78-322">1</span><span class="sxs-lookup"><span data-stu-id="72b78-322">1</span></span>|  
|<span data-ttu-id="72b78-323">Propriétaire</span><span class="sxs-lookup"><span data-stu-id="72b78-323">Owner</span></span>|@Owner|<span data-ttu-id="72b78-324">CONSTRAINT_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="72b78-324">CONSTRAINT_SCHEMA</span></span>|<span data-ttu-id="72b78-325">2</span><span class="sxs-lookup"><span data-stu-id="72b78-325">2</span></span>|  
|<span data-ttu-id="72b78-326">Table</span><span class="sxs-lookup"><span data-stu-id="72b78-326">Table</span></span>|@Table|<span data-ttu-id="72b78-327">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="72b78-327">TABLE_NAME</span></span>|<span data-ttu-id="72b78-328">3</span><span class="sxs-lookup"><span data-stu-id="72b78-328">3</span></span>|  
|<span data-ttu-id="72b78-329">Nom</span><span class="sxs-lookup"><span data-stu-id="72b78-329">Name</span></span>|@Name|<span data-ttu-id="72b78-330">CONSTRAINT_NAME</span><span class="sxs-lookup"><span data-stu-id="72b78-330">CONSTRAINT_NAME</span></span>|<span data-ttu-id="72b78-331">4</span><span class="sxs-lookup"><span data-stu-id="72b78-331">4</span></span>|  
  
## <a name="sql-server-2008-schema-restrictions"></a><span data-ttu-id="72b78-332">Restrictions de schéma SQL Server 2008</span><span class="sxs-lookup"><span data-stu-id="72b78-332">SQL Server 2008 Schema Restrictions</span></span>  
 <span data-ttu-id="72b78-333">Les tableaux suivants répertorient les restrictions pour les collections de schémas SQL Server 2008.</span><span class="sxs-lookup"><span data-stu-id="72b78-333">The following tables list the restrictions for SQL Server 2008 schema collections.</span></span> <span data-ttu-id="72b78-334">Ces restrictions s'appliquent à partir de la version 3.5 SP1 de .NET Framework et SQL Server 2008.</span><span class="sxs-lookup"><span data-stu-id="72b78-334">These restrictions are valid beginning with version 3.5 SP1 of the .NET Framework and SQL Server 2008.</span></span> <span data-ttu-id="72b78-335">Elles ne sont pas prises en charge dans les versions précédentes de .NET Framework et SQL Server.</span><span class="sxs-lookup"><span data-stu-id="72b78-335">They are not supported in earlier versions of the .NET Framework and SQL Server.</span></span>  
  
### <a name="columnsetcolumns"></a><span data-ttu-id="72b78-336">ColumnSetColumns</span><span class="sxs-lookup"><span data-stu-id="72b78-336">ColumnSetColumns</span></span>  
  
|<span data-ttu-id="72b78-337">Nom de restriction</span><span class="sxs-lookup"><span data-stu-id="72b78-337">Restriction Name</span></span>|<span data-ttu-id="72b78-338">nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="72b78-338">Parameter Name</span></span>|<span data-ttu-id="72b78-339">Valeur par défaut de la restriction</span><span class="sxs-lookup"><span data-stu-id="72b78-339">Restriction Default</span></span>|<span data-ttu-id="72b78-340">Numéro de restriction</span><span class="sxs-lookup"><span data-stu-id="72b78-340">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="72b78-341">Catalogue</span><span class="sxs-lookup"><span data-stu-id="72b78-341">Catalog</span></span>|@Catalog|<span data-ttu-id="72b78-342">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="72b78-342">TABLE_CATALOG</span></span>|<span data-ttu-id="72b78-343">1</span><span class="sxs-lookup"><span data-stu-id="72b78-343">1</span></span>|  
|<span data-ttu-id="72b78-344">Propriétaire</span><span class="sxs-lookup"><span data-stu-id="72b78-344">Owner</span></span>|@Owner|<span data-ttu-id="72b78-345">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="72b78-345">TABLE_SCHEMA</span></span>|<span data-ttu-id="72b78-346">2</span><span class="sxs-lookup"><span data-stu-id="72b78-346">2</span></span>|  
|<span data-ttu-id="72b78-347">Table</span><span class="sxs-lookup"><span data-stu-id="72b78-347">Table</span></span>|@Table|<span data-ttu-id="72b78-348">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="72b78-348">TABLE_NAME</span></span>|<span data-ttu-id="72b78-349">3</span><span class="sxs-lookup"><span data-stu-id="72b78-349">3</span></span>|  
  
### <a name="allcolumns"></a><span data-ttu-id="72b78-350">AllColumns</span><span class="sxs-lookup"><span data-stu-id="72b78-350">AllColumns</span></span>  
  
|<span data-ttu-id="72b78-351">Nom de restriction</span><span class="sxs-lookup"><span data-stu-id="72b78-351">Restriction Name</span></span>|<span data-ttu-id="72b78-352">nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="72b78-352">Parameter Name</span></span>|<span data-ttu-id="72b78-353">Valeur par défaut de la restriction</span><span class="sxs-lookup"><span data-stu-id="72b78-353">Restriction Default</span></span>|<span data-ttu-id="72b78-354">Numéro de restriction</span><span class="sxs-lookup"><span data-stu-id="72b78-354">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="72b78-355">Catalogue</span><span class="sxs-lookup"><span data-stu-id="72b78-355">Catalog</span></span>|@Catalog|<span data-ttu-id="72b78-356">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="72b78-356">TABLE_CATALOG</span></span>|<span data-ttu-id="72b78-357">1</span><span class="sxs-lookup"><span data-stu-id="72b78-357">1</span></span>|  
|<span data-ttu-id="72b78-358">Propriétaire</span><span class="sxs-lookup"><span data-stu-id="72b78-358">Owner</span></span>|@Owner|<span data-ttu-id="72b78-359">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="72b78-359">TABLE_SCHEMA</span></span>|<span data-ttu-id="72b78-360">2</span><span class="sxs-lookup"><span data-stu-id="72b78-360">2</span></span>|  
|<span data-ttu-id="72b78-361">Table</span><span class="sxs-lookup"><span data-stu-id="72b78-361">Table</span></span>|@Table|<span data-ttu-id="72b78-362">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="72b78-362">TABLE_NAME</span></span>|<span data-ttu-id="72b78-363">3</span><span class="sxs-lookup"><span data-stu-id="72b78-363">3</span></span>|  
|<span data-ttu-id="72b78-364">Colonne</span><span class="sxs-lookup"><span data-stu-id="72b78-364">Column</span></span>|@Column|<span data-ttu-id="72b78-365">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="72b78-365">COLUMN_NAME</span></span>|<span data-ttu-id="72b78-366">4</span><span class="sxs-lookup"><span data-stu-id="72b78-366">4</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="72b78-367">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="72b78-367">See also</span></span>

- [<span data-ttu-id="72b78-368">Fournisseurs managés ADO.NET et centre de développement DataSet</span><span class="sxs-lookup"><span data-stu-id="72b78-368">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
