---
title: Commande dotnet new
description: La commande dotnet new crée des projets .NET Core basés sur le modèle spécifié.
ms.date: 04/10/2020
ms.openlocfilehash: 1544f519f2a5f6a1a6e042c1db720eff45f5d98c
ms.sourcegitcommit: 7b1497c1927cb449cefd313bc5126ae37df30746
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/16/2020
ms.locfileid: "83442239"
---
# <a name="dotnet-new"></a>dotnet new

**Cet article s’applique à : ✔️ le kit de** développement logiciel (SDK) .net Core 2,0 et versions ultérieures

## <a name="name"></a>Nom

`dotnet new` : crée un projet, un fichier de configuration ou une solution en fonction du modèle spécifié.

## <a name="synopsis"></a>Synopsis

```dotnetcli
dotnet new <TEMPLATE> [--dry-run] [--force] [-i|--install {PATH|NUGET_ID}]
    [-lang|--language {"C#"|"F#"|VB}] [-n|--name <OUTPUT_NAME>]
    [--nuget-source <SOURCE>] [-o|--output <OUTPUT_DIRECTORY>]
    [-u|--uninstall] [--update-apply] [--update-check] [Template options]

dotnet new <TEMPLATE> [-l|--list] [--type <TYPE>]

dotnet new -h|--help
```

## <a name="description"></a>Description

La `dotnet new` commande crée un projet .net Core ou d’autres artefacts basés sur un modèle.

