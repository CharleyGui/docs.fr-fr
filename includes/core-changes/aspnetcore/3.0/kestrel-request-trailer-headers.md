---
ms.openlocfilehash: b0e1d6d720a1c9b827fb4585606e64b545d395d7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "72393925"
---
### <a name="kestrel-request-trailer-headers-moved-to-new-collection"></a>Kestrel : les en-têtes de demande de code de fin sont déplacés vers la nouvelle collection

Dans les versions antérieures, Kestrel a ajouté les en-têtes de code de fin en bloc HTTP/1.1 dans la collection d’en-têtes de demande lorsque le corps de la demande a été lu jusqu’à la fin. Ce comportement est dû à des problèmes d’ambiguïté entre les en-têtes et les codes de fin. La décision a été prise de déplacer les codes de fin vers une nouvelle collection.

Les codes de fin de requête HTTP/2 n’étaient pas disponibles dans ASP.NET Core 2,2, mais ils sont désormais également disponibles dans ce nouveau regroupement dans ASP.NET Core 3,0.

De nouvelles méthodes d’extension de requête ont été ajoutées pour accéder à ces codes de fin.

Les codes de fin HTTP/1.1 sont disponibles une fois que le corps de la demande a été lu dans son intégralité.

Les codes de fin HTTP/2 sont disponibles une fois qu’ils sont reçus du client. Le client n’enverra pas les codes de fin tant que le corps de la demande n’a pas été au moins mis en mémoire tampon par le serveur. Vous devrez peut-être lire le corps de la demande pour libérer de l’espace dans la mémoire tampon. Les codes de fin sont toujours disponibles si vous lisez le corps de la demande à la fin. Les remorques marquent la fin du corps.

#### <a name="version-introduced"></a>Version introduite

3.0

#### <a name="old-behavior"></a>Ancien comportement

Les en-têtes de demande de fin sont `HttpRequest.Headers` ajoutés à la collection.

#### <a name="new-behavior"></a>Nouveau comportement

Les en-têtes de demande de fin `HttpRequest.Headers` **ne sont pas présents** dans la collection. Utilisez les méthodes d’extension suivantes `HttpRequest` sur pour y accéder :

- `GetDeclaredTrailers()`-Obtient l’en-tête « code de fin » de la demande qui répertorie les codes de fin à attendre après le corps.
- `SupportsTrailers()`-Indique si la demande prend en charge la réception des en-têtes de code de fin.
- `CheckTrailersAvailable()`: Détermine si la requête prend en charge les codes de fin et si elles sont disponibles pour la lecture.
- `GetTrailer(string trailerName)`: Obtient l’en-tête de fin demandé de la réponse.

#### <a name="reason-for-change"></a>Motif de modification

Les codes de fin sont une fonctionnalité clé dans des scénarios tels que gRPC. La fusion des codes de fin dans les en-têtes de demande était confuse pour les utilisateurs.

#### <a name="recommended-action"></a>Action recommandée

Utilisez les méthodes d’extension liées `HttpRequest` à la remorque pour accéder aux codes de fin.

#### <a name="category"></a>Category

ASP.NET Core

#### <a name="affected-apis"></a>API affectées

<xref:Microsoft.AspNetCore.Http.HttpRequest.Headers?displayProperty=nameWithType>

<!--

#### Affected APIs

`P:Microsoft.AspNetCore.Http.HttpRequest.Headers`

-->
