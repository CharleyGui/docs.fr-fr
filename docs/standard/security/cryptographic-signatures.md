---
title: Signatures de chiffrement
ms.date: 07/14/2020
dev_langs:
- csharp
- vb
helpviewer_keywords:
- digital signatures
- cryptography [.NET], signatures
- digital signatures, XML signing
- signatures, cryptographic
- digital signatures, generating
- verifying signatures
- generating signatures
- digital signatures, about
- encryption [.NET], signatures
- security [.NET], signatures
- XML signing
- digital signatures, verifying
- signing XML
ms.assetid: aa87cb7f-e608-4a81-948b-c9b8a1225783
ms.openlocfilehash: 453e9d887012826da3f64d199e15a05fd0661191
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94831128"
---
# <a name="cryptographic-signatures"></a><span data-ttu-id="5221a-102">Signatures de chiffrement</span><span class="sxs-lookup"><span data-stu-id="5221a-102">Cryptographic Signatures</span></span>

<span data-ttu-id="5221a-103">Les signatures numériques de chiffrement utilisent des algorithmes de clé publique pour assurer l'intégrité des données.</span><span class="sxs-lookup"><span data-stu-id="5221a-103">Cryptographic digital signatures use public key algorithms to provide data integrity.</span></span> <span data-ttu-id="5221a-104">Quand vous signez des données avec une signature numérique, un tiers peut vérifier la signature et prouver que les données viennent bien de vous et qu'elles n'ont pas été modifiées après que vous les avez signées.</span><span class="sxs-lookup"><span data-stu-id="5221a-104">When you sign data with a digital signature, someone else can verify the signature, and can prove that the data originated from you and was not altered after you signed it.</span></span> <span data-ttu-id="5221a-105">Pour plus d’informations sur les signatures numériques, consultez [Cryptographic Services](cryptographic-services.md).</span><span class="sxs-lookup"><span data-stu-id="5221a-105">For more information about digital signatures, see [Cryptographic Services](cryptographic-services.md).</span></span>

<span data-ttu-id="5221a-106">Cette rubrique explique comment générer et vérifier des signatures numériques en utilisant les classes de l'espace de noms <xref:System.Security.Cryptography> .</span><span class="sxs-lookup"><span data-stu-id="5221a-106">This topic explains how to generate and verify digital signatures using classes in the <xref:System.Security.Cryptography> namespace.</span></span>

## <a name="generating-signatures"></a><span data-ttu-id="5221a-107">Génération de signatures</span><span class="sxs-lookup"><span data-stu-id="5221a-107">Generating Signatures</span></span>

<span data-ttu-id="5221a-108">Les signatures numériques sont généralement appliquées à des valeurs de hachage qui représentent des données plus volumineuses.</span><span class="sxs-lookup"><span data-stu-id="5221a-108">Digital signatures are usually applied to hash values that represent larger data.</span></span> <span data-ttu-id="5221a-109">Dans l'exemple suivant, une signature numérique est appliquée à une valeur de hachage.</span><span class="sxs-lookup"><span data-stu-id="5221a-109">The following example applies a digital signature to a hash value.</span></span> <span data-ttu-id="5221a-110">Dans un premier temps, une nouvelle instance de la classe <xref:System.Security.Cryptography.RSA> est créée pour générer une paire de clés publique/privée.</span><span class="sxs-lookup"><span data-stu-id="5221a-110">First, a new instance of the <xref:System.Security.Cryptography.RSA> class is created to generate a public/private key pair.</span></span> <span data-ttu-id="5221a-111">Ensuite, <xref:System.Security.Cryptography.RSA> est passé à une nouvelle instance de la classe <xref:System.Security.Cryptography.RSAPKCS1SignatureFormatter> .</span><span class="sxs-lookup"><span data-stu-id="5221a-111">Next, the <xref:System.Security.Cryptography.RSA> is passed to a new instance of the <xref:System.Security.Cryptography.RSAPKCS1SignatureFormatter> class.</span></span> <span data-ttu-id="5221a-112">Cela a pour effet de transférer la clé privée à <xref:System.Security.Cryptography.RSAPKCS1SignatureFormatter>, qui effectue la signature numérique proprement dite.</span><span class="sxs-lookup"><span data-stu-id="5221a-112">This transfers the private key to the <xref:System.Security.Cryptography.RSAPKCS1SignatureFormatter>, which actually performs the digital signing.</span></span> <span data-ttu-id="5221a-113">Pour pouvoir signer le code de hachage, vous devez au préalable spécifier l'algorithme de hachage à utiliser.</span><span class="sxs-lookup"><span data-stu-id="5221a-113">Before you can sign the hash code, you must specify a hash algorithm to use.</span></span> <span data-ttu-id="5221a-114">Dans cet exemple, c'est l'algorithme SHA1 qui est utilisé.</span><span class="sxs-lookup"><span data-stu-id="5221a-114">This example uses the SHA1 algorithm.</span></span> <span data-ttu-id="5221a-115">Enfin, la méthode <xref:System.Security.Cryptography.AsymmetricSignatureFormatter.CreateSignature%2A> est appelée pour effectuer la signature.</span><span class="sxs-lookup"><span data-stu-id="5221a-115">Finally, the <xref:System.Security.Cryptography.AsymmetricSignatureFormatter.CreateSignature%2A> method is called to perform the signing.</span></span>

