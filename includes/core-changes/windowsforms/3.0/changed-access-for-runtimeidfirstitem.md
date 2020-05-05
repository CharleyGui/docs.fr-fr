---
ms.openlocfilehash: 5bbbf9075683b0f124e126b661b4ab85011e6c2e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "74644046"
---
### <a name="change-of-access-for-accessibleobjectruntimeidfirstitem"></a>Changement d’accès pour AccessibleObject. RuntimeIDFirstItem

À compter de .NET Core 3,0 RC1, l’accessibilité `AccessibleObject.RuntimeIDFirstItem` de est passée `protected` de `internal`à.

#### <a name="change-description"></a>Description de la modification

À compter de .NET Core 3,0 Preview 4, `AccessibleObject.RuntimeIDFirstItem` le champ `protected`était. À compter de .NET Core 3,0 RC1, il est passé `protected` de `internal` à pour s’aligner sur l’accessibilité du champ dans la .NET Framework.

#### <a name="version-introduced"></a>Version introduite

3,0 RC1

#### <a name="recommended-action"></a>Action recommandée

La modification peut vous affecter si vous avez développé une application .NET Core avec un type qui dérive de <xref:System.Windows.Forms.AccessibleObject> et accède au `RuntimeIDFirstItem` champ. Si c’est le cas, vous pouvez définir une constante locale comme suit :

```csharp
const int RuntimeIDFirstItem = 0x2a;
```

#### <a name="category"></a>Category

Windows Forms

#### <a name="affected-apis"></a>API affectées

- Non détectable via l’analyse des API.

<!-- 

### Affected APIs

- Not detectable via API analysis.

-->
