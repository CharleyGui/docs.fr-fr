---
title: 'Didacticiel : installer et utiliser les outils locaux .NET Core'
description: Découvrez comment installer et utiliser un outil .NET comme un outil local.
ms.date: 02/12/2020
ms.openlocfilehash: 6de620772cec1e9d1b1f57380b72c0163d68337c
ms.sourcegitcommit: 771c554c84ba38cbd4ac0578324ec4cfc979cf2e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/21/2020
ms.locfileid: "77543865"
---
# <a name="tutorial-install-and-use-a-net-core-local-tool-using-the-net-core-cli"></a><span data-ttu-id="23c19-103">Didacticiel : installer et utiliser un outil local .NET Core à l’aide de l’CLI .NET Core</span><span class="sxs-lookup"><span data-stu-id="23c19-103">Tutorial: Install and use a .NET Core local tool using the .NET Core CLI</span></span>

<span data-ttu-id="23c19-104">**Cet article s’applique à : ✔️ le kit de** développement logiciel (SDK) .net Core 3,0 et versions ultérieures</span><span class="sxs-lookup"><span data-stu-id="23c19-104">**This article applies to:** ✔️ .NET Core 3.0 SDK and later versions</span></span>

<span data-ttu-id="23c19-105">Ce didacticiel vous apprend à installer et à utiliser un outil local.</span><span class="sxs-lookup"><span data-stu-id="23c19-105">This tutorial teaches you how to install and use a local tool.</span></span> <span data-ttu-id="23c19-106">Vous utilisez un outil que vous créez dans le [premier didacticiel de cette série](global-tools-how-to-create.md).</span><span class="sxs-lookup"><span data-stu-id="23c19-106">You use a tool that you create in the [first tutorial of this series](global-tools-how-to-create.md).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="23c19-107">Conditions préalables requises</span><span class="sxs-lookup"><span data-stu-id="23c19-107">Prerequisites</span></span>

