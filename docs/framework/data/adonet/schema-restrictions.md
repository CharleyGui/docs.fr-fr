---
title: Restrictions de schéma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 73d2980e-e73c-4987-913a-8ddc93d09144
ms.openlocfilehash: 17c42c5131252993d1f16e4a2f7a6450f0984d11
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79149009"
---
# <a name="schema-restrictions"></a><span data-ttu-id="80740-102">Restrictions de schéma</span><span class="sxs-lookup"><span data-stu-id="80740-102">Schema Restrictions</span></span>
<span data-ttu-id="80740-103">Le deuxième paramètre facultatif de la méthode **GetSchema** est les restrictions qui sont utilisées pour limiter la quantité d’informations schéma retournées, et il est transmis à la méthode **GetSchema** comme un tableau de cordes.</span><span class="sxs-lookup"><span data-stu-id="80740-103">The second optional parameter of the **GetSchema** method is the restrictions that are used to limit the amount of schema information returned, and it is passed to the **GetSchema** method as an array of strings.</span></span> <span data-ttu-id="80740-104">La position dans le tableau détermine les valeurs que vous pouvez passer et équivaut au numéro de restriction.</span><span class="sxs-lookup"><span data-stu-id="80740-104">The position in the array determines the values that you can pass, and this is equivalent to the restriction number.</span></span>  
  
 <span data-ttu-id="80740-105">Par exemple, le tableau suivant décrit les restrictions prises en charge par la collection de schémas « Tables » utilisant le fournisseur de données .NET Framework pour SQL Server.</span><span class="sxs-lookup"><span data-stu-id="80740-105">For example, the following table describes the restrictions supported by the "Tables" schema collection using the .NET Framework Data Provider for SQL Server.</span></span> <span data-ttu-id="80740-106">Des restrictions supplémentaires pour les collections de schémas SQL Server figurent à la fin de cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="80740-106">Additional restrictions for SQL Server schema collections are listed at the end of this topic.</span></span>  
  
|<span data-ttu-id="80740-107">Nom de restriction</span><span class="sxs-lookup"><span data-stu-id="80740-107">Restriction Name</span></span>|<span data-ttu-id="80740-108">Nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="80740-108">Parameter Name</span></span>|<span data-ttu-id="80740-109">Valeur par défaut de la restriction</span><span class="sxs-lookup"><span data-stu-id="80740-109">Restriction Default</span></span>|<span data-ttu-id="80740-110">Numéro de restriction</span><span class="sxs-lookup"><span data-stu-id="80740-110">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="80740-111">Catalogue</span><span class="sxs-lookup"><span data-stu-id="80740-111">Catalog</span></span>|@Catalog|<span data-ttu-id="80740-112">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="80740-112">TABLE_CATALOG</span></span>|<span data-ttu-id="80740-113">1</span><span class="sxs-lookup"><span data-stu-id="80740-113">1</span></span>|  
|<span data-ttu-id="80740-114">Propriétaire</span><span class="sxs-lookup"><span data-stu-id="80740-114">Owner</span></span>|@Owner|<span data-ttu-id="80740-115">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="80740-115">TABLE_SCHEMA</span></span>|<span data-ttu-id="80740-116">2</span><span class="sxs-lookup"><span data-stu-id="80740-116">2</span></span>|  
|<span data-ttu-id="80740-117">Table de charge de travail</span><span class="sxs-lookup"><span data-stu-id="80740-117">Table</span></span>|@Name|<span data-ttu-id="80740-118">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="80740-118">TABLE_NAME</span></span>|<span data-ttu-id="80740-119">3</span><span class="sxs-lookup"><span data-stu-id="80740-119">3</span></span>|  
|<span data-ttu-id="80740-120">TableType</span><span class="sxs-lookup"><span data-stu-id="80740-120">TableType</span></span>|@TableType|<span data-ttu-id="80740-121">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="80740-121">TABLE_TYPE</span></span>|<span data-ttu-id="80740-122">4</span><span class="sxs-lookup"><span data-stu-id="80740-122">4</span></span>|  
  
