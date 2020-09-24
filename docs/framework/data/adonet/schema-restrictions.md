---
title: Restrictions de schéma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 73d2980e-e73c-4987-913a-8ddc93d09144
ms.openlocfilehash: c0a3cafef45341cd95fa0a4f65c818129e120e44
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91147822"
---
# <a name="schema-restrictions"></a><span data-ttu-id="1d486-102">Restrictions de schéma</span><span class="sxs-lookup"><span data-stu-id="1d486-102">Schema Restrictions</span></span>

<span data-ttu-id="1d486-103">Le deuxième paramètre facultatif de la méthode **GetSchema** correspond aux restrictions utilisées pour limiter la quantité d’informations de schéma retournées, et il est passé à la méthode **GetSchema** sous la forme d’un tableau de chaînes.</span><span class="sxs-lookup"><span data-stu-id="1d486-103">The second optional parameter of the **GetSchema** method is the restrictions that are used to limit the amount of schema information returned, and it is passed to the **GetSchema** method as an array of strings.</span></span> <span data-ttu-id="1d486-104">La position dans le tableau détermine les valeurs que vous pouvez passer et équivaut au numéro de restriction.</span><span class="sxs-lookup"><span data-stu-id="1d486-104">The position in the array determines the values that you can pass, and this is equivalent to the restriction number.</span></span>  
  
 <span data-ttu-id="1d486-105">Par exemple, le tableau suivant décrit les restrictions prises en charge par la collection de schémas « Tables » utilisant le fournisseur de données .NET Framework pour SQL Server.</span><span class="sxs-lookup"><span data-stu-id="1d486-105">For example, the following table describes the restrictions supported by the "Tables" schema collection using the .NET Framework Data Provider for SQL Server.</span></span> <span data-ttu-id="1d486-106">Des restrictions supplémentaires pour les collections de schémas SQL Server figurent à la fin de cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="1d486-106">Additional restrictions for SQL Server schema collections are listed at the end of this topic.</span></span>  
  
|<span data-ttu-id="1d486-107">Nom de restriction</span><span class="sxs-lookup"><span data-stu-id="1d486-107">Restriction Name</span></span>|<span data-ttu-id="1d486-108">Nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="1d486-108">Parameter Name</span></span>|<span data-ttu-id="1d486-109">Valeur par défaut de la restriction</span><span class="sxs-lookup"><span data-stu-id="1d486-109">Restriction Default</span></span>|<span data-ttu-id="1d486-110">Numéro de restriction</span><span class="sxs-lookup"><span data-stu-id="1d486-110">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="1d486-111">Catalogue</span><span class="sxs-lookup"><span data-stu-id="1d486-111">Catalog</span></span>|@Catalog|<span data-ttu-id="1d486-112">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="1d486-112">TABLE_CATALOG</span></span>|<span data-ttu-id="1d486-113">1</span><span class="sxs-lookup"><span data-stu-id="1d486-113">1</span></span>|  
|<span data-ttu-id="1d486-114">Propriétaire</span><span class="sxs-lookup"><span data-stu-id="1d486-114">Owner</span></span>|@Owner|<span data-ttu-id="1d486-115">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="1d486-115">TABLE_SCHEMA</span></span>|<span data-ttu-id="1d486-116">2</span><span class="sxs-lookup"><span data-stu-id="1d486-116">2</span></span>|  
|<span data-ttu-id="1d486-117">Table de charge de travail</span><span class="sxs-lookup"><span data-stu-id="1d486-117">Table</span></span>|@Name|<span data-ttu-id="1d486-118">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="1d486-118">TABLE_NAME</span></span>|<span data-ttu-id="1d486-119">3</span><span class="sxs-lookup"><span data-stu-id="1d486-119">3</span></span>|  
|<span data-ttu-id="1d486-120">TableType</span><span class="sxs-lookup"><span data-stu-id="1d486-120">TableType</span></span>|@TableType|<span data-ttu-id="1d486-121">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="1d486-121">TABLE_TYPE</span></span>|<span data-ttu-id="1d486-122">4</span><span class="sxs-lookup"><span data-stu-id="1d486-122">4</span></span>|  
  
