---
title: Chiffrement de données
description: Découvrez comment chiffrer des données dans .NET, à l’aide d’un algorithme symétrique ou d’un algorithme asymétrique.
ms.date: 07/14/2020
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- encryption [.NET], symmetric
- symmetric encryption
- cryptography [.NET], asymmetric
- asymmetric encryption
ms.assetid: 7ecce51f-db5f-4bd4-9321-cceb6fcb2a77
ms.openlocfilehash: 8a8b5988a13ab571284b08c7aaece3542467aa71
ms.sourcegitcommit: b7a8b09828bab4e90f66af8d495ecd7024c45042
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87556967"
---
# <a name="encrypting-data"></a><span data-ttu-id="5f094-103">Chiffrement de données</span><span class="sxs-lookup"><span data-stu-id="5f094-103">Encrypting Data</span></span>

<span data-ttu-id="5f094-104">Le chiffrement symétrique et le chiffrement asymétrique utilisent des processus différents.</span><span class="sxs-lookup"><span data-stu-id="5f094-104">Symmetric encryption and asymmetric encryption are performed using different processes.</span></span> <span data-ttu-id="5f094-105">Le chiffrement symétrique est effectué sur des flux. Il est donc utile pour le chiffrement de grandes quantités de données.</span><span class="sxs-lookup"><span data-stu-id="5f094-105">Symmetric encryption is performed on streams and is therefore useful to encrypt large amounts of data.</span></span> <span data-ttu-id="5f094-106">Le chiffrement asymétrique s'effectue sur un petit nombre d'octets. Il n'est donc utile que pour les petites quantités de données.</span><span class="sxs-lookup"><span data-stu-id="5f094-106">Asymmetric encryption is performed on a small number of bytes and is therefore useful only for small amounts of data.</span></span>  
  
## <a name="symmetric-encryption"></a><span data-ttu-id="5f094-107">Chiffrement symétrique</span><span class="sxs-lookup"><span data-stu-id="5f094-107">Symmetric Encryption</span></span>  

<span data-ttu-id="5f094-108">Les classes managées de chiffrement symétrique sont utilisées avec une classe de flux spéciale appelée <xref:System.Security.Cryptography.CryptoStream> , qui chiffre les données lues dans le flux.</span><span class="sxs-lookup"><span data-stu-id="5f094-108">The managed symmetric cryptography classes are used with a special stream class called a <xref:System.Security.Cryptography.CryptoStream> that encrypts data read into the stream.</span></span> <span data-ttu-id="5f094-109">La classe **CryptoStream** est initialisée avec une classe de flux managée, une classe qui implémente l' <xref:System.Security.Cryptography.ICryptoTransform> interface (créée à partir d’une classe qui implémente un algorithme de chiffrement) et une <xref:System.Security.Cryptography.CryptoStreamMode> énumération qui décrit le type d’accès autorisé à la classe **CryptoStream**.</span><span class="sxs-lookup"><span data-stu-id="5f094-109">The **CryptoStream** class is initialized with a managed stream class, a class that implements the <xref:System.Security.Cryptography.ICryptoTransform> interface (created from a class that implements a cryptographic algorithm), and a <xref:System.Security.Cryptography.CryptoStreamMode> enumeration that describes the type of access permitted to the **CryptoStream**.</span></span> <span data-ttu-id="5f094-110">La classe **CryptoStream** peut être initialisée à l’aide de n’importe quelle classe qui dérive de la <xref:System.IO.Stream> classe, y compris <xref:System.IO.FileStream> , <xref:System.IO.MemoryStream> et <xref:System.Net.Sockets.NetworkStream> .</span><span class="sxs-lookup"><span data-stu-id="5f094-110">The **CryptoStream** class can be initialized using any class that derives from the <xref:System.IO.Stream> class, including <xref:System.IO.FileStream>, <xref:System.IO.MemoryStream>, and <xref:System.Net.Sockets.NetworkStream>.</span></span> <span data-ttu-id="5f094-111">À l'aide de ces classes, vous pouvez effectuer le chiffrement symétrique sur une variété d'objets de flux.</span><span class="sxs-lookup"><span data-stu-id="5f094-111">Using these classes, you can perform symmetric encryption on a variety of stream objects.</span></span>  
  
