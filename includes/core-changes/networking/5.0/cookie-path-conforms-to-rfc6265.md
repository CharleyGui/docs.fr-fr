---
ms.openlocfilehash: 7140f6d4cac063088b3663ab98d292104218b542
ms.sourcegitcommit: e7acba36517134238065e4d50bb4a1cfe47ebd06
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2020
ms.locfileid: "89465509"
---
### <a name="cookie-path-handling-now-conforms-to-rfc-6265"></a>La gestion des chemins d’accès des cookies est maintenant conforme à la norme RFC 6265

Les algorithmes de gestion des chemins d’accès définis dans la [RFC 6265](https://tools.ietf.org/html/rfc6265) ont été implémentés pour les <xref:System.Net.Cookie> <xref:System.Net.CookieContainer> classes et.

#### <a name="version-introduced"></a>Version introduite

5.0

#### <a name="change-description"></a>Description de la modification

- La <xref:System.Net.Cookie.Path> propriété ne doit plus être un préfixe du chemin d’accès de la requête.
- Le calcul de la valeur par défaut de <xref:System.Net.Cookie.Path> et des algorithmes de correspondance de chemin d’accès a été implémenté comme défini dans la [section 5.1.4](https://tools.ietf.org/html/rfc6265#section-5.1.4) de la RFC 6265.

#### <a name="recommended-action"></a>Action recommandée

Dans la plupart des cas, vous n’avez aucune action à effectuer. Toutefois, si votre code dépend de la <xref:System.Net.Cookie.Path> validation, vous devez implémenter la validation requise dans votre code. Si votre code dépend du calcul de la valeur par défaut pour <xref:System.Net.Cookie.Path> , envisagez de fournir la <xref:System.Net.Cookie.Path> valeur manuellement au lieu d’utiliser la valeur par défaut.

#### <a name="category"></a>Category

Mise en réseau

#### <a name="affected-apis"></a>API affectées

- <xref:System.Net.Cookie?displayProperty=fullName>
- <xref:System.Net.CookieContainer?displayProperty=fullName>

<!--

#### Affected APIs

- `T:System.Net.Cookie`
- `T:System.Net.CookieContainer`

-->
