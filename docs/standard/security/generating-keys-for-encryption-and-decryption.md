---
title: Génération de clés pour le chiffrement et le déchiffrement
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- keys, encryption and decryption
- keys, asymmetric
- keys, symmetric
- encryption [.NET Framework], keys
- symmetric keys
- asymmetric keys [.NET Framework]
- cryptography [.NET Framework], keys
ms.assetid: c197dfc9-a453-4226-898d-37a16638056e
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 52ec268df38a12dfe7dac469eed9901d7c0646a1
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67769608"
---
# <a name="generating-keys-for-encryption-and-decryption"></a><span data-ttu-id="b9ab0-102">Génération de clés pour le chiffrement et le déchiffrement</span><span class="sxs-lookup"><span data-stu-id="b9ab0-102">Generating Keys for Encryption and Decryption</span></span>
<span data-ttu-id="b9ab0-103">La création et la gestion des clés constituent une part importante du processus de chiffrement.</span><span class="sxs-lookup"><span data-stu-id="b9ab0-103">Creating and managing keys is an important part of the cryptographic process.</span></span> <span data-ttu-id="b9ab0-104">Les algorithmes symétriques nécessitent la création d'une clé et d'un vecteur d'initialisation.</span><span class="sxs-lookup"><span data-stu-id="b9ab0-104">Symmetric algorithms require the creation of a key and an initialization vector (IV).</span></span> <span data-ttu-id="b9ab0-105">La clé ne doit pas être divulguée aux personnes qui ne sont pas autorisées à déchiffrer vos données.</span><span class="sxs-lookup"><span data-stu-id="b9ab0-105">The key must be kept secret from anyone who should not decrypt your data.</span></span> <span data-ttu-id="b9ab0-106">Le vecteur d'initialisation peut être divulgué, mais doit être modifié à chaque session.</span><span class="sxs-lookup"><span data-stu-id="b9ab0-106">The IV does not have to be secret, but should be changed for each session.</span></span> <span data-ttu-id="b9ab0-107">Les algorithmes asymétriques nécessitent la création d'une clé publique et d'une clé privée.</span><span class="sxs-lookup"><span data-stu-id="b9ab0-107">Asymmetric algorithms require the creation of a public key and a private key.</span></span> <span data-ttu-id="b9ab0-108">La clé publique peut être donnée à tout le monde. Toutefois, la clé privée ne doit être connue que de la partie chargée du déchiffrement des données chiffrées à l'aide de la clé publique.</span><span class="sxs-lookup"><span data-stu-id="b9ab0-108">The public key can be made public to anyone, while the private key must known only by the party who will decrypt the data encrypted with the public key.</span></span> <span data-ttu-id="b9ab0-109">Cette section décrit comment générer et gérer des clés pour les algorithmes symétriques et asymétriques.</span><span class="sxs-lookup"><span data-stu-id="b9ab0-109">This section describes how to generate and manage keys for both symmetric and asymmetric algorithms.</span></span>  
  
