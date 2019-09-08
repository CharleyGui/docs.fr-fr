---
title: Restrictions de schéma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 73d2980e-e73c-4987-913a-8ddc93d09144
ms.openlocfilehash: d0250e573dc24bfcad97a2f2606cb2e6c8e520da
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70782761"
---
# <a name="schema-restrictions"></a><span data-ttu-id="a3282-102">Restrictions de schéma</span><span class="sxs-lookup"><span data-stu-id="a3282-102">Schema Restrictions</span></span>
<span data-ttu-id="a3282-103">Le deuxième paramètre facultatif de la méthode **GetSchema** correspond aux restrictions utilisées pour limiter la quantité d’informations de schéma retournées, et il est passé à la méthode **GetSchema** sous la forme d’un tableau de chaînes.</span><span class="sxs-lookup"><span data-stu-id="a3282-103">The second optional parameter of the **GetSchema** method is the restrictions that are used to limit the amount of schema information returned, and it is passed to the **GetSchema** method as an array of strings.</span></span> <span data-ttu-id="a3282-104">La position dans le tableau détermine les valeurs que vous pouvez passer et équivaut au numéro de restriction.</span><span class="sxs-lookup"><span data-stu-id="a3282-104">The position in the array determines the values that you can pass, and this is equivalent to the restriction number.</span></span>  
  
 <span data-ttu-id="a3282-105">Par exemple, le tableau suivant décrit les restrictions prises en charge par la collection de schémas « Tables » utilisant le fournisseur de données .NET Framework pour SQL Server.</span><span class="sxs-lookup"><span data-stu-id="a3282-105">For example, the following table describes the restrictions supported by the "Tables" schema collection using the .NET Framework Data Provider for SQL Server.</span></span> <span data-ttu-id="a3282-106">Des restrictions supplémentaires pour les collections de schémas SQL Server figurent à la fin de cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="a3282-106">Additional restrictions for SQL Server schema collections are listed at the end of this topic.</span></span>  
  
|<span data-ttu-id="a3282-107">Nom de restriction</span><span class="sxs-lookup"><span data-stu-id="a3282-107">Restriction Name</span></span>|<span data-ttu-id="a3282-108">nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="a3282-108">Parameter Name</span></span>|<span data-ttu-id="a3282-109">Valeur par défaut de la restriction</span><span class="sxs-lookup"><span data-stu-id="a3282-109">Restriction Default</span></span>|<span data-ttu-id="a3282-110">Numéro de restriction</span><span class="sxs-lookup"><span data-stu-id="a3282-110">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="a3282-111">Catalogue</span><span class="sxs-lookup"><span data-stu-id="a3282-111">Catalog</span></span>|@Catalog|<span data-ttu-id="a3282-112">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="a3282-112">TABLE_CATALOG</span></span>|<span data-ttu-id="a3282-113">1</span><span class="sxs-lookup"><span data-stu-id="a3282-113">1</span></span>|  
|<span data-ttu-id="a3282-114">Propriétaire</span><span class="sxs-lookup"><span data-stu-id="a3282-114">Owner</span></span>|@Owner|<span data-ttu-id="a3282-115">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="a3282-115">TABLE_SCHEMA</span></span>|<span data-ttu-id="a3282-116">2</span><span class="sxs-lookup"><span data-stu-id="a3282-116">2</span></span>|  
|<span data-ttu-id="a3282-117">Table</span><span class="sxs-lookup"><span data-stu-id="a3282-117">Table</span></span>|@Name|<span data-ttu-id="a3282-118">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="a3282-118">TABLE_NAME</span></span>|<span data-ttu-id="a3282-119">3</span><span class="sxs-lookup"><span data-stu-id="a3282-119">3</span></span>|  
|<span data-ttu-id="a3282-120">TableType</span><span class="sxs-lookup"><span data-stu-id="a3282-120">TableType</span></span>|@TableType|<span data-ttu-id="a3282-121">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="a3282-121">TABLE_TYPE</span></span>|<span data-ttu-id="a3282-122">4</span><span class="sxs-lookup"><span data-stu-id="a3282-122">4</span></span>|  
  
