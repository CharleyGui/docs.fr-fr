---
ms.openlocfilehash: d1562cb76f37b6cc2aeb6fe2f7c17c393e169e84
ms.sourcegitcommit: c2c1269a81ffdcfc8675bcd9a8505b1a11ffb271
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/25/2020
ms.locfileid: "82158470"
---
### <a name="invalidasynchronousstateexception-moved-to-another-assembly"></a>InvalidAsynchronousStateException déplacé vers un autre assembly

La <xref:System.ComponentModel.InvalidAsynchronousStateException> classe a été déplacée.

#### <a name="change-description"></a>Description de la modification

Dans .NET Core 2,2 et les versions antérieures, <xref:System.ComponentModel.InvalidAsynchronousStateException> la classe se trouve dans l’assembly *System. ComponentModel. TypeConverter* .

À compter de .NET Core 3,0, il se trouve dans l’assembly *System. ComponentModel. Primitives* .

#### <a name="version-introduced"></a>Version introduite

3.0

#### <a name="recommended-action"></a>Action recommandée

Cette modification affecte uniquement les applications qui utilisent la réflexion pour <xref:System.ComponentModel.InvalidAsynchronousStateException> charger le en appelant une méthode <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType> telle que ou une <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType> surcharge de qui suppose que le type se trouve dans un assembly particulier. Si tel est le cas, mettez à jour l’assembly référencé dans l’appel de la méthode pour refléter le nouvel emplacement de l’assembly du type.

#### <a name="category"></a>Category

Bibliothèques .NET Core

#### <a name="affected-apis"></a>API affectées

Aucune.

<!--

### Affected APIs

- Not detectable via API analysis

-->
