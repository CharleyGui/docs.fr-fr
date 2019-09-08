---
title: BFILE Oracle
ms.date: 03/30/2017
ms.assetid: 341bbf84-4734-4d44-8723-ccedee954e21
ms.openlocfilehash: 214140bb8fcf43154b014ea3db609d355a27af7c
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70794627"
---
# <a name="oracle-bfiles"></a><span data-ttu-id="c43e2-102">BFILE Oracle</span><span class="sxs-lookup"><span data-stu-id="c43e2-102">Oracle BFILEs</span></span>
<span data-ttu-id="c43e2-103">Le fournisseur de données .NET Framework pour Oracle inclut la classe <xref:System.Data.OracleClient.OracleBFile> qui est utilisée pour opérer avec le type de données <xref:System.Data.OracleClient.OracleType.BFile> Oracle.</span><span class="sxs-lookup"><span data-stu-id="c43e2-103">The .NET Framework Data Provider for Oracle includes the <xref:System.Data.OracleClient.OracleBFile> class, which is used to work with the Oracle <xref:System.Data.OracleClient.OracleType.BFile> data type.</span></span>  
  
 <span data-ttu-id="c43e2-104">Le type de données Oracle **BFILE** est un type de données **LOB** Oracle qui contient une référence à des données binaires d’une taille maximale de 4 gigaoctets.</span><span class="sxs-lookup"><span data-stu-id="c43e2-104">The Oracle **BFILE** data type is an Oracle **LOB** data type that contains a reference to binary data with a maximum size of 4 gigabytes.</span></span> <span data-ttu-id="c43e2-105">Oracle **BFILE** diffère des autres types de données **LOB** Oracle en ce que ses données sont stockées dans un fichier physique dans le système d’exploitation et non sur le serveur.</span><span class="sxs-lookup"><span data-stu-id="c43e2-105">An Oracle **BFILE** differs from other Oracle **LOB** data types in that its data is stored in a physical file in the operating system instead of on the server.</span></span> <span data-ttu-id="c43e2-106">Notez que le type de données **BFILE** fournit un accès en lecture seule aux données.</span><span class="sxs-lookup"><span data-stu-id="c43e2-106">Note that the **BFILE** data type provides read-only access to data.</span></span>  
  
 <span data-ttu-id="c43e2-107">Les autres caractéristiques d’un type de données **BFILE** qui le distinguent d’un type de données **LOB** sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="c43e2-107">Other characteristics of a **BFILE** data type that distinguish it from a **LOB** data type are that it:</span></span>  
  
- <span data-ttu-id="c43e2-108">Il contient des données non structurées.</span><span class="sxs-lookup"><span data-stu-id="c43e2-108">Contains unstructured data.</span></span>  
  
- <span data-ttu-id="c43e2-109">Il prend en charge la fragmentation côté serveur.</span><span class="sxs-lookup"><span data-stu-id="c43e2-109">Supports server-side chunking.</span></span>  
  