## <a name="specifying-restriction-values"></a><span data-ttu-id="a3282-123">Spécification des valeurs de restriction</span><span class="sxs-lookup"><span data-stu-id="a3282-123">Specifying Restriction Values</span></span>  
 <span data-ttu-id="a3282-124">Pour utiliser l’une des restrictions de la collection de schémas « Tables », créez simplement un tableau de chaînes contenant quatre éléments, puis placez une valeur dans l’élément correspondant au numéro de restriction.</span><span class="sxs-lookup"><span data-stu-id="a3282-124">To use one of the restrictions of the "Tables" schema collection, simply create an array of strings with four elements, then place a value in the element that matches the restriction number.</span></span> <span data-ttu-id="a3282-125">Par exemple, pour restreindre les tables retournées par la méthode **GetSchema** aux seules tables du schéma « Sales », définissez le deuxième élément du tableau sur « sales » avant de le passer à la méthode **GetSchema** .</span><span class="sxs-lookup"><span data-stu-id="a3282-125">For example, to restrict the tables returned by the **GetSchema** method to only those tables in the "Sales" schema, set the second element of the array to "Sales" before passing it to the **GetSchema** method.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a3282-126">Les collections de restrictions pour `SqlClient` et `OracleClient` comportent une colonne `ParameterName` supplémentaire.</span><span class="sxs-lookup"><span data-stu-id="a3282-126">The restrictions collections for `SqlClient` and `OracleClient` have an additional `ParameterName` column.</span></span> <span data-ttu-id="a3282-127">La colonne par défaut de la restriction est encore là pour la compatibilité ascendante, mais est désormais ignorée.</span><span class="sxs-lookup"><span data-stu-id="a3282-127">The restriction default column is still there for backwards compatibility, but is currently ignored.</span></span> <span data-ttu-id="a3282-128">Il convient d'utiliser des requêtes paramétrées plutôt qu'un remplacement de chaîne afin de minimiser le risque d'attaque par injection SQL lors de la spécification de valeurs de restriction.</span><span class="sxs-lookup"><span data-stu-id="a3282-128">Parameterized queries rather than string replacement should be used to minimize the risk of an SQL injection attack when specifying restriction values.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a3282-129">Le nombre d'éléments du tableau doit être inférieur ou égal au nombre de restrictions prises en charge pour la collection de schémas spécifiée, sans quoi une exception <xref:System.ArgumentException> est levée.</span><span class="sxs-lookup"><span data-stu-id="a3282-129">The number of elements in the array must be less than or equal to the number of restrictions supported for the specified schema collection else an <xref:System.ArgumentException> will be thrown.</span></span> <span data-ttu-id="a3282-130">Il peut y avoir moins de restrictions que le nombre maximal de restrictions.</span><span class="sxs-lookup"><span data-stu-id="a3282-130">There can be fewer than the maximum number of restrictions.</span></span> <span data-ttu-id="a3282-131">Les restrictions manquantes sont supposées avoir la valeur null (aucune restriction).</span><span class="sxs-lookup"><span data-stu-id="a3282-131">The missing restrictions are assumed to be null (unrestricted).</span></span>  
  
 <span data-ttu-id="a3282-132">Vous pouvez interroger un fournisseur managé .NET Framework pour déterminer la liste des restrictions prises en charge en appelant la méthode **GetSchema** avec le nom de la collection de schémas de restrictions, qui est « restrictions ».</span><span class="sxs-lookup"><span data-stu-id="a3282-132">You can query a .NET Framework managed provider to determine the list of supported restrictions by calling the **GetSchema** method with the name of the restrictions schema collection, which is "Restrictions".</span></span> <span data-ttu-id="a3282-133">Cette opération retourne un <xref:System.Data.DataTable> contenant une liste des noms de collections, des noms de restriction, des valeurs de restriction par défaut et des numéros de restriction.</span><span class="sxs-lookup"><span data-stu-id="a3282-133">This will return a <xref:System.Data.DataTable> with a list of the collection names, the restriction names, the default restriction values, and the restriction numbers.</span></span>  
  
### <a name="example"></a><span data-ttu-id="a3282-134">Exemple</span><span class="sxs-lookup"><span data-stu-id="a3282-134">Example</span></span>  
 <span data-ttu-id="a3282-135">Les exemples suivants montrent comment utiliser la <xref:System.Data.SqlClient.SqlConnection.GetSchema%2A> méthode de la .NET Framework fournisseur de données pour la classe SQL Server <xref:System.Data.SqlClient.SqlConnection> pour récupérer des informations de schéma sur toutes les tables contenues dans l’exemple de base de données **AdventureWorks** , et pour limiter les informations retournées aux seules tables du schéma « Sales » :</span><span class="sxs-lookup"><span data-stu-id="a3282-135">The following examples demonstrate how to use the <xref:System.Data.SqlClient.SqlConnection.GetSchema%2A> method of the .NET Framework Data Provider for the SQL Server <xref:System.Data.SqlClient.SqlConnection> class to retrieve schema information about all of the tables contained in the **AdventureWorks** sample database, and to restrict the information returned to only those tables in the "Sales" schema:</span></span>  
  
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
  
## <a name="sql-server-schema-restrictions"></a><span data-ttu-id="a3282-136">Restrictions de schéma SQL Server</span><span class="sxs-lookup"><span data-stu-id="a3282-136">SQL Server Schema Restrictions</span></span>  
 <span data-ttu-id="a3282-137">Les tableaux suivants énumèrent les restrictions pour les collections de schémas SQL Server.</span><span class="sxs-lookup"><span data-stu-id="a3282-137">The following tables list the restrictions for SQL Server schema collections.</span></span>  
  
### <a name="users"></a><span data-ttu-id="a3282-138">Utilisateurs</span><span class="sxs-lookup"><span data-stu-id="a3282-138">Users</span></span>  
  
|<span data-ttu-id="a3282-139">Nom de restriction</span><span class="sxs-lookup"><span data-stu-id="a3282-139">Restriction Name</span></span>|<span data-ttu-id="a3282-140">nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="a3282-140">Parameter Name</span></span>|<span data-ttu-id="a3282-141">Valeur par défaut de la restriction</span><span class="sxs-lookup"><span data-stu-id="a3282-141">Restriction Default</span></span>|<span data-ttu-id="a3282-142">Numéro de restriction</span><span class="sxs-lookup"><span data-stu-id="a3282-142">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="a3282-143">User_Name</span><span class="sxs-lookup"><span data-stu-id="a3282-143">User_Name</span></span>|@Name|<span data-ttu-id="a3282-144">name</span><span class="sxs-lookup"><span data-stu-id="a3282-144">name</span></span>|<span data-ttu-id="a3282-145">1</span><span class="sxs-lookup"><span data-stu-id="a3282-145">1</span></span>|  
  