La commande appelle le [moteur de modèles](https://github.com/dotnet/templating) pour créer les artefacts sur le disque en fonction du modèle et des options spécifiés.

### <a name="implicit-restore"></a>Restauration implicite

[!INCLUDE[dotnet restore note](~/includes/dotnet-restore-note.md)]

## <a name="arguments"></a>Arguments

- **`TEMPLATE`**

  Modèle à instancier quand la commande est appelée. Vous pouvez passer des options spécifiques pour chaque modèle. Pour plus d'informations, consultez [Options de modèle](#template-options).

  Vous pouvez exécuter `dotnet new --list` ou `dotnet new -l` pour afficher la liste de tous les modèles installés. Si la `TEMPLATE` valeur ne correspond pas exactement au texte de la colonne **Templates** ou **Short Name** de la table retournée, une correspondance de sous-chaînes est effectuée sur ces deux colonnes.

  À compter du kit de développement logiciel (SDK) .NET Core 3,0, l’interface CLI recherche des modèles dans NuGet.org quand vous appelez la `dotnet new` commande dans les conditions suivantes :

  - Si l’interface CLI ne peut pas trouver de correspondance de modèle lors de l’appel `dotnet new` de, pas encore partiel.
  - Si une version plus récente du modèle est disponible. Dans ce cas, le projet ou l’artefact est créé, mais l’interface CLI vous avertit d’une version mise à jour du modèle.

  Le tableau suivant répertorie les modèles qui sont préinstallés avec le kit SDK .NET Core. Le langage par défaut pour le modèle est indiqué entre crochets. Cliquez sur le lien nom abrégé pour afficher les options de modèle spécifiques.

| Modèles                                    | Nom court                      | Langage     | Étiquettes                                  | Présent |
|----------------------------------------------|---------------------------------|--------------|---------------------------------------|------------|
| Application console                          | [Console](#console)             | [C#], F#, VB | Communes/Console                        | 1.0        |
| Bibliothèque de classes                                | [classlib](#classlib)           | [C#], F#, VB | Communes/Bibliothèque                        | 1.0        |
| Application WPF                              | [WPF](#wpf)                     | [C#]         | Commun/WPF                            | 3.0        |
| Bibliothèque de classes WPF                            | [wpflib](#wpf)                  | [C#]         | Commun/WPF                            | 3.0        |
| Bibliothèque de contrôles personnalisés WPF                   | [wpfcustomcontrollib](#wpf)     | [C#]         | Commun/WPF                            | 3.0        |
| Bibliothèque de contrôles utilisateur WPF                     | [wpfusercontrollib](#wpf)       | [C#]         | Commun/WPF                            | 3.0        |
| Application Windows Forms (WinForms)         | [WinForms](#winforms)           | [C#]         | Common/WinForms                       | 3.0        |
| Bibliothèque de classes Windows Forms (WinForms)       | [winformslib](#winforms)        | [C#]         | Common/WinForms                       | 3.0        |
| Service Worker                               | [collabor](#web-others)           | [C#]         | Commun/Worker/Web                     | 3.0        |
| Projet de test unitaire                            | [MSTest](#test)                 | [C#], F#, VB | Test/MSTest                           | 1.0        |
| Projet de test NUnit 3                         | [nunit](#nunit)                  | [C#], F#, VB | Test/NUnit                            | 2.1.400    |
| Élément de test NUnit 3                            | `nunit-test`                    | [C#], F#, VB | Test/NUnit                            | 2.2        |
| Projet de test xUnit                           | [xunit](#test)                  | [C#], F#, VB | Test/xUnit                            | 1.0        |
| Composant Razor                              | `razorcomponent`                | [C#]         | Web/ASP.NET                           | 3.0        |
| Page Razor                                   | [pagination](#page)                   | [C#]         | Web/ASP.NET                           | 2.0        |
| ViewImports MVC                              | [viewimports](#namespace)       | [C#]         | Web/ASP.NET                           | 2.0        |
| ViewStart MVC                                | `viewstart`                     | [C#]         | Web/ASP.NET                           | 2.0        |
| Application de serveur éblouissante                            | [blazorserver](#blazorserver)   | [C#]         | Web/éblouissant                            | 3.0        |
| ASP.NET Core vide                           | [Internet](#web)                     | [C#], F#     | Web/vides                             | 1.0        |
| Application web ASP.NET Core (Model-View-Controller) | [MVC](#web-options)             | [C#], F#     | Web/MVC                               | 1.0        |
| Application web ASP.NET Core                         | [webapp, Razor](#web-options)   | [C#]         | Web/MVC/Razor Pages                   | 2,2, 2,0   |
| ASP.NET Core avec Angular                    | [oblique](#spa)                 | [C#]         | Web/MVC/SPA                           | 2.0        |
| ASP.NET Core avec React.js                   | [réagir](#spa)                   | [C#]         | Web/MVC/SPA                           | 2.0        |
| ASP.NET Core avec React.js et Redux         | [reactredux](#reactredux)       | [C#]         | Web/MVC/SPA                           | 2.0        |
| Bibliothèque de classes Razor                          | [razorclasslib](#razorclasslib) | [C#]         | Web/Razor/Library/Bibliothèque de classes Razor | 2.1        |
| API web ASP.NET Core                         | [WebAPI](#webapi)               | [C#], F#     | Web/WebAPI                            | 1.0        |
| ASP.NET Core Service gRPC                    | [GRPC](#web-others)             | [C#]         | Web/gRPC                              | 3.0        |
| fichier gitignore dotnet                        | `gitignore`                     |              | Config                                | 3.0        |
| fichier global.json                             | [globaljson](#globaljson)       |              | Config                                | 2.0        |
| Configuration NuGet                                 | `nugetconfig`                   |              | Config                                | 1.0        |
| Fichier manifeste de l’outil local dotnet              | `tool-manifest`                 |              | Config                                | 3.0        |
| Configuration Web                                   | `webconfig`                     |              | Config                                | 1.0        |
| Fichier solution                                | `sln`                           |              | Solution                              | 1.0        |
| Fichier de mémoire tampon de protocole                         | [proto](#namespace)             |              | Web/gRPC                              | 3.0        |

## <a name="options"></a>Options

- **`--dry-run`**

  Affiche un récapitulatif de ce qui se passerait si la commande donnée était exécutée (si cela donnerait lieu à la création d’un modèle). Disponible depuis le kit de développement logiciel (SDK) .NET Core 2,2.

- **`--force`**

  Force le contenu à être généré même s’il change les fichiers existants. Cela est obligatoire lorsque le modèle choisi remplace les fichiers existants dans le répertoire de sortie.

- **`-h|--help`**

  Affiche l’aide pour la commande. Elle peut être appelée pour la `dotnet new` commande elle-même ou pour n’importe quel modèle. Par exemple : `dotnet new mvc --help`.

- **`-i|--install <PATH|NUGET_ID>`**

  Installe un pack de modèles à partir du `PATH` ou `NUGET_ID` fourni. Si vous souhaitez installer une préversion d’un package de modèle, vous devez spécifier la version au format `<package-name>::<package-version>`. Par défaut, `dotnet new` passe \* pour la version, qui représente la dernière version stable du package. Consultez un exemple dans la section [exemples](#examples) .
  
  Si une version du modèle a déjà été installée lorsque vous exécutez cette commande, le modèle sera mis à jour vers la version spécifiée, ou vers la version stable la plus récente si aucune version n’a été spécifiée.

  Pour plus d’informations sur la création de modèles personnalisés, consultez [Modèles personnalisés pour dotnet new](custom-templates.md).

- **`-l|--list`**

  Liste les modèles contenant le nom spécifié. Si aucun nom n’est spécifié, répertorie tous les modèles.

- **`-lang|--language {C#|F#|VB}`**

  Langage du modèle à créer. Le langage accepté diffère selon le modèle (voir les valeurs par défaut dans la section [arguments](#arguments)). Non valide pour certains modèles.

  > [!NOTE]
  > Certains interpréteurs interprètent la commande `#` comme un caractère spécial. Dans ce cas, mettez la valeur du paramètre de langue entre guillemets. Par exemple : `dotnet new console -lang "F#"`.

- **`-n|--name <OUTPUT_NAME>`**

  Le nom de la sortie créée. Si aucun nom n’est spécifié, le nom du répertoire actif est utilisé.

- **`--nuget-source <SOURCE>`**

  Spécifie une source NuGet à utiliser pendant l’installation. Disponible depuis le kit de développement logiciel (SDK) .NET Core 2,1.

- **`-o|--output <OUTPUT_DIRECTORY>`**

  Emplacement où placer la sortie générée. L'emplacement par défaut est le répertoire actif.

- **`--type <TYPE>`**

  Filtre les modèles en fonction des types disponibles. Les valeurs prédéfinies sont `project` , `item` et `other` .

- **`-u|--uninstall [PATH|NUGET_ID]`**

  Désinstalle un pack de modèles au niveau de `PATH` ou `NUGET_ID` fourni. Lorsque la `<PATH|NUGET_ID>` valeur n’est pas spécifiée, tous les packs de modèles actuellement installés et leurs modèles associés sont affichés. Lorsque vous spécifiez `NUGET_ID` , n’incluez pas le numéro de version.

  Si vous ne spécifiez pas de paramètre pour cette option, la commande répertorie les modèles installés et fournit des détails à leur sujet.

  > [!NOTE]
  > Pour désinstaller un modèle à l’aide de `PATH`, vous devez qualifier le chemin d’accès avec un nom complet. Par exemple, *C:/Users/ \< User>/documents/templates/garciasoftware.consoletemplate.CSharp* fonctionnera, mais *./GarciaSoftware.ConsoleTemplate.CSharp* à partir du dossier conteneur ne le sera pas.
  > N’incluez pas de barre oblique finale de répertoire finale dans le chemin d’accès de votre modèle.

- **`--update-apply`**

  Vérifie si des mises à jour sont disponibles pour les packs de modèles qui sont actuellement installés et les installe. Option disponible à partir du kit SDK .NET Core 3.0.

- **`--update-check`**

  Vérifie si des mises à jour sont disponibles pour les packs de modèles qui sont actuellement installés. Option disponible à partir du kit SDK .NET Core 3.0.

## <a name="template-options"></a>Options de modèle

Chaque modèle de projet peut présenter d’autres options disponibles. Les modèles de base ont les options supplémentaires suivantes :

### <a name="console"></a>console

- **`-f|--framework <FRAMEWORK>`**

  Spécifie le [Framework](../../standard/frameworks.md) à cibler. Option disponible à partir du kit SDK .NET Core 3.0.

  Le tableau suivant répertorie les valeurs par défaut en fonction du numéro de version du kit de développement logiciel (SDK) que vous utilisez :

  | Version du SDK | Valeur par défaut   |
  |-------------|-----------------|
  | 3.1         | `netcoreapp3.1` |
  | 3.0         | `netcoreapp3.0` |

- **`--langVersion <VERSION_NUMBER>`**

  Définit la `LangVersion` propriété dans le fichier projet créé. Par exemple, choisissez `--langVersion 7.3` pour utiliser C# 7.3. Non pris en charge pour F#. Disponible depuis le kit de développement logiciel (SDK) .NET Core 2,2.

  Pour obtenir la liste des versions C# par défaut, consultez [valeurs par défaut](../../csharp/language-reference/configure-language-version.md#defaults).

- **`--no-restore`**

  S’il est spécifié, n’exécute pas de restauration implicite pendant la création du projet. Disponible depuis le kit de développement logiciel (SDK) .NET Core 2,2.

***

### <a name="classlib"></a>classlib

- **`-f|--framework <FRAMEWORK>`**

  Spécifie le [Framework](../../standard/frameworks.md) à cibler. Valeurs : `netcoreapp<version>` pour créer une bibliothèque de classes .NET Core ou `netstandard<version>` pour créer une bibliothèque de classes .NET Standard. La valeur par défaut est `netstandard2.0`.

- **`--langVersion <VERSION_NUMBER>`**

  Définit la `LangVersion` propriété dans le fichier projet créé. Par exemple, choisissez `--langVersion 7.3` pour utiliser C# 7.3. Non pris en charge pour F#. Disponible depuis le kit de développement logiciel (SDK) .NET Core 2,2.

  Pour obtenir la liste des versions C# par défaut, consultez [valeurs par défaut](../../csharp/language-reference/configure-language-version.md#defaults).

- **`--no-restore`**

  N’exécute pas de restauration implicite pendant la création du projet.

***

### <a name="wpf-wpflib-wpfcustomcontrollib-wpfusercontrollib"></a><a name="wpf"></a>WPF, wpflib, wpfcustomcontrollib, wpfusercontrollib

- **`-f|--framework <FRAMEWORK>`**

  Spécifie le [Framework](../../standard/frameworks.md) à cibler. La valeur par défaut est `netcoreapp3.1`. Disponible depuis le kit de développement logiciel (SDK) .NET Core 3,1.

- **`--langVersion <VERSION_NUMBER>`**

  Définit la `LangVersion` propriété dans le fichier projet créé. Par exemple, choisissez `--langVersion 7.3` pour utiliser C# 7.3.

  Pour obtenir la liste des versions C# par défaut, consultez [valeurs par défaut](../../csharp/language-reference/configure-language-version.md#defaults).

- **`--no-restore`**

  N’exécute pas de restauration implicite pendant la création du projet.

***

### <a name="winforms-winformslib"></a><a name="winforms"></a>WinForms, winformslib

- **`--langVersion <VERSION_NUMBER>`**

  Définit la `LangVersion` propriété dans le fichier projet créé. Par exemple, choisissez `--langVersion 7.3` pour utiliser C# 7.3.

  Pour obtenir la liste des versions C# par défaut, consultez [valeurs par défaut](../../csharp/language-reference/configure-language-version.md#defaults).

- **`--no-restore`**

  N’exécute pas de restauration implicite pendant la création du projet.

***

### <a name="worker-grpc"></a><a name="web-others"></a>Worker, GRPC

- **`-f|--framework <FRAMEWORK>`**

  Spécifie le [Framework](../../standard/frameworks.md) à cibler. La valeur par défaut est `netcoreapp3.1`. Disponible depuis le kit de développement logiciel (SDK) .NET Core 3,1.

- **`--exclude-launch-settings`**

  Exclut *launchSettings. JSON* du modèle généré.

- **`--no-restore`**

  N’exécute pas de restauration implicite pendant la création du projet.

***

### <a name="mstest-xunit"></a><a name="test"></a>MSTest, xUnit

- **`-f|--framework <FRAMEWORK>`**

  Spécifie le [Framework](../../standard/frameworks.md) à cibler. Option disponible depuis le kit de développement logiciel (SDK) .NET Core 3,0.

  Le tableau suivant répertorie les valeurs par défaut en fonction du numéro de version du kit de développement logiciel (SDK) que vous utilisez :

  | Version du SDK | Valeur par défaut   |
  |-------------|-----------------|
  | 3.1         | `netcoreapp3.1` |
  | 3.0         | `netcoreapp3.0` |

- **`-p|--enable-pack`**

  Active l’empaquetage pour le projet à l’aide de [dotnet Pack](dotnet-pack.md).

- **`--no-restore`**

  N’exécute pas de restauration implicite pendant la création du projet.

***

### <a name="nunit"></a>nunit

- **`-f|--framework <FRAMEWORK>`**

  Spécifie le [Framework](../../standard/frameworks.md) à cibler.

  Le tableau suivant répertorie les valeurs par défaut en fonction du numéro de version du kit de développement logiciel (SDK) que vous utilisez :

  | Version du SDK | Valeur par défaut   |
  |-------------|-----------------|
  | 3.1         | `netcoreapp3.1` |
  | 3.0         | `netcoreapp3.0` |
  | 2.2         | `netcoreapp2.2` |
  | 2.1         | `netcoreapp2.1` |

- **`-p|--enable-pack`**

  Active l’empaquetage pour le projet à l’aide de [dotnet Pack](dotnet-pack.md).

- **`--no-restore`**

  N’exécute pas de restauration implicite pendant la création du projet.

***

### <a name="page"></a>page

- **`-na|--namespace <NAMESPACE_NAME>`**

  Espace de noms pour le code généré. La valeur par défaut est `MyApp.Namespace`.

- **`-np|--no-pagemodel`**

  Crée la page sans PageModel.

***

### <a name="viewimports-proto"></a><a name="namespace"></a>viewimports, proto

- **`-na|--namespace <NAMESPACE_NAME>`**

  Espace de noms pour le code généré. La valeur par défaut est `MyApp.Namespace`.

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

  Instance Azure Active Directory B2C à laquelle se connecter. À utiliser avec l’authentification `IndividualB2C`. La valeur par défaut est `https://login.microsoftonline.com/tfp/`.

- **`-ssp|--susi-policy-id <ID>`**

  ID de la stratégie de connexion et d’inscription pour ce projet. À utiliser avec l’authentification `IndividualB2C`.

- **`-rp|--reset-password-policy-id <ID>`**

  ID de la stratégie de réinitialisation du mot de passe pour ce projet. À utiliser avec l’authentification `IndividualB2C`.

- **`-ep|--edit-profile-policy-id <ID>`**

  ID de stratégie de modification de profil pour ce projet. À utiliser avec l’authentification `IndividualB2C`.

- **`--aad-instance <INSTANCE>`**

  Instance Azure Active Directory à laquelle se connecter. À utiliser avec l’authentification `SingleOrg` ou `MultiOrg`. La valeur par défaut est `https://login.microsoftonline.com/`.

- **`--client-id <ID>`**

  ID client pour ce projet. À utiliser avec l’authentification `IndividualB2C`, `SingleOrg` ou `MultiOrg`. La valeur par défaut est `11111111-1111-1111-11111111111111111`.

- **`--domain <DOMAIN>`**

  Domaine du locataire d’annuaire. À utiliser avec l’authentification `SingleOrg` ou `IndividualB2C`. La valeur par défaut est `qualified.domain.name`.

- **`--tenant-id <ID>`**

  ID TenantId de l’annuaire auquel se connecter. À utiliser avec l’authentification `SingleOrg`. La valeur par défaut est `22222222-2222-2222-2222-222222222222`.

- **`--callback-path <PATH>`**

  Chemin d’accès de la requête dans le chemin d’accès de base de l’application de l’URI de redirection. À utiliser avec l’authentification `SingleOrg` ou `IndividualB2C`. La valeur par défaut est `/signin-oidc`.

- **`-r|--org-read-access`**

  Permet à cette application d’accéder en lecture à l’annuaire. S’applique uniquement à l’authentification `SingleOrg` ou `MultiOrg`.

- **`--exclude-launch-settings`**

  Exclut *launchSettings. JSON* du modèle généré.

- **`--no-https`**

  Désactive le protocole HTTPs. Cette option s’applique uniquement si `Individual` , `IndividualB2C` , `SingleOrg` ou `MultiOrg` ne sont pas utilisés pour `--auth` .

- **`-uld|--use-local-db`**

  Spécifie que la base de données locale doit être utilisée à la place de SQLite. S’applique uniquement à l’authentification `Individual` ou `IndividualB2C`.

- **`--no-restore`**

  N’exécute pas de restauration implicite pendant la création du projet.

***

### <a name="web"></a>web

- **`--exclude-launch-settings`**

  Exclut *launchSettings. JSON* du modèle généré.

- **`-f|--framework <FRAMEWORK>`**

  Spécifie le [Framework](../../standard/frameworks.md) à cibler. Option non disponible dans le kit de développement logiciel (SDK) .NET Core 2,2.

  Le tableau suivant répertorie les valeurs par défaut en fonction du numéro de version du kit de développement logiciel (SDK) que vous utilisez :

  | Version du SDK | Valeur par défaut   |
  |-------------|-----------------|
  | 3.1         | `netcoreapp3.1` |
  | 3.0         | `netcoreapp3.0` |
  | 2.1         | `netcoreapp2.1` |

- **`--no-restore`**

  N’exécute pas de restauration implicite pendant la création du projet.

- **`--no-https`**

  Désactive le protocole HTTPs.

***

### <a name="mvc-webapp"></a><a name="web-options"></a>MVC, WebApp

- **`-au|--auth <AUTHENTICATION_TYPE>`**

  Type d’authentification à utiliser. Les valeurs possibles sont les suivantes :

  - `None` : aucune authentification (configuration par défaut).
  - `Individual` : authentification individuelle.
  - `IndividualB2C` : authentification individuelle avec Azure AD B2C.
  - `SingleOrg` : authentification d’organisation pour un seul abonné.
  - `MultiOrg` : authentification d’organisation pour plusieurs abonnés.
  - `Windows` : authentification Windows.

- **`--aad-b2c-instance <INSTANCE>`**

  Instance Azure Active Directory B2C à laquelle se connecter. À utiliser avec l’authentification `IndividualB2C`. La valeur par défaut est `https://login.microsoftonline.com/tfp/`.

- **`-ssp|--susi-policy-id <ID>`**

  ID de la stratégie de connexion et d’inscription pour ce projet. À utiliser avec l’authentification `IndividualB2C`.

- **`-rp|--reset-password-policy-id <ID>`**

  ID de la stratégie de réinitialisation du mot de passe pour ce projet. À utiliser avec l’authentification `IndividualB2C`.

- **`-ep|--edit-profile-policy-id <ID>`**

  ID de stratégie de modification de profil pour ce projet. À utiliser avec l’authentification `IndividualB2C`.

- **`--aad-instance <INSTANCE>`**

  Instance Azure Active Directory à laquelle se connecter. À utiliser avec l’authentification `SingleOrg` ou `MultiOrg`. La valeur par défaut est `https://login.microsoftonline.com/`.

- **`--client-id <ID>`**

  ID client pour ce projet. À utiliser avec l’authentification `IndividualB2C`, `SingleOrg` ou `MultiOrg`. La valeur par défaut est `11111111-1111-1111-11111111111111111`.

- **`--domain <DOMAIN>`**

  Domaine du locataire d’annuaire. À utiliser avec l’authentification `SingleOrg` ou `IndividualB2C`. La valeur par défaut est `qualified.domain.name`.

- **`--tenant-id <ID>`**

  ID TenantId de l’annuaire auquel se connecter. À utiliser avec l’authentification `SingleOrg`. La valeur par défaut est `22222222-2222-2222-2222-222222222222`.

- **`--callback-path <PATH>`**

  Chemin d’accès de la requête dans le chemin d’accès de base de l’application de l’URI de redirection. À utiliser avec l’authentification `SingleOrg` ou `IndividualB2C`. La valeur par défaut est `/signin-oidc`.

- **`-r|--org-read-access`**

  Permet à cette application d’accéder en lecture à l’annuaire. S’applique uniquement à l’authentification `SingleOrg` ou `MultiOrg`.

- **`--exclude-launch-settings`**

  Exclut *launchSettings. JSON* du modèle généré.

- **`--no-https`**

  Désactive le protocole HTTPs. Cette option s’applique uniquement si `Individual`, `IndividualB2C`, `SingleOrg` ou `MultiOrg` ne sont pas utilisés.

- **`-uld|--use-local-db`**

  Spécifie que la base de données locale doit être utilisée à la place de SQLite. S’applique uniquement à l’authentification `Individual` ou `IndividualB2C`.

- **`-f|--framework <FRAMEWORK>`**

  Spécifie le [Framework](../../standard/frameworks.md) à cibler. Option disponible depuis le kit de développement logiciel (SDK) .NET Core 3,0.

  Le tableau suivant répertorie les valeurs par défaut en fonction du numéro de version du kit de développement logiciel (SDK) que vous utilisez :

  | Version du SDK | Valeur par défaut   |
  |-------------|-----------------|
  | 3.1         | `netcoreapp3.1` |
  | 3.0         | `netcoreapp3.0` |

- **`--no-restore`**

  N’exécute pas de restauration implicite pendant la création du projet.

- **`--use-browserlink`**

  Comprend BrowserLink dans le projet. Option non disponible dans le kit de développement logiciel (SDK) .NET Core 2,2 et 3,1.

- **`-rrc|--razor-runtime-compilation`**

  Détermine si le projet est configuré pour utiliser la [compilation du runtime Razor](/aspnet/core/mvc/views/view-compilation#runtime-compilation) dans les versions Debug. Option disponible depuis le kit de développement logiciel (SDK) 3.1.201 .NET Core.

***

### <a name="angular-react"></a><a name="spa"></a>angulaire, réaction

- **`-au|--auth <AUTHENTICATION_TYPE>`**

  Type d’authentification à utiliser. Option disponible à partir du kit SDK .NET Core 3.0.
  
  Les valeurs possibles sont les suivantes :

  - `None` : aucune authentification (configuration par défaut).
  - `Individual` : authentification individuelle.

- **`--exclude-launch-settings`**

  Exclut *launchSettings. JSON* du modèle généré.

- **`--no-restore`**

  N’exécute pas de restauration implicite pendant la création du projet.

- **`--no-https`**

  Désactive le protocole HTTPs. Cette option s’applique uniquement si l’authentification est `None` .

- **`-uld|--use-local-db`**

  Spécifie que la base de données locale doit être utilisée à la place de SQLite. S’applique uniquement à l’authentification `Individual` ou `IndividualB2C`. Option disponible à partir du kit SDK .NET Core 3.0.

- **`-f|--framework <FRAMEWORK>`**

  Spécifie le [Framework](../../standard/frameworks.md) à cibler. Option non disponible dans le kit de développement logiciel (SDK) .NET Core 2,2.

  Le tableau suivant répertorie les valeurs par défaut en fonction du numéro de version du kit de développement logiciel (SDK) que vous utilisez :

  | Version du SDK | Valeur par défaut   |
  |-------------|-----------------|
  | 3.1         | `netcoreapp3.1` |
  | 3.0         | `netcoreapp3.0` |
  | 2.1         | `netcoreapp2.0` |

***

### <a name="reactredux"></a>reactredux

- **`--exclude-launch-settings`**

  Exclut *launchSettings. JSON* du modèle généré.

- **`-f|--framework <FRAMEWORK>`**

  Spécifie le [Framework](../../standard/frameworks.md) à cibler. Option non disponible dans le kit de développement logiciel (SDK) .NET Core 2,2.

  Le tableau suivant répertorie les valeurs par défaut en fonction du numéro de version du kit de développement logiciel (SDK) que vous utilisez :

  | Version du SDK | Valeur par défaut   |
  |-------------|-----------------|
  | 3.1         | `netcoreapp3.1` |
  | 3.0         | `netcoreapp3.0` |
  | 2.1         | `netcoreapp2.0` |

- **`--no-restore`**

  N’exécute pas de restauration implicite pendant la création du projet.

- **`--no-https`**

  Désactive le protocole HTTPs.

***

### <a name="razorclasslib"></a>razorclasslib

- **`--no-restore`**

  N’exécute pas de restauration implicite pendant la création du projet.

- **`-s|--support-pages-and-views`**

  Prend en charge l’ajout de pages et de vues Razor traditionnelles en plus des composants de cette bibliothèque. Option disponible à partir du kit SDK .NET Core 3.0.

***
  
### <a name="webapi"></a>webapi

- **`-au|--auth <AUTHENTICATION_TYPE>`**

  Type d’authentification à utiliser. Les valeurs possibles sont les suivantes :

  - `None` : aucune authentification (configuration par défaut).
  - `IndividualB2C` : authentification individuelle avec Azure AD B2C.
  - `SingleOrg` : authentification d’organisation pour un seul abonné.
  - `Windows` : authentification Windows.

- **`--aad-b2c-instance <INSTANCE>`**

  Instance Azure Active Directory B2C à laquelle se connecter. À utiliser avec l’authentification `IndividualB2C`. La valeur par défaut est `https://login.microsoftonline.com/tfp/`.

- **`-ssp|--susi-policy-id <ID>`**

  ID de la stratégie de connexion et d’inscription pour ce projet. À utiliser avec l’authentification `IndividualB2C`.

- **`--aad-instance <INSTANCE>`**

  Instance Azure Active Directory à laquelle se connecter. À utiliser avec l’authentification `SingleOrg`. La valeur par défaut est `https://login.microsoftonline.com/`.

- **`--client-id <ID>`**

  ID client pour ce projet. À utiliser avec l’authentification `IndividualB2C` ou `SingleOrg`. La valeur par défaut est `11111111-1111-1111-11111111111111111`.

- **`--domain <DOMAIN>`**

  Domaine du locataire d’annuaire. À utiliser avec l’authentification `IndividualB2C` ou `SingleOrg`. La valeur par défaut est `qualified.domain.name`.

- **`--tenant-id <ID>`**

  ID TenantId de l’annuaire auquel se connecter. À utiliser avec l’authentification `SingleOrg`. La valeur par défaut est `22222222-2222-2222-2222-222222222222`.

- **`-r|--org-read-access`**

  Permet à cette application d’accéder en lecture à l’annuaire. S’applique uniquement à `SingleOrg` l’authentification.

- **`--exclude-launch-settings`**

  Exclut *launchSettings. JSON* du modèle généré.

- **`--no-https`**

  Désactive le protocole HTTPs. `app.UseHsts` et `app.UseHttpsRedirection` ne sont pas ajoutés à `Startup.Configure`. Cette option s’applique uniquement si `IndividualB2C` ou `SingleOrg` ne sont pas utilisés pour l’authentification.

- **`-uld|--use-local-db`**

  Spécifie que la base de données locale doit être utilisée à la place de SQLite. S’applique uniquement à `IndividualB2C` l’authentification.

- **`-f|--framework <FRAMEWORK>`**

  Spécifie le [Framework](../../standard/frameworks.md) à cibler. Option non disponible dans le kit de développement logiciel (SDK) .NET Core 2,2.

  Le tableau suivant répertorie les valeurs par défaut en fonction du numéro de version du kit de développement logiciel (SDK) que vous utilisez :

  | Version du SDK | Valeur par défaut   |
  |-------------|-----------------|
  | 3.1         | `netcoreapp3.1` |
  | 3.0         | `netcoreapp3.0` |
  | 2.1         | `netcoreapp2.1` |

- **`--no-restore`**

  N’exécute pas de restauration implicite pendant la création du projet.

***

### <a name="globaljson"></a>globaljson

- **`--sdk-version <VERSION_NUMBER>`**

  Spécifie la version de la kit SDK .NET Core à utiliser dans le fichier *global. JSON* .

***

## <a name="examples"></a>Exemples

- Créez un projet d’application console C# en spécifiant le nom du modèle :

  ```dotnetcli
  dotnet new "Console Application"
  ```

- Créez un projet d’application console F# dans le répertoire actif :

  ```dotnetcli
  dotnet new console -lang "F#"
  ```

- Créez un projet de bibliothèque de classes .NET Standard dans le répertoire spécifié :

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

- Répertorier tous les modèles disponibles pour les modèles d’application à page unique (SPA) :

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

- Installez la version 2,0 des modèles SPA pour ASP.NET Core :

  ```dotnetcli
  dotnet new -i Microsoft.DotNet.Web.Spa.ProjectTemplates::2.0.0
  ```

- Répertoriez les modèles installés et les détails les concernant, notamment comment les désinstaller :

  ```dotnetcli
  dotnet new -u
  ```

- Créez un *global. JSON* dans le répertoire actif en définissant la version du kit de développement logiciel (SDK) sur 3.1.101 :

  ```dotnetcli
  dotnet new globaljson --sdk-version 3.1.101
  ```

## <a name="see-also"></a>Voir aussi

- [Modèles personnalisés pour dotnet new](custom-templates.md)
- [Créer un modèle personnalisé pour dotnet new](../tutorials/cli-templates-create-item-template.md)
- [Dépôt GitHub dotnet/dotnet-template-samples](https://github.com/dotnet/dotnet-template-samples)
- [Modèles disponibles pour dotnet new](https://github.com/dotnet/templating/wiki/Available-templates-for-dotnet-new)
