---
title: commande de restauration de l’outil dotnet
description: La commande de restauration de l’outil dotnet installe sur votre machine les outils locaux .NET qui sont dans l’étendue du répertoire actif.
ms.date: 02/14/2020
ms.openlocfilehash: 3425bc6b78fd53f578c209013f83b006305dbb81
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96242927"
---
# <a name="dotnet-tool-restore"></a><span data-ttu-id="fbbb7-103">dotnet tool restore</span><span class="sxs-lookup"><span data-stu-id="fbbb7-103">dotnet tool restore</span></span>

<span data-ttu-id="fbbb7-104">**Cet article s’applique à : ✔️ le kit de** développement logiciel (SDK) .net Core 3,0 et versions ultérieures</span><span class="sxs-lookup"><span data-stu-id="fbbb7-104">**This article applies to:** ✔️ .NET Core 3.0 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="fbbb7-105">Nom</span><span class="sxs-lookup"><span data-stu-id="fbbb7-105">Name</span></span>

<span data-ttu-id="fbbb7-106">`dotnet tool restore` -Installe les outils locaux .NET qui sont dans l’étendue du répertoire actif.</span><span class="sxs-lookup"><span data-stu-id="fbbb7-106">`dotnet tool restore` - Installs the .NET local tools that are in scope for the current directory.</span></span>

## <a name="synopsis"></a><span data-ttu-id="fbbb7-107">Synopsis</span><span class="sxs-lookup"><span data-stu-id="fbbb7-107">Synopsis</span></span>

```dotnetcli
dotnet tool restore
    [--configfile <FILE>] [--add-source <SOURCE>]
    [tool-manifest <PATH_TO_MANIFEST_FILE>] [--disable-parallel]
    [--ignore-failed-sources] [--no-cache] [--interactive]
    [-v|--verbosity <LEVEL>]

dotnet tool restore -h|--help
```

## <a name="description"></a><span data-ttu-id="fbbb7-108">Description</span><span class="sxs-lookup"><span data-stu-id="fbbb7-108">Description</span></span>

<span data-ttu-id="fbbb7-109">La `dotnet tool restore` commande recherche le fichier de manifeste de l’outil qui est dans la portée du répertoire actif et installe les outils qui y sont répertoriés.</span><span class="sxs-lookup"><span data-stu-id="fbbb7-109">The `dotnet tool restore` command finds the tool manifest file that is in scope for the current directory and installs the tools that are listed in it.</span></span> <span data-ttu-id="fbbb7-110">Pour plus d’informations sur les fichiers manifestes, consultez [installer un outil local](global-tools.md#install-a-local-tool) et [appeler un outil local](global-tools.md#invoke-a-local-tool).</span><span class="sxs-lookup"><span data-stu-id="fbbb7-110">For information about manifest files, see [Install a local tool](global-tools.md#install-a-local-tool) and [Invoke a local tool](global-tools.md#invoke-a-local-tool).</span></span>

## <a name="options"></a><span data-ttu-id="fbbb7-111">Options</span><span class="sxs-lookup"><span data-stu-id="fbbb7-111">Options</span></span>

- **`--configfile <FILE>`**

  <span data-ttu-id="fbbb7-112">Fichier de configuration NuGet (*nuget.config*) à utiliser.</span><span class="sxs-lookup"><span data-stu-id="fbbb7-112">The NuGet configuration (*nuget.config*) file to use.</span></span>

- **`--add-source <SOURCE>`**

  <span data-ttu-id="fbbb7-113">Ajoute une source de package NuGet supplémentaire à utiliser pendant l’installation.</span><span class="sxs-lookup"><span data-stu-id="fbbb7-113">Adds an additional NuGet package source to use during installation.</span></span>

- **`--tool-manifest <PATH>`**

  <span data-ttu-id="fbbb7-114">Chemin d’accès au fichier manifeste.</span><span class="sxs-lookup"><span data-stu-id="fbbb7-114">Path to the manifest file.</span></span>

- **`--disable-parallel`**

  <span data-ttu-id="fbbb7-115">Empêcher la restauration en parallèle de plusieurs projets.</span><span class="sxs-lookup"><span data-stu-id="fbbb7-115">Prevent restoring multiple projects in parallel.</span></span>

- **`--ignore-failed-sources`**

  <span data-ttu-id="fbbb7-116">Considérer les défaillances de la source du package comme des avertissements.</span><span class="sxs-lookup"><span data-stu-id="fbbb7-116">Treat package source failures as warnings.</span></span>

- **`--no-cache`**

  <span data-ttu-id="fbbb7-117">Ne pas mettre en cache les packages et les requêtes http.</span><span class="sxs-lookup"><span data-stu-id="fbbb7-117">Do not cache packages and http requests.</span></span>

- **`--interactive`**

  <span data-ttu-id="fbbb7-118">Permet à la commande de s’arrêter et d’attendre une saisie ou une action de l’utilisateur (par exemple, s’identifier).</span><span class="sxs-lookup"><span data-stu-id="fbbb7-118">Allows the command to stop and wait for user input or action (for example to complete authentication).</span></span>

- **`-h|--help`**

  <span data-ttu-id="fbbb7-119">Affiche une aide brève pour la commande.</span><span class="sxs-lookup"><span data-stu-id="fbbb7-119">Prints out a short help for the command.</span></span>

- **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="fbbb7-120">Définit le niveau de détail de la commande.</span><span class="sxs-lookup"><span data-stu-id="fbbb7-120">Sets the verbosity level of the command.</span></span> <span data-ttu-id="fbbb7-121">Les valeurs autorisées sont `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` et `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="fbbb7-121">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

## <a name="example"></a><span data-ttu-id="fbbb7-122"> Exemple</span><span class="sxs-lookup"><span data-stu-id="fbbb7-122">Example</span></span>

- **`dotnet tool restore`**

  <span data-ttu-id="fbbb7-123">Restaure les outils locaux pour le répertoire actif.</span><span class="sxs-lookup"><span data-stu-id="fbbb7-123">Restores local tools for the current directory.</span></span>

## <a name="see-also"></a><span data-ttu-id="fbbb7-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fbbb7-124">See also</span></span>

- [<span data-ttu-id="fbbb7-125">Outils .NET</span><span class="sxs-lookup"><span data-stu-id="fbbb7-125">.NET tools</span></span>](global-tools.md)
- [<span data-ttu-id="fbbb7-126">Didacticiel : installer et utiliser un outil local .NET à l’aide de l’interface de commande .NET</span><span class="sxs-lookup"><span data-stu-id="fbbb7-126">Tutorial: Install and use a .NET local tool using the .NET CLI</span></span>](local-tools-how-to-use.md)
