---
title: Génération de clés pour le chiffrement et le déchiffrement
description: Découvrez comment créer et gérer des clés symétriques et asymétriques pour le chiffrement et le déchiffrement dans .NET.
ms.date: 07/14/2020
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- keys, encryption and decryption
- keys, asymmetric
- keys, symmetric
- encryption [.NET], keys
- symmetric keys
- asymmetric keys [.NET]
- cryptography [.NET], keys
ms.assetid: c197dfc9-a453-4226-898d-37a16638056e
ms.openlocfilehash: 7ce19dc465fb1fac22545398e0724e6b76dd7098
ms.sourcegitcommit: b7a8b09828bab4e90f66af8d495ecd7024c45042
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87556941"
---
# <a name="generating-keys-for-encryption-and-decryption"></a><span data-ttu-id="2b473-103">Génération de clés pour le chiffrement et le déchiffrement</span><span class="sxs-lookup"><span data-stu-id="2b473-103">Generating Keys for Encryption and Decryption</span></span>
<span data-ttu-id="2b473-104">La création et la gestion des clés constituent une part importante du processus de chiffrement.</span><span class="sxs-lookup"><span data-stu-id="2b473-104">Creating and managing keys is an important part of the cryptographic process.</span></span> <span data-ttu-id="2b473-105">Les algorithmes symétriques nécessitent la création d'une clé et d'un vecteur d'initialisation.</span><span class="sxs-lookup"><span data-stu-id="2b473-105">Symmetric algorithms require the creation of a key and an initialization vector (IV).</span></span> <span data-ttu-id="2b473-106">La clé ne doit pas être divulguée aux personnes qui ne sont pas autorisées à déchiffrer vos données.</span><span class="sxs-lookup"><span data-stu-id="2b473-106">The key must be kept secret from anyone who should not decrypt your data.</span></span> <span data-ttu-id="2b473-107">Le vecteur d'initialisation peut être divulgué, mais doit être modifié à chaque session.</span><span class="sxs-lookup"><span data-stu-id="2b473-107">The IV does not have to be secret, but should be changed for each session.</span></span> <span data-ttu-id="2b473-108">Les algorithmes asymétriques nécessitent la création d'une clé publique et d'une clé privée.</span><span class="sxs-lookup"><span data-stu-id="2b473-108">Asymmetric algorithms require the creation of a public key and a private key.</span></span> <span data-ttu-id="2b473-109">La clé publique peut être donnée à tout le monde. Toutefois, la clé privée ne doit être connue que de la partie chargée du déchiffrement des données chiffrées à l'aide de la clé publique.</span><span class="sxs-lookup"><span data-stu-id="2b473-109">The public key can be made public to anyone, while the private key must known only by the party who will decrypt the data encrypted with the public key.</span></span> <span data-ttu-id="2b473-110">Cette section décrit comment générer et gérer des clés pour les algorithmes symétriques et asymétriques.</span><span class="sxs-lookup"><span data-stu-id="2b473-110">This section describes how to generate and manage keys for both symmetric and asymmetric algorithms.</span></span>  
  
