---
title: Vue d’ensemble de global.json
description: Découvrez comment utiliser le fichier global.json pour définir la version du kit SDK .NET Core pendant l’exécution de commandes CLI .NET Core.
ms.date: 04/21/2020
ms.custom: updateeachrelease
ms.openlocfilehash: 5384b59cccb629a5409d26a8df7c81b3999fc95f
ms.sourcegitcommit: 348bb052d5cef109a61a3d5253faa5d7167d55ac
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "82021353"
---
# <a name="globaljson-overview"></a><span data-ttu-id="6b512-103">Vue d’ensemble de global.json</span><span class="sxs-lookup"><span data-stu-id="6b512-103">global.json overview</span></span>

<span data-ttu-id="6b512-104">**Cet article s’applique à:** ✔️ .NET Core 2.0 SDK et les versions ultérieures</span><span class="sxs-lookup"><span data-stu-id="6b512-104">**This article applies to:** ✔️ .NET Core 2.0 SDK and later versions</span></span>

<span data-ttu-id="6b512-105">Le fichier *global.json* vous permet de définir la version du kit SDK .NET Core utilisée pendant l’exécution des commandes de l’interface CLI .NET Core.</span><span class="sxs-lookup"><span data-stu-id="6b512-105">The *global.json* file allows you to define which .NET Core SDK version is used when you run .NET Core CLI commands.</span></span> <span data-ttu-id="6b512-106">La sélection du kit SDK .NET Core est indépendante de la spécification du runtime ciblé par votre projet.</span><span class="sxs-lookup"><span data-stu-id="6b512-106">Selecting the .NET Core SDK is independent from specifying the runtime your project targets.</span></span> <span data-ttu-id="6b512-107">La version SDK core .NET indique quelles versions de l’IFC core .NET est utilisée.</span><span class="sxs-lookup"><span data-stu-id="6b512-107">The .NET Core SDK version indicates which versions of the .NET Core CLI is used.</span></span>

<span data-ttu-id="6b512-108">En général, vous souhaitez utiliser la dernière version des outils SDK, donc aucun fichier *global.json* n’est nécessaire.</span><span class="sxs-lookup"><span data-stu-id="6b512-108">In general, you want to use the latest version of the SDK tools, so no *global.json* file is needed.</span></span> <span data-ttu-id="6b512-109">Dans certains scénarios avancés, vous voudrez peut-être contrôler la version des outils SDK, et cet article explique comment le faire.</span><span class="sxs-lookup"><span data-stu-id="6b512-109">In some advanced scenarios, you might want to control the version of the SDK tools, and this article explains how to do this.</span></span>

