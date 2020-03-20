---
ms.openlocfilehash: dbe96abebdc61fae469f7727673e6fcb93cbc739
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "67803213"
---
### <a name="no-longer-able-to-set-enableviewstatemac-to-false"></a><span data-ttu-id="73e12-101">Il n’est plus possible de définir EnableViewStateMac sur false</span><span class="sxs-lookup"><span data-stu-id="73e12-101">No longer able to set EnableViewStateMac to false</span></span>

|   |   |
|---|---|
|<span data-ttu-id="73e12-102">Détails</span><span class="sxs-lookup"><span data-stu-id="73e12-102">Details</span></span>|<span data-ttu-id="73e12-103">ASP.NET ne permet plus aux développeurs de spécifier <code>&lt;pages enableViewStateMac=&quot;false&quot;/&gt;</code> ou <code>&lt;@Page EnableViewStateMac=&quot;false&quot; %&gt;</code>.</span><span class="sxs-lookup"><span data-stu-id="73e12-103">ASP.NET no longer allows developers to specify <code>&lt;pages enableViewStateMac=&quot;false&quot;/&gt;</code> or <code>&lt;@Page EnableViewStateMac=&quot;false&quot; %&gt;</code>.</span></span> <span data-ttu-id="73e12-104">Le code d'authentification de message (code MAC) de l'état d'affichage est à présent appliqué à toutes les demandes avec état d'affichage intégré.</span><span class="sxs-lookup"><span data-stu-id="73e12-104">The view state message authentication code (MAC) is now enforced for all requests with embedded view state.</span></span> <span data-ttu-id="73e12-105">Seules les applications qui définissent explicitement la propriété EnableViewStateMac sur <code>false</code> sont affectées.</span><span class="sxs-lookup"><span data-stu-id="73e12-105">Only apps that explicitly set the EnableViewStateMac property to <code>false</code> are affected.</span></span>|
|<span data-ttu-id="73e12-106">Suggestion</span><span class="sxs-lookup"><span data-stu-id="73e12-106">Suggestion</span></span>|<span data-ttu-id="73e12-107">EnableViewStateMac doit être supposé être vrai, et toutes les erreurs MAC résultant doivent être résolues (comme expliqué dans [cette directive](https://support.microsoft.com/kb/2915218), qui contient plusieurs résolutions en fonction des spécificités de ce qui cause des erreurs DE MAC).</span><span class="sxs-lookup"><span data-stu-id="73e12-107">EnableViewStateMac must be assumed to be true, and any resulting MAC errors must be resolved (as explained in [this guidance](https://support.microsoft.com/kb/2915218), which contains multiple resolutions depending on the specifics of what is causing MAC errors).</span></span>|
|<span data-ttu-id="73e12-108">Étendue</span><span class="sxs-lookup"><span data-stu-id="73e12-108">Scope</span></span>|<span data-ttu-id="73e12-109">Majeure</span><span class="sxs-lookup"><span data-stu-id="73e12-109">Major</span></span>|
|<span data-ttu-id="73e12-110">Version</span><span class="sxs-lookup"><span data-stu-id="73e12-110">Version</span></span>|<span data-ttu-id="73e12-111">4.5.2</span><span class="sxs-lookup"><span data-stu-id="73e12-111">4.5.2</span></span>|
|<span data-ttu-id="73e12-112">Type</span><span class="sxs-lookup"><span data-stu-id="73e12-112">Type</span></span>|<span data-ttu-id="73e12-113">Runtime</span><span class="sxs-lookup"><span data-stu-id="73e12-113">Runtime</span></span>|
