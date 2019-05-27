---
title: Commande dotnet new
description: La commande dotnet new crée des projets .NET Core basés sur le modèle spécifié.
ms.date: 05/06/2019
ms.openlocfilehash: f8bc8cb59ae6e421f4e9bd05925376399939056d
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2019
ms.locfileid: "65878314"
---
# <a name="dotnet-new"></a>dotnet new

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>Name

`dotnet new` : crée un projet, un fichier de configuration ou une solution en fonction du modèle spécifié.

## <a name="synopsis"></a>Résumé

# <a name="net-core-22tabnetcore22"></a>[.NET Core 2.2](#tab/netcore22)

```console
dotnet new <TEMPLATE> [--dry-run] [--force] [-i|--install] [-lang|--language] [-n|--name] [--nuget-source] [-o|--output] [-u|--uninstall] [Template options]
dotnet new <TEMPLATE> [-l|--list] [--type]
dotnet new [-h|--help]
```

# <a name="net-core-21tabnetcore21"></a>[.NET Core 2.1](#tab/netcore21)

```console
dotnet new <TEMPLATE> [--force] [-i|--install] [-lang|--language] [-n|--name] [--nuget-source] [-o|--output] [-u|--uninstall] [Template options]
dotnet new <TEMPLATE> [-l|--list] [--type]
dotnet new [-h|--help]
```

# <a name="net-core-20tabnetcore20"></a>[.NET Core 2.0](#tab/netcore20)

```console
dotnet new <TEMPLATE> [--force] [-i|--install] [-lang|--language] [-n|--name] [-o|--output] [-u|--uninstall] [Template options]
dotnet new <TEMPLATE> [-l|--list] [--type]
dotnet new [-h|--help]
```

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

```console
dotnet new <TEMPLATE> [-lang|--language] [-n|--name] [-o|--output] [-all|--show-all] [-h|--help] [Template options]
dotnet new <TEMPLATE> [-l|--list]
dotnet new [-all|--show-all]
dotnet new [-h|--help]
```

---

## <a name="description"></a>Description

La commande `dotnet new` offre un moyen pratique d’initialiser un projet .NET Core valide.

