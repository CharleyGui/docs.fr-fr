---
title: Signatures de chiffrement
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- digital signatures
- cryptography [.NET Framework], signatures
- digital signatures, XML signing
- signatures, cryptographic
- digital signatures, generating
- verifying signatures
- generating signatures
- digital signatures, about
- encryption [.NET Framework], signatures
- security [.NET Framework], signatures
- XML signing
- digital signatures, verifying
- signing XML
ms.assetid: aa87cb7f-e608-4a81-948b-c9b8a1225783
ms.openlocfilehash: 9e69578ceffeeacb73cf059f5b577fe7c137b599
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84288392"
---
# <a name="cryptographic-signatures"></a><span data-ttu-id="f5391-102">Signatures de chiffrement</span><span class="sxs-lookup"><span data-stu-id="f5391-102">Cryptographic Signatures</span></span>

<span data-ttu-id="f5391-103">Les signatures numériques de chiffrement utilisent des algorithmes de clé publique pour assurer l'intégrité des données.</span><span class="sxs-lookup"><span data-stu-id="f5391-103">Cryptographic digital signatures use public key algorithms to provide data integrity.</span></span> <span data-ttu-id="f5391-104">Quand vous signez des données avec une signature numérique, un tiers peut vérifier la signature et prouver que les données viennent bien de vous et qu'elles n'ont pas été modifiées après que vous les avez signées.</span><span class="sxs-lookup"><span data-stu-id="f5391-104">When you sign data with a digital signature, someone else can verify the signature, and can prove that the data originated from you and was not altered after you signed it.</span></span> <span data-ttu-id="f5391-105">Pour plus d’informations sur les signatures numériques, consultez [Cryptographic Services](cryptographic-services.md).</span><span class="sxs-lookup"><span data-stu-id="f5391-105">For more information about digital signatures, see [Cryptographic Services](cryptographic-services.md).</span></span>

<span data-ttu-id="f5391-106">Cette rubrique explique comment générer et vérifier des signatures numériques en utilisant les classes de l'espace de noms <xref:System.Security.Cryptography?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="f5391-106">This topic explains how to generate and verify digital signatures using classes in the <xref:System.Security.Cryptography?displayProperty=nameWithType> namespace.</span></span>

## <a name="generating-signatures"></a><span data-ttu-id="f5391-107">Génération de signatures</span><span class="sxs-lookup"><span data-stu-id="f5391-107">Generating Signatures</span></span>

<span data-ttu-id="f5391-108">Les signatures numériques sont généralement appliquées à des valeurs de hachage qui représentent des données plus volumineuses.</span><span class="sxs-lookup"><span data-stu-id="f5391-108">Digital signatures are usually applied to hash values that represent larger data.</span></span> <span data-ttu-id="f5391-109">Dans l'exemple suivant, une signature numérique est appliquée à une valeur de hachage.</span><span class="sxs-lookup"><span data-stu-id="f5391-109">The following example applies a digital signature to a hash value.</span></span> <span data-ttu-id="f5391-110">Dans un premier temps, une nouvelle instance de la classe <xref:System.Security.Cryptography.RSACryptoServiceProvider> est créée pour générer une paire de clés publique/privée.</span><span class="sxs-lookup"><span data-stu-id="f5391-110">First, a new instance of the <xref:System.Security.Cryptography.RSACryptoServiceProvider> class is created to generate a public/private key pair.</span></span> <span data-ttu-id="f5391-111">Ensuite, <xref:System.Security.Cryptography.RSACryptoServiceProvider> est passé à une nouvelle instance de la classe <xref:System.Security.Cryptography.RSAPKCS1SignatureFormatter> .</span><span class="sxs-lookup"><span data-stu-id="f5391-111">Next, the <xref:System.Security.Cryptography.RSACryptoServiceProvider> is passed to a new instance of the <xref:System.Security.Cryptography.RSAPKCS1SignatureFormatter> class.</span></span> <span data-ttu-id="f5391-112">Cela a pour effet de transférer la clé privée à <xref:System.Security.Cryptography.RSAPKCS1SignatureFormatter>, qui effectue la signature numérique proprement dite.</span><span class="sxs-lookup"><span data-stu-id="f5391-112">This transfers the private key to the <xref:System.Security.Cryptography.RSAPKCS1SignatureFormatter>, which actually performs the digital signing.</span></span> <span data-ttu-id="f5391-113">Pour pouvoir signer le code de hachage, vous devez au préalable spécifier l'algorithme de hachage à utiliser.</span><span class="sxs-lookup"><span data-stu-id="f5391-113">Before you can sign the hash code, you must specify a hash algorithm to use.</span></span> <span data-ttu-id="f5391-114">Dans cet exemple, c'est l'algorithme SHA1 qui est utilisé.</span><span class="sxs-lookup"><span data-stu-id="f5391-114">This example uses the SHA1 algorithm.</span></span> <span data-ttu-id="f5391-115">Enfin, la méthode <xref:System.Security.Cryptography.AsymmetricSignatureFormatter.CreateSignature%2A> est appelée pour effectuer la signature.</span><span class="sxs-lookup"><span data-stu-id="f5391-115">Finally, the <xref:System.Security.Cryptography.AsymmetricSignatureFormatter.CreateSignature%2A> method is called to perform the signing.</span></span>

