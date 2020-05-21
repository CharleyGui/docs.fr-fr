---
ms.openlocfilehash: 7a2617f27dfd6bb527ff6d408fae6382075f24ae
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83721527"
---
### <a name="typedescriptionproviderattribute-moved-to-another-assembly"></a>TypeDescriptionProviderAttribute déplacé vers un autre assembly

La <xref:System.ComponentModel.TypeDescriptionProviderAttribute> classe a été déplacée.

#### <a name="change-description"></a>Description de la modification

Dans .NET Core 2,2 et les versions antérieures, la <xref:System.ComponentModel.TypeDescriptionProviderAttribute> classe se trouve dans l’assembly *System. ComponentModel. TypeConverter* .

À compter de .NET Core 3,0, il se trouve dans l’assembly *System. ObjectModel* .

#### <a name="version-introduced"></a>Version introduite

3.0

#### <a name="recommended-action"></a>Action recommandée

Cette modification affecte uniquement les applications qui utilisent la réflexion pour charger le <xref:System.ComponentModel.TypeDescriptionProviderAttribute> type en appelant une méthode telle que <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType> ou une surcharge de <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType> qui suppose que le type se trouve dans un assembly particulier. Si tel est le cas, l’assembly référencé dans l’appel de méthode doit être mis à jour pour refléter le nouvel emplacement de l’assembly du type.

#### <a name="category"></a>Category

Windows Forms

#### <a name="affected-apis"></a>API affectées

Aucun.

<!--

#### Affected APIs

- Not detectable via API analysis

-->
