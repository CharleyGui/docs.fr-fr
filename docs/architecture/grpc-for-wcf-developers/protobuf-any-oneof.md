---
title: Protobuf tous les champs et OneOf pour les types variant-gRPC pour les développeurs WCF
description: Découvrez comment utiliser le type any et le mot clé OneOf pour représenter des types d’objets variants dans des messages.
author: markrendle
ms.date: 09/09/2019
ms.openlocfilehash: 10f55288eb4a6aa603228da5b4850317d6bde614
ms.sourcegitcommit: 337bdc5a463875daf2cc6883e5a2da97d56f5000
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/24/2019
ms.locfileid: "72846389"
---
# <a name="protobuf-any-and-oneof-fields-for-variant-types"></a><span data-ttu-id="54a6b-103">Protobuf tous les champs et OneOf pour les types variant</span><span class="sxs-lookup"><span data-stu-id="54a6b-103">Protobuf Any and Oneof fields for variant types</span></span>

<span data-ttu-id="54a6b-104">La gestion des types de propriétés dynamiques (autrement dit, les propriétés de type `object`) dans WCF est compliquée.</span><span class="sxs-lookup"><span data-stu-id="54a6b-104">Handling dynamic property types (that is, properties of type `object`) in WCF is complicated.</span></span> <span data-ttu-id="54a6b-105">Les sérialiseurs doivent être spécifiés, les attributs [KnownType](xref:System.Runtime.Serialization.KnownTypeAttribute) doivent être fournis, et ainsi de suite.</span><span class="sxs-lookup"><span data-stu-id="54a6b-105">Serializers must be specified, [KnownType](xref:System.Runtime.Serialization.KnownTypeAttribute) attributes must be provided, and so on.</span></span>

<span data-ttu-id="54a6b-106">Protobuf fournit deux options plus simples pour traiter les valeurs qui peuvent être de plus d’un type.</span><span class="sxs-lookup"><span data-stu-id="54a6b-106">Protobuf provides two simpler options for dealing with values that may be of more than one type.</span></span> <span data-ttu-id="54a6b-107">Le type de `Any` peut représenter n’importe quel type de message Protobuf connu, tandis que le mot clé `oneof` vous permet de spécifier qu’une seule plage de champs peut être définie dans un message donné.</span><span class="sxs-lookup"><span data-stu-id="54a6b-107">The `Any` type can represent any known Protobuf message type, while the `oneof` keyword allows you to specify that only one of a range of fields can be set in any given message.</span></span>

## <a name="any"></a><span data-ttu-id="54a6b-108">Any</span><span class="sxs-lookup"><span data-stu-id="54a6b-108">Any</span></span>

<span data-ttu-id="54a6b-109">`Any` est l’un des « types connus » d’Protobuf : une collection de types de messages utiles et réutilisables avec des implémentations dans toutes les langues prises en charge.</span><span class="sxs-lookup"><span data-stu-id="54a6b-109">`Any` is one of Protobuf's "well-known types": a collection of useful, reusable message types with implementations in all supported languages.</span></span> <span data-ttu-id="54a6b-110">Pour utiliser le type de `Any`, vous devez importer la définition de la `google/protobuf/any.proto`.</span><span class="sxs-lookup"><span data-stu-id="54a6b-110">To use the `Any` type, you must import the `google/protobuf/any.proto` definition.</span></span>

```protobuf
syntax "proto3"

import "google/protobuf/any.proto"

message Stock {
    // Stock-specific data
}

message Currency {
    // Currency-specific data
}

message ChangeNotification {
    int32 id = 1;
    google.protobuf.Any instrument = 2;
}
```

<span data-ttu-id="54a6b-111">Dans le C# code, la classe`Any`fournit des méthodes pour définir le champ, extraire le message et vérifier le type.</span><span class="sxs-lookup"><span data-stu-id="54a6b-111">In the C# code, the `Any` class provides methods for setting the field, extracting the message, and checking the type.</span></span>

```csharp
public void FormatChangeNotification(ChangeNotification change)
{
    if (change.Instrument.Is(Stock.Descriptor))
    {
        FormatStock(change.Instrument.Unpack<Stock>());
    }
    else if (change.Instrument.Is(Currency.Descriptor))
    {
        FormatCurrency(change.Instrument.Unpack<Currency>());
    }
    else
    {
        throw new ArgumentException("Unknown instrument type");
    }
}
```

