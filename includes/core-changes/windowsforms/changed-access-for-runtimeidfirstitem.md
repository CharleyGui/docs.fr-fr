---
ms.openlocfilehash: 5bbbf9075683b0f124e126b661b4ab85011e6c2e
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72003027"
---
### <a name="change-of-access-for-accessibleobjectruntimeidfirstitem"></a>Changement d’accès pour AccessibleObject. RuntimeIDFirstItem

À compter de .NET Core 3,0 RC1, l’accessibilité de `AccessibleObject.RuntimeIDFirstItem` est passée de `protected` à `internal`.

#### <a name="change-description"></a>Modifier la description

À compter de .NET Core 3,0 Preview 4, le champ `AccessibleObject.RuntimeIDFirstItem` était `protected`. À compter de .NET Core 3,0 RC1, il est passé de `protected` à `internal` pour s’aligner avec l’accessibilité du champ dans le .NET Framework.

#### <a name="version-introduced"></a>Version introduite

3,0 RC1

#### <a name="recommended-action"></a>Action recommandée

La modification peut vous affecter si vous avez développé une application .NET Core avec un type dérivant de <xref:System.Windows.Forms.AccessibleObject> et que vous accédez au champ `RuntimeIDFirstItem`. Si c’est le cas, vous pouvez définir une constante locale comme suit :

```csharp
const int RuntimeIDFirstItem = 0x2a;
```

#### <a name="category"></a>Catégorie

Windows Forms

#### <a name="affected-apis"></a>API affectées

- Non détectable via l’analyse des API.

<!-- 

### Affected APIs

- Not detectable via API analysis.

-->
