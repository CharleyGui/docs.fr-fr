---
title: 'Modification avec rupture : les API System. Security. Cryptography ne sont pas prises en charge sur le webassembly éblouissant'
description: Découvrez les modifications avec rupture dans .NET 5,0 où les API de chiffrement lèvent une exception lorsqu’elles sont exécutées sur un navigateur.
ms.date: 09/16/2020
ms.openlocfilehash: ec10fa777e91f641b5582378830536a0cfa8dd72
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95760887"
---
# <a name="systemsecuritycryptography-apis-not-supported-on-blazor-webassembly"></a><span data-ttu-id="12b53-103">API System. Security. Cryptography non prises en charge sur le webassembly éblouissant</span><span class="sxs-lookup"><span data-stu-id="12b53-103">System.Security.Cryptography APIs not supported on Blazor WebAssembly</span></span>

<span data-ttu-id="12b53-104"><xref:System.Security.Cryptography> Les API lèvent une <xref:System.PlatformNotSupportedException> au moment de l’exécution lorsqu’elles sont exécutées sur un navigateur.</span><span class="sxs-lookup"><span data-stu-id="12b53-104"><xref:System.Security.Cryptography> APIs throw a <xref:System.PlatformNotSupportedException> at run time when run on a browser.</span></span>

## <a name="change-description"></a><span data-ttu-id="12b53-105">Description de la modification</span><span class="sxs-lookup"><span data-stu-id="12b53-105">Change description</span></span>

<span data-ttu-id="12b53-106">Dans les versions précédentes de .NET, la plupart des <xref:System.Security.Cryptography> API ne sont pas disponibles pour les applications Webassembly éblouissantes.</span><span class="sxs-lookup"><span data-stu-id="12b53-106">In previous .NET versions, most of the <xref:System.Security.Cryptography> APIs aren't available to Blazor WebAssembly apps.</span></span> <span data-ttu-id="12b53-107">À compter de .NET 5,0, les applications de l’assembly Web éblouissant ciblent la surface d’exposition complète de l’API .NET 5. Toutefois, toutes les API .NET 5 ne sont pas prises en charge en raison des contraintes du bac à sable (sandbox).</span><span class="sxs-lookup"><span data-stu-id="12b53-107">Starting in .NET 5.0, Blazor WebAssembly apps target the full .NET 5 API surface area, however, not all .NET 5 APIs are supported due to browser sandbox constraints.</span></span> <span data-ttu-id="12b53-108">Dans .NET 5,0 et versions ultérieures, les API non prises en charge <xref:System.Security.Cryptography> lèvent une <xref:System.PlatformNotSupportedException> lorsqu’elles s’exécutent sur webassembly.</span><span class="sxs-lookup"><span data-stu-id="12b53-108">In .NET 5.0 and later versions, the unsupported <xref:System.Security.Cryptography> APIs throw a <xref:System.PlatformNotSupportedException> when running on WebAssembly.</span></span>

> [!TIP]
> <span data-ttu-id="12b53-109">L' [Analyseur de compatibilité](../../code-analysis/5.0/ca1416-platform-compatibility-analyzer.md) de la plateforme signale tous les appels aux API affectées lorsque vous générez un projet qui prend en charge la plateforme du navigateur.</span><span class="sxs-lookup"><span data-stu-id="12b53-109">The [Platform compatibility analyzer](../../code-analysis/5.0/ca1416-platform-compatibility-analyzer.md) will flag any calls to the affected APIs when you build a project that supports the browser platform.</span></span> <span data-ttu-id="12b53-110">Cet analyseur s’exécute par défaut dans les applications .NET 5,0 et ultérieures.</span><span class="sxs-lookup"><span data-stu-id="12b53-110">This analyzer runs by default in .NET 5.0 and later apps.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="12b53-111">Motif de modification</span><span class="sxs-lookup"><span data-stu-id="12b53-111">Reason for change</span></span>

<span data-ttu-id="12b53-112">Microsoft n’est pas en mesure d’envoyer OpenSSL comme dépendance dans la configuration de l’assembly éblouissant.</span><span class="sxs-lookup"><span data-stu-id="12b53-112">Microsoft is unable to ship OpenSSL as a dependency in the Blazor WebAssembly configuration.</span></span> <span data-ttu-id="12b53-113">Nous avons tenté de contourner ce contournement en tentant de s’intégrer à l’API du navigateur `SubtleCrypto` .</span><span class="sxs-lookup"><span data-stu-id="12b53-113">We attempted to work around this by trying to integrate with the browser's `SubtleCrypto` API.</span></span> <span data-ttu-id="12b53-114">Malheureusement, il nécessitait des modifications d’API importantes qui rendaientait trop difficile l’intégration.</span><span class="sxs-lookup"><span data-stu-id="12b53-114">Unfortunately, it required significant API changes that made it too hard to integrate.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="12b53-115">Version introduite</span><span class="sxs-lookup"><span data-stu-id="12b53-115">Version introduced</span></span>

<span data-ttu-id="12b53-116">5.0</span><span class="sxs-lookup"><span data-stu-id="12b53-116">5.0</span></span>

## <a name="recommended-action"></a><span data-ttu-id="12b53-117">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="12b53-117">Recommended action</span></span>

<span data-ttu-id="12b53-118">Il n’existe aucune solution de contournement pour l’instant.</span><span class="sxs-lookup"><span data-stu-id="12b53-118">There are no good workarounds to suggest at this time.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="12b53-119">API affectées</span><span class="sxs-lookup"><span data-stu-id="12b53-119">Affected APIs</span></span>

<span data-ttu-id="12b53-120">Toutes les <xref:System.Security.Cryptography?displayProperty=fullName> API sauf les suivantes :</span><span class="sxs-lookup"><span data-stu-id="12b53-120">All <xref:System.Security.Cryptography?displayProperty=fullName> APIs except the following:</span></span>

- `System.Security.Cryptography.RandomNumberGenerator`
- `System.Security.Cryptography.IncrementalHash`
- `System.Security.Cryptography.SHA1`
- `System.Security.Cryptography.SHA256`
- `System.Security.Cryptography.SHA384`
- `System.Security.Cryptography.SHA512`
- `System.Security.Cryptography.SHA1Managed`
- `System.Security.Cryptography.SHA256Managed`
- `System.Security.Cryptography.SHA384Managed`
- `System.Security.Cryptography.SHA512Managed`

<!--

### Affected APIs

- `T:System.Security.Cryptography`

### Category

- ASP.NET Core
- Cryptography

-->
