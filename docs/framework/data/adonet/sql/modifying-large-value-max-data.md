---
title: Modification des données à grande valeur (max)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8aca5f00-d80e-4320-81b3-016d0466f7ee
ms.openlocfilehash: 00a4ae83270bb74e9703faebfc93e26b5c069478
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174275"
---
# <a name="modifying-large-value-max-data-in-adonet"></a>Modification de données de valeurs élevées (max) dans ADO.NET
Les types de données LOB (Large Object) sont ceux dont la taille maximale de ligne dépasse huit kilo-octets (Ko). SQL Server fournit un spécificateur `max` pour les types de données `varchar`, `nvarchar` et `varbinary` afin de permettre le stockage de valeurs pouvant atteindre 2^32 octets. Les colonnes de table et les variables Transact-SQL peuvent spécifier des types de données `varchar(max)`, `nvarchar(max)` ou `varbinary(max)`. Dans ADO.NET, les types de données `max` peuvent être extraits par un `DataReader` et spécifiés comme valeurs de paramètre d'entrée ou de sortie sans que cela nécessite une manipulation particulière. Pour les types de données `varchar` de valeur élevée, les données peuvent être récupérées et mises à jour de façon incrémentielle.  
  
 Les types de données `max` peuvent être utilisés pour effectuer des comparaisons, en tant que variables Transact-SQL, ainsi que des concaténations. Elles peuvent également être utilisées dans les clauses DISTINCT, ORDER BY et GROUP BY d’une instruction SELECT, ainsi que dans les agrégats, jointures et sous-requêtes.  
  
 Le tableau suivant présente des liens vers les ressources dans la documentation en ligne de SQL Server.  
  
 **Documentation SQL Server**  
  