### <a name="databases"></a><span data-ttu-id="a3282-146">Bases de données</span><span class="sxs-lookup"><span data-stu-id="a3282-146">Databases</span></span>  
  
|<span data-ttu-id="a3282-147">Nom de restriction</span><span class="sxs-lookup"><span data-stu-id="a3282-147">Restriction Name</span></span>|<span data-ttu-id="a3282-148">nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="a3282-148">Parameter Name</span></span>|<span data-ttu-id="a3282-149">Valeur par défaut de la restriction</span><span class="sxs-lookup"><span data-stu-id="a3282-149">Restriction Default</span></span>|<span data-ttu-id="a3282-150">Numéro de restriction</span><span class="sxs-lookup"><span data-stu-id="a3282-150">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="a3282-151">Name</span><span class="sxs-lookup"><span data-stu-id="a3282-151">Name</span></span>|@Name|<span data-ttu-id="a3282-152">Name</span><span class="sxs-lookup"><span data-stu-id="a3282-152">Name</span></span>|<span data-ttu-id="a3282-153">1</span><span class="sxs-lookup"><span data-stu-id="a3282-153">1</span></span>|  
  
### <a name="tables"></a><span data-ttu-id="a3282-154">Tables</span><span class="sxs-lookup"><span data-stu-id="a3282-154">Tables</span></span>  
  
|<span data-ttu-id="a3282-155">Nom de restriction</span><span class="sxs-lookup"><span data-stu-id="a3282-155">Restriction Name</span></span>|<span data-ttu-id="a3282-156">nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="a3282-156">Parameter Name</span></span>|<span data-ttu-id="a3282-157">Valeur par défaut de la restriction</span><span class="sxs-lookup"><span data-stu-id="a3282-157">Restriction Default</span></span>|<span data-ttu-id="a3282-158">Numéro de restriction</span><span class="sxs-lookup"><span data-stu-id="a3282-158">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="a3282-159">Catalogue</span><span class="sxs-lookup"><span data-stu-id="a3282-159">Catalog</span></span>|@Catalog|<span data-ttu-id="a3282-160">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="a3282-160">TABLE_CATALOG</span></span>|<span data-ttu-id="a3282-161">1</span><span class="sxs-lookup"><span data-stu-id="a3282-161">1</span></span>|  
|<span data-ttu-id="a3282-162">Propriétaire</span><span class="sxs-lookup"><span data-stu-id="a3282-162">Owner</span></span>|@Owner|<span data-ttu-id="a3282-163">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="a3282-163">TABLE_SCHEMA</span></span>|<span data-ttu-id="a3282-164">2</span><span class="sxs-lookup"><span data-stu-id="a3282-164">2</span></span>|  
|<span data-ttu-id="a3282-165">Table</span><span class="sxs-lookup"><span data-stu-id="a3282-165">Table</span></span>|@Name|<span data-ttu-id="a3282-166">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="a3282-166">TABLE_NAME</span></span>|<span data-ttu-id="a3282-167">3</span><span class="sxs-lookup"><span data-stu-id="a3282-167">3</span></span>|  
|<span data-ttu-id="a3282-168">TableType</span><span class="sxs-lookup"><span data-stu-id="a3282-168">TableType</span></span>|@TableType|<span data-ttu-id="a3282-169">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="a3282-169">TABLE_TYPE</span></span>|<span data-ttu-id="a3282-170">4</span><span class="sxs-lookup"><span data-stu-id="a3282-170">4</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="a3282-171">Colonnes</span><span class="sxs-lookup"><span data-stu-id="a3282-171">Columns</span></span>  
  
|<span data-ttu-id="a3282-172">Nom de restriction</span><span class="sxs-lookup"><span data-stu-id="a3282-172">Restriction Name</span></span>|<span data-ttu-id="a3282-173">nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="a3282-173">Parameter Name</span></span>|<span data-ttu-id="a3282-174">Valeur par défaut de la restriction</span><span class="sxs-lookup"><span data-stu-id="a3282-174">Restriction Default</span></span>|<span data-ttu-id="a3282-175">Numéro de restriction</span><span class="sxs-lookup"><span data-stu-id="a3282-175">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="a3282-176">Catalogue</span><span class="sxs-lookup"><span data-stu-id="a3282-176">Catalog</span></span>|@Catalog|<span data-ttu-id="a3282-177">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="a3282-177">TABLE_CATALOG</span></span>|<span data-ttu-id="a3282-178">1</span><span class="sxs-lookup"><span data-stu-id="a3282-178">1</span></span>|  
|<span data-ttu-id="a3282-179">Propriétaire</span><span class="sxs-lookup"><span data-stu-id="a3282-179">Owner</span></span>|@Owner|<span data-ttu-id="a3282-180">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="a3282-180">TABLE_SCHEMA</span></span>|<span data-ttu-id="a3282-181">2</span><span class="sxs-lookup"><span data-stu-id="a3282-181">2</span></span>|  
|<span data-ttu-id="a3282-182">Table</span><span class="sxs-lookup"><span data-stu-id="a3282-182">Table</span></span>|@Table|<span data-ttu-id="a3282-183">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="a3282-183">TABLE_NAME</span></span>|<span data-ttu-id="a3282-184">3</span><span class="sxs-lookup"><span data-stu-id="a3282-184">3</span></span>|  
|<span data-ttu-id="a3282-185">Colonne</span><span class="sxs-lookup"><span data-stu-id="a3282-185">Column</span></span>|@Column|<span data-ttu-id="a3282-186">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="a3282-186">COLUMN_NAME</span></span>|<span data-ttu-id="a3282-187">4</span><span class="sxs-lookup"><span data-stu-id="a3282-187">4</span></span>|  
  
