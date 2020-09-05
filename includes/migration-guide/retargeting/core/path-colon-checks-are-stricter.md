---
ms.openlocfilehash: 6af63c0a58a3273aa98fa70f22e3637b481806b4
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496888"
---
### <a name="path-colon-checks-are-stricter"></a><span data-ttu-id="2613d-101">Les vérifications des signes deux-points dans les chemins d’accès sont plus strictes</span><span class="sxs-lookup"><span data-stu-id="2613d-101">Path colon checks are stricter</span></span>

#### <a name="details"></a><span data-ttu-id="2613d-102">Détails</span><span class="sxs-lookup"><span data-stu-id="2613d-102">Details</span></span>

<span data-ttu-id="2613d-103">Dans .NET Framework 4.6.2, un certain nombre de modifications ont été apportées pour prendre en charge les chemins d’accès précédemment non pris en charge (à la fois en termes de longueur et de format).</span><span class="sxs-lookup"><span data-stu-id="2613d-103">In .NET Framework 4.6.2, a number of changes were made to support previously unsupported paths (both in length and format).</span></span> <span data-ttu-id="2613d-104">Vérifie que la syntaxe du séparateur de lecteur (deux-points) est devenue plus correcte, ce qui a eu pour effet secondaire de bloquer certains chemins d’accès URI dans quelques API de chemin d’accès SELECT où elles étaient précédemment tolérées.</span><span class="sxs-lookup"><span data-stu-id="2613d-104">Checks for proper drive separator (colon) syntax were made more correct, which had the side effect of blocking some URI paths in a few select Path APIs where they were previously tolerated.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="2613d-105">Suggestion</span><span class="sxs-lookup"><span data-stu-id="2613d-105">Suggestion</span></span>

<span data-ttu-id="2613d-106">Si vous passez un URI à des API affectées, modifiez d’abord la chaîne pour en faire un chemin valide.</span><span class="sxs-lookup"><span data-stu-id="2613d-106">If passing a URI to affected APIs, modify the string to be a legal path first.</span></span>

- <span data-ttu-id="2613d-107">Supprimer manuellement le schéma des URL (par exemple, supprimer `file://` des URL).</span><span class="sxs-lookup"><span data-stu-id="2613d-107">Remove the scheme from URLs manually (for example, remove `file://` from URLs).</span></span>

- <span data-ttu-id="2613d-108">Transmettez l’URI à la <xref:System.Uri> classe et utilisez <xref:System.Uri.LocalPath> .</span><span class="sxs-lookup"><span data-stu-id="2613d-108">Pass the URI to the <xref:System.Uri> class and use <xref:System.Uri.LocalPath>.</span></span>

<span data-ttu-id="2613d-109">Vous pouvez également désactiver la nouvelle normalisation de chemin d’accès en définissant le `Switch.System.IO.UseLegacyPathHandling` commutateur AppContext sur `true` .</span><span class="sxs-lookup"><span data-stu-id="2613d-109">Alternatively, you can opt out of the new path normalization by setting the `Switch.System.IO.UseLegacyPathHandling` AppContext switch to `true`.</span></span>

| <span data-ttu-id="2613d-110">Name</span><span class="sxs-lookup"><span data-stu-id="2613d-110">Name</span></span>    | <span data-ttu-id="2613d-111">Valeur</span><span class="sxs-lookup"><span data-stu-id="2613d-111">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="2613d-112">Étendue</span><span class="sxs-lookup"><span data-stu-id="2613d-112">Scope</span></span>   | <span data-ttu-id="2613d-113">Edge</span><span class="sxs-lookup"><span data-stu-id="2613d-113">Edge</span></span>        |
| <span data-ttu-id="2613d-114">Version</span><span class="sxs-lookup"><span data-stu-id="2613d-114">Version</span></span> | <span data-ttu-id="2613d-115">4.6.2</span><span class="sxs-lookup"><span data-stu-id="2613d-115">4.6.2</span></span>       |
| <span data-ttu-id="2613d-116">Type</span><span class="sxs-lookup"><span data-stu-id="2613d-116">Type</span></span>    | <span data-ttu-id="2613d-117">Reciblage</span><span class="sxs-lookup"><span data-stu-id="2613d-117">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="2613d-118">API affectées</span><span class="sxs-lookup"><span data-stu-id="2613d-118">Affected APIs</span></span>

- <xref:System.IO.Path.GetDirectoryName(System.String)?displayProperty=nameWithType>
- <xref:System.IO.Path.GetPathRoot(System.String)?displayProperty=nameWithType>
