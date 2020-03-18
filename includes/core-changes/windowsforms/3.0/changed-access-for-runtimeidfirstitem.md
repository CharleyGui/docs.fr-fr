---
ms.openlocfilehash: 5bbbf9075683b0f124e126b661b4ab85011e6c2e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "74644046"
---
### <a name="change-of-access-for-accessibleobjectruntimeidfirstitem"></a>Changement d’accès pour AccessibleObject.RuntimeIDFirstItem

À partir de .NET Core 3.0 `AccessibleObject.RuntimeIDFirstItem` RC1, l’accessibilité de a changé de `protected` . `internal`

#### <a name="change-description"></a>Description de la modification

En commençant par .NET Core 3.0 Aperçu 4, le `AccessibleObject.RuntimeIDFirstItem` champ a été `protected`. À partir de .NET Core 3.0 `protected` RC1, il est passé de l’autre `internal` pour s’aligner sur l’accessibilité du champ dans le cadre .NET.

#### <a name="version-introduced"></a>Version introduite

3.0 RC1

#### <a name="recommended-action"></a>Action recommandée

La modification peut vous affecter si vous avez développé une application <xref:System.Windows.Forms.AccessibleObject> .NET Core `RuntimeIDFirstItem` avec un type qui dérive et accède au champ. Si c’est le cas, vous pouvez définir une constante locale comme suit :

```csharp
const int RuntimeIDFirstItem = 0x2a;
```

#### <a name="category"></a>Category

Windows Forms

#### <a name="affected-apis"></a>API affectées

- Non détectable par l’analyse de l’API.

<!-- 

### Affected APIs

- Not detectable via API analysis.

-->