## <a name="symmetric-keys"></a><span data-ttu-id="2b473-111">Clés symétriques</span><span class="sxs-lookup"><span data-stu-id="2b473-111">Symmetric Keys</span></span>  
 <span data-ttu-id="2b473-112">Les classes de chiffrement symétrique fournies par .NET requièrent une clé et un nouveau vecteur d’initialisation (IV) pour chiffrer et déchiffrer les données.</span><span class="sxs-lookup"><span data-stu-id="2b473-112">The symmetric encryption classes supplied by .NET require a key and a new initialization vector (IV) to encrypt and decrypt data.</span></span> <span data-ttu-id="2b473-113">Chaque fois que vous créez une nouvelle instance de l’une des classes de chiffrement symétrique managées à l’aide de la méthode sans paramètre `Create()` , une nouvelle clé et un nouveau vecteur d’exécution sont créés automatiquement.</span><span class="sxs-lookup"><span data-stu-id="2b473-113">Whenever you create a new instance of one of the managed symmetric cryptographic classes using the parameterless `Create()` method, a new key and IV are automatically created.</span></span> <span data-ttu-id="2b473-114">Toute personne que vous autorisez à déchiffrer vos données doit posséder la même clé et le même vecteur d'initialisation, et doit utiliser le même algorithme.</span><span class="sxs-lookup"><span data-stu-id="2b473-114">Anyone that you allow to decrypt your data must possess the same key and IV and use the same algorithm.</span></span> <span data-ttu-id="2b473-115">En général, une nouvelle clé et un nouveau vecteur d'initialisation doivent être créés pour chaque session. Ni la clé, ni le vecteur d'initialisation ne doivent être stockés en vue d'être utilisés dans une session ultérieure.</span><span class="sxs-lookup"><span data-stu-id="2b473-115">Generally, a new key and IV should be created for every session, and neither the key nor IV should be stored for use in a later session.</span></span>  
  
 <span data-ttu-id="2b473-116">Pour communiquer une clé symétrique et un vecteur d'initialisation à une partie distante, vous devez, en général, chiffrer la clé symétrique à l'aide du chiffrement asymétrique.</span><span class="sxs-lookup"><span data-stu-id="2b473-116">To communicate a symmetric key and IV to a remote party, you would usually encrypt the symmetric key by using asymmetric encryption.</span></span> <span data-ttu-id="2b473-117">L'envoi d'une clé non chiffrée vers un réseau non sécurisé est risqué, car toute personne qui intercepte la clé et le vecteur d'initialisation peut ensuite déchiffrer vos données.</span><span class="sxs-lookup"><span data-stu-id="2b473-117">Sending the key across an insecure network without encrypting it is unsafe, because anyone who intercepts the key and IV can then decrypt your data.</span></span>  
  
 <span data-ttu-id="2b473-118">L’exemple suivant illustre la création d’une nouvelle instance de la classe d’implémentation par défaut pour l' <xref:System.Security.Cryptography.Aes> algorithme.</span><span class="sxs-lookup"><span data-stu-id="2b473-118">The following example shows the creation of a new instance of the default implementation class for the <xref:System.Security.Cryptography.Aes> algorithm.</span></span>  
  
```vb  
Dim aes As Aes = Aes.Create()  
```  
  
```csharp  
Aes aes = Aes.Create();  
```  
  
 <span data-ttu-id="2b473-119">Quand le code précédent est exécuté, une nouvelle clé et un nouveau vecteur d'initialisation sont générés, puis placés dans les propriétés **Key** et **IV** , respectivement.</span><span class="sxs-lookup"><span data-stu-id="2b473-119">When the previous code is executed, a new key and IV are generated and placed in the **Key** and **IV** properties, respectively.</span></span>  
  
 <span data-ttu-id="2b473-120">Vous devrez parfois générer plusieurs clés.</span><span class="sxs-lookup"><span data-stu-id="2b473-120">Sometimes you might need to generate multiple keys.</span></span> <span data-ttu-id="2b473-121">Dans ce cas, vous pouvez créer une instance d'une classe qui implémente un algorithme symétrique et ensuite créer une nouvelle clé et un nouveau vecteur d'initialisation en appelant les méthodes **GenerateKey** et **GenerateIV** .</span><span class="sxs-lookup"><span data-stu-id="2b473-121">In this situation, you can create a new instance of a class that implements a symmetric algorithm and then create a new key and IV by calling the **GenerateKey** and **GenerateIV** methods.</span></span> <span data-ttu-id="2b473-122">L’exemple de code suivant montre comment créer de nouvelles clés et IV après avoir effectué une nouvelle instance de la classe de chiffrement symétrique.</span><span class="sxs-lookup"><span data-stu-id="2b473-122">The following code example illustrates how to create new keys and IVs after a new instance of the symmetric cryptographic class has been made.</span></span>  
  
```vb  
Dim aes As Aes = Aes.Create()  
aes.GenerateIV()  
aes.GenerateKey()  
```  
  
```csharp  
Aes aes = Aes.Create();  
aes.GenerateIV();  
aes.GenerateKey();  
```  
  
 <span data-ttu-id="2b473-123">Lorsque le code précédent est exécuté, une clé et un vecteur d’exécution sont générés lorsque la nouvelle instance d' **AES** est créée.</span><span class="sxs-lookup"><span data-stu-id="2b473-123">When the preceding code is executed, a key and IV are generated when the new instance of **Aes** is made.</span></span> <span data-ttu-id="2b473-124">Une autre clé et un autre vecteur d'initialisation sont créés quand les méthodes **GenerateKey** et **GenerateIV** sont appelées.</span><span class="sxs-lookup"><span data-stu-id="2b473-124">Another key and IV are created when the **GenerateKey** and **GenerateIV** methods are called.</span></span>
  
