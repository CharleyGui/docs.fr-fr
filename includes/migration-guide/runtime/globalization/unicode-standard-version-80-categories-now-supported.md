---
ms.openlocfilehash: f389a9e9bcf4ac1777db66731a085d74889c4a98
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497924"
---
### <a name="unicode-standard-version-80-categories-now-supported"></a><span data-ttu-id="75258-101">Catégories de version Unicode standard 8.0 maintenant prises en charge</span><span class="sxs-lookup"><span data-stu-id="75258-101">Unicode standard version 8.0 categories now supported</span></span>

#### <a name="details"></a><span data-ttu-id="75258-102">Détails</span><span class="sxs-lookup"><span data-stu-id="75258-102">Details</span></span>

<span data-ttu-id="75258-103">Dans .NET Framework 4.6.2, les données Unicode ont été mises à niveau de la version Unicode Standard 6.3 vers la version 8.0.</span><span class="sxs-lookup"><span data-stu-id="75258-103">In .NET Framework 4.6.2, Unicode data has been upgraded from Unicode Standard version 6.3 to version 8.0.</span></span>  <span data-ttu-id="75258-104">Quand vous demandez des catégories de caractères Unicode dans .NET Framework 4.6.2, certains résultats peuvent ne pas correspondre à ceux des versions précédentes du .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="75258-104">When requesting Unicode character categories in .NET Framework 4.6.2, some results might not match the results in previous .NET Framework versions.</span></span>  <span data-ttu-id="75258-105">Ce changement affecte principalement les syllabes Cherokee et voyelles diacritiques nouveau taï-lue ainsi que les accents toniques.</span><span class="sxs-lookup"><span data-stu-id="75258-105">This change mostly affects Cherokee syllables and New Tai Lue vowels signs and tone marks.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="75258-106">Suggestion</span><span class="sxs-lookup"><span data-stu-id="75258-106">Suggestion</span></span>

<span data-ttu-id="75258-107">Passez en revue le code et supprimez ou modifiez la logique qui varie selon les catégories de caractères Unicode codées en dur.</span><span class="sxs-lookup"><span data-stu-id="75258-107">Review code and remove/change logic that depends on hard-coded Unicode character categories.</span></span>

| <span data-ttu-id="75258-108">Name</span><span class="sxs-lookup"><span data-stu-id="75258-108">Name</span></span>    | <span data-ttu-id="75258-109">Valeur</span><span class="sxs-lookup"><span data-stu-id="75258-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="75258-110">Étendue</span><span class="sxs-lookup"><span data-stu-id="75258-110">Scope</span></span>   |<span data-ttu-id="75258-111">Secondaire</span><span class="sxs-lookup"><span data-stu-id="75258-111">Minor</span></span>|
|<span data-ttu-id="75258-112">Version</span><span class="sxs-lookup"><span data-stu-id="75258-112">Version</span></span>|<span data-ttu-id="75258-113">4.6.2</span><span class="sxs-lookup"><span data-stu-id="75258-113">4.6.2</span></span>|
|<span data-ttu-id="75258-114">Type</span><span class="sxs-lookup"><span data-stu-id="75258-114">Type</span></span>|<span data-ttu-id="75258-115">Runtime</span><span class="sxs-lookup"><span data-stu-id="75258-115">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="75258-116">API affectées</span><span class="sxs-lookup"><span data-stu-id="75258-116">Affected APIs</span></span>

- <xref:System.Char.GetUnicodeCategory(System.Char)?displayProperty=nameWithType>
- <xref:System.Globalization.CharUnicodeInfo.GetUnicodeCategory(System.Char)?displayProperty=nameWithType>
- <xref:System.Globalization.CharUnicodeInfo.GetUnicodeCategory(System.String,System.Int32)?displayProperty=nameWithType>

<!--

#### Affected APIs

- `M:System.Char.GetUnicodeCategory(System.Char)`
- `M:System.Globalization.CharUnicodeInfo.GetUnicodeCategory(System.Char)`
- `M:System.Globalization.CharUnicodeInfo.GetUnicodeCategory(System.String,System.Int32)`

-->