* <span data-ttu-id="23c19-108">Effectuez le [premier didacticiel de cette série](global-tools-how-to-create.md).</span><span class="sxs-lookup"><span data-stu-id="23c19-108">Complete the [first tutorial of this series](global-tools-how-to-create.md).</span></span>
* <span data-ttu-id="23c19-109">Installez le Runtime .NET Core 2,1.</span><span class="sxs-lookup"><span data-stu-id="23c19-109">Install the .NET Core 2.1 runtime.</span></span>

  <span data-ttu-id="23c19-110">Pour ce didacticiel, vous installez et utilisez un outil qui cible .NET Core 2,1. vous devez donc installer ce Runtime sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="23c19-110">For this tutorial you install and use a tool that targets .NET Core 2.1, so you need to have that runtime installed on your machine.</span></span> <span data-ttu-id="23c19-111">Pour installer le runtime 2,1, accédez à la [page de téléchargement de .net Core 2,1](https://dotnet.microsoft.com/download/dotnet-core/2.1) et recherchez le lien d’installation du runtime dans la colonne **exécuter des applications-Runtime** .</span><span class="sxs-lookup"><span data-stu-id="23c19-111">To install the 2.1 runtime, go to the [.NET Core 2.1 download page](https://dotnet.microsoft.com/download/dotnet-core/2.1) and find the runtime installation link in the **Run apps - Runtime** column.</span></span>

## <a name="create-a-manifest-file"></a><span data-ttu-id="23c19-112">Créer un fichier manifeste</span><span class="sxs-lookup"><span data-stu-id="23c19-112">Create a manifest file</span></span>

<span data-ttu-id="23c19-113">Pour installer un outil pour un accès local uniquement (pour le répertoire et les sous-répertoires actifs), il doit être ajouté à un fichier manifeste.</span><span class="sxs-lookup"><span data-stu-id="23c19-113">To install a tool for local access only (for the current directory and subdirectories), it has to be added to a manifest file.</span></span> 

<span data-ttu-id="23c19-114">Dans le dossier *botsay-\<nom >* , accédez à un niveau vers le dossier du *référentiel* :</span><span class="sxs-lookup"><span data-stu-id="23c19-114">From the *botsay-\<name>* folder, navigate up one level to the *repository* folder:</span></span>

```console
cd ..
```

<span data-ttu-id="23c19-115">Créez un fichier manifeste en exécutant la commande [dotnet New](dotnet-new.md) :</span><span class="sxs-lookup"><span data-stu-id="23c19-115">Create a manifest file by running the [dotnet new](dotnet-new.md) command:</span></span>

```dotnetcli
dotnet new tool-manifest
```

<span data-ttu-id="23c19-116">La sortie indique que la création du fichier a réussi.</span><span class="sxs-lookup"><span data-stu-id="23c19-116">The output indicates successful creation of the file.</span></span>

```console
The template "Dotnet local tool manifest file" was created successfully.
```

<span data-ttu-id="23c19-117">Le fichier *. config/dotnet-Tools. JSON* ne contient pas encore d’outils :</span><span class="sxs-lookup"><span data-stu-id="23c19-117">The *.config/dotnet-tools.json* file has no tools in it yet:</span></span>

```json
{
  "version": 1,
  "isRoot": true,
  "tools": {}
}
```

<span data-ttu-id="23c19-118">Les outils répertoriés dans un fichier manifeste sont disponibles dans le répertoire et les sous-répertoires actifs.</span><span class="sxs-lookup"><span data-stu-id="23c19-118">The tools listed in a manifest file are available to the current directory and subdirectories.</span></span> <span data-ttu-id="23c19-119">Le répertoire actif est celui qui contient le répertoire *. config* avec le fichier manifeste.</span><span class="sxs-lookup"><span data-stu-id="23c19-119">The current directory is the one that contains the *.config* directory with the manifest file.</span></span>

<span data-ttu-id="23c19-120">Lorsque vous utilisez une commande CLI qui fait référence à un outil local, le kit de développement logiciel (SDK) recherche un fichier manifeste dans le répertoire actif et les répertoires parents.</span><span class="sxs-lookup"><span data-stu-id="23c19-120">When you use a CLI command that refers to a local tool, the SDK searches for a manifest file in the current directory and parent directories.</span></span> <span data-ttu-id="23c19-121">S’il trouve un fichier manifeste, mais que le fichier n’inclut pas l’outil référencé, il continue la recherche dans les répertoires parents.</span><span class="sxs-lookup"><span data-stu-id="23c19-121">If it finds a manifest file, but the file doesn't include the referenced tool, it continues the search up through parent directories.</span></span> <span data-ttu-id="23c19-122">La recherche se termine lorsqu’elle trouve l’outil référencé ou lorsqu’elle trouve un fichier manifeste avec `isRoot` défini sur `true`.</span><span class="sxs-lookup"><span data-stu-id="23c19-122">The search ends when it finds the referenced tool or it finds a manifest file with `isRoot` set to `true`.</span></span>

## <a name="install-botsay-as-a-local-tool"></a><span data-ttu-id="23c19-123">Installer botsay en tant qu’outil local</span><span class="sxs-lookup"><span data-stu-id="23c19-123">Install botsay as a local tool</span></span>

<span data-ttu-id="23c19-124">Installez l’outil à partir du package que vous avez créé dans le premier didacticiel :</span><span class="sxs-lookup"><span data-stu-id="23c19-124">Install the tool from the package that you created in the first tutorial:</span></span>

```dotnetcli
dotnet tool install --add-source ./botsay-<name>/nupkg botsay-<name>
```

<span data-ttu-id="23c19-125">Cette commande ajoute l’outil au fichier manifeste que vous avez créé à l’étape précédente.</span><span class="sxs-lookup"><span data-stu-id="23c19-125">This command adds the tool to the manifest file that you created in the preceding step.</span></span> <span data-ttu-id="23c19-126">La sortie de la commande indique le fichier manifeste dans lequel se trouve l’outil qui vient d’être installé :</span><span class="sxs-lookup"><span data-stu-id="23c19-126">The command output shows which manifest file the newly installed tool is in:</span></span>

 ```console
 You can invoke the tool from this directory using the following command:
 'dotnet tool run botsay' or 'dotnet botsay'
 Tool 'botsay-<name>' (version '1.0.0') was successfully installed.
 Entry is added to the manifest file /home/name/repository/.config/dotnet-tools.json
 ```

<span data-ttu-id="23c19-127">Le fichier *. config/dotnet-Tools. JSON* dispose désormais d’un outil :</span><span class="sxs-lookup"><span data-stu-id="23c19-127">The *.config/dotnet-tools.json* file now has one tool:</span></span>

```json
{
  "version": 1,
  "isRoot": true,
  "tools": {
    "botsay-<name>": {
      "version": "1.0.0",
      "commands": [
        "botsay"
      ]
    }
  }
}
```

## <a name="use-the-tool"></a><span data-ttu-id="23c19-128">Utiliser l’outil</span><span class="sxs-lookup"><span data-stu-id="23c19-128">Use the tool</span></span>

<span data-ttu-id="23c19-129">Appelez l’outil en exécutant la commande `dotnet tool run` à partir du dossier du *référentiel* :</span><span class="sxs-lookup"><span data-stu-id="23c19-129">Invoke the tool by running the `dotnet tool run` command from the *repository* folder:</span></span>

```dotnetcli
dotnet tool run botsay hello from the bot
```

## <a name="restore-a-local-tool-installed-by-others"></a><span data-ttu-id="23c19-130">Restaurer un outil local installé par d’autres</span><span class="sxs-lookup"><span data-stu-id="23c19-130">Restore a local tool installed by others</span></span>

<span data-ttu-id="23c19-131">En général, vous installez un outil local dans le répertoire racine du référentiel.</span><span class="sxs-lookup"><span data-stu-id="23c19-131">You typically install a local tool in the root directory of the repository.</span></span> <span data-ttu-id="23c19-132">Une fois que vous avez vérifié le fichier manifeste dans le référentiel, d’autres développeurs peuvent récupérer le dernier fichier manifeste.</span><span class="sxs-lookup"><span data-stu-id="23c19-132">After you check in the manifest file to the repository, other developers can get the latest manifest file.</span></span> <span data-ttu-id="23c19-133">Pour installer tous les outils listés dans le fichier manifeste, ils peuvent exécuter une seule commande `dotnet tool restore`.</span><span class="sxs-lookup"><span data-stu-id="23c19-133">To install all of the tools listed in the manifest file, they can run a single `dotnet tool restore` command.</span></span>

1. <span data-ttu-id="23c19-134">Ouvrez le fichier *. config/dotnet-Tools. JSON* et remplacez le contenu par le code JSON suivant :</span><span class="sxs-lookup"><span data-stu-id="23c19-134">Open the *.config/dotnet-tools.json* file, and replace the contents with the following JSON:</span></span>

   ```json
   {
     "version": 1,
     "isRoot": true,
     "tools": {
       "botsay-<name>": {
         "version": "1.0.0",
         "commands": [
           "botsay"
         ]
       },
       "dotnetsay": {
         "version": "2.1.3",
         "commands": [
           "dotnetsay"
         ]
       }
     }
   }
   ```

1. <span data-ttu-id="23c19-135">Remplacez `<name>` par le nom que vous avez utilisé pour créer le projet.</span><span class="sxs-lookup"><span data-stu-id="23c19-135">Replace `<name>` with the name you used to create the project.</span></span>

1. <span data-ttu-id="23c19-136">Enregistrez vos modifications.</span><span class="sxs-lookup"><span data-stu-id="23c19-136">Save your changes.</span></span>

   <span data-ttu-id="23c19-137">Cette modification revient à obtenir la version la plus récente à partir du référentiel après que quelqu’un d’autre a installé le package `dotnetsay` pour le répertoire du projet.</span><span class="sxs-lookup"><span data-stu-id="23c19-137">Making this change is the same as getting the latest version from the repository after someone else installed the package `dotnetsay` for the project directory.</span></span> 

1. <span data-ttu-id="23c19-138">Exécutez la commande `dotnet tool restore`.</span><span class="sxs-lookup"><span data-stu-id="23c19-138">Run the `dotnet tool restore` command.</span></span>

   ```dotnetcli
   dotnet tool restore
   ```

   <span data-ttu-id="23c19-139">La commande produit une sortie similaire à l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="23c19-139">The command produces output like the following example:</span></span>

   ```console
   Tool 'botsay-<name>' (version '1.0.0') was restored. Available commands: botsay
   Tool 'dotnetsay' (version '2.1.3') was restored. Available commands: dotnetsay
   Restore was successful.
   ```

1. <span data-ttu-id="23c19-140">Vérifiez que les outils sont disponibles :</span><span class="sxs-lookup"><span data-stu-id="23c19-140">Verify that the tools are available:</span></span>

   ```dotnetcli
   dotnet tool list
   ```

   <span data-ttu-id="23c19-141">La sortie est une liste de packages et de commandes, similaire à l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="23c19-141">The output is a list of packages and commands, similar to the following example:</span></span>

   ```console
   Package Id      Version      Commands       Manifest
   -------------------------------------------------------------------------------------------
   botsay-<name>   1.0.0        botsay         /home/name/repository/.config/dotnet-tools.json
   dotnetsay       2.1.3        dotnetsay      /home/name/repository/.config/dotnet-tools.json
   ```

1. <span data-ttu-id="23c19-142">Testez les outils :</span><span class="sxs-lookup"><span data-stu-id="23c19-142">Test the tools:</span></span>

   ```dotnetcli
   dotnet tool run dotnetsay hello from dotnetsay
   dotnet tool run botsay hello from botsay
   ```

## <a name="update-a-local-tool"></a><span data-ttu-id="23c19-143">Mettre à jour un outil local</span><span class="sxs-lookup"><span data-stu-id="23c19-143">Update a local tool</span></span>

<span data-ttu-id="23c19-144">La version installée de l’outil local `dotnetsay` est 2.1.3.</span><span class="sxs-lookup"><span data-stu-id="23c19-144">The installed version of local tool `dotnetsay` is 2.1.3.</span></span>  <span data-ttu-id="23c19-145">La version la plus récente est 2.1.4.</span><span class="sxs-lookup"><span data-stu-id="23c19-145">The latest version is 2.1.4.</span></span> <span data-ttu-id="23c19-146">Utilisez la commande de [mise à jour de l’outil dotnet](dotnet-tool-update.md) pour mettre à jour l’outil avec la dernière version.</span><span class="sxs-lookup"><span data-stu-id="23c19-146">Use the [dotnet tool update](dotnet-tool-update.md) command to update the tool to the latest version.</span></span>

```dotnetcli
dotnet tool update dotnetsay
```

<span data-ttu-id="23c19-147">La sortie indique le nouveau numéro de version :</span><span class="sxs-lookup"><span data-stu-id="23c19-147">The output indicates the new version number:</span></span>

```console
Tool 'dotnetsay' was successfully updated from version '2.1.3' to version '2.1.4'
(manifest file /home/name/repository/.config/dotnet-tools.json).
```

<span data-ttu-id="23c19-148">La commande Update recherche le premier fichier manifeste qui contient l’ID de package et le met à jour.</span><span class="sxs-lookup"><span data-stu-id="23c19-148">The update command finds the first manifest file that contains the package ID and updates it.</span></span> <span data-ttu-id="23c19-149">S’il n’existe aucun ID de package de ce type dans un fichier manifeste qui se trouve dans l’étendue de la recherche, le kit de développement logiciel (SDK) ajoute une nouvelle entrée au fichier manifeste le plus proche.</span><span class="sxs-lookup"><span data-stu-id="23c19-149">If there is no such package ID in any manifest file that is in the scope of the search, the SDK adds a new entry to the closest manifest file.</span></span> <span data-ttu-id="23c19-150">L’étendue de recherche se trouve dans les répertoires parents jusqu’à ce qu’un fichier manifeste avec `isRoot = true` soit trouvé.</span><span class="sxs-lookup"><span data-stu-id="23c19-150">The search scope is up through parent directories until a manifest file with `isRoot = true` is found.</span></span>

## <a name="remove-local-tools"></a><span data-ttu-id="23c19-151">Supprimer les outils locaux</span><span class="sxs-lookup"><span data-stu-id="23c19-151">Remove local tools</span></span>

<span data-ttu-id="23c19-152">Supprimez les outils installés en exécutant la commande de [désinstallation de l’outil dotnet](dotnet-tool-uninstall.md) :</span><span class="sxs-lookup"><span data-stu-id="23c19-152">Remove the installed tools by running the [dotnet tool uninstall](dotnet-tool-uninstall.md) command:</span></span>

```dotnetcli
dotnet tool uninstall botsay-<name>
```

```dotnetcli
dotnet tool uninstall dotnetsay
```

## <a name="troubleshoot"></a><span data-ttu-id="23c19-153">Dépanner</span><span class="sxs-lookup"><span data-stu-id="23c19-153">Troubleshoot</span></span>

<span data-ttu-id="23c19-154">Si vous obtenez un message d’erreur lors de la suite du didacticiel, consultez [résoudre les problèmes d’utilisation de l’outil .net Core](troubleshoot-usage-issues.md).</span><span class="sxs-lookup"><span data-stu-id="23c19-154">If you get an error message while following the tutorial, see [Troubleshoot .NET Core tool usage issues](troubleshoot-usage-issues.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="23c19-155">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="23c19-155">See also</span></span>

<span data-ttu-id="23c19-156">Pour plus d’informations, consultez [outils .net Core](global-tools.md)</span><span class="sxs-lookup"><span data-stu-id="23c19-156">For more information, see [.NET Core tools](global-tools.md)</span></span>