### <a name="structuredtypemembers"></a><span data-ttu-id="a3282-188">StructuredTypeMembers</span><span class="sxs-lookup"><span data-stu-id="a3282-188">StructuredTypeMembers</span></span>  
  
|<span data-ttu-id="a3282-189">Nom de restriction</span><span class="sxs-lookup"><span data-stu-id="a3282-189">Restriction Name</span></span>|<span data-ttu-id="a3282-190">nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="a3282-190">Parameter Name</span></span>|<span data-ttu-id="a3282-191">Valeur par défaut de la restriction</span><span class="sxs-lookup"><span data-stu-id="a3282-191">Restriction Default</span></span>|<span data-ttu-id="a3282-192">Numéro de restriction</span><span class="sxs-lookup"><span data-stu-id="a3282-192">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="a3282-193">Catalogue</span><span class="sxs-lookup"><span data-stu-id="a3282-193">Catalog</span></span>|@Catalog|<span data-ttu-id="a3282-194">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="a3282-194">TABLE_CATALOG</span></span>|<span data-ttu-id="a3282-195">1</span><span class="sxs-lookup"><span data-stu-id="a3282-195">1</span></span>|  
|<span data-ttu-id="a3282-196">Propriétaire</span><span class="sxs-lookup"><span data-stu-id="a3282-196">Owner</span></span>|@Owner|<span data-ttu-id="a3282-197">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="a3282-197">TABLE_SCHEMA</span></span>|<span data-ttu-id="a3282-198">2</span><span class="sxs-lookup"><span data-stu-id="a3282-198">2</span></span>|  
|<span data-ttu-id="a3282-199">Table</span><span class="sxs-lookup"><span data-stu-id="a3282-199">Table</span></span>|@Table|<span data-ttu-id="a3282-200">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="a3282-200">TABLE_NAME</span></span>|<span data-ttu-id="a3282-201">3</span><span class="sxs-lookup"><span data-stu-id="a3282-201">3</span></span>|  
|<span data-ttu-id="a3282-202">Colonne</span><span class="sxs-lookup"><span data-stu-id="a3282-202">Column</span></span>|@Column|<span data-ttu-id="a3282-203">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="a3282-203">COLUMN_NAME</span></span>|<span data-ttu-id="a3282-204">4</span><span class="sxs-lookup"><span data-stu-id="a3282-204">4</span></span>|  
  
### <a name="views"></a><span data-ttu-id="a3282-205">Affichages</span><span class="sxs-lookup"><span data-stu-id="a3282-205">Views</span></span>  
  
|<span data-ttu-id="a3282-206">Nom de restriction</span><span class="sxs-lookup"><span data-stu-id="a3282-206">Restriction Name</span></span>|<span data-ttu-id="a3282-207">nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="a3282-207">Parameter Name</span></span>|<span data-ttu-id="a3282-208">Valeur par défaut de la restriction</span><span class="sxs-lookup"><span data-stu-id="a3282-208">Restriction Default</span></span>|<span data-ttu-id="a3282-209">Numéro de restriction</span><span class="sxs-lookup"><span data-stu-id="a3282-209">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="a3282-210">Catalogue</span><span class="sxs-lookup"><span data-stu-id="a3282-210">Catalog</span></span>|@Catalog|<span data-ttu-id="a3282-211">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="a3282-211">TABLE_CATALOG</span></span>|<span data-ttu-id="a3282-212">1</span><span class="sxs-lookup"><span data-stu-id="a3282-212">1</span></span>|  
|<span data-ttu-id="a3282-213">Propriétaire</span><span class="sxs-lookup"><span data-stu-id="a3282-213">Owner</span></span>|@Owner|<span data-ttu-id="a3282-214">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="a3282-214">TABLE_SCHEMA</span></span>|<span data-ttu-id="a3282-215">2</span><span class="sxs-lookup"><span data-stu-id="a3282-215">2</span></span>|  
|<span data-ttu-id="a3282-216">Table</span><span class="sxs-lookup"><span data-stu-id="a3282-216">Table</span></span>|@Table|<span data-ttu-id="a3282-217">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="a3282-217">TABLE_NAME</span></span>|<span data-ttu-id="a3282-218">3</span><span class="sxs-lookup"><span data-stu-id="a3282-218">3</span></span>|  
  
### <a name="viewcolumns"></a><span data-ttu-id="a3282-219">ViewColumns</span><span class="sxs-lookup"><span data-stu-id="a3282-219">ViewColumns</span></span>  
  
