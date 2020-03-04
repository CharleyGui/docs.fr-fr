---
title: Chiffrement de données
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- encryption [.NET Framework], symmetric
- symmetric encryption
- cryptography [.NET Framework], asymmetric
- asymmetric encryption
ms.assetid: 7ecce51f-db5f-4bd4-9321-cceb6fcb2a77
ms.openlocfilehash: 669b9c77ca0102ed94d8743cf37b18c0d0c528dc
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/28/2020
ms.locfileid: "78159401"
---
# <a name="encrypting-data"></a><span data-ttu-id="22018-102">Chiffrement de données</span><span class="sxs-lookup"><span data-stu-id="22018-102">Encrypting Data</span></span>
<span data-ttu-id="22018-103">Le chiffrement symétrique et le chiffrement asymétrique utilisent des processus différents.</span><span class="sxs-lookup"><span data-stu-id="22018-103">Symmetric encryption and asymmetric encryption are performed using different processes.</span></span> <span data-ttu-id="22018-104">Le chiffrement symétrique est effectué sur des flux. Il est donc utile pour le chiffrement de grandes quantités de données.</span><span class="sxs-lookup"><span data-stu-id="22018-104">Symmetric encryption is performed on streams and is therefore useful to encrypt large amounts of data.</span></span> <span data-ttu-id="22018-105">Le chiffrement asymétrique s'effectue sur un petit nombre d'octets. Il n'est donc utile que pour les petites quantités de données.</span><span class="sxs-lookup"><span data-stu-id="22018-105">Asymmetric encryption is performed on a small number of bytes and is therefore useful only for small amounts of data.</span></span>  
  
## <a name="symmetric-encryption"></a><span data-ttu-id="22018-106">Chiffrement symétrique</span><span class="sxs-lookup"><span data-stu-id="22018-106">Symmetric Encryption</span></span>  
 <span data-ttu-id="22018-107">Les classes managées de chiffrement symétrique sont utilisées avec une classe de flux spéciale appelée <xref:System.Security.Cryptography.CryptoStream> , qui chiffre les données lues dans le flux.</span><span class="sxs-lookup"><span data-stu-id="22018-107">The managed symmetric cryptography classes are used with a special stream class called a <xref:System.Security.Cryptography.CryptoStream> that encrypts data read into the stream.</span></span> <span data-ttu-id="22018-108">La classe **CryptoStream** est initialisée avec une classe de flux managée, une classe qui implémente l'interface <xref:System.Security.Cryptography.ICryptoTransform> (créée à partir d'une classe qui implémente un algorithme de chiffrement) et une énumération <xref:System.Security.Cryptography.CryptoStreamMode> qui décrit le type d'accès autorisé à **CryptoStream**.</span><span class="sxs-lookup"><span data-stu-id="22018-108">The **CryptoStream** class is initialized with a managed stream class, a class implements the <xref:System.Security.Cryptography.ICryptoTransform> interface (created from a class that implements a cryptographic algorithm), and a <xref:System.Security.Cryptography.CryptoStreamMode> enumeration that describes the type of access permitted to the **CryptoStream**.</span></span> <span data-ttu-id="22018-109">La classe **CryptoStream** peut être initialisée à l'aide de n'importe quelle classe dérivée de la classe <xref:System.IO.Stream> , y compris <xref:System.IO.FileStream>, <xref:System.IO.MemoryStream>et <xref:System.Net.Sockets.NetworkStream>.</span><span class="sxs-lookup"><span data-stu-id="22018-109">The **CryptoStream** class can be initialized using any class that derives from the <xref:System.IO.Stream> class, including <xref:System.IO.FileStream>, <xref:System.IO.MemoryStream>, and <xref:System.Net.Sockets.NetworkStream>.</span></span> <span data-ttu-id="22018-110">À l'aide de ces classes, vous pouvez effectuer le chiffrement symétrique sur une variété d'objets de flux.</span><span class="sxs-lookup"><span data-stu-id="22018-110">Using these classes, you can perform symmetric encryption on a variety of stream objects.</span></span>  
  
 <span data-ttu-id="22018-111">L'exemple suivant montre comment créer une instance de la classe <xref:System.Security.Cryptography.RijndaelManaged> qui implémente l'algorithme de chiffrement Rijndael, et comment l'utiliser pour effectuer un chiffrement sur une classe **CryptoStream** .</span><span class="sxs-lookup"><span data-stu-id="22018-111">The following example illustrates how to create a new instance of the <xref:System.Security.Cryptography.RijndaelManaged> class, which implements the Rijndael encryption algorithm, and use it to perform encryption on a **CryptoStream** class.</span></span> <span data-ttu-id="22018-112">Dans cet exemple, la classe **CryptoStream** est initialisée avec un objet de flux nommé `myStream` qui peut correspondre à n'importe quel type de flux managé.</span><span class="sxs-lookup"><span data-stu-id="22018-112">In this example, the **CryptoStream** is initialized with a stream object called `myStream` that can be any type of managed stream.</span></span> <span data-ttu-id="22018-113">La méthode **CreateEncryptor** de la classe **RijndaelManaged** reçoit la clé et le vecteur d'initialisation utilisés pour le chiffrement.</span><span class="sxs-lookup"><span data-stu-id="22018-113">The **CreateEncryptor** method from the **RijndaelManaged** class is passed the key and IV that are used for encryption.</span></span> <span data-ttu-id="22018-114">Dans ce cas, la clé et le vecteur d'initialisation par défaut générés à partir de `rmCrypto` sont utilisés.</span><span class="sxs-lookup"><span data-stu-id="22018-114">In this case, the default key and IV generated from `rmCrypto` are used.</span></span> <span data-ttu-id="22018-115">Enfin, **CryptoStreamMode.Write** est passé, en spécifiant l'accès en écriture dans le flux.</span><span class="sxs-lookup"><span data-stu-id="22018-115">Finally, the **CryptoStreamMode.Write** is passed, specifying write access to the stream.</span></span>  
  
