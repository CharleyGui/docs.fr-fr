---
title: Sérialisation JSON dans .NET
author: tdykstra
ms.author: tdykstra
ms.date: 09/16/2019
helpviewer_keywords:
- JSON serialization
- serializing objects
- serialization
- objects, serializing
ms.assetid: 4d1111c0-9447-4231-a997-96a2b74b3453
ms.openlocfilehash: 6cb45fded220b6123dbf4461f5f1cf1c3556ff69
ms.sourcegitcommit: a2d0e1f66367367065bc8dc0dde488ab536da73f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2019
ms.locfileid: "71083093"
---
# <a name="json-serialization-in-net"></a>Sérialisation JSON dans .NET

L' `System.Text.Json` espace de noms fournit des fonctionnalités pour sérialiser vers et à partir de JavaScript Object Notation (JSON).

La conception de la bibliothèque met l’accent sur des performances élevées et une allocation de mémoire faible sur un ensemble complet de fonctionnalités. La prise en charge UTF-8 intégrée optimise le processus de lecture et d’écriture du texte JSON encodé au format UTF-8, qui est l’encodage le plus courant pour les données sur le Web et les fichiers sur le disque.

La bibliothèque fournit également des classes pour l’utilisation d’un modèle DOM (Document Object Model) en mémoire. Cette fonctionnalité permet un accès en lecture seule aléatoire des éléments dans un fichier JSON ou une chaîne. 

## <a name="how-to-get-the-library"></a>Obtention de la bibliothèque

* La bibliothèque est intégrée dans le cadre de l’infrastructure partagée [.net Core 3,0](https://aka.ms/netcore3download) .
* Pour les autres frameworks cibles, installez le package NuGet [System. Text. JSON](https://www.nuget.org/packages/System.Text.Json) . Le package prend en charge :
  * .NET Standard 2,0 et versions ultérieures
  * .NET Framework 4,61 et versions ultérieures
  * .NET Core 2,0 et versions ultérieures

## <a name="additional-resources"></a>Ressources supplémentaires

* [Comment utiliser la bibliothèque](system-text-json-how-to.md)
* [Code source](https://github.com/dotnet/corefx/tree/master/src/System.Text.Json)
* [Informations de référence sur les API](xref:System.Text.Json)
* [Feuille de route](https://github.com/dotnet/corefx/blob/master/src/System.Text.Json/roadmap/README.md)
* GitHub problèmes dans le référentiel dotnet/corefx
  * [Discussion sur le développement de System. Text. JSON](https://github.com/dotnet/corefx/issues/33115)
  * [Tous les problèmes liés à System. Text. JSON](https://github.com/dotnet/corefx/issues?q=is%3Aopen+is%3Aissue+label%3Aarea-System.Text.Json)
  * [Problèmes relatifs à System. Text. JSON étiquetés JSON-fonctionnalité-doc](https://github.com/dotnet/corefx/labels/json-functionality-doc)
