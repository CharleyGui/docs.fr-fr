---
title: Organiser des projets pour .NET Framework et .NET Core
description: Aide destinée aux propriétaires de projet qui souhaitent compiler leur solution côte à côte pour le .NET Framework et .NET Core.
author: conniey
ms.date: 12/07/2018
ms.openlocfilehash: d71cc3102846c08f4e35831921b8cc4ca82f9e1b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75777332"
---
# <a name="organize-your-project-to-support-both-net-framework-and-net-core"></a>Organiser votre projet pour prendre en charge à la fois le .NET Framework et .NET Core

Vous pouvez créer une solution qui compile à la fois pour .NET Framework et .NET Core côte à côte. Cet article couvre plusieurs options d’organisation de projets pour vous aider à atteindre cet objectif. Voici quelques scénarios typiques à considérer lorsque vous décidez comment configurer votre mise en page de projet avec .NET Core. La liste peut ne pas couvrir tout ce que vous souhaitez : établissez vos priorités en fonction des besoins de votre projet.

- [**Combiner des projets existants et des projets .NET Core pour en faire des projets uniques**](#replace-existing-projects-with-a-multi-targeted-net-core-project)

  *En voici les avantages :*
  - Simplifie votre processus de construction en compilant un seul projet plutôt que plusieurs projets que chaque cible d’une version ou d’une plate-forme cadre .NET différente.
  - Simplifie la gestion des fichiers sources pour les projets multi-ciblés car vous devez gérer un seul fichier de projet. Lors de l’ajout ou de la suppression des fichiers source, les solutions de rechange vous obligent à les synchroniser manuellement avec vos autres projets.
  - Générer facilement un paquet NuGet pour la consommation.
  - Vous permet d’écrire du code pour une version spécifique du .NET Framework dans vos bibliothèques via l’utilisation de directives de compilation.

  *Scénarios non pris en compte :*
  - Exige que les développeurs utilisent Visual Studio 2017 ou une version ultérieure pour ouvrir des projets existants. Pour prendre en charge les versions antérieures de Visual Studio, [conserver vos fichiers projet dans des dossiers différents](#support-vs) est une meilleure option.

- <a name="support-vs"></a>[**Séparer les projets existants des nouveaux projets .NET Core**](#keep-existing-projects-and-create-a-net-core-project)

  *En voici les avantages :*
  - Soutient le développement sur les projets existants pour les développeurs et les contributeurs qui n’ont peut-être pas Visual Studio 2017 ou une version ultérieure.
  - Réduit la possibilité de créer de nouveaux bogues dans les projets existants parce qu’aucun désabonnement de code n’est nécessaire dans ces projets.

## <a name="example"></a> Exemple

Considérez le dépôt ci-dessous :

![Projet existant](./media/project-structure/existing-project-structure.png)

[**Source Code**](https://github.com/dotnet/samples/tree/master/framework/libraries/migrate-library/)

La section suivante décrit plusieurs méthodes pour ajouter la prise en charge de .NET Core pour ce dépôt en fonction des contraintes et de la complexité des projets existants.

## <a name="replace-existing-projects-with-a-multi-targeted-net-core-project"></a>Remplacer les projets existants par un projet .NET Core multiciblé

Réorganiser le référentiel de sorte que tous les fichiers * \*.csproj existants* soient supprimés et qu’un seul * \*fichier .csproj* soit créé qui cible plusieurs cadres. C’est une excellente option, car un seul projet est capable de compiler pour différents cadres. Elle permet également de gérer différentes options de compilation et dépendances par framework ciblé.

![Créer un csproj ciblant plusieurs frameworks](./media/project-structure/multi-targeted-project.png)

[**Source Code**](https://github.com/dotnet/samples/tree/master/framework/libraries/migrate-library-csproj/)

Les modifications à noter sont :

- Remplacement de *packages.config* et de *\*.csproj* par un nouveau [.csproj *\*.NET Core*](https://github.com/dotnet/samples/tree/master/framework/libraries/migrate-library-csproj/src/Car/Car.csproj). Les packages NuGet sont spécifiés avec `<PackageReference> ItemGroup`.

## <a name="keep-existing-projects-and-create-a-net-core-project"></a>Conserver les projets existants et créer un projet .NET Core

Si des projets existants ciblent des frameworks plus anciens, vous pouvez laisser ces projets inchangés et utiliser un projet .NET Core pour cibler les futurs frameworks.

![Projet .NET Core avec un projet existant dans un dossier différent](./media/project-structure/separate-projects-same-source.png)

[**Source Code**](https://github.com/dotnet/samples/tree/master/framework/libraries/migrate-library-csproj-keep-existing/)

Le projet .NET Core et les projets existants sont conservés dans des dossiers distincts. Garder des projets dans des dossiers séparés évite de vous forcer à avoir Visual Studio 2017 ou des versions ultérieures. Vous pouvez créer une solution distincte qui ouvre seulement les anciens projets.

## <a name="see-also"></a>Voir aussi

- [.NET Documentation de portage de base](index.md)
