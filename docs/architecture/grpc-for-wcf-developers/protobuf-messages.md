---
title: Messages Protobuf - gRPC pour les développeurs WCF
description: Découvrez comment les messages Protobuf sont définis dans l’IDL et générés en C.
ms.date: 09/09/2019
ms.openlocfilehash: 5b3d4383de39a3785ef804fec21939a740f54669
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79147982"
---
# <a name="protobuf-messages"></a>Messages Protobuf

Cette section couvre la façon de déclarer les `.proto` messages De mémoire tampon (Protobuf) dans les fichiers. Il explique les concepts fondamentaux des nombres et des types `protoc` de terrain, et il examine le code Cmd que le compilateur génère.

Le reste du chapitre examinera plus en détail comment différents types de données sont représentés dans Protobuf.

## <a name="declaring-a-message"></a>Déclarer un message

Dans Windows Communication Foundation (WCF), une `Stock` classe pour une application de négociation boursière peut être définie comme l’exemple suivant :

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

Pour implémenter la classe équivalente dans `.proto` Protobuf, vous devez la déclarer dans le fichier. Le `protoc` compilateur générera ensuite la classe .NET dans le cadre du processus de construction.

```protobuf
syntax "proto3";

option csharp_namespace = "TraderSys";

message Stock {

    int32 id = 1;
    string symbol = 2;
    string display_name = 3;
    int32 market_id = 4;

}  
```

La première ligne déclare la version syntaxe utilisée. La version 3 de la langue est sortie en 2016. C’est la version que nous recommandons pour les services gRPC.

La `option csharp_namespace` ligne spécifie l’espace nom à utiliser pour les types C générés. Cette option sera ignorée lorsque le `.proto` fichier sera compilé pour d’autres langues. Les fichiers Protobuf contiennent souvent des options spécifiques à la langue pour plusieurs langues.

La `Stock` définition du message spécifie quatre champs. Chacun a un type, un nom et un numéro de champ.

## <a name="field-numbers"></a>Numéros de terrain

Les numéros de terrain sont une partie importante de Protobuf. Ils sont utilisés pour identifier les champs dans les données codées binaires, ce qui signifie qu’ils ne peuvent pas changer de la version à la version de votre service. L’avantage est que la compatibilité vers l’arrière et la compatibilité vers l’avant sont possibles. Les clients et les services ignoreront simplement les numéros de terrain qu’ils ne connaissent pas, tant que la possibilité de manquer des valeurs est gérée.

Dans le format binaire, le numéro de champ est combiné avec un identifiant de type. Les numéros de champ de 1 à 15 peuvent être codés avec leur type comme un seul byte. Les numéros de 16 à 2 047 prennent 2 octets. Vous pouvez aller plus haut si vous avez besoin de plus de 2 047 champs sur un message pour n’importe quelle raison. Les identifiants d’endo unique pour les numéros de champ 1 à 15 offrent de meilleures performances, de sorte que vous devriez les utiliser pour les champs les plus basiques, fréquemment utilisés.

## <a name="types"></a>Types

Les déclarations de type utilisent les types de données scalaires indigènes de Protobuf, qui sont discutés plus en détail dans [la section suivante](protobuf-data-types.md). Le reste de ce chapitre couvrira les types intégrés de Protobuf et montrera comment ils se rapportent aux types .NET communs.

> [!NOTE]
> Protobuf ne supporte pas `decimal` un `double` type natif, est donc utilisé à la place. Pour les applications qui nécessitent une précision décimale complète, se référer à la [section sur les décimales](protobuf-data-types.md#decimals) dans la prochaine partie de ce chapitre.

## <a name="the-generated-code"></a>Code généré

Lorsque vous construisez votre application, Protobuf crée des classes pour chacun de vos messages, cartographiant ses types natifs en types C. Le `Stock` type généré aurait la signature suivante :

```csharp
public class Stock
{
    public int Id { get; set; }
    public string Symbol { get; set; }
    public string DisplayName { get; set; }
    public int MarketId { get; set; }
}
```

Le code réel qui est généré est beaucoup plus compliqué que cela. La raison en est que chaque classe contient tout le code nécessaire pour sérialiser et se déséialiser au format de fil binaire.

### <a name="property-names"></a>Noms de propriété

Notez que le compilateur `PascalCase` Protobuf s’est `snake_case` appliqué `.proto` aux noms de propriété, bien qu’ils étaient dans le fichier. Le [guide de style Protobuf](https://developers.google.com/protocol-buffers/docs/style) recommande d’utiliser `snake_case` dans vos définitions de messages afin que la génération de code pour d’autres plates-formes produise le cas prévu pour leurs conventions.

>[!div class="step-by-step"]
>[Suivant précédent](protocol-buffers.md)
>[Next](protobuf-data-types.md)
