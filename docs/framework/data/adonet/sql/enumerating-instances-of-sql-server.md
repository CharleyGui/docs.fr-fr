---
title: Énumération des instances de SQL Server (ADO.NET)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ddf1c83c-9d40-45e6-b04d-9828c6cbbfdc
ms.openlocfilehash: 304387197c7c6ca31d76ce429cd1516be27ba7b9
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69938171"
---
# <a name="enumerating-instances-of-sql-server-adonet"></a><span data-ttu-id="6f12d-102">Énumération des instances de SQL Server (ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="6f12d-102">Enumerating Instances of SQL Server (ADO.NET)</span></span>
<span data-ttu-id="6f12d-103">SQL Server permet aux applications de trouver des instances de SQL Server dans le réseau actuel.</span><span class="sxs-lookup"><span data-stu-id="6f12d-103">SQL Server permits applications to find SQL Server instances within the current network.</span></span> <span data-ttu-id="6f12d-104">La classe <xref:System.Data.Sql.SqlDataSourceEnumerator> expose ces informations au développeur d'applications, en fournissant un <xref:System.Data.DataTable> contenant des informations sur tous les serveurs visibles.</span><span class="sxs-lookup"><span data-stu-id="6f12d-104">The <xref:System.Data.Sql.SqlDataSourceEnumerator> class exposes this information to the application developer, providing a <xref:System.Data.DataTable> containing information about all the visible servers.</span></span> <span data-ttu-id="6f12d-105">Cette table retournée contient une liste d’instances de serveur disponibles sur le réseau qui correspond à la liste fournie lorsqu’un utilisateur tente de créer une nouvelle connexion, puis développe la liste déroulante contenant tous les serveurs disponibles dans les **Propriétés de connexion.** boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="6f12d-105">This returned table contains a list of server instances available on the network that matches the list provided when a user attempts to create a new connection, and expands the drop-down list containing all the available servers on the **Connection Properties** dialog box.</span></span> <span data-ttu-id="6f12d-106">Les résultats affichés ne sont pas toujours complets.</span><span class="sxs-lookup"><span data-stu-id="6f12d-106">The results displayed are not always complete.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6f12d-107">Comme avec la plupart des services Windows, il est préférable d'exécuter le service SQL Browser avec le moins possible de privilèges.</span><span class="sxs-lookup"><span data-stu-id="6f12d-107">As with most Windows services, it is best to run the SQL Browser service with the least possible privileges.</span></span> <span data-ttu-id="6f12d-108">Pour plus d'informations sur le service SQL Browser et sur la manière de gérer son comportement, voir la documentation en ligne de SQL Server.</span><span class="sxs-lookup"><span data-stu-id="6f12d-108">See SQL Server Books Online for more information on the SQL Browser service, and how to manage its behavior.</span></span>  
  
## <a name="retrieving-an-enumerator-instance"></a><span data-ttu-id="6f12d-109">Extraction d'une instance d'énumérateur</span><span class="sxs-lookup"><span data-stu-id="6f12d-109">Retrieving an Enumerator Instance</span></span>  
 <span data-ttu-id="6f12d-110">Pour extraire la table contenant des informations sur les instances de SQL Server disponibles, vous devez commencer par extraire un énumérateur en utilisant la propriété partagée/statique <xref:System.Data.Sql.SqlDataSourceEnumerator.Instance%2A> :</span><span class="sxs-lookup"><span data-stu-id="6f12d-110">In order to retrieve the table containing information about the available SQL Server instances, you must first retrieve an enumerator, using the shared/static <xref:System.Data.Sql.SqlDataSourceEnumerator.Instance%2A> property:</span></span>  
  
```vb  
Dim instance As System.Data.Sql.SqlDataSourceEnumerator = _  
   System.Data.Sql.SqlDataSourceEnumerator.Instance  
```  
  
```csharp  
System.Data.Sql.SqlDataSourceEnumerator instance =   
   System.Data.Sql.SqlDataSourceEnumerator.Instance  
```  
  
 <span data-ttu-id="6f12d-111">Après avoir extrait l'instance statique, vous pouvez appeler la méthode <xref:System.Data.Sql.SqlDataSourceEnumerator.GetDataSources%2A> qui retourne un <xref:System.Data.DataTable> contenant des informations sur les serveurs disponibles :</span><span class="sxs-lookup"><span data-stu-id="6f12d-111">Once you have retrieved the static instance, you can call the <xref:System.Data.Sql.SqlDataSourceEnumerator.GetDataSources%2A> method, which returns a <xref:System.Data.DataTable> containing information about the available servers:</span></span>  
  
```vb  
Dim dataTable As System.Data.DataTable = instance.GetDataSources()  
```  
  
