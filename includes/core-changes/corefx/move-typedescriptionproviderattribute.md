---
ms.openlocfilehash: 4fbec1028b6d75b90d4638814c877c263c8c8936
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2019
ms.locfileid: "71182073"
---
### <a name="typedescriptionproviderattribute-moved-to-another-assembly"></a>TypeDescriptionProviderAttribute déplacé vers un autre assembly

La <xref:System.ComponentModel.TypeDescriptionProviderAttribute> classe a été déplacée.

#### <a name="change-description"></a>Modifier la description

Dans .net Core 2,2 et les versions antérieures, <xref:System.ComponentModel.TypeDescriptionProviderAttribute> la classe se trouve dans l’assembly *System. ComponentModel. TypeConverter* .

À compter de .NET Core 3,0, il se trouve dans l’assembly *System. ObjectModel* .

#### <a name="version-introduced"></a>Version introduite

3.0

#### <a name="recommended-action"></a>Action recommandée

Cette modification affecte uniquement les applications qui utilisent la réflexion pour <xref:System.ComponentModel.TypeDescriptionProviderAttribute> charger le type en appelant une méthode <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType> telle que ou une <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType> surcharge de qui suppose que le type se trouve dans un assembly particulier. Si tel est le cas, l’assembly référencé dans l’appel de méthode doit être mis à jour pour refléter le nouvel emplacement de l’assembly du type.

#### <a name="category"></a>Category

Windows Forms

#### <a name="affected-apis"></a>API affectées

- Aucun.

<!-- 

### Affected APIs

- Not detectable via API analysis

-->