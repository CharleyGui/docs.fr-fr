---
title: Installer .NET sur Linux avec Snap-.NET
description: Montre comment installer le kit de développement logiciel (SDK) .NET ou le Runtime .NET sur Linux avec Snap.
author: adegeo
ms.author: adegeo
ms.date: 01/06/2021
ms.openlocfilehash: 741933b5ca6f01d73b388675fe7f8a43c4efb0f9
ms.sourcegitcommit: 7ef96827b161ef3fcde75f79d839885632e26ef1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/07/2021
ms.locfileid: "97970965"
---
# <a name="install-the-net-sdk-or-the-net-runtime-with-snap"></a><span data-ttu-id="afe21-103">Installer le kit de développement logiciel (SDK) .NET ou le Runtime .NET avec Snap</span><span class="sxs-lookup"><span data-stu-id="afe21-103">Install the .NET SDK or the .NET Runtime with Snap</span></span>

<span data-ttu-id="afe21-104">Utilisez un package d’installation pour installer le kit de développement logiciel (SDK) .NET ou le Runtime .NET.</span><span class="sxs-lookup"><span data-stu-id="afe21-104">Use a Snap package to install the .NET SDK or .NET Runtime.</span></span> <span data-ttu-id="afe21-105">Les instantanés sont une excellente alternative au gestionnaire de package intégré à votre distribution Linux.</span><span class="sxs-lookup"><span data-stu-id="afe21-105">Snaps are a great alternative to the package manager built into your Linux distribution.</span></span> <span data-ttu-id="afe21-106">Cet article explique comment installer .NET via le [composant logiciel enfichable](https://snapcraft.io/dotnet-sdk).</span><span class="sxs-lookup"><span data-stu-id="afe21-106">This article describes how to install .NET through [Snap](https://snapcraft.io/dotnet-sdk).</span></span>

<span data-ttu-id="afe21-107">Un Snap est un bundle d’une application et de ses dépendances qui fonctionnent sans modification sur de nombreuses distributions Linux différentes.</span><span class="sxs-lookup"><span data-stu-id="afe21-107">A snap is a bundle of an app and its dependencies that works without modification across many different Linux distributions.</span></span> <span data-ttu-id="afe21-108">Les instantanés sont détectables et installables à partir du magasin d’instantanés.</span><span class="sxs-lookup"><span data-stu-id="afe21-108">Snaps are discoverable and installable from the Snap Store.</span></span> <span data-ttu-id="afe21-109">Pour plus d’informations sur SNAP, consultez [prise en main du composant logiciel enfichable](https://snapcraft.io/docs/getting-started).</span><span class="sxs-lookup"><span data-stu-id="afe21-109">For more information about Snap, see [Getting started with Snap](https://snapcraft.io/docs/getting-started).</span></span>

> [!CAUTION]
> <span data-ttu-id="afe21-110">Les packages Snap ne sont pas pris en charge dans WSL2 sur Windows 10.</span><span class="sxs-lookup"><span data-stu-id="afe21-110">Snap packages aren't supported in WSL2 on Windows 10.</span></span> <span data-ttu-id="afe21-111">Vous pouvez également utiliser le [ `dotnet-install` script](linux-scripted-manual.md#scripted-install) ou le gestionnaire de package pour la distribution WSL2 particulière.</span><span class="sxs-lookup"><span data-stu-id="afe21-111">As an alternative, use the [`dotnet-install` script](linux-scripted-manual.md#scripted-install) or the package manager for the particular WSL2 distribution.</span></span> <span data-ttu-id="afe21-112">Ce n’est pas recommandé, mais vous pouvez essayer d’activer Snap avec une [solution de contournement non prise en charge à partir des forums snapcraft](https://forum.snapcraft.io/t/running-snaps-on-wsl2-insiders-only-for-now/13033).</span><span class="sxs-lookup"><span data-stu-id="afe21-112">It's not recommended but you can try to enable snap with an [unsupported workaround from the snapcraft forums](https://forum.snapcraft.io/t/running-snaps-on-wsl2-insiders-only-for-now/13033).</span></span>

## <a name="net-releases"></a><span data-ttu-id="afe21-113">Versions de .NET</span><span class="sxs-lookup"><span data-stu-id="afe21-113">.NET releases</span></span>

<span data-ttu-id="afe21-114">✔️ seules les versions prises en charge du kit de développement logiciel (SDK) .NET sont disponibles via l’option Snap.</span><span class="sxs-lookup"><span data-stu-id="afe21-114">Only ✔️ supported versions of .NET SDK are available through Snap.</span></span> <span data-ttu-id="afe21-115">Toutes les versions du Runtime .NET sont disponibles via le composant logiciel enfichable à partir de la version 2,1.</span><span class="sxs-lookup"><span data-stu-id="afe21-115">All versions of the .NET Runtime are available through snap starting with version 2.1.</span></span> <span data-ttu-id="afe21-116">Le tableau suivant répertorie les versions de .NET (et .NET Core) :</span><span class="sxs-lookup"><span data-stu-id="afe21-116">The following table lists the .NET (and .NET Core) releases:</span></span>

| <span data-ttu-id="afe21-117">✔️ pris en charge</span><span class="sxs-lookup"><span data-stu-id="afe21-117">✔️ Supported</span></span> | <span data-ttu-id="afe21-118">❌ Pris en charge</span><span class="sxs-lookup"><span data-stu-id="afe21-118">❌ Unsupported</span></span> |
|-------------|---------------|
| <span data-ttu-id="afe21-119">5.0</span><span class="sxs-lookup"><span data-stu-id="afe21-119">5.0</span></span>         | <span data-ttu-id="afe21-120">3.0</span><span class="sxs-lookup"><span data-stu-id="afe21-120">3.0</span></span>           |
| <span data-ttu-id="afe21-121">3,1 (LTS)</span><span class="sxs-lookup"><span data-stu-id="afe21-121">3.1 (LTS)</span></span>   | <span data-ttu-id="afe21-122">2.2</span><span class="sxs-lookup"><span data-stu-id="afe21-122">2.2</span></span>           |
| <span data-ttu-id="afe21-123">2,1 (LTS)</span><span class="sxs-lookup"><span data-stu-id="afe21-123">2.1 (LTS)</span></span>   | <span data-ttu-id="afe21-124">2,0</span><span class="sxs-lookup"><span data-stu-id="afe21-124">2.0</span></span>           |
|             | <span data-ttu-id="afe21-125">1,1</span><span class="sxs-lookup"><span data-stu-id="afe21-125">1.1</span></span>           |
|             | <span data-ttu-id="afe21-126">1.0</span><span class="sxs-lookup"><span data-stu-id="afe21-126">1.0</span></span>           |

<span data-ttu-id="afe21-127">Pour plus d’informations sur le cycle de vie des versions de .NET, consultez [stratégie de support .net Core et .net 5](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).</span><span class="sxs-lookup"><span data-stu-id="afe21-127">For more information about the life cycle of .NET releases, see [.NET Core and .NET 5 Support Policy](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).</span></span>

## <a name="sdk-or-runtime"></a><span data-ttu-id="afe21-128">SDK ou Runtime</span><span class="sxs-lookup"><span data-stu-id="afe21-128">SDK or Runtime</span></span>

[!INCLUDE [linux-intro-sdk-vs-runtime](includes/linux-intro-sdk-vs-runtime.md)]

## <a name="install-the-sdk"></a><span data-ttu-id="afe21-129">Installer le SDK</span><span class="sxs-lookup"><span data-stu-id="afe21-129">Install the SDK</span></span>

<span data-ttu-id="afe21-130">Les packages Snap pour le kit de développement logiciel (SDK) .NET sont tous publiés sous le même identificateur : `dotnet-sdk` .</span><span class="sxs-lookup"><span data-stu-id="afe21-130">Snap packages for the .NET SDK are all published under the same identifier: `dotnet-sdk`.</span></span> <span data-ttu-id="afe21-131">Une version spécifique du kit de développement logiciel (SDK) peut être installée en spécifiant le canal.</span><span class="sxs-lookup"><span data-stu-id="afe21-131">A specific version of the SDK can be installed by specifying the channel.</span></span> <span data-ttu-id="afe21-132">Le kit de développement logiciel (SDK) comprend le runtime correspondant.</span><span class="sxs-lookup"><span data-stu-id="afe21-132">The SDK includes the corresponding runtime.</span></span> <span data-ttu-id="afe21-133">Le tableau suivant répertorie les canaux :</span><span class="sxs-lookup"><span data-stu-id="afe21-133">The following table lists the channels:</span></span>

| <span data-ttu-id="afe21-134">Version de .NET</span><span class="sxs-lookup"><span data-stu-id="afe21-134">.NET version</span></span> | <span data-ttu-id="afe21-135">Package d’alignement ou canal</span><span class="sxs-lookup"><span data-stu-id="afe21-135">Snap package or channel</span></span>  |
|--------------|--------------------------|
| <span data-ttu-id="afe21-136">5.0</span><span class="sxs-lookup"><span data-stu-id="afe21-136">5.0</span></span>          | <span data-ttu-id="afe21-137">`5.0` ou `latest/stable`</span><span class="sxs-lookup"><span data-stu-id="afe21-137">`5.0` or `latest/stable`</span></span> |
| <span data-ttu-id="afe21-138">3,1 (LTS)</span><span class="sxs-lookup"><span data-stu-id="afe21-138">3.1 (LTS)</span></span>    | <span data-ttu-id="afe21-139">`3.1` ou `lts/stable`</span><span class="sxs-lookup"><span data-stu-id="afe21-139">`3.1` or `lts/stable`</span></span>    |
| <span data-ttu-id="afe21-140">2,1 (LTS)</span><span class="sxs-lookup"><span data-stu-id="afe21-140">2.1 (LTS)</span></span>    | `2.1`                    |

<span data-ttu-id="afe21-141">Utilisez la `snap install` commande pour installer un package du kit de développement logiciel (SDK) .net.</span><span class="sxs-lookup"><span data-stu-id="afe21-141">Use the `snap install` command to install a .NET SDK snap package.</span></span> <span data-ttu-id="afe21-142">Utilisez le `--channel` paramètre pour indiquer la version à installer.</span><span class="sxs-lookup"><span data-stu-id="afe21-142">Use the `--channel` parameter to indicate which version to install.</span></span> <span data-ttu-id="afe21-143">Si ce paramètre est omis, `latest/stable` est utilisé.</span><span class="sxs-lookup"><span data-stu-id="afe21-143">If this parameter is omitted, `latest/stable` is used.</span></span> <span data-ttu-id="afe21-144">Dans cet exemple, `5.0` est spécifié :</span><span class="sxs-lookup"><span data-stu-id="afe21-144">In this example, `5.0` is specified:</span></span>

```bash
sudo snap install dotnet-sdk --classic --channel=5.0
```

<span data-ttu-id="afe21-145">Ensuite, inscrivez la `dotnet` commande pour le système à l’aide de la `snap alias` commande :</span><span class="sxs-lookup"><span data-stu-id="afe21-145">Next, register the `dotnet` command for the system with the `snap alias` command:</span></span>

```bash
sudo snap alias dotnet-sdk.dotnet dotnet
```

<span data-ttu-id="afe21-146">Cette commande est au format : `sudo snap alias {package}.{command} {alias}` .</span><span class="sxs-lookup"><span data-stu-id="afe21-146">This command is formatted as: `sudo snap alias {package}.{command} {alias}`.</span></span> <span data-ttu-id="afe21-147">Vous pouvez choisir n’importe quel `{alias}` nom.</span><span class="sxs-lookup"><span data-stu-id="afe21-147">You can choose any `{alias}` name you would like.</span></span> <span data-ttu-id="afe21-148">Par exemple, vous pouvez nommer la commande après la version spécifique installée par le composant logiciel enfichable : `sudo snap alias dotnet-sdk.dotnet dotnet50` .</span><span class="sxs-lookup"><span data-stu-id="afe21-148">For example, you could name the command after the specific version installed by snap: `sudo snap alias dotnet-sdk.dotnet dotnet50`.</span></span> <span data-ttu-id="afe21-149">Lorsque vous utilisez la commande `dotnet50` , vous appellerez cette version spécifique de .net.</span><span class="sxs-lookup"><span data-stu-id="afe21-149">When you use the command `dotnet50`, you'll invoke this specific version of .NET.</span></span> <span data-ttu-id="afe21-150">Toutefois, le choix d’un alias différent est incompatible avec la plupart des didacticiels et des exemples, car ils attendent qu’une `dotnet` commande soit utilisée.</span><span class="sxs-lookup"><span data-stu-id="afe21-150">But choosing a different alias is incompatible with most tutorials and examples as they expect a `dotnet` command to be used.</span></span>

## <a name="install-the-runtime"></a><span data-ttu-id="afe21-151">Installer le runtime</span><span class="sxs-lookup"><span data-stu-id="afe21-151">Install the runtime</span></span>

<span data-ttu-id="afe21-152">Les packages Snap pour le Runtime .NET sont publiés sous leur propre identificateur de package.</span><span class="sxs-lookup"><span data-stu-id="afe21-152">Snap packages for the .NET Runtime are each published under their own package identifier.</span></span> <span data-ttu-id="afe21-153">Le tableau suivant répertorie les identificateurs de package :</span><span class="sxs-lookup"><span data-stu-id="afe21-153">The following table lists the package identifiers:</span></span>

| <span data-ttu-id="afe21-154">Version de .NET</span><span class="sxs-lookup"><span data-stu-id="afe21-154">.NET version</span></span>      | <span data-ttu-id="afe21-155">Package d’alignement</span><span class="sxs-lookup"><span data-stu-id="afe21-155">Snap package</span></span>        |
|-------------------|---------------------|
| <span data-ttu-id="afe21-156">5.0</span><span class="sxs-lookup"><span data-stu-id="afe21-156">5.0</span></span>               | `dotnet-runtime-50` |
| <span data-ttu-id="afe21-157">3,1 (LTS)</span><span class="sxs-lookup"><span data-stu-id="afe21-157">3.1 (LTS)</span></span>         | `dotnet-runtime-31` |
| <span data-ttu-id="afe21-158">3.0</span><span class="sxs-lookup"><span data-stu-id="afe21-158">3.0</span></span>               | `dotnet-runtime-30` |
| <span data-ttu-id="afe21-159">2.2</span><span class="sxs-lookup"><span data-stu-id="afe21-159">2.2</span></span>               | `dotnet-runtime-22` |
| <span data-ttu-id="afe21-160">2,1 (LTS)</span><span class="sxs-lookup"><span data-stu-id="afe21-160">2.1 (LTS)</span></span>         | `dotnet-runtime-21` |

<span data-ttu-id="afe21-161">Utilisez la `snap install` commande pour installer un package Snap .NET Runtime.</span><span class="sxs-lookup"><span data-stu-id="afe21-161">Use the `snap install` command to install a .NET Runtime snap package.</span></span> <span data-ttu-id="afe21-162">Dans cet exemple, .NET 5,0 est installé :</span><span class="sxs-lookup"><span data-stu-id="afe21-162">In this example, .NET 5.0 is installed:</span></span>

```bash
sudo snap install dotnet-runtime-50 --classic
```

<span data-ttu-id="afe21-163">Ensuite, inscrivez la `dotnet` commande pour le système à l’aide de la `snap alias` commande :</span><span class="sxs-lookup"><span data-stu-id="afe21-163">Next, register the `dotnet` command for the system with the `snap alias` command:</span></span>

```bash
sudo snap alias dotnet-runtime-50.dotnet dotnet
```

<span data-ttu-id="afe21-164">La commande est mise en forme de la façon suivante : `sudo snap alias {package}.{command} {alias}` .</span><span class="sxs-lookup"><span data-stu-id="afe21-164">The command is formatted as: `sudo snap alias {package}.{command} {alias}`.</span></span> <span data-ttu-id="afe21-165">Vous pouvez choisir n’importe quel `{alias}` nom.</span><span class="sxs-lookup"><span data-stu-id="afe21-165">You can choose any `{alias}` name you would like.</span></span> <span data-ttu-id="afe21-166">Par exemple, vous pouvez nommer la commande après la version spécifique installée par le composant logiciel enfichable : `sudo snap alias dotnet-runtime-50.dotnet dotnet50` .</span><span class="sxs-lookup"><span data-stu-id="afe21-166">For example, you could name the command after the specific version installed by snap: `sudo snap alias dotnet-runtime-50.dotnet dotnet50`.</span></span> <span data-ttu-id="afe21-167">Quand vous utilisez la commande `dotnet50` , vous appelez une version spécifique de .net.</span><span class="sxs-lookup"><span data-stu-id="afe21-167">When you use the command `dotnet50`, you'll invoke a specific version of .NET.</span></span> <span data-ttu-id="afe21-168">Toutefois, le choix d’un alias différent est incompatible avec la plupart des didacticiels et des exemples, car ils attendent qu’une `dotnet` commande soit disponible.</span><span class="sxs-lookup"><span data-stu-id="afe21-168">But choosing a different alias is incompatible with most tutorials and examples as they expect a `dotnet` command to be available.</span></span>

## <a name="tlsssl-certificate-errors"></a><span data-ttu-id="afe21-169">Erreurs de certificat TLS/SSL</span><span class="sxs-lookup"><span data-stu-id="afe21-169">TLS/SSL Certificate errors</span></span>

<span data-ttu-id="afe21-170">Lorsque .NET est installé via le composant logiciel enfichable, il est possible que sur certains distributions les certificats TLS/SSL .NET soient introuvables et que vous receviez une erreur lors de l’opération `restore` :</span><span class="sxs-lookup"><span data-stu-id="afe21-170">When .NET is installed through Snap, it's possible that on some distros the .NET TLS/SSL certificates may not be found and you may receive an error during `restore`:</span></span>

```bash
Processing post-creation actions...
Running 'dotnet restore' on /home/myhome/test/test.csproj...
  Restoring packages for /home/myhome/test/test.csproj...
/snap/dotnet-sdk/27/sdk/2.2.103/NuGet.targets(114,5): error : Unable to load the service index for source https://api.nuget.org/v3/index.json. [/home/myhome/test/test.csproj]
/snap/dotnet-sdk/27/sdk/2.2.103/NuGet.targets(114,5): error :   The SSL connection could not be established, see inner exception. [/home/myhome/test/test.csproj]
/snap/dotnet-sdk/27/sdk/2.2.103/NuGet.targets(114,5): error :   The remote certificate is invalid according to the validation procedure. [/home/myhome/test/test.csproj]
```

<span data-ttu-id="afe21-171">Pour résoudre ce problème, définissez quelques variables d’environnement :</span><span class="sxs-lookup"><span data-stu-id="afe21-171">To resolve this problem, set a few environment variables:</span></span>

```bash
export SSL_CERT_FILE=[path-to-certificate-file]
export SSL_CERT_DIR=/dev/null
```

<span data-ttu-id="afe21-172">L’emplacement du certificat varie selon le distribution.</span><span class="sxs-lookup"><span data-stu-id="afe21-172">The certificate location will vary by distro.</span></span> <span data-ttu-id="afe21-173">Voici les emplacements du distributions où le problème a été rencontré.</span><span class="sxs-lookup"><span data-stu-id="afe21-173">Here are the locations for the distros where the issue has been experienced.</span></span>

| <span data-ttu-id="afe21-174">Distribution</span><span class="sxs-lookup"><span data-stu-id="afe21-174">Distribution</span></span> | <span data-ttu-id="afe21-175">Localisation</span><span class="sxs-lookup"><span data-stu-id="afe21-175">Location</span></span>                                            |
|--------------|-----------------------------------------------------|
| <span data-ttu-id="afe21-176">**Fedora**</span><span class="sxs-lookup"><span data-stu-id="afe21-176">**Fedora**</span></span>   | `/etc/pki/ca-trust/extracted/pem/tls-ca-bundle.pem` |
| <span data-ttu-id="afe21-177">**OpenSUSE**</span><span class="sxs-lookup"><span data-stu-id="afe21-177">**OpenSUSE**</span></span> | `/etc/ssl/ca-bundle.pem`                            |
| <span data-ttu-id="afe21-178">**Solus**</span><span class="sxs-lookup"><span data-stu-id="afe21-178">**Solus**</span></span>    | `/etc/ssl/certs/ca-certificates.crt`                |

## <a name="next-steps"></a><span data-ttu-id="afe21-179">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="afe21-179">Next steps</span></span>

- [<span data-ttu-id="afe21-180">Comment activer la saisie semi-automatique via la touche TAB pour .NET CLI</span><span class="sxs-lookup"><span data-stu-id="afe21-180">How to enable TAB completion for the .NET CLI</span></span>](../tools/enable-tab-autocomplete.md)
- [<span data-ttu-id="afe21-181">Didacticiel : créer une application console avec le kit de développement logiciel (SDK) .NET à l’aide de Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="afe21-181">Tutorial: Create a console application with .NET SDK using Visual Studio Code</span></span>](../tutorials/with-visual-studio-code.md)