<span data-ttu-id="6b512-110">Pour plus d’informations sur la spécification du runtime, consultez [Versions cibles de .NET Framework](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="6b512-110">For more information about specifying the runtime instead, see [Target frameworks](../../standard/frameworks.md).</span></span>

<span data-ttu-id="6b512-111">Le kit SDK .NET Core recherche un fichier *global.json* dans le répertoire de travail actif (qui n’est pas nécessairement le même que le répertoire du projet) ou dans l’un de ses répertoires parents.</span><span class="sxs-lookup"><span data-stu-id="6b512-111">.NET Core SDK looks for a *global.json* file in the current working directory (which isn't necessarily the same as the project directory) or one of its parent directories.</span></span>

## <a name="globaljson-schema"></a><span data-ttu-id="6b512-112">Schéma de global.json</span><span class="sxs-lookup"><span data-stu-id="6b512-112">global.json schema</span></span>

### <a name="sdk"></a><span data-ttu-id="6b512-113">SDK</span><span class="sxs-lookup"><span data-stu-id="6b512-113">sdk</span></span>

<span data-ttu-id="6b512-114">Entrez : `object`</span><span class="sxs-lookup"><span data-stu-id="6b512-114">Type: `object`</span></span>

<span data-ttu-id="6b512-115">Spécifie des informations sur le kit SDK .NET Core à sélectionner.</span><span class="sxs-lookup"><span data-stu-id="6b512-115">Specifies information about the .NET Core SDK to select.</span></span>

#### <a name="version"></a><span data-ttu-id="6b512-116">version</span><span class="sxs-lookup"><span data-stu-id="6b512-116">version</span></span>

- <span data-ttu-id="6b512-117">Entrez : `string`</span><span class="sxs-lookup"><span data-stu-id="6b512-117">Type: `string`</span></span>

- <span data-ttu-id="6b512-118">Disponible depuis: .NET Core 1.0 SDK.</span><span class="sxs-lookup"><span data-stu-id="6b512-118">Available since: .NET Core 1.0 SDK.</span></span>

<span data-ttu-id="6b512-119">Version du kit SDK .NET Core à utiliser.</span><span class="sxs-lookup"><span data-stu-id="6b512-119">The version of the .NET Core SDK to use.</span></span>

<span data-ttu-id="6b512-120">Ce domaine:</span><span class="sxs-lookup"><span data-stu-id="6b512-120">This field:</span></span>

- <span data-ttu-id="6b512-121">N’a pas de support wildcard, c’est-à-dire que le numéro de version complet doit être spécifié.</span><span class="sxs-lookup"><span data-stu-id="6b512-121">Doesn't have wildcard support, that is, the full version number has to be specified.</span></span>
- <span data-ttu-id="6b512-122">Ne prend pas en charge les plages de versions.</span><span class="sxs-lookup"><span data-stu-id="6b512-122">Doesn't support version ranges.</span></span>

#### <a name="allowprerelease"></a><span data-ttu-id="6b512-123">autoriserPrerelease</span><span class="sxs-lookup"><span data-stu-id="6b512-123">allowPrerelease</span></span>

- <span data-ttu-id="6b512-124">Entrez : `boolean`</span><span class="sxs-lookup"><span data-stu-id="6b512-124">Type: `boolean`</span></span>

- <span data-ttu-id="6b512-125">Disponible depuis: .NET Core 3.0 SDK.</span><span class="sxs-lookup"><span data-stu-id="6b512-125">Available since: .NET Core 3.0 SDK.</span></span>

<span data-ttu-id="6b512-126">Indique si le résolveur SDK doit tenir compte des versions préreléase lors de la sélection de la version SDK à utiliser.</span><span class="sxs-lookup"><span data-stu-id="6b512-126">Indicates whether the SDK resolver should consider prerelease versions when selecting the SDK version to use.</span></span>

<span data-ttu-id="6b512-127">Si vous ne définissez pas cette valeur explicitement, la valeur par défaut dépend si vous êtes en cours d’exécution à partir de Visual Studio:</span><span class="sxs-lookup"><span data-stu-id="6b512-127">If you don't set this value explicitly, the default value depends on whether you're running from Visual Studio:</span></span>

- <span data-ttu-id="6b512-128">Si vous n’êtes **pas** dans Visual `true`Studio, la valeur par défaut est .</span><span class="sxs-lookup"><span data-stu-id="6b512-128">If you're **not** in Visual Studio, the default value is `true`.</span></span>
- <span data-ttu-id="6b512-129">Si vous êtes dans Visual Studio, il utilise le statut de prérédition demandé.</span><span class="sxs-lookup"><span data-stu-id="6b512-129">If you are in Visual Studio, it uses the prerelease status requested.</span></span> <span data-ttu-id="6b512-130">Autrement dit, si vous utilisez une version Aperçu de Visual Studio ou si vous définissez les **aperçus d’utilisation de l’option .NET Core SDK** (sous **tools** > **Options** > **Environment** > **Preview Features**), la valeur par défaut est `true`; autrement, `false`.</span><span class="sxs-lookup"><span data-stu-id="6b512-130">That is, if you're using a Preview version of Visual Studio or you set the **Use previews of the .NET Core SDK** option (under **Tools** > **Options** > **Environment** > **Preview Features**), the default value is `true`; otherwise, `false`.</span></span>

#### <a name="rollforward"></a><span data-ttu-id="6b512-131">rollForward</span><span class="sxs-lookup"><span data-stu-id="6b512-131">rollForward</span></span>

- <span data-ttu-id="6b512-132">Entrez : `string`</span><span class="sxs-lookup"><span data-stu-id="6b512-132">Type: `string`</span></span>

- <span data-ttu-id="6b512-133">Disponible depuis: .NET Core 3.0 SDK.</span><span class="sxs-lookup"><span data-stu-id="6b512-133">Available since: .NET Core 3.0 SDK.</span></span>

<span data-ttu-id="6b512-134">La stratégie de déploiement à utiliser lors de la sélection d’une version SDK, soit comme un repli lorsqu’une version spécifique SDK est manquante ou comme une directive pour utiliser une version supérieure.</span><span class="sxs-lookup"><span data-stu-id="6b512-134">The roll-forward policy to use when selecting an SDK version, either as a fallback when a specific SDK version is missing or as a directive to use a higher version.</span></span> <span data-ttu-id="6b512-135">Une [version](#version) doit être `rollForward` spécifiée avec une valeur, sauf si vous la définissez à `latestMajor`.</span><span class="sxs-lookup"><span data-stu-id="6b512-135">A [version](#version) must be specified with a `rollForward` value, unless you're setting it to `latestMajor`.</span></span>

<span data-ttu-id="6b512-136">Pour comprendre les politiques disponibles et leur comportement, considérez les `x.y.znn`définitions suivantes pour une version SDK dans le format :</span><span class="sxs-lookup"><span data-stu-id="6b512-136">To understand the available policies and their behavior, consider the following definitions for an SDK version in the format `x.y.znn`:</span></span>

- <span data-ttu-id="6b512-137">`x`est la version principale.</span><span class="sxs-lookup"><span data-stu-id="6b512-137">`x` is the major version.</span></span>
- <span data-ttu-id="6b512-138">`y`est la version mineure.</span><span class="sxs-lookup"><span data-stu-id="6b512-138">`y` is the minor version.</span></span>
- <span data-ttu-id="6b512-139">`z`est le groupe de longs métrages.</span><span class="sxs-lookup"><span data-stu-id="6b512-139">`z` is the feature band.</span></span>
- <span data-ttu-id="6b512-140">`nn`est la version patch.</span><span class="sxs-lookup"><span data-stu-id="6b512-140">`nn` is the patch version.</span></span>

<span data-ttu-id="6b512-141">Le tableau suivant montre les `rollForward` valeurs possibles pour la clé :</span><span class="sxs-lookup"><span data-stu-id="6b512-141">The following table shows the possible values for the `rollForward` key:</span></span>

| <span data-ttu-id="6b512-142">Valeur</span><span class="sxs-lookup"><span data-stu-id="6b512-142">Value</span></span>         | <span data-ttu-id="6b512-143">Comportement</span><span class="sxs-lookup"><span data-stu-id="6b512-143">Behavior</span></span> |
| ------------- | ---------- |
| `patch`       | <span data-ttu-id="6b512-144">Utilise la version spécifiée.</span><span class="sxs-lookup"><span data-stu-id="6b512-144">Uses the specified version.</span></span> <br> <span data-ttu-id="6b512-145">S’il n’est pas trouvé, roule vers l’avant vers le dernier niveau de patch.</span><span class="sxs-lookup"><span data-stu-id="6b512-145">If not found, rolls forward to the latest patch level.</span></span> <br> <span data-ttu-id="6b512-146">S’il n’est pas trouvé, échoue.</span><span class="sxs-lookup"><span data-stu-id="6b512-146">If not found, fails.</span></span> <br><br> <span data-ttu-id="6b512-147">Cette valeur est le comportement hérité des versions antérieures de la SDK.</span><span class="sxs-lookup"><span data-stu-id="6b512-147">This value is the legacy behavior from the earlier versions of the SDK.</span></span> |
| `feature`     | <span data-ttu-id="6b512-148">Utilise le dernier niveau de patch pour la bande majeure spécifiée, mineure, et de dispositif.</span><span class="sxs-lookup"><span data-stu-id="6b512-148">Uses the latest patch level for the specified major, minor, and feature band.</span></span> <br> <span data-ttu-id="6b512-149">S’il n’est pas trouvé, roule vers l’avant à la bande de fonctionnalité supérieure suivante dans le même majeur / mineur et utilise le dernier niveau de patch pour cette bande de fonctionnalité.</span><span class="sxs-lookup"><span data-stu-id="6b512-149">If not found, rolls forward to the next higher feature band within the same major/minor and uses the latest patch level for that feature band.</span></span> <br> <span data-ttu-id="6b512-150">S’il n’est pas trouvé, échoue.</span><span class="sxs-lookup"><span data-stu-id="6b512-150">If not found, fails.</span></span> |
| `minor`       | <span data-ttu-id="6b512-151">Utilise le dernier niveau de patch pour la bande majeure spécifiée, mineure, et de dispositif.</span><span class="sxs-lookup"><span data-stu-id="6b512-151">Uses the latest patch level for the specified major, minor, and feature band.</span></span> <br> <span data-ttu-id="6b512-152">S’il n’est pas trouvé, roule vers l’avant à la bande de fonctionnalité supérieure suivante dans la même version majeure / mineur et utilise le dernier niveau de patch pour cette bande de fonctionnalité.</span><span class="sxs-lookup"><span data-stu-id="6b512-152">If not found, rolls forward to the next higher feature band within the same major/minor version and uses the latest patch level for that feature band.</span></span> <br> <span data-ttu-id="6b512-153">S’il n’est pas trouvé, roule vers l’avant à la prochaine plus haute bande mineure et fonctionnalité dans le même majeur et utilise le dernier niveau de patch pour cette bande de fonctionnalité.</span><span class="sxs-lookup"><span data-stu-id="6b512-153">If not found, rolls forward to the next higher minor and feature band within the same major and uses the latest patch level for that feature band.</span></span> <br> <span data-ttu-id="6b512-154">S’il n’est pas trouvé, échoue.</span><span class="sxs-lookup"><span data-stu-id="6b512-154">If not found, fails.</span></span> |
| `major`       | <span data-ttu-id="6b512-155">Utilise le dernier niveau de patch pour la bande majeure spécifiée, mineure, et de dispositif.</span><span class="sxs-lookup"><span data-stu-id="6b512-155">Uses the latest patch level for the specified major, minor, and feature band.</span></span> <br> <span data-ttu-id="6b512-156">S’il n’est pas trouvé, roule vers l’avant à la bande de fonctionnalité supérieure suivante dans la même version majeure / mineur et utilise le dernier niveau de patch pour cette bande de fonctionnalité.</span><span class="sxs-lookup"><span data-stu-id="6b512-156">If not found, rolls forward to the next higher feature band within the same major/minor version and uses the latest patch level for that feature band.</span></span> <br> <span data-ttu-id="6b512-157">S’il n’est pas trouvé, roule vers l’avant à la prochaine plus haute bande mineure et fonctionnalité dans le même majeur et utilise le dernier niveau de patch pour cette bande de fonctionnalité.</span><span class="sxs-lookup"><span data-stu-id="6b512-157">If not found, rolls forward to the next higher minor and feature band within the same major and uses the latest patch level for that feature band.</span></span> <br> <span data-ttu-id="6b512-158">S’il n’est pas trouvé, roule vers l’avant à la prochaine bande supérieure majeure, mineure, et fonctionnalité et utilise le dernier niveau de patch pour cette bande de fonctionnalité.</span><span class="sxs-lookup"><span data-stu-id="6b512-158">If not found, rolls forward to the next higher major, minor, and feature band and uses the latest patch level for that feature band.</span></span> <br> <span data-ttu-id="6b512-159">S’il n’est pas trouvé, échoue.</span><span class="sxs-lookup"><span data-stu-id="6b512-159">If not found, fails.</span></span> |
| `latestPatch` | <span data-ttu-id="6b512-160">Utilise le dernier niveau de patch installé qui correspond à la bande de majeur, mineure et de fonctionnalité demandée avec un niveau de patch et qui est plus ou égale que la valeur spécifiée.</span><span class="sxs-lookup"><span data-stu-id="6b512-160">Uses the latest installed patch level that matches the requested major, minor, and feature band with a patch level and that is greater or equal than the specified value.</span></span> <br> <span data-ttu-id="6b512-161">S’il n’est pas trouvé, échoue.</span><span class="sxs-lookup"><span data-stu-id="6b512-161">If not found, fails.</span></span> |
| `latestFeature` | <span data-ttu-id="6b512-162">Utilise la bande de fonctionnalité et le niveau de patch les plus élevés qui correspondent au majeur et au mineur demandés avec une bande de fonctionnalités supérieure ou égale à la valeur spécifiée.</span><span class="sxs-lookup"><span data-stu-id="6b512-162">Uses the highest installed feature band and patch level that matches the requested major and minor with a feature band that is greater or equal than the specified value.</span></span> <br> <span data-ttu-id="6b512-163">S’il n’est pas trouvé, échoue.</span><span class="sxs-lookup"><span data-stu-id="6b512-163">If not found, fails.</span></span> |
| `latestMinor` | <span data-ttu-id="6b512-164">Utilise le mineur installé le plus haut, bande de fonctionnalité, et le niveau de patch qui correspond à la majeure demandée avec un mineur qui est plus ou égal que la valeur spécifiée.</span><span class="sxs-lookup"><span data-stu-id="6b512-164">Uses the highest installed minor, feature band, and patch level that matches the requested major with a minor that is greater or equal than the specified value.</span></span> <br> <span data-ttu-id="6b512-165">S’il n’est pas trouvé, échoue.</span><span class="sxs-lookup"><span data-stu-id="6b512-165">If not found, fails.</span></span> |
| `latestMajor` | <span data-ttu-id="6b512-166">Utilise le SDK de base le plus élevé installé .NET avec une majeure qui est supérieure ou égale à la valeur spécifiée.</span><span class="sxs-lookup"><span data-stu-id="6b512-166">Uses the highest installed .NET Core SDK with a major that is greater or equal than the specified value.</span></span> <br> <span data-ttu-id="6b512-167">S’il n’est pas trouvé, échouez.</span><span class="sxs-lookup"><span data-stu-id="6b512-167">If not found, fail.</span></span> |
| `disable`     | <span data-ttu-id="6b512-168">Il ne roule pas en avant.</span><span class="sxs-lookup"><span data-stu-id="6b512-168">Doesn't roll forward.</span></span> <span data-ttu-id="6b512-169">Correspondance exacte requise.</span><span class="sxs-lookup"><span data-stu-id="6b512-169">Exact match required.</span></span> |

## <a name="examples"></a><span data-ttu-id="6b512-170">Exemples</span><span class="sxs-lookup"><span data-stu-id="6b512-170">Examples</span></span>

<span data-ttu-id="6b512-171">L’exemple suivant montre comment ne pas utiliser les versions prérelease :</span><span class="sxs-lookup"><span data-stu-id="6b512-171">The following example shows how to not use prerelease versions:</span></span>

```json
{
  "sdk": {
    "allowPrerelease": false
  }
}
```

<span data-ttu-id="6b512-172">L’exemple suivant montre comment utiliser la version la plus élevée installée qui est supérieure ou égale à la version spécifiée :</span><span class="sxs-lookup"><span data-stu-id="6b512-172">The following example shows how to use the highest version installed that is greater or equal than the specified version:</span></span>

```json
{
  "sdk": {
    "version": "3.1.100",
    "rollForward": "latestMajor"
  }
}
```

<span data-ttu-id="6b512-173">L’exemple suivant montre comment utiliser la version spécifiée exacte :</span><span class="sxs-lookup"><span data-stu-id="6b512-173">The following example shows how to use the exact specified version:</span></span>

```json
{
  "sdk": {
    "version": "3.1.100",
    "rollForward": "disable"
  }
}
```

<span data-ttu-id="6b512-174">L’exemple suivant montre comment utiliser la dernière bande de fonctionnalités et la version patch installée d’une version majeure et mineure spécifique :</span><span class="sxs-lookup"><span data-stu-id="6b512-174">The following example shows how to use the latest feature band and patch version installed of a specific major and minor version:</span></span>

```json
{
  "sdk": {
    "version": "3.1.000",
    "rollForward": "latestFeature"
  }
}
```

<span data-ttu-id="6b512-175">L’exemple suivant montre comment utiliser la version patch la plus élevée installée d’une version spécifique (sous la forme, 3.1.1xx):</span><span class="sxs-lookup"><span data-stu-id="6b512-175">The following example shows how to use the highest patch version installed of a specific version (in the form, 3.1.1xx):</span></span>

```json
{
  "sdk": {
    "version": "3.1.100",
    "rollForward": "latestPatch"
  }
}
```

## <a name="globaljson-and-the-net-core-cli"></a><span data-ttu-id="6b512-176">global.JSON et l’interface CLI .NET Core</span><span class="sxs-lookup"><span data-stu-id="6b512-176">global.json and the .NET Core CLI</span></span>

<span data-ttu-id="6b512-177">Il est utile de savoir quelles versions SDK sont installées sur votre machine pour en définir une dans le fichier *global.json.*</span><span class="sxs-lookup"><span data-stu-id="6b512-177">It's helpful to know which SDK versions are installed on your machine to set one in the *global.json* file.</span></span> <span data-ttu-id="6b512-178">Pour plus d’informations sur la façon de le faire, voir [Comment vérifier que .NET Core est déjà installé](../install/how-to-detect-installed-versions.md#check-sdk-versions).</span><span class="sxs-lookup"><span data-stu-id="6b512-178">For more information on how to do that, see [How to check that .NET Core is already installed](../install/how-to-detect-installed-versions.md#check-sdk-versions).</span></span>

<span data-ttu-id="6b512-179">Pour installer d’autres versions SDK core .NET supplémentaires sur votre machine, visitez la page [Télécharger .NET Core.](https://dotnet.microsoft.com/download/dotnet-core)</span><span class="sxs-lookup"><span data-stu-id="6b512-179">To install additional .NET Core SDK versions on your machine, visit the [Download .NET Core](https://dotnet.microsoft.com/download/dotnet-core) page.</span></span>

<span data-ttu-id="6b512-180">Vous pouvez créer un fichier *global.json* dans le répertoire actif en exécutant la commande [dotnet new](dotnet-new.md), comme dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="6b512-180">You can create a new the *global.json* file in the current directory by executing the [dotnet new](dotnet-new.md) command, similar to the following example:</span></span>

```dotnetcli
dotnet new globaljson --sdk-version 3.0.100
```

## <a name="matching-rules"></a><span data-ttu-id="6b512-181">Règles de correspondance</span><span class="sxs-lookup"><span data-stu-id="6b512-181">Matching rules</span></span>

> [!NOTE]
> <span data-ttu-id="6b512-182">Les règles de correspondance `dotnet.exe` sont régies par le point d’entrée, qui est commun à tous les runtimes installés .NET Core installé.</span><span class="sxs-lookup"><span data-stu-id="6b512-182">The matching rules are governed by the `dotnet.exe` entry point, which is common across all installed .NET Core installed runtimes.</span></span> <span data-ttu-id="6b512-183">Les règles de correspondance pour la dernière version installée du .NET Core Runtime sont utilisées lorsque vous avez plusieurs temps d’exécution installés côte à côte.</span><span class="sxs-lookup"><span data-stu-id="6b512-183">The matching rules for the latest installed version of the .NET Core Runtime are used when you have multiple runtimes installed side-by-side.</span></span>

## <a name="net-core-3x"></a>[<span data-ttu-id="6b512-184">.NET Core 3.x</span><span class="sxs-lookup"><span data-stu-id="6b512-184">.NET Core 3.x</span></span>](#tab/netcore3x)

<span data-ttu-id="6b512-185">En commençant par .NET Core 3.0, les règles suivantes s’appliquent lorsqu’elles déterminent la version du SDK à utiliser :</span><span class="sxs-lookup"><span data-stu-id="6b512-185">Starting with .NET Core 3.0, the following rules apply when determining which version of the SDK to use:</span></span>

- <span data-ttu-id="6b512-186">Si aucun fichier *global.json* n’est trouvé, ou *global.json* ne `allowPrerelease` spécifie pas une version SDK `latestMajor`ni une valeur, la version SDK installée la plus élevée est utilisée (équivalent à la mise à). `rollForward`</span><span class="sxs-lookup"><span data-stu-id="6b512-186">If no *global.json* file is found, or *global.json* doesn't specify an SDK version nor an `allowPrerelease` value, the highest installed SDK version is used (equivalent to setting `rollForward` to `latestMajor`).</span></span> <span data-ttu-id="6b512-187">La question de savoir si les versions `dotnet` SDK préreléase sont considérées dépend de la façon dont elles sont invoquées.</span><span class="sxs-lookup"><span data-stu-id="6b512-187">Whether prerelease SDK versions are considered depends on how `dotnet` is being invoked.</span></span>
  - <span data-ttu-id="6b512-188">Si vous n’êtes **pas** dans Visual Studio, les versions prérelease sont prises en considération.</span><span class="sxs-lookup"><span data-stu-id="6b512-188">If you're **not** in Visual Studio, prerelease versions are considered.</span></span>
  - <span data-ttu-id="6b512-189">Si vous êtes dans Visual Studio, il utilise le statut de prérédition demandé.</span><span class="sxs-lookup"><span data-stu-id="6b512-189">If you are in Visual Studio, it uses the prerelease status requested.</span></span> <span data-ttu-id="6b512-190">Autrement dit, si vous utilisez une version Aperçu de Visual Studio ou si vous définissez les **aperçus d’utilisation de l’option .NET Core SDK** (sous **tools** > **Options** > **Environment** > Preview**Features**), les versions préreléase sont envisagées; autrement, seules les versions de version sont prises en considération.</span><span class="sxs-lookup"><span data-stu-id="6b512-190">That is, if you're using a Preview version of Visual Studio or you set the **Use previews of the .NET Core SDK** option (under **Tools** > **Options** > **Environment** > **Preview Features**), prerelease versions are considered; otherwise, only release versions are considered.</span></span>
- <span data-ttu-id="6b512-191">Si un fichier *global.json* est trouvé qui ne spécifie `allowPrerelease` pas une version SDK mais il spécifie une valeur, la version SDK installée la plus élevée est utilisée (équivalent au réglage `rollForward` à `latestMajor`).</span><span class="sxs-lookup"><span data-stu-id="6b512-191">If a *global.json* file is found that doesn't specify an SDK version but it specifies an `allowPrerelease` value, the highest installed SDK version is used (equivalent to setting `rollForward` to `latestMajor`).</span></span> <span data-ttu-id="6b512-192">Si la dernière version SDK peut être libéré ou `allowPrerelease`prérelease dépend de la valeur de .</span><span class="sxs-lookup"><span data-stu-id="6b512-192">Whether the latest SDK version can be release or prerelease depends on the value of `allowPrerelease`.</span></span> <span data-ttu-id="6b512-193">`true`indique que les versions préreléase sont envisagées; `false` indique que seules les versions de version sont prises en considération.</span><span class="sxs-lookup"><span data-stu-id="6b512-193">`true` indicates prerelease versions are considered; `false` indicates that only release versions are considered.</span></span>
- <span data-ttu-id="6b512-194">Si un fichier *global.json* est trouvé et il spécifie une version SDK:</span><span class="sxs-lookup"><span data-stu-id="6b512-194">If a *global.json* file is found and it specifies an SDK version:</span></span>

  - <span data-ttu-id="6b512-195">Si `rollFoward` aucune valeur n’est définie, elle s’utilise `latestPatch` comme stratégie par défaut. `rollForward`</span><span class="sxs-lookup"><span data-stu-id="6b512-195">If no `rollFoward` value is set, it uses `latestPatch` as the default `rollForward` policy.</span></span> <span data-ttu-id="6b512-196">Sinon, vérifiez chaque valeur et leur comportement dans la section [rollForward.](#rollforward)</span><span class="sxs-lookup"><span data-stu-id="6b512-196">Otherwise, check each value and their behavior in the [rollForward](#rollforward) section.</span></span>
  - <span data-ttu-id="6b512-197">Si les versions prérelease sont considérées `allowPrerelease` et quel est le comportement par défaut quand n’est pas défini est décrit dans la section [allowPrerelease.](#allowprerelease)</span><span class="sxs-lookup"><span data-stu-id="6b512-197">Whether prerelease versions are considered and what's the default behavior when `allowPrerelease` isn't set is described in the [allowPrerelease](#allowprerelease) section.</span></span>

## <a name="net-core-2x"></a>[<span data-ttu-id="6b512-198">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="6b512-198">.NET Core 2.x</span></span>](#tab/netcore2x)

<span data-ttu-id="6b512-199">Dans .NET Core 2.x SDK, les règles suivantes s’appliquent lorsqu’elles déterminent quelle version du SDK utiliser :</span><span class="sxs-lookup"><span data-stu-id="6b512-199">In .NET Core 2.x SDK, the following rules apply when determining which version of the SDK to use:</span></span>

- <span data-ttu-id="6b512-200">Si aucun fichier *global.json* n’est trouvé ou que *global.json* ne spécifie pas de version du kit SDK, la dernière version installée du kit SDK est utilisée.</span><span class="sxs-lookup"><span data-stu-id="6b512-200">If no *global.json* file is found or *global.json* doesn't specify an SDK version, the latest installed SDK version is used.</span></span> <span data-ttu-id="6b512-201">La dernière version SDK peut être soit la libération ou la prérénée - le nombre de versions la plus élevée gagne.</span><span class="sxs-lookup"><span data-stu-id="6b512-201">Latest SDK version can be either release or prerelease - the highest version number wins.</span></span>
- <span data-ttu-id="6b512-202">Si la version du kit SDK n’est pas spécifiée dans *global.json* :</span><span class="sxs-lookup"><span data-stu-id="6b512-202">If *global.json* does specify an SDK version:</span></span>
  - <span data-ttu-id="6b512-203">Si la version spécifiée du kit SDK se trouve sur la machine, c’est cette même version qui est utilisée.</span><span class="sxs-lookup"><span data-stu-id="6b512-203">If the specified SDK version is found on the machine, that exact version is used.</span></span>
  - <span data-ttu-id="6b512-204">Si la version spécifiée du kit SDK est introuvable sur la machine, c’est la dernière **version corrective** installée du kit SDK qui est utilisée.</span><span class="sxs-lookup"><span data-stu-id="6b512-204">If the specified SDK version can't be found on the machine, the latest installed SDK **patch version** of that version is used.</span></span> <span data-ttu-id="6b512-205">La dernière version installée de **patch** SDK peut être soit la libération ou la prérénée - le nombre de version le plus élevé gagne.</span><span class="sxs-lookup"><span data-stu-id="6b512-205">Latest installed SDK **patch version** can be either release or prerelease - the highest version number wins.</span></span> <span data-ttu-id="6b512-206">Dans .NET Core 2.1 et ultérieur, les **versions correctives** antérieures à la **version corrective** spécifiée sont ignorées dans la sélection du kit SDK.</span><span class="sxs-lookup"><span data-stu-id="6b512-206">In .NET Core 2.1 and higher, the **patch versions** lower than the **patch version** specified are ignored in the SDK selection.</span></span>
  - <span data-ttu-id="6b512-207">Dans le cas où ni la version spécifiée du kit SDK, ni une **version corrective** appropriée du kit SDK n’est trouvée, une erreur est générée.</span><span class="sxs-lookup"><span data-stu-id="6b512-207">If the specified SDK version and an appropriate SDK **patch version** can't be found, an error is thrown.</span></span>

<span data-ttu-id="6b512-208">La version SDK est composée des parties suivantes :</span><span class="sxs-lookup"><span data-stu-id="6b512-208">The SDK version is composed of the following parts:</span></span>

`[.NET Core major version].[.NET Core minor version].[xyz][-optional preview name]`

<span data-ttu-id="6b512-209">La **future version** du kit SDK .NET Core est représentée par le premier chiffre (`x`) de la dernière partie du nombre (`xyz`) pour les versions 2.1.100 et ultérieures du kit SDK.</span><span class="sxs-lookup"><span data-stu-id="6b512-209">The **feature release** of the .NET Core SDK is represented by the first digit (`x`) in the last portion of the number (`xyz`) for SDK versions 2.1.100 and higher.</span></span> <span data-ttu-id="6b512-210">En règle générale, le cycle de lancement du kit SDK .NET Core est plus rapide que celui de .NET Core.</span><span class="sxs-lookup"><span data-stu-id="6b512-210">In general, the .NET Core SDK has a faster release cycle than .NET Core.</span></span>

<span data-ttu-id="6b512-211">La **version corrective** est définie par les deux derniers chiffres (`yz`) de la dernière partie du nombre (`xyz`) pour les versions 2.1.100 et ultérieures du kit SDK.</span><span class="sxs-lookup"><span data-stu-id="6b512-211">The **patch version** is defined by the last two digits (`yz`) in the last portion of the number (`xyz`) for SDK versions 2.1.100 and higher.</span></span> <span data-ttu-id="6b512-212">Par exemple, si vous spécifiez la version `2.1.300` du kit SDK, le mécanisme de sélection du kit SDK trouve la version `2.1.399`, mais la version `2.1.400` n’est pas considérée comme une version corrective de la version `2.1.300`.</span><span class="sxs-lookup"><span data-stu-id="6b512-212">For example, if you specify `2.1.300` as the SDK version, SDK selection finds up to `2.1.399` but `2.1.400` isn't considered a patch version for `2.1.300`.</span></span>

<span data-ttu-id="6b512-213">Les versions du kit SDK .NET Core comprises entre `2.1.100` et `2.1.201` ont été lancées pendant la période transitoire entre les modèles de numérotation des versions et ne gèrent pas correctement la notation `xyz`.</span><span class="sxs-lookup"><span data-stu-id="6b512-213">.NET Core SDK versions `2.1.100` through `2.1.201` were released during the transition between version number schemes and don't correctly handle the `xyz` notation.</span></span> <span data-ttu-id="6b512-214">Si vous spécifiez ces versions dans le fichier *global.json*, nous vous recommandons vivement de vérifier que les versions spécifiées se trouvent sur les machines cibles.</span><span class="sxs-lookup"><span data-stu-id="6b512-214">We highly recommend if you specify these versions in the *global.json* file, that you ensure the specified versions are on the target machines.</span></span>

---

## <a name="troubleshoot-build-warnings"></a><span data-ttu-id="6b512-215">Avertissements de construction de dépanneurs</span><span class="sxs-lookup"><span data-stu-id="6b512-215">Troubleshoot build warnings</span></span>

* <span data-ttu-id="6b512-216">L’avertissement suivant indique que votre projet a été compilé à l’aide d’une version préréactive du SDK core .NET :</span><span class="sxs-lookup"><span data-stu-id="6b512-216">The following warning indicates that your project was compiled using a prerelease version of the .NET Core SDK:</span></span>

  > <span data-ttu-id="6b512-217">Vous utilisez une préversion du kit SDK .NET Core.</span><span class="sxs-lookup"><span data-stu-id="6b512-217">You are working with a preview version of the .NET Core SDK.</span></span> <span data-ttu-id="6b512-218">Vous pouvez définir la version du kit SDK via un fichier global.json dans le projet actif.</span><span class="sxs-lookup"><span data-stu-id="6b512-218">You can define the SDK version via a global.json file in the current project.</span></span> <span data-ttu-id="6b512-219">Plus <https://go.microsoft.com/fwlink/?linkid=869452>à .</span><span class="sxs-lookup"><span data-stu-id="6b512-219">More at <https://go.microsoft.com/fwlink/?linkid=869452>.</span></span>

  <span data-ttu-id="6b512-220">Les versions du kit SDK .NET Core jouissent d’une image et d’un engagement de qualité.</span><span class="sxs-lookup"><span data-stu-id="6b512-220">.NET Core SDK versions have a history and commitment of being high quality.</span></span> <span data-ttu-id="6b512-221">Toutefois, si vous ne voulez pas utiliser une version préréactivease, vérifiez les différentes stratégies que vous pouvez utiliser avec le .NET Core 3.0 SDK ou une version ultérieure dans la section [allowPrerelease.](#allowprerelease)</span><span class="sxs-lookup"><span data-stu-id="6b512-221">However, if you don't want to use a prerelease version, check the different strategies you can use with the .NET Core 3.0 SDK or a later version in the [allowPrerelease](#allowprerelease) section.</span></span> <span data-ttu-id="6b512-222">Pour les machines qui n’ont jamais eu un .NET Core 3.0 ou plus Runtime ou SDK installé, vous devez créer un fichier *global.json* et spécifier la version exacte que vous voulez utiliser.</span><span class="sxs-lookup"><span data-stu-id="6b512-222">For machines that have never had a .NET Core 3.0 or higher Runtime or SDK installed, you need to create a *global.json* file and specify the exact version you want to use.</span></span>

* <span data-ttu-id="6b512-223">L’avertissement suivant indique que votre projet cible EF Core 1.0 ou 1.1, ce qui n’est pas compatible avec .NET Core 2.1 SDK et les versions ultérieures :</span><span class="sxs-lookup"><span data-stu-id="6b512-223">The following warning indicates that your project targets EF Core 1.0 or 1.1, which isn't compatible with .NET Core 2.1 SDK and later versions:</span></span>

  > <span data-ttu-id="6b512-224">Le projet de démarrage '{startupProject}' cible le framework '.NETCoreApp' version '{targetFrameworkVersion}'.</span><span class="sxs-lookup"><span data-stu-id="6b512-224">Startup project '{startupProject}' targets framework '.NETCoreApp' version '{targetFrameworkVersion}'.</span></span> <span data-ttu-id="6b512-225">Cette version des outils en ligne de commande Entity Framework Core .NET prend uniquement en charge la version 2.0 ou supérieure.</span><span class="sxs-lookup"><span data-stu-id="6b512-225">This version of the Entity Framework Core .NET Command-line Tools only supports version 2.0 or higher.</span></span> <span data-ttu-id="6b512-226">Pour plus d’informations sur l’utilisation des anciennes versions des outils, voir <https://go.microsoft.com/fwlink/?linkid=871254>.</span><span class="sxs-lookup"><span data-stu-id="6b512-226">For information on using older versions of the tools, see <https://go.microsoft.com/fwlink/?linkid=871254>.</span></span>

  <span data-ttu-id="6b512-227">À partir du kit SDK .NET Core 2.1 (version 2.1.300), la commande `dotnet ef` est incluse dans le kit SDK.</span><span class="sxs-lookup"><span data-stu-id="6b512-227">Starting with .NET Core 2.1 SDK (version 2.1.300), the `dotnet ef` command comes included in the SDK.</span></span> <span data-ttu-id="6b512-228">Pour compiler votre projet, installez .NET Core 2.0 SDK (version 2.1.201) ou plus tôt sur votre machine et définissez la version SDK souhaitée à l’aide du fichier *global.json.*</span><span class="sxs-lookup"><span data-stu-id="6b512-228">To compile your project, install .NET Core 2.0 SDK (version 2.1.201) or earlier on your machine and define the desired SDK version using the *global.json* file.</span></span> <span data-ttu-id="6b512-229">Pour plus d’informations sur la commande `dotnet ef`, consultez [Outils en ligne de commande EF Core .NET](/ef/core/miscellaneous/cli/dotnet).</span><span class="sxs-lookup"><span data-stu-id="6b512-229">For more information about the `dotnet ef` command, see [EF Core .NET Command-line Tools](/ef/core/miscellaneous/cli/dotnet).</span></span>

## <a name="see-also"></a><span data-ttu-id="6b512-230">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6b512-230">See also</span></span>

- [<span data-ttu-id="6b512-231">Méthode de résolution des kits SDK de projet</span><span class="sxs-lookup"><span data-stu-id="6b512-231">How project SDKs are resolved</span></span>](/visualstudio/msbuild/how-to-use-project-sdk#how-project-sdks-are-resolved)
