---
title: Commande dotnet clean
description: La commande dotnet clean nettoie le répertoire actif.
ms.date: 06/26/2019
ms.openlocfilehash: 982232833b460b4ea4181acebee74dcef54d3131
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2019
ms.locfileid: "71117744"
---
# <a name="dotnet-clean"></a><span data-ttu-id="68297-103">dotnet clean</span><span class="sxs-lookup"><span data-stu-id="68297-103">dotnet clean</span></span>

<span data-ttu-id="68297-104">**Cette rubrique s’applique à : ✓** SDK .NET Core 1.x et ultérieur</span><span class="sxs-lookup"><span data-stu-id="68297-104">**This topic applies to: ✓** .NET Core 1.x SDK and later versions</span></span>

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]
-->

## <a name="name"></a><span data-ttu-id="68297-105">Name</span><span class="sxs-lookup"><span data-stu-id="68297-105">Name</span></span>

<span data-ttu-id="68297-106">`dotnet clean` : Nettoie la sortie d’un projet.</span><span class="sxs-lookup"><span data-stu-id="68297-106">`dotnet clean` - Cleans the output of a project.</span></span>

## <a name="synopsis"></a><span data-ttu-id="68297-107">Résumé</span><span class="sxs-lookup"><span data-stu-id="68297-107">Synopsis</span></span>

```dotnetcli
dotnet clean [<PROJECT>|<SOLUTION>] [-c|--configuration] [-f|--framework] [--interactive] 
    [--nologo] [-o|--output] [-r|--runtime] [-v|--verbosity]
dotnet clean [-h|--help]
```

## <a name="description"></a><span data-ttu-id="68297-108">Description</span><span class="sxs-lookup"><span data-stu-id="68297-108">Description</span></span>

<span data-ttu-id="68297-109">La commande `dotnet clean` nettoie la sortie de la génération précédente.</span><span class="sxs-lookup"><span data-stu-id="68297-109">The `dotnet clean` command cleans the output of the previous build.</span></span> <span data-ttu-id="68297-110">Comme elle est implémentée en tant que [cible MSBuild](/visualstudio/msbuild/msbuild-targets), le projet est évalué lorsque la commande est exécutée.</span><span class="sxs-lookup"><span data-stu-id="68297-110">It's implemented as an [MSBuild target](/visualstudio/msbuild/msbuild-targets), so the project is evaluated when the command is run.</span></span> <span data-ttu-id="68297-111">Seules les sorties créées lors de la génération sont nettoyées.</span><span class="sxs-lookup"><span data-stu-id="68297-111">Only the outputs created during the build are cleaned.</span></span> <span data-ttu-id="68297-112">Les dossiers de sortie intermédiaire (*obj*) et de sortie finale (*bin*) sont tous deux nettoyés.</span><span class="sxs-lookup"><span data-stu-id="68297-112">Both intermediate (*obj*) and final output (*bin*) folders are cleaned.</span></span>

## <a name="arguments"></a><span data-ttu-id="68297-113">Arguments</span><span class="sxs-lookup"><span data-stu-id="68297-113">Arguments</span></span>

`PROJECT | SOLUTION`

<span data-ttu-id="68297-114">Projet ou solution MSBuild à nettoyer.</span><span class="sxs-lookup"><span data-stu-id="68297-114">The MSBuild project or solution to clean.</span></span> <span data-ttu-id="68297-115">Si vous ne spécifiez pas de fichier projet ou solution, MSBuild recherche dans le répertoire de travail actif un fichier dont l’extension se termine par *proj* ou *sln* et l’utilise.</span><span class="sxs-lookup"><span data-stu-id="68297-115">If a project or solution file is not specified, MSBuild searches the current working directory for a file that has a file extension that ends in *proj* or *sln*, and uses that file.</span></span>

## <a name="options"></a><span data-ttu-id="68297-116">Options</span><span class="sxs-lookup"><span data-stu-id="68297-116">Options</span></span>

* **`-c|--configuration {Debug|Release}`**

  <span data-ttu-id="68297-117">Définit la configuration de build.</span><span class="sxs-lookup"><span data-stu-id="68297-117">Defines the build configuration.</span></span> <span data-ttu-id="68297-118">La valeur par défaut est `Debug`.</span><span class="sxs-lookup"><span data-stu-id="68297-118">The default value is `Debug`.</span></span> <span data-ttu-id="68297-119">Cette option est uniquement requise durant le nettoyage si vous l’avez spécifiée au moment de la génération.</span><span class="sxs-lookup"><span data-stu-id="68297-119">This option is only required when cleaning if you specified it during build time.</span></span>