## <a name="specifying-restriction-values"></a><span data-ttu-id="1d486-123">Spécification des valeurs de restriction</span><span class="sxs-lookup"><span data-stu-id="1d486-123">Specifying Restriction Values</span></span>  

 <span data-ttu-id="1d486-124">Pour utiliser l’une des restrictions de la collection de schémas « Tables », créez simplement un tableau de chaînes contenant quatre éléments, puis placez une valeur dans l’élément correspondant au numéro de restriction.</span><span class="sxs-lookup"><span data-stu-id="1d486-124">To use one of the restrictions of the "Tables" schema collection, simply create an array of strings with four elements, then place a value in the element that matches the restriction number.</span></span> <span data-ttu-id="1d486-125">Par exemple, pour restreindre les tables retournées par la méthode **GetSchema** aux seules tables du schéma « Sales », définissez le deuxième élément du tableau sur « sales » avant de le passer à la méthode **GetSchema** .</span><span class="sxs-lookup"><span data-stu-id="1d486-125">For example, to restrict the tables returned by the **GetSchema** method to only those tables in the "Sales" schema, set the second element of the array to "Sales" before passing it to the **GetSchema** method.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1d486-126">Les collections de restrictions pour `SqlClient` et `OracleClient` comportent une colonne `ParameterName` supplémentaire.</span><span class="sxs-lookup"><span data-stu-id="1d486-126">The restrictions collections for `SqlClient` and `OracleClient` have an additional `ParameterName` column.</span></span> <span data-ttu-id="1d486-127">La colonne par défaut de la restriction est encore là pour la compatibilité ascendante, mais est désormais ignorée.</span><span class="sxs-lookup"><span data-stu-id="1d486-127">The restriction default column is still there for backwards compatibility, but is currently ignored.</span></span> <span data-ttu-id="1d486-128">Il convient d'utiliser des requêtes paramétrées plutôt qu'un remplacement de chaîne afin de minimiser le risque d'attaque par injection SQL lors de la spécification de valeurs de restriction.</span><span class="sxs-lookup"><span data-stu-id="1d486-128">Parameterized queries rather than string replacement should be used to minimize the risk of an SQL injection attack when specifying restriction values.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1d486-129">Le nombre d'éléments du tableau doit être inférieur ou égal au nombre de restrictions prises en charge pour la collection de schémas spécifiée, sans quoi une exception <xref:System.ArgumentException> est levée.</span><span class="sxs-lookup"><span data-stu-id="1d486-129">The number of elements in the array must be less than or equal to the number of restrictions supported for the specified schema collection else an <xref:System.ArgumentException> will be thrown.</span></span> <span data-ttu-id="1d486-130">Il peut y avoir moins de restrictions que le nombre maximal de restrictions.</span><span class="sxs-lookup"><span data-stu-id="1d486-130">There can be fewer than the maximum number of restrictions.</span></span> <span data-ttu-id="1d486-131">Les restrictions manquantes sont supposées avoir la valeur null (aucune restriction).</span><span class="sxs-lookup"><span data-stu-id="1d486-131">The missing restrictions are assumed to be null (unrestricted).</span></span>  
  
 <span data-ttu-id="1d486-132">Vous pouvez interroger un fournisseur managé .NET Framework pour déterminer la liste des restrictions prises en charge en appelant la méthode **GetSchema** avec le nom de la collection de schémas de restrictions, qui est « restrictions ».</span><span class="sxs-lookup"><span data-stu-id="1d486-132">You can query a .NET Framework managed provider to determine the list of supported restrictions by calling the **GetSchema** method with the name of the restrictions schema collection, which is "Restrictions".</span></span> <span data-ttu-id="1d486-133">Cette opération retourne un <xref:System.Data.DataTable> contenant une liste des noms de collections, des noms de restriction, des valeurs de restriction par défaut et des numéros de restriction.</span><span class="sxs-lookup"><span data-stu-id="1d486-133">This will return a <xref:System.Data.DataTable> with a list of the collection names, the restriction names, the default restriction values, and the restriction numbers.</span></span>  
  
### <a name="example"></a><span data-ttu-id="1d486-134">Exemple</span><span class="sxs-lookup"><span data-stu-id="1d486-134">Example</span></span>  

 <span data-ttu-id="1d486-135">Les exemples suivants montrent comment utiliser la <xref:System.Data.SqlClient.SqlConnection.GetSchema%2A> méthode de la .NET Framework fournisseur de données pour la classe SQL Server <xref:System.Data.SqlClient.SqlConnection> pour récupérer des informations de schéma sur toutes les tables contenues dans l’exemple de base de données **AdventureWorks** et pour limiter les informations retournées aux seules tables du schéma « Sales » :</span><span class="sxs-lookup"><span data-stu-id="1d486-135">The following examples demonstrate how to use the <xref:System.Data.SqlClient.SqlConnection.GetSchema%2A> method of the .NET Framework Data Provider for the SQL Server <xref:System.Data.SqlClient.SqlConnection> class to retrieve schema information about all of the tables contained in the **AdventureWorks** sample database, and to restrict the information returned to only those tables in the "Sales" schema:</span></span>  
  
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
  
## <a name="sql-server-schema-restrictions"></a><span data-ttu-id="1d486-136">Restrictions de schéma SQL Server</span><span class="sxs-lookup"><span data-stu-id="1d486-136">SQL Server Schema Restrictions</span></span>  

 <span data-ttu-id="1d486-137">Les tableaux suivants énumèrent les restrictions pour les collections de schémas SQL Server.</span><span class="sxs-lookup"><span data-stu-id="1d486-137">The following tables list the restrictions for SQL Server schema collections.</span></span>  
  
### <a name="users"></a><span data-ttu-id="1d486-138">Utilisateurs</span><span class="sxs-lookup"><span data-stu-id="1d486-138">Users</span></span>  
  
|<span data-ttu-id="1d486-139">Nom de restriction</span><span class="sxs-lookup"><span data-stu-id="1d486-139">Restriction Name</span></span>|<span data-ttu-id="1d486-140">Nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="1d486-140">Parameter Name</span></span>|<span data-ttu-id="1d486-141">Valeur par défaut de la restriction</span><span class="sxs-lookup"><span data-stu-id="1d486-141">Restriction Default</span></span>|<span data-ttu-id="1d486-142">Numéro de restriction</span><span class="sxs-lookup"><span data-stu-id="1d486-142">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="1d486-143">User_Name</span><span class="sxs-lookup"><span data-stu-id="1d486-143">User_Name</span></span>|@Name|<span data-ttu-id="1d486-144">name</span><span class="sxs-lookup"><span data-stu-id="1d486-144">name</span></span>|<span data-ttu-id="1d486-145">1</span><span class="sxs-lookup"><span data-stu-id="1d486-145">1</span></span>|  
  
