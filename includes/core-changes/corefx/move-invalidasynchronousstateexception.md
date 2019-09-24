---
ms.openlocfilehash: 82835915efa0e113e81bb09bd5062ee3252f2a64
ms.sourcegitcommit: 56f1d1203d0075a461a10a301459d3aa452f4f47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71217100"
---
### <a name="invalidasynchronousstateexception-moved-to-another-assembly"></a>InvalidAsynchronousStateException déplacé vers un autre assembly

La <xref:System.ComponentModel.InvalidAsynchronousStateException> classe a été déplacée.

#### <a name="change-description"></a>Modifier la description

Dans .net Core 2,2 et les versions antérieures, <xref:System.ComponentModel.InvalidAsynchronousStateException> la classe se trouve dans l’assembly *System. ComponentModel. TypeConverter* .

À compter de .NET Core 3,0, il se trouve dans l’assembly *System. ComponentModel. Primitives* .

#### <a name="version-introduced"></a>Version introduite

3.0

#### <a name="recommended-action"></a>Action recommandée

Cette modification affecte uniquement les applications qui utilisent la réflexion pour <xref:System.ComponentModel.InvalidAsynchronousStateException> charger le en appelant une méthode <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType> telle que ou une <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType> surcharge de qui suppose que le type se trouve dans un assembly particulier. Si tel est le cas, l’assembly référencé dans l’appel de méthode doit être mis à jour pour refléter le nouvel emplacement de l’assembly du type.

#### <a name="category"></a>Category

CoreFx

#### <a name="affected-apis"></a>API affectées

- Aucun.

<!--

### Affected APIs

- Not detectable via API analysis

-->
