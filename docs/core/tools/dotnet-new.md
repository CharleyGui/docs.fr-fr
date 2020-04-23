---
title: Commande dotnet new
description: La commande dotnet new crée des projets .NET Core basés sur le modèle spécifié.
ms.date: 04/10/2020
ms.openlocfilehash: 1979f98a6005a414acc64c5eaa086a88aca9f033
ms.sourcegitcommit: 73aa9653547a1cd70ee6586221f79cc29b588ebd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2020
ms.locfileid: "82102825"
---
# <a name="dotnet-new"></a>dotnet new

**Cet article s’applique à:** ✔️ .NET Core 2.0 SDK et les versions ultérieures

## <a name="name"></a>Nom

`dotnet new` : crée un projet, un fichier de configuration ou une solution en fonction du modèle spécifié.

## <a name="synopsis"></a>Synopsis

```dotnetcli
dotnet new <TEMPLATE> [--dry-run] [--force] [-i|--install {PATH|NUGET_ID}]
    [-lang|--language {C#|F#|VB}] [-n|--name <OUTPUT_NAME>]
    [--nuget-source <SOURCE>] [-o|--output <OUTPUT_DIRECTORY>]
    [-u|--uninstall] [--update-apply] [--update-check] [Template options]

dotnet new <TEMPLATE> [-l|--list] [--type <TYPE>]

dotnet new -h|--help
```

## <a name="description"></a>Description

La `dotnet new` commande crée un projet .NET Core ou d’autres artefacts basés sur un modèle.

