---
title: Déchiffrement de données
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data [.NET Framework], decryption
- symmetric decryption
- asymmetric decryption
- decryption
ms.assetid: 9b266b6c-a9b2-4d20-afd8-b3a0d8fd48a0
ms.openlocfilehash: 844561c0d207106a183243f5f2b3e0cea3e70422
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84288366"
---
# <a name="decrypting-data"></a><span data-ttu-id="9b443-102">Déchiffrement de données</span><span class="sxs-lookup"><span data-stu-id="9b443-102">Decrypting Data</span></span>

<span data-ttu-id="9b443-103">Le déchiffrement est l'opération inverse du chiffrement.</span><span class="sxs-lookup"><span data-stu-id="9b443-103">Decryption is the reverse operation of encryption.</span></span> <span data-ttu-id="9b443-104">Pour le chiffrement à clé secrète, vous devez connaître à la fois la clé et le vecteur d'initialisation qui ont été utilisés pour chiffrer les données.</span><span class="sxs-lookup"><span data-stu-id="9b443-104">For secret-key encryption, you must know both the key and IV that were used to encrypt the data.</span></span> <span data-ttu-id="9b443-105">Pour le chiffrement à clé publique, vous devez connaître soit la clé publique (si les données ont été chiffrées à l'aide de la clé privée), soit la clé privée (si les données ont été chiffrées à l'aide de la clé publique).</span><span class="sxs-lookup"><span data-stu-id="9b443-105">For public-key encryption, you must know either the public key (if the data was encrypted using the private key) or the private key (if the data was encrypted using the public key).</span></span>

## <a name="symmetric-decryption"></a><span data-ttu-id="9b443-106">Déchiffrement symétrique</span><span class="sxs-lookup"><span data-stu-id="9b443-106">Symmetric Decryption</span></span>

<span data-ttu-id="9b443-107">Le déchiffrement de données chiffrées à l'aide d'algorithmes symétriques est similaire au processus utilisé pour chiffrer les données à l'aide d'algorithmes symétriques.</span><span class="sxs-lookup"><span data-stu-id="9b443-107">The decryption of data encrypted with symmetric algorithms is similar to the process used to encrypt data with symmetric algorithms.</span></span> <span data-ttu-id="9b443-108">La classe <xref:System.Security.Cryptography.CryptoStream> est utilisée avec les classes de chiffrement symétrique fournies par .NET Framework pour déchiffrer des données lues à partir de n'importe quel objet de flux managé.</span><span class="sxs-lookup"><span data-stu-id="9b443-108">The <xref:System.Security.Cryptography.CryptoStream> class is used with symmetric cryptography classes provided by the .NET Framework to decrypt data read from any managed stream object.</span></span>

<span data-ttu-id="9b443-109">L'exemple suivant montre comment créer une instance de la classe <xref:System.Security.Cryptography.RijndaelManaged> et l'utiliser pour effectuer un déchiffrement sur un objet <xref:System.Security.Cryptography.CryptoStream> .</span><span class="sxs-lookup"><span data-stu-id="9b443-109">The following example illustrates how to create a new instance of the <xref:System.Security.Cryptography.RijndaelManaged> class and use it to perform decryption on a <xref:System.Security.Cryptography.CryptoStream> object.</span></span> <span data-ttu-id="9b443-110">Cet exemple crée d'abord une nouvelle instance de la classe **RijndaelManaged** .</span><span class="sxs-lookup"><span data-stu-id="9b443-110">This example first creates a new instance of the **RijndaelManaged** class.</span></span> <span data-ttu-id="9b443-111">Ensuite, il crée un objet **CryptoStream** et l'initialise à la valeur d'un flux managé appelé `myStream`.</span><span class="sxs-lookup"><span data-stu-id="9b443-111">Next it creates a **CryptoStream** object and initializes it to the value of a managed stream called `myStream`.</span></span> <span data-ttu-id="9b443-112">Ensuite, la méthode **CreateDecryptor** de la classe **RijndaelManaged** reçoit la même clé et le même vecteur d'initialisation que ceux utilisés pour le chiffrement. Elle est ensuite passée au constructeur **CryptoStream** .</span><span class="sxs-lookup"><span data-stu-id="9b443-112">Next, the **CreateDecryptor** method from the **RijndaelManaged** class is passed the same key and IV that was used for encryption and is then passed to the **CryptoStream** constructor.</span></span> <span data-ttu-id="9b443-113">Enfin, l'énumération **CryptoStreamMode** est passée au constructeur **CryptoStream** pour spécifier l'accès en lecture au flux.</span><span class="sxs-lookup"><span data-stu-id="9b443-113">Finally, the **CryptoStreamMode.Read** enumeration is passed to the **CryptoStream** constructor to specify read access to the stream.</span></span>