### <a name="databases"></a><span data-ttu-id="1d486-146">Bases de données</span><span class="sxs-lookup"><span data-stu-id="1d486-146">Databases</span></span>  
  
|<span data-ttu-id="1d486-147">Nom de restriction</span><span class="sxs-lookup"><span data-stu-id="1d486-147">Restriction Name</span></span>|<span data-ttu-id="1d486-148">Nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="1d486-148">Parameter Name</span></span>|<span data-ttu-id="1d486-149">Valeur par défaut de la restriction</span><span class="sxs-lookup"><span data-stu-id="1d486-149">Restriction Default</span></span>|<span data-ttu-id="1d486-150">Numéro de restriction</span><span class="sxs-lookup"><span data-stu-id="1d486-150">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="1d486-151">Nom</span><span class="sxs-lookup"><span data-stu-id="1d486-151">Name</span></span>|@Name|<span data-ttu-id="1d486-152">Nom</span><span class="sxs-lookup"><span data-stu-id="1d486-152">Name</span></span>|<span data-ttu-id="1d486-153">1</span><span class="sxs-lookup"><span data-stu-id="1d486-153">1</span></span>|  
  
### <a name="tables"></a><span data-ttu-id="1d486-154">Tables</span><span class="sxs-lookup"><span data-stu-id="1d486-154">Tables</span></span>  
  
|<span data-ttu-id="1d486-155">Nom de restriction</span><span class="sxs-lookup"><span data-stu-id="1d486-155">Restriction Name</span></span>|<span data-ttu-id="1d486-156">Nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="1d486-156">Parameter Name</span></span>|<span data-ttu-id="1d486-157">Valeur par défaut de la restriction</span><span class="sxs-lookup"><span data-stu-id="1d486-157">Restriction Default</span></span>|<span data-ttu-id="1d486-158">Numéro de restriction</span><span class="sxs-lookup"><span data-stu-id="1d486-158">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="1d486-159">Catalogue</span><span class="sxs-lookup"><span data-stu-id="1d486-159">Catalog</span></span>|@Catalog|<span data-ttu-id="1d486-160">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="1d486-160">TABLE_CATALOG</span></span>|<span data-ttu-id="1d486-161">1</span><span class="sxs-lookup"><span data-stu-id="1d486-161">1</span></span>|  
|<span data-ttu-id="1d486-162">Propriétaire</span><span class="sxs-lookup"><span data-stu-id="1d486-162">Owner</span></span>|@Owner|<span data-ttu-id="1d486-163">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="1d486-163">TABLE_SCHEMA</span></span>|<span data-ttu-id="1d486-164">2</span><span class="sxs-lookup"><span data-stu-id="1d486-164">2</span></span>|  
|<span data-ttu-id="1d486-165">Table de charge de travail</span><span class="sxs-lookup"><span data-stu-id="1d486-165">Table</span></span>|@Name|<span data-ttu-id="1d486-166">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="1d486-166">TABLE_NAME</span></span>|<span data-ttu-id="1d486-167">3</span><span class="sxs-lookup"><span data-stu-id="1d486-167">3</span></span>|  
|<span data-ttu-id="1d486-168">TableType</span><span class="sxs-lookup"><span data-stu-id="1d486-168">TableType</span></span>|@TableType|<span data-ttu-id="1d486-169">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="1d486-169">TABLE_TYPE</span></span>|<span data-ttu-id="1d486-170">4</span><span class="sxs-lookup"><span data-stu-id="1d486-170">4</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="1d486-171">Colonnes</span><span class="sxs-lookup"><span data-stu-id="1d486-171">Columns</span></span>  
  
|<span data-ttu-id="1d486-172">Nom de restriction</span><span class="sxs-lookup"><span data-stu-id="1d486-172">Restriction Name</span></span>|<span data-ttu-id="1d486-173">Nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="1d486-173">Parameter Name</span></span>|<span data-ttu-id="1d486-174">Valeur par défaut de la restriction</span><span class="sxs-lookup"><span data-stu-id="1d486-174">Restriction Default</span></span>|<span data-ttu-id="1d486-175">Numéro de restriction</span><span class="sxs-lookup"><span data-stu-id="1d486-175">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="1d486-176">Catalogue</span><span class="sxs-lookup"><span data-stu-id="1d486-176">Catalog</span></span>|@Catalog|<span data-ttu-id="1d486-177">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="1d486-177">TABLE_CATALOG</span></span>|<span data-ttu-id="1d486-178">1</span><span class="sxs-lookup"><span data-stu-id="1d486-178">1</span></span>|  
|<span data-ttu-id="1d486-179">Propriétaire</span><span class="sxs-lookup"><span data-stu-id="1d486-179">Owner</span></span>|@Owner|<span data-ttu-id="1d486-180">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="1d486-180">TABLE_SCHEMA</span></span>|<span data-ttu-id="1d486-181">2</span><span class="sxs-lookup"><span data-stu-id="1d486-181">2</span></span>|  
|<span data-ttu-id="1d486-182">Table de charge de travail</span><span class="sxs-lookup"><span data-stu-id="1d486-182">Table</span></span>|@Table|<span data-ttu-id="1d486-183">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="1d486-183">TABLE_NAME</span></span>|<span data-ttu-id="1d486-184">3</span><span class="sxs-lookup"><span data-stu-id="1d486-184">3</span></span>|  
|<span data-ttu-id="1d486-185">Colonne</span><span class="sxs-lookup"><span data-stu-id="1d486-185">Column</span></span>|@Column|<span data-ttu-id="1d486-186">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="1d486-186">COLUMN_NAME</span></span>|<span data-ttu-id="1d486-187">4</span><span class="sxs-lookup"><span data-stu-id="1d486-187">4</span></span>|  
  
