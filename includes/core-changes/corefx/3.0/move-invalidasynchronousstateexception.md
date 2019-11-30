---
ms.openlocfilehash: 82835915efa0e113e81bb09bd5062ee3252f2a64
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2019
ms.locfileid: "74568232"
---
### <a name="invalidasynchronousstateexception-moved-to-another-assembly"></a>InvalidAsynchronousStateException déplacé vers un autre assembly

La classe <xref:System.ComponentModel.InvalidAsynchronousStateException> a été déplacée.

#### <a name="change-description"></a>Modifier la description

Dans .NET Core 2,2 et les versions antérieures, la classe <xref:System.ComponentModel.InvalidAsynchronousStateException> se trouve dans l’assembly *System. ComponentModel. TypeConverter* .

À compter de .NET Core 3,0, il se trouve dans l’assembly *System. ComponentModel. Primitives* .

#### <a name="version-introduced"></a>Version introduite

3.0

#### <a name="recommended-action"></a>Action recommandée

Cette modification affecte uniquement les applications qui utilisent la réflexion pour charger le <xref:System.ComponentModel.InvalidAsynchronousStateException> en appelant une méthode telle que <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType> ou une surcharge de <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType> qui suppose que le type se trouve dans un assembly particulier. Si tel est le cas, l’assembly référencé dans l’appel de méthode doit être mis à jour pour refléter le nouvel emplacement de l’assembly du type.

#### <a name="category"></a>Category

CoreFx

#### <a name="affected-apis"></a>API affectées

- Aucun

<!--

### Affected APIs

- Not detectable via API analysis

-->
