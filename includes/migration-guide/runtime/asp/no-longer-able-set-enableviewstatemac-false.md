---
ms.openlocfilehash: c1793bb51f7da9169e912078fde202d0d62a4183
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497104"
---
### <a name="no-longer-able-to-set-enableviewstatemac-to-false"></a><span data-ttu-id="0c1a1-101">Il n’est plus possible de définir EnableViewStateMac sur false</span><span class="sxs-lookup"><span data-stu-id="0c1a1-101">No longer able to set EnableViewStateMac to false</span></span>

#### <a name="details"></a><span data-ttu-id="0c1a1-102">Détails</span><span class="sxs-lookup"><span data-stu-id="0c1a1-102">Details</span></span>

<span data-ttu-id="0c1a1-103">ASP.NET ne permet plus aux développeurs de spécifier <code>&lt;pages enableViewStateMac=&quot;false&quot;/&gt;</code> ou <code>&lt;@Page EnableViewStateMac=&quot;false&quot; %&gt;</code>.</span><span class="sxs-lookup"><span data-stu-id="0c1a1-103">ASP.NET no longer allows developers to specify <code>&lt;pages enableViewStateMac=&quot;false&quot;/&gt;</code> or <code>&lt;@Page EnableViewStateMac=&quot;false&quot; %&gt;</code>.</span></span> <span data-ttu-id="0c1a1-104">Le code d'authentification de message (code MAC) de l'état d'affichage est à présent appliqué à toutes les demandes avec état d'affichage intégré.</span><span class="sxs-lookup"><span data-stu-id="0c1a1-104">The view state message authentication code (MAC) is now enforced for all requests with embedded view state.</span></span> <span data-ttu-id="0c1a1-105">Seules les applications qui définissent explicitement la propriété EnableViewStateMac sur <code>false</code> sont affectées.</span><span class="sxs-lookup"><span data-stu-id="0c1a1-105">Only apps that explicitly set the EnableViewStateMac property to <code>false</code> are affected.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="0c1a1-106">Suggestion</span><span class="sxs-lookup"><span data-stu-id="0c1a1-106">Suggestion</span></span>

<span data-ttu-id="0c1a1-107">EnableViewStateMac doit être supposé être true et toutes les erreurs MAC résultantes doivent être résolues (comme expliqué dans [cette aide](https://support.microsoft.com/kb/2915218), qui contient plusieurs résolutions en fonction des spécificités de la cause des erreurs Mac).</span><span class="sxs-lookup"><span data-stu-id="0c1a1-107">EnableViewStateMac must be assumed to be true, and any resulting MAC errors must be resolved (as explained in [this guidance](https://support.microsoft.com/kb/2915218), which contains multiple resolutions depending on the specifics of what is causing MAC errors).</span></span>

| <span data-ttu-id="0c1a1-108">Name</span><span class="sxs-lookup"><span data-stu-id="0c1a1-108">Name</span></span>    | <span data-ttu-id="0c1a1-109">Valeur</span><span class="sxs-lookup"><span data-stu-id="0c1a1-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="0c1a1-110">Étendue</span><span class="sxs-lookup"><span data-stu-id="0c1a1-110">Scope</span></span>   |<span data-ttu-id="0c1a1-111">Majeure</span><span class="sxs-lookup"><span data-stu-id="0c1a1-111">Major</span></span>|
|<span data-ttu-id="0c1a1-112">Version</span><span class="sxs-lookup"><span data-stu-id="0c1a1-112">Version</span></span>|<span data-ttu-id="0c1a1-113">4.5.2</span><span class="sxs-lookup"><span data-stu-id="0c1a1-113">4.5.2</span></span>|
|<span data-ttu-id="0c1a1-114">Type</span><span class="sxs-lookup"><span data-stu-id="0c1a1-114">Type</span></span>|<span data-ttu-id="0c1a1-115">Runtime</span><span class="sxs-lookup"><span data-stu-id="0c1a1-115">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="0c1a1-116">API affectées</span><span class="sxs-lookup"><span data-stu-id="0c1a1-116">Affected APIs</span></span>

<span data-ttu-id="0c1a1-117">Non détectable via l’analyse des API.</span><span class="sxs-lookup"><span data-stu-id="0c1a1-117">Not detectable via API analysis.</span></span>

<!--

#### Affected APIs

Not detectable via API analysis.

-->