## <a name="asymmetric-keys"></a><span data-ttu-id="2b473-125">Clés asymétriques</span><span class="sxs-lookup"><span data-stu-id="2b473-125">Asymmetric Keys</span></span>

 <span data-ttu-id="2b473-126">.NET fournit la <xref:System.Security.Cryptography.RSA> classe pour le chiffrement asymétrique.</span><span class="sxs-lookup"><span data-stu-id="2b473-126">.NET provides the <xref:System.Security.Cryptography.RSA> class for asymmetric encryption.</span></span> <span data-ttu-id="2b473-127">Cette classe crée une paire de clés publique/privée quand vous utilisez la méthode sans paramètre `Create()` pour créer une nouvelle instance.</span><span class="sxs-lookup"><span data-stu-id="2b473-127">This class creates a public/private key pair when you use the parameterless `Create()` method to create a new instance.</span></span> <span data-ttu-id="2b473-128">Les clés asymétriques peuvent être stockées en vue d'être utilisées pour plusieurs sessions, ou bien être générées pour une session unique.</span><span class="sxs-lookup"><span data-stu-id="2b473-128">Asymmetric keys can be either stored for use in multiple sessions or generated for one session only.</span></span> <span data-ttu-id="2b473-129">La clé publique peut être connue de tous, contrairement à la clé privée qui ne doit être divulguée qu'à certaines personnes.</span><span class="sxs-lookup"><span data-stu-id="2b473-129">While the public key can be made generally available, the private key should be closely guarded.</span></span>  
  
 <span data-ttu-id="2b473-130">Une paire de clés publique/privée est générée chaque fois qu'une nouvelle instance d'une classe d'algorithme asymétrique est créée.</span><span class="sxs-lookup"><span data-stu-id="2b473-130">A public/private key pair is generated whenever a new instance of an asymmetric algorithm class is created.</span></span> <span data-ttu-id="2b473-131">Après la création d’une nouvelle instance de la classe, les informations de clé peuvent être extraites à l’aide de la <xref:System.Security.Cryptography.RSA.ExportParameters%2A> méthode, qui retourne une <xref:System.Security.Cryptography.RSAParameters> structure qui contient les informations de clé.</span><span class="sxs-lookup"><span data-stu-id="2b473-131">After a new instance of the class is created, the key information can be extracted using the <xref:System.Security.Cryptography.RSA.ExportParameters%2A> method, which returns an <xref:System.Security.Cryptography.RSAParameters> structure that holds the key information.</span></span> <span data-ttu-id="2b473-132">La méthode accepte une valeur booléenne qui indique s’il faut retourner uniquement les informations sur la clé publique ou retourner les informations de clé publique et de clé privée.</span><span class="sxs-lookup"><span data-stu-id="2b473-132">The method accepts a Boolean value that indicates whether to return only the public key information or to return both the public-key and the private-key information.</span></span>

<span data-ttu-id="2b473-133">Il existe également d’autres méthodes qui vous permettent d’extraire des informations clés, telles que :</span><span class="sxs-lookup"><span data-stu-id="2b473-133">There are also other methods that let you extract key information, such as:</span></span>

* <xref:System.Security.Cryptography.RSA.ExportRSAPublicKey%2A?displayProperty=nameWithType>
* <xref:System.Security.Cryptography.RSA.ExportRSAPrivateKey%2A?displayProperty=nameWithType>
* <xref:System.Security.Cryptography.AsymmetricAlgorithm.ExportSubjectPublicKeyInfo%2A?displayProperty=nameWithType>
* <xref:System.Security.Cryptography.AsymmetricAlgorithm.ExportPkcs8PrivateKey%2A?displayProperty=nameWithType>
* <xref:System.Security.Cryptography.AsymmetricAlgorithm.ExportEncryptedPkcs8PrivateKey%2A?displayProperty=nameWithType>

