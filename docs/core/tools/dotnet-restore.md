---
title: Commande dotnet restore
description: Découvrez comment restaurer les dépendances et les outils spécifiques du projet avec la commande dotnet restore.
ms.date: 02/27/2020
ms.openlocfilehash: f49f0cda4424a4cc54ab7d4d4c6f729919dc7e60
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463432"
---
# <a name="dotnet-restore"></a>dotnet restore

**Cet article s’applique à:** ✔️ .NET Core 2.1 SDK et les versions ultérieures

## <a name="name"></a>Nom

`dotnet restore` : Restaure les dépendances et les outils d’un projet.

## <a name="synopsis"></a>Synopsis

```dotnetcli
dotnet restore [<ROOT>] [--configfile <FILE>] [--disable-parallel]
    [-f|--force] [--force-evaluate] [--ignore-failed-sources]
    [--interactive] [--lock-file-path <LOCK_FILE_PATH>] [--locked-mode]
    [--no-cache] [--no-dependencies] [--packages <PACKAGES_DIRECTORY>]
    [-r|--runtime <RUNTIME_IDENTIFIER>] [-s|--source <SOURCE>]
    [--use-lockfile] [-v|--verbosity <LEVEL>]

dotnet restore -h|--help
```

## <a name="description"></a>Description

La commande `dotnet restore` utilise NuGet pour restaurer les dépendances, ainsi que les outils spécifiques aux projets qui sont spécifiés dans le fichier projet. Par défaut, la restauration des dépendances et celle des outils sont exécutées en parallèle.

Pour restaurer les dépendances, NuGet a besoin des flux où sont situés les packages. Les flux sont généralement fournis via le fichier de configuration *nuget.config*. Un fichier de configuration par défaut est fourni lors de l’installation du SDK .NET Core. Vous pouvez spécifier d’autres flux en créant votre propre fichier *nuget.config* dans le répertoire du projet. Vous pouvez remplacer les flux *nuget.config* avec `-s` l’option.

Pour les dépendances, vous pouvez spécifier l’emplacement des packages restaurés pendant l’opération de restauration à l’aide de l’argument `--packages`. Si aucune valeur n’est spécifiée, le cache du package NuGet par défaut est utilisé. Il se trouve dans le répertoire `.nuget/packages`, situé dans le répertoire de base de l’utilisateur, sur tous les systèmes d’exploitation. Par exemple, */home/user1* sur Linux ou *C:\Users\user1* sur Windows.

Pour les outils spécifiques au projet, `dotnet restore` commence par restaurer le package dans lequel l’outil est empaqueté, puis il restaure les dépendances de l’outil, comme spécifié dans son fichier projet.

### <a name="nugetconfig-differences"></a>Différences dans nuget.config

Le comportement de la commande `dotnet restore` est affecté par les paramètres du fichier *nuget.config*, s’il est présent. Par exemple, si vous définissez `globalPackagesFolder` dans *nuget.config*, les packages NuGet restaurés sont placés dans le dossier spécifié. Cette méthode permet également de spécifier l’option `--packages` sur la commande `dotnet restore`. Pour plus d’informations, consultez [Informations de référence sur nuget.config](/nuget/schema/nuget-config-file).

Trois paramètres spécifiques sont ignorés par `dotnet restore` :

