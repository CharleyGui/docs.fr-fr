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
# <a name="protobuf-enumerations"></a><span data-ttu-id="14b60-103">Énumérations Protobuf</span><span class="sxs-lookup"><span data-stu-id="14b60-103">Protobuf enumerations</span></span>

<span data-ttu-id="14b60-104">Protobuf prend en charge les types d’énumération.</span><span class="sxs-lookup"><span data-stu-id="14b60-104">Protobuf supports enumeration types.</span></span> <span data-ttu-id="14b60-105">Vous avez vu ce soutien dans la section précédente, où `Oneof` un enum a été utilisé pour déterminer le type de champ.</span><span class="sxs-lookup"><span data-stu-id="14b60-105">You saw this support in the previous section, where an enum was used to determine the type of a `Oneof` field.</span></span> <span data-ttu-id="14b60-106">Vous pouvez définir vos propres types d’énumération, et Protobuf les compilera aux types d’enum de C.</span><span class="sxs-lookup"><span data-stu-id="14b60-106">You can define your own enumeration types, and Protobuf will compile them to C# enum types.</span></span>

<span data-ttu-id="14b60-107">Parce que vous pouvez utiliser Protobuf avec différentes langues, les conventions de nommage pour les énumérations sont différentes des conventions de C.</span><span class="sxs-lookup"><span data-stu-id="14b60-107">Because you can use Protobuf with various languages, the naming conventions for enumerations are different from the C# conventions.</span></span> <span data-ttu-id="14b60-108">Cependant, le générateur de code convertit les noms en boîtier traditionnel C.</span><span class="sxs-lookup"><span data-stu-id="14b60-108">However, the code generator converts the names to the traditional C# case.</span></span> <span data-ttu-id="14b60-109">Si l’équivalent Pascal-case du nom de champ commence avec le nom d’énumération, alors il est supprimé.</span><span class="sxs-lookup"><span data-stu-id="14b60-109">If the Pascal-case equivalent of the field name starts with the enumeration name, then it's removed.</span></span>

<span data-ttu-id="14b60-110">Par exemple, dans le recensement Protobuf suivant, les `ACCOUNT_STATUS`champs sont préfixés avec .</span><span class="sxs-lookup"><span data-stu-id="14b60-110">For example, in the following Protobuf enumeration, the fields are prefixed with `ACCOUNT_STATUS`.</span></span> <span data-ttu-id="14b60-111">Ce préfixe est équivalent au nom `AccountStatus`Pascal-cas enum, .</span><span class="sxs-lookup"><span data-stu-id="14b60-111">This prefix is equivalent to the Pascal-case enum name, `AccountStatus`.</span></span>

```protobuf
enum AccountStatus {
  ACCOUNT_STATUS_UNKNOWN = 0;
  ACCOUNT_STATUS_PENDING = 1;
  ACCOUNT_STATUS_ACTIVE = 2;
  ACCOUNT_STATUS_SUSPENDED = 3;
  ACCOUNT_STATUS_CLOSED = 4;
}
```

<span data-ttu-id="14b60-112">Le générateur crée un enum Cmd équivalent au code suivant :</span><span class="sxs-lookup"><span data-stu-id="14b60-112">The generator creates a C# enum equivalent to the following code:</span></span>

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

<span data-ttu-id="14b60-113">Les définitions de recensement des protobufs *doivent* avoir une constante zéro comme premier champ.</span><span class="sxs-lookup"><span data-stu-id="14b60-113">Protobuf enumeration definitions *must* have a zero constant as their first field.</span></span> <span data-ttu-id="14b60-114">Comme dans C, vous pouvez déclarer plusieurs champs avec la même valeur.</span><span class="sxs-lookup"><span data-stu-id="14b60-114">As in C#, you can declare multiple fields with the same value.</span></span> <span data-ttu-id="14b60-115">Mais vous devez activer explicitement `allow_alias` cette option en utilisant l’option dans l’enum :</span><span class="sxs-lookup"><span data-stu-id="14b60-115">But you must explicitly enable this option by using the `allow_alias` option in the enum:</span></span>

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

<span data-ttu-id="14b60-116">Vous pouvez déclarer des énumérations au `.proto` niveau supérieur dans un fichier, ou imbriqué dans une définition de message.</span><span class="sxs-lookup"><span data-stu-id="14b60-116">You can declare enumerations at the top level in a `.proto` file, or nested within a message definition.</span></span> <span data-ttu-id="14b60-117">Les énumérations imbriquées, comme les messages `.Types` imbriqués, seront déclarées dans la classe statique dans la classe de messages générée.</span><span class="sxs-lookup"><span data-stu-id="14b60-117">Nested enumerations—like nested messages—will be declared within the `.Types` static class in the generated message class.</span></span>

<span data-ttu-id="14b60-118">Il n’y a aucun moyen d’appliquer [l’attribut [Flags]](xref:System.FlagsAttribute) à un enum généré par Protobuf, et Protobuf ne comprend pas les combinaisons de enum peu.</span><span class="sxs-lookup"><span data-stu-id="14b60-118">There's no way to apply the [[Flags]](xref:System.FlagsAttribute) attribute to a Protobuf-generated enum, and Protobuf doesn't understand bitwise enum combinations.</span></span> <span data-ttu-id="14b60-119">Regardez l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="14b60-119">Look at the following example:</span></span>

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

<span data-ttu-id="14b60-120">Si vous `product.AvailableIn` `Region.NorthAmerica | Region.SouthAmerica`définissez à , il est sérialisé comme la valeur `3`integer .</span><span class="sxs-lookup"><span data-stu-id="14b60-120">If you set `product.AvailableIn` to `Region.NorthAmerica | Region.SouthAmerica`, it's serialized as the integer value `3`.</span></span> <span data-ttu-id="14b60-121">Quand un client ou un serveur essaie de déséialiser la valeur, il `3`ne trouvera pas une correspondance dans la définition enum pour .</span><span class="sxs-lookup"><span data-stu-id="14b60-121">When a client or server tries to deserialize the value, it won't find a match in the enum definition for `3`.</span></span> <span data-ttu-id="14b60-122">Le résultat `Region.None`sera .</span><span class="sxs-lookup"><span data-stu-id="14b60-122">The result will be `Region.None`.</span></span>

<span data-ttu-id="14b60-123">La meilleure façon de travailler avec plusieurs valeurs enum `repeated` dans Protobuf est d’utiliser un champ du type enum.</span><span class="sxs-lookup"><span data-stu-id="14b60-123">The best way to work with multiple enum values in Protobuf is to use a `repeated` field of the enum type.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="14b60-124">[Suivant précédent](protobuf-any-oneof.md)
>[Next](protobuf-maps.md)</span><span class="sxs-lookup"><span data-stu-id="14b60-124">[Previous](protobuf-any-oneof.md)
[Next](protobuf-maps.md)</span></span>
