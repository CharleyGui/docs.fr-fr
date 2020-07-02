---
ms.openlocfilehash: 80e61d4dd5b8d4754a39e95e37475fefff57fcbd
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617175"
---
### <a name="new-ambiguous-dispatcherinvoke-overloads-could-result-in-different-behavior"></a><span data-ttu-id="d81c8-101">Les nouvelles surcharges (ambiguës) Dispatcher.Invoke peuvent entraîner un comportement différent</span><span class="sxs-lookup"><span data-stu-id="d81c8-101">New (ambiguous) Dispatcher.Invoke overloads could result in different behavior</span></span>

#### <a name="details"></a><span data-ttu-id="d81c8-102">Détails</span><span class="sxs-lookup"><span data-stu-id="d81c8-102">Details</span></span>

<span data-ttu-id="d81c8-103">NET Framework 4.5 ajoute de nouvelles surcharges à <xref:System.Windows.Threading.Dispatcher.Invoke%2A?displayProperty=nameWithType> qui incluent un paramètre de type <xref:System.Action>.</span><span class="sxs-lookup"><span data-stu-id="d81c8-103">The .NET Framework 4.5 adds new overloads to <xref:System.Windows.Threading.Dispatcher.Invoke%2A?displayProperty=nameWithType> that include a parameter of type <xref:System.Action>.</span></span> <span data-ttu-id="d81c8-104">Quand le code existant est recompilé, les compilateurs peuvent résoudre les appels aux méthodes Dispatcher.Invoke dotées d’un paramètre <xref:System.Delegate> comme des appels aux méthodes Dispatcher.Invoke ayant un paramètre <xref:System.Action>.</span><span class="sxs-lookup"><span data-stu-id="d81c8-104">When existing code is recompiled, compilers may resolve calls to Dispatcher.Invoke methods that have a <xref:System.Delegate> parameter as calls to Dispatcher.Invoke methods with an <xref:System.Action> parameter.</span></span> <span data-ttu-id="d81c8-105">Si un appel à une surcharge Dispatcher.Invoke avec un paramètre <xref:System.Delegate> est résolu comme un appel à une surcharge Dispatcher.Invoke avec un paramètre <xref:System.Action>, les différences de comportement suivantes peuvent survenir :</span><span class="sxs-lookup"><span data-stu-id="d81c8-105">If a call to a Dispatcher.Invoke overload with a  <xref:System.Delegate> parameter is resolved as a call to a Dispatcher.Invoke overload with an <xref:System.Action> parameter, the following differences in behavior may occur:</span></span>

- <span data-ttu-id="d81c8-106">Si une exception se produit, les événements <xref:System.Windows.Threading.Dispatcher.UnhandledExceptionFilter> et <xref:System.Windows.Threading.Dispatcher.UnhandledException> ne sont pas déclenchés.</span><span class="sxs-lookup"><span data-stu-id="d81c8-106">If an exception occurs, the <xref:System.Windows.Threading.Dispatcher.UnhandledExceptionFilter> and <xref:System.Windows.Threading.Dispatcher.UnhandledException> events are not raised.</span></span> <span data-ttu-id="d81c8-107">À la place, les exceptions sont gérées par l'événement <xref:System.Threading.Tasks.TaskScheduler.UnobservedTaskException?displayProperty=fullName>.</span><span class="sxs-lookup"><span data-stu-id="d81c8-107">Instead, exceptions are handled by the <xref:System.Threading.Tasks.TaskScheduler.UnobservedTaskException?displayProperty=fullName> event.</span></span>
- <span data-ttu-id="d81c8-108">Les appels à certains membres, tels que <xref:System.Windows.Threading.DispatcherOperation.Result>, sont bloqués jusqu'à ce que l'opération soit terminée.</span><span class="sxs-lookup"><span data-stu-id="d81c8-108">Calls to some members, such as <xref:System.Windows.Threading.DispatcherOperation.Result>, block until the operation has completed.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="d81c8-109">Suggestion</span><span class="sxs-lookup"><span data-stu-id="d81c8-109">Suggestion</span></span>

<span data-ttu-id="d81c8-110">Pour éviter toute ambiguïté (et d’éventuelles différences au niveau de la gestion des exceptions et du blocage des comportements), le code Dispatcher.Invoke appelant peut passer un object[] vide en tant que deuxième paramètre à l’appel Invoke de manière à garantir la résolution de la surcharge de méthode .NET Framework 4.0.</span><span class="sxs-lookup"><span data-stu-id="d81c8-110">To avoid ambiguity (and potential differences in exception handling or blocking behaviors), code calling Dispatcher.Invoke can pass an empty object[] as a second parameter to the Invoke call to be sure of resolving to the .NET Framework 4.0 method overload.</span></span>

| <span data-ttu-id="d81c8-111">Nom</span><span class="sxs-lookup"><span data-stu-id="d81c8-111">Name</span></span>    | <span data-ttu-id="d81c8-112">Valeur</span><span class="sxs-lookup"><span data-stu-id="d81c8-112">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="d81c8-113">Étendue</span><span class="sxs-lookup"><span data-stu-id="d81c8-113">Scope</span></span>   | <span data-ttu-id="d81c8-114">Secondaire</span><span class="sxs-lookup"><span data-stu-id="d81c8-114">Minor</span></span>       |
| <span data-ttu-id="d81c8-115">Version</span><span class="sxs-lookup"><span data-stu-id="d81c8-115">Version</span></span> | <span data-ttu-id="d81c8-116">4,5</span><span class="sxs-lookup"><span data-stu-id="d81c8-116">4.5</span></span>         |
| <span data-ttu-id="d81c8-117">Type</span><span class="sxs-lookup"><span data-stu-id="d81c8-117">Type</span></span>    | <span data-ttu-id="d81c8-118">Reciblage</span><span class="sxs-lookup"><span data-stu-id="d81c8-118">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="d81c8-119">API affectées</span><span class="sxs-lookup"><span data-stu-id="d81c8-119">Affected APIs</span></span>

- <xref:System.Windows.Threading.Dispatcher.Invoke(System.Delegate,System.Object[])?displayProperty=nameWithType>
- <xref:System.Windows.Threading.Dispatcher.Invoke(System.Delegate,System.TimeSpan,System.Object[])?displayProperty=nameWithType>
- <xref:System.Windows.Threading.Dispatcher.Invoke(System.Delegate,System.TimeSpan,System.Windows.Threading.DispatcherPriority,System.Object[])?displayProperty=nameWithType>
- <xref:System.Windows.Threading.Dispatcher.Invoke(System.Delegate,System.Windows.Threading.DispatcherPriority,System.Object[])?displayProperty=nameWithType>
