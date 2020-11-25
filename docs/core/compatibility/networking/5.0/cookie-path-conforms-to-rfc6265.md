---
title: 'Modification avec rupture : la gestion des chemins d’accès des cookies est maintenant conforme à la norme RFC 6265'
description: Découvrez la modification avec rupture dans .NET 5,0 où les algorithmes de gestion des chemins d’accès définis dans la RFC 6265 ont été implémentés pour les classes cookie et CookieContainer.
ms.date: 08/18/2020
ms.openlocfilehash: 4aea06f434c4bbbef7d94b4b39ff647dd954745e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95760936"
---
# <a name="cookie-path-handling-now-conforms-to-rfc-6265"></a><span data-ttu-id="66ffd-103">La gestion des chemins d’accès des cookies est maintenant conforme à la norme RFC 6265</span><span class="sxs-lookup"><span data-stu-id="66ffd-103">Cookie path handling now conforms to RFC 6265</span></span>

<span data-ttu-id="66ffd-104">Les algorithmes de gestion des chemins d’accès définis dans la [RFC 6265](https://tools.ietf.org/html/rfc6265) ont été implémentés pour les <xref:System.Net.Cookie> <xref:System.Net.CookieContainer> classes et.</span><span class="sxs-lookup"><span data-stu-id="66ffd-104">Path-handling algorithms defined in [RFC 6265](https://tools.ietf.org/html/rfc6265) were implemented for the <xref:System.Net.Cookie> and <xref:System.Net.CookieContainer> classes.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="66ffd-105">Version introduite</span><span class="sxs-lookup"><span data-stu-id="66ffd-105">Version introduced</span></span>

<span data-ttu-id="66ffd-106">5.0</span><span class="sxs-lookup"><span data-stu-id="66ffd-106">5.0</span></span>

## <a name="change-description"></a><span data-ttu-id="66ffd-107">Description de la modification</span><span class="sxs-lookup"><span data-stu-id="66ffd-107">Change description</span></span>

- <span data-ttu-id="66ffd-108">La <xref:System.Net.Cookie.Path> propriété ne doit plus être un préfixe du chemin d’accès de la requête.</span><span class="sxs-lookup"><span data-stu-id="66ffd-108">The <xref:System.Net.Cookie.Path> property is no longer required to be a prefix of the request path.</span></span>
- <span data-ttu-id="66ffd-109">Le calcul de la valeur par défaut de <xref:System.Net.Cookie.Path> et des algorithmes de correspondance de chemin d’accès a été implémenté comme défini dans la [section 5.1.4](https://tools.ietf.org/html/rfc6265#section-5.1.4) de la RFC 6265.</span><span class="sxs-lookup"><span data-stu-id="66ffd-109">The calculation of the default value of <xref:System.Net.Cookie.Path> and path-matching algorithms were implemented as defined in [section 5.1.4](https://tools.ietf.org/html/rfc6265#section-5.1.4) of RFC 6265.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="66ffd-110">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="66ffd-110">Recommended action</span></span>

<span data-ttu-id="66ffd-111">Dans la plupart des cas, vous n’avez aucune action à effectuer.</span><span class="sxs-lookup"><span data-stu-id="66ffd-111">In most cases, you won't need to take any action.</span></span> <span data-ttu-id="66ffd-112">Toutefois, si votre code dépend de la <xref:System.Net.Cookie.Path> validation, vous devez implémenter la validation requise dans votre code.</span><span class="sxs-lookup"><span data-stu-id="66ffd-112">However, if your code was dependent on <xref:System.Net.Cookie.Path> validation, you'll need to implement required validation in your code.</span></span> <span data-ttu-id="66ffd-113">Si votre code dépend du calcul de la valeur par défaut pour <xref:System.Net.Cookie.Path> , envisagez de fournir la <xref:System.Net.Cookie.Path> valeur manuellement au lieu d’utiliser la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="66ffd-113">If your code was dependent on default value calculation for <xref:System.Net.Cookie.Path>, consider supplying the <xref:System.Net.Cookie.Path> value manually instead of using the default value.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="66ffd-114">API affectées</span><span class="sxs-lookup"><span data-stu-id="66ffd-114">Affected APIs</span></span>

- <xref:System.Net.Cookie?displayProperty=fullName>
- <xref:System.Net.CookieContainer?displayProperty=fullName>

<!--

### Affected APIs

- `T:System.Net.Cookie`
- `T:System.Net.CookieContainer`

### Category

Networking

-->
