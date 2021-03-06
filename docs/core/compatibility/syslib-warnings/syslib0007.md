---
title: AVERTISSEMENT SYSLIB0007
description: En savoir plus sur les obsoletions qui génèrent un avertissement au moment de la compilation SYSLIB0007.
ms.topic: reference
ms.date: 10/20/2020
ms.openlocfilehash: c011340665a0c53172bf5b23e032d78301b3cd72
ms.sourcegitcommit: e301979e3049ce412d19b094c60ed95b316a8f8c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/16/2020
ms.locfileid: "97596524"
---
# <a name="syslib0007-default-implementations-of-cryptography-algorithms-not-supported"></a>SYSLIB0007 : les implémentations par défaut des algorithmes de chiffrement ne sont pas prises en charge

Le système de configuration de chiffrement dans .NET Framework n’autorise pas l’agilité de chiffrement appropriée et n’est pas présent dans .NET Core et .NET 5 +. . Les exigences de compatibilité descendante de .net empêchent également l’infrastructure de mettre à jour certaines API de chiffrement pour suivre les avancées du chiffrement. Par conséquent, les API suivantes sont marquées comme obsolètes, à partir de .NET 5,0. L’utilisation de ces API génère un avertissement `SYSLIB0007` au moment de la compilation.

- <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create?displayProperty=fullName>
- <xref:System.Security.Cryptography.HashAlgorithm.Create?displayProperty=fullName>
- <xref:System.Security.Cryptography.HMAC.Create?displayProperty=fullName>
- <xref:System.Security.Cryptography.KeyedHashAlgorithm.Create?displayProperty=fullName>
- <xref:System.Security.Cryptography.SymmetricAlgorithm.Create?displayProperty=fullName>

## <a name="workarounds"></a>Solutions de contournement

- La procédure recommandée consiste à remplacer les appels aux API désormais obsolètes par des appels aux méthodes de fabrique pour des algorithmes spécifiques, par exemple, <xref:System.Security.Cryptography.Aes.Create?displayProperty=nameWithType> . Cela vous donne un contrôle total sur les algorithmes qui sont instanciés.

- Si vous avez besoin de maintenir la compatibilité avec les charges utiles existantes générées par .NET Framework les applications qui utilisent les API désormais obsolètes, utilisez les remplacements suggérés dans le tableau suivant. La table fournit un mappage de .NET Framework les algorithmes par défaut à leurs équivalents .NET 5 +.

  | .NET Framework | .NET Core/.NET 5.0 + remplacement compatible | Notes |
  | - | - | - |
  | <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create?displayProperty=nameWithType> | <xref:System.Security.Cryptography.RSA.Create?displayProperty=nameWithType> | |
  | <xref:System.Security.Cryptography.HashAlgorithm.Create?displayProperty=nameWithType> | <xref:System.Security.Cryptography.SHA1.Create?displayProperty=nameWithType> | L’algorithme SHA-1 est considéré comme cassé. Envisagez d’utiliser un algorithme plus fort si possible. Pour plus d’informations, consultez votre conseiller en sécurité. |
  | <xref:System.Security.Cryptography.HMAC.Create?displayProperty=nameWithType> | <xref:System.Security.Cryptography.HMACSHA1.%23ctor> | L’algorithme HMACSHA1 est déconseillé pour la plupart des applications modernes. Envisagez d’utiliser un algorithme plus fort si possible. Pour plus d’informations, consultez votre conseiller en sécurité. |
  | <xref:System.Security.Cryptography.KeyedHashAlgorithm.Create?displayProperty=nameWithType> | <xref:System.Security.Cryptography.HMACSHA1.%23ctor> | L’algorithme HMACSHA1 est déconseillé pour la plupart des applications modernes. Envisagez d’utiliser un algorithme plus fort si possible. Pour plus d’informations, consultez votre conseiller en sécurité. |
  | <xref:System.Security.Cryptography.SymmetricAlgorithm.Create?displayProperty=nameWithType> | <xref:System.Security.Cryptography.Aes.Create?displayProperty=nameWithType> |

[!INCLUDE [suppress-syslib-warning](../../../../includes/suppress-syslib-warning.md)]

## <a name="see-also"></a>Voir aussi

- [L’instanciation des implémentations par défaut des abstractions de chiffrement n’est pas prise en charge](../cryptography/5.0/instantiating-default-implementations-of-cryptographic-abstractions-not-supported.md)