## <a name="specifying-restriction-values"></a><span data-ttu-id="80740-123">Spécification des valeurs de restriction</span><span class="sxs-lookup"><span data-stu-id="80740-123">Specifying Restriction Values</span></span>  
 <span data-ttu-id="80740-124">Pour utiliser l’une des restrictions de la collection de schémas « Tables », créez simplement un tableau de chaînes contenant quatre éléments, puis placez une valeur dans l’élément correspondant au numéro de restriction.</span><span class="sxs-lookup"><span data-stu-id="80740-124">To use one of the restrictions of the "Tables" schema collection, simply create an array of strings with four elements, then place a value in the element that matches the restriction number.</span></span> <span data-ttu-id="80740-125">Par exemple, limiter les tables retournées par la méthode **GetSchema** à seulement les tables du schéma "Sales", définissez le deuxième élément du tableau à "Sales" avant de le transmettre à la méthode **GetSchema.**</span><span class="sxs-lookup"><span data-stu-id="80740-125">For example, to restrict the tables returned by the **GetSchema** method to only those tables in the "Sales" schema, set the second element of the array to "Sales" before passing it to the **GetSchema** method.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="80740-126">Les collections de restrictions pour `SqlClient` et `OracleClient` comportent une colonne `ParameterName` supplémentaire.</span><span class="sxs-lookup"><span data-stu-id="80740-126">The restrictions collections for `SqlClient` and `OracleClient` have an additional `ParameterName` column.</span></span> <span data-ttu-id="80740-127">La colonne par défaut de la restriction est encore là pour la compatibilité ascendante, mais est désormais ignorée.</span><span class="sxs-lookup"><span data-stu-id="80740-127">The restriction default column is still there for backwards compatibility, but is currently ignored.</span></span> <span data-ttu-id="80740-128">Il convient d'utiliser des requêtes paramétrées plutôt qu'un remplacement de chaîne afin de minimiser le risque d'attaque par injection SQL lors de la spécification de valeurs de restriction.</span><span class="sxs-lookup"><span data-stu-id="80740-128">Parameterized queries rather than string replacement should be used to minimize the risk of an SQL injection attack when specifying restriction values.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="80740-129">Le nombre d'éléments du tableau doit être inférieur ou égal au nombre de restrictions prises en charge pour la collection de schémas spécifiée, sans quoi une exception <xref:System.ArgumentException> est levée.</span><span class="sxs-lookup"><span data-stu-id="80740-129">The number of elements in the array must be less than or equal to the number of restrictions supported for the specified schema collection else an <xref:System.ArgumentException> will be thrown.</span></span> <span data-ttu-id="80740-130">Il peut y avoir moins de restrictions que le nombre maximal de restrictions.</span><span class="sxs-lookup"><span data-stu-id="80740-130">There can be fewer than the maximum number of restrictions.</span></span> <span data-ttu-id="80740-131">Les restrictions manquantes sont supposées avoir la valeur null (aucune restriction).</span><span class="sxs-lookup"><span data-stu-id="80740-131">The missing restrictions are assumed to be null (unrestricted).</span></span>  
  
 <span data-ttu-id="80740-132">Vous pouvez interroger un fournisseur géré par cadre .NET pour déterminer la liste des restrictions prises en charge en appelant la méthode **GetSchema** avec le nom de la collecte de schémas de restrictions, qui est "Restrictions".</span><span class="sxs-lookup"><span data-stu-id="80740-132">You can query a .NET Framework managed provider to determine the list of supported restrictions by calling the **GetSchema** method with the name of the restrictions schema collection, which is "Restrictions".</span></span> <span data-ttu-id="80740-133">Cette opération retourne un <xref:System.Data.DataTable> contenant une liste des noms de collections, des noms de restriction, des valeurs de restriction par défaut et des numéros de restriction.</span><span class="sxs-lookup"><span data-stu-id="80740-133">This will return a <xref:System.Data.DataTable> with a list of the collection names, the restriction names, the default restriction values, and the restriction numbers.</span></span>  
  
### <a name="example"></a><span data-ttu-id="80740-134"> Exemple</span><span class="sxs-lookup"><span data-stu-id="80740-134">Example</span></span>  
 <span data-ttu-id="80740-135">Les exemples suivants démontrent <xref:System.Data.SqlClient.SqlConnection.GetSchema%2A> comment utiliser la méthode du fournisseur <xref:System.Data.SqlClient.SqlConnection> de données-cadres .NET pour la classe SQL Server pour récupérer les informations sur les schémas sur toutes les tables contenues dans la base de données de l’échantillon **AdventureWorks,** et pour limiter les informations retournées uniquement à ces tableaux dans le schéma « Ventes » :</span><span class="sxs-lookup"><span data-stu-id="80740-135">The following examples demonstrate how to use the <xref:System.Data.SqlClient.SqlConnection.GetSchema%2A> method of the .NET Framework Data Provider for the SQL Server <xref:System.Data.SqlClient.SqlConnection> class to retrieve schema information about all of the tables contained in the **AdventureWorks** sample database, and to restrict the information returned to only those tables in the "Sales" schema:</span></span>  
  
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
  
## <a name="sql-server-schema-restrictions"></a><span data-ttu-id="80740-136">Restrictions de schéma SQL Server</span><span class="sxs-lookup"><span data-stu-id="80740-136">SQL Server Schema Restrictions</span></span>  
 <span data-ttu-id="80740-137">Les tableaux suivants énumèrent les restrictions pour les collections de schémas SQL Server.</span><span class="sxs-lookup"><span data-stu-id="80740-137">The following tables list the restrictions for SQL Server schema collections.</span></span>  
  
### <a name="users"></a><span data-ttu-id="80740-138">Utilisateurs</span><span class="sxs-lookup"><span data-stu-id="80740-138">Users</span></span>  
  
|<span data-ttu-id="80740-139">Nom de restriction</span><span class="sxs-lookup"><span data-stu-id="80740-139">Restriction Name</span></span>|<span data-ttu-id="80740-140">Nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="80740-140">Parameter Name</span></span>|<span data-ttu-id="80740-141">Valeur par défaut de la restriction</span><span class="sxs-lookup"><span data-stu-id="80740-141">Restriction Default</span></span>|<span data-ttu-id="80740-142">Numéro de restriction</span><span class="sxs-lookup"><span data-stu-id="80740-142">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="80740-143">User_Name</span><span class="sxs-lookup"><span data-stu-id="80740-143">User_Name</span></span>|@Name|<span data-ttu-id="80740-144">name</span><span class="sxs-lookup"><span data-stu-id="80740-144">name</span></span>|<span data-ttu-id="80740-145">1</span><span class="sxs-lookup"><span data-stu-id="80740-145">1</span></span>|  
  
