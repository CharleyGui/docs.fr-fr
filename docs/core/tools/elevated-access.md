---
title: Accès de niveau élevé pour les commandes dotnet
description: Découvrez les bonnes pratiques concernant les commandes dotnet qui nécessitent un accès de niveau élevé.
author: wli3
ms.date: 06/26/2019
ms.openlocfilehash: 1cf29012736e5b6d858ca22dc2a9b97e7e8e33ef
ms.sourcegitcommit: f38e527623883b92010cf4760246203073e12898
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/20/2020
ms.locfileid: "77503566"
---
# <a name="elevated-access-for-dotnet-commands"></a><span data-ttu-id="5a40c-103">Accès de niveau élevé pour les commandes dotnet</span><span class="sxs-lookup"><span data-stu-id="5a40c-103">Elevated access for dotnet commands</span></span>

<span data-ttu-id="5a40c-104">Les bonnes pratiques guident les développeurs dans l’écriture de logiciels qui nécessitent des privilèges peu élevés.</span><span class="sxs-lookup"><span data-stu-id="5a40c-104">Software development best practices guide developers to writing software that requires the least amount of privilege.</span></span> <span data-ttu-id="5a40c-105">Toutefois, certains logiciels, comme les outils de supervision des performances, nécessitent des autorisations d’administrateur en raison de règles liées au système d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="5a40c-105">However, some software, like performance monitoring tools, requires admin permission because of operating system rules.</span></span> <span data-ttu-id="5a40c-106">Le guide qui suit décrit les scénarios pris en charge pour l’écriture de tels logiciels avec .NET Core.</span><span class="sxs-lookup"><span data-stu-id="5a40c-106">The following guidance describes supported scenarios for writing such software with .NET Core.</span></span> 

<span data-ttu-id="5a40c-107">Les commandes suivantes peuvent être exécutées avec des privilèges élevés :</span><span class="sxs-lookup"><span data-stu-id="5a40c-107">The following commands can be run elevated:</span></span>

- <span data-ttu-id="5a40c-108">Commandes `dotnet tool`, comme [dotnet tool install](dotnet-tool-install.md).</span><span class="sxs-lookup"><span data-stu-id="5a40c-108">`dotnet tool` commands, such as [dotnet tool install](dotnet-tool-install.md).</span></span>
- `dotnet run --no-build`

<span data-ttu-id="5a40c-109">Il est déconseillé d’exécuter les autres commandes avec des privilèges élevés.</span><span class="sxs-lookup"><span data-stu-id="5a40c-109">We don't recommend running other commands elevated.</span></span> <span data-ttu-id="5a40c-110">Plus précisément, il est déconseillé d’utiliser des privilèges élevés avec les commandes qui utilisent MSBuild, telles que [dotnet restore](dotnet-restore.md), [dotnet build](dotnet-build.md) et [dotnet run](dotnet-run.md).</span><span class="sxs-lookup"><span data-stu-id="5a40c-110">In particular, we don't recommend elevation with commands that use MSBuild, such as [dotnet restore](dotnet-restore.md), [dotnet build](dotnet-build.md), and [dotnet run](dotnet-run.md).</span></span> <span data-ttu-id="5a40c-111">Le problème le plus courant est celui qui est lié à la gestion des autorisations, lorsqu’un utilisateur passe régulièrement d’un compte racine à un compte restreint, après l’émission de commandes dotnet.</span><span class="sxs-lookup"><span data-stu-id="5a40c-111">The primary issue is permission management problems when a user transitions back and forth between root and a restricted account after issuing dotnet commands.</span></span> <span data-ttu-id="5a40c-112">Vous pouvez vous rendre compte, qu’en tant qu’utilisateur restreint, que vous ne pouvez pas accéder au fichier créé par un utilisateur racine.</span><span class="sxs-lookup"><span data-stu-id="5a40c-112">You may find as a restricted user that you don't have access to the file built by a root user.</span></span> <span data-ttu-id="5a40c-113">Il existe des moyens de résoudre ce problème, mais nous n’avons pas besoin de nous y intéresser tout de suite.</span><span class="sxs-lookup"><span data-stu-id="5a40c-113">There are ways to resolve this situation, but they're unnecessary to get into in the first place.</span></span>

<span data-ttu-id="5a40c-114">Vous pouvez exécuter des commandes avec un compte racine, du moment que vous ne passez constamment d’un compte racine à un compte restreint.</span><span class="sxs-lookup"><span data-stu-id="5a40c-114">You can run commands as root as long as you don’t transition back and forth between root and a restricted account.</span></span> <span data-ttu-id="5a40c-115">Par exemple, les conteneurs Docker sont exécutés par défaut avec un compte racine. Ils ont donc cette caractéristique.</span><span class="sxs-lookup"><span data-stu-id="5a40c-115">For example, Docker containers run as root by default, so they have this characteristic.</span></span>

## <a name="global-tool-installation"></a><span data-ttu-id="5a40c-116">Installation de l’outil global</span><span class="sxs-lookup"><span data-stu-id="5a40c-116">Global tool installation</span></span>