### <a name="structuredtypemembers"></a><span data-ttu-id="1d486-188">StructuredTypeMembers</span><span class="sxs-lookup"><span data-stu-id="1d486-188">StructuredTypeMembers</span></span>  
  
|<span data-ttu-id="1d486-189">Nom de restriction</span><span class="sxs-lookup"><span data-stu-id="1d486-189">Restriction Name</span></span>|<span data-ttu-id="1d486-190">Nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="1d486-190">Parameter Name</span></span>|<span data-ttu-id="1d486-191">Valeur par défaut de la restriction</span><span class="sxs-lookup"><span data-stu-id="1d486-191">Restriction Default</span></span>|<span data-ttu-id="1d486-192">Numéro de restriction</span><span class="sxs-lookup"><span data-stu-id="1d486-192">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="1d486-193">Catalogue</span><span class="sxs-lookup"><span data-stu-id="1d486-193">Catalog</span></span>|@Catalog|<span data-ttu-id="1d486-194">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="1d486-194">TABLE_CATALOG</span></span>|<span data-ttu-id="1d486-195">1</span><span class="sxs-lookup"><span data-stu-id="1d486-195">1</span></span>|  
|<span data-ttu-id="1d486-196">Propriétaire</span><span class="sxs-lookup"><span data-stu-id="1d486-196">Owner</span></span>|@Owner|<span data-ttu-id="1d486-197">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="1d486-197">TABLE_SCHEMA</span></span>|<span data-ttu-id="1d486-198">2</span><span class="sxs-lookup"><span data-stu-id="1d486-198">2</span></span>|  
|<span data-ttu-id="1d486-199">Table de charge de travail</span><span class="sxs-lookup"><span data-stu-id="1d486-199">Table</span></span>|@Table|<span data-ttu-id="1d486-200">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="1d486-200">TABLE_NAME</span></span>|<span data-ttu-id="1d486-201">3</span><span class="sxs-lookup"><span data-stu-id="1d486-201">3</span></span>|  
|<span data-ttu-id="1d486-202">Colonne</span><span class="sxs-lookup"><span data-stu-id="1d486-202">Column</span></span>|@Column|<span data-ttu-id="1d486-203">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="1d486-203">COLUMN_NAME</span></span>|<span data-ttu-id="1d486-204">4</span><span class="sxs-lookup"><span data-stu-id="1d486-204">4</span></span>|  
  
### <a name="views"></a><span data-ttu-id="1d486-205">Les vues</span><span class="sxs-lookup"><span data-stu-id="1d486-205">Views</span></span>  
  
|<span data-ttu-id="1d486-206">Nom de restriction</span><span class="sxs-lookup"><span data-stu-id="1d486-206">Restriction Name</span></span>|<span data-ttu-id="1d486-207">Nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="1d486-207">Parameter Name</span></span>|<span data-ttu-id="1d486-208">Valeur par défaut de la restriction</span><span class="sxs-lookup"><span data-stu-id="1d486-208">Restriction Default</span></span>|<span data-ttu-id="1d486-209">Numéro de restriction</span><span class="sxs-lookup"><span data-stu-id="1d486-209">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="1d486-210">Catalogue</span><span class="sxs-lookup"><span data-stu-id="1d486-210">Catalog</span></span>|@Catalog|<span data-ttu-id="1d486-211">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="1d486-211">TABLE_CATALOG</span></span>|<span data-ttu-id="1d486-212">1</span><span class="sxs-lookup"><span data-stu-id="1d486-212">1</span></span>|  
|<span data-ttu-id="1d486-213">Propriétaire</span><span class="sxs-lookup"><span data-stu-id="1d486-213">Owner</span></span>|@Owner|<span data-ttu-id="1d486-214">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="1d486-214">TABLE_SCHEMA</span></span>|<span data-ttu-id="1d486-215">2</span><span class="sxs-lookup"><span data-stu-id="1d486-215">2</span></span>|  
|<span data-ttu-id="1d486-216">Table de charge de travail</span><span class="sxs-lookup"><span data-stu-id="1d486-216">Table</span></span>|@Table|<span data-ttu-id="1d486-217">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="1d486-217">TABLE_NAME</span></span>|<span data-ttu-id="1d486-218">3</span><span class="sxs-lookup"><span data-stu-id="1d486-218">3</span></span>|  
  
### <a name="viewcolumns"></a><span data-ttu-id="1d486-219">ViewColumns</span><span class="sxs-lookup"><span data-stu-id="1d486-219">ViewColumns</span></span>  
  
