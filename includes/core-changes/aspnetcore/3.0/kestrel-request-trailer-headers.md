---
ms.openlocfilehash: b0e1d6d720a1c9b827fb4585606e64b545d395d7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "72393925"
---
### <a name="kestrel-request-trailer-headers-moved-to-new-collection"></a>Kestrel: En-têtes de remorque de demande déplacé à la nouvelle collection

Dans les versions précédentes, Kestrel a ajouté HTTP/1.1 en-têtes de remorque en morceaux dans la collection d’en-têtes de demande lorsque le corps de demande a été lu à la fin. Ce comportement a suscité des inquiétudes quant à l’ambiguïté entre les en-têtes et les remorques. La décision a été prise de déplacer les remorques vers une nouvelle collection.

Les remorques de demande HTTP/2 n’étaient pas disponibles dans ASP.NET Core 2.2, mais sont maintenant également disponibles dans cette nouvelle collection dans ASP.NET Core 3.0.

De nouvelles méthodes d’extension de demande ont été ajoutées pour accéder à ces remorques.

LES remorques HTTP/1.1 sont disponibles une fois que l’ensemble du corps de demande a été lu.

Les bandes-annonces HTTP/2 sont disponibles une fois reçues du client. Le client n’enverra pas les remorques jusqu’à ce que l’ensemble du corps de demande a été au moins tamponné par le serveur. Vous devrez peut-être lire le corps de demande pour libérer l’espace tampon. Les remorques sont toujours disponibles si vous lisez le corps de demande jusqu’à la fin. Les remorques marquent la fin du corps.

#### <a name="version-introduced"></a>Version introduite

3.0

#### <a name="old-behavior"></a>Ancien comportement

Les en-têtes de remorque `HttpRequest.Headers` de demande seraient ajoutés à la collection.

#### <a name="new-behavior"></a>Nouveau comportement

Les en-têtes de bande-annonce de demande **ne sont pas présents** dans la `HttpRequest.Headers` collection. Utilisez les méthodes `HttpRequest` d’extension suivantes pour y accéder :

- `GetDeclaredTrailers()`- Obtient la demande "Bande-annonce" en-tête qui énumère les remorques à attendre après le corps.
- `SupportsTrailers()`- Indique si la demande prend en charge la réception des en-têtes de remorque.
- `CheckTrailersAvailable()`- Détermine si la demande prend en charge les remorques et si elles sont disponibles pour la lecture.
- `GetTrailer(string trailerName)`- Obtient l’en-tête demandé de la réponse.

#### <a name="reason-for-change"></a>Raison du changement

Les bandes-annonces sont une caractéristique clé dans des scénarios comme gRPC. La fusion des remorques pour demander des en-têtes était déroutant pour les utilisateurs.

#### <a name="recommended-action"></a>Action recommandée

Utilisez les méthodes d’extension liées à la remorque pour `HttpRequest` accéder aux remorques.

#### <a name="category"></a>Category

ASP.NET Core

#### <a name="affected-apis"></a>API affectées

<xref:Microsoft.AspNetCore.Http.HttpRequest.Headers?displayProperty=nameWithType>

<!--

#### Affected APIs

`P:Microsoft.AspNetCore.Http.HttpRequest.Headers`

-->