```vb
Dim rmCrypto As New RijndaelManaged()
Dim cryptStream As New CryptoStream(myStream, rmCrypto.CreateDecryptor(rmCrypto.Key, rmCrypto.IV), CryptoStreamMode.Read)
```

```csharp
RijndaelManaged rmCrypto = new RijndaelManaged();
CryptoStream cryptStream = new CryptoStream(myStream, rmCrypto.CreateDecryptor(Key, IV), CryptoStreamMode.Read);
```

<span data-ttu-id="9b443-114">L'exemple suivant montre l'intégralité des processus de création de flux, de déchiffrement de flux, de lecture depuis un flux et de fermeture de flux.</span><span class="sxs-lookup"><span data-stu-id="9b443-114">The following example shows the entire process of creating a stream, decrypting the stream, reading from the stream, and closing the streams.</span></span> <span data-ttu-id="9b443-115">Un objet <xref:System.Net.Sockets.TcpListener> est créé. Cet objet initialise un flux de réseau quand une connexion est établie avec l’objet d’écoute.</span><span class="sxs-lookup"><span data-stu-id="9b443-115">A <xref:System.Net.Sockets.TcpListener> object is created that initializes a network stream when a connection to the listening object is made.</span></span> <span data-ttu-id="9b443-116">Le flux de réseau est ensuite déchiffré à l'aide de la classe **CryptoStream** et de la classe **RijndaelManaged** .</span><span class="sxs-lookup"><span data-stu-id="9b443-116">The network stream is then decrypted using the **CryptoStream** class and the **RijndaelManaged** class.</span></span> <span data-ttu-id="9b443-117">Cet exemple suppose que les valeurs de la clé et du vecteur d'initialisation ont été transférées ou qu'elles ont fait l'objet d'un accord.</span><span class="sxs-lookup"><span data-stu-id="9b443-117">This example assumes that the key and IV values have been either successfully transferred or previously agreed upon.</span></span> <span data-ttu-id="9b443-118">Il ne montre pas le code nécessaire pour chiffrer et transférer ces valeurs.</span><span class="sxs-lookup"><span data-stu-id="9b443-118">It does not show the code needed to encrypt and transfer these values.</span></span>

```vb
Imports System.IO
Imports System.Net
Imports System.Net.Sockets
Imports System.Security.Cryptography
Imports System.Threading

Module Module1
    Sub Main()
            'The key and IV must be the same values that were used
            'to encrypt the stream.
            Dim key As Byte() = {&H1, &H2, &H3, &H4, &H5, &H6, &H7, &H8, &H9, &H10, &H11, &H12, &H13, &H14, &H15, &H16}
            Dim iv As Byte() = {&H1, &H2, &H3, &H4, &H5, &H6, &H7, &H8, &H9, &H10, &H11, &H12, &H13, &H14, &H15, &H16}
        Try
            'Initialize a TCPListener on port 11000
            'using the current IP address.
            Dim tcpListen As New TcpListener(IPAddress.Any, 11000)

            'Start the listener.
            tcpListen.Start()

            'Check for a connection every five seconds.
            While Not tcpListen.Pending()
                Console.WriteLine("Still listening. Will try in 5 seconds.")

                Thread.Sleep(5000)
            End While

            'Accept the client if one is found.
            Dim tcp As TcpClient = tcpListen.AcceptTcpClient()

            'Create a network stream from the connection.
            Dim netStream As NetworkStream = tcp.GetStream()

            'Create a new instance of the RijndaelManaged class
            'and decrypt the stream.
            Dim rmCrypto As New RijndaelManaged()

            'Create an instance of the CryptoStream class, pass it the NetworkStream, and decrypt
            'it with the Rijndael class using the key and IV.
            Dim cryptStream As New CryptoStream(netStream, rmCrypto.CreateDecryptor(key, iv), CryptoStreamMode.Read)

            'Read the stream.
            Dim sReader As New StreamReader(cryptStream)

            'Display the message.
            Console.WriteLine("The decrypted original message: {0}", sReader.ReadToEnd())

            'Close the streams.
            sReader.Close()
            netStream.Close()
            tcp.Close()
            'Catch any exceptions.
        Catch
            Console.WriteLine("The Listener Failed.")
        End Try
    End Sub
End Module
```

