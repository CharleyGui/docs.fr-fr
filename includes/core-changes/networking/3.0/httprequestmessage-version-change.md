---
ms.openlocfilehash: 5ad9c494fd02059e05cc744aad3b06cfc9399995
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "77451882"
---
### <a name="default-value-of-httprequestmessageversion-changed-to-11"></a>La valeur par défaut de HttpRequestMessage. version est passée à 1,1

La valeur par défaut de <xref:System.Net.Http.HttpRequestMessage.Version?displayProperty=fullName> la propriété est passée de 2,0 à 1,1.

#### <a name="version-introduced"></a>Version introduite

3.0

#### <a name="change-description"></a>Description de la modification

Dans .NET Core 1,0 à 2,0, la valeur par défaut de <xref:System.Net.Http.HttpRequestMessage.Version?displayProperty=fullName> la propriété est 1,1. À compter de .NET Core 2,1, il a été remplacé par 2,1.

À compter de .NET Core 3,0, le numéro de version par défaut <xref:System.Net.Http.HttpRequestMessage.Version?displayProperty=fullName> retourné par la propriété est encore une fois 1,1.

#### <a name="recommended-action"></a>Action recommandée

Mettez à jour votre code s’il dépend <xref:System.Net.Http.HttpRequestMessage.Version?displayProperty=fullName> de la propriété qui retourne une valeur par défaut de 2,0.

#### <a name="category"></a>Category

Mise en réseau

#### <a name="affected-apis"></a>API affectées

- <xref:System.Net.Http.HttpRequestMessage.Version?displayProperty=fullName>

<!--

#### Affected APIs

- `P:System.Net.Http.HttpRequestMessage.Version`

-->