<span data-ttu-id="f5391-116">En raison de problèmes de collision avec SHA1, Microsoft recommande SHA256 ou une meilleure solution.</span><span class="sxs-lookup"><span data-stu-id="f5391-116">Due to collision problems with SHA1, Microsoft recommends SHA256 or better.</span></span>

```vb
Imports System.Security.Cryptography

Module Module1
    Sub Main()
        'The hash value to sign.
        Dim hashValue As Byte() = {59, 4, 248, 102, 77, 97, 142, 201, 210, 12, 224, 93, 25, 41, 100, 197, 213, 134, 130, 135}

        'The value to hold the signed value.
        Dim signedHashValue() As Byte

        'Generate a public/private key pair.
        Dim rsa As New RSACryptoServiceProvider()

        'Create an RSAPKCS1SignatureFormatter object and pass it
        'the RSACryptoServiceProvider to transfer the private key.
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
      RSACryptoServiceProvider rsa = new RSACryptoServiceProvider();

      //Create an RSAPKCS1SignatureFormatter object and pass it the
      //RSACryptoServiceProvider to transfer the private key.
      RSAPKCS1SignatureFormatter rsaFormatter = new RSAPKCS1SignatureFormatter(rsa);

      //Set the hash algorithm to SHA1.
      rsaFormatter.SetHashAlgorithm("SHA1");

      //Create a signature for hashValue and assign it to
      //signedHashValue.
      signedHashValue = rsaFormatter.CreateSignature(hashValue);
   }
}
```

### <a name="signing-xml-files"></a><span data-ttu-id="f5391-117">Signature des fichiers XML</span><span class="sxs-lookup"><span data-stu-id="f5391-117">Signing XML Files</span></span>

<span data-ttu-id="f5391-118">Le .NET Framework fournit l’espace de noms <xref:System.Security.Cryptography.Xml> , qui vous permet de signer le XML.</span><span class="sxs-lookup"><span data-stu-id="f5391-118">The .NET Framework provides the <xref:System.Security.Cryptography.Xml> namespace, which enables you sign XML.</span></span> <span data-ttu-id="f5391-119">Il est important de signer le XML quand vous voulez vérifier qu'il provient bien d'une certaine source.</span><span class="sxs-lookup"><span data-stu-id="f5391-119">Signing XML is important when you want to verify that the XML originates from a certain source.</span></span> <span data-ttu-id="f5391-120">Par exemple, si vous utilisez un service de cotation boursière qui utilise du XML, vous pouvez vérifier la source de ce dernier s'il est signé.</span><span class="sxs-lookup"><span data-stu-id="f5391-120">For example, if you are using a stock quote service that uses XML, you can verify the source of the XML if it is signed.</span></span>

