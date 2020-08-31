---
ms.openlocfilehash: 5e77b7bd73c09e061a94a29703cf5286814d1ebb
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84602914"
---

[.NET Core est disponible dans le magasin d’instantanés.](https://snapcraft.io/dotnet-sdk)

Un Snap est un bundle d’une application et de ses dépendances qui fonctionnent sans modification sur de nombreuses distributions Linux différentes. Les instantanés sont détectables et installables à partir du magasin d’instantanés. Pour plus d’informations sur SNAP, consultez [prise en main du composant logiciel enfichable](https://snapcraft.io/docs/getting-started).

Seules les versions prises en charge de .NET Core sont disponibles par le biais de l’option Snap.

### <a name="install-the-sdk"></a>Installer le Kit de développement logiciel (SDK)

Les packages d’alignement pour kit SDK .NET Core sont tous publiés sous le même identificateur : `dotnet-sdk` . Une version spécifique du kit de développement logiciel (SDK) peut être installée en spécifiant le canal. Le kit de développement logiciel (SDK) comprend le runtime de cofacette. Le tableau suivant répertorie les canaux :

| Version .NET Core | Package d’alignement             |
|-------------------|--------------------------|
| 3,1 (LTS)         | `3.1` ou `latest/stable` |
| 2,1 (LTS)         | `2.1`                    |
| Version préliminaire de .NET 5,0  | `5.0/beta`               |

Utilisez la `snap install` commande pour installer un package kit SDK .net Core Snap. Utilisez le `--channel` paramètre pour indiquer la version à installer. Si ce paramètre est omis, `latest/stable` est utilisé. Dans cet exemple, `3.1` est spécifié :

```bash
sudo snap install dotnet-sdk --classic --channel=3.1
```

Ensuite, inscrivez la `dotnet` commande pour le système à l’aide de la `snap alias` commande :

```bash
sudo snap alias dotnet-sdk.dotnet dotnet
```

Cette commande est au format : `sudo snap alias {package}.{command} {alias}` . Vous pouvez choisir n’importe quel `{alias}` nom. Par exemple, vous pouvez nommer la commande après la version spécifique installée par le composant logiciel enfichable : `sudo snap alias dotnet-sdk.dotnet dotnet31` . Lorsque vous utilisez la commande `dotnet31` , vous appellerez cette version spécifique de .net. Mais cela n’est pas compatible avec la plupart des didacticiels et des exemples, car ils attendent qu’une `dotnet` commande soit disponible.

### <a name="install-the-runtime"></a>Installer le runtime

Les packages Snap pour le Runtime .NET Core sont publiés sous leur propre identificateur de package. Le tableau suivant répertorie les identificateurs de package :

| Version .NET Core | Package d’alignement        |
|-------------------|---------------------|
| 3,1 (LTS)         | `dotnet-runtime-31` |
| 3.0               | `dotnet-runtime-30` |
| 2,2               | `dotnet-runtime-22` |
| 2,1 (LTS)         | `dotnet-runtime-21` |

Utilisez la `snap install` commande pour installer un package de composant logiciel enfichable du Runtime .net core. Dans cet exemple, .NET Core 3,1 est installé :

```bash
sudo snap install dotnet-runtime-31 --classic
```

Ensuite, inscrivez la `dotnet` commande pour le système à l’aide de la `snap alias` commande :

```bash
sudo snap alias dotnet-runtime-31.dotnet dotnet
```

Cette commande est au format : `sudo snap alias {package}.{command} {alias}` . Vous pouvez choisir n’importe quel `{alias}` nom. Par exemple, vous pouvez nommer la commande après la version spécifique installée par le composant logiciel enfichable : `sudo snap alias dotnet-runtime-31.dotnet dotnet31` . Lorsque vous utilisez la commande `dotnet31` , vous appellerez cette version spécifique de .net. Mais cela n’est pas compatible avec la plupart des didacticiels et des exemples, car ils attendent qu’une `dotnet` commande soit disponible.

### <a name="ssl-certificate-errors"></a>Erreurs de certificat SSL

Lorsque .NET est installé par le biais de l’option Snap, il est possible que sur certains distributions les certificats SSL .NET soient introuvables et que vous receviez un message d’erreur semblable au suivant pendant `restore` :

```bash
Processing post-creation actions...
Running 'dotnet restore' on /home/myhome/test/test.csproj...
  Restoring packages for /home/myhome/test/test.csproj...
/snap/dotnet-sdk/27/sdk/2.2.103/NuGet.targets(114,5): error : Unable to load the service index for source https://api.nuget.org/v3/index.json. [/home/myhome/test/test.csproj]
/snap/dotnet-sdk/27/sdk/2.2.103/NuGet.targets(114,5): error :   The SSL connection could not be established, see inner exception. [/home/myhome/test/test.csproj]
/snap/dotnet-sdk/27/sdk/2.2.103/NuGet.targets(114,5): error :   The remote certificate is invalid according to the validation procedure. [/home/myhome/test/test.csproj]
```

Pour résoudre ce problème, définissez quelques variables environnement :

```bash
export SSL_CERT_FILE=[path-to-certificate-file]
export SSL_CERT_DIR=/dev/null
```

L’emplacement du certificat varie selon le distribution. Voici les emplacements du distributions où nous avons rencontré le problème.

* Fedora `/etc/pki/ca-trust/extracted/pem/tls-ca-bundle.pem`
* OpenSUSE `/etc/ssl/ca-bundle.pem`
* Solus - `/etc/ssl/certs/ca-certificates.crt`
