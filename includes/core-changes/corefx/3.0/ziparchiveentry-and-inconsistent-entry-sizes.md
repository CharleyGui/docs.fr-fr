---
ms.openlocfilehash: 8c8e87c885c99d28aa9a7a5d5a2b48c80d40d7db
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/25/2020
ms.locfileid: "96032041"
---
### <a name="ziparchiveentry-no-longer-handles-archives-with-inconsistent-entry-sizes"></a><span data-ttu-id="f9b46-101">ZipArchiveEntry ne gère plus les archives avec des tailles d’entrée incohérentes</span><span class="sxs-lookup"><span data-stu-id="f9b46-101">ZipArchiveEntry no longer handles archives with inconsistent entry sizes</span></span>

<span data-ttu-id="f9b46-102">Les archives zip répertorient à la fois la taille compressée et la taille non compressée dans le répertoire central et l’en-tête local.</span><span class="sxs-lookup"><span data-stu-id="f9b46-102">Zip archives list both compressed size and uncompressed size in the central directory and local header.</span></span>  <span data-ttu-id="f9b46-103">Les données d’entrée lui-même indiquent également sa taille.</span><span class="sxs-lookup"><span data-stu-id="f9b46-103">The entry data itself also indicates its size.</span></span>  <span data-ttu-id="f9b46-104">Dans .NET Core 2,2 et les versions antérieures, ces valeurs n’ont jamais été vérifiées pour des fins de cohérence.</span><span class="sxs-lookup"><span data-stu-id="f9b46-104">In .NET Core 2.2 and earlier versions, these values were never checked for consistency.</span></span> <span data-ttu-id="f9b46-105">À compter de .NET Core 3,0, ils sont désormais.</span><span class="sxs-lookup"><span data-stu-id="f9b46-105">Starting with .NET Core 3.0, they now are.</span></span>

#### <a name="change-description"></a><span data-ttu-id="f9b46-106">Description de la modification</span><span class="sxs-lookup"><span data-stu-id="f9b46-106">Change description</span></span>

<span data-ttu-id="f9b46-107">Dans .NET Core 2,2 et les versions antérieures, <xref:System.IO.Compression.ZipArchiveEntry.Open?displayProperty=nameWithType> fonctionne même si l’en-tête local est en désaccord avec l’en-tête central du fichier zip.</span><span class="sxs-lookup"><span data-stu-id="f9b46-107">In .NET Core 2.2 and earlier versions, <xref:System.IO.Compression.ZipArchiveEntry.Open?displayProperty=nameWithType> succeeds even if the local header disagrees with the central header of the zip file.</span></span> <span data-ttu-id="f9b46-108">Les données sont décompressées jusqu’à la fin du flux compressé, même si leur longueur dépasse la taille du fichier non compressé figurant dans le répertoire central/l’en-tête local.</span><span class="sxs-lookup"><span data-stu-id="f9b46-108">Data is decompressed until the end of the compressed stream is reached, even if its length exceeds the uncompressed file size listed in the central directory/local header.</span></span>

<span data-ttu-id="f9b46-109">À compter de .NET Core 3,0, la <xref:System.IO.Compression.ZipArchiveEntry.Open?displayProperty=nameWithType> méthode vérifie que l’en-tête local et l’en-tête central s’accordent sur des tailles compressées et non compressées d’une entrée.</span><span class="sxs-lookup"><span data-stu-id="f9b46-109">Starting with .NET Core 3.0, the <xref:System.IO.Compression.ZipArchiveEntry.Open?displayProperty=nameWithType> method checks that local header and central header agree on compressed and uncompressed sizes of an entry.</span></span>  <span data-ttu-id="f9b46-110">Si ce n’est pas le cas, la méthode lève une <xref:System.IO.InvalidDataException> si les tailles d’en-tête local et/ou de liste de descripteurs de données de l’archive ne sont pas en accord avec le répertoire central du fichier. zip.</span><span class="sxs-lookup"><span data-stu-id="f9b46-110">If they do not, the method throws an <xref:System.IO.InvalidDataException> if the archive's local header and/or data descriptor list sizes that disagree with the central directory of the zip file.</span></span> <span data-ttu-id="f9b46-111">Lors de la lecture d’une entrée, les données décompressées sont tronquées à la taille de fichier non compressée indiquée dans l’en-tête.</span><span class="sxs-lookup"><span data-stu-id="f9b46-111">When reading an entry, decompressed data is truncated to the uncompressed file size listed in the header.</span></span>

<span data-ttu-id="f9b46-112">Cette modification a été apportée pour s’assurer qu’un <xref:System.IO.Compression.ZipArchiveEntry> correspond correctement à la taille de ses données et que seule cette quantité de données est lue.</span><span class="sxs-lookup"><span data-stu-id="f9b46-112">This change was made to ensure that a <xref:System.IO.Compression.ZipArchiveEntry> correctly represents the size of its data and that only that amount of data is read.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="f9b46-113">Version introduite</span><span class="sxs-lookup"><span data-stu-id="f9b46-113">Version introduced</span></span>

<span data-ttu-id="f9b46-114">3.0</span><span class="sxs-lookup"><span data-stu-id="f9b46-114">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="f9b46-115">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="f9b46-115">Recommended action</span></span>

<span data-ttu-id="f9b46-116">Reconditionner toute archive zip qui présente ces problèmes.</span><span class="sxs-lookup"><span data-stu-id="f9b46-116">Repackage any zip archive that exhibits these problems.</span></span>

#### <a name="category"></a><span data-ttu-id="f9b46-117">Category</span><span class="sxs-lookup"><span data-stu-id="f9b46-117">Category</span></span>

<span data-ttu-id="f9b46-118">CoreFx</span><span class="sxs-lookup"><span data-stu-id="f9b46-118">CoreFx</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="f9b46-119">API affectées</span><span class="sxs-lookup"><span data-stu-id="f9b46-119">Affected APIs</span></span>

- <xref:System.IO.Compression.ZipArchiveEntry.Open?displayProperty=nameWithType>
- <xref:System.IO.Compression.ZipFileExtensions.ExtractToDirectory%2A?displayProperty=nameWithType>
- <xref:System.IO.Compression.ZipFileExtensions.ExtractToFile%2A?displayProperty=nameWithType>
- <xref:System.IO.Compression.ZipFile.ExtractToDirectory%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

`M:System.IO.Compression.ZipArchiveEntry.Open`
`Overload:System.IO.Compression.ZipFileExtensions.ExtractToDirectory%2A`
`Overload:System.IO.Compression.ZipFileExtensions.ExtractToFile%2A`
`Overload:System.IO.Compression.ZipFile.ExtractToDirectory%2A`

-->
