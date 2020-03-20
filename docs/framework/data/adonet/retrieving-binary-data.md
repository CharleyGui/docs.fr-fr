---
title: Extraction de données binaires
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 56c5a9e3-31f1-482f-bce0-ff1c41a658d0
ms.openlocfilehash: c914a9b0780e2e87e177502b0f9faff0e7c4b617
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79149048"
---
# <a name="retrieving-binary-data"></a>Extraction de données binaires
Par défaut, le **DataReader** charge les données entrantes dès qu’une série entière de données est disponible. Les objets binaires volumineux ou BLOB doivent néanmoins être traités différemment car ils peuvent renfermer plusieurs gigaoctets de données qu'une seule ligne ne suffirait pas à contenir. La méthode **Command.ExecuteReader** a une surcharge <xref:System.Data.CommandBehavior> qui prendra un argument pour modifier le comportement par défaut du **DataReader**. Vous pouvez <xref:System.Data.CommandBehavior.SequentialAccess> passer à la méthode **ExecuteReader** pour modifier le comportement par défaut du **DataReader** de sorte qu’au lieu de charger des lignes de données, il chargera les données de manière séquentielle au fur et à mesure qu’elle est reçue. Cela est idéal pour charger les BLOB ou d'autres grosses structures de données. Notez que ce comportement peut différer selon votre source de données. Par exemple, un BLOB retourné de Microsoft Access est entièrement chargé dans la mémoire, au lieu que les données soient chargées de façon séquentielle à mesure qu'elles arrivent.  
  
 Lors de la définition du **DataReader** pour utiliser **SequentialAccess**, il est important de noter la séquence dans laquelle vous accédez aux champs retournés. Le comportement par défaut du **DataReader**, qui charge une ligne entière dès qu’il est disponible, vous permet d’accéder aux champs retournés dans n’importe quel ordre jusqu’à ce que la prochaine ligne soit lue. Lors de **l’utilisation de SéquentialAccess** cependant, vous devez accéder aux champs retournés par le **DataReader** dans l’ordre. Par exemple, si votre requête retourne trois colonnes, la troisième étant un BLOB, vous devez retourner les valeurs des premier et deuxième champs avant d'accéder aux données BLOB du troisième champ. Si vous accédez au troisième champ avant le premier ou le deuxième, les valeurs de ces champs ne seront plus disponibles. C’est parce que **SequentialAccess** a modifié le **DataReader** pour retourner les données dans l’ordre et les données ne sont pas disponibles après que le **DataReader** l’a lu au-delà.  
  
 Lors de l’accès aux données dans le champ BLOB, utilisez les accesseurs dactylographes **GetBytes** ou **GetChars** du **DataReader**, qui remplissent un tableau de données. Vous pouvez également utiliser **GetString** pour les données de caractère; Cependant. pour économiser les ressources système, vous souhaitez peut-être ne pas charger la valeur entière du BLOB dans une seule variable chaîne. Au lieu de cela, vous pouvez spécifier une taille de mémoire tampon spécifique des données à retourner ainsi qu'un emplacement de départ pour le premier octet ou le premier caractère lu des données retournées. **GetBytes** et **GetChars** `long` retourneront une valeur, qui représente le nombre d’octets ou de caractères retournés. Si vous passez un tableau nul à **GetBytes** ou **GetChars**, la valeur longue retournée sera le nombre total d’octets ou de caractères dans le BLOB. Vous pouvez éventuellement spécifier un index dans le tableau comme position de départ pour les données en cours de lecture.  
  
## <a name="example"></a> Exemple  
 L’exemple suivant renvoie l’identifiant et le logo de l’éditeur de la base de données d’échantillons **de pubs** dans Microsoft SQL Server. L'ID de l'éditeur (`pub_id`) est un champ texte et le logo est une image (un BLOB). Parce que le champ **de logo** est un bitmap, l’exemple renvoie les données binaires en utilisant **GetBytes**. Notez que pour la ligne de données actuelle, il faut accéder à l'ID de l'éditeur avant d'accéder au logo car l'accès aux champs doit être séquentiel.  
  
