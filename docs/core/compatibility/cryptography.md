---
title: Modifications avec rupture de chiffrement
description: Répertorie les modifications avec rupture liées au chiffrement dans .NET Core.
ms.date: 04/22/2020
ms.openlocfilehash: f7d580938fb7620728b8ff7f67412c9f5bbbb6c3
ms.sourcegitcommit: 8bfeb5930ca48b2ee6053f16082dcaf24d46d221
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/18/2020
ms.locfileid: "88557999"
---
# <a name="cryptography-breaking-changes"></a><span data-ttu-id="8e24c-103">Modifications avec rupture de chiffrement</span><span class="sxs-lookup"><span data-stu-id="8e24c-103">Cryptography breaking changes</span></span>

<span data-ttu-id="8e24c-104">Les modifications avec rupture suivantes sont documentées sur cette page :</span><span class="sxs-lookup"><span data-stu-id="8e24c-104">The following breaking changes are documented on this page:</span></span>

| <span data-ttu-id="8e24c-105">Modification avec rupture</span><span class="sxs-lookup"><span data-stu-id="8e24c-105">Breaking change</span></span> | <span data-ttu-id="8e24c-106">Version introduite</span><span class="sxs-lookup"><span data-stu-id="8e24c-106">Version introduced</span></span> |
| - | :-: |
| [<span data-ttu-id="8e24c-107">System. Security. Cryptography. OID est fonctionnellement init-only</span><span class="sxs-lookup"><span data-stu-id="8e24c-107">System.Security.Cryptography.Oid is functionally init-only</span></span>](#systemsecuritycryptographyoid-is-functionally-init-only) | <span data-ttu-id="8e24c-108">5.0</span><span class="sxs-lookup"><span data-stu-id="8e24c-108">5.0</span></span> |
| [<span data-ttu-id="8e24c-109">La syntaxe de début de certificat approuvé n’est plus prise en charge sur Linux</span><span class="sxs-lookup"><span data-stu-id="8e24c-109">BEGIN TRUSTED CERTIFICATE syntax no longer supported on Linux</span></span>](#begin-trusted-certificate-syntax-no-longer-supported-for-root-certificates-on-linux) | <span data-ttu-id="8e24c-110">3.0</span><span class="sxs-lookup"><span data-stu-id="8e24c-110">3.0</span></span> |
| [<span data-ttu-id="8e24c-111">La valeur par défaut de EnvelopedCms est le chiffrement AES-256</span><span class="sxs-lookup"><span data-stu-id="8e24c-111">EnvelopedCms defaults to AES-256 encryption</span></span>](#envelopedcms-defaults-to-aes-256-encryption) | <span data-ttu-id="8e24c-112">3.0</span><span class="sxs-lookup"><span data-stu-id="8e24c-112">3.0</span></span> |
| [<span data-ttu-id="8e24c-113">La taille minimale de la génération de la clé de RSAOpenSsl a augmenté</span><span class="sxs-lookup"><span data-stu-id="8e24c-113">Minimum size for RSAOpenSsl key generation has increased</span></span>](#minimum-size-for-rsaopenssl-key-generation-has-increased) | <span data-ttu-id="8e24c-114">3.0</span><span class="sxs-lookup"><span data-stu-id="8e24c-114">3.0</span></span> |
| [<span data-ttu-id="8e24c-115">.NET Core 3,0 préfère OpenSSL 1.1. x à OpenSSL 1.0. x</span><span class="sxs-lookup"><span data-stu-id="8e24c-115">.NET Core 3.0 prefers OpenSSL 1.1.x to OpenSSL 1.0.x</span></span>](#net-core-30-prefers-openssl-11x-to-openssl-10x) | <span data-ttu-id="8e24c-116">3.0</span><span class="sxs-lookup"><span data-stu-id="8e24c-116">3.0</span></span> |
| [<span data-ttu-id="8e24c-117">Le paramètre booléen de SignedCms. ComputeSignature est respecté</span><span class="sxs-lookup"><span data-stu-id="8e24c-117">Boolean parameter of SignedCms.ComputeSignature is respected</span></span>](#boolean-parameter-of-signedcmscomputesignature-is-respected) | <span data-ttu-id="8e24c-118">2.1</span><span class="sxs-lookup"><span data-stu-id="8e24c-118">2.1</span></span> |

## <a name="net-50"></a><span data-ttu-id="8e24c-119">.NET 5,0</span><span class="sxs-lookup"><span data-stu-id="8e24c-119">.NET 5.0</span></span>

[!INCLUDE [cryptography-oid-init-only](../../../includes/core-changes/cryptography/5.0/cryptography-oid-init-only.md)]

***

## <a name="net-core-30"></a><span data-ttu-id="8e24c-120">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="8e24c-120">.NET Core 3.0</span></span>

[!INCLUDE [begin-trusted-cert-linux](~/includes/core-changes/cryptography/3.0/begin-trusted-cert-linux.md)]

***

[!INCLUDE[EnvelopedCms defaults to AES-256 encryption](~/includes/core-changes/cryptography/3.0/envelopedcms-defaults-to-aes256.md)]

***

[!INCLUDE[Minimum size for RSAOpenSsl key generation has increased](~/includes/core-changes/cryptography/3.0/minimum-rsaopenssl-key-size-change.md)]

***

[!INCLUDE[.NET Core 3.0 prefers OpenSSL 1.1.x to OpenSSL 1.0.x](~/includes/core-changes/cryptography/3.0/net-core-3-0-prefers-openssl-1-1-x.md)]

***

## <a name="net-core-21"></a><span data-ttu-id="8e24c-121">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="8e24c-121">.NET Core 2.1</span></span>

[!INCLUDE [Boolean parameter of SignedCms.ComputeSignature is respected](~/includes/core-changes/cryptography/2.1/compute-signature-silent-parameter.md)]

***