|<span data-ttu-id="a3282-220">Nom de restriction</span><span class="sxs-lookup"><span data-stu-id="a3282-220">Restriction Name</span></span>|<span data-ttu-id="a3282-221">nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="a3282-221">Parameter Name</span></span>|<span data-ttu-id="a3282-222">Valeur par défaut de la restriction</span><span class="sxs-lookup"><span data-stu-id="a3282-222">Restriction Default</span></span>|<span data-ttu-id="a3282-223">Numéro de restriction</span><span class="sxs-lookup"><span data-stu-id="a3282-223">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="a3282-224">Catalogue</span><span class="sxs-lookup"><span data-stu-id="a3282-224">Catalog</span></span>|@Catalog|<span data-ttu-id="a3282-225">VIEW_CATALOG</span><span class="sxs-lookup"><span data-stu-id="a3282-225">VIEW_CATALOG</span></span>|<span data-ttu-id="a3282-226">1</span><span class="sxs-lookup"><span data-stu-id="a3282-226">1</span></span>|  
|<span data-ttu-id="a3282-227">Propriétaire</span><span class="sxs-lookup"><span data-stu-id="a3282-227">Owner</span></span>|@Owner|<span data-ttu-id="a3282-228">VIEW_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="a3282-228">VIEW_SCHEMA</span></span>|<span data-ttu-id="a3282-229">2</span><span class="sxs-lookup"><span data-stu-id="a3282-229">2</span></span>|  
|<span data-ttu-id="a3282-230">Table</span><span class="sxs-lookup"><span data-stu-id="a3282-230">Table</span></span>|@Table|<span data-ttu-id="a3282-231">VIEW_NAME</span><span class="sxs-lookup"><span data-stu-id="a3282-231">VIEW_NAME</span></span>|<span data-ttu-id="a3282-232">3</span><span class="sxs-lookup"><span data-stu-id="a3282-232">3</span></span>|  
|<span data-ttu-id="a3282-233">Colonne</span><span class="sxs-lookup"><span data-stu-id="a3282-233">Column</span></span>|@Column|<span data-ttu-id="a3282-234">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="a3282-234">COLUMN_NAME</span></span>|<span data-ttu-id="a3282-235">4</span><span class="sxs-lookup"><span data-stu-id="a3282-235">4</span></span>|  
  
### <a name="procedureparameters"></a><span data-ttu-id="a3282-236">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="a3282-236">ProcedureParameters</span></span>  
  
|<span data-ttu-id="a3282-237">Nom de restriction</span><span class="sxs-lookup"><span data-stu-id="a3282-237">Restriction Name</span></span>|<span data-ttu-id="a3282-238">nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="a3282-238">Parameter Name</span></span>|<span data-ttu-id="a3282-239">Valeur par défaut de la restriction</span><span class="sxs-lookup"><span data-stu-id="a3282-239">Restriction Default</span></span>|<span data-ttu-id="a3282-240">Numéro de restriction</span><span class="sxs-lookup"><span data-stu-id="a3282-240">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="a3282-241">Catalogue</span><span class="sxs-lookup"><span data-stu-id="a3282-241">Catalog</span></span>|@Catalog|<span data-ttu-id="a3282-242">SPECIFIC_CATALOG</span><span class="sxs-lookup"><span data-stu-id="a3282-242">SPECIFIC_CATALOG</span></span>|<span data-ttu-id="a3282-243">1</span><span class="sxs-lookup"><span data-stu-id="a3282-243">1</span></span>|  
|<span data-ttu-id="a3282-244">Propriétaire</span><span class="sxs-lookup"><span data-stu-id="a3282-244">Owner</span></span>|@Owner|<span data-ttu-id="a3282-245">SPECIFIC_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="a3282-245">SPECIFIC_SCHEMA</span></span>|<span data-ttu-id="a3282-246">2</span><span class="sxs-lookup"><span data-stu-id="a3282-246">2</span></span>|  
|<span data-ttu-id="a3282-247">Name</span><span class="sxs-lookup"><span data-stu-id="a3282-247">Name</span></span>|@Name|<span data-ttu-id="a3282-248">SPECIFIC_NAME</span><span class="sxs-lookup"><span data-stu-id="a3282-248">SPECIFIC_NAME</span></span>|<span data-ttu-id="a3282-249">3</span><span class="sxs-lookup"><span data-stu-id="a3282-249">3</span></span>|  
|<span data-ttu-id="a3282-250">Paramètre</span><span class="sxs-lookup"><span data-stu-id="a3282-250">Parameter</span></span>|@Parameter|<span data-ttu-id="a3282-251">PARAMETER_NAME</span><span class="sxs-lookup"><span data-stu-id="a3282-251">PARAMETER_NAME</span></span>|<span data-ttu-id="a3282-252">4</span><span class="sxs-lookup"><span data-stu-id="a3282-252">4</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="a3282-253">Procédures</span><span class="sxs-lookup"><span data-stu-id="a3282-253">Procedures</span></span>  
  
