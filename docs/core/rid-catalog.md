---
title: Catalogue d’identificateurs de Runtime .NET (RID)
description: En savoir plus sur l’identificateur de Runtime (RID) et la façon dont les RID sont utilisés dans .NET.
ms.date: 01/28/2021
ms.openlocfilehash: e5e1c4712965211b25a02b14a7cf2c91d74d8306
ms.sourcegitcommit: 68c9d9d9a97aab3b59d388914004b5474cf1dbd7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/30/2021
ms.locfileid: "99216003"
---
# <a name="net-rid-catalog"></a><span data-ttu-id="b0db3-103">Catalogue RID .NET</span><span class="sxs-lookup"><span data-stu-id="b0db3-103">.NET RID Catalog</span></span>

<span data-ttu-id="b0db3-104">RID est l’abréviation de *Runtime identifier*.</span><span class="sxs-lookup"><span data-stu-id="b0db3-104">RID is short for *Runtime Identifier*.</span></span> <span data-ttu-id="b0db3-105">Les valeurs RID sont utilisées pour identifier les plateformes cibles où l’application s’exécute.</span><span class="sxs-lookup"><span data-stu-id="b0db3-105">RID values are used to identify target platforms where the application runs.</span></span>
<span data-ttu-id="b0db3-106">Elles sont utilisées par les packages .NET pour représenter des ressources spécifiques à une plateforme dans les packages NuGet.</span><span class="sxs-lookup"><span data-stu-id="b0db3-106">They're used by .NET packages to represent platform-specific assets in NuGet packages.</span></span> <span data-ttu-id="b0db3-107">Les valeurs suivantes sont des exemples d’identificateurs RID : `linux-x64`, `ubuntu.14.04-x64`, `win7-x64` ou `osx.10.12-x64`.</span><span class="sxs-lookup"><span data-stu-id="b0db3-107">The following values are examples of RIDs: `linux-x64`, `ubuntu.14.04-x64`, `win7-x64`, or `osx.10.12-x64`.</span></span>
<span data-ttu-id="b0db3-108">Pour les packages ayant des dépendances natives, les RID désignent les plateformes sur lesquelles ils peuvent être restaurés.</span><span class="sxs-lookup"><span data-stu-id="b0db3-108">For the packages with native dependencies, the RID designates on which platforms the package can be restored.</span></span>

<span data-ttu-id="b0db3-109">Un seul RID peut être défini dans l’élément `<RuntimeIdentifier>` de votre fichier projet.</span><span class="sxs-lookup"><span data-stu-id="b0db3-109">A single RID can be set in the `<RuntimeIdentifier>` element of your project file.</span></span> <span data-ttu-id="b0db3-110">Les RID multiples peuvent être définis sous forme de liste de valeurs séparées par des points-virgules dans l’élément `<RuntimeIdentifiers>` du fichier projet.</span><span class="sxs-lookup"><span data-stu-id="b0db3-110">Multiple RIDs can be defined as a semicolon-delimited list in the project file's `<RuntimeIdentifiers>` element.</span></span> <span data-ttu-id="b0db3-111">Elles sont également utilisées par le biais de l' `--runtime` option avec les [commandes CLI .net](./tools/index.md)suivantes :</span><span class="sxs-lookup"><span data-stu-id="b0db3-111">They're also used via the `--runtime` option with the following [.NET CLI commands](./tools/index.md):</span></span>

- [<span data-ttu-id="b0db3-112">dotnet build</span><span class="sxs-lookup"><span data-stu-id="b0db3-112">dotnet build</span></span>](./tools/dotnet-build.md)
- [<span data-ttu-id="b0db3-113">dotnet clean</span><span class="sxs-lookup"><span data-stu-id="b0db3-113">dotnet clean</span></span>](./tools/dotnet-clean.md)
- [<span data-ttu-id="b0db3-114">dotnet pack</span><span class="sxs-lookup"><span data-stu-id="b0db3-114">dotnet pack</span></span>](./tools/dotnet-pack.md)
- [<span data-ttu-id="b0db3-115">dotnet publish</span><span class="sxs-lookup"><span data-stu-id="b0db3-115">dotnet publish</span></span>](./tools/dotnet-publish.md)
- [<span data-ttu-id="b0db3-116">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="b0db3-116">dotnet restore</span></span>](./tools/dotnet-restore.md)
- [<span data-ttu-id="b0db3-117">dotnet run</span><span class="sxs-lookup"><span data-stu-id="b0db3-117">dotnet run</span></span>](./tools/dotnet-run.md)
- [<span data-ttu-id="b0db3-118">dotnet store</span><span class="sxs-lookup"><span data-stu-id="b0db3-118">dotnet store</span></span>](./tools/dotnet-store.md)

