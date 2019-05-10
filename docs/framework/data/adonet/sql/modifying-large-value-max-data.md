---
title: Modification de données de valeurs élevées (max) dans ADO.NET
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8aca5f00-d80e-4320-81b3-016d0466f7ee
ms.openlocfilehash: 134759d729d6f291db61e6f64ebd51dfe5a4443b
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64648721"
---
# <a name="modifying-large-value-max-data-in-adonet"></a>Modification de données de valeurs élevées (max) dans ADO.NET
Les types de données LOB sont ceux dont la taille maximale de ligne dépasse 8 kilo-octets (Ko). SQL Server fournit un spécificateur `max` pour les types de données `varchar`, `nvarchar` et `varbinary` pour permettre le stockage de valeurs pouvant atteindre 2^32 octets. Les colonnes de table et les variables Transact-SQL peuvent spécifier des types de données `varchar(max)`, `nvarchar(max)` ou `varbinary(max)`. Dans ADO.NET, les types de données `max` peuvent être extraits par un `DataReader` et spécifiés comme valeurs de paramètre d'entrée ou de sortie sans que cela nécessite une manipulation particulière. Pour les types de données `varchar` volumineux, il est possible d'extraire et de mettre à jour les données de façon incrémentielle.  
  
 Les types de données `max` peuvent être utilisés pour effectuer des comparaisons, par exemple des variables Transact-SQL, ainsi que des concaténations. Ils peuvent également être utilisés dans des clauses DISTINCT, ORDER BY et GROUP BY d'une instruction SELECT ainsi que comme agrégats, jointures et sous-requêtes.  
  
 Le tableau suivant présente des liens vers les ressources dans la documentation en ligne de SQL Server.  
  
 **Documentation en ligne de SQL Server**  
  
