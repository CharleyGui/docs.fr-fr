---
title: Sérialiser et désérialiser JSON à C# l’aide de-.net
author: tdykstra
ms.author: tdykstra
ms.date: 09/16/2019
helpviewer_keywords:
- JSON serialization
- serializing objects
- serialization
- objects, serializing
ms.assetid: 4d1111c0-9447-4231-a997-96a2b74b3453
ms.openlocfilehash: 5ce98a7908470a402779436db43333d46f5101fc
ms.sourcegitcommit: dfd612ba454ce775a766bcc6fe93bc1d43dfda47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/09/2019
ms.locfileid: "72180156"
---
# <a name="json-serialization-in-net---overview"></a>Sérialisation JSON dans .NET-vue d’ensemble

L’espace de noms `System.Text.Json` fournit des fonctionnalités pour sérialiser vers et désérialiser à partir de JavaScript Object Notation (JSON).

La conception de la bibliothèque met l’accent sur des performances élevées et une allocation de mémoire faible sur un ensemble complet de fonctionnalités. La prise en charge UTF-8 intégrée optimise le processus de lecture et d’écriture du texte JSON encodé au format UTF-8, qui est l’encodage le plus courant pour les données sur le Web et les fichiers sur le disque.

La bibliothèque fournit également des classes pour l’utilisation d’un modèle DOM (Document Object Model) en mémoire. Cette fonctionnalité permet un accès en lecture seule aléatoire des éléments dans un fichier JSON ou une chaîne. 

## <a name="how-to-get-the-library"></a>Obtention de la bibliothèque

* La bibliothèque est intégrée dans le cadre de l’infrastructure partagée [.net Core 3,0](https://aka.ms/netcore3download) .
* Pour les autres frameworks cibles, installez le package NuGet [System. Text. JSON](https://www.nuget.org/packages/System.Text.Json) . Le package prend en charge :
  * .NET Standard 2,0 et versions ultérieures
  * .NET Framework 4.6.1 et versions ultérieures
  * .NET Core 2,0, 2,1 et 2,2

## <a name="additional-resources"></a>Ressources supplémentaires

* [Comment utiliser la bibliothèque](system-text-json-how-to.md)
* [Code source](https://github.com/dotnet/corefx/tree/master/src/System.Text.Json)
* [Informations de référence sur les API](xref:System.Text.Json)
* [Feuille de route](https://github.com/dotnet/corefx/blob/master/src/System.Text.Json/roadmap/README.md)
* GitHub problèmes dans le référentiel dotnet/corefx
  * [Discussion sur le développement de System. Text. JSON](https://github.com/dotnet/corefx/issues/33115)
  * [Tous les problèmes liés à System. Text. JSON](https://github.com/dotnet/corefx/issues?q=is%3Aopen+is%3Aissue+label%3Aarea-System.Text.Json)
  * [Problèmes relatifs à System. Text. JSON étiquetés JSON-fonctionnalité-doc](https://github.com/dotnet/corefx/labels/json-functionality-doc)