<span data-ttu-id="2b473-134">Une instance **RSA** peut être initialisée à la valeur d’une structure **RSAParameters** à l’aide de la <xref:System.Security.Cryptography.RSA.ImportParameters%2A> méthode.</span><span class="sxs-lookup"><span data-stu-id="2b473-134">An **RSA** instance can be initialized to the value of an **RSAParameters** structure by using the <xref:System.Security.Cryptography.RSA.ImportParameters%2A> method.</span></span> <span data-ttu-id="2b473-135">Ou créez une nouvelle instance de à l’aide de la <xref:System.Security.Cryptography.RSA.Create(System.Security.Cryptography.RSAParameters)?displayProperty=nameWithType> méthode.</span><span class="sxs-lookup"><span data-stu-id="2b473-135">Or create a new instance by using the <xref:System.Security.Cryptography.RSA.Create(System.Security.Cryptography.RSAParameters)?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="2b473-136">Les clés privées asymétriques ne doivent jamais être stockées textuellement ou en texte brut sur l'ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="2b473-136">Asymmetric private keys should never be stored verbatim or in plain text on the local computer.</span></span> <span data-ttu-id="2b473-137">Si vous avez besoin de stocker une clé privée, vous devez utiliser un conteneur de clé.</span><span class="sxs-lookup"><span data-stu-id="2b473-137">If you need to store a private key, you should use a key container.</span></span> <span data-ttu-id="2b473-138">Pour plus d’informations sur la façon de stocker une clé privée dans un conteneur de clé, consultez [Comment : stocker des clés asymétriques dans un conteneur de clé](how-to-store-asymmetric-keys-in-a-key-container.md).</span><span class="sxs-lookup"><span data-stu-id="2b473-138">For more information about how to store a private key in a key container, see [How to: Store Asymmetric Keys in a Key Container](how-to-store-asymmetric-keys-in-a-key-container.md).</span></span>  
  
 <span data-ttu-id="2b473-139">L’exemple de code suivant crée une nouvelle instance de la classe **RSA** , en créant une paire de clés publique/privée, puis enregistre les informations de clé publique dans une structure **RSAParameters** .</span><span class="sxs-lookup"><span data-stu-id="2b473-139">The following code example creates a new instance of the **RSA** class, creating a public/private key pair, and saves the public key information to an **RSAParameters** structure.</span></span>  
  
```vb  
'Generate a public/private key pair.  
Dim rsa as RSA = RSA.Create()  
'Save the public key information to an RSAParameters structure.  
Dim rsaKeyInfo As RSAParameters = rsa.ExportParameters(false)  
```  
  
```csharp  
//Generate a public/private key pair.  
RSA rsa = RSA.Create();  
//Save the public key information to an RSAParameters structure.  
RSAParameters rsaKeyInfo = rsa.ExportParameters(false);  
```  
  
## <a name="see-also"></a><span data-ttu-id="2b473-140">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2b473-140">See also</span></span>

- [<span data-ttu-id="2b473-141">Chiffrement de données</span><span class="sxs-lookup"><span data-stu-id="2b473-141">Encrypting Data</span></span>](encrypting-data.md)
- [<span data-ttu-id="2b473-142">Déchiffrement de données</span><span class="sxs-lookup"><span data-stu-id="2b473-142">Decrypting Data</span></span>](decrypting-data.md)
- [<span data-ttu-id="2b473-143">services de chiffrement</span><span class="sxs-lookup"><span data-stu-id="2b473-143">Cryptographic Services</span></span>](cryptographic-services.md)
- [<span data-ttu-id="2b473-144">Procédure : stocker des clés asymétriques dans un conteneur de clé</span><span class="sxs-lookup"><span data-stu-id="2b473-144">How to: Store Asymmetric Keys in a Key Container</span></span>](how-to-store-asymmetric-keys-in-a-key-container.md)
- [<span data-ttu-id="2b473-145">Chiffrement multiplateforme</span><span class="sxs-lookup"><span data-stu-id="2b473-145">Cross-Platform Cryptography</span></span>](cross-platform-cryptography.md)
- [<span data-ttu-id="2b473-146">Protection des données ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="2b473-146">ASP.NET Core Data Protection</span></span>](/aspnet/core/security/data-protection/introduction)