```vb  
Dim rmCrypto As New RijndaelManaged()  
Dim cryptStream As New CryptoStream(myStream, rmCrypto.CreateEncryptor(rmCrypto.Key, rmCrypto.IV), CryptoStreamMode.Write)  
```  
  
```csharp  
RijndaelManaged rmCrypto = new RijndaelManaged();  
CryptoStream cryptStream = new CryptoStream(myStream, rmCrypto.CreateEncryptor(), CryptoStreamMode.Write);  
```  
  
 <span data-ttu-id="22018-116">Une fois ce code exécuté, les données écrites dans l'objet **CryptoStream** sont chiffrées à l'aide de l'algorithme Rijndael.</span><span class="sxs-lookup"><span data-stu-id="22018-116">After this code is executed, any data written to the **CryptoStream** object is encrypted using the Rijndael algorithm.</span></span>  
  
 <span data-ttu-id="22018-117">L'exemple suivant montre l'intégralité des processus de création de flux, de chiffrement de flux, d'écriture au sein de flux et de fermeture de flux.</span><span class="sxs-lookup"><span data-stu-id="22018-117">The following example shows the entire process of creating a stream, encrypting the stream, writing to the stream, and closing the stream.</span></span> <span data-ttu-id="22018-118">Cet exemple crée un flux de réseau qui est chiffré à l'aide de la classe **CryptoStream** et de la classe **RijndaelManaged** .</span><span class="sxs-lookup"><span data-stu-id="22018-118">This example creates a network stream that is encrypted using the **CryptoStream** class and the **RijndaelManaged** class.</span></span> <span data-ttu-id="22018-119">Un message est écrit dans le flux chiffré avec la classe <xref:System.IO.StreamWriter> .</span><span class="sxs-lookup"><span data-stu-id="22018-119">A message is written to the encrypted stream with the <xref:System.IO.StreamWriter> class.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="22018-120">Vous pouvez également utiliser cet exemple pour écrire dans un fichier.</span><span class="sxs-lookup"><span data-stu-id="22018-120">You can also use this example to write to a file.</span></span> <span data-ttu-id="22018-121">Pour cela, supprimez la référence <xref:System.Net.Sockets.TcpClient> et remplacez <xref:System.Net.Sockets.NetworkStream> par un <xref:System.IO.FileStream>.</span><span class="sxs-lookup"><span data-stu-id="22018-121">To do that, delete the <xref:System.Net.Sockets.TcpClient> reference and replace the <xref:System.Net.Sockets.NetworkStream> with a <xref:System.IO.FileStream>.</span></span>  
  
