---
title: Modèle de chiffrement .NET
description: Passez en revue les implémentations des algorithmes de chiffrement habituels dans .NET. Découvrez le modèle de chiffrement extensible de l’héritage d’objets, de la conception de flux & de la configuration.
ms.date: 07/14/2020
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- cryptography [.NET], model
- encryption [.NET], model
ms.assetid: 12fecad4-fbab-432a-bade-2f05976a2971
ms.openlocfilehash: a157a9a76f87a2a56c616b76c933e6d8d6415b03
ms.sourcegitcommit: 74d05613d6c57106f83f82ce8ee71176874ea3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/03/2020
ms.locfileid: "93281582"
---
# <a name="net-cryptography-model"></a>Modèle de chiffrement .NET

.NET fournit des implémentations de nombreux algorithmes de chiffrement standard, et le modèle de chiffrement .NET est extensible.

## <a name="object-inheritance"></a>Héritage d'objet

Le système de chiffrement .NET implémente un modèle extensible d’héritage de classes dérivées. Cette hiérarchie se présente comme suit :

- Classe de type algorithme, telle que <xref:System.Security.Cryptography.SymmetricAlgorithm> ,  <xref:System.Security.Cryptography.AsymmetricAlgorithm> ou <xref:System.Security.Cryptography.HashAlgorithm> . Ce niveau est abstrait.

- Classe d'algorithme qui hérite d'une classe de type algorithme, par exemple, <xref:System.Security.Cryptography.Aes>, <xref:System.Security.Cryptography.RSA> ou <xref:System.Security.Cryptography.ECDiffieHellman>. Ce niveau est abstrait.

- Implémentation d'une classe d'algorithme qui hérite d'une classe d'algorithme, par exemple, <xref:System.Security.Cryptography.AesManaged>, <xref:System.Security.Cryptography.RC2CryptoServiceProvider> ou <xref:System.Security.Cryptography.ECDiffieHellmanCng>. Ce niveau est totalement implémenté.

Ce modèle de classes dérivées vous permet d’ajouter un nouvel algorithme ou une nouvelle implémentation d’un algorithme existant. Par exemple, pour créer un algorithme de clé publique, vous devez hériter de la classe <xref:System.Security.Cryptography.AsymmetricAlgorithm>. Pour créer une nouvelle implémentation d'un algorithme spécifique, vous devez créer une classe non abstraite dérivée de cet algorithme.

## <a name="how-algorithms-are-implemented-in-net"></a>Comment les algorithmes sont implémentés dans .NET

Prenez comme exemple d'implémentation les algorithmes symétriques. La base de tous les algorithmes symétriques est <xref:System.Security.Cryptography.SymmetricAlgorithm> , qui est héritée par <xref:System.Security.Cryptography.Aes> , <xref:System.Security.Cryptography.TripleDES> et d’autres qui ne sont plus recommandées.

<xref:System.Security.Cryptography.Aes> est hérité par <xref:System.Security.Cryptography.AesCryptoServiceProvider> , <xref:System.Security.Cryptography.AesCng> et <xref:System.Security.Cryptography.AesManaged> .

Dans .NET Framework sur Windows :

* `*CryptoServiceProvider` les classes d’algorithme, telles que <xref:System.Security.Cryptography.AesCryptoServiceProvider> , sont des wrappers autour de l’implémentation de l’API de chiffrement Windows (CAPI) d’un algorithme.
* `*Cng` les classes d’algorithme, telles que <xref:System.Security.Cryptography.ECDiffieHellmanCng> , sont des wrappers autour de l’implémentation CNG (Windows Cryptography Next Generation).
* `*Managed` les classes, telles que <xref:System.Security.Cryptography.AesManaged> , sont écrites entièrement dans du code managé. `*Managed` les implémentations ne sont pas certifiées par les normes FIPS (Federal Information Processing Standards) et peuvent être plus lentes que les `*CryptoServiceProvider` `*Cng` classes wrapper et.

Dans .NET Core et .NET 5 et versions ultérieures, toutes les classes d’implémentation ( `*CryptoServiceProvider` , `*Managed` et `*Cng` ) sont des wrappers pour les algorithmes du système d’exploitation. Si les algorithmes de système d’exploitation sont certifiés FIPS, .NET utilise des algorithmes certifiés FIPS. Pour plus d’informations, consultez la page [chiffrement multiplateforme](cross-platform-cryptography.md).

Dans la plupart des cas, vous n’avez pas besoin de référencer directement une classe d’implémentation d’algorithme, telle que `AesCryptoServiceProvider` . Les méthodes et les propriétés dont vous avez généralement besoin sont sur la classe d’algorithme de base, par exemple `Aes` . Créez une instance d’une classe d’implémentation par défaut en utilisant une méthode de fabrique sur la classe d’algorithme de base et reportez-vous à la classe d’algorithme de base. Par exemple, consultez la ligne de code en surbrillance dans l’exemple suivant :

:::code language="csharp" source="snippets/encrypting-data/csharp/aes-encrypt.cs" highlight="16":::
:::code language="vb" source="snippets/encrypting-data/vb/aes-encrypt.vb" highlight="12":::

## <a name="cryptographic-configuration"></a>Configuration du chiffrement

La configuration du chiffrement vous permet de résoudre une implémentation spécifique d’un algorithme en un nom d’algorithme, ce qui permet l’extensibilité des classes de chiffrement .NET. Vous pouvez ajouter votre propre implémentation logicielle ou matérielle d'un algorithme, puis la mapper vers le nom d'algorithme de votre choix. Si un algorithme n'est pas spécifié dans le fichier de configuration, les paramètres par défaut sont utilisés.

## <a name="choosing-an-algorithm"></a>Choix d'un algorithme

Vous pouvez sélectionner un algorithme pour différentes raisons. Par exemple, pour l'intégrité ou la confidentialité des données, ou pour générer une clé. Les algorithmes symétriques et les algorithmes de hachage sont conçus pour protéger les données pour des raisons d'intégrité (empêcher leur modification) ou pour des raisons de confidentialité (empêcher leur affichage). Les algorithmes de hachage sont principalement utilisés pour l'intégrité des données.

Voici une liste des algorithmes recommandés pour chaque application :

- Confidentialité des données :
  - <xref:System.Security.Cryptography.Aes>
- Intégrité des données :
  - <xref:System.Security.Cryptography.HMACSHA256>
  - <xref:System.Security.Cryptography.HMACSHA512>
- Signature numérique :
  - <xref:System.Security.Cryptography.ECDsa>
  - <xref:System.Security.Cryptography.RSA>
- Échange de clés :
  - <xref:System.Security.Cryptography.ECDiffieHellman>
  - <xref:System.Security.Cryptography.RSA>
- Génération de nombres aléatoires :
  - <xref:System.Security.Cryptography.RandomNumberGenerator.Create%2A?displayProperty=nameWithType>
- Génération d'une clé à partir d'un mot de passe :
  - <xref:System.Security.Cryptography.Rfc2898DeriveBytes>

## <a name="see-also"></a>Voir aussi

- [services de chiffrement](cryptographic-services.md)
- [Chiffrement multiplateforme](cross-platform-cryptography.md)
- [Protection des données ASP.NET Core](/aspnet/core/security/data-protection/introduction)
