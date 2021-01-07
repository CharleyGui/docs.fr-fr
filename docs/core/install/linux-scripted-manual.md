---
title: Installer manuellement .NET sur Linux-.NET
description: Montre comment installer le kit de développement logiciel (SDK) .NET et le Runtime .NET sans le gestionnaire de package sur Linux. Utilisez le script d’installation ou extrayez manuellement les fichiers binaires.
author: adegeo
ms.author: adegeo
ms.date: 01/06/2021
ms.openlocfilehash: 5879d4d66aba8bfa00caadbe3c33d6df0d7da59a
ms.sourcegitcommit: 7ef96827b161ef3fcde75f79d839885632e26ef1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/07/2021
ms.locfileid: "97970966"
---
# <a name="install-the-net-sdk-or-the-net-runtime-manually"></a><span data-ttu-id="7d15d-104">Installer manuellement le kit de développement logiciel (SDK) .NET ou le Runtime .NET</span><span class="sxs-lookup"><span data-stu-id="7d15d-104">Install the .NET SDK or the .NET Runtime manually</span></span>

<span data-ttu-id="7d15d-105">.NET est pris en charge sur Linux et cet article explique comment installer .NET sur Linux à l’aide du script d’installation ou en extrayant les fichiers binaires.</span><span class="sxs-lookup"><span data-stu-id="7d15d-105">.NET is supported on Linux and this article describes how to install .NET on Linux using the install script or by extracting the binaries.</span></span> <span data-ttu-id="7d15d-106">Pour obtenir la liste des distributions qui prennent en charge le gestionnaire de package intégré, consultez [installer .net sur Linux](linux.md).</span><span class="sxs-lookup"><span data-stu-id="7d15d-106">For a list of distributions that support the built-in package manager, see [Install .NET on Linux](linux.md).</span></span>

<span data-ttu-id="7d15d-107">Vous pouvez également installer .NET avec le composant logiciel enfichable.</span><span class="sxs-lookup"><span data-stu-id="7d15d-107">You can also install .NET with snap.</span></span> <span data-ttu-id="7d15d-108">Pour plus d’informations, consultez [installer le kit de développement logiciel (SDK) .net ou le Runtime .net avec le composant logiciel enfichable](linux-snap.md).</span><span class="sxs-lookup"><span data-stu-id="7d15d-108">For more information, see [Install the .NET SDK or the .NET Runtime with Snap](linux-snap.md).</span></span>

[!INCLUDE [linux-intro-sdk-vs-runtime](includes/linux-intro-sdk-vs-runtime.md)]

## <a name="net-releases"></a><span data-ttu-id="7d15d-109">Versions de .NET</span><span class="sxs-lookup"><span data-stu-id="7d15d-109">.NET releases</span></span>

<span data-ttu-id="7d15d-110">Le tableau suivant répertorie les versions de .NET (et .NET Core) :</span><span class="sxs-lookup"><span data-stu-id="7d15d-110">The following table lists the .NET (and .NET Core) releases:</span></span>

| <span data-ttu-id="7d15d-111">✔️ pris en charge</span><span class="sxs-lookup"><span data-stu-id="7d15d-111">✔️ Supported</span></span> | <span data-ttu-id="7d15d-112">❌ Pris en charge</span><span class="sxs-lookup"><span data-stu-id="7d15d-112">❌ Unsupported</span></span> |
|-------------|---------------|
| <span data-ttu-id="7d15d-113">5.0</span><span class="sxs-lookup"><span data-stu-id="7d15d-113">5.0</span></span>         | <span data-ttu-id="7d15d-114">3.0</span><span class="sxs-lookup"><span data-stu-id="7d15d-114">3.0</span></span>           |
| <span data-ttu-id="7d15d-115">3,1 (LTS)</span><span class="sxs-lookup"><span data-stu-id="7d15d-115">3.1 (LTS)</span></span>   | <span data-ttu-id="7d15d-116">2.2</span><span class="sxs-lookup"><span data-stu-id="7d15d-116">2.2</span></span>           |
| <span data-ttu-id="7d15d-117">2,1 (LTS)</span><span class="sxs-lookup"><span data-stu-id="7d15d-117">2.1 (LTS)</span></span>   | <span data-ttu-id="7d15d-118">2,0</span><span class="sxs-lookup"><span data-stu-id="7d15d-118">2.0</span></span>           |
|             | <span data-ttu-id="7d15d-119">1,1</span><span class="sxs-lookup"><span data-stu-id="7d15d-119">1.1</span></span>           |
|             | <span data-ttu-id="7d15d-120">1.0</span><span class="sxs-lookup"><span data-stu-id="7d15d-120">1.0</span></span>           |

