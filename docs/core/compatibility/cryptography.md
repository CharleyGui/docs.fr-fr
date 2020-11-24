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
# <a name="cryptography-breaking-changes-for-net-core-21-30"></a><span data-ttu-id="87102-103">Modifications avec rupture de chiffrement pour .NET Core 2.1-3.0</span><span class="sxs-lookup"><span data-stu-id="87102-103">Cryptography breaking changes for .NET Core 2.1-3.0</span></span>

<span data-ttu-id="87102-104">Les modifications avec rupture suivantes sont documentées sur cette page :</span><span class="sxs-lookup"><span data-stu-id="87102-104">The following breaking changes are documented on this page:</span></span>

| <span data-ttu-id="87102-105">Modification avec rupture</span><span class="sxs-lookup"><span data-stu-id="87102-105">Breaking change</span></span> | <span data-ttu-id="87102-106">Version introduite</span><span class="sxs-lookup"><span data-stu-id="87102-106">Version introduced</span></span> |
| - | :-: |
| [<span data-ttu-id="87102-107">La syntaxe de début de certificat approuvé n’est plus prise en charge sur Linux</span><span class="sxs-lookup"><span data-stu-id="87102-107">BEGIN TRUSTED CERTIFICATE syntax no longer supported on Linux</span></span>](#begin-trusted-certificate-syntax-no-longer-supported-for-root-certificates-on-linux) | <span data-ttu-id="87102-108">3.0</span><span class="sxs-lookup"><span data-stu-id="87102-108">3.0</span></span> |
| [<span data-ttu-id="87102-109">La valeur par défaut de EnvelopedCms est le chiffrement AES-256</span><span class="sxs-lookup"><span data-stu-id="87102-109">EnvelopedCms defaults to AES-256 encryption</span></span>](#envelopedcms-defaults-to-aes-256-encryption) | <span data-ttu-id="87102-110">3.0</span><span class="sxs-lookup"><span data-stu-id="87102-110">3.0</span></span> |
| [<span data-ttu-id="87102-111">La taille minimale de la génération de la clé de RSAOpenSsl a augmenté</span><span class="sxs-lookup"><span data-stu-id="87102-111">Minimum size for RSAOpenSsl key generation has increased</span></span>](#minimum-size-for-rsaopenssl-key-generation-has-increased) | <span data-ttu-id="87102-112">3.0</span><span class="sxs-lookup"><span data-stu-id="87102-112">3.0</span></span> |
| [<span data-ttu-id="87102-113">.NET Core 3,0 préfère OpenSSL 1.1. x à OpenSSL 1.0. x</span><span class="sxs-lookup"><span data-stu-id="87102-113">.NET Core 3.0 prefers OpenSSL 1.1.x to OpenSSL 1.0.x</span></span>](#net-core-30-prefers-openssl-11x-to-openssl-10x) | <span data-ttu-id="87102-114">3.0</span><span class="sxs-lookup"><span data-stu-id="87102-114">3.0</span></span> |
| [<span data-ttu-id="87102-115">CryptoStream. dispose transforme le bloc final uniquement lors de l’écriture</span><span class="sxs-lookup"><span data-stu-id="87102-115">CryptoStream.Dispose transforms final block only when writing</span></span>](#cryptostreamdispose-transforms-final-block-only-when-writing) | <span data-ttu-id="87102-116">3.0</span><span class="sxs-lookup"><span data-stu-id="87102-116">3.0</span></span> |
| [<span data-ttu-id="87102-117">Le paramètre booléen de SignedCms. ComputeSignature est respecté</span><span class="sxs-lookup"><span data-stu-id="87102-117">Boolean parameter of SignedCms.ComputeSignature is respected</span></span>](#boolean-parameter-of-signedcmscomputesignature-is-respected) | <span data-ttu-id="87102-118">2.1</span><span class="sxs-lookup"><span data-stu-id="87102-118">2.1</span></span> |

## <a name="net-core-30"></a><span data-ttu-id="87102-119">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="87102-119">.NET Core 3.0</span></span>

[!INCLUDE [begin-trusted-cert-linux](~/includes/core-changes/cryptography/3.0/begin-trusted-cert-linux.md)]

***

[!INCLUDE[EnvelopedCms defaults to AES-256 encryption](~/includes/core-changes/cryptography/3.0/envelopedcms-defaults-to-aes256.md)]

<span data-ttu-id="87102-120">\*\*_</span><span class="sxs-lookup"><span data-stu-id="87102-120">\*\*_</span></span>

[!INCLUDE[Minimum size for RSAOpenSsl key generation has increased](~/includes/core-changes/cryptography/3.0/minimum-rsaopenssl-key-size-change.md)]

_*_

[!INCLUDE[.NET Core 3.0 prefers OpenSSL 1.1.x to OpenSSL 1.0.x](~/includes/core-changes/cryptography/3.0/net-core-3-0-prefers-openssl-1-1-x.md)]

_*_

[!INCLUDE [CryptoStream.Dispose transforms final block only when writing](~/includes/core-changes/cryptography/3.0/cryptography-cryptostream-dispose-final-block-write.md)]

_*_

## <a name="net-core-21"></a><span data-ttu-id="87102-121">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="87102-121">.NET Core 2.1</span></span>

[!INCLUDE [Boolean parameter of SignedCms.ComputeSignature is respected](~/includes/core-changes/cryptography/2.1/compute-signature-silent-parameter.md)]

<span data-ttu-id="87102-122">_\*\*</span><span class="sxs-lookup"><span data-stu-id="87102-122">_\*\*</span></span>
