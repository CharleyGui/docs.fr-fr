---
ms.openlocfilehash: 43ebb37124b8efe077b9f81fe5351bd7db2c72f7
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87302706"
---
### <a name="vectort-always-throws-notsupportedexception-for-unsupported-types"></a>Vector \<T> lève toujours l’exception NotSupportedException pour les types non pris en charge

<xref:System.Numerics.Vector%601?displayProperty=nameWithType>lève à présent toujours un <xref:System.NotSupportedException> pour les paramètres de type non pris en charge.

#### <a name="change-description"></a>Description de la modification

Auparavant, les membres de <xref:System.Numerics.Vector%601> ne lèvent pas toujours une exception <xref:System.NotSupportedException> quand `T` était un [type non pris en charge](#unsupported-types). L’exception n’a pas toujours été levée en raison des chemins de code qui ont pris en charge l’accélération matérielle. Par exemple, `Vector<bool> + Vector<bool>` retourné `default` au lieu de lever une exception sur les plateformes qui n’ont pas d’accélération matérielle, telles que ARM32. Pour les types non pris en charge, <xref:System.Numerics.Vector%601> les membres présentent un comportement incohérent sur différentes plateformes et configurations matérielles.

À compter de .NET 5,0, <xref:System.Numerics.Vector%601> les membres lèvent toujours une <xref:System.NotSupportedException> sur toutes les configurations matérielles lorsque `T` n’est pas un type pris en charge.

##### <a name="unsupported-types"></a>Types non pris en charge

Les types pris en charge pour le paramètre de type de <xref:System.Numerics.Vector%601> sont :

- `byte`
- `sbyte`
- `short`
- `ushort`
- `int`
- `uint`
- `long`
- `ulong`
- `float`
- `double`

Les types pris en charge n’ont pas changé, toutefois, ils peuvent changer à l’avenir.

#### <a name="version-introduced"></a>Version introduite

5,0 Preview 8

#### <a name="recommended-action"></a>Action recommandée

N’utilisez pas un type non pris en charge pour le paramètre de type de <xref:System.Numerics.Vector%601> .

#### <a name="category"></a>Category

Bibliothèques .NET Core

#### <a name="affected-apis"></a>API affectées

- <xref:System.Numerics.Vector%601?displayProperty=fullName>et tous ses membres

<!--

#### Affected APIs

- ``T:System.Numerics.Vector`1``

-->
