---
title: Prise en charge de la diffusion en continu pour SqlClient
ms.date: 03/30/2017
ms.assetid: c449365b-470b-4edb-9d61-8353149f5531
ms.openlocfilehash: 83a657d1156774ec5ea342d47dca0434fd9d506c
ms.sourcegitcommit: 4735bb7741555bcb870d7b42964d3774f4897a6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/30/2019
ms.locfileid: "66379994"
---
# <a name="sqlclient-streaming-support"></a><span data-ttu-id="592ab-102">Prise en charge de la diffusion en continu pour SqlClient</span><span class="sxs-lookup"><span data-stu-id="592ab-102">SqlClient Streaming Support</span></span>

<span data-ttu-id="592ab-103">Diffusion en continu de prise en charge entre SQL Server et une application (nouveautée de .NET Framework 4.5) prend en charge les données non structurées sur le serveur (documents, images et fichiers multimédias).</span><span class="sxs-lookup"><span data-stu-id="592ab-103">Streaming support between SQL Server and an application (new in .NET Framework 4.5) supports unstructured data on the server (documents, images, and media files).</span></span> <span data-ttu-id="592ab-104">Une base de données SQL Server peut stocker des objets binaires volumineux (BLOB), mais la récupération des objets BLOB peuvent utiliser beaucoup de mémoire.</span><span class="sxs-lookup"><span data-stu-id="592ab-104">A SQL Server database can store binary large objects (BLOBs), but retrieving BLOBS can use a lot of memory.</span></span>

<span data-ttu-id="592ab-105">Diffusion en continu de prise en charge vers et depuis SQL Server simplifie l’écriture d’applications ces données de flux de données, sans devoir entièrement charger les données en mémoire, ce qui entraîne moins exceptions de dépassement de capacité de mémoire.</span><span class="sxs-lookup"><span data-stu-id="592ab-105">Streaming support to and from SQL Server simplifies writing applications that stream data, without having to fully load the data into memory, resulting in fewer memory overflow exceptions.</span></span>

<span data-ttu-id="592ab-106">La prise en charge de la diffusion en continu facilite la montée en charge des applications intermédiaires, surtout dans les scénarios où les objets métiers se connectent à SQL Azure afin d'envoyer, de récupérer et manipuler des BLOB.</span><span class="sxs-lookup"><span data-stu-id="592ab-106">Streaming support will also enable middle-tier applications to scale better, especially in scenarios where business objects connect to SQL Azure in order to send, retrieve, and manipulate large BLOBs.</span></span>

> [!WARNING]
> <span data-ttu-id="592ab-107">Les appels asynchrones ne sont pas pris en charge si une application utilise également le mot clé de chaîne de connexion `Context Connection`.</span><span class="sxs-lookup"><span data-stu-id="592ab-107">Asynchronous calls are not supported if an application also uses the `Context Connection` connection string keyword.</span></span>
>
> <span data-ttu-id="592ab-108">Les membres ajoutés pour la prise en charge de la diffusion en continu sont utilisés pour récupérer des données de requêtes et passer des paramètres aux requêtes et aux procédures stockées.</span><span class="sxs-lookup"><span data-stu-id="592ab-108">The members added to support streaming are used to retrieve data from queries and to pass parameters to queries and stored procedures.</span></span> <span data-ttu-id="592ab-109">La fonctionnalité de diffusion en continu répond à des scénarios OLTP de base et de migration des données et s’applique aux environnements de migration des données sur site et hors site.</span><span class="sxs-lookup"><span data-stu-id="592ab-109">The streaming feature addresses basic OLTP and data migration scenarios and is applicable to on premise and off premise data migrations.environments.</span></span>

## <a name="streaming-support-from-sql-server"></a><span data-ttu-id="592ab-110">Prise en charge de diffusion en continu à partir de SQL Server</span><span class="sxs-lookup"><span data-stu-id="592ab-110">Streaming Support from SQL Server</span></span>

