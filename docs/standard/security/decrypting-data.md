---
title: Déchiffrement de données
description: Découvrez Comment déchiffrer des données dans .NET, à l’aide d’un algorithme symétrique ou d’un algorithme asymétrique.
ms.date: 07/16/2020
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data [.NET], decryption
- symmetric decryption
- asymmetric decryption
- decryption
ms.assetid: 9b266b6c-a9b2-4d20-afd8-b3a0d8fd48a0
ms.openlocfilehash: cf286eeca8a9372c6532c56701e4775d5e09d786
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94831102"
---
# <a name="decrypting-data"></a><span data-ttu-id="91638-103">Déchiffrement de données</span><span class="sxs-lookup"><span data-stu-id="91638-103">Decrypting Data</span></span>

<span data-ttu-id="91638-104">Le déchiffrement est l'opération inverse du chiffrement.</span><span class="sxs-lookup"><span data-stu-id="91638-104">Decryption is the reverse operation of encryption.</span></span> <span data-ttu-id="91638-105">Pour le chiffrement à clé secrète, vous devez connaître à la fois la clé et le vecteur d'initialisation qui ont été utilisés pour chiffrer les données.</span><span class="sxs-lookup"><span data-stu-id="91638-105">For secret-key encryption, you must know both the key and IV that were used to encrypt the data.</span></span> <span data-ttu-id="91638-106">Pour le chiffrement à clé publique, vous devez connaître soit la clé publique (si les données ont été chiffrées à l'aide de la clé privée), soit la clé privée (si les données ont été chiffrées à l'aide de la clé publique).</span><span class="sxs-lookup"><span data-stu-id="91638-106">For public-key encryption, you must know either the public key (if the data was encrypted using the private key) or the private key (if the data was encrypted using the public key).</span></span>

## <a name="symmetric-decryption"></a><span data-ttu-id="91638-107">Déchiffrement symétrique</span><span class="sxs-lookup"><span data-stu-id="91638-107">Symmetric Decryption</span></span>

<span data-ttu-id="91638-108">Le déchiffrement de données chiffrées à l'aide d'algorithmes symétriques est similaire au processus utilisé pour chiffrer les données à l'aide d'algorithmes symétriques.</span><span class="sxs-lookup"><span data-stu-id="91638-108">The decryption of data encrypted with symmetric algorithms is similar to the process used to encrypt data with symmetric algorithms.</span></span> <span data-ttu-id="91638-109">La <xref:System.Security.Cryptography.CryptoStream> classe est utilisée avec les classes de chiffrement symétrique fournies par .net pour déchiffrer les données lues à partir de n’importe quel objet de flux managé.</span><span class="sxs-lookup"><span data-stu-id="91638-109">The <xref:System.Security.Cryptography.CryptoStream> class is used with symmetric cryptography classes provided by .NET to decrypt data read from any managed stream object.</span></span>

<span data-ttu-id="91638-110">L’exemple suivant illustre la création d’une nouvelle instance de la classe d’implémentation par défaut pour l' <xref:System.Security.Cryptography.Aes> algorithme.</span><span class="sxs-lookup"><span data-stu-id="91638-110">The following example illustrates how to create a new instance of the default implementation class for the <xref:System.Security.Cryptography.Aes> algorithm.</span></span> <span data-ttu-id="91638-111">L’instance est utilisée pour effectuer un déchiffrement sur un <xref:System.Security.Cryptography.CryptoStream> objet.</span><span class="sxs-lookup"><span data-stu-id="91638-111">The instance is used to perform decryption on a <xref:System.Security.Cryptography.CryptoStream> object.</span></span> <span data-ttu-id="91638-112">Cet exemple crée d’abord une nouvelle instance de la <xref:System.Security.Cryptography.Aes> classe d’implémentation.</span><span class="sxs-lookup"><span data-stu-id="91638-112">This example first creates a new instance of the <xref:System.Security.Cryptography.Aes> implementation class.</span></span> <span data-ttu-id="91638-113">Il lit la valeur du vecteur d’initialisation (IV) à partir d’une variable de flux managée, `myStream` .</span><span class="sxs-lookup"><span data-stu-id="91638-113">It reads the initialization vector (IV) value from a managed stream variable, `myStream`.</span></span> <span data-ttu-id="91638-114">Ensuite, il instancie un <xref:System.Security.Cryptography.CryptoStream> objet et l’initialise à la valeur de l' `myStream` instance.</span><span class="sxs-lookup"><span data-stu-id="91638-114">Next it instantiates a <xref:System.Security.Cryptography.CryptoStream> object and initializes it to the value of the `myStream` instance.</span></span> <span data-ttu-id="91638-115">La <xref:System.Security.Cryptography.SymmetricAlgorithm.CreateDecryptor%2A?displayProperty=nameWithType> méthode de l' <xref:System.Security.Cryptography.Aes> instance reçoit la valeur IV et la même clé que celle utilisée pour le chiffrement.</span><span class="sxs-lookup"><span data-stu-id="91638-115">The <xref:System.Security.Cryptography.SymmetricAlgorithm.CreateDecryptor%2A?displayProperty=nameWithType> method from the <xref:System.Security.Cryptography.Aes> instance is passed the IV value and the same key that was used for encryption.</span></span>

