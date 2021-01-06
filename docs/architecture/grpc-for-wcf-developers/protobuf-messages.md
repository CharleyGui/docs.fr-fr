---
title: Messages Protobuf-gRPC pour les développeurs WCF
description: Découvrez comment les messages Protobuf sont définis dans l’IDL et générés en C#.
ms.date: 12/15/2020
ms.openlocfilehash: c1f2a3071d45dcbe4b98d747f19fed508bad102f
ms.sourcegitcommit: 655f8a16c488567dfa696fc0b293b34d3c81e3df
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/06/2021
ms.locfileid: "97938102"
---
# <a name="protobuf-messages"></a>Messages Protobuf

Cette section explique comment déclarer des messages de tampon de protocole (Protobuf) dans des `.proto` fichiers. Il explique les concepts fondamentaux des nombres de champs et des types, et il examine le code C# généré par le `protoc` compilateur.

Le reste du chapitre aborde plus en détail la façon dont les différents types de données sont représentés dans Protobuf.

## <a name="declaring-a-message"></a>Déclaration d’un message

Dans Windows Communication Foundation (WCF), une `Stock` classe pour une application commerciale boursière peut être définie comme dans l’exemple suivant :

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

Pour implémenter la classe équivalente dans Protobuf, vous devez la déclarer dans le `.proto` fichier. Le `protoc` compilateur génère ensuite la classe .net dans le cadre du processus de génération.

```protobuf
syntax = "proto3";

option csharp_namespace = "TraderSys";

message Stock {

    int32 id = 1;
    string symbol = 2;
    string display_name = 3;
    int32 market_id = 4;

}  
```

La première ligne déclare la version de syntaxe utilisée. La version 3 de la langue a été publiée en 2016. C’est la version que nous recommandons pour les services gRPC.

La `option csharp_namespace` ligne spécifie l’espace de noms à utiliser pour les types C# générés. Cette option est ignorée lorsque le `.proto` fichier est compilé pour d’autres langues. Les fichiers Protobuf contiennent souvent des options spécifiques à la langue pour plusieurs langues.

La `Stock` définition du message spécifie quatre champs. Chaque a un type, un nom et un numéro de champ.

## <a name="field-numbers"></a>Numéros de champ

Les numéros de champ constituent une partie importante de Protobuf. Elles sont utilisées pour identifier les champs dans les données binaires codées, ce qui signifie qu’elles ne peuvent pas passer d’une version à une version de votre service. L’avantage est que la compatibilité descendante et la compatibilité ascendante sont possibles. Les clients et les services ignorent les numéros de champ qu’ils ne connaissent pas, à condition que la possibilité de valeurs manquantes soit gérée.

Dans le format binaire, le numéro de champ est associé à un identificateur de type. Les numéros de champ de 1 à 15 peuvent être encodés avec leur type comme un seul octet. Les nombres compris entre 16 et 2 047 prennent 2 octets. Vous pouvez aller plus haut si vous avez besoin de plus de 2 047 champs sur un message pour une raison quelconque. Les identificateurs sur un octet pour les numéros de champ 1 à 15 offrent de meilleures performances. vous devez donc les utiliser pour les champs les plus basiques et les plus fréquemment utilisés.

## <a name="types"></a>Types

Les déclarations de type utilisent les types de données scalaires natives de Protobuf, qui sont décrits plus en détail dans [la section suivante](protobuf-data-types.md). Le reste de ce chapitre traite des types intégrés de Protobuf et montre comment ils se rapportent aux types .NET courants.

> [!NOTE]
> Protobuf ne prend pas en charge de manière native un `decimal` type, donc `double` est utilisé à la place. Pour les applications qui requièrent une précision décimale complète, reportez-vous à la [section sur les décimales](protobuf-data-types.md#decimals) dans la partie suivante de ce chapitre.

## <a name="the-generated-code"></a>Code généré

Quand vous générez votre application, Protobuf crée des classes pour chacun de vos messages, en mappant ses types natifs aux types C#. Le `Stock` type généré aurait la signature suivante :

```csharp
public class Stock
{
    public int Id { get; set; }
    public string Symbol { get; set; }
    public string DisplayName { get; set; }
    public int MarketId { get; set; }
}
```

Le code réel qui est généré est beaucoup plus complexe que celui-ci. La raison en est que chaque classe contient tout le code nécessaire pour sérialiser et désérialiser lui-même au format de câble binaire.

### <a name="property-names"></a>Noms des propriétés

Notez que le compilateur Protobuf appliqué `PascalCase` aux noms de propriété, même s’ils se trouvaient `snake_case` dans le `.proto` fichier. Le [Guide de style Protobuf](https://developers.google.com/protocol-buffers/docs/style) recommande l’utilisation `snake_case` de dans vos définitions de message afin que la génération de code pour d’autres plateformes produise la casse attendue pour leurs conventions.

>[!div class="step-by-step"]
>[Précédent](protocol-buffers.md) 
> [Suivant](protobuf-data-types.md)