|<span data-ttu-id="1d486-220">Nom de restriction</span><span class="sxs-lookup"><span data-stu-id="1d486-220">Restriction Name</span></span>|<span data-ttu-id="1d486-221">Nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="1d486-221">Parameter Name</span></span>|<span data-ttu-id="1d486-222">Valeur par défaut de la restriction</span><span class="sxs-lookup"><span data-stu-id="1d486-222">Restriction Default</span></span>|<span data-ttu-id="1d486-223">Numéro de restriction</span><span class="sxs-lookup"><span data-stu-id="1d486-223">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="1d486-224">Catalogue</span><span class="sxs-lookup"><span data-stu-id="1d486-224">Catalog</span></span>|@Catalog|<span data-ttu-id="1d486-225">VIEW_CATALOG</span><span class="sxs-lookup"><span data-stu-id="1d486-225">VIEW_CATALOG</span></span>|<span data-ttu-id="1d486-226">1</span><span class="sxs-lookup"><span data-stu-id="1d486-226">1</span></span>|  
|<span data-ttu-id="1d486-227">Propriétaire</span><span class="sxs-lookup"><span data-stu-id="1d486-227">Owner</span></span>|@Owner|<span data-ttu-id="1d486-228">VIEW_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="1d486-228">VIEW_SCHEMA</span></span>|<span data-ttu-id="1d486-229">2</span><span class="sxs-lookup"><span data-stu-id="1d486-229">2</span></span>|  
|<span data-ttu-id="1d486-230">Table de charge de travail</span><span class="sxs-lookup"><span data-stu-id="1d486-230">Table</span></span>|@Table|<span data-ttu-id="1d486-231">VIEW_NAME</span><span class="sxs-lookup"><span data-stu-id="1d486-231">VIEW_NAME</span></span>|<span data-ttu-id="1d486-232">3</span><span class="sxs-lookup"><span data-stu-id="1d486-232">3</span></span>|  
|<span data-ttu-id="1d486-233">Colonne</span><span class="sxs-lookup"><span data-stu-id="1d486-233">Column</span></span>|@Column|<span data-ttu-id="1d486-234">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="1d486-234">COLUMN_NAME</span></span>|<span data-ttu-id="1d486-235">4</span><span class="sxs-lookup"><span data-stu-id="1d486-235">4</span></span>|  
  
### <a name="procedureparameters"></a><span data-ttu-id="1d486-236">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="1d486-236">ProcedureParameters</span></span>  
  
|<span data-ttu-id="1d486-237">Nom de restriction</span><span class="sxs-lookup"><span data-stu-id="1d486-237">Restriction Name</span></span>|<span data-ttu-id="1d486-238">Nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="1d486-238">Parameter Name</span></span>|<span data-ttu-id="1d486-239">Valeur par défaut de la restriction</span><span class="sxs-lookup"><span data-stu-id="1d486-239">Restriction Default</span></span>|<span data-ttu-id="1d486-240">Numéro de restriction</span><span class="sxs-lookup"><span data-stu-id="1d486-240">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="1d486-241">Catalogue</span><span class="sxs-lookup"><span data-stu-id="1d486-241">Catalog</span></span>|@Catalog|<span data-ttu-id="1d486-242">SPECIFIC_CATALOG</span><span class="sxs-lookup"><span data-stu-id="1d486-242">SPECIFIC_CATALOG</span></span>|<span data-ttu-id="1d486-243">1</span><span class="sxs-lookup"><span data-stu-id="1d486-243">1</span></span>|  
|<span data-ttu-id="1d486-244">Propriétaire</span><span class="sxs-lookup"><span data-stu-id="1d486-244">Owner</span></span>|@Owner|<span data-ttu-id="1d486-245">SPECIFIC_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="1d486-245">SPECIFIC_SCHEMA</span></span>|<span data-ttu-id="1d486-246">2</span><span class="sxs-lookup"><span data-stu-id="1d486-246">2</span></span>|  
|<span data-ttu-id="1d486-247">Nom</span><span class="sxs-lookup"><span data-stu-id="1d486-247">Name</span></span>|@Name|<span data-ttu-id="1d486-248">SPECIFIC_NAME</span><span class="sxs-lookup"><span data-stu-id="1d486-248">SPECIFIC_NAME</span></span>|<span data-ttu-id="1d486-249">3</span><span class="sxs-lookup"><span data-stu-id="1d486-249">3</span></span>|  
|<span data-ttu-id="1d486-250">Paramètre</span><span class="sxs-lookup"><span data-stu-id="1d486-250">Parameter</span></span>|@Parameter|<span data-ttu-id="1d486-251">PARAMETER_NAME</span><span class="sxs-lookup"><span data-stu-id="1d486-251">PARAMETER_NAME</span></span>|<span data-ttu-id="1d486-252">4</span><span class="sxs-lookup"><span data-stu-id="1d486-252">4</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="1d486-253">Procédures</span><span class="sxs-lookup"><span data-stu-id="1d486-253">Procedures</span></span>  
  