### <a name="databases"></a><span data-ttu-id="80740-146">Bases de données</span><span class="sxs-lookup"><span data-stu-id="80740-146">Databases</span></span>  
  
|<span data-ttu-id="80740-147">Nom de restriction</span><span class="sxs-lookup"><span data-stu-id="80740-147">Restriction Name</span></span>|<span data-ttu-id="80740-148">Nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="80740-148">Parameter Name</span></span>|<span data-ttu-id="80740-149">Valeur par défaut de la restriction</span><span class="sxs-lookup"><span data-stu-id="80740-149">Restriction Default</span></span>|<span data-ttu-id="80740-150">Numéro de restriction</span><span class="sxs-lookup"><span data-stu-id="80740-150">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="80740-151">Nom</span><span class="sxs-lookup"><span data-stu-id="80740-151">Name</span></span>|@Name|<span data-ttu-id="80740-152">Nom</span><span class="sxs-lookup"><span data-stu-id="80740-152">Name</span></span>|<span data-ttu-id="80740-153">1</span><span class="sxs-lookup"><span data-stu-id="80740-153">1</span></span>|  
  
### <a name="tables"></a><span data-ttu-id="80740-154">Tables</span><span class="sxs-lookup"><span data-stu-id="80740-154">Tables</span></span>  
  
|<span data-ttu-id="80740-155">Nom de restriction</span><span class="sxs-lookup"><span data-stu-id="80740-155">Restriction Name</span></span>|<span data-ttu-id="80740-156">Nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="80740-156">Parameter Name</span></span>|<span data-ttu-id="80740-157">Valeur par défaut de la restriction</span><span class="sxs-lookup"><span data-stu-id="80740-157">Restriction Default</span></span>|<span data-ttu-id="80740-158">Numéro de restriction</span><span class="sxs-lookup"><span data-stu-id="80740-158">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="80740-159">Catalogue</span><span class="sxs-lookup"><span data-stu-id="80740-159">Catalog</span></span>|@Catalog|<span data-ttu-id="80740-160">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="80740-160">TABLE_CATALOG</span></span>|<span data-ttu-id="80740-161">1</span><span class="sxs-lookup"><span data-stu-id="80740-161">1</span></span>|  
|<span data-ttu-id="80740-162">Propriétaire</span><span class="sxs-lookup"><span data-stu-id="80740-162">Owner</span></span>|@Owner|<span data-ttu-id="80740-163">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="80740-163">TABLE_SCHEMA</span></span>|<span data-ttu-id="80740-164">2</span><span class="sxs-lookup"><span data-stu-id="80740-164">2</span></span>|  
|<span data-ttu-id="80740-165">Table de charge de travail</span><span class="sxs-lookup"><span data-stu-id="80740-165">Table</span></span>|@Name|<span data-ttu-id="80740-166">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="80740-166">TABLE_NAME</span></span>|<span data-ttu-id="80740-167">3</span><span class="sxs-lookup"><span data-stu-id="80740-167">3</span></span>|  
|<span data-ttu-id="80740-168">TableType</span><span class="sxs-lookup"><span data-stu-id="80740-168">TableType</span></span>|@TableType|<span data-ttu-id="80740-169">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="80740-169">TABLE_TYPE</span></span>|<span data-ttu-id="80740-170">4</span><span class="sxs-lookup"><span data-stu-id="80740-170">4</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="80740-171">Colonnes</span><span class="sxs-lookup"><span data-stu-id="80740-171">Columns</span></span>  
  
|<span data-ttu-id="80740-172">Nom de restriction</span><span class="sxs-lookup"><span data-stu-id="80740-172">Restriction Name</span></span>|<span data-ttu-id="80740-173">Nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="80740-173">Parameter Name</span></span>|<span data-ttu-id="80740-174">Valeur par défaut de la restriction</span><span class="sxs-lookup"><span data-stu-id="80740-174">Restriction Default</span></span>|<span data-ttu-id="80740-175">Numéro de restriction</span><span class="sxs-lookup"><span data-stu-id="80740-175">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="80740-176">Catalogue</span><span class="sxs-lookup"><span data-stu-id="80740-176">Catalog</span></span>|@Catalog|<span data-ttu-id="80740-177">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="80740-177">TABLE_CATALOG</span></span>|<span data-ttu-id="80740-178">1</span><span class="sxs-lookup"><span data-stu-id="80740-178">1</span></span>|  
|<span data-ttu-id="80740-179">Propriétaire</span><span class="sxs-lookup"><span data-stu-id="80740-179">Owner</span></span>|@Owner|<span data-ttu-id="80740-180">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="80740-180">TABLE_SCHEMA</span></span>|<span data-ttu-id="80740-181">2</span><span class="sxs-lookup"><span data-stu-id="80740-181">2</span></span>|  
|<span data-ttu-id="80740-182">Table de charge de travail</span><span class="sxs-lookup"><span data-stu-id="80740-182">Table</span></span>|@Table|<span data-ttu-id="80740-183">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="80740-183">TABLE_NAME</span></span>|<span data-ttu-id="80740-184">3</span><span class="sxs-lookup"><span data-stu-id="80740-184">3</span></span>|  
|<span data-ttu-id="80740-185">Colonne</span><span class="sxs-lookup"><span data-stu-id="80740-185">Column</span></span>|@Column|<span data-ttu-id="80740-186">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="80740-186">COLUMN_NAME</span></span>|<span data-ttu-id="80740-187">4</span><span class="sxs-lookup"><span data-stu-id="80740-187">4</span></span>|  
  
