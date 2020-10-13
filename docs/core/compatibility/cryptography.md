---
title: Modifications avec rupture de chiffrement
description: Répertorie les modifications avec rupture liées au chiffrement dans .NET Core.
ms.date: 04/22/2020
ms.openlocfilehash: c9405625cc4075c05468dc9b8502bf8c76587bad
ms.sourcegitcommit: e078b7540a8293ca1b604c9c0da1ff1506f0170b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/13/2020
ms.locfileid: "91997745"
---
# <a name="cryptography-breaking-changes"></a><span data-ttu-id="51f8d-103">Modifications avec rupture de chiffrement</span><span class="sxs-lookup"><span data-stu-id="51f8d-103">Cryptography breaking changes</span></span>

<span data-ttu-id="51f8d-104">Les modifications avec rupture suivantes sont documentées sur cette page :</span><span class="sxs-lookup"><span data-stu-id="51f8d-104">The following breaking changes are documented on this page:</span></span>

| <span data-ttu-id="51f8d-105">Modification avec rupture</span><span class="sxs-lookup"><span data-stu-id="51f8d-105">Breaking change</span></span> | <span data-ttu-id="51f8d-106">Version introduite</span><span class="sxs-lookup"><span data-stu-id="51f8d-106">Version introduced</span></span> |
| - | :-: |
| [<span data-ttu-id="51f8d-107">Suites de chiffrement TLS par défaut pour .NET sur Linux</span><span class="sxs-lookup"><span data-stu-id="51f8d-107">Default TLS cipher suites for .NET on Linux</span></span>](#default-tls-cipher-suites-for-net-on-linux) | <span data-ttu-id="51f8d-108">5.0</span><span class="sxs-lookup"><span data-stu-id="51f8d-108">5.0</span></span> |
| [<span data-ttu-id="51f8d-109">API System. Security. Cryptography non prises en charge sur le webassembly éblouissant</span><span class="sxs-lookup"><span data-stu-id="51f8d-109">System.Security.Cryptography APIs not supported on Blazor WebAssembly</span></span>](#systemsecuritycryptography-apis-not-supported-on-blazor-webassembly) | <span data-ttu-id="51f8d-110">5.0</span><span class="sxs-lookup"><span data-stu-id="51f8d-110">5.0</span></span> |
| [<span data-ttu-id="51f8d-111">System. Security. Cryptography. OID est fonctionnellement init-only</span><span class="sxs-lookup"><span data-stu-id="51f8d-111">System.Security.Cryptography.Oid is functionally init-only</span></span>](#systemsecuritycryptographyoid-is-functionally-init-only) | <span data-ttu-id="51f8d-112">5.0</span><span class="sxs-lookup"><span data-stu-id="51f8d-112">5.0</span></span> |
| [<span data-ttu-id="51f8d-113">La syntaxe de début de certificat approuvé n’est plus prise en charge sur Linux</span><span class="sxs-lookup"><span data-stu-id="51f8d-113">BEGIN TRUSTED CERTIFICATE syntax no longer supported on Linux</span></span>](#begin-trusted-certificate-syntax-no-longer-supported-for-root-certificates-on-linux) | <span data-ttu-id="51f8d-114">3.0</span><span class="sxs-lookup"><span data-stu-id="51f8d-114">3.0</span></span> |
| [<span data-ttu-id="51f8d-115">La valeur par défaut de EnvelopedCms est le chiffrement AES-256</span><span class="sxs-lookup"><span data-stu-id="51f8d-115">EnvelopedCms defaults to AES-256 encryption</span></span>](#envelopedcms-defaults-to-aes-256-encryption) | <span data-ttu-id="51f8d-116">3.0</span><span class="sxs-lookup"><span data-stu-id="51f8d-116">3.0</span></span> |
| [<span data-ttu-id="51f8d-117">La taille minimale de la génération de la clé de RSAOpenSsl a augmenté</span><span class="sxs-lookup"><span data-stu-id="51f8d-117">Minimum size for RSAOpenSsl key generation has increased</span></span>](#minimum-size-for-rsaopenssl-key-generation-has-increased) | <span data-ttu-id="51f8d-118">3.0</span><span class="sxs-lookup"><span data-stu-id="51f8d-118">3.0</span></span> |
| [<span data-ttu-id="51f8d-119">.NET Core 3,0 préfère OpenSSL 1.1. x à OpenSSL 1.0. x</span><span class="sxs-lookup"><span data-stu-id="51f8d-119">.NET Core 3.0 prefers OpenSSL 1.1.x to OpenSSL 1.0.x</span></span>](#net-core-30-prefers-openssl-11x-to-openssl-10x) | <span data-ttu-id="51f8d-120">3.0</span><span class="sxs-lookup"><span data-stu-id="51f8d-120">3.0</span></span> |
| [<span data-ttu-id="51f8d-121">CryptoStream. dispose transforme le bloc final uniquement lors de l’écriture</span><span class="sxs-lookup"><span data-stu-id="51f8d-121">CryptoStream.Dispose transforms final block only when writing</span></span>](#cryptostreamdispose-transforms-final-block-only-when-writing) | <span data-ttu-id="51f8d-122">3.0</span><span class="sxs-lookup"><span data-stu-id="51f8d-122">3.0</span></span> |
| [<span data-ttu-id="51f8d-123">Le paramètre booléen de SignedCms. ComputeSignature est respecté</span><span class="sxs-lookup"><span data-stu-id="51f8d-123">Boolean parameter of SignedCms.ComputeSignature is respected</span></span>](#boolean-parameter-of-signedcmscomputesignature-is-respected) | <span data-ttu-id="51f8d-124">2.1</span><span class="sxs-lookup"><span data-stu-id="51f8d-124">2.1</span></span> |

## <a name="net-50"></a><span data-ttu-id="51f8d-125">.NET 5,0</span><span class="sxs-lookup"><span data-stu-id="51f8d-125">.NET 5.0</span></span>

[!INCLUDE [default-cipher-suites-for-tls-on-linux](../../../includes/core-changes/cryptography/5.0/default-cipher-suites-for-tls-on-linux.md)]

***

[!INCLUDE[Cryptography APIs not supported on Blazor WebAssembly](~/includes/core-changes/cryptography/5.0/cryptography-apis-not-supported-on-blazor-webassembly.md)]

***

[!INCLUDE [cryptography-oid-init-only](../../../includes/core-changes/cryptography/5.0/cryptography-oid-init-only.md)]

***

## <a name="net-core-30"></a><span data-ttu-id="51f8d-126">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="51f8d-126">.NET Core 3.0</span></span>

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

## <a name="net-core-21"></a><span data-ttu-id="51f8d-127">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="51f8d-127">.NET Core 2.1</span></span>

[!INCLUDE [Boolean parameter of SignedCms.ComputeSignature is respected](~/includes/core-changes/cryptography/2.1/compute-signature-silent-parameter.md)]

***