|<span data-ttu-id="1d486-254">Nom de restriction</span><span class="sxs-lookup"><span data-stu-id="1d486-254">Restriction Name</span></span>|<span data-ttu-id="1d486-255">Nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="1d486-255">Parameter Name</span></span>|<span data-ttu-id="1d486-256">Valeur par défaut de la restriction</span><span class="sxs-lookup"><span data-stu-id="1d486-256">Restriction Default</span></span>|<span data-ttu-id="1d486-257">Numéro de restriction</span><span class="sxs-lookup"><span data-stu-id="1d486-257">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="1d486-258">Catalogue</span><span class="sxs-lookup"><span data-stu-id="1d486-258">Catalog</span></span>|@Catalog|<span data-ttu-id="1d486-259">SPECIFIC_CATALOG</span><span class="sxs-lookup"><span data-stu-id="1d486-259">SPECIFIC_CATALOG</span></span>|<span data-ttu-id="1d486-260">1</span><span class="sxs-lookup"><span data-stu-id="1d486-260">1</span></span>|  
|<span data-ttu-id="1d486-261">Propriétaire</span><span class="sxs-lookup"><span data-stu-id="1d486-261">Owner</span></span>|@Owner|<span data-ttu-id="1d486-262">SPECIFIC_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="1d486-262">SPECIFIC_SCHEMA</span></span>|<span data-ttu-id="1d486-263">2</span><span class="sxs-lookup"><span data-stu-id="1d486-263">2</span></span>|  
|<span data-ttu-id="1d486-264">Nom</span><span class="sxs-lookup"><span data-stu-id="1d486-264">Name</span></span>|@Name|<span data-ttu-id="1d486-265">SPECIFIC_NAME</span><span class="sxs-lookup"><span data-stu-id="1d486-265">SPECIFIC_NAME</span></span>|<span data-ttu-id="1d486-266">3</span><span class="sxs-lookup"><span data-stu-id="1d486-266">3</span></span>|  
|<span data-ttu-id="1d486-267">Type</span><span class="sxs-lookup"><span data-stu-id="1d486-267">Type</span></span>|@Type|<span data-ttu-id="1d486-268">ROUTINE_TYPE</span><span class="sxs-lookup"><span data-stu-id="1d486-268">ROUTINE_TYPE</span></span>|<span data-ttu-id="1d486-269">4</span><span class="sxs-lookup"><span data-stu-id="1d486-269">4</span></span>|  
  
### <a name="indexcolumns"></a><span data-ttu-id="1d486-270">IndexColumns</span><span class="sxs-lookup"><span data-stu-id="1d486-270">IndexColumns</span></span>  
  
|<span data-ttu-id="1d486-271">Nom de restriction</span><span class="sxs-lookup"><span data-stu-id="1d486-271">Restriction Name</span></span>|<span data-ttu-id="1d486-272">Nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="1d486-272">Parameter Name</span></span>|<span data-ttu-id="1d486-273">Valeur par défaut de la restriction</span><span class="sxs-lookup"><span data-stu-id="1d486-273">Restriction Default</span></span>|<span data-ttu-id="1d486-274">Numéro de restriction</span><span class="sxs-lookup"><span data-stu-id="1d486-274">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="1d486-275">Catalogue</span><span class="sxs-lookup"><span data-stu-id="1d486-275">Catalog</span></span>|@Catalog|<span data-ttu-id="1d486-276">db_name()</span><span class="sxs-lookup"><span data-stu-id="1d486-276">db_name()</span></span>|<span data-ttu-id="1d486-277">1</span><span class="sxs-lookup"><span data-stu-id="1d486-277">1</span></span>|  
|<span data-ttu-id="1d486-278">Propriétaire</span><span class="sxs-lookup"><span data-stu-id="1d486-278">Owner</span></span>|@Owner|<span data-ttu-id="1d486-279">user_name()</span><span class="sxs-lookup"><span data-stu-id="1d486-279">user_name()</span></span>|<span data-ttu-id="1d486-280">2</span><span class="sxs-lookup"><span data-stu-id="1d486-280">2</span></span>|  
|<span data-ttu-id="1d486-281">Table de charge de travail</span><span class="sxs-lookup"><span data-stu-id="1d486-281">Table</span></span>|@Table|<span data-ttu-id="1d486-282">o.name</span><span class="sxs-lookup"><span data-stu-id="1d486-282">o.name</span></span>|<span data-ttu-id="1d486-283">3</span><span class="sxs-lookup"><span data-stu-id="1d486-283">3</span></span>|  
|<span data-ttu-id="1d486-284">ConstraintName</span><span class="sxs-lookup"><span data-stu-id="1d486-284">ConstraintName</span></span>|@ConstraintName|<span data-ttu-id="1d486-285">x.name</span><span class="sxs-lookup"><span data-stu-id="1d486-285">x.name</span></span>|<span data-ttu-id="1d486-286">4</span><span class="sxs-lookup"><span data-stu-id="1d486-286">4</span></span>|  
|<span data-ttu-id="1d486-287">Colonne</span><span class="sxs-lookup"><span data-stu-id="1d486-287">Column</span></span>|@Column|<span data-ttu-id="1d486-288">c.name</span><span class="sxs-lookup"><span data-stu-id="1d486-288">c.name</span></span>|<span data-ttu-id="1d486-289">5</span><span class="sxs-lookup"><span data-stu-id="1d486-289">5</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="1d486-290">Index</span><span class="sxs-lookup"><span data-stu-id="1d486-290">Indexes</span></span>  
  
|<span data-ttu-id="1d486-291">Nom de restriction</span><span class="sxs-lookup"><span data-stu-id="1d486-291">Restriction Name</span></span>|<span data-ttu-id="1d486-292">Nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="1d486-292">Parameter Name</span></span>|<span data-ttu-id="1d486-293">Valeur par défaut de la restriction</span><span class="sxs-lookup"><span data-stu-id="1d486-293">Restriction Default</span></span>|<span data-ttu-id="1d486-294">Numéro de restriction</span><span class="sxs-lookup"><span data-stu-id="1d486-294">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="1d486-295">Catalogue</span><span class="sxs-lookup"><span data-stu-id="1d486-295">Catalog</span></span>|@Catalog|<span data-ttu-id="1d486-296">db_name()</span><span class="sxs-lookup"><span data-stu-id="1d486-296">db_name()</span></span>|<span data-ttu-id="1d486-297">1</span><span class="sxs-lookup"><span data-stu-id="1d486-297">1</span></span>|  
|<span data-ttu-id="1d486-298">Propriétaire</span><span class="sxs-lookup"><span data-stu-id="1d486-298">Owner</span></span>|@Owner|<span data-ttu-id="1d486-299">user_name()</span><span class="sxs-lookup"><span data-stu-id="1d486-299">user_name()</span></span>|<span data-ttu-id="1d486-300">2</span><span class="sxs-lookup"><span data-stu-id="1d486-300">2</span></span>|  
|<span data-ttu-id="1d486-301">Table de charge de travail</span><span class="sxs-lookup"><span data-stu-id="1d486-301">Table</span></span>|@Table|<span data-ttu-id="1d486-302">o.name</span><span class="sxs-lookup"><span data-stu-id="1d486-302">o.name</span></span>|<span data-ttu-id="1d486-303">3</span><span class="sxs-lookup"><span data-stu-id="1d486-303">3</span></span>|  
  
