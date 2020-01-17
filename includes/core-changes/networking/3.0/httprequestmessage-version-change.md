---
ms.openlocfilehash: 9aff20e35469f9e786f0f790fda4ffaa04e76e64
ms.sourcegitcommit: ed3f926b6cdd372037bbcc214dc8f08a70366390
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/16/2020
ms.locfileid: "76116412"
---
### <a name="default-value-of-httprequestmessageversion-changed-to-11"></a>La valeur par défaut de HttpRequestMessage. version est passée à 1,1

La valeur par défaut de la propriété <xref:System.Net.Http.HttpRequestMessage.Version?displayProperty=fullName> est passée de 2,0 à 1,1.

#### <a name="version-introduced"></a>Version introduite

.NET Core 3.0

#### <a name="change-description"></a>Description des modifications

Dans .NET Core 1,0 à 2,0, la valeur par défaut de la propriété <xref:System.Net.Http.HttpRequestMessage.Version?displayProperty=fullName> est 1,1. À compter de .NET Core 2,1, il a été remplacé par 2,1.

À compter de .NET Core 3,0, le numéro de version par défaut retourné par la propriété <xref:System.Net.Http.HttpRequestMessage.Version?displayProperty=fullName> est encore une fois 1,1.

#### <a name="recommended-action"></a>Action recommandée

Mettez à jour votre code s’il dépend de la propriété <xref:System.Net.Http.HttpRequestMessage.Version?displayProperty=fullName> retournant une valeur par défaut de 2,0.

#### <a name="category"></a>Catégorie

Mise en réseau

#### <a name="affected-apis"></a>API affectées

- <xref:System.Net.Http.HttpRequestMessage.Version?displayProperty=fullName>

<!--
a def
### Affected APIs

- `P:System.Net.Http.HttpRequestMessage.Version`

-->
