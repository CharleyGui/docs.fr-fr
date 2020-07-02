---
ms.openlocfilehash: 5c949b79eefa68ea6f8d4ad27c716c438e24f170
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619961"
---
### <a name="deserialization-of-objects-across-appdomains-can-fail"></a><span data-ttu-id="57d96-101">La désérialisation d’objets entre les domaines d’application peut échouer</span><span class="sxs-lookup"><span data-stu-id="57d96-101">Deserialization of objects across appdomains can fail</span></span>

#### <a name="details"></a><span data-ttu-id="57d96-102">Détails</span><span class="sxs-lookup"><span data-stu-id="57d96-102">Details</span></span>

<span data-ttu-id="57d96-103">Dans certains cas, quand une application utilise deux domaines d'application ou plus avec des bases d'application différentes, une tentative de désérialisation des objets dans le contexte d'appel logique entre les domaines d'application lève une exception.</span><span class="sxs-lookup"><span data-stu-id="57d96-103">In some cases, when an app uses two or more app domains with different application bases, trying to deserialize objects in the logical call context across app domains throws an exception.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="57d96-104">Suggestion</span><span class="sxs-lookup"><span data-stu-id="57d96-104">Suggestion</span></span>

<span data-ttu-id="57d96-105">Consultez [Atténuation : désérialisation des objets entre les domaines d’application](~/docs/framework/migration-guide/mitigation-deserialization-of-objects-across-app-domains.md)</span><span class="sxs-lookup"><span data-stu-id="57d96-105">See [Mitigation: Deserialization of Objects Across App Domains](~/docs/framework/migration-guide/mitigation-deserialization-of-objects-across-app-domains.md)</span></span>

| <span data-ttu-id="57d96-106">Nom</span><span class="sxs-lookup"><span data-stu-id="57d96-106">Name</span></span>    | <span data-ttu-id="57d96-107">Valeur</span><span class="sxs-lookup"><span data-stu-id="57d96-107">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="57d96-108">Étendue</span><span class="sxs-lookup"><span data-stu-id="57d96-108">Scope</span></span>   |<span data-ttu-id="57d96-109">Edge</span><span class="sxs-lookup"><span data-stu-id="57d96-109">Edge</span></span>|
|<span data-ttu-id="57d96-110">Version</span><span class="sxs-lookup"><span data-stu-id="57d96-110">Version</span></span>|<span data-ttu-id="57d96-111">4.5.1</span><span class="sxs-lookup"><span data-stu-id="57d96-111">4.5.1</span></span>|
|<span data-ttu-id="57d96-112">Type</span><span class="sxs-lookup"><span data-stu-id="57d96-112">Type</span></span>|<span data-ttu-id="57d96-113">Runtime</span><span class="sxs-lookup"><span data-stu-id="57d96-113">Runtime</span></span>|