<span data-ttu-id="5f094-112">L’exemple suivant illustre la création d’une nouvelle instance de la classe d’implémentation par défaut pour l' <xref:System.Security.Cryptography.Aes> algorithme.</span><span class="sxs-lookup"><span data-stu-id="5f094-112">The following example illustrates how to create a new instance of the default implementation class for the <xref:System.Security.Cryptography.Aes> algorithm.</span></span> <span data-ttu-id="5f094-113">L’instance est utilisée pour effectuer le chiffrement sur une classe **CryptoStream** .</span><span class="sxs-lookup"><span data-stu-id="5f094-113">The instance is used to perform encryption on a **CryptoStream** class.</span></span> <span data-ttu-id="5f094-114">Dans cet exemple, la classe **CryptoStream** est initialisée avec un objet de flux nommé `myStream` qui peut correspondre à n'importe quel type de flux managé.</span><span class="sxs-lookup"><span data-stu-id="5f094-114">In this example, the **CryptoStream** is initialized with a stream object called `myStream` that can be any type of managed stream.</span></span> <span data-ttu-id="5f094-115">La méthode **CreateEncryptor** de la classe **AES** reçoit la clé et le vecteur d’utilisation utilisés pour le chiffrement.</span><span class="sxs-lookup"><span data-stu-id="5f094-115">The **CreateEncryptor** method from the **Aes** class is passed the key and IV that are used for encryption.</span></span> <span data-ttu-id="5f094-116">Dans ce cas, la clé et le vecteur d'initialisation par défaut générés à partir de `aes` sont utilisés.</span><span class="sxs-lookup"><span data-stu-id="5f094-116">In this case, the default key and IV generated from `aes` are used.</span></span>
  
```vb  
Dim aes As Aes = Aes.Create()  
Dim cryptStream As New CryptoStream(myStream, aes.CreateEncryptor(key, iv), CryptoStreamMode.Write)  
```  
  
```csharp  
Aes aes = Aes.Create();  
CryptoStream cryptStream = new CryptoStream(myStream, aes.CreateEncryptor(key, iv), CryptoStreamMode.Write);  
```  
  
<span data-ttu-id="5f094-117">Une fois ce code exécuté, toutes les données écrites dans l’objet **CryptoStream** sont chiffrées à l’aide de l’algorithme AES.</span><span class="sxs-lookup"><span data-stu-id="5f094-117">After this code is executed, any data written to the **CryptoStream** object is encrypted using the AES algorithm.</span></span>  
  
<span data-ttu-id="5f094-118">L'exemple suivant montre l'intégralité des processus de création de flux, de chiffrement de flux, d'écriture au sein de flux et de fermeture de flux.</span><span class="sxs-lookup"><span data-stu-id="5f094-118">The following example shows the entire process of creating a stream, encrypting the stream, writing to the stream, and closing the stream.</span></span> <span data-ttu-id="5f094-119">Cet exemple crée un flux de fichier qui est chiffré à l’aide de la classe **CryptoStream** et de la classe **AES** .</span><span class="sxs-lookup"><span data-stu-id="5f094-119">This example creates a file stream that is encrypted using the **CryptoStream** class and the **Aes** class.</span></span> <span data-ttu-id="5f094-120">Un message est écrit dans le flux chiffré avec la classe <xref:System.IO.StreamWriter> .</span><span class="sxs-lookup"><span data-stu-id="5f094-120">A message is written to the encrypted stream with the <xref:System.IO.StreamWriter> class.</span></span>
  
:::code language="csharp" source="snippets/encrypting-data/csharp/aes-encrypt.cs":::
:::code language="vb" source="snippets/encrypting-data/vb/aes-encrypt.vb":::

<span data-ttu-id="5f094-121">Le code chiffre le flux à l’aide de l’algorithme symétrique AES et écrit « Hello World ! »</span><span class="sxs-lookup"><span data-stu-id="5f094-121">The code encrypts the stream using the AES symmetric algorithm, and writes "Hello World!"</span></span> <span data-ttu-id="5f094-122">dans le flux.</span><span class="sxs-lookup"><span data-stu-id="5f094-122">to the stream.</span></span> <span data-ttu-id="5f094-123">Si le code réussit, il crée un fichier chiffré nommé *TestData.txt* et affiche le texte suivant dans la console :</span><span class="sxs-lookup"><span data-stu-id="5f094-123">If the code is successful, it creates an encrypted file named *TestData.txt* and displays the following text to the console:</span></span>  
  
```console  
The text was encrypted.  
```  

<span data-ttu-id="5f094-124">Vous pouvez déchiffrer le fichier à l’aide de l’exemple de déchiffrement symétrique dans [déchiffrement des données](decrypting-data.md).</span><span class="sxs-lookup"><span data-stu-id="5f094-124">You can decrypt the file by using the symmetric decryption example in [Decrypting Data](decrypting-data.md).</span></span> <span data-ttu-id="5f094-125">Cet exemple et cet exemple spécifient la même clé et le même vecteur d’en-dessus.</span><span class="sxs-lookup"><span data-stu-id="5f094-125">That example and this example specify the same key and IV.</span></span>

