---
title: dotnet outil restaurer la commande
description: L’outil dotnet restaurer la commande installe sur votre machine les outils locaux .NET Core qui sont en portée pour l’annuaire actuel.
ms.date: 02/14/2020
ms.openlocfilehash: 0d1e67ec809ddd725721698cc741f9acc99e1ce7
ms.sourcegitcommit: c91110ef6ee3fedb591f3d628dc17739c4a7071e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/15/2020
ms.locfileid: "81389615"
---
# <a name="dotnet-tool-restore"></a><span data-ttu-id="1b086-103">dotnet tool restore</span><span class="sxs-lookup"><span data-stu-id="1b086-103">dotnet tool restore</span></span>

<span data-ttu-id="1b086-104">**Cet article s’applique à:** ✔️ .NET Core 3.0 SDK et les versions ultérieures</span><span class="sxs-lookup"><span data-stu-id="1b086-104">**This article applies to:** ✔️ .NET Core 3.0 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="1b086-105">Nom</span><span class="sxs-lookup"><span data-stu-id="1b086-105">Name</span></span>

<span data-ttu-id="1b086-106">`dotnet tool restore`- Installe sur votre machine les outils locaux .NET Core qui sont en portée pour l’annuaire actuel.</span><span class="sxs-lookup"><span data-stu-id="1b086-106">`dotnet tool restore` - Installs on your machine the .NET Core local tools that are in scope for the current directory.</span></span>

## <a name="synopsis"></a><span data-ttu-id="1b086-107">Synopsis</span><span class="sxs-lookup"><span data-stu-id="1b086-107">Synopsis</span></span>

```dotnetcli
dotnet tool restore <PACKAGE_NAME>
    [--configfile] [--add-source] [tool-manifest]
    [--disable-parallel] [--ignore-failed-sources]
    [--no-cache] [--interactive] [-v|--verbosity]

dotnet tool restore <-h|--help>
```

## <a name="description"></a><span data-ttu-id="1b086-108">Description</span><span class="sxs-lookup"><span data-stu-id="1b086-108">Description</span></span>

<span data-ttu-id="1b086-109">La `dotnet tool restore` commande trouve le fichier manifeste de l’outil qui est en portée pour l’annuaire actuel et installe les outils qui y sont répertoriés.</span><span class="sxs-lookup"><span data-stu-id="1b086-109">The `dotnet tool restore` command finds the tool manifest file that is in scope for the current directory and installs the tools that are listed in it.</span></span> <span data-ttu-id="1b086-110">Pour plus d’informations sur les fichiers manifestes, voir [Installer un outil local](global-tools.md#install-a-local-tool) et [invoquer un outil local](global-tools.md#invoke-a-local-tool).</span><span class="sxs-lookup"><span data-stu-id="1b086-110">For information about manifest files, see [Install a local tool](global-tools.md#install-a-local-tool) and [Invoke a local tool](global-tools.md#invoke-a-local-tool).</span></span>

## <a name="arguments"></a><span data-ttu-id="1b086-111">Arguments</span><span class="sxs-lookup"><span data-stu-id="1b086-111">Arguments</span></span>

- **`PACKAGE_NAME`**

<span data-ttu-id="1b086-112">Nom/ID du paquet NuGet qui contient l’outil .NET Core à installer.</span><span class="sxs-lookup"><span data-stu-id="1b086-112">Name/ID of the NuGet package that contains the .NET Core tool to install.</span></span>

## <a name="options"></a><span data-ttu-id="1b086-113">Options</span><span class="sxs-lookup"><span data-stu-id="1b086-113">Options</span></span>

- **`--configfile <FILE>`**

  <span data-ttu-id="1b086-114">Fichier de configuration NuGet (*nuget.config*) à utiliser.</span><span class="sxs-lookup"><span data-stu-id="1b086-114">The NuGet configuration (*nuget.config*) file to use.</span></span>

- **`--add-source <SOURCE>`**

  <span data-ttu-id="1b086-115">Ajoute une source de package NuGet supplémentaire à utiliser pendant l’installation.</span><span class="sxs-lookup"><span data-stu-id="1b086-115">Adds an additional NuGet package source to use during installation.</span></span>

- **`--tool-manifest <PATH>`**

  <span data-ttu-id="1b086-116">Chemin vers le fichier manifeste.</span><span class="sxs-lookup"><span data-stu-id="1b086-116">Path to the manifest file.</span></span>

- **`--disable-parallel`**

  <span data-ttu-id="1b086-117">Empêcher la restauration de plusieurs projets en parallèle.</span><span class="sxs-lookup"><span data-stu-id="1b086-117">Prevent restoring multiple projects in parallel.</span></span>

- **`--ignore-failed-sources`**

  <span data-ttu-id="1b086-118">Traiter les défaillances des sources de colis comme des avertissements.</span><span class="sxs-lookup"><span data-stu-id="1b086-118">Treat package source failures as warnings.</span></span>

- **`--no-cache`**

  <span data-ttu-id="1b086-119">Ne cachez pas les paquets et les demandes http.</span><span class="sxs-lookup"><span data-stu-id="1b086-119">Do not cache packages and http requests.</span></span>

- **`--interactive`**

  <span data-ttu-id="1b086-120">Permet à la commande de s’arrêter et d’attendre une saisie ou une action de l’utilisateur (par exemple, s’identifier).</span><span class="sxs-lookup"><span data-stu-id="1b086-120">Allows the command to stop and wait for user input or action (for example to complete authentication).</span></span>

- **`-h|--help`**

  <span data-ttu-id="1b086-121">Affiche une aide brève pour la commande.</span><span class="sxs-lookup"><span data-stu-id="1b086-121">Prints out a short help for the command.</span></span>

- **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="1b086-122">Définit le niveau de détail de la commande.</span><span class="sxs-lookup"><span data-stu-id="1b086-122">Sets the verbosity level of the command.</span></span> <span data-ttu-id="1b086-123">Les valeurs autorisées sont `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` et `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="1b086-123">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

## <a name="example"></a><span data-ttu-id="1b086-124">Exemple</span><span class="sxs-lookup"><span data-stu-id="1b086-124">Example</span></span>

- **`dotnet tool restore`**

  <span data-ttu-id="1b086-125">Restaure les outils locaux pour l’annuaire actuel.</span><span class="sxs-lookup"><span data-stu-id="1b086-125">Restores local tools for the current directory.</span></span>

## <a name="see-also"></a><span data-ttu-id="1b086-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1b086-126">See also</span></span>

- [<span data-ttu-id="1b086-127">.NET Outils de base</span><span class="sxs-lookup"><span data-stu-id="1b086-127">.NET Core tools</span></span>](global-tools.md)
- [<span data-ttu-id="1b086-128">Tutorial: Installer et utiliser un outil local .NET Core en utilisant le CLI .NET Core</span><span class="sxs-lookup"><span data-stu-id="1b086-128">Tutorial: Install and use a .NET Core local tool using the .NET Core CLI</span></span>](local-tools-how-to-use.md)
