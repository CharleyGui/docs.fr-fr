---
title: Énumérations Protobuf-gRPC pour les développeurs WCF
description: Découvrez comment déclarer et utiliser des énumérations dans Protobuf.
ms.date: 09/09/2019
ms.openlocfilehash: 01cf4a4e5e0eda1e7ddff2a6780119fcb3120dad
ms.sourcegitcommit: 771c554c84ba38cbd4ac0578324ec4cfc979cf2e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/21/2020
ms.locfileid: "77543142"
---
# <a name="protobuf-enumerations"></a><span data-ttu-id="6c8f5-103">Énumérations Protobuf</span><span class="sxs-lookup"><span data-stu-id="6c8f5-103">Protobuf enumerations</span></span>

<span data-ttu-id="6c8f5-104">Protobuf prend en charge les types énumération.</span><span class="sxs-lookup"><span data-stu-id="6c8f5-104">Protobuf supports enumeration types.</span></span> <span data-ttu-id="6c8f5-105">Vous avez vu cette prise en charge dans la section précédente, où une énumération a été utilisée pour déterminer le type d’un champ de `Oneof`.</span><span class="sxs-lookup"><span data-stu-id="6c8f5-105">You saw this support in the previous section, where an enum was used to determine the type of a `Oneof` field.</span></span> <span data-ttu-id="6c8f5-106">Vous pouvez définir vos propres types énumération, et Protobuf les compilera en C# types ENUM.</span><span class="sxs-lookup"><span data-stu-id="6c8f5-106">You can define your own enumeration types, and Protobuf will compile them to C# enum types.</span></span> 

<span data-ttu-id="6c8f5-107">Étant donné que vous pouvez utiliser Protobuf avec différents langages, les conventions d’affectation des noms pour C# les énumérations diffèrent des conventions.</span><span class="sxs-lookup"><span data-stu-id="6c8f5-107">Because you can use Protobuf with various languages, the naming conventions for enumerations are different from the C# conventions.</span></span> <span data-ttu-id="6c8f5-108">Toutefois, le générateur de code convertit les noms dans C# le cas traditionnel.</span><span class="sxs-lookup"><span data-stu-id="6c8f5-108">However, the code generator converts the names to the traditional C# case.</span></span> <span data-ttu-id="6c8f5-109">Si l’équivalent en casse Pascal du nom de champ commence par le nom de l’énumération, il est supprimé.</span><span class="sxs-lookup"><span data-stu-id="6c8f5-109">If the Pascal-case equivalent of the field name starts with the enumeration name, then it's removed.</span></span>

<span data-ttu-id="6c8f5-110">Par exemple, dans l’énumération Protobuf suivante, les champs sont préfixés avec `ACCOUNT_STATUS`.</span><span class="sxs-lookup"><span data-stu-id="6c8f5-110">For example, in the following Protobuf enumeration, the fields are prefixed with `ACCOUNT_STATUS`.</span></span> <span data-ttu-id="6c8f5-111">Ce préfixe est équivalent au nom de l’enum en respectant la casse Pascal, `AccountStatus`.</span><span class="sxs-lookup"><span data-stu-id="6c8f5-111">This prefix is equivalent to the Pascal-case enum name, `AccountStatus`.</span></span>

```protobuf
enum AccountStatus {
  ACCOUNT_STATUS_UNKNOWN = 0;
  ACCOUNT_STATUS_PENDING = 1;
  ACCOUNT_STATUS_ACTIVE = 2;
  ACCOUNT_STATUS_SUSPENDED = 3;
  ACCOUNT_STATUS_CLOSED = 4;
}
```

<span data-ttu-id="6c8f5-112">Le générateur crée un C# enum équivalent au code suivant :</span><span class="sxs-lookup"><span data-stu-id="6c8f5-112">The generator creates a C# enum equivalent to the following code:</span></span>

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

<span data-ttu-id="6c8f5-113">Les définitions d’énumération Protobuf *doivent* avoir une constante zéro comme premier champ.</span><span class="sxs-lookup"><span data-stu-id="6c8f5-113">Protobuf enumeration definitions *must* have a zero constant as their first field.</span></span> <span data-ttu-id="6c8f5-114">Comme dans C#, vous pouvez déclarer plusieurs champs avec la même valeur.</span><span class="sxs-lookup"><span data-stu-id="6c8f5-114">As in C#, you can declare multiple fields with the same value.</span></span> <span data-ttu-id="6c8f5-115">Toutefois, vous devez activer explicitement cette option à l’aide de l’option `allow_alias` dans l’énumération :</span><span class="sxs-lookup"><span data-stu-id="6c8f5-115">But you must explicitly enable this option by using the `allow_alias` option in the enum:</span></span>

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

<span data-ttu-id="6c8f5-116">Vous pouvez déclarer des énumérations au niveau supérieur dans un fichier `.proto` ou imbriquées dans une définition de message.</span><span class="sxs-lookup"><span data-stu-id="6c8f5-116">You can declare enumerations at the top level in a `.proto` file, or nested within a message definition.</span></span> <span data-ttu-id="6c8f5-117">Les énumérations imbriquées, comme les messages imbriqués, seront déclarées dans la classe statique `.Types` de la classe de message générée.</span><span class="sxs-lookup"><span data-stu-id="6c8f5-117">Nested enumerations—like nested messages—will be declared within the `.Types` static class in the generated message class.</span></span>

<span data-ttu-id="6c8f5-118">Il n’existe aucun moyen d’appliquer l’attribut [[Flags]](xref:System.FlagsAttribute) à un enum généré par Protobuf, et Protobuf ne comprend pas les combinaisons d’énumération au niveau du bit.</span><span class="sxs-lookup"><span data-stu-id="6c8f5-118">There's no way to apply the [[Flags]](xref:System.FlagsAttribute) attribute to a Protobuf-generated enum, and Protobuf doesn't understand bitwise enum combinations.</span></span> <span data-ttu-id="6c8f5-119">Examinez l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="6c8f5-119">Look at the following example:</span></span>

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

<span data-ttu-id="6c8f5-120">Si vous affectez à `product.AvailableIn` la valeur `Region.NorthAmerica | Region.SouthAmerica`, elle est sérialisée en tant que valeur entière `3`.</span><span class="sxs-lookup"><span data-stu-id="6c8f5-120">If you set `product.AvailableIn` to `Region.NorthAmerica | Region.SouthAmerica`, it's serialized as the integer value `3`.</span></span> <span data-ttu-id="6c8f5-121">Lorsqu’un client ou un serveur tente de désérialiser la valeur, il ne trouve pas de correspondance dans la définition d’énumération pour `3`.</span><span class="sxs-lookup"><span data-stu-id="6c8f5-121">When a client or server tries to deserialize the value, it won't find a match in the enum definition for `3`.</span></span> <span data-ttu-id="6c8f5-122">Le résultat sera `Region.None`.</span><span class="sxs-lookup"><span data-stu-id="6c8f5-122">The result will be `Region.None`.</span></span>

<span data-ttu-id="6c8f5-123">La meilleure façon de travailler avec plusieurs valeurs enum dans Protobuf consiste à utiliser un champ `repeated` du type enum.</span><span class="sxs-lookup"><span data-stu-id="6c8f5-123">The best way to work with multiple enum values in Protobuf is to use a `repeated` field of the enum type.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="6c8f5-124">[Précédent](protobuf-any-oneof.md)
>[Suivant](protobuf-maps.md)</span><span class="sxs-lookup"><span data-stu-id="6c8f5-124">[Previous](protobuf-any-oneof.md)
[Next](protobuf-maps.md)</span></span>
