---
title: Énumérations Protobuf - gRPC pour les développeurs WCF
description: Apprenez à déclarer et à utiliser des énumérations dans Protobuf.
ms.date: 09/09/2019
ms.openlocfilehash: 2177f568a671fa0e651625c6e025ac70c243feb5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79148073"
---
# <a name="protobuf-enumerations"></a>Énumérations Protobuf

Protobuf prend en charge les types d’énumération. Vous avez vu ce soutien dans la section précédente, où `Oneof` un enum a été utilisé pour déterminer le type de champ. Vous pouvez définir vos propres types d’énumération, et Protobuf les compilera aux types d’enum de C.

Parce que vous pouvez utiliser Protobuf avec différentes langues, les conventions de nommage pour les énumérations sont différentes des conventions de C. Cependant, le générateur de code convertit les noms en boîtier traditionnel C. Si l’équivalent Pascal-case du nom de champ commence avec le nom d’énumération, alors il est supprimé.

Par exemple, dans le recensement Protobuf suivant, les `ACCOUNT_STATUS`champs sont préfixés avec . Ce préfixe est équivalent au nom `AccountStatus`Pascal-cas enum, .

```protobuf
enum AccountStatus {
  ACCOUNT_STATUS_UNKNOWN = 0;
  ACCOUNT_STATUS_PENDING = 1;
  ACCOUNT_STATUS_ACTIVE = 2;
  ACCOUNT_STATUS_SUSPENDED = 3;
  ACCOUNT_STATUS_CLOSED = 4;
}
```

Le générateur crée un enum Cmd équivalent au code suivant :

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

Les définitions de recensement des protobufs *doivent* avoir une constante zéro comme premier champ. Comme dans C, vous pouvez déclarer plusieurs champs avec la même valeur. Mais vous devez activer explicitement `allow_alias` cette option en utilisant l’option dans l’enum :

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

Vous pouvez déclarer des énumérations au `.proto` niveau supérieur dans un fichier, ou imbriqué dans une définition de message. Les énumérations imbriquées, comme les messages `.Types` imbriqués, seront déclarées dans la classe statique dans la classe de messages générée.

Il n’y a aucun moyen d’appliquer [l’attribut [Flags]](xref:System.FlagsAttribute) à un enum généré par Protobuf, et Protobuf ne comprend pas les combinaisons de enum peu. Regardez l’exemple suivant :

```protobuf
enum Region {
  REGION_NONE = 0;
  REGION_NORTH_AMERICA = 1;
  REGION_SOUTH_AMERICA = 2;
  REGION_EMEA = 4;
  REGION_APAC = 8;
}

message Product {
  Region available_in = 1;
}
```

Si vous `product.AvailableIn` `Region.NorthAmerica | Region.SouthAmerica`définissez à , il est sérialisé comme la valeur `3`integer . Quand un client ou un serveur essaie de déséialiser la valeur, il `3`ne trouvera pas une correspondance dans la définition enum pour . Le résultat `Region.None`sera .

La meilleure façon de travailler avec plusieurs valeurs enum `repeated` dans Protobuf est d’utiliser un champ du type enum.

>[!div class="step-by-step"]
>[Suivant précédent](protobuf-any-oneof.md)
>[Next](protobuf-maps.md)