1. [Utilisation de types de données de valeur élevée](https://docs.microsoft.com/previous-versions/sql/sql-server-2008/ms178158(v=sql.100))  
  
## <a name="large-value-type-restrictions"></a>Restrictions relatives aux types de valeur élevée  
 Les restrictions suivantes s’appliquent aux types de données `max`, et n’existent pas pour les types de données plus petits :  
  
- Un `sql_variant` ne peut pas contenir un type de données `varchar` de valeur élevée.  
  
- Les colonnes `varchar` de valeur élevée ne peuvent pas être spécifiées en tant que colonne clé dans un index. Elles sont autorisées dans une colonne incluse dans un index non cluster.  
  
- Les colonnes `varchar` de valeur élevée ne peuvent pas être utilisées en tant que colonnes clés de partitionnement.  
  
## <a name="working-with-large-value-types-in-transact-sql"></a>Utilisation de types de valeur élevée dans Transact-SQL  
 La fonction Transact-SQL `OPENROWSET` est une méthode unique de connexion et d’accès aux données distantes. Elle inclut toutes les informations de connexion nécessaires pour accéder à des données distantes à partir d'une source de données OLE DB. Il est possible de référencer `OPENROWSET` dans la clause FROM d’une requête comme s’il s’agissait du nom d’une table. Il peut également être référencé comme table cible d'une instruction INSERT, UPDATE ou DELETE, sujette aux capacités du fournisseur OLE DB.  
  
 La fonction `OPENROWSET` comprend le fournisseur de jeu de lignes `BULK`, qui permet de lire directement les données d'un fichier sans devoir les charger dans une table cible. Cela vous permet d’utiliser `OPENROWSET` dans une simple instruction INSERT SELECT.  
  
 Les arguments de l’option `OPENROWSET BULK` permettent d’exercer un contrôle important sur l’emplacement où commence et se termine la lecture de données, sur la manière de gérer les erreurs et sur la façon d’interpréter les données. Vous pouvez par exemple spécifier que le fichier de données soit lu comme un ensemble d’une seule ligne et d’une seule colonne du type `varbinary`, `varchar` ou `nvarchar`. Pour obtenir la syntaxe complète et les options, consultez la Documentation en ligne de SQL Server.  
  
 L’exemple suivant insère une photo dans la table ProductPhoto de l’exemple de base de données AdventureWorks. Lors de l’utilisation du fournisseur `BULK OPENROWSET`, vous devez fournir la liste nommée des colonnes même si vous n’insérez pas de valeurs dans chaque colonne. Dans ce cas, la clé primaire est définie comme une colonne d’identité et peut être omise dans la liste des colonnes. Notez que vous devez également fournir un nom de corrélation à la fin de l’instruction `OPENROWSET`, dans ce cas ThumbnailPhoto. Cela correspond à la colonne de la table `ProductPhoto` dans laquelle le fichier est chargé.  
  
```sql  
INSERT Production.ProductPhoto (  
    ThumbnailPhoto,
    ThumbnailPhotoFilePath,
    LargePhoto,
    LargePhotoFilePath)  
SELECT ThumbnailPhoto.*, null, null, N'tricycle_pink.gif'  
FROM OPENROWSET
    (BULK 'c:\images\tricycle.jpg', SINGLE_BLOB) ThumbnailPhoto  
```  
  
## <a name="updating-data-using-update-write"></a>Mise à jour de données à l'aide de UPDATE .WRITE  
 L’instruction Transact-SQL UPDATE possède une nouvelle syntaxe WRITE permettant de modifier le contenu des colonnes `varchar(max)`, `nvarchar(max)` ou `varbinary(max)`. Cela vous permet d’effectuer des mises à jour partielles des données. La syntaxe UPDATE .WRITE est présentée ici sous forme abrégée :  
  
 UPDATE  
  
 * \<l’objet>*  
  
 SET  
  
 column_name *column_name* . WRITE *(expression* @Offset @Length , , )  
  
 La méthode WRITE spécifie qu’une section de la valeur *column_name* sera modifiée. L’expression est la valeur qui sera copiée dans *column_name*, `@Offset` est le point à partir duquel l’expression sera écrite et l’argument `@Length` indique la longueur de la section dans la colonne.  
  
|Si|Alors|  
|--------|----------|  
|L’expression est définie sur NULL|`@Length` est ignoré et la valeur de *column_name* est tronquée à l’emplacement spécifié par `@Offset`.|  
|`@Offset` est NULL|L’opération de mise à jour ajoute l’expression à la fin de la valeur de *column_name* existante et `@Length` est ignoré.|  
|`@Offset` est supérieur à la longueur de la valeur column_name|SQL Server retourne une erreur.|  
|`@Length` est NULL|La mise à jour supprime toutes les données de `@Offset` jusqu’à la fin de la valeur de `column_name`.|  
  
> [!NOTE]
> Ni `@Offset` ni `@Length` ne peuvent être un nombre négatif.  
  
## <a name="example"></a> Exemple  
 Cet exemple Transact-SQL met à jour une valeur partielle dans DocumentSummary, une colonne `nvarchar(max)` dans la table Document de la base de données AdventureWorks. Le terme « components » est remplacé par le terme « features », en spécifiant le terme de remplacement, la position de départ (décalage) du terme à remplacer dans les données existantes et le nombre de caractères à remplacer (longueur). L’exemple comprend des instructions SELECT avant et après l’instruction UPDATE pour comparer les résultats.  
  
```sql
USE AdventureWorks;  
GO  
--View the existing value.  
SELECT DocumentSummary  
FROM Production.Document  
WHERE DocumentID = 3;  
GO  
-- The first sentence of the results will be:  
-- Reflectors are vital safety components of your bicycle.  
  
--Modify a single word in the DocumentSummary column  
UPDATE Production.Document  
SET DocumentSummary .WRITE (N'features',28,10)  
WHERE DocumentID = 3 ;  
GO
--View the modified value.  
SELECT DocumentSummary  
FROM Production.Document  
WHERE DocumentID = 3;  
GO  
-- The first sentence of the results will be:  
-- Reflectors are vital safety features of your bicycle.  
```  
  
## <a name="working-with-large-value-types-in-adonet"></a>Utilisation de types de valeur élevée dans ADO.NET  
 Vous pouvez utiliser des types de valeur élevée dans ADO.NET en spécifiant des types de valeur élevée comme objets <xref:System.Data.SqlClient.SqlParameter> d’un objet <xref:System.Data.SqlClient.SqlDataReader> afin de retourner un jeu de résultats, ou en utilisant un objet <xref:System.Data.SqlClient.SqlDataAdapter> pour remplir un `DataSet`/`DataTable`. Il n’y a aucune différence entre la façon dont vous travaillez avec un type de valeur élevée et le type de données de plus petite valeur associé.  
  
### <a name="using-getsqlbytes-to-retrieve-data"></a>Utilisation de GetSqlBytes pour récupérer des données  
 La méthode `GetSqlBytes` du <xref:System.Data.SqlClient.SqlDataReader> peut être utilisée pour récupérer le contenu d’une colonne `varbinary(max)`. Le fragment de code suivant suppose un objet <xref:System.Data.SqlClient.SqlCommand> nommé `cmd` qui sélectionne des données `varbinary(max)` d’une table et un objet <xref:System.Data.SqlClient.SqlDataReader> nommé `reader` qui récupère les données en tant que <xref:System.Data.SqlTypes.SqlBytes>.  
  
```vb  
reader = cmd.ExecuteReader(CommandBehavior.CloseConnection)  
While reader.Read()  
    Dim bytes As SqlBytes = reader.GetSqlBytes(0)  
End While  
```  
  
```csharp  
reader = cmd.ExecuteReader(CommandBehavior.CloseConnection);  
while (reader.Read())  
    {  
        SqlBytes bytes = reader.GetSqlBytes(0);  
    }  
```  
  
### <a name="using-getsqlchars-to-retrieve-data"></a>Utilisation de GetSqlChars pour extraire des données  
 La méthode `GetSqlChars` du <xref:System.Data.SqlClient.SqlDataReader> peut être utilisée pour récupérer le contenu d’une colonne `varchar(max)` ou `nvarchar(max)`. Le fragment de code suivant suppose un objet <xref:System.Data.SqlClient.SqlCommand> nommé `cmd` qui sélectionne des données `nvarchar(max)` d’une table et un objet <xref:System.Data.SqlClient.SqlDataReader> nommé `reader` qui récupère les données.  
  
```vb  
reader = cmd.ExecuteReader(CommandBehavior.CloseConnection)  
While reader.Read()  
    Dim buffer As SqlChars = reader.GetSqlChars(0)  
End While  
```  
  
```csharp  
reader = cmd.ExecuteReader(CommandBehavior.CloseConnection);  
while (reader.Read())  
{  
    SqlChars buffer = reader.GetSqlChars(0);  
}  
```  
  
### <a name="using-getsqlbinary-to-retrieve-data"></a>Utilisation de GetSqlBinary pour extraire des données  
 La méthode `GetSqlBinary` d’un <xref:System.Data.SqlClient.SqlDataReader> peut être utilisée pour récupérer le contenu d’une colonne `varbinary(max)`. Le fragment de code suivant suppose un objet <xref:System.Data.SqlClient.SqlCommand> nommé `cmd` qui sélectionne des données `varbinary(max)` d’une table et un objet <xref:System.Data.SqlClient.SqlDataReader> nommé `reader` qui récupère les données en tant que flux <xref:System.Data.SqlTypes.SqlBinary>.  
  
```vb  
reader = cmd.ExecuteReader(CommandBehavior.CloseConnection)  
While reader.Read()  
    Dim binaryStream As SqlBinary = reader.GetSqlBinary(0)  
End While  
```  
  
```csharp  
reader = cmd.ExecuteReader(CommandBehavior.CloseConnection);  
while (reader.Read())  
    {  
        SqlBinary binaryStream = reader.GetSqlBinary(0);  
    }  
```  
  
### <a name="using-getbytes-to-retrieve-data"></a>Utilisation de GetBytes pour extraire des données  
 La méthode `GetBytes` d’un <xref:System.Data.SqlClient.SqlDataReader> lit un flux d'octets à partir de l'offset de colonne spécifié dans un tableau d’octets commençant à l’offset de tableau donné. Le fragment de code suivant suppose un objet <xref:System.Data.SqlClient.SqlDataReader> nommé `reader` qui récupère les octets dans un tableau d’octets. Notez que, contrairement à `GetSqlBytes`, `GetBytes` nécessite une taille pour la mémoire tampon du tableau.  
  
```vb  
While reader.Read()  
    Dim buffer(4000) As Byte  
    Dim byteCount As Integer = _  
    CInt(reader.GetBytes(1, 0, buffer, 0, 4000))  
End While  
```  
  
```csharp  
while (reader.Read())  
{  
    byte[] buffer = new byte[4000];  
    long byteCount = reader.GetBytes(1, 0, buffer, 0, 4000);  
}  
```  
  
### <a name="using-getvalue-to-retrieve-data"></a>Utilisation de GetValue pour extraire des données  
 La méthode `GetValue` d’un <xref:System.Data.SqlClient.SqlDataReader> lit la valeur à partir de l’offset de colonne spécifié dans un tableau. Le fragment de code suivant suppose un objet <xref:System.Data.SqlClient.SqlDataReader> nommé `reader` qui récupère les données binaires à partir de l’offset de la première colonne, puis les données de chaîne à partir du deuxième offset de colonne.  
  
```vb  
While reader.Read()  
    ' Read the data from varbinary(max) column  
    Dim binaryData() As Byte = CByte(reader.GetValue(0))  
  
    ' Read the data from varchar(max) or nvarchar(max) column  
    Dim stringData() As String = Cstr((reader.GetValue(1))  
End While  
```  
  
```csharp  
while (reader.Read())  
{  
    // Read the data from varbinary(max) column  
    byte[] binaryData = (byte[])reader.GetValue(0);  
  
    // Read the data from varchar(max) or nvarchar(max) column  
    String stringData = (String)reader.GetValue(1);  
}  
```  
  
## <a name="converting-from-large-value-types-to-clr-types"></a>Conversion de types de valeur élevée en types CLR  
 Vous pouvez convertir le contenu d’une colonne `varchar(max)` ou `nvarchar(max)` à l’aide d’une des méthodes de conversion de chaînes, comme `ToString`. Le fragment de code suivant suppose un objet <xref:System.Data.SqlClient.SqlDataReader> nommé `reader` qui récupère les données.  
  
```vb  
While reader.Read()  
    Dim str as String = reader(0).ToString()  
    Console.WriteLine(str)  
End While  
```  
  
```csharp  
while (reader.Read())  
{  
     string str = reader[0].ToString();  
     Console.WriteLine(str);  
}  
```  
  
### <a name="example"></a> Exemple  
 Le code suivant récupère le nom et l’objet `LargePhoto` à partir de la table `ProductPhoto` dans la base de données `AdventureWorks` et l’enregistre dans un fichier. L’assembly doit être compilé avec une référence à l’espace de noms <xref:System.Drawing>.  La méthode <xref:System.Data.SqlClient.SqlDataReader.GetSqlBytes%2A> du <xref:System.Data.SqlClient.SqlDataReader> retourne un objet <xref:System.Data.SqlTypes.SqlBytes> qui expose une propriété `Stream`. Le code utilise celle-ci pour créer un nouvel objet `Bitmap`, puis l’enregistre dans le Gif `ImageFormat`.  
  
 [!code-csharp[DataWorks LargeValueType.Photo#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks LargeValueType.Photo/CS/source.cs#1)]
 [!code-vb[DataWorks LargeValueType.Photo#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks LargeValueType.Photo/VB/source.vb#1)]  
  
## <a name="using-large-value-type-parameters"></a>Utilisation de paramètres de types de valeur élevée  
 Les types de valeur élevée peuvent être utilisés dans des objets <xref:System.Data.SqlClient.SqlParameter> de la même façon que vous utilisez des types de valeur plus petits dans des objets <xref:System.Data.SqlClient.SqlParameter>. Vous pouvez extraire des types de valeur élevée en tant que valeurs <xref:System.Data.SqlClient.SqlParameter>, comme illustré dans l’exemple suivant. Le code suppose que la procédure stockée GetDocumentSummary suivante existe dans l’exemple de base de données AdventureWorks. La procédure stockée prend un caractère d’entrée nommé @DocumentID et retourne le contenu de la colonne DocumentSummary dans le paramètre de sortie @DocumentSummary.  
  
```sql
CREATE PROCEDURE GetDocumentSummary
(  
    @DocumentID int,  
    @DocumentSummary nvarchar(MAX) OUTPUT  
)  
AS  
SET NOCOUNT ON  
SELECT  @DocumentSummary=Convert(nvarchar(MAX), DocumentSummary)  
FROM    Production.Document  
WHERE   DocumentID=@DocumentID  
```  
  
### <a name="example"></a> Exemple  
 Le code ADO.NET crée des objets <xref:System.Data.SqlClient.SqlConnection> et <xref:System.Data.SqlClient.SqlCommand> pour exécuter la procédure stockée GetDocumentSummary et récupérer le résumé du document, qui est stocké en tant que type de valeur élevée. Le code transmet une valeur pour le paramètre d’entrée @DocumentID et affiche les résultats retournés dans le paramètre de sortie @DocumentSummary dans la fenêtre de console.  
  
 [!code-csharp[DataWorks LargeValueType.Param#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks LargeValueType.Param/CS/source.cs#1)]
 [!code-vb[DataWorks LargeValueType.Param#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks LargeValueType.Param/VB/source.vb#1)]  
  
## <a name="see-also"></a>Voir aussi

- [SqL Server Données binaires et à grande valeur](sql-server-binary-and-large-value-data.md)
- [Mappages de types de données SQL Server](../sql-server-data-type-mappings.md)
- [Opérations de données de serveur SQL en ADO.NET](sql-server-data-operations.md)
- [Vue d'ensemble d’ADO.NET](../ado-net-overview.md)