|<span data-ttu-id="a3282-254">Nom de restriction</span><span class="sxs-lookup"><span data-stu-id="a3282-254">Restriction Name</span></span>|<span data-ttu-id="a3282-255">nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="a3282-255">Parameter Name</span></span>|<span data-ttu-id="a3282-256">Valeur par défaut de la restriction</span><span class="sxs-lookup"><span data-stu-id="a3282-256">Restriction Default</span></span>|<span data-ttu-id="a3282-257">Numéro de restriction</span><span class="sxs-lookup"><span data-stu-id="a3282-257">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="a3282-258">Catalogue</span><span class="sxs-lookup"><span data-stu-id="a3282-258">Catalog</span></span>|@Catalog|<span data-ttu-id="a3282-259">SPECIFIC_CATALOG</span><span class="sxs-lookup"><span data-stu-id="a3282-259">SPECIFIC_CATALOG</span></span>|<span data-ttu-id="a3282-260">1</span><span class="sxs-lookup"><span data-stu-id="a3282-260">1</span></span>|  
|<span data-ttu-id="a3282-261">Propriétaire</span><span class="sxs-lookup"><span data-stu-id="a3282-261">Owner</span></span>|@Owner|<span data-ttu-id="a3282-262">SPECIFIC_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="a3282-262">SPECIFIC_SCHEMA</span></span>|<span data-ttu-id="a3282-263">2</span><span class="sxs-lookup"><span data-stu-id="a3282-263">2</span></span>|  
|<span data-ttu-id="a3282-264">Name</span><span class="sxs-lookup"><span data-stu-id="a3282-264">Name</span></span>|@Name|<span data-ttu-id="a3282-265">SPECIFIC_NAME</span><span class="sxs-lookup"><span data-stu-id="a3282-265">SPECIFIC_NAME</span></span>|<span data-ttu-id="a3282-266">3</span><span class="sxs-lookup"><span data-stu-id="a3282-266">3</span></span>|  
|<span data-ttu-id="a3282-267">Type</span><span class="sxs-lookup"><span data-stu-id="a3282-267">Type</span></span>|@Type|<span data-ttu-id="a3282-268">ROUTINE_TYPE</span><span class="sxs-lookup"><span data-stu-id="a3282-268">ROUTINE_TYPE</span></span>|<span data-ttu-id="a3282-269">4</span><span class="sxs-lookup"><span data-stu-id="a3282-269">4</span></span>|  
  
### <a name="indexcolumns"></a><span data-ttu-id="a3282-270">IndexColumns</span><span class="sxs-lookup"><span data-stu-id="a3282-270">IndexColumns</span></span>  
  
|<span data-ttu-id="a3282-271">Nom de restriction</span><span class="sxs-lookup"><span data-stu-id="a3282-271">Restriction Name</span></span>|<span data-ttu-id="a3282-272">nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="a3282-272">Parameter Name</span></span>|<span data-ttu-id="a3282-273">Valeur par défaut de la restriction</span><span class="sxs-lookup"><span data-stu-id="a3282-273">Restriction Default</span></span>|<span data-ttu-id="a3282-274">Numéro de restriction</span><span class="sxs-lookup"><span data-stu-id="a3282-274">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="a3282-275">Catalogue</span><span class="sxs-lookup"><span data-stu-id="a3282-275">Catalog</span></span>|@Catalog|<span data-ttu-id="a3282-276">db_name()</span><span class="sxs-lookup"><span data-stu-id="a3282-276">db_name()</span></span>|<span data-ttu-id="a3282-277">1</span><span class="sxs-lookup"><span data-stu-id="a3282-277">1</span></span>|  
|<span data-ttu-id="a3282-278">Propriétaire</span><span class="sxs-lookup"><span data-stu-id="a3282-278">Owner</span></span>|@Owner|<span data-ttu-id="a3282-279">user_name()</span><span class="sxs-lookup"><span data-stu-id="a3282-279">user_name()</span></span>|<span data-ttu-id="a3282-280">2</span><span class="sxs-lookup"><span data-stu-id="a3282-280">2</span></span>|  
|<span data-ttu-id="a3282-281">Table</span><span class="sxs-lookup"><span data-stu-id="a3282-281">Table</span></span>|@Table|<span data-ttu-id="a3282-282">o.name</span><span class="sxs-lookup"><span data-stu-id="a3282-282">o.name</span></span>|<span data-ttu-id="a3282-283">3</span><span class="sxs-lookup"><span data-stu-id="a3282-283">3</span></span>|  
|<span data-ttu-id="a3282-284">ConstraintName</span><span class="sxs-lookup"><span data-stu-id="a3282-284">ConstraintName</span></span>|@ConstraintName|<span data-ttu-id="a3282-285">x.name</span><span class="sxs-lookup"><span data-stu-id="a3282-285">x.name</span></span>|<span data-ttu-id="a3282-286">4</span><span class="sxs-lookup"><span data-stu-id="a3282-286">4</span></span>|  
|<span data-ttu-id="a3282-287">Colonne</span><span class="sxs-lookup"><span data-stu-id="a3282-287">Column</span></span>|@Column|<span data-ttu-id="a3282-288">c.name</span><span class="sxs-lookup"><span data-stu-id="a3282-288">c.name</span></span>|<span data-ttu-id="a3282-289">5\.</span><span class="sxs-lookup"><span data-stu-id="a3282-289">5</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="a3282-290">Index</span><span class="sxs-lookup"><span data-stu-id="a3282-290">Indexes</span></span>  
  
|<span data-ttu-id="a3282-291">Nom de restriction</span><span class="sxs-lookup"><span data-stu-id="a3282-291">Restriction Name</span></span>|<span data-ttu-id="a3282-292">nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="a3282-292">Parameter Name</span></span>|<span data-ttu-id="a3282-293">Valeur par défaut de la restriction</span><span class="sxs-lookup"><span data-stu-id="a3282-293">Restriction Default</span></span>|<span data-ttu-id="a3282-294">Numéro de restriction</span><span class="sxs-lookup"><span data-stu-id="a3282-294">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="a3282-295">Catalogue</span><span class="sxs-lookup"><span data-stu-id="a3282-295">Catalog</span></span>|@Catalog|<span data-ttu-id="a3282-296">db_name()</span><span class="sxs-lookup"><span data-stu-id="a3282-296">db_name()</span></span>|<span data-ttu-id="a3282-297">1</span><span class="sxs-lookup"><span data-stu-id="a3282-297">1</span></span>|  
|<span data-ttu-id="a3282-298">Propriétaire</span><span class="sxs-lookup"><span data-stu-id="a3282-298">Owner</span></span>|@Owner|<span data-ttu-id="a3282-299">user_name()</span><span class="sxs-lookup"><span data-stu-id="a3282-299">user_name()</span></span>|<span data-ttu-id="a3282-300">2</span><span class="sxs-lookup"><span data-stu-id="a3282-300">2</span></span>|  
|<span data-ttu-id="a3282-301">Table</span><span class="sxs-lookup"><span data-stu-id="a3282-301">Table</span></span>|@Table|<span data-ttu-id="a3282-302">o.name</span><span class="sxs-lookup"><span data-stu-id="a3282-302">o.name</span></span>|<span data-ttu-id="a3282-303">3</span><span class="sxs-lookup"><span data-stu-id="a3282-303">3</span></span>|  
  