<span data-ttu-id="5221a-116">En raison de problèmes de collision avec SHA1, nous vous recommandons SHA256 ou une meilleure solution.</span><span class="sxs-lookup"><span data-stu-id="5221a-116">Due to collision problems with SHA1, we recommend SHA256 or better.</span></span>

```vb
Imports System.Security.Cryptography

Module Module1
    Sub Main()
        'The hash value to sign.
        Dim hashValue As Byte() = {59, 4, 248, 102, 77, 97, 142, 201, 210, 12, 224, 93, 25, 41, 100, 197, 213, 134, 130, 135}

        'The value to hold the signed value.
        Dim signedHashValue() As Byte

        'Generate a public/private key pair.
        Dim rsa As RSA = RSA.Create()

        'Create an RSAPKCS1SignatureFormatter object and pass it
        'the RSA instance to transfer the private key.
        Dim rsaFormatter As New RSAPKCS1SignatureFormatter(rsa)

        'Set the hash algorithm to SHA1.
        rsaFormatter.SetHashAlgorithm("SHA1")

        'Create a signature for hashValue and assign it to
        'signedHashValue.
        signedHashValue = rsaFormatter.CreateSignature(hashValue)
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
      //The hash value to sign.
      byte[] hashValue = {59,4,248,102,77,97,142,201,210,12,224,93,25,41,100,197,213,134,130,135};

      //The value to hold the signed value.
      byte[] signedHashValue;

      //Generate a public/private key pair.
      RSA rsa = RSA.Create();

      //Create an RSAPKCS1SignatureFormatter object and pass it the
      //RSA instance to transfer the private key.
      RSAPKCS1SignatureFormatter rsaFormatter = new RSAPKCS1SignatureFormatter(rsa);

      //Set the hash algorithm to SHA1.
      rsaFormatter.SetHashAlgorithm("SHA1");

      //Create a signature for hashValue and assign it to
      //signedHashValue.
      signedHashValue = rsaFormatter.CreateSignature(hashValue);
   }
}
```

## <a name="verifying-signatures"></a><span data-ttu-id="5221a-117">Vérification des signatures</span><span class="sxs-lookup"><span data-stu-id="5221a-117">Verifying Signatures</span></span>

<span data-ttu-id="5221a-118">Pour vérifier que les données ont été signées par un tiers donné, vous devez disposer des informations suivantes :</span><span class="sxs-lookup"><span data-stu-id="5221a-118">To verify that data was signed by a particular party, you must have the following information:</span></span>

- <span data-ttu-id="5221a-119">la clé publique du tiers qui a signé les données ;</span><span class="sxs-lookup"><span data-stu-id="5221a-119">The public key of the party that signed the data.</span></span>

- <span data-ttu-id="5221a-120">la signature numérique ;</span><span class="sxs-lookup"><span data-stu-id="5221a-120">The digital signature.</span></span>

- <span data-ttu-id="5221a-121">les données qui ont été signées ;</span><span class="sxs-lookup"><span data-stu-id="5221a-121">The data that was signed.</span></span>

