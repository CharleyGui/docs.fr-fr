---
title: 'Modification avec rupture : reconnaissance URI de chemins d’accès UNC sur UNIX'
description: Découvrez la modification avec rupture .NET 5,0 dans les bibliothèques .NET de base où la classe Uri reconnaît désormais les chaînes qui commencent par deux barres obliques comme chemins d’accès UNC sur UNIX.
ms.date: 11/01/2020
ms.openlocfilehash: 0d5d9cd8dd869f24e94d15724e5e16eaddf6ed47
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95760875"
---
# <a name="uri-recognition-of-unc-paths-on-unix"></a><span data-ttu-id="c8a97-103">Reconnaissance d’URI de chemins d’accès UNC sur UNIX</span><span class="sxs-lookup"><span data-stu-id="c8a97-103">Uri recognition of UNC paths on Unix</span></span>

<span data-ttu-id="c8a97-104">La <xref:System.Uri> classe reconnaît maintenant les chaînes qui commencent par deux barres obliques ( `//` ) en tant que chemins d’accès UNC (Universal Naming Convention) sur les systèmes d’exploitation UNIX.</span><span class="sxs-lookup"><span data-stu-id="c8a97-104">The <xref:System.Uri> class now recognizes strings that start with two forward slashes (`//`) as universal naming convention (UNC) paths on Unix operating systems.</span></span> <span data-ttu-id="c8a97-105">Cette modification rend le comportement de ces chaînes cohérent sur toutes les plateformes.</span><span class="sxs-lookup"><span data-stu-id="c8a97-105">This change makes the behavior for such strings consistent across all platforms.</span></span>

## <a name="change-description"></a><span data-ttu-id="c8a97-106">Description de la modification</span><span class="sxs-lookup"><span data-stu-id="c8a97-106">Change description</span></span>

<span data-ttu-id="c8a97-107">Dans les versions précédentes de .NET, la <xref:System.Uri> classe reconnaît les chaînes qui commencent par deux barres obliques, par exemple, `//contoso` sous la forme de chemins de fichiers absolus sur les systèmes d’exploitation UNIX.</span><span class="sxs-lookup"><span data-stu-id="c8a97-107">In previous versions of .NET, the <xref:System.Uri> class recognizes strings that start with two forward slashes, for example, `//contoso`, as absolute file paths on Unix operating systems.</span></span> <span data-ttu-id="c8a97-108">Toutefois, sous Windows, ces chaînes sont reconnues comme des chemins d’accès UNC.</span><span class="sxs-lookup"><span data-stu-id="c8a97-108">However, on Windows, such strings are recognized as UNC paths.</span></span>

<span data-ttu-id="c8a97-109">À compter de .NET 5,0, la <xref:System.Uri> classe reconnaît les chaînes qui commencent par deux barres obliques comme chemins d’accès UNC sur toutes les plateformes, y compris UNIX.</span><span class="sxs-lookup"><span data-stu-id="c8a97-109">Starting in .NET 5.0,  the <xref:System.Uri> class recognizes strings that start with two forward slashes as UNC paths on all platforms, including Unix.</span></span> <span data-ttu-id="c8a97-110">En outre, les propriétés se comportent selon la sémantique UNC :</span><span class="sxs-lookup"><span data-stu-id="c8a97-110">In addition, properties behave according to UNC semantics:</span></span>

- <span data-ttu-id="c8a97-111"><xref:System.Uri.IsUnc?displayProperty=nameWithType> retourne `true`.</span><span class="sxs-lookup"><span data-stu-id="c8a97-111"><xref:System.Uri.IsUnc?displayProperty=nameWithType> returns `true`.</span></span>
- <span data-ttu-id="c8a97-112">Les barres obliques inverses dans le chemin d’accès sont remplacées par des barres obliques.</span><span class="sxs-lookup"><span data-stu-id="c8a97-112">Backslashes in the path are replaced with forward slashes.</span></span> <span data-ttu-id="c8a97-113">Par exemple, `//first\second` devient `//first/second`.</span><span class="sxs-lookup"><span data-stu-id="c8a97-113">For example, `//first\second` becomes `//first/second`.</span></span>
- <span data-ttu-id="c8a97-114"><xref:System.Uri.LocalPath?displayProperty=nameWithType> n’encode pas les caractères en pourcentage.</span><span class="sxs-lookup"><span data-stu-id="c8a97-114"><xref:System.Uri.LocalPath?displayProperty=nameWithType> doesn't percent-encode characters.</span></span> <span data-ttu-id="c8a97-115">Par exemple, `//first/\uFFF0` n’est *pas* converti en `//first/%EF%BF%B0` .</span><span class="sxs-lookup"><span data-stu-id="c8a97-115">For example, `//first/\uFFF0` is *not* converted to `//first/%EF%BF%B0`.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="c8a97-116">Version introduite</span><span class="sxs-lookup"><span data-stu-id="c8a97-116">Version introduced</span></span>

<span data-ttu-id="c8a97-117">5.0</span><span class="sxs-lookup"><span data-stu-id="c8a97-117">5.0</span></span>

## <a name="recommended-action"></a><span data-ttu-id="c8a97-118">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="c8a97-118">Recommended action</span></span>

<span data-ttu-id="c8a97-119">Aucune action n’est requise de la part du développeur.</span><span class="sxs-lookup"><span data-stu-id="c8a97-119">No action is required on the part of the developer.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="c8a97-120">API affectées</span><span class="sxs-lookup"><span data-stu-id="c8a97-120">Affected APIs</span></span>

- <xref:System.Uri?displayProperty=fullName>

<!--

#### Category

Core .NET libraries

### Affected APIs

- `T:System.Uri`

-->