### <a name="userdefinedtypes"></a><span data-ttu-id="a3282-304">UserDefinedTypes</span><span class="sxs-lookup"><span data-stu-id="a3282-304">UserDefinedTypes</span></span>  
  
|<span data-ttu-id="a3282-305">Nom de restriction</span><span class="sxs-lookup"><span data-stu-id="a3282-305">Restriction Name</span></span>|<span data-ttu-id="a3282-306">nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="a3282-306">Parameter Name</span></span>|<span data-ttu-id="a3282-307">Valeur par défaut de la restriction</span><span class="sxs-lookup"><span data-stu-id="a3282-307">Restriction Default</span></span>|<span data-ttu-id="a3282-308">Numéro de restriction</span><span class="sxs-lookup"><span data-stu-id="a3282-308">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="a3282-309">assembly_name</span><span class="sxs-lookup"><span data-stu-id="a3282-309">assembly_name</span></span>|@AssemblyName|<span data-ttu-id="a3282-310">assemblies.name</span><span class="sxs-lookup"><span data-stu-id="a3282-310">assemblies.name</span></span>|<span data-ttu-id="a3282-311">1</span><span class="sxs-lookup"><span data-stu-id="a3282-311">1</span></span>|  
|<span data-ttu-id="a3282-312">udt_name</span><span class="sxs-lookup"><span data-stu-id="a3282-312">udt_name</span></span>|@UDTName|<span data-ttu-id="a3282-313">types.assembly_class</span><span class="sxs-lookup"><span data-stu-id="a3282-313">types.assembly_class</span></span>|<span data-ttu-id="a3282-314">2</span><span class="sxs-lookup"><span data-stu-id="a3282-314">2</span></span>|  
  
### <a name="foreignkeys"></a><span data-ttu-id="a3282-315">ForeignKeys</span><span class="sxs-lookup"><span data-stu-id="a3282-315">ForeignKeys</span></span>  
  
|<span data-ttu-id="a3282-316">Nom de restriction</span><span class="sxs-lookup"><span data-stu-id="a3282-316">Restriction Name</span></span>|<span data-ttu-id="a3282-317">nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="a3282-317">Parameter Name</span></span>|<span data-ttu-id="a3282-318">Valeur par défaut de la restriction</span><span class="sxs-lookup"><span data-stu-id="a3282-318">Restriction Default</span></span>|<span data-ttu-id="a3282-319">Numéro de restriction</span><span class="sxs-lookup"><span data-stu-id="a3282-319">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="a3282-320">Catalogue</span><span class="sxs-lookup"><span data-stu-id="a3282-320">Catalog</span></span>|@Catalog|<span data-ttu-id="a3282-321">CONSTRAINT_CATALOG</span><span class="sxs-lookup"><span data-stu-id="a3282-321">CONSTRAINT_CATALOG</span></span>|<span data-ttu-id="a3282-322">1</span><span class="sxs-lookup"><span data-stu-id="a3282-322">1</span></span>|  
|<span data-ttu-id="a3282-323">Propriétaire</span><span class="sxs-lookup"><span data-stu-id="a3282-323">Owner</span></span>|@Owner|<span data-ttu-id="a3282-324">CONSTRAINT_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="a3282-324">CONSTRAINT_SCHEMA</span></span>|<span data-ttu-id="a3282-325">2</span><span class="sxs-lookup"><span data-stu-id="a3282-325">2</span></span>|  
|<span data-ttu-id="a3282-326">Table</span><span class="sxs-lookup"><span data-stu-id="a3282-326">Table</span></span>|@Table|<span data-ttu-id="a3282-327">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="a3282-327">TABLE_NAME</span></span>|<span data-ttu-id="a3282-328">3</span><span class="sxs-lookup"><span data-stu-id="a3282-328">3</span></span>|  
|<span data-ttu-id="a3282-329">Nom</span><span class="sxs-lookup"><span data-stu-id="a3282-329">Name</span></span>|@Name|<span data-ttu-id="a3282-330">CONSTRAINT_NAME</span><span class="sxs-lookup"><span data-stu-id="a3282-330">CONSTRAINT_NAME</span></span>|<span data-ttu-id="a3282-331">4</span><span class="sxs-lookup"><span data-stu-id="a3282-331">4</span></span>|  
  
