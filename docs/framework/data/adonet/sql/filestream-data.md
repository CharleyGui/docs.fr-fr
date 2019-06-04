---
title: Données FILESTREAM
ms.date: 03/30/2017
ms.assetid: bd8b845c-0f09-4295-b466-97ef106eefa8
ms.openlocfilehash: 4edd03a38f8f5df6cb4fb9c2446f966dfe601564
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2019
ms.locfileid: "66490064"
---
# <a name="filestream-data"></a>Données FILESTREAM

L'attribut de stockage FILESTREAM est destiné aux données binaires (BLOB) stockées dans une colonne varbinary(max). Avant l'introduction de cet attribut, le stockage des données binaires nécessitait un traitement spécial. Les données non structurées, telles que les documents texte, les images et les vidéos, sont souvent stockées en dehors de la base de données, ce qui rend difficile leur gestion.

> [!NOTE]
> Vous devez installer le .NET Framework 3.5 SP1 (ou version ultérieure) pour utiliser les données FILESTREAM avec SqlClient.

Si vous spécifiez l'attribut FILESTREAM sur une colonne varbinary(max), SQL Server stocke les données sur le système de fichiers NTFS local au lieu du fichier de base de données. Même si elles sont stockées séparément, vous pouvez utiliser les mêmes instructions Transact-SQL prises en charge pour l'utilisation des données varbinary(max) stockées dans la base.

## <a name="sqlclient-support-for-filestream"></a>Prise en charge de SqlClient pour FILESTREAM

Le fournisseur de données .NET Framework pour SQL Server, <xref:System.Data.SqlClient>, prend en charge la lecture et écriture aux données FILESTREAM en utilisant le <xref:System.Data.SqlTypes.SqlFileStream> classe définie dans le <xref:System.Data.SqlTypes> espace de noms. `SqlFileStream` hérite de la classe <xref:System.IO.Stream>, qui fournit les méthodes permettant de lire et d'écrire vers les flux de données. La lecture à partir d'un flux transfère les données du flux dans une structure de données, tel qu'un tableau d'octets. L'écriture transfère les données de la structure dans un flux.

### <a name="creating-the-sql-server-table"></a>Création de la table SQL Server

L'instruction Transact-SQL suivante crée une table nommée employees et y insère une ligne de données. Après avoir activé le stockage FILESTREAM, vous pouvez combiner cette table aux exemples de code suivants. Les liens vers des ressources dans la documentation en ligne de SQL Server se trouvent à la fin de cette rubrique.

```sql
CREATE TABLE employees
(
  EmployeeId INT  NOT NULL  PRIMARY KEY,
  Photo VARBINARY(MAX) FILESTREAM  NULL,
  RowGuid UNIQUEIDENTIFIER  NOT NULL  ROWGUIDCOL
  UNIQUE DEFAULT NEWID()
)
GO
Insert into employees
Values(1, 0x00, default)
GO
```

### <a name="example-reading-overwriting-and-inserting-filestream-data"></a>Exemple : Lecture, remplacement et insertion de données FILESTREAM

L'exemple suivant montre comment lire les données à partir d'un fichier FILESTREAM. Le code obtient le chemin d’accès logique au fichier, en affectant la valeur `FileAccess` à `Read` et la valeur `FileOptions` à `SequentialScan`. Puis le code lit les octets à partir du SqlFileStream dans la mémoire tampon. Les octets s'affichent ensuite dans la fenêtre de console.

Cet exemple montre également comment écrire des données dans un fichier FILESTREAM dans lequel toutes les données existantes sont remplacées. Le code obtient le chemin d’accès logique au fichier et crée l’élément `SqlFileStream`, en affectant la valeur `FileAccess` à `Write` et la valeur `FileOptions` à `SequentialScan`. Un seul octet est écrit dans le `SqlFileStream`, remplaçant ainsi les données du fichier.

L'exemple également montre comment écrire des données dans un fichier FILESTREAM en utilisant la méthode Seek pour ajouter des données à la fin du fichier. Le code obtient le chemin d’accès logique au fichier et crée l’élément `SqlFileStream`, en affectant la valeur `FileAccess` à `ReadWrite` et la valeur `FileOptions` à `SequentialScan`. Le code utilise la méthode Seek pour ajouter un seul octet à la fin du fichier existant.