### <a name="structuredtypemembers"></a><span data-ttu-id="80740-188">StructuredTypeMembers</span><span class="sxs-lookup"><span data-stu-id="80740-188">StructuredTypeMembers</span></span>  
  
|<span data-ttu-id="80740-189">Nom de restriction</span><span class="sxs-lookup"><span data-stu-id="80740-189">Restriction Name</span></span>|<span data-ttu-id="80740-190">Nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="80740-190">Parameter Name</span></span>|<span data-ttu-id="80740-191">Valeur par défaut de la restriction</span><span class="sxs-lookup"><span data-stu-id="80740-191">Restriction Default</span></span>|<span data-ttu-id="80740-192">Numéro de restriction</span><span class="sxs-lookup"><span data-stu-id="80740-192">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="80740-193">Catalogue</span><span class="sxs-lookup"><span data-stu-id="80740-193">Catalog</span></span>|@Catalog|<span data-ttu-id="80740-194">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="80740-194">TABLE_CATALOG</span></span>|<span data-ttu-id="80740-195">1</span><span class="sxs-lookup"><span data-stu-id="80740-195">1</span></span>|  
|<span data-ttu-id="80740-196">Propriétaire</span><span class="sxs-lookup"><span data-stu-id="80740-196">Owner</span></span>|@Owner|<span data-ttu-id="80740-197">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="80740-197">TABLE_SCHEMA</span></span>|<span data-ttu-id="80740-198">2</span><span class="sxs-lookup"><span data-stu-id="80740-198">2</span></span>|  
|<span data-ttu-id="80740-199">Table de charge de travail</span><span class="sxs-lookup"><span data-stu-id="80740-199">Table</span></span>|@Table|<span data-ttu-id="80740-200">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="80740-200">TABLE_NAME</span></span>|<span data-ttu-id="80740-201">3</span><span class="sxs-lookup"><span data-stu-id="80740-201">3</span></span>|  
|<span data-ttu-id="80740-202">Colonne</span><span class="sxs-lookup"><span data-stu-id="80740-202">Column</span></span>|@Column|<span data-ttu-id="80740-203">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="80740-203">COLUMN_NAME</span></span>|<span data-ttu-id="80740-204">4</span><span class="sxs-lookup"><span data-stu-id="80740-204">4</span></span>|  
  
### <a name="views"></a><span data-ttu-id="80740-205">Les vues</span><span class="sxs-lookup"><span data-stu-id="80740-205">Views</span></span>  
  
|<span data-ttu-id="80740-206">Nom de restriction</span><span class="sxs-lookup"><span data-stu-id="80740-206">Restriction Name</span></span>|<span data-ttu-id="80740-207">Nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="80740-207">Parameter Name</span></span>|<span data-ttu-id="80740-208">Valeur par défaut de la restriction</span><span class="sxs-lookup"><span data-stu-id="80740-208">Restriction Default</span></span>|<span data-ttu-id="80740-209">Numéro de restriction</span><span class="sxs-lookup"><span data-stu-id="80740-209">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="80740-210">Catalogue</span><span class="sxs-lookup"><span data-stu-id="80740-210">Catalog</span></span>|@Catalog|<span data-ttu-id="80740-211">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="80740-211">TABLE_CATALOG</span></span>|<span data-ttu-id="80740-212">1</span><span class="sxs-lookup"><span data-stu-id="80740-212">1</span></span>|  
|<span data-ttu-id="80740-213">Propriétaire</span><span class="sxs-lookup"><span data-stu-id="80740-213">Owner</span></span>|@Owner|<span data-ttu-id="80740-214">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="80740-214">TABLE_SCHEMA</span></span>|<span data-ttu-id="80740-215">2</span><span class="sxs-lookup"><span data-stu-id="80740-215">2</span></span>|  
|<span data-ttu-id="80740-216">Table de charge de travail</span><span class="sxs-lookup"><span data-stu-id="80740-216">Table</span></span>|@Table|<span data-ttu-id="80740-217">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="80740-217">TABLE_NAME</span></span>|<span data-ttu-id="80740-218">3</span><span class="sxs-lookup"><span data-stu-id="80740-218">3</span></span>|  
  
### <a name="viewcolumns"></a><span data-ttu-id="80740-219">ViewColumns</span><span class="sxs-lookup"><span data-stu-id="80740-219">ViewColumns</span></span>  
  
