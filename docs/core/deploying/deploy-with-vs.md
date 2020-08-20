---
title: Déployer des applications .NET Core avec Visual Studio
description: Apprenez à déployer des applications .NET Core avec Visual Studio.
ms.date: 09/03/2018
dev_langs:
- csharp
- vb
ms.custom: vs-dotnet
ms.openlocfilehash: 73eee58a3d11f2f898a6d57cb282ccf4e802cdca
ms.sourcegitcommit: c4a15c6c4ecbb8a46ad4e67d9b3ab9b8b031d849
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/20/2020
ms.locfileid: "88656597"
---
# <a name="deploy-net-core-apps-with-visual-studio"></a>Déployer des applications .NET Core avec Visual Studio

Pour déployer une application .NET Core, vous pouvez soit effectuer un *déploiement dépendant du framework* (qui inclut vos binaires d’application, mais qui dépend de la présence de .NET Core sur le système cible), soit effectuer un *déploiement autonome* (qui inclut votre application et les binaires .NET Core). Pour obtenir une vue d’ensemble du déploiement des applications .NET Core, consultez [Déploiement d’applications .NET Core](index.md).

Les sections suivantes montrent comment utiliser Microsoft Visual Studio pour créer les genres de déploiements suivants :

- Déploiement dépendant du framework
- Déploiement dépendant du framework avec des dépendances tierces
- Déploiement autonome
- Déploiement autonome avec des dépendances tierces

Pour plus d’informations sur l’utilisation de Visual Studio pour développer des applications .NET Core, consultez [dépendances et exigences de .net Core](../install/dependencies.md?pivots=os-windows).

## <a name="framework-dependent-deployment"></a>Déploiement dépendant du framework

Le déploiement d’un déploiement dépendant du framework sans dépendances tierces implique simplement la génération, le test et la publication de l’application. Un exemple simple écrit en C# illustre le processus.