```csharp
using System;
using System.IO;
using System.Net;
using System.Net.Sockets;
using System.Security.Cryptography;
using System.Threading;

class Class1
{
   static void Main(string[] args)
   {
      //The key and IV must be the same values that were used
      //to encrypt the stream.
      byte[] key = {0x01, 0x02, 0x03, 0x04, 0x05, 0x06, 0x07, 0x08, 0x09, 0x10, 0x11, 0x12, 0x13, 0x14, 0x15, 0x16};
      byte[] iv = {0x01, 0x02, 0x03, 0x04, 0x05, 0x06, 0x07, 0x08, 0x09, 0x10, 0x11, 0x12, 0x13, 0x14, 0x15, 0x16};
      try
      {
         //Initialize a TCPListener on port 11000
         //using the current IP address.
         TcpListener tcpListen = new TcpListener(IPAddress.Any, 11000);

         //Start the listener.
         tcpListen.Start();

         //Check for a connection every five seconds.
         while(!tcpListen.Pending())
         {
            Console.WriteLine("Still listening. Will try in 5 seconds.");
            Thread.Sleep(5000);
         }

         //Accept the client if one is found.
         TcpClient tcp = tcpListen.AcceptTcpClient();

         //Create a network stream from the connection.
         NetworkStream netStream = tcp.GetStream();

         //Create a new instance of the RijndaelManaged class
         // and decrypt the stream.
         RijndaelManaged rmCrypto = new RijndaelManaged();

         //Create a CryptoStream, pass it the NetworkStream, and decrypt
         //it with the Rijndael class using the key and IV.
         CryptoStream cryptStream = new CryptoStream(netStream,
            rmCrypto.CreateDecryptor(key, iv),
            CryptoStreamMode.Read);

         //Read the stream.
         StreamReader sReader = new StreamReader(cryptStream);

         //Display the message.
         Console.WriteLine("The decrypted original message: {0}", sReader.ReadToEnd());

         //Close the streams.
         sReader.Close();
         netStream.Close();
         tcp.Close();
      }
      //Catch any exceptions.
      catch
      {
         Console.WriteLine("The Listener Failed.");
      }
   }
}
```

<span data-ttu-id="9b443-119">Pour que l'exemple précédent fonctionne, une connexion chiffrée doit être établie avec l'écouteur.</span><span class="sxs-lookup"><span data-stu-id="9b443-119">For the previous sample to work, an encrypted connection must be made to the listener.</span></span> <span data-ttu-id="9b443-120">La connexion doit utiliser la même clé, le même vecteur d'initialisation et le même algorithme que ceux utilisés par l'écouteur.</span><span class="sxs-lookup"><span data-stu-id="9b443-120">The connection must use the same key, IV, and algorithm used in the listener.</span></span> <span data-ttu-id="9b443-121">Si une telle connexion est établie, le message est déchiffré et s'affiche dans la console.</span><span class="sxs-lookup"><span data-stu-id="9b443-121">If such a connection is made, the message is decrypted and displayed to the console.</span></span>

## <a name="asymmetric-decryption"></a><span data-ttu-id="9b443-122">Déchiffrement asymétrique</span><span class="sxs-lookup"><span data-stu-id="9b443-122">Asymmetric Decryption</span></span>