<span data-ttu-id="54a6b-112">Le `Descriptor` champ statique sur chaque type généré est utilisé par le code de réflexion interne de Protobuf pour résoudre `Any` types de champs.</span><span class="sxs-lookup"><span data-stu-id="54a6b-112">The `Descriptor` static field on each generated type is used by Protobuf's internal reflection code to resolve `Any` field types.</span></span> <span data-ttu-id="54a6b-113">Il existe également une méthode `TryUnpack<T>`, mais qui crée une instance non initialisée de `T` même en cas d’échec. il est donc préférable d’utiliser la méthode `Is` comme indiqué ci-dessus.</span><span class="sxs-lookup"><span data-stu-id="54a6b-113">There's also a `TryUnpack<T>` method, but that creates an uninitialized instance of `T` even when it fails, so it's better to use the `Is` method as shown above.</span></span>

## <a name="oneof"></a><span data-ttu-id="54a6b-114">Oneof</span><span class="sxs-lookup"><span data-stu-id="54a6b-114">Oneof</span></span>

<span data-ttu-id="54a6b-115">Les champs OneOf sont une fonctionnalité de langage : le mot clé `oneof` est géré par le compilateur lors de la génération de la classe de message.</span><span class="sxs-lookup"><span data-stu-id="54a6b-115">Oneof fields are a language feature: the `oneof` keyword is handled by the compiler when it generates the message class.</span></span> <span data-ttu-id="54a6b-116">L’utilisation de `oneof` pour spécifier le message `ChangeNotification` peut se présenter comme suit :</span><span class="sxs-lookup"><span data-stu-id="54a6b-116">Using `oneof` to specify the `ChangeNotification` message might look like this:</span></span>

```protobuf
message Stock {
    // Stock-specific data
}

message Currency {
    // Currency-specific data
}

message ChangeNotification {
  int32 id = 1;
  oneof instrument {
    Stock stock = 2;
    Currency currency = 3;
  }
}
```

<span data-ttu-id="54a6b-117">Les champs dans le jeu de `oneof` doivent avoir des numéros de champ uniques dans la déclaration globale du message.</span><span class="sxs-lookup"><span data-stu-id="54a6b-117">Fields within the `oneof` set must have unique field numbers within the overall message declaration.</span></span>

<span data-ttu-id="54a6b-118">Lorsque vous utilisez `oneof`, le code C# généré inclut une énumération qui spécifie les champs qui ont été définis.</span><span class="sxs-lookup"><span data-stu-id="54a6b-118">When you use `oneof`, the generated C# code includes an enum that specifies which of the fields has been set.</span></span> <span data-ttu-id="54a6b-119">Vous pouvez tester l’énumération pour rechercher le champ défini.</span><span class="sxs-lookup"><span data-stu-id="54a6b-119">You can test the enum to find which field is set.</span></span> <span data-ttu-id="54a6b-120">Les champs qui ne sont pas définis retournent `null` ou la valeur par défaut, au lieu de lever une exception.</span><span class="sxs-lookup"><span data-stu-id="54a6b-120">Fields that aren't set return `null` or the default value, rather than throwing an exception.</span></span>

```csharp
public void FormatChangeNotification(ChangeNotification change)
{
    switch (change.InstrumentCase)
    {
        case ChangeNotification.InstrumentOneofCase.None:
            return;
        case ChangeNotification.InstrumentOneofCase.Stock:
            FormatStock(change.Stock);
            break;
        case ChangeNotification.InstrumentOneofCase.Currency:
            FormatCurrency(change.Currency);
            break;
        default:
            throw new ArgumentException("Unknown instrument type");
    }
}
```

<span data-ttu-id="54a6b-121">La définition d’un champ qui fait partie d’un `oneof` jeu efface automatiquement tous les autres champs de l’ensemble.</span><span class="sxs-lookup"><span data-stu-id="54a6b-121">Setting any field that is part of a `oneof` set will automatically clear any other fields in the set.</span></span> <span data-ttu-id="54a6b-122">Vous ne pouvez pas utiliser `repeated` avec `oneof`.</span><span class="sxs-lookup"><span data-stu-id="54a6b-122">You can't use `repeated` with `oneof`.</span></span> <span data-ttu-id="54a6b-123">Au lieu de cela, vous pouvez créer un message imbriqué avec le champ répété ou le `oneof` défini pour contourner cette limitation.</span><span class="sxs-lookup"><span data-stu-id="54a6b-123">Instead, you can create a nested message with either the repeated field or the `oneof` set to work around this limitation.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="54a6b-124">[Précédent](protobuf-reserved.md)
>[Suivant](protobuf-enums.md)</span><span class="sxs-lookup"><span data-stu-id="54a6b-124">[Previous](protobuf-reserved.md)
[Next](protobuf-enums.md)</span></span>
