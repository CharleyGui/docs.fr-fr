---
ms.openlocfilehash: a20fad5f9c95e59c14ffd91f4921cf8bfab443cd
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621074"
---
### <a name="unicode-standard-version-80-categories-now-supported"></a><span data-ttu-id="b85f8-101">Catégories de version Unicode standard 8.0 maintenant prises en charge</span><span class="sxs-lookup"><span data-stu-id="b85f8-101">Unicode standard version 8.0 categories now supported</span></span>

#### <a name="details"></a><span data-ttu-id="b85f8-102">Détails</span><span class="sxs-lookup"><span data-stu-id="b85f8-102">Details</span></span>

<span data-ttu-id="b85f8-103">Dans .NET Framework 4.6.2, les données Unicode ont été mises à niveau de la version Unicode Standard 6.3 vers la version 8.0.</span><span class="sxs-lookup"><span data-stu-id="b85f8-103">In .NET Framework 4.6.2, Unicode data has been upgraded from Unicode Standard version 6.3 to version 8.0.</span></span>  <span data-ttu-id="b85f8-104">Quand vous demandez des catégories de caractères Unicode dans .NET Framework 4.6.2, certains résultats peuvent ne pas correspondre à ceux des versions précédentes du .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="b85f8-104">When requesting Unicode character categories in .NET Framework 4.6.2, some results might not match the results in previous .NET Framework versions.</span></span>  <span data-ttu-id="b85f8-105">Ce changement affecte principalement les syllabes Cherokee et voyelles diacritiques nouveau taï-lue ainsi que les accents toniques.</span><span class="sxs-lookup"><span data-stu-id="b85f8-105">This change mostly affects Cherokee syllables and New Tai Lue vowels signs and tone marks.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="b85f8-106">Suggestion</span><span class="sxs-lookup"><span data-stu-id="b85f8-106">Suggestion</span></span>

<span data-ttu-id="b85f8-107">Passez en revue le code et supprimez ou modifiez la logique qui varie selon les catégories de caractères Unicode codées en dur.</span><span class="sxs-lookup"><span data-stu-id="b85f8-107">Review code and remove/change logic that depends on hard-coded Unicode character categories.</span></span>

| <span data-ttu-id="b85f8-108">Nom</span><span class="sxs-lookup"><span data-stu-id="b85f8-108">Name</span></span>    | <span data-ttu-id="b85f8-109">Valeur</span><span class="sxs-lookup"><span data-stu-id="b85f8-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="b85f8-110">Étendue</span><span class="sxs-lookup"><span data-stu-id="b85f8-110">Scope</span></span>   |<span data-ttu-id="b85f8-111">Secondaire</span><span class="sxs-lookup"><span data-stu-id="b85f8-111">Minor</span></span>|
|<span data-ttu-id="b85f8-112">Version</span><span class="sxs-lookup"><span data-stu-id="b85f8-112">Version</span></span>|<span data-ttu-id="b85f8-113">4.6.2</span><span class="sxs-lookup"><span data-stu-id="b85f8-113">4.6.2</span></span>|
|<span data-ttu-id="b85f8-114">Type</span><span class="sxs-lookup"><span data-stu-id="b85f8-114">Type</span></span>|<span data-ttu-id="b85f8-115">Runtime</span><span class="sxs-lookup"><span data-stu-id="b85f8-115">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="b85f8-116">API affectées</span><span class="sxs-lookup"><span data-stu-id="b85f8-116">Affected APIs</span></span>

-<xref:System.Char.GetUnicodeCategory(System.Char)?displayProperty=nameWithType></li><li><xref:System.Globalization.CharUnicodeInfo.GetUnicodeCategory(System.Char)?displayProperty=nameWithType></li><li><xref:System.Globalization.CharUnicodeInfo.GetUnicodeCategory(System.String,System.Int32)?displayProperty=nameWithType></li></ul>|
