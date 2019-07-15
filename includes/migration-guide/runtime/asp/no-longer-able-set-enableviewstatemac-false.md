---
ms.openlocfilehash: 78f4d533f1efdc8d43a9ab96508b84a77e3260bc
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/11/2019
ms.locfileid: "67803213"
---
### <a name="no-longer-able-to-set-enableviewstatemac-to-false"></a><span data-ttu-id="38930-101">Il n’est plus possible de définir EnableViewStateMac sur false</span><span class="sxs-lookup"><span data-stu-id="38930-101">No longer able to set EnableViewStateMac to false</span></span>

|   |   |
|---|---|
|<span data-ttu-id="38930-102">Détails</span><span class="sxs-lookup"><span data-stu-id="38930-102">Details</span></span>|<span data-ttu-id="38930-103">ASP.NET ne permet plus aux développeurs de spécifier <code>&lt;pages enableViewStateMac=&quot;false&quot;/&gt;</code> ou <code>&lt;@Page EnableViewStateMac=&quot;false&quot; %&gt;</code>.</span><span class="sxs-lookup"><span data-stu-id="38930-103">ASP.NET no longer allows developers to specify <code>&lt;pages enableViewStateMac=&quot;false&quot;/&gt;</code> or <code>&lt;@Page EnableViewStateMac=&quot;false&quot; %&gt;</code>.</span></span> <span data-ttu-id="38930-104">Le code d'authentification de message (code MAC) de l'état d'affichage est à présent appliqué à toutes les demandes avec état d'affichage intégré.</span><span class="sxs-lookup"><span data-stu-id="38930-104">The view state message authentication code (MAC) is now enforced for all requests with embedded view state.</span></span> <span data-ttu-id="38930-105">Seules les applications qui définissent explicitement la propriété EnableViewStateMac sur <code>false</code> sont affectées.</span><span class="sxs-lookup"><span data-stu-id="38930-105">Only apps that explicitly set the EnableViewStateMac property to <code>false</code> are affected.</span></span>|
|<span data-ttu-id="38930-106">Suggestion</span><span class="sxs-lookup"><span data-stu-id="38930-106">Suggestion</span></span>|<span data-ttu-id="38930-107">Vous devez supposer que la propriété EnableViewStateMac a la valeur true. Les erreurs MAC résultantes doivent être résolues (comme expliqué dans [cette aide](https://support.microsoft.com/kb/2915218), qui contient plusieurs résolutions en fonction de l’origine des erreurs MAC).</span><span class="sxs-lookup"><span data-stu-id="38930-107">EnableViewStateMac must be assumed to be true, and any resulting MAC errors must be resolved (as explained in [this guidance](https://support.microsoft.com/kb/2915218), which contains multiple resolutions depending on the specifics of what is causing MAC errors).</span></span>|
|<span data-ttu-id="38930-108">Portée</span><span class="sxs-lookup"><span data-stu-id="38930-108">Scope</span></span>|<span data-ttu-id="38930-109">Majeur</span><span class="sxs-lookup"><span data-stu-id="38930-109">Major</span></span>|
|<span data-ttu-id="38930-110">Version</span><span class="sxs-lookup"><span data-stu-id="38930-110">Version</span></span>|<span data-ttu-id="38930-111">4.5.2</span><span class="sxs-lookup"><span data-stu-id="38930-111">4.5.2</span></span>|
|<span data-ttu-id="38930-112">Type</span><span class="sxs-lookup"><span data-stu-id="38930-112">Type</span></span>|<span data-ttu-id="38930-113">Runtime</span><span class="sxs-lookup"><span data-stu-id="38930-113">Runtime</span></span>|

