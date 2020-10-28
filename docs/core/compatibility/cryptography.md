---
title: Modifications avec rupture de chiffrement
description: Répertorie les modifications avec rupture liées au chiffrement dans .NET Core.
ms.date: 04/22/2020
ms.openlocfilehash: b755876624a7709cfe08b5993655e78be9f8e1f2
ms.sourcegitcommit: 4a938327bad8b2e20cabd0f46a9dc50882596f13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/28/2020
ms.locfileid: "92888609"
---
# <a name="cryptography-breaking-changes"></a><span data-ttu-id="e76f4-103">Modifications avec rupture de chiffrement</span><span class="sxs-lookup"><span data-stu-id="e76f4-103">Cryptography breaking changes</span></span>

<span data-ttu-id="e76f4-104">Les modifications avec rupture suivantes sont documentées sur cette page :</span><span class="sxs-lookup"><span data-stu-id="e76f4-104">The following breaking changes are documented on this page:</span></span>

| <span data-ttu-id="e76f4-105">Modification avec rupture</span><span class="sxs-lookup"><span data-stu-id="e76f4-105">Breaking change</span></span> | <span data-ttu-id="e76f4-106">Version introduite</span><span class="sxs-lookup"><span data-stu-id="e76f4-106">Version introduced</span></span> |
| - | :-: |
| [<span data-ttu-id="e76f4-107">Valeur FeedbackSize par défaut pour les instances créées par TripleDES. Create Changed</span><span class="sxs-lookup"><span data-stu-id="e76f4-107">Default FeedbackSize value for instances created by TripleDES.Create changed</span></span>](#default-feedbacksize-value-for-instances-created-by-tripledescreate-changed) | <span data-ttu-id="e76f4-108">5.0</span><span class="sxs-lookup"><span data-stu-id="e76f4-108">5.0</span></span> |
| [<span data-ttu-id="e76f4-109">L’instanciation des implémentations par défaut des abstractions de chiffrement n’est pas prise en charge</span><span class="sxs-lookup"><span data-stu-id="e76f4-109">Instantiating default implementations of cryptographic abstractions is not supported</span></span>](#instantiating-default-implementations-of-cryptographic-abstractions-is-not-supported) | <span data-ttu-id="e76f4-110">5.0</span><span class="sxs-lookup"><span data-stu-id="e76f4-110">5.0</span></span> |
| [<span data-ttu-id="e76f4-111">Suites de chiffrement TLS par défaut pour .NET sur Linux</span><span class="sxs-lookup"><span data-stu-id="e76f4-111">Default TLS cipher suites for .NET on Linux</span></span>](#default-tls-cipher-suites-for-net-on-linux) | <span data-ttu-id="e76f4-112">5.0</span><span class="sxs-lookup"><span data-stu-id="e76f4-112">5.0</span></span> |
| [<span data-ttu-id="e76f4-113">API System. Security. Cryptography non prises en charge sur le webassembly éblouissant</span><span class="sxs-lookup"><span data-stu-id="e76f4-113">System.Security.Cryptography APIs not supported on Blazor WebAssembly</span></span>](#systemsecuritycryptography-apis-not-supported-on-blazor-webassembly) | <span data-ttu-id="e76f4-114">5.0</span><span class="sxs-lookup"><span data-stu-id="e76f4-114">5.0</span></span> |
| [<span data-ttu-id="e76f4-115">System. Security. Cryptography. OID est fonctionnellement init-only</span><span class="sxs-lookup"><span data-stu-id="e76f4-115">System.Security.Cryptography.Oid is functionally init-only</span></span>](#systemsecuritycryptographyoid-is-functionally-init-only) | <span data-ttu-id="e76f4-116">5.0</span><span class="sxs-lookup"><span data-stu-id="e76f4-116">5.0</span></span> |
| [<span data-ttu-id="e76f4-117">La syntaxe de début de certificat approuvé n’est plus prise en charge sur Linux</span><span class="sxs-lookup"><span data-stu-id="e76f4-117">BEGIN TRUSTED CERTIFICATE syntax no longer supported on Linux</span></span>](#begin-trusted-certificate-syntax-no-longer-supported-for-root-certificates-on-linux) | <span data-ttu-id="e76f4-118">3.0</span><span class="sxs-lookup"><span data-stu-id="e76f4-118">3.0</span></span> |
| [<span data-ttu-id="e76f4-119">La valeur par défaut de EnvelopedCms est le chiffrement AES-256</span><span class="sxs-lookup"><span data-stu-id="e76f4-119">EnvelopedCms defaults to AES-256 encryption</span></span>](#envelopedcms-defaults-to-aes-256-encryption) | <span data-ttu-id="e76f4-120">3.0</span><span class="sxs-lookup"><span data-stu-id="e76f4-120">3.0</span></span> |
| [<span data-ttu-id="e76f4-121">La taille minimale de la génération de la clé de RSAOpenSsl a augmenté</span><span class="sxs-lookup"><span data-stu-id="e76f4-121">Minimum size for RSAOpenSsl key generation has increased</span></span>](#minimum-size-for-rsaopenssl-key-generation-has-increased) | <span data-ttu-id="e76f4-122">3.0</span><span class="sxs-lookup"><span data-stu-id="e76f4-122">3.0</span></span> |
| [<span data-ttu-id="e76f4-123">.NET Core 3,0 préfère OpenSSL 1.1. x à OpenSSL 1.0. x</span><span class="sxs-lookup"><span data-stu-id="e76f4-123">.NET Core 3.0 prefers OpenSSL 1.1.x to OpenSSL 1.0.x</span></span>](#net-core-30-prefers-openssl-11x-to-openssl-10x) | <span data-ttu-id="e76f4-124">3.0</span><span class="sxs-lookup"><span data-stu-id="e76f4-124">3.0</span></span> |
| [<span data-ttu-id="e76f4-125">CryptoStream. dispose transforme le bloc final uniquement lors de l’écriture</span><span class="sxs-lookup"><span data-stu-id="e76f4-125">CryptoStream.Dispose transforms final block only when writing</span></span>](#cryptostreamdispose-transforms-final-block-only-when-writing) | <span data-ttu-id="e76f4-126">3.0</span><span class="sxs-lookup"><span data-stu-id="e76f4-126">3.0</span></span> |
| [<span data-ttu-id="e76f4-127">Le paramètre booléen de SignedCms. ComputeSignature est respecté</span><span class="sxs-lookup"><span data-stu-id="e76f4-127">Boolean parameter of SignedCms.ComputeSignature is respected</span></span>](#boolean-parameter-of-signedcmscomputesignature-is-respected) | <span data-ttu-id="e76f4-128">2.1</span><span class="sxs-lookup"><span data-stu-id="e76f4-128">2.1</span></span> |

## <a name="net-50"></a><span data-ttu-id="e76f4-129">.NET 5,0</span><span class="sxs-lookup"><span data-stu-id="e76f4-129">.NET 5.0</span></span>

[!INCLUDE [tripledes-default-feedback-size-change](../../../includes/core-changes/cryptography/5.0/tripledes-default-feedback-size-change.md)]

***

[!INCLUDE [instantiating-default-implementations-of-cryptographic-abstractions-not-supported](../../../includes/core-changes/cryptography/5.0/instantiating-default-implementations-of-cryptographic-abstractions-not-supported.md)]

<span data-ttu-id="e76f4-130">\*\*_</span><span class="sxs-lookup"><span data-stu-id="e76f4-130">\*\*_</span></span>

[!INCLUDE [default-cipher-suites-for-tls-on-linux](../../../includes/core-changes/cryptography/5.0/default-cipher-suites-for-tls-on-linux.md)]

_*_

[!INCLUDE[Cryptography APIs not supported on Blazor WebAssembly](~/includes/core-changes/cryptography/5.0/cryptography-apis-not-supported-on-blazor-webassembly.md)]

_*_

[!INCLUDE [cryptography-oid-init-only](../../../includes/core-changes/cryptography/5.0/cryptography-oid-init-only.md)]

_*_

## <a name="net-core-30"></a><span data-ttu-id="e76f4-131">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="e76f4-131">.NET Core 3.0</span></span>

[!INCLUDE [begin-trusted-cert-linux](~/includes/core-changes/cryptography/3.0/begin-trusted-cert-linux.md)]

_*_

[!INCLUDE[EnvelopedCms defaults to AES-256 encryption](~/includes/core-changes/cryptography/3.0/envelopedcms-defaults-to-aes256.md)]

_*_

[!INCLUDE[Minimum size for RSAOpenSsl key generation has increased](~/includes/core-changes/cryptography/3.0/minimum-rsaopenssl-key-size-change.md)]

_*_

[!INCLUDE[.NET Core 3.0 prefers OpenSSL 1.1.x to OpenSSL 1.0.x](~/includes/core-changes/cryptography/3.0/net-core-3-0-prefers-openssl-1-1-x.md)]

_*_

[!INCLUDE [CryptoStream.Dispose transforms final block only when writing](~/includes/core-changes/cryptography/3.0/cryptography-cryptostream-dispose-final-block-write.md)]

_*_

## <a name="net-core-21"></a><span data-ttu-id="e76f4-132">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="e76f4-132">.NET Core 2.1</span></span>

[!INCLUDE [Boolean parameter of SignedCms.ComputeSignature is respected](~/includes/core-changes/cryptography/2.1/compute-signature-silent-parameter.md)]

<span data-ttu-id="e76f4-133">_\*\*</span><span class="sxs-lookup"><span data-stu-id="e76f4-133">_\*\*</span></span>