```csharp  
System.Data.DataTable dataTable = instance.GetDataSources();  
```  
  
 <span data-ttu-id="6f12d-112">La table retournée par l'appel de la méthode comprend les colonnes suivantes qui contiennent toutes des valeurs `string` :</span><span class="sxs-lookup"><span data-stu-id="6f12d-112">The table returned from the method call contains the following columns, all of which contain `string` values:</span></span>  
  
|<span data-ttu-id="6f12d-113">Colonne</span><span class="sxs-lookup"><span data-stu-id="6f12d-113">Column</span></span>|<span data-ttu-id="6f12d-114">Description</span><span class="sxs-lookup"><span data-stu-id="6f12d-114">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="6f12d-115">**ServerName**</span><span class="sxs-lookup"><span data-stu-id="6f12d-115">**ServerName**</span></span>|<span data-ttu-id="6f12d-116">Nom du serveur.</span><span class="sxs-lookup"><span data-stu-id="6f12d-116">Name of the server.</span></span>|  
|<span data-ttu-id="6f12d-117">**InstanceName**</span><span class="sxs-lookup"><span data-stu-id="6f12d-117">**InstanceName**</span></span>|<span data-ttu-id="6f12d-118">Nom de l'instance du serveur.</span><span class="sxs-lookup"><span data-stu-id="6f12d-118">Name of the server instance.</span></span> <span data-ttu-id="6f12d-119">Vide si le serveur s'exécute comme instance par défaut.</span><span class="sxs-lookup"><span data-stu-id="6f12d-119">Blank if the server is running as the default instance.</span></span>|  
|<span data-ttu-id="6f12d-120">**IsClustered**</span><span class="sxs-lookup"><span data-stu-id="6f12d-120">**IsClustered**</span></span>|<span data-ttu-id="6f12d-121">Indique si le serveur fait partie d'un cluster.</span><span class="sxs-lookup"><span data-stu-id="6f12d-121">Indicates whether the server is part of a cluster.</span></span>|  
|<span data-ttu-id="6f12d-122">**Version**</span><span class="sxs-lookup"><span data-stu-id="6f12d-122">**Version**</span></span>|<span data-ttu-id="6f12d-123">Version du serveur.</span><span class="sxs-lookup"><span data-stu-id="6f12d-123">Version of the server.</span></span> <span data-ttu-id="6f12d-124">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="6f12d-124">For example:</span></span><br /><br /> <span data-ttu-id="6f12d-125">-9,00. x (SQL Server 2005)</span><span class="sxs-lookup"><span data-stu-id="6f12d-125">-   9.00.x (SQL Server 2005)</span></span><br /><span data-ttu-id="6f12d-126">-10.0. XX (SQL Server 2008)</span><span class="sxs-lookup"><span data-stu-id="6f12d-126">-   10.0.xx (SQL Server 2008)</span></span><br /><span data-ttu-id="6f12d-127">-10,50. x (SQL Server 2008 R2)</span><span class="sxs-lookup"><span data-stu-id="6f12d-127">-   10.50.x (SQL Server 2008 R2)</span></span><br /><span data-ttu-id="6f12d-128">-11.0. XX (SQL Server 2012)</span><span class="sxs-lookup"><span data-stu-id="6f12d-128">-   11.0.xx (SQL Server 2012)</span></span>|  
  
