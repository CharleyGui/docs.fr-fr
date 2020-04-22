---
ms.openlocfilehash: 22dbb1e982f83687a9e0eb288ed72c78c676db77
ms.sourcegitcommit: 348bb052d5cef109a61a3d5253faa5d7167d55ac
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "82021615"
---
### <a name="floating-point-formatting-and-parsing-behavior-changed"></a><span data-ttu-id="1b20b-101">Le formatage et l’analyse des points flottants ont changé</span><span class="sxs-lookup"><span data-stu-id="1b20b-101">Floating-point formatting and parsing behavior changed</span></span>

<span data-ttu-id="1b20b-102">Le comportement flottant d’analyse et <xref:System.Double> de <xref:System.Single> formatage des points (par les types et les types) est maintenant conforme à l’IEEE.</span><span class="sxs-lookup"><span data-stu-id="1b20b-102">Floating point parsing and formatting behavior (by the <xref:System.Double> and <xref:System.Single> types) are now IEEE-compliant.</span></span>

#### <a name="change-description"></a><span data-ttu-id="1b20b-103">Description de la modification</span><span class="sxs-lookup"><span data-stu-id="1b20b-103">Change description</span></span>

<span data-ttu-id="1b20b-104">Dans .NET Core 2.2 et les <xref:System.Double.ToString%2A?displayProperty=nameWithType> versions antérieures, le formatage avec <xref:System.Single.ToString%2A?displayProperty=nameWithType>et , et l’analyse <xref:System.Double.Parse%2A?displayProperty=nameWithType>avec , <xref:System.Double.TryParse%2A?displayProperty=nameWithType>, <xref:System.Single.Parse%2A?displayProperty=nameWithType>, et <xref:System.Single.TryParse%2A?displayProperty=nameWithType> ne sont pas conformes à l’IEEE.</span><span class="sxs-lookup"><span data-stu-id="1b20b-104">In .NET Core 2.2 and earlier versions, formatting with <xref:System.Double.ToString%2A?displayProperty=nameWithType> and <xref:System.Single.ToString%2A?displayProperty=nameWithType>, and parsing with <xref:System.Double.Parse%2A?displayProperty=nameWithType>, <xref:System.Double.TryParse%2A?displayProperty=nameWithType>, <xref:System.Single.Parse%2A?displayProperty=nameWithType>, and <xref:System.Single.TryParse%2A?displayProperty=nameWithType> are not IEEE-compliant.</span></span> <span data-ttu-id="1b20b-105">Par conséquent, il est impossible de garantir qu’une valeur sera aller-retour avec n’importe quelle chaîne de format standard ou personnalisé prise en charge.</span><span class="sxs-lookup"><span data-stu-id="1b20b-105">As a result, it is impossible to guarantee that a value will roundtrip with any supported standard or custom format string.</span></span> <span data-ttu-id="1b20b-106">Pour certaines entrées, la tentative d’analyser une valeur formatée peut échouer, et pour d’autres, la valeur analysée n’égale pas la valeur originale.</span><span class="sxs-lookup"><span data-stu-id="1b20b-106">For some inputs, the attempt to parse a formatted value can fail, and for others, the parsed value doesn't equal the original value.</span></span>

<span data-ttu-id="1b20b-107">À partir de .NET Core 3.0, les opérations d’analyse et de mise en forme sont conformes à l’IEEE 754.</span><span class="sxs-lookup"><span data-stu-id="1b20b-107">Starting with .NET Core 3.0, parsing and formatting operations are IEEE 754-compliant.</span></span> <span data-ttu-id="1b20b-108">Cela garantit que le comportement des types de points flottants en .NET correspond à celui des langues conformes à l’IEEE telles que le C.</span><span class="sxs-lookup"><span data-stu-id="1b20b-108">This ensures that the behavior of floating-point types in .NET matches that of IEEE-compliant languages such as C#.</span></span> <span data-ttu-id="1b20b-109">Pour plus d’informations, voir les améliorations de l’analyse et du formatage des points flottants dans le billet de blog [.NET Core 3.0.](https://devblogs.microsoft.com/dotnet/floating-point-parsing-and-formatting-improvements-in-net-core-3-0/)</span><span class="sxs-lookup"><span data-stu-id="1b20b-109">For more information, see the [Floating-point parsing and formatting improvements in .NET Core 3.0](https://devblogs.microsoft.com/dotnet/floating-point-parsing-and-formatting-improvements-in-net-core-3-0/) blog post.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="1b20b-110">Version introduite</span><span class="sxs-lookup"><span data-stu-id="1b20b-110">Version introduced</span></span>

<span data-ttu-id="1b20b-111">3.0</span><span class="sxs-lookup"><span data-stu-id="1b20b-111">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="1b20b-112">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="1b20b-112">Recommended action</span></span>

<span data-ttu-id="1b20b-113">La section « Impact potentiel sur le code existant » des améliorations de l’analyse et du formatage des points flottants dans le billet de blog [.NET Core 3.0](https://devblogs.microsoft.com/dotnet/floating-point-parsing-and-formatting-improvements-in-net-core-3-0/) suggère des modifications à votre code si vous observez un changement de comportement par rapport aux applications .NET Core 2.2 En général, cela implique l’utilisation d’une chaîne de format standard ou personnalisée différente pour appliquer le comportement souhaité.</span><span class="sxs-lookup"><span data-stu-id="1b20b-113">The "Potential impact to existing code" section of the [Floating-point parsing and formatting improvements in .NET Core 3.0](https://devblogs.microsoft.com/dotnet/floating-point-parsing-and-formatting-improvements-in-net-core-3-0/) blog post suggests changes to your code if you observe a change of behavior when compared to .NET Core 2.2 applications Generally, this involves using a different standard or custom format string to enforce the desired behavior.</span></span> <span data-ttu-id="1b20b-114">Certains résultats peuvent ne pas avoir une solution de contournement s’ils étaient auparavant incorrects.</span><span class="sxs-lookup"><span data-stu-id="1b20b-114">Some results may not have a workaround if they were previously incorrect.</span></span>

#### <a name="category"></a><span data-ttu-id="1b20b-115">Category</span><span class="sxs-lookup"><span data-stu-id="1b20b-115">Category</span></span>

<span data-ttu-id="1b20b-116">Core .NET bibliothèques</span><span class="sxs-lookup"><span data-stu-id="1b20b-116">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="1b20b-117">API affectées</span><span class="sxs-lookup"><span data-stu-id="1b20b-117">Affected APIs</span></span>

- <xref:System.Double.ToString%2A?displayProperty=nameWithType>
- <xref:System.Single.ToString%2A?displayProperty=nameWithType>
- <xref:System.Double.Parse%2A?displayProperty=nameWithType>
- <xref:System.Double.TryParse%2A?displayProperty=nameWithType>
- <xref:System.Single.Parse%2A?displayProperty=nameWithType>
- <xref:System.Single.TryParse%2A?displayProperty=nameWithType>

<!-- 

### Affected APIs

- `Overload:System.Double.ToString`
- `Overload:System.Single.ToString`
- `Overload:System.Double.Parse`
- `Overload:System.Double.TryParse`
- `Overload:System.Single.Parse`
- `Overload:System.Single.TryParse`

-->