<span data-ttu-id="592ab-111">Diffusion en continu de prise en charge à partir de SQL Server introduit une nouvelle fonctionnalité dans le <xref:System.Data.Common.DbDataReader> et dans le <xref:System.Data.SqlClient.SqlDataReader> classes afin d’obtenir <xref:System.IO.Stream>, <xref:System.Xml.XmlReader>, et <xref:System.IO.TextReader> objets et de réagir à ces derniers.</span><span class="sxs-lookup"><span data-stu-id="592ab-111">Streaming support from SQL Server introduces new functionality in the <xref:System.Data.Common.DbDataReader> and in the <xref:System.Data.SqlClient.SqlDataReader> classes in order to get <xref:System.IO.Stream>, <xref:System.Xml.XmlReader>, and <xref:System.IO.TextReader> objects and react to them.</span></span> <span data-ttu-id="592ab-112">Ces classes sont utilisées pour récupérer les données des requêtes.</span><span class="sxs-lookup"><span data-stu-id="592ab-112">These classes are used to retrieve data from queries.</span></span> <span data-ttu-id="592ab-113">Par conséquent, prise en charge de la diffusion en continu à partir de SQL Server répond aux scénarios OLTP et s’applique sur site et des environnements hors site.</span><span class="sxs-lookup"><span data-stu-id="592ab-113">As a result, Streaming support from SQL Server addresses OLTP scenarios and applies to on-premise and off-premise environments.</span></span>

<span data-ttu-id="592ab-114">Les membres suivants ont été ajoutés à <xref:System.Data.SqlClient.SqlDataReader> pour activer la prise en charge de diffusion en continu à partir de SQL Server :</span><span class="sxs-lookup"><span data-stu-id="592ab-114">The following members were added to <xref:System.Data.SqlClient.SqlDataReader> to enable streaming support from SQL Server:</span></span>

1. <xref:System.Data.SqlClient.SqlDataReader.IsDBNullAsync%2A>

2. <xref:System.Data.SqlClient.SqlDataReader.GetFieldValue%2A?displayProperty=nameWithType>

3. <xref:System.Data.SqlClient.SqlDataReader.GetFieldValueAsync%2A>

4. <xref:System.Data.SqlClient.SqlDataReader.GetStream%2A>

5. <xref:System.Data.SqlClient.SqlDataReader.GetTextReader%2A>

6. <xref:System.Data.SqlClient.SqlDataReader.GetXmlReader%2A>

<span data-ttu-id="592ab-115">Les membres suivants ont été ajoutés à <xref:System.Data.Common.DbDataReader> pour activer la prise en charge de diffusion en continu à partir de SQL Server :</span><span class="sxs-lookup"><span data-stu-id="592ab-115">The following members were added to <xref:System.Data.Common.DbDataReader> to enable streaming support from SQL Server:</span></span>

1. <xref:System.Data.Common.DbDataReader.GetFieldValue%2A>

2. <xref:System.Data.Common.DbDataReader.GetStream%2A>

3. <xref:System.Data.Common.DbDataReader.GetTextReader%2A>

## <a name="streaming-support-to-sql-server"></a><span data-ttu-id="592ab-116">Prise en charge de diffusion en continu vers SQL Server</span><span class="sxs-lookup"><span data-stu-id="592ab-116">Streaming Support to SQL Server</span></span>

<span data-ttu-id="592ab-117">Diffusion en continu de prise en charge pour SQL Server introduit une nouvelle fonctionnalité dans le <xref:System.Data.SqlClient.SqlParameter> classe afin de pouvoir accepter et réagir aux <xref:System.Xml.XmlReader>, <xref:System.IO.Stream>, et <xref:System.IO.TextReader> objets.</span><span class="sxs-lookup"><span data-stu-id="592ab-117">Streaming support to SQL Server introduces new functionality in the <xref:System.Data.SqlClient.SqlParameter> class so it can accept and react to <xref:System.Xml.XmlReader>, <xref:System.IO.Stream>, and <xref:System.IO.TextReader> objects.</span></span> <span data-ttu-id="592ab-118"><xref:System.Data.SqlClient.SqlParameter> est utilisé pour passer des paramètres aux requêtes et aux procédures stockées.</span><span class="sxs-lookup"><span data-stu-id="592ab-118"><xref:System.Data.SqlClient.SqlParameter> is used to pass parameters to queries and stored procedures.</span></span>

<span data-ttu-id="592ab-119">Supprimer un objet <xref:System.Data.SqlClient.SqlCommand> ou appeler <xref:System.Data.SqlClient.SqlCommand.Cancel%2A> doit annuler toute opération en continu.</span><span class="sxs-lookup"><span data-stu-id="592ab-119">Disposing a <xref:System.Data.SqlClient.SqlCommand> object or calling <xref:System.Data.SqlClient.SqlCommand.Cancel%2A> must cancel any streaming operation.</span></span> <span data-ttu-id="592ab-120">Si une application envoie <xref:System.Threading.CancellationToken>, l'annulation n'est pas garantie.</span><span class="sxs-lookup"><span data-stu-id="592ab-120">If an application sends <xref:System.Threading.CancellationToken>, cancellation is not guaranteed.</span></span>

