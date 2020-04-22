---
ms.openlocfilehash: ace0a4a60ad4d3f3a13cf4bdb2431e61d04ad8e7
ms.sourcegitcommit: 348bb052d5cef109a61a3d5253faa5d7167d55ac
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "82021547"
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

Core .NET bibliothèques

#### <a name="affected-apis"></a>API affectées

Aucun.

<!--

### Affected APIs

- Not detectable via API analysis

-->
