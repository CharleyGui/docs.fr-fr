---
ms.openlocfilehash: 3e4a5936bbac4e77efc5f7e68b55ddf49bae5d43
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614483"
---
### <a name="path-colon-checks-are-stricter"></a><span data-ttu-id="c78cc-101">Les vérifications des signes deux-points dans les chemins d’accès sont plus strictes</span><span class="sxs-lookup"><span data-stu-id="c78cc-101">Path colon checks are stricter</span></span>

#### <a name="details"></a><span data-ttu-id="c78cc-102">Détails</span><span class="sxs-lookup"><span data-stu-id="c78cc-102">Details</span></span>

<span data-ttu-id="c78cc-103">Dans .NET Framework 4.6.2, un certain nombre de modifications ont été apportées pour prendre en charge les chemins d’accès précédemment non pris en charge (à la fois en termes de longueur et de format).</span><span class="sxs-lookup"><span data-stu-id="c78cc-103">In .NET Framework 4.6.2, a number of changes were made to support previously unsupported paths (both in length and format).</span></span> <span data-ttu-id="c78cc-104">Les vérifications de bonne syntaxe de séparateur de lecteur (le signe deux-points) ont été rendues plus correctes, ce qui a eu pour effet secondaire de bloquer certains chemins d’URI dans quelques API de sélection de chemin d’accès, où ils étaient tolérés.</span><span class="sxs-lookup"><span data-stu-id="c78cc-104">Checks for proper drive separator (colon) syntax were made more correct, which had the side effect of blocking some URI paths in a few select Path APIs where they used to be tolerated.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="c78cc-105">Suggestion</span><span class="sxs-lookup"><span data-stu-id="c78cc-105">Suggestion</span></span>

<span data-ttu-id="c78cc-106">Si vous passez un URI à des API affectées, modifiez d’abord la chaîne pour en faire un chemin valide.</span><span class="sxs-lookup"><span data-stu-id="c78cc-106">If passing a URI to affected APIs, modify the string to be a legal path first.</span></span><ul><li><span data-ttu-id="c78cc-107">Supprimez manuellement le schéma des URL (par exemple, supprimez `file://` des URL)</span><span class="sxs-lookup"><span data-stu-id="c78cc-107">Remove the scheme from URLs manually (e.g. remove `file://` from URLs)</span></span>

- <span data-ttu-id="c78cc-108">Passez l’URI de la classe <xref:System.Uri> et utilisez <xref:System.Uri.LocalPath></span><span class="sxs-lookup"><span data-stu-id="c78cc-108">Pass the URI to the <xref:System.Uri> class and use <xref:System.Uri.LocalPath></span></span>

<span data-ttu-id="c78cc-109">Vous pouvez également refuser la nouvelle normalisation de chemin en définissant le commutateur AppContext `Switch.System.IO.UseLegacyPathHandling` sur true.</span><span class="sxs-lookup"><span data-stu-id="c78cc-109">Alternatively, you can opt out of the new path normalization by setting the `Switch.System.IO.UseLegacyPathHandling` AppContext switch to true.</span></span>

| <span data-ttu-id="c78cc-110">Nom</span><span class="sxs-lookup"><span data-stu-id="c78cc-110">Name</span></span>    | <span data-ttu-id="c78cc-111">Valeur</span><span class="sxs-lookup"><span data-stu-id="c78cc-111">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="c78cc-112">Étendue</span><span class="sxs-lookup"><span data-stu-id="c78cc-112">Scope</span></span>   | <span data-ttu-id="c78cc-113">Edge</span><span class="sxs-lookup"><span data-stu-id="c78cc-113">Edge</span></span>        |
| <span data-ttu-id="c78cc-114">Version</span><span class="sxs-lookup"><span data-stu-id="c78cc-114">Version</span></span> | <span data-ttu-id="c78cc-115">4.6.2</span><span class="sxs-lookup"><span data-stu-id="c78cc-115">4.6.2</span></span>       |
| <span data-ttu-id="c78cc-116">Type</span><span class="sxs-lookup"><span data-stu-id="c78cc-116">Type</span></span>    | <span data-ttu-id="c78cc-117">Reciblage</span><span class="sxs-lookup"><span data-stu-id="c78cc-117">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="c78cc-118">API affectées</span><span class="sxs-lookup"><span data-stu-id="c78cc-118">Affected APIs</span></span>

- <xref:System.IO.Path.GetDirectoryName(System.String)?displayProperty=nameWithType>
- <xref:System.IO.Path.GetPathRoot(System.String)?displayProperty=nameWithType>
