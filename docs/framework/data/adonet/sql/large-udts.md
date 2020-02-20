---
title: UDT volumineux
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 420ae24e-762b-4e09-b4c3-2112c470ee49
ms.openlocfilehash: 012bddc0b4c29a0b50abc3a0df5c3cd34dc4725a
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452394"
---
# <a name="large-udts"></a>UDT volumineux
Les types définis par l’utilisateur (UDT) permettent au développeur d’étendre le système de type scalaire du serveur en stockant des objets CLR (Common Language Runtime) dans une base de données SQL Server. Les UDT peuvent contenir plusieurs éléments et avoir des comportements, contrairement aux types de données alias traditionnels, qui ne comprennent qu’un seul type de données système SQL Server.  
  
> [!NOTE]
> Vous devez installer le .NET Framework 3.5 SP1 (ou version ultérieure) pour tirer parti de la prise en charge améliorée de SqlClient pour les UDT volumineux.  
  
 Auparavant, les UDT étaient limités à une taille maximale de 8 kilo-octets. Dans SQL Server 2008, cette restriction a été supprimée pour les UDT ayant un format <xref:Microsoft.SqlServer.Server.Format.UserDefined>.  
  
 Pour la documentation complète relative aux types définis par l'utilisateur, consultez la version de la documentation en ligne de SQL Server correspondant à la version de SQL Server que vous utilisez.  
  
 **Documentation SQL Server**  
  
1. [Types CLR définis par l’utilisateur](/sql/relational-databases/clr-integration-database-objects-user-defined-types/clr-user-defined-types)  
  
## <a name="retrieving-udt-schemas-using-getschema"></a>Récupération de schémas UDT à l'aide de GetSchema  
 La méthode <xref:System.Data.SqlClient.SqlConnection.GetSchema%2A> de <xref:System.Data.SqlClient.SqlConnection> retourne les informations de schéma de la base de données dans un objet <xref:System.Data.DataTable>. Pour plus d’informations, consultez [SQL Server collections de schémas](../sql-server-schema-collections.md).  
  
### <a name="getschematable-column-values-for-udts"></a>Valeurs de colonne GetSchemaTable Column pour les UDT  
 La méthode <xref:System.Data.SqlClient.SqlDataReader.GetSchemaTable%2A> d'un objet <xref:System.Data.SqlClient.SqlDataReader> retourne un objet <xref:System.Data.DataTable> qui décrit les métadonnées des colonnes. Le tableau suivant décrit les différences dans les métadonnées des colonnes pour les UDT volumineux entre SQL Server 2005 et SQL Server 2008.  
  
|Colonne SqlDataReader|SQL Server 2005|SQL Server 2008 et ultérieur|  
|--------------------------|---------------------|-------------------------------|  
|`ColumnSize`|Variable|Variable|  
|`NumericPrecision`|255|255|  
|`NumericScale`|255|255|  
|`DataType`|`Byte[]`|Instance UDT|  
|`ProviderSpecificDataType`|`SqlTypes.SqlBinary`|Instance UDT|  
|`ProviderType`|21 (`SqlDbType.VarBinary`)|29 (`SqlDbType.Udt`)|  
|`NonVersionedProviderType`|29 (`SqlDbType.Udt`)|29 (`SqlDbType.Udt`)|  
|`DataTypeName`|`SqlDbType.VarBinary`|Nom en trois parties spécifié sous la forme *Database.SchemaName.TypeName*.|  
|`IsLong`|Variable|Variable|  
  
## <a name="sqldatareader-considerations"></a>Considérations relatives à SqlDataReader  
 L’objet <xref:System.Data.SqlClient.SqlDataReader> a été étendu à compter de SQL Server 2008 pour prendre en charge la récupération des valeurs UDT volumineuses. La manière dont un <xref:System.Data.SqlClient.SqlDataReader> traite les valeurs UDT volumineuses par dépend de la version de SQL Server que vous utilisez, ainsi que du `Type System Version` spécifié dans la chaîne de connexion. Pour plus d’informations, consultez <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A>.  
  
 Les méthodes suivantes de <xref:System.Data.SqlClient.SqlDataReader> retournent un <xref:System.Data.SqlTypes.SqlBinary> au lieu d'un type défini par l'utilisateur lorsque `Type System Version` est défini à SQL Server 2005 :  
  
- <xref:System.Data.SqlClient.SqlDataReader.GetProviderSpecificFieldType%2A>  
  
- <xref:System.Data.SqlClient.SqlDataReader.GetProviderSpecificValue%2A>  
  