<span data-ttu-id="f5391-121">Les classes de cet espace de noms suivent les [recommandations en matière de syntaxe et de traitement des signatures XML](https://www.w3.org/TR/xmldsig-core/) du World Wide Web Consortium.</span><span class="sxs-lookup"><span data-stu-id="f5391-121">The classes in this namespace follow the [XML-Signature Syntax and Processing recommendation](https://www.w3.org/TR/xmldsig-core/) from the World Wide Web Consortium.</span></span>

## <a name="verifying-signatures"></a><span data-ttu-id="f5391-122">Vérification des signatures</span><span class="sxs-lookup"><span data-stu-id="f5391-122">Verifying Signatures</span></span>

<span data-ttu-id="f5391-123">Pour vérifier que les données ont été signées par un tiers donné, vous devez disposer des informations suivantes :</span><span class="sxs-lookup"><span data-stu-id="f5391-123">To verify that data was signed by a particular party, you must have the following information:</span></span>

- <span data-ttu-id="f5391-124">la clé publique du tiers qui a signé les données ;</span><span class="sxs-lookup"><span data-stu-id="f5391-124">The public key of the party that signed the data.</span></span>

- <span data-ttu-id="f5391-125">la signature numérique ;</span><span class="sxs-lookup"><span data-stu-id="f5391-125">The digital signature.</span></span>

- <span data-ttu-id="f5391-126">les données qui ont été signées ;</span><span class="sxs-lookup"><span data-stu-id="f5391-126">The data that was signed.</span></span>

- <span data-ttu-id="f5391-127">l'algorithme de hachage utilisé par le signataire.</span><span class="sxs-lookup"><span data-stu-id="f5391-127">The hash algorithm used by the signer.</span></span>

<span data-ttu-id="f5391-128">Pour vérifier une signature signée par la classe <xref:System.Security.Cryptography.RSAPKCS1SignatureFormatter> , utilisez la classe <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter> .</span><span class="sxs-lookup"><span data-stu-id="f5391-128">To verify a signature signed by the <xref:System.Security.Cryptography.RSAPKCS1SignatureFormatter> class, use the <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter> class.</span></span> <span data-ttu-id="f5391-129">La clé publique du signataire doit être fournie à la classe <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter> .</span><span class="sxs-lookup"><span data-stu-id="f5391-129">The <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter> class must be supplied the public key of the signer.</span></span> <span data-ttu-id="f5391-130">Vous aurez besoin des valeurs du modulo et de l'exposant pour spécifier la clé publique.</span><span class="sxs-lookup"><span data-stu-id="f5391-130">You will need the values of the modulus and the exponent to specify the public key.</span></span> <span data-ttu-id="f5391-131">(Le tiers qui a généré la paire de clés publique/privée doit fournir ces valeurs.) Commencez par créer un <xref:System.Security.Cryptography.RSACryptoServiceProvider> objet pour contenir la clé publique qui vérifiera la signature, puis initialisez une <xref:System.Security.Cryptography.RSAParameters> structure avec les valeurs de l’exposant et du modulo qui spécifient la clé publique.</span><span class="sxs-lookup"><span data-stu-id="f5391-131">(The party that generated the public/private key pair should provide these values.) First create an <xref:System.Security.Cryptography.RSACryptoServiceProvider> object to hold the public key that will verify the signature, and then initialize an <xref:System.Security.Cryptography.RSAParameters> structure to the modulus and exponent values that specify the public key.</span></span>

<span data-ttu-id="f5391-132">Le code suivant illustre la création d’une structure <xref:System.Security.Cryptography.RSAParameters> .</span><span class="sxs-lookup"><span data-stu-id="f5391-132">The following code shows the creation of an <xref:System.Security.Cryptography.RSAParameters> structure.</span></span> <span data-ttu-id="f5391-133">La propriété `Modulus` est définie avec la valeur d'un tableau d'octets nommé `modulusData` , tandis que la propriété `Exponent` est définie avec la valeur d'un tableau d'octets nommé `exponentData`.</span><span class="sxs-lookup"><span data-stu-id="f5391-133">The `Modulus` property is set to the value of a byte array called `modulusData` and the `Exponent` property is set to the value of a byte array called `exponentData`.</span></span>

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

<span data-ttu-id="f5391-134">Après avoir créé l’objet <xref:System.Security.Cryptography.RSAParameters> , vous pouvez initialiser une nouvelle instance de la classe <xref:System.Security.Cryptography.RSACryptoServiceProvider> avec les valeurs spécifiées dans <xref:System.Security.Cryptography.RSAParameters>.</span><span class="sxs-lookup"><span data-stu-id="f5391-134">After you have created the <xref:System.Security.Cryptography.RSAParameters> object, you can initialize a new instance of the <xref:System.Security.Cryptography.RSACryptoServiceProvider> class to the values specified in <xref:System.Security.Cryptography.RSAParameters>.</span></span> <span data-ttu-id="f5391-135">À son tour, la classe <xref:System.Security.Cryptography.RSACryptoServiceProvider> est transmise au constructeur d'un <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter> pour transférer la clé.</span><span class="sxs-lookup"><span data-stu-id="f5391-135">The <xref:System.Security.Cryptography.RSACryptoServiceProvider> is, in turn, passed to the constructor of an <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter> to transfer the key.</span></span>

<span data-ttu-id="f5391-136">L'exemple suivant illustre ce processus.</span><span class="sxs-lookup"><span data-stu-id="f5391-136">The following example illustrates this process.</span></span> <span data-ttu-id="f5391-137">Dans cet exemple, `hashValue` et `signedHashValue` sont les tableaux d'octets fournis par un tiers distant.</span><span class="sxs-lookup"><span data-stu-id="f5391-137">In this example, `hashValue` and `signedHashValue` are arrays of bytes provided by a remote party.</span></span> <span data-ttu-id="f5391-138">Le tiers distant a signé `hashValue` à l'aide de l'algorithme SHA1, générant ainsi la signature numérique `signedHashValue`.</span><span class="sxs-lookup"><span data-stu-id="f5391-138">The remote party has signed the `hashValue` using the SHA1 algorithm, producing the digital signature `signedHashValue`.</span></span> <span data-ttu-id="f5391-139">La <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter.VerifySignature%2A?displayProperty=nameWithType> méthode vérifie que la signature numérique est valide et qu’elle a été utilisée pour signer `hashValue` .</span><span class="sxs-lookup"><span data-stu-id="f5391-139">The <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter.VerifySignature%2A?displayProperty=nameWithType> method verifies that the digital signature is valid and was used to sign the `hashValue`.</span></span>

```vb
Dim rsa As New RSACryptoServiceProvider()
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
RSACryptoServiceProvider rsa = new RSACryptoServiceProvider();
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

<span data-ttu-id="f5391-140">Ce fragment de code affiche «`The signature is valid`» si la signature est valide et «`The signature is not valid`» si elle ne l'est pas.</span><span class="sxs-lookup"><span data-stu-id="f5391-140">This code fragment will display "`The signature is valid`" if the signature is valid and "`The signature is not valid`" if it is not.</span></span>

## <a name="see-also"></a><span data-ttu-id="f5391-141">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f5391-141">See also</span></span>

- [<span data-ttu-id="f5391-142">Services de chiffrement</span><span class="sxs-lookup"><span data-stu-id="f5391-142">Cryptographic Services</span></span>](cryptographic-services.md)
