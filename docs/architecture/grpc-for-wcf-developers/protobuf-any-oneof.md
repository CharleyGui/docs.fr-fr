---
title: Protobuf tous les champs et OneOf pour les types variant-gRPC pour les développeurs WCF
description: Découvrez comment utiliser le type any et le mot clé OneOf pour représenter des types d’objets variants dans des messages.
ms.date: 09/09/2019
ms.openlocfilehash: 6fe7acbd1ec35289f7ad6f3acee8509ab934619d
ms.sourcegitcommit: 771c554c84ba38cbd4ac0578324ec4cfc979cf2e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/21/2020
ms.locfileid: "77543194"
---
# <a name="protobuf-any-and-oneof-fields-for-variant-types"></a><span data-ttu-id="1a3f3-103">Protobuf tous les champs et OneOf pour les types variant</span><span class="sxs-lookup"><span data-stu-id="1a3f3-103">Protobuf Any and Oneof fields for variant types</span></span>

<span data-ttu-id="1a3f3-104">La gestion des types de propriétés dynamiques (autrement dit, les propriétés de type `object`) dans Windows Communication Foundation (WCF) est complexe.</span><span class="sxs-lookup"><span data-stu-id="1a3f3-104">Handling dynamic property types (that is, properties of type `object`) in Windows Communication Foundation (WCF) is complicated.</span></span> <span data-ttu-id="1a3f3-105">Par exemple, vous devez spécifier des sérialiseurs et fournir des attributs [KnownType](xref:System.Runtime.Serialization.KnownTypeAttribute) .</span><span class="sxs-lookup"><span data-stu-id="1a3f3-105">For example, you must specify serializers and provide [KnownType](xref:System.Runtime.Serialization.KnownTypeAttribute) attributes.</span></span>

<span data-ttu-id="1a3f3-106">La mémoire tampon de protocole (Protobuf) fournit deux options plus simples pour traiter les valeurs qui peuvent être de plusieurs types.</span><span class="sxs-lookup"><span data-stu-id="1a3f3-106">Protocol Buffer (Protobuf) provides two simpler options for dealing with values that might be of more than one type.</span></span> <span data-ttu-id="1a3f3-107">Le type de `Any` peut représenter n’importe quel type de message Protobuf connu.</span><span class="sxs-lookup"><span data-stu-id="1a3f3-107">The `Any` type can represent any known Protobuf message type.</span></span> <span data-ttu-id="1a3f3-108">Vous pouvez utiliser le mot clé `oneof` pour spécifier qu’une seule plage de champs peut être définie dans un message.</span><span class="sxs-lookup"><span data-stu-id="1a3f3-108">And you can use the `oneof` keyword to specify that only one of a range of fields can be set in any message.</span></span>

## <a name="any"></a><span data-ttu-id="1a3f3-109">Quelconque</span><span class="sxs-lookup"><span data-stu-id="1a3f3-109">Any</span></span>

<span data-ttu-id="1a3f3-110">`Any` est l’un des « types connus » d’Protobuf : une collection de types de messages utiles et réutilisables avec des implémentations dans toutes les langues prises en charge.</span><span class="sxs-lookup"><span data-stu-id="1a3f3-110">`Any` is one of Protobuf's "well-known types": a collection of useful, reusable message types with implementations in all supported languages.</span></span> <span data-ttu-id="1a3f3-111">Pour utiliser le type de `Any`, vous devez importer la définition de la `google/protobuf/any.proto`.</span><span class="sxs-lookup"><span data-stu-id="1a3f3-111">To use the `Any` type, you must import the `google/protobuf/any.proto` definition.</span></span>

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

<span data-ttu-id="1a3f3-112">Dans le C# code, la classe `Any` fournit des méthodes pour définir le champ, extraire le message et vérifier le type.</span><span class="sxs-lookup"><span data-stu-id="1a3f3-112">In the C# code, the `Any` class provides methods for setting the field, extracting the message, and checking the type.</span></span>

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