```vb  
' Assumes that connection is a valid SqlConnection object.  
Dim command As SqlCommand = New SqlCommand( _  
  "SELECT pub_id, logo FROM pub_info", connection)  
  
' Writes the BLOB to a file (*.bmp).  
Dim stream As FileStream
' Streams the binary data to the FileStream object.  
Dim writer As BinaryWriter
' The size of the BLOB buffer.  
Dim bufferSize As Integer = 100
' The BLOB byte() buffer to be filled by GetBytes.  
Dim outByte(bufferSize - 1) As Byte
' The bytes returned from GetBytes.  
Dim retval As Long
' The starting position in the BLOB output.  
Dim startIndex As Long = 0
  
' The publisher id to use in the file name.  
Dim pubID As String = ""
  
' Open the connection and read data into the DataReader.  
connection.Open()  
Dim reader As SqlDataReader = command.ExecuteReader(CommandBehavior.SequentialAccess)  
  
Do While reader.Read()  
  ' Get the publisher id, which must occur before getting the logo.  
  pubID = reader.GetString(0)  
  
  ' Create a file to hold the output.  
  stream = New FileStream( _  
    "logo" & pubID & ".bmp", FileMode.OpenOrCreate, FileAccess.Write)  
  writer = New BinaryWriter(stream)  
  
  ' Reset the starting byte for a new BLOB.  
  startIndex = 0  
  
  ' Read bytes into outByte() and retain the number of bytes returned.  
  retval = reader.GetBytes(1, startIndex, outByte, 0, bufferSize)  
  
  ' Continue while there are bytes beyond the size of the buffer.  
  Do While retval = bufferSize  
    writer.Write(outByte)  
    writer.Flush()  
  
    ' Reposition start index to end of the last buffer and fill buffer.  
    startIndex += bufferSize  
    retval = reader.GetBytes(1, startIndex, outByte, 0, bufferSize)  
  Loop  
  
  ' Write the remaining buffer.  
  writer.Write(outByte, 0 , retval - 1)  
  writer.Flush()  
  
  ' Close the output file.  
  writer.Close()  
  stream.Close()  
Loop  
  
' Close the reader and the connection.  
reader.Close()  
connection.Close()  
```  
  
```csharp  
// Assumes that connection is a valid SqlConnection object.  
SqlCommand command = new SqlCommand(  
  "SELECT pub_id, logo FROM pub_info", connection);  
  
// Writes the BLOB to a file (*.bmp).  
FileStream stream;
// Streams the BLOB to the FileStream object.  
BinaryWriter writer;
  
// Size of the BLOB buffer.  
int bufferSize = 100;
// The BLOB byte[] buffer to be filled by GetBytes.  
byte[] outByte = new byte[bufferSize];
// The bytes returned from GetBytes.  
long retval;
// The starting position in the BLOB output.  
long startIndex = 0;
  
// The publisher id to use in the file name.  
string pubID = "";
  
// Open the connection and read data into the DataReader.  
connection.Open();  
SqlDataReader reader = command.ExecuteReader(CommandBehavior.SequentialAccess);  
  
while (reader.Read())  
{  
  // Get the publisher id, which must occur before getting the logo.  
  pubID = reader.GetString(0);
  
  // Create a file to hold the output.  
  stream = new FileStream(  
    "logo" + pubID + ".bmp", FileMode.OpenOrCreate, FileAccess.Write);  
  writer = new BinaryWriter(stream);  
  
  // Reset the starting byte for the new BLOB.  
  startIndex = 0;  
  
  // Read bytes into outByte[] and retain the number of bytes returned.  
  retval = reader.GetBytes(1, startIndex, outByte, 0, bufferSize);  
  
  // Continue while there are bytes beyond the size of the buffer.  
  while (retval == bufferSize)  
  {  
    writer.Write(outByte);  
    writer.Flush();  
  
    // Reposition start index to end of last buffer and fill buffer.  
    startIndex += bufferSize;  
    retval = reader.GetBytes(1, startIndex, outByte, 0, bufferSize);  
  }  
  
  // Write the remaining buffer.  
  writer.Write(outByte, 0, (int)retval);  
  writer.Flush();  
  
  // Close the output file.  
  writer.Close();  
  stream.Close();  
}  
  
// Close the reader and the connection.  
reader.Close();  
connection.Close();  
```  
  
## <a name="see-also"></a>Voir aussi

- [SqL Server Données binaires et à grande valeur](./sql/sql-server-binary-and-large-value-data.md)
- [Vue d'ensemble d’ADO.NET](ado-net-overview.md)