<span data-ttu-id="b0db3-119">Les RID qui représentent des systèmes d’exploitation concrets suivent généralement ce modèle : `[os].[version]-[architecture]-[additional qualifiers]` où :</span><span class="sxs-lookup"><span data-stu-id="b0db3-119">RIDs that represent concrete operating systems usually follow this pattern: `[os].[version]-[architecture]-[additional qualifiers]` where:</span></span>

- <span data-ttu-id="b0db3-120">`[os]` représente le moniker du système d’exploitation/de la plateforme.</span><span class="sxs-lookup"><span data-stu-id="b0db3-120">`[os]` is the operating/platform system moniker.</span></span> <span data-ttu-id="b0db3-121">Par exemple : `ubuntu`.</span><span class="sxs-lookup"><span data-stu-id="b0db3-121">For example, `ubuntu`.</span></span>

- <span data-ttu-id="b0db3-122">`[version]` représente la version du système d’exploitation sous la forme d’un numéro de version (`.`) séparé par un point.</span><span class="sxs-lookup"><span data-stu-id="b0db3-122">`[version]` is the operating system version in the form of a dot-separated (`.`) version number.</span></span> <span data-ttu-id="b0db3-123">Par exemple : `15.10`.</span><span class="sxs-lookup"><span data-stu-id="b0db3-123">For example, `15.10`.</span></span>

  - <span data-ttu-id="b0db3-124">La version **ne doit pas** correspondre à des versions marketing, car celles-ci représentent souvent plusieurs versions distinctes du système d’exploitation avec une surface d’exposition variable des API de la plateforme.</span><span class="sxs-lookup"><span data-stu-id="b0db3-124">The version **shouldn't** be marketing versions, as they often represent multiple discrete versions of the operating system with varying platform API surface area.</span></span>

- <span data-ttu-id="b0db3-125">`[architecture]` représente l’architecture de processeur.</span><span class="sxs-lookup"><span data-stu-id="b0db3-125">`[architecture]` is the processor architecture.</span></span> <span data-ttu-id="b0db3-126">Par exemple : `x86`, `x64`, `arm` ou `arm64`.</span><span class="sxs-lookup"><span data-stu-id="b0db3-126">For example: `x86`, `x64`, `arm`, or `arm64`.</span></span>

- <span data-ttu-id="b0db3-127">`[additional qualifiers]` permet de distinguer davantage les plateformes.</span><span class="sxs-lookup"><span data-stu-id="b0db3-127">`[additional qualifiers]` further differentiate different platforms.</span></span> <span data-ttu-id="b0db3-128">Par exemple : `aot`.</span><span class="sxs-lookup"><span data-stu-id="b0db3-128">For example: `aot`.</span></span>

## <a name="rid-graph"></a><span data-ttu-id="b0db3-129">Graphe RID</span><span class="sxs-lookup"><span data-stu-id="b0db3-129">RID graph</span></span>