- <span data-ttu-id="c43e2-110">Il utilise une sémantique de copie de référence.</span><span class="sxs-lookup"><span data-stu-id="c43e2-110">Uses reference copy semantics.</span></span> <span data-ttu-id="c43e2-111">Par exemple, si vous effectuez une opération de copie sur un **BFILE**, seul le localisateur **BFILE** (qui est une référence au fichier) est copié.</span><span class="sxs-lookup"><span data-stu-id="c43e2-111">For example, if you perform a copy operation on a **BFILE**, only the **BFILE** locator (which is a reference to the file) is copied.</span></span> <span data-ttu-id="c43e2-112">Les données du fichier ne sont pas copiées.</span><span class="sxs-lookup"><span data-stu-id="c43e2-112">The data in the file is not copied.</span></span>  
  
 <span data-ttu-id="c43e2-113">Le type de données **BFILE** doit être utilisé pour faire référence à des LOB de grande taille et, par conséquent, il n’est pas pratique de les stocker dans la base de données.</span><span class="sxs-lookup"><span data-stu-id="c43e2-113">The **BFILE** data type should be used for referencing LOBs that are large in size, and therefore, not practical to store in the database.</span></span> <span data-ttu-id="c43e2-114">Une plus grande surcharge du client, du serveur et de la communication est impliquée lors de l’utilisation d’un type de données **BFILE** comparé au type de données **LOB** .</span><span class="sxs-lookup"><span data-stu-id="c43e2-114">More client, server, and communication overhead is involved when using a **BFILE** data type compared with the **LOB** data type.</span></span> <span data-ttu-id="c43e2-115">Il est plus efficace d’accéder à un **BFILE** si vous ne devez obtenir qu’une petite quantité de données.</span><span class="sxs-lookup"><span data-stu-id="c43e2-115">It is more efficient to access a **BFILE** if you only need to obtain a small amount of data.</span></span> <span data-ttu-id="c43e2-116">Il est plus efficace d'accéder à des LOB résidant en mémoire si vous avez besoin d'obtenir l'objet entier.</span><span class="sxs-lookup"><span data-stu-id="c43e2-116">It is more efficient to access database-resident LOBs if you need to obtain the entire object.</span></span>  
  
 <span data-ttu-id="c43e2-117">Chaque objet **OracleBFile** non null est associé à deux entités qui définissent l’emplacement du fichier physique sous-jacent :</span><span class="sxs-lookup"><span data-stu-id="c43e2-117">Each non-NULL **OracleBFile** object is associated with two entities that define the location of the underlying physical file:</span></span>  
  
1. <span data-ttu-id="c43e2-118">Un objet DIRECTORY Oracle, qui est un alias de base de données pour un répertoire du système de fichiers.</span><span class="sxs-lookup"><span data-stu-id="c43e2-118">An Oracle DIRECTORY object, which is a database alias for a directory in the file system, and</span></span>  
  
2. <span data-ttu-id="c43e2-119">Le nom du fichier physique sous-jacent, qui se trouve dans le répertoire associé à l'objet DIRECTORY.</span><span class="sxs-lookup"><span data-stu-id="c43e2-119">The file name of the underlying physical file, which is located in the directory associated with the DIRECTORY object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c43e2-120">Exemple</span><span class="sxs-lookup"><span data-stu-id="c43e2-120">Example</span></span>  
 <span data-ttu-id="c43e2-121">L’exemple C# suivant montre comment vous pouvez créer un **BFILE** dans une table Oracle, puis le récupérer sous la forme d’un objet **OracleBFile** .</span><span class="sxs-lookup"><span data-stu-id="c43e2-121">The following C# example demonstrates how you can create a **BFILE** in an Oracle table and then retrieve it in the form of an **OracleBFile** object.</span></span> <span data-ttu-id="c43e2-122">L’exemple illustre l’utilisation <xref:System.Data.OracleClient.OracleDataReader> de l’objet et des méthodes de **recherche** et de **lecture** de **OracleBFile** .</span><span class="sxs-lookup"><span data-stu-id="c43e2-122">The example demonstrates using the <xref:System.Data.OracleClient.OracleDataReader> object and the **OracleBFile** **Seek** and **Read** methods.</span></span> <span data-ttu-id="c43e2-123">Notez que pour pouvoir utiliser cet exemple, vous devez d’abord créer un répertoire nommé « c :\\\bfiles » et un fichier nommé « myFile. jpg » sur le serveur Oracle.</span><span class="sxs-lookup"><span data-stu-id="c43e2-123">Note that in order to use this sample, you must first create a directory named "c:\\\bfiles" and file named "MyFile.jpg" on the Oracle server.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="c43e2-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c43e2-124">See also</span></span>

- [<span data-ttu-id="c43e2-125">Oracle et ADO.NET</span><span class="sxs-lookup"><span data-stu-id="c43e2-125">Oracle and ADO.NET</span></span>](oracle-and-adonet.md)
- [<span data-ttu-id="c43e2-126">Vue d’ensemble d’ADO.NET</span><span class="sxs-lookup"><span data-stu-id="c43e2-126">ADO.NET Overview</span></span>](ado-net-overview.md)
