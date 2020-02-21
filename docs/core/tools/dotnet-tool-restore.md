---
title: commande de restauration de l’outil dotnet
description: La commande de restauration de l’outil dotnet installe sur votre machine les outils locaux .NET Core qui sont dans l’étendue du répertoire actif.
ms.date: 02/14/2020
ms.openlocfilehash: 2900d431987661a9232ceed10d9a424093f8be45
ms.sourcegitcommit: 771c554c84ba38cbd4ac0578324ec4cfc979cf2e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/21/2020
ms.locfileid: "77543907"
---
# <a name="dotnet-tool-restore"></a><span data-ttu-id="0797c-103">restauration de l’outil dotnet</span><span class="sxs-lookup"><span data-stu-id="0797c-103">dotnet tool restore</span></span>

<span data-ttu-id="0797c-104">**Cet article s’applique à : ✔️ le kit de** développement logiciel (SDK) .net Core 3,0 et versions ultérieures</span><span class="sxs-lookup"><span data-stu-id="0797c-104">**This article applies to:** ✔️ .NET Core 3.0 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="0797c-105">Name</span><span class="sxs-lookup"><span data-stu-id="0797c-105">Name</span></span>

<span data-ttu-id="0797c-106">`dotnet tool restore`-installe sur votre machine les outils locaux .NET Core qui sont dans l’étendue du répertoire actif.</span><span class="sxs-lookup"><span data-stu-id="0797c-106">`dotnet tool restore` - Installs on your machine the .NET Core local tools that are in scope for the current directory.</span></span>

## <a name="synopsis"></a><span data-ttu-id="0797c-107">Synopsis</span><span class="sxs-lookup"><span data-stu-id="0797c-107">Synopsis</span></span>

```dotnetcli
dotnet tool restore <PACKAGE_NAME> [--configfile] [--add-source] [tool-manifest] [--disable-parallel] [--ignore-failed-sources] [--no-cache] [-interactive] [-v|--verbosity]
dotnet tool restore <-h|--help>
```

## <a name="description"></a><span data-ttu-id="0797c-108">Description</span><span class="sxs-lookup"><span data-stu-id="0797c-108">Description</span></span>

<span data-ttu-id="0797c-109">La commande `dotnet tool restore` recherche le fichier de manifeste de l’outil qui est dans la portée du répertoire actif et installe les outils qui y sont répertoriés.</span><span class="sxs-lookup"><span data-stu-id="0797c-109">The `dotnet tool restore` command finds the tool manifest file that is in scope for the current directory and installs the tools that are listed in it.</span></span> <span data-ttu-id="0797c-110">Pour plus d’informations sur les fichiers manifestes, consultez [installer un outil local](global-tools.md#install-a-local-tool) et [appeler un outil local](global-tools.md#invoke-a-local-tool).</span><span class="sxs-lookup"><span data-stu-id="0797c-110">For information about manifest files, see [Install a local tool](global-tools.md#install-a-local-tool) and [Invoke a local tool](global-tools.md#invoke-a-local-tool).</span></span>

## <a name="arguments"></a><span data-ttu-id="0797c-111">Arguments</span><span class="sxs-lookup"><span data-stu-id="0797c-111">Arguments</span></span>

- **`PACKAGE_NAME`**

<span data-ttu-id="0797c-112">Nom/ID du package NuGet qui contient l’outil .NET Core à installer.</span><span class="sxs-lookup"><span data-stu-id="0797c-112">Name/ID of the NuGet package that contains the .NET Core tool to install.</span></span>

## <a name="options"></a><span data-ttu-id="0797c-113">Options</span><span class="sxs-lookup"><span data-stu-id="0797c-113">Options</span></span>

- **`--configfile <FILE>`**

  <span data-ttu-id="0797c-114">Fichier de configuration NuGet (*nuget.config*) à utiliser.</span><span class="sxs-lookup"><span data-stu-id="0797c-114">The NuGet configuration (*nuget.config*) file to use.</span></span>

- **`--add-source <SOURCE>`**

  <span data-ttu-id="0797c-115">Ajoute une source de package NuGet supplémentaire à utiliser pendant l’installation.</span><span class="sxs-lookup"><span data-stu-id="0797c-115">Adds an additional NuGet package source to use during installation.</span></span>

- **`--tool-manifest <PATH>`**

  <span data-ttu-id="0797c-116">Chemin d’accès au fichier manifeste.</span><span class="sxs-lookup"><span data-stu-id="0797c-116">Path to the manifest file.</span></span>

- **`--disable-parallel`**

  <span data-ttu-id="0797c-117">Empêcher la restauration en parallèle de plusieurs projets.</span><span class="sxs-lookup"><span data-stu-id="0797c-117">Prevent restoring multiple projects in parallel.</span></span>

- **`--ignore-failed-sources`**

  <span data-ttu-id="0797c-118">Considérer les défaillances de la source du package comme des avertissements.</span><span class="sxs-lookup"><span data-stu-id="0797c-118">Treat package source failures as warnings.</span></span>

- **`--no-cache`**

  <span data-ttu-id="0797c-119">Ne pas mettre en cache les packages et les requêtes http.</span><span class="sxs-lookup"><span data-stu-id="0797c-119">Do not cache packages and http requests.</span></span>

- **`--interactive`**

  <span data-ttu-id="0797c-120">Permet à la commande de s’arrêter et d’attendre une saisie ou une action de l’utilisateur (par exemple, s’authentifier).</span><span class="sxs-lookup"><span data-stu-id="0797c-120">Allows the command to stop and wait for user input or action (for example to complete authentication).</span></span>

- **`-h|--help`**

  <span data-ttu-id="0797c-121">Affiche une aide brève pour la commande.</span><span class="sxs-lookup"><span data-stu-id="0797c-121">Prints out a short help for the command.</span></span>

- **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="0797c-122">Définit le niveau de détail de la commande.</span><span class="sxs-lookup"><span data-stu-id="0797c-122">Sets the verbosity level of the command.</span></span> <span data-ttu-id="0797c-123">Les valeurs autorisées sont `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` et `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="0797c-123">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

## <a name="example"></a><span data-ttu-id="0797c-124">Exemple</span><span class="sxs-lookup"><span data-stu-id="0797c-124">Example</span></span>

- **`dotnet tool restore`**

  <span data-ttu-id="0797c-125">Restaure les outils locaux pour le répertoire actif.</span><span class="sxs-lookup"><span data-stu-id="0797c-125">Restores local tools for the current directory.</span></span>

## <a name="see-also"></a><span data-ttu-id="0797c-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0797c-126">See also</span></span>

- [<span data-ttu-id="0797c-127">Outils .NET Core</span><span class="sxs-lookup"><span data-stu-id="0797c-127">.NET Core tools</span></span>](global-tools.md)