<span data-ttu-id="5a40c-117">Les instructions suivantes montrent la méthode recommandée pour installer, exécuter et désinstaller les outils .NET Core dont l’exécution nécessite des autorisations élevées.</span><span class="sxs-lookup"><span data-stu-id="5a40c-117">The following instructions demonstrate the recommended way to install, run, and uninstall .NET Core tools that require elevated permissions to execute.</span></span>

<!-- markdownlint-disable MD025 -->

# <a name="windows"></a>[<span data-ttu-id="5a40c-118">Windows</span><span class="sxs-lookup"><span data-stu-id="5a40c-118">Windows</span></span>](#tab/windows)

### <a name="install-the-global-tool"></a><span data-ttu-id="5a40c-119">Installer l’outil global</span><span class="sxs-lookup"><span data-stu-id="5a40c-119">Install the global tool</span></span>

<span data-ttu-id="5a40c-120">Si le dossier `%ProgramFiles%\dotnet-tools` existe déjà, effectuez les étapes suivantes pour vérifier si le groupe « Utilisateurs » est autorisé à écrire ou à modifier ce répertoire :</span><span class="sxs-lookup"><span data-stu-id="5a40c-120">If the folder `%ProgramFiles%\dotnet-tools` already exists, do the following to check whether the "Users" group has permission to write or modify that directory:</span></span>

- <span data-ttu-id="5a40c-121">Cliquez avec le bouton droit sur le dossier `%ProgramFiles%\dotnet-tools`, puis sélectionnez **Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="5a40c-121">Right-click the `%ProgramFiles%\dotnet-tools` folder and select **Properties**.</span></span> <span data-ttu-id="5a40c-122">La boîte de dialogue **Propriétés communes** s’ouvre.</span><span class="sxs-lookup"><span data-stu-id="5a40c-122">The **Common Properties** dialog box opens.</span></span> 
- <span data-ttu-id="5a40c-123">Sélectionnez l’onglet **sécurité** . Sous **groupes ou noms d’utilisateurs**, vérifiez si le groupe « utilisateurs » a l’autorisation d’écrire ou de modifier le répertoire.</span><span class="sxs-lookup"><span data-stu-id="5a40c-123">Select the **Security** tab. Under **Group or user names**, check whether the “Users” group has permission to write or modify the directory.</span></span> 
- <span data-ttu-id="5a40c-124">Si le groupe « Utilisateurs » peut modifier le répertoire ou y écrire des données, utilisez un nom de répertoire autre que *dotnet-tools* lorsque vous installez les outils.</span><span class="sxs-lookup"><span data-stu-id="5a40c-124">If the "Users" group can write or modify the directory, use a different directory name when installing the tools rather than *dotnet-tools*.</span></span>

<span data-ttu-id="5a40c-125">Pour installer les outils, exécutez la commande suivante dans l’invite de commandes avec élévation de privilèges.</span><span class="sxs-lookup"><span data-stu-id="5a40c-125">To install tools, run the following command in elevated prompt.</span></span> <span data-ttu-id="5a40c-126">Cela va créer le dossier *dotnet-tools* pendant l’installation.</span><span class="sxs-lookup"><span data-stu-id="5a40c-126">It will create the *dotnet-tools* folder during the installation.</span></span>

```dotnetcli
dotnet tool install PACKAGEID --tool-path "%ProgramFiles%\dotnet-tools".
```

### <a name="run-the-global-tool"></a><span data-ttu-id="5a40c-127">Exécuter l’outil global</span><span class="sxs-lookup"><span data-stu-id="5a40c-127">Run the global tool</span></span>

<span data-ttu-id="5a40c-128">**Option 1** Utilisez le chemin complet dans l’invite de commandes avec élévation de privilèges :</span><span class="sxs-lookup"><span data-stu-id="5a40c-128">**Option 1** Use the full path with elevated prompt:</span></span>

```cmd
"%ProgramFiles%\dotnet-tools\TOOLCOMMAND"
```

<span data-ttu-id="5a40c-129">**Option 2** Ajoutez le dossier que vous venez de créer dans `%Path%`.</span><span class="sxs-lookup"><span data-stu-id="5a40c-129">**Option 2** Add the newly created folder to `%Path%`.</span></span> <span data-ttu-id="5a40c-130">Cette opération n’est à exécuter qu’une seule fois.</span><span class="sxs-lookup"><span data-stu-id="5a40c-130">You only need to do this operation once.</span></span>

```cmd
setx Path "%Path%;%ProgramFiles%\dotnet-tools\"
```

<span data-ttu-id="5a40c-131">Puis exécutez avec :</span><span class="sxs-lookup"><span data-stu-id="5a40c-131">And run with:</span></span>

```cmd
TOOLCOMMAND
```

### <a name="uninstall-the-global-tool"></a><span data-ttu-id="5a40c-132">Désinstaller l’outil global</span><span class="sxs-lookup"><span data-stu-id="5a40c-132">Uninstall the global tool</span></span>

<span data-ttu-id="5a40c-133">À l’invite de commandes avec privilèges élevés, tapez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="5a40c-133">In an elevated prompt, type the following command:</span></span>

