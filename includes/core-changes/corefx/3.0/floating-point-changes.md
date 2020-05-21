---
ms.openlocfilehash: 719f336e1b38597674d6ee8f0c5429dd965054b1
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83721681"
---
### <a name="floating-point-formatting-and-parsing-behavior-changed"></a><span data-ttu-id="51baf-101">Modification du comportement de l’analyse et de la mise en forme à virgule flottante</span><span class="sxs-lookup"><span data-stu-id="51baf-101">Floating-point formatting and parsing behavior changed</span></span>

<span data-ttu-id="51baf-102">Le comportement d’analyse et de mise en forme de virgule flottante (par les <xref:System.Double> <xref:System.Single> types et) est désormais conforme à la norme IEEE.</span><span class="sxs-lookup"><span data-stu-id="51baf-102">Floating point parsing and formatting behavior (by the <xref:System.Double> and <xref:System.Single> types) are now IEEE-compliant.</span></span>

#### <a name="change-description"></a><span data-ttu-id="51baf-103">Description de la modification</span><span class="sxs-lookup"><span data-stu-id="51baf-103">Change description</span></span>

<span data-ttu-id="51baf-104">Dans .net Core 2,2 et versions antérieures, la mise en forme avec <xref:System.Double.ToString%2A?displayProperty=nameWithType> et <xref:System.Single.ToString%2A?displayProperty=nameWithType> , ainsi que l’analyse avec <xref:System.Double.Parse%2A?displayProperty=nameWithType> ,, et ne <xref:System.Double.TryParse%2A?displayProperty=nameWithType> <xref:System.Single.Parse%2A?displayProperty=nameWithType> <xref:System.Single.TryParse%2A?displayProperty=nameWithType> sont pas conformes à IEEE.</span><span class="sxs-lookup"><span data-stu-id="51baf-104">In .NET Core 2.2 and earlier versions, formatting with <xref:System.Double.ToString%2A?displayProperty=nameWithType> and <xref:System.Single.ToString%2A?displayProperty=nameWithType>, and parsing with <xref:System.Double.Parse%2A?displayProperty=nameWithType>, <xref:System.Double.TryParse%2A?displayProperty=nameWithType>, <xref:System.Single.Parse%2A?displayProperty=nameWithType>, and <xref:System.Single.TryParse%2A?displayProperty=nameWithType> are not IEEE-compliant.</span></span> <span data-ttu-id="51baf-105">Par conséquent, il est impossible de garantir qu’une valeur fera l’aller-retour avec toute chaîne de format standard ou personnalisée prise en charge.</span><span class="sxs-lookup"><span data-stu-id="51baf-105">As a result, it is impossible to guarantee that a value will roundtrip with any supported standard or custom format string.</span></span> <span data-ttu-id="51baf-106">Pour certaines entrées, la tentative d’analyse d’une valeur mise en forme peut échouer et, pour d’autres, la valeur analysée n’est pas égale à la valeur d’origine.</span><span class="sxs-lookup"><span data-stu-id="51baf-106">For some inputs, the attempt to parse a formatted value can fail, and for others, the parsed value doesn't equal the original value.</span></span>

<span data-ttu-id="51baf-107">À compter de .NET Core 3,0, les opérations d’analyse et de mise en forme sont conformes à la norme IEEE 754.</span><span class="sxs-lookup"><span data-stu-id="51baf-107">Starting with .NET Core 3.0, parsing and formatting operations are IEEE 754-compliant.</span></span> <span data-ttu-id="51baf-108">Cela garantit que le comportement des types à virgule flottante dans .NET correspond à celui des langages compatibles IEEE tels que C#.</span><span class="sxs-lookup"><span data-stu-id="51baf-108">This ensures that the behavior of floating-point types in .NET matches that of IEEE-compliant languages such as C#.</span></span> <span data-ttu-id="51baf-109">Pour plus d’informations, consultez le billet de blog [améliorations de la mise en forme et de l’analyse de la virgule flottante dans .net Core 3,0](https://devblogs.microsoft.com/dotnet/floating-point-parsing-and-formatting-improvements-in-net-core-3-0/) .</span><span class="sxs-lookup"><span data-stu-id="51baf-109">For more information, see the [Floating-point parsing and formatting improvements in .NET Core 3.0](https://devblogs.microsoft.com/dotnet/floating-point-parsing-and-formatting-improvements-in-net-core-3-0/) blog post.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="51baf-110">Version introduite</span><span class="sxs-lookup"><span data-stu-id="51baf-110">Version introduced</span></span>

<span data-ttu-id="51baf-111">3.0</span><span class="sxs-lookup"><span data-stu-id="51baf-111">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="51baf-112">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="51baf-112">Recommended action</span></span>

<span data-ttu-id="51baf-113">La section « impact potentiel sur le code existant » des améliorations de l’analyse de la [virgule flottante et de la mise en forme dans le billet de blog .net core 3,0](https://devblogs.microsoft.com/dotnet/floating-point-parsing-and-formatting-improvements-in-net-core-3-0/) suggère des modifications apportées à votre code si vous observez un changement de comportement par rapport aux applications .net Core 2,2 généralement, cela implique l’utilisation d’une chaîne de format standard ou personnalisée différente pour appliquer le comportement souhaité.</span><span class="sxs-lookup"><span data-stu-id="51baf-113">The "Potential impact to existing code" section of the [Floating-point parsing and formatting improvements in .NET Core 3.0](https://devblogs.microsoft.com/dotnet/floating-point-parsing-and-formatting-improvements-in-net-core-3-0/) blog post suggests changes to your code if you observe a change of behavior when compared to .NET Core 2.2 applications Generally, this involves using a different standard or custom format string to enforce the desired behavior.</span></span> <span data-ttu-id="51baf-114">Certains résultats peuvent ne pas avoir de solution de contournement s’ils étaient précédemment incorrects.</span><span class="sxs-lookup"><span data-stu-id="51baf-114">Some results may not have a workaround if they were previously incorrect.</span></span>

#### <a name="category"></a><span data-ttu-id="51baf-115">Category</span><span class="sxs-lookup"><span data-stu-id="51baf-115">Category</span></span>

<span data-ttu-id="51baf-116">Bibliothèques .NET Core</span><span class="sxs-lookup"><span data-stu-id="51baf-116">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="51baf-117">API affectées</span><span class="sxs-lookup"><span data-stu-id="51baf-117">Affected APIs</span></span>

- <xref:System.Double.ToString%2A?displayProperty=nameWithType>
- <xref:System.Single.ToString%2A?displayProperty=nameWithType>
- <xref:System.Double.Parse%2A?displayProperty=nameWithType>
- <xref:System.Double.TryParse%2A?displayProperty=nameWithType>
- <xref:System.Single.Parse%2A?displayProperty=nameWithType>
- <xref:System.Single.TryParse%2A?displayProperty=nameWithType>

<!-- 

#### Affected APIs

- `Overload:System.Double.ToString`
- `Overload:System.Single.ToString`
- `Overload:System.Double.Parse`
- `Overload:System.Double.TryParse`
- `Overload:System.Single.Parse`
- `Overload:System.Single.TryParse`

-->
