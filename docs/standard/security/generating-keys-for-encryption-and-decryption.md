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
# <a name="generating-keys-for-encryption-and-decryption"></a>Génération de clés pour le chiffrement et le déchiffrement
La création et la gestion des clés constituent une part importante du processus de chiffrement. Les algorithmes symétriques nécessitent la création d'une clé et d'un vecteur d'initialisation. La clé ne doit pas être divulguée aux personnes qui ne sont pas autorisées à déchiffrer vos données. Le vecteur d'initialisation peut être divulgué, mais doit être modifié à chaque session. Les algorithmes asymétriques nécessitent la création d'une clé publique et d'une clé privée. La clé publique peut être donnée à tout le monde. Toutefois, la clé privée ne doit être connue que de la partie chargée du déchiffrement des données chiffrées à l'aide de la clé publique. Cette section décrit comment générer et gérer des clés pour les algorithmes symétriques et asymétriques.  
  
## <a name="symmetric-keys"></a>Clés symétriques  
 Les classes de chiffrement symétrique fournies par .NET requièrent une clé et un nouveau vecteur d’initialisation (IV) pour chiffrer et déchiffrer les données. Chaque fois que vous créez une nouvelle instance de l’une des classes de chiffrement symétrique managées à l’aide de la méthode sans paramètre `Create()` , une nouvelle clé et un nouveau vecteur d’exécution sont créés automatiquement. Toute personne que vous autorisez à déchiffrer vos données doit posséder la même clé et le même vecteur d'initialisation, et doit utiliser le même algorithme. En général, une nouvelle clé et un nouveau vecteur d'initialisation doivent être créés pour chaque session. Ni la clé, ni le vecteur d'initialisation ne doivent être stockés en vue d'être utilisés dans une session ultérieure.  
  
 Pour communiquer une clé symétrique et un vecteur d'initialisation à une partie distante, vous devez, en général, chiffrer la clé symétrique à l'aide du chiffrement asymétrique. L'envoi d'une clé non chiffrée vers un réseau non sécurisé est risqué, car toute personne qui intercepte la clé et le vecteur d'initialisation peut ensuite déchiffrer vos données.  
  
 L’exemple suivant illustre la création d’une nouvelle instance de la classe d’implémentation par défaut pour l' <xref:System.Security.Cryptography.Aes> algorithme.  
  
```vb  
Dim aes As Aes = Aes.Create()  
```  
  
```csharp  
Aes aes = Aes.Create();  
```  
  
 Quand le code précédent est exécuté, une nouvelle clé et un nouveau vecteur d'initialisation sont générés, puis placés dans les propriétés **Key** et **IV** , respectivement.  
  
 Vous devrez parfois générer plusieurs clés. Dans ce cas, vous pouvez créer une instance d'une classe qui implémente un algorithme symétrique et ensuite créer une nouvelle clé et un nouveau vecteur d'initialisation en appelant les méthodes **GenerateKey** et **GenerateIV** . L’exemple de code suivant montre comment créer de nouvelles clés et IV après avoir effectué une nouvelle instance de la classe de chiffrement symétrique.  
  
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
  
 Lorsque le code précédent est exécuté, une clé et un vecteur d’exécution sont générés lorsque la nouvelle instance d' **AES** est créée. Une autre clé et un autre vecteur d'initialisation sont créés quand les méthodes **GenerateKey** et **GenerateIV** sont appelées.
  
## <a name="asymmetric-keys"></a>Clés asymétriques

 .NET fournit la <xref:System.Security.Cryptography.RSA> classe pour le chiffrement asymétrique. Cette classe crée une paire de clés publique/privée quand vous utilisez la méthode sans paramètre `Create()` pour créer une nouvelle instance. Les clés asymétriques peuvent être stockées en vue d'être utilisées pour plusieurs sessions, ou bien être générées pour une session unique. La clé publique peut être connue de tous, contrairement à la clé privée qui ne doit être divulguée qu'à certaines personnes.  
  
 Une paire de clés publique/privée est générée chaque fois qu'une nouvelle instance d'une classe d'algorithme asymétrique est créée. Après la création d’une nouvelle instance de la classe, les informations de clé peuvent être extraites à l’aide de la <xref:System.Security.Cryptography.RSA.ExportParameters%2A> méthode, qui retourne une <xref:System.Security.Cryptography.RSAParameters> structure qui contient les informations de clé. La méthode accepte une valeur booléenne qui indique s’il faut retourner uniquement les informations sur la clé publique ou retourner les informations de clé publique et de clé privée.

Il existe également d’autres méthodes qui vous permettent d’extraire des informations clés, telles que :

* <xref:System.Security.Cryptography.RSA.ExportRSAPublicKey%2A?displayProperty=nameWithType>
* <xref:System.Security.Cryptography.RSA.ExportRSAPrivateKey%2A?displayProperty=nameWithType>
* <xref:System.Security.Cryptography.AsymmetricAlgorithm.ExportSubjectPublicKeyInfo%2A?displayProperty=nameWithType>
* <xref:System.Security.Cryptography.AsymmetricAlgorithm.ExportPkcs8PrivateKey%2A?displayProperty=nameWithType>
* <xref:System.Security.Cryptography.AsymmetricAlgorithm.ExportEncryptedPkcs8PrivateKey%2A?displayProperty=nameWithType>

Une instance **RSA** peut être initialisée à la valeur d’une structure **RSAParameters** à l’aide de la <xref:System.Security.Cryptography.RSA.ImportParameters%2A> méthode. Ou créez une nouvelle instance de à l’aide de la <xref:System.Security.Cryptography.RSA.Create(System.Security.Cryptography.RSAParameters)?displayProperty=nameWithType> méthode.  
  
 Les clés privées asymétriques ne doivent jamais être stockées textuellement ou en texte brut sur l'ordinateur local. Si vous avez besoin de stocker une clé privée, vous devez utiliser un conteneur de clé. Pour plus d’informations sur la façon de stocker une clé privée dans un conteneur de clé, consultez [Comment : stocker des clés asymétriques dans un conteneur de clé](how-to-store-asymmetric-keys-in-a-key-container.md).  
  
 L’exemple de code suivant crée une nouvelle instance de la classe **RSA** , en créant une paire de clés publique/privée, puis enregistre les informations de clé publique dans une structure **RSAParameters** .  
  
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
  
## <a name="see-also"></a>Voir aussi

- [Chiffrement de données](encrypting-data.md)
- [Déchiffrement de données](decrypting-data.md)
- [services de chiffrement](cryptographic-services.md)
- [Procédure : stocker des clés asymétriques dans un conteneur de clé](how-to-store-asymmetric-keys-in-a-key-container.md)
- [Chiffrement multiplateforme](cross-platform-cryptography.md)
- [Protection des données ASP.NET Core](/aspnet/core/security/data-protection/introduction)
