---
title: Catalogue d’identificateurs de runtime (RID) .NET Core
description: Découvrez plus en détails l’identificateur de runtime (RID) et la façon dont les identificateurs RID sont utilisés dans .NET Core.
ms.date: 02/22/2019
ms.openlocfilehash: feb19632f16a047ecfb2dcb697a9b837824a1929
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "77451731"
---
# <a name="net-core-rid-catalog"></a>Catalogue RID .NET Core

RID est l’abréviation de *Runtime IDentifier* (identificateur de runtime). Les valeurs RID sont utilisées pour identifier les plateformes cibles où l’application s’exécute.
Elles sont utilisées par les packages .NET pour représenter des ressources spécifiques à une plateforme dans les packages NuGet. Les valeurs suivantes sont des exemples d’identificateurs RID : `linux-x64`, `ubuntu.14.04-x64`, `win7-x64` ou `osx.10.12-x64`.
Pour les packages ayant des dépendances natives, les RID désignent les plateformes sur lesquelles ils peuvent être restaurés.

Un seul RID peut être défini dans l’élément `<RuntimeIdentifier>` de votre fichier projet. Les RID multiples peuvent être définis sous forme de liste de valeurs séparées par des points-virgules dans l’élément `<RuntimeIdentifiers>` du fichier projet. Ils sont également utilisés par le biais de l’option `--runtime` avec les [commandes de l’interface CLI .NET Core](./tools/index.md) suivantes :

- [dotnet build](./tools/dotnet-build.md)
- [dotnet clean](./tools/dotnet-clean.md)
- [dotnet pack](./tools/dotnet-pack.md)
- [dotnet publish](./tools/dotnet-publish.md)
- [dotnet restore](./tools/dotnet-restore.md)
- [dotnet run](./tools/dotnet-run.md)
- [dotnet store](./tools/dotnet-store.md)

Les RID qui représentent des systèmes d’exploitation concrets suivent généralement ce modèle : `[os].[version]-[architecture]-[additional qualifiers]` où :

- `[os]` représente le moniker du système d’exploitation/de la plateforme. Par exemple : `ubuntu`.

- `[version]` représente la version du système d’exploitation sous la forme d’un numéro de version (`.`) séparé par un point. Par exemple : `15.10`.

  - La version **ne doit pas** correspondre à des versions marketing, car celles-ci représentent souvent plusieurs versions distinctes du système d’exploitation avec une surface d’exposition variable des API de la plateforme.

- `[architecture]` représente l’architecture de processeur. Par exemple : `x86`, `x64`, `arm` ou `arm64`.

- `[additional qualifiers]` permet de distinguer davantage les plateformes. Par exemple : `aot`.

## <a name="rid-graph"></a>Graphe RID

