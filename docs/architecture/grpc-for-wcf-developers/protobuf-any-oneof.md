---
title: Protobuf tous les champs et OneOf pour les types variant-gRPC pour les développeurs WCF
description: Découvrez comment utiliser le type any et le mot clé OneOf pour représenter des types d’objets variants dans des messages.
author: markrendle
ms.date: 09/09/2019
ms.openlocfilehash: 9e730e96bfdb25ef6e07ee10967921408c6f2e84
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2019
ms.locfileid: "71184280"
---
# <a name="protobuf-any-and-oneof-fields-for-variant-types"></a><span data-ttu-id="82ffd-103">Protobuf tous les champs et OneOf pour les types variant</span><span class="sxs-lookup"><span data-stu-id="82ffd-103">Protobuf Any and Oneof fields for variant types</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="82ffd-104">La gestion des types de propriétés dynamiques (autrement dit, `object`des propriétés de type) dans WCF est compliquée.</span><span class="sxs-lookup"><span data-stu-id="82ffd-104">Handling dynamic property types (that is, properties of type `object`) in WCF is complicated.</span></span> <span data-ttu-id="82ffd-105">Les sérialiseurs doivent être spécifiés, les attributs [KnownType](xref:System.Runtime.Serialization.KnownTypeAttribute) doivent être fournis, et ainsi de suite.</span><span class="sxs-lookup"><span data-stu-id="82ffd-105">Serializers must be specified, [KnownType](xref:System.Runtime.Serialization.KnownTypeAttribute) attributes must be provided, and so on.</span></span>

<span data-ttu-id="82ffd-106">Protobuf fournit deux options plus simples pour traiter les valeurs qui peuvent être de plus d’un type.</span><span class="sxs-lookup"><span data-stu-id="82ffd-106">Protobuf provides two simpler options for dealing with values that may be of more than one type.</span></span> <span data-ttu-id="82ffd-107">Le `Any` type peut représenter n’importe quel type de message Protobuf connu `oneof` , tandis que le mot clé vous permet de spécifier qu’une seule plage de champs peut être définie dans un message donné.</span><span class="sxs-lookup"><span data-stu-id="82ffd-107">The `Any` type can represent any known Protobuf message type, while the `oneof` keyword allows you to specify that only one of a range of fields can be set in any given message.</span></span>

## <a name="any"></a><span data-ttu-id="82ffd-108">Any</span><span class="sxs-lookup"><span data-stu-id="82ffd-108">Any</span></span>

<span data-ttu-id="82ffd-109">`Any`est l’un des « types connus » d’Protobuf : une collection de types de messages utiles et réutilisables avec des implémentations dans toutes les langues prises en charge.</span><span class="sxs-lookup"><span data-stu-id="82ffd-109">`Any` is one of Protobuf's "well-known types": a collection of useful, reusable message types with implementations in all supported languages.</span></span> <span data-ttu-id="82ffd-110">Pour utiliser le `Any` type, vous devez importer la `google/protobuf/any.proto` définition.</span><span class="sxs-lookup"><span data-stu-id="82ffd-110">To use the `Any` type, you must import the `google/protobuf/any.proto` definition.</span></span>

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

<span data-ttu-id="82ffd-111">Dans le C# code, la `Any` classe fournit des méthodes pour définir le champ, extraire le message et vérifier le type.</span><span class="sxs-lookup"><span data-stu-id="82ffd-111">In the C# code, the `Any` class provides methods for setting the field, extracting the message, and checking the type.</span></span>

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

<span data-ttu-id="82ffd-112">Le `Descriptor` champ statique sur chaque type généré est utilisé par le code de réflexion interne de Protobuf `Any` pour résoudre les types de champs.</span><span class="sxs-lookup"><span data-stu-id="82ffd-112">The `Descriptor` static field on each generated type is used by Protobuf's internal reflection code to resolve `Any` field types.</span></span> <span data-ttu-id="82ffd-113">Il y a également `TryUnpack<T>` une méthode, mais cela crée une instance non initialisée `T` de même en cas d’échec. il est donc préférable d' `Is` utiliser la méthode comme indiqué ci-dessus.</span><span class="sxs-lookup"><span data-stu-id="82ffd-113">There's also a `TryUnpack<T>` method, but that creates an uninitialized instance of `T` even when it fails, so it's better to use the `Is` method as shown above.</span></span>

## <a name="oneof"></a><span data-ttu-id="82ffd-114">Oneof</span><span class="sxs-lookup"><span data-stu-id="82ffd-114">Oneof</span></span>

<span data-ttu-id="82ffd-115">Les champs OneOf sont une fonctionnalité de langage `oneof` : le mot clé est géré par le compilateur lors de la génération de la classe de message.</span><span class="sxs-lookup"><span data-stu-id="82ffd-115">Oneof fields are a language feature: the `oneof` keyword is handled by the compiler when it generates the message class.</span></span> <span data-ttu-id="82ffd-116">L' `oneof` utilisation de pour `ChangeNotification` spécifier le message peut se présenter comme suit :</span><span class="sxs-lookup"><span data-stu-id="82ffd-116">Using `oneof` to specify the `ChangeNotification` message might look like this:</span></span>

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

<span data-ttu-id="82ffd-117">Les champs de `oneof` l’ensemble doivent avoir des numéros de champ uniques dans la déclaration globale du message.</span><span class="sxs-lookup"><span data-stu-id="82ffd-117">Fields within the `oneof` set must have unique field numbers within the overall message declaration.</span></span>

<span data-ttu-id="82ffd-118">Lorsque vous utilisez `oneof`, le code C# généré inclut une énumération qui spécifie les champs qui ont été définis.</span><span class="sxs-lookup"><span data-stu-id="82ffd-118">When you use `oneof`, the generated C# code includes an enum that specifies which of the fields has been set.</span></span> <span data-ttu-id="82ffd-119">Vous pouvez tester l’énumération pour rechercher le champ défini.</span><span class="sxs-lookup"><span data-stu-id="82ffd-119">You can test the enum to find which field is set.</span></span> <span data-ttu-id="82ffd-120">Les champs qui ne sont `null` pas définis retournent ou la valeur par défaut, plutôt que de lever une exception.</span><span class="sxs-lookup"><span data-stu-id="82ffd-120">Fields that aren't set return `null` or the default value, rather than throwing an exception.</span></span>

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

<span data-ttu-id="82ffd-121">La définition d’un champ qui fait partie `oneof` d’un jeu efface automatiquement tous les autres champs de l’ensemble.</span><span class="sxs-lookup"><span data-stu-id="82ffd-121">Setting any field that is part of a `oneof` set will automatically clear any other fields in the set.</span></span> <span data-ttu-id="82ffd-122">Vous ne pouvez `repeated` pas `oneof`utiliser avec.</span><span class="sxs-lookup"><span data-stu-id="82ffd-122">You can't use `repeated` with `oneof`.</span></span> <span data-ttu-id="82ffd-123">Au lieu de cela, vous pouvez créer un message imbriqué avec le champ répété ou `oneof` le jeu pour contourner cette limitation.</span><span class="sxs-lookup"><span data-stu-id="82ffd-123">Instead, you can create a nested message with either the repeated field or the `oneof` set to work around this limitation.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="82ffd-124">[Précédent](protobuf-reserved.md)
>[Suivant](protobuf-enums.md)</span><span class="sxs-lookup"><span data-stu-id="82ffd-124">[Previous](protobuf-reserved.md)
[Next](protobuf-enums.md)</span></span>
