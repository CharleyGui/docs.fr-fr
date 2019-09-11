---
title: Vue d’ensemble de global.json
description: Découvrez comment utiliser le fichier global.json pour définir la version du kit SDK .NET Core pendant l’exécution de commandes CLI .NET Core.
ms.date: 12/03/2018
ms.custom: updateeachrelease, seodec18
ms.openlocfilehash: 3c3793011560cd7428e47bd3340d0a935247760f
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70849599"
---
# <a name="globaljson-overview"></a><span data-ttu-id="b85e9-103">Vue d’ensemble de global.json</span><span class="sxs-lookup"><span data-stu-id="b85e9-103">global.json overview</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

<span data-ttu-id="b85e9-104">Le fichier *global.json* vous permet de définir la version du kit SDK .NET Core utilisée pendant l’exécution des commandes de l’interface CLI .NET Core.</span><span class="sxs-lookup"><span data-stu-id="b85e9-104">The *global.json* file allows you to define which .NET Core SDK version is used when you run .NET Core CLI commands.</span></span> <span data-ttu-id="b85e9-105">La sélection du kit SDK .NET Core est indépendante de la spécification du runtime ciblé par votre projet.</span><span class="sxs-lookup"><span data-stu-id="b85e9-105">Selecting the .NET Core SDK is independent from specifying the runtime your project targets.</span></span> <span data-ttu-id="b85e9-106">La version du kit SDK .NET Core détermine les versions des outils CLI .NET Core qui sont utilisées.</span><span class="sxs-lookup"><span data-stu-id="b85e9-106">The .NET Core SDK version indicates which versions of the .NET Core CLI tools are used.</span></span> <span data-ttu-id="b85e9-107">En règle générale, il est préférable d’utiliser la dernière version des outils. Dans ce cas, aucun fichier *global.json* n’est nécessaire.</span><span class="sxs-lookup"><span data-stu-id="b85e9-107">In general, you want to use the latest version of the tools, so no *global.json* file is needed.</span></span>

