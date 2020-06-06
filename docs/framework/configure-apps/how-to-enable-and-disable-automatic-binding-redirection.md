---
title: Activer ou désactiver les redirections de liaison générées automatiquement
ms.date: 10/30/2018
helpviewer_keywords:
- side-by-side execution, assembly binding redirection
- assemblies [.NET Framework], binding redirection
ms.assetid: 5fca42f3-bdce-4b81-a704-61e42c89d3ba
ms.openlocfilehash: 178d5070dd7018bbc0fce474cdd0b31ba3d17f77
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "69913032"
---
# <a name="how-to-enable-and-disable-automatic-binding-redirection"></a>Procédure : Activer et désactiver la redirection de liaison automatique

Quand vous compilez des applications dans Visual Studio qui ciblent le .NET Framework 4.5.1 et versions ultérieures, les redirections de liaison peuvent être ajoutées automatiquement au fichier de configuration d’application pour remplacer l’unification d’assemblys. Les redirections de liaison sont ajoutées si votre application ou ses composants font référence à plusieurs versions du même assembly, même si vous spécifiez manuellement des redirections de liaison dans le fichier de configuration de votre application. La fonctionnalité de redirection de liaison automatique affecte les applications de bureau et les applications Web qui ciblent le .NET Framework 4.5.1 ou une version ultérieure, même si le comportement est légèrement différent pour une application Web. Vous pouvez activer la redirection de liaison automatique si vous avez des applications existantes qui ciblent des versions antérieures du .NET Framework, ou vous pouvez désactiver cette fonctionnalité si vous souhaitez créer manuellement des redirections de liaison.

## <a name="disable-automatic-binding-redirects-in-desktop-apps"></a>Désactiver les redirections de liaison automatiques dans les applications de bureau

Les redirections de liaison automatiques sont activées par défaut pour les applications de bureau Windows qui ciblent le .NET Framework 4.5.1 et les versions ultérieures. Les redirections de liaison sont ajoutées au fichier de configuration de sortie (**app. config**) lorsque l’application est compilée et remplacent l’unification d’assemblys qui pourrait autrement se produire. Le fichier **app. config** source n’est pas modifié. Vous pouvez désactiver cette fonctionnalité en modifiant le fichier projet de l’application ou en désélectionnant une case à cocher dans les propriétés du projet dans Visual Studio.

### <a name="disable-through-project-properties"></a>Désactiver via les propriétés du projet

Si vous disposez de Visual Studio 2017 version 15,7 ou ultérieure, vous pouvez facilement désactiver les redirections de liaison générées automatiquement dans les pages de propriétés du projet.

1. Dans **Explorateur de solutions** , cliquez avec le bouton droit sur le projet, puis sélectionnez **Propriétés**.

2. Sur la page **application** , décochez l’option **générer automatiquement les redirections de liaison** .

3. Appuyez sur **CTRL** + **S** pour enregistrer la modification.

### <a name="disable-manually-in-the-project-file"></a>Désactiver manuellement dans le fichier projet

1. Ouvrez le fichier projet pour le modifier à l’aide de l’une des méthodes suivantes :

   - Dans Visual Studio, sélectionnez le projet dans **Explorateur de solutions**, puis choisissez **ouvrir le dossier dans l’Explorateur de fichiers** dans le menu contextuel. Dans l’Explorateur de fichiers, recherchez le fichier projet (. csproj ou. vbproj) et ouvrez-le dans le bloc-notes.
   - Dans Visual Studio, dans **Explorateur de solutions**, cliquez avec le bouton droit sur le projet et choisissez **décharger le projet**. Cliquez à nouveau avec le bouton droit sur le projet déchargé, puis choisissez **modifier [ProjectName. csproj]**.

2. Dans le fichier projet, recherchez l'entrée de propriété suivante :

   ```xml
   <AutoGenerateBindingRedirects>true</AutoGenerateBindingRedirects>
   ```

3. Remplacez `true` par `false` :

   ```xml
   <AutoGenerateBindingRedirects>false</AutoGenerateBindingRedirects>
   ```