La commande appelle le [moteur de modèles](https://github.com/dotnet/templating) pour créer les artefacts sur le disque en fonction du modèle et des options spécifiés.

## <a name="arguments"></a>Arguments

`TEMPLATE`

Modèle à instancier quand la commande est appelée. Vous pouvez passer des options spécifiques pour chaque modèle. Pour plus d'informations, consultez [Options de modèle](#template-options).

Si la valeur `TEMPLATE` ne correspond pas exactement au texte des colonnes **Modèles** ou **Nom court**, une comparaison de sous-chaîne est exécutée sur ces deux colonnes.

# <a name="net-core-22tabnetcore22"></a>[.NET Core 2.2](#tab/netcore22)

La commande contient une liste par défaut de modèles. Utilisez `dotnet new -l` pour obtenir une liste des modèles disponibles. Le tableau suivant présente les modèles préinstallés avec le SDK .NET Core 2.2.100. Le langage par défaut pour le modèle est indiqué entre crochets.

| Modèles                                    | Nom court        | Langue     | Balises                                  |
|----------------------------------------------|-------------------|--------------|---------------------------------------|
| Application console                          | `console`         | [C#], F#, VB | Communes/Console                        |
| Bibliothèque de classes                                | `classlib`        | [C#], F#, VB | Communes/Bibliothèque                        |
| Projet de test unitaire                            | `mstest`          | [C#], F#, VB | Test/MSTest                           |
| Projet de test NUnit 3                         | `nunit`           | [C#], F#, VB | Test/NUnit                            |
| Élément de test NUnit 3                            | `nunit-test`      | [C#], F#, VB | Test/NUnit                            |
| Projet de test xUnit                           | `xunit`           | [C#], F#, VB | Test/xUnit                            |
| Page Razor                                   | `page`            | [C#]         | Web/ASP.NET                           |
| ViewImports MVC                              | `viewimports`     | [C#]         | Web/ASP.NET                           |
| ViewStart MVC                                | `viewstart`       | [C#]         | Web/ASP.NET                           |
| ASP.NET Core vide                           | `web`             | [C#], F#     | Web/vides                             |
| Application web ASP.NET Core (Model-View-Controller) | `mvc`             | [C#], F#     | Web/MVC                               |
| Application web ASP.NET Core                         | `webapp`, `razor` | [C#]         | Web/MVC/Razor Pages                   |
| ASP.NET Core avec Angular                    | `angular`         | [C#]         | Web/MVC/SPA                           |
| ASP.NET Core avec React.js                   | `react`           | [C#]         | Web/MVC/SPA                           |
| ASP.NET Core avec React.js et Redux         | `reactredux`      | [C#]         | Web/MVC/SPA                           |
| Bibliothèque de classes Razor                          | `razorclasslib`   | [C#]         | Web/Razor/Library/Bibliothèque de classes Razor |
| API web ASP.NET Core                         | `webapi`          | [C#], F#     | Web/WebAPI                            |
| fichier global.json                             | `globaljson`      |              | Config                                |
| Configuration NuGet                                 | `nugetconfig`     |              | Config                                |
| Configuration Web                                   | `webconfig`       |              | Config                                |
| Fichier solution                                | `sln`             |              | Solution                              |

# <a name="net-core-21tabnetcore21"></a>[.NET Core 2.1](#tab/netcore21)

La commande contient une liste par défaut de modèles. Utilisez `dotnet new -l` pour obtenir une liste des modèles disponibles. Le tableau suivant présente les modèles préinstallés avec le SDK .NET Core 2.1.300. Le langage par défaut pour le modèle est indiqué entre crochets.

| Modèles                                    | Nom court      | Langue     | Balises                                  |
|----------------------------------------------|-----------------|--------------|---------------------------------------|
| Application console                          | `console`       | [C#], F#, VB | Communes/Console                        |
| Bibliothèque de classes                                | `classlib`      | [C#], F#, VB | Communes/Bibliothèque                        |
| Projet de test unitaire                            | `mstest`        | [C#], F#, VB | Test/MSTest                           |
| Projet de test xUnit                           | `xunit`         | [C#], F#, VB | Test/xUnit                            |
| Page Razor                                   | `page`          | [C#]         | Web/ASP.NET                           |
| ViewImports MVC                              | `viewimports`   | [C#]         | Web/ASP.NET                           |
| ViewStart MVC                                | `viewstart`     | [C#]         | Web/ASP.NET                           |
| ASP.NET Core vide                           | `web`           | [C#], F#     | Web/vides                             |
| Application web ASP.NET Core (Model-View-Controller) | `mvc`           | [C#], F#     | Web/MVC                               |
| Application web ASP.NET Core                         | `razor`         | [C#]         | Web/MVC/Razor Pages                   |
| ASP.NET Core avec Angular                    | `angular`       | [C#]         | Web/MVC/SPA                           |
| ASP.NET Core avec React.js                   | `react`         | [C#]         | Web/MVC/SPA                           |
| ASP.NET Core avec React.js et Redux         | `reactredux`    | [C#]         | Web/MVC/SPA                           | 
| Bibliothèque de classes Razor                          | `razorclasslib` | [C#]         | Web/Razor/Library/Bibliothèque de classes Razor |
| API web ASP.NET Core                         | `webapi`        | [C#], F#     | Web/WebAPI                            |
| fichier global.json                             | `globaljson`    |              | Config                                |
| Configuration NuGet                                 | `nugetconfig`   |              | Config                                |
| Configuration Web                                   | `webconfig`     |              | Config                                |
| Fichier solution                                | `sln`           |              | Solution                              |

# <a name="net-core-20tabnetcore20"></a>[.NET Core 2.0](#tab/netcore20)

La commande contient une liste par défaut de modèles. Utilisez `dotnet new -l` pour obtenir une liste des modèles disponibles. Le tableau suivant présente les modèles préinstallés avec le SDK .NET Core 2.0.0. Le langage par défaut pour le modèle est indiqué entre crochets.

| Modèles                                    | Nom court    | Langue     | Balises                |
|----------------------------------------------|---------------|--------------|---------------------|
| Application console                          | `console`     | [C#], F#, VB | Communes/Console      |
| Bibliothèque de classes                                | `classlib`    | [C#], F#, VB | Communes/Bibliothèque      |
| Projet de test unitaire                            | `mstest`      | [C#], F#, VB | Test/MSTest         |
| Projet de test xUnit                           | `xunit`       | [C#], F#, VB | Test/xUnit          |
| ASP.NET Core vide                           | `web`         | [C#], F#     | Web/vides           |
| Application web ASP.NET Core (Model-View-Controller) | `mvc`         | [C#], F#     | Web/MVC             |
| Application web ASP.NET Core                         | `razor`       | [C#]         | Web/MVC/Razor Pages |
| ASP.NET Core avec Angular                    | `angular`     | [C#]         | Web/MVC/SPA         |
| ASP.NET Core avec React.js                   | `react`       | [C#]         | Web/MVC/SPA         |
| ASP.NET Core avec React.js et Redux         | `reactredux`  | [C#]         | Web/MVC/SPA         |
| API web ASP.NET Core                         | `webapi`      | [C#], F#     | Web/WebAPI          |
| fichier global.json                             | `globaljson`  |              | Config              |
| Configuration NuGet                                 | `nugetconfig` |              | Config              |
| Configuration Web                                   | `webconfig`   |              | Config              |
| Fichier solution                                | `sln`         |              | Solution            |
| Page Razor                                   | `page`        |              | Web/ASP.NET         |
| ViewImports MVC                              | `viewimports` |              | Web/ASP.NET         |
| ViewStart MVC                                | `viewstart`   |              | Web/ASP.NET         |

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

La commande contient une liste par défaut de modèles. Utilisez `dotnet new -all` pour obtenir une liste des modèles disponibles. Le tableau suivant présente les modèles préinstallés avec le SDK .NET Core 1.0.1. Le langage par défaut pour le modèle est indiqué entre crochets.

| Modèles            | Nom court    | Langue | Balises           |
|----------------------|---------------|----------|----------------|
| Application console  | `console`     | [C#], F# | Communes/Console |
| Bibliothèque de classes        | `classlib`    | [C#], F# | Communes/Bibliothèque |
| Projet de test unitaire    | `mstest`      | [C#], F# | Test/MSTest    |
| Projet de test xUnit   | `xunit`       | [C#], F# | Test/xUnit     |
| ASP.NET Core vide   | `web`         | [C#]     | Web/vides      |
| Application web ASP.NET Core | `mvc`         | [C#], F# | Web/MVC        |
| API web ASP.NET Core | `webapi`      | [C#]     | Web/WebAPI     |
| Configuration NuGet         | `nugetconfig` |          | Config         |
| Configuration Web           | `webconfig`   |          | Config         |
| Fichier solution        | `sln`         |          | Solution       |

---

## <a name="options"></a>Options

# <a name="net-core-22tabnetcore22"></a>[.NET Core 2.2](#tab/netcore22)

`--dry-run`

Affiche un récapitulatif de ce qui se passerait si la commande donnée était exécutée (si cela donnerait lieu à la création d’un modèle).

`--force`

Force le contenu à être généré même s’il change les fichiers existants. Ceci est nécessaire quand le répertoire de sortie contient déjà un projet.

`-h|--help`

Affiche l’aide pour la commande. Elle peut être appelée pour la commande `dotnet new` elle-même ou pour n’importe quel modèle, par exemple, `dotnet new mvc --help`.

`-i|--install <PATH|NUGET_ID>`

Installe un pack source ou de modèle à partir du `PATH` ou `NUGET_ID` fourni. Si vous souhaitez installer une préversion d’un package de modèle, vous devez spécifier la version au format `<package-name>::<package-version>`. Par défaut, `dotnet new` passe \* pour la version, qui représente la dernière version stable du package. Consultez un exemple dans la section [Exemples](#examples).

Pour plus d’informations sur la création de modèles personnalisés, consultez [Modèles personnalisés pour dotnet new](custom-templates.md).

`-l|--list`

Liste les modèles contenant le nom spécifié. Si elle est appelée pour la commande `dotnet new`, elle liste les modèles disponibles dans le répertoire donné. Par exemple, si le répertoire contient déjà un projet, elle ne liste pas tous les modèles de projet.

`-lang|--language {C#|F#|VB}`

Langage du modèle à créer. Le langage accepté diffère selon le modèle (voir les valeurs par défaut dans la section [arguments](#arguments)). Non valide pour certains modèles.

> [!NOTE]
> Certains interpréteurs interprètent la commande `#` comme un caractère spécial. Dans ce cas, vous devez placer la valeur de paramètre de langage entre guillemets doubles, par exemple `dotnet new console -lang "F#"`.

`-n|--name <OUTPUT_NAME>`

Le nom de la sortie créée. Si aucun nom n’est spécifié, le nom du répertoire actif est utilisé.

`--nuget-source`

Spécifie une source NuGet à utiliser pendant l’installation.

`-o|--output <OUTPUT_DIRECTORY>`

Emplacement où placer la sortie générée. La valeur par défaut correspond au répertoire actif.

`--type`

Filtre les modèles en fonction des types disponibles. Les valeurs prédéfinies sont « project », « item » ou « other ».

`-u|--uninstall <PATH|NUGET_ID>`

Désinstalle un pack source ou de modèle au `PATH` ou `NUGET_ID` fourni. Quand vous excluez la valeur `<PATH|NUGET_ID>`, tous les packs de modèles actuellement installés sont affichés, ainsi que les modèles qui leur sont associés.

> [!NOTE]
> Pour désinstaller un modèle à l’aide de `PATH`, vous devez qualifier le chemin d’accès avec un nom complet. Par exemple, *C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* fonctionne, mais *./GarciaSoftware.ConsoleTemplate.CSharp* à partir du dossier conteneur ne fonctionne pas.
> En outre, n’incluez pas de barre oblique finale après le répertoire dans votre chemin d’accès au modèle.

# <a name="net-core-21tabnetcore21"></a>[.NET Core 2.1](#tab/netcore21)

`--force`

Force le contenu à être généré même s’il change les fichiers existants. Ceci est nécessaire quand le répertoire de sortie contient déjà un projet.

`-h|--help`

Affiche l’aide pour la commande. Elle peut être appelée pour la commande `dotnet new` elle-même ou pour n’importe quel modèle, par exemple, `dotnet new mvc --help`.

`-i|--install <PATH|NUGET_ID>`

Installe un pack source ou de modèle à partir du `PATH` ou `NUGET_ID` fourni. Si vous souhaitez installer une préversion d’un package de modèle, vous devez spécifier la version au format `<package-name>::<package-version>`. Par défaut, `dotnet new` passe \* pour la version, qui représente la dernière version stable du package. Consultez un exemple dans la section [Exemples](#examples).

Pour plus d’informations sur la création de modèles personnalisés, consultez [Modèles personnalisés pour dotnet new](custom-templates.md).

`-l|--list`

Liste les modèles contenant le nom spécifié. Si elle est appelée pour la commande `dotnet new`, elle liste les modèles disponibles dans le répertoire donné. Par exemple, si le répertoire contient déjà un projet, elle ne liste pas tous les modèles de projet.

`-lang|--language {C#|F#|VB}`

Langage du modèle à créer. Le langage accepté diffère selon le modèle (voir les valeurs par défaut dans la section [arguments](#arguments)). Non valide pour certains modèles.

> [!NOTE]
> Certains interpréteurs interprètent la commande `#` comme un caractère spécial. Dans ce cas, vous devez placer la valeur de paramètre de langage entre guillemets doubles, par exemple `dotnet new console -lang "F#"`.

`-n|--name <OUTPUT_NAME>`

Le nom de la sortie créée. Si aucun nom n’est spécifié, le nom du répertoire actif est utilisé.

`--nuget-source`

Spécifie une source NuGet à utiliser pendant l’installation.

`-o|--output <OUTPUT_DIRECTORY>`

Emplacement où placer la sortie générée. La valeur par défaut correspond au répertoire actif.

`--type`

Filtre les modèles en fonction des types disponibles. Les valeurs prédéfinies sont « project », « item » ou « other ».

`-u|--uninstall <PATH|NUGET_ID>`

Désinstalle un pack source ou de modèle au `PATH` ou `NUGET_ID` fourni.

> [!NOTE]
> Pour désinstaller un modèle à l’aide de `PATH`, vous devez qualifier le chemin d’accès avec un nom complet. Par exemple, *C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* fonctionne, mais *./GarciaSoftware.ConsoleTemplate.CSharp* à partir du dossier conteneur ne fonctionne pas.
> En outre, n’incluez pas de barre oblique finale après le répertoire dans votre chemin d’accès au modèle.

# <a name="net-core-20tabnetcore20"></a>[.NET Core 2.0](#tab/netcore20)

`--force`

Force le contenu à être généré même s’il change les fichiers existants. Ceci est nécessaire quand le répertoire de sortie contient déjà un projet.

`-h|--help`

Affiche l’aide pour la commande. Elle peut être appelée pour la commande `dotnet new` elle-même ou pour n’importe quel modèle, par exemple, `dotnet new mvc --help`.

`-i|--install <PATH|NUGET_ID>`

Installe un pack source ou de modèle à partir du `PATH` ou `NUGET_ID` fourni. Si vous souhaitez installer une préversion d’un package de modèle, vous devez spécifier la version au format `<package-name>::<package-version>`. Par défaut, `dotnet new` passe \* pour la version, qui représente la dernière version stable du package. Consultez un exemple dans la section [Exemples](#examples).

Pour plus d’informations sur la création de modèles personnalisés, consultez [Modèles personnalisés pour dotnet new](custom-templates.md).

`-l|--list`

Liste les modèles contenant le nom spécifié. Si elle est appelée pour la commande `dotnet new`, elle liste les modèles disponibles dans le répertoire donné. Par exemple, si le répertoire contient déjà un projet, elle ne liste pas tous les modèles de projet.

`-lang|--language {C#|F#|VB}`

Langage du modèle à créer. Le langage accepté diffère selon le modèle (voir les valeurs par défaut dans la section [arguments](#arguments)). Non valide pour certains modèles.

> [!NOTE]
> Certains interpréteurs interprètent la commande `#` comme un caractère spécial. Dans ce cas, vous devez placer la valeur de paramètre de langage entre guillemets doubles, par exemple `dotnet new console -lang "F#"`.

`-n|--name <OUTPUT_NAME>`

Le nom de la sortie créée. Si aucun nom n’est spécifié, le nom du répertoire actif est utilisé.

`-o|--output <OUTPUT_DIRECTORY>`

Emplacement où placer la sortie générée. La valeur par défaut correspond au répertoire actif.

`--type`

Filtre les modèles en fonction des types disponibles. Les valeurs prédéfinies sont « project », « item » ou « other ».

`-u|--uninstall <PATH|NUGET_ID>`

Désinstalle un pack source ou de modèle au `PATH` ou `NUGET_ID` fourni.

> [!NOTE]
> Pour désinstaller un modèle à l’aide de `PATH` source, vous devez qualifier le chemin d’accès avec un nom complet. Par exemple, *C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* fonctionne, mais *./GarciaSoftware.ConsoleTemplate.CSharp* à partir du dossier conteneur ne fonctionne pas. En outre, n’incluez pas de barre oblique finale après le répertoire dans votre chemin d’accès au modèle.
> 
> Si vous ne parvenez pas à déterminer l’argument `PATH` ou `NUGET_ID` nécessaire pour désinstaller un modèle, l’exécution de `dotnet new --uninstall` sans argument répertorie tous les modèles installés et l’argument requis pour les désinstaller.

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

`-all|--show-all`

Affiche tous les modèles pour un type de projet spécifique lors de l’exécution dans le contexte de la commande `dotnet new` seule. Lors de l’exécution dans le contexte d’un modèle spécifique, comme `dotnet new web -all`, `-all` est interprété comme un indicateur de création forcée. Ceci est nécessaire quand le répertoire de sortie contient déjà un projet.

`-h|--help`

Affiche l’aide pour la commande. Elle peut être appelée pour la commande `dotnet new` elle-même ou pour n’importe quel modèle, par exemple, `dotnet new mvc --help`.

`-l|--list`

Liste les modèles contenant le nom spécifié. Si elle est appelée pour la commande `dotnet new`, elle liste les modèles disponibles dans le répertoire donné. Par exemple, si le répertoire contient déjà un projet, elle ne liste pas tous les modèles de projet.

`-lang|--language {C#|F#}`

Langage du modèle à créer. Le langage accepté diffère selon le modèle (voir les valeurs par défaut dans la section [arguments](#arguments)). Non valide pour certains modèles.

> [!NOTE]
> Certains interpréteurs interprètent la commande `#` comme un caractère spécial. Dans ce cas, vous devez placer la valeur de paramètre de langage entre guillemets doubles, par exemple `dotnet new console -lang "F#"`.

`-n|--name <OUTPUT_NAME>`

Le nom de la sortie créée. Si aucun nom n’est spécifié, le nom du répertoire actif est utilisé.

`-o|--output <OUTPUT_DIRECTORY>`

Emplacement où placer la sortie générée. La valeur par défaut correspond au répertoire actif.

---

## <a name="template-options"></a>Options de modèle

Chaque modèle de projet peut présenter d’autres options disponibles. Les modèles de base ont les options supplémentaires suivantes :

# <a name="net-core-22tabnetcore22"></a>[.NET Core 2.2](#tab/netcore22)

**console**

`--langVersion <VERSION_NUMBER>` - Définit la propriété `LangVersion` dans le fichier de projet créé. Par exemple, choisissez `--langVersion 7.3` pour utiliser C# 7.3. Non pris en charge pour F#.

`--no-restore` - N’exécute aucune restauration implicite pendant la création du projet.

**angular, react, reactredux**

`--exclude-launch-settings` - Exclure *launchSettings.json* du modèle généré.

`--no-restore` - N’exécute aucune restauration implicite pendant la création du projet.

`--no-https` - Le projet ne nécessite pas le protocole HTTPS. Cette option s’applique uniquement si `IndividualAuth` ou `OrganizationalAuth` ne sont pas utilisés.

**razorclasslib**

`--no-restore` - N’exécute aucune restauration implicite pendant la création du projet.

**classlib**

`-f|--framework <FRAMEWORK>` : spécifie le [framework](../../standard/frameworks.md) à cibler. Valeurs : `netcoreapp2.2` pour créer une bibliothèque de classes .NET Core ou `netstandard2.0` pour créer une bibliothèque de classes .NET Standard. La valeur par défaut est `netstandard2.0`.

`--langVersion <VERSION_NUMBER>` - Définit la propriété `LangVersion` dans le fichier de projet créé. Par exemple, choisissez `--langVersion 7.3` pour utiliser C# 7.3. Non pris en charge pour F#.

`--no-restore` - N’exécute aucune restauration implicite pendant la création du projet.

**mstest, xunit**

`-p|--enable-pack` : permet l’empaquetage pour le projet à l’aide de [dotnet pack](dotnet-pack.md).

`--no-restore` - N’exécute aucune restauration implicite pendant la création du projet.

**nunit**

`-f|--framework <FRAMEWORK>` : spécifie le [framework](../../standard/frameworks.md) à cibler. La valeur par défaut est `netcoreapp2.1`.

`-p|--enable-pack` : permet l’empaquetage pour le projet à l’aide de [dotnet pack](dotnet-pack.md).

`--no-restore` - N’exécute aucune restauration implicite pendant la création du projet.

**page**

`-na|--namespace <NAMESPACE_NAME>` - Espace de noms pour le code généré. La valeur par défaut est `MyApp.Namespace`.

`-np|--no-pagemodel` : crée la page sans modèle de page.

**viewimports**

`-na|--namespace <NAMESPACE_NAME>` - Espace de noms pour le code généré. La valeur par défaut est `MyApp.Namespace`.

**web**

`--exclude-launch-settings` - Exclure *launchSettings.json* du modèle généré.

`--no-restore` - N’exécute aucune restauration implicite pendant la création du projet.

`--no-https` - Le projet ne nécessite pas le protocole HTTPS. Cette option s’applique uniquement si `IndividualAuth` ou `OrganizationalAuth` ne sont pas utilisés.

**mvc, webapp**

`-au|--auth <AUTHENTICATION_TYPE>` : type d’authentification à utiliser. Les valeurs possibles sont :

- `None` : aucune authentification (configuration par défaut).
- `Individual` : authentification individuelle.
- `IndividualB2C` : authentification individuelle avec Azure AD B2C.
- `SingleOrg` : authentification d’organisation pour un seul abonné.
- `MultiOrg` : authentification d’organisation pour plusieurs abonnés.
- `Windows` : authentification Windows.

`--aad-b2c-instance <INSTANCE>` : instance d’Azure Active Directory B2C à laquelle se connecter. À utiliser avec l’authentification `IndividualB2C`. La valeur par défaut est `https://login.microsoftonline.com/tfp/`.

`-ssp|--susi-policy-id <ID>` : ID de la stratégie de connexion et d’inscription pour ce projet. À utiliser avec l’authentification `IndividualB2C`.

`-rp|--reset-password-policy-id <ID>` : ID de stratégie de réinitialisation du mot de passe pour ce projet. À utiliser avec l’authentification `IndividualB2C`.

`-ep|--edit-profile-policy-id <ID>` : ID de stratégie de modification du profil pour ce projet. À utiliser avec l’authentification `IndividualB2C`.

`--aad-instance <INSTANCE>` : instance d’Azure Active Directory à laquelle se connecter. À utiliser avec l’authentification `SingleOrg` ou `MultiOrg`. La valeur par défaut est `https://login.microsoftonline.com/`.

`--client-id <ID>` : ID client pour ce projet. À utiliser avec l’authentification `IndividualB2C`, `SingleOrg` ou `MultiOrg`. La valeur par défaut est `11111111-1111-1111-11111111111111111`.

`--domain <DOMAIN>` : domaine de l’abonné d’annuaire. À utiliser avec l’authentification `SingleOrg` ou `IndividualB2C`. La valeur par défaut est `qualified.domain.name`.

`--tenant-id <ID>` : ID d’abonné de l’annuaire auquel se connecter. À utiliser avec l’authentification `SingleOrg`. La valeur par défaut est `22222222-2222-2222-2222-222222222222`.

`--callback-path <PATH>` : chemin de demande dans le chemin de base de l’application de l’URI de redirection. À utiliser avec l’authentification `SingleOrg` ou `IndividualB2C`. La valeur par défaut est `/signin-oidc`.

`-r|--org-read-access` : accorde à cette application un accès en lecture au répertoire. S’applique uniquement à l’authentification `SingleOrg` ou `MultiOrg`.

`--exclude-launch-settings` - Exclure *launchSettings.json* du modèle généré.

`--no-https` - Le projet ne nécessite pas le protocole HTTPS. `app.UseHsts` et `app.UseHttpsRedirection` ne sont pas ajoutés à `Startup.Configure`. Cette option s’applique uniquement si `Individual`, `IndividualB2C`, `SingleOrg` ou `MultiOrg` ne sont pas utilisés.

`-uld|--use-local-db` : spécifie que la base de données locale doit être utilisée à la place de SQLite. S’applique uniquement à l’authentification `Individual` ou `IndividualB2C`.

`--no-restore` - N’exécute aucune restauration implicite pendant la création du projet.

**webapi**

`-au|--auth <AUTHENTICATION_TYPE>` : type d’authentification à utiliser. Les valeurs possibles sont :

- `None` : aucune authentification (configuration par défaut).
- `IndividualB2C` : authentification individuelle avec Azure AD B2C.
- `SingleOrg` : authentification d’organisation pour un seul abonné.
- `Windows` : authentification Windows.

`--aad-b2c-instance <INSTANCE>` : instance d’Azure Active Directory B2C à laquelle se connecter. À utiliser avec l’authentification `IndividualB2C`. La valeur par défaut est `https://login.microsoftonline.com/tfp/`.

`-ssp|--susi-policy-id <ID>` : ID de la stratégie de connexion et d’inscription pour ce projet. À utiliser avec l’authentification `IndividualB2C`.

`--aad-instance <INSTANCE>` : instance d’Azure Active Directory à laquelle se connecter. À utiliser avec l’authentification `SingleOrg`. La valeur par défaut est `https://login.microsoftonline.com/`.

`--client-id <ID>` : ID client pour ce projet. À utiliser avec l’authentification `IndividualB2C` ou `SingleOrg`. La valeur par défaut est `11111111-1111-1111-11111111111111111`.

`--domain <DOMAIN>` : domaine de l’abonné d’annuaire. À utiliser avec l’authentification `SingleOrg` ou `IndividualB2C`. La valeur par défaut est `qualified.domain.name`.

`--tenant-id <ID>` : ID d’abonné de l’annuaire auquel se connecter. À utiliser avec l’authentification `SingleOrg`. La valeur par défaut est `22222222-2222-2222-2222-222222222222`.

`-r|--org-read-access` : accorde à cette application un accès en lecture au répertoire. S’applique uniquement à l’authentification `SingleOrg` ou `MultiOrg`.

`--exclude-launch-settings` - Exclure *launchSettings.json* du modèle généré.

`--no-https` - Le projet ne nécessite pas le protocole HTTPS. `app.UseHsts` et `app.UseHttpsRedirection` ne sont pas ajoutés à `Startup.Configure`. Cette option s’applique uniquement si `Individual`, `IndividualB2C`, `SingleOrg` ou `MultiOrg` ne sont pas utilisés.

`-uld|--use-local-db` : spécifie que la base de données locale doit être utilisée à la place de SQLite. S’applique uniquement à l’authentification `Individual` ou `IndividualB2C`.

`--no-restore` - N’exécute aucune restauration implicite pendant la création du projet.

**globaljson**

`--sdk-version <VERSION_NUMBER>` : spécifie la version du SDK .NET Core à utiliser dans le fichier *global.json*.

# <a name="net-core-21tabnetcore21"></a>[.NET Core 2.1](#tab/netcore21)

**console, angular, react, reactredux, razorclasslib**

`--no-restore` - N’exécute aucune restauration implicite pendant la création du projet.

**classlib**

`-f|--framework <FRAMEWORK>` : spécifie le [framework](../../standard/frameworks.md) à cibler. Valeurs : `netcoreapp2.1` pour créer une bibliothèque de classes .NET Core ou `netstandard2.0` pour créer une bibliothèque de classes .NET Standard. La valeur par défaut est `netstandard2.0`.

`--no-restore` - N’exécute aucune restauration implicite pendant la création du projet.

**mstest, xunit**

`-p|--enable-pack` : permet l’empaquetage pour le projet à l’aide de [dotnet pack](dotnet-pack.md).

`--no-restore` - N’exécute aucune restauration implicite pendant la création du projet.

**globaljson**

`--sdk-version <VERSION_NUMBER>` : spécifie la version du SDK .NET Core à utiliser dans le fichier *global.json*.

**web**

`--exclude-launch-settings` - Exclure *launchSettings.json* du modèle généré.

`--no-restore` - N’exécute aucune restauration implicite pendant la création du projet.

`--no-https` - Le projet ne nécessite pas le protocole HTTPS. Cette option s’applique uniquement si `IndividualAuth` ou `OrganizationalAuth` ne sont pas utilisés.

**webapi**

`-au|--auth <AUTHENTICATION_TYPE>` : type d’authentification à utiliser. Les valeurs possibles sont :

- `None` : aucune authentification (configuration par défaut).
- `IndividualB2C` : authentification individuelle avec Azure AD B2C.
- `SingleOrg` : authentification d’organisation pour un seul abonné.
- `Windows` : authentification Windows.

`--aad-b2c-instance <INSTANCE>` : instance d’Azure Active Directory B2C à laquelle se connecter. À utiliser avec l’authentification `IndividualB2C`. La valeur par défaut est `https://login.microsoftonline.com/tfp/`.

`-ssp|--susi-policy-id <ID>` : ID de la stratégie de connexion et d’inscription pour ce projet. À utiliser avec l’authentification `IndividualB2C`.

`--aad-instance <INSTANCE>` : instance d’Azure Active Directory à laquelle se connecter. À utiliser avec l’authentification `SingleOrg`. La valeur par défaut est `https://login.microsoftonline.com/`.

`--client-id <ID>` : ID client pour ce projet. À utiliser avec l’authentification `IndividualB2C` ou `SingleOrg`. La valeur par défaut est `11111111-1111-1111-11111111111111111`.

`--domain <DOMAIN>` : domaine de l’abonné d’annuaire. À utiliser avec l’authentification `SingleOrg` ou `IndividualB2C`. La valeur par défaut est `qualified.domain.name`.

`--tenant-id <ID>` : ID d’abonné de l’annuaire auquel se connecter. À utiliser avec l’authentification `SingleOrg`. La valeur par défaut est `22222222-2222-2222-2222-222222222222`.

`-r|--org-read-access` : accorde à cette application un accès en lecture au répertoire. S’applique uniquement à l’authentification `SingleOrg` ou `MultiOrg`.

`--exclude-launch-settings` - Exclure *launchSettings.json* du modèle généré.

`-uld|--use-local-db` : spécifie que la base de données locale doit être utilisée à la place de SQLite. S’applique uniquement à l’authentification `Individual` ou `IndividualB2C`.

`--no-restore` - N’exécute aucune restauration implicite pendant la création du projet.

`--no-https` - Le projet ne nécessite pas le protocole HTTPS. `app.UseHsts` et `app.UseHttpsRedirection` ne sont pas ajoutés à `Startup.Configure`. Cette option s’applique uniquement si `Individual`, `IndividualB2C`, `SingleOrg` ou `MultiOrg` ne sont pas utilisés.

**mvc, razor**

`-au|--auth <AUTHENTICATION_TYPE>` : type d’authentification à utiliser. Les valeurs possibles sont :

- `None` : aucune authentification (configuration par défaut).
- `Individual` : authentification individuelle.
- `IndividualB2C` : authentification individuelle avec Azure AD B2C.
- `SingleOrg` : authentification d’organisation pour un seul abonné.
- `MultiOrg` : authentification d’organisation pour plusieurs abonnés.
- `Windows` : authentification Windows.

`--aad-b2c-instance <INSTANCE>` : instance d’Azure Active Directory B2C à laquelle se connecter. À utiliser avec l’authentification `IndividualB2C`. La valeur par défaut est `https://login.microsoftonline.com/tfp/`.

`-ssp|--susi-policy-id <ID>` : ID de la stratégie de connexion et d’inscription pour ce projet. À utiliser avec l’authentification `IndividualB2C`.

`-rp|--reset-password-policy-id <ID>` : ID de stratégie de réinitialisation du mot de passe pour ce projet. À utiliser avec l’authentification `IndividualB2C`.

`-ep|--edit-profile-policy-id <ID>` : ID de stratégie de modification du profil pour ce projet. À utiliser avec l’authentification `IndividualB2C`.

`--aad-instance <INSTANCE>` : instance d’Azure Active Directory à laquelle se connecter. À utiliser avec l’authentification `SingleOrg` ou `MultiOrg`. La valeur par défaut est `https://login.microsoftonline.com/`.

`--client-id <ID>` : ID client pour ce projet. À utiliser avec l’authentification `IndividualB2C`, `SingleOrg` ou `MultiOrg`. La valeur par défaut est `11111111-1111-1111-11111111111111111`.

`--domain <DOMAIN>` : domaine de l’abonné d’annuaire. À utiliser avec l’authentification `SingleOrg` ou `IndividualB2C`. La valeur par défaut est `qualified.domain.name`.

`--tenant-id <ID>` : ID d’abonné de l’annuaire auquel se connecter. À utiliser avec l’authentification `SingleOrg`. La valeur par défaut est `22222222-2222-2222-2222-222222222222`.

`--callback-path <PATH>` : chemin de demande dans le chemin de base de l’application de l’URI de redirection. À utiliser avec l’authentification `SingleOrg` ou `IndividualB2C`. La valeur par défaut est `/signin-oidc`.

`-r|--org-read-access` : accorde à cette application un accès en lecture au répertoire. S’applique uniquement à l’authentification `SingleOrg` ou `MultiOrg`.

`--exclude-launch-settings` - Exclure *launchSettings.json* du modèle généré.

`--use-browserlink` : inclut BrowserLink dans le projet.

`-uld|--use-local-db` : spécifie que la base de données locale doit être utilisée à la place de SQLite. S’applique uniquement à l’authentification `Individual` ou `IndividualB2C`.

`--no-restore` - N’exécute aucune restauration implicite pendant la création du projet.

`--no-https` - Le projet ne nécessite pas le protocole HTTPS. `app.UseHsts` et `app.UseHttpsRedirection` ne sont pas ajoutés à `Startup.Configure`. Cette option s’applique uniquement si `Individual`, `IndividualB2C`, `SingleOrg` ou `MultiOrg` ne sont pas utilisés.

**page**

`-na|--namespace <NAMESPACE_NAME>` - Espace de noms pour le code généré. La valeur par défaut est `MyApp.Namespace`.

`-np|--no-pagemodel` : crée la page sans modèle de page.

**viewimports**

`-na|--namespace <NAMESPACE_NAME>` - Espace de noms pour le code généré. La valeur par défaut est `MyApp.Namespace`.

# <a name="net-core-20tabnetcore20"></a>[.NET Core 2.0](#tab/netcore20)

**console, angular, react, reactredux**

`--no-restore` - N’exécute aucune restauration implicite pendant la création du projet.

**classlib**

`-f|--framework <FRAMEWORK>` : spécifie le [framework](../../standard/frameworks.md) à cibler. Valeurs : `netcoreapp2.0` pour créer une bibliothèque de classes .NET Core ou `netstandard2.0` pour créer une bibliothèque de classes .NET Standard. La valeur par défaut est `netstandard2.0`.

`--no-restore` - N’exécute aucune restauration implicite pendant la création du projet.

**mstest, xunit**

`-p|--enable-pack` : permet l’empaquetage pour le projet à l’aide de [dotnet pack](dotnet-pack.md).

`--no-restore` - N’exécute aucune restauration implicite pendant la création du projet.

**globaljson**

`--sdk-version <VERSION_NUMBER>` : spécifie la version du SDK .NET Core à utiliser dans le fichier *global.json*.

**web**

`--use-launch-settings` : inclut *launchSettings.json* dans la sortie de modèle générée.

`--no-restore` - N’exécute aucune restauration implicite pendant la création du projet.

**webapi**

`-au|--auth <AUTHENTICATION_TYPE>` : type d’authentification à utiliser. Les valeurs possibles sont :

- `None` : aucune authentification (configuration par défaut).
- `IndividualB2C` : authentification individuelle avec Azure AD B2C.
- `SingleOrg` : authentification d’organisation pour un seul abonné.
- `Windows` : authentification Windows.

`--aad-b2c-instance <INSTANCE>` : instance d’Azure Active Directory B2C à laquelle se connecter. À utiliser avec l’authentification `IndividualB2C`. La valeur par défaut est `https://login.microsoftonline.com/tfp/`.

`-ssp|--susi-policy-id <ID>` : ID de la stratégie de connexion et d’inscription pour ce projet. À utiliser avec l’authentification `IndividualB2C`.

`--aad-instance <INSTANCE>` : instance d’Azure Active Directory à laquelle se connecter. À utiliser avec l’authentification `SingleOrg`. La valeur par défaut est `https://login.microsoftonline.com/`.

`--client-id <ID>` : ID client pour ce projet. À utiliser avec l’authentification `IndividualB2C` ou `SingleOrg`. La valeur par défaut est `11111111-1111-1111-11111111111111111`.

`--domain <DOMAIN>` : domaine de l’abonné d’annuaire. À utiliser avec l’authentification `SingleOrg` ou `IndividualB2C`. La valeur par défaut est `qualified.domain.name`.

`--tenant-id <ID>` : ID d’abonné de l’annuaire auquel se connecter. À utiliser avec l’authentification `SingleOrg`. La valeur par défaut est `22222222-2222-2222-2222-222222222222`.

`-r|--org-read-access` : accorde à cette application un accès en lecture au répertoire. S’applique uniquement à l’authentification `SingleOrg` ou `MultiOrg`.

`--use-launch-settings` : inclut *launchSettings.json* dans la sortie de modèle générée.

`-uld|--use-local-db` : spécifie que la base de données locale doit être utilisée à la place de SQLite. S’applique uniquement à l’authentification `Individual` ou `IndividualB2C`.

`--no-restore` - N’exécute aucune restauration implicite pendant la création du projet.

**mvc, razor**

`-au|--auth <AUTHENTICATION_TYPE>` : type d’authentification à utiliser. Les valeurs possibles sont :

- `None` : aucune authentification (configuration par défaut).
- `Individual` : authentification individuelle.
- `IndividualB2C` : authentification individuelle avec Azure AD B2C.
- `SingleOrg` : authentification d’organisation pour un seul abonné.
- `MultiOrg` : authentification d’organisation pour plusieurs abonnés.
- `Windows` : authentification Windows.

`--aad-b2c-instance <INSTANCE>` : instance d’Azure Active Directory B2C à laquelle se connecter. À utiliser avec l’authentification `IndividualB2C`. La valeur par défaut est `https://login.microsoftonline.com/tfp/`.

`-ssp|--susi-policy-id <ID>` : ID de la stratégie de connexion et d’inscription pour ce projet. À utiliser avec l’authentification `IndividualB2C`.

`-rp|--reset-password-policy-id <ID>` : ID de stratégie de réinitialisation du mot de passe pour ce projet. À utiliser avec l’authentification `IndividualB2C`.

`-ep|--edit-profile-policy-id <ID>` : ID de stratégie de modification du profil pour ce projet. À utiliser avec l’authentification `IndividualB2C`.

`--aad-instance <INSTANCE>` : instance d’Azure Active Directory à laquelle se connecter. À utiliser avec l’authentification `SingleOrg` ou `MultiOrg`. La valeur par défaut est `https://login.microsoftonline.com/`.

`--client-id <ID>` : ID client pour ce projet. À utiliser avec l’authentification `IndividualB2C`, `SingleOrg` ou `MultiOrg`. La valeur par défaut est `11111111-1111-1111-11111111111111111`.

`--domain <DOMAIN>` : domaine de l’abonné d’annuaire. À utiliser avec l’authentification `SingleOrg` ou `IndividualB2C`. La valeur par défaut est `qualified.domain.name`.

`--tenant-id <ID>` : ID d’abonné de l’annuaire auquel se connecter. À utiliser avec l’authentification `SingleOrg`. La valeur par défaut est `22222222-2222-2222-2222-222222222222`.

`--callback-path <PATH>` : chemin de demande dans le chemin de base de l’application de l’URI de redirection. À utiliser avec l’authentification `SingleOrg` ou `IndividualB2C`. La valeur par défaut est `/signin-oidc`.

`-r|--org-read-access` : accorde à cette application un accès en lecture au répertoire. S’applique uniquement à l’authentification `SingleOrg` ou `MultiOrg`.

`--use-launch-settings` : inclut *launchSettings.json* dans la sortie de modèle générée.

`--use-browserlink` : inclut BrowserLink dans le projet.

`-uld|--use-local-db` : spécifie que la base de données locale doit être utilisée à la place de SQLite. S’applique uniquement à l’authentification `Individual` ou `IndividualB2C`.

`--no-restore` - N’exécute aucune restauration implicite pendant la création du projet.

**page**

`-na|--namespace <NAMESPACE_NAME>` : espace de noms pour le code généré. La valeur par défaut est `MyApp.Namespace`.

`-np|--no-pagemodel` : crée la page sans modèle de page.

**viewimports**

`-na|--namespace <NAMESPACE_NAME>` : espace de noms pour le code généré. La valeur par défaut est `MyApp.Namespace`.

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

**console, xunit, mstest, web, webapi**

`-f|--framework <FRAMEWORK>` : spécifie le [framework](../../standard/frameworks.md) à cibler. Valeurs : `netcoreapp1.0` ou `netcoreapp1.1`. La valeur par défaut est `netcoreapp1.0`.

**classlib**

`-f|--framework <FRAMEWORK>` : spécifie le [framework](../../standard/frameworks.md) à cibler. Valeurs : `netcoreapp1.0`, `netcoreapp1.1` ou `netstandard1.0` à `netstandard1.6`. La valeur par défaut est `netstandard1.4`.

**mvc**

`-f|--framework <FRAMEWORK>` : spécifie le [framework](../../standard/frameworks.md) à cibler. Valeurs : `netcoreapp1.0` ou `netcoreapp1.1`. La valeur par défaut est `netcoreapp1.0`.

`-au|--auth <AUTHENTICATION_TYPE>` : type d’authentification à utiliser. Valeurs : `None` ou `Individual`. La valeur par défaut est `None`.

`-uld|--use-local-db` : spécifie s’il convient ou non d’utiliser LocalDB au lieu de SQLite. Valeurs : `true` ou `false`. La valeur par défaut est `false`.

---

## <a name="examples"></a>Exemples

Créez un projet d’application console C# en spécifiant le nom du modèle :

`dotnet new "Console Application"`

Créez un projet d’application console F# dans le répertoire actif :

`dotnet new console -lang F#`

Créez un projet de bibliothèque de classes .NET Standard dans le répertoire spécifié (disponible uniquement avec le SDK .NET Core 2.0 ou ultérieur) :

`dotnet new classlib -lang VB -o MyLibrary`

Créez un projet ASP.NET Core C# MVC dans le répertoire actif sans authentification :

`dotnet new mvc -au None`

Créez un projet xUnit :

`dotnet new xunit`

Répertoriez tous les modèles disponibles pour MVC :

`dotnet new mvc -l`

Liste de tous les modèles correspondant à la sous-chaîne *we*. Aucune correspondance exacte n’a été trouvée, donc la recherche de sous-chaîne est exécutée sur les colonnes Nom court et Nom.

`dotnet new we -l`

Tentative d’appel du modèle correspondant à *ng*. Si aucune correspondance exacte n’est trouvée, listez les modèles qui correspondent partiellement.

`dotnet new ng`

Installez la version 2.0 des modèles d’application monopage pour ASP.NET Core (option de commande disponible pour .NET Core  SDK 1.1 et versions ultérieures uniquement) :

`dotnet new -i Microsoft.DotNet.Web.Spa.ProjectTemplates::2.0.0`

Créez un fichier *global.json* dans le répertoire actif en définissant la version du SDK sur 2.0.0 (disponible uniquement avec le SDK .NET Core 2.0 ou ultérieure) :

`dotnet new globaljson --sdk-version 2.0.0`

## <a name="see-also"></a>Voir aussi

- [Modèles personnalisés pour dotnet new](custom-templates.md)
- [Créer un modèle personnalisé pour dotnet new](~/docs/core/tutorials/create-custom-template.md)
- [Dépôt GitHub dotnet/dotnet-template-samples](https://github.com/dotnet/dotnet-template-samples)
- [Modèles disponibles pour dotnet new](https://github.com/dotnet/templating/wiki/Available-templates-for-dotnet-new)
