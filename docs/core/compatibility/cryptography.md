---
title: Modifications avec rupture de chiffrement
description: Répertorie les modifications avec rupture liées au chiffrement dans .NET Core.
ms.date: 04/22/2020
ms.openlocfilehash: 667d983fc6f2592c2169f97d328cd7947c8bcc81
ms.sourcegitcommit: 1274a1a4a4c7e2eaf56b38da76ef7cec789726ef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/28/2020
ms.locfileid: "91406143"
---
# <a name="cryptography-breaking-changes"></a>Modifications avec rupture de chiffrement

Les modifications avec rupture suivantes sont documentées sur cette page :

| Modification avec rupture | Version introduite |
| - | :-: |
| [API System. Security. Cryptography non prises en charge sur le webassembly éblouissant](#systemsecuritycryptography-apis-not-supported-on-blazor-webassembly) | 5.0 |
| [System. Security. Cryptography. OID est fonctionnellement init-only](#systemsecuritycryptographyoid-is-functionally-init-only) | 5.0 |
| [La syntaxe de début de certificat approuvé n’est plus prise en charge sur Linux](#begin-trusted-certificate-syntax-no-longer-supported-for-root-certificates-on-linux) | 3.0 |
| [La valeur par défaut de EnvelopedCms est le chiffrement AES-256](#envelopedcms-defaults-to-aes-256-encryption) | 3.0 |
| [La taille minimale de la génération de la clé de RSAOpenSsl a augmenté](#minimum-size-for-rsaopenssl-key-generation-has-increased) | 3.0 |
| [.NET Core 3,0 préfère OpenSSL 1.1. x à OpenSSL 1.0. x](#net-core-30-prefers-openssl-11x-to-openssl-10x) | 3.0 |
| [CryptoStream. dispose transforme le bloc final uniquement lors de l’écriture](#cryptostreamdispose-transforms-final-block-only-when-writing) | 3.0 |
| [Le paramètre booléen de SignedCms. ComputeSignature est respecté](#boolean-parameter-of-signedcmscomputesignature-is-respected) | 2.1 |

## <a name="net-50"></a>.NET 5,0

[!INCLUDE[Cryptography APIs not supported on Blazor WebAssembly](~/includes/core-changes/cryptography/5.0/cryptography-apis-not-supported-on-blazor-webassembly.md)]

***

[!INCLUDE [cryptography-oid-init-only](../../../includes/core-changes/cryptography/5.0/cryptography-oid-init-only.md)]

***

## <a name="net-core-30"></a>.NET Core 3.0

[!INCLUDE [begin-trusted-cert-linux](~/includes/core-changes/cryptography/3.0/begin-trusted-cert-linux.md)]

***

[!INCLUDE[EnvelopedCms defaults to AES-256 encryption](~/includes/core-changes/cryptography/3.0/envelopedcms-defaults-to-aes256.md)]

***

[!INCLUDE[Minimum size for RSAOpenSsl key generation has increased](~/includes/core-changes/cryptography/3.0/minimum-rsaopenssl-key-size-change.md)]

***

[!INCLUDE[.NET Core 3.0 prefers OpenSSL 1.1.x to OpenSSL 1.0.x](~/includes/core-changes/cryptography/3.0/net-core-3-0-prefers-openssl-1-1-x.md)]

***

[!INCLUDE [CryptoStream.Dispose transforms final block only when writing](~/includes/core-changes/cryptography/3.0/cryptography-cryptostream-dispose-final-block-write.md)]

***

## <a name="net-core-21"></a>.NET Core 2.1

[!INCLUDE [Boolean parameter of SignedCms.ComputeSignature is respected](~/includes/core-changes/cryptography/2.1/compute-signature-silent-parameter.md)]

***
