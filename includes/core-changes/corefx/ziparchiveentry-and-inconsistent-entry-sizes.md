---
ms.openlocfilehash: 9520f8c6b6671917f5694bc602293a00e2dab82d
ms.sourcegitcommit: 56f1d1203d0075a461a10a301459d3aa452f4f47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71217058"
---
### <a name="ziparchiveentry-no-longer-handles-archives-with-inconsistent-entry-sizes"></a><span data-ttu-id="c5adb-101">ZipArchiveEntry ne gère plus les archives avec des tailles d’entrée incohérentes</span><span class="sxs-lookup"><span data-stu-id="c5adb-101">ZipArchiveEntry no longer handles archives with inconsistent entry sizes</span></span>

<span data-ttu-id="c5adb-102">Les archives zip répertorient à la fois la taille compressée et la taille non compressée dans le répertoire central et l’en-tête local.</span><span class="sxs-lookup"><span data-stu-id="c5adb-102">Zip archives list both compressed size and uncompressed size in the central directory and local header.</span></span>  <span data-ttu-id="c5adb-103">Les données d’entrée lui-même indiquent également sa taille.</span><span class="sxs-lookup"><span data-stu-id="c5adb-103">The entry data itself also indicates its size.</span></span>  <span data-ttu-id="c5adb-104">Dans .NET Core 2,2 et les versions antérieures, ces valeurs n’ont jamais été vérifiées pour des fins de cohérence.</span><span class="sxs-lookup"><span data-stu-id="c5adb-104">In .NET Core 2.2 and earlier versions, these values were never checked for consistency.</span></span> <span data-ttu-id="c5adb-105">À compter de .NET Core 3,0, ils sont désormais.</span><span class="sxs-lookup"><span data-stu-id="c5adb-105">Starting with .NET Core 3.0, they now are.</span></span>

#### <a name="change-description"></a><span data-ttu-id="c5adb-106">Modifier la description</span><span class="sxs-lookup"><span data-stu-id="c5adb-106">Change description</span></span>

<span data-ttu-id="c5adb-107">Dans .net Core 2,2 et les versions antérieures <xref:System.IO.Compression.ZipArchiveEntry.Open?displayProperty=nameWithType> , fonctionne même si l’en-tête local est en désaccord avec l’en-tête central du fichier zip.</span><span class="sxs-lookup"><span data-stu-id="c5adb-107">In .NET Core 2.2 and earlier versions, <xref:System.IO.Compression.ZipArchiveEntry.Open?displayProperty=nameWithType> succeeds even if the local header disagrees with the central header of the zip file.</span></span> <span data-ttu-id="c5adb-108">Les données sont décompressées jusqu’à la fin du flux compressé, même si leur longueur dépasse la taille du fichier non compressé figurant dans le répertoire central/l’en-tête local.</span><span class="sxs-lookup"><span data-stu-id="c5adb-108">Data is decompressed until the end of the compressed stream is reached, even if its length exceeds the uncompressed file size listed in the central directory/local header.</span></span>

<span data-ttu-id="c5adb-109">À compter de .net Core 3,0, <xref:System.IO.Compression.ZipArchiveEntry.Open?displayProperty=nameWithType> la méthode vérifie que l’en-tête local et l’en-tête central s’accordent sur des tailles compressées et non compressées d’une entrée.</span><span class="sxs-lookup"><span data-stu-id="c5adb-109">Starting with .NET Core 3.0, the <xref:System.IO.Compression.ZipArchiveEntry.Open?displayProperty=nameWithType> method checks that local header and central header agree on compressed and uncompressed sizes of an entry.</span></span>  <span data-ttu-id="c5adb-110">Si ce n’est pas le cas, la méthode <xref:System.IO.InvalidDataException> lève une si les tailles d’en-tête local et/ou de liste de descripteurs de données de l’archive ne sont pas en accord avec le répertoire central du fichier. zip.</span><span class="sxs-lookup"><span data-stu-id="c5adb-110">If they do not, the method throws an <xref:System.IO.InvalidDataException> if the archive's local header and/or data descriptor list sizes that disagree with the central directory of the zip file.</span></span> <span data-ttu-id="c5adb-111">Lors de la lecture d’une entrée, les données décompressées sont tronquées à la taille de fichier non compressée indiquée dans l’en-tête.</span><span class="sxs-lookup"><span data-stu-id="c5adb-111">When reading an entry, decompressed data is truncated to the uncompressed file size listed in the header.</span></span>

<span data-ttu-id="c5adb-112">Cette modification a été apportée pour <xref:System.IO.Compression.ZipArchiveEntry> s’assurer qu’un correspond correctement à la taille de ses données et que seule cette quantité de données est lue.</span><span class="sxs-lookup"><span data-stu-id="c5adb-112">This change was made to ensure that a <xref:System.IO.Compression.ZipArchiveEntry> correctly represents the size of its data and that only that amount of data is read.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="c5adb-113">Version introduite</span><span class="sxs-lookup"><span data-stu-id="c5adb-113">Version introduced</span></span>

<span data-ttu-id="c5adb-114">3.0</span><span class="sxs-lookup"><span data-stu-id="c5adb-114">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="c5adb-115">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="c5adb-115">Recommended action</span></span>

<span data-ttu-id="c5adb-116">Reconditionner toute archive zip qui présente ces problèmes.</span><span class="sxs-lookup"><span data-stu-id="c5adb-116">Repackage any zip archive that exhibits these problems.</span></span>

#### <a name="category"></a><span data-ttu-id="c5adb-117">Category</span><span class="sxs-lookup"><span data-stu-id="c5adb-117">Category</span></span>

<span data-ttu-id="c5adb-118">CoreFx</span><span class="sxs-lookup"><span data-stu-id="c5adb-118">CoreFx</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="c5adb-119">API affectées</span><span class="sxs-lookup"><span data-stu-id="c5adb-119">Affected APIs</span></span>

- <xref:System.IO.Compression.ZipArchiveEntry.Open?displayProperty=nameWithType>
- <xref:System.IO.Compression.ZipFileExtensions.ExtractToDirectory%2A?displayProperty=nameWithType>
- <xref:System.IO.Compression.ZipFileExtensions.ExtractToFile%2A?displayProperty=nameWithType>
- <xref:System.IO.Compression.ZipFile.ExtractToDirectory%2A?displayProperty=nameWithType>

<!--

### Affected APIs

`M:System.IO.Compression.ZipArchiveEntry.Open`
`Overload:System.IO.Compression.ZipFileExtensions.ExtractToDirectory%2A`
`Overload:System.IO.Compression.ZipFileExtensions.ExtractToFile%2A`
`Overload:System.IO.Compression.ZipFile.ExtractToDirectory%2A`

-->