```dotnetcli
dotnet tool uninstall PACKAGEID --tool-path "%ProgramFiles%\dotnet-tools"
```

# <a name="linux"></a>[<span data-ttu-id="5a40c-134">Linux</span><span class="sxs-lookup"><span data-stu-id="5a40c-134">Linux</span></span>](#tab/linux)

[!INCLUDE [elevated-access-unix](../../../includes/elevated-access-unix.md)]

# <a name="macos"></a>[<span data-ttu-id="5a40c-135">macOS</span><span class="sxs-lookup"><span data-stu-id="5a40c-135">macOS</span></span>](#tab/macos)

[!INCLUDE [elevated-access-unix](../../../includes/elevated-access-unix.md)]

---

## <a name="local-tools"></a><span data-ttu-id="5a40c-136">Outils locaux</span><span class="sxs-lookup"><span data-stu-id="5a40c-136">Local tools</span></span>

<span data-ttu-id="5a40c-137">L’étendue des outils locaux se limite à l’arborescence des sous-répertoires et à l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="5a40c-137">Local tools are scoped per subdirectory tree, per user.</span></span> <span data-ttu-id="5a40c-138">Lorsqu’ils sont exécutés avec des privilèges élevés, les outils locaux partagent un environnement d’utilisateur restreint avec l’environnement à privilèges élevés.</span><span class="sxs-lookup"><span data-stu-id="5a40c-138">When run elevated, local tools share a restricted user environment to the elevated environment.</span></span> <span data-ttu-id="5a40c-139">Sur Linux et macOS, seuls les utilisateurs racines peuvent accéder aux fichiers.</span><span class="sxs-lookup"><span data-stu-id="5a40c-139">In Linux and macOS, this results in files being set with root user-only access.</span></span> <span data-ttu-id="5a40c-140">Si l’utilisateur bascule vers un compte restreint, il ne peut plus accéder aux fichiers ni y écrire des données.</span><span class="sxs-lookup"><span data-stu-id="5a40c-140">If the user switches back to a restricted account, the user can no longer access or write to the files.</span></span> <span data-ttu-id="5a40c-141">Il n’est donc pas recommandé d’installer des outils qui nécessitent des privilèges élevés, comme les outils locaux.</span><span class="sxs-lookup"><span data-stu-id="5a40c-141">So installing tools that require elevation as local tools isn't recommended.</span></span> <span data-ttu-id="5a40c-142">Utilisez plutôt l’option `--tool-path` et les instructions précédentes concernant les outils globaux.</span><span class="sxs-lookup"><span data-stu-id="5a40c-142">Instead, use the `--tool-path` option and the previous guidelines for global tools.</span></span>

## <a name="elevation-during-development"></a><span data-ttu-id="5a40c-143">Élévation des privilèges pendant le développement</span><span class="sxs-lookup"><span data-stu-id="5a40c-143">Elevation during development</span></span>

<span data-ttu-id="5a40c-144">Pendant le développement, vous aurez peut-être besoin de privilèges élevés pour tester votre application.</span><span class="sxs-lookup"><span data-stu-id="5a40c-144">During development, you may need elevated access to test your application.</span></span> <span data-ttu-id="5a40c-145">Ce scénario est courant pour les applications IoT, par exemple.</span><span class="sxs-lookup"><span data-stu-id="5a40c-145">This scenario is common for IoT apps, for example.</span></span> <span data-ttu-id="5a40c-146">Nous recommandons de générer l’application sans privilèges élevés, puis de l’exécuter avec des privilèges élevés.</span><span class="sxs-lookup"><span data-stu-id="5a40c-146">We recommend that you build the application without elevation and then run it with elevation.</span></span> <span data-ttu-id="5a40c-147">Il existe quelques modèles, par exemple :</span><span class="sxs-lookup"><span data-stu-id="5a40c-147">There are a few patterns, as follows:</span></span>

- <span data-ttu-id="5a40c-148">Utilisation d’un fichier exécutable généré (fournit les meilleures performances de démarrage) :</span><span class="sxs-lookup"><span data-stu-id="5a40c-148">Using generated executable (it provides the best startup performance):</span></span>

   ```dotnetcli
   dotnet build
   sudo ./bin/Debug/netcoreapp3.0/APPLICATIONNAME
   ```
    
- <span data-ttu-id="5a40c-149">Utilisation de la commande [dotnet run](dotnet-run.md) avec l’indicateur `—no-build` pour éviter de générer de nouveaux fichiers binaires :</span><span class="sxs-lookup"><span data-stu-id="5a40c-149">Using the [dotnet run](dotnet-run.md) command with the `—no-build` flag to avoid generating new binaries:</span></span>

   ```dotnetcli
   dotnet build
   sudo dotnet run --no-build
   ```

## <a name="see-also"></a><span data-ttu-id="5a40c-150">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5a40c-150">See also</span></span>

- [<span data-ttu-id="5a40c-151">Vue d’ensemble des outils globaux .NET Core</span><span class="sxs-lookup"><span data-stu-id="5a40c-151">.NET Core Global Tools overview</span></span>](global-tools.md)