### <a name="userdefinedtypes"></a><span data-ttu-id="1d486-304">UserDefinedTypes</span><span class="sxs-lookup"><span data-stu-id="1d486-304">UserDefinedTypes</span></span>  
  
|<span data-ttu-id="1d486-305">Nom de restriction</span><span class="sxs-lookup"><span data-stu-id="1d486-305">Restriction Name</span></span>|<span data-ttu-id="1d486-306">Nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="1d486-306">Parameter Name</span></span>|<span data-ttu-id="1d486-307">Valeur par défaut de la restriction</span><span class="sxs-lookup"><span data-stu-id="1d486-307">Restriction Default</span></span>|<span data-ttu-id="1d486-308">Numéro de restriction</span><span class="sxs-lookup"><span data-stu-id="1d486-308">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="1d486-309">assembly_name</span><span class="sxs-lookup"><span data-stu-id="1d486-309">assembly_name</span></span>|@AssemblyName|<span data-ttu-id="1d486-310">assemblies.name</span><span class="sxs-lookup"><span data-stu-id="1d486-310">assemblies.name</span></span>|<span data-ttu-id="1d486-311">1</span><span class="sxs-lookup"><span data-stu-id="1d486-311">1</span></span>|  
|<span data-ttu-id="1d486-312">udt_name</span><span class="sxs-lookup"><span data-stu-id="1d486-312">udt_name</span></span>|@UDTName|<span data-ttu-id="1d486-313">types.assembly_class</span><span class="sxs-lookup"><span data-stu-id="1d486-313">types.assembly_class</span></span>|<span data-ttu-id="1d486-314">2</span><span class="sxs-lookup"><span data-stu-id="1d486-314">2</span></span>|  
  
### <a name="foreignkeys"></a><span data-ttu-id="1d486-315">ForeignKeys</span><span class="sxs-lookup"><span data-stu-id="1d486-315">ForeignKeys</span></span>  
  
|<span data-ttu-id="1d486-316">Nom de restriction</span><span class="sxs-lookup"><span data-stu-id="1d486-316">Restriction Name</span></span>|<span data-ttu-id="1d486-317">Nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="1d486-317">Parameter Name</span></span>|<span data-ttu-id="1d486-318">Valeur par défaut de la restriction</span><span class="sxs-lookup"><span data-stu-id="1d486-318">Restriction Default</span></span>|<span data-ttu-id="1d486-319">Numéro de restriction</span><span class="sxs-lookup"><span data-stu-id="1d486-319">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="1d486-320">Catalogue</span><span class="sxs-lookup"><span data-stu-id="1d486-320">Catalog</span></span>|@Catalog|<span data-ttu-id="1d486-321">CONSTRAINT_CATALOG</span><span class="sxs-lookup"><span data-stu-id="1d486-321">CONSTRAINT_CATALOG</span></span>|<span data-ttu-id="1d486-322">1</span><span class="sxs-lookup"><span data-stu-id="1d486-322">1</span></span>|  
|<span data-ttu-id="1d486-323">Propriétaire</span><span class="sxs-lookup"><span data-stu-id="1d486-323">Owner</span></span>|@Owner|<span data-ttu-id="1d486-324">CONSTRAINT_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="1d486-324">CONSTRAINT_SCHEMA</span></span>|<span data-ttu-id="1d486-325">2</span><span class="sxs-lookup"><span data-stu-id="1d486-325">2</span></span>|  
|<span data-ttu-id="1d486-326">Table de charge de travail</span><span class="sxs-lookup"><span data-stu-id="1d486-326">Table</span></span>|@Table|<span data-ttu-id="1d486-327">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="1d486-327">TABLE_NAME</span></span>|<span data-ttu-id="1d486-328">3</span><span class="sxs-lookup"><span data-stu-id="1d486-328">3</span></span>|  
|<span data-ttu-id="1d486-329">Nom</span><span class="sxs-lookup"><span data-stu-id="1d486-329">Name</span></span>|@Name|<span data-ttu-id="1d486-330">CONSTRAINT_NAME</span><span class="sxs-lookup"><span data-stu-id="1d486-330">CONSTRAINT_NAME</span></span>|<span data-ttu-id="1d486-331">4</span><span class="sxs-lookup"><span data-stu-id="1d486-331">4</span></span>|  
  