<span data-ttu-id="b0db3-130">Le graphe RID ou le graphe de secours du runtime consiste en une liste d’identificateurs RID compatibles entre eux.</span><span class="sxs-lookup"><span data-stu-id="b0db3-130">The RID graph or runtime fallback graph is a list of RIDs that are compatible with each other.</span></span> <span data-ttu-id="b0db3-131">Les RID sont définis dans le package [Microsoft.NETCore.Platforms](https://www.nuget.org/packages/Microsoft.NETCore.Platforms/).</span><span class="sxs-lookup"><span data-stu-id="b0db3-131">The RIDs are defined in the [Microsoft.NETCore.Platforms](https://www.nuget.org/packages/Microsoft.NETCore.Platforms/) package.</span></span> <span data-ttu-id="b0db3-132">Vous pouvez voir la liste des RID pris en charge et le graphique RID dans le [*runtime.jssur*](https://github.com/dotnet/runtime/blob/master/src/libraries/Microsoft.NETCore.Platforms/pkg/runtime.json) le fichier, qui se trouve dans le `dotnet/runtime` référentiel.</span><span class="sxs-lookup"><span data-stu-id="b0db3-132">You can see the list of supported RIDs and the RID graph in the [*runtime.json*](https://github.com/dotnet/runtime/blob/master/src/libraries/Microsoft.NETCore.Platforms/pkg/runtime.json) file, which is located in the `dotnet/runtime` repository.</span></span> <span data-ttu-id="b0db3-133">Dans ce fichier, vous pouvez voir que tous les RID, sauf celui de base, contiennent une instruction `"#import"`.</span><span class="sxs-lookup"><span data-stu-id="b0db3-133">In this file, you can see that all RIDs, except for the base one, contain an `"#import"` statement.</span></span> <span data-ttu-id="b0db3-134">Ces instructions indiquent des RID compatibles.</span><span class="sxs-lookup"><span data-stu-id="b0db3-134">These statements indicate compatible RIDs.</span></span>

<span data-ttu-id="b0db3-135">Lorsque NuGet restaure des packages, il tente de trouver une correspondance exacte pour le runtime spécifié.</span><span class="sxs-lookup"><span data-stu-id="b0db3-135">When NuGet restores packages, it tries to find an exact match for the specified runtime.</span></span>
<span data-ttu-id="b0db3-136">Si aucune correspondance exacte n’est trouvée, NuGet remonte le graphe jusqu'à ce qu’il trouve le système compatible le plus proche selon le graphe RID.</span><span class="sxs-lookup"><span data-stu-id="b0db3-136">If an exact match is not found, NuGet walks back the graph until it finds the closest compatible system according to the RID graph.</span></span>

<span data-ttu-id="b0db3-137">L’exemple suivant est l’entrée réelle pour le RID `osx.10.12-x64` :</span><span class="sxs-lookup"><span data-stu-id="b0db3-137">The following example is the actual entry for the `osx.10.12-x64` RID:</span></span>

```json
"osx.10.12-x64": {
    "#import": [ "osx.10.12", "osx.10.11-x64" ]
}
```

<span data-ttu-id="b0db3-138">Le RID ci-dessus indique que `osx.10.12-x64` importe `osx.10.11-x64`.</span><span class="sxs-lookup"><span data-stu-id="b0db3-138">The above RID specifies that `osx.10.12-x64` imports `osx.10.11-x64`.</span></span> <span data-ttu-id="b0db3-139">Donc, lorsque NuGet restaure des packages, il tente de trouver une correspondance exacte pour `osx.10.12-x64` dans le package.</span><span class="sxs-lookup"><span data-stu-id="b0db3-139">So, when NuGet restores packages, it tries to find an exact match for  `osx.10.12-x64` in the package.</span></span> <span data-ttu-id="b0db3-140">Si NuGet ne trouve pas le runtime spécifique, il peut restaurer des packages qui spécifient des runtimes `osx.10.11-x64`, par exemple.</span><span class="sxs-lookup"><span data-stu-id="b0db3-140">If NuGet cannot find the specific runtime, it can restore packages that specify `osx.10.11-x64` runtimes, for example.</span></span>

<span data-ttu-id="b0db3-141">L’exemple suivant illustre un graphe RID légèrement plus grand également défini dans le fichier *runtime.json* :</span><span class="sxs-lookup"><span data-stu-id="b0db3-141">The following example shows a slightly bigger RID graph also defined in the *runtime.json*  file:</span></span>

```
    win7-x64    win7-x86
       |   \   /    |
       |   win7     |
       |     |      |
    win-x64  |  win-x86
          \  |  /
            win
             |
            any
```

<span data-ttu-id="b0db3-142">Tous les RID sont finalement remappés au RID `any` racine.</span><span class="sxs-lookup"><span data-stu-id="b0db3-142">All RIDs eventually map back to the root `any` RID.</span></span>

<span data-ttu-id="b0db3-143">Lorsque vous utilisez les RID, il existe quelques remarques que vous devez garder à l’esprit :</span><span class="sxs-lookup"><span data-stu-id="b0db3-143">There are some considerations about RIDs that you have to keep in mind when working with them:</span></span>

- <span data-ttu-id="b0db3-144">N’essayez pas d’analyser les RID pour récupérer des composants.</span><span class="sxs-lookup"><span data-stu-id="b0db3-144">Don't try to parse RIDs to retrieve component parts.</span></span>
- <span data-ttu-id="b0db3-145">Ne générez pas les RID par programme.</span><span class="sxs-lookup"><span data-stu-id="b0db3-145">Don't build RIDs programmatically.</span></span>
- <span data-ttu-id="b0db3-146">Utilisez des RID déjà définis pour la plateforme.</span><span class="sxs-lookup"><span data-stu-id="b0db3-146">Use RIDs that are already defined for the platform.</span></span>
- <span data-ttu-id="b0db3-147">Les RID se devant d’être spécifiques, ne déduisez rien de leur valeur réelle.</span><span class="sxs-lookup"><span data-stu-id="b0db3-147">The RIDs need to be specific, so don't assume anything from the actual RID value.</span></span>

## <a name="using-rids"></a><span data-ttu-id="b0db3-148">Utilisation de RID</span><span class="sxs-lookup"><span data-stu-id="b0db3-148">Using RIDs</span></span>

<span data-ttu-id="b0db3-149">Pour utiliser des RID, vous devez savoir lesquels existent.</span><span class="sxs-lookup"><span data-stu-id="b0db3-149">To be able to use RIDs, you have to know which RIDs exist.</span></span> <span data-ttu-id="b0db3-150">De nouvelles valeurs sont régulièrement ajoutées à la plateforme.</span><span class="sxs-lookup"><span data-stu-id="b0db3-150">New values are added regularly to the platform.</span></span>
<span data-ttu-id="b0db3-151">Pour obtenir la version la plus récente et la plus complète, consultez le [runtime.js](https://github.com/dotnet/runtime/blob/master/src/libraries/Microsoft.NETCore.Platforms/pkg/runtime.json) fichier dans le `dotnet/runtime` référentiel.</span><span class="sxs-lookup"><span data-stu-id="b0db3-151">For the latest and complete version, see the [runtime.json](https://github.com/dotnet/runtime/blob/master/src/libraries/Microsoft.NETCore.Platforms/pkg/runtime.json) file in the `dotnet/runtime` repository.</span></span>

<span data-ttu-id="b0db3-152">Les RID portables sont des valeurs ajoutées au graphique RID qui ne sont pas liées à une version spécifique ou à une distribution de système d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="b0db3-152">Portable RIDs are values added to the RID graph that aren't tied to a specific version or OS distribution.</span></span> <span data-ttu-id="b0db3-153">Il s’agit du choix privilégié, en particulier lors du traitement de plusieurs distributions Linux, car la plupart des RID de distribution sont mappés aux RID portables.</span><span class="sxs-lookup"><span data-stu-id="b0db3-153">They are the preferred choice, especially when dealing with multiple Linux distros since most distribution RIDs are mapped to the portable RIDs.</span></span>

<span data-ttu-id="b0db3-154">La liste suivante présente un petit sous-ensemble des RID les plus courants utilisés pour chaque système d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="b0db3-154">The following list shows a small subset of the most common RIDs used for each OS.</span></span>

## <a name="windows-rids"></a><span data-ttu-id="b0db3-155">RID Windows</span><span class="sxs-lookup"><span data-stu-id="b0db3-155">Windows RIDs</span></span>

<span data-ttu-id="b0db3-156">Seules les valeurs courantes sont présentées.</span><span class="sxs-lookup"><span data-stu-id="b0db3-156">Only common values are listed.</span></span> <span data-ttu-id="b0db3-157">Pour obtenir la version la plus récente et la plus complète, consultez le [runtime.js](https://github.com/dotnet/runtime/blob/master/src/libraries/Microsoft.NETCore.Platforms/pkg/runtime.json) fichier dans le `dotnet/runtime` référentiel.</span><span class="sxs-lookup"><span data-stu-id="b0db3-157">For the latest and complete version, see the [runtime.json](https://github.com/dotnet/runtime/blob/master/src/libraries/Microsoft.NETCore.Platforms/pkg/runtime.json) file in the `dotnet/runtime` repository.</span></span>

- <span data-ttu-id="b0db3-158">Portable</span><span class="sxs-lookup"><span data-stu-id="b0db3-158">Portable</span></span>
  - `win-x64`
  - `win-x86`
  - `win-arm`
  - `win-arm64`
- <span data-ttu-id="b0db3-159">Windows 7 / Windows Server 2008 R2</span><span class="sxs-lookup"><span data-stu-id="b0db3-159">Windows 7 / Windows Server 2008 R2</span></span>
  - `win7-x64`
  - `win7-x86`
- <span data-ttu-id="b0db3-160">Windows 8.1 / Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="b0db3-160">Windows 8.1 / Windows Server 2012 R2</span></span>
  - `win81-x64`
  - `win81-x86`
  - `win81-arm`
- <span data-ttu-id="b0db3-161">Windows 10 / Windows Server 2016</span><span class="sxs-lookup"><span data-stu-id="b0db3-161">Windows 10 / Windows Server 2016</span></span>
  - `win10-x64`
  - `win10-x86`
  - `win10-arm`
  - `win10-arm64`

<span data-ttu-id="b0db3-162">Pour plus d’informations, consultez [.net Dependencies and Requirements](./install/windows.md#dependencies).</span><span class="sxs-lookup"><span data-stu-id="b0db3-162">For more information, see [.NET dependencies and requirements](./install/windows.md#dependencies).</span></span>

## <a name="linux-rids"></a><span data-ttu-id="b0db3-163">RID Linux</span><span class="sxs-lookup"><span data-stu-id="b0db3-163">Linux RIDs</span></span>

<span data-ttu-id="b0db3-164">Seules les valeurs courantes sont présentées.</span><span class="sxs-lookup"><span data-stu-id="b0db3-164">Only common values are listed.</span></span> <span data-ttu-id="b0db3-165">Pour obtenir la version la plus récente et la plus complète, consultez le [runtime.js](https://github.com/dotnet/runtime/blob/master/src/libraries/Microsoft.NETCore.Platforms/pkg/runtime.json) fichier dans le `dotnet/runtime` référentiel.</span><span class="sxs-lookup"><span data-stu-id="b0db3-165">For the latest and complete version, see the [runtime.json](https://github.com/dotnet/runtime/blob/master/src/libraries/Microsoft.NETCore.Platforms/pkg/runtime.json) file in the `dotnet/runtime` repository.</span></span> <span data-ttu-id="b0db3-166">Les appareils dont la distribution ne figure pas ci-dessous sont susceptibles de fonctionner avec l’un des RID portables.</span><span class="sxs-lookup"><span data-stu-id="b0db3-166">Devices running a distribution not listed below may work with one of the Portable RIDs.</span></span> <span data-ttu-id="b0db3-167">Par exemple, les appareils Raspberry Pi exécutant une distribution Linux non listée peuvent être ciblés avec `linux-arm`.</span><span class="sxs-lookup"><span data-stu-id="b0db3-167">For example, Raspberry Pi devices running a Linux distribution not listed can be targeted with `linux-arm`.</span></span>

- <span data-ttu-id="b0db3-168">Portable</span><span class="sxs-lookup"><span data-stu-id="b0db3-168">Portable</span></span>
  - <span data-ttu-id="b0db3-169">`linux-x64` (La plupart des distributions de bureau telles que CentOS, Debian, Fedora, Ubuntu et les dérivés)</span><span class="sxs-lookup"><span data-stu-id="b0db3-169">`linux-x64` (Most desktop distributions like CentOS, Debian, Fedora, Ubuntu, and derivatives)</span></span>
  - <span data-ttu-id="b0db3-170">`linux-musl-x64` (distributions légères utilisant [musl](https://wiki.musl-libc.org/projects-using-musl.html), comme Linux Alpine)</span><span class="sxs-lookup"><span data-stu-id="b0db3-170">`linux-musl-x64` (Lightweight distributions using [musl](https://wiki.musl-libc.org/projects-using-musl.html) like Alpine Linux)</span></span>
  - <span data-ttu-id="b0db3-171">`linux-arm` (Distributions Linux exécutées sur ARM comme Raspbian sur Raspberry pi Model 2 +)</span><span class="sxs-lookup"><span data-stu-id="b0db3-171">`linux-arm` (Linux distributions running on ARM like Raspbian on Raspberry Pi Model 2+)</span></span>
  - <span data-ttu-id="b0db3-172">`linux-arm64` (Distributions Linux s’exécutant sur un ARM 64 bits comme Ubuntu Server 64-bit sur Raspberry pi Model 3 +)</span><span class="sxs-lookup"><span data-stu-id="b0db3-172">`linux-arm64` (Linux distributions running on 64-bit ARM like Ubuntu Server 64-bit on Raspberry Pi Model 3+)</span></span>
- <span data-ttu-id="b0db3-173">Red Hat Enterprise Linux</span><span class="sxs-lookup"><span data-stu-id="b0db3-173">Red Hat Enterprise Linux</span></span>
  - <span data-ttu-id="b0db3-174">`rhel-x64` (remplacé par `linux-x64` pour RHEL après la version 6)</span><span class="sxs-lookup"><span data-stu-id="b0db3-174">`rhel-x64` (Superseded by `linux-x64` for RHEL above version 6)</span></span>
  - `rhel.6-x64`
- <span data-ttu-id="b0db3-175">Tizen</span><span class="sxs-lookup"><span data-stu-id="b0db3-175">Tizen</span></span>
  - `tizen`
  - `tizen.4.0.0`
  - `tizen.5.0.0`

<span data-ttu-id="b0db3-176">Pour plus d’informations, consultez [.net Dependencies and Requirements](./install/linux.md).</span><span class="sxs-lookup"><span data-stu-id="b0db3-176">For more information, see [.NET dependencies and requirements](./install/linux.md).</span></span>

## <a name="macos-rids"></a><span data-ttu-id="b0db3-177">RID macOS</span><span class="sxs-lookup"><span data-stu-id="b0db3-177">macOS RIDs</span></span>

<span data-ttu-id="b0db3-178">Les RID macOS utilisent l’ancien logo « OSX ».</span><span class="sxs-lookup"><span data-stu-id="b0db3-178">macOS RIDs use the older "OSX" branding.</span></span> <span data-ttu-id="b0db3-179">Seules les valeurs courantes sont présentées.</span><span class="sxs-lookup"><span data-stu-id="b0db3-179">Only common values are listed.</span></span> <span data-ttu-id="b0db3-180">Pour obtenir la version la plus récente et la plus complète, consultez le [runtime.js](https://github.com/dotnet/runtime/blob/master/src/libraries/Microsoft.NETCore.Platforms/pkg/runtime.json) fichier dans le `dotnet/runtime` référentiel.</span><span class="sxs-lookup"><span data-stu-id="b0db3-180">For the latest and complete version, see the [runtime.json](https://github.com/dotnet/runtime/blob/master/src/libraries/Microsoft.NETCore.Platforms/pkg/runtime.json) file in the `dotnet/runtime` repository.</span></span>

- <span data-ttu-id="b0db3-181">Portable</span><span class="sxs-lookup"><span data-stu-id="b0db3-181">Portable</span></span>
  - <span data-ttu-id="b0db3-182">`osx-x64` (la version minimale du système d’exploitation est macOS 10.12 Sierra)</span><span class="sxs-lookup"><span data-stu-id="b0db3-182">`osx-x64` (Minimum OS version is macOS 10.12 Sierra)</span></span>
- <span data-ttu-id="b0db3-183">macOS 10.10  Yosemite</span><span class="sxs-lookup"><span data-stu-id="b0db3-183">macOS 10.10  Yosemite</span></span>
  - `osx.10.10-x64`
- <span data-ttu-id="b0db3-184">macOS 10.11 El Capitan</span><span class="sxs-lookup"><span data-stu-id="b0db3-184">macOS 10.11 El Capitan</span></span>
  - `osx.10.11-x64`
- <span data-ttu-id="b0db3-185">macOS 10.12 Sierra</span><span class="sxs-lookup"><span data-stu-id="b0db3-185">macOS 10.12 Sierra</span></span>
  - `osx.10.12-x64`
- <span data-ttu-id="b0db3-186">macOS 10.13 High Sierra</span><span class="sxs-lookup"><span data-stu-id="b0db3-186">macOS 10.13 High Sierra</span></span>
  - `osx.10.13-x64`
- <span data-ttu-id="b0db3-187">macOS 10.14 Mojave</span><span class="sxs-lookup"><span data-stu-id="b0db3-187">macOS 10.14 Mojave</span></span>
  - `osx.10.14-x64`
- <span data-ttu-id="b0db3-188">macOS 10.15 Catalina</span><span class="sxs-lookup"><span data-stu-id="b0db3-188">macOS 10.15 Catalina</span></span>
  - `osx.10.15-x64`
- <span data-ttu-id="b0db3-189">macOS 11,01 Big sur</span><span class="sxs-lookup"><span data-stu-id="b0db3-189">macOS 11.01 Big Sur</span></span>
  - `osx.11.0-x64`
  - `osx.11.0-arm64`

<span data-ttu-id="b0db3-190">Pour plus d’informations, consultez [.net Dependencies and Requirements](./install/macos.md#dependencies).</span><span class="sxs-lookup"><span data-stu-id="b0db3-190">For more information, see [.NET dependencies and requirements](./install/macos.md#dependencies).</span></span>

## <a name="see-also"></a><span data-ttu-id="b0db3-191">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b0db3-191">See also</span></span>

- [<span data-ttu-id="b0db3-192">ID du runtime</span><span class="sxs-lookup"><span data-stu-id="b0db3-192">Runtime IDs</span></span>](https://github.com/dotnet/runtime/blob/master/src/libraries/Microsoft.NETCore.Platforms/readme.md)