Le graphe RID ou le graphe de secours du runtime consiste en une liste d’identificateurs RID compatibles entre eux. Les RID sont définis dans le package [Microsoft.NETCore.Platforms](https://www.nuget.org/packages/Microsoft.NETCore.Platforms/). Vous pouvez voir la liste des RID pris en charge et le graphique RID `dotnet/runtime` dans le fichier [*runtime.json,*](https://github.com/dotnet/runtime/blob/master/src/libraries/pkg/Microsoft.NETCore.Platforms/runtime.json) qui se trouve au référentiel. Dans ce fichier, vous pouvez voir que tous les RID, sauf celui de base, contiennent une instruction `"#import"`. Ces instructions indiquent des RID compatibles.

Lorsque NuGet restaure des packages, il tente de trouver une correspondance exacte pour le runtime spécifié.
Si aucune correspondance exacte n’est trouvée, NuGet remonte le graphe jusqu'à ce qu’il trouve le système compatible le plus proche selon le graphe RID.

L’exemple suivant est l’entrée réelle pour le RID `osx.10.12-x64` :

```json
"osx.10.12-x64": {
    "#import": [ "osx.10.12", "osx.10.11-x64" ]
}
```

Le RID ci-dessus indique que `osx.10.12-x64` importe `osx.10.11-x64`. Donc, lorsque NuGet restaure des packages, il tente de trouver une correspondance exacte pour `osx.10.12-x64` dans le package. Si NuGet ne trouve pas le runtime spécifique, il peut restaurer des packages qui spécifient des runtimes `osx.10.11-x64`, par exemple.

L’exemple suivant illustre un graphe RID légèrement plus grand également défini dans le fichier *runtime.json* :

```
    win7-x64    win7-x86
       |   \   /    |
       |   win7     |
       |     |      |
    win-x64  |  win-x86
          \  |  /
            win
             |
            any
```

Tous les RID sont finalement remappés au RID `any` racine.

Lorsque vous utilisez les RID, il existe quelques remarques que vous devez garder à l’esprit :

- Les RID sont des **chaînes opaques** qui doivent être considérées comme des boîtes noires.
- Ne générez pas les RID par programme.
- Utilisez des RID déjà définis pour la plateforme.
- Les RID se devant d’être spécifiques, ne déduisez rien de leur valeur réelle.

## <a name="using-rids"></a>Utilisation de RID

Pour utiliser des RID, vous devez savoir lesquels existent. De nouvelles valeurs sont régulièrement ajoutées à la plateforme.
Pour la version la plus récente et complète, `dotnet/runtime` consultez le fichier [runtime.json](https://github.com/dotnet/runtime/blob/master/src/libraries/pkg/Microsoft.NETCore.Platforms/runtime.json) sur le référentiel.

Le kit SDK .NET Core 2.0 introduit le concept d’identificateurs RID portables. Il s’agit de nouvelles valeurs ajoutées au graphe RID qui ne sont liées à aucune version ou distribution du système d’exploitation spécifique. Elles sont recommandées avec .NET Core 2.0 et les versions ultérieures. Elles sont particulièrement utiles pour gérer plusieurs distributions Linux, car la plupart des RID de distribution correspondent aux RID portables.

La liste suivante présente un petit sous-ensemble des RID les plus courants utilisés pour chaque système d’exploitation.

## <a name="windows-rids"></a>RID Windows

Seules les valeurs courantes sont présentées. Pour la version la plus récente et complète, `dotnet/runtime` consultez le fichier [runtime.json](https://github.com/dotnet/runtime/blob/master/src/libraries/pkg/Microsoft.NETCore.Platforms/runtime.json) sur le référentiel.

- Portable (.NET Core 2.0 ou versions ultérieures)
  - `win-x64`
  - `win-x86`
  - `win-arm`
  - `win-arm64`
- Windows 7 / Windows Server 2008 R2
  - `win7-x64`
  - `win7-x86`
- Windows 8.1 / Windows Server 2012 R2
  - `win81-x64`
  - `win81-x86`
  - `win81-arm`
- Windows 10 / Windows Server 2016
  - `win10-x64`
  - `win10-x86`
  - `win10-arm`
  - `win10-arm64`

Pour plus d’informations, voir [.NET Core dépendances et exigences](install/dependencies.md?pivots=os-windows).

## <a name="linux-rids"></a>RID Linux

Seules les valeurs courantes sont présentées. Pour la version la plus récente et complète, `dotnet/runtime` consultez le fichier [runtime.json](https://github.com/dotnet/runtime/blob/master/src/libraries/pkg/Microsoft.NETCore.Platforms/runtime.json) sur le référentiel. Les appareils dont la distribution ne figure pas ci-dessous sont susceptibles de fonctionner avec l’un des RID portables. Par exemple, les appareils Raspberry Pi exécutant une distribution Linux non listée peuvent être ciblés avec `linux-arm`.

- Portable (.NET Core 2.0 ou versions ultérieures)
  - `linux-x64`(La plupart des distributions de bureau comme CentOS, Debian, Fedora, Ubuntu et dérivés)
  - `linux-musl-x64` (distributions légères utilisant [musl](https://wiki.musl-libc.org/projects-using-musl.html), comme Linux Alpine)
  - `linux-arm` (distributions Linux qui s’exécutent sur ARM, comme Raspberry Pi)
- Red Hat Enterprise Linux
  - `rhel-x64` (remplacé par `linux-x64` pour RHEL après la version 6)
  - `rhel.6-x64` (.NET Core 2.0 ou versions ultérieures)
- Tizen (.NET Core 2.0 ou versions ultérieures)
  - `tizen`
  - `tizen.4.0.0`
  - `tizen.5.0.0`

Pour plus d’informations, voir [.NET Core dépendances et exigences](install/dependencies.md?pivots=os-linux).

## <a name="macos-rids"></a>RID macOS

Les RID macOS utilisent l’ancien logo « OSX ». Seules les valeurs courantes sont présentées. Pour la version la plus récente et complète, `dotnet/runtime` consultez le fichier [runtime.json](https://github.com/dotnet/runtime/blob/master/src/libraries/pkg/Microsoft.NETCore.Platforms/runtime.json) sur le référentiel.

- Portable (.NET Core 2.0 ou versions ultérieures)
  - `osx-x64` (la version minimale du système d’exploitation est macOS 10.12 Sierra)
- macOS 10.10  Yosemite
  - `osx.10.10-x64`
- macOS 10.11 El Capitan
  - `osx.10.11-x64`
- macOS 10.12 Sierra (.NET Core 1.1 ou versions ultérieures)
  - `osx.10.12-x64`
- macOS 10.13 High Sierra (.NET Core 1.1 ou versions ultérieures)
  - `osx.10.13-x64`
- macOS 10.14 Mojave (.NET Core 1.1 ou versions ultérieures)
  - `osx.10.14-x64`

Pour plus d’informations, voir [.NET Core dépendances et exigences](install/dependencies.md?pivots=os-macos).

## <a name="see-also"></a>Voir aussi

- [ID du runtime](https://github.com/dotnet/runtime/blob/master/src/libraries/pkg/Microsoft.NETCore.Platforms/readme.md)
