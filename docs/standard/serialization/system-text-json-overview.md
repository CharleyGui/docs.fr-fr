---
title: Sérialiser et désérialiser JSON à C# l’aide de-.net
ms.date: 01/10/2020
no-loc:
- System.Text.Json
- Newtonsoft.Json
helpviewer_keywords:
- JSON serialization
- serializing objects
- serialization
- objects, serializing
ms.openlocfilehash: acb83be9b20a155b6b6a9fb5ade38e099f54e71d
ms.sourcegitcommit: 5d769956a04b6d68484dd717077fabc191c21da5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/17/2020
ms.locfileid: "76163590"
---
# <a name="json-serialization-and-deserialization-marshalling-and-unmarshalling-in-net---overview"></a>Sérialisation et désérialisation JSON (marshaling et démarshaling) dans .NET-vue d’ensemble

L’espace de noms `System.Text.Json` fournit des fonctionnalités pour sérialiser vers et désérialiser à partir de JavaScript Object Notation (JSON).

La conception de la bibliothèque met l’accent sur des performances élevées et une allocation de mémoire faible sur un ensemble complet de fonctionnalités. La prise en charge UTF-8 intégrée optimise le processus de lecture et d’écriture du texte JSON encodé au format UTF-8, qui est l’encodage le plus courant pour les données sur le Web et les fichiers sur le disque.

La bibliothèque fournit également des classes pour l’utilisation d’un modèle DOM (Document Object Model) en mémoire. Cette fonctionnalité permet un accès en lecture seule aléatoire des éléments dans un fichier JSON ou une chaîne. 

## <a name="how-to-get-the-library"></a>Obtention de la bibliothèque

* La bibliothèque est intégrée dans le cadre de l’infrastructure partagée [.net Core 3,0](https://aka.ms/netcore3download) .
* Pour les autres frameworks cibles, installez le package NuGet [System.Text.Json](https://www.nuget.org/packages/System.Text.Json) . Le package prend en charge :
  * .NET Standard 2,0 et versions ultérieures
  * .NET Framework 4.7.2 et versions ultérieures
  * .NET Core 2,0, 2,1 et 2,2

## <a name="additional-resources"></a>Ressources supplémentaires

* [Comment utiliser la bibliothèque](system-text-json-how-to.md)
* [Migration à partir de Newtonsoft.Json](system-text-json-migrate-from-newtonsoft-how-to.md)
* [Comment écrire des convertisseurs](system-text-json-converters-how-to.md)
* [code source System.Text.Json](https://github.com/dotnet/runtime/tree/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json)
* [informations de référence sur l’API System.Text.Json](xref:System.Text.Json)
* [System.Text.Json. Référence de l’API de sérialisation](xref:System.Text.Json.Serialization)
<!-- * [Roadmap](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/roadmap/README.md)-->
