---
title: Extraction de données binaires
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 56c5a9e3-31f1-482f-bce0-ff1c41a658d0
ms.openlocfilehash: 11f7a81bc0d4b0e2a8d66387410d9a24503c7519
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91150659"
---
# <a name="retrieving-binary-data"></a>Extraction de données binaires

Par défaut, le **DataReader** charge les données entrantes sous forme de ligne dès qu’une ligne entière de données est disponible. Les objets binaires volumineux ou BLOB doivent néanmoins être traités différemment car ils peuvent renfermer plusieurs gigaoctets de données qu'une seule ligne ne suffirait pas à contenir. La méthode **Command.ExecuteReader** a une surcharge qui prendra un <xref:System.Data.CommandBehavior> argument pour modifier le comportement par défaut du **DataReader**. Vous pouvez passer <xref:System.Data.CommandBehavior.SequentialAccess> à la méthode **ExecuteReader** pour modifier le comportement par défaut du **DataReader** de sorte qu’au lieu de charger des lignes de données, il charge les données de manière séquentielle au fur et à mesure de leur réception. Cela est idéal pour charger les BLOB ou d'autres grosses structures de données. Notez que ce comportement peut différer selon votre source de données. Par exemple, un BLOB retourné de Microsoft Access est entièrement chargé dans la mémoire, au lieu que les données soient chargées de façon séquentielle à mesure qu'elles arrivent.  
  
 Quand vous définissez le **DataReader** pour utiliser **SequentialAccess**, il est important de noter l’ordre dans lequel vous accédez aux champs retournés. Le comportement par défaut du **DataReader**, qui charge une ligne entière dès qu’il est disponible, vous permet d’accéder aux champs retournés dans n’importe quel ordre jusqu’à la lecture de la ligne suivante. Toutefois, lors de l’utilisation de **SequentialAccess** , vous devez accéder aux champs retournés par le **DataReader** dans l’ordre. Par exemple, si votre requête retourne trois colonnes, la troisième étant un BLOB, vous devez retourner les valeurs des premier et deuxième champs avant d'accéder aux données BLOB du troisième champ. Si vous accédez au troisième champ avant le premier ou le deuxième, les valeurs de ces champs ne seront plus disponibles. Cela est dû au fait que **SequentialAccess** a modifié **DataReader** pour retourner des données en séquence et que les données ne sont pas disponibles après la lecture du **DataReader** .  
  
 Lors de l’accès aux données dans le champ BLOB, utilisez les accesseurs de type **GetBytes** ou **GetChars** du **DataReader**, qui remplissent un tableau avec des données. Vous pouvez également utiliser **GetString** pour les données de caractères ; Toutefois. pour économiser les ressources système, vous souhaitez peut-être ne pas charger la valeur entière du BLOB dans une seule variable chaîne. Au lieu de cela, vous pouvez spécifier une taille de mémoire tampon spécifique des données à retourner ainsi qu'un emplacement de départ pour le premier octet ou le premier caractère lu des données retournées. **GetBytes** et **GetChars** retournent une `long` valeur, qui représente le nombre d’octets ou de caractères retournés. Si vous transmettez un tableau null à **GetBytes** ou **GetChars**, la valeur long retournée est le nombre total d’octets ou de caractères dans l’objet BLOB. Vous pouvez éventuellement spécifier un index dans le tableau comme position de départ pour les données en cours de lecture.  
  
## <a name="example"></a>Exemple  

 L’exemple suivant retourne l’ID et le logo de l’éditeur de l’exemple de base de données **pubs** dans Microsoft SQL Server. L'ID de l'éditeur (`pub_id`) est un champ texte et le logo est une image (un BLOB). Étant donné que le champ **logo** est une image bitmap, l’exemple retourne des données binaires à l’aide de **GetBytes**. Notez que pour la ligne de données actuelle, il faut accéder à l'ID de l'éditeur avant d'accéder au logo car l'accès aux champs doit être séquentiel.  
  
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

- [SQL Server des données binaires et de grande valeur](./sql/sql-server-binary-and-large-value-data.md)
- [Vue d'ensemble d’ADO.NET](ado-net-overview.md)
