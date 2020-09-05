---
ms.openlocfilehash: fccf349517133245ec85ae3c25cedbfb27a7dd8b
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496448"
---
### <a name="the-replace-method-in-odata-urls-is-disabled-by-default"></a><span data-ttu-id="2952b-101">La méthode Replace est désactivée par défaut dans les URL OData</span><span class="sxs-lookup"><span data-stu-id="2952b-101">The Replace method in OData URLs is disabled by default</span></span>

#### <a name="details"></a><span data-ttu-id="2952b-102">Détails</span><span class="sxs-lookup"><span data-stu-id="2952b-102">Details</span></span>

<span data-ttu-id="2952b-103">À compter de la version 4.5 du .NET Framework, la méthode Replace des URL OData est désactivée par défaut.</span><span class="sxs-lookup"><span data-stu-id="2952b-103">Beginning in the .NET Framework 4.5, the Replace method in OData URLs is disabled by default.</span></span> <span data-ttu-id="2952b-104">Quand la méthode Replace OData est désactivée (ce qui est désormais le cas par défaut), toutes les demandes utilisateur, y compris les fonctions de remplacement (qui sont rares) échouent.</span><span class="sxs-lookup"><span data-stu-id="2952b-104">When OData Replace is disabled (now by default), any user requests including replace functions (which are uncommon) will fail.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="2952b-105">Suggestion</span><span class="sxs-lookup"><span data-stu-id="2952b-105">Suggestion</span></span>

<span data-ttu-id="2952b-106">Si la méthode Replace est nécessaire (ce qui est rare), elle peut être réactivée via les paramètres de configuration (<xref:System.Data.Services.Configuration.DataServicesFeaturesSection.ReplaceFunction?displayProperty=fullName>).</span><span class="sxs-lookup"><span data-stu-id="2952b-106">If the replace method is required (which is uncommon), it can be re-enabled through a config settings (<xref:System.Data.Services.Configuration.DataServicesFeaturesSection.ReplaceFunction?displayProperty=fullName>).</span></span> <span data-ttu-id="2952b-107">Toutefois, l’activation d’une méthode Replace peut créer des failles de sécurité et ne doit donc être utilisée qu’après un examen minutieux.</span><span class="sxs-lookup"><span data-stu-id="2952b-107">However, an enabled replace method can open security vulnerabilities and should only be used after careful review.</span></span>

| <span data-ttu-id="2952b-108">Name</span><span class="sxs-lookup"><span data-stu-id="2952b-108">Name</span></span>    | <span data-ttu-id="2952b-109">Valeur</span><span class="sxs-lookup"><span data-stu-id="2952b-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="2952b-110">Étendue</span><span class="sxs-lookup"><span data-stu-id="2952b-110">Scope</span></span>   |<span data-ttu-id="2952b-111">Edge</span><span class="sxs-lookup"><span data-stu-id="2952b-111">Edge</span></span>|
|<span data-ttu-id="2952b-112">Version</span><span class="sxs-lookup"><span data-stu-id="2952b-112">Version</span></span>|<span data-ttu-id="2952b-113">4,5</span><span class="sxs-lookup"><span data-stu-id="2952b-113">4.5</span></span>|
|<span data-ttu-id="2952b-114">Type</span><span class="sxs-lookup"><span data-stu-id="2952b-114">Type</span></span>|<span data-ttu-id="2952b-115">Runtime</span><span class="sxs-lookup"><span data-stu-id="2952b-115">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="2952b-116">API affectées</span><span class="sxs-lookup"><span data-stu-id="2952b-116">Affected APIs</span></span>

- <xref:System.Data.Services.DataService%601?displayProperty=nameWithType>

<!--

#### Affected APIs

- ``T:System.Data.Services.DataService`1``

-->
