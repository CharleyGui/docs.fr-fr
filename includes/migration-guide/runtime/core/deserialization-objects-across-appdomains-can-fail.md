---
ms.openlocfilehash: 3f82a4daac3b5d8981532f0c82e9a76f13c68b6e
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497258"
---
### <a name="deserialization-of-objects-across-appdomains-can-fail"></a><span data-ttu-id="b4097-101">La désérialisation d’objets entre les domaines d’application peut échouer</span><span class="sxs-lookup"><span data-stu-id="b4097-101">Deserialization of objects across appdomains can fail</span></span>

#### <a name="details"></a><span data-ttu-id="b4097-102">Détails</span><span class="sxs-lookup"><span data-stu-id="b4097-102">Details</span></span>

<span data-ttu-id="b4097-103">Dans certains cas, quand une application utilise deux domaines d'application ou plus avec des bases d'application différentes, une tentative de désérialisation des objets dans le contexte d'appel logique entre les domaines d'application lève une exception.</span><span class="sxs-lookup"><span data-stu-id="b4097-103">In some cases, when an app uses two or more app domains with different application bases, trying to deserialize objects in the logical call context across app domains throws an exception.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="b4097-104">Suggestion</span><span class="sxs-lookup"><span data-stu-id="b4097-104">Suggestion</span></span>

<span data-ttu-id="b4097-105">Consultez [Atténuation : désérialisation des objets entre les domaines d’application](~/docs/framework/migration-guide/mitigation-deserialization-of-objects-across-app-domains.md)</span><span class="sxs-lookup"><span data-stu-id="b4097-105">See [Mitigation: Deserialization of Objects Across App Domains](~/docs/framework/migration-guide/mitigation-deserialization-of-objects-across-app-domains.md)</span></span>

| <span data-ttu-id="b4097-106">Name</span><span class="sxs-lookup"><span data-stu-id="b4097-106">Name</span></span>    | <span data-ttu-id="b4097-107">Valeur</span><span class="sxs-lookup"><span data-stu-id="b4097-107">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="b4097-108">Étendue</span><span class="sxs-lookup"><span data-stu-id="b4097-108">Scope</span></span>   |<span data-ttu-id="b4097-109">Edge</span><span class="sxs-lookup"><span data-stu-id="b4097-109">Edge</span></span>|
|<span data-ttu-id="b4097-110">Version</span><span class="sxs-lookup"><span data-stu-id="b4097-110">Version</span></span>|<span data-ttu-id="b4097-111">4.5.1</span><span class="sxs-lookup"><span data-stu-id="b4097-111">4.5.1</span></span>|
|<span data-ttu-id="b4097-112">Type</span><span class="sxs-lookup"><span data-stu-id="b4097-112">Type</span></span>|<span data-ttu-id="b4097-113">Runtime</span><span class="sxs-lookup"><span data-stu-id="b4097-113">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="b4097-114">API affectées</span><span class="sxs-lookup"><span data-stu-id="b4097-114">Affected APIs</span></span>

<span data-ttu-id="b4097-115">Non détectable via l’analyse des API.</span><span class="sxs-lookup"><span data-stu-id="b4097-115">Not detectable via API analysis.</span></span>

<!--

#### Affected APIs

Not detectable via API analysis.

-->
