---
title: 'Modification avec rupture : constructeurs non publics et sans paramètre non utilisés pour la désérialisation'
description: Découvrez la modification avec rupture dans .NET 5,0 où les constructeurs non publics et sans paramètre ne sont plus utilisés pour la désérialisation avec JsonSerializer.
ms.date: 10/18/2020
ms.openlocfilehash: a2ea54b6a76692dae7d6e01b06b11218d66b1cd7
ms.sourcegitcommit: 4d5e25a46aa7cd0d29b4b9227b92987354d444c4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/26/2021
ms.locfileid: "98794707"
---
# <a name="non-public-parameterless-constructors-not-used-for-deserialization"></a>Les constructeurs sans paramètre et non publics ne sont pas utilisés pour la désérialisation

Pour garantir la cohérence entre tous les monikers du Framework cible (TFM) pris en charge, les constructeurs non publics et sans paramètre ne sont plus utilisés pour la désérialisation avec <xref:System.Text.Json.JsonSerializer> , par défaut.

## <a name="change-description"></a>Description de la modification

LesSystem.Text.Jsautonomes [ sur les packages NuGet](https://www.nuget.org/packages/System.Text.Json/) qui prennent en charge .NET standard 2,0 et versions ultérieures, autrement dit, les versions 4.6.0-4.7.2, se comportent de façon incohérente avec le comportement intégré sur .net Core 3,0 et 3,1. Sur .NET Core 3. x, les constructeurs internes et privés peuvent être utilisés pour la désérialisation. Dans les packages autonomes, les constructeurs non publics ne sont pas autorisés, et une <xref:System.MissingMethodException> exception est levée si aucun constructeur sans paramètre public n’est défini.

À compter de .NET 5,0 et System.Text.Jssur le package NuGet 5.0.0, le comportement est cohérent entre le package NuGet et les API intégrées. Les constructeurs non publics, y compris les constructeurs sans paramètre, sont ignorés par défaut par le sérialiseur. Le sérialiseur utilise l’un des constructeurs suivants pour la désérialisation :

- Constructeur public annoté avec <xref:System.Text.Json.Serialization.JsonConstructorAttribute> .
- Constructeur sans paramètre public.
- Constructeur public paramétré (s’il s’agit du seul constructeur public présent).

Si aucun de ces constructeurs n’est disponible, une <xref:System.NotSupportedException> exception est levée si vous tentez de désérialiser le type.

## <a name="version-introduced"></a>Version introduite

5.0

## <a name="reason-for-change"></a>Motif de modification

- Pour appliquer un comportement cohérent entre tous les monikers du Framework cible (TFM) <xref:System.Text.Json?displayProperty=fullName> générés par (.net Core 3,0 et versions ultérieures et .NET Standard 2,0)
- Étant donné que <xref:System.Text.Json.JsonSerializer> ne doit pas appeler la surface d’exposition non publique d’un type, qu’il s’agisse d’un constructeur, d’une propriété ou d’un champ.

## <a name="recommended-action"></a>Action recommandée

- Si vous êtes propriétaire du type et que cela est faisable, rendez le constructeur sans paramètre public.
- Sinon, implémentez un <xref:System.Text.Json.Serialization.JsonConverter%601> pour le type et contrôlez le comportement de désérialisation. Vous pouvez appeler un constructeur non public à partir d’une <xref:System.Text.Json.Serialization.JsonConverter%601> implémentation si les règles d’accessibilité C# pour ce scénario l’autorisent.

## <a name="affected-apis"></a>API affectées

- <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=fullName>
- <xref:System.Text.Json.JsonSerializer.DeserializeAsync%2A?displayProperty=fullName>

<!--

### Affected APIs

- `Overload:System.Text.Json.JsonSerializer.Deserialize`
- `Overload:System.Text.Json.JsonSerializer.DeserializeAsync`

### Category

Serialization

-->