<span data-ttu-id="b85e9-108">Pour plus d’informations sur la spécification du runtime, consultez [Versions cibles de .NET Framework](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="b85e9-108">For more information about specifying the runtime instead, see [Target frameworks](../../standard/frameworks.md).</span></span>

<span data-ttu-id="b85e9-109">Le kit SDK .NET Core recherche un fichier *global.json* dans le répertoire de travail actif (qui n’est pas nécessairement le même que le répertoire du projet) ou dans l’un de ses répertoires parents.</span><span class="sxs-lookup"><span data-stu-id="b85e9-109">.NET Core SDK looks for a *global.json* file in the current working directory (which isn't necessarily the same as the project directory) or one of its parent directories.</span></span>

## <a name="globaljson-schema"></a><span data-ttu-id="b85e9-110">Schéma de global.json</span><span class="sxs-lookup"><span data-stu-id="b85e9-110">global.json schema</span></span>

### <a name="sdk"></a><span data-ttu-id="b85e9-111">sdk</span><span class="sxs-lookup"><span data-stu-id="b85e9-111">sdk</span></span>

<span data-ttu-id="b85e9-112">Tapez : Object</span><span class="sxs-lookup"><span data-stu-id="b85e9-112">Type: Object</span></span>

<span data-ttu-id="b85e9-113">Spécifie des informations sur le kit SDK .NET Core à sélectionner.</span><span class="sxs-lookup"><span data-stu-id="b85e9-113">Specifies information about the .NET Core SDK to select.</span></span>

#### <a name="version"></a><span data-ttu-id="b85e9-114">version</span><span class="sxs-lookup"><span data-stu-id="b85e9-114">version</span></span>

<span data-ttu-id="b85e9-115">Tapez : String</span><span class="sxs-lookup"><span data-stu-id="b85e9-115">Type: String</span></span>

<span data-ttu-id="b85e9-116">Version du kit SDK .NET Core à utiliser.</span><span class="sxs-lookup"><span data-stu-id="b85e9-116">The version of the .NET Core SDK to use.</span></span>

<span data-ttu-id="b85e9-117">Notez que ce champ :</span><span class="sxs-lookup"><span data-stu-id="b85e9-117">Note that this field:</span></span>

- <span data-ttu-id="b85e9-118">Ne prend pas en charge l’utilisation de caractères génériques. Autrement dit, il convient de spécifier le numéro complet de la version.</span><span class="sxs-lookup"><span data-stu-id="b85e9-118">Doesn't have globbing support, that is, the full version number has to be specified.</span></span>
- <span data-ttu-id="b85e9-119">Ne prend pas en charge les plages de versions.</span><span class="sxs-lookup"><span data-stu-id="b85e9-119">Doesn't support version ranges.</span></span>

<span data-ttu-id="b85e9-120">L’exemple suivant montre le contenu d’un fichier *global.json* :</span><span class="sxs-lookup"><span data-stu-id="b85e9-120">The following example shows the contents of a *global.json* file:</span></span>

```json
{
  "sdk": {
    "version": "2.2.100"
  }
}
```

## <a name="globaljson-and-the-net-core-cli"></a><span data-ttu-id="b85e9-121">global.JSON et l’interface CLI .NET Core</span><span class="sxs-lookup"><span data-stu-id="b85e9-121">global.json and the .NET Core CLI</span></span>

<span data-ttu-id="b85e9-122">Il est utile de connaître les versions disponibles pour en définir une dans le fichier *global.json*.</span><span class="sxs-lookup"><span data-stu-id="b85e9-122">It's helpful to know which versions are available in order to set one in the *global.json* file.</span></span> <span data-ttu-id="b85e9-123">Vous trouverez la liste complète des kits de développement logiciel (SDK) disponibles pris en charge sur la page [Télécharger .net Core](https://dotnet.microsoft.com/download/dotnet-core) .</span><span class="sxs-lookup"><span data-stu-id="b85e9-123">You can find the full list of supported available SDKs at the [Download .NET Core](https://dotnet.microsoft.com/download/dotnet-core) page.</span></span> <span data-ttu-id="b85e9-124">À partir du kit SDK .NET Core 2.1, vous pouvez exécuter la commande suivante pour savoir quelles versions du kit SDK sont déjà installées sur votre ordinateur :</span><span class="sxs-lookup"><span data-stu-id="b85e9-124">Starting with .NET Core 2.1 SDK, you can run the following command to verify which SDK versions are already installed on your machine:</span></span>

```console
dotnet --list-sdks
```

<span data-ttu-id="b85e9-125">Pour installer des versions de kit SDK .NET Core supplémentaires sur votre ordinateur, visitez la page [Télécharger .net Core](https://dotnet.microsoft.com/download/dotnet-core) .</span><span class="sxs-lookup"><span data-stu-id="b85e9-125">To install additional .NET Core SDK versions on your machine, visit the [Download .NET Core](https://dotnet.microsoft.com/download/dotnet-core) page.</span></span>

<span data-ttu-id="b85e9-126">Vous pouvez créer un fichier *global.json* dans le répertoire actif en exécutant la commande [dotnet new](dotnet-new.md), comme dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="b85e9-126">You can create a new the *global.json* file in the current directory by executing the [dotnet new](dotnet-new.md) command, similar to the following example:</span></span>

```console
dotnet new globaljson --sdk-version 2.2.100
```

## <a name="matching-rules"></a><span data-ttu-id="b85e9-127">Règles de correspondance</span><span class="sxs-lookup"><span data-stu-id="b85e9-127">Matching rules</span></span>

> [!NOTE]
> <span data-ttu-id="b85e9-128">Les règles de correspondance sont régies par apphost, qui fait partie du runtime .NET Core.</span><span class="sxs-lookup"><span data-stu-id="b85e9-128">The matching rules are governed by the apphost, which is part of the .NET Core runtime.</span></span>
> <span data-ttu-id="b85e9-129">La dernière version de l’hôte est utilisée quand plusieurs runtimes sont installés côte à côte.</span><span class="sxs-lookup"><span data-stu-id="b85e9-129">The latest version of the host is used when you have multiple runtimes installed side-by-side.</span></span>

<span data-ttu-id="b85e9-130">À partir de .NET Core 2.0, voici les règles qui s’appliquent pour déterminer quelle version du kit SDK utiliser :</span><span class="sxs-lookup"><span data-stu-id="b85e9-130">Starting with .NET Core 2.0, the following rules apply when determining which version of the SDK to use:</span></span>

- <span data-ttu-id="b85e9-131">Si aucun fichier *global.json* n’est trouvé ou que *global.json* ne spécifie pas de version du kit SDK, la dernière version installée du kit SDK est utilisée.</span><span class="sxs-lookup"><span data-stu-id="b85e9-131">If no *global.json* file is found or *global.json* doesn't specify an SDK version, the latest installed SDK version is used.</span></span> <span data-ttu-id="b85e9-132">La dernière version du kit SDK peut être une version ou une préversion (le numéro de version le plus élevé l’emporte).</span><span class="sxs-lookup"><span data-stu-id="b85e9-132">Latest SDK version can be either release or pre-release - the highest version number wins.</span></span>
- <span data-ttu-id="b85e9-133">Si la version du kit SDK n’est pas spécifiée dans *global.json* :</span><span class="sxs-lookup"><span data-stu-id="b85e9-133">If *global.json* does specify an SDK version:</span></span>
  - <span data-ttu-id="b85e9-134">Si la version spécifiée du kit SDK se trouve sur la machine, c’est cette même version qui est utilisée.</span><span class="sxs-lookup"><span data-stu-id="b85e9-134">If the specified SDK version is found on the machine, that exact version is used.</span></span>
  - <span data-ttu-id="b85e9-135">Si la version spécifiée du kit SDK est introuvable sur la machine, c’est la dernière **version corrective** installée du kit SDK qui est utilisée.</span><span class="sxs-lookup"><span data-stu-id="b85e9-135">If the specified SDK version can't be found on the machine, the latest installed SDK **patch version** of that version is used.</span></span> <span data-ttu-id="b85e9-136">La dernière **version corrective** installée du kit SDK peut être une version ou une préversion (le numéro de version le plus élevé l’emporte).</span><span class="sxs-lookup"><span data-stu-id="b85e9-136">Latest installed SDK **patch version** can be either release or pre-release - the highest version number wins.</span></span> <span data-ttu-id="b85e9-137">Dans .NET Core 2.1 et ultérieur, les **versions correctives** antérieures à la **version corrective** spécifiée sont ignorées dans la sélection du kit SDK.</span><span class="sxs-lookup"><span data-stu-id="b85e9-137">In .NET Core 2.1 and higher, the **patch versions** lower than the **patch version** specified are ignored in the SDK selection.</span></span>
  - <span data-ttu-id="b85e9-138">Dans le cas où ni la version spécifiée du kit SDK, ni une **version corrective** appropriée du kit SDK n’est trouvée, une erreur est générée.</span><span class="sxs-lookup"><span data-stu-id="b85e9-138">If the specified SDK version and an appropriate SDK **patch version** can't be found, an error is thrown.</span></span>

<span data-ttu-id="b85e9-139">La version du kit SDK se compose actuellement des éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="b85e9-139">The SDK version is currently composed of the following parts:</span></span>

`[.NET Core major version].[.NET Core minor version].[xyz][-optional preview name]`

<span data-ttu-id="b85e9-140">La **future version** du kit SDK .NET Core est représentée par le premier chiffre (`x`) de la dernière partie du nombre (`xyz`) pour les versions 2.1.100 et ultérieures du kit SDK.</span><span class="sxs-lookup"><span data-stu-id="b85e9-140">The **feature release** of the .NET Core SDK is represented by the first digit (`x`) in the last portion of the number (`xyz`) for SDK versions 2.1.100 and higher.</span></span> <span data-ttu-id="b85e9-141">En règle générale, le cycle de lancement du kit SDK .NET Core est plus rapide que celui de .NET Core.</span><span class="sxs-lookup"><span data-stu-id="b85e9-141">In general, the .NET Core SDK has a faster release cycle than .NET Core.</span></span>

<span data-ttu-id="b85e9-142">La **version corrective** est définie par les deux derniers chiffres (`yz`) de la dernière partie du nombre (`xyz`) pour les versions 2.1.100 et ultérieures du kit SDK.</span><span class="sxs-lookup"><span data-stu-id="b85e9-142">The **patch version** is defined by the last two digits (`yz`) in the last portion of the number (`xyz`) for SDK versions 2.1.100 and higher.</span></span> <span data-ttu-id="b85e9-143">Par exemple, si vous spécifiez la version `2.1.300` du kit SDK, le mécanisme de sélection du kit SDK trouve la version `2.1.399`, mais la version `2.1.400` n’est pas considérée comme une version corrective de la version `2.1.300`.</span><span class="sxs-lookup"><span data-stu-id="b85e9-143">For example, if you specify `2.1.300` as the SDK version, SDK selection finds up to `2.1.399` but `2.1.400` isn't considered a patch version for `2.1.300`.</span></span>

<span data-ttu-id="b85e9-144">Les versions du kit SDK .NET Core comprises entre `2.1.100` et `2.1.201` ont été lancées pendant la période transitoire entre les modèles de numérotation des versions et ne gèrent pas correctement la notation `xyz`.</span><span class="sxs-lookup"><span data-stu-id="b85e9-144">.NET Core SDK versions `2.1.100` through `2.1.201` were released during the transition between version number schemes and don't correctly handle the `xyz` notation.</span></span> <span data-ttu-id="b85e9-145">Si vous spécifiez ces versions dans le fichier *global.json*, nous vous recommandons vivement de vérifier que les versions spécifiées se trouvent sur les machines cibles.</span><span class="sxs-lookup"><span data-stu-id="b85e9-145">We highly recommend if you specify these versions in the *global.json* file, that you ensure the specified versions are on the target machines.</span></span>

<span data-ttu-id="b85e9-146">Pour le kit SDK .NET Core 1.x, si vous avez spécifié une version et qu’aucune correspondance exacte n’a été trouvée, la dernière version installée du kit SDK a été utilisée.</span><span class="sxs-lookup"><span data-stu-id="b85e9-146">With .NET Core SDK 1.x, if you specified a version and no exact match was found, the latest installed SDK version was used.</span></span> <span data-ttu-id="b85e9-147">La dernière version du kit SDK peut être une version ou une préversion (le numéro de version le plus élevé l’emporte).</span><span class="sxs-lookup"><span data-stu-id="b85e9-147">Latest SDK version can be either release or pre-release - the highest version number wins.</span></span>

## <a name="troubleshooting-build-warnings"></a><span data-ttu-id="b85e9-148">Résolutions des problèmes liés aux avertissements de build</span><span class="sxs-lookup"><span data-stu-id="b85e9-148">Troubleshooting build warnings</span></span>

> [!WARNING]
> <span data-ttu-id="b85e9-149">Vous utilisez une préversion du kit SDK .NET Core.</span><span class="sxs-lookup"><span data-stu-id="b85e9-149">You are working with a preview version of the .NET Core SDK.</span></span> <span data-ttu-id="b85e9-150">Vous pouvez définir la version du kit SDK via un fichier global.json dans le projet actif.</span><span class="sxs-lookup"><span data-stu-id="b85e9-150">You can define the SDK version via a global.json file in the current project.</span></span> <span data-ttu-id="b85e9-151">Pour plus d’informations, consultez <https://go.microsoft.com/fwlink/?linkid=869452></span><span class="sxs-lookup"><span data-stu-id="b85e9-151">More at <https://go.microsoft.com/fwlink/?linkid=869452></span></span>

<span data-ttu-id="b85e9-152">Cet avertissement indique que votre projet est compilé à partir d’une préversion du kit SDK .NET Core, comme indiqué dans la section [Règles de correspondance](#matching-rules).</span><span class="sxs-lookup"><span data-stu-id="b85e9-152">This warning indicates that your project is being compiled using a preview version of the .NET Core SDK, as explained in the [Matching rules](#matching-rules) section.</span></span> <span data-ttu-id="b85e9-153">Les versions du kit SDK .NET Core jouissent d’une image et d’un engagement de qualité.</span><span class="sxs-lookup"><span data-stu-id="b85e9-153">.NET Core SDK versions have a history and commitment of being high quality.</span></span> <span data-ttu-id="b85e9-154">Cependant, si vous ne voulez pas utiliser de préversion, ajoutez un fichier *global.json* à la structure hiérarchique de votre projet pour spécifier la version du kit SDK à utiliser, puis utilisez `dotnet --list-sdks` pour vérifier que la version est installée sur votre machine.</span><span class="sxs-lookup"><span data-stu-id="b85e9-154">However, if you don't want to use a preview version, add a *global.json* file to your project hierarchy structure to specify which SDK version to use, and use `dotnet --list-sdks` to confirm that the version is installed on your machine.</span></span> <span data-ttu-id="b85e9-155">Pour utiliser une nouvelle version au moment où celle-ci est lancée, supprimez le fichier *global.json* ou mettez-le à jour pour utiliser la version plus récente.</span><span class="sxs-lookup"><span data-stu-id="b85e9-155">When a new version is released, to use the new version, either remove the *global.json* file or update it to use the newer version.</span></span>

> [!WARNING]
> <span data-ttu-id="b85e9-156">Le projet de démarrage '{startupProject}' cible le framework '.NETCoreApp' version '{targetFrameworkVersion}'.</span><span class="sxs-lookup"><span data-stu-id="b85e9-156">Startup project '{startupProject}' targets framework '.NETCoreApp' version '{targetFrameworkVersion}'.</span></span> <span data-ttu-id="b85e9-157">Cette version des outils en ligne de commande Entity Framework Core .NET prend uniquement en charge la version 2.0 ou supérieure.</span><span class="sxs-lookup"><span data-stu-id="b85e9-157">This version of the Entity Framework Core .NET Command-line Tools only supports version 2.0 or higher.</span></span> <span data-ttu-id="b85e9-158">Pour plus d’informations sur l’utilisation d’anciennes versions des outils, consultez <https://go.microsoft.com/fwlink/?linkid=871254>.</span><span class="sxs-lookup"><span data-stu-id="b85e9-158">For information on using older versions of the tools, see <https://go.microsoft.com/fwlink/?linkid=871254></span></span>

<span data-ttu-id="b85e9-159">À partir du kit SDK .NET Core 2.1 (version 2.1.300), la commande `dotnet ef` est incluse dans le kit SDK.</span><span class="sxs-lookup"><span data-stu-id="b85e9-159">Starting with .NET Core 2.1 SDK (version 2.1.300), the `dotnet ef` command comes included in the SDK.</span></span> <span data-ttu-id="b85e9-160">Cet avertissement indique que votre projet cible EF Core 1.0 ou 1.1, qui n’est pas compatible avec le kit SDK .NET Core 2.1 (et les versions ultérieures).</span><span class="sxs-lookup"><span data-stu-id="b85e9-160">This warning indicates that your project targets EF Core 1.0 or 1.1, which isn't compatible with .NET Core 2.1 SDK and later versions.</span></span> <span data-ttu-id="b85e9-161">Pour compiler votre projet, installez le kit SDK .NET Core 2.0 (version 2.1.201) ou une version antérieure sur votre ordinateur et définissez la version du SDK à utiliser dans le fichier *global.json*.</span><span class="sxs-lookup"><span data-stu-id="b85e9-161">To compile your project, install .NET Core 2.0 SDK (version 2.1.201) and earlier on your machine and define the desired SDK version using the *global.json* file.</span></span> <span data-ttu-id="b85e9-162">Pour plus d’informations sur la commande `dotnet ef`, consultez [Outils en ligne de commande EF Core .NET](/ef/core/miscellaneous/cli/dotnet).</span><span class="sxs-lookup"><span data-stu-id="b85e9-162">For more information about the `dotnet ef` command, see [EF Core .NET Command-line Tools](/ef/core/miscellaneous/cli/dotnet).</span></span>

## <a name="see-also"></a><span data-ttu-id="b85e9-163">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b85e9-163">See also</span></span>

- [<span data-ttu-id="b85e9-164">Méthode de résolution des kits SDK de projet</span><span class="sxs-lookup"><span data-stu-id="b85e9-164">How project SDKs are resolved</span></span>](/visualstudio/msbuild/how-to-use-project-sdk#how-project-sdks-are-resolved)
