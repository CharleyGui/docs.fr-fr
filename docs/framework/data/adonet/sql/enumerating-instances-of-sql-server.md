---
title: Énumération des instances de SQL Server (ADO.NET)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ddf1c83c-9d40-45e6-b04d-9828c6cbbfdc
ms.openlocfilehash: d6d76d677bcf7dfa7df632bde8de76401a46db05
ms.sourcegitcommit: d6e27023aeaffc4b5a3cb4b88685018d6284ada4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/09/2019
ms.locfileid: "67661889"
---
# <a name="enumerating-instances-of-sql-server-adonet"></a>Énumération des instances de SQL Server (ADO.NET)
SQL Server permet à des applications pour rechercher des instances de SQL Server dans le réseau actuel. La classe <xref:System.Data.Sql.SqlDataSourceEnumerator> expose ces informations au développeur d'applications, en fournissant un <xref:System.Data.DataTable> contenant des informations sur tous les serveurs visibles. Cette table retournée contient une liste d’instances de serveur disponibles sur le réseau qui correspond à la liste fournie lorsqu’un utilisateur tente de créer une nouvelle connexion et développe la liste déroulante contenant tous les serveurs disponibles sur le **connexion Propriétés** boîte de dialogue. Les résultats affichés ne sont pas toujours complets.  
  
> [!NOTE]
>  Comme avec la plupart des services Windows, il est préférable d'exécuter le service SQL Browser avec le moins possible de privilèges. Pour plus d'informations sur le service SQL Browser et sur la manière de gérer son comportement, voir la documentation en ligne de SQL Server.  
  
## <a name="retrieving-an-enumerator-instance"></a>Extraction d'une instance d'énumérateur  
 Pour extraire la table contenant des informations sur les instances de SQL Server disponibles, vous devez commencer par extraire un énumérateur en utilisant la propriété partagée/statique <xref:System.Data.Sql.SqlDataSourceEnumerator.Instance%2A> :  
  
```vb  
Dim instance As System.Data.Sql.SqlDataSourceEnumerator = _  
   System.Data.Sql.SqlDataSourceEnumerator.Instance  
```  
  
```csharp  
System.Data.Sql.SqlDataSourceEnumerator instance =   
   System.Data.Sql.SqlDataSourceEnumerator.Instance  
```  
  
 Après avoir extrait l'instance statique, vous pouvez appeler la méthode <xref:System.Data.Sql.SqlDataSourceEnumerator.GetDataSources%2A> qui retourne un <xref:System.Data.DataTable> contenant des informations sur les serveurs disponibles :  
  
```vb  
Dim dataTable As System.Data.DataTable = instance.GetDataSources()  
```  
  
```csharp  
System.Data.DataTable dataTable = instance.GetDataSources();  
```  
  
 La table retournée par l'appel de la méthode comprend les colonnes suivantes qui contiennent toutes des valeurs `string` :  
  
|Colonne|Description|  
|------------|-----------------|  
|**ServerName**|Nom du serveur.|  
|**InstanceName**|Nom de l'instance du serveur. Vide si le serveur s'exécute comme instance par défaut.|  
|**IsClustered**|Indique si le serveur fait partie d'un cluster.|  
|**Version**|Version du serveur. Par exemple :<br /><br /> -9.00.x (SQL Server 2005)<br />-10.0.xx (SQL Server 2008)<br />-10.50.x (SQL Server 2008 R2)<br />-11.0.xx (SQL Server 2012)|  
  
## <a name="enumeration-limitations"></a>Limitations des énumérations  
 Tous les serveurs disponibles peuvent être répertoriés ou ne pas l'être. La liste peut varier en fonction de facteurs tels que des délais d'attente et le trafic réseau. Cela peut avoir pour effet que la liste diffère sur deux appels consécutifs. Seuls des serveurs sur le même réseau sont répertoriés. Les paquets de diffusion ne traversent généralement pas les routeurs, ce qui explique pourquoi vous pouvez ne pas voir un serveur dans la liste, alors qu'il est stable dans l'ensemble des appels.  
  
 Les serveurs répertoriés peuvent avoir ou non des informations supplémentaires, telles qu'un `IsClustered` et une version. Cela dépend de la manière dont la liste a été obtenue. Les serveurs répertoriés à l'aide du service de navigateur de SQL Server offrent plus de détails que ceux trouvés via l'infrastructure Windows dont seul le nom est indiqué.  
  
> [!NOTE]
>  L'énumération des serveurs n'est disponible qu'en mode d'exécution avec un niveau de confiance totale. Les assemblys s'exécutant dans un environnement bénéficiant d'un niveau de confiance partielle ne peuvent pas l'utiliser, même s'ils disposent de l'autorisation de sécurité d'accès du code CAS (Code Access Security) <xref:System.Data.SqlClient.SqlClientPermission>.  
  
 SQL Server fournit des informations pour le <xref:System.Data.Sql.SqlDataSourceEnumerator> en utilisant un service Windows externe nommé SQL Browser. Ce service est activé par défaut mais les administrateurs peuvent l'arrêter ou le désactiver, ce qui rend l'instance du serveur invisible pour cette classe.  
  
## <a name="example"></a>Exemple  
 L'application console suivante extrait des informations sur toutes les instances de SQL Server visibles et affiche les informations dans la fenêtre de console.  
  
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
  
## <a name="see-also"></a>Voir aussi

- [SQL Server et ADO.NET](../../../../../docs/framework/data/adonet/sql/index.md)
- [Fournisseurs managés ADO.NET et centre de développement DataSet](https://go.microsoft.com/fwlink/?LinkId=217917)