1. Créez le projet.

   Sélectionnez **Fichier** > **Nouveau** > **Projet**. Dans la boîte de dialogue **Nouveau projet**, développez les catégories de projet de votre langage (C# ou Visual Basic) au sein du volet des types de projet **Installé**, choisissez **.NET Core**, puis sélectionnez le modèle **Application console (.NET Core)** dans le volet central. Entrez un nom de projet, tel que « FDD », dans la zone de texte **Nom**. Cliquez sur le bouton **OK**.

1. Ajoutez le code source de l’application.

   Ouvrez le fichier *Program.cs* ou *Program. vb* dans l’éditeur et remplacez le code généré automatiquement par le code suivant. Il invite l’utilisateur à entrer du texte et affiche les différents mots entrés. Il utilise l’expression régulière `\w+` pour séparer les mots dans le texte d’entrée.

   [!code-csharp[deployment#1](./snippets/deploy-with-vs/csharp/deployment-example.cs)]
   [!code-vb[deployment#1](./snippets/deploy-with-vs/vb/deployment-example.vb)]

1. Créez une build Debug de votre application.

   Sélectionnez **Générer** > **Générer la solution**. Vous pouvez également compiler et exécuter la version Debug de votre application en sélectionnant **Déboguer**  >  **Démarrer le débogage**.

1. Déployez votre application.

   Après avoir débogué et testé le programme, créez les fichiers à déployer avec votre application. Pour publier à partir de Visual Studio, effectuez les étapes suivantes :

      1. Remplacez la configuration de solution **Debug** par **Release** dans la barre d’outils pour générer une build Release (et non une build Debug) de votre application.

      1. Cliquez avec le bouton droit sur le projet (pas la solution) dans l’**Explorateur de solutions**, puis sélectionnez **Publier**.

      1. Sous l’onglet **Publier**, sélectionnez **Publier**. Visual Studio écrit les fichiers qui composent votre application dans le système de fichiers local.

      1. L’onglet **Publier** affiche maintenant un seul profil, **FolderProfile**. Les paramètres de configuration du profil sont affichés dans la section **Résumé** de l’onglet.

   Les fichiers résultants sont placés dans un répertoire nommé `Publish` sur Windows (`publish` sur les systèmes Unix), qui se trouve dans un sous-répertoire du sous-répertoire *.\bin\release\netcoreapp2.1* de votre projet.

En même temps que les fichiers de votre application, le processus de publication produit un fichier de base de données du programme (.pdb) qui contient des informations de débogage sur votre application. Le fichier est surtout utile pour le débogage d’exceptions. Vous pouvez choisir de ne pas l’empaqueter avec les fichiers de votre application. Vous devez toutefois l’enregistrer au cas où vous souhaiteriez déboguer la build Release de votre application.

Déployez l’ensemble complet des fichiers d’application de la façon qui vous convient. Par exemple, vous pouvez les empaqueter dans un fichier Zip, utiliser une simple commande `copy` ou les déployer avec n’importe quel package d’installation de votre choix. Une fois l’installation terminée, les utilisateurs peuvent exécuter votre application en utilisant la commande `dotnet` suivie du nom de l’application. Par exemple : `dotnet fdd.dll`.

Outre les binaires de l’application, votre programme d’installation doit également regrouper le programme d’installation du framework partagé ou vérifier qu’il est bien installé comme prérequis de l’installation de l’application.  L’installation du framework partagé nécessite un accès Administrateur/root car il est à l’échelle de la machine.

## <a name="framework-dependent-deployment-with-third-party-dependencies"></a>Déploiement dépendant du framework avec des dépendances tierces

Pour exécuter un déploiement dépendant du framework avec une ou plusieurs dépendances tierces, ces dépendances doivent être accessibles à votre projet. Avant de pouvoir générer votre application, vous devez effectuer les étapes suivantes :

1. Utilisez le **Gestionnaire de package NuGet** pour ajouter à votre projet une référence à un package NuGet et installer le package s’il n’est pas disponible sur votre système. Pour ouvrir le gestionnaire de package, sélectionnez **Outils**  >  **Gestionnaire de package NuGet**  >  **gérer les packages NuGet pour la solution**.

1. Vérifiez que vos dépendances tierces (par exemple, `Newtonsoft.Json` ) sont installées sur votre système et, si elles ne le sont pas, installez-les. L’onglet **Installé** répertorie les packages NuGet installés sur votre système. Si `Newtonsoft.Json` n’est pas répertorié, sélectionnez l’onglet **Parcourir** et entrez « Newtonsoft.Json » dans la zone de recherche. Sélectionnez `Newtonsoft.Json` et, dans le volet droit, choisissez votre projet avant de sélectionner **Installer**.

1. Si `Newtonsoft.Json` est déjà installé sur votre système, ajoutez-le à votre projet en sélectionnant votre projet dans le volet droit de l’onglet **Gérer les packages de la solution**.

Un déploiement dépendant du Framework avec des dépendances tierces n’est que portable comme ses dépendances tierces. Par exemple, si une bibliothèque tierce prend uniquement en charge macOS, l’application n’est pas portable sur des systèmes Windows. Cela se produit si la dépendance tierce elle-même dépend du code natif. Un [serveur Kestrel](/aspnet/core/fundamentals/servers/kestrel) constitue un bon exemple, car il nécessite une dépendance native à [libuv](https://github.com/libuv/libuv). Quand un déploiement dépendant du framework est créé pour une application avec ce type de dépendance tierce, le résultat publié contient un dossier pour chaque [identificateur de runtime](../rid-catalog.md) pris en charge par la dépendance native (et qui existe dans le package NuGet).

## <a name="self-contained-deployment-without-third-party-dependencies"></a><a name="simpleSelf"></a> Déploiement autonome sans dépendances tierces

L’exécution d’un déploiement autonome sans aucune dépendance tierce implique la création du projet, la modification du fichier *csproj*, la génération, le test et la publication de l’application. Un exemple simple écrit en C# illustre le processus. Commencez par créer, coder et tester votre projet comme pour un déploiement dépendant du framework :

1. Créez le projet.

   Sélectionnez **Fichier** > **Nouveau** > **Projet**. Dans la boîte de dialogue **Nouveau projet**, développez les catégories de projet de votre langage (C# ou Visual Basic) au sein du volet des types de projet **Installé**, choisissez **.NET Core**, puis sélectionnez le modèle **Application console (.NET Core)** dans le volet central. Entrez un nom de projet, tel que « SCD », dans la zone de texte **Nom**, puis sélectionnez le bouton **OK**.

1. Ajoutez le code source de l’application.

   Ouvrez le fichier *Program.cs* ou *Program. vb* dans votre éditeur et remplacez le code généré automatiquement par le code suivant. Il invite l’utilisateur à entrer du texte et affiche les différents mots entrés. Il utilise l’expression régulière `\w+` pour séparer les mots dans le texte d’entrée.

   [!code-csharp[deployment#1](./snippets/deploy-with-vs/csharp/deployment-example.cs)]
   [!code-vb[deployment#1](./snippets/deploy-with-vs/vb/deployment-example.vb)]

1. Déterminez si vous souhaitez utiliser le mode invariant de globalisation.

   En particulier, si votre application cible Linux, vous pouvez réduire la taille totale de votre déploiement en tirant parti du [mode invariant de globalisation](https://github.com/dotnet/runtime/blob/master/docs/design/features/globalization-invariant-mode.md). Le mode invariant de globalisation est utile pour les applications qui ne sont pas globalement compatibles et qui peuvent utiliser les conventions de mise en forme, les conventions de casse et la comparaison de chaînes, ainsi que l’ordre de tri de la [culture invariante](xref:System.Globalization.CultureInfo.InvariantCulture).

   Pour activer le mode invariant, cliquez avec le bouton droit sur le projet (pas la solution) dans l’**Explorateur de solutions**, puis sélectionnez **Modifier SCD.csproj** ou **Modifier SCD.vbproj**. Ajoutez ensuite les lignes en surbrillance suivantes au fichier :

   [!code-xml[globalization-invariant-mode](./snippets/deploy-with-vs/xml/invariant.csproj?highlight=7-9)]

1. Créez une build Debug de votre application.

   Sélectionnez **Générer** > **Générer la solution**. Vous pouvez également compiler et exécuter la version Debug de votre application en sélectionnant **Déboguer**  >  **Démarrer le débogage**. Cette étape de débogage vous permet d’identifier les problèmes de votre application quand elle s’exécute sur la plateforme hôte. Vous devez tout de même la tester sur chacune des plateformes cibles.

   Si vous avez activé le mode invariant de globalisation, vérifiez si l’absence de données relatives à la culture convient à votre application.

Une fois le débogage effectué, vous pouvez publier votre déploiement autonome :

<!-- markdownlint-disable MD025 -->

# <a name="visual-studio-156-and-earlier"></a>[Visual Studio 15.6 et versions antérieures](#tab/vs156)

Après avoir débogué et testé le programme, créez les fichiers à déployer avec votre application pour chaque plateforme ciblée.

Pour publier votre application à partir de Visual Studio, effectuez les étapes suivantes :

1. Définissez les plateformes ciblées par votre application.

   1. Cliquez avec le bouton droit sur le projet (pas la solution) dans l’**Explorateur de solutions**, puis sélectionnez **Modifier SCD.csproj**.

   1. Créez une balise `<RuntimeIdentifiers>` dans la section `<PropertyGroup>` de votre fichier *csproj* qui définit les plateformes ciblées par votre application, et spécifiez l’identificateur de runtime de chaque plateforme ciblée. Vous devez également ajouter un point-virgule pour séparer les RID. Consultez [catalogue des identificateurs](../rid-catalog.md) de Runtime pour obtenir la liste des identificateurs de Runtime.

   Dans l’exemple suivant, l’application s’exécute sur les systèmes d’exploitation Windows 10 64 bits et sur le système d’exploitation OS X 64 bits version 10.11.

   ```xml
   <PropertyGroup>
      <RuntimeIdentifiers>win10-x64;osx.10.11-x64</RuntimeIdentifiers>
   </PropertyGroup>
   ```

   L' `<RuntimeIdentifiers>` élément peut accéder à n’importe quel élément `<PropertyGroup>` de votre fichier *csproj* . Un exemple complet de fichier *csproj* figure plus loin dans cette section.

1. Publiez votre application.

   Après avoir débogué et testé le programme, créez les fichiers à déployer avec votre application pour chaque plateforme ciblée.

   Pour publier votre application à partir de Visual Studio, effectuez les étapes suivantes :

      1. Remplacez la configuration de solution **Debug** par **Release** dans la barre d’outils pour générer une build Release (et non une build Debug) de votre application.

      1. Cliquez avec le bouton droit sur le projet (pas la solution) dans l’**Explorateur de solutions**, puis sélectionnez **Publier**.

      1. Sous l’onglet **Publier**, sélectionnez **Publier**. Visual Studio écrit les fichiers qui composent votre application dans le système de fichiers local.

      1. L’onglet **Publier** affiche maintenant un seul profil, **FolderProfile**. Les paramètres de configuration du profil s’affichent dans la section **Résumé** de l’onglet. le **Runtime cible** identifie le runtime qui a été publié et l' **emplacement cible** identifie l’emplacement d’écriture des fichiers pour le déploiement autonome.

      1. Par défaut, Visual Studio écrit tous les fichiers publiés dans un répertoire unique. Pour des raisons pratiques, il est préférable de créer des profils séparés pour chaque runtime cible et de placer les fichiers publiés dans un répertoire spécifique à la plateforme. Vous devez donc créer un profil de publication distinct pour chaque plateforme cible. À présent, effectuez les étapes suivantes pour regénérer l’application pour chaque plateforme :

         1. Sélectionnez **Créer un profil** dans la boîte de dialogue **Publier**.

         1. Dans la boîte de dialogue **Choisir une cible de publication** remplacez l’emplacement indiqué dans **Choisir un dossier** par *bin\Release\PublishOutput\win10-x64*. Sélectionnez **OK**.

         1. Sélectionnez le nouveau profil (**FolderProfile1**) dans la liste des profils et vérifiez que le **Runtime cible** est `win10-x64`. Si ce n’est pas le cas, sélectionnez **Paramètres**. Dans la boîte de dialogue **Paramètres du profil**, définissez **Runtime cible** avec la valeur `win10-x64` et sélectionnez **Enregistrer**. Sinon, sélectionnez **Annuler**.

         1. Sélectionnez **Publier** pour publier votre application pour des plateformes Windows 10 64 bits.

         1. Suivez les étapes précédentes pour créer un profil pour la plateforme `osx.10.11-x64`. L’**Emplacement cible** est *bin\Release\PublishOutput\osx.10.11-x64* et le **Runtime cible** est `osx.10.11-x64`. Le nom attribué par Visual Studio à ce profil est **FolderProfile2**.

      Chaque emplacement cible contient l’ensemble complet des fichiers (les fichiers de votre application et tous les fichiers .NET Core) nécessaires pour lancer votre application.

En même temps que les fichiers de votre application, le processus de publication produit un fichier de base de données du programme (.pdb) qui contient des informations de débogage sur votre application. Le fichier est surtout utile pour le débogage d’exceptions. Vous pouvez choisir de ne pas l’empaqueter avec les fichiers de votre application. Vous devez toutefois l’enregistrer au cas où vous souhaiteriez déboguer la build Release de votre application.

Déployez les fichiers publiés de la façon qui vous convient. Par exemple, vous pouvez les empaqueter dans un fichier Zip, utiliser une simple commande `copy` ou les déployer avec n’importe quel package d’installation de votre choix.

Voici le fichier *csproj* complet pour ce projet.

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp2.1</TargetFramework>
    <RuntimeIdentifiers>win10-x64;osx.10.11-x64</RuntimeIdentifiers>
  </PropertyGroup>
</Project>
```

# <a name="visual-studio-157-and-later"></a>[Visual Studio 15.7 et versions ultérieures](#tab/vs157)

Après avoir débogué et testé le programme, créez les fichiers à déployer avec votre application pour chaque plateforme ciblée. Cela implique la création d’un profil distinct pour chaque plateforme cible.

Pour chaque plateforme ciblée par votre application, effectuez ce qui suit :

1. Créez un profil pour la plateforme cible.

   S’il s’agit du premier profil que vous créez, cliquez avec le bouton droit sur le projet (pas la solution) dans l’**Explorateur de solutions**, puis sélectionnez **Publier**.

   Si vous avez déjà créé un profil, cliquez avec le bouton droit sur le projet pour ouvrir la boîte de dialogue **Publier**, le cas échéant. Sélectionnez ensuite **Nouveau profil**.

   La boîte de dialogue **Choisir une cible de publication** s’ouvre.

1. Sélectionnez l’emplacement où Visual Studio publie votre application.

   Si vous publiez uniquement sur une seule plateforme, vous pouvez accepter la valeur par défaut dans la zone de texte **choisir un dossier** . Cela permet de publier le déploiement dépendant du Framework de votre application dans le répertoire * \<project-directory> \bin\Release\netcoreapp2.1\publish* .

   Si vous publiez sur plusieurs plateformes, ajoutez une chaîne identifiant la plateforme cible. Par exemple, si vous ajoutez la chaîne « Linux » au chemin d’accès du fichier, Visual Studio publie le déploiement dépendant du Framework de votre application dans le répertoire * \<project-directory> \bin\Release\netcoreapp2.1\publish\linux* .

1. Pour créer le profil, sélectionnez l’icône de liste déroulante en regard du bouton **Publier**, puis sélectionnez **Créer un profil**. Sélectionnez ensuite le bouton **Créer un profil** pour créer le profil.

1. Indiquez que vous publiez un déploiement autonome, et définissez la plateforme ciblée par votre application.

   1. Dans la boîte de dialogue **Publier**, sélectionnez le lien **Configurer** pour ouvrir la boîte de dialogue **Paramètres du profil**.

   1. Sélectionnez **Autonome** dans la zone de liste **Mode de déploiement**.

   1. Dans la zone de liste **Runtime cible**, sélectionnez l’une des plateformes ciblées par votre application.

   1. Sélectionnez **Enregistrer** pour faire accepter vos changements, puis fermez la boîte de dialogue.

1. Nommez votre profil.

   1. Sélectionnez **actions**  >  **Renommer le profil** pour nommer votre profil.

   2. Attribuez au profil un nom qui identifie la plateforme cible, puis sélectionnez **Enregistrer*.

Répétez ces étapes pour définir les plateformes cibles supplémentaires ciblées par votre application.

Vous avez configuré vos profils et êtes maintenant prêt à publier votre application. Pour ce faire :

   1. Si la fenêtre **Publier** n’est pas ouverte, cliquez avec le bouton droit sur le projet (pas la solution) dans l’**Explorateur de solutions**, puis sélectionnez **Publier**.

   2. Sélectionnez le profil à publier, puis sélectionnez **Publier**. Procédez ainsi pour chaque profil à publier.

   Chaque emplacement cible (dans le cas de notre exemple, bin\release\netcoreapp2.1\publish \\ *profile-name* contient l’ensemble complet des fichiers (les fichiers de votre application et tous les fichiers .net Core) nécessaires pour lancer votre application.

En même temps que les fichiers de votre application, le processus de publication produit un fichier de base de données du programme (.pdb) qui contient des informations de débogage sur votre application. Le fichier est surtout utile pour le débogage d’exceptions. Vous pouvez choisir de ne pas l’empaqueter avec les fichiers de votre application. Vous devez toutefois l’enregistrer au cas où vous souhaiteriez déboguer la build Release de votre application.

Déployez les fichiers publiés de la façon qui vous convient. Par exemple, vous pouvez les empaqueter dans un fichier Zip, utiliser une simple commande `copy` ou les déployer avec n’importe quel package d’installation de votre choix.

Voici le fichier *csproj* complet pour ce projet.

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp2.1</TargetFramework>
  </PropertyGroup>
</Project>
```

De plus, Visual Studio crée un profil de publication distinct (\*.pubxml) pour chaque plateforme que vous ciblez. Par exemple, le fichier de notre profil linux (linux.pubxml) se présente comme suit :

```xml
<?xml version="1.0" encoding="utf-8"?>
<!--
https://go.microsoft.com/fwlink/?LinkID=208121.
-->
<Project ToolsVersion="4.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <PropertyGroup>
    <PublishProtocol>FileSystem</PublishProtocol>
    <Configuration>Release</Configuration>
    <Platform>Any CPU</Platform>
    <TargetFramework>netcoreapp2.1</TargetFramework>
    <PublishDir>bin\Release\netcoreapp2.1\publish\linux</PublishDir>
    <RuntimeIdentifier>win-x86</RuntimeIdentifier>
    <SelfContained>true</SelfContained>
    <_IsPortable>false</_IsPortable>
  </PropertyGroup>
</Project>
```

---

## <a name="self-contained-deployment-with-third-party-dependencies"></a>Déploiement autonome avec des dépendances tierces

L’exécution d’un déploiement autonome avec une ou plusieurs dépendances tierces implique l’ajout des dépendances. Avant de pouvoir générer votre application, vous devez effectuer les étapes suivantes :

1. Utilisez le **Gestionnaire de package NuGet** pour ajouter à votre projet une référence à un package NuGet et installer le package s’il n’est pas disponible sur votre système. Pour ouvrir le gestionnaire de package, sélectionnez **Outils**  >  **Gestionnaire de package NuGet**  >  **gérer les packages NuGet pour la solution**.

1. Vérifiez que vos dépendances tierces (par exemple, `Newtonsoft.Json` ) sont installées sur votre système et, si elles ne le sont pas, installez-les. L’onglet **Installé** répertorie les packages NuGet installés sur votre système. Si `Newtonsoft.Json` n’est pas répertorié, sélectionnez l’onglet **Parcourir** et entrez « Newtonsoft.Json » dans la zone de recherche. Sélectionnez `Newtonsoft.Json` et, dans le volet droit, choisissez votre projet avant de sélectionner **Installer**.

1. Si `Newtonsoft.Json` est déjà installé sur votre système, ajoutez-le à votre projet en sélectionnant votre projet dans le volet droit de l’onglet **Gérer les packages de la solution**.

Voici le fichier *csproj* complet pour ce projet :

# <a name="visual-studio-156-and-earlier"></a>[Visual Studio 15.6 et versions antérieures](#tab/vs156)

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp2.1</TargetFramework>
    <RuntimeIdentifiers>win10-x64;osx.10.11-x64</RuntimeIdentifiers>
  </PropertyGroup>
  <ItemGroup>
    <PackageReference Include="Newtonsoft.Json" Version="10.0.2" />
  </ItemGroup>
</Project>
```

# <a name="visual-studio-157-and-later"></a>[Visual Studio 15.7 et versions ultérieures](#tab/vs157)

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp2.1</TargetFramework>
  </PropertyGroup>
  <ItemGroup>
    <PackageReference Include="Newtonsoft.Json" Version="10.0.2" />
  </ItemGroup>
</Project>
```

---

Quand vous déployez votre application, toutes les dépendances tierces utilisées dans votre application sont également incluses avec vos fichiers d’application. Il n’est pas nécessaire que les bibliothèques tierces soient déjà présentes sur le système sur lequel l’application s’exécute.

Vous pouvez uniquement déployer un déploiement autonome avec une bibliothèque tierce sur les plateformes prises en charge par cette bibliothèque. Cela revient à avoir des dépendances tierces avec des dépendances natives dans votre déploiement dépendant du framework, où les dépendances natives n’existent pas sur la plateforme cible, sauf si elles y ont été installées précédemment.

## <a name="see-also"></a>Voir aussi

- [Déploiement d’applications .NET Core](index.md)
- [Catalogue d’identificateurs de Runtime (RID) .NET Core](../rid-catalog.md)
