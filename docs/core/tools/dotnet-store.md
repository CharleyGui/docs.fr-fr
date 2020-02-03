---
title: Commande dotnet store
description: La commande « dotnet store » stocke les assemblys spécifiés dans le magasin de packages de runtime.
ms.date: 05/29/2018
ms.openlocfilehash: cc5b4b6160ba296e1529f006c15e238746d9e08a
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76733052"
---
# <a name="dotnet-store"></a><span data-ttu-id="bc2f7-103">dotnet store</span><span class="sxs-lookup"><span data-stu-id="bc2f7-103">dotnet store</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-2plus.md)]

## <a name="name"></a><span data-ttu-id="bc2f7-104">Nom</span><span class="sxs-lookup"><span data-stu-id="bc2f7-104">Name</span></span>

<span data-ttu-id="bc2f7-105">`dotnet store` : stocke les assemblys spécifiés dans le [magasin de packages de runtime](../deploying/runtime-store.md).</span><span class="sxs-lookup"><span data-stu-id="bc2f7-105">`dotnet store` - Stores the specified assemblies in the [runtime package store](../deploying/runtime-store.md).</span></span>

## <a name="synopsis"></a><span data-ttu-id="bc2f7-106">Résumé</span><span class="sxs-lookup"><span data-stu-id="bc2f7-106">Synopsis</span></span>

`dotnet store -m|--manifest -f|--framework -r|--runtime  [--framework-version] [-h|--help] [--output] [--skip-optimization] [--skip-symbols] [-v|--verbosity] [--working-dir]`

## <a name="description"></a><span data-ttu-id="bc2f7-107">Description</span><span class="sxs-lookup"><span data-stu-id="bc2f7-107">Description</span></span>

<span data-ttu-id="bc2f7-108">`dotnet store` stocke les assemblys spécifiés dans le [magasin de packages de runtime](../deploying/runtime-store.md).</span><span class="sxs-lookup"><span data-stu-id="bc2f7-108">`dotnet store` stores the specified assemblies in the [runtime package store](../deploying/runtime-store.md).</span></span> <span data-ttu-id="bc2f7-109">Par défaut, les assemblys sont optimisés pour les runtime et framework cibles.</span><span class="sxs-lookup"><span data-stu-id="bc2f7-109">By default, assemblies are optimized for the target runtime and framework.</span></span> <span data-ttu-id="bc2f7-110">Pour plus d’informations, consultez la rubrique [Magasin de packages de runtime](../deploying/runtime-store.md).</span><span class="sxs-lookup"><span data-stu-id="bc2f7-110">For more information, see the [runtime package store](../deploying/runtime-store.md) topic.</span></span>

## <a name="required-options"></a><span data-ttu-id="bc2f7-111">Options obligatoires</span><span class="sxs-lookup"><span data-stu-id="bc2f7-111">Required options</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="bc2f7-112">Spécifie le [framework cible](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="bc2f7-112">Specifies the [target framework](../../standard/frameworks.md).</span></span>

`-m|--manifest <PATH_TO_MANIFEST_FILE>`

<span data-ttu-id="bc2f7-113">Le *fichier manifeste du magasin de packages* est un fichier XML qui contient la liste des packages à stocker.</span><span class="sxs-lookup"><span data-stu-id="bc2f7-113">The *package store manifest file* is an XML file that contains the list of packages to store.</span></span> <span data-ttu-id="bc2f7-114">Le format du fichier manifeste est compatible avec celui du projet de style SDK.</span><span class="sxs-lookup"><span data-stu-id="bc2f7-114">The format of the manifest file is compatible with the SDK-style project format.</span></span> <span data-ttu-id="bc2f7-115">Ainsi, vous pouvez utiliser un fichier projet qui référence les packages souhaités avec l’option `-m|--manifest` pour stocker des assemblys dans le magasin de packages de runtime.</span><span class="sxs-lookup"><span data-stu-id="bc2f7-115">So, a project file that references the desired packages can be used with the `-m|--manifest` option to store assemblies in the runtime package store.</span></span> <span data-ttu-id="bc2f7-116">Pour spécifier plusieurs fichiers manifeste, répétez l’option et le chemin pour chaque fichier.</span><span class="sxs-lookup"><span data-stu-id="bc2f7-116">To specify multiple manifest files, repeat the option and path for each file.</span></span> <span data-ttu-id="bc2f7-117">Par exemple : `--manifest packages1.csproj --manifest packages2.csproj`.</span><span class="sxs-lookup"><span data-stu-id="bc2f7-117">For example: `--manifest packages1.csproj --manifest packages2.csproj`.</span></span>

`-r|--runtime <RUNTIME_IDENTIFIER>`

