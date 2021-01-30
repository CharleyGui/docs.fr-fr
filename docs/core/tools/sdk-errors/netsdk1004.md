---
title: 'NETSDK1004 : fichier de ressources introuvable'
description: En savoir plus sur l’erreur du kit de développement logiciel (SDK) .NET NETSDK1004, qui se produit lorsque l' project.assets.jssur le fichier est introuvable.
ms.topic: error-reference
ms.date: 01/29/2021
f1_keywords:
- NETSDK1004
ms.openlocfilehash: 8416063fe318106cbcb4dbccacef3ecaaff5bba2
ms.sourcegitcommit: 68c9d9d9a97aab3b59d388914004b5474cf1dbd7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/30/2021
ms.locfileid: "99216433"
---
# <a name="netsdk1004-assets-file-not-found"></a><span data-ttu-id="13af5-103">NETSDK1004 : fichier de ressources introuvable</span><span class="sxs-lookup"><span data-stu-id="13af5-103">NETSDK1004: Assets file not found</span></span>

<span data-ttu-id="13af5-104">**Cet article s’applique à :** ✔️ Kit de développement logiciel (SDK) 2.1.100 .net Core et versions ultérieures</span><span class="sxs-lookup"><span data-stu-id="13af5-104">**This article applies to:** ✔️ .NET Core 2.1.100 SDK and later versions</span></span>

<span data-ttu-id="13af5-105">NuGet écrit un fichier nommé *project.assets.js* dans le dossier *obj* , et le kit de développement logiciel (SDK) .net l’utilise pour obtenir des informations sur les packages à passer au compilateur.</span><span class="sxs-lookup"><span data-stu-id="13af5-105">NuGet writes a file named *project.assets.json* in the *obj* folder, and the .NET SDK uses it to get information about packages to pass into the compiler.</span></span> <span data-ttu-id="13af5-106">Cette erreur se produit lorsque le fichier *de ressourcesproject.assets.jssur* est introuvable lors de la génération.</span><span class="sxs-lookup"><span data-stu-id="13af5-106">This error occurs when the assets file *project.assets.json* is not found during build.</span></span> <span data-ttu-id="13af5-107">Le message d’erreur complet est semblable à l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="13af5-107">The full error message is similar to the following example:</span></span>

<span data-ttu-id="13af5-108">**NETSDK1004 : le fichier de ressources' C:\path\to\project.assets.json’est introuvable. Exécutez une restauration de package NuGet pour générer ce fichier.**</span><span class="sxs-lookup"><span data-stu-id="13af5-108">**NETSDK1004: Assets file 'C:\path\to\project.assets.json' not found. Run a NuGet package restore to generate this file.**</span></span>

<span data-ttu-id="13af5-109">Voici quelques causes possibles de l’erreur :</span><span class="sxs-lookup"><span data-stu-id="13af5-109">Here are some possible causes of the error:</span></span>

* <span data-ttu-id="13af5-110">Vous exécutez la `dotnet build` commande à partir d’un chemin d’accès de répertoire contenant un `%` caractère.</span><span class="sxs-lookup"><span data-stu-id="13af5-110">You are running the `dotnet build` command from a directory path that contains a `%` character.</span></span> <span data-ttu-id="13af5-111">Pour résoudre l’erreur, supprimez du `%` nom de dossier, puis réexécutez `dotnet build` .</span><span class="sxs-lookup"><span data-stu-id="13af5-111">To resolve the error, remove the `%` from the folder name, and rerun `dotnet build`.</span></span>
* <span data-ttu-id="13af5-112">Une modification apportée au fichier projet n’a pas été automatiquement détectée et restaurée par le système de projet.</span><span class="sxs-lookup"><span data-stu-id="13af5-112">A change to the project file wasn't automatically detected and restored by the project system.</span></span> <span data-ttu-id="13af5-113">Pour résoudre l’erreur, ouvrez une invite de commandes et exécutez `dotnet restore` sur le projet.</span><span class="sxs-lookup"><span data-stu-id="13af5-113">To resolve the error, open a command prompt and run `dotnet restore` on the project.</span></span>
* <span data-ttu-id="13af5-114">Un projet a été restauré séparément par une version antérieure de Nuget.exe.</span><span class="sxs-lookup"><span data-stu-id="13af5-114">A project was restored separately by an older version of Nuget.exe.</span></span> <span data-ttu-id="13af5-115">Pour résoudre l’erreur, ouvrez une invite de commandes et exécutez `dotnet restore` sur le projet.</span><span class="sxs-lookup"><span data-stu-id="13af5-115">To resolve the error, open a command prompt and run `dotnet restore` on the project.</span></span>
* <span data-ttu-id="13af5-116">Une erreur antérieure, telle que NETSDK1045 (la version du kit de développement logiciel (SDK) que vous utilisez ne prend pas en charge le Framework cible du projet), a empêché NuGet de créer le fichier de ressources du projet.</span><span class="sxs-lookup"><span data-stu-id="13af5-116">An earlier error, such as NETSDK1045 (the version of the SDK you're using doesn't support the project's target framework), prevented NuGet from creating the project assets file.</span></span> <span data-ttu-id="13af5-117">Pour résoudre l’erreur NETSDK1004, résolvez l’erreur antérieure, puis exécutez `dotnet restore` sur le projet.</span><span class="sxs-lookup"><span data-stu-id="13af5-117">To resolve the NETSDK1004 error, resolve the earlier error, and then run `dotnet restore` on the project.</span></span>
* <span data-ttu-id="13af5-118">App Center CI crée un projet qui a un assembly externe qui n’est pas dans NuGet.</span><span class="sxs-lookup"><span data-stu-id="13af5-118">App Center CI is building a project that has an external assembly that is not in NuGet.</span></span> <span data-ttu-id="13af5-119">Pour résoudre l’erreur, utilisez un package NuGet pour l’assembly.</span><span class="sxs-lookup"><span data-stu-id="13af5-119">To resolve the error, use a NuGet package for the assembly.</span></span>
