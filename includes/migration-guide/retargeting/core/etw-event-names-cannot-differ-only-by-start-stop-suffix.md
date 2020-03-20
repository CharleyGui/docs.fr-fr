---
ms.openlocfilehash: 71c81cf188fa4c2300661f10eb87e7ae00e031f6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "67804424"
---
### <a name="etw-event-names-cannot-differ-only-by-a-start-or-stop-suffix"></a><span data-ttu-id="c178c-101">Les noms d’événements ETW ne peuvent pas différer uniquement par le suffixe « Start » ou « Stop »</span><span class="sxs-lookup"><span data-stu-id="c178c-101">ETW event names cannot differ only by a "Start" or "Stop" suffix</span></span>

|   |   |
|---|---|
|<span data-ttu-id="c178c-102">Détails</span><span class="sxs-lookup"><span data-stu-id="c178c-102">Details</span></span>|<span data-ttu-id="c178c-103">Dans .NET Framework 4.6 et 4.6.1, le runtime lève un <xref:System.ArgumentException> quand deux noms d’événements ETW (Event Tracing for Windows) diffèrent uniquement par le suffixe &quot;Start&quot; ou &quot;Stop&quot; (comme quand un événement est nommé <code>LogUser</code> et un autre <code>LogUserStart</code>).</span><span class="sxs-lookup"><span data-stu-id="c178c-103">In the .NET Framework 4.6 and 4.6.1, the runtime throws an <xref:System.ArgumentException> when two Event Tracing for Windows (ETW) event names differ only by a &quot;Start&quot; or &quot;Stop&quot; suffix (as when one event is named <code>LogUser</code> and another is named <code>LogUserStart</code>).</span></span> <span data-ttu-id="c178c-104">Dans ce cas, le runtime ne peut pas construire la source d’événements, qui ne peut pas émettre de journalisation.</span><span class="sxs-lookup"><span data-stu-id="c178c-104">In this case, the runtime cannot construct the event source, which cannot emit any logging.</span></span>|
|<span data-ttu-id="c178c-105">Suggestion</span><span class="sxs-lookup"><span data-stu-id="c178c-105">Suggestion</span></span>|<span data-ttu-id="c178c-106">Pour empêcher cette exception, vérifiez qu’aucun des deux noms d’événement ne diffère uniquement par un suffixe &quot;Start&quot; ou &quot;Stop&quot;. À compter de .NET Framework 4.6.2, cette vérification n’est plus nécessaire. Le runtime est désormais capable de lever l’ambiguïté des noms d’événements qui diffèrent uniquement par le suffixe &quot;Start&quot; et &quot;Stop&quot;.</span><span class="sxs-lookup"><span data-stu-id="c178c-106">To prevent the exception, ensure that no two event names differ only by a &quot;Start&quot; or &quot;Stop&quot; suffix.This requirement is removed starting with the .NET Framework 4.6.2; the runtime can disambiguate event names that differ only by the &quot;Start&quot; and &quot;Stop&quot; suffix.</span></span>|
|<span data-ttu-id="c178c-107">Étendue</span><span class="sxs-lookup"><span data-stu-id="c178c-107">Scope</span></span>|<span data-ttu-id="c178c-108">Edge</span><span class="sxs-lookup"><span data-stu-id="c178c-108">Edge</span></span>|
|<span data-ttu-id="c178c-109">Version</span><span class="sxs-lookup"><span data-stu-id="c178c-109">Version</span></span>|<span data-ttu-id="c178c-110">4.6</span><span class="sxs-lookup"><span data-stu-id="c178c-110">4.6</span></span>|
|<span data-ttu-id="c178c-111">Type</span><span class="sxs-lookup"><span data-stu-id="c178c-111">Type</span></span>|<span data-ttu-id="c178c-112">Reciblage</span><span class="sxs-lookup"><span data-stu-id="c178c-112">Retargeting</span></span>|
