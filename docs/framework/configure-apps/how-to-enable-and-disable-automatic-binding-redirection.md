---
title: Activer ou désactiver les redirections de liaison généré automatiquement
ms.date: 10/30/2018
helpviewer_keywords:
- side-by-side execution, assembly binding redirection
- assemblies [.NET Framework], binding redirection
ms.assetid: 5fca42f3-bdce-4b81-a704-61e42c89d3ba
ms.openlocfilehash: b6c9c3508c53e8a68a3f7e1cb12b6b6c95600e7b
ms.sourcegitcommit: 4735bb7741555bcb870d7b42964d3774f4897a6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/30/2019
ms.locfileid: "66380100"
---
# <a name="how-to-enable-and-disable-automatic-binding-redirection"></a>Procédure : Activer et désactiver la redirection de liaison automatique

Lorsque vous compilez des applications dans Visual Studio qui ciblent le .NET Framework 4.5.1 et versions ultérieures, les redirections de liaison peuvent être automatiquement ajoutées au fichier de configuration d’application pour remplacer l’unification d’assembly. Les redirections de liaison sont ajoutées si votre application ou ses composants font référence à plusieurs versions du même assembly, même si vous spécifiez manuellement des redirections de liaison dans le fichier de configuration de votre application. La fonctionnalité de redirection de liaison automatique affecte les applications web et les applications de bureau qui ciblent le .NET Framework 4.5.1 ou version ultérieure, bien que le comportement est légèrement différent pour une application web. Vous pouvez activer la redirection de liaison automatique si vous avez des applications existantes qui ciblent des versions précédentes du .NET Framework, ou vous pouvez désactiver cette fonctionnalité si vous souhaitez créer manuellement des redirections de liaison.

## <a name="disable-automatic-binding-redirects-in-desktop-apps"></a>Désactiver les redirections de liaison automatiques dans les applications de bureau

Redirections de liaison automatiques sont activées par défaut pour les applications de bureau Windows qui ciblent le .NET Framework 4.5.1 et versions ultérieures. Les redirections de liaison sont ajoutées à la configuration de sortie (**app.config**) du fichier lorsque l’application est compilée et remplacer l’unification d’assembly qui peut avoir lieu. La source de **app.config** fichier n’est pas modifié. Vous pouvez désactiver cette fonctionnalité en modifiant le fichier projet pour l’application ou en désactivant une case à cocher dans les propriétés du projet dans Visual Studio.

### <a name="disable-through-project-properties"></a>Désactivation de via les propriétés du projet

Si vous avez Visual Studio 2017 version 15.7 ou version ultérieure, vous pouvez facilement désactiver les redirections de liaison généré automatiquement dans les pages de propriétés du projet.

1. Cliquez avec le bouton droit sur le projet dans **l’Explorateur de solutions**, puis sélectionnez **Propriétés**.

2. Sur le **Application** page, désactivez le **générer automatiquement des redirections de liaison** option.

3. Appuyez sur **Ctrl**+**S** pour enregistrer la modification.

### <a name="disable-manually-in-the-project-file"></a>Désactiver manuellement dans le fichier projet

1. Ouvrez le fichier de projet pour la modification à l’aide d’une des méthodes suivantes :

   - Dans Visual Studio, sélectionnez le projet dans **l’Explorateur de solutions**, puis choisissez **ouvrir le dossier dans l’Explorateur de fichiers** dans le menu contextuel. Dans l’Explorateur de fichiers, recherchez le fichier de projet (.csproj ou .vbproj) et ouvrez-le dans le bloc-notes.
   - Dans Visual Studio, dans **l’Explorateur de solutions**, cliquez sur le projet et choisissez **décharger le projet**. Cliquez de nouveau sur le projet déchargé, puis choisissez **modifier [NomProjet.csproj]** .

2. Dans le fichier projet, recherchez l'entrée de propriété suivante :

   ```xml
   <AutoGenerateBindingRedirects>true</AutoGenerateBindingRedirects>
   ```

3. Remplacez `true` par `false` :

   ```xml
   <AutoGenerateBindingRedirects>false</AutoGenerateBindingRedirects>
   ```