- <span data-ttu-id="5221a-122">l'algorithme de hachage utilisé par le signataire.</span><span class="sxs-lookup"><span data-stu-id="5221a-122">The hash algorithm used by the signer.</span></span>

<span data-ttu-id="5221a-123">Pour vérifier une signature signée par la classe <xref:System.Security.Cryptography.RSAPKCS1SignatureFormatter> , utilisez la classe <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter> .</span><span class="sxs-lookup"><span data-stu-id="5221a-123">To verify a signature signed by the <xref:System.Security.Cryptography.RSAPKCS1SignatureFormatter> class, use the <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter> class.</span></span> <span data-ttu-id="5221a-124">La clé publique du signataire doit être fournie à la classe <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter> .</span><span class="sxs-lookup"><span data-stu-id="5221a-124">The <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter> class must be supplied the public key of the signer.</span></span> <span data-ttu-id="5221a-125">Pour RSA, vous aurez besoin des valeurs du modulo et de l’exposant pour spécifier la clé publique.</span><span class="sxs-lookup"><span data-stu-id="5221a-125">For RSA, you will need the values of the modulus and the exponent to specify the public key.</span></span> <span data-ttu-id="5221a-126">(Le tiers qui a généré la paire de clés publique/privée doit fournir ces valeurs.) Commencez par créer un <xref:System.Security.Cryptography.RSA> objet pour contenir la clé publique qui vérifiera la signature, puis initialisez une <xref:System.Security.Cryptography.RSAParameters> structure avec les valeurs de l’exposant et du modulo qui spécifient la clé publique.</span><span class="sxs-lookup"><span data-stu-id="5221a-126">(The party that generated the public/private key pair should provide these values.) First create an <xref:System.Security.Cryptography.RSA> object to hold the public key that will verify the signature, and then initialize an <xref:System.Security.Cryptography.RSAParameters> structure to the modulus and exponent values that specify the public key.</span></span>

<span data-ttu-id="5221a-127">Le code suivant illustre la création d’une structure <xref:System.Security.Cryptography.RSAParameters> .</span><span class="sxs-lookup"><span data-stu-id="5221a-127">The following code shows the creation of an <xref:System.Security.Cryptography.RSAParameters> structure.</span></span> <span data-ttu-id="5221a-128">La propriété `Modulus` est définie avec la valeur d'un tableau d'octets nommé `modulusData` , tandis que la propriété `Exponent` est définie avec la valeur d'un tableau d'octets nommé `exponentData`.</span><span class="sxs-lookup"><span data-stu-id="5221a-128">The `Modulus` property is set to the value of a byte array called `modulusData` and the `Exponent` property is set to the value of a byte array called `exponentData`.</span></span>

```vb
Dim rsaKeyInfo As RSAParameters
rsaKeyInfo.Modulus = modulusData
rsaKeyInfo.Exponent = exponentData
```

```csharp
RSAParameters rsaKeyInfo;
rsaKeyInfo.Modulus = modulusData;
rsaKeyInfo.Exponent = exponentData;
```

<span data-ttu-id="5221a-129">Après avoir créé l' <xref:System.Security.Cryptography.RSAParameters> objet, vous pouvez initialiser une nouvelle instance de la <xref:System.Security.Cryptography.RSA> classe d’implémentation aux valeurs spécifiées dans <xref:System.Security.Cryptography.RSAParameters> .</span><span class="sxs-lookup"><span data-stu-id="5221a-129">After you have created the <xref:System.Security.Cryptography.RSAParameters> object, you can initialize a new instance of the <xref:System.Security.Cryptography.RSA> implementation class to the values specified in <xref:System.Security.Cryptography.RSAParameters>.</span></span> <span data-ttu-id="5221a-130">L' <xref:System.Security.Cryptography.RSA> instance est, à son tour, passée au constructeur d’un <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter> pour transférer la clé.</span><span class="sxs-lookup"><span data-stu-id="5221a-130">The <xref:System.Security.Cryptography.RSA> instance is, in turn, passed to the constructor of an <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter> to transfer the key.</span></span>