```vb  
Imports System  
Imports System.IO  
Imports System.Security.Cryptography  
Imports System.Net.Sockets  
  
Module Module1  
Sub Main()  
   Try  
      'Create a TCP connection to a listening TCP process.  
      'Use "localhost" to specify the current computer or  
      'replace "localhost" with the IP address of the
      'listening process.
      Dim tcp As New TcpClient("localhost", 11000)  
  
      'Create a network stream from the TCP connection.
      Dim netStream As NetworkStream = tcp.GetStream()  
  
      'Create a new instance of the RijndaelManaged class  
      'and encrypt the stream.  
      Dim rmCrypto As New RijndaelManaged()  
  
            Dim key As Byte() = {&H1, &H2, &H3, &H4, &H5, &H6, &H7, &H8, &H9, &H10, &H11, &H12, &H13, &H14, &H15, &H16}  
            Dim iv As Byte() = {&H1, &H2, &H3, &H4, &H5, &H6, &H7, &H8, &H9, &H10, &H11, &H12, &H13, &H14, &H15, &H16}  
  
      'Create a CryptoStream, pass it the NetworkStream, and encrypt
      'it with the Rijndael class.  
      Dim cryptStream As New CryptoStream(netStream, rmCrypto.CreateEncryptor(key, iv), CryptoStreamMode.Write)  
  
      'Create a StreamWriter for easy writing to the
      'network stream.  
      Dim sWriter As New StreamWriter(cryptStream)  
  
      'Write to the stream.  
      sWriter.WriteLine("Hello World!")  
  
      'Inform the user that the message was written  
      'to the stream.  
      Console.WriteLine("The message was sent.")  
  
      'Close all the connections.  
      sWriter.Close()  
      cryptStream.Close()  
      netStream.Close()  
      tcp.Close()  
   Catch  
      'Inform the user that an exception was raised.  
      Console.WriteLine("The connection failed.")  
   End Try  
End Sub  
End Module  
```  
  
```csharp  
using System;  
using System.IO;  
using System.Security.Cryptography;  
using System.Net.Sockets;  
  
public class main  
{  
   public static void Main(string[] args)  
   {  
      try  
      {  
         //Create a TCP connection to a listening TCP process.  
         //Use "localhost" to specify the current computer or  
         //replace "localhost" with the IP address of the
         //listening process.
         TcpClient tcp = new TcpClient("localhost",11000);  
  
         //Create a network stream from the TCP connection.
         NetworkStream netStream = tcp.GetStream();  
  
         //Create a new instance of the RijndaelManaged class  
         // and encrypt the stream.  
         RijndaelManaged rmCrypto = new RijndaelManaged();  
  
         byte[] key = {0x01, 0x02, 0x03, 0x04, 0x05, 0x06, 0x07, 0x08, 0x09, 0x10, 0x11, 0x12, 0x13, 0x14, 0x15, 0x16};  
         byte[] iv = {0x01, 0x02, 0x03, 0x04, 0x05, 0x06, 0x07, 0x08, 0x09, 0x10, 0x11, 0x12, 0x13, 0x14, 0x15, 0x16};  
  
         //Create a CryptoStream, pass it the NetworkStream, and encrypt
         //it with the Rijndael class.  
         CryptoStream cryptStream = new CryptoStream(netStream,
         rmCrypto.CreateEncryptor(key, iv),
         CryptoStreamMode.Write);  
  
         //Create a StreamWriter for easy writing to the
         //network stream.  
         StreamWriter sWriter = new StreamWriter(cryptStream);  
  
         //Write to the stream.  
         sWriter.WriteLine("Hello World!");  
  
         //Inform the user that the message was written  
         //to the stream.  
         Console.WriteLine("The message was sent.");  
  
         //Close all the connections.  
         sWriter.Close();  
         cryptStream.Close();  
         netStream.Close();  
         tcp.Close();  
      }  
      catch  
      {  
         //Inform the user that an exception was raised.  
         Console.WriteLine("The connection failed.");  
      }  
   }  
}  
```  
  
 <span data-ttu-id="22018-122">Pour que l’exemple précédent s’exécute correctement, un processus doit écouter l’adresse IP et le numéro de port spécifié dans la classe <xref:System.Net.Sockets.TcpClient> .</span><span class="sxs-lookup"><span data-stu-id="22018-122">For the previous example to execute successfully, there must be a process listening on the IP address and port number specified in the <xref:System.Net.Sockets.TcpClient> class.</span></span> <span data-ttu-id="22018-123">Si un processus d’écoute existe, le code se connecte à lui, chiffre le flux à l’aide de l’algorithme symétrique Rijndael et écrit « Hello World! »</span><span class="sxs-lookup"><span data-stu-id="22018-123">If a listening process exists, the code will connect to the listening process, encrypt the stream using the Rijndael symmetric algorithm, and write "Hello World!"</span></span> <span data-ttu-id="22018-124">dans le flux.</span><span class="sxs-lookup"><span data-stu-id="22018-124">to the stream.</span></span> <span data-ttu-id="22018-125">Si le code réussit, il affichera le texte suivant dans la console :</span><span class="sxs-lookup"><span data-stu-id="22018-125">If the code is successful, it displays the following text to the console:</span></span>  
  
