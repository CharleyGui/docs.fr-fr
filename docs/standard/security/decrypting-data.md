---
title: Déchiffrement de données
description: Découvrez Comment déchiffrer des données dans .NET, à l’aide d’un algorithme symétrique ou d’un algorithme asymétrique.
ms.date: 07/16/2020
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data [.NET], decryption
- symmetric decryption
- asymmetric decryption
- decryption
ms.assetid: 9b266b6c-a9b2-4d20-afd8-b3a0d8fd48a0
ms.openlocfilehash: 7e8fe5a8b7ed7c217a31a8ee91a5d111257fed45
ms.sourcegitcommit: 30a686fd4377fe6472aa04e215c0de711bc1c322
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/10/2020
ms.locfileid: "94440983"
---
# <a name="decrypting-data"></a>Déchiffrement de données

Le déchiffrement est l'opération inverse du chiffrement. Pour le chiffrement à clé secrète, vous devez connaître à la fois la clé et le vecteur d'initialisation qui ont été utilisés pour chiffrer les données. Pour le chiffrement à clé publique, vous devez connaître soit la clé publique (si les données ont été chiffrées à l'aide de la clé privée), soit la clé privée (si les données ont été chiffrées à l'aide de la clé publique).

## <a name="symmetric-decryption"></a>Déchiffrement symétrique

Le déchiffrement de données chiffrées à l'aide d'algorithmes symétriques est similaire au processus utilisé pour chiffrer les données à l'aide d'algorithmes symétriques. La <xref:System.Security.Cryptography.CryptoStream> classe est utilisée avec les classes de chiffrement symétrique fournies par .net pour déchiffrer les données lues à partir de n’importe quel objet de flux managé.

L’exemple suivant illustre la création d’une nouvelle instance de la classe d’implémentation par défaut pour l' <xref:System.Security.Cryptography.Aes> algorithme. L’instance est utilisée pour effectuer un déchiffrement sur un <xref:System.Security.Cryptography.CryptoStream> objet. Cet exemple crée d’abord une nouvelle instance de la <xref:System.Security.Cryptography.Aes> classe d’implémentation. Il lit la valeur du vecteur d’initialisation (IV) à partir d’une variable de flux managée, `myStream` . Ensuite, il instancie un <xref:System.Security.Cryptography.CryptoStream> objet et l’initialise à la valeur de l' `myStream` instance. La <xref:System.Security.Cryptography.SymmetricAlgorithm.CreateDecryptor%2A?displayProperty=nameWithType> méthode de l' <xref:System.Security.Cryptography.Aes> instance reçoit la valeur IV et la même clé que celle utilisée pour le chiffrement.

```vb
Dim aes As Aes = Aes.Create()
Dim cryptStream As New CryptoStream(myStream, aes.CreateDecryptor(key, iv), CryptoStreamMode.Read)
```

```csharp
Aes aes = Aes.Create();
CryptoStream cryptStream = new CryptoStream(myStream, aes.CreateDecryptor(key, iv), CryptoStreamMode.Read);
```

L'exemple suivant montre l'intégralité des processus de création de flux, de déchiffrement de flux, de lecture depuis un flux et de fermeture de flux. Un objet de flux de fichier qui lit un fichier nommé *TestData.txt* est créé. Le flux de fichier est ensuite déchiffré à l’aide de la classe **CryptoStream** et de la classe **AES** . Cet exemple spécifie la valeur de clé utilisée dans l’exemple de chiffrement symétrique pour le [chiffrement des données](encrypting-data.md). Il ne montre pas le code nécessaire pour chiffrer et transférer ces valeurs.

:::code language="csharp" source="snippets/decrypting-data/csharp/aes-decrypt.cs":::
:::code language="vb" source="snippets/decrypting-data/vb/aes-decrypt.vb":::

L’exemple précédent utilise la même clé, et l’algorithme utilisé dans l’exemple de chiffrement symétrique pour le [chiffrement des données](encrypting-data.md). Il déchiffre le fichier *TestData.txt* créé par cet exemple et affiche le texte d’origine sur la console.

## <a name="asymmetric-decryption"></a>Déchiffrement asymétrique

En règle générale, une partie (partie A) génère à la fois une clé publique et une clé privée, et stocke ces clés dans la mémoire ou dans un conteneur de clé de chiffrement. La partie A envoie ensuite la clé publique à une autre partie (partie B). À l’aide de la clé publique, le tiers B chiffre les données et renvoie les données au tiers A. Après avoir reçu les données, la partie A les déchiffre à l’aide de la clé privée qui correspond. Le déchiffrement réussira uniquement si la partie A utilise la clé privée qui correspond à la clé publique utilisée par la partie B pour chiffrer les données.

Pour plus d’informations sur le stockage des clés asymétriques dans un conteneur de clé de chiffrement sécurisé et sur la récupération des clés asymétriques, consultez [How to: Store Asymmetric Keys in a Key Container](how-to-store-asymmetric-keys-in-a-key-container.md).

L'exemple suivant montre le déchiffrement de deux tableaux d'octets qui représentent une clé symétrique et un vecteur d'initialisation. Pour plus d’informations sur l’extraction de la clé publique asymétrique de l’objet <xref:System.Security.Cryptography.RSA> dans un format que vous pouvez facilement envoyer à un tiers, consultez [Encrypting Data](encrypting-data.md).

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

## <a name="see-also"></a>Voir aussi

- [Génération de clés pour le chiffrement et le déchiffrement](generating-keys-for-encryption-and-decryption.md)
- [Chiffrement de données](encrypting-data.md)
- [services de chiffrement](cryptographic-services.md)
- [Modèle de chiffrement](cryptography-model.md)
- [Chiffrement multiplateforme](cross-platform-cryptography.md)
- [Vulnérabilités de temporisation avec le déchiffrement symétrique en mode CBC à l’aide du remplissage](vulnerabilities-cbc-mode.md)
- [Protection des données ASP.NET Core](/aspnet/core/security/data-protection/introduction)
