---
ms.openlocfilehash: efa0efaf40e2e432d477f1659d7bde3abc98241d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "67857517"
---
### <a name="unicode-standard-version-80-categories-now-supported"></a><span data-ttu-id="02323-101">Catégories de version Unicode standard 8.0 maintenant prises en charge</span><span class="sxs-lookup"><span data-stu-id="02323-101">Unicode standard version 8.0 categories now supported</span></span>

|   |   |
|---|---|
|<span data-ttu-id="02323-102">Détails</span><span class="sxs-lookup"><span data-stu-id="02323-102">Details</span></span>|<span data-ttu-id="02323-103">Dans .NET Framework 4.6.2, les données Unicode ont été mises à niveau de la version Unicode Standard 6.3 vers la version 8.0.</span><span class="sxs-lookup"><span data-stu-id="02323-103">In .NET Framework 4.6.2, Unicode data has been upgraded from Unicode Standard version 6.3 to version 8.0.</span></span>  <span data-ttu-id="02323-104">Quand vous demandez des catégories de caractères Unicode dans .NET Framework 4.6.2, certains résultats peuvent ne pas correspondre à ceux des versions précédentes du .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="02323-104">When requesting Unicode character categories in .NET Framework 4.6.2, some results might not match the results in previous .NET Framework versions.</span></span>  <span data-ttu-id="02323-105">Ce changement affecte principalement les syllabes Cherokee et voyelles diacritiques nouveau taï-lue ainsi que les accents toniques.</span><span class="sxs-lookup"><span data-stu-id="02323-105">This change mostly affects Cherokee syllables and New Tai Lue vowels signs and tone marks.</span></span>|
|<span data-ttu-id="02323-106">Suggestion</span><span class="sxs-lookup"><span data-stu-id="02323-106">Suggestion</span></span>|<span data-ttu-id="02323-107">Passez en revue le code et supprimez ou modifiez la logique qui varie selon les catégories de caractères Unicode codées en dur.</span><span class="sxs-lookup"><span data-stu-id="02323-107">Review code and remove/change logic that depends on hard-coded Unicode character categories.</span></span>|
|<span data-ttu-id="02323-108">Étendue</span><span class="sxs-lookup"><span data-stu-id="02323-108">Scope</span></span>|<span data-ttu-id="02323-109">Secondaire</span><span class="sxs-lookup"><span data-stu-id="02323-109">Minor</span></span>|
|<span data-ttu-id="02323-110">Version</span><span class="sxs-lookup"><span data-stu-id="02323-110">Version</span></span>|<span data-ttu-id="02323-111">4.6.2</span><span class="sxs-lookup"><span data-stu-id="02323-111">4.6.2</span></span>|
|<span data-ttu-id="02323-112">Type</span><span class="sxs-lookup"><span data-stu-id="02323-112">Type</span></span>|<span data-ttu-id="02323-113">Runtime</span><span class="sxs-lookup"><span data-stu-id="02323-113">Runtime</span></span>|
|<span data-ttu-id="02323-114">API affectées</span><span class="sxs-lookup"><span data-stu-id="02323-114">Affected APIs</span></span>|<ul><li><xref:System.Char.GetUnicodeCategory(System.Char)?displayProperty=nameWithType></li><li><xref:System.Globalization.CharUnicodeInfo.GetUnicodeCategory(System.Char)?displayProperty=nameWithType></li><li><xref:System.Globalization.CharUnicodeInfo.GetUnicodeCategory(System.String,System.Int32)?displayProperty=nameWithType></li></ul>|