```console  
The message was sent.  
```  
  
 <span data-ttu-id="22018-126">Toutefois, si aucun processus d'écoute n'est trouvé, ou si une exception est levée, le code affichera le texte suivant dans la console :</span><span class="sxs-lookup"><span data-stu-id="22018-126">However, if no listening process is found or an exception is raised, the code displays the following text to the console:</span></span>  
  
```console  
The connection failed.  
```  
  
## <a name="asymmetric-encryption"></a><span data-ttu-id="22018-127">Chiffrement asymétrique</span><span class="sxs-lookup"><span data-stu-id="22018-127">Asymmetric Encryption</span></span>  
 <span data-ttu-id="22018-128">Les algorithmes asymétriques sont généralement utilisés pour chiffrer de petites quantités de données telles qu'une clé symétrique et un vecteur d'initialisation.</span><span class="sxs-lookup"><span data-stu-id="22018-128">Asymmetric algorithms are usually used to encrypt small amounts of data such as the encryption of a symmetric key and IV.</span></span> <span data-ttu-id="22018-129">En règle générale, un utilisateur effectuant un chiffrement asymétrique utilise la clé publique générée par une autre partie.</span><span class="sxs-lookup"><span data-stu-id="22018-129">Typically, an individual performing asymmetric encryption uses the public key generated by another party.</span></span> <span data-ttu-id="22018-130">La classe <xref:System.Security.Cryptography.RSACryptoServiceProvider> est fournie à cet effet par .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="22018-130">The <xref:System.Security.Cryptography.RSACryptoServiceProvider> class is provided by the .NET Framework for this purpose.</span></span>  
  
 <span data-ttu-id="22018-131">L'exemple suivant utilise les informations de clé publique pour chiffrer une clé symétrique et un vecteur d'initialisation.</span><span class="sxs-lookup"><span data-stu-id="22018-131">The following example uses public key information to encrypt a symmetric key and IV.</span></span> <span data-ttu-id="22018-132">Deux tableaux d'octets qui représentent la clé publique d'un tiers sont initialisés.</span><span class="sxs-lookup"><span data-stu-id="22018-132">Two byte arrays are initialized that represent the public key of a third party.</span></span> <span data-ttu-id="22018-133">Un objet <xref:System.Security.Cryptography.RSAParameters> est initialisé vers ces valeurs.</span><span class="sxs-lookup"><span data-stu-id="22018-133">An <xref:System.Security.Cryptography.RSAParameters> object is initialized to these values.</span></span> <span data-ttu-id="22018-134">Ensuite, l'objet **RSAParameters** (avec la clé publique qu'il représente) est importé dans un **RSACryptoServiceProvider** à l'aide de la méthode <xref:System.Security.Cryptography.RSACryptoServiceProvider.ImportParameters%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="22018-134">Next, the **RSAParameters** object (along with the public key it represents) is imported into an **RSACryptoServiceProvider** using the <xref:System.Security.Cryptography.RSACryptoServiceProvider.ImportParameters%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="22018-135">Enfin, la clé privée et le vecteur d'initialisation créés par une classe <xref:System.Security.Cryptography.RijndaelManaged> sont chiffrés.</span><span class="sxs-lookup"><span data-stu-id="22018-135">Finally, the private key and IV created by a <xref:System.Security.Cryptography.RijndaelManaged> class are encrypted.</span></span> <span data-ttu-id="22018-136">Cet exemple nécessite qu'un chiffrement 128 bits soit installé sur les systèmes.</span><span class="sxs-lookup"><span data-stu-id="22018-136">This example requires systems to have 128-bit encryption installed.</span></span>  
  
