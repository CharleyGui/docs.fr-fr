---
title: 'Tutorial: Installer et utiliser .NET Core outils locaux'
description: Apprenez à installer et à utiliser un outil .NET comme outil local.
ms.date: 02/12/2020
ms.openlocfilehash: a4355886513040e2436bdbd87905e5baee2dd7a5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "78156697"
---
# <a name="tutorial-install-and-use-a-net-core-local-tool-using-the-net-core-cli"></a><span data-ttu-id="8cfa4-103">Tutorial: Installer et utiliser un outil local .NET Core en utilisant le CLI .NET Core</span><span class="sxs-lookup"><span data-stu-id="8cfa4-103">Tutorial: Install and use a .NET Core local tool using the .NET Core CLI</span></span>

<span data-ttu-id="8cfa4-104">**Cet article s’applique à:** ✔️ .NET Core 3.0 SDK et les versions ultérieures</span><span class="sxs-lookup"><span data-stu-id="8cfa4-104">**This article applies to:** ✔️ .NET Core 3.0 SDK and later versions</span></span>

<span data-ttu-id="8cfa4-105">Ce tutoriel vous apprend à installer et à utiliser un outil local.</span><span class="sxs-lookup"><span data-stu-id="8cfa4-105">This tutorial teaches you how to install and use a local tool.</span></span> <span data-ttu-id="8cfa4-106">Vous utilisez un outil que vous créez dans le [premier tutoriel de cette série](global-tools-how-to-create.md).</span><span class="sxs-lookup"><span data-stu-id="8cfa4-106">You use a tool that you create in the [first tutorial of this series](global-tools-how-to-create.md).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="8cfa4-107">Conditions préalables requises</span><span class="sxs-lookup"><span data-stu-id="8cfa4-107">Prerequisites</span></span>

