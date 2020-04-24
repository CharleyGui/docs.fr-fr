---
title: Limitations de dapper
ms.date: 12/13/2019
description: Décrit certaines des limitations que vous pouvez rencontrer lors de l’utilisation de dapper.
ms.openlocfilehash: 396507f25f591a9ab5c3bb07c0af6fd8d175e4ea
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/11/2020
ms.locfileid: "75901209"
---
# <a name="dapper-limitations"></a>Limitations de dapper

Il existe quelques limitations que vous devez connaître lors de l’utilisation de Microsoft. Data. sqlite avec [dapper](https://stackexchange.github.io/Dapper/).

## <a name="parameters"></a>Paramètres

Les noms de paramètres SQLite sont sensibles à la casse. Assurez-vous que les noms de paramètres utilisés dans SQL correspondent à la casse des propriétés de l’objet anonyme. Le problème [#18861](https://github.com/dotnet/efcore/issues/18861) améliorer cette expérience.

Dapper s’attend également à ce que les `@` paramètres utilisent le préfixe. Les autres préfixes ne fonctionneront pas.

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/DapperSample/Program.cs?name=snippet_Parameter)]

## <a name="data-types"></a>Types de données

Dapper lit les valeurs à l’aide de l’indexeur SqliteDataReader. Le type de retour de cet indexeur est Object, ce qui signifie qu’il ne renverra jamais de valeurs de type long, double, String ou Byte []. Pour plus d’informations, consultez [types de données](types.md). Dapper gère la plupart des conversions entre ces types primitifs et les autres. Malheureusement, il ne gère `DateTimeOffset`pas `Guid`, ou `TimeSpan`. Créez des gestionnaires de types si vous souhaitez utiliser ces types dans vos résultats.

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/DapperSample/Program.cs?name=snippet_TypeHandlers)]

N’oubliez pas d’ajouter les gestionnaires de types avant d’interroger.

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/DapperSample/Program.cs?name=snippet_AddTypeHandlers)]

## <a name="see-also"></a>Voir aussi

* [Types de données](types.md)
* [Limitations Async](async.md)
