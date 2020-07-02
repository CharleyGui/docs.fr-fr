---
ms.openlocfilehash: 0bd90b3d479a7e0897aaf78b7718ae156a4a239f
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619949"
---
### <a name="assemblies-compiled-with-regexcompiletoassembly-breaks-between-40-and-45"></a><span data-ttu-id="14103-101">Les assemblys compilés avec Regex.CompileToAssembly sont rompus entre 4.0 et 4.5</span><span class="sxs-lookup"><span data-stu-id="14103-101">Assemblies compiled with Regex.CompileToAssembly breaks between 4.0 and 4.5</span></span>

#### <a name="details"></a><span data-ttu-id="14103-102">Détails</span><span class="sxs-lookup"><span data-stu-id="14103-102">Details</span></span>

<span data-ttu-id="14103-103">Si un assembly d’expressions régulières compilées est généré avec .NET Framework 4.5 mais qu’il cible .NET Framework 4, toute tentative d’utiliser l’une des expressions régulières dans cet assembly sur un système sur lequel .NET Framework 4 est installé lève une exception.</span><span class="sxs-lookup"><span data-stu-id="14103-103">If an assembly of compiled regular expressions is built with the .NET Framework 4.5 but targets the .NET Framework 4, attempting to use one of the regular expressions in that assembly on a system with .NET Framework 4 installed throws an exception.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="14103-104">Suggestion</span><span class="sxs-lookup"><span data-stu-id="14103-104">Suggestion</span></span>

<span data-ttu-id="14103-105">Pour contourner ce problème, vous pouvez procéder de l'une des manières suivantes :</span><span class="sxs-lookup"><span data-stu-id="14103-105">To work around this problem, you can do either of the following:</span></span><ul><li><span data-ttu-id="14103-106">Générez l’assembly qui contient les expressions régulières avec .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="14103-106">Build the assembly that contains the regular expressions with the .NET Framework 4.</span></span></li><li><span data-ttu-id="14103-107">Utilisez une expression régulière interprétée.</span><span class="sxs-lookup"><span data-stu-id="14103-107">Use an interpreted regular expression.</span></span></li></ul>

| <span data-ttu-id="14103-108">Nom</span><span class="sxs-lookup"><span data-stu-id="14103-108">Name</span></span>    | <span data-ttu-id="14103-109">Valeur</span><span class="sxs-lookup"><span data-stu-id="14103-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="14103-110">Étendue</span><span class="sxs-lookup"><span data-stu-id="14103-110">Scope</span></span>   |<span data-ttu-id="14103-111">Secondaire</span><span class="sxs-lookup"><span data-stu-id="14103-111">Minor</span></span>|
|<span data-ttu-id="14103-112">Version</span><span class="sxs-lookup"><span data-stu-id="14103-112">Version</span></span>|<span data-ttu-id="14103-113">4,5</span><span class="sxs-lookup"><span data-stu-id="14103-113">4.5</span></span>|
|<span data-ttu-id="14103-114">Type</span><span class="sxs-lookup"><span data-stu-id="14103-114">Type</span></span>|<span data-ttu-id="14103-115">Runtime</span><span class="sxs-lookup"><span data-stu-id="14103-115">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="14103-116">API affectées</span><span class="sxs-lookup"><span data-stu-id="14103-116">Affected APIs</span></span>

-<xref:System.Text.RegularExpressions.Regex.CompileToAssembly(System.Text.RegularExpressions.RegexCompilationInfo[],System.Reflection.AssemblyName)?displayProperty=nameWithType></li><li><xref:System.Text.RegularExpressions.Regex.CompileToAssembly(System.Text.RegularExpressions.RegexCompilationInfo[],System.Reflection.AssemblyName,System.Reflection.Emit.CustomAttributeBuilder[])?displayProperty=nameWithType></li><li><xref:System.Text.RegularExpressions.Regex.CompileToAssembly(System.Text.RegularExpressions.RegexCompilationInfo[],System.Reflection.AssemblyName,System.Reflection.Emit.CustomAttributeBuilder[],System.String)?displayProperty=nameWithType></li></ul>|
