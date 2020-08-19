---
ms.openlocfilehash: a635e2ed6a735b5234c92fd8f5ffa1685fe9373e
ms.sourcegitcommit: 8bfeb5930ca48b2ee6053f16082dcaf24d46d221
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/18/2020
ms.locfileid: "88558172"
---
### <a name="microsoftdotnetplatformabstractions-package-removed"></a><span data-ttu-id="d5f90-101">Package Microsoft. DotNet. PlatformAbstractions supprimé</span><span class="sxs-lookup"><span data-stu-id="d5f90-101">Microsoft.DotNet.PlatformAbstractions package removed</span></span>

<span data-ttu-id="d5f90-102">Aucune nouvelle version du [package NuGet Microsoft. dotnet. PlatformAbstractions](https://www.nuget.org/packages/Microsoft.DotNet.PlatformAbstractions/) ne sera produite.</span><span class="sxs-lookup"><span data-stu-id="d5f90-102">No new versions of the [Microsoft.DotNet.PlatformAbstractions NuGet package](https://www.nuget.org/packages/Microsoft.DotNet.PlatformAbstractions/) will be produced.</span></span>

#### <a name="change-description"></a><span data-ttu-id="d5f90-103">Description de la modification</span><span class="sxs-lookup"><span data-stu-id="d5f90-103">Change description</span></span>

<span data-ttu-id="d5f90-104">Auparavant, les nouvelles versions de la <xref:Microsoft.DotNet.PlatformAbstractions?displayProperty=fullName> bibliothèque étaient produites avec les nouvelles versions de .net core.</span><span class="sxs-lookup"><span data-stu-id="d5f90-104">Previously, new versions of the <xref:Microsoft.DotNet.PlatformAbstractions?displayProperty=fullName> library were produced alongside new versions of .NET Core.</span></span> <span data-ttu-id="d5f90-105">À l’avenir, aucune nouvelle fonctionnalité ne sera ajoutée à la bibliothèque et aucune nouvelle version principale ne sera publiée.</span><span class="sxs-lookup"><span data-stu-id="d5f90-105">Going forward, no new functionality will be added to the library, and no new major versions will be released.</span></span> <span data-ttu-id="d5f90-106">Toutefois, les versions existantes de la bibliothèque continuent de fonctionner et seront desservies.</span><span class="sxs-lookup"><span data-stu-id="d5f90-106">However, existing versions of the library will continue to work and be serviced.</span></span>

<span data-ttu-id="d5f90-107">La <xref:Microsoft.DotNet.PlatformAbstractions?displayProperty=fullName> bibliothèque chevauche les API qui sont déjà établies dans System. \* namespaces.</span><span class="sxs-lookup"><span data-stu-id="d5f90-107">The <xref:Microsoft.DotNet.PlatformAbstractions?displayProperty=fullName> library overlaps with APIs that are already established in the System.\* namespaces.</span></span> <span data-ttu-id="d5f90-108">En outre, certaines <xref:Microsoft.DotNet.PlatformAbstractions> API n’ont pas été conçues avec le même niveau de surveillance et de prise en charge à long terme que le reste du système. \* Interfaces.</span><span class="sxs-lookup"><span data-stu-id="d5f90-108">Also, some <xref:Microsoft.DotNet.PlatformAbstractions> APIs weren't designed with the same level of scrutiny and long-term supportability as the rest of the System.\* APIs.</span></span> <span data-ttu-id="d5f90-109">Par exemple, <xref:Microsoft.DotNet.PlatformAbstractions> utilise l' `Platform` énumération pour décrire la plateforme du système d’exploitation actuel.</span><span class="sxs-lookup"><span data-stu-id="d5f90-109">For example, <xref:Microsoft.DotNet.PlatformAbstractions> uses the `Platform` enumeration to describe the current operating system platform.</span></span> <span data-ttu-id="d5f90-110">Cette conception d’énumération a été explicitement rejetée lorsque l' <xref:System.Runtime.InteropServices.RuntimeInformation.IsOSPlatform(System.Runtime.InteropServices.OSPlatform)?displayProperty=nameWithType> API a été conçue, afin de permettre de nouvelles plateformes et une flexibilité future.</span><span class="sxs-lookup"><span data-stu-id="d5f90-110">This enumeration design was explicitly rejected when the <xref:System.Runtime.InteropServices.RuntimeInformation.IsOSPlatform(System.Runtime.InteropServices.OSPlatform)?displayProperty=nameWithType> API was designed, to allow for new platforms and future flexibility.</span></span>

<span data-ttu-id="d5f90-111">Les scénarios activés par la <xref:Microsoft.DotNet.PlatformAbstractions?displayProperty=fullName> bibliothèque sont désormais possibles sans lui.</span><span class="sxs-lookup"><span data-stu-id="d5f90-111">The scenarios enabled by the <xref:Microsoft.DotNet.PlatformAbstractions?displayProperty=fullName> library are now possible without it.</span></span> <span data-ttu-id="d5f90-112">Les versions existantes continueront à fonctionner, même dans .NET 5,0 et versions ultérieures, et seront servies avec les versions précédentes de .NET Core.</span><span class="sxs-lookup"><span data-stu-id="d5f90-112">Existing versions will continue to work, even in .NET 5.0 and later, and will be serviced along with previous versions of .NET Core.</span></span> <span data-ttu-id="d5f90-113">Toutefois, les nouvelles fonctionnalités ne seront pas ajoutées à la bibliothèque.</span><span class="sxs-lookup"><span data-stu-id="d5f90-113">However, new functionality won't be added to the library.</span></span> <span data-ttu-id="d5f90-114">Au lieu de cela, de nouvelles fonctionnalités seront ajoutées à d’autres bibliothèques et API.</span><span class="sxs-lookup"><span data-stu-id="d5f90-114">Instead, new functionality will be added to other libraries and APIs.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="d5f90-115">Version introduite</span><span class="sxs-lookup"><span data-stu-id="d5f90-115">Version introduced</span></span>

<span data-ttu-id="d5f90-116">5,0 Preview 6</span><span class="sxs-lookup"><span data-stu-id="d5f90-116">5.0 Preview 6</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="d5f90-117">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="d5f90-117">Recommended action</span></span>

- <span data-ttu-id="d5f90-118">Vous pouvez continuer à utiliser des versions antérieures de la bibliothèque si elles répondent à vos besoins.</span><span class="sxs-lookup"><span data-stu-id="d5f90-118">You can continue to use older versions of the library if they meet your requirements.</span></span>

- <span data-ttu-id="d5f90-119">Si les versions antérieures ne répondent pas à vos besoins, remplacez les utilisations des `PlatformAbstractions` API par les remplacements recommandés.</span><span class="sxs-lookup"><span data-stu-id="d5f90-119">If the older versions don't meet your requirements, replace usages of the `PlatformAbstractions` APIs with the recommended replacements.</span></span>

  | <span data-ttu-id="d5f90-120">`PlatformAbstractions` MOBILEVBACTIVEX</span><span class="sxs-lookup"><span data-stu-id="d5f90-120">`PlatformAbstractions` API</span></span> | <span data-ttu-id="d5f90-121">Remplacement recommandé</span><span class="sxs-lookup"><span data-stu-id="d5f90-121">Recommended replacement</span></span> |
  |-|-|
  | `ApplicationEnvironment.ApplicationBasePath` | <xref:System.AppContext.BaseDirectory?displayProperty=nameWithType> |
  | <xref:Microsoft.DotNet.PlatformAbstractions.HashCodeCombiner> | <xref:System.HashCode?displayProperty=nameWithType> |
  | `RuntimeEnvironment.GetRuntimeIdentifier()` | <xref:System.Runtime.InteropServices.RuntimeInformation.RuntimeIdentifier?displayProperty=nameWithType> |
  | `RuntimeEnvironment.OperatingSystemPlatform` | <xref:System.Runtime.InteropServices.RuntimeInformation.IsOSPlatform(System.Runtime.InteropServices.OSPlatform)?displayProperty=nameWithType> |
  | `RuntimeEnvironment.RuntimeArchitecture` | <xref:System.Runtime.InteropServices.RuntimeInformation.ProcessArchitecture?displayProperty=nameWithType> |
  | `RuntimeEnvironment.OperatingSystem` | <xref:System.Runtime.InteropServices.RuntimeInformation.OSDescription?displayProperty=nameWithType> |
  | `RuntimeEnvironment.OperatingSystemVersion` | <span data-ttu-id="d5f90-122"><xref:System.Runtime.InteropServices.RuntimeInformation.OSDescription?displayProperty=nameWithType> et <xref:System.Environment.OSVersion?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="d5f90-122"><xref:System.Runtime.InteropServices.RuntimeInformation.OSDescription?displayProperty=nameWithType> and <xref:System.Environment.OSVersion?displayProperty=nameWithType></span></span> |

  > [!NOTE]
  > <span data-ttu-id="d5f90-123">La plupart des cas d’usage pour et sont utilisés à des `RuntimeEnvironment.OperatingSystem` `RuntimeEnvironment.OperatingSystemVersion` fins d’affichage, par exemple, pour afficher à un utilisateur, journalisation et télémétrie.</span><span class="sxs-lookup"><span data-stu-id="d5f90-123">Most use cases for `RuntimeEnvironment.OperatingSystem` and `RuntimeEnvironment.OperatingSystemVersion` are for display purposes, for example, displaying to a user, logging, and telemetry.</span></span> <span data-ttu-id="d5f90-124">Il n’est pas recommandé de prendre des décisions d’exécution basées sur une version du système d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="d5f90-124">It's not recommended to make run-time decisions based on an operating system (OS) version.</span></span> <span data-ttu-id="d5f90-125"><xref:System.Environment.OSVersion?displayProperty=nameWithType>[retourne désormais la version correcte pour les](../../../../docs/core/compatibility/corefx.md#environmentosversion-returns-the-correct-operating-system-version) systèmes d’exploitation Windows et MacOS.</span><span class="sxs-lookup"><span data-stu-id="d5f90-125"><xref:System.Environment.OSVersion?displayProperty=nameWithType> now [returns the correct version](../../../../docs/core/compatibility/corefx.md#environmentosversion-returns-the-correct-operating-system-version) for Windows and macOS operating systems.</span></span> <span data-ttu-id="d5f90-126">Toutefois, pour la plupart des distributions UNIX, ce qui est considéré comme étant la « version du système d’exploitation » n’est pas aussi simple.</span><span class="sxs-lookup"><span data-stu-id="d5f90-126">However, for most Unix distributions, what is considered to be the "OS version" is not as straightforward.</span></span> <span data-ttu-id="d5f90-127">Par exemple, il peut s’agir de la version du noyau Linux, ou de la version distribution.</span><span class="sxs-lookup"><span data-stu-id="d5f90-127">For example, it could be the Linux kernel version, or it could be the distro version.</span></span> <span data-ttu-id="d5f90-128">Pour la plupart des plateformes UNIX, <xref:System.Environment.OSVersion?displayProperty=nameWithType> et <xref:System.Runtime.InteropServices.RuntimeInformation.OSDescription?displayProperty=nameWithType> retournent la version retournée par `uname` .</span><span class="sxs-lookup"><span data-stu-id="d5f90-128">For most Unix platforms, <xref:System.Environment.OSVersion?displayProperty=nameWithType> and <xref:System.Runtime.InteropServices.RuntimeInformation.OSDescription?displayProperty=nameWithType> return the version that's returned by `uname`.</span></span> <span data-ttu-id="d5f90-129">Pour obtenir le nom et la version des distribution Linux, l’approche recommandée consiste à lire le fichier */etc/OS-Release* .</span><span class="sxs-lookup"><span data-stu-id="d5f90-129">To get the Linux distro name and version information, the recommended approach is to read the */etc/os-release* file.</span></span>

#### <a name="category"></a><span data-ttu-id="d5f90-130">Category</span><span class="sxs-lookup"><span data-stu-id="d5f90-130">Category</span></span>

<span data-ttu-id="d5f90-131">Bibliothèques .NET Core</span><span class="sxs-lookup"><span data-stu-id="d5f90-131">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="d5f90-132">API affectées</span><span class="sxs-lookup"><span data-stu-id="d5f90-132">Affected APIs</span></span>

- `Microsoft.DotNet.PlatformAbstractions.ApplicationEnvironment.ApplicationBasePath`
- <xref:Microsoft.DotNet.PlatformAbstractions.HashCodeCombiner?displayProperty=fullName>
- `Microsoft.DotNet.PlatformAbstractions.RuntimeEnvironment.GetRuntimeIdentifier()`
- `Microsoft.DotNet.PlatformAbstractions.RuntimeEnvironment.OperatingSystem`
- `Microsoft.DotNet.PlatformAbstractions.RuntimeEnvironment.OperatingSystemPlatform`
- `Microsoft.DotNet.PlatformAbstractions.RuntimeEnvironment.OperatingSystemVersion`
- `Microsoft.DotNet.PlatformAbstractions.RuntimeEnvironment.RuntimeArchitecture`

<!--

#### Affected APIs

- `P:Microsoft.DotNet.PlatformAbstractions.ApplicationEnvironment.ApplicationBasePath`
- `T:Microsoft.DotNet.PlatformAbstractions.HashCodeCombiner`
- `M:Microsoft.DotNet.PlatformAbstractions.RuntimeEnvironment.GetRuntimeIdentifier`
- `P:Microsoft.DotNet.PlatformAbstractions.RuntimeEnvironment.OperatingSystem`
- `P:Microsoft.DotNet.PlatformAbstractions.RuntimeEnvironment.OperatingSystemPlatform`
- `P:Microsoft.DotNet.PlatformAbstractions.RuntimeEnvironment.OperatingSystemVersion`
- `P:Microsoft.DotNet.PlatformAbstractions.RuntimeEnvironment.RuntimeArchitecture`

-->
