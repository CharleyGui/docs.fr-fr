---
title: Membres
description: En savoir plus sur les membres F# d’objet dans le langage de programmation.
ms.date: 05/16/2016
ms.openlocfilehash: 2e85d014cd1e9b7997638cb210fed5705c217719
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73425072"
---
# <a name="members"></a>Membres

Cette section décrit les membres de types d’objet F#.

## <a name="remarks"></a>Notes

Les *membres* sont des fonctionnalités qui font partie d’une définition de type et qui sont déclarées avec le mot clé `member`. Les types d’objet F#, comme les enregistrements, les classes, les unions discriminées, les interfaces et les structures, prennent en charge les membres. Pour plus d’informations, consultez [Enregistrements](../records.md), [Classes](../classes.md), [Unions discriminées](../discriminated-Unions.md), [Interfaces](../interfaces.md) et [Structures](../structures.md).

Les membres constituent en général l’interface publique d’un type ; c’est pourquoi ils sont publics, sauf spécification contraire. Les membres peuvent également être déclarés comme privés ou internes. Pour plus d’informations, consultez [Contrôle d’accès](../access-Control.md). Des signatures peuvent également être utilisées pour les types pour exposer ou ne pas exposer certains membres d’un type. Pour plus d’informations, consultez [Signatures](../signature-files.md).

Les champs privés et les liaisons `do`, qui sont uniquement utilisés avec des classes, ne sont pas de vrais membres parce qu’ils ne font jamais partie de l’interface publique d’un type et ne sont pas déclarés avec le mot clé `member`. Toutefois, ils sont décrits dans cette section.

## <a name="related-topics"></a>Rubriques connexes

|Rubrique|Description|
|-----|-----------|
|[Liaisons `let` dans des classes](let-bindings-in-classes.md)|Décrit la définition de champs et de fonctions privés dans des classes.|
|[Liaisons `do` dans des classes](do-bindings-in-classes.md)|Décrit la spécification du code d’initialisation d’objet.|
|[Propriétés](properties.md)|Décrit les membres de propriété dans les classes et d’autres types.|
|[Propriétés indexées](indexed-properties.md)|Décrit les propriétés de type tableau dans des classes et d’autres types.|
|[Méthodes](methods.md)|Décrit les fonctions qui sont membres d’un type.|
|[Constructeurs](constructors.md)|Décrit les fonctions spéciales qui initialisent des objets d’un type.|
|[Surcharge d'opérateur](../operator-overloading.md)|Décrit la définition d’opérateurs personnalisés pour les types.|
|[Événements](events.md)|Décrit la définition d’événements et la prise en charge de la gestion des événements en F#.|
|[Champs explicites : mot clé `val`](explicit-fields-the-val-keyword.md)|Décrit la définition de champs non initialisés dans un type.|