1. [À l’aide des Types de données de valeur élevée](https://go.microsoft.com/fwlink/?LinkId=120498)  
  
## <a name="large-value-type-restrictions"></a>Restrictions relatives aux types de valeur élevée  
 Les restrictions suivantes s'appliquent aux types de données `max`, qui n'existent pas pour les types de données moins volumineux :  
  
- Un `sql_variant` ne peut pas contenir un type de données `varchar` volumineux.  
  
- Des colonnes `varchar` volumineuses ne peuvent pas être spécifiées comme colonnes clés dans un index. Elles sont autorisées dans une colonne incluse dans un index sans clusters.  
  
- Des colonnes `varchar` volumineuses ne peuvent pas être utilisées comme colonnes clés de partitionnement.  
  
## <a name="working-with-large-value-types-in-transact-sql"></a>Utilisation de types de valeur élevée dans Transact-SQL  
 La fonction Transact-SQL `OPENROWSET` est une méthode permettant de se connecter et d'accéder à des données distantes en une seule opération. Elle inclut toutes les informations de connexion nécessaires pour accéder à des données distantes à partir d'une source de données OLE DB. `OPENROWSET` peut être référencé dans la clause FROM d'une requête comme s'il s'agissait du nom d'une table. Il peut également être référencé comme table cible d'une instruction INSERT, UPDATE ou DELETE, sujette aux capacités du fournisseur OLE DB.  
  
 La fonction `OPENROWSET` inclut le fournisseur de jeu de lignes `BULK`, qui permet de lire directement les données d'un fichier sans devoir les charger dans une table cible. Cela vous permet d'utiliser `OPENROWSET` dans une simple instruction INSERT SELECT.  
  
 Le `OPENROWSET BULK` arguments de l’option fournissent un contrôle important sur l’emplacement où commence et se termine la lecture des données, comment gérer les erreurs et l’interprétation des données. Par exemple, vous pouvez spécifier que le fichier de données doit être lu comme une seule ligne, un jeu de lignes en une seule colonne de type `varbinary`, `varchar` ou `nvarchar`. Pour découvrir la syntaxe complète et les options, voir la documentation en ligne de SQL Server.  
  
 L'exemple suivant insère une photo dans la table ProductPhoto de l'exemple de base de données AdventureWorks. Lorsque vous utilisez le `BULK OPENROWSET` fournisseur, vous devez fournir la liste nommée des colonnes même si vous n’insérez pas de valeurs dans chaque colonne. Dans ce cas, la clé primaire est définie comme une colonne identité et peut être omise de la liste des colonnes. Notez que vous devez également fournir un nom de corrélation à la fin de l'instruction `OPENROWSET` ; en l'occurrence, il s'agit de ThumbnailPhoto. Cela établit une corrélation avec la colonne de la table `ProductPhoto` dans laquelle le fichier est chargé.  
  
```  
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
 L'instruction Transact-SQL UPDATE utilise une nouvelle syntaxe WRITE pour modifier le contenu de colonnes `varchar(max)`, `nvarchar(max)` ou `varbinary(max)`. Cela vous permet d'effectuer des mises à jour partielles des données. La syntaxe de UPDATE .WRITE est présentée ici sous forme abrégée :  
  
 UPDATE  
  
 { *\<object>* }  
  
 SET  
  
 { *column_name* = { .WRITE ( *expression* , @Offset , @Length ) }  
  
 La méthode WRITE Spécifie qu’une section de la valeur de la *column_name* sera modifiée. L’expression est la valeur qui sera copiée dans le *column_name*, le `@Offset` est le point à partir duquel l’expression sera écrite et le `@Length` argument est la longueur de la section dans la colonne.  
  
|If|Then|  
|--------|----------|  
|La valeur de l'expression est NULL.|`@Length` est ignoré et la valeur dans *column_name* est tronquée à l’emplacement spécifié `@Offset`.|  
|`@Offset` a la valeur NULL|L’opération de mise à jour ajoute l’expression à la fin de l’existante *column_name* valeur et `@Length` est ignoré.|  
|`@Offset` est supérieur à la longueur de la valeur column_name.|SQL Server retourne une erreur.|  
|`@Length` a la valeur NULL|L'opération de mise à jour supprime toutes les données à partir de `@Offset` jusqu'à la fin de la valeur `column_name`.|  
  
> [!NOTE]
>  Ni `@Offset` ni `@Length` ne peuvent avoir pour valeur un nombre négatif.  
  
## <a name="example"></a>Exemple  
 Cet exemple Transact-SQL met à jour une valeur partielle dans DocumentSummary, colonne `nvarchar(max)` dans la table Document de la base de données AdventureWorks. Le mot « components » est remplacé par le mot « features » en spécifiant le mot de remplacement, l’emplacement où commence (offset) le mot à remplacer dans les données existantes et le nombre de caractères à remplacer (length). L'exemple inclut des instructions SELECT devant et derrière l'instruction UPDATE afin de comparer les résultats.  
  
```  
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
 Vous pouvez travailler avec les types de valeur volumineux dans ADO.NET en spécifiant les types de valeur volumineux comme <xref:System.Data.SqlClient.SqlParameter> des objets dans un <xref:System.Data.SqlClient.SqlDataReader> pour retourner un résultat défini, ou en utilisant un <xref:System.Data.SqlClient.SqlDataAdapter> pour remplir un `DataSet` / `DataTable`. Il n'y a pas de différence d'utilisation entre un type de valeur élevée et le type de données de valeur moins élevée apparenté.  
  
### <a name="using-getsqlbytes-to-retrieve-data"></a>Utilisation de GetSqlBytes pour extraire des données  
 La méthode `GetSqlBytes` du <xref:System.Data.SqlClient.SqlDataReader> permet d'extraire le contenu d'une colonne `varbinary(max)`. Le fragment de code suivant est basé sur l'hypothèse de l'existence d'un objet <xref:System.Data.SqlClient.SqlCommand> nommé `cmd` qui sélectionne des données `varbinary(max)` dans une table et d'un objet <xref:System.Data.SqlClient.SqlDataReader> nommé `reader` qui extrait les données comme <xref:System.Data.SqlTypes.SqlBytes>.  
  
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
 La méthode `GetSqlChars` de l'objet <xref:System.Data.SqlClient.SqlDataReader> permet d'extraire le contenu d'une colonne `varchar(max)` ou `nvarchar(max)`. Le fragment de code suivant est basé sur l'hypothèse de l'existence d'un objet <xref:System.Data.SqlClient.SqlCommand> nommé `cmd` qui sélectionne des données `nvarchar(max)` dans une table et d'un objet <xref:System.Data.SqlClient.SqlDataReader> nommé `reader` qui extrait les données.  
  
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
 La méthode `GetSqlBinary` d'un objet <xref:System.Data.SqlClient.SqlDataReader> permet d'extraire le contenu d'une colonne `varbinary(max)`. Le fragment de code suivant est basé sur l'hypothèse de l'existence d'un objet <xref:System.Data.SqlClient.SqlCommand> nommé `cmd` qui sélectionne des données `varbinary(max)` dans une table et d'un objet <xref:System.Data.SqlClient.SqlDataReader> nommé `reader` qui extrait les données comme flux <xref:System.Data.SqlTypes.SqlBinary>.  
  
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
 La méthode `GetBytes` d'un <xref:System.Data.SqlClient.SqlDataReader> lit un flux d'octets à partir de l'emplacement de décalage (offset) de colonne spécifié dans un tableau d'octets commençant au décalage de tableau spécifié. Le fragment de code suivant est basé sur l'hypothèse de l'existence d'un objet <xref:System.Data.SqlClient.SqlDataReader> nommé `reader` qui extrait des octets vers un tableau d'octets. Notez que, contrairement à `GetSqlBytes`, `GetBytes` requiert une taille pour le tampon de tableau.  
  
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
 La méthode `GetValue` d'un objet <xref:System.Data.SqlClient.SqlDataReader> lit la valeur à partir de l'emplacement de décalage (offset) de colonne spécifié dans un tableau. Le fragment de code suivant est basé sur l'hypothèse de l'existence d'un objet <xref:System.Data.SqlClient.SqlDataReader> nommé `reader` qui extrait des données binaires à partir du premier emplacement de décalage (offset) de colonne, puis chaîne les données à partir du second emplacement de décalage de colonne.  
  
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
 Vous pouvez convertir le contenu d'une colonne `varchar(max)` ou `nvarchar(max)` à l'aide de n'importe quelle méthode de conversion de chaîne, telle que `ToString`. Le fragment de code suivant est basé sur l'hypothèse de l'existence d'un objet <xref:System.Data.SqlClient.SqlDataReader> nommé `reader` qui extrait les données.  
  
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
  
### <a name="example"></a>Exemple  
 Le code suivant extrait le nom et l'objet `LargePhoto` de la table `ProductPhoto` dans la base de données `AdventureWorks` et les enregistre dans un fichier. L'assembly doit être compilé avec une référence à l'espace de noms <xref:System.Drawing>.  La méthode <xref:System.Data.SqlClient.SqlDataReader.GetSqlBytes%2A> de l'objet <xref:System.Data.SqlClient.SqlDataReader> retourne un objet <xref:System.Data.SqlTypes.SqlBytes> qui expose une propriété `Stream`. Le code utilise celle-ci pour créer un nouveau `Bitmap` de l’objet, puis l’enregistre dans le fichier Gif `ImageFormat`.  
  
 [!code-csharp[DataWorks LargeValueType.Photo#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks LargeValueType.Photo/CS/source.cs#1)]
 [!code-vb[DataWorks LargeValueType.Photo#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks LargeValueType.Photo/VB/source.vb#1)]  
  
## <a name="using-large-value-type-parameters"></a>Utilisation de paramètres de types de valeur élevée  
 Vous pouvez utiliser des types de valeur élevée dans des objets <xref:System.Data.SqlClient.SqlParameter> de la même manière que des types de valeur moins élevée dans des objets <xref:System.Data.SqlClient.SqlParameter>. Vous pouvez récupérer des types de valeur volumineux comme <xref:System.Data.SqlClient.SqlParameter> des valeurs, comme indiqué dans l’exemple suivant. Le code est basé sur l'hypothèse que la procédure stockée GetDocumentSummary suivante existe dans l'exemple de base de données AdventureWorks. La procédure stockée accepte un paramètre d’entrée nommé @DocumentID et retourne le contenu de la colonne DocumentSummary dans le @DocumentSummary paramètre de sortie.  
  
```  
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
  
### <a name="example"></a>Exemple  
 Le code ADO.NET crée les objets <xref:System.Data.SqlClient.SqlConnection> et <xref:System.Data.SqlClient.SqlCommand> pour exécuter la procédure stockée GetDocumentSummary et extraire le résumé du document qui est stocké comme type de valeur élevée. Le code transmet une valeur le @DocumentID paramètre d’entrée et affiche les résultats sont transmis dans le @DocumentSummary paramètre dans la fenêtre de Console de sortie.  
  
 [!code-csharp[DataWorks LargeValueType.Param#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks LargeValueType.Param/CS/source.cs#1)]
 [!code-vb[DataWorks LargeValueType.Param#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks LargeValueType.Param/VB/source.vb#1)]  
  
## <a name="see-also"></a>Voir aussi

- [Données binaires et de valeur élevée SQL Server](../../../../../docs/framework/data/adonet/sql/sql-server-binary-and-large-value-data.md)
- [Mappages de types de données SQL Server](../../../../../docs/framework/data/adonet/sql-server-data-type-mappings.md)
- [Opérations sur les données SQL Server dans ADO.NET](../../../../../docs/framework/data/adonet/sql/sql-server-data-operations.md)
- [Fournisseurs managés ADO.NET et centre de développement DataSet](https://go.microsoft.com/fwlink/?LinkId=217917)
