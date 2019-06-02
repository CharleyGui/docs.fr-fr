---
title: Créer un modèle personnalisé pour dotnet new
description: Découvrez comment créer un modèle personnalisé pour la commande dotnet new dans ce didacticiel amusant.
author: mairaw
ms.date: 08/12/2017
ms.custom: seodec18
ms.openlocfilehash: e47da048584ec31c275ff9c122d157f34556268a
ms.sourcegitcommit: 621a5f6df00152006160987395b93b5b55f7ffcd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66299957"
---
# <a name="create-a-custom-template-for-dotnet-new"></a>Créer un modèle personnalisé pour dotnet new

Ce didacticiel vous montre comment effectuer les opérations suivantes :

- Créer un modèle de base à partir d’un projet existant ou d’un nouveau projet d’application console
- Empaqueter le modèle à des fins de distribution sur nuget.org ou à partir d’un fichier *nupkg* local
- Installer le modèle à partir de nuget.org, d’un fichier *nupkg* local ou du système de fichiers local
- Désinstaller le modèle

Si vous préférez poursuivre le didacticiel avec un exemple complet, téléchargez [l’exemple de modèle de projet](https://github.com/dotnet/dotnet-template-samples/tree/master/16-nuget-package). L’exemple de modèle est configuré pour une distribution NuGet.

Si vous souhaitez utiliser l’exemple téléchargé avec une distribution à partir du système de fichiers, effectuez les opérations suivantes :

- Remontez le contenu du dossier *content* de l’exemple d’un niveau jusqu’au dossier *GarciaSoftware.ConsoleTemplate.CSharp*.
- Supprimez le dossier *content* vide.
- Supprimez le fichier *nuspec*.

## <a name="prerequisites"></a>Prérequis

- Installez le [SDK .NET Core 2.0](https://www.microsoft.com/net/core) ou ultérieur.
- Lisez la rubrique de référence [Modèles personnalisés pour dotnet new](../tools/custom-templates.md).

## <a name="create-a-template-from-a-project"></a>Créer un modèle à partir d’un projet

Utilisez un projet existant dont vous savez qu’il peut être compilé et exécuté, ou créez un projet d’application console dans un dossier de votre disque dur. Ce didacticiel suppose que le dossier de projet porte le nom *GarciaSoftware.ConsoleTemplate.CSharp* et qu’il est stocké à l’emplacement *Documents\Templates* dans le profil de l’utilisateur. Le nom du modèle de projet du didacticiel est au format *\<nom de la société>.\<type de modèle>.\<langage de programmation>* , mais vous êtes libre de nommer votre projet et votre modèle comme vous le souhaitez.

1. Ajoutez un dossier nommé *.template.config* à la racine du projet.
1. Dans le dossier *.template.config*, créez un fichier *template.json* pour configurer votre modèle. Pour obtenir plus d’informations et connaître les définitions de membre du fichier *template.json*, consultez la rubrique [Modèles personnalisés pour dotnet new](../tools/custom-templates.md#templatejson) et le schéma [*template.json* dans le magasin de schémas JSON](http://json.schemastore.org/template).

```json
{
    "$schema": "http://json.schemastore.org/template",
    "author": "Catalina Garcia",
    "classifications": [ "Common", "Console" ],
    "identity": "GarciaSoftware.ConsoleTemplate.CSharp",
    "name": "Garcia Software Console Application",
    "shortName": "garciaconsole"
}
```

Le modèle est terminé. À ce stade, vous avez deux options pour distribuer le modèle. Pour continuer ce didacticiel, choisissez l’une des deux procédures suivantes :

1. [Distribution NuGet](#use-nuget-distribution) : installer le modèle à partir de NuGet ou du fichier local *nupkg*, et utiliser le modèle installé.
2. [Distribution à partir du système de fichiers](#use-file-system-distribution).

## <a name="use-nuget-distribution"></a>Utiliser la distribution NuGet

### <a name="pack-the-template-into-a-nuget-package"></a>Empaqueter le modèle dans un package NuGet

1. Créez un dossier pour le package NuGet. Pour le didacticiel, le nom de dossier *GarciaSoftware.ConsoleTemplate.CSharp* est utilisé, et le dossier est créé dans un dossier *Documents\NuGetTemplates* du profil de l’utilisateur. Créez un dossier nommé *content* dans le nouveau dossier de modèle pour y stocker les fichiers projet.
1. Copiez le contenu du dossier de votre projet, avec son fichier *.template.config/template.json*, dans le dossier *content* que vous avez créé.
1. À côté du dossier *content*, ajoutez un fichier [*nuspec*](/nuget/create-packages/creating-a-package). Le fichier nuspec est un fichier manifeste XML qui décrit le contenu d’un package et pilote le processus de création du package NuGet.

   ![Structure de répertoires représentant la disposition du package NuGet](./media/create-custom-template/nuget-directory-layout.png)

1. À l’intérieur d’un élément **\<packageTypes>** dans le fichier *nuspec*, ajoutez un élément **\<packageType>** avec une valeur d’attribut `name` de `Template`. Le dossier *content* et le fichier *nuspec* doivent être tous les deux dans le même répertoire. Le tableau indique les éléments du fichier *nuspec* indispensables pour produire un modèle sous forme de package NuGet.

   | Élément            | Type   | Description |
   | ------------------ | ------ | ----------- |
   | **\<authors>**     | string | Liste séparée par des virgules des auteurs de packages, qui correspondent aux noms de profil sur nuget.org. Les auteurs sont affichés dans la galerie NuGet sur nuget.org et servent à croiser les références des packages de mêmes auteurs. |
   | **\<description>** | string | Description longue du package pour l’affichage de l’interface utilisateur. |
   | **\<id>**          | string | Identificateur de package respectant la casse, qui doit être unique dans nuget.org ou dans toute autre galerie susceptible de l’héberger. Les ID ne peuvent pas contenir d’espaces ou de caractères qui ne sont pas valides pour une URL et suivent généralement les règles d’espace de noms .NET. Pour obtenir des conseils, consultez [Choix d’un identificateur de package unique et définition du numéro de version](/nuget/create-packages/creating-a-package#choosing-a-unique-package-identifier-and-setting-the-version-number). |
   | **\<packageType>** | string | Placez cet élément à l’intérieur d’un élément **\<packageTypes>** parmi les éléments **\<metadata>** . Affectez à l’attribut `name` de l’élément **\<packageType>** la valeur `Template`. |
   | **\<version>**     | string | Version du package, selon le format version_principale.version_secondaire.version_corrective. Les numéros de version peuvent inclure un suffixe de préversion comme décrit dans [Préversions](/nuget/create-packages/prerelease-packages#semantic-versioning). |

   Consultez les [informations de référence sur .nuspec](/nuget/schema/nuspec) pour connaître le schéma du fichier *nuspec*.

   Le fichier *nuspec* utilisé dans ce didacticiel est nommé *GarciaSoftware.ConsoleTemplate.CSharp.nuspec* et présente le contenu suivant :

   ```xml
   <?xml version="1.0" encoding="utf-8"?>
   <package xmlns="http://schemas.microsoft.com/packaging/2012/06/nuspec.xsd">
     <metadata>
       <id>GarciaSoftware.ConsoleTemplate.CSharp</id>
       <version>1.0.0</version>
       <description>
         Creates the Garcia Software console app.
       </description>
       <authors>Catalina Garcia</authors>
       <packageTypes>
         <packageType name="Template" />
       </packageTypes>
     </metadata>
   </package>
   ```

1. [Créez le package](/nuget/create-packages/creating-a-package#creating-the-package) à l’aide de la commande `nuget pack <PATH_TO_NUSPEC_FILE>`. La commande suivante suppose que le dossier qui contient les composants NuGet se trouve à l’emplacement *C:\Users\\\<USER>\Documents\Templates\GarciaSoftware.ConsoleTemplate.CSharp*. Toutefois, où que vous placiez le dossier sur votre système, la commande `nuget pack` accepte le chemin du fichier *nuspec* :

   ```console
   nuget pack C:\Users\<USER>\Documents\NuGetTemplates\GarciaSoftware.ConsoleTemplate.CSharp\GarciaSoftware.ConsoleTemplate.CSharp.nuspec
   ```

### <a name="publishing-the-package-to-nugetorg"></a>Publication du package sur nuget.org

Pour publier un package NuGet, suivez les instructions de la rubrique [Créer et publier un package](/nuget/quickstart/create-and-publish-a-package#publish-the-package). Cela dit, nous vous recommandons de ne pas publier le modèle du didacticiel sur NuGet, car une fois publié, il ne peut pas être supprimé, mais seulement retiré. Le package NuGet se présentant désormais sous la forme d’un fichier *nupkg*, nous vous suggérons de suivre les instructions ci-dessous pour installer le modèle directement à partir du fichier *nupkg* local.

### <a name="install-the-template-from-a-nuget-package"></a>Installer le modèle à partir d’un package NuGet

#### <a name="install-the-template-from-the-local-nupkg-file"></a>Installer le modèle à partir du fichier *nupkg* local

Pour installer le modèle à partir du fichier *nupkg* que vous avez créé, utilisez la commande `dotnet new` avec l’option `-i|--install` et indiquez le chemin du fichier *nupkg* :

```console
dotnet new -i C:\Users\<USER>\GarciaSoftware.ConsoleTemplate.CSharp.1.0.0.nupkg
```

#### <a name="install-the-template-from-a-nuget-package-stored-at-nugetorg"></a>Installer le modèle à partir d’un package NuGet stocké sur nuget.org

Si vous souhaitez installer un modèle à partir d’un package NuGet stocké sur nuget.org, utilisez la commande `dotnet new` avec l’option `-i|--install` et indiquez le nom du package NuGet :

```console
dotnet new -i GarciaSoftware.ConsoleTemplate.CSharp
```

> [!NOTE]
> L’exemple est fourni à des fins de démonstration uniquement. Aucun package NuGet `GarciaSoftware.ConsoleTemplate.CSharp` n’existe sur nuget.org, et nous vous déconseillons de publier et de consommer des modèles de test à partir de NuGet. Si vous exécutez la commande, aucun modèle n’est installé. Toutefois, vous pouvez installer un modèle qui n’a pas été publié sur nuget.org en référençant le fichier *nupkg* directement sur votre système de fichiers local, comme indiqué dans la section précédente [Installer le modèle à partir du fichier nupkg local](#install-the-template-from-the-local-nupkg-file).

Si vous souhaitez un exemple concret d’installation d’un modèle à partir d’un package sur nuget.org, vous pouvez utiliser le [modèle NUnit 3 pour dotnet-new](https://www.nuget.org/packages/NUnit3.DotNetNew.Template/). Ce modèle définit un projet pour utiliser des tests unitaires NUnit. Utilisez la commande suivante pour l’installer :

```console
dotnet new -i NUnit3.DotNetNew.Template
```

Quand vous affichez la liste des modèles avec `dotnet new -l`, le *projet de test NUnit 3* apparaît sous la forme abrégée *nunit*. Vous êtes prêt à utiliser le modèle dans la section suivante.

![Fenêtre de console montrant le modèle NUnit avec d’autres modèles](./media/create-custom-template/nunit-template-console-window.png)

### <a name="create-a-project-from-the-template"></a>Créer un projet à partir du modèle

Une fois le modèle installé à partir de NuGet, utilisez-le en exécutant la commande `dotnet new <TEMPLATE>` à partir du répertoire où vous souhaitez que soit placée la sortie du moteur de modèle (sauf si vous utilisez l’option `-o|--output` pour spécifier un répertoire spécifique). Pour plus d’informations, consultez [Options `dotnet new`](~/docs/core/tools/dotnet-new.md#options). Indiquez le nom court du modèle directement dans la commande `dotnet new`. Pour créer un projet à partir du modèle NUnit, exécutez la commande suivante :

```console
dotnet new nunit
```

La console indique que le projet est créé et que les packages du projet sont restaurés. Une fois la commande exécutée, le projet est prêt à être utilisé.

![La fenêtre de console affiche la sortie du nouveau nunit dotnet incluant la restauration des dépendances du projet](./media/create-custom-template/dotnet-new-nunit-console-output.png)

### <a name="to-uninstall-a-template-from-a-nuget-package-stored-at-nugetorg"></a>Pour désinstaller un modèle à partir d’un package NuGet stocké sur nuget.org

```console
dotnet new -u GarciaSoftware.ConsoleTemplate.CSharp
```

> [!NOTE]
> L’exemple est fourni à des fins de démonstration uniquement. Aucun package NuGet `GarciaSoftware.ConsoleTemplate.CSharp` n’existe sur nuget.org ou n’est installé avec le SDK .NET Core. Si vous exécutez la commande, aucun modèle/package n’est désinstallé et vous recevez l’exception suivante :
>
> > Impossible de désinstaller quelque chose appelé 'GarciaSoftware.ConsoleTemplate.CSharp'.

Si vous avez installé le [modèle NUnit 3 pour dotnet-new](https://www.nuget.org/packages/NUnit3.DotNetNew.Template/) et que vous souhaitez le désinstaller, utilisez la commande suivante :

```console
dotnet new -u NUnit3.DotNetNew.Template
```

### <a name="uninstall-the-template-from-a-local-nupkg-file"></a>Désinstaller le modèle à partir d’un fichier nupkg local

Quand vous souhaitez désinstaller le modèle, n’essayez pas d’utiliser le chemin du fichier *nupkg*. *La tentative de désinstaller un modèle à l’aide de `dotnet new -u <PATH_TO_NUPKG_FILE>` est vouée à l’échec.* Référencez le package par son `id` :

```console
dotnet new -u GarciaSoftware.ConsoleTemplate.CSharp.1.0.0
```

## <a name="use-file-system-distribution"></a>Utiliser la distribution à partir du système de fichiers

Pour distribuer le modèle, placez le dossier du modèle de projet dans un emplacement accessible aux utilisateurs de votre réseau. Utilisez la commande `dotnet new` avec l’option `-i|--install` et spécifiez le chemin du dossier de modèles (le dossier de projet contenant le projet et le dossier *.template.config*).

Ce didacticiel suppose que le modèle de projet est stocké dans le dossier *Documents/Templates* du profil de l’utilisateur. À partir de cet emplacement, installez le modèle à l’aide de la commande suivante en remplaçant \<USER> par le nom de profil de l’utilisateur :

```console
dotnet new -i C:\Users\<USER>\Documents\Templates\GarciaSoftware.ConsoleTemplate.CSharp
```

### <a name="create-a-project-from-the-template"></a>Créer un projet à partir du modèle

Une fois le modèle installé à partir du système de fichiers, utilisez-le en exécutant la commande `dotnet new <TEMPLATE>` à partir du répertoire où vous souhaitez que soit placée la sortie du moteur de modèle (sauf si vous utilisez l’option `-o|--output` pour spécifier un répertoire spécifique). Pour plus d’informations, consultez [Options `dotnet new`](~/docs/core/tools/dotnet-new.md#options). Indiquez le nom court du modèle directement dans la commande `dotnet new`.

À partir d’un nouveau dossier de projet créé à l’emplacement *C:\Users\\\<USER>\Documents\Projects\MyConsoleApp*, créez un projet à partir du modèle `garciaconsole` :

```console
dotnet new garciaconsole
```

### <a name="uninstall-the-template"></a>Désinstaller le modèle

Si vous avez créé le modèle sur votre système de fichiers local à l’emplacement *C:\Users\\\<USER>\Documents\Templates\GarciaSoftware.ConsoleTemplate.CSharp*, désinstallez-le à l’aide du commutateur `-u|--uninstall` et du chemin du dossier de modèles :

```console
dotnet new -u C:\Users\<USER>\Documents\Templates\GarciaSoftware.ConsoleTemplate.CSharp
```

> [!NOTE]
> Pour désinstaller le modèle de votre système de fichiers local, vous devez qualifier le chemin d’accès avec un nom complet. Par exemple, *C:\Users\\\<USER>\Documents\Templates\GarciaSoftware.ConsoleTemplate.CSharp* fonctionne, mais *./GarciaSoftware.ConsoleTemplate.CSharp* à partir du dossier conteneur ne fonctionne pas.
> En outre, n’incluez pas de barre oblique finale après le répertoire dans votre chemin d’accès au modèle.

## <a name="see-also"></a>Voir aussi

- [Wiki du dépôt GitHub dotnet/templating](https://github.com/dotnet/templating/wiki)
- [Dépôt GitHub dotnet/dotnet-template-samples](https://github.com/dotnet/dotnet-template-samples)
- [Guide pratique pour créer vos propres modèles pour dotnet new](https://devblogs.microsoft.com/dotnet/how-to-create-your-own-templates-for-dotnet-new/)
- [Schéma *template.json* dans le magasin de schémas JSON](http://json.schemastore.org/template)