<span data-ttu-id="bc2f7-118">[Identificateur du runtime](../rid-catalog.md) à cibler.</span><span class="sxs-lookup"><span data-stu-id="bc2f7-118">The [runtime identifier](../rid-catalog.md) to target.</span></span>

## <a name="optional-options"></a><span data-ttu-id="bc2f7-119">Options facultatives</span><span class="sxs-lookup"><span data-stu-id="bc2f7-119">Optional options</span></span>

`--framework-version <FRAMEWORK_VERSION>`

<span data-ttu-id="bc2f7-120">Spécifie la version du SDK .NET Core.</span><span class="sxs-lookup"><span data-stu-id="bc2f7-120">Specifies the .NET Core SDK version.</span></span> <span data-ttu-id="bc2f7-121">Cette option vous permet de sélectionner une version de framework spécifique en plus du framework indiqué par l’option `-f|--framework`.</span><span class="sxs-lookup"><span data-stu-id="bc2f7-121">This option enables you to select a specific framework version beyond the framework specified by the `-f|--framework` option.</span></span>

`-h|--help`

<span data-ttu-id="bc2f7-122">Affiche des informations d’aide.</span><span class="sxs-lookup"><span data-stu-id="bc2f7-122">Shows help information.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="bc2f7-123">Spécifie le chemin du magasin de packages de runtime.</span><span class="sxs-lookup"><span data-stu-id="bc2f7-123">Specifies the path to the runtime package store.</span></span> <span data-ttu-id="bc2f7-124">Si ce chemin n’est pas spécifié, le sous-répertoire *store* du répertoire d’installation de .NET Core du profil de l’utilisateur est choisi par défaut.</span><span class="sxs-lookup"><span data-stu-id="bc2f7-124">If not specified, it defaults to the *store* subdirectory of the user profile .NET Core installation directory.</span></span>

`--skip-optimization`

<span data-ttu-id="bc2f7-125">Ignore la phase d’optimisation.</span><span class="sxs-lookup"><span data-stu-id="bc2f7-125">Skips the optimization phase.</span></span>

`--skip-symbols`

<span data-ttu-id="bc2f7-126">Ignore la génération de symboles.</span><span class="sxs-lookup"><span data-stu-id="bc2f7-126">Skips symbol generation.</span></span> <span data-ttu-id="bc2f7-127">Vous pouvez uniquement générer des symboles sur Windows et Linux.</span><span class="sxs-lookup"><span data-stu-id="bc2f7-127">Currently, you can only generate symbols on Windows and Linux.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="bc2f7-128">Définit le niveau de détail de la commande.</span><span class="sxs-lookup"><span data-stu-id="bc2f7-128">Sets the verbosity level of the command.</span></span> <span data-ttu-id="bc2f7-129">Les valeurs autorisées sont `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` et `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="bc2f7-129">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

`-w|--working-dir <INTERMEDIATE_WORKING_DIRECTORY>`

<span data-ttu-id="bc2f7-130">Répertoire de travail utilisé par la commande.</span><span class="sxs-lookup"><span data-stu-id="bc2f7-130">The working directory used by the command.</span></span> <span data-ttu-id="bc2f7-131">S’il n’est pas spécifié, il utilise le sous-répertoire *obj* du répertoire actuel.</span><span class="sxs-lookup"><span data-stu-id="bc2f7-131">If not specified, it uses the *obj* subdirectory of the current directory.</span></span>

## <a name="examples"></a><span data-ttu-id="bc2f7-132">Exemples</span><span class="sxs-lookup"><span data-stu-id="bc2f7-132">Examples</span></span>

<span data-ttu-id="bc2f7-133">Stocker les packages spécifiés dans le fichier projet *packages.csproj* pour .NET Core 2.0.0 :</span><span class="sxs-lookup"><span data-stu-id="bc2f7-133">Store the packages specified in the *packages.csproj* project file for .NET Core 2.0.0:</span></span>

`dotnet store --manifest packages.csproj --framework-version 2.0.0`

<span data-ttu-id="bc2f7-134">Stocker les packages spécifiés dans le fichier projet *packages.csproj* sans optimisation :</span><span class="sxs-lookup"><span data-stu-id="bc2f7-134">Store the packages specified in the *packages.csproj* without optimization:</span></span>

`dotnet store --manifest packages.csproj --skip-optimization`

## <a name="see-also"></a><span data-ttu-id="bc2f7-135">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bc2f7-135">See also</span></span>

- [<span data-ttu-id="bc2f7-136">Magasin de packages de runtime</span><span class="sxs-lookup"><span data-stu-id="bc2f7-136">Runtime package store</span></span>](../deploying/runtime-store.md)