|<span data-ttu-id="80740-220">Nom de restriction</span><span class="sxs-lookup"><span data-stu-id="80740-220">Restriction Name</span></span>|<span data-ttu-id="80740-221">Nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="80740-221">Parameter Name</span></span>|<span data-ttu-id="80740-222">Valeur par défaut de la restriction</span><span class="sxs-lookup"><span data-stu-id="80740-222">Restriction Default</span></span>|<span data-ttu-id="80740-223">Numéro de restriction</span><span class="sxs-lookup"><span data-stu-id="80740-223">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="80740-224">Catalogue</span><span class="sxs-lookup"><span data-stu-id="80740-224">Catalog</span></span>|@Catalog|<span data-ttu-id="80740-225">VIEW_CATALOG</span><span class="sxs-lookup"><span data-stu-id="80740-225">VIEW_CATALOG</span></span>|<span data-ttu-id="80740-226">1</span><span class="sxs-lookup"><span data-stu-id="80740-226">1</span></span>|  
|<span data-ttu-id="80740-227">Propriétaire</span><span class="sxs-lookup"><span data-stu-id="80740-227">Owner</span></span>|@Owner|<span data-ttu-id="80740-228">VIEW_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="80740-228">VIEW_SCHEMA</span></span>|<span data-ttu-id="80740-229">2</span><span class="sxs-lookup"><span data-stu-id="80740-229">2</span></span>|  
|<span data-ttu-id="80740-230">Table de charge de travail</span><span class="sxs-lookup"><span data-stu-id="80740-230">Table</span></span>|@Table|<span data-ttu-id="80740-231">VIEW_NAME</span><span class="sxs-lookup"><span data-stu-id="80740-231">VIEW_NAME</span></span>|<span data-ttu-id="80740-232">3</span><span class="sxs-lookup"><span data-stu-id="80740-232">3</span></span>|  
|<span data-ttu-id="80740-233">Colonne</span><span class="sxs-lookup"><span data-stu-id="80740-233">Column</span></span>|@Column|<span data-ttu-id="80740-234">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="80740-234">COLUMN_NAME</span></span>|<span data-ttu-id="80740-235">4</span><span class="sxs-lookup"><span data-stu-id="80740-235">4</span></span>|  
  
### <a name="procedureparameters"></a><span data-ttu-id="80740-236">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="80740-236">ProcedureParameters</span></span>  
  
|<span data-ttu-id="80740-237">Nom de restriction</span><span class="sxs-lookup"><span data-stu-id="80740-237">Restriction Name</span></span>|<span data-ttu-id="80740-238">Nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="80740-238">Parameter Name</span></span>|<span data-ttu-id="80740-239">Valeur par défaut de la restriction</span><span class="sxs-lookup"><span data-stu-id="80740-239">Restriction Default</span></span>|<span data-ttu-id="80740-240">Numéro de restriction</span><span class="sxs-lookup"><span data-stu-id="80740-240">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="80740-241">Catalogue</span><span class="sxs-lookup"><span data-stu-id="80740-241">Catalog</span></span>|@Catalog|<span data-ttu-id="80740-242">SPECIFIC_CATALOG</span><span class="sxs-lookup"><span data-stu-id="80740-242">SPECIFIC_CATALOG</span></span>|<span data-ttu-id="80740-243">1</span><span class="sxs-lookup"><span data-stu-id="80740-243">1</span></span>|  
|<span data-ttu-id="80740-244">Propriétaire</span><span class="sxs-lookup"><span data-stu-id="80740-244">Owner</span></span>|@Owner|<span data-ttu-id="80740-245">SPECIFIC_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="80740-245">SPECIFIC_SCHEMA</span></span>|<span data-ttu-id="80740-246">2</span><span class="sxs-lookup"><span data-stu-id="80740-246">2</span></span>|  
|<span data-ttu-id="80740-247">Nom</span><span class="sxs-lookup"><span data-stu-id="80740-247">Name</span></span>|@Name|<span data-ttu-id="80740-248">SPECIFIC_NAME</span><span class="sxs-lookup"><span data-stu-id="80740-248">SPECIFIC_NAME</span></span>|<span data-ttu-id="80740-249">3</span><span class="sxs-lookup"><span data-stu-id="80740-249">3</span></span>|  
|<span data-ttu-id="80740-250">Paramètre</span><span class="sxs-lookup"><span data-stu-id="80740-250">Parameter</span></span>|@Parameter|<span data-ttu-id="80740-251">PARAMETER_NAME</span><span class="sxs-lookup"><span data-stu-id="80740-251">PARAMETER_NAME</span></span>|<span data-ttu-id="80740-252">4</span><span class="sxs-lookup"><span data-stu-id="80740-252">4</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="80740-253">Procédures</span><span class="sxs-lookup"><span data-stu-id="80740-253">Procedures</span></span>  
  
