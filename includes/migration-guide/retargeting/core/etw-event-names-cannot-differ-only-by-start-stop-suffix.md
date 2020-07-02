---
ms.openlocfilehash: 0e25d5d9b545e5cb400cbf701fb13da572fadf10
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614454"
---
### <a name="etw-event-names-cannot-differ-only-by-a-start-or-stop-suffix"></a><span data-ttu-id="32a9b-101">Les noms d’événements ETW ne peuvent pas différer uniquement par le suffixe « Start » ou « Stop »</span><span class="sxs-lookup"><span data-stu-id="32a9b-101">ETW event names cannot differ only by a "Start" or "Stop" suffix</span></span>

#### <a name="details"></a><span data-ttu-id="32a9b-102">Détails</span><span class="sxs-lookup"><span data-stu-id="32a9b-102">Details</span></span>

<span data-ttu-id="32a9b-103">Dans les .NET Framework 4,6 et 4.6.1, le runtime lève une exception <xref:System.ArgumentException> lorsque deux noms d’événements suivi d’v nements pour Windows (ETW) diffèrent uniquement par un suffixe « Start » ou « stop » (comme lorsqu’un événement est nommé `LogUser` et un autre est nommé `LogUserStart` ).</span><span class="sxs-lookup"><span data-stu-id="32a9b-103">In the .NET Framework 4.6 and 4.6.1, the runtime throws an <xref:System.ArgumentException> when two Event Tracing for Windows (ETW) event names differ only by a "Start" or "Stop" suffix (as when one event is named `LogUser` and another is named `LogUserStart`).</span></span> <span data-ttu-id="32a9b-104">Dans ce cas, le runtime ne peut pas construire la source d’événements, qui ne peut pas émettre de journalisation.</span><span class="sxs-lookup"><span data-stu-id="32a9b-104">In this case, the runtime cannot construct the event source, which cannot emit any logging.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="32a9b-105">Suggestion</span><span class="sxs-lookup"><span data-stu-id="32a9b-105">Suggestion</span></span>

<span data-ttu-id="32a9b-106">Pour éviter l’exception, assurez-vous que deux noms d’événements ne diffèrent que par un suffixe « Start » ou « stop ». Cette exigence est supprimée à partir de la .NET Framework 4.6.2 ; le runtime peut lever l’ambiguïté des noms d’événements qui diffèrent uniquement par le suffixe « Start » et « Stop ».</span><span class="sxs-lookup"><span data-stu-id="32a9b-106">To prevent the exception, ensure that no two event names differ only by a "Start" or "Stop" suffix.This requirement is removed starting with the .NET Framework 4.6.2; the runtime can disambiguate event names that differ only by the "Start" and "Stop" suffix.</span></span>

| <span data-ttu-id="32a9b-107">Nom</span><span class="sxs-lookup"><span data-stu-id="32a9b-107">Name</span></span>    | <span data-ttu-id="32a9b-108">Valeur</span><span class="sxs-lookup"><span data-stu-id="32a9b-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="32a9b-109">Étendue</span><span class="sxs-lookup"><span data-stu-id="32a9b-109">Scope</span></span>   | <span data-ttu-id="32a9b-110">Edge</span><span class="sxs-lookup"><span data-stu-id="32a9b-110">Edge</span></span>        |
| <span data-ttu-id="32a9b-111">Version</span><span class="sxs-lookup"><span data-stu-id="32a9b-111">Version</span></span> | <span data-ttu-id="32a9b-112">4.6</span><span class="sxs-lookup"><span data-stu-id="32a9b-112">4.6</span></span>         |
| <span data-ttu-id="32a9b-113">Type</span><span class="sxs-lookup"><span data-stu-id="32a9b-113">Type</span></span>    | <span data-ttu-id="32a9b-114">Reciblage</span><span class="sxs-lookup"><span data-stu-id="32a9b-114">Retargeting</span></span> |
