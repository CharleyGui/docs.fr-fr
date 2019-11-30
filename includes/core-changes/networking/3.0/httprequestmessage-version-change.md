---
ms.openlocfilehash: ff156afb3da4b921517fd841c5de2295265a8d7b
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2019
ms.locfileid: "74567753"
---
### <a name="default-value-of-httprequestmessageversion-changed-to-11"></a>La valeur par défaut de HttpRequestMessage. version est passée à 1,1

La valeur par défaut de la propriété <xref:System.Net.Http.HttpRequestMessage.Version?displayProperty=fullName> est passée de 2,0 à 1,1.

#### <a name="version-introduced"></a>Version introduite

.NET Core 3.0

#### <a name="change-description"></a>Modifier la description

Dans .NET Core 1,0 à 2,0, la valeur par défaut de la propriété <xref:System.Net.Http.HttpRequestMessage.Version?displayProperty=fullName> est 1,1. À compter de .NET Core 2,1, il a été remplacé par 2,1.

À compter de .NET Core 3,0, le numéro de version par défaut retourné par la propriété <xref:System.Net.Http.HttpRequestMessage.Version?displayProperty=fullName> est encore une fois 1,1.

#### <a name="recommended-action"></a>Action recommandée

Mettez à jour votre code s’il dépend de la propriété <xref:System.Net.Http.HttpRequestMessage.Version?displayProperty=fullName> retournant une valeur par défaut de 2,0.

#### <a name="category"></a>Category

Mise en réseau

#### <a name="affected-apis"></a>API affectées

- <xref:System.Net.Http.HttpRequestMessage.Version?displayProperty=fullName>

<!--
a def
### Affected APIs

- `P:System.Net.Http.HttpRequestMessage.Version`

-- >