|<span data-ttu-id="80740-254">Nom de restriction</span><span class="sxs-lookup"><span data-stu-id="80740-254">Restriction Name</span></span>|<span data-ttu-id="80740-255">Nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="80740-255">Parameter Name</span></span>|<span data-ttu-id="80740-256">Valeur par défaut de la restriction</span><span class="sxs-lookup"><span data-stu-id="80740-256">Restriction Default</span></span>|<span data-ttu-id="80740-257">Numéro de restriction</span><span class="sxs-lookup"><span data-stu-id="80740-257">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="80740-258">Catalogue</span><span class="sxs-lookup"><span data-stu-id="80740-258">Catalog</span></span>|@Catalog|<span data-ttu-id="80740-259">SPECIFIC_CATALOG</span><span class="sxs-lookup"><span data-stu-id="80740-259">SPECIFIC_CATALOG</span></span>|<span data-ttu-id="80740-260">1</span><span class="sxs-lookup"><span data-stu-id="80740-260">1</span></span>|  
|<span data-ttu-id="80740-261">Propriétaire</span><span class="sxs-lookup"><span data-stu-id="80740-261">Owner</span></span>|@Owner|<span data-ttu-id="80740-262">SPECIFIC_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="80740-262">SPECIFIC_SCHEMA</span></span>|<span data-ttu-id="80740-263">2</span><span class="sxs-lookup"><span data-stu-id="80740-263">2</span></span>|  
|<span data-ttu-id="80740-264">Nom</span><span class="sxs-lookup"><span data-stu-id="80740-264">Name</span></span>|@Name|<span data-ttu-id="80740-265">SPECIFIC_NAME</span><span class="sxs-lookup"><span data-stu-id="80740-265">SPECIFIC_NAME</span></span>|<span data-ttu-id="80740-266">3</span><span class="sxs-lookup"><span data-stu-id="80740-266">3</span></span>|  
|<span data-ttu-id="80740-267">Type</span><span class="sxs-lookup"><span data-stu-id="80740-267">Type</span></span>|@Type|<span data-ttu-id="80740-268">ROUTINE_TYPE</span><span class="sxs-lookup"><span data-stu-id="80740-268">ROUTINE_TYPE</span></span>|<span data-ttu-id="80740-269">4</span><span class="sxs-lookup"><span data-stu-id="80740-269">4</span></span>|  
  
### <a name="indexcolumns"></a><span data-ttu-id="80740-270">IndexColumns</span><span class="sxs-lookup"><span data-stu-id="80740-270">IndexColumns</span></span>  
  
|<span data-ttu-id="80740-271">Nom de restriction</span><span class="sxs-lookup"><span data-stu-id="80740-271">Restriction Name</span></span>|<span data-ttu-id="80740-272">Nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="80740-272">Parameter Name</span></span>|<span data-ttu-id="80740-273">Valeur par défaut de la restriction</span><span class="sxs-lookup"><span data-stu-id="80740-273">Restriction Default</span></span>|<span data-ttu-id="80740-274">Numéro de restriction</span><span class="sxs-lookup"><span data-stu-id="80740-274">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="80740-275">Catalogue</span><span class="sxs-lookup"><span data-stu-id="80740-275">Catalog</span></span>|@Catalog|<span data-ttu-id="80740-276">db_name()</span><span class="sxs-lookup"><span data-stu-id="80740-276">db_name()</span></span>|<span data-ttu-id="80740-277">1</span><span class="sxs-lookup"><span data-stu-id="80740-277">1</span></span>|  
|<span data-ttu-id="80740-278">Propriétaire</span><span class="sxs-lookup"><span data-stu-id="80740-278">Owner</span></span>|@Owner|<span data-ttu-id="80740-279">user_name()</span><span class="sxs-lookup"><span data-stu-id="80740-279">user_name()</span></span>|<span data-ttu-id="80740-280">2</span><span class="sxs-lookup"><span data-stu-id="80740-280">2</span></span>|  
|<span data-ttu-id="80740-281">Table de charge de travail</span><span class="sxs-lookup"><span data-stu-id="80740-281">Table</span></span>|@Table|<span data-ttu-id="80740-282">o.name</span><span class="sxs-lookup"><span data-stu-id="80740-282">o.name</span></span>|<span data-ttu-id="80740-283">3</span><span class="sxs-lookup"><span data-stu-id="80740-283">3</span></span>|  
|<span data-ttu-id="80740-284">ConstraintName</span><span class="sxs-lookup"><span data-stu-id="80740-284">ConstraintName</span></span>|@ConstraintName|<span data-ttu-id="80740-285">x.name</span><span class="sxs-lookup"><span data-stu-id="80740-285">x.name</span></span>|<span data-ttu-id="80740-286">4</span><span class="sxs-lookup"><span data-stu-id="80740-286">4</span></span>|  
|<span data-ttu-id="80740-287">Colonne</span><span class="sxs-lookup"><span data-stu-id="80740-287">Column</span></span>|@Column|<span data-ttu-id="80740-288">c.name</span><span class="sxs-lookup"><span data-stu-id="80740-288">c.name</span></span>|<span data-ttu-id="80740-289">5</span><span class="sxs-lookup"><span data-stu-id="80740-289">5</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="80740-290">Index</span><span class="sxs-lookup"><span data-stu-id="80740-290">Indexes</span></span>  
  
|<span data-ttu-id="80740-291">Nom de restriction</span><span class="sxs-lookup"><span data-stu-id="80740-291">Restriction Name</span></span>|<span data-ttu-id="80740-292">Nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="80740-292">Parameter Name</span></span>|<span data-ttu-id="80740-293">Valeur par défaut de la restriction</span><span class="sxs-lookup"><span data-stu-id="80740-293">Restriction Default</span></span>|<span data-ttu-id="80740-294">Numéro de restriction</span><span class="sxs-lookup"><span data-stu-id="80740-294">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="80740-295">Catalogue</span><span class="sxs-lookup"><span data-stu-id="80740-295">Catalog</span></span>|@Catalog|<span data-ttu-id="80740-296">db_name()</span><span class="sxs-lookup"><span data-stu-id="80740-296">db_name()</span></span>|<span data-ttu-id="80740-297">1</span><span class="sxs-lookup"><span data-stu-id="80740-297">1</span></span>|  
|<span data-ttu-id="80740-298">Propriétaire</span><span class="sxs-lookup"><span data-stu-id="80740-298">Owner</span></span>|@Owner|<span data-ttu-id="80740-299">user_name()</span><span class="sxs-lookup"><span data-stu-id="80740-299">user_name()</span></span>|<span data-ttu-id="80740-300">2</span><span class="sxs-lookup"><span data-stu-id="80740-300">2</span></span>|  
|<span data-ttu-id="80740-301">Table de charge de travail</span><span class="sxs-lookup"><span data-stu-id="80740-301">Table</span></span>|@Table|<span data-ttu-id="80740-302">o.name</span><span class="sxs-lookup"><span data-stu-id="80740-302">o.name</span></span>|<span data-ttu-id="80740-303">3</span><span class="sxs-lookup"><span data-stu-id="80740-303">3</span></span>|  
  