<span data-ttu-id="592ab-121">Les types suivants <xref:System.Data.SqlClient.SqlParameter.SqlDbType%2A> acceptent un <xref:System.Data.SqlClient.SqlParameter.Value%2A> de <xref:System.IO.Stream> :</span><span class="sxs-lookup"><span data-stu-id="592ab-121">The following <xref:System.Data.SqlClient.SqlParameter.SqlDbType%2A> types will accept a <xref:System.Data.SqlClient.SqlParameter.Value%2A> of <xref:System.IO.Stream>:</span></span>

- <span data-ttu-id="592ab-122">**Binary**</span><span class="sxs-lookup"><span data-stu-id="592ab-122">**Binary**</span></span>

- <span data-ttu-id="592ab-123">**VarBinary**</span><span class="sxs-lookup"><span data-stu-id="592ab-123">**VarBinary**</span></span>

<span data-ttu-id="592ab-124">Les types suivants <xref:System.Data.SqlClient.SqlParameter.SqlDbType%2A> acceptent un <xref:System.Data.SqlClient.SqlParameter.Value%2A> de <xref:System.IO.TextReader> :</span><span class="sxs-lookup"><span data-stu-id="592ab-124">The following <xref:System.Data.SqlClient.SqlParameter.SqlDbType%2A> types will accept a <xref:System.Data.SqlClient.SqlParameter.Value%2A> of <xref:System.IO.TextReader>:</span></span>

- <span data-ttu-id="592ab-125">**Char**</span><span class="sxs-lookup"><span data-stu-id="592ab-125">**Char**</span></span>

- <span data-ttu-id="592ab-126">**NChar**</span><span class="sxs-lookup"><span data-stu-id="592ab-126">**NChar**</span></span>

- <span data-ttu-id="592ab-127">**NVarChar**</span><span class="sxs-lookup"><span data-stu-id="592ab-127">**NVarChar**</span></span>

- <span data-ttu-id="592ab-128">**Xml**</span><span class="sxs-lookup"><span data-stu-id="592ab-128">**Xml**</span></span>

<span data-ttu-id="592ab-129">Le **Xml** <xref:System.Data.SqlClient.SqlParameter.SqlDbType%2A> type accepte un <xref:System.Data.SqlClient.SqlParameter.Value%2A> de <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="592ab-129">The **Xml**<xref:System.Data.SqlClient.SqlParameter.SqlDbType%2A> type will accept a <xref:System.Data.SqlClient.SqlParameter.Value%2A> of <xref:System.Xml.XmlReader>.</span></span>

<span data-ttu-id="592ab-130"><xref:System.Data.SqlClient.SqlParameter.SqlValue%2A> accepte des valeurs de type <xref:System.Xml.XmlReader>, <xref:System.IO.TextReader> et <xref:System.IO.Stream>.</span><span class="sxs-lookup"><span data-stu-id="592ab-130"><xref:System.Data.SqlClient.SqlParameter.SqlValue%2A> can accept values of type <xref:System.Xml.XmlReader>, <xref:System.IO.TextReader>, and <xref:System.IO.Stream>.</span></span>

<span data-ttu-id="592ab-131"><xref:System.Xml.XmlReader>, <xref:System.IO.TextReader>, et l'objet <xref:System.IO.Stream> seront envoyés jusqu'à la valeur définie par <xref:System.Data.SqlClient.SqlParameter.Size%2A>.</span><span class="sxs-lookup"><span data-stu-id="592ab-131">The <xref:System.Xml.XmlReader>, <xref:System.IO.TextReader>, and <xref:System.IO.Stream> object will be transferred up to the value defined by the <xref:System.Data.SqlClient.SqlParameter.Size%2A>.</span></span>

## <a name="sample----streaming-from-sql-server"></a><span data-ttu-id="592ab-132">Exemple--Diffusion en continu à partir de SQL Server</span><span class="sxs-lookup"><span data-stu-id="592ab-132">Sample -- Streaming from SQL Server</span></span>

<span data-ttu-id="592ab-133">Utilisez le code [!INCLUDE[tsql](../../../../includes/tsql-md.md)] suivant pour créer l'exemple de base de données :</span><span class="sxs-lookup"><span data-stu-id="592ab-133">Use the following [!INCLUDE[tsql](../../../../includes/tsql-md.md)] to create the sample database:</span></span>