```vb  
Imports System  
Imports System.Security.Cryptography  
  
Module Module1  
  
    Sub Main()  
        'Initialize the byte arrays to the public key information.  
      Dim publicKey As Byte() =  {214, 46, 220, 83, 160, 73, 40, 39, 201, 155, 19,202, 3, 11, 191, 178, 56, 74, 90, 36, 248, 103, 18, 144, 170, 163, 145, 87, 54, 61, 34, 220, 222, 207, 137, 149, 173, 14, 92, 120, 206, 222, 158, 28, 40, 24, 30, 16, 175, 108, 128, 35, 230, 118, 40, 121, 113, 125, 216, 130, 11, 24, 90, 48, 194, 240, 105, 44, 76, 34, 57, 249, 228, 125, 80, 38, 9, 136, 29, 117, 207, 139, 168, 181, 85, 137, 126, 10, 126, 242, 120, 247, 121, 8, 100, 12, 201, 171, 38, 226, 193, 180, 190, 117, 177, 87, 143, 242, 213, 11, 44, 180, 113, 93, 106, 99, 179, 68, 175, 211, 164, 116, 64, 148, 226, 254, 172, 147}  
  
        Dim exponent As Byte() = {1, 0, 1}  
  
        'Create values to store encrypted symmetric keys.  
        Dim encryptedSymmetricKey() As Byte  
        Dim encryptedSymmetricIV() As Byte  
  
        'Create a new instance of the RSACryptoServiceProvider class.  
        Dim rsa As New RSACryptoServiceProvider()  
  
        'Create a new instance of the RSAParameters structure.  
        Dim rsaKeyInfo As New RSAParameters()  
  
        'Set rsaKeyInfo to the public key values.
        rsaKeyInfo.Modulus = publicKey  
        rsaKeyInfo.Exponent = exponent  
  
        'Import key parameters into rsa.  
        rsa.ImportParameters(rsaKeyInfo)  
  
        'Create a new instance of the RijndaelManaged class.  
        Dim RM As New RijndaelManaged()  
  
        'Encrypt the symmetric key and IV.  
        encryptedSymmetricKey = rsa.Encrypt(RM.Key, False)  
        encryptedSymmetricIV = rsa.Encrypt(RM.IV, False)  
    End Sub  
  
End Module  
```  
  
```csharp  
using System;  
using System.Security.Cryptography;  
  
class Class1  
{  
   static void Main()  
   {  
      //Initialize the byte arrays to the public key information.  
      byte[] publicKey = {214,46,220,83,160,73,40,39,201,155,19,202,3,11,191,178,56,  
            74,90,36,248,103,18,144,170,163,145,87,54,61,34,220,222,  
            207,137,149,173,14,92,120,206,222,158,28,40,24,30,16,175,  
            108,128,35,230,118,40,121,113,125,216,130,11,24,90,48,194,  
            240,105,44,76,34,57,249,228,125,80,38,9,136,29,117,207,139,  
            168,181,85,137,126,10,126,242,120,247,121,8,100,12,201,171,  
            38,226,193,180,190,117,177,87,143,242,213,11,44,180,113,93,  
            106,99,179,68,175,211,164,116,64,148,226,254,172,147};  
  
      byte[] exponent = {1,0,1};  
  
      //Create values to store encrypted symmetric keys.  
      byte[] encryptedSymmetricKey;  
      byte[] encryptedSymmetricIV;  
  
      //Create a new instance of the RSACryptoServiceProvider class.  
      RSACryptoServiceProvider rsa = new RSACryptoServiceProvider();  
  
      //Create a new instance of the RSAParameters structure.  
      RSAParameters rsaKeyInfo = new RSAParameters();  
  
      //Set rsaKeyInfo to the public key values.
      rsaKeyInfo.Modulus = publicKey;  
      rsaKeyInfo.Exponent = exponent;  
  
      //Import key parameters into RSA.  
      rsa.ImportParameters(rsaKeyInfo);  
  
      //Create a new instance of the RijndaelManaged class.  
      RijndaelManaged rm = new RijndaelManaged();  
  
      //Encrypt the symmetric key and IV.  
      encryptedSymmetricKey = rsa.Encrypt(rm.Key, false);  
      encryptedSymmetricIV = rsa.Encrypt(rm.IV, false);  
   }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="22018-137">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="22018-137">See also</span></span>

- [<span data-ttu-id="22018-138">Génération de clés pour le chiffrement et le déchiffrement</span><span class="sxs-lookup"><span data-stu-id="22018-138">Generating Keys for Encryption and Decryption</span></span>](../../../docs/standard/security/generating-keys-for-encryption-and-decryption.md)
- [<span data-ttu-id="22018-139">Déchiffrement de données</span><span class="sxs-lookup"><span data-stu-id="22018-139">Decrypting Data</span></span>](../../../docs/standard/security/decrypting-data.md)
- [<span data-ttu-id="22018-140">Services de chiffrement</span><span class="sxs-lookup"><span data-stu-id="22018-140">Cryptographic Services</span></span>](../../../docs/standard/security/cryptographic-services.md)