### <a name="userdefinedtypes"></a><span data-ttu-id="80740-304">UserDefinedTypes</span><span class="sxs-lookup"><span data-stu-id="80740-304">UserDefinedTypes</span></span>  
  
|<span data-ttu-id="80740-305">Nom de restriction</span><span class="sxs-lookup"><span data-stu-id="80740-305">Restriction Name</span></span>|<span data-ttu-id="80740-306">Nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="80740-306">Parameter Name</span></span>|<span data-ttu-id="80740-307">Valeur par défaut de la restriction</span><span class="sxs-lookup"><span data-stu-id="80740-307">Restriction Default</span></span>|<span data-ttu-id="80740-308">Numéro de restriction</span><span class="sxs-lookup"><span data-stu-id="80740-308">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="80740-309">assembly_name</span><span class="sxs-lookup"><span data-stu-id="80740-309">assembly_name</span></span>|@AssemblyName|<span data-ttu-id="80740-310">assemblies.name</span><span class="sxs-lookup"><span data-stu-id="80740-310">assemblies.name</span></span>|<span data-ttu-id="80740-311">1</span><span class="sxs-lookup"><span data-stu-id="80740-311">1</span></span>|  
|<span data-ttu-id="80740-312">udt_name</span><span class="sxs-lookup"><span data-stu-id="80740-312">udt_name</span></span>|@UDTName|<span data-ttu-id="80740-313">types.assembly_class</span><span class="sxs-lookup"><span data-stu-id="80740-313">types.assembly_class</span></span>|<span data-ttu-id="80740-314">2</span><span class="sxs-lookup"><span data-stu-id="80740-314">2</span></span>|  
  
### <a name="foreignkeys"></a><span data-ttu-id="80740-315">ForeignKeys</span><span class="sxs-lookup"><span data-stu-id="80740-315">ForeignKeys</span></span>  
  
|<span data-ttu-id="80740-316">Nom de restriction</span><span class="sxs-lookup"><span data-stu-id="80740-316">Restriction Name</span></span>|<span data-ttu-id="80740-317">Nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="80740-317">Parameter Name</span></span>|<span data-ttu-id="80740-318">Valeur par défaut de la restriction</span><span class="sxs-lookup"><span data-stu-id="80740-318">Restriction Default</span></span>|<span data-ttu-id="80740-319">Numéro de restriction</span><span class="sxs-lookup"><span data-stu-id="80740-319">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="80740-320">Catalogue</span><span class="sxs-lookup"><span data-stu-id="80740-320">Catalog</span></span>|@Catalog|<span data-ttu-id="80740-321">CONSTRAINT_CATALOG</span><span class="sxs-lookup"><span data-stu-id="80740-321">CONSTRAINT_CATALOG</span></span>|<span data-ttu-id="80740-322">1</span><span class="sxs-lookup"><span data-stu-id="80740-322">1</span></span>|  
|<span data-ttu-id="80740-323">Propriétaire</span><span class="sxs-lookup"><span data-stu-id="80740-323">Owner</span></span>|@Owner|<span data-ttu-id="80740-324">CONSTRAINT_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="80740-324">CONSTRAINT_SCHEMA</span></span>|<span data-ttu-id="80740-325">2</span><span class="sxs-lookup"><span data-stu-id="80740-325">2</span></span>|  
|<span data-ttu-id="80740-326">Table de charge de travail</span><span class="sxs-lookup"><span data-stu-id="80740-326">Table</span></span>|@Table|<span data-ttu-id="80740-327">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="80740-327">TABLE_NAME</span></span>|<span data-ttu-id="80740-328">3</span><span class="sxs-lookup"><span data-stu-id="80740-328">3</span></span>|  
|<span data-ttu-id="80740-329">Nom</span><span class="sxs-lookup"><span data-stu-id="80740-329">Name</span></span>|@Name|<span data-ttu-id="80740-330">CONSTRAINT_NAME</span><span class="sxs-lookup"><span data-stu-id="80740-330">CONSTRAINT_NAME</span></span>|<span data-ttu-id="80740-331">4</span><span class="sxs-lookup"><span data-stu-id="80740-331">4</span></span>|  
  
