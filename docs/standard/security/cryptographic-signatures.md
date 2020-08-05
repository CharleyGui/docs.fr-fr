---
title: Signatures de chiffrement
ms.date: 07/14/2020
ms.technology: dotnet-standard
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
ms.openlocfilehash: ce2be1d509da4e399bf87e1c8df7ba061fc2707c
ms.sourcegitcommit: b7a8b09828bab4e90f66af8d495ecd7024c45042
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87557006"
---
# <a name="cryptographic-signatures"></a>Signatures de chiffrement

Les signatures numériques de chiffrement utilisent des algorithmes de clé publique pour assurer l'intégrité des données. Quand vous signez des données avec une signature numérique, un tiers peut vérifier la signature et prouver que les données viennent bien de vous et qu'elles n'ont pas été modifiées après que vous les avez signées. Pour plus d’informations sur les signatures numériques, consultez [Cryptographic Services](cryptographic-services.md).

Cette rubrique explique comment générer et vérifier des signatures numériques en utilisant les classes de l'espace de noms <xref:System.Security.Cryptography> .

## <a name="generating-signatures"></a>Génération de signatures

Les signatures numériques sont généralement appliquées à des valeurs de hachage qui représentent des données plus volumineuses. Dans l'exemple suivant, une signature numérique est appliquée à une valeur de hachage. Dans un premier temps, une nouvelle instance de la classe <xref:System.Security.Cryptography.RSA> est créée pour générer une paire de clés publique/privée. Ensuite, <xref:System.Security.Cryptography.RSA> est passé à une nouvelle instance de la classe <xref:System.Security.Cryptography.RSAPKCS1SignatureFormatter> . Cela a pour effet de transférer la clé privée à <xref:System.Security.Cryptography.RSAPKCS1SignatureFormatter>, qui effectue la signature numérique proprement dite. Pour pouvoir signer le code de hachage, vous devez au préalable spécifier l'algorithme de hachage à utiliser. Dans cet exemple, c'est l'algorithme SHA1 qui est utilisé. Enfin, la méthode <xref:System.Security.Cryptography.AsymmetricSignatureFormatter.CreateSignature%2A> est appelée pour effectuer la signature.

En raison de problèmes de collision avec SHA1, nous vous recommandons SHA256 ou une meilleure solution.

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

## <a name="verifying-signatures"></a>Vérification des signatures

Pour vérifier que les données ont été signées par un tiers donné, vous devez disposer des informations suivantes :

- la clé publique du tiers qui a signé les données ;

- la signature numérique ;

- les données qui ont été signées ;

- l'algorithme de hachage utilisé par le signataire.

Pour vérifier une signature signée par la classe <xref:System.Security.Cryptography.RSAPKCS1SignatureFormatter> , utilisez la classe <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter> . La clé publique du signataire doit être fournie à la classe <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter> . Pour RSA, vous aurez besoin des valeurs du modulo et de l’exposant pour spécifier la clé publique. (Le tiers qui a généré la paire de clés publique/privée doit fournir ces valeurs.) Commencez par créer un <xref:System.Security.Cryptography.RSA> objet pour contenir la clé publique qui vérifiera la signature, puis initialisez une <xref:System.Security.Cryptography.RSAParameters> structure avec les valeurs de l’exposant et du modulo qui spécifient la clé publique.

Le code suivant illustre la création d’une structure <xref:System.Security.Cryptography.RSAParameters> . La propriété `Modulus` est définie avec la valeur d'un tableau d'octets nommé `modulusData` , tandis que la propriété `Exponent` est définie avec la valeur d'un tableau d'octets nommé `exponentData`.

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

Après avoir créé l' <xref:System.Security.Cryptography.RSAParameters> objet, vous pouvez initialiser une nouvelle instance de la <xref:System.Security.Cryptography.RSA> classe d’implémentation aux valeurs spécifiées dans <xref:System.Security.Cryptography.RSAParameters> . L' <xref:System.Security.Cryptography.RSA> instance est, à son tour, passée au constructeur d’un <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter> pour transférer la clé.

L'exemple suivant illustre ce processus. Dans cet exemple, `hashValue` et `signedHashValue` sont les tableaux d'octets fournis par un tiers distant. Le tiers distant a signé `hashValue` à l'aide de l'algorithme SHA1, générant ainsi la signature numérique `signedHashValue`. La <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter.VerifySignature%2A?displayProperty=nameWithType> méthode vérifie que la signature numérique est valide et qu’elle a été utilisée pour signer `hashValue` .

En raison de problèmes de collision avec SHA1, nous vous recommandons SHA256 ou une meilleure solution.  Toutefois, si SHA1 a été utilisé pour créer la signature, vous devez utiliser SHA1 pour vérifier la signature.

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

Ce fragment de code affiche «`The signature is valid`» si la signature est valide et «`The signature is not valid`» si elle ne l'est pas.

## <a name="see-also"></a>Voir aussi

- [services de chiffrement](cryptographic-services.md)
- [Modèle de chiffrement](cryptography-model.md)
- [Chiffrement multiplateforme](cross-platform-cryptography.md)
- [Protection des données ASP.NET Core](/aspnet/core/security/data-protection/introduction)