```sql
CREATE DATABASE [Demo]
GO
USE [Demo]
GO
CREATE TABLE [Streams] (
[id] INT PRIMARY KEY IDENTITY(1, 1),
[textdata] NVARCHAR(MAX),
[bindata] VARBINARY(MAX),
[xmldata] XML)
GO
INSERT INTO [Streams] (textdata, bindata, xmldata) VALUES (N'This is a test', 0x48656C6C6F, N'<test>value</test>')
INSERT INTO [Streams] (textdata, bindata, xmldata) VALUES (N'Hello, World!', 0x54657374696E67, N'<test>value2</test>')
INSERT INTO [Streams] (textdata, bindata, xmldata) VALUES (N'Another row', 0x666F6F626172, N'<fff>bbb</fff><fff>bbc</fff>')
GO
```

<span data-ttu-id="592ab-134">L'exemple montre comment effectuer les actions suivantes :</span><span class="sxs-lookup"><span data-stu-id="592ab-134">The sample shows how to do the following:</span></span>

- <span data-ttu-id="592ab-135">Éviter de bloquer un thread d'interface utilisateur en fournissant une façon asynchrone de récupérer des fichiers volumineux.</span><span class="sxs-lookup"><span data-stu-id="592ab-135">Avoid blocking a user-interface thread by providing an asynchronous way to retrieve large files.</span></span>

- <span data-ttu-id="592ab-136">Transférer un fichier texte volumineux à partir de SQL Server dans .NET Framework 4.5.</span><span class="sxs-lookup"><span data-stu-id="592ab-136">Transfer a large text file from SQL Server in .NET Framework 4.5.</span></span>

- <span data-ttu-id="592ab-137">Transférer un grand fichier XML à partir de SQL Server dans .NET Framework 4.5.</span><span class="sxs-lookup"><span data-stu-id="592ab-137">Transfer a large XML file from SQL Server in .NET Framework 4.5.</span></span>

- <span data-ttu-id="592ab-138">Récupérer des données à partir de SQL Server.</span><span class="sxs-lookup"><span data-stu-id="592ab-138">Retrieve data from SQL Server.</span></span>

- <span data-ttu-id="592ab-139">Transférer des fichiers volumineux (BLOB) à partir d’une base de données SQL Server vers un autre sans insuffisance de mémoire.</span><span class="sxs-lookup"><span data-stu-id="592ab-139">Transfer large files (BLOBs) from one SQL Server database to another without running out of memory.</span></span>

