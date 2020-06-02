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
ms.openlocfilehash: 3230836b93ea191e5de27717a918038f2f8dead6
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84288353"
---
# <a name="encrypting-data"></a>Chiffrement de données
Le chiffrement symétrique et le chiffrement asymétrique utilisent des processus différents. Le chiffrement symétrique est effectué sur des flux. Il est donc utile pour le chiffrement de grandes quantités de données. Le chiffrement asymétrique s'effectue sur un petit nombre d'octets. Il n'est donc utile que pour les petites quantités de données.  
  
## <a name="symmetric-encryption"></a>Chiffrement symétrique  
 Les classes managées de chiffrement symétrique sont utilisées avec une classe de flux spéciale appelée <xref:System.Security.Cryptography.CryptoStream> , qui chiffre les données lues dans le flux. La classe **CryptoStream** est initialisée avec une classe de flux managée, une classe qui implémente l'interface <xref:System.Security.Cryptography.ICryptoTransform> (créée à partir d'une classe qui implémente un algorithme de chiffrement) et une énumération <xref:System.Security.Cryptography.CryptoStreamMode> qui décrit le type d'accès autorisé à **CryptoStream**. La classe **CryptoStream** peut être initialisée à l’aide de n’importe quelle classe qui dérive de la <xref:System.IO.Stream> classe, y compris <xref:System.IO.FileStream> , <xref:System.IO.MemoryStream> et <xref:System.Net.Sockets.NetworkStream> . À l'aide de ces classes, vous pouvez effectuer le chiffrement symétrique sur une variété d'objets de flux.  
  
 L'exemple suivant montre comment créer une instance de la classe <xref:System.Security.Cryptography.RijndaelManaged> qui implémente l'algorithme de chiffrement Rijndael, et comment l'utiliser pour effectuer un chiffrement sur une classe **CryptoStream** . Dans cet exemple, la classe **CryptoStream** est initialisée avec un objet de flux nommé `myStream` qui peut correspondre à n'importe quel type de flux managé. La méthode **CreateEncryptor** de la classe **RijndaelManaged** reçoit la clé et le vecteur d'initialisation utilisés pour le chiffrement. Dans ce cas, la clé et le vecteur d'initialisation par défaut générés à partir de `rmCrypto` sont utilisés. Enfin, **CryptoStreamMode.Write** est passé, en spécifiant l'accès en écriture dans le flux.  
  
```vb  
Dim rmCrypto As New RijndaelManaged()  
Dim cryptStream As New CryptoStream(myStream, rmCrypto.CreateEncryptor(rmCrypto.Key, rmCrypto.IV), CryptoStreamMode.Write)  
```  
  
```csharp  
RijndaelManaged rmCrypto = new RijndaelManaged();  
CryptoStream cryptStream = new CryptoStream(myStream, rmCrypto.CreateEncryptor(), CryptoStreamMode.Write);  
```  
  
 Une fois ce code exécuté, les données écrites dans l'objet **CryptoStream** sont chiffrées à l'aide de l'algorithme Rijndael.  
  
 L'exemple suivant montre l'intégralité des processus de création de flux, de chiffrement de flux, d'écriture au sein de flux et de fermeture de flux. Cet exemple crée un flux de réseau qui est chiffré à l'aide de la classe **CryptoStream** et de la classe **RijndaelManaged** . Un message est écrit dans le flux chiffré avec la classe <xref:System.IO.StreamWriter> .  
  
> [!NOTE]
> Vous pouvez également utiliser cet exemple pour écrire dans un fichier. Pour cela, supprimez la référence <xref:System.Net.Sockets.TcpClient> et remplacez <xref:System.Net.Sockets.NetworkStream> par un <xref:System.IO.FileStream>.  
  
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
  
 Pour que l’exemple précédent s’exécute correctement, un processus doit écouter l’adresse IP et le numéro de port spécifié dans la classe <xref:System.Net.Sockets.TcpClient> . Si un processus d’écoute existe, le code se connecte à lui, chiffre le flux à l’aide de l’algorithme symétrique Rijndael et écrit « Hello World! » dans le flux. Si le code réussit, il affichera le texte suivant dans la console :  
  
```console  
The message was sent.  
```  
  
 Toutefois, si aucun processus d'écoute n'est trouvé, ou si une exception est levée, le code affichera le texte suivant dans la console :  
  
```console  
The connection failed.  
```  
  
## <a name="asymmetric-encryption"></a>Chiffrement asymétrique  
 Les algorithmes asymétriques sont généralement utilisés pour chiffrer de petites quantités de données telles qu'une clé symétrique et un vecteur d'initialisation. En règle générale, un utilisateur effectuant un chiffrement asymétrique utilise la clé publique générée par une autre partie. La classe <xref:System.Security.Cryptography.RSACryptoServiceProvider> est fournie à cet effet par .NET Framework.  
  
 L'exemple suivant utilise les informations de clé publique pour chiffrer une clé symétrique et un vecteur d'initialisation. Deux tableaux d'octets qui représentent la clé publique d'un tiers sont initialisés. Un objet <xref:System.Security.Cryptography.RSAParameters> est initialisé vers ces valeurs. Ensuite, l'objet **RSAParameters** (avec la clé publique qu'il représente) est importé dans un **RSACryptoServiceProvider** à l'aide de la méthode <xref:System.Security.Cryptography.RSACryptoServiceProvider.ImportParameters%2A?displayProperty=nameWithType> . Enfin, la clé privée et le vecteur d'initialisation créés par une classe <xref:System.Security.Cryptography.RijndaelManaged> sont chiffrés. Cet exemple nécessite qu'un chiffrement 128 bits soit installé sur les systèmes.  
  
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
  
## <a name="see-also"></a>Voir aussi

- [Génération de clés pour le chiffrement et le déchiffrement](generating-keys-for-encryption-and-decryption.md)
- [Déchiffrement de données](decrypting-data.md)
- [Services de chiffrement](cryptographic-services.md)
