---
ms.openlocfilehash: 5e77b7bd73c09e061a94a29703cf5286814d1ebb
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84602914"
---

[<span data-ttu-id="7ad44-101">.NET Core est disponible dans le magasin d’instantanés.</span><span class="sxs-lookup"><span data-stu-id="7ad44-101">.NET Core is available from the Snap Store.</span></span>](https://snapcraft.io/dotnet-sdk)

<span data-ttu-id="7ad44-102">Un Snap est un bundle d’une application et de ses dépendances qui fonctionnent sans modification sur de nombreuses distributions Linux différentes.</span><span class="sxs-lookup"><span data-stu-id="7ad44-102">A snap is a bundle of an app and its dependencies that works without modification across many different Linux distributions.</span></span> <span data-ttu-id="7ad44-103">Les instantanés sont détectables et installables à partir du magasin d’instantanés.</span><span class="sxs-lookup"><span data-stu-id="7ad44-103">Snaps are discoverable and installable from the Snap Store.</span></span> <span data-ttu-id="7ad44-104">Pour plus d’informations sur SNAP, consultez [prise en main du composant logiciel enfichable](https://snapcraft.io/docs/getting-started).</span><span class="sxs-lookup"><span data-stu-id="7ad44-104">For more information about Snap, see [Getting started with Snap](https://snapcraft.io/docs/getting-started).</span></span>

<span data-ttu-id="7ad44-105">Seules les versions prises en charge de .NET Core sont disponibles par le biais de l’option Snap.</span><span class="sxs-lookup"><span data-stu-id="7ad44-105">Only supported versions of .NET Core are available through Snap.</span></span>

### <a name="install-the-sdk"></a><span data-ttu-id="7ad44-106">Installer le Kit de développement logiciel (SDK)</span><span class="sxs-lookup"><span data-stu-id="7ad44-106">Install the SDK</span></span>

<span data-ttu-id="7ad44-107">Les packages d’alignement pour kit SDK .NET Core sont tous publiés sous le même identificateur : `dotnet-sdk` .</span><span class="sxs-lookup"><span data-stu-id="7ad44-107">Snap packages for .NET Core SDK are all published under the same identifier: `dotnet-sdk`.</span></span> <span data-ttu-id="7ad44-108">Une version spécifique du kit de développement logiciel (SDK) peut être installée en spécifiant le canal.</span><span class="sxs-lookup"><span data-stu-id="7ad44-108">A specific version of the SDK can be installed by specifying the channel.</span></span> <span data-ttu-id="7ad44-109">Le kit de développement logiciel (SDK) comprend le runtime de cofacette.</span><span class="sxs-lookup"><span data-stu-id="7ad44-109">The SDK includes the coresponding runtime.</span></span> <span data-ttu-id="7ad44-110">Le tableau suivant répertorie les canaux :</span><span class="sxs-lookup"><span data-stu-id="7ad44-110">The following table list the channels:</span></span>

| <span data-ttu-id="7ad44-111">Version .NET Core</span><span class="sxs-lookup"><span data-stu-id="7ad44-111">.NET Core version</span></span> | <span data-ttu-id="7ad44-112">Package d’alignement</span><span class="sxs-lookup"><span data-stu-id="7ad44-112">Snap package</span></span>             |
|-------------------|--------------------------|
| <span data-ttu-id="7ad44-113">3,1 (LTS)</span><span class="sxs-lookup"><span data-stu-id="7ad44-113">3.1 (LTS)</span></span>         | <span data-ttu-id="7ad44-114">`3.1` ou `latest/stable`</span><span class="sxs-lookup"><span data-stu-id="7ad44-114">`3.1` or `latest/stable`</span></span> |
| <span data-ttu-id="7ad44-115">2,1 (LTS)</span><span class="sxs-lookup"><span data-stu-id="7ad44-115">2.1 (LTS)</span></span>         | `2.1`                    |
| <span data-ttu-id="7ad44-116">Version préliminaire de .NET 5,0</span><span class="sxs-lookup"><span data-stu-id="7ad44-116">.NET 5.0 preview</span></span>  | `5.0/beta`               |

<span data-ttu-id="7ad44-117">Utilisez la `snap install` commande pour installer un package kit SDK .net Core Snap.</span><span class="sxs-lookup"><span data-stu-id="7ad44-117">Use the `snap install` command to install a .NET Core SDK snap package.</span></span> <span data-ttu-id="7ad44-118">Utilisez le `--channel` paramètre pour indiquer la version à installer.</span><span class="sxs-lookup"><span data-stu-id="7ad44-118">Use the `--channel` parameter to indicate which version to install.</span></span> <span data-ttu-id="7ad44-119">Si ce paramètre est omis, `latest/stable` est utilisé.</span><span class="sxs-lookup"><span data-stu-id="7ad44-119">If this parameter is omitted, `latest/stable` is used.</span></span> <span data-ttu-id="7ad44-120">Dans cet exemple, `3.1` est spécifié :</span><span class="sxs-lookup"><span data-stu-id="7ad44-120">In this example, `3.1` is specified:</span></span>

```bash
sudo snap install dotnet-sdk --classic --channel=3.1
```

<span data-ttu-id="7ad44-121">Ensuite, inscrivez la `dotnet` commande pour le système à l’aide de la `snap alias` commande :</span><span class="sxs-lookup"><span data-stu-id="7ad44-121">Next, register the `dotnet` command for the system with the `snap alias` command:</span></span>

```bash
sudo snap alias dotnet-sdk.dotnet dotnet
```

<span data-ttu-id="7ad44-122">Cette commande est au format : `sudo snap alias {package}.{command} {alias}` .</span><span class="sxs-lookup"><span data-stu-id="7ad44-122">This command is formatted as: `sudo snap alias {package}.{command} {alias}`.</span></span> <span data-ttu-id="7ad44-123">Vous pouvez choisir n’importe quel `{alias}` nom.</span><span class="sxs-lookup"><span data-stu-id="7ad44-123">You can choose any `{alias}` name you would like.</span></span> <span data-ttu-id="7ad44-124">Par exemple, vous pouvez nommer la commande après la version spécifique installée par le composant logiciel enfichable : `sudo snap alias dotnet-sdk.dotnet dotnet31` .</span><span class="sxs-lookup"><span data-stu-id="7ad44-124">For example, you could name the command after the specific version installed by snap: `sudo snap alias dotnet-sdk.dotnet dotnet31`.</span></span> <span data-ttu-id="7ad44-125">Lorsque vous utilisez la commande `dotnet31` , vous appellerez cette version spécifique de .net.</span><span class="sxs-lookup"><span data-stu-id="7ad44-125">When you use the command `dotnet31`, you'll invoke this specific version of .NET.</span></span> <span data-ttu-id="7ad44-126">Mais cela n’est pas compatible avec la plupart des didacticiels et des exemples, car ils attendent qu’une `dotnet` commande soit disponible.</span><span class="sxs-lookup"><span data-stu-id="7ad44-126">But this is incompatible with most tutorials and examples as they expect a `dotnet` command to be available.</span></span>

### <a name="install-the-runtime"></a><span data-ttu-id="7ad44-127">Installer le runtime</span><span class="sxs-lookup"><span data-stu-id="7ad44-127">Install the runtime</span></span>

<span data-ttu-id="7ad44-128">Les packages Snap pour le Runtime .NET Core sont publiés sous leur propre identificateur de package.</span><span class="sxs-lookup"><span data-stu-id="7ad44-128">Snap packages for .NET Core Runtime are each published under their own package identifier.</span></span> <span data-ttu-id="7ad44-129">Le tableau suivant répertorie les identificateurs de package :</span><span class="sxs-lookup"><span data-stu-id="7ad44-129">The following table lists the package identifiers:</span></span>

| <span data-ttu-id="7ad44-130">Version .NET Core</span><span class="sxs-lookup"><span data-stu-id="7ad44-130">.NET Core version</span></span> | <span data-ttu-id="7ad44-131">Package d’alignement</span><span class="sxs-lookup"><span data-stu-id="7ad44-131">Snap package</span></span>        |
|-------------------|---------------------|
| <span data-ttu-id="7ad44-132">3,1 (LTS)</span><span class="sxs-lookup"><span data-stu-id="7ad44-132">3.1 (LTS)</span></span>         | `dotnet-runtime-31` |
| <span data-ttu-id="7ad44-133">3.0</span><span class="sxs-lookup"><span data-stu-id="7ad44-133">3.0</span></span>               | `dotnet-runtime-30` |
| <span data-ttu-id="7ad44-134">2.2</span><span class="sxs-lookup"><span data-stu-id="7ad44-134">2.2</span></span>               | `dotnet-runtime-22` |
| <span data-ttu-id="7ad44-135">2,1 (LTS)</span><span class="sxs-lookup"><span data-stu-id="7ad44-135">2.1 (LTS)</span></span>         | `dotnet-runtime-21` |

<span data-ttu-id="7ad44-136">Utilisez la `snap install` commande pour installer un package de composant logiciel enfichable du Runtime .net core.</span><span class="sxs-lookup"><span data-stu-id="7ad44-136">Use the `snap install` command to install a .NET Core Runtime snap package.</span></span> <span data-ttu-id="7ad44-137">Dans cet exemple, .NET Core 3,1 est installé :</span><span class="sxs-lookup"><span data-stu-id="7ad44-137">In this example, .NET Core 3.1 is installed:</span></span>

```bash
sudo snap install dotnet-runtime-31 --classic
```

<span data-ttu-id="7ad44-138">Ensuite, inscrivez la `dotnet` commande pour le système à l’aide de la `snap alias` commande :</span><span class="sxs-lookup"><span data-stu-id="7ad44-138">Next, register the `dotnet` command for the system with the `snap alias` command:</span></span>

```bash
sudo snap alias dotnet-runtime-31.dotnet dotnet
```

<span data-ttu-id="7ad44-139">Cette commande est au format : `sudo snap alias {package}.{command} {alias}` .</span><span class="sxs-lookup"><span data-stu-id="7ad44-139">This command is formatted as: `sudo snap alias {package}.{command} {alias}`.</span></span> <span data-ttu-id="7ad44-140">Vous pouvez choisir n’importe quel `{alias}` nom.</span><span class="sxs-lookup"><span data-stu-id="7ad44-140">You can choose any `{alias}` name you would like.</span></span> <span data-ttu-id="7ad44-141">Par exemple, vous pouvez nommer la commande après la version spécifique installée par le composant logiciel enfichable : `sudo snap alias dotnet-runtime-31.dotnet dotnet31` .</span><span class="sxs-lookup"><span data-stu-id="7ad44-141">For example, you could name the command after the specific version installed by snap: `sudo snap alias dotnet-runtime-31.dotnet dotnet31`.</span></span> <span data-ttu-id="7ad44-142">Lorsque vous utilisez la commande `dotnet31` , vous appellerez cette version spécifique de .net.</span><span class="sxs-lookup"><span data-stu-id="7ad44-142">When you use the command `dotnet31`, you'll invoke this specific version of .NET.</span></span> <span data-ttu-id="7ad44-143">Mais cela n’est pas compatible avec la plupart des didacticiels et des exemples, car ils attendent qu’une `dotnet` commande soit disponible.</span><span class="sxs-lookup"><span data-stu-id="7ad44-143">But this is incompatible with most tutorials and examples as they expect a `dotnet` command to be available.</span></span>

### <a name="ssl-certificate-errors"></a><span data-ttu-id="7ad44-144">Erreurs de certificat SSL</span><span class="sxs-lookup"><span data-stu-id="7ad44-144">SSL Certificate errors</span></span>

<span data-ttu-id="7ad44-145">Lorsque .NET est installé par le biais de l’option Snap, il est possible que sur certains distributions les certificats SSL .NET soient introuvables et que vous receviez un message d’erreur semblable au suivant pendant `restore` :</span><span class="sxs-lookup"><span data-stu-id="7ad44-145">When .NET is installed through Snap, it's possible that on some distros the .NET SSL certificates may not be found and you may receive an error similar to the following during `restore`:</span></span>

```bash
Processing post-creation actions...
Running 'dotnet restore' on /home/myhome/test/test.csproj...
  Restoring packages for /home/myhome/test/test.csproj...
/snap/dotnet-sdk/27/sdk/2.2.103/NuGet.targets(114,5): error : Unable to load the service index for source https://api.nuget.org/v3/index.json. [/home/myhome/test/test.csproj]
/snap/dotnet-sdk/27/sdk/2.2.103/NuGet.targets(114,5): error :   The SSL connection could not be established, see inner exception. [/home/myhome/test/test.csproj]
/snap/dotnet-sdk/27/sdk/2.2.103/NuGet.targets(114,5): error :   The remote certificate is invalid according to the validation procedure. [/home/myhome/test/test.csproj]
```

<span data-ttu-id="7ad44-146">Pour résoudre ce problème, définissez quelques variables environnement :</span><span class="sxs-lookup"><span data-stu-id="7ad44-146">To resolve this issue, set a few enviornment variables:</span></span>

```bash
export SSL_CERT_FILE=[path-to-certificate-file]
export SSL_CERT_DIR=/dev/null
```

<span data-ttu-id="7ad44-147">L’emplacement du certificat varie selon le distribution.</span><span class="sxs-lookup"><span data-stu-id="7ad44-147">The certificate location will vary by distro.</span></span> <span data-ttu-id="7ad44-148">Voici les emplacements du distributions où nous avons rencontré le problème.</span><span class="sxs-lookup"><span data-stu-id="7ad44-148">Here are the locations for the distros where we have experienced the issue.</span></span>

* <span data-ttu-id="7ad44-149">Fedora`/etc/pki/ca-trust/extracted/pem/tls-ca-bundle.pem`</span><span class="sxs-lookup"><span data-stu-id="7ad44-149">Fedora - `/etc/pki/ca-trust/extracted/pem/tls-ca-bundle.pem`</span></span>
* <span data-ttu-id="7ad44-150">OpenSUSE`/etc/ssl/ca-bundle.pem`</span><span class="sxs-lookup"><span data-stu-id="7ad44-150">OpenSUSE - `/etc/ssl/ca-bundle.pem`</span></span>
* <span data-ttu-id="7ad44-151">Solus -`/etc/ssl/certs/ca-certificates.crt`</span><span class="sxs-lookup"><span data-stu-id="7ad44-151">Solus - `/etc/ssl/certs/ca-certificates.crt`</span></span>
