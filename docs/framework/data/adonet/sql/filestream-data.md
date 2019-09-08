---
title: Données FILESTREAM
ms.date: 03/30/2017
ms.assetid: bd8b845c-0f09-4295-b466-97ef106eefa8
ms.openlocfilehash: 87bed5dd345c240cc00b2c36aa976ec53fe63b93
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70794097"
---
# <a name="filestream-data"></a><span data-ttu-id="9b0e1-102">Données FILESTREAM</span><span class="sxs-lookup"><span data-stu-id="9b0e1-102">FILESTREAM Data</span></span>

<span data-ttu-id="9b0e1-103">L'attribut de stockage FILESTREAM est destiné aux données binaires (BLOB) stockées dans une colonne varbinary(max).</span><span class="sxs-lookup"><span data-stu-id="9b0e1-103">The FILESTREAM storage attribute is for binary (BLOB) data stored in a varbinary(max) column.</span></span> <span data-ttu-id="9b0e1-104">Avant l'introduction de cet attribut, le stockage des données binaires nécessitait un traitement spécial.</span><span class="sxs-lookup"><span data-stu-id="9b0e1-104">Before FILESTREAM, storing binary data required special handling.</span></span> <span data-ttu-id="9b0e1-105">Les données non structurées, telles que les documents texte, les images et les vidéos, sont souvent stockées en dehors de la base de données, ce qui rend difficile leur gestion.</span><span class="sxs-lookup"><span data-stu-id="9b0e1-105">Unstructured data, such as text documents, images and video, is often stored outside of the database, making it difficult to manage.</span></span>

> [!NOTE]
> <span data-ttu-id="9b0e1-106">Vous devez installer le .NET Framework 3.5 SP1 (ou version ultérieure) pour utiliser les données FILESTREAM avec SqlClient.</span><span class="sxs-lookup"><span data-stu-id="9b0e1-106">You must install the .NET Framework 3.5 SP1 (or later) to work with FILESTREAM data using SqlClient.</span></span>

<span data-ttu-id="9b0e1-107">Si vous spécifiez l'attribut FILESTREAM sur une colonne varbinary(max), SQL Server stocke les données sur le système de fichiers NTFS local au lieu du fichier de base de données.</span><span class="sxs-lookup"><span data-stu-id="9b0e1-107">Specifying the FILESTREAM attribute on a varbinary(max) column causes SQL Server to store the data on the local NTFS file system instead of in the database file.</span></span> <span data-ttu-id="9b0e1-108">Même si elles sont stockées séparément, vous pouvez utiliser les mêmes instructions Transact-SQL prises en charge pour l'utilisation des données varbinary(max) stockées dans la base.</span><span class="sxs-lookup"><span data-stu-id="9b0e1-108">Although it is stored separately, you can use the same Transact-SQL statements that are supported for working with varbinary(max) data that is stored in the database.</span></span>

## <a name="sqlclient-support-for-filestream"></a><span data-ttu-id="9b0e1-109">Prise en charge de SqlClient pour FILESTREAM</span><span class="sxs-lookup"><span data-stu-id="9b0e1-109">SqlClient Support for FILESTREAM</span></span>

<span data-ttu-id="9b0e1-110">La .NET Framework fournisseur de données pour SQL Server, <xref:System.Data.SqlClient>, prend en charge la lecture et l’écriture de <xref:System.Data.SqlTypes.SqlFileStream> données FILESTREAM à l' <xref:System.Data.SqlTypes> aide de la classe définie dans l’espace de noms.</span><span class="sxs-lookup"><span data-stu-id="9b0e1-110">The .NET Framework Data Provider for SQL Server, <xref:System.Data.SqlClient>, supports reading and writing to FILESTREAM data using the <xref:System.Data.SqlTypes.SqlFileStream> class defined in the <xref:System.Data.SqlTypes> namespace.</span></span> <span data-ttu-id="9b0e1-111">`SqlFileStream` hérite de la classe <xref:System.IO.Stream>, qui fournit les méthodes permettant de lire et d'écrire vers les flux de données.</span><span class="sxs-lookup"><span data-stu-id="9b0e1-111">`SqlFileStream` inherits from the <xref:System.IO.Stream> class, which provides methods for reading and writing to streams of data.</span></span> <span data-ttu-id="9b0e1-112">La lecture à partir d'un flux transfère les données du flux dans une structure de données, tel qu'un tableau d'octets.</span><span class="sxs-lookup"><span data-stu-id="9b0e1-112">Reading from a stream transfers data from the stream into a data structure, such as an array of bytes.</span></span> <span data-ttu-id="9b0e1-113">L'écriture transfère les données de la structure dans un flux.</span><span class="sxs-lookup"><span data-stu-id="9b0e1-113">Writing transfers the data from the data structure into a stream.</span></span>

