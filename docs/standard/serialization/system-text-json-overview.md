---
title: Sérialiser et désérialiser JSON à l’aide de C#-.NET
description: Cette vue d’ensemble décrit les System.Text.Json fonctionnalités d’espace de noms pour sérialiser vers et désérialiser à partir de JSON dans .net.
ms.date: 01/10/2020
no-loc:
- System.Text.Json
- Newtonsoft.Json
helpviewer_keywords:
- JSON serialization
- serializing objects
- serialization
- objects, serializing
ms.openlocfilehash: b4432e7a137720216e7c0941b3384ce7ad7049e9
ms.sourcegitcommit: 7ef96827b161ef3fcde75f79d839885632e26ef1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/07/2021
ms.locfileid: "97970913"
---
# <a name="json-serialization-and-deserialization-marshalling-and-unmarshalling-in-net---overview"></a>Sérialisation et désérialisation JSON (marshaling et démarshaling) dans .NET-vue d’ensemble

L' `System.Text.Json` espace de noms fournit des fonctionnalités pour sérialiser vers et désérialiser à partir de JavaScript Object Notation (JSON).

La conception de la bibliothèque met l’accent sur des performances élevées et une allocation de mémoire faible sur un ensemble complet de fonctionnalités. La prise en charge UTF-8 intégrée optimise le processus de lecture et d’écriture du texte JSON encodé au format UTF-8, qui est l’encodage le plus courant pour les données sur le Web et les fichiers sur le disque.

La bibliothèque fournit également des classes pour l’utilisation d’un modèle DOM (Document Object Model) en mémoire. Cette fonctionnalité permet un accès en lecture seule aléatoire des éléments dans un fichier JSON ou une chaîne.

## <a name="how-to-get-the-library"></a>Obtention de la bibliothèque

* La bibliothèque est intégrée dans le cadre de l’infrastructure partagée pour .NET Core 3,0 et versions ultérieures.
* Pour les versions antérieures du Framework, installez le [System.Text.Json](https://www.nuget.org/packages/System.Text.Json) package NuGet. Le package prend en charge :

  * .NET Standard 2,0 et versions ultérieures
  * .NET Framework 4.7.2 et versions ultérieures
  * .NET Core 2,0, 2,1 et 2,2

## <a name="additional-resources"></a>Ressources supplémentaires

* [Comment utiliser la bibliothèque](system-text-json-how-to.md)
* [Instancier des instances JsonSerializerOptions](system-text-json-configure-options.md)
* [Activer la correspondance non sensible à la casse](system-text-json-character-casing.md)
* [Personnaliser les noms et valeurs de propriété](system-text-json-customize-properties.md)
* [Ignorer les propriétés](system-text-json-ignore-properties.md)
* [Autoriser JSON non valide](system-text-json-invalid-json.md)
* [Gérer le JSON de dépassement](system-text-json-handle-overflow.md)
* [Préserver les références](system-text-json-preserve-references.md)
* [Types immuables et accesseurs non publics](system-text-json-immutability.md)
* [Sérialisation polymorphe](system-text-json-polymorphism.md)
* [Migrer de Newtonsoft.Json vers System.Text.Json](system-text-json-migrate-from-newtonsoft-how-to.md)
* [Personnaliser l’encodage de caractères](system-text-json-character-encoding.md)
* [Écrire des sérialiseurs et des désérialiseurs personnalisés](write-custom-serializer-deserializer.md)
* [Écrire des convertisseurs personnalisés pour la sérialisation JSON](system-text-json-converters-how-to.md)
* [Prise en charge DateTime et DateTimeOffset](../datetime/system-text-json-support.md)
* [Types de collections pris en charge dans System.Text.Json](system-text-json-supported-collection-types.md)
* [System.Text.Json Référence d’API](xref:System.Text.Json)
* [System.Text.Json. Référence de l’API de sérialisation](xref:System.Text.Json.Serialization)