## <a name="sql-server-2008-schema-restrictions"></a><span data-ttu-id="1d486-332">Restrictions de schéma SQL Server 2008</span><span class="sxs-lookup"><span data-stu-id="1d486-332">SQL Server 2008 Schema Restrictions</span></span>  

 <span data-ttu-id="1d486-333">Les tableaux suivants répertorient les restrictions pour les collections de schémas SQL Server 2008.</span><span class="sxs-lookup"><span data-stu-id="1d486-333">The following tables list the restrictions for SQL Server 2008 schema collections.</span></span> <span data-ttu-id="1d486-334">Ces restrictions s'appliquent à partir de la version 3.5 SP1 de .NET Framework et SQL Server 2008.</span><span class="sxs-lookup"><span data-stu-id="1d486-334">These restrictions are valid beginning with version 3.5 SP1 of the .NET Framework and SQL Server 2008.</span></span> <span data-ttu-id="1d486-335">Elles ne sont pas prises en charge dans les versions précédentes de .NET Framework et SQL Server.</span><span class="sxs-lookup"><span data-stu-id="1d486-335">They are not supported in earlier versions of the .NET Framework and SQL Server.</span></span>  
  
### <a name="columnsetcolumns"></a><span data-ttu-id="1d486-336">ColumnSetColumns</span><span class="sxs-lookup"><span data-stu-id="1d486-336">ColumnSetColumns</span></span>  
  
|<span data-ttu-id="1d486-337">Nom de restriction</span><span class="sxs-lookup"><span data-stu-id="1d486-337">Restriction Name</span></span>|<span data-ttu-id="1d486-338">Nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="1d486-338">Parameter Name</span></span>|<span data-ttu-id="1d486-339">Valeur par défaut de la restriction</span><span class="sxs-lookup"><span data-stu-id="1d486-339">Restriction Default</span></span>|<span data-ttu-id="1d486-340">Numéro de restriction</span><span class="sxs-lookup"><span data-stu-id="1d486-340">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="1d486-341">Catalogue</span><span class="sxs-lookup"><span data-stu-id="1d486-341">Catalog</span></span>|@Catalog|<span data-ttu-id="1d486-342">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="1d486-342">TABLE_CATALOG</span></span>|<span data-ttu-id="1d486-343">1</span><span class="sxs-lookup"><span data-stu-id="1d486-343">1</span></span>|  
|<span data-ttu-id="1d486-344">Propriétaire</span><span class="sxs-lookup"><span data-stu-id="1d486-344">Owner</span></span>|@Owner|<span data-ttu-id="1d486-345">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="1d486-345">TABLE_SCHEMA</span></span>|<span data-ttu-id="1d486-346">2</span><span class="sxs-lookup"><span data-stu-id="1d486-346">2</span></span>|  
|<span data-ttu-id="1d486-347">Table de charge de travail</span><span class="sxs-lookup"><span data-stu-id="1d486-347">Table</span></span>|@Table|<span data-ttu-id="1d486-348">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="1d486-348">TABLE_NAME</span></span>|<span data-ttu-id="1d486-349">3</span><span class="sxs-lookup"><span data-stu-id="1d486-349">3</span></span>|  
  
### <a name="allcolumns"></a><span data-ttu-id="1d486-350">AllColumns</span><span class="sxs-lookup"><span data-stu-id="1d486-350">AllColumns</span></span>  
  
|<span data-ttu-id="1d486-351">Nom de restriction</span><span class="sxs-lookup"><span data-stu-id="1d486-351">Restriction Name</span></span>|<span data-ttu-id="1d486-352">Nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="1d486-352">Parameter Name</span></span>|<span data-ttu-id="1d486-353">Valeur par défaut de la restriction</span><span class="sxs-lookup"><span data-stu-id="1d486-353">Restriction Default</span></span>|<span data-ttu-id="1d486-354">Numéro de restriction</span><span class="sxs-lookup"><span data-stu-id="1d486-354">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="1d486-355">Catalogue</span><span class="sxs-lookup"><span data-stu-id="1d486-355">Catalog</span></span>|@Catalog|<span data-ttu-id="1d486-356">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="1d486-356">TABLE_CATALOG</span></span>|<span data-ttu-id="1d486-357">1</span><span class="sxs-lookup"><span data-stu-id="1d486-357">1</span></span>|  
|<span data-ttu-id="1d486-358">Propriétaire</span><span class="sxs-lookup"><span data-stu-id="1d486-358">Owner</span></span>|@Owner|<span data-ttu-id="1d486-359">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="1d486-359">TABLE_SCHEMA</span></span>|<span data-ttu-id="1d486-360">2</span><span class="sxs-lookup"><span data-stu-id="1d486-360">2</span></span>|  
|<span data-ttu-id="1d486-361">Table de charge de travail</span><span class="sxs-lookup"><span data-stu-id="1d486-361">Table</span></span>|@Table|<span data-ttu-id="1d486-362">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="1d486-362">TABLE_NAME</span></span>|<span data-ttu-id="1d486-363">3</span><span class="sxs-lookup"><span data-stu-id="1d486-363">3</span></span>|  
|<span data-ttu-id="1d486-364">Colonne</span><span class="sxs-lookup"><span data-stu-id="1d486-364">Column</span></span>|@Column|<span data-ttu-id="1d486-365">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="1d486-365">COLUMN_NAME</span></span>|<span data-ttu-id="1d486-366">4</span><span class="sxs-lookup"><span data-stu-id="1d486-366">4</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="1d486-367">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1d486-367">See also</span></span>

- [<span data-ttu-id="1d486-368">Vue d'ensemble d’ADO.NET</span><span class="sxs-lookup"><span data-stu-id="1d486-368">ADO.NET Overview</span></span>](ado-net-overview.md)
