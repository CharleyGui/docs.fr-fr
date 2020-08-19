---
ms.openlocfilehash: 115cd6be935ae12a1293f948a0f899c6c3ff0d78
ms.sourcegitcommit: cbb19e56d48cf88375d35d0c27554d4722761e0d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/19/2020
ms.locfileid: "88608465"
---
### <a name="winhttphandler-removed-from-net-runtime"></a>WinHttpHandler supprimé du Runtime .NET

La `WinHttpHandler` classe a été supprimée de l’assembly *System.Net.Http.dll* . Il est désormais disponible uniquement en tant que [package NuGet](https://www.nuget.org/packages/System.Net.Http.WinHttpHandler/)hors-bande (OOB).

#### <a name="version-introduced"></a>Version introduite

5.0

#### <a name="change-description"></a>Description de la modification

Dans les versions précédentes de .NET, la <xref:System.Net.Http.WinHttpHandler> classe est disponible dans le cadre des bibliothèques .net de base. À compter de .NET 5,0, la <xref:System.Net.Http.WinHttpHandler> classe est uniquement disponible en tant que [package NuGet](https://www.nuget.org/packages/System.Net.Http.WinHttpHandler/)installé séparément.

#### <a name="recommended-action"></a>Action recommandée

Installez le [package NuGet System .net. http. WinHttpHandler](https://www.nuget.org/packages/System.Net.Http.WinHttpHandler/). Ou, si vous n’avez pas besoin de fonctionnalités spécifiques à WinHTTP, utilisez à la <xref:System.Net.Http.SocketsHttpHandler> place.

#### <a name="category"></a>Category

Mise en réseau

#### <a name="affected-apis"></a>API affectées

- <xref:System.Net.Http.WinHttpHandler?displayProperty=fullName>

<!--

#### Affected APIs

- `T:System.Net.Http.WinHttpHandler`

-->
