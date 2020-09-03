---
ms.openlocfilehash: fdbe8ca9b6dbf24c08a2d041c5c7f2e869995f69
ms.sourcegitcommit: b1f4756120deaecb8b554477bb040620f69a4209
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/03/2020
ms.locfileid: "89414450"
---
### <a name="cookie-path-handling-now-conforms-to-rfc-6265"></a><span data-ttu-id="fbfe3-101">La gestion des chemins d’accès des cookies est maintenant conforme à la norme RFC 6265</span><span class="sxs-lookup"><span data-stu-id="fbfe3-101">Cookie Path handling now conforms to RFC 6265</span></span>

<span data-ttu-id="fbfe3-102">Les algorithmes de gestion des chemins d’accès définis dans la [RFC 6265](https://tools.ietf.org/html/rfc6265) ont été implémentés pour les `Cookie` `CookieContainer` classes et.</span><span class="sxs-lookup"><span data-stu-id="fbfe3-102">Path handling algorithms defined in [RFC 6265](https://tools.ietf.org/html/rfc6265) were implemented for `Cookie` and `CookieContainer` classes.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="fbfe3-103">Version introduite</span><span class="sxs-lookup"><span data-stu-id="fbfe3-103">Version introduced</span></span>

<span data-ttu-id="fbfe3-104">5.0</span><span class="sxs-lookup"><span data-stu-id="fbfe3-104">5.0</span></span>

#### <a name="change-description"></a><span data-ttu-id="fbfe3-105">Description de la modification</span><span class="sxs-lookup"><span data-stu-id="fbfe3-105">Change description</span></span>

- <span data-ttu-id="fbfe3-106">La restriction de l' `Path` attribut est supprimée (il n’est plus censé être un préfixe du chemin d’accès de la demande).</span><span class="sxs-lookup"><span data-stu-id="fbfe3-106">Restriction for the `Path` attribute is removed (it's no longer expected to be a prefix of the request path).</span></span>
- <span data-ttu-id="fbfe3-107">Le calcul des algorithmes de valeur par défaut `Path` et de correspondance de chemin d’accès a été implémenté comme défini dans la [section 5.1.4](https://tools.ietf.org/html/rfc6265#section-5.1.4) de la RFC 6265.</span><span class="sxs-lookup"><span data-stu-id="fbfe3-107">Calculation of the default value of `Path` and path matching algorithms were implemented as defined in [section 5.1.4](https://tools.ietf.org/html/rfc6265#section-5.1.4) of RFC 6265.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="fbfe3-108">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="fbfe3-108">Recommended action</span></span>

<span data-ttu-id="fbfe3-109">Dans la plupart des cas, vous n’avez aucune action à effectuer.</span><span class="sxs-lookup"><span data-stu-id="fbfe3-109">In most cases, you won't need to take any action.</span></span> <span data-ttu-id="fbfe3-110">Toutefois, si votre code dépend de la `Path` validation, vous devez implémenter la validation requise dans votre code, ou si votre code dépend du `Path` calcul de la valeur par défaut de, vous souhaiterez peut-être fournir la `Path` valeur manuellement au lieu d’utiliser la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="fbfe3-110">However, if your code was dependent on `Path` validation you would need to implement required validation in your code; or if your code was dependent on `Path`'s default value calculation, you might want to supply the `Path` value manually instead of using the default value.</span></span>

#### <a name="category"></a><span data-ttu-id="fbfe3-111">Category</span><span class="sxs-lookup"><span data-stu-id="fbfe3-111">Category</span></span>

<span data-ttu-id="fbfe3-112">Mise en réseau</span><span class="sxs-lookup"><span data-stu-id="fbfe3-112">Networking</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="fbfe3-113">API affectées</span><span class="sxs-lookup"><span data-stu-id="fbfe3-113">Affected APIs</span></span>

- <xref:System.Net.Cookie?displayProperty=fullName>
- <xref:System.Net.CookieContainer?displayProperty=fullName>

<!--

#### Affected APIs

- `T:System.Net.Cookie`
- `T:System.Net.CookieContainer`

-->