<span data-ttu-id="1a3f3-113">Le code de réflexion interne de Protobuf utilise le champ statique `Descriptor` sur chaque type généré pour résoudre `Any` types de champs.</span><span class="sxs-lookup"><span data-stu-id="1a3f3-113">Protobuf's internal reflection code uses the `Descriptor` static field on each generated type to resolve `Any` field types.</span></span> <span data-ttu-id="1a3f3-114">Il y a également une méthode `TryUnpack<T>`, mais cela crée une instance non initialisée de `T` même en cas d’échec.</span><span class="sxs-lookup"><span data-stu-id="1a3f3-114">There's also a `TryUnpack<T>` method, but that creates an uninitialized instance of `T` even when it fails.</span></span> <span data-ttu-id="1a3f3-115">Il est préférable d’utiliser la méthode `Is` comme indiqué plus haut.</span><span class="sxs-lookup"><span data-stu-id="1a3f3-115">It's better to use the `Is` method as shown earlier.</span></span>

## <a name="oneof"></a><span data-ttu-id="1a3f3-116">Oneof</span><span class="sxs-lookup"><span data-stu-id="1a3f3-116">Oneof</span></span>

<span data-ttu-id="1a3f3-117">Les champs OneOf sont une fonctionnalité de langage : le compilateur gère le mot clé `oneof` lors de la génération de la classe message.</span><span class="sxs-lookup"><span data-stu-id="1a3f3-117">Oneof fields are a language feature: the compiler handles the `oneof` keyword when it generates the message class.</span></span> <span data-ttu-id="1a3f3-118">L’utilisation de `oneof` pour spécifier le message `ChangeNotification` peut se présenter comme suit :</span><span class="sxs-lookup"><span data-stu-id="1a3f3-118">Using `oneof` to specify the `ChangeNotification` message might look like this:</span></span>

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

<span data-ttu-id="1a3f3-119">Les champs dans le jeu de `oneof` doivent avoir des numéros de champ uniques dans la déclaration globale du message.</span><span class="sxs-lookup"><span data-stu-id="1a3f3-119">Fields within the `oneof` set must have unique field numbers in the overall message declaration.</span></span>

<span data-ttu-id="1a3f3-120">Lorsque vous utilisez `oneof`, le code C# généré inclut une énumération qui spécifie les champs qui ont été définis.</span><span class="sxs-lookup"><span data-stu-id="1a3f3-120">When you use `oneof`, the generated C# code includes an enum that specifies which of the fields has been set.</span></span> <span data-ttu-id="1a3f3-121">Vous pouvez tester l’énumération pour rechercher le champ défini.</span><span class="sxs-lookup"><span data-stu-id="1a3f3-121">You can test the enum to find which field is set.</span></span> <span data-ttu-id="1a3f3-122">Les champs qui ne sont pas définis retournent `null` ou la valeur par défaut, au lieu de lever une exception.</span><span class="sxs-lookup"><span data-stu-id="1a3f3-122">Fields that aren't set return `null` or the default value, rather than throwing an exception.</span></span>

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

<span data-ttu-id="1a3f3-123">La définition de n’importe quel champ qui fait partie d’un `oneof` jeu efface automatiquement tous les autres champs de l’ensemble.</span><span class="sxs-lookup"><span data-stu-id="1a3f3-123">Setting any field that's part of a `oneof` set will automatically clear any other fields in the set.</span></span> <span data-ttu-id="1a3f3-124">Vous ne pouvez pas utiliser `repeated` avec `oneof`.</span><span class="sxs-lookup"><span data-stu-id="1a3f3-124">You can't use `repeated` with `oneof`.</span></span> <span data-ttu-id="1a3f3-125">Au lieu de cela, vous pouvez créer un message imbriqué avec le champ répété ou le `oneof` défini pour contourner cette limitation.</span><span class="sxs-lookup"><span data-stu-id="1a3f3-125">Instead, you can create a nested message with either the repeated field or the `oneof` set to work around this limitation.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="1a3f3-126">[Précédent](protobuf-reserved.md)
>[Suivant](protobuf-enums.md)</span><span class="sxs-lookup"><span data-stu-id="1a3f3-126">[Previous](protobuf-reserved.md)
[Next](protobuf-enums.md)</span></span>