```vb
Dim aes As Aes = Aes.Create()
Dim cryptStream As New CryptoStream(myStream, aes.CreateDecryptor(key, iv), CryptoStreamMode.Read)
```

```csharp
Aes aes = Aes.Create();
CryptoStream cryptStream = new CryptoStream(myStream, aes.CreateDecryptor(key, iv), CryptoStreamMode.Read);
```

<span data-ttu-id="91638-116">L'exemple suivant montre l'intégralité des processus de création de flux, de déchiffrement de flux, de lecture depuis un flux et de fermeture de flux.</span><span class="sxs-lookup"><span data-stu-id="91638-116">The following example shows the entire process of creating a stream, decrypting the stream, reading from the stream, and closing the streams.</span></span> <span data-ttu-id="91638-117">Un objet de flux de fichier qui lit un fichier nommé *TestData.txt* est créé.</span><span class="sxs-lookup"><span data-stu-id="91638-117">A file stream object is created that reads a file named *TestData.txt*.</span></span> <span data-ttu-id="91638-118">Le flux de fichier est ensuite déchiffré à l’aide de la classe **CryptoStream** et de la classe **AES** .</span><span class="sxs-lookup"><span data-stu-id="91638-118">The file stream is then decrypted using the **CryptoStream** class and the **Aes** class.</span></span> <span data-ttu-id="91638-119">Cet exemple spécifie la valeur de clé utilisée dans l’exemple de chiffrement symétrique pour le [chiffrement des données](encrypting-data.md).</span><span class="sxs-lookup"><span data-stu-id="91638-119">This example specifies key value that is used in the symmetric encryption example for [Encrypting Data](encrypting-data.md).</span></span> <span data-ttu-id="91638-120">Il ne montre pas le code nécessaire pour chiffrer et transférer ces valeurs.</span><span class="sxs-lookup"><span data-stu-id="91638-120">It does not show the code needed to encrypt and transfer these values.</span></span>

:::code language="csharp" source="snippets/decrypting-data/csharp/aes-decrypt.cs":::
:::code language="vb" source="snippets/decrypting-data/vb/aes-decrypt.vb":::

<span data-ttu-id="91638-121">L’exemple précédent utilise la même clé, et l’algorithme utilisé dans l’exemple de chiffrement symétrique pour le [chiffrement des données](encrypting-data.md).</span><span class="sxs-lookup"><span data-stu-id="91638-121">The preceding example uses the same key, and algorithm used in the symmetric encryption example for [Encrypting Data](encrypting-data.md).</span></span> <span data-ttu-id="91638-122">Il déchiffre le fichier *TestData.txt* créé par cet exemple et affiche le texte d’origine sur la console.</span><span class="sxs-lookup"><span data-stu-id="91638-122">It decrypts the *TestData.txt* file that is created by that example and displays the original text on the console.</span></span>

## <a name="asymmetric-decryption"></a><span data-ttu-id="91638-123">Déchiffrement asymétrique</span><span class="sxs-lookup"><span data-stu-id="91638-123">Asymmetric Decryption</span></span>

<span data-ttu-id="91638-124">En règle générale, une partie (partie A) génère à la fois une clé publique et une clé privée, et stocke ces clés dans la mémoire ou dans un conteneur de clé de chiffrement.</span><span class="sxs-lookup"><span data-stu-id="91638-124">Typically, a party (party A) generates both a public and private key and stores the key either in memory or in a cryptographic key container.</span></span> <span data-ttu-id="91638-125">La partie A envoie ensuite la clé publique à une autre partie (partie B).</span><span class="sxs-lookup"><span data-stu-id="91638-125">Party A then sends the public key to another party (party B).</span></span> <span data-ttu-id="91638-126">À l’aide de la clé publique, le tiers B chiffre les données et renvoie les données au tiers A. Après avoir reçu les données, la partie A les déchiffre à l’aide de la clé privée qui correspond.</span><span class="sxs-lookup"><span data-stu-id="91638-126">Using the public key, party B encrypts data and sends the data back to party A. After receiving the data, party A decrypts it using the private key that corresponds.</span></span> <span data-ttu-id="91638-127">Le déchiffrement réussira uniquement si la partie A utilise la clé privée qui correspond à la clé publique utilisée par la partie B pour chiffrer les données.</span><span class="sxs-lookup"><span data-stu-id="91638-127">Decryption will be successful only if party A uses the private key that corresponds to the public key Party B used to encrypt the data.</span></span>

