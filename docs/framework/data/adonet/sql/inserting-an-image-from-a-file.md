---
title: Insertion d'une image à partir d'un fichier
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 35900aa2-5615-4174-8212-ba184c6b82fb
ms.openlocfilehash: d47f5b7eaf6b5f6a3174982e6b4cf43859c031a5
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70794152"
---
# <a name="inserting-an-image-from-a-file"></a><span data-ttu-id="9ce4b-102">Insertion d'une image à partir d'un fichier</span><span class="sxs-lookup"><span data-stu-id="9ce4b-102">Inserting an Image from a File</span></span>
<span data-ttu-id="9ce4b-103">Vous pouvez écrire des objets binaires volumineux (BLOB) dans une base de données sous forme de données de type binaire ou caractère en fonction du type du champ de votre source de données.</span><span class="sxs-lookup"><span data-stu-id="9ce4b-103">You can write a binary large object (BLOB) to a database as either binary or character data, depending on the type of field at your data source.</span></span> <span data-ttu-id="9ce4b-104">BLOB est un terme générique qui fait référence aux types de données `text`, `ntext` et `image` qui contiennent généralement des documents et des images.</span><span class="sxs-lookup"><span data-stu-id="9ce4b-104">BLOB is a generic term that refers to the `text`, `ntext`, and `image` data types, which typically contain documents and pictures.</span></span>  
  
 <span data-ttu-id="9ce4b-105">Pour écrire une valeur d’objet BLOB dans votre base de données, émettez l’instruction INSERT ou UPDATE appropriée et transmettez la valeur de l’objet BLOB en tant que paramètre d’entrée (consultez [Configuration des paramètres et des types de données de paramètre](../configuring-parameters-and-parameter-data-types.md)).</span><span class="sxs-lookup"><span data-stu-id="9ce4b-105">To write a BLOB value to your database, issue the appropriate INSERT or UPDATE statement and pass the BLOB value as an input parameter (see [Configuring Parameters and Parameter Data Types](../configuring-parameters-and-parameter-data-types.md)).</span></span> <span data-ttu-id="9ce4b-106">Si le BLOB est stocké sous forme de texte, dans le cas, par exemple, d'un champ `text` SQL Server, vous pouvez le passer en tant que paramètre de chaîne.</span><span class="sxs-lookup"><span data-stu-id="9ce4b-106">If your BLOB is stored as text, such as a SQL Server `text` field, you can pass the BLOB as a string parameter.</span></span> <span data-ttu-id="9ce4b-107">Si le BLOB est stocké sous forme binaire, dans le cas, par exemple, d'un champ `image` SQL Server, vous pouvez passer un tableau de type `byte` en tant que paramètre binaire.</span><span class="sxs-lookup"><span data-stu-id="9ce4b-107">If the BLOB is stored in binary format, such as a SQL Server `image` field, you can pass an array of type `byte` as a binary parameter.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9ce4b-108">Exemples</span><span class="sxs-lookup"><span data-stu-id="9ce4b-108">Example</span></span>  
 <span data-ttu-id="9ce4b-109">L'exemple de code suivant ajoute les informations relatives à un employé dans la table Employees de la base de données Northwind.</span><span class="sxs-lookup"><span data-stu-id="9ce4b-109">The following code example adds employee information to the Employees table in the Northwind database.</span></span> <span data-ttu-id="9ce4b-110">Une photo de l'employé est lue dans un fichier et ajoutée dans le champ Photo de la table, qui est un champ image.</span><span class="sxs-lookup"><span data-stu-id="9ce4b-110">A photo of the employee is read from a file and added to the Photo field in the table, which is an image field.</span></span>  
  