* <span data-ttu-id="8cfa4-108">Compléter le [premier tutoriel de cette série](global-tools-how-to-create.md).</span><span class="sxs-lookup"><span data-stu-id="8cfa4-108">Complete the [first tutorial of this series](global-tools-how-to-create.md).</span></span>
* <span data-ttu-id="8cfa4-109">Installez le temps d’exécution .NET Core 2.1.</span><span class="sxs-lookup"><span data-stu-id="8cfa4-109">Install the .NET Core 2.1 runtime.</span></span>

  <span data-ttu-id="8cfa4-110">Pour ce tutoriel, vous installez et utilisez un outil qui cible .NET Core 2.1, de sorte que vous devez avoir ce temps d’exécution installé sur votre machine.</span><span class="sxs-lookup"><span data-stu-id="8cfa4-110">For this tutorial you install and use a tool that targets .NET Core 2.1, so you need to have that runtime installed on your machine.</span></span> <span data-ttu-id="8cfa4-111">Pour installer l’heure d’exécution 2.1, rendez-vous sur la [page de téléchargement .NET Core 2.1](https://dotnet.microsoft.com/download/dotnet-core/2.1) et trouvez le lien d’installation runtime dans la colonne **Run apps - Runtime.**</span><span class="sxs-lookup"><span data-stu-id="8cfa4-111">To install the 2.1 runtime, go to the [.NET Core 2.1 download page](https://dotnet.microsoft.com/download/dotnet-core/2.1) and find the runtime installation link in the **Run apps - Runtime** column.</span></span>

## <a name="create-a-manifest-file"></a><span data-ttu-id="8cfa4-112">Créer un fichier manifeste</span><span class="sxs-lookup"><span data-stu-id="8cfa4-112">Create a manifest file</span></span>

<span data-ttu-id="8cfa4-113">Pour installer un outil d’accès local uniquement (pour l’annuaire actuel et les sous-directeurs), il doit être ajouté à un fichier manifeste.</span><span class="sxs-lookup"><span data-stu-id="8cfa4-113">To install a tool for local access only (for the current directory and subdirectories), it has to be added to a manifest file.</span></span>

<span data-ttu-id="8cfa4-114">Du dossier *microsoft.botsay,* naviguez jusqu’à un niveau au dossier *de dépôt* :</span><span class="sxs-lookup"><span data-stu-id="8cfa4-114">From the *microsoft.botsay* folder, navigate up one level to the *repository* folder:</span></span>

```console
cd ..
```

<span data-ttu-id="8cfa4-115">Créez un fichier manifeste en exécutant la nouvelle commande [dotnet](dotnet-new.md) :</span><span class="sxs-lookup"><span data-stu-id="8cfa4-115">Create a manifest file by running the [dotnet new](dotnet-new.md) command:</span></span>

```dotnetcli
dotnet new tool-manifest
```

<span data-ttu-id="8cfa4-116">La sortie indique la création réussie du fichier.</span><span class="sxs-lookup"><span data-stu-id="8cfa4-116">The output indicates successful creation of the file.</span></span>

```console
The template "Dotnet local tool manifest file" was created successfully.
```

<span data-ttu-id="8cfa4-117">Le fichier *.config/dotnet-tools.json* n’a pas encore d’outils :</span><span class="sxs-lookup"><span data-stu-id="8cfa4-117">The *.config/dotnet-tools.json* file has no tools in it yet:</span></span>

```json
{
  "version": 1,
  "isRoot": true,
  "tools": {}
}
```

<span data-ttu-id="8cfa4-118">Les outils énumérés dans un fichier manifeste sont mis à la disposition de l’annuaire et des sous-directeurs actuels.</span><span class="sxs-lookup"><span data-stu-id="8cfa4-118">The tools listed in a manifest file are available to the current directory and subdirectories.</span></span> <span data-ttu-id="8cfa4-119">L’annuaire actuel est celui qui contient le répertoire *.config* avec le fichier manifeste.</span><span class="sxs-lookup"><span data-stu-id="8cfa4-119">The current directory is the one that contains the *.config* directory with the manifest file.</span></span>

<span data-ttu-id="8cfa4-120">Lorsque vous utilisez une commande CLI qui fait référence à un outil local, le SDK recherche un fichier manifeste dans l’annuaire actuel et les répertoires parent.</span><span class="sxs-lookup"><span data-stu-id="8cfa4-120">When you use a CLI command that refers to a local tool, the SDK searches for a manifest file in the current directory and parent directories.</span></span> <span data-ttu-id="8cfa4-121">S’il trouve un fichier manifeste, mais que le fichier n’inclut pas l’outil référencé, il poursuit la recherche à travers les répertoires parentaux.</span><span class="sxs-lookup"><span data-stu-id="8cfa4-121">If it finds a manifest file, but the file doesn't include the referenced tool, it continues the search up through parent directories.</span></span> <span data-ttu-id="8cfa4-122">La recherche se termine lorsqu’elle trouve l’outil `isRoot` référencé ou qu’elle trouve un fichier manifeste avec l’ensemble `true`de .</span><span class="sxs-lookup"><span data-stu-id="8cfa4-122">The search ends when it finds the referenced tool or it finds a manifest file with `isRoot` set to `true`.</span></span>

## <a name="install-botsay-as-a-local-tool"></a><span data-ttu-id="8cfa4-123">Installer botsay comme un outil local</span><span class="sxs-lookup"><span data-stu-id="8cfa4-123">Install botsay as a local tool</span></span>

<span data-ttu-id="8cfa4-124">Installez l’outil à partir du paquet que vous avez créé dans le premier tutoriel:</span><span class="sxs-lookup"><span data-stu-id="8cfa4-124">Install the tool from the package that you created in the first tutorial:</span></span>

```dotnetcli
dotnet tool install --add-source ./microsoft.botsay/nupkg microsoft.botsay
```

<span data-ttu-id="8cfa4-125">Cette commande ajoute l’outil au fichier manifeste que vous avez créé dans l’étape précédente.</span><span class="sxs-lookup"><span data-stu-id="8cfa4-125">This command adds the tool to the manifest file that you created in the preceding step.</span></span> <span data-ttu-id="8cfa4-126">La sortie de commande indique dans quel fichier manifeste l’outil nouvellement installé est :</span><span class="sxs-lookup"><span data-stu-id="8cfa4-126">The command output shows which manifest file the newly installed tool is in:</span></span>

 ```console
 You can invoke the tool from this directory using the following command:
 'dotnet tool run botsay' or 'dotnet botsay'
 Tool 'microsoft.botsay' (version '1.0.0') was successfully installed.
 Entry is added to the manifest file /home/name/repository/.config/dotnet-tools.json
 ```

<span data-ttu-id="8cfa4-127">Le fichier *.config/dotnet-tools.json* dispose désormais d’un outil :</span><span class="sxs-lookup"><span data-stu-id="8cfa4-127">The *.config/dotnet-tools.json* file now has one tool:</span></span>

```json
{
  "version": 1,
  "isRoot": true,
  "tools": {
    "microsoft.botsay": {
      "version": "1.0.0",
      "commands": [
        "botsay"
      ]
    }
  }
}
```

## <a name="use-the-tool"></a><span data-ttu-id="8cfa4-128">Utiliser l’outil</span><span class="sxs-lookup"><span data-stu-id="8cfa4-128">Use the tool</span></span>

<span data-ttu-id="8cfa4-129">Invoquez l’outil en exécutant la `dotnet tool run` commande à partir du dossier de *dépôt* :</span><span class="sxs-lookup"><span data-stu-id="8cfa4-129">Invoke the tool by running the `dotnet tool run` command from the *repository* folder:</span></span>

```dotnetcli
dotnet tool run botsay hello from the bot
```

## <a name="restore-a-local-tool-installed-by-others"></a><span data-ttu-id="8cfa4-130">Restaurer un outil local installé par d’autres</span><span class="sxs-lookup"><span data-stu-id="8cfa4-130">Restore a local tool installed by others</span></span>

<span data-ttu-id="8cfa4-131">Vous installez généralement un outil local dans le répertoire racine du référentiel.</span><span class="sxs-lookup"><span data-stu-id="8cfa4-131">You typically install a local tool in the root directory of the repository.</span></span> <span data-ttu-id="8cfa4-132">Après avoir vérifié le fichier manifeste au référentiel, d’autres développeurs peuvent obtenir le dernier fichier manifeste.</span><span class="sxs-lookup"><span data-stu-id="8cfa4-132">After you check in the manifest file to the repository, other developers can get the latest manifest file.</span></span> <span data-ttu-id="8cfa4-133">Pour installer tous les outils énumérés dans le `dotnet tool restore` fichier manifeste, ils peuvent exécuter une seule commande.</span><span class="sxs-lookup"><span data-stu-id="8cfa4-133">To install all of the tools listed in the manifest file, they can run a single `dotnet tool restore` command.</span></span>

1. <span data-ttu-id="8cfa4-134">Ouvrez le fichier *.config/dotnet-tools.json,* et remplacez le contenu par le JSON suivant :</span><span class="sxs-lookup"><span data-stu-id="8cfa4-134">Open the *.config/dotnet-tools.json* file, and replace the contents with the following JSON:</span></span>

   ```json
   {
     "version": 1,
     "isRoot": true,
     "tools": {
       "microsoft.botsay": {
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

1. <span data-ttu-id="8cfa4-135">Remplacez-vous `<name>` par le nom que vous avez utilisé pour créer le projet.</span><span class="sxs-lookup"><span data-stu-id="8cfa4-135">Replace `<name>` with the name you used to create the project.</span></span>

1. <span data-ttu-id="8cfa4-136">Enregistrez vos modifications.</span><span class="sxs-lookup"><span data-stu-id="8cfa4-136">Save your changes.</span></span>

   <span data-ttu-id="8cfa4-137">Faire ce changement est la même chose que d’obtenir la `dotnetsay` dernière version du référentiel après que quelqu’un d’autre a installé le paquet pour l’annuaire du projet.</span><span class="sxs-lookup"><span data-stu-id="8cfa4-137">Making this change is the same as getting the latest version from the repository after someone else installed the package `dotnetsay` for the project directory.</span></span>

1. <span data-ttu-id="8cfa4-138">Exécutez la commande `dotnet tool restore`.</span><span class="sxs-lookup"><span data-stu-id="8cfa4-138">Run the `dotnet tool restore` command.</span></span>

   ```dotnetcli
   dotnet tool restore
   ```

   <span data-ttu-id="8cfa4-139">La commande produit la sortie comme l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="8cfa4-139">The command produces output like the following example:</span></span>

   ```console
   Tool 'microsoft.botsay' (version '1.0.0') was restored. Available commands: botsay
   Tool 'dotnetsay' (version '2.1.3') was restored. Available commands: dotnetsay
   Restore was successful.
   ```

1. <span data-ttu-id="8cfa4-140">Vérifiez que les outils sont disponibles :</span><span class="sxs-lookup"><span data-stu-id="8cfa4-140">Verify that the tools are available:</span></span>

   ```dotnetcli
   dotnet tool list
   ```

   <span data-ttu-id="8cfa4-141">La sortie est une liste de paquets et de commandes, similaire à l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="8cfa4-141">The output is a list of packages and commands, similar to the following example:</span></span>

   ```console
   Package Id      Version      Commands       Manifest
   --------------------------------------------------------------------------------------------
   microsoft.botsay 1.0.0        botsay         /home/name/repository/.config/dotnet-tools.json
   dotnetsay        2.1.3        dotnetsay      /home/name/repository/.config/dotnet-tools.json
   ```

1. <span data-ttu-id="8cfa4-142">Testez les outils :</span><span class="sxs-lookup"><span data-stu-id="8cfa4-142">Test the tools:</span></span>

   ```dotnetcli
   dotnet tool run dotnetsay hello from dotnetsay
   dotnet tool run botsay hello from botsay
   ```

## <a name="update-a-local-tool"></a><span data-ttu-id="8cfa4-143">Mettre à jour un outil local</span><span class="sxs-lookup"><span data-stu-id="8cfa4-143">Update a local tool</span></span>

<span data-ttu-id="8cfa4-144">La version installée `dotnetsay` de l’outil local est 2.1.3.</span><span class="sxs-lookup"><span data-stu-id="8cfa4-144">The installed version of local tool `dotnetsay` is 2.1.3.</span></span>  <span data-ttu-id="8cfa4-145">La dernière version est 2.1.4.</span><span class="sxs-lookup"><span data-stu-id="8cfa4-145">The latest version is 2.1.4.</span></span> <span data-ttu-id="8cfa4-146">Utilisez la commande [de mise à jour de l’outil dotnet](dotnet-tool-update.md) pour mettre à jour l’outil de la dernière version.</span><span class="sxs-lookup"><span data-stu-id="8cfa4-146">Use the [dotnet tool update](dotnet-tool-update.md) command to update the tool to the latest version.</span></span>

```dotnetcli
dotnet tool update dotnetsay
```

<span data-ttu-id="8cfa4-147">La sortie indique le nouveau numéro de version :</span><span class="sxs-lookup"><span data-stu-id="8cfa4-147">The output indicates the new version number:</span></span>

```console
Tool 'dotnetsay' was successfully updated from version '2.1.3' to version '2.1.4'
(manifest file /home/name/repository/.config/dotnet-tools.json).
```

<span data-ttu-id="8cfa4-148">La commande de mise à jour trouve le premier fichier manifeste qui contient l’ID du paquet et le met à jour.</span><span class="sxs-lookup"><span data-stu-id="8cfa4-148">The update command finds the first manifest file that contains the package ID and updates it.</span></span> <span data-ttu-id="8cfa4-149">S’il n’y a pas d’id de paquet dans un fichier manifeste qui est dans la portée de la recherche, le SDK ajoute une nouvelle entrée au fichier manifeste le plus proche.</span><span class="sxs-lookup"><span data-stu-id="8cfa4-149">If there is no such package ID in any manifest file that is in the scope of the search, the SDK adds a new entry to the closest manifest file.</span></span> <span data-ttu-id="8cfa4-150">La portée de recherche est en place `isRoot = true` à travers les répertoires des parents jusqu’à ce qu’un fichier manifeste avec est trouvé.</span><span class="sxs-lookup"><span data-stu-id="8cfa4-150">The search scope is up through parent directories until a manifest file with `isRoot = true` is found.</span></span>

## <a name="remove-local-tools"></a><span data-ttu-id="8cfa4-151">Supprimer les outils locaux</span><span class="sxs-lookup"><span data-stu-id="8cfa4-151">Remove local tools</span></span>

<span data-ttu-id="8cfa4-152">Retirez les outils installés en exécutant [l’outil dotnet désinstaller la](dotnet-tool-uninstall.md) commande :</span><span class="sxs-lookup"><span data-stu-id="8cfa4-152">Remove the installed tools by running the [dotnet tool uninstall](dotnet-tool-uninstall.md) command:</span></span>

```dotnetcli
dotnet tool uninstall microsoft.botsay
```

```dotnetcli
dotnet tool uninstall dotnetsay
```

## <a name="troubleshoot"></a><span data-ttu-id="8cfa4-153">Dépanner</span><span class="sxs-lookup"><span data-stu-id="8cfa4-153">Troubleshoot</span></span>

<span data-ttu-id="8cfa4-154">Si vous obtenez un message d’erreur tout en suivant le tutoriel, voir [Troubleshoot .NET Core problèmes d’utilisation de l’outil](troubleshoot-usage-issues.md).</span><span class="sxs-lookup"><span data-stu-id="8cfa4-154">If you get an error message while following the tutorial, see [Troubleshoot .NET Core tool usage issues](troubleshoot-usage-issues.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="8cfa4-155">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8cfa4-155">See also</span></span>

<span data-ttu-id="8cfa4-156">Pour plus d’informations, voir [outils .NET Core](global-tools.md)</span><span class="sxs-lookup"><span data-stu-id="8cfa4-156">For more information, see [.NET Core tools](global-tools.md)</span></span>
