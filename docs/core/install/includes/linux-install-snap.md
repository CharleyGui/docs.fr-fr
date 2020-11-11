---
ms.openlocfilehash: 4ab2fc0645f76870dead99b5f45eef763643fb27
ms.sourcegitcommit: bc9c63541c3dc756d48a7ce9d22b5583a18cf7fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/11/2020
ms.locfileid: "94506898"
---

[<span data-ttu-id="c69e2-101">.NET Core est disponible dans le magasin d’instantanés.</span><span class="sxs-lookup"><span data-stu-id="c69e2-101">.NET Core is available from the Snap Store.</span></span>](https://snapcraft.io/dotnet-sdk)

<span data-ttu-id="c69e2-102">Un Snap est un bundle d’une application et de ses dépendances qui fonctionnent sans modification sur de nombreuses distributions Linux différentes.</span><span class="sxs-lookup"><span data-stu-id="c69e2-102">A snap is a bundle of an app and its dependencies that works without modification across many different Linux distributions.</span></span> <span data-ttu-id="c69e2-103">Les instantanés sont détectables et installables à partir du magasin d’instantanés.</span><span class="sxs-lookup"><span data-stu-id="c69e2-103">Snaps are discoverable and installable from the Snap Store.</span></span> <span data-ttu-id="c69e2-104">Pour plus d’informations sur SNAP, consultez [prise en main du composant logiciel enfichable](https://snapcraft.io/docs/getting-started).</span><span class="sxs-lookup"><span data-stu-id="c69e2-104">For more information about Snap, see [Getting started with Snap](https://snapcraft.io/docs/getting-started).</span></span>

<span data-ttu-id="c69e2-105">Seules les versions prises en charge de .NET Core sont disponibles par le biais de l’option Snap.</span><span class="sxs-lookup"><span data-stu-id="c69e2-105">Only supported versions of .NET Core are available through Snap.</span></span>

### <a name="install-the-sdk"></a><span data-ttu-id="c69e2-106">Installer le SDK</span><span class="sxs-lookup"><span data-stu-id="c69e2-106">Install the SDK</span></span>

<span data-ttu-id="c69e2-107">Les packages Snap pour le kit de développement logiciel (SDK) .NET sont tous publiés sous le même identificateur : `dotnet-sdk` .</span><span class="sxs-lookup"><span data-stu-id="c69e2-107">Snap packages for .NET SDK are all published under the same identifier: `dotnet-sdk`.</span></span> <span data-ttu-id="c69e2-108">Une version spécifique du kit de développement logiciel (SDK) peut être installée en spécifiant le canal.</span><span class="sxs-lookup"><span data-stu-id="c69e2-108">A specific version of the SDK can be installed by specifying the channel.</span></span> <span data-ttu-id="c69e2-109">Le kit de développement logiciel (SDK) comprend le runtime de cofacette.</span><span class="sxs-lookup"><span data-stu-id="c69e2-109">The SDK includes the coresponding runtime.</span></span> <span data-ttu-id="c69e2-110">Le tableau suivant répertorie les canaux :</span><span class="sxs-lookup"><span data-stu-id="c69e2-110">The following table list the channels:</span></span>

| <span data-ttu-id="c69e2-111">Version de .NET</span><span class="sxs-lookup"><span data-stu-id="c69e2-111">.NET version</span></span> | <span data-ttu-id="c69e2-112">Package d’alignement</span><span class="sxs-lookup"><span data-stu-id="c69e2-112">Snap package</span></span>             |
|--------------|--------------------------|
| <span data-ttu-id="c69e2-113">5.0</span><span class="sxs-lookup"><span data-stu-id="c69e2-113">5.0</span></span>          | <span data-ttu-id="c69e2-114">`5.0` ou `latest/stable`</span><span class="sxs-lookup"><span data-stu-id="c69e2-114">`5.0` or `latest/stable`</span></span> |
| <span data-ttu-id="c69e2-115">3,1 (LTS)</span><span class="sxs-lookup"><span data-stu-id="c69e2-115">3.1 (LTS)</span></span>    | <span data-ttu-id="c69e2-116">`3.1` ou `lts/stable`</span><span class="sxs-lookup"><span data-stu-id="c69e2-116">`3.1` or `lts/stable`</span></span>    |
| <span data-ttu-id="c69e2-117">2,1 (LTS)</span><span class="sxs-lookup"><span data-stu-id="c69e2-117">2.1 (LTS)</span></span>    | `2.1`                    |

<span data-ttu-id="c69e2-118">Utilisez la `snap install` commande pour installer un package du kit de développement logiciel (SDK) .net.</span><span class="sxs-lookup"><span data-stu-id="c69e2-118">Use the `snap install` command to install a .NET SDK snap package.</span></span> <span data-ttu-id="c69e2-119">Utilisez le `--channel` paramètre pour indiquer la version à installer.</span><span class="sxs-lookup"><span data-stu-id="c69e2-119">Use the `--channel` parameter to indicate which version to install.</span></span> <span data-ttu-id="c69e2-120">Si ce paramètre est omis, `latest/stable` est utilisé.</span><span class="sxs-lookup"><span data-stu-id="c69e2-120">If this parameter is omitted, `latest/stable` is used.</span></span> <span data-ttu-id="c69e2-121">Dans cet exemple, `5.0` est spécifié :</span><span class="sxs-lookup"><span data-stu-id="c69e2-121">In this example, `5.0` is specified:</span></span>

```bash
sudo snap install dotnet-sdk --classic --channel=5.0
```

<span data-ttu-id="c69e2-122">Ensuite, inscrivez la `dotnet` commande pour le système à l’aide de la `snap alias` commande :</span><span class="sxs-lookup"><span data-stu-id="c69e2-122">Next, register the `dotnet` command for the system with the `snap alias` command:</span></span>

```bash
sudo snap alias dotnet-sdk.dotnet dotnet
```

<span data-ttu-id="c69e2-123">Cette commande est au format : `sudo snap alias {package}.{command} {alias}` .</span><span class="sxs-lookup"><span data-stu-id="c69e2-123">This command is formatted as: `sudo snap alias {package}.{command} {alias}`.</span></span> <span data-ttu-id="c69e2-124">Vous pouvez choisir n’importe quel `{alias}` nom.</span><span class="sxs-lookup"><span data-stu-id="c69e2-124">You can choose any `{alias}` name you would like.</span></span> <span data-ttu-id="c69e2-125">Par exemple, vous pouvez nommer la commande après la version spécifique installée par le composant logiciel enfichable : `sudo snap alias dotnet-sdk.dotnet dotnet50` .</span><span class="sxs-lookup"><span data-stu-id="c69e2-125">For example, you could name the command after the specific version installed by snap: `sudo snap alias dotnet-sdk.dotnet dotnet50`.</span></span> <span data-ttu-id="c69e2-126">Lorsque vous utilisez la commande `dotnet50` , vous appellerez cette version spécifique de .net.</span><span class="sxs-lookup"><span data-stu-id="c69e2-126">When you use the command `dotnet50`, you'll invoke this specific version of .NET.</span></span> <span data-ttu-id="c69e2-127">Mais cela n’est pas compatible avec la plupart des didacticiels et des exemples, car ils attendent qu’une `dotnet` commande soit disponible.</span><span class="sxs-lookup"><span data-stu-id="c69e2-127">But this is incompatible with most tutorials and examples as they expect a `dotnet` command to be available.</span></span>

### <a name="install-the-runtime"></a><span data-ttu-id="c69e2-128">Installer le runtime</span><span class="sxs-lookup"><span data-stu-id="c69e2-128">Install the runtime</span></span>

<span data-ttu-id="c69e2-129">Les packages Snap pour le Runtime .NET Core sont publiés sous leur propre identificateur de package.</span><span class="sxs-lookup"><span data-stu-id="c69e2-129">Snap packages for .NET Core Runtime are each published under their own package identifier.</span></span> <span data-ttu-id="c69e2-130">Le tableau suivant répertorie les identificateurs de package :</span><span class="sxs-lookup"><span data-stu-id="c69e2-130">The following table lists the package identifiers:</span></span>

| <span data-ttu-id="c69e2-131">Version de .NET</span><span class="sxs-lookup"><span data-stu-id="c69e2-131">.NET version</span></span>      | <span data-ttu-id="c69e2-132">Package d’alignement</span><span class="sxs-lookup"><span data-stu-id="c69e2-132">Snap package</span></span>        |
|-------------------|---------------------|
| <span data-ttu-id="c69e2-133">5.0</span><span class="sxs-lookup"><span data-stu-id="c69e2-133">5.0</span></span>               | `dotnet-runtime-50` |
| <span data-ttu-id="c69e2-134">3,1 (LTS)</span><span class="sxs-lookup"><span data-stu-id="c69e2-134">3.1 (LTS)</span></span>         | `dotnet-runtime-31` |
| <span data-ttu-id="c69e2-135">3.0</span><span class="sxs-lookup"><span data-stu-id="c69e2-135">3.0</span></span>               | `dotnet-runtime-30` |
| <span data-ttu-id="c69e2-136">2.2</span><span class="sxs-lookup"><span data-stu-id="c69e2-136">2.2</span></span>               | `dotnet-runtime-22` |
| <span data-ttu-id="c69e2-137">2,1 (LTS)</span><span class="sxs-lookup"><span data-stu-id="c69e2-137">2.1 (LTS)</span></span>         | `dotnet-runtime-21` |

<span data-ttu-id="c69e2-138">Utilisez la `snap install` commande pour installer un package Snap .NET Runtime.</span><span class="sxs-lookup"><span data-stu-id="c69e2-138">Use the `snap install` command to install a .NET Runtime snap package.</span></span> <span data-ttu-id="c69e2-139">Dans cet exemple, .NET 5,0 est installé :</span><span class="sxs-lookup"><span data-stu-id="c69e2-139">In this example, .NET 5.0 is installed:</span></span>

```bash
sudo snap install dotnet-runtime-50 --classic
```

<span data-ttu-id="c69e2-140">Ensuite, inscrivez la `dotnet` commande pour le système à l’aide de la `snap alias` commande :</span><span class="sxs-lookup"><span data-stu-id="c69e2-140">Next, register the `dotnet` command for the system with the `snap alias` command:</span></span>

```bash
sudo snap alias dotnet-runtime-50.dotnet dotnet
```

<span data-ttu-id="c69e2-141">Cette commande est au format : `sudo snap alias {package}.{command} {alias}` .</span><span class="sxs-lookup"><span data-stu-id="c69e2-141">This command is formatted as: `sudo snap alias {package}.{command} {alias}`.</span></span> <span data-ttu-id="c69e2-142">Vous pouvez choisir n’importe quel `{alias}` nom.</span><span class="sxs-lookup"><span data-stu-id="c69e2-142">You can choose any `{alias}` name you would like.</span></span> <span data-ttu-id="c69e2-143">Par exemple, vous pouvez nommer la commande après la version spécifique installée par le composant logiciel enfichable : `sudo snap alias dotnet-runtime-50.dotnet dotnet50` .</span><span class="sxs-lookup"><span data-stu-id="c69e2-143">For example, you could name the command after the specific version installed by snap: `sudo snap alias dotnet-runtime-50.dotnet dotnet50`.</span></span> <span data-ttu-id="c69e2-144">Lorsque vous utilisez la commande `dotnet50` , vous appellerez cette version spécifique de .net.</span><span class="sxs-lookup"><span data-stu-id="c69e2-144">When you use the command `dotnet50`, you'll invoke this specific version of .NET.</span></span> <span data-ttu-id="c69e2-145">Mais cela n’est pas compatible avec la plupart des didacticiels et des exemples, car ils attendent qu’une `dotnet` commande soit disponible.</span><span class="sxs-lookup"><span data-stu-id="c69e2-145">But this is incompatible with most tutorials and examples as they expect a `dotnet` command to be available.</span></span>

### <a name="ssl-certificate-errors"></a><span data-ttu-id="c69e2-146">Erreurs de certificat SSL</span><span class="sxs-lookup"><span data-stu-id="c69e2-146">SSL Certificate errors</span></span>

<span data-ttu-id="c69e2-147">Lorsque .NET est installé par le biais de l’option Snap, il est possible que sur certains distributions les certificats SSL .NET soient introuvables et que vous receviez un message d’erreur semblable au suivant pendant `restore` :</span><span class="sxs-lookup"><span data-stu-id="c69e2-147">When .NET is installed through Snap, it's possible that on some distros the .NET SSL certificates may not be found and you may receive an error similar to the following during `restore`:</span></span>

```bash
Processing post-creation actions...
Running 'dotnet restore' on /home/myhome/test/test.csproj...
  Restoring packages for /home/myhome/test/test.csproj...
/snap/dotnet-sdk/27/sdk/2.2.103/NuGet.targets(114,5): error : Unable to load the service index for source https://api.nuget.org/v3/index.json. [/home/myhome/test/test.csproj]
/snap/dotnet-sdk/27/sdk/2.2.103/NuGet.targets(114,5): error :   The SSL connection could not be established, see inner exception. [/home/myhome/test/test.csproj]
/snap/dotnet-sdk/27/sdk/2.2.103/NuGet.targets(114,5): error :   The remote certificate is invalid according to the validation procedure. [/home/myhome/test/test.csproj]
```

<span data-ttu-id="c69e2-148">Pour résoudre ce problème, définissez quelques variables environnement :</span><span class="sxs-lookup"><span data-stu-id="c69e2-148">To resolve this issue, set a few enviornment variables:</span></span>

```bash
export SSL_CERT_FILE=[path-to-certificate-file]
export SSL_CERT_DIR=/dev/null
```

<span data-ttu-id="c69e2-149">L’emplacement du certificat varie selon le distribution.</span><span class="sxs-lookup"><span data-stu-id="c69e2-149">The certificate location will vary by distro.</span></span> <span data-ttu-id="c69e2-150">Voici les emplacements du distributions où nous avons rencontré le problème.</span><span class="sxs-lookup"><span data-stu-id="c69e2-150">Here are the locations for the distros where we have experienced the issue.</span></span>

* <span data-ttu-id="c69e2-151">Fedora `/etc/pki/ca-trust/extracted/pem/tls-ca-bundle.pem`</span><span class="sxs-lookup"><span data-stu-id="c69e2-151">Fedora - `/etc/pki/ca-trust/extracted/pem/tls-ca-bundle.pem`</span></span>
* <span data-ttu-id="c69e2-152">OpenSUSE `/etc/ssl/ca-bundle.pem`</span><span class="sxs-lookup"><span data-stu-id="c69e2-152">OpenSUSE - `/etc/ssl/ca-bundle.pem`</span></span>
* <span data-ttu-id="c69e2-153">Solus - `/etc/ssl/certs/ca-certificates.crt`</span><span class="sxs-lookup"><span data-stu-id="c69e2-153">Solus - `/etc/ssl/certs/ca-certificates.crt`</span></span>
