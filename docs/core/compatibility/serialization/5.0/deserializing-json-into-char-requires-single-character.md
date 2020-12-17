---
title: 'Modification avec rupture : la désérialisation de char requiert une chaîne à un seul caractère'
description: Découvrez la modification avec rupture dans .NET 5,0 où System.Text.Jssur requiert une chaîne à un seul caractère dans le JSON lors de la désérialisation vers une cible char.
ms.date: 12/15/2020
ms.openlocfilehash: 39a2d25b00bf8855cfbf46a4d78b8545052703e5
ms.sourcegitcommit: 635a0ff775d2447a81ef7233a599b8f88b162e5d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/17/2020
ms.locfileid: "97633869"
---
# <a name="systemtextjson-requires-single-char-string-to-deserialize-a-char"></a>System.Text.Jssur requiert une chaîne à un seul caractère pour désérialiser un caractère

Pour désérialiser avec succès un <xref:System.Char> à l’aide de <xref:System.Text.Json> , la chaîne JSON doit contenir un seul caractère.

## <a name="change-description"></a>Description de la modification

Dans les versions précédentes de .NET, une `char` chaîne multiple dans le JSON est correctement désérialisée en une `char` propriété ou un champ. Seul le premier `char` de la chaîne est utilisé, comme dans l’exemple suivant :

```csharp
// .NET Core 3.0 and 3.1: Returns the first char 'a'.
// .NET 5.0 and later: Throws JsonException because payload has more than one char.
char deserializedChar = JsonSerializer.Deserialize<char>("\"abc\"");
```

Dans .NET 5,0 et versions ultérieures, toute autre chose qu’une `char` chaîne unique entraîne <xref:System.Text.Json.JsonException> la levée d’une exception lorsque la cible de désérialisation est un `char` . L’exemple de chaîne suivant est correctement désérialisé dans toutes les versions de .NET :

```csharp
// Correct usage.
char deserializedChar = JsonSerializer.Deserialize<char>("\"a\"");
```

## <a name="version-introduced"></a>Version introduite

5.0

## <a name="reason-for-change"></a>Motif de modification

L’analyse de la désérialisation doit être effectuée uniquement lorsque la charge utile fournie est valide pour le type cible. Pour un `char` type, la seule charge utile valide est une `char` chaîne unique.

## <a name="recommended-action"></a>Action recommandée

Lorsque vous désérialisez JSON dans une cible, assurez-vous `char` que la chaîne est constituée d’un seul `char` .

## <a name="affected-apis"></a>API affectées

- <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=fullName>

<!--

### Affected APIs

- `Overload:System.Text.Json.JsonSerializer.Deserialize`

### Category

Serialization

-->
