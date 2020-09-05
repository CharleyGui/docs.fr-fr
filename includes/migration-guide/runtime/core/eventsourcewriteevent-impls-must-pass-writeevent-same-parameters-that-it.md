---
ms.openlocfilehash: 99a7fa0fcfce6d490a182f85709b5dd0e0e8c86f
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496600"
---
### <a name="eventsourcewriteevent-impls-must-pass-writeevent-the-same-parameters-that-it-received-plus-id"></a><span data-ttu-id="77f15-101">Les implémentations d’EventSource.WriteEvent doivent passer à WriteEvent les mêmes paramètres qu’il a reçus (plus l’ID)</span><span class="sxs-lookup"><span data-stu-id="77f15-101">EventSource.WriteEvent impls must pass WriteEvent the same parameters that it received (plus ID)</span></span>

#### <a name="details"></a><span data-ttu-id="77f15-102">Détails</span><span class="sxs-lookup"><span data-stu-id="77f15-102">Details</span></span>

<span data-ttu-id="77f15-103">Le runtime applique à présent le contrat qui stipule ce qui suit : une classe dérivée de <xref:System.Diagnostics.Tracing.EventSource?displayProperty=fullName> qui définit une méthode d'événement ETW doit appeler la méthode <code>EventSource.WriteEvent</code> de la classe de base avec l'ID d'événement suivi des mêmes arguments que ceux passés à la méthode d'événement ETW.</span><span class="sxs-lookup"><span data-stu-id="77f15-103">The runtime now enforces the contract that specifies the following: A class derived from <xref:System.Diagnostics.Tracing.EventSource?displayProperty=fullName> that defines an ETW event method must call the base class <code>EventSource.WriteEvent</code> method with the event ID followed by the same arguments that the ETW event method was passed.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="77f15-104">Suggestion</span><span class="sxs-lookup"><span data-stu-id="77f15-104">Suggestion</span></span>

<span data-ttu-id="77f15-105">Une exception <xref:System.IndexOutOfRangeException?displayProperty=fullName> est levée si un <xref:System.Diagnostics.Tracing.EventListener?displayProperty=fullName> lit des données <xref:System.Diagnostics.Tracing.EventSource?displayProperty=fullName> dans le processus pour une source d'événement qui ne respecte pas ce contrat.</span><span class="sxs-lookup"><span data-stu-id="77f15-105">An <xref:System.IndexOutOfRangeException?displayProperty=fullName> exception is thrown if an <xref:System.Diagnostics.Tracing.EventListener?displayProperty=fullName> reads <xref:System.Diagnostics.Tracing.EventSource?displayProperty=fullName> data in process for an event source that violates this contract.</span></span>

| <span data-ttu-id="77f15-106">Name</span><span class="sxs-lookup"><span data-stu-id="77f15-106">Name</span></span>    | <span data-ttu-id="77f15-107">Valeur</span><span class="sxs-lookup"><span data-stu-id="77f15-107">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="77f15-108">Étendue</span><span class="sxs-lookup"><span data-stu-id="77f15-108">Scope</span></span>   |<span data-ttu-id="77f15-109">Secondaire</span><span class="sxs-lookup"><span data-stu-id="77f15-109">Minor</span></span>|
|<span data-ttu-id="77f15-110">Version</span><span class="sxs-lookup"><span data-stu-id="77f15-110">Version</span></span>|<span data-ttu-id="77f15-111">4.5.1</span><span class="sxs-lookup"><span data-stu-id="77f15-111">4.5.1</span></span>|
|<span data-ttu-id="77f15-112">Type</span><span class="sxs-lookup"><span data-stu-id="77f15-112">Type</span></span>|<span data-ttu-id="77f15-113">Runtime</span><span class="sxs-lookup"><span data-stu-id="77f15-113">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="77f15-114">API affectées</span><span class="sxs-lookup"><span data-stu-id="77f15-114">Affected APIs</span></span>

<span data-ttu-id="77f15-115">Non détectable via l’analyse des API.</span><span class="sxs-lookup"><span data-stu-id="77f15-115">Not detectable via API analysis.</span></span>

<!--

#### Affected APIs

Not detectable via API analysis.

-->
