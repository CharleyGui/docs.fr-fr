---
ms.openlocfilehash: 2ea9abca7578c2ddf92712a1c597f8f1ff4a5c0c
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/25/2020
ms.locfileid: "96032002"
---
### <a name="unauthorizedaccessexception-thrown-by-filesysteminfoattributes"></a><span data-ttu-id="c3e55-101">UnauthorizedAccessException levée par FileSystemInfo. Attributes</span><span class="sxs-lookup"><span data-stu-id="c3e55-101">UnauthorizedAccessException thrown by FileSystemInfo.Attributes</span></span>

<span data-ttu-id="c3e55-102">Dans .NET Core, une <xref:System.UnauthorizedAccessException> exception est levée lorsque l’appelant tente de définir une valeur d’attribut de fichier mais ne dispose pas de l’autorisation d’écriture.</span><span class="sxs-lookup"><span data-stu-id="c3e55-102">In .NET Core, an <xref:System.UnauthorizedAccessException> is thrown when the caller attempts to set a file attribute value but doesn't have write permission.</span></span>

#### <a name="change-description"></a><span data-ttu-id="c3e55-103">Description de la modification</span><span class="sxs-lookup"><span data-stu-id="c3e55-103">Change description</span></span>

<span data-ttu-id="c3e55-104">Dans .NET Framework, une <xref:System.ArgumentException> exception est levée lorsque l’appelant tente de définir une valeur d’attribut de fichier dans, <xref:System.IO.FileSystemInfo.Attributes?displayProperty=nameWithType> mais ne dispose pas de l’autorisation d’écriture.</span><span class="sxs-lookup"><span data-stu-id="c3e55-104">In .NET Framework, an <xref:System.ArgumentException> is thrown when the caller attempts to set a file attribute value in <xref:System.IO.FileSystemInfo.Attributes?displayProperty=nameWithType> but doesn't have write permission.</span></span> <span data-ttu-id="c3e55-105">Dans .NET Core, une <xref:System.UnauthorizedAccessException> exception est levée à la place.</span><span class="sxs-lookup"><span data-stu-id="c3e55-105">In .NET Core, an <xref:System.UnauthorizedAccessException> is thrown instead.</span></span> <span data-ttu-id="c3e55-106">(Dans .NET Core, une <xref:System.ArgumentException> est toujours levée si l’appelant tente de définir un attribut de fichier non valide.)</span><span class="sxs-lookup"><span data-stu-id="c3e55-106">(In .NET Core, an <xref:System.ArgumentException> is still thrown if the caller attempts to set an invalid file attribute.)</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="c3e55-107">Version introduite</span><span class="sxs-lookup"><span data-stu-id="c3e55-107">Version introduced</span></span>

<span data-ttu-id="c3e55-108">1.0</span><span class="sxs-lookup"><span data-stu-id="c3e55-108">1.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="c3e55-109">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="c3e55-109">Recommended action</span></span>

<span data-ttu-id="c3e55-110">Modifiez toutes les `catch` instructions pour intercepter un <xref:System.UnauthorizedAccessException> au lieu de, ou en plus d’un <xref:System.ArgumentException> , si nécessaire.</span><span class="sxs-lookup"><span data-stu-id="c3e55-110">Modify any `catch` statements to catch an <xref:System.UnauthorizedAccessException> instead of, or in addition to, an <xref:System.ArgumentException>, as necessary.</span></span>

#### <a name="category"></a><span data-ttu-id="c3e55-111">Category</span><span class="sxs-lookup"><span data-stu-id="c3e55-111">Category</span></span>

<span data-ttu-id="c3e55-112">Bibliothèques .NET Core</span><span class="sxs-lookup"><span data-stu-id="c3e55-112">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="c3e55-113">API affectées</span><span class="sxs-lookup"><span data-stu-id="c3e55-113">Affected APIs</span></span>

- <xref:System.IO.FileSystemInfo.Attributes?displayProperty=nameWithType>

<!--

#### Affected APIs

- `P:System.IO.FileSystemInfo.Attributes`

-->
