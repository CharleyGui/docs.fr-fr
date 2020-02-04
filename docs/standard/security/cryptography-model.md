---
title: Modèle de chiffrement de .NET Framework
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- cryptography [.NET Framework], model
- encryption [.NET Framework], model
ms.assetid: 12fecad4-fbab-432a-bade-2f05976a2971
ms.openlocfilehash: 964c63e01a6b09e63e305e9a10dca46e62c18648
ms.sourcegitcommit: feb42222f1430ca7b8115ae45e7a38fc4a1ba623
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/02/2020
ms.locfileid: "76965956"
---
# <a name="net-framework-cryptography-model"></a>Modèle de chiffrement de .NET Framework

.NET Framework fournit des implémentations de nombreux algorithmes de chiffrement standard. Ces algorithmes sont faciles à utiliser et leurs propriétés par défaut sont les plus sûres possible. En outre, le modèle de chiffrement .NET Framework de l'héritage d'objets, de la conception orientée flux et de la configuration, est très extensible.

## <a name="object-inheritance"></a>Héritage d'objets

Le système de sécurité .NET Framework implémente un modèle extensible d’héritage de classes dérivées. Cette hiérarchie se présente comme suit :

- Classe de type algorithme, telle que <xref:System.Security.Cryptography.SymmetricAlgorithm>, <xref:System.Security.Cryptography.AsymmetricAlgorithm> ou <xref:System.Security.Cryptography.HashAlgorithm>. Ce niveau est abstrait.

- Classe d'algorithme qui hérite d'une classe de type algorithme, par exemple, <xref:System.Security.Cryptography.Aes>, <xref:System.Security.Cryptography.RC2> ou <xref:System.Security.Cryptography.ECDiffieHellman>. Ce niveau est abstrait.

- Implémentation d'une classe d'algorithme qui hérite d'une classe d'algorithme, par exemple, <xref:System.Security.Cryptography.AesManaged>, <xref:System.Security.Cryptography.RC2CryptoServiceProvider> ou <xref:System.Security.Cryptography.ECDiffieHellmanCng>. Ce niveau est totalement implémenté.

À l’aide de ce modèle de classes dérivées, il est facile d’ajouter un nouvel algorithme ou la nouvelle implémentation d’un algorithme existant. Par exemple, pour créer un algorithme de clé publique, vous devez hériter de la classe <xref:System.Security.Cryptography.AsymmetricAlgorithm>. Pour créer une nouvelle implémentation d'un algorithme spécifique, vous devez créer une classe non abstraite dérivée de cet algorithme.

## <a name="how-algorithms-are-implemented-in-the-net-framework"></a>Comment les algorithmes sont implémentés dans .NET Framework

Prenez comme exemple d'implémentation les algorithmes symétriques. La base de tous les algorithmes symétriques est <xref:System.Security.Cryptography.SymmetricAlgorithm>, qui est hérité par les algorithmes suivants :

* <xref:System.Security.Cryptography.Aes>
* <xref:System.Security.Cryptography.DES>
* <xref:System.Security.Cryptography.RC2>
* <xref:System.Security.Cryptography.Rijndael>
* <xref:System.Security.Cryptography.TripleDES>

<xref:System.Security.Cryptography.Aes> est hérité par deux classes : <xref:System.Security.Cryptography.AesCryptoServiceProvider> et <xref:System.Security.Cryptography.AesManaged>. La classe <xref:System.Security.Cryptography.AesCryptoServiceProvider> est un wrapper pour l'implémentation de l'API de chiffrement Windows (CAPI) d'AES. La classe <xref:System.Security.Cryptography.AesManaged> est écrite entièrement en code managé. Il existe également l'implémentation Cryptography Next Generation (CNG), en plus des implémentations CAPI et managées. <xref:System.Security.Cryptography.ECDiffieHellmanCng> est un exemple d'algorithme CNG. Les algorithmes CNG sont disponibles sur Windows Vista et versions ultérieures.

Vous pouvez choisir l'implémentation qui vous convient le mieux.  Les implémentations managées sont disponibles sur toutes les plateformes qui prennent en charge .NET Framework.  Les implémentations CAPI sont disponibles sur les anciens systèmes d'exploitation et ne sont plus développées. L'implémentation CNG est la plus récente et c'est elle qui fait l'objet des derniers développements en date. Toutefois, les implémentations managées ne sont pas certifiées par les normes FIPS et peuvent être plus lentes que les classes wrapper.

## <a name="stream-design"></a>Conception orientée flux

Le Common Language Runtime utilise une conception orientée flux pour implémenter les algorithmes symétriques et les algorithmes de hachage. La base de cette conception est la classe <xref:System.Security.Cryptography.CryptoStream> qui dérive de la classe <xref:System.IO.Stream>. Les objets de chiffrement basés sur les flux prennent en charge une seule interface standard (`CryptoStream`) pour la gestion du transfert des données de l'objet. Comme tous les objets sont créés à l'aide d'une interface standard, vous pouvez chaîner plusieurs objets (par exemple, un objet de hachage suivi d'un objet de chiffrement), ainsi qu'effectuer plusieurs opérations sur les données sans avoir besoin de stockage intermédiaire. Le modèle basé sur les flux vous permet également de créer des objets à partir d'objets plus petits. Par exemple, un algorithme combinant hachage et chiffrement peut être affiché comme un objet de flux unique, même si cet objet a été créé à partir d'un ensemble d'objets de flux.

## <a name="cryptographic-configuration"></a>Configuration du chiffrement

La configuration du chiffrement vous permet de résoudre une implémentation d'un algorithme en un nom d'algorithme. De cette façon, les classes de chiffrement .NET Framework peuvent être étendues. Vous pouvez ajouter votre propre implémentation logicielle ou matérielle d'un algorithme, puis la mapper vers le nom d'algorithme de votre choix. Si un algorithme n'est pas spécifié dans le fichier de configuration, les paramètres par défaut sont utilisés. Pour plus d’informations sur la configuration de chiffrement, consultez [Configuration des classes de chiffrement](../../../docs/framework/configure-apps/configure-cryptography-classes.md).

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
  - <xref:System.Security.Cryptography.RNGCryptoServiceProvider>
- Génération d'une clé à partir d'un mot de passe :
  - <xref:System.Security.Cryptography.Rfc2898DeriveBytes>

## <a name="see-also"></a>Voir aussi

- [Cryptographic Services](../../../docs/standard/security/cryptographic-services.md)
- [Appliquer les protocoles de chiffrement, les algorithmes et le code source en C, par Bruce Schneier](https://www.schneier.com/books/applied_cryptography/)