<span data-ttu-id="5f094-126">Toutefois, si une exception est levée, le code affiche le texte suivant dans la console :</span><span class="sxs-lookup"><span data-stu-id="5f094-126">However, if an exception is raised, the code displays the following text to the console:</span></span>  
  
```console  
The encryption failed.  
```

## <a name="asymmetric-encryption"></a><span data-ttu-id="5f094-127">Chiffrement asymétrique</span><span class="sxs-lookup"><span data-stu-id="5f094-127">Asymmetric Encryption</span></span>

<span data-ttu-id="5f094-128">Les algorithmes asymétriques sont généralement utilisés pour chiffrer de petites quantités de données telles qu'une clé symétrique et un vecteur d'initialisation.</span><span class="sxs-lookup"><span data-stu-id="5f094-128">Asymmetric algorithms are usually used to encrypt small amounts of data such as the encryption of a symmetric key and IV.</span></span> <span data-ttu-id="5f094-129">En règle générale, un utilisateur effectuant un chiffrement asymétrique utilise la clé publique générée par une autre partie.</span><span class="sxs-lookup"><span data-stu-id="5f094-129">Typically, an individual performing asymmetric encryption uses the public key generated by another party.</span></span> <span data-ttu-id="5f094-130">La <xref:System.Security.Cryptography.RSA> classe est fournie par .net à cet effet.</span><span class="sxs-lookup"><span data-stu-id="5f094-130">The <xref:System.Security.Cryptography.RSA> class is provided by .NET for this purpose.</span></span>  
  
<span data-ttu-id="5f094-131">L'exemple suivant utilise les informations de clé publique pour chiffrer une clé symétrique et un vecteur d'initialisation.</span><span class="sxs-lookup"><span data-stu-id="5f094-131">The following example uses public key information to encrypt a symmetric key and IV.</span></span> <span data-ttu-id="5f094-132">Deux tableaux d'octets qui représentent la clé publique d'un tiers sont initialisés.</span><span class="sxs-lookup"><span data-stu-id="5f094-132">Two byte arrays are initialized that represent the public key of a third party.</span></span> <span data-ttu-id="5f094-133">Un objet <xref:System.Security.Cryptography.RSAParameters> est initialisé vers ces valeurs.</span><span class="sxs-lookup"><span data-stu-id="5f094-133">An <xref:System.Security.Cryptography.RSAParameters> object is initialized to these values.</span></span> <span data-ttu-id="5f094-134">Ensuite, l’objet **RSAParameters** (avec la clé publique qu’il représente) est importé dans une instance **RSA** à l’aide de la <xref:System.Security.Cryptography.RSA.ImportParameters%2A?displayProperty=nameWithType> méthode.</span><span class="sxs-lookup"><span data-stu-id="5f094-134">Next, the **RSAParameters** object (along with the public key it represents) is imported into an **RSA** instance using the <xref:System.Security.Cryptography.RSA.ImportParameters%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="5f094-135">Enfin, la clé privée et le vecteur d’aide créés par une <xref:System.Security.Cryptography.Aes> classe sont chiffrés.</span><span class="sxs-lookup"><span data-stu-id="5f094-135">Finally, the private key and IV created by an <xref:System.Security.Cryptography.Aes> class are encrypted.</span></span> <span data-ttu-id="5f094-136">Cet exemple nécessite qu'un chiffrement 128 bits soit installé sur les systèmes.</span><span class="sxs-lookup"><span data-stu-id="5f094-136">This example requires systems to have 128-bit encryption installed.</span></span>  
  
