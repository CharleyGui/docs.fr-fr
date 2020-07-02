---
ms.openlocfilehash: 9c3c0bf7fbd8d45eba84eaa8634fd2d834195702
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617204"
---
### <a name="systemuri-parsing-adheres-to-rfc-3987"></a><span data-ttu-id="d1e13-101">L’analyse des objets System.Uri respecte la norme RFC 3987</span><span class="sxs-lookup"><span data-stu-id="d1e13-101">System.Uri parsing adheres to RFC 3987</span></span>

#### <a name="details"></a><span data-ttu-id="d1e13-102">Détails</span><span class="sxs-lookup"><span data-stu-id="d1e13-102">Details</span></span>

<span data-ttu-id="d1e13-103">L’analyse URI a changé à différents niveaux dans .NET Framework 4.5.</span><span class="sxs-lookup"><span data-stu-id="d1e13-103">URI parsing has changed in several ways in .NET Framework 4.5.</span></span> <span data-ttu-id="d1e13-104">Notez, cependant, que ces changements affectent uniquement le code qui cible .NET Framework 4.5.</span><span class="sxs-lookup"><span data-stu-id="d1e13-104">Note, however, that these changes only affect code targeting .NET Framework 4.5.</span></span> <span data-ttu-id="d1e13-105">Si un fichier binaire cible .NET Framework 4.0, l’ancien comportement est appliqué.</span><span class="sxs-lookup"><span data-stu-id="d1e13-105">If a binary targets .NET Framework 4.0, the old behavior will be observed.</span></span> <span data-ttu-id="d1e13-106">Les changements appliqués à l’analyse URI dans .NET Framework 4.5 sont les suivants :</span><span class="sxs-lookup"><span data-stu-id="d1e13-106">Changes to URI parsing in .NET Framework 4.5 include:</span></span>

- <span data-ttu-id="d1e13-107">L’analyse des URI effectue la normalisation et la vérification des caractères selon les dernières règles IRI de la norme RFC 3987.</span><span class="sxs-lookup"><span data-stu-id="d1e13-107">URI parsing will perform normalization and character checking according to the latest IRI rules in RFC 3987.</span></span>
- <span data-ttu-id="d1e13-108">Le formulaire C de normalisation Unicode n’est appliqué que sur la partie hôte de l’URI.</span><span class="sxs-lookup"><span data-stu-id="d1e13-108">Unicode normalization form C will only be performed on the host portion of the URI.</span></span>
- <span data-ttu-id="d1e13-109">Les URI mailto: non valides génèrent désormais une exception.</span><span class="sxs-lookup"><span data-stu-id="d1e13-109">Invalid mailto: URIs will now cause an exception.</span></span>
- <span data-ttu-id="d1e13-110">Les espaces à la fin d’un segment de chemin sont désormais conservés.</span><span class="sxs-lookup"><span data-stu-id="d1e13-110">Trailing dots at the end of a path segment are now preserved.</span></span>
- <span data-ttu-id="d1e13-111">Les URI `file://` n’échappent pas le caractère `?`.</span><span class="sxs-lookup"><span data-stu-id="d1e13-111">`file://` URIs do not escape the `?` character.</span></span>
- <span data-ttu-id="d1e13-112">Les caractères de contrôle Unicode allant de `U+0080` à `U+009F` ne sont pas pris en charge.</span><span class="sxs-lookup"><span data-stu-id="d1e13-112">Unicode control characters `U+0080` through `U+009F` are not supported.</span></span>
- <span data-ttu-id="d1e13-113">Les virgules `,` ou `%2c` ne sont pas automatiquement sans séquence d’échappement.</span><span class="sxs-lookup"><span data-stu-id="d1e13-113">Comma characters `,` or `%2c` are not automatically unescaped.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="d1e13-114">Suggestion</span><span class="sxs-lookup"><span data-stu-id="d1e13-114">Suggestion</span></span>

<span data-ttu-id="d1e13-115">Si l’ancienne sémantique d’analyse URI de .NET Framework 4.0 est nécessaire (et c’est souvent le cas), elle peut être utilisée en ciblant .NET Framework 4.0.</span><span class="sxs-lookup"><span data-stu-id="d1e13-115">If the old .NET Framework 4.0 URI parsing semantics are necessary (they often aren't), they can be used by targeting .NET Framework 4.0.</span></span> <span data-ttu-id="d1e13-116">Pour cela, utilisez un <xref:System.Runtime.Versioning.TargetFrameworkAttribute?displayProperty=fullName> sur l’assembly ou modifiez les propriétés du projet dans l’interface utilisateur du système de projet de Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="d1e13-116">This can be accomplished by using a <xref:System.Runtime.Versioning.TargetFrameworkAttribute?displayProperty=fullName> on the assembly, or through Visual Studio's project system UI in the 'project properties' page.</span></span>

| <span data-ttu-id="d1e13-117">Nom</span><span class="sxs-lookup"><span data-stu-id="d1e13-117">Name</span></span>    | <span data-ttu-id="d1e13-118">Valeur</span><span class="sxs-lookup"><span data-stu-id="d1e13-118">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="d1e13-119">Étendue</span><span class="sxs-lookup"><span data-stu-id="d1e13-119">Scope</span></span>   | <span data-ttu-id="d1e13-120">Majeure</span><span class="sxs-lookup"><span data-stu-id="d1e13-120">Major</span></span>       |
| <span data-ttu-id="d1e13-121">Version</span><span class="sxs-lookup"><span data-stu-id="d1e13-121">Version</span></span> | <span data-ttu-id="d1e13-122">4,5</span><span class="sxs-lookup"><span data-stu-id="d1e13-122">4.5</span></span>         |
| <span data-ttu-id="d1e13-123">Type</span><span class="sxs-lookup"><span data-stu-id="d1e13-123">Type</span></span>    | <span data-ttu-id="d1e13-124">Reciblage</span><span class="sxs-lookup"><span data-stu-id="d1e13-124">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="d1e13-125">API affectées</span><span class="sxs-lookup"><span data-stu-id="d1e13-125">Affected APIs</span></span>

- <xref:System.Uri.%23ctor(System.String)>
- <xref:System.Uri.%23ctor(System.String,System.Boolean)>
- <xref:System.Uri.%23ctor(System.String,System.UriKind)>
- <xref:System.Uri.%23ctor(System.Uri,System.String)>
- <xref:System.Uri.TryCreate(System.String,System.UriKind,System.Uri@)?displayProperty=nameWithType>
- <xref:System.Uri.TryCreate(System.Uri,System.String,System.Uri@)?displayProperty=nameWithType>
- <xref:System.Uri.TryCreate(System.Uri,System.Uri,System.Uri@)?displayProperty=nameWithType>