<span data-ttu-id="91638-128">Pour plus d’informations sur le stockage des clés asymétriques dans un conteneur de clé de chiffrement sécurisé et sur la récupération des clés asymétriques, consultez [How to: Store Asymmetric Keys in a Key Container](how-to-store-asymmetric-keys-in-a-key-container.md).</span><span class="sxs-lookup"><span data-stu-id="91638-128">For information on how to store an asymmetric key in secure cryptographic key container and how to later retrieve the asymmetric key, see [How to: Store Asymmetric Keys in a Key Container](how-to-store-asymmetric-keys-in-a-key-container.md).</span></span>

<span data-ttu-id="91638-129">L'exemple suivant montre le déchiffrement de deux tableaux d'octets qui représentent une clé symétrique et un vecteur d'initialisation.</span><span class="sxs-lookup"><span data-stu-id="91638-129">The following example illustrates the decryption of two arrays of bytes that represent a symmetric key and IV.</span></span> <span data-ttu-id="91638-130">Pour plus d’informations sur l’extraction de la clé publique asymétrique de l’objet <xref:System.Security.Cryptography.RSA> dans un format que vous pouvez facilement envoyer à un tiers, consultez [Encrypting Data](encrypting-data.md).</span><span class="sxs-lookup"><span data-stu-id="91638-130">For information on how to extract the asymmetric public key from the <xref:System.Security.Cryptography.RSA> object in a format that you can easily send to a third party, see [Encrypting Data](encrypting-data.md).</span></span>

```vb
'Create a new instance of the RSA class.
Dim rsa As RSA = RSA.Create()

' Export the public key information and send it to a third party.
' Wait for the third party to encrypt some data and send it back.

'Decrypt the symmetric key and IV.
symmetricKey = rsa.Decrypt(encryptedSymmetricKey, RSAEncryptionPadding.Pkcs1)
symmetricIV = rsa.Decrypt(encryptedSymmetricIV, RSAEncryptionPadding.Pkcs1)
```

```csharp
//Create a new instance of the RSA class.
RSA rsa = RSA.Create();

// Export the public key information and send it to a third party.
// Wait for the third party to encrypt some data and send it back.

//Decrypt the symmetric key and IV.
symmetricKey = rsa.Decrypt(encryptedSymmetricKey, RSAEncryptionPadding.Pkcs1);
symmetricIV = rsa.Decrypt(encryptedSymmetricIV , RSAEncryptionPadding.Pkcs1);
```

## <a name="see-also"></a><span data-ttu-id="91638-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="91638-131">See also</span></span>

- [<span data-ttu-id="91638-132">Génération de clés pour le chiffrement et le déchiffrement</span><span class="sxs-lookup"><span data-stu-id="91638-132">Generating Keys for Encryption and Decryption</span></span>](generating-keys-for-encryption-and-decryption.md)
- [<span data-ttu-id="91638-133">Chiffrement de données</span><span class="sxs-lookup"><span data-stu-id="91638-133">Encrypting Data</span></span>](encrypting-data.md)
- [<span data-ttu-id="91638-134">services de chiffrement</span><span class="sxs-lookup"><span data-stu-id="91638-134">Cryptographic Services</span></span>](cryptographic-services.md)
- [<span data-ttu-id="91638-135">Modèle de chiffrement</span><span class="sxs-lookup"><span data-stu-id="91638-135">Cryptography Model</span></span>](cryptography-model.md)
- [<span data-ttu-id="91638-136">Chiffrement multiplateforme</span><span class="sxs-lookup"><span data-stu-id="91638-136">Cross-Platform Cryptography</span></span>](cross-platform-cryptography.md)
- [<span data-ttu-id="91638-137">Vulnérabilités de temporisation avec le déchiffrement symétrique en mode CBC à l’aide du remplissage</span><span class="sxs-lookup"><span data-stu-id="91638-137">Timing vulnerabilities with CBC-mode symmetric decryption using padding</span></span>](vulnerabilities-cbc-mode.md)
- [<span data-ttu-id="91638-138">Protection des données ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="91638-138">ASP.NET Core Data Protection</span></span>](/aspnet/core/security/data-protection/introduction)