```csharp
using System;
using System.Data.SqlClient;
using System.Data.SqlTypes;
using System.Data;
using System.IO;

namespace FileStreamTest
{
    class Program
    {
        static void Main(string[] args)
        {
            SqlConnectionStringBuilder builder = new SqlConnectionStringBuilder("server=(local);integrated security=true;database=myDB");
            ReadFileStream(builder);
            OverwriteFileStream(builder);
            InsertFileStream(builder);

            Console.WriteLine("Done");
        }

        private static void ReadFileStream(SqlConnectionStringBuilder connStringBuilder)
        {
            using (SqlConnection connection = new SqlConnection(connStringBuilder.ToString()))
            {
                connection.Open();
                SqlCommand command = new SqlCommand("SELECT TOP(1) Photo.PathName(), GET_FILESTREAM_TRANSACTION_CONTEXT() FROM employees", connection);

                SqlTransaction tran = connection.BeginTransaction(IsolationLevel.ReadCommitted);
                command.Transaction = tran;

                using (SqlDataReader reader = command.ExecuteReader())
                {
                    while (reader.Read())
                    {
                        // Get the pointer for the file
                        string path = reader.GetString(0);
                        byte[] transactionContext = reader.GetSqlBytes(1).Buffer;

                        // Create the SqlFileStream
                        using (Stream fileStream = new SqlFileStream(path, transactionContext, FileAccess.Read, FileOptions.SequentialScan, allocationSize: 0))
                        {
                            // Read the contents as bytes and write them to the console
                            for (long index = 0; index < fileStream.Length; index++)
                            {
                                Console.WriteLine(fileStream.ReadByte());
                            }
                        }
                    }
                }
                tran.Commit();
            }
        }

        private static void OverwriteFileStream(SqlConnectionStringBuilder connStringBuilder)
        {
            using (SqlConnection connection = new SqlConnection(connStringBuilder.ToString()))
            {
                connection.Open();

                SqlCommand command = new SqlCommand("SELECT TOP(1) Photo.PathName(), GET_FILESTREAM_TRANSACTION_CONTEXT() FROM employees", connection);

                SqlTransaction tran = connection.BeginTransaction(IsolationLevel.ReadCommitted);
                command.Transaction = tran;

                using (SqlDataReader reader = command.ExecuteReader())
                {
                    while (reader.Read())
                    {
                        // Get the pointer for file
                        string path = reader.GetString(0);
                        byte[] transactionContext = reader.GetSqlBytes(1).Buffer;

                        // Create the SqlFileStream
                        using (Stream fileStream = new SqlFileStream(path, transactionContext, FileAccess.Write, FileOptions.SequentialScan, allocationSize: 0))
                        {
                            // Write a single byte to the file. This will
                            // replace any data in the file.
                            fileStream.WriteByte(0x01);
                        }
                    }
                }
                tran.Commit();
            }
        }

        private static void InsertFileStream(SqlConnectionStringBuilder connStringBuilder)
        {
            using (SqlConnection connection = new SqlConnection(connStringBuilder.ToString()))
            {
                connection.Open();

                SqlCommand command = new SqlCommand("SELECT TOP(1) Photo.PathName(), GET_FILESTREAM_TRANSACTION_CONTEXT() FROM employees", connection);

                SqlTransaction tran = connection.BeginTransaction(IsolationLevel.ReadCommitted);
                command.Transaction = tran;

                using (SqlDataReader reader = command.ExecuteReader())
                {
                    while (reader.Read())
                    {
                        // Get the pointer for file
                        string path = reader.GetString(0);
                        byte[] transactionContext = reader.GetSqlBytes(1).Buffer;

                        using (Stream fileStream = new SqlFileStream(path, transactionContext, FileAccess.ReadWrite, FileOptions.SequentialScan, allocationSize: 0))
                        {
                            // Seek to the end of the file
                            fileStream.Seek(0, SeekOrigin.End);

                            // Append a single byte
                            fileStream.WriteByte(0x01);
                        }
                    }
                }
                tran.Commit();
            }

        }
    }
}
```

Pour obtenir un autre exemple, consultez [comment stocker et récupérer des données binaires dans une colonne de flux de fichier](https://www.codeproject.com/Articles/32216/How-to-store-and-fetch-binary-data-into-a-file-str).

## <a name="resources-in-sql-server-books-online"></a>Ressources dans la documentation en ligne de SQL Server.

La documentation complète relative à FILESTREAM se trouve dans les sections suivantes dans la documentation en ligne de SQL Server.

|Rubrique|Description|
|-----------|-----------------|
|[FILESTREAM (SQL Server)](/sql/relational-databases/blob/filestream-sql-server)|Explique quand utiliser le stockage FILESTREAM et comment il intègre le moteur de base de données SQL Server avec un système de fichiers NTFS.|
|[Créer des Applications clientes pour les données FILESTREAM](/sql/relational-databases/blob/create-client-applications-for-filestream-data)|Décrit les fonctions API de Windows pour utiliser les données FILESTREAM.|
|[FILESTREAM et autres fonctionnalités SQL Server](/sql/relational-databases/blob/filestream-compatibility-with-other-sql-server-features)|Fournit des considérations, indications et limitations relatives à l’utilisation des données FILESTREAM avec d’autres fonctionnalités de SQL Server.|

## <a name="see-also"></a>Voir aussi

- [Types de données SQL Server et ADO.NET](../../../../../docs/framework/data/adonet/sql/sql-server-data-types.md)
- [Extraction et modification de données dans ADO.NET](../../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)
- [Sécurité d’accès du code et ADO.NET](../../../../../docs/framework/data/adonet/code-access-security.md)
- [Données binaires et de valeur élevée SQL Server](../../../../../docs/framework/data/adonet/sql/sql-server-binary-and-large-value-data.md)
- [Vue d’ensemble d’ADO.NET](../../../../../docs/framework/data/adonet/ado-net-overview.md)
