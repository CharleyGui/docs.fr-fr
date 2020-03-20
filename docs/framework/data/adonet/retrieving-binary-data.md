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
# <a name="retrieving-binary-data"></a><span data-ttu-id="cb8eb-102">Extraction de données binaires</span><span class="sxs-lookup"><span data-stu-id="cb8eb-102">Retrieving Binary Data</span></span>
<span data-ttu-id="cb8eb-103">Par défaut, le **DataReader** charge les données entrantes dès qu’une série entière de données est disponible.</span><span class="sxs-lookup"><span data-stu-id="cb8eb-103">By default, the **DataReader** loads incoming data as a row as soon as an entire row of data is available.</span></span> <span data-ttu-id="cb8eb-104">Les objets binaires volumineux ou BLOB doivent néanmoins être traités différemment car ils peuvent renfermer plusieurs gigaoctets de données qu'une seule ligne ne suffirait pas à contenir.</span><span class="sxs-lookup"><span data-stu-id="cb8eb-104">Binary large objects (BLOBs) need different treatment, however, because they can contain gigabytes of data that cannot be contained in a single row.</span></span> <span data-ttu-id="cb8eb-105">La méthode **Command.ExecuteReader** a une surcharge <xref:System.Data.CommandBehavior> qui prendra un argument pour modifier le comportement par défaut du **DataReader**.</span><span class="sxs-lookup"><span data-stu-id="cb8eb-105">The **Command.ExecuteReader** method has an overload that will take a <xref:System.Data.CommandBehavior> argument to modify the default behavior of the **DataReader**.</span></span> <span data-ttu-id="cb8eb-106">Vous pouvez <xref:System.Data.CommandBehavior.SequentialAccess> passer à la méthode **ExecuteReader** pour modifier le comportement par défaut du **DataReader** de sorte qu’au lieu de charger des lignes de données, il chargera les données de manière séquentielle au fur et à mesure qu’elle est reçue.</span><span class="sxs-lookup"><span data-stu-id="cb8eb-106">You can pass <xref:System.Data.CommandBehavior.SequentialAccess> to the **ExecuteReader** method to modify the default behavior of the **DataReader** so that instead of loading rows of data, it will load data sequentially as it is received.</span></span> <span data-ttu-id="cb8eb-107">Cela est idéal pour charger les BLOB ou d'autres grosses structures de données.</span><span class="sxs-lookup"><span data-stu-id="cb8eb-107">This is ideal for loading BLOBs or other large data structures.</span></span> <span data-ttu-id="cb8eb-108">Notez que ce comportement peut différer selon votre source de données.</span><span class="sxs-lookup"><span data-stu-id="cb8eb-108">Note that this behavior may depend on your data source.</span></span> <span data-ttu-id="cb8eb-109">Par exemple, un BLOB retourné de Microsoft Access est entièrement chargé dans la mémoire, au lieu que les données soient chargées de façon séquentielle à mesure qu'elles arrivent.</span><span class="sxs-lookup"><span data-stu-id="cb8eb-109">For example, returning a BLOB from Microsoft Access will load the entire BLOB being loaded into memory, rather than sequentially as it is received.</span></span>  
  
 <span data-ttu-id="cb8eb-110">Lors de la définition du **DataReader** pour utiliser **SequentialAccess**, il est important de noter la séquence dans laquelle vous accédez aux champs retournés.</span><span class="sxs-lookup"><span data-stu-id="cb8eb-110">When setting the **DataReader** to use **SequentialAccess**, it is important to note the sequence in which you access the fields returned.</span></span> <span data-ttu-id="cb8eb-111">Le comportement par défaut du **DataReader**, qui charge une ligne entière dès qu’il est disponible, vous permet d’accéder aux champs retournés dans n’importe quel ordre jusqu’à ce que la prochaine ligne soit lue.</span><span class="sxs-lookup"><span data-stu-id="cb8eb-111">The default behavior of the **DataReader**, which loads an entire row as soon as it is available, allows you to access the fields returned in any order until the next row is read.</span></span> <span data-ttu-id="cb8eb-112">Lors de **l’utilisation de SéquentialAccess** cependant, vous devez accéder aux champs retournés par le **DataReader** dans l’ordre.</span><span class="sxs-lookup"><span data-stu-id="cb8eb-112">When using **SequentialAccess** however, you must access the fields returned by the **DataReader** in order.</span></span> <span data-ttu-id="cb8eb-113">Par exemple, si votre requête retourne trois colonnes, la troisième étant un BLOB, vous devez retourner les valeurs des premier et deuxième champs avant d'accéder aux données BLOB du troisième champ.</span><span class="sxs-lookup"><span data-stu-id="cb8eb-113">For example, if your query returns three columns, the third of which is a BLOB, you must return the values of the first and second fields before accessing the BLOB data in the third field.</span></span> <span data-ttu-id="cb8eb-114">Si vous accédez au troisième champ avant le premier ou le deuxième, les valeurs de ces champs ne seront plus disponibles.</span><span class="sxs-lookup"><span data-stu-id="cb8eb-114">If you access the third field before the first or second fields, the first and second field values are no longer available.</span></span> <span data-ttu-id="cb8eb-115">C’est parce que **SequentialAccess** a modifié le **DataReader** pour retourner les données dans l’ordre et les données ne sont pas disponibles après que le **DataReader** l’a lu au-delà.</span><span class="sxs-lookup"><span data-stu-id="cb8eb-115">This is because **SequentialAccess** has modified the **DataReader** to return data in sequence and the data is not available after the **DataReader** has read past it.</span></span>  
  
 <span data-ttu-id="cb8eb-116">Lors de l’accès aux données dans le champ BLOB, utilisez les accesseurs dactylographes **GetBytes** ou **GetChars** du **DataReader**, qui remplissent un tableau de données.</span><span class="sxs-lookup"><span data-stu-id="cb8eb-116">When accessing the data in the BLOB field, use the **GetBytes** or **GetChars** typed accessors of the **DataReader**, which fill an array with data.</span></span> <span data-ttu-id="cb8eb-117">Vous pouvez également utiliser **GetString** pour les données de caractère; Cependant.</span><span class="sxs-lookup"><span data-stu-id="cb8eb-117">You can also use **GetString** for character data; however.</span></span> <span data-ttu-id="cb8eb-118">pour économiser les ressources système, vous souhaitez peut-être ne pas charger la valeur entière du BLOB dans une seule variable chaîne.</span><span class="sxs-lookup"><span data-stu-id="cb8eb-118">to conserve system resources you might not want to load an entire BLOB value into a single string variable.</span></span> <span data-ttu-id="cb8eb-119">Au lieu de cela, vous pouvez spécifier une taille de mémoire tampon spécifique des données à retourner ainsi qu'un emplacement de départ pour le premier octet ou le premier caractère lu des données retournées.</span><span class="sxs-lookup"><span data-stu-id="cb8eb-119">You can instead specify a specific buffer size of data to be returned, and a starting location for the first byte or character to be read from the returned data.</span></span> <span data-ttu-id="cb8eb-120">**GetBytes** et **GetChars** `long` retourneront une valeur, qui représente le nombre d’octets ou de caractères retournés.</span><span class="sxs-lookup"><span data-stu-id="cb8eb-120">**GetBytes** and **GetChars** will return a `long` value, which represents the number of bytes or characters returned.</span></span> <span data-ttu-id="cb8eb-121">Si vous passez un tableau nul à **GetBytes** ou **GetChars**, la valeur longue retournée sera le nombre total d’octets ou de caractères dans le BLOB.</span><span class="sxs-lookup"><span data-stu-id="cb8eb-121">If you pass a null array to **GetBytes** or **GetChars**, the long value returned will be the total number of bytes or characters in the BLOB.</span></span> <span data-ttu-id="cb8eb-122">Vous pouvez éventuellement spécifier un index dans le tableau comme position de départ pour les données en cours de lecture.</span><span class="sxs-lookup"><span data-stu-id="cb8eb-122">You can optionally specify an index in the array as a starting position for the data being read.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cb8eb-123"> Exemple</span><span class="sxs-lookup"><span data-stu-id="cb8eb-123">Example</span></span>  
 <span data-ttu-id="cb8eb-124">L’exemple suivant renvoie l’identifiant et le logo de l’éditeur de la base de données d’échantillons **de pubs** dans Microsoft SQL Server.</span><span class="sxs-lookup"><span data-stu-id="cb8eb-124">The following example returns the publisher ID and logo from the **pubs** sample database in Microsoft SQL Server.</span></span> <span data-ttu-id="cb8eb-125">L'ID de l'éditeur (`pub_id`) est un champ texte et le logo est une image (un BLOB).</span><span class="sxs-lookup"><span data-stu-id="cb8eb-125">The publisher ID (`pub_id`) is a character field, and the logo is an image, which is a BLOB.</span></span> <span data-ttu-id="cb8eb-126">Parce que le champ **de logo** est un bitmap, l’exemple renvoie les données binaires en utilisant **GetBytes**.</span><span class="sxs-lookup"><span data-stu-id="cb8eb-126">Because the **logo** field is a bitmap, the example returns binary data using **GetBytes**.</span></span> <span data-ttu-id="cb8eb-127">Notez que pour la ligne de données actuelle, il faut accéder à l'ID de l'éditeur avant d'accéder au logo car l'accès aux champs doit être séquentiel.</span><span class="sxs-lookup"><span data-stu-id="cb8eb-127">Notice that the publisher ID is accessed for the current row of data before the logo, because the fields must be accessed sequentially.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="cb8eb-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="cb8eb-128">See also</span></span>

- [<span data-ttu-id="cb8eb-129">SqL Server Données binaires et à grande valeur</span><span class="sxs-lookup"><span data-stu-id="cb8eb-129">SQL Server Binary and Large-Value Data</span></span>](./sql/sql-server-binary-and-large-value-data.md)
- [<span data-ttu-id="cb8eb-130">Vue d'ensemble d’ADO.NET</span><span class="sxs-lookup"><span data-stu-id="cb8eb-130">ADO.NET Overview</span></span>](ado-net-overview.md)
