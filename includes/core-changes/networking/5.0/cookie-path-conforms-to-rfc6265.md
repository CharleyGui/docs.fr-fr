---
ms.openlocfilehash: 7140f6d4cac063088b3663ab98d292104218b542
ms.sourcegitcommit: e7acba36517134238065e4d50bb4a1cfe47ebd06
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2020
ms.locfileid: "89465509"
---
### <a name="cookie-path-handling-now-conforms-to-rfc-6265"></a><span data-ttu-id="5a4be-101">La gestion des chemins d’accès des cookies est maintenant conforme à la norme RFC 6265</span><span class="sxs-lookup"><span data-stu-id="5a4be-101">Cookie Path handling now conforms to RFC 6265</span></span>

<span data-ttu-id="5a4be-102">Les algorithmes de gestion des chemins d’accès définis dans la [RFC 6265](https://tools.ietf.org/html/rfc6265) ont été implémentés pour les <xref:System.Net.Cookie> <xref:System.Net.CookieContainer> classes et.</span><span class="sxs-lookup"><span data-stu-id="5a4be-102">Path-handling algorithms defined in [RFC 6265](https://tools.ietf.org/html/rfc6265) were implemented for the <xref:System.Net.Cookie> and <xref:System.Net.CookieContainer> classes.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="5a4be-103">Version introduite</span><span class="sxs-lookup"><span data-stu-id="5a4be-103">Version introduced</span></span>

<span data-ttu-id="5a4be-104">5.0</span><span class="sxs-lookup"><span data-stu-id="5a4be-104">5.0</span></span>

#### <a name="change-description"></a><span data-ttu-id="5a4be-105">Description de la modification</span><span class="sxs-lookup"><span data-stu-id="5a4be-105">Change description</span></span>

- <span data-ttu-id="5a4be-106">La <xref:System.Net.Cookie.Path> propriété ne doit plus être un préfixe du chemin d’accès de la requête.</span><span class="sxs-lookup"><span data-stu-id="5a4be-106">The <xref:System.Net.Cookie.Path> property is no longer required to be a prefix of the request path.</span></span>
- <span data-ttu-id="5a4be-107">Le calcul de la valeur par défaut de <xref:System.Net.Cookie.Path> et des algorithmes de correspondance de chemin d’accès a été implémenté comme défini dans la [section 5.1.4](https://tools.ietf.org/html/rfc6265#section-5.1.4) de la RFC 6265.</span><span class="sxs-lookup"><span data-stu-id="5a4be-107">The calculation of the default value of <xref:System.Net.Cookie.Path> and path-matching algorithms were implemented as defined in [section 5.1.4](https://tools.ietf.org/html/rfc6265#section-5.1.4) of RFC 6265.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="5a4be-108">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="5a4be-108">Recommended action</span></span>

<span data-ttu-id="5a4be-109">Dans la plupart des cas, vous n’avez aucune action à effectuer.</span><span class="sxs-lookup"><span data-stu-id="5a4be-109">In most cases, you won't need to take any action.</span></span> <span data-ttu-id="5a4be-110">Toutefois, si votre code dépend de la <xref:System.Net.Cookie.Path> validation, vous devez implémenter la validation requise dans votre code.</span><span class="sxs-lookup"><span data-stu-id="5a4be-110">However, if your code was dependent on <xref:System.Net.Cookie.Path> validation, you'll need to implement required validation in your code.</span></span> <span data-ttu-id="5a4be-111">Si votre code dépend du calcul de la valeur par défaut pour <xref:System.Net.Cookie.Path> , envisagez de fournir la <xref:System.Net.Cookie.Path> valeur manuellement au lieu d’utiliser la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="5a4be-111">If your code was dependent on default value calculation for <xref:System.Net.Cookie.Path>, consider supplying the <xref:System.Net.Cookie.Path> value manually instead of using the default value.</span></span>

#### <a name="category"></a><span data-ttu-id="5a4be-112">Category</span><span class="sxs-lookup"><span data-stu-id="5a4be-112">Category</span></span>

<span data-ttu-id="5a4be-113">Mise en réseau</span><span class="sxs-lookup"><span data-stu-id="5a4be-113">Networking</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="5a4be-114">API affectées</span><span class="sxs-lookup"><span data-stu-id="5a4be-114">Affected APIs</span></span>

- <xref:System.Net.Cookie?displayProperty=fullName>
- <xref:System.Net.CookieContainer?displayProperty=fullName>

<!--

#### Affected APIs

- `T:System.Net.Cookie`
- `T:System.Net.CookieContainer`

-->
