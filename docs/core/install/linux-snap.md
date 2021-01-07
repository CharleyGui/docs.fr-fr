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
# <a name="install-the-net-sdk-or-the-net-runtime-with-snap"></a>Installer le kit de développement logiciel (SDK) .NET ou le Runtime .NET avec Snap

Utilisez un package d’installation pour installer le kit de développement logiciel (SDK) .NET ou le Runtime .NET. Les instantanés sont une excellente alternative au gestionnaire de package intégré à votre distribution Linux. Cet article explique comment installer .NET via le [composant logiciel enfichable](https://snapcraft.io/dotnet-sdk).

Un Snap est un bundle d’une application et de ses dépendances qui fonctionnent sans modification sur de nombreuses distributions Linux différentes. Les instantanés sont détectables et installables à partir du magasin d’instantanés. Pour plus d’informations sur SNAP, consultez [prise en main du composant logiciel enfichable](https://snapcraft.io/docs/getting-started).

> [!CAUTION]
> Les packages Snap ne sont pas pris en charge dans WSL2 sur Windows 10. Vous pouvez également utiliser le [ `dotnet-install` script](linux-scripted-manual.md#scripted-install) ou le gestionnaire de package pour la distribution WSL2 particulière. Ce n’est pas recommandé, mais vous pouvez essayer d’activer Snap avec une [solution de contournement non prise en charge à partir des forums snapcraft](https://forum.snapcraft.io/t/running-snaps-on-wsl2-insiders-only-for-now/13033).

## <a name="net-releases"></a>Versions de .NET

✔️ seules les versions prises en charge du kit de développement logiciel (SDK) .NET sont disponibles via l’option Snap. Toutes les versions du Runtime .NET sont disponibles via le composant logiciel enfichable à partir de la version 2,1. Le tableau suivant répertorie les versions de .NET (et .NET Core) :

| ✔️ pris en charge | ❌ Pris en charge |
|-------------|---------------|
| 5.0         | 3.0           |
| 3,1 (LTS)   | 2.2           |
| 2,1 (LTS)   | 2,0           |
|             | 1,1           |
|             | 1.0           |

Pour plus d’informations sur le cycle de vie des versions de .NET, consultez [stratégie de support .net Core et .net 5](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).

## <a name="sdk-or-runtime"></a>SDK ou Runtime

[!INCLUDE [linux-intro-sdk-vs-runtime](includes/linux-intro-sdk-vs-runtime.md)]

## <a name="install-the-sdk"></a>Installer le SDK

Les packages Snap pour le kit de développement logiciel (SDK) .NET sont tous publiés sous le même identificateur : `dotnet-sdk` . Une version spécifique du kit de développement logiciel (SDK) peut être installée en spécifiant le canal. Le kit de développement logiciel (SDK) comprend le runtime correspondant. Le tableau suivant répertorie les canaux :

| Version de .NET | Package d’alignement ou canal  |
|--------------|--------------------------|
| 5.0          | `5.0` ou `latest/stable` |
| 3,1 (LTS)    | `3.1` ou `lts/stable`    |
| 2,1 (LTS)    | `2.1`                    |

Utilisez la `snap install` commande pour installer un package du kit de développement logiciel (SDK) .net. Utilisez le `--channel` paramètre pour indiquer la version à installer. Si ce paramètre est omis, `latest/stable` est utilisé. Dans cet exemple, `5.0` est spécifié :

```bash
sudo snap install dotnet-sdk --classic --channel=5.0
```

Ensuite, inscrivez la `dotnet` commande pour le système à l’aide de la `snap alias` commande :

```bash
sudo snap alias dotnet-sdk.dotnet dotnet
```

Cette commande est au format : `sudo snap alias {package}.{command} {alias}` . Vous pouvez choisir n’importe quel `{alias}` nom. Par exemple, vous pouvez nommer la commande après la version spécifique installée par le composant logiciel enfichable : `sudo snap alias dotnet-sdk.dotnet dotnet50` . Lorsque vous utilisez la commande `dotnet50` , vous appellerez cette version spécifique de .net. Toutefois, le choix d’un alias différent est incompatible avec la plupart des didacticiels et des exemples, car ils attendent qu’une `dotnet` commande soit utilisée.

## <a name="install-the-runtime"></a>Installer le runtime

Les packages Snap pour le Runtime .NET sont publiés sous leur propre identificateur de package. Le tableau suivant répertorie les identificateurs de package :

| Version de .NET      | Package d’alignement        |
|-------------------|---------------------|
| 5.0               | `dotnet-runtime-50` |
| 3,1 (LTS)         | `dotnet-runtime-31` |
| 3.0               | `dotnet-runtime-30` |
| 2.2               | `dotnet-runtime-22` |
| 2,1 (LTS)         | `dotnet-runtime-21` |

Utilisez la `snap install` commande pour installer un package Snap .NET Runtime. Dans cet exemple, .NET 5,0 est installé :

```bash
sudo snap install dotnet-runtime-50 --classic
```

Ensuite, inscrivez la `dotnet` commande pour le système à l’aide de la `snap alias` commande :

```bash
sudo snap alias dotnet-runtime-50.dotnet dotnet
```

La commande est mise en forme de la façon suivante : `sudo snap alias {package}.{command} {alias}` . Vous pouvez choisir n’importe quel `{alias}` nom. Par exemple, vous pouvez nommer la commande après la version spécifique installée par le composant logiciel enfichable : `sudo snap alias dotnet-runtime-50.dotnet dotnet50` . Quand vous utilisez la commande `dotnet50` , vous appelez une version spécifique de .net. Toutefois, le choix d’un alias différent est incompatible avec la plupart des didacticiels et des exemples, car ils attendent qu’une `dotnet` commande soit disponible.

## <a name="tlsssl-certificate-errors"></a>Erreurs de certificat TLS/SSL

Lorsque .NET est installé via le composant logiciel enfichable, il est possible que sur certains distributions les certificats TLS/SSL .NET soient introuvables et que vous receviez une erreur lors de l’opération `restore` :

```bash
Processing post-creation actions...
Running 'dotnet restore' on /home/myhome/test/test.csproj...
  Restoring packages for /home/myhome/test/test.csproj...
/snap/dotnet-sdk/27/sdk/2.2.103/NuGet.targets(114,5): error : Unable to load the service index for source https://api.nuget.org/v3/index.json. [/home/myhome/test/test.csproj]
/snap/dotnet-sdk/27/sdk/2.2.103/NuGet.targets(114,5): error :   The SSL connection could not be established, see inner exception. [/home/myhome/test/test.csproj]
/snap/dotnet-sdk/27/sdk/2.2.103/NuGet.targets(114,5): error :   The remote certificate is invalid according to the validation procedure. [/home/myhome/test/test.csproj]
```

Pour résoudre ce problème, définissez quelques variables d’environnement :

```bash
export SSL_CERT_FILE=[path-to-certificate-file]
export SSL_CERT_DIR=/dev/null
```

L’emplacement du certificat varie selon le distribution. Voici les emplacements du distributions où le problème a été rencontré.

| Distribution | Localisation                                            |
|--------------|-----------------------------------------------------|
| **Fedora**   | `/etc/pki/ca-trust/extracted/pem/tls-ca-bundle.pem` |
| **OpenSUSE** | `/etc/ssl/ca-bundle.pem`                            |
| **Solus**    | `/etc/ssl/certs/ca-certificates.crt`                |

## <a name="next-steps"></a>Étapes suivantes

- [Comment activer la saisie semi-automatique via la touche TAB pour .NET CLI](../tools/enable-tab-autocomplete.md)
- [Didacticiel : créer une application console avec le kit de développement logiciel (SDK) .NET à l’aide de Visual Studio Code](../tutorials/with-visual-studio-code.md)
