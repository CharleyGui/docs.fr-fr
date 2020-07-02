---
ms.openlocfilehash: 148312743dd274728b178951548889dc3a680528
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614467"
---
### <a name="change-in-path-separator-character-in-fullname-property-of-ziparchiveentry-objects"></a><span data-ttu-id="0e980-101">Changement du caractère séparateur de chemin dans la propriété FullName des objets ZipArchiveEntry</span><span class="sxs-lookup"><span data-stu-id="0e980-101">Change in path separator character in FullName property of ZipArchiveEntry objects</span></span>

#### <a name="details"></a><span data-ttu-id="0e980-102">Détails</span><span class="sxs-lookup"><span data-stu-id="0e980-102">Details</span></span>

<span data-ttu-id="0e980-103">Pour les applications qui ciblent le .NET Framework 4.6.1 et les versions ultérieures, le caractère de séparation du chemin d’accès est passé d’une barre oblique inverse (" \" ) à une barre oblique ("/") dans la <xref:System.IO.Compression.ZipArchiveEntry.FullName> propriété des <xref:System.IO.Compression.ZipArchiveEntry> objets créés par les surcharges de la <xref:System.IO.Compression.ZipFile.CreateFromDirectory%2A> méthode.</span><span class="sxs-lookup"><span data-stu-id="0e980-103">For apps that target the .NET Framework 4.6.1 and later versions, the path separator character has changed from a backslash ("\") to a forward slash ("/") in the <xref:System.IO.Compression.ZipArchiveEntry.FullName> property of <xref:System.IO.Compression.ZipArchiveEntry>  objects created by overloads of the <xref:System.IO.Compression.ZipFile.CreateFromDirectory%2A> method.</span></span> <span data-ttu-id="0e980-104">L’implémentation .NET est ainsi conforme à la section 4.4.17.1 des [Spécifications relatives au format des fichiers ZIP](https://pkware.cachefly.net/webdocs/casestudies/APPNOTE.TXT) et permet aux archives ZIP d’être décompressées sur des systèmes non Windows.</span><span class="sxs-lookup"><span data-stu-id="0e980-104">The change brings the .NET implementation into conformity with section 4.4.17.1 of the [.ZIP File Format Specification](https://pkware.cachefly.net/webdocs/casestudies/APPNOTE.TXT) and allows .ZIP archives to be decompressed on non-Windows systems.</span></span><br /><span data-ttu-id="0e980-105">La décompression d’un fichier zip créé par une application qui cible une version antérieure du .NET Framework sur les systèmes d’exploitation non-Windows, tels que les ordinateurs Macintosh, ne permet pas de conserver la structure de répertoire.</span><span class="sxs-lookup"><span data-stu-id="0e980-105">Decompressing a zip file created by an app that targets a previous version of the .NET Framework on non-Windows operating systems such as the Macintosh fails to preserve the directory structure.</span></span> <span data-ttu-id="0e980-106">Par exemple, pour les ordinateurs Macintosh, cela crée un ensemble de fichiers dont le nom concatène le chemin d’accès, ainsi que toute barre oblique inverse («  ») et le nom de fichier.</span><span class="sxs-lookup"><span data-stu-id="0e980-106">For example, on the Macintosh, it creates a set of files whose filename concatenates the directory path, along with any backslash ("") characters, and the filename.</span></span> <span data-ttu-id="0e980-107">Par conséquent, la structure de répertoires des fichiers décompressés n’est pas conservée.</span><span class="sxs-lookup"><span data-stu-id="0e980-107">As a result, the directory structure of decompressed files is not preserved.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="0e980-108">Suggestion</span><span class="sxs-lookup"><span data-stu-id="0e980-108">Suggestion</span></span>

<span data-ttu-id="0e980-109">Impact de cette modification sur. Les fichiers ZIP décompressés sur le système d’exploitation Windows par les API dans l' <xref:System.IO?displayProperty=nameWithType> espace de noms .NET Framework doivent être minimaux, puisque ces API peuvent gérer en toute transparence une barre oblique (« / ») ou une barre oblique inverse («» \" ) comme séparateur de chemin.</span><span class="sxs-lookup"><span data-stu-id="0e980-109">The impact of this change on .ZIP files that are decompressed on the Windows operating system by APIs in the .NET Framework <xref:System.IO?displayProperty=nameWithType> namespace should be minimal, since these APIs can seamlessly handle either a forward slash ("/") or a backslash ("\") as the path separator character.</span></span><br /><span data-ttu-id="0e980-110">Si cette modification n’est pas souhaitable, vous pouvez choisir de l’annuler en ajoutant un paramètre de configuration à la [<](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) section de votre fichier de configuration de l’application.</span><span class="sxs-lookup"><span data-stu-id="0e980-110">If this change is undesirable, you can opt out of it by adding a configuration setting to the [<](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) section of your application configuration file.</span></span> <span data-ttu-id="0e980-111">L’exemple suivant montre la section `<runtime>` et l’option d’annulation `Switch.System.IO.Compression.ZipFile.UseBackslash` :</span><span class="sxs-lookup"><span data-stu-id="0e980-111">The following example shows both the `<runtime>` section and the `Switch.System.IO.Compression.ZipFile.UseBackslash` opt-out switch:</span></span>

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.IO.Compression.ZipFile.UseBackslash=true" />
</runtime>
```

<span data-ttu-id="0e980-112">En outre, les applications qui ciblent des versions antérieures du .NET Framework mais s’exécutent sur le .NET Framework 4.6.1 et les versions ultérieures peuvent accepter ce comportement en ajoutant un paramètre de configuration à la [<](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) section du fichier de configuration de l’application.</span><span class="sxs-lookup"><span data-stu-id="0e980-112">In addition, apps that target previous versions of the .NET Framework but are running on the .NET Framework 4.6.1 and later versions can opt in to this behavior by adding a configuration setting to the [<](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) section of the application configuration file.</span></span> <span data-ttu-id="0e980-113">L’exemple suivant montre la section `<runtime>` et l’option d’activation `Switch.System.IO.Compression.ZipFile.UseBackslash`.</span><span class="sxs-lookup"><span data-stu-id="0e980-113">The following shows both the `<runtime>` section and the `Switch.System.IO.Compression.ZipFile.UseBackslash` opt-in switch.</span></span>

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.IO.Compression.ZipFile.UseBackslash=false" />
</runtime>
```

| <span data-ttu-id="0e980-114">Nom</span><span class="sxs-lookup"><span data-stu-id="0e980-114">Name</span></span>    | <span data-ttu-id="0e980-115">Valeur</span><span class="sxs-lookup"><span data-stu-id="0e980-115">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="0e980-116">Étendue</span><span class="sxs-lookup"><span data-stu-id="0e980-116">Scope</span></span>   | <span data-ttu-id="0e980-117">Edge</span><span class="sxs-lookup"><span data-stu-id="0e980-117">Edge</span></span>        |
| <span data-ttu-id="0e980-118">Version</span><span class="sxs-lookup"><span data-stu-id="0e980-118">Version</span></span> | <span data-ttu-id="0e980-119">4.6.1</span><span class="sxs-lookup"><span data-stu-id="0e980-119">4.6.1</span></span>       |
| <span data-ttu-id="0e980-120">Type</span><span class="sxs-lookup"><span data-stu-id="0e980-120">Type</span></span>    | <span data-ttu-id="0e980-121">Reciblage</span><span class="sxs-lookup"><span data-stu-id="0e980-121">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="0e980-122">API affectées</span><span class="sxs-lookup"><span data-stu-id="0e980-122">Affected APIs</span></span>

- <xref:System.IO.Compression.ZipFile.CreateFromDirectory(System.String,System.String)?displayProperty=nameWithType>
- <xref:System.IO.Compression.ZipFile.CreateFromDirectory(System.String,System.String,System.IO.Compression.CompressionLevel,System.Boolean)?displayProperty=nameWithType>
- <xref:System.IO.Compression.ZipFile.CreateFromDirectory(System.String,System.String,System.IO.Compression.CompressionLevel,System.Boolean,System.Text.Encoding)?displayProperty=nameWithType>
