---
title: Énumérations Protobuf-gRPC pour les développeurs WCF
description: Découvrez comment déclarer et utiliser des énumérations dans Protobuf.
author: markrendle
ms.date: 09/09/2019
ms.openlocfilehash: d93319b713588129a19246976a82bb03a90ce680
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2019
ms.locfileid: "71184238"
---
# <a name="protobuf-enumerations"></a>Énumérations Protobuf

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Protobuf prend en charge les types énumération, comme indiqué dans la section précédente où une énumération a été utilisée `oneof` pour déterminer le type d’un champ. Vous pouvez définir vos propres types énumération et Protobuf les compilera en C# types ENUM. Étant donné que Protobuf peut être utilisé avec des langages différents, les conventions d’affectation des noms C# pour les énumérations diffèrent des conventions. Toutefois, le générateur de code est intelligent et convertit les noms dans C# le cas traditionnel. Si l’équivalent en casse Pascal du nom de champ commence par le nom de l’énumération, il est supprimé.

Par exemple, dans cette énumération Protobuf, les champs sont préfixés avec `ACCOUNT_STATUS`, ce qui équivaut au nom de l’enum de la casse Pascal :. `AccountStatus`

```protobuf
enum AccountStatus {
  ACCOUNT_STATUS_UNKNOWN = 0;
  ACCOUNT_STATUS_PENDING = 1;
  ACCOUNT_STATUS_ACTIVE = 2;
  ACCOUNT_STATUS_SUSPENDED = 3;
  ACCOUNT_STATUS_CLOSED = 4;
}
```

Par conséquent, le générateur crée C# un enum équivalent au code suivant :

```csharp
public enum AccountStatus
{
    Unknown = 0,
    Pending = 1,
    Active = 2,
    Suspended = 3,
    Closed = 4
}
```

Les définitions d’énumération Protobuf **doivent** avoir une constante zéro comme premier champ. Comme dans C#, vous pouvez déclarer plusieurs champs avec la même valeur, mais vous devez activer explicitement cette option à l' `allow_alias` aide de l’option dans l’énumération :

```protobuf
enum AccountStatus {
  option allow_alias = true;
  ACCOUNT_STATUS_UNKNOWN = 0;
  ACCOUNT_STATUS_PENDING = 1;
  ACCOUNT_STATUS_ACTIVE = 2;
  ACCOUNT_STATUS_SUSPENDED = 3;
  ACCOUNT_STATUS_CLOSED = 4;
  ACCOUNT_STATUS_CANCELLED = 4;
}
```

Vous pouvez déclarer des énumérations au niveau supérieur dans un `.proto` fichier ou imbriquées dans une définition de message. Les énumérations imbriquées, comme les messages imbriqués, seront déclarées `.Types` dans la classe statique de la classe de message générée.

Il n’existe aucun moyen d’appliquer l’attribut [[Flags]](xref:System.FlagsAttribute) à un enum généré par Protobuf, et Protobuf ne comprend pas les combinaisons d’énumération au niveau du bit. Jetez un coup d’œil à l’exemple suivant :

```protobuf
enum Region {
  REGION_NONE = 0;
  REGION_NORTH_AMERICA = 1;
  REGION_SOUTH_AMERICA = 2;
  REGION_EMEA = 4;
  REGION_APAC = 8;
}

message Product {
  Region availableIn = 1;
}
```

Si vous `product.AvailableIn` affectez `Region.NorthAmerica | Region.SouthAmerica`à la valeur, elle est sérialisée en `3`tant que valeur entière. Lorsqu’un client ou un serveur tente de désérialiser la valeur, il ne trouve pas de correspondance dans la définition `3` enum pour et le résultat `Region.None`est.

La meilleure façon de travailler avec plusieurs valeurs enum dans Protobuf consiste à utiliser un `repeated` champ du type enum.

>[!div class="step-by-step"]
>[Précédent](protobuf-any-oneof.md)
>[Suivant](protobuf-maps.md)
