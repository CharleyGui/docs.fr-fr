---
title: Insertion d'une image à partir d'un fichier
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 35900aa2-5615-4174-8212-ba184c6b82fb
ms.openlocfilehash: 94ec554ca2dc5ed4eb6792b9b42ae6f1b856f51e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79148606"
---
# <a name="inserting-an-image-from-a-file"></a>Insertion d'une image à partir d'un fichier
Vous pouvez écrire un objet binaire large (BLOB) dans une base de données sous forme de données binaires ou de caractères, selon le type de champ de votre source de données. L’objet BLOB est un terme générique qui fait référence aux types de données `text`, `ntext` et `image`, qui contiennent généralement des documents et des images.  
  
 Pour écrire une valeur BLOB à votre base de données, publiez l’énoncé INSERT ou UPDATE approprié et passez la valeur BLOB comme paramètre d’entrée (voir [Paramètres configurants et types de données de paramètres](../configuring-parameters-and-parameter-data-types.md)). Si votre objet BLOB est stocké sous forme de texte, tel qu’un champ SQL Server `text`, vous pouvez passer l’objet BLOB comme paramètre de chaîne. Si l’objet BLOB est stocké au format binaire, tel qu’un champ SQL Server `image`, vous pouvez passer un tableau de type `byte` comme paramètre binaire.  
  
## <a name="example"></a> Exemple  
 L’exemple de code suivant ajoute des informations sur les employés à la table Employees de la base de données Northwind. Une photo de l’employé est lue à partir d’un fichier et ajoutée au champ photo dans la table, qui est un champ d’image.  
  
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
  
## <a name="see-also"></a>Voir aussi

- [Utilisation des commandes pour modifier les données](../using-commands-to-modify-data.md)
- [Récupération des données binaires](../retrieving-binary-data.md)
- [SqL Server Données binaires et à grande valeur](sql-server-binary-and-large-value-data.md)
- [Mappages de types de données SQL Server](../sql-server-data-type-mappings.md)
- [Vue d'ensemble d’ADO.NET](../ado-net-overview.md)