La commande appelle le [moteur de modèles](https://github.com/dotnet/templating) pour créer les artefacts sur le disque en fonction du modèle et des options spécifiés.

### <a name="implicit-restore"></a>Restauration implicite

[!INCLUDE[dotnet restore note](~/includes/dotnet-restore-note.md)]

## <a name="arguments"></a>Arguments

- **`TEMPLATE`**

  Modèle à instancier quand la commande est appelée. Vous pouvez passer des options spécifiques pour chaque modèle. Pour plus d'informations, consultez [Options de modèle](#template-options).

  Vous pouvez `dotnet new --list` courir pour voir une liste de tous les modèles installés. Si `TEMPLATE` la valeur n’est pas une correspondance exacte sur le texte dans les **Modèles** ou la colonne **Short Name** de la table retournée, un match de sous-corde est effectué sur ces deux colonnes.

  En commençant par .NET Core 3.0 SDK, le CLI recherche des `dotnet new` modèles dans NuGet.org lorsque vous invoquez la commande dans les conditions suivantes :

  - Si le CLI ne peut pas trouver `dotnet new`un modèle de correspondance lors de l’invocation , même pas partielle.
  - S’il y a une nouvelle version du modèle disponible. Dans ce cas, le projet ou l’artefact est créé, mais le CLI vous avertit d’une version mise à jour du modèle.

  La commande contient une liste par défaut de modèles. Utilisez `dotnet new -l` pour obtenir une liste des modèles disponibles. Le tableau suivant montre les modèles qui viennent pré-installé avec le SDK .NET Core. Le langage par défaut pour le modèle est indiqué entre crochets. Cliquez sur le lien de nom court pour voir les options spécifiques de modèle.

| Modèles                                    | Nom court                      | Langage     | Balises                                  | Introduit |
|----------------------------------------------|---------------------------------|--------------|---------------------------------------|------------|
| Application console                          | [console](#console)             | [C#], F#, VB | Communes/Console                        | 1.0        |
| Bibliothèque de classes                                | [classlib](#classlib)           | [C#], F#, VB | Communes/Bibliothèque                        | 1.0        |
| Application WPF                              | [Wpf](#wpf)                     | [C#]         | Common/WPF                            | 3.0        |
| Bibliothèque de classe WPF                            | [wpflib (wpflib)](#wpf)                  | [C#]         | Common/WPF                            | 3.0        |
| Bibliothèque de contrôles personnalisés WPF                   | [wpfcustomcontrollib](#wpf)     | [C#]         | Common/WPF                            | 3.0        |
| Bibliothèque de contrôles utilisateur WPF                     | [wpfusercontrollib](#wpf)       | [C#]         | Common/WPF                            | 3.0        |
| Application des formulaires Windows (WinForms)         | [Winforms](#winforms)           | [C#]         | Common/WinForms                       | 3.0        |
| Bibliothèque de classe Windows Forms (WinForms)       | [winformslib](#winforms)        | [C#]         | Common/WinForms                       | 3.0        |
| Service aux travailleurs                               | [Travailleur](#web-others)           | [C#]         | Commun/Travailleur/Web                     | 3.0        |
| Projet de test unitaire                            | [mstest](#test)                 | [C#], F#, VB | Test/MSTest                           | 1.0        |
| Projet de test NUnit 3                         | [Nunit](#nunit)                  | [C#], F#, VB | Test/NUnit                            | 2.1.400    |
| Élément de test NUnit 3                            | `nunit-test`                    | [C#], F#, VB | Test/NUnit                            | 2.2        |
| Projet de test xUnit                           | [xunit](#test)                  | [C#], F#, VB | Test/xUnit                            | 1.0        |
| Composant de rasoir                              | `razorcomponent`                | [C#]         | Web/ASP.NET                           | 3.0        |
| Page Razor                                   | [Page](#page)                   | [C#]         | Web/ASP.NET                           | 2.0        |
| ViewImports MVC                              | [viewimports](#namespace)       | [C#]         | Web/ASP.NET                           | 2.0        |
| ViewStart MVC                                | `viewstart`                     | [C#]         | Web/ASP.NET                           | 2.0        |
| Application Serveur Blazor                            | [blazorserver](#blazorserver)   | [C#]         | Web/Blazor                            | 3.0        |
| ASP.NET Core vide                           | [Web](#web)                     | [C#], F#     | Web/vides                             | 1.0        |
| Application web ASP.NET Core (Model-View-Controller) | [Mvc](#web-options)             | [C#], F#     | Web/MVC                               | 1.0        |
| Application web ASP.NET Core                         | [webapp, rasoir](#web-options)   | [C#]         | Web/MVC/Razor Pages                   | 2.2, 2.0   |
| ASP.NET Core avec Angular                    | [Angulaire](#spa)                 | [C#]         | Web/MVC/SPA                           | 2.0        |
| ASP.NET Core avec React.js                   | [Réagir](#spa)                   | [C#]         | Web/MVC/SPA                           | 2.0        |
| ASP.NET Core avec React.js et Redux         | [reactredux](#reactredux)       | [C#]         | Web/MVC/SPA                           | 2.0        |
| Bibliothèque de classes Razor                          | [razorclasslib](#razorclasslib) | [C#]         | Web/Razor/Library/Bibliothèque de classes Razor | 2.1        |
| API web ASP.NET Core                         | [webapi webapi](#webapi)               | [C#], F#     | Web/WebAPI                            | 1.0        |
| ASP.NET Core gRPC Service                    | [grpc grpc](#web-others)             | [C#]         | Web/gRPC                              | 3.0        |
| Fichier tampon de protocole                         | [Proto](#namespace)             |              | Web/gRPC                              | 3.0        |
| fichier gitignore dotnet                        | `gitignore`                     |              | Config                                | 3.0        |
| fichier global.json                             | [globaljson (globaljson)](#globaljson)       |              | Config                                | 2.0        |
| Configuration NuGet                                 | `nugetconfig`                   |              | Config                                | 1.0        |
| dotnet local outil manifeste fichier              | `tool-manifest`                 |              | Config                                | 3.0        |
| Configuration Web                                   | `webconfig`                     |              | Config                                | 1.0        |
| Fichier solution                                | `sln`                           |              | Solution                              | 1.0        |

## <a name="options"></a>Options

- **`--dry-run`**

  Affiche un résumé de ce qui se passerait si la commande donnée était exécutée. Disponible depuis .NET Core 2.2 SDK.

- **`--force`**

  Force le contenu à être généré même s’il change les fichiers existants. Cela est nécessaire lorsque le modèle choisi remplacerait les fichiers existants dans l’annuaire de sortie.

- **`-h|--help`**

  Affiche l’aide pour la commande. Il peut être invoqué `dotnet new` pour la commande elle-même ou pour n’importe quel modèle. Par exemple : `dotnet new mvc --help`.

- **`-i|--install <PATH|NUGET_ID>`**

  Installe un pack de `PATH` `NUGET_ID` gabarit à partir de la ou fournie. Si vous souhaitez installer une préversion d’un package de modèle, vous devez spécifier la version au format `<package-name>::<package-version>`. Par `dotnet new` défaut, \* passe pour la version, qui représente la dernière version de paquet stable. Voir un exemple dans la section [Exemples.](#examples)
  
  Si une version du modèle a déjà été installée lorsque vous exécutez cette commande, le modèle sera mis à jour à la version spécifiée, ou à la dernière version stable si aucune version n’a été spécifiée.

  Pour plus d’informations sur la création de modèles personnalisés, consultez [Modèles personnalisés pour dotnet new](custom-templates.md).

- **`-l|--list`**

  Liste les modèles contenant le nom spécifié. Si aucun nom n’est spécifié, répertorie tous les modèles.

- **`-lang|--language {C#|F#|VB}`**

  Langage du modèle à créer. Le langage accepté diffère selon le modèle (voir les valeurs par défaut dans la section [arguments](#arguments)). Non valide pour certains modèles.

  > [!NOTE]
  > Certains interpréteurs interprètent la commande `#` comme un caractère spécial. Dans ces cas, joindre la valeur du paramètre linguistique dans les guillemets. Par exemple : `dotnet new console -lang "F#"`.

- **`-n|--name <OUTPUT_NAME>`**

  Le nom de la sortie créée. Si aucun nom n’est spécifié, le nom du répertoire actif est utilisé.

- **`--nuget-source <SOURCE>`**

  Spécifie une source NuGet à utiliser pendant l’installation. Disponible depuis .NET Core 2.1 SDK.

- **`-o|--output <OUTPUT_DIRECTORY>`**

  Emplacement où placer la sortie générée. L'emplacement par défaut est le répertoire actif.

- **`--type <TYPE>`**

  Filtre les modèles en fonction des types disponibles. Les valeurs prédéfinies sont, `project` `item`, ou `other`.

- **`-u|--uninstall [PATH|NUGET_ID]`**

  Désinstallez un pack `PATH` de `NUGET_ID` gabarit ou fourni. Lorsque `<PATH|NUGET_ID>` la valeur n’est pas spécifiée, tous les packs de modèles actuellement installés et leurs modèles associés sont affichés. Lorsque vous `NUGET_ID`spécifiez, n’incluez pas le numéro de version.

  Si vous ne spécifiez pas un paramètre à cette option, la commande répertorie les modèles installés et les détails à leur sujet.

  > [!NOTE]
  > Pour désinstaller un modèle à l’aide de `PATH`, vous devez qualifier le chemin d’accès avec un nom complet. Par exemple, *\<C:/Users/ USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* fonctionnera, mais *./GarciaSoftware.ConsoleTemplate.CSharp* du dossier contenant ne fonctionnera pas.
  > N’incluez pas une dernière barre oblique de terminat sur votre trajectoire de modèle.

- **`--update-apply`**

  Vérifie s’il existe des mises à jour disponibles pour les packs de modèles qui sont actuellement installés et les installe. Option disponible à partir du kit SDK .NET Core 3.0.

- **`--update-check`**

  Vérifie s’il existe des mises à jour disponibles pour les packs de modèles qui sont actuellement installés. Option disponible à partir du kit SDK .NET Core 3.0.

## <a name="template-options"></a>Options de modèle

Chaque modèle de projet peut présenter d’autres options disponibles. Les modèles de base ont les options supplémentaires suivantes :

### <a name="console"></a>console

- **`-f|--framework <FRAMEWORK>`**

  Spécifie le [cadre](../../standard/frameworks.md) à cibler. Option disponible à partir du kit SDK .NET Core 3.0.

  Le tableau suivant répertorie les valeurs par défaut en fonction du numéro de version SDK que vous utilisez :

  | Version du SDK | Valeur par défaut   |
  |-------------|-----------------|
  | 3.1         | `netcoreapp3.1` |
  | 3.0         | `netcoreapp3.0` |

- **`--langVersion <VERSION_NUMBER>`**

  Définit `LangVersion` la propriété dans le fichier de projet créé. Par exemple, choisissez `--langVersion 7.3` pour utiliser C# 7.3. Non pris en charge pour F#. Disponible depuis .NET Core 2.2 SDK.

  Pour une liste des versions par défaut de C, voir [Par défaut](../../csharp/language-reference/configure-language-version.md#defaults).

- **`--no-restore`**

  Si spécifié, n’exécute pas une restauration implicite pendant la création du projet. Disponible depuis .NET Core 2.2 SDK.

***

### <a name="classlib"></a>classlib

- **`-f|--framework <FRAMEWORK>`**

  Spécifie le [cadre](../../standard/frameworks.md) à cibler. Valeurs : `netcoreapp<version>` pour créer une bibliothèque de classes .NET Core ou `netstandard<version>` pour créer une bibliothèque de classes .NET Standard. La valeur par défaut est `netstandard2.0`.

- **`--langVersion <VERSION_NUMBER>`**

  Définit `LangVersion` la propriété dans le fichier de projet créé. Par exemple, choisissez `--langVersion 7.3` pour utiliser C# 7.3. Non pris en charge pour F#. Disponible depuis .NET Core 2.2 SDK.

  Pour une liste des versions par défaut de C, voir [Par défaut](../../csharp/language-reference/configure-language-version.md#defaults).

- **`--no-restore`**

  N’exécute pas une restauration implicite pendant la création du projet.

***

### <a name="wpf-wpflib-wpfcustomcontrollib-wpfusercontrollib"></a><a name="wpf"></a>wpf, wpflib, wpfcustomcontrollib, wpfusercontrollib

- **`-f|--framework <FRAMEWORK>`**

  Spécifie le [cadre](../../standard/frameworks.md) à cibler. La valeur par défaut est `netcoreapp3.1`. Disponible depuis .NET Core 3.1 SDK.

- **`--langVersion <VERSION_NUMBER>`**

  Définit `LangVersion` la propriété dans le fichier de projet créé. Par exemple, choisissez `--langVersion 7.3` pour utiliser C# 7.3.

  Pour une liste des versions par défaut de C, voir [Par défaut](../../csharp/language-reference/configure-language-version.md#defaults).

- **`--no-restore`**

  N’exécute pas une restauration implicite pendant la création du projet.

***

### <a name="winforms-winformslib"></a><a name="winforms"></a>winforms, winformslib

- **`--langVersion <VERSION_NUMBER>`**

  Définit `LangVersion` la propriété dans le fichier de projet créé. Par exemple, choisissez `--langVersion 7.3` pour utiliser C# 7.3.

  Pour une liste des versions par défaut de C, voir [Par défaut](../../csharp/language-reference/configure-language-version.md#defaults).

- **`--no-restore`**

  N’exécute pas une restauration implicite pendant la création du projet.

***

### <a name="worker-grpc"></a><a name="web-others"></a>travailleur, grpc

- **`-f|--framework <FRAMEWORK>`**

  Spécifie le [cadre](../../standard/frameworks.md) à cibler. La valeur par défaut est `netcoreapp3.1`. Disponible depuis .NET Core 3.1 SDK.

- **`--exclude-launch-settings`**

  Exclut *le lancementSettings.json* du modèle généré.

- **`--no-restore`**

  N’exécute pas une restauration implicite pendant la création du projet.

***

### <a name="mstest-xunit"></a><a name="test"></a>mstest, xunit

- **`-f|--framework <FRAMEWORK>`**

  Spécifie le [cadre](../../standard/frameworks.md) à cibler. Option disponible depuis .NET Core 3.0 SDK.

  Le tableau suivant répertorie les valeurs par défaut en fonction du numéro de version SDK que vous utilisez :

  | Version du SDK | Valeur par défaut   |
  |-------------|-----------------|
  | 3.1         | `netcoreapp3.1` |
  | 3.0         | `netcoreapp3.0` |

- **`-p|--enable-pack`**

  Permet l’emballage pour le projet à l’aide [de dotnet pack](dotnet-pack.md).

- **`--no-restore`**

  N’exécute pas une restauration implicite pendant la création du projet.

***

### <a name="nunit"></a>Nunit

- **`-f|--framework <FRAMEWORK>`**

  Spécifie le [cadre](../../standard/frameworks.md) à cibler.

  Le tableau suivant répertorie les valeurs par défaut en fonction du numéro de version SDK que vous utilisez :

  | Version du SDK | Valeur par défaut   |
  |-------------|-----------------|
  | 3.1         | `netcoreapp3.1` |
  | 3.0         | `netcoreapp3.0` |
  | 2.2         | `netcoreapp2.2` |
  | 2.1         | `netcoreapp2.1` |

- **`-p|--enable-pack`**

  Permet l’emballage pour le projet à l’aide [de dotnet pack](dotnet-pack.md).

- **`--no-restore`**

  N’exécute pas une restauration implicite pendant la création du projet.

***

### <a name="page"></a>page

- **`-na|--namespace <NAMESPACE_NAME>`**

  Espace nom pour le code généré. La valeur par défaut est `MyApp.Namespace`.

- **`-np|--no-pagemodel`**

  Crée la page sans PageModel.

***

### <a name="viewimports-proto"></a><a name="namespace"></a>viewimports, proto

- **`-na|--namespace <NAMESPACE_NAME>`**

  Espace nom pour le code généré. La valeur par défaut est `MyApp.Namespace`.

***

### <a name="blazorserver"></a>blazorserver

- **`-au|--auth <AUTHENTICATION_TYPE>`**

  Type d’authentification à utiliser. Les valeurs possibles sont les suivantes :

  - `None` : aucune authentification (configuration par défaut).
  - `Individual` : authentification individuelle.
  - `IndividualB2C` : authentification individuelle avec Azure AD B2C.
  - `SingleOrg` : authentification d’organisation pour un seul abonné.
  - `MultiOrg` : authentification d’organisation pour plusieurs abonnés.
  - `Windows` : authentification Windows.

- **`--aad-b2c-instance <INSTANCE>`**

  L’instance Azure Active Directory B2C à connecter. À utiliser avec l’authentification `IndividualB2C`. La valeur par défaut est `https://login.microsoftonline.com/tfp/`.

- **`-ssp|--susi-policy-id <ID>`**

  L’id de la stratégie d’inscription et d’inscription pour ce projet. À utiliser avec l’authentification `IndividualB2C`.

- **`-rp|--reset-password-policy-id <ID>`**

  L’ID de stratégie de mot de passe de réinitialisation pour ce projet. À utiliser avec l’authentification `IndividualB2C`.

- **`-ep|--edit-profile-policy-id <ID>`**

  L’ID de la stratégie de profil d’édition pour ce projet. À utiliser avec l’authentification `IndividualB2C`.

- **`--aad-instance <INSTANCE>`**

  L’instance Azure Active Directory à connecter. À utiliser avec l’authentification `SingleOrg` ou `MultiOrg`. La valeur par défaut est `https://login.microsoftonline.com/`.

- **`--client-id <ID>`**

  L’ID client pour ce projet. À utiliser avec l’authentification `IndividualB2C`, `SingleOrg` ou `MultiOrg`. La valeur par défaut est `11111111-1111-1111-11111111111111111`.

- **`--domain <DOMAIN>`**

  Le domaine pour le locataire de l’annuaire. À utiliser avec l’authentification `SingleOrg` ou `IndividualB2C`. La valeur par défaut est `qualified.domain.name`.

- **`--tenant-id <ID>`**

  L’ID TenantId de l’annuaire pour se connecter à. À utiliser avec l’authentification `SingleOrg`. La valeur par défaut est `22222222-2222-2222-2222-222222222222`.

- **`--callback-path <PATH>`**

  Le chemin de demande dans le chemin de base de l’application de l’URI rediriger. À utiliser avec l’authentification `SingleOrg` ou `IndividualB2C`. La valeur par défaut est `/signin-oidc`.

- **`-r|--org-read-access`**

  Permet à cette application de lire l’accès à l’annuaire. S’applique uniquement à l’authentification `SingleOrg` ou `MultiOrg`.

- **`--exclude-launch-settings`**

  Exclut *le lancementSettings.json* du modèle généré.

- **`--no-https`**

  Éteint HTTPS. Cette option ne `Individual` `IndividualB2C`s’applique `MultiOrg` que si, `--auth`, `SingleOrg`, ou ne sont pas utilisés pour .

- **`-uld|--use-local-db`**

  Spécifie LocalDB devrait être utilisé au lieu de SQLite. S’applique uniquement à l’authentification `Individual` ou `IndividualB2C`.

- **`--no-restore`**

  N’exécute pas une restauration implicite pendant la création du projet.

***

### <a name="web"></a>web

- **`--exclude-launch-settings`**

  Exclut *le lancementSettings.json* du modèle généré.

- **`-f|--framework <FRAMEWORK>`**

  Spécifie le [cadre](../../standard/frameworks.md) à cibler. Option non disponible en .NET Core 2.2 SDK.

  Le tableau suivant répertorie les valeurs par défaut en fonction du numéro de version SDK que vous utilisez :

  | Version du SDK | Valeur par défaut   |
  |-------------|-----------------|
  | 3.1         | `netcoreapp3.1` |
  | 3.0         | `netcoreapp3.0` |
  | 2.1         | `netcoreapp2.1` |

- **`--no-restore`**

  N’exécute pas une restauration implicite pendant la création du projet.

- **`--no-https`**

  Éteint HTTPS.

***

### <a name="mvc-webapp"></a><a name="web-options"></a>mvc, webapp

- **`-au|--auth <AUTHENTICATION_TYPE>`**

  Type d’authentification à utiliser. Les valeurs possibles sont les suivantes :

  - `None` : aucune authentification (configuration par défaut).
  - `Individual` : authentification individuelle.
  - `IndividualB2C` : authentification individuelle avec Azure AD B2C.
  - `SingleOrg` : authentification d’organisation pour un seul abonné.
  - `MultiOrg` : authentification d’organisation pour plusieurs abonnés.
  - `Windows` : authentification Windows.

- **`--aad-b2c-instance <INSTANCE>`**

  L’instance Azure Active Directory B2C à connecter. À utiliser avec l’authentification `IndividualB2C`. La valeur par défaut est `https://login.microsoftonline.com/tfp/`.

- **`-ssp|--susi-policy-id <ID>`**

  L’id de la stratégie d’inscription et d’inscription pour ce projet. À utiliser avec l’authentification `IndividualB2C`.

- **`-rp|--reset-password-policy-id <ID>`**

  L’ID de stratégie de mot de passe de réinitialisation pour ce projet. À utiliser avec l’authentification `IndividualB2C`.

- **`-ep|--edit-profile-policy-id <ID>`**

  L’ID de la stratégie de profil d’édition pour ce projet. À utiliser avec l’authentification `IndividualB2C`.

- **`--aad-instance <INSTANCE>`**

  L’instance Azure Active Directory à connecter. À utiliser avec l’authentification `SingleOrg` ou `MultiOrg`. La valeur par défaut est `https://login.microsoftonline.com/`.

- **`--client-id <ID>`**

  L’ID client pour ce projet. À utiliser avec l’authentification `IndividualB2C`, `SingleOrg` ou `MultiOrg`. La valeur par défaut est `11111111-1111-1111-11111111111111111`.

- **`--domain <DOMAIN>`**

  Le domaine pour le locataire de l’annuaire. À utiliser avec l’authentification `SingleOrg` ou `IndividualB2C`. La valeur par défaut est `qualified.domain.name`.

- **`--tenant-id <ID>`**

  L’ID TenantId de l’annuaire pour se connecter à. À utiliser avec l’authentification `SingleOrg`. La valeur par défaut est `22222222-2222-2222-2222-222222222222`.

- **`--callback-path <PATH>`**

  Le chemin de demande dans le chemin de base de l’application de l’URI rediriger. À utiliser avec l’authentification `SingleOrg` ou `IndividualB2C`. La valeur par défaut est `/signin-oidc`.

- **`-r|--org-read-access`**

  Permet à cette application de lire l’accès à l’annuaire. S’applique uniquement à l’authentification `SingleOrg` ou `MultiOrg`.

- **`--exclude-launch-settings`**

  Exclut *le lancementSettings.json* du modèle généré.

- **`--no-https`**

  Éteint HTTPS. Cette option s’applique uniquement si `Individual`, `IndividualB2C`, `SingleOrg` ou `MultiOrg` ne sont pas utilisés.

- **`-uld|--use-local-db`**

  Spécifie LocalDB devrait être utilisé au lieu de SQLite. S’applique uniquement à l’authentification `Individual` ou `IndividualB2C`.

- **`-f|--framework <FRAMEWORK>`**

  Spécifie le [cadre](../../standard/frameworks.md) à cibler. Option disponible depuis .NET Core 3.0 SDK.

  Le tableau suivant répertorie les valeurs par défaut en fonction du numéro de version SDK que vous utilisez :

  | Version du SDK | Valeur par défaut   |
  |-------------|-----------------|
  | 3.1         | `netcoreapp3.1` |
  | 3.0         | `netcoreapp3.0` |

- **`--no-restore`**

  N’exécute pas une restauration implicite pendant la création du projet.

- **`--use-browserlink`**

  Inclut BrowserLink dans le projet. Option non disponible en .NET Core 2.2 et 3.1 SDK.

- **`-rrc|--razor-runtime-compilation`**

  Détermine si le projet est configuré pour utiliser [la compilation Razor runtime](/aspnet/core/mvc/views/view-compilation#runtime-compilation) dans les versions Debug. Option disponible depuis .NET Core 3.1 SDK.

***

### <a name="angular-react"></a><a name="spa"></a>angulaire, réagir

- **`-au|--auth <AUTHENTICATION_TYPE>`**

  Type d’authentification à utiliser. Option disponible à partir du kit SDK .NET Core 3.0.
  
  Les valeurs possibles sont les suivantes :

  - `None` : aucune authentification (configuration par défaut).
  - `Individual` : authentification individuelle.

- **`--exclude-launch-settings`**

  Exclut *le lancementSettings.json* du modèle généré.

- **`--no-restore`**

  N’exécute pas une restauration implicite pendant la création du projet.

- **`--no-https`**

  Éteint HTTPS. Cette option ne s’applique que si l’authentification est `None`.

- **`-uld|--use-local-db`**

  Spécifie LocalDB devrait être utilisé au lieu de SQLite. S’applique uniquement à l’authentification `Individual` ou `IndividualB2C`. Option disponible à partir du kit SDK .NET Core 3.0.

- **`-f|--framework <FRAMEWORK>`**

  Spécifie le [cadre](../../standard/frameworks.md) à cibler. Option non disponible en .NET Core 2.2 SDK.

  Le tableau suivant répertorie les valeurs par défaut en fonction du numéro de version SDK que vous utilisez :

  | Version du SDK | Valeur par défaut   |
  |-------------|-----------------|
  | 3.1         | `netcoreapp3.1` |
  | 3.0         | `netcoreapp3.0` |
  | 2.1         | `netcoreapp2.0` |

***

### <a name="reactredux"></a>reactredux

- **`--exclude-launch-settings`**

  Exclut *le lancementSettings.json* du modèle généré.

- **`-f|--framework <FRAMEWORK>`**

  Spécifie le [cadre](../../standard/frameworks.md) à cibler. Option non disponible en .NET Core 2.2 SDK.

  Le tableau suivant répertorie les valeurs par défaut en fonction du numéro de version SDK que vous utilisez :

  | Version du SDK | Valeur par défaut   |
  |-------------|-----------------|
  | 3.1         | `netcoreapp3.1` |
  | 3.0         | `netcoreapp3.0` |
  | 2.1         | `netcoreapp2.0` |

- **`--no-restore`**

  N’exécute pas une restauration implicite pendant la création du projet.

- **`--no-https`**

  Éteint HTTPS.

***

### <a name="razorclasslib"></a>razorclasslib

- **`--no-restore`**

  N’exécute pas une restauration implicite pendant la création du projet.

- **`-s|--support-pages-and-views`**

  Prend en charge l’ajout de pages et de vues traditionnelles razor en plus des composants de cette bibliothèque. Option disponible à partir du kit SDK .NET Core 3.0.

***
  
### <a name="webapi"></a>webapi

- **`-au|--auth <AUTHENTICATION_TYPE>`**

  Type d’authentification à utiliser. Les valeurs possibles sont les suivantes :

  - `None` : aucune authentification (configuration par défaut).
  - `IndividualB2C` : authentification individuelle avec Azure AD B2C.
  - `SingleOrg` : authentification d’organisation pour un seul abonné.
  - `Windows` : authentification Windows.

- **`--aad-b2c-instance <INSTANCE>`**

  L’instance Azure Active Directory B2C à connecter. À utiliser avec l’authentification `IndividualB2C`. La valeur par défaut est `https://login.microsoftonline.com/tfp/`.

- **`-ssp|--susi-policy-id <ID>`**

  L’id de la stratégie d’inscription et d’inscription pour ce projet. À utiliser avec l’authentification `IndividualB2C`.

- **`--aad-instance <INSTANCE>`**

  L’instance Azure Active Directory à connecter. À utiliser avec l’authentification `SingleOrg`. La valeur par défaut est `https://login.microsoftonline.com/`.

- **`--client-id <ID>`**

  L’ID client pour ce projet. À utiliser avec l’authentification `IndividualB2C` ou `SingleOrg`. La valeur par défaut est `11111111-1111-1111-11111111111111111`.

- **`--domain <DOMAIN>`**

  Le domaine pour le locataire de l’annuaire. À utiliser avec l’authentification `IndividualB2C` ou `SingleOrg`. La valeur par défaut est `qualified.domain.name`.

- **`--tenant-id <ID>`**

  L’ID TenantId de l’annuaire pour se connecter à. À utiliser avec l’authentification `SingleOrg`. La valeur par défaut est `22222222-2222-2222-2222-222222222222`.

- **`-r|--org-read-access`**

  Permet à cette application de lire l’accès à l’annuaire. Ne s’applique qu’à l’authentification. `SingleOrg`

- **`--exclude-launch-settings`**

  Exclut *le lancementSettings.json* du modèle généré.

- **`--no-https`**

  Éteint HTTPS. `app.UseHsts` et `app.UseHttpsRedirection` ne sont pas ajoutés à `Startup.Configure`. Cette option ne `IndividualB2C` `SingleOrg` s’applique que si l’authentification est utilisée ou non.

- **`-uld|--use-local-db`**

  Spécifie LocalDB devrait être utilisé au lieu de SQLite. Ne s’applique qu’à l’authentification. `IndividualB2C`

- **`-f|--framework <FRAMEWORK>`**

  Spécifie le [cadre](../../standard/frameworks.md) à cibler. Option non disponible en .NET Core 2.2 SDK.

  Le tableau suivant répertorie les valeurs par défaut en fonction du numéro de version SDK que vous utilisez :

  | Version du SDK | Valeur par défaut   |
  |-------------|-----------------|
  | 3.1         | `netcoreapp3.1` |
  | 3.0         | `netcoreapp3.0` |
  | 2.1         | `netcoreapp2.1` |

- **`--no-restore`**

  N’exécute pas une restauration implicite pendant la création du projet.

***

### <a name="globaljson"></a>globaljson

- **`--sdk-version <VERSION_NUMBER>`**

  Spécifie la version du .NET Core SDK à utiliser dans le fichier *global.json.*

***

## <a name="examples"></a>Exemples

- Créez un projet d’application console C# en spécifiant le nom du modèle :

  ```dotnetcli
  dotnet new "Console Application"
  ```

- Créez un projet d’application console F# dans le répertoire actif :

  ```dotnetcli
  dotnet new console -lang F#
  ```

- Créez un projet de bibliothèque de classe Standard .NET dans l’annuaire spécifié :

  ```dotnetcli
  dotnet new classlib -lang VB -o MyLibrary
  ```

- Créez un projet ASP.NET Core C# MVC dans le répertoire actif sans authentification :

  ```dotnetcli
  dotnet new mvc -au None
  ```

- Créez un projet xUnit :

  ```dotnetcli
  dotnet new xunit
  ```

- Énumérez tous les modèles disponibles pour les modèles d’application d’une page unique (SPA) :

  ```dotnetcli
  dotnet new spa -l
  ```

- Liste de tous les modèles correspondant à la sous-chaîne *we*. Aucune correspondance exacte n’a été trouvée, donc la recherche de sous-chaîne est exécutée sur les colonnes Nom court et Nom.

  ```dotnetcli
  dotnet new we -l
  ```

- Tentative d’appel du modèle correspondant à *ng*. Si aucune correspondance exacte n’est trouvée, listez les modèles qui correspondent partiellement.

  ```dotnetcli
  dotnet new ng
  ```

- Installer la version 2.0 des modèles SPA pour ASP.NET Core :

  ```dotnetcli
  dotnet new -i Microsoft.DotNet.Web.Spa.ProjectTemplates::2.0.0
  ```

- Énumérez les modèles et les détails installés à leur sujet, y compris la façon de les désinstaller :

  ```dotnetcli
  dotnet new -u
  ```

- Créez un *global.json* dans l’annuaire actuel définissant la version SDK à 3.1.101 :

  ```dotnetcli
  dotnet new globaljson --sdk-version 3.1.101
  ```

## <a name="see-also"></a>Voir aussi

- [Modèles personnalisés pour dotnet new](custom-templates.md)
- [Créer un modèle personnalisé pour dotnet new](../tutorials/cli-templates-create-item-template.md)
- [Dépôt GitHub dotnet/dotnet-template-samples](https://github.com/dotnet/dotnet-template-samples)
- [Modèles disponibles pour dotnet new](https://github.com/dotnet/templating/wiki/Available-templates-for-dotnet-new)
