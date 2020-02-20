---
ms.openlocfilehash: 4091bdcf7d9ed8872aed5faa6e6d3ed143903787
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77449395"
---
### <a name="unauthorizedaccessexception-thrown-by-filesysteminfoattributes"></a><span data-ttu-id="38032-101">UnauthorizedAccessException levée par FileSystemInfo. Attributes</span><span class="sxs-lookup"><span data-stu-id="38032-101">UnauthorizedAccessException thrown by FileSystemInfo.Attributes</span></span>

<span data-ttu-id="38032-102">Dans .NET Core, une <xref:System.UnauthorizedAccessException> est levée lorsque l’appelant tente de définir une valeur d’attribut de fichier, mais ne dispose pas de l’autorisation d’écriture.</span><span class="sxs-lookup"><span data-stu-id="38032-102">In .NET Core, an <xref:System.UnauthorizedAccessException> is thrown when the caller attempts to set a file attribute value but doesn't have write permission.</span></span>

#### <a name="change-description"></a><span data-ttu-id="38032-103">Modifier la description</span><span class="sxs-lookup"><span data-stu-id="38032-103">Change description</span></span>

<span data-ttu-id="38032-104">Dans .NET Framework, une <xref:System.ArgumentException> est levée lorsque l’appelant tente de définir une valeur d’attribut de fichier dans <xref:System.IO.FileSystemInfo.Attributes?displayProperty=nameWithType>, mais ne dispose pas de l’autorisation d’écriture.</span><span class="sxs-lookup"><span data-stu-id="38032-104">In .NET Framework, an <xref:System.ArgumentException> is thrown when the caller attempts to set a file attribute value in <xref:System.IO.FileSystemInfo.Attributes?displayProperty=nameWithType> but doesn't have write permission.</span></span> <span data-ttu-id="38032-105">Dans .NET Core, une <xref:System.UnauthorizedAccessException> est levée à la place.</span><span class="sxs-lookup"><span data-stu-id="38032-105">In .NET Core, an <xref:System.UnauthorizedAccessException> is thrown instead.</span></span> <span data-ttu-id="38032-106">(Dans .NET Core, une <xref:System.ArgumentException> est toujours levée si l’appelant tente de définir un attribut de fichier non valide.)</span><span class="sxs-lookup"><span data-stu-id="38032-106">(In .NET Core, an <xref:System.ArgumentException> is still thrown if the caller attempts to set an invalid file attribute.)</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="38032-107">Version introduite</span><span class="sxs-lookup"><span data-stu-id="38032-107">Version introduced</span></span>

<span data-ttu-id="38032-108">1.0</span><span class="sxs-lookup"><span data-stu-id="38032-108">1.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="38032-109">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="38032-109">Recommended action</span></span>

<span data-ttu-id="38032-110">Modifiez les instructions `catch` pour intercepter une <xref:System.UnauthorizedAccessException> au lieu de, ou en plus d’un <xref:System.ArgumentException>, si nécessaire.</span><span class="sxs-lookup"><span data-stu-id="38032-110">Modify any `catch` statements to catch an <xref:System.UnauthorizedAccessException> instead of, or in addition to, an <xref:System.ArgumentException>, as necessary.</span></span>

#### <a name="category"></a><span data-ttu-id="38032-111">Category</span><span class="sxs-lookup"><span data-stu-id="38032-111">Category</span></span>

<span data-ttu-id="38032-112">CoreFx</span><span class="sxs-lookup"><span data-stu-id="38032-112">CoreFx</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="38032-113">API affectées</span><span class="sxs-lookup"><span data-stu-id="38032-113">Affected APIs</span></span>

- <xref:System.IO.FileSystemInfo.Attributes?displayProperty=nameWithType>

<!--

#### Affected APIs

- `P:System.IO.FileSystemInfo.Attributes`

-->