<span data-ttu-id="7d15d-121">Pour plus d’informations sur le cycle de vie des versions de .NET, consultez [stratégie de support .net Core et .net 5](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).</span><span class="sxs-lookup"><span data-stu-id="7d15d-121">For more information about the life cycle of .NET releases, see [.NET Core and .NET 5 Support Policy](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).</span></span>

## <a name="dependencies"></a><span data-ttu-id="7d15d-122">Dépendances</span><span class="sxs-lookup"><span data-stu-id="7d15d-122">Dependencies</span></span>

<span data-ttu-id="7d15d-123">Lorsque vous installez .NET, il est possible que des dépendances spécifiques ne soient pas installées, par exemple lors de [l’installation manuelle](#manual-install).</span><span class="sxs-lookup"><span data-stu-id="7d15d-123">It's possible that when you install .NET, specific dependencies may not be installed, such as when [manually installing](#manual-install).</span></span> <span data-ttu-id="7d15d-124">La liste suivante répertorie les distributions Linux prises en charge par Microsoft et qui présentent des dépendances que vous devrez peut-être installer.</span><span class="sxs-lookup"><span data-stu-id="7d15d-124">The following list details Linux distributions that are supported by Microsoft and have dependencies you may need to install.</span></span> <span data-ttu-id="7d15d-125">Consultez la page distribution pour plus d’informations :</span><span class="sxs-lookup"><span data-stu-id="7d15d-125">Check the distribution page for more information:</span></span>

- [<span data-ttu-id="7d15d-126">Alpine</span><span class="sxs-lookup"><span data-stu-id="7d15d-126">Alpine</span></span>](linux-alpine.md#dependencies)
- [<span data-ttu-id="7d15d-127">Debian</span><span class="sxs-lookup"><span data-stu-id="7d15d-127">Debian</span></span>](linux-debian.md#dependencies)
- [<span data-ttu-id="7d15d-128">CentOS</span><span class="sxs-lookup"><span data-stu-id="7d15d-128">CentOS</span></span>](linux-centos.md#dependencies)
- [<span data-ttu-id="7d15d-129">Fedora</span><span class="sxs-lookup"><span data-stu-id="7d15d-129">Fedora</span></span>](linux-fedora.md#dependencies)
- [<span data-ttu-id="7d15d-130">RHEL</span><span class="sxs-lookup"><span data-stu-id="7d15d-130">RHEL</span></span>](linux-rhel.md#dependencies)
- [<span data-ttu-id="7d15d-131">SLES</span><span class="sxs-lookup"><span data-stu-id="7d15d-131">SLES</span></span>](linux-sles.md#dependencies)
- [<span data-ttu-id="7d15d-132">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="7d15d-132">Ubuntu</span></span>](linux-ubuntu.md#dependencies)

<span data-ttu-id="7d15d-133">Pour obtenir des informations générales sur les dépendances, consultez [applications Linux autonomes](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md).</span><span class="sxs-lookup"><span data-stu-id="7d15d-133">For generic information about the dependencies, see [Self-contained Linux apps](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md).</span></span>

### <a name="rpm-dependencies"></a><span data-ttu-id="7d15d-134">Dépendances RPM</span><span class="sxs-lookup"><span data-stu-id="7d15d-134">RPM dependencies</span></span>

<span data-ttu-id="7d15d-135">Si votre distribution n’a pas été précédemment listée et est basée sur RPM, vous pouvez avoir besoin des dépendances suivantes :</span><span class="sxs-lookup"><span data-stu-id="7d15d-135">If your distribution wasn't previously listed, and is RPM-based, you may need the following dependencies:</span></span>

- <span data-ttu-id="7d15d-136">krb5-libs</span><span class="sxs-lookup"><span data-stu-id="7d15d-136">krb5-libs</span></span>
- <span data-ttu-id="7d15d-137">libicu</span><span class="sxs-lookup"><span data-stu-id="7d15d-137">libicu</span></span>
- <span data-ttu-id="7d15d-138">openssl-libs</span><span class="sxs-lookup"><span data-stu-id="7d15d-138">openssl-libs</span></span>

<span data-ttu-id="7d15d-139">Si la version OpenSSL de l’environnement d’exécution cible est 1,1 ou une version plus récente, vous devez installer **compat-openssl10**.</span><span class="sxs-lookup"><span data-stu-id="7d15d-139">If the target runtime environment's OpenSSL version is 1.1 or newer, you'll need to install **compat-openssl10**.</span></span>

### <a name="deb-dependencies"></a><span data-ttu-id="7d15d-140">Dépendances DEB</span><span class="sxs-lookup"><span data-stu-id="7d15d-140">DEB dependencies</span></span>

<span data-ttu-id="7d15d-141">Si votre distribution n’a pas été précédemment listée et est basée sur Debian, vous pouvez avoir besoin des dépendances suivantes :</span><span class="sxs-lookup"><span data-stu-id="7d15d-141">If your distribution wasn't previously listed, and is debian-based, you may need the following dependencies:</span></span>

- <span data-ttu-id="7d15d-142">libc6</span><span class="sxs-lookup"><span data-stu-id="7d15d-142">libc6</span></span>
- <span data-ttu-id="7d15d-143">libgcc1</span><span class="sxs-lookup"><span data-stu-id="7d15d-143">libgcc1</span></span>
- <span data-ttu-id="7d15d-144">libgssapi-krb5-2</span><span class="sxs-lookup"><span data-stu-id="7d15d-144">libgssapi-krb5-2</span></span>
- <span data-ttu-id="7d15d-145">libicu67</span><span class="sxs-lookup"><span data-stu-id="7d15d-145">libicu67</span></span>
- <span data-ttu-id="7d15d-146">libssl 1.1</span><span class="sxs-lookup"><span data-stu-id="7d15d-146">libssl1.1</span></span>
- <span data-ttu-id="7d15d-147">libstdc + + 6</span><span class="sxs-lookup"><span data-stu-id="7d15d-147">libstdc++6</span></span>
- <span data-ttu-id="7d15d-148">zlib1g</span><span class="sxs-lookup"><span data-stu-id="7d15d-148">zlib1g</span></span>

### <a name="common-dependencies"></a><span data-ttu-id="7d15d-149">Dépendances courantes</span><span class="sxs-lookup"><span data-stu-id="7d15d-149">Common dependencies</span></span>

<span data-ttu-id="7d15d-150">Pour les applications .NET qui utilisent l’assembly *System. Drawing. Common* , vous avez également besoin de la dépendance suivante :</span><span class="sxs-lookup"><span data-stu-id="7d15d-150">For .NET apps that use the *System.Drawing.Common* assembly, you'll also need the following dependency:</span></span>

- [<span data-ttu-id="7d15d-151">libgdiplus (version 6.0.1 ou ultérieure)</span><span class="sxs-lookup"><span data-stu-id="7d15d-151">libgdiplus (version 6.0.1 or later)</span></span>](https://www.mono-project.com/docs/gui/libgdiplus/)

  > [!WARNING]
  > <span data-ttu-id="7d15d-152">Vous pouvez installer une version récente de *libgdiplus* en ajoutant le référentiel mono à votre système.</span><span class="sxs-lookup"><span data-stu-id="7d15d-152">You can install a recent version of *libgdiplus* by adding the Mono repository to your system.</span></span> <span data-ttu-id="7d15d-153">Pour plus d'informations, consultez <https://www.mono-project.com/download/stable/>.</span><span class="sxs-lookup"><span data-stu-id="7d15d-153">For more information, see <https://www.mono-project.com/download/stable/>.</span></span>

## <a name="scripted-install"></a><span data-ttu-id="7d15d-154">Installation par script</span><span class="sxs-lookup"><span data-stu-id="7d15d-154">Scripted install</span></span>

<span data-ttu-id="7d15d-155">Les [scripts dotnet-install](../tools/dotnet-install-script.md) sont utilisés pour l’automatisation et les installations non administratives du **Kit de développement logiciel (SDK)** et du **Runtime**.</span><span class="sxs-lookup"><span data-stu-id="7d15d-155">The [dotnet-install scripts](../tools/dotnet-install-script.md) are used for automation and non-admin installs of the **SDK** and **Runtime**.</span></span> <span data-ttu-id="7d15d-156">Vous pouvez télécharger le script depuis <https://dot.net/v1/dotnet-install.sh>.</span><span class="sxs-lookup"><span data-stu-id="7d15d-156">You can download the script from <https://dot.net/v1/dotnet-install.sh>.</span></span>

<span data-ttu-id="7d15d-157">Par défaut, le script installe la version la plus récente du kit de développement logiciel [(SDK) LTS](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) , qui est .net Core 3,1.</span><span class="sxs-lookup"><span data-stu-id="7d15d-157">The script defaults to installing the latest SDK [long term support (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) version, which is .NET Core 3.1.</span></span> <span data-ttu-id="7d15d-158">Pour installer la version actuelle, qui ne peut pas être une version (LTS), utilisez le `-c Current` paramètre.</span><span class="sxs-lookup"><span data-stu-id="7d15d-158">To install the current release, which may not be an (LTS) version, use the `-c Current` parameter.</span></span>

```bash
./dotnet-install.sh -c Current
```

<span data-ttu-id="7d15d-159">Pour installer le Runtime .NET au lieu du kit de développement logiciel (SDK), utilisez le `--runtime` paramètre.</span><span class="sxs-lookup"><span data-stu-id="7d15d-159">To install .NET Runtime instead of the SDK, use the `--runtime` parameter.</span></span>

```bash
./dotnet-install.sh -c Current --runtime aspnetcore
```

<span data-ttu-id="7d15d-160">Vous pouvez installer une version spécifique en modifiant le `-c` paramètre pour indiquer la version spécifique.</span><span class="sxs-lookup"><span data-stu-id="7d15d-160">You can install a specific version by altering the `-c` parameter to indicate the specific version.</span></span> <span data-ttu-id="7d15d-161">La commande suivante installe le kit de développement logiciel (SDK) .NET 5,0.</span><span class="sxs-lookup"><span data-stu-id="7d15d-161">The following command installs .NET SDK 5.0.</span></span>

```bash
./dotnet-install.sh -c 5.0
```

<span data-ttu-id="7d15d-162">Pour plus d’informations, consultez informations de référence sur les [scripts dotnet-install](../tools/dotnet-install-script.md).</span><span class="sxs-lookup"><span data-stu-id="7d15d-162">For more information, see [dotnet-install scripts reference](../tools/dotnet-install-script.md).</span></span>

## <a name="manual-install"></a><span data-ttu-id="7d15d-163">Installation manuelle</span><span class="sxs-lookup"><span data-stu-id="7d15d-163">Manual install</span></span>

<!-- Note, this content is copied in macos.md. Any fixes should be applied there too, though content may be different -->

<span data-ttu-id="7d15d-164">Comme alternative aux gestionnaires de packages, vous pouvez télécharger et installer manuellement le kit de développement logiciel (SDK) et le Runtime.</span><span class="sxs-lookup"><span data-stu-id="7d15d-164">As an alternative to the package managers, you can download and manually install the SDK and runtime.</span></span> <span data-ttu-id="7d15d-165">L’installation manuelle est couramment utilisée dans le cadre du test d’intégration continue ou sur une distribution Linux non prise en charge.</span><span class="sxs-lookup"><span data-stu-id="7d15d-165">Manual install is commonly used as part of continuous integration testing or on an unsupported Linux distribution.</span></span> <span data-ttu-id="7d15d-166">Pour un développeur ou un utilisateur, il est préférable d’utiliser un gestionnaire de package.</span><span class="sxs-lookup"><span data-stu-id="7d15d-166">For a developer or user, it's better to use a package manager.</span></span>

<span data-ttu-id="7d15d-167">Si vous installez le kit de développement logiciel (SDK) .NET, vous n’avez pas besoin d’installer le runtime correspondant.</span><span class="sxs-lookup"><span data-stu-id="7d15d-167">If you install .NET SDK, you don't need to install the corresponding runtime.</span></span> <span data-ttu-id="7d15d-168">Tout d’abord, téléchargez une version **binaire** pour le kit de développement logiciel (SDK) ou le runtime à partir de l’un des sites suivants :</span><span class="sxs-lookup"><span data-stu-id="7d15d-168">First, download a **binary** release for either the SDK or the runtime from one of the following sites:</span></span>

- <span data-ttu-id="7d15d-169">[téléchargements .net 5,0](https://dotnet.microsoft.com/download/dotnet/5.0) ✔️</span><span class="sxs-lookup"><span data-stu-id="7d15d-169">✔️ [.NET 5.0 downloads](https://dotnet.microsoft.com/download/dotnet/5.0)</span></span>
- <span data-ttu-id="7d15d-170">✔️ [téléchargements .net Core 3,1](https://dotnet.microsoft.com/download/dotnet-core/3.1)</span><span class="sxs-lookup"><span data-stu-id="7d15d-170">✔️ [.NET Core 3.1 downloads](https://dotnet.microsoft.com/download/dotnet-core/3.1)</span></span>
- <span data-ttu-id="7d15d-171">✔️ [téléchargements .net Core 2,1](https://dotnet.microsoft.com/download/dotnet-core/2.1)</span><span class="sxs-lookup"><span data-stu-id="7d15d-171">✔️ [.NET Core 2.1 downloads](https://dotnet.microsoft.com/download/dotnet-core/2.1)</span></span>
- [<span data-ttu-id="7d15d-172">Tous les téléchargements .NET Core</span><span class="sxs-lookup"><span data-stu-id="7d15d-172">All .NET Core downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core)

<span data-ttu-id="7d15d-173">Ensuite, extrayez le fichier téléchargé et utilisez la `export` commande pour définir les variables utilisées par .net, puis vérifiez que .net est dans le chemin d’accès.</span><span class="sxs-lookup"><span data-stu-id="7d15d-173">Next, extract the downloaded file and use the `export` command to set variables used by .NET and then ensure .NET is in PATH.</span></span>

<span data-ttu-id="7d15d-174">Pour extraire le runtime et rendre les commandes de l’interface de commande .NET CLI disponibles sur le terminal, commencez par télécharger une version binaire .NET.</span><span class="sxs-lookup"><span data-stu-id="7d15d-174">To extract the runtime and make the .NET CLI commands available at the terminal, first download a .NET binary release.</span></span> <span data-ttu-id="7d15d-175">Ensuite, ouvrez un terminal et exécutez les commandes suivantes à partir du répertoire dans lequel le fichier a été enregistré.</span><span class="sxs-lookup"><span data-stu-id="7d15d-175">Then, open a terminal and run the following commands from the directory where the file was saved.</span></span> <span data-ttu-id="7d15d-176">Le nom du fichier d’archive peut être différent en fonction de ce que vous avez téléchargé.</span><span class="sxs-lookup"><span data-stu-id="7d15d-176">The archive file name may be different depending on what you downloaded.</span></span>

<span data-ttu-id="7d15d-177">**Utilisez la commande suivante pour extraire le runtime**:</span><span class="sxs-lookup"><span data-stu-id="7d15d-177">**Use the following command to extract the runtime**:</span></span>

```bash
mkdir -p "$HOME/dotnet" && tar zxf aspnetcore-runtime-5.0.0-linux-x64.tar.gz -C "$HOME/dotnet"
export DOTNET_ROOT=$HOME/dotnet
export PATH=$PATH:$HOME/dotnet
```

<span data-ttu-id="7d15d-178">**Utilisez la commande suivante pour extraire le kit de développement logiciel (SDK)**:</span><span class="sxs-lookup"><span data-stu-id="7d15d-178">**Use the following command to extract the SDK**:</span></span>

```bash
mkdir -p "$HOME/dotnet" && tar zxf dotnet-sdk-5.0.100-linux-x64.tar.gz -C "$HOME/dotnet"
export DOTNET_ROOT=$HOME/dotnet
export PATH=$PATH:$HOME/dotnet
```

> [!TIP]
> <span data-ttu-id="7d15d-179">Les `export` commandes précédentes rendent uniquement les commandes de l’interface de commande .net CLI disponibles pour la session Terminal dans laquelle elle a été exécutée.</span><span class="sxs-lookup"><span data-stu-id="7d15d-179">The preceding `export` commands only make the .NET CLI commands available for the terminal session in which it was run.</span></span>
>
> <span data-ttu-id="7d15d-180">Vous pouvez modifier votre profil de Shell pour ajouter définitivement les commandes.</span><span class="sxs-lookup"><span data-stu-id="7d15d-180">You can edit your shell profile to permanently add the commands.</span></span> <span data-ttu-id="7d15d-181">Un certain nombre de shells différents sont disponibles pour Linux et chacun d’eux a un profil différent.</span><span class="sxs-lookup"><span data-stu-id="7d15d-181">There are a number of different shells available for Linux and each has a different profile.</span></span> <span data-ttu-id="7d15d-182">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="7d15d-182">For example:</span></span>
>
> - <span data-ttu-id="7d15d-183">**Interpréteur** de commandes bash : *~/.bash_profile*, *~ fichier/.bashrc*</span><span class="sxs-lookup"><span data-stu-id="7d15d-183">**Bash Shell**: *~/.bash_profile*, *~/.bashrc*</span></span>
> - <span data-ttu-id="7d15d-184">**Shell Korn**: *~/.kshrc* ou *. Profile*</span><span class="sxs-lookup"><span data-stu-id="7d15d-184">**Korn Shell**: *~/.kshrc* or *.profile*</span></span>
> - <span data-ttu-id="7d15d-185">**Z Shell**: *~/.zshrc* ou *. zprofile*</span><span class="sxs-lookup"><span data-stu-id="7d15d-185">**Z Shell**: *~/.zshrc* or *.zprofile*</span></span>
>
> <span data-ttu-id="7d15d-186">Modifiez le fichier source approprié pour votre shell et ajoutez `:$HOME/dotnet` à la fin de l' `PATH` instruction existante.</span><span class="sxs-lookup"><span data-stu-id="7d15d-186">Edit the appropriate source file for your shell and add `:$HOME/dotnet` to the end of the existing `PATH` statement.</span></span> <span data-ttu-id="7d15d-187">Si aucune `PATH` instruction n’est incluse, ajoutez une nouvelle ligne avec `export PATH=$PATH:$HOME/dotnet` .</span><span class="sxs-lookup"><span data-stu-id="7d15d-187">If no `PATH` statement is included, add a new line with `export PATH=$PATH:$HOME/dotnet`.</span></span>
>
> <span data-ttu-id="7d15d-188">Ajoutez également `export DOTNET_ROOT=$HOME/dotnet` à la fin du fichier.</span><span class="sxs-lookup"><span data-stu-id="7d15d-188">Also, add `export DOTNET_ROOT=$HOME/dotnet` to the end of the file.</span></span>

<span data-ttu-id="7d15d-189">Cette approche vous permet d’installer différentes versions dans des emplacements distincts et de choisir explicitement celle qui doit être utilisée par l’application.</span><span class="sxs-lookup"><span data-stu-id="7d15d-189">This approach lets you install different versions into separate locations and choose explicitly which one to use by which application.</span></span>

## <a name="next-steps"></a><span data-ttu-id="7d15d-190">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="7d15d-190">Next steps</span></span>

- [<span data-ttu-id="7d15d-191">Comment activer la saisie semi-automatique via la touche TAB pour .NET CLI</span><span class="sxs-lookup"><span data-stu-id="7d15d-191">How to enable TAB completion for the .NET CLI</span></span>](../tools/enable-tab-autocomplete.md)
- [<span data-ttu-id="7d15d-192">Didacticiel : créer une application console avec le kit de développement logiciel (SDK) .NET à l’aide de Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="7d15d-192">Tutorial: Create a console application with .NET SDK using Visual Studio Code</span></span>](../tutorials/with-visual-studio-code.md)