```vb  
Public Shared Sub AddEmployee( _  
  lastName As String, _  
  firstName As String, _  
  title As String, _  
  hireDate As DateTime, _  
  reportsTo As Integer, _  
  photoFilePath As String, _  
  connectionString As String)  
  
  Dim photo() as Byte = GetPhoto(photoFilePath)  
  
  Using connection As SqlConnection = New SqlConnection( _  
    connectionString)  
  
  Dim command As SqlCommand = New SqlCommand( _  
    "INSERT INTO Employees (LastName, FirstName, Title, " & _  
    "HireDate, ReportsTo, Photo) " & _  
    "Values(@LastName, @FirstName, @Title, " & _  
    "@HireDate, @ReportsTo, @Photo)", connection)   
  
  command.Parameters.Add("@LastName",  _  
    SqlDbType.NVarChar, 20).Value = lastName  
  command.Parameters.Add("@FirstName", _  
    SqlDbType.NVarChar, 10).Value = firstName  
  command.Parameters.Add("@Title", _  
    SqlDbType.NVarChar, 30).Value = title  
  command.Parameters.Add("@HireDate", _  
    SqlDbType.DateTime).Value = hireDate  
  command.Parameters.Add("@ReportsTo", _  
    SqlDbType.Int).Value = reportsTo  
  
  command.Parameters.Add("@Photo", _  
    SqlDbType.Image, photo.Length).Value = photo  
  
  connection.Open()  
  command.ExecuteNonQuery()  
  
  End Using  
End Sub  
  
Public Shared Function GetPhoto(filePath As String) As Byte()  
  Dim stream As FileStream = new FileStream( _  
     filePath, FileMode.Open, FileAccess.Read)  
  Dim reader As BinaryReader = new BinaryReader(stream)  
  
  Dim photo() As Byte = reader.ReadBytes(stream.Length)  
  
  reader.Close()  
  stream.Close()  
  
  Return photo  
End Function  
```  
  
```csharp  
public static void AddEmployee(  
  string lastName,   
  string firstName,   
  string title,   
  DateTime hireDate,   
  int reportsTo,   
  string photoFilePath,   
  string connectionString)  
{  
  byte[] photo = GetPhoto(photoFilePath);  
  
  using (SqlConnection connection = new SqlConnection(  
    connectionString))  
  
  SqlCommand command = new SqlCommand(  
    "INSERT INTO Employees (LastName, FirstName, " +  
    "Title, HireDate, ReportsTo, Photo) " +  
    "Values(@LastName, @FirstName, @Title, " +  
    "@HireDate, @ReportsTo, @Photo)", connection);   
  
  command.Parameters.Add("@LastName",    
     SqlDbType.NVarChar, 20).Value = lastName;  
  command.Parameters.Add("@FirstName",   
      SqlDbType.NVarChar, 10).Value = firstName;  
  command.Parameters.Add("@Title",       
      SqlDbType.NVarChar, 30).Value = title;  
  command.Parameters.Add("@HireDate",   
       SqlDbType.DateTime).Value = hireDate;  
  command.Parameters.Add("@ReportsTo",   
      SqlDbType.Int).Value = reportsTo;  
  
  command.Parameters.Add("@Photo",  
      SqlDbType.Image, photo.Length).Value = photo;  
  
  connection.Open();  
  command.ExecuteNonQuery();  
  }  
}  
  
public static byte[] GetPhoto(string filePath)  
{  
  FileStream stream = new FileStream(  
      filePath, FileMode.Open, FileAccess.Read);  
  BinaryReader reader = new BinaryReader(stream);  
  
  byte[] photo = reader.ReadBytes((int)stream.Length);  
  
  reader.Close();  
  stream.Close();  
  
  return photo;  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="9ce4b-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9ce4b-111">See also</span></span>

- [<span data-ttu-id="9ce4b-112">Utilisation des commandes pour modifier les données</span><span class="sxs-lookup"><span data-stu-id="9ce4b-112">Using Commands to Modify Data</span></span>](../using-commands-to-modify-data.md)
- [<span data-ttu-id="9ce4b-113">Récupération de données binaires</span><span class="sxs-lookup"><span data-stu-id="9ce4b-113">Retrieving Binary Data</span></span>](../retrieving-binary-data.md)
- [<span data-ttu-id="9ce4b-114">Données binaires et de valeur élevée SQL Server</span><span class="sxs-lookup"><span data-stu-id="9ce4b-114">SQL Server Binary and Large-Value Data</span></span>](sql-server-binary-and-large-value-data.md)
- [<span data-ttu-id="9ce4b-115">Mappages de types de données SQL Server</span><span class="sxs-lookup"><span data-stu-id="9ce4b-115">SQL Server Data Type Mappings</span></span>](../sql-server-data-type-mappings.md)
- [<span data-ttu-id="9ce4b-116">Vue d’ensemble d’ADO.NET</span><span class="sxs-lookup"><span data-stu-id="9ce4b-116">ADO.NET Overview</span></span>](../ado-net-overview.md)
