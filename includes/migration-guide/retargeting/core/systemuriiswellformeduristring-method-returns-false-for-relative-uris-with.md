---
ms.openlocfilehash: f7dcf9c4c3dc7ea536ddc847769a1a30f1298bb2
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617216"
---
### <a name="systemuriiswellformeduristring-method-returns-false-for-relative-uris-with-a-colon-char-in-first-segment"></a><span data-ttu-id="f1609-101">La méthode System.Uri.IsWellFormedUriString retourne la valeur false pour les URI relatifs comprenant un caractère deux-points dans le premier segment</span><span class="sxs-lookup"><span data-stu-id="f1609-101">System.Uri.IsWellFormedUriString method returns false for relative URIs with a colon char in first segment</span></span>

#### <a name="details"></a><span data-ttu-id="f1609-102">Détails</span><span class="sxs-lookup"><span data-stu-id="f1609-102">Details</span></span>

<span data-ttu-id="f1609-103">À compter de .NET Framework 4.5, <xref:System.Uri.IsWellFormedUriString(System.String,System.UriKind)> traite les URI relatifs comprenant un `:` dans leur premier segment comme n’étant pas bien formés.</span><span class="sxs-lookup"><span data-stu-id="f1609-103">Beginning with the .NET Framework 4.5, <xref:System.Uri.IsWellFormedUriString(System.String,System.UriKind)> will treat relative URIs with a `:` in their first segment as not well formed.</span></span> <span data-ttu-id="f1609-104">Il s’agit là d’un changement par rapport au comportement de <xref:System.Uri.IsWellFormedUriString(System.String,System.UriKind)?displayProperty=fullName> dans .NET Framework 4.0 qui a été apporté pour qu’il soit conforme à la norme RFC 3986.</span><span class="sxs-lookup"><span data-stu-id="f1609-104">This is a change from <xref:System.Uri.IsWellFormedUriString(System.String,System.UriKind)?displayProperty=fullName> behavior in the .NET Framework 4.0 that was made to conform to RFC3986.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="f1609-105">Suggestion</span><span class="sxs-lookup"><span data-stu-id="f1609-105">Suggestion</span></span>

<span data-ttu-id="f1609-106">Ce changement (comme de nombreux autres changements relatifs aux URI) affecte uniquement les applications qui ciblent .NET Framework 4.5 (ou les versions ultérieures).</span><span class="sxs-lookup"><span data-stu-id="f1609-106">This change (like many other URI changes) will only affect applications targeting the .NET Framework 4.5 (or later).</span></span> <span data-ttu-id="f1609-107">Pour continuer à utiliser l’ancien comportement, ciblez l’application sur .NET Framework 4.0.</span><span class="sxs-lookup"><span data-stu-id="f1609-107">To keep using the old behavior, target the app against the .NET Framework 4.0.</span></span> <span data-ttu-id="f1609-108">Si l’ancien comportement est souhaitable, vous pouvez également analyser les URI avant d’appeler <xref:System.Uri.IsWellFormedUriString(System.String,System.UriKind)?displayProperty=fullName> pour rechercher les caractères `:` que vous voulez supprimer à des fins de validation.</span><span class="sxs-lookup"><span data-stu-id="f1609-108">Alternatively, scan URI's prior to calling <xref:System.Uri.IsWellFormedUriString(System.String,System.UriKind)?displayProperty=fullName> looking for `:` characters that you may want to remove for validation purposes, if the old behavior is desirable.</span></span>

| <span data-ttu-id="f1609-109">Nom</span><span class="sxs-lookup"><span data-stu-id="f1609-109">Name</span></span>    | <span data-ttu-id="f1609-110">Valeur</span><span class="sxs-lookup"><span data-stu-id="f1609-110">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="f1609-111">Étendue</span><span class="sxs-lookup"><span data-stu-id="f1609-111">Scope</span></span>   | <span data-ttu-id="f1609-112">Secondaire</span><span class="sxs-lookup"><span data-stu-id="f1609-112">Minor</span></span>       |
| <span data-ttu-id="f1609-113">Version</span><span class="sxs-lookup"><span data-stu-id="f1609-113">Version</span></span> | <span data-ttu-id="f1609-114">4,5</span><span class="sxs-lookup"><span data-stu-id="f1609-114">4.5</span></span>         |
| <span data-ttu-id="f1609-115">Type</span><span class="sxs-lookup"><span data-stu-id="f1609-115">Type</span></span>    | <span data-ttu-id="f1609-116">Reciblage</span><span class="sxs-lookup"><span data-stu-id="f1609-116">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="f1609-117">API affectées</span><span class="sxs-lookup"><span data-stu-id="f1609-117">Affected APIs</span></span>

- <xref:System.Uri.IsWellFormedUriString(System.String,System.UriKind)?displayProperty=nameWithType>
