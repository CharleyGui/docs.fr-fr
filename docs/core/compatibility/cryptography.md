---
title: Modifications avec rupture de chiffrement
description: Répertorie les modifications avec rupture liées au chiffrement dans .NET Core.
ms.date: 02/10/2020
ms.openlocfilehash: c25eefa8e3ee01ed7a1df4ec4aa9225f2c347a4d
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77449213"
---
# <a name="cryptography-breaking-changes"></a>Modifications avec rupture de chiffrement

Les modifications avec rupture suivantes sont documentées sur cette page :

| Modification avec rupture | Version introduite |
| - | :-: |
| [La valeur par défaut de EnvelopedCms est le chiffrement AES-256](#envelopedcms-defaults-to-aes-256-encryption) | 3.0 |
| [La taille minimale de la génération de la clé de RSAOpenSsl a augmenté](#minimum-size-for-rsaopenssl-key-generation-has-increased) | 3.0 |
| [.NET Core 3,0 préfère OpenSSL 1.1. x à OpenSSL 1.0. x](#net-core-30-prefers-openssl-11x-to-openssl-10x) | 3.0 |
| [Meilleure validation d’argument dans le constructeur Pkcs8PrivateKeyInfo](#better-argument-validation-in-the-pkcs8privatekeyinfo-constructor) | 3.0 |
| [Le paramètre booléen de SignedCms. ComputeSignature est respecté](#boolean-parameter-of-signedcmscomputesignature-is-respected) | 2.1 |

## <a name="net-core-30"></a>.NET Core 3.0

[!INCLUDE[EnvelopedCms defaults to AES-256 encryption](~/includes/core-changes/cryptography/3.0/envelopedcms-defaults-to-aes256.md)]

***

[!INCLUDE[Minimum size for RSAOpenSsl key generation has increased](~/includes/core-changes/cryptography/3.0/minimum-rsaopenssl-key-size-change.md)]

***

[!INCLUDE[.NET Core 3.0 prefers OpenSSL 1.1.x to OpenSSL 1.0.x](~/includes/core-changes/cryptography/3.0/net-core-3-0-prefers-openssl-1-1-x.md)]

***

[!INCLUDE[Better argument validation in the Pkcs8PrivateKeyInfo constructor](~/includes/core-changes/cryptography/3.0/better-argument-validation-in-pkcs8privatekeyinfo-ctor.md)]

***

## <a name="net-core-21"></a>.NET Core 2.1

[!INCLUDE [Boolean parameter of SignedCms.ComputeSignature is respected](~/includes/core-changes/cryptography/2.1/compute-signature-silent-parameter.md)]

***
