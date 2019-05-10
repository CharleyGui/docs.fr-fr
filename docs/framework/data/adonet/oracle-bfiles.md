---
title: BFILE Oracle
ms.date: 03/30/2017
ms.assetid: 341bbf84-4734-4d44-8723-ccedee954e21
ms.openlocfilehash: 2d7db741cea5421b2391588c0479f44e2b478ca3
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64626422"
---
# <a name="oracle-bfiles"></a>BFILE Oracle
Le fournisseur de données .NET Framework pour Oracle inclut la classe <xref:System.Data.OracleClient.OracleBFile> qui est utilisée pour opérer avec le type de données <xref:System.Data.OracleClient.OracleType.BFile> Oracle.  
  
 Oracle **BFILE** type de données est Oracle **LOB** type de données qui contient une référence à des données binaires d’une taille maximale de 4 gigaoctets. Oracle **BFILE** diffère des autres Oracle **LOB** data types, car ses données sont stockées dans un fichier physique dans le système d’exploitation au lieu de sur le serveur. Notez que le **BFILE** type de données fournit un accès en lecture seule aux données.  
  
 Autres caractéristiques d’un **BFILE** type de données qui le distinguent un **LOB** type de données :  
  
- Il contient des données non structurées.  
  
- Il prend en charge la fragmentation côté serveur.  
  
- Il utilise une sémantique de copie de référence. Par exemple, si vous effectuez une opération de copie sur un **BFILE**, seule la **BFILE** (qui est une référence au fichier) est copiée. Les données du fichier ne sont pas copiées.  
  
 Le **BFILE** type de données doit être utilisé pour référencer les LOB de grande taille et par conséquent, pas pratique de stocker dans la base de données. Davantage de surcharge client, serveur et communication intervient lorsque vous utilisez un **BFILE** type de données par rapport à la **LOB** type de données. Il est plus efficace d’accéder à un **BFILE** si vous avez besoin uniquement d’obtenir une petite quantité de données. Il est plus efficace d'accéder à des LOB résidant en mémoire si vous avez besoin d'obtenir l'objet entier.  
  
 Chaque valeur non NULL **OracleBFile** objet est associé à deux entités qui définissent l’emplacement du fichier physique sous-jacent :  
  
1. Un objet DIRECTORY Oracle, qui est un alias de base de données pour un répertoire du système de fichiers.  
  
2. Le nom du fichier physique sous-jacent, qui se trouve dans le répertoire associé à l'objet DIRECTORY.  
  
## <a name="example"></a>Exemple  
 L’exemple c# suivant montre comment vous pouvez créer un **BFILE** dans une table Oracle, puis l’extraire sous la forme d’un **OracleBFile** objet. L’exemple montre comment utiliser le <xref:System.Data.OracleClient.OracleDataReader> objet et le **OracleBFile** **recherche** et **en lecture** méthodes. Notez que pour pouvoir utiliser cet exemple, vous devez d’abord créer un répertoire nommé « c:\\\bfiles » et le fichier nommé « MyFile.jpg » sur le serveur Oracle.  
  
```csharp  
using System;  
using System.IO;  
using System.Data;  
using System.Data.OracleClient;  
  
public class Sample  
{  
   public static void Main(string[] args)  
   {  
      OracleConnection connection = new OracleConnection(  
        "Data Source=Oracle8i;Integrated Security=yes");  
      connection.Open();  
  
      OracleCommand command = connection.CreateCommand();  
      command.CommandText =   
        "CREATE or REPLACE DIRECTORY MyDir as 'c:\\bfiles'";  
      command.ExecuteNonQuery();  
      command.CommandText =   
        "DROP TABLE MyBFileTable";  
      try {  
        command.ExecuteNonQuery();  
      }  
      catch {  
      }  
      command.CommandText =   
        "CREATE TABLE MyBFileTable(col1 number, col2 BFILE)";  
      command.ExecuteNonQuery();  
      command.CommandText =   
        "INSERT INTO MyBFileTable values ('2', BFILENAME('MyDir', " +  
        "'MyFile.jpg'))";  
      command.ExecuteNonQuery();  
      command.CommandText = "SELECT * FROM MyBFileTable";  
  
        byte[] buffer = new byte[100];  
  
      OracleDataReader reader = command.ExecuteReader();  
      using (reader) {  
          if (reader.Read()) {  
                OracleBFile bFile = reader.GetOracleBFile(1);  
                using (bFile) {  
                  bFile.Seek(0, SeekOrigin.Begin);  
                  bFile.Read(buffer, 0, 100);  
              }  
          }  
      }  
  
      connection.Close();  
   }  
  
}  
```  
  
## <a name="see-also"></a>Voir aussi

- [Oracle et ADO.NET](../../../../docs/framework/data/adonet/oracle-and-adonet.md)
- [Fournisseurs managés ADO.NET et centre de développement DataSet](https://go.microsoft.com/fwlink/?LinkId=217917)