## <a name="enumeration-limitations"></a><span data-ttu-id="6f12d-129">Limitations des énumérations</span><span class="sxs-lookup"><span data-stu-id="6f12d-129">Enumeration Limitations</span></span>  
 <span data-ttu-id="6f12d-130">Tous les serveurs disponibles peuvent être répertoriés ou ne pas l'être.</span><span class="sxs-lookup"><span data-stu-id="6f12d-130">All of the available servers may or may not be listed.</span></span> <span data-ttu-id="6f12d-131">La liste peut varier en fonction de facteurs tels que des délais d'attente et le trafic réseau.</span><span class="sxs-lookup"><span data-stu-id="6f12d-131">The list can vary depending on factors such as timeouts and network traffic.</span></span> <span data-ttu-id="6f12d-132">Cela peut avoir pour effet que la liste diffère sur deux appels consécutifs.</span><span class="sxs-lookup"><span data-stu-id="6f12d-132">This can cause the list to be different on two consecutive calls.</span></span> <span data-ttu-id="6f12d-133">Seuls des serveurs sur le même réseau sont répertoriés.</span><span class="sxs-lookup"><span data-stu-id="6f12d-133">Only servers on the same network will be listed.</span></span> <span data-ttu-id="6f12d-134">Les paquets de diffusion ne traversent généralement pas les routeurs, ce qui explique pourquoi vous pouvez ne pas voir un serveur dans la liste, alors qu'il est stable dans l'ensemble des appels.</span><span class="sxs-lookup"><span data-stu-id="6f12d-134">Broadcast packets typically won't traverse routers, which is why you may not see a server listed, but it will be stable across calls.</span></span>  
  
 <span data-ttu-id="6f12d-135">Les serveurs répertoriés peuvent avoir ou non des informations supplémentaires, telles qu'un `IsClustered` et une version.</span><span class="sxs-lookup"><span data-stu-id="6f12d-135">Listed servers may or may not have additional information such as `IsClustered` and version.</span></span> <span data-ttu-id="6f12d-136">Cela dépend de la manière dont la liste a été obtenue.</span><span class="sxs-lookup"><span data-stu-id="6f12d-136">This is dependent on how the list was obtained.</span></span> <span data-ttu-id="6f12d-137">Les serveurs répertoriés à l'aide du service de navigateur de SQL Server offrent plus de détails que ceux trouvés via l'infrastructure Windows dont seul le nom est indiqué.</span><span class="sxs-lookup"><span data-stu-id="6f12d-137">Servers listed through the SQL Server browser service will have more details than those found through the Windows infrastructure, which will list only the name.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6f12d-138">L'énumération des serveurs n'est disponible qu'en mode d'exécution avec un niveau de confiance totale.</span><span class="sxs-lookup"><span data-stu-id="6f12d-138">Server enumeration is only available when running in full-trust.</span></span> <span data-ttu-id="6f12d-139">Les assemblys s'exécutant dans un environnement bénéficiant d'un niveau de confiance partielle ne peuvent pas l'utiliser, même s'ils disposent de l'autorisation de sécurité d'accès du code CAS (Code Access Security) <xref:System.Data.SqlClient.SqlClientPermission>.</span><span class="sxs-lookup"><span data-stu-id="6f12d-139">Assemblies running in a partially-trusted environment will not be able to use it, even if they have the <xref:System.Data.SqlClient.SqlClientPermission> Code Access Security (CAS) permission.</span></span>  
  
 <span data-ttu-id="6f12d-140">SQL Server fournit des informations sur <xref:System.Data.Sql.SqlDataSourceEnumerator> l’utilisation d’un service Windows externe nommé SQL Browser.</span><span class="sxs-lookup"><span data-stu-id="6f12d-140">SQL Server provides information for the <xref:System.Data.Sql.SqlDataSourceEnumerator> through the use of an external Windows service named SQL Browser.</span></span> <span data-ttu-id="6f12d-141">Ce service est activé par défaut mais les administrateurs peuvent l'arrêter ou le désactiver, ce qui rend l'instance du serveur invisible pour cette classe.</span><span class="sxs-lookup"><span data-stu-id="6f12d-141">This service is enabled by default, but administrators may turn it off or disable it, making the server instance invisible to this class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6f12d-142">Exemple</span><span class="sxs-lookup"><span data-stu-id="6f12d-142">Example</span></span>  
 <span data-ttu-id="6f12d-143">L'application console suivante extrait des informations sur toutes les instances de SQL Server visibles et affiche les informations dans la fenêtre de console.</span><span class="sxs-lookup"><span data-stu-id="6f12d-143">The following console application retrieves information about all of the visible SQL Server instances and displays the information in the console window.</span></span>  
  
```vb  
Imports System.Data.Sql  
  
Module Module1  
  Sub Main()  
    ' Retrieve the enumerator instance and then the data.  
    Dim instance As SqlDataSourceEnumerator = _  
     SqlDataSourceEnumerator.Instance  
    Dim table As System.Data.DataTable = instance.GetDataSources()  
  
    ' Display the contents of the table.  
    DisplayData(table)  
  
    Console.WriteLine("Press any key to continue.")  
    Console.ReadKey()  
  End Sub  
  
  Private Sub DisplayData(ByVal table As DataTable)  
    For Each row As DataRow In table.Rows  
      For Each col As DataColumn In table.Columns  
        Console.WriteLine("{0} = {1}", col.ColumnName, row(col))  
      Next  
      Console.WriteLine("============================")  
    Next  
  End Sub  
End Module  
```  
  
```csharp  
using System.Data.Sql;  
  
class Program  
{  
  static void Main()  
  {  
    // Retrieve the enumerator instance and then the data.  
    SqlDataSourceEnumerator instance =  
      SqlDataSourceEnumerator.Instance;  
    System.Data.DataTable table = instance.GetDataSources();  
  
    // Display the contents of the table.  
    DisplayData(table);  
  
    Console.WriteLine("Press any key to continue.");  
    Console.ReadKey();  
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
  
## <a name="see-also"></a><span data-ttu-id="6f12d-144">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6f12d-144">See also</span></span>

- [<span data-ttu-id="6f12d-145">SQL Server et ADO.NET</span><span class="sxs-lookup"><span data-stu-id="6f12d-145">SQL Server and ADO.NET</span></span>](../../../../../docs/framework/data/adonet/sql/index.md)
- [<span data-ttu-id="6f12d-146">Fournisseurs managés ADO.NET et centre de développement DataSet</span><span class="sxs-lookup"><span data-stu-id="6f12d-146">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
