---
title: Modifications avec rupture de chiffrement
description: Répertorie les modifications avec rupture liées au chiffrement dans .NET Core 2.1-3.0.
ms.date: 04/22/2020
ms.openlocfilehash: a4801bb4d5a859e2c8c2b536ee0597cb4db2f65d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95682651"
---
# <a name="cryptography-breaking-changes-for-net-core-21-30"></a>Modifications avec rupture de chiffrement pour .NET Core 2.1-3.0

Les modifications avec rupture suivantes sont documentées sur cette page :

| Modification avec rupture | Version introduite |
| - | :-: |
| [La syntaxe de début de certificat approuvé n’est plus prise en charge sur Linux](#begin-trusted-certificate-syntax-no-longer-supported-for-root-certificates-on-linux) | 3.0 |
| [La valeur par défaut de EnvelopedCms est le chiffrement AES-256](#envelopedcms-defaults-to-aes-256-encryption) | 3.0 |
| [La taille minimale de la génération de la clé de RSAOpenSsl a augmenté](#minimum-size-for-rsaopenssl-key-generation-has-increased) | 3.0 |
| [.NET Core 3,0 préfère OpenSSL 1.1. x à OpenSSL 1.0. x](#net-core-30-prefers-openssl-11x-to-openssl-10x) | 3.0 |
| [CryptoStream. dispose transforme le bloc final uniquement lors de l’écriture](#cryptostreamdispose-transforms-final-block-only-when-writing) | 3.0 |
| [Le paramètre booléen de SignedCms. ComputeSignature est respecté](#boolean-parameter-of-signedcmscomputesignature-is-respected) | 2.1 |

## <a name="net-core-30"></a>.NET Core 3.0

[!INCLUDE [begin-trusted-cert-linux](~/includes/core-changes/cryptography/3.0/begin-trusted-cert-linux.md)]

***

[!INCLUDE[EnvelopedCms defaults to AES-256 encryption](~/includes/core-changes/cryptography/3.0/envelopedcms-defaults-to-aes256.md)]

**_

[!INCLUDE[Minimum size for RSAOpenSsl key generation has increased](~/includes/core-changes/cryptography/3.0/minimum-rsaopenssl-key-size-change.md)]

_*_

[!INCLUDE[.NET Core 3.0 prefers OpenSSL 1.1.x to OpenSSL 1.0.x](~/includes/core-changes/cryptography/3.0/net-core-3-0-prefers-openssl-1-1-x.md)]

_*_

[!INCLUDE [CryptoStream.Dispose transforms final block only when writing](~/includes/core-changes/cryptography/3.0/cryptography-cryptostream-dispose-final-block-write.md)]

_*_

## <a name="net-core-21"></a>.NET Core 2.1

[!INCLUDE [Boolean parameter of SignedCms.ComputeSignature is respected](~/includes/core-changes/cryptography/2.1/compute-signature-silent-parameter.md)]

_**