## <a name="sql-server-2008-schema-restrictions"></a><span data-ttu-id="a3282-332">Restrictions de schéma SQL Server 2008</span><span class="sxs-lookup"><span data-stu-id="a3282-332">SQL Server 2008 Schema Restrictions</span></span>  
 <span data-ttu-id="a3282-333">Les tableaux suivants répertorient les restrictions pour les collections de schémas SQL Server 2008.</span><span class="sxs-lookup"><span data-stu-id="a3282-333">The following tables list the restrictions for SQL Server 2008 schema collections.</span></span> <span data-ttu-id="a3282-334">Ces restrictions s'appliquent à partir de la version 3.5 SP1 de .NET Framework et SQL Server 2008.</span><span class="sxs-lookup"><span data-stu-id="a3282-334">These restrictions are valid beginning with version 3.5 SP1 of the .NET Framework and SQL Server 2008.</span></span> <span data-ttu-id="a3282-335">Elles ne sont pas prises en charge dans les versions précédentes de .NET Framework et SQL Server.</span><span class="sxs-lookup"><span data-stu-id="a3282-335">They are not supported in earlier versions of the .NET Framework and SQL Server.</span></span>  
  
### <a name="columnsetcolumns"></a><span data-ttu-id="a3282-336">ColumnSetColumns</span><span class="sxs-lookup"><span data-stu-id="a3282-336">ColumnSetColumns</span></span>  
  
|<span data-ttu-id="a3282-337">Nom de restriction</span><span class="sxs-lookup"><span data-stu-id="a3282-337">Restriction Name</span></span>|<span data-ttu-id="a3282-338">nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="a3282-338">Parameter Name</span></span>|<span data-ttu-id="a3282-339">Valeur par défaut de la restriction</span><span class="sxs-lookup"><span data-stu-id="a3282-339">Restriction Default</span></span>|<span data-ttu-id="a3282-340">Numéro de restriction</span><span class="sxs-lookup"><span data-stu-id="a3282-340">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="a3282-341">Catalogue</span><span class="sxs-lookup"><span data-stu-id="a3282-341">Catalog</span></span>|@Catalog|<span data-ttu-id="a3282-342">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="a3282-342">TABLE_CATALOG</span></span>|<span data-ttu-id="a3282-343">1</span><span class="sxs-lookup"><span data-stu-id="a3282-343">1</span></span>|  
|<span data-ttu-id="a3282-344">Propriétaire</span><span class="sxs-lookup"><span data-stu-id="a3282-344">Owner</span></span>|@Owner|<span data-ttu-id="a3282-345">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="a3282-345">TABLE_SCHEMA</span></span>|<span data-ttu-id="a3282-346">2</span><span class="sxs-lookup"><span data-stu-id="a3282-346">2</span></span>|  
|<span data-ttu-id="a3282-347">Table</span><span class="sxs-lookup"><span data-stu-id="a3282-347">Table</span></span>|@Table|<span data-ttu-id="a3282-348">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="a3282-348">TABLE_NAME</span></span>|<span data-ttu-id="a3282-349">3</span><span class="sxs-lookup"><span data-stu-id="a3282-349">3</span></span>|  
  
### <a name="allcolumns"></a><span data-ttu-id="a3282-350">AllColumns</span><span class="sxs-lookup"><span data-stu-id="a3282-350">AllColumns</span></span>  
  
|<span data-ttu-id="a3282-351">Nom de restriction</span><span class="sxs-lookup"><span data-stu-id="a3282-351">Restriction Name</span></span>|<span data-ttu-id="a3282-352">nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="a3282-352">Parameter Name</span></span>|<span data-ttu-id="a3282-353">Valeur par défaut de la restriction</span><span class="sxs-lookup"><span data-stu-id="a3282-353">Restriction Default</span></span>|<span data-ttu-id="a3282-354">Numéro de restriction</span><span class="sxs-lookup"><span data-stu-id="a3282-354">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="a3282-355">Catalogue</span><span class="sxs-lookup"><span data-stu-id="a3282-355">Catalog</span></span>|@Catalog|<span data-ttu-id="a3282-356">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="a3282-356">TABLE_CATALOG</span></span>|<span data-ttu-id="a3282-357">1</span><span class="sxs-lookup"><span data-stu-id="a3282-357">1</span></span>|  
|<span data-ttu-id="a3282-358">Propriétaire</span><span class="sxs-lookup"><span data-stu-id="a3282-358">Owner</span></span>|@Owner|<span data-ttu-id="a3282-359">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="a3282-359">TABLE_SCHEMA</span></span>|<span data-ttu-id="a3282-360">2</span><span class="sxs-lookup"><span data-stu-id="a3282-360">2</span></span>|  
|<span data-ttu-id="a3282-361">Table</span><span class="sxs-lookup"><span data-stu-id="a3282-361">Table</span></span>|@Table|<span data-ttu-id="a3282-362">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="a3282-362">TABLE_NAME</span></span>|<span data-ttu-id="a3282-363">3</span><span class="sxs-lookup"><span data-stu-id="a3282-363">3</span></span>|  
|<span data-ttu-id="a3282-364">Colonne</span><span class="sxs-lookup"><span data-stu-id="a3282-364">Column</span></span>|@Column|<span data-ttu-id="a3282-365">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="a3282-365">COLUMN_NAME</span></span>|<span data-ttu-id="a3282-366">4</span><span class="sxs-lookup"><span data-stu-id="a3282-366">4</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a3282-367">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a3282-367">See also</span></span>

- [<span data-ttu-id="a3282-368">Vue d’ensemble d’ADO.NET</span><span class="sxs-lookup"><span data-stu-id="a3282-368">ADO.NET Overview</span></span>](ado-net-overview.md)
