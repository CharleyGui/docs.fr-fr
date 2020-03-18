---
ms.openlocfilehash: 9520f8c6b6671917f5694bc602293a00e2dab82d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "74568091"
---
### <a name="ziparchiveentry-no-longer-handles-archives-with-inconsistent-entry-sizes"></a><span data-ttu-id="66af2-101">ZipArchiveEntry ne gère plus les archives avec des tailles d’entrée incohérentes</span><span class="sxs-lookup"><span data-stu-id="66af2-101">ZipArchiveEntry no longer handles archives with inconsistent entry sizes</span></span>

<span data-ttu-id="66af2-102">Les archives zip énumèrent à la fois la taille comprimée et la taille non compressée dans le répertoire central et l’en-tête local.</span><span class="sxs-lookup"><span data-stu-id="66af2-102">Zip archives list both compressed size and uncompressed size in the central directory and local header.</span></span>  <span data-ttu-id="66af2-103">Les données d’entrée elles-mêmes indiquent également sa taille.</span><span class="sxs-lookup"><span data-stu-id="66af2-103">The entry data itself also indicates its size.</span></span>  <span data-ttu-id="66af2-104">Dans .NET Core 2.2 et les versions antérieures, ces valeurs n’ont jamais été vérifiées pour la cohérence.</span><span class="sxs-lookup"><span data-stu-id="66af2-104">In .NET Core 2.2 and earlier versions, these values were never checked for consistency.</span></span> <span data-ttu-id="66af2-105">En commençant par .NET Core 3.0, ils le sont maintenant.</span><span class="sxs-lookup"><span data-stu-id="66af2-105">Starting with .NET Core 3.0, they now are.</span></span>

#### <a name="change-description"></a><span data-ttu-id="66af2-106">Description de la modification</span><span class="sxs-lookup"><span data-stu-id="66af2-106">Change description</span></span>

<span data-ttu-id="66af2-107">Dans .NET Core 2.2 et <xref:System.IO.Compression.ZipArchiveEntry.Open?displayProperty=nameWithType> les versions antérieures, réussit même si l’en-tête local n’est pas d’accord avec l’en-tête central du fichier zip.</span><span class="sxs-lookup"><span data-stu-id="66af2-107">In .NET Core 2.2 and earlier versions, <xref:System.IO.Compression.ZipArchiveEntry.Open?displayProperty=nameWithType> succeeds even if the local header disagrees with the central header of the zip file.</span></span> <span data-ttu-id="66af2-108">Les données sont décompressées jusqu’à ce que la fin du flux compressé soit atteinte, même si sa longueur dépasse la taille du fichier non compressé énuméré dans l’annuaire central /en-tête local.</span><span class="sxs-lookup"><span data-stu-id="66af2-108">Data is decompressed until the end of the compressed stream is reached, even if its length exceeds the uncompressed file size listed in the central directory/local header.</span></span>

<span data-ttu-id="66af2-109">À partir de .NET Core 3.0, la méthode vérifie que l’en-tête <xref:System.IO.Compression.ZipArchiveEntry.Open?displayProperty=nameWithType> local et l’en-tête central s’entendent sur les tailles comprimées et non compressées d’une entrée.</span><span class="sxs-lookup"><span data-stu-id="66af2-109">Starting with .NET Core 3.0, the <xref:System.IO.Compression.ZipArchiveEntry.Open?displayProperty=nameWithType> method checks that local header and central header agree on compressed and uncompressed sizes of an entry.</span></span>  <span data-ttu-id="66af2-110">S’ils ne le font <xref:System.IO.InvalidDataException> pas, la méthode jette un si l’en-tête local de l’archive et / ou les tailles de liste descripteur de données qui ne sont pas d’accord avec l’annuaire central du fichier zip.</span><span class="sxs-lookup"><span data-stu-id="66af2-110">If they do not, the method throws an <xref:System.IO.InvalidDataException> if the archive's local header and/or data descriptor list sizes that disagree with the central directory of the zip file.</span></span> <span data-ttu-id="66af2-111">Lors de la lecture d’une entrée, les données décompressées sont tronquées sur la taille du fichier non compressé figurant dans l’en-tête.</span><span class="sxs-lookup"><span data-stu-id="66af2-111">When reading an entry, decompressed data is truncated to the uncompressed file size listed in the header.</span></span>

<span data-ttu-id="66af2-112">Cette modification a été <xref:System.IO.Compression.ZipArchiveEntry> apportée pour s’assurer qu’un traitement à juste titre représente la taille de ses données et que seule cette quantité de données est lue.</span><span class="sxs-lookup"><span data-stu-id="66af2-112">This change was made to ensure that a <xref:System.IO.Compression.ZipArchiveEntry> correctly represents the size of its data and that only that amount of data is read.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="66af2-113">Version introduite</span><span class="sxs-lookup"><span data-stu-id="66af2-113">Version introduced</span></span>

<span data-ttu-id="66af2-114">3.0</span><span class="sxs-lookup"><span data-stu-id="66af2-114">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="66af2-115">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="66af2-115">Recommended action</span></span>

<span data-ttu-id="66af2-116">Reconditionner toute archive zip qui présente ces problèmes.</span><span class="sxs-lookup"><span data-stu-id="66af2-116">Repackage any zip archive that exhibits these problems.</span></span>

#### <a name="category"></a><span data-ttu-id="66af2-117">Category</span><span class="sxs-lookup"><span data-stu-id="66af2-117">Category</span></span>

<span data-ttu-id="66af2-118">CoreFx</span><span class="sxs-lookup"><span data-stu-id="66af2-118">CoreFx</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="66af2-119">API affectées</span><span class="sxs-lookup"><span data-stu-id="66af2-119">Affected APIs</span></span>

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