* **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="68297-120">Le [framework](../../standard/frameworks.md) spécifié au moment de la génération.</span><span class="sxs-lookup"><span data-stu-id="68297-120">The [framework](../../standard/frameworks.md) that was specified at build time.</span></span> <span data-ttu-id="68297-121">Le framework doit être défini dans le [fichier projet](csproj.md).</span><span class="sxs-lookup"><span data-stu-id="68297-121">The framework must be defined in the [project file](csproj.md).</span></span> <span data-ttu-id="68297-122">Si vous avez spécifié le framework au moment de la génération, vous devez spécifier le framework lors du nettoyage.</span><span class="sxs-lookup"><span data-stu-id="68297-122">If you specified the framework at build time, you must specify the framework when cleaning.</span></span>

* **`-h|--help`**

  <span data-ttu-id="68297-123">Affiche une aide brève pour la commande.</span><span class="sxs-lookup"><span data-stu-id="68297-123">Prints out a short help for the command.</span></span>

* **`--interactive`**

  <span data-ttu-id="68297-124">Permet à la commande de s’arrêter et d’attendre une action ou une entrée utilisateur.</span><span class="sxs-lookup"><span data-stu-id="68297-124">Allows the command to stop and wait for user input or action.</span></span> <span data-ttu-id="68297-125">Par exemple, pour effectuer une authentification.</span><span class="sxs-lookup"><span data-stu-id="68297-125">For example, to complete authentication.</span></span> <span data-ttu-id="68297-126">Option disponible à partir du kit SDK .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="68297-126">Available since .NET Core 3.0 SDK.</span></span>

* **`--nologo`**

  <span data-ttu-id="68297-127">N’affiche pas la bannière de démarrage ni le message de copyright.</span><span class="sxs-lookup"><span data-stu-id="68297-127">Doesn't display the startup banner or the copyright message.</span></span> <span data-ttu-id="68297-128">Option disponible à partir du kit SDK .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="68297-128">Available since .NET Core 3.0 SDK.</span></span>

* **`-o|--output <OUTPUT_DIRECTORY>`**

  <span data-ttu-id="68297-129">Répertoire contenant les artefacts de build à nettoyer.</span><span class="sxs-lookup"><span data-stu-id="68297-129">The directory that contains the build artifacts to clean.</span></span> <span data-ttu-id="68297-130">Spécifiez le commutateur `-f|--framework <FRAMEWORK>` avec le commutateur de répertoire de sortie si vous avez spécifié le framework lorsque le projet a été généré.</span><span class="sxs-lookup"><span data-stu-id="68297-130">Specify the `-f|--framework <FRAMEWORK>` switch with the output directory switch if you specified the framework when the project was built.</span></span>

* **`-r|--runtime <RUNTIME_IDENTIFIER>`**

  <span data-ttu-id="68297-131">Nettoie le dossier de sortie du runtime spécifié.</span><span class="sxs-lookup"><span data-stu-id="68297-131">Cleans the output folder of the specified runtime.</span></span> <span data-ttu-id="68297-132">Cette option est utilisée à la création d’un [déploiement autonome](../deploying/index.md#self-contained-deployments-scd).</span><span class="sxs-lookup"><span data-stu-id="68297-132">This is used when a [self-contained deployment](../deploying/index.md#self-contained-deployments-scd) was created.</span></span> <span data-ttu-id="68297-133">Option disponible à partir du kit SDK .NET Core 2.0.</span><span class="sxs-lookup"><span data-stu-id="68297-133">Option available since .NET Core 2.0 SDK.</span></span>

* **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="68297-134">Définit le niveau de détail MSBuild.</span><span class="sxs-lookup"><span data-stu-id="68297-134">Sets the MSBuild verbosity level.</span></span> <span data-ttu-id="68297-135">Les valeurs autorisées sont `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` et `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="68297-135">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="68297-136">La valeur par défaut est `normal`.</span><span class="sxs-lookup"><span data-stu-id="68297-136">The default is `normal`.</span></span>

## <a name="examples"></a><span data-ttu-id="68297-137">Exemples</span><span class="sxs-lookup"><span data-stu-id="68297-137">Examples</span></span>

* <span data-ttu-id="68297-138">Nettoyez une génération par défaut du projet :</span><span class="sxs-lookup"><span data-stu-id="68297-138">Clean a default build of the project:</span></span>

  ```dotnetcli
  dotnet clean
  ```

* <span data-ttu-id="68297-139">Nettoyez un projet généré à l’aide de la configuration Release :</span><span class="sxs-lookup"><span data-stu-id="68297-139">Clean a project built using the Release configuration:</span></span>

  ```dotnetcli
  dotnet clean --configuration Release
  ```