<span data-ttu-id="5221a-131">L'exemple suivant illustre ce processus.</span><span class="sxs-lookup"><span data-stu-id="5221a-131">The following example illustrates this process.</span></span> <span data-ttu-id="5221a-132">Dans cet exemple, `hashValue` et `signedHashValue` sont les tableaux d'octets fournis par un tiers distant.</span><span class="sxs-lookup"><span data-stu-id="5221a-132">In this example, `hashValue` and `signedHashValue` are arrays of bytes provided by a remote party.</span></span> <span data-ttu-id="5221a-133">Le tiers distant a signé `hashValue` à l'aide de l'algorithme SHA1, générant ainsi la signature numérique `signedHashValue`.</span><span class="sxs-lookup"><span data-stu-id="5221a-133">The remote party has signed the `hashValue` using the SHA1 algorithm, producing the digital signature `signedHashValue`.</span></span> <span data-ttu-id="5221a-134">La <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter.VerifySignature%2A?displayProperty=nameWithType> méthode vérifie que la signature numérique est valide et qu’elle a été utilisée pour signer `hashValue` .</span><span class="sxs-lookup"><span data-stu-id="5221a-134">The <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter.VerifySignature%2A?displayProperty=nameWithType> method verifies that the digital signature is valid and was used to sign the `hashValue`.</span></span>

<span data-ttu-id="5221a-135">En raison de problèmes de collision avec SHA1, nous vous recommandons SHA256 ou une meilleure solution.</span><span class="sxs-lookup"><span data-stu-id="5221a-135">Due to collision problems with SHA1, we recommend SHA256 or better.</span></span>  <span data-ttu-id="5221a-136">Toutefois, si SHA1 a été utilisé pour créer la signature, vous devez utiliser SHA1 pour vérifier la signature.</span><span class="sxs-lookup"><span data-stu-id="5221a-136">However, if SHA1 was used to create the signature, you have to use SHA1 to verify the signature.</span></span>

```vb
Dim rsa As RSA = RSA.Create()
rsa.ImportParameters(rsaKeyInfo)
Dim rsaDeformatter As New RSAPKCS1SignatureDeformatter(rsa)
rsaDeformatter.SetHashAlgorithm("SHA1")
If rsaDeformatter.VerifySignature(hashValue, signedHashValue) Then
   Console.WriteLine("The signature is valid.")
Else
   Console.WriteLine("The signature is not valid.")
End If
```

```csharp
RSA rsa = RSA.Create();
rsa.ImportParameters(rsaKeyInfo);
RSAPKCS1SignatureDeformatter rsaDeformatter = new RSAPKCS1SignatureDeformatter(rsa);
rsaDeformatter.SetHashAlgorithm("SHA1");
if(rsaDeformatter.VerifySignature(hashValue, signedHashValue))
{
   Console.WriteLine("The signature is valid.");
}
else
{
   Console.WriteLine("The signature is not valid.");
}
```

<span data-ttu-id="5221a-137">Ce fragment de code affiche «`The signature is valid`» si la signature est valide et «`The signature is not valid`» si elle ne l'est pas.</span><span class="sxs-lookup"><span data-stu-id="5221a-137">This code fragment will display "`The signature is valid`" if the signature is valid and "`The signature is not valid`" if it is not.</span></span>

## <a name="see-also"></a><span data-ttu-id="5221a-138">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5221a-138">See also</span></span>

- [<span data-ttu-id="5221a-139">services de chiffrement</span><span class="sxs-lookup"><span data-stu-id="5221a-139">Cryptographic Services</span></span>](cryptographic-services.md)
- [<span data-ttu-id="5221a-140">Modèle de chiffrement</span><span class="sxs-lookup"><span data-stu-id="5221a-140">Cryptography Model</span></span>](cryptography-model.md)
- [<span data-ttu-id="5221a-141">Chiffrement multiplateforme</span><span class="sxs-lookup"><span data-stu-id="5221a-141">Cross-Platform Cryptography</span></span>](cross-platform-cryptography.md)
- [<span data-ttu-id="5221a-142">Protection des données ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="5221a-142">ASP.NET Core Data Protection</span></span>](/aspnet/core/security/data-protection/introduction)