## <a name="enable-automatic-binding-redirects-manually"></a>Activer manuellement des redirections de liaison automatiques

Vous pouvez activer les redirections de liaison automatiques dans les applications existantes qui ciblent des versions antérieures du .NET Framework, ou dans les cas où vous n’êtes pas automatiquement invité à ajouter une redirection. Si vous ciblez une version plus récente du framework mais ne pas automatiquement invité à ajouter une redirection, vous obtiendrez probablement un résultat de build qui suggère de que remapper les assemblys.

1. Ouvrez le fichier de projet pour la modification à l’aide d’une des méthodes suivantes :

   - Dans Visual Studio, sélectionnez le projet dans **l’Explorateur de solutions**, puis choisissez **ouvrir le dossier dans l’Explorateur de fichiers** dans le menu contextuel. Dans l’Explorateur de fichiers, recherchez le fichier de projet (.csproj ou .vbproj) et ouvrez-le dans le bloc-notes.
   - Dans Visual Studio, dans **l’Explorateur de solutions**, cliquez sur le projet et choisissez **décharger le projet**. Cliquez de nouveau sur le projet déchargé, puis choisissez **modifier [NomProjet.csproj]** .

2. Ajoutez l’élément suivant pour le premier groupe de propriétés de configuration (sous le \<PropertyGroup > balise) :

   ```xml
   <AutoGenerateBindingRedirects>true</AutoGenerateBindingRedirects>
   ```

   Voici un exemple de fichier de projet avec l’élément inséré :

   ```xml
   <?xml version="1.0" encoding="utf-8"?>
   <Project ToolsVersion="12.0" DefaultTargets="Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
     <Import Project="$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\Microsoft.Common.props" Condition="Exists('$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\Microsoft.Common.props')" />
       <PropertyGroup>
         <Configuration Condition=" '$(Configuration)' == ''     ">Debug</Configuration>
         <Platform Condition=" '$(Platform)' == '' ">AnyCPU</Platform>
         <ProjectGuid>{123334}</ProjectGuid>
         ...
         <AutoGenerateBindingRedirects>true</AutoGenerateBindingRedirects>
       </PropertyGroup>
     ...
   </Project>
   ```

3. Compilez votre application.

## <a name="enable-automatic-binding-redirects-in-web-apps"></a>Activer les redirections de liaison automatiques dans les applications web

Les redirections de liaison automatiques sont implémentées différemment pour les applications web. Étant donné que la configuration de la source (**web.config**) fichier doit être modifié pour les applications web, les redirections de liaison ne sont pas automatiquement ajoutées au fichier de configuration. Toutefois, Visual Studio vous informe des éventuels conflits de liaison et vous pouvez ajouter des redirections de liaison pour résoudre ces conflits. Étant donné que vous êtes toujours invité à ajouter des redirections de liaison, vous n’avez pas besoin de désactiver explicitement cette fonctionnalité pour une application web.

Pour ajouter des redirections de liaison à un **web.config** fichier :

1. Dans Visual Studio, compilez l'application et vérifiez les avertissements sur la génération.

   ![Générer l’avertissement pour les conflits de référence d’assembly](../../../docs/framework/configure-apps/media/clr-assemblyrefwarning.png "CLR_AssemblyRefWarning")

2. En cas de conflit de liaison d’assembly, un avertissement s’affiche. Double-cliquez sur l’avertissement, ou sélectionnez l’avertissement et appuyez sur **entrée**.

   Une boîte de dialogue qui vous permet d’ajouter automatiquement la liaison nécessaires redirige vers la source **web.config** fichier s’affiche.

   ![Boîte de dialogue liaison de redirection autorisation](../../../docs/framework/configure-apps/media/clr-addbindingredirect.png "CLR_AddBindingRedirect")

## <a name="see-also"></a>Voir aussi

- [\<bindingRedirect > élément](../../../docs/framework/configure-apps/file-schema/runtime/bindingredirect-element.md)
- [Redirection des versions d'assemblys](../../../docs/framework/configure-apps/redirect-assembly-versions.md)