- <xref:System.Data.SqlClient.SqlDataReader.GetProviderSpecificValues%2A>  
  
- <xref:System.Data.SqlClient.SqlDataReader.GetSqlValue%2A>  
  
- <xref:System.Data.SqlClient.SqlDataReader.GetSqlValues%2A>  
  
 Les méthodes suivantes retournent un tableau de `Byte[]` au lieu d'un UDT lorsque `Type System Version` est défini à SQL Server 2005 :  
  
- <xref:System.Data.SqlClient.SqlDataReader.GetValue%2A>  
  
- <xref:System.Data.SqlClient.SqlDataReader.GetValues%2A>  
  
 Notez qu'aucune conversion n'est effectuée pour la version actuelle d'ADO.NET.  
  
## <a name="specifying-sqlparameters"></a>Spécification de SqlParameters  
 Les propriétés <xref:System.Data.SqlClient.SqlParameter> suivantes ont été étendues pour fonctionner avec des UDT volumineux.  
  
|Propriété SqlParameter|Description|  
|---------------------------|-----------------|  
|<xref:System.Data.SqlClient.SqlParameter.Value%2A>|Obtient ou définit un objet qui représente la valeur du paramètre. La valeur par défaut est null. La propriété peut être `SqlBinary`, `Byte[]` ou un objet managé.|  
|<xref:System.Data.SqlClient.SqlParameter.SqlValue%2A>|Obtient ou définit un objet qui représente la valeur du paramètre. La valeur par défaut est null. La propriété peut être `SqlBinary`, `Byte[]` ou un objet managé.|  
|<xref:System.Data.SqlClient.SqlParameter.Size%2A>|Obtient ou définit la taille de la valeur de paramètre à résoudre. La valeur par défaut est 0. La propriété peut être un nombre entier qui représente la taille de la valeur de paramètre. Pour les UDT volumineux, elle peut être la taille réelle de l’UDT, ou -1 pour inconnu.|  
  
## <a name="retrieving-data-example"></a>Exemple d'extraction de données  
 Le fragment de code suivant montre comment extraire des données UDT volumineuses. La variable `connectionString` suppose une connexion valide à une base de données SQL Server, et la variable `commandString` suppose une instruction SELECT valide avec la colonne de clé primaire apparaissant en premier.  
  
```csharp  
using (SqlConnection connection = new SqlConnection(   
    connectionString, commandString))  
{  
  connection.Open();  
  SqlCommand command = new SqlCommand(commandString);  
  SqlDataReader reader = command.ExecuteReader();  
  while (reader.Read())  
  {  
    // Retrieve the value of the Primary Key column.  
    int id = reader.GetInt32(0);  
  
    // Retrieve the value of the UDT.  
    LargeUDT udt = (LargeUDT)reader[1];  
  
    // You can also use GetSqlValue and GetValue.  
    // LargeUDT udt = (LargeUDT)reader.GetSqlValue(1);  
    // LargeUDT udt = (LargeUDT)reader.GetValue(1);  
  
    Console.WriteLine(  
     "ID={0} LargeUDT={1}", id, udt);  
  }  
reader.close  
}  
```  
  
```vb  
Using connection As New SqlConnection( _  
    connectionString, commandString)  
    connection.Open()  
    Dim command As New SqlCommand(commandString, connection)  
    Dim reader As SqlDataReader  
    reader = command.ExecuteReader  
  
    While reader.Read()  
      ' Retrieve the value of the Primary Key column.  
      Dim id As Int32 = reader.GetInt32(0)  
  
      ' Retrieve the value of the UDT.  
      Dim udt As LargeUDT = CType(reader(1), LargeUDT)  
  
     ' You can also use GetSqlValue and GetValue.  
     ' Dim udt As LargeUDT = CType(reader.GetSqlValue(1), LargeUDT)  
     ' Dim udt As LargeUDT = CType(reader.GetValue(1), LargeUDT)  
  
      ' Print values.  
      Console.WriteLine("ID={0} LargeUDT={1}", id, udt)  
    End While  
    reader.Close()  
End Using  
```  
  
## <a name="see-also"></a>Voir aussi

- [Configuration des paramètres et des types de données des paramètres](../configuring-parameters-and-parameter-data-types.md)
- [Récupération des informations de schéma de base de données](../retrieving-database-schema-information.md)
- [Mappages de types de données SQL Server](../sql-server-data-type-mappings.md)
- [Données binaires et de valeur élevée SQL Server](sql-server-binary-and-large-value-data.md)
- [Vue d’ensemble d’ADO.NET](../ado-net-overview.md)
