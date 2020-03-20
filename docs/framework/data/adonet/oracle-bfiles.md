---
title: BFILE Oracle
ms.date: 03/30/2017
ms.assetid: 341bbf84-4734-4d44-8723-ccedee954e21
ms.openlocfilehash: 40060a7ea8576e08140d972072d086606d640366
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79149438"
---
# <a name="oracle-bfiles"></a>BFILE Oracle
Le fournisseur de données .NET Framework pour Oracle inclut la classe <xref:System.Data.OracleClient.OracleBFile> qui est utilisée pour opérer avec le type de données <xref:System.Data.OracleClient.OracleType.BFile> Oracle.  
  
 Le type de données Oracle **BFILE** est un type de données Oracle **LOB** qui contient une référence aux données binaires d’une taille maximale de 4 gigaoctets. Un Oracle **BFILE** diffère des autres types de données Oracle **LOB** en ce que ses données sont stockées dans un fichier physique dans le système d’exploitation plutôt que sur le serveur. Notez que le type de données **BFILE** fournit un accès de lecture uniquement aux données.  
  
 D’autres caractéristiques d’un type de données **BFILE** qui le distinguent d’un type de données **LOB** sont qu’il est :  
  
- Il contient des données non structurées.  
  
- Il prend en charge la fragmentation côté serveur.  
  
- Il utilise une sémantique de copie de référence. Par exemple, si vous effectuez une opération de copie sur un **BFILE**, seul le localisateur **BFILE** (qui est une référence au fichier) est copié. Les données du fichier ne sont pas copiées.  
  
 Le type de données **BFILE** doit être utilisé pour le référencement des LOB de grande taille et, par conséquent, pas pratique à stocker dans la base de données. Plus de frais généraux de client, de serveur et de communication sont impliqués lors de l’utilisation d’un type de données **BFILE** par rapport au type de données **LOB.** Il est plus efficace d’accéder à un **BFILE** si vous n’avez besoin que d’obtenir une petite quantité de données. Il est plus efficace d'accéder à des LOB résidant en mémoire si vous avez besoin d'obtenir l'objet entier.  
  
 Chaque objet **OracleBFile** non-NULL est associé à deux entités qui définissent l’emplacement du fichier physique sous-jacent :  
  
1. Un objet DIRECTORY Oracle, qui est un alias de base de données pour un répertoire du système de fichiers.  
  
2. Le nom du fichier physique sous-jacent, qui se trouve dans le répertoire associé à l'objet DIRECTORY.  
  
## <a name="example"></a> Exemple  
 L’exemple CMD suivant montre comment vous pouvez créer un **BFILE** dans une table Oracle, puis le récupérer sous la forme d’un objet **OracleBFile.** L’exemple montre <xref:System.Data.OracleClient.OracleDataReader> l’utilisation de l’objet et des méthodes **OracleBFile** **Seek** and **Read.** Notez que pour utiliser cet exemple, vous devez d’abord créer un répertoire nommé "c:\\'bfiles" et fichier nommé "MyFile.jpg" sur le serveur Oracle.  
  
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

- [Oracle et ADO.NET](oracle-and-adonet.md)
- [Vue d'ensemble d’ADO.NET](ado-net-overview.md)
