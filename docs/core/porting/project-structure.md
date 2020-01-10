---
title: Organiser des projets pour .NET Framework et .NET Core
description: Aide destinée aux propriétaires de projet qui souhaitent compiler leur solution côte à côte pour le .NET Framework et .NET Core.
author: conniey
ms.date: 12/07/2018
ms.openlocfilehash: d71cc3102846c08f4e35831921b8cc4ca82f9e1b
ms.sourcegitcommit: cbdc0f4fd39172b5191a35200c33d5030774463c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/09/2020
ms.locfileid: "75777332"
---
# <a name="organize-your-project-to-support-both-net-framework-and-net-core"></a>Organiser votre projet pour prendre en charge à la fois le .NET Framework et .NET Core

Vous pouvez créer une solution compilée pour .NET Framework et .NET Core côte à côte. Cet article aborde plusieurs options d’organisation de projets pour vous aider à atteindre cet objectif. Voici quelques scénarios classiques à prendre en compte lorsque vous décidez comment configurer la disposition de votre projet avec .NET Core. La liste peut ne pas couvrir tout ce que vous souhaitez : établissez vos priorités en fonction des besoins de votre projet.

- [**Combiner des projets existants et des projets .NET Core pour en faire des projets uniques**](#replace-existing-projects-with-a-multi-targeted-net-core-project)

  *En voici les avantages :*
  - Simplifie votre processus de génération en compilant un projet unique plutôt que plusieurs projets qui ciblent chacun une version ou une plateforme .NET Framework différente.
  - Simplifie la gestion des fichiers sources pour les projets multi-ciblés, car vous devez gérer un seul fichier projet. Lors de l’ajout ou de la suppression de fichiers sources, les alternatives vous obligent à les synchroniser manuellement avec d’autres projets.
  - Générez facilement un package NuGet à des fins de consommation.
  - Vous permet d’écrire du code pour une version spécifique du .NET Framework dans vos bibliothèques via l’utilisation de directives de compilation.

  *Scénarios non pris en charge :*
  - Requiert que les développeurs utilisent Visual Studio 2017 ou une version ultérieure pour ouvrir des projets existants. Pour prendre en charge les versions antérieures de Visual Studio, [conserver vos fichiers projet dans des dossiers différents](#support-vs) est une meilleure option.

- <a name="support-vs"></a>[**Séparer les projets existants des nouveaux projets .NET Core**](#keep-existing-projects-and-create-a-net-core-project)

  *En voici les avantages :*
  - Prend en charge le développement sur des projets existants pour les développeurs et les contributeurs qui ne disposent pas de Visual Studio 2017 ou d’une version ultérieure.
  - Réduit la possibilité de créer des bogues dans des projets existants car aucune évolution du code n’est requise dans ces projets.

## <a name="example"></a>Exemple

Considérez le dépôt ci-dessous :

![Projet existant](./media/project-structure/existing-project-structure.png)

[**Code source**](https://github.com/dotnet/samples/tree/master/framework/libraries/migrate-library/)

La section suivante décrit plusieurs méthodes pour ajouter la prise en charge de .NET Core pour ce dépôt en fonction des contraintes et de la complexité des projets existants.

## <a name="replace-existing-projects-with-a-multi-targeted-net-core-project"></a>Remplacer les projets existants par un projet .NET Core multiciblé

Réorganisez le dépôt de sorte que tous les fichiers *\*.csproj* existants soient supprimés et qu’un seul fichier *\*.csproj* ciblant plusieurs frameworks soit créé. Il s’agit d’une option intéressante, car un seul projet peut être compilé pour différents frameworks. Elle permet également de gérer différentes options de compilation et dépendances par framework ciblé.

![Créer un csproj ciblant plusieurs frameworks](./media/project-structure/multi-targeted-project.png)

[**Code source**](https://github.com/dotnet/samples/tree/master/framework/libraries/migrate-library-csproj/)

Les modifications à noter sont :

- Remplacement de *packages.config* et de *\*.csproj* par un nouveau [.csproj *\*.NET Core*](https://github.com/dotnet/samples/tree/master/framework/libraries/migrate-library-csproj/src/Car/Car.csproj). Les packages NuGet sont spécifiés avec `<PackageReference> ItemGroup`.

## <a name="keep-existing-projects-and-create-a-net-core-project"></a>Conserver les projets existants et créer un projet .NET Core

Si des projets existants ciblent des frameworks plus anciens, vous pouvez laisser ces projets inchangés et utiliser un projet .NET Core pour cibler les futurs frameworks.

![Projet .NET Core avec un projet existant dans un dossier différent](./media/project-structure/separate-projects-same-source.png)

[**Code source**](https://github.com/dotnet/samples/tree/master/framework/libraries/migrate-library-csproj-keep-existing/)

Le projet .NET Core et les projets existants sont conservés dans des dossiers distincts. Si vous conservez des projets dans des dossiers distincts, vous n’avez pas besoin de disposer de Visual Studio 2017 ou d’une version ultérieure. Vous pouvez créer une solution distincte qui ouvre seulement les anciens projets.

## <a name="see-also"></a>Voir aussi

- [Documentation sur le portage .NET Core](index.md)