### <a name="creating-the-sql-server-table"></a><span data-ttu-id="9b0e1-114">Création de la table SQL Server</span><span class="sxs-lookup"><span data-stu-id="9b0e1-114">Creating the SQL Server Table</span></span>

<span data-ttu-id="9b0e1-115">L'instruction Transact-SQL suivante crée une table nommée employees et y insère une ligne de données.</span><span class="sxs-lookup"><span data-stu-id="9b0e1-115">The following Transact-SQL statements creates a table named employees and inserts a row of data.</span></span> <span data-ttu-id="9b0e1-116">Après avoir activé le stockage FILESTREAM, vous pouvez combiner cette table aux exemples de code suivants.</span><span class="sxs-lookup"><span data-stu-id="9b0e1-116">Once you have enabled FILESTREAM storage, you can use this table in conjunction with the code examples that follow.</span></span> <span data-ttu-id="9b0e1-117">Les liens vers les ressources dans Documentation en ligne de SQL Server se trouvent à la fin de cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="9b0e1-117">The links to resources in SQL Server Books Online are located at the end of this topic.</span></span>

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

### <a name="example-reading-overwriting-and-inserting-filestream-data"></a><span data-ttu-id="9b0e1-118">Exemple : Lecture, remplacement et insertion de données FILESTREAM</span><span class="sxs-lookup"><span data-stu-id="9b0e1-118">Example: Reading, Overwriting, and Inserting FILESTREAM Data</span></span>

<span data-ttu-id="9b0e1-119">L'exemple suivant montre comment lire les données à partir d'un fichier FILESTREAM.</span><span class="sxs-lookup"><span data-stu-id="9b0e1-119">The following sample demonstrates how to read data from a FILESTREAM.</span></span> <span data-ttu-id="9b0e1-120">Le code obtient le chemin d’accès logique au fichier, en affectant la valeur `FileAccess` à `Read` et la valeur `FileOptions` à `SequentialScan`.</span><span class="sxs-lookup"><span data-stu-id="9b0e1-120">The code gets the logical path to the file, setting the `FileAccess` to `Read` and the `FileOptions` to `SequentialScan`.</span></span> <span data-ttu-id="9b0e1-121">Puis le code lit les octets à partir du SqlFileStream dans la mémoire tampon.</span><span class="sxs-lookup"><span data-stu-id="9b0e1-121">The code then reads the bytes from the SqlFileStream into the buffer.</span></span> <span data-ttu-id="9b0e1-122">Les octets s'affichent ensuite dans la fenêtre de console.</span><span class="sxs-lookup"><span data-stu-id="9b0e1-122">The bytes are then written to the console window.</span></span>

<span data-ttu-id="9b0e1-123">Cet exemple montre également comment écrire des données dans un fichier FILESTREAM dans lequel toutes les données existantes sont remplacées.</span><span class="sxs-lookup"><span data-stu-id="9b0e1-123">The sample also demonstrates how to write data to a FILESTREAM in which all existing data is overwritten.</span></span> <span data-ttu-id="9b0e1-124">Le code obtient le chemin d’accès logique au fichier et crée l’élément `SqlFileStream`, en affectant la valeur `FileAccess` à `Write` et la valeur `FileOptions` à `SequentialScan`.</span><span class="sxs-lookup"><span data-stu-id="9b0e1-124">The code gets the logical path to the file and creates the `SqlFileStream`, setting the `FileAccess` to `Write` and the `FileOptions` to `SequentialScan`.</span></span> <span data-ttu-id="9b0e1-125">Un seul octet est écrit dans le `SqlFileStream`, remplaçant ainsi les données du fichier.</span><span class="sxs-lookup"><span data-stu-id="9b0e1-125">A single byte is written to the `SqlFileStream`, replacing any data in the file.</span></span>

<span data-ttu-id="9b0e1-126">L'exemple également montre comment écrire des données dans un fichier FILESTREAM en utilisant la méthode Seek pour ajouter des données à la fin du fichier.</span><span class="sxs-lookup"><span data-stu-id="9b0e1-126">The sample also demonstrates how to write data to a FILESTREAM by using the Seek method to append data to the end of the file.</span></span> <span data-ttu-id="9b0e1-127">Le code obtient le chemin d’accès logique au fichier et crée l’élément `SqlFileStream`, en affectant la valeur `FileAccess` à `ReadWrite` et la valeur `FileOptions` à `SequentialScan`.</span><span class="sxs-lookup"><span data-stu-id="9b0e1-127">The code gets the logical path to the file and creates the `SqlFileStream`, setting the `FileAccess` to `ReadWrite` and the `FileOptions` to `SequentialScan`.</span></span> <span data-ttu-id="9b0e1-128">Le code utilise la méthode Seek pour ajouter un seul octet à la fin du fichier existant.</span><span class="sxs-lookup"><span data-stu-id="9b0e1-128">The code uses the Seek method to seek to the end of the file, appending a single byte to the existing file.</span></span>

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

