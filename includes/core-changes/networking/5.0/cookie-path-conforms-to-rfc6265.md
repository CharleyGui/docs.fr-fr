---
ms.openlocfilehash: fdbe8ca9b6dbf24c08a2d041c5c7f2e869995f69
ms.sourcegitcommit: b1f4756120deaecb8b554477bb040620f69a4209
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/03/2020
ms.locfileid: "89414450"
---
### <a name="cookie-path-handling-now-conforms-to-rfc-6265"></a>La gestion des chemins d’accès des cookies est maintenant conforme à la norme RFC 6265

Les algorithmes de gestion des chemins d’accès définis dans la [RFC 6265](https://tools.ietf.org/html/rfc6265) ont été implémentés pour les `Cookie` `CookieContainer` classes et.

#### <a name="version-introduced"></a>Version introduite

5.0

#### <a name="change-description"></a>Description de la modification

- La restriction de l' `Path` attribut est supprimée (il n’est plus censé être un préfixe du chemin d’accès de la demande).
- Le calcul des algorithmes de valeur par défaut `Path` et de correspondance de chemin d’accès a été implémenté comme défini dans la [section 5.1.4](https://tools.ietf.org/html/rfc6265#section-5.1.4) de la RFC 6265.

#### <a name="recommended-action"></a>Action recommandée

Dans la plupart des cas, vous n’avez aucune action à effectuer. Toutefois, si votre code dépend de la `Path` validation, vous devez implémenter la validation requise dans votre code, ou si votre code dépend du `Path` calcul de la valeur par défaut de, vous souhaiterez peut-être fournir la `Path` valeur manuellement au lieu d’utiliser la valeur par défaut.

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
