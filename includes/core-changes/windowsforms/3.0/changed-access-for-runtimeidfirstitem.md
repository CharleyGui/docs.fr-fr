---
ms.openlocfilehash: 1ea2d70a7cfe04cc4c4b9b58ea6bb6fa0226b245
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83720951"
---
### <a name="change-of-access-for-accessibleobjectruntimeidfirstitem"></a>Changement d’accès pour AccessibleObject. RuntimeIDFirstItem

À compter de .NET Core 3,0 RC1, l’accessibilité de `AccessibleObject.RuntimeIDFirstItem` est passée de `protected` à `internal` .

#### <a name="change-description"></a>Description de la modification

À compter de .NET Core 3,0 Preview 4, le `AccessibleObject.RuntimeIDFirstItem` champ était `protected` . À compter de .NET Core 3,0 RC1, il est passé de `protected` à `internal` pour s’aligner sur l’accessibilité du champ dans la .NET Framework.

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

#### Affected APIs

- Not detectable via API analysis.

-->