<span data-ttu-id="9b443-123">En règle générale, une partie (partie A) génère à la fois une clé publique et une clé privée, et stocke ces clés dans la mémoire ou dans un conteneur de clé de chiffrement.</span><span class="sxs-lookup"><span data-stu-id="9b443-123">Typically, a party (party A) generates both a public and private key and stores the key either in memory or in a cryptographic key container.</span></span> <span data-ttu-id="9b443-124">La partie A envoie ensuite la clé publique à une autre partie (partie B).</span><span class="sxs-lookup"><span data-stu-id="9b443-124">Party A then sends the public key to another party (party B).</span></span> <span data-ttu-id="9b443-125">À l’aide de la clé publique, le tiers B chiffre les données et renvoie les données au tiers A. Après avoir reçu les données, la partie A les déchiffre à l’aide de la clé privée qui correspond.</span><span class="sxs-lookup"><span data-stu-id="9b443-125">Using the public key, party B encrypts data and sends the data back to party A. After receiving the data, party A decrypts it using the private key that corresponds.</span></span> <span data-ttu-id="9b443-126">Le déchiffrement réussira uniquement si la partie A utilise la clé privée qui correspond à la clé publique utilisée par la partie B pour chiffrer les données.</span><span class="sxs-lookup"><span data-stu-id="9b443-126">Decryption will be successful only if party A uses the private key that corresponds to the public key Party B used to encrypt the data.</span></span>

<span data-ttu-id="9b443-127">Pour plus d’informations sur le stockage des clés asymétriques dans un conteneur de clé de chiffrement sécurisé et sur la récupération des clés asymétriques, consultez [How to: Store Asymmetric Keys in a Key Container](how-to-store-asymmetric-keys-in-a-key-container.md).</span><span class="sxs-lookup"><span data-stu-id="9b443-127">For information on how to store an asymmetric key in secure cryptographic key container and how to later retrieve the asymmetric key, see [How to: Store Asymmetric Keys in a Key Container](how-to-store-asymmetric-keys-in-a-key-container.md).</span></span>

<span data-ttu-id="9b443-128">L'exemple suivant montre le déchiffrement de deux tableaux d'octets qui représentent une clé symétrique et un vecteur d'initialisation.</span><span class="sxs-lookup"><span data-stu-id="9b443-128">The following example illustrates the decryption of two arrays of bytes that represent a symmetric key and IV.</span></span> <span data-ttu-id="9b443-129">Pour plus d’informations sur l’extraction de la clé publique asymétrique de l’objet <xref:System.Security.Cryptography.RSACryptoServiceProvider> dans un format que vous pouvez facilement envoyer à un tiers, consultez [Encrypting Data](encrypting-data.md).</span><span class="sxs-lookup"><span data-stu-id="9b443-129">For information on how to extract the asymmetric public key from the <xref:System.Security.Cryptography.RSACryptoServiceProvider> object in a format that you can easily send to a third party, see [Encrypting Data](encrypting-data.md).</span></span>

```vb
'Create a new instance of the RSACryptoServiceProvider class.
Dim rsa As New RSACryptoServiceProvider()

' Export the public key information and send it to a third party.
' Wait for the third party to encrypt some data and send it back.

'Decrypt the symmetric key and IV.
symmetricKey = rsa.Decrypt(encryptedSymmetricKey, False)
symmetricIV = rsa.Decrypt(encryptedSymmetricIV, False)
```

```csharp
//Create a new instance of the RSACryptoServiceProvider class.
RSACryptoServiceProvider rsa = new RSACryptoServiceProvider();

// Export the public key information and send it to a third party.
// Wait for the third party to encrypt some data and send it back.

//Decrypt the symmetric key and IV.
symmetricKey = rsa.Decrypt(encryptedSymmetricKey, false);
symmetricIV = rsa.Decrypt(encryptedSymmetricIV , false);
```

## <a name="see-also"></a><span data-ttu-id="9b443-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9b443-130">See also</span></span>

- [<span data-ttu-id="9b443-131">Génération de clés pour le chiffrement et le déchiffrement</span><span class="sxs-lookup"><span data-stu-id="9b443-131">Generating Keys for Encryption and Decryption</span></span>](generating-keys-for-encryption-and-decryption.md)
- [<span data-ttu-id="9b443-132">Chiffrement de données</span><span class="sxs-lookup"><span data-stu-id="9b443-132">Encrypting Data</span></span>](encrypting-data.md)
- [<span data-ttu-id="9b443-133">Services de chiffrement</span><span class="sxs-lookup"><span data-stu-id="9b443-133">Cryptographic Services</span></span>](cryptographic-services.md)