## <a name="enable-automatic-binding-redirects-manually"></a>Activer les redirections de liaison automatiques manuellement

Vous pouvez activer les redirections de liaison automatiques dans les applications existantes qui ciblent des versions antérieures du .NET Framework ou dans les cas où vous n’êtes pas automatiquement invité à ajouter une redirection. Si vous ciblez une version plus récente du Framework, mais que vous n’êtes pas invité automatiquement à ajouter une redirection, vous obtiendrez probablement une sortie de génération qui vous suggère de remapper les assemblys.

1. Ouvrez le fichier projet pour le modifier à l’aide de l’une des méthodes suivantes :

   - Dans Visual Studio, sélectionnez le projet dans **Explorateur de solutions**, puis choisissez **ouvrir le dossier dans l’Explorateur de fichiers** dans le menu contextuel. Dans l’Explorateur de fichiers, recherchez le fichier projet (. csproj ou. vbproj) et ouvrez-le dans le bloc-notes.
   - Dans Visual Studio, dans **Explorateur de solutions**, cliquez avec le bouton droit sur le projet et choisissez **décharger le projet**. Cliquez à nouveau avec le bouton droit sur le projet déchargé, puis choisissez **modifier [ProjectName. csproj]**.

2. Ajoutez l’élément suivant au premier groupe de propriétés de configuration (sous la \<PropertyGroup> balise) :

   ```xml
   <AutoGenerateBindingRedirects>true</AutoGenerateBindingRedirects>
   ```

   L’exemple suivant montre un exemple de fichier projet avec l’élément inséré :

   ```xml
   <?xml version="1.0" encoding="utf-8"?>
   <Project ToolsVersion="12.0" DefaultTargets="Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
     <Import Project="$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\Microsoft.Common.props" Condition="Exists('$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\Microsoft.Common.props')" />
     <PropertyGroup>
       <Configuration Condition=" '$(Configuration)' == '' ">Debug</Configuration>
       <Platform Condition=" '$(Platform)' == '' ">AnyCPU</Platform>
       <ProjectGuid>{123334}</ProjectGuid>
       ...
       <AutoGenerateBindingRedirects>true</AutoGenerateBindingRedirects>
     </PropertyGroup>
     ...
   </Project>
   ```

3. Compilez votre application.

## <a name="enable-automatic-binding-redirects-in-web-apps"></a>Activer les redirections de liaison automatiques dans les applications Web

Les redirections de liaison automatiques sont implémentées différemment pour les applications web. Étant donné que le fichier de configuration source (**Web. config**) doit être modifié pour les applications Web, les redirections de liaison ne sont pas automatiquement ajoutées au fichier de configuration. Toutefois, Visual Studio vous informe des éventuels conflits de liaison et vous pouvez ajouter des redirections de liaison pour résoudre ces conflits. Étant donné que vous êtes toujours invité à ajouter des redirections de liaison, vous n’avez pas besoin de désactiver explicitement cette fonctionnalité pour une application Web.

Pour ajouter des redirections de liaison à un fichier **Web. config** :

1. Dans Visual Studio, compilez l'application et vérifiez les avertissements sur la génération.

   ![Avertissement sur la génération des conflits de la référence d'assembly](./media/clr-assemblyrefwarning.png "CLR_AssemblyRefWarning")

2. En cas de conflit de liaison d’assembly, un avertissement s’affiche. Double-cliquez sur l’avertissement ou sélectionnez l’avertissement et appuyez sur **entrée**.

   Une boîte de dialogue qui vous permet d’ajouter automatiquement les redirections de liaison nécessaires vers le fichier **Web. config** source s’affiche.

   ![Boîte de dialogue des autorisations de redirection de liaison](./media/clr-addbindingredirect.png "CLR_AddBindingRedirect")

## <a name="see-also"></a>Voir aussi

- [\<bindingRedirect>Appartient](./file-schema/runtime/bindingredirect-element.md)
- [Redirection des versions d'assemblys](redirect-assembly-versions.md)