- [bindingRedirects](/nuget/schema/nuget-config-file#bindingredirects-section)

  Les redirections de liaison ne fonctionnent pas avec les éléments `<PackageReference>` et .NET Core prend en charge seulement les éléments `<PackageReference>` pour les packages NuGet.

- [Solution](/nuget/schema/nuget-config-file#solution-section)

  Ce paramètre est spécifique à Visual Studio et ne s’applique pas à .NET Core. .NET Core n’utilise pas de fichier `packages.config` et utilise à la place des éléments `<PackageReference>` pour les packages NuGet.

- [trustedSigners](/nuget/schema/nuget-config-file#trustedsigners-section)

  Ce paramètre n’est pas applicable, car [NuGet ne prend pas encore en charge la vérification multiplateforme](https://github.com/NuGet/Home/issues/7939) des packages approuvés.

## <a name="implicit-restore"></a>Restauration implicite

La `dotnet restore` commande est exécutée implicitement si nécessaire lorsque vous exécutez les commandes suivantes :

- [`dotnet new`](dotnet-new.md)
- [`dotnet build`](dotnet-build.md)
- [`dotnet build-server`](dotnet-build-server.md)
- [`dotnet run`](dotnet-run.md)
- [`dotnet test`](dotnet-test.md)
- [`dotnet publish`](dotnet-publish.md)
- [`dotnet pack`](dotnet-pack.md)

Dans la plupart des cas, vous `dotnet restore` n’avez pas besoin d’utiliser explicitement la commande.

Parfois, il peut s’avérer fastidieux d’exécuter `dotnet restore` implicitement. Par exemple, certains systèmes automatisés, comme les systèmes de génération, doivent appeler explicitement `dotnet restore` pour contrôler quand la restauration a lieu afin de pouvoir contrôler l’utilisation du réseau. Pour empêcher l’exécution implicite de `dotnet restore`, vous pouvez utiliser l’indicateur `--no-restore` avec l’une de ces commandes afin de désactiver la restauration implicite.

## <a name="arguments"></a>Arguments

- **`ROOT`**

  Chemin facultatif du fichier projet à restaurer.

## <a name="options"></a>Options

- **`--configfile <FILE>`**

  Fichier de configuration NuGet (*nuget.config*) à utiliser pour l’opération de restauration.

- **`--disable-parallel`**

  Désactive la restauration de plusieurs projets en parallèle.

- **`--force`**

  Force la résolution de toutes les dépendances même si la dernière restauration a réussi. Définir cet indicateur revient à supprimer le fichier *project.assets.json*.

- **`--force-evaluate`**

  Les forces restaurent pour réévaluer toutes les dépendances même si un fichier de verrouillage existe déjà.

- **`-h|--help`**

  Affiche une aide brève pour la commande.

- **`--ignore-failed-sources`**

  N’avertit en cas d’échec des sources que si des packages répondent aux exigences de versions.

- **`--interactive`**

  Permet à la commande de s’arrêter et d’attendre une saisie ou une action de l’utilisateur (par exemple, s’identifier). Depuis .NET Core 2.1.400.

- **`--lock-file-path <LOCK_FILE_PATH>`**

  Emplacement de sortie où le fichier de verrouillage du projet est écrit. Par défaut, il *s’agit de PROJECT_ROOT-packages.lock.json*.

- **`--locked-mode`**

  N’autorisez pas la mise à jour du fichier de verrouillage du projet.

- **`--no-cache`**

  Spécifie de ne pas mettre en cache les packages et les requêtes HTTP.

- **`--no-dependencies`**

  En cas de restauration d’un projet avec des références entre projets (P2P), restaure le projet racine et non les références.

- **`--packages <PACKAGES_DIRECTORY>`**

  Spécifie le répertoire des packages restaurés.

- **`-r|--runtime <RUNTIME_IDENTIFIER>`**

  Spécifie un runtime pour la restauration du package. Cela permet de restaurer les packages des runtimes qui ne sont pas explicitement listés dans la balise `<RuntimeIdentifiers>` du fichier *.csproj*. Pour connaître les identificateurs de runtime, consultez le [catalogue des identificateurs de runtime](../rid-catalog.md). Fournissez plusieurs identificateurs de runtime en spécifiant cette option plusieurs fois.

- **`-s|--source <SOURCE>`**

  Spécifie la source de package NuGet à utiliser pendant l’opération de restauration. Ce paramètre remplace toutes les sources spécifiées dans les fichiers *nuget.config*. Vous pouvez spécifier plusieurs sources en spécifiant cette option plusieurs fois.

- **`--use-lockfile`**

  Permet de générer et d’utiliser le fichier de verrouillage du projet lors de la restauration.

- **`-v|--verbosity <LEVEL>`**

  Définit le niveau de détail de la commande. Les valeurs autorisées sont `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` et `diag[nostic]`. La valeur par défaut est `minimal`.

## <a name="examples"></a>Exemples

- Restaurez des dépendances et des outils pour le projet se trouvant dans le répertoire actif :

  ```dotnetcli
  dotnet restore
  ```

- Restaurer les dépendances et `app1` les outils du projet trouvé dans le chemin donné :

  ```dotnetcli
  dotnet restore ~/projects/app1/app1.csproj
  ```

- Restaurer les dépendances et les outils du projet dans l’annuaire actuel en utilisant le chemin de fichier fourni comme source :

  ```dotnetcli
  dotnet restore -s c:\packages\mypackages
  ```

- Restaurer les dépendances et les outils du projet dans l’annuaire actuel en utilisant les deux voies de fichiers fournies comme sources :

  ```dotnetcli
  dotnet restore -s c:\packages\mypackages -s c:\packages\myotherpackages
  ```

- Restaurer les dépendances et les outils du projet dans l’annuaire actuel montrant une sortie détaillée :

  ```dotnetcli
  dotnet restore --verbosity detailed
  ```