```csharp
using System;
using System.Data;
using System.Data.SqlClient;
using System.IO;
using System.Threading.Tasks;
using System.Xml;

namespace StreamingFromServer {
   class Program {
      // Replace the connection string if needed, for instance to connect to SQL Express: @"Server=(local)\SQLEXPRESS;Database=Demo;Integrated Security=true"
      private const string connectionString = @"Server=(localdb)\V11.0;Database=Demo";

      static void Main(string[] args) {
         CopyBinaryValueToFile().Wait();
         PrintTextValues().Wait();
         PrintXmlValues().Wait();
         PrintXmlValuesViaNVarChar().Wait();

         Console.WriteLine("Done");
      }

      // Application retrieving a large BLOB from SQL Server in .NET 4.5 using the new asynchronous capability
      private static async Task CopyBinaryValueToFile() {
         string filePath = Path.Combine(Environment.GetFolderPath(Environment.SpecialFolder.MyDocuments), "binarydata.bin");

         using (SqlConnection connection = new SqlConnection(connectionString)) {
            await connection.OpenAsync();
            using (SqlCommand command = new SqlCommand("SELECT [bindata] FROM [Streams] WHERE [id]=@id", connection)) {
               command.Parameters.AddWithValue("id", 1);

               // The reader needs to be executed with the SequentialAccess behavior to enable network streaming
               // Otherwise ReadAsync will buffer the entire BLOB into memory which can cause scalability issues or even OutOfMemoryExceptions
               using (SqlDataReader reader = await command.ExecuteReaderAsync(CommandBehavior.SequentialAccess)) {
                  if (await reader.ReadAsync()) {
                     if (!(await reader.IsDBNullAsync(0))) {
                        using (FileStream file = new FileStream(filePath, FileMode.Create, FileAccess.Write)) {
                           using (Stream data = reader.GetStream(0)) {

                              // Asynchronously copy the stream from the server to the file we just created
                              await data.CopyToAsync(file);
                           }
                        }
                     }
                  }
               }
            }
         }
      }

      // Application transferring a large Text File from SQL Server in .NET 4.5
      private static async Task PrintTextValues() {
         using (SqlConnection connection = new SqlConnection(connectionString)) {
            await connection.OpenAsync();
            using (SqlCommand command = new SqlCommand("SELECT [id], [textdata] FROM [Streams]", connection)) {

               // The reader needs to be executed with the SequentialAccess behavior to enable network streaming
               // Otherwise ReadAsync will buffer the entire text document into memory which can cause scalability issues or even OutOfMemoryExceptions
               using (SqlDataReader reader = await command.ExecuteReaderAsync(CommandBehavior.SequentialAccess)) {
                  while (await reader.ReadAsync()) {
                     Console.Write("{0}: ", reader.GetInt32(0));

                     if (await reader.IsDBNullAsync(1)) {
                        Console.Write("(NULL)");
                     }
                     else {
                        char[] buffer = new char[4096];
                        int charsRead = 0;
                        using (TextReader data = reader.GetTextReader(1)) {
                           do {
                              // Grab each chunk of text and write it to the console
                              // If you are writing to a TextWriter you should use WriteAsync or WriteLineAsync
                              charsRead = await data.ReadAsync(buffer, 0, buffer.Length);
                              Console.Write(buffer, 0, charsRead);
                           } while (charsRead > 0);
                        }
                     }

                     Console.WriteLine();
                  }
               }
            }
         }
      }

      // Application transferring a large Xml Document from SQL Server in .NET 4.5
      private static async Task PrintXmlValues() {
         using (SqlConnection connection = new SqlConnection(connectionString)) {
            await connection.OpenAsync();
            using (SqlCommand command = new SqlCommand("SELECT [id], [xmldata] FROM [Streams]", connection)) {

               // The reader needs to be executed with the SequentialAccess behavior to enable network streaming
               // Otherwise ReadAsync will buffer the entire Xml Document into memory which can cause scalability issues or even OutOfMemoryExceptions
               using (SqlDataReader reader = await command.ExecuteReaderAsync(CommandBehavior.SequentialAccess)) {
                  while (await reader.ReadAsync()) {
                     Console.WriteLine("{0}: ", reader.GetInt32(0));

                     if (await reader.IsDBNullAsync(1)) {
                        Console.WriteLine("\t(NULL)");
                     }
                     else {
                        using (XmlReader xmlReader = reader.GetXmlReader(1)) {
                           int depth = 1;
                           // NOTE: The XmlReader returned by GetXmlReader does NOT support async operations
                           // See the example below (PrintXmlValuesViaNVarChar) for how to get an XmlReader with asynchronous capabilities
                           while (xmlReader.Read()) {
                              switch (xmlReader.NodeType) {
                                 case XmlNodeType.Element:
                                    Console.WriteLine("{0}<{1}>", new string('\t', depth), xmlReader.Name);
                                    depth++;
                                    break;
                                 case XmlNodeType.Text:
                                    Console.WriteLine("{0}{1}", new string('\t', depth), xmlReader.Value);
                                    break;
                                 case XmlNodeType.EndElement:
                                    depth--;
                                    Console.WriteLine("{0}</{1}>", new string('\t', depth), xmlReader.Name);
                                    break;
                              }
                           }
                        }
                     }
                  }
               }
            }
         }
      }

      // Application transferring a large Xml Document from SQL Server in .NET 4.5
      // This goes via NVarChar and TextReader to enable asynchronous reading
      private static async Task PrintXmlValuesViaNVarChar() {
         XmlReaderSettings xmlSettings = new XmlReaderSettings() {
            // Async must be explicitly enabled in the XmlReaderSettings otherwise the XmlReader will throw exceptions when async methods are called
            Async = true,
            // Since we will immediately wrap the TextReader we are creating in an XmlReader, we will permit the XmlReader to take care of closing\disposing it
            CloseInput = true,
            // If the Xml you are reading is not a valid document (as per <https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/6bts1x50(v=vs.100)>) you will need to set the conformance level to Fragment
            ConformanceLevel = ConformanceLevel.Fragment
         };

         using (SqlConnection connection = new SqlConnection(connectionString)) {
            await connection.OpenAsync();

            // Cast the XML into NVarChar to enable GetTextReader - trying to use GetTextReader on an XML type will throw an exception
            using (SqlCommand command = new SqlCommand("SELECT [id], CAST([xmldata] AS NVARCHAR(MAX)) FROM [Streams]", connection)) {

               // The reader needs to be executed with the SequentialAccess behavior to enable network streaming
               // Otherwise ReadAsync will buffer the entire Xml Document into memory which can cause scalability issues or even OutOfMemoryExceptions
               using (SqlDataReader reader = await command.ExecuteReaderAsync(CommandBehavior.SequentialAccess)) {
                  while (await reader.ReadAsync()) {
                     Console.WriteLine("{0}:", reader.GetInt32(0));

                     if (await reader.IsDBNullAsync(1)) {
                        Console.WriteLine("\t(NULL)");
                     }
                     else {
                        // Grab the row as a TextReader, then create an XmlReader on top of it
                        // We are not keeping a reference to the TextReader since the XmlReader is created with the "CloseInput" setting (so it will close the TextReader when needed)
                        using (XmlReader xmlReader = XmlReader.Create(reader.GetTextReader(1), xmlSettings)) {
                           int depth = 1;
                           // The XmlReader above now supports asynchronous operations, so we can use ReadAsync here
                           while (await xmlReader.ReadAsync()) {
                              switch (xmlReader.NodeType) {
                                 case XmlNodeType.Element:
                                    Console.WriteLine("{0}<{1}>", new string('\t', depth), xmlReader.Name);
                                    depth++;
                                    break;
                                 case XmlNodeType.Text:
                                    // Depending on what your data looks like, you should either use Value or GetValueAsync
                                    // Value has less overhead (since it doesn't create a Task), but it may also block if additional data is required
                                    Console.WriteLine("{0}{1}", new string('\t', depth), await xmlReader.GetValueAsync());
                                    break;
                                 case XmlNodeType.EndElement:
                                    depth--;
                                    Console.WriteLine("{0}</{1}>", new string('\t', depth), xmlReader.Name);
                                    break;
                              }
                           }
                        }
                     }
                  }
               }
            }
         }
      }
   }
}
```

