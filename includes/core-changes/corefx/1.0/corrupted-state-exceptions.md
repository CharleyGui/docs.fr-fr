---
ms.openlocfilehash: 394f2daebad7b6af94bee4d7876796e87fe8ab19
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/25/2020
ms.locfileid: "96031994"
---
### <a name="handling-corrupted-state-exceptions-is-not-supported"></a>La gestion des exceptions d’état endommagé n’est pas prise en charge

La gestion des exceptions d’état de processus endommagées dans .NET Core n’est pas prise en charge.

#### <a name="change-description"></a>Description de la modification

Auparavant, les exceptions d’état de processus endommagé pouvaient être interceptées et gérées par les gestionnaires d’exceptions de code managé, par exemple, à l’aide d’une instruction [try-catch](../../../../docs/csharp/language-reference/keywords/try-catch.md) en C#.

À compter de .NET Core 1,0, les exceptions d’état de processus endommagées ne peuvent pas être gérées par le code managé. La common language runtime ne remet pas d’exceptions d’état de processus endommagées au code managé.

#### <a name="version-introduced"></a>Version introduite

1.0

#### <a name="recommended-action"></a>Action recommandée

Évitez la nécessité de gérer les exceptions d’état de processus endommagées en résolvant les situations qui les mènent à la place. S’il est absolument nécessaire de gérer les exceptions d’état de processus endommagées, écrivez le gestionnaire d’exceptions en code C ou C++.

#### <a name="category"></a>Category

Bibliothèques .NET Core

#### <a name="affected-apis"></a>API affectées

- <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute?displayProperty=fullName>
- [legacyCorruptedStateExceptionsPolicy (élément)](~/docs/framework/configure-apps/file-schema/runtime/legacycorruptedstateexceptionspolicy-element.md)

<!--

#### Affected APIs

- `T:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute`

-->