<span data-ttu-id="9b0e1-129">Pour un autre exemple, consultez [Comment stocker et récupérer des données binaires dans une colonne de flux de fichier](https://www.codeproject.com/Articles/32216/How-to-store-and-fetch-binary-data-into-a-file-str).</span><span class="sxs-lookup"><span data-stu-id="9b0e1-129">For another sample, see [How to store and fetch binary data into a file stream column](https://www.codeproject.com/Articles/32216/How-to-store-and-fetch-binary-data-into-a-file-str).</span></span>

## <a name="resources-in-sql-server-books-online"></a><span data-ttu-id="9b0e1-130">Ressources dans la documentation en ligne de SQL Server.</span><span class="sxs-lookup"><span data-stu-id="9b0e1-130">Resources in SQL Server Books Online</span></span>

<span data-ttu-id="9b0e1-131">La documentation complète de FILESTREAM se trouve dans les sections suivantes de Documentation en ligne de SQL Server.</span><span class="sxs-lookup"><span data-stu-id="9b0e1-131">The complete documentation for FILESTREAM is located in the following sections in SQL Server Books Online.</span></span>

|<span data-ttu-id="9b0e1-132">Rubrique</span><span class="sxs-lookup"><span data-stu-id="9b0e1-132">Topic</span></span>|<span data-ttu-id="9b0e1-133">Description</span><span class="sxs-lookup"><span data-stu-id="9b0e1-133">Description</span></span>|
|-----------|-----------------|
|[<span data-ttu-id="9b0e1-134">FILESTREAM (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="9b0e1-134">FILESTREAM (SQL Server)</span></span>](/sql/relational-databases/blob/filestream-sql-server)|<span data-ttu-id="9b0e1-135">Explique quand utiliser le stockage FILESTREAM et comment il intègre le moteur de base de données SQL Server avec un système de fichiers NTFS.</span><span class="sxs-lookup"><span data-stu-id="9b0e1-135">Describes when to use FILESTREAM storage and how it integrates the SQL Server Database Engine with an NTFS file system.</span></span>|
|[<span data-ttu-id="9b0e1-136">Créer des applications clientes pour les données FILESTREAM</span><span class="sxs-lookup"><span data-stu-id="9b0e1-136">Create Client Applications for FILESTREAM Data</span></span>](/sql/relational-databases/blob/create-client-applications-for-filestream-data)|<span data-ttu-id="9b0e1-137">Décrit les fonctions de l’API Windows permettant d’utiliser des données FILESTREAM.</span><span class="sxs-lookup"><span data-stu-id="9b0e1-137">Describes the Windows API functions for working with FILESTREAM data.</span></span>|
|[<span data-ttu-id="9b0e1-138">FILESTREAM et autres fonctionnalités de SQL Server</span><span class="sxs-lookup"><span data-stu-id="9b0e1-138">FILESTREAM and Other SQL Server Features</span></span>](/sql/relational-databases/blob/filestream-compatibility-with-other-sql-server-features)|<span data-ttu-id="9b0e1-139">Fournit des considérations, indications et limitations relatives à l’utilisation des données FILESTREAM avec d’autres fonctionnalités de SQL Server.</span><span class="sxs-lookup"><span data-stu-id="9b0e1-139">Provides considerations, guidelines and limitations for using FILESTREAM data with other features of SQL Server.</span></span>|

## <a name="see-also"></a><span data-ttu-id="9b0e1-140">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9b0e1-140">See also</span></span>

- [<span data-ttu-id="9b0e1-141">Types de données SQL Server et ADO.NET</span><span class="sxs-lookup"><span data-stu-id="9b0e1-141">SQL Server Data Types and ADO.NET</span></span>](sql-server-data-types.md)
- [<span data-ttu-id="9b0e1-142">Extraction et modification de données dans ADO.NET</span><span class="sxs-lookup"><span data-stu-id="9b0e1-142">Retrieving and Modifying Data in ADO.NET</span></span>](../retrieving-and-modifying-data.md)
- [<span data-ttu-id="9b0e1-143">Sécurité d’accès du code et ADO.NET</span><span class="sxs-lookup"><span data-stu-id="9b0e1-143">Code Access Security and ADO.NET</span></span>](../code-access-security.md)
- [<span data-ttu-id="9b0e1-144">Données binaires et de valeur élevée SQL Server</span><span class="sxs-lookup"><span data-stu-id="9b0e1-144">SQL Server Binary and Large-Value Data</span></span>](sql-server-binary-and-large-value-data.md)
- [<span data-ttu-id="9b0e1-145">Vue d’ensemble d’ADO.NET</span><span class="sxs-lookup"><span data-stu-id="9b0e1-145">ADO.NET Overview</span></span>](../ado-net-overview.md)