## <a name="sample----streaming-to-sql-server"></a><span data-ttu-id="592ab-140">Exemple--Diffusion en continu vers SQL Server</span><span class="sxs-lookup"><span data-stu-id="592ab-140">Sample -- Streaming to SQL Server</span></span>

<span data-ttu-id="592ab-141">Utilisez le code [!INCLUDE[tsql](../../../../includes/tsql-md.md)] suivant pour créer l'exemple de base de données :</span><span class="sxs-lookup"><span data-stu-id="592ab-141">Use the following [!INCLUDE[tsql](../../../../includes/tsql-md.md)] to create the sample database:</span></span>

```sql
CREATE DATABASE [Demo2]
GO
USE [Demo2]
GO
CREATE TABLE [BinaryStreams] (
[id] INT PRIMARY KEY IDENTITY(1, 1),
[bindata] VARBINARY(MAX))
GO
CREATE TABLE [TextStreams] (
[id] INT PRIMARY KEY IDENTITY(1, 1),
[textdata] NVARCHAR(MAX))
GO
CREATE TABLE [BinaryStreamsCopy] (
[id] INT PRIMARY KEY IDENTITY(1, 1),
[bindata] VARBINARY(MAX))
GO
```

<span data-ttu-id="592ab-142">L'exemple montre comment effectuer les actions suivantes :</span><span class="sxs-lookup"><span data-stu-id="592ab-142">The sample shows how to do the following:</span></span>

- <span data-ttu-id="592ab-143">Transfert d’un objet BLOB vers SQL Server dans .NET Framework 4.5.</span><span class="sxs-lookup"><span data-stu-id="592ab-143">Transferring a large BLOB to SQL Server in .NET Framework 4.5.</span></span>

- <span data-ttu-id="592ab-144">Transfert d’un fichier texte volumineux vers SQL Server dans .NET Framework 4.5.</span><span class="sxs-lookup"><span data-stu-id="592ab-144">Transferring a large text file to SQL Server in .NET Framework 4.5.</span></span>

- <span data-ttu-id="592ab-145">Utilisation de la nouvelle fonctionnalité asynchrone pour transférer un objet BLOB.</span><span class="sxs-lookup"><span data-stu-id="592ab-145">Using the new asynchronous feature to transfer a large BLOB.</span></span>

- <span data-ttu-id="592ab-146">Utilisation de la nouvelle fonctionnalité asynchrone et du mot clé await pour transférer un objet BLOB.</span><span class="sxs-lookup"><span data-stu-id="592ab-146">Using the new asynchronous feature and the await keyword to transfer a large BLOB.</span></span>

