---
ms.openlocfilehash: 4091bdcf7d9ed8872aed5faa6e6d3ed143903787
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "77449395"
---
### <a name="unauthorizedaccessexception-thrown-by-filesysteminfoattributes"></a><span data-ttu-id="539f8-101">UnauthorizedAccessException jeté par FileSystemInfo.Attributes</span><span class="sxs-lookup"><span data-stu-id="539f8-101">UnauthorizedAccessException thrown by FileSystemInfo.Attributes</span></span>

<span data-ttu-id="539f8-102">Dans .NET Core, un <xref:System.UnauthorizedAccessException> est lancé lorsque l’appelant tente de définir une valeur d’attribut de fichier, mais n’a pas d’autorisation d’écriture.</span><span class="sxs-lookup"><span data-stu-id="539f8-102">In .NET Core, an <xref:System.UnauthorizedAccessException> is thrown when the caller attempts to set a file attribute value but doesn't have write permission.</span></span>

#### <a name="change-description"></a><span data-ttu-id="539f8-103">Description de la modification</span><span class="sxs-lookup"><span data-stu-id="539f8-103">Change description</span></span>

<span data-ttu-id="539f8-104">Dans .NET Framework, un <xref:System.ArgumentException> est lancé lorsque l’appelant <xref:System.IO.FileSystemInfo.Attributes?displayProperty=nameWithType> tente de définir une valeur d’attribut de fichier, mais n’a pas d’autorisation d’écriture.</span><span class="sxs-lookup"><span data-stu-id="539f8-104">In .NET Framework, an <xref:System.ArgumentException> is thrown when the caller attempts to set a file attribute value in <xref:System.IO.FileSystemInfo.Attributes?displayProperty=nameWithType> but doesn't have write permission.</span></span> <span data-ttu-id="539f8-105">Dans .NET Core, un <xref:System.UnauthorizedAccessException> est jeté à la place.</span><span class="sxs-lookup"><span data-stu-id="539f8-105">In .NET Core, an <xref:System.UnauthorizedAccessException> is thrown instead.</span></span> <span data-ttu-id="539f8-106">(Dans .NET Core, un <xref:System.ArgumentException> est toujours jeté si l’appelant tente de définir un attribut de fichier invalide.)</span><span class="sxs-lookup"><span data-stu-id="539f8-106">(In .NET Core, an <xref:System.ArgumentException> is still thrown if the caller attempts to set an invalid file attribute.)</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="539f8-107">Version introduite</span><span class="sxs-lookup"><span data-stu-id="539f8-107">Version introduced</span></span>

<span data-ttu-id="539f8-108">1.0</span><span class="sxs-lookup"><span data-stu-id="539f8-108">1.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="539f8-109">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="539f8-109">Recommended action</span></span>

<span data-ttu-id="539f8-110">Modifier `catch` toutes les <xref:System.UnauthorizedAccessException> déclarations pour attraper un <xref:System.ArgumentException>au lieu ou en plus d’un , si nécessaire.</span><span class="sxs-lookup"><span data-stu-id="539f8-110">Modify any `catch` statements to catch an <xref:System.UnauthorizedAccessException> instead of, or in addition to, an <xref:System.ArgumentException>, as necessary.</span></span>

#### <a name="category"></a><span data-ttu-id="539f8-111">Category</span><span class="sxs-lookup"><span data-stu-id="539f8-111">Category</span></span>

<span data-ttu-id="539f8-112">CoreFx</span><span class="sxs-lookup"><span data-stu-id="539f8-112">CoreFx</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="539f8-113">API affectées</span><span class="sxs-lookup"><span data-stu-id="539f8-113">Affected APIs</span></span>

- <xref:System.IO.FileSystemInfo.Attributes?displayProperty=nameWithType>

<!--

#### Affected APIs

- `P:System.IO.FileSystemInfo.Attributes`

-->
