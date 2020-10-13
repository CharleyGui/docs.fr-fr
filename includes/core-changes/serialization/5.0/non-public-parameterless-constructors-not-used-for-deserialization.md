---
ms.openlocfilehash: 572ebc47d26e30738fc4e5b8a8fab1f2643e3d83
ms.sourcegitcommit: e078b7540a8293ca1b604c9c0da1ff1506f0170b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/13/2020
ms.locfileid: "91997708"
---
### <a name="non-public-parameterless-constructors-not-used-for-deserialization"></a>Constructeurs non publics, sans paramètre, non utilisés pour la désérialisation

Pour garantir la cohérence entre tous les monikers du Framework cible (TFM) pris en charge, les constructeurs non publics et sans paramètre ne sont plus utilisés pour la désérialisation avec <xref:System.Text.Json.JsonSerializer> , par défaut.

#### <a name="change-description"></a>Description de la modification

Sur .NET Core 3,0 et 3,1, les constructeurs internes et privés peuvent être utilisés pour la désérialisation. Sur .NET Standard 2,0 et 2,1, les constructeurs internes et privés ne sont pas autorisés, et une <xref:System.MissingMethodException> exception est levée si aucun constructeur sans paramètre public n’est défini.

À compter de .NET 5,0, les constructeurs non publics, y compris les constructeurs sans paramètre, sont ignorés par défaut par le sérialiseur. Le sérialiseur utilise l’un des constructeurs suivants pour la désérialisation :

- Constructeur public annoté avec <xref:System.Text.Json.Serialization.JsonConstructorAttribute> .
- Constructeur sans paramètre public.
- Constructeur public paramétré (s’il s’agit du seul constructeur public présent).

Si aucun de ces constructeurs n’est disponible, une <xref:System.NotSupportedException> exception est levée si vous tentez de désérialiser le type.

#### <a name="version-introduced"></a>Version introduite

5.0

#### <a name="reason-for-change"></a>Motif de modification

- Pour appliquer un comportement cohérent entre tous les monikers du Framework cible (TFM) <xref:System.Text.Json?displayProperty=fullName> générés par (.net Core 3,0 et versions ultérieures, ainsi que les .NET Standard 2,0 et 2,1)
- Étant donné que <xref:System.Text.Json.JsonSerializer> ne doit pas appeler la surface d’exposition non publique d’un type, qu’il s’agisse d’un constructeur, d’une propriété ou d’un champ.

#### <a name="recommended-action"></a>Action recommandée

- Si vous êtes propriétaire du type et que cela est faisable, rendez le constructeur sans paramètre public.
- Sinon, implémentez un `JsonConverter<T>` pour le type et contrôlez le comportement de désérialisation.

#### <a name="category"></a>Category

Sérialisation

#### <a name="affected-apis"></a>API affectées

- <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=fullName>
- <xref:System.Text.Json.JsonSerializer.DeserializeAsync%2A?displayProperty=fullName>

<!--

#### Affected APIs

- `Overload:System.Text.Json.JsonSerializer.Deserialize`
- `Overload:System.Text.Json.JsonSerializer.DeserializeAsync`

-->