- <span data-ttu-id="592ab-147">Annuler le transfert d’un objet BLOB.</span><span class="sxs-lookup"><span data-stu-id="592ab-147">Cancelling the transfer of a large BLOB.</span></span>

- <span data-ttu-id="592ab-148">Diffusion en continu à partir d’une instance SQL Server à un autre à l’aide de la nouvelle fonctionnalité asynchrone.</span><span class="sxs-lookup"><span data-stu-id="592ab-148">Streaming from one SQL Server to another using the new asynchronous feature.</span></span>

```csharp
using System;
using System.Data;
using System.Data.SqlClient;
using System.IO;
using System.Threading;
using System.Threading.Tasks;

namespace StreamingToServer {
   class Program {
      // Replace the connection string if needed, for instance to connect to SQL Express: @"Server=(local)\SQLEXPRESS;Database=Demo2;Integrated Security=true"
      private const string connectionString = @"Server=(localdb)\V11.0;Database=Demo2";

      static void Main(string[] args) {
         CreateDemoFiles();

         StreamBLOBToServer().Wait();
         StreamTextToServer().Wait();

         // Create a CancellationTokenSource that will be cancelled after 100ms
         // Typically this token source will be cancelled by a user request (e.g. a Cancel button)
         CancellationTokenSource tokenSource = new CancellationTokenSource();
         tokenSource.CancelAfter(100);
         try {
            CancelBLOBStream(tokenSource.Token).Wait();
         }
         catch (AggregateException ex) {
            // Cancelling an async operation will throw an exception
            // Since we are using the Task's Wait method, this exception will be wrapped in an AggregateException
            // If you were using the 'await' keyword, the compiler would take care of unwrapping the AggregateException
            // Depending on when the cancellation occurs, you can either get an error from SQL Server or from .Net
            if ((ex.InnerException is SqlException) || (ex.InnerException is TaskCanceledException)) {
               // This is an expected exception
               Console.WriteLine("Got expected exception: {0}", ex.InnerException.Message);
            }
            else {
               // Did not expect this exception - re-throw it
               throw;
            }
         }

         Console.WriteLine("Done");
      }

      // This is used to generate the files which are used by the other sample methods
      private static void CreateDemoFiles() {
         Random rand = new Random();
         byte[] data = new byte[1024];
         rand.NextBytes(data);

         using (FileStream file = File.Open("binarydata.bin", FileMode.Create)) {
            file.Write(data, 0, data.Length);
         }

         using (StreamWriter writer = new StreamWriter(File.Open("textdata.txt", FileMode.Create))) {
            writer.Write(Convert.ToBase64String(data));
         }
      }

      // Application transferring a large BLOB to SQL Server in .NET 4.5
      private static async Task StreamBLOBToServer() {
         using (SqlConnection conn = new SqlConnection(connectionString)) {
            await conn.OpenAsync();
            using (SqlCommand cmd = new SqlCommand("INSERT INTO [BinaryStreams] (bindata) VALUES (@bindata)", conn)) {
               using (FileStream file = File.Open("binarydata.bin", FileMode.Open)) {

                  // Add a parameter which uses the FileStream we just opened
                  // Size is set to -1 to indicate "MAX"
                  cmd.Parameters.Add("@bindata", SqlDbType.Binary, -1).Value = file;

                  // Send the data to the server asynchronously
                  await cmd.ExecuteNonQueryAsync();
               }
            }
         }
      }

      // Application transferring a large Text File to SQL Server in .NET 4.5
      private static async Task StreamTextToServer() {
         using (SqlConnection conn = new SqlConnection(connectionString)) {
            await conn.OpenAsync();
            using (SqlCommand cmd = new SqlCommand("INSERT INTO [TextStreams] (textdata) VALUES (@textdata)", conn)) {
               using (StreamReader file = File.OpenText("textdata.txt")) {

                  // Add a parameter which uses the StreamReader we just opened
                  // Size is set to -1 to indicate "MAX"
                  cmd.Parameters.Add("@textdata", SqlDbType.NVarChar, -1).Value = file;

                  // Send the data to the server asynchronously
                  await cmd.ExecuteNonQueryAsync();
               }
            }
         }
      }

      // Cancelling the transfer of a large BLOB
      private static async Task CancelBLOBStream(CancellationToken cancellationToken) {
         using (SqlConnection conn = new SqlConnection(connectionString)) {
            // We can cancel not only sending the data to the server, but also opening the connection
            await conn.OpenAsync(cancellationToken);

            // Artificially delay the command by 100ms
            using (SqlCommand cmd = new SqlCommand("WAITFOR DELAY '00:00:00:100';INSERT INTO [BinaryStreams] (bindata) VALUES (@bindata)", conn)) {
               using (FileStream file = File.Open("binarydata.bin", FileMode.Open)) {

                  // Add a parameter which uses the FileStream we just opened
                  // Size is set to -1 to indicate "MAX"
                  cmd.Parameters.Add("@bindata", SqlDbType.Binary, -1).Value = file;

                  // Send the data to the server asynchronously
                  // Pass the cancellation token such that the command will be cancelled if needed
                  await cmd.ExecuteNonQueryAsync(cancellationToken);
               }
            }
         }
      }
   }
}
```