```vb  
Imports System
Imports System.Security.Cryptography

Module Module1

    Sub Main()
        'Initialize the byte arrays to the public key information.  
        Dim modulus As Byte() = {214, 46, 220, 83, 160, 73, 40, 39, 201, 155, 19, 202, 3, 11, 191, 178, 56, 74, 90, 36, 248, 103, 18, 144, 170, 163, 145, 87, 54, 61, 34, 220, 222, 207, 137, 149, 173, 14, 92, 120, 206, 222, 158, 28, 40, 24, 30, 16, 175, 108, 128, 35, 230, 118, 40, 121, 113, 125, 216, 130, 11, 24, 90, 48, 194, 240, 105, 44, 76, 34, 57, 249, 228, 125, 80, 38, 9, 136, 29, 117, 207, 139, 168, 181, 85, 137, 126, 10, 126, 242, 120, 247, 121, 8, 100, 12, 201, 171, 38, 226, 193, 180, 190, 117, 177, 87, 143, 242, 213, 11, 44, 180, 113, 93, 106, 99, 179, 68, 175, 211, 164, 116, 64, 148, 226, 254, 172, 147}

        Dim exponent As Byte() = {1, 0, 1}

        'Create values to store encrypted symmetric keys.  
        Dim encryptedSymmetricKey() As Byte
        Dim encryptedSymmetricIV() As Byte

        'Create a new instance of the default RSA implementation class.
        Dim rsa As RSA = RSA.Create()

        'Create a new instance of the RSAParameters structure.  
        Dim rsaKeyInfo As New RSAParameters()

        'Set rsaKeyInfo to the public key values.
        rsaKeyInfo.Modulus = modulus
        rsaKeyInfo.Exponent = exponent

        'Import key parameters into rsa
        rsa.ImportParameters(rsaKeyInfo)

        'Create a new instance of the default Aes implementation class.  
        Dim aes As Aes = Aes.Create()

        'Encrypt the symmetric key and IV.  
        encryptedSymmetricKey = rsa.Encrypt(aes.Key, RSAEncryptionPadding.Pkcs1)
        encryptedSymmetricIV = rsa.Encrypt(aes.IV, RSAEncryptionPadding.Pkcs1)
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
        byte[] modulus = {214,46,220,83,160,73,40,39,201,155,19,202,3,11,191,178,56,
            74,90,36,248,103,18,144,170,163,145,87,54,61,34,220,222,
            207,137,149,173,14,92,120,206,222,158,28,40,24,30,16,175,
            108,128,35,230,118,40,121,113,125,216,130,11,24,90,48,194,
            240,105,44,76,34,57,249,228,125,80,38,9,136,29,117,207,139,
            168,181,85,137,126,10,126,242,120,247,121,8,100,12,201,171,
            38,226,193,180,190,117,177,87,143,242,213,11,44,180,113,93,
            106,99,179,68,175,211,164,116,64,148,226,254,172,147};

        byte[] exponent = { 1, 0, 1 };

        //Create values to store encrypted symmetric keys.  
        byte[] encryptedSymmetricKey;
        byte[] encryptedSymmetricIV;

        //Create a new instance of the RSA class.  
        RSA rsa = RSA.Create();

        //Create a new instance of the RSAParameters structure.  
        RSAParameters rsaKeyInfo = new RSAParameters();

        //Set rsaKeyInfo to the public key values.
        rsaKeyInfo.Modulus = modulus;
        rsaKeyInfo.Exponent = exponent;

        //Import key parameters into rsa.  
        rsa.ImportParameters(rsaKeyInfo);

        //Create a new instance of the default Aes implementation class.  
        Aes aes = Aes.Create();

        //Encrypt the symmetric key and IV.  
        encryptedSymmetricKey = rsa.Encrypt(aes.Key, RSAEncryptionPadding.Pkcs1);
        encryptedSymmetricIV = rsa.Encrypt(aes.IV, RSAEncryptionPadding.Pkcs1);
    }
}
```  
  
## <a name="see-also"></a><span data-ttu-id="5f094-137">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5f094-137">See also</span></span>

- [<span data-ttu-id="5f094-138">Génération de clés pour le chiffrement et le déchiffrement</span><span class="sxs-lookup"><span data-stu-id="5f094-138">Generating Keys for Encryption and Decryption</span></span>](generating-keys-for-encryption-and-decryption.md)
- [<span data-ttu-id="5f094-139">Déchiffrement de données</span><span class="sxs-lookup"><span data-stu-id="5f094-139">Decrypting Data</span></span>](decrypting-data.md)
- [<span data-ttu-id="5f094-140">services de chiffrement</span><span class="sxs-lookup"><span data-stu-id="5f094-140">Cryptographic Services</span></span>](cryptographic-services.md)
- [<span data-ttu-id="5f094-141">Chiffrement multiplateforme</span><span class="sxs-lookup"><span data-stu-id="5f094-141">Cross-Platform Cryptography</span></span>](cross-platform-cryptography.md)
- [<span data-ttu-id="5f094-142">Vulnérabilités de temporisation avec le déchiffrement symétrique en mode CBC à l’aide du remplissage</span><span class="sxs-lookup"><span data-stu-id="5f094-142">Timing vulnerabilities with CBC-mode symmetric decryption using padding</span></span>](vulnerabilities-cbc-mode.md)
- [<span data-ttu-id="5f094-143">Protection des données ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="5f094-143">ASP.NET Core Data Protection</span></span>](/aspnet/core/security/data-protection/introduction)
