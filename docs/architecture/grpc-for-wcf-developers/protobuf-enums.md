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
# <a name="protobuf-enumerations"></a><span data-ttu-id="7e124-103">Énumérations Protobuf</span><span class="sxs-lookup"><span data-stu-id="7e124-103">Protobuf enumerations</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="7e124-104">Protobuf prend en charge les types énumération, comme indiqué dans la section précédente où une énumération a été utilisée `oneof` pour déterminer le type d’un champ.</span><span class="sxs-lookup"><span data-stu-id="7e124-104">Protobuf supports enumeration types, as seen in the previous section where an enum was used to determine the type of a `oneof` field.</span></span> <span data-ttu-id="7e124-105">Vous pouvez définir vos propres types énumération et Protobuf les compilera en C# types ENUM.</span><span class="sxs-lookup"><span data-stu-id="7e124-105">You can define your own enumeration types and Protobuf will compile them to C# enum types.</span></span> <span data-ttu-id="7e124-106">Étant donné que Protobuf peut être utilisé avec des langages différents, les conventions d’affectation des noms C# pour les énumérations diffèrent des conventions.</span><span class="sxs-lookup"><span data-stu-id="7e124-106">Since Protobuf can be used with different languages, the naming conventions for enumerations are different from the C# conventions.</span></span> <span data-ttu-id="7e124-107">Toutefois, le générateur de code est intelligent et convertit les noms dans C# le cas traditionnel.</span><span class="sxs-lookup"><span data-stu-id="7e124-107">However, the code generator is clever and converts the names to the traditional C# case.</span></span> <span data-ttu-id="7e124-108">Si l’équivalent en casse Pascal du nom de champ commence par le nom de l’énumération, il est supprimé.</span><span class="sxs-lookup"><span data-stu-id="7e124-108">If the Pascal-case equivalent of the field name starts with the enumeration name, then it's removed.</span></span>

<span data-ttu-id="7e124-109">Par exemple, dans cette énumération Protobuf, les champs sont préfixés avec `ACCOUNT_STATUS`, ce qui équivaut au nom de l’enum de la casse Pascal :. `AccountStatus`</span><span class="sxs-lookup"><span data-stu-id="7e124-109">For example, in this Protobuf enumeration the fields are prefixed with `ACCOUNT_STATUS`, which is equivalent to the Pascal case enum name: `AccountStatus`.</span></span>

```protobuf
enum AccountStatus {
  ACCOUNT_STATUS_UNKNOWN = 0;
  ACCOUNT_STATUS_PENDING = 1;
  ACCOUNT_STATUS_ACTIVE = 2;
  ACCOUNT_STATUS_SUSPENDED = 3;
  ACCOUNT_STATUS_CLOSED = 4;
}
```

<span data-ttu-id="7e124-110">Par conséquent, le générateur crée C# un enum équivalent au code suivant :</span><span class="sxs-lookup"><span data-stu-id="7e124-110">So, the generator creates a C# enum equivalent to the following code:</span></span>

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

<span data-ttu-id="7e124-111">Les définitions d’énumération Protobuf **doivent** avoir une constante zéro comme premier champ.</span><span class="sxs-lookup"><span data-stu-id="7e124-111">Protobuf enumeration definitions **must** have a zero constant as their first field.</span></span> <span data-ttu-id="7e124-112">Comme dans C#, vous pouvez déclarer plusieurs champs avec la même valeur, mais vous devez activer explicitement cette option à l' `allow_alias` aide de l’option dans l’énumération :</span><span class="sxs-lookup"><span data-stu-id="7e124-112">As in C#, you can declare multiple fields with the same value, but you must explicitly enable this option using the `allow_alias` option in the enum:</span></span>

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

<span data-ttu-id="7e124-113">Vous pouvez déclarer des énumérations au niveau supérieur dans un `.proto` fichier ou imbriquées dans une définition de message.</span><span class="sxs-lookup"><span data-stu-id="7e124-113">You can declare enumerations at the top level in a `.proto` file, or nested within a message definition.</span></span> <span data-ttu-id="7e124-114">Les énumérations imbriquées, comme les messages imbriqués, seront déclarées `.Types` dans la classe statique de la classe de message générée.</span><span class="sxs-lookup"><span data-stu-id="7e124-114">Nested enumerations—like nested messages—will be declared within the `.Types` static class in the generated message class.</span></span>

<span data-ttu-id="7e124-115">Il n’existe aucun moyen d’appliquer l’attribut [[Flags]](xref:System.FlagsAttribute) à un enum généré par Protobuf, et Protobuf ne comprend pas les combinaisons d’énumération au niveau du bit.</span><span class="sxs-lookup"><span data-stu-id="7e124-115">There's no way to apply the [[Flags]](xref:System.FlagsAttribute) attribute to a Protobuf-generated enum, and Protobuf doesn't understand bitwise enum combinations.</span></span> <span data-ttu-id="7e124-116">Jetez un coup d’œil à l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="7e124-116">Take a look at the following example:</span></span>

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

<span data-ttu-id="7e124-117">Si vous `product.AvailableIn` affectez `Region.NorthAmerica | Region.SouthAmerica`à la valeur, elle est sérialisée en `3`tant que valeur entière.</span><span class="sxs-lookup"><span data-stu-id="7e124-117">If you set `product.AvailableIn` to `Region.NorthAmerica | Region.SouthAmerica`, it's serialized as the integer value `3`.</span></span> <span data-ttu-id="7e124-118">Lorsqu’un client ou un serveur tente de désérialiser la valeur, il ne trouve pas de correspondance dans la définition `3` enum pour et le résultat `Region.None`est.</span><span class="sxs-lookup"><span data-stu-id="7e124-118">When a client or server tries to deserialize the value, it won't find a match in the enum definition for `3` and the result will be `Region.None`.</span></span>

<span data-ttu-id="7e124-119">La meilleure façon de travailler avec plusieurs valeurs enum dans Protobuf consiste à utiliser un `repeated` champ du type enum.</span><span class="sxs-lookup"><span data-stu-id="7e124-119">The best way to work with multiple enum values in Protobuf is to use a `repeated` field of the enum type.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="7e124-120">[Précédent](protobuf-any-oneof.md)
>[Suivant](protobuf-maps.md)</span><span class="sxs-lookup"><span data-stu-id="7e124-120">[Previous](protobuf-any-oneof.md)
[Next](protobuf-maps.md)</span></span>