## <a name="sample----streaming-from-one-sql-server-to-another-sql-server"></a><span data-ttu-id="592ab-149">Exemple--Diffusion en continu à partir d’une instance SQL Server vers un autre serveur SQL</span><span class="sxs-lookup"><span data-stu-id="592ab-149">Sample -- Streaming From One SQL Server to Another SQL Server</span></span>

<span data-ttu-id="592ab-150">Cet exemple montre comment diffuser en continu un objet BLOB à partir d’une instance SQL Server vers un autre, avec prise en charge l’annulation.</span><span class="sxs-lookup"><span data-stu-id="592ab-150">This sample demonstrates how to asynchronously stream a large BLOB from one SQL Server to another, with support for cancellation.</span></span>

```csharp
using System;
using System.Data;
using System.Data.SqlClient;
using System.IO;
using System.Threading;
using System.Threading.Tasks;

namespace StreamingFromServerToAnother {
   class Program {
      // Replace the connection string if needed, for instance to connect to SQL Express: @"Server=(local)\SQLEXPRESS;Database=Demo2;Integrated Security=true"
      private const string connectionString = @"Server=(localdb)\V11.0;Database=Demo2";

      static void Main(string[] args) {
         // For this example, we don't want to cancel
         // So we can pass in a "blank" cancellation token
         E2EStream(CancellationToken.None).Wait();

         Console.WriteLine("Done");
      }

      // Streaming from one SQL Server to Another One using the new Async.NET
      private static async Task E2EStream(CancellationToken cancellationToken) {
         using (SqlConnection readConn = new SqlConnection(connectionString)) {
            using (SqlConnection writeConn = new SqlConnection(connectionString)) {

               // Note that we are using the same cancellation token for calls to both connections\commands
               // Also we can start both the connection opening asynchronously, and then wait for both to complete
               Task openReadConn = readConn.OpenAsync(cancellationToken);
               Task openWriteConn = writeConn.OpenAsync(cancellationToken);
               await Task.WhenAll(openReadConn, openWriteConn);

               using (SqlCommand readCmd = new SqlCommand("SELECT [bindata] FROM [BinaryStreams]", readConn)) {
                  using (SqlCommand writeCmd = new SqlCommand("INSERT INTO [BinaryStreamsCopy] (bindata) VALUES (@bindata)", writeConn)) {

                     // Add an empty parameter to the write command which will be used for the streams we are copying
                     // Size is set to -1 to indicate "MAX"
                     SqlParameter streamParameter = writeCmd.Parameters.Add("@bindata", SqlDbType.Binary, -1);

                     // The reader needs to be executed with the SequentialAccess behavior to enable network streaming
                     // Otherwise ReadAsync will buffer the entire BLOB into memory which can cause scalability issues or even OutOfMemoryExceptions
                     using (SqlDataReader reader = await readCmd.ExecuteReaderAsync(CommandBehavior.SequentialAccess, cancellationToken)) {
                        while (await reader.ReadAsync(cancellationToken)) {
                           // Grab a stream to the binary data in the source database
                           using (Stream dataStream = reader.GetStream(0)) {

                              // Set the parameter value to the stream source that was opened
                              streamParameter.Value = dataStream;

                              // Asynchronously send data from one database to another
                              await writeCmd.ExecuteNonQueryAsync(cancellationToken);
                           }
                        }
                     }
                  }
               }
            }
         }
      }
   }
}
```

## <a name="see-also"></a><span data-ttu-id="592ab-151">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="592ab-151">See also</span></span>

- [<span data-ttu-id="592ab-152">Extraction et modification de données dans ADO.NET</span><span class="sxs-lookup"><span data-stu-id="592ab-152">Retrieving and Modifying Data in ADO.NET</span></span>](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)
