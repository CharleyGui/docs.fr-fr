---
ms.openlocfilehash: 19359422f79f8240676b0057c7391f6b06f961ee
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79147547"
---
### <a name="invalidasynchronousstateexception-moved-to-another-assembly"></a>InvalidAsynchroneStateException a déménagé à une autre assemblée

La <xref:System.ComponentModel.InvalidAsynchronousStateException> classe a été déplacée.

#### <a name="change-description"></a>Description de la modification

Dans .NET Core 2.2 et <xref:System.ComponentModel.InvalidAsynchronousStateException> les versions antérieures, la classe se trouve dans *l’assemblage System.ComponentModel.TypeConverter.*

En commençant par .NET Core 3.0, il se trouve dans *l’assemblage System.ComponentModel.Primitives.*

#### <a name="version-introduced"></a>Version introduite

3.0

#### <a name="recommended-action"></a>Action recommandée

Ce changement n’affecte que les <xref:System.ComponentModel.InvalidAsynchronousStateException> applications qui utilisent <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType> la réflexion <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType> pour charger le en appelant une méthode telle que ou une surcharge de ce qui suppose que le type est dans un assemblage particulier. Si tel est le cas, l’assemblage référencé dans l’appel de méthode doit être mis à jour pour refléter le nouveau lieu d’assemblage du type.

#### <a name="category"></a>Category

CoreFx

#### <a name="affected-apis"></a>API affectées

Aucun.

<!--

### Affected APIs

- Not detectable via API analysis

-->
