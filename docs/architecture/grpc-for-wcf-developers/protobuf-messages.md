---
title: Messages Protobuf-gRPC pour les développeurs WCF
description: Découvrez comment les messages Protobuf sont définis dans l’IDL et générés dans C#.
author: markrendle
ms.date: 09/09/2019
ms.openlocfilehash: f6bb67fe3bc37fcb49c0e69b7960a00d584307b8
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2019
ms.locfileid: "71184203"
---
# <a name="protobuf-messages"></a>Messages Protobuf

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Cette section explique comment déclarer des messages Protobuf dans `.proto` des fichiers, explique les concepts fondamentaux des nombres et types de champs et examine le C# code généré par le `protoc` compilateur. Le reste du chapitre aborde plus en détail la façon dont les différents types de données sont représentés dans Protobuf.

## <a name="declaring-a-message"></a>Déclaration d’un message

Dans WCF, une `Stock` classe pour une application commerciale boursière peut être définie comme dans l’exemple suivant :

```csharp
namespace TraderSys
{
    [DataContract]
    public class Stock
    {
        [DataMember]
        public int Id { get; set;}
        [DataMember]
        public string Symbol { get; set;}
        [DataMember]
        public string DisplayName { get; set;}
        [DataMember]
        public int MarketId { get; set; }
    }
}
```

Pour implémenter la classe équivalente dans Protobuf, elle doit être déclarée dans le `.proto` fichier. Le `protoc` compilateur génère ensuite la classe .net dans le cadre du processus de génération.

```protobuf
syntax "proto3";

option csharp_namespace = "TraderSys";

message Stock {

    int32 id = 1;
    string symbol = 2;
    string displayName = 3;
    int32 marketId = 4;

}  
```

La première ligne déclare la version de syntaxe utilisée. La version 3 de la langue a été publiée en 2016 et est la version recommandée pour les services gRPC.

La `option csharp_namespace` ligne spécifie l’espace de noms à utiliser pour C# les types générés. Cette option est ignorée lorsque le `.proto` fichier est compilé pour d’autres langues. Il est courant que les fichiers Protobuf contiennent des options spécifiques à la langue pour plusieurs langues.

La `Stock` définition de message spécifie quatre champs, chacun avec un type, un nom et un numéro de champ.

## <a name="field-numbers"></a>Numéros de champ

Les numéros de champ constituent une partie importante de Protobuf. Elles sont utilisées pour identifier les champs dans les données binaires codées, ce qui signifie qu’elles ne peuvent pas passer d’une version à une version de votre service. L’avantage est que la compatibilité ascendante et descendante est possible. Les clients et les services ignorent simplement les numéros de champ qu’ils ne connaissent pas, à condition que la possibilité de valeurs manquantes soit gérée.

Dans le format binaire, le numéro de champ est associé à un identificateur de type. Les numéros de champ de 1 à 15 peuvent être encodés avec leur type comme un octet unique ; les nombres compris entre 16 et 2047 prennent 2 octets. Vous pouvez aller plus haut si vous avez besoin de plus de 2047 champs sur un message pour une raison quelconque. Les identificateurs à un seul octet pour les numéros de champ 1 à 15 offrent de meilleures performances. vous devez donc les utiliser pour les champs les plus basiques et les plus fréquemment utilisés.

## <a name="types"></a>Types

Les déclarations de type utilisent les types de données scalaires natives de Protobuf, qui sont décrits plus en détail dans [la section suivante](protobuf-data-types.md). Le reste de ce chapitre traite des types intégrés de Protobuf et montre comment ils se rapportent aux types .NET courants.

> [!NOTE]
> Protobuf ne prend pas en charge `decimal` de manière native un type, donc double est utilisé à la place. Pour les applications qui requièrent une précision décimale complète, reportez-vous à la [section sur les décimales](protobuf-data-types.md#decimals) dans la partie suivante de ce chapitre.

## <a name="the-generated-code"></a>Code généré

Quand vous générez votre application, Protobuf crée des classes pour chacun de vos messages, en mappant ses C# types natifs aux types. Le type `Stock` généré aurait la signature suivante :

```csharp
public class Stock
{
    public int Id { get; set; }
    public string Symbol { get; set; }
    public string DisplayName { get; set; }
    public int MarketId { get; set; }
}
```

Le code réel qui est généré est beaucoup plus complexe, car chaque classe contient tout le code nécessaire pour sérialiser et désérialiser lui-même au format de câble binaire.

### <a name="property-names"></a>Noms des propriétés

Notez que le compilateur Protobuf appliqué `PascalCase` aux noms de propriétés bien qu’ils `camelCase` se trouvaient dans le `.proto` fichier. Il est préférable d’utiliser `camelCase` dans la définition de message afin que la génération de code pour d’autres plateformes produise la casse attendue pour leurs conventions.

>[!div class="step-by-step"]
>[Précédent](protocol-buffers.md)
>[Suivant](protobuf-data-types.md)