## <a name="sql-server-2008-schema-restrictions"></a><span data-ttu-id="80740-332">Restrictions de schéma SQL Server 2008</span><span class="sxs-lookup"><span data-stu-id="80740-332">SQL Server 2008 Schema Restrictions</span></span>  
 <span data-ttu-id="80740-333">Les tableaux suivants répertorient les restrictions pour les collections de schémas SQL Server 2008.</span><span class="sxs-lookup"><span data-stu-id="80740-333">The following tables list the restrictions for SQL Server 2008 schema collections.</span></span> <span data-ttu-id="80740-334">Ces restrictions s'appliquent à partir de la version 3.5 SP1 de .NET Framework et SQL Server 2008.</span><span class="sxs-lookup"><span data-stu-id="80740-334">These restrictions are valid beginning with version 3.5 SP1 of the .NET Framework and SQL Server 2008.</span></span> <span data-ttu-id="80740-335">Elles ne sont pas prises en charge dans les versions précédentes de .NET Framework et SQL Server.</span><span class="sxs-lookup"><span data-stu-id="80740-335">They are not supported in earlier versions of the .NET Framework and SQL Server.</span></span>  
  
### <a name="columnsetcolumns"></a><span data-ttu-id="80740-336">ColumnSetColumns</span><span class="sxs-lookup"><span data-stu-id="80740-336">ColumnSetColumns</span></span>  
  
|<span data-ttu-id="80740-337">Nom de restriction</span><span class="sxs-lookup"><span data-stu-id="80740-337">Restriction Name</span></span>|<span data-ttu-id="80740-338">Nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="80740-338">Parameter Name</span></span>|<span data-ttu-id="80740-339">Valeur par défaut de la restriction</span><span class="sxs-lookup"><span data-stu-id="80740-339">Restriction Default</span></span>|<span data-ttu-id="80740-340">Numéro de restriction</span><span class="sxs-lookup"><span data-stu-id="80740-340">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="80740-341">Catalogue</span><span class="sxs-lookup"><span data-stu-id="80740-341">Catalog</span></span>|@Catalog|<span data-ttu-id="80740-342">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="80740-342">TABLE_CATALOG</span></span>|<span data-ttu-id="80740-343">1</span><span class="sxs-lookup"><span data-stu-id="80740-343">1</span></span>|  
|<span data-ttu-id="80740-344">Propriétaire</span><span class="sxs-lookup"><span data-stu-id="80740-344">Owner</span></span>|@Owner|<span data-ttu-id="80740-345">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="80740-345">TABLE_SCHEMA</span></span>|<span data-ttu-id="80740-346">2</span><span class="sxs-lookup"><span data-stu-id="80740-346">2</span></span>|  
|<span data-ttu-id="80740-347">Table de charge de travail</span><span class="sxs-lookup"><span data-stu-id="80740-347">Table</span></span>|@Table|<span data-ttu-id="80740-348">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="80740-348">TABLE_NAME</span></span>|<span data-ttu-id="80740-349">3</span><span class="sxs-lookup"><span data-stu-id="80740-349">3</span></span>|  
  
### <a name="allcolumns"></a><span data-ttu-id="80740-350">AllColumns</span><span class="sxs-lookup"><span data-stu-id="80740-350">AllColumns</span></span>  
  
|<span data-ttu-id="80740-351">Nom de restriction</span><span class="sxs-lookup"><span data-stu-id="80740-351">Restriction Name</span></span>|<span data-ttu-id="80740-352">Nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="80740-352">Parameter Name</span></span>|<span data-ttu-id="80740-353">Valeur par défaut de la restriction</span><span class="sxs-lookup"><span data-stu-id="80740-353">Restriction Default</span></span>|<span data-ttu-id="80740-354">Numéro de restriction</span><span class="sxs-lookup"><span data-stu-id="80740-354">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="80740-355">Catalogue</span><span class="sxs-lookup"><span data-stu-id="80740-355">Catalog</span></span>|@Catalog|<span data-ttu-id="80740-356">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="80740-356">TABLE_CATALOG</span></span>|<span data-ttu-id="80740-357">1</span><span class="sxs-lookup"><span data-stu-id="80740-357">1</span></span>|  
|<span data-ttu-id="80740-358">Propriétaire</span><span class="sxs-lookup"><span data-stu-id="80740-358">Owner</span></span>|@Owner|<span data-ttu-id="80740-359">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="80740-359">TABLE_SCHEMA</span></span>|<span data-ttu-id="80740-360">2</span><span class="sxs-lookup"><span data-stu-id="80740-360">2</span></span>|  
|<span data-ttu-id="80740-361">Table de charge de travail</span><span class="sxs-lookup"><span data-stu-id="80740-361">Table</span></span>|@Table|<span data-ttu-id="80740-362">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="80740-362">TABLE_NAME</span></span>|<span data-ttu-id="80740-363">3</span><span class="sxs-lookup"><span data-stu-id="80740-363">3</span></span>|  
|<span data-ttu-id="80740-364">Colonne</span><span class="sxs-lookup"><span data-stu-id="80740-364">Column</span></span>|@Column|<span data-ttu-id="80740-365">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="80740-365">COLUMN_NAME</span></span>|<span data-ttu-id="80740-366">4</span><span class="sxs-lookup"><span data-stu-id="80740-366">4</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="80740-367">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="80740-367">See also</span></span>

- [<span data-ttu-id="80740-368">Vue d'ensemble d’ADO.NET</span><span class="sxs-lookup"><span data-stu-id="80740-368">ADO.NET Overview</span></span>](ado-net-overview.md)