## <a name="symmetric-keys"></a><span data-ttu-id="b9ab0-110">Clés symétriques</span><span class="sxs-lookup"><span data-stu-id="b9ab0-110">Symmetric Keys</span></span>  
 <span data-ttu-id="b9ab0-111">Les classes de chiffrement symétrique fournies par .NET Framework nécessitent une clé et un nouveau vecteur d'initialisation pour chiffrer et déchiffrer les données.</span><span class="sxs-lookup"><span data-stu-id="b9ab0-111">The symmetric encryption classes supplied by the .NET Framework require a key and a new initialization vector (IV) to encrypt and decrypt data.</span></span> <span data-ttu-id="b9ab0-112">Chaque fois que vous créez une nouvelle instance de l’une des classes de chiffrement symétriques gérés à l’aide du constructeur sans paramètre, une nouvelle clé et un vecteur d’initialisation sont automatiquement créés.</span><span class="sxs-lookup"><span data-stu-id="b9ab0-112">Whenever you create a new instance of one of the managed symmetric cryptographic classes using the parameterless constructor, a new key and IV are automatically created.</span></span> <span data-ttu-id="b9ab0-113">Toute personne que vous autorisez à déchiffrer vos données doit posséder la même clé et le même vecteur d'initialisation, et doit utiliser le même algorithme.</span><span class="sxs-lookup"><span data-stu-id="b9ab0-113">Anyone that you allow to decrypt your data must possess the same key and IV and use the same algorithm.</span></span> <span data-ttu-id="b9ab0-114">En général, une nouvelle clé et un nouveau vecteur d'initialisation doivent être créés pour chaque session. Ni la clé, ni le vecteur d'initialisation ne doivent être stockés en vue d'être utilisés dans une session ultérieure.</span><span class="sxs-lookup"><span data-stu-id="b9ab0-114">Generally, a new key and IV should be created for every session, and neither the key nor IV should be stored for use in a later session.</span></span>  
  
 <span data-ttu-id="b9ab0-115">Pour communiquer une clé symétrique et un vecteur d'initialisation à une partie distante, vous devez, en général, chiffrer la clé symétrique à l'aide du chiffrement asymétrique.</span><span class="sxs-lookup"><span data-stu-id="b9ab0-115">To communicate a symmetric key and IV to a remote party, you would usually encrypt the symmetric key by using asymmetric encryption.</span></span> <span data-ttu-id="b9ab0-116">L'envoi d'une clé non chiffrée vers un réseau non sécurisé est risqué, car toute personne qui intercepte la clé et le vecteur d'initialisation peut ensuite déchiffrer vos données.</span><span class="sxs-lookup"><span data-stu-id="b9ab0-116">Sending the key across an insecure network without encrypting it is unsafe, because anyone who intercepts the key and IV can then decrypt your data.</span></span> <span data-ttu-id="b9ab0-117">Pour plus d'informations sur l'échange de données à l'aide du chiffrement, consultez [Création d'un modèle de chiffrement](../../../docs/standard/security/creating-a-cryptographic-scheme.md).</span><span class="sxs-lookup"><span data-stu-id="b9ab0-117">For more information about exchanging data by using encryption, see [Creating a Cryptographic Scheme](../../../docs/standard/security/creating-a-cryptographic-scheme.md).</span></span>  
  
 <span data-ttu-id="b9ab0-118">L'exemple suivant illustre la création d'une nouvelle instance de la classe <xref:System.Security.Cryptography.TripleDESCryptoServiceProvider> qui implémente l'algorithme TripleDES.</span><span class="sxs-lookup"><span data-stu-id="b9ab0-118">The following example shows the creation of a new instance of the <xref:System.Security.Cryptography.TripleDESCryptoServiceProvider> class that implements the TripleDES algorithm.</span></span>  
  
```vb  
Dim tdes As TripleDESCryptoServiceProvider = new TripleDESCryptoServiceProvider()  
```  
  
```csharp  
TripleDESCryptoServiceProvider tdes = new TripleDESCryptoServiceProvider();  
```  
  
 <span data-ttu-id="b9ab0-119">Quand le code précédent est exécuté, une nouvelle clé et un nouveau vecteur d'initialisation sont générés, puis placés dans les propriétés **Key** et **IV** , respectivement.</span><span class="sxs-lookup"><span data-stu-id="b9ab0-119">When the previous code is executed, a new key and IV are generated and placed in the **Key** and **IV** properties, respectively.</span></span>  
  
 <span data-ttu-id="b9ab0-120">Vous devrez parfois générer plusieurs clés.</span><span class="sxs-lookup"><span data-stu-id="b9ab0-120">Sometimes you might need to generate multiple keys.</span></span> <span data-ttu-id="b9ab0-121">Dans ce cas, vous pouvez créer une instance d'une classe qui implémente un algorithme symétrique et ensuite créer une nouvelle clé et un nouveau vecteur d'initialisation en appelant les méthodes **GenerateKey** et **GenerateIV** .</span><span class="sxs-lookup"><span data-stu-id="b9ab0-121">In this situation, you can create a new instance of a class that implements a symmetric algorithm and then create a new key and IV by calling the **GenerateKey** and **GenerateIV** methods.</span></span> <span data-ttu-id="b9ab0-122">L’exemple de code suivant illustre comment créer de nouvelles clés et IV après la réalisation d’une nouvelle instance de la classe de chiffrement symétrique.</span><span class="sxs-lookup"><span data-stu-id="b9ab0-122">The following code example illustrates how to create new keys and IVs after a new instance of the symmetric cryptographic class has been made.</span></span>  
  
```vb  
Dim tdes As TripleDESCryptoServiceProvider = new TripleDESCryptoServiceProvider()  
tdes.GenerateIV()  
tdes.GenerateKey()  
```  
  
```csharp  
TripleDESCryptoServiceProvider tdes = new TripleDESCryptoServiceProvider();  
tdes.GenerateIV();  
tdes.GenerateKey();  
```  
  
 <span data-ttu-id="b9ab0-123">Quand le code précédent est exécuté, une clé et un vecteur d'initialisation sont générés quand la nouvelle instance de **TripleDESCryptoServiceProvider** est créée.</span><span class="sxs-lookup"><span data-stu-id="b9ab0-123">When the previous code is executed, a key and IV are generated when the new instance of **TripleDESCryptoServiceProvider** is made.</span></span> <span data-ttu-id="b9ab0-124">Une autre clé et un autre vecteur d'initialisation sont créés quand les méthodes **GenerateKey** et **GenerateIV** sont appelées.</span><span class="sxs-lookup"><span data-stu-id="b9ab0-124">Another key and IV are created when the **GenerateKey** and **GenerateIV** methods are called.</span></span>  
  
## <a name="asymmetric-keys"></a><span data-ttu-id="b9ab0-125">Clés asymétriques</span><span class="sxs-lookup"><span data-stu-id="b9ab0-125">Asymmetric Keys</span></span>  
 <span data-ttu-id="b9ab0-126">.NET Framework fournit les classes <xref:System.Security.Cryptography.RSACryptoServiceProvider> et <xref:System.Security.Cryptography.DSACryptoServiceProvider> pour le chiffrement asymétrique.</span><span class="sxs-lookup"><span data-stu-id="b9ab0-126">The .NET Framework provides the <xref:System.Security.Cryptography.RSACryptoServiceProvider> and <xref:System.Security.Cryptography.DSACryptoServiceProvider> classes for asymmetric encryption.</span></span> <span data-ttu-id="b9ab0-127">Ces classes créent une paire de clés publique/privée lorsque vous utilisez le constructeur sans paramètre pour créer une nouvelle instance.</span><span class="sxs-lookup"><span data-stu-id="b9ab0-127">These classes create a public/private key pair when you use the parameterless constructor to create a new instance.</span></span> <span data-ttu-id="b9ab0-128">Les clés asymétriques peuvent être stockées en vue d'être utilisées pour plusieurs sessions, ou bien être générées pour une session unique.</span><span class="sxs-lookup"><span data-stu-id="b9ab0-128">Asymmetric keys can be either stored for use in multiple sessions or generated for one session only.</span></span> <span data-ttu-id="b9ab0-129">La clé publique peut être connue de tous, contrairement à la clé privée qui ne doit être divulguée qu'à certaines personnes.</span><span class="sxs-lookup"><span data-stu-id="b9ab0-129">While the public key can be made generally available, the private key should be closely guarded.</span></span>  
  
 <span data-ttu-id="b9ab0-130">Une paire de clés publique/privée est générée chaque fois qu'une nouvelle instance d'une classe d'algorithme asymétrique est créée.</span><span class="sxs-lookup"><span data-stu-id="b9ab0-130">A public/private key pair is generated whenever a new instance of an asymmetric algorithm class is created.</span></span> <span data-ttu-id="b9ab0-131">Après la création d'une nouvelle instance de la classe, les informations de clé peuvent être extraites à l'aide de deux méthodes :</span><span class="sxs-lookup"><span data-stu-id="b9ab0-131">After a new instance of the class is created, the key information can be extracted using one of two methods:</span></span>  
  
- <span data-ttu-id="b9ab0-132">La méthode <xref:System.Security.Cryptography.RSA.ToXmlString%2A> , qui retourne une représentation XML des informations de clé.</span><span class="sxs-lookup"><span data-stu-id="b9ab0-132">The <xref:System.Security.Cryptography.RSA.ToXmlString%2A> method, which returns an XML representation of the key information.</span></span>  
  
- <span data-ttu-id="b9ab0-133">La méthode <xref:System.Security.Cryptography.RSACryptoServiceProvider.ExportParameters%2A> qui retourne une structure <xref:System.Security.Cryptography.RSAParameters> qui contient les informations de clé.</span><span class="sxs-lookup"><span data-stu-id="b9ab0-133">The <xref:System.Security.Cryptography.RSACryptoServiceProvider.ExportParameters%2A> method, which returns an <xref:System.Security.Cryptography.RSAParameters> structure that holds the key information.</span></span>  
  
 <span data-ttu-id="b9ab0-134">Les deux méthodes acceptent une valeur booléenne qui indique s'il faut retourner uniquement les informations concernant la clé publique ou retourner les informations concernant la clé publique et la clé privée.</span><span class="sxs-lookup"><span data-stu-id="b9ab0-134">Both methods accept a Boolean value that indicates whether to return only the public key information or to return both the public-key and the private-key information.</span></span> <span data-ttu-id="b9ab0-135">Une classe **RSACryptoServiceProvider** peut être initialisée à la valeur d'une structure **RSAParameters** à l'aide de la méthode <xref:System.Security.Cryptography.RSACryptoServiceProvider.ImportParameters%2A> .</span><span class="sxs-lookup"><span data-stu-id="b9ab0-135">An **RSACryptoServiceProvider** class can be initialized to the value of an **RSAParameters** structure by using the <xref:System.Security.Cryptography.RSACryptoServiceProvider.ImportParameters%2A> method.</span></span>  
  
 <span data-ttu-id="b9ab0-136">Les clés privées asymétriques ne doivent jamais être stockées textuellement ou en texte brut sur l'ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="b9ab0-136">Asymmetric private keys should never be stored verbatim or in plain text on the local computer.</span></span> <span data-ttu-id="b9ab0-137">Si vous avez besoin de stocker une clé privée, vous devez utiliser un conteneur de clé.</span><span class="sxs-lookup"><span data-stu-id="b9ab0-137">If you need to store a private key, you should use a key container.</span></span> <span data-ttu-id="b9ab0-138">Pour plus d’informations sur la façon de stocker une clé privée dans un conteneur de clé, consultez [Comment : Store les clés asymétriques dans un conteneur de clé](../../../docs/standard/security/how-to-store-asymmetric-keys-in-a-key-container.md).</span><span class="sxs-lookup"><span data-stu-id="b9ab0-138">For more on how to store a private key in a key container, see [How to: Store Asymmetric Keys in a Key Container](../../../docs/standard/security/how-to-store-asymmetric-keys-in-a-key-container.md).</span></span>  
  
 <span data-ttu-id="b9ab0-139">L'exemple de code suivant crée une nouvelle instance de la classe **RSACryptoServiceProvider** , en créant une paire de clés publique/privée et en enregistrant les informations de clé publique dans une structure **RSAParameters** .</span><span class="sxs-lookup"><span data-stu-id="b9ab0-139">The following code example creates a new instance of the **RSACryptoServiceProvider** class, creating a public/private key pair, and saves the public key information to an **RSAParameters** structure.</span></span>  
  
```vb  
'Generate a public/private key pair.  
Dim rsa as RSACryptoServiceProvider = new RSACryptoServiceProvider()  
'Save the public key information to an RSAParameters structure.  
Dim rsaKeyInfo As RSAParameters = rsa.ExportParameters(false)  
```  
  
```csharp  
//Generate a public/private key pair.  
RSACryptoServiceProvider rsa = new RSACryptoServiceProvider();  
//Save the public key information to an RSAParameters structure.  
RSAParameters rsaKeyInfo = rsa.ExportParameters(false);  
```  
  
## <a name="see-also"></a><span data-ttu-id="b9ab0-140">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b9ab0-140">See also</span></span>

- [<span data-ttu-id="b9ab0-141">Chiffrement de données</span><span class="sxs-lookup"><span data-stu-id="b9ab0-141">Encrypting Data</span></span>](../../../docs/standard/security/encrypting-data.md)
- [<span data-ttu-id="b9ab0-142">Déchiffrement de données</span><span class="sxs-lookup"><span data-stu-id="b9ab0-142">Decrypting Data</span></span>](../../../docs/standard/security/decrypting-data.md)
- [<span data-ttu-id="b9ab0-143">Cryptographic Services</span><span class="sxs-lookup"><span data-stu-id="b9ab0-143">Cryptographic Services</span></span>](../../../docs/standard/security/cryptographic-services.md)
- [<span data-ttu-id="b9ab0-144">Guide pratique pour Store les clés asymétriques dans un conteneur de clé</span><span class="sxs-lookup"><span data-stu-id="b9ab0-144">How to: Store Asymmetric Keys in a Key Container</span></span>](../../../docs/standard/security/how-to-store-asymmetric-keys-in-a-key-container.md)
