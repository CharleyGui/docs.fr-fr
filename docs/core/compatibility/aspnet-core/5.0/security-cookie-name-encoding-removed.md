---
title: 'Modification avec rupture : sécurité : encodage du nom du cookie supprimé'
description: 'En savoir plus sur la modification avec rupture dans ASP.NET Core 5,0 intitulée sécurité : encodage du nom du cookie supprimé'
author: scottaddie
ms.author: scaddie
ms.date: 10/01/2020
ms.openlocfilehash: 3cd40d2b04d0cdf0863e3a3fb6d790c2b35692bc
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95761268"
---
# <a name="security-cookie-name-encoding-removed"></a>Sécurité : encodage du nom du cookie supprimé

La [norme de cookie http](https://tools.ietf.org/html/rfc6265#section-4.1.1) autorise uniquement des caractères spécifiques dans les noms et les valeurs des cookies. Pour prendre en charge les caractères non autorisés, ASP.NET Core :

* Encode lors de la création d’un cookie de réponse.
* Décode lors de la lecture d’un cookie de requête.

Dans ASP.NET Core 5,0, ce comportement d’encodage a changé en réponse à un problème de sécurité.

Pour plus d’informations, consultez GitHub issue [dotnet/aspnetcore # 23578](https://github.com/dotnet/aspnetcore/issues/23578).

## <a name="version-introduced"></a>Version introduite

5,0 Preview 8

## <a name="old-behavior"></a>Ancien comportement

Les noms de cookie de réponse sont encodés. Les noms des cookies de la demande sont décodés.

## <a name="new-behavior"></a>Nouveau comportement

L’encodage et le décodage des noms de cookies ont été supprimés. Pour les [versions antérieures prises en charge](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) de ASP.net Core, l’équipe envisage de limiter le problème de décodage sur place. En outre, <xref:Microsoft.AspNetCore.Http.IResponseCookies.Append%2A?displayProperty=nameWithType> l’appel de avec un nom de cookie non valide lève une exception de type <xref:System.ArgumentException> . L’encodage et le décodage des valeurs de cookie restent inchangés.

## <a name="reason-for-change"></a>Motif de modification

Un problème a été découvert dans [plusieurs infrastructures Web](https://github.com/advisories/GHSA-j6w9-fv6q-3q52). L’encodage et le décodage pourraient permettre à une personne malveillante de contourner une fonctionnalité de sécurité appelée [préfixes de cookie](https://tools.ietf.org/html/draft-ietf-httpbis-cookie-prefixes-00) en usurpant des préfixes réservés comme `__Host-` avec des valeurs encodées comme `__%48ost-` . L’attaque nécessite une exploitation secondaire pour injecter les cookies usurpés, tels qu’une vulnérabilité de script entre sites (XSS), dans le site Web. Ces préfixes ne sont pas utilisés par défaut dans les ASP.NET Core ou les `Microsoft.Owin` bibliothèques ou les modèles.

## <a name="recommended-action"></a>Action recommandée

Si vous déplacez des projets vers ASP.NET Core 5,0 ou version ultérieure, assurez-vous que leurs noms de cookie sont conformes aux spécifications de [jeton](https://tools.ietf.org/html/rfc2616#section-2.2): caractères ASCII, à l’exclusion des contrôles et des séparateurs `"(" | ")" | "<" | ">" | "@" | "," | ";" | ":" | "\" | <"> | "/" | "[" | "]" | "?" | "=" | "{" | "}" | SP | HT` . L’utilisation de caractères non-ASCII dans les noms de cookie ou d’autres en-têtes HTTP peut provoquer une exception du serveur ou un arrondi incorrectement effectué par le client.

## <a name="affected-apis"></a>API affectées

- <xref:Microsoft.AspNetCore.Http.HttpRequest.Cookies%2A?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Http.HttpResponse.Cookies%2A?displayProperty=nameWithType>
- <xref:Microsoft.Owin.IOwinRequest.Cookies?displayProperty=nameWithType>
- <xref:Microsoft.Owin.IOwinResponse.Cookies?displayProperty=nameWithType>

<!--

### Category

ASP.NET Core

### Affected APIs

- `Overload:Microsoft.AspNetCore.Http.HttpRequest.Cookies`
- `Overload:Microsoft.AspNetCore.Http.HttpResponse.Cookies`
- `P:Microsoft.Owin.IOwinRequest.Cookies`
- `P:Microsoft.Owin.IOwinResponse.Cookies`

-->
