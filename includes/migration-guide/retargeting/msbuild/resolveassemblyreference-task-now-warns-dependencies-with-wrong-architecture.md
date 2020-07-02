---
ms.openlocfilehash: 4d410811095786b33580d25f6c6eab3ac2f27148
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85616054"
---
### <a name="resolveassemblyreference-task-now-warns-of-dependencies-with-the-wrong-architecture"></a><span data-ttu-id="30e65-101">La tâche ResolveAssemblyReference avertit désormais en cas de dépendances avec une architecture incorrecte</span><span class="sxs-lookup"><span data-stu-id="30e65-101">ResolveAssemblyReference task now warns of dependencies with the wrong architecture</span></span>

#### <a name="details"></a><span data-ttu-id="30e65-102">Détails</span><span class="sxs-lookup"><span data-stu-id="30e65-102">Details</span></span>

<span data-ttu-id="30e65-103">La tâche émet un avertissement, MSB3270, qui indique qu’une référence ou l’une de ses dépendances ne correspond pas à l’architecture de l’application.</span><span class="sxs-lookup"><span data-stu-id="30e65-103">The task emits a warning, MSB3270, which indicates that a reference or any of its dependencies does not match the app's architecture.</span></span> <span data-ttu-id="30e65-104">Cette situation se produit, par exemple, si une application qui a été compilée avec l'option `AnyCPU` inclut une référence x86.</span><span class="sxs-lookup"><span data-stu-id="30e65-104">For example, this occurs if an app that was compiled with the `AnyCPU` option includes an x86 reference.</span></span> <span data-ttu-id="30e65-105">Ainsi, l'application peut échouer au moment de l'exécution (si l'application est déployée en tant que processus x64 dans notre exemple).</span><span class="sxs-lookup"><span data-stu-id="30e65-105">Such a scenario could result in an app failure at run time (in this case, if the app is deployed as an x64 process).</span></span>

#### <a name="suggestion"></a><span data-ttu-id="30e65-106">Suggestion</span><span class="sxs-lookup"><span data-stu-id="30e65-106">Suggestion</span></span>

<span data-ttu-id="30e65-107">Deux domaines sont impactés :</span><span class="sxs-lookup"><span data-stu-id="30e65-107">There are two areas of impact:</span></span>

- <span data-ttu-id="30e65-108">La recompilation génère des avertissements qui n'étaient pas apparus quand l'application avait été compilée sous une version antérieure de MSBuild.</span><span class="sxs-lookup"><span data-stu-id="30e65-108">Recompilation generates warnings that did not appear when the app was compiled under a previous version of MSBuild.</span></span> <span data-ttu-id="30e65-109">En revanche, étant donné que l'avertissement identifie une source potentielle d'échec du runtime, vous devez l'examiner et le traiter.</span><span class="sxs-lookup"><span data-stu-id="30e65-109">However, because the warning identifies a possible source of runtime failure, it should be investigated and addressed.</span></span>
- <span data-ttu-id="30e65-110">Si les avertissements sont considérés comme des erreurs, la compilation de l'application échouera.</span><span class="sxs-lookup"><span data-stu-id="30e65-110">If warnings are treated as errors, the app will fail to compile.</span></span>

| <span data-ttu-id="30e65-111">Nom</span><span class="sxs-lookup"><span data-stu-id="30e65-111">Name</span></span>    | <span data-ttu-id="30e65-112">Valeur</span><span class="sxs-lookup"><span data-stu-id="30e65-112">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="30e65-113">Étendue</span><span class="sxs-lookup"><span data-stu-id="30e65-113">Scope</span></span>   | <span data-ttu-id="30e65-114">Secondaire</span><span class="sxs-lookup"><span data-stu-id="30e65-114">Minor</span></span>       |
| <span data-ttu-id="30e65-115">Version</span><span class="sxs-lookup"><span data-stu-id="30e65-115">Version</span></span> | <span data-ttu-id="30e65-116">4.5.1</span><span class="sxs-lookup"><span data-stu-id="30e65-116">4.5.1</span></span>       |
| <span data-ttu-id="30e65-117">Type</span><span class="sxs-lookup"><span data-stu-id="30e65-117">Type</span></span>    | <span data-ttu-id="30e65-118">Reciblage</span><span class="sxs-lookup"><span data-stu-id="30e65-118">Retargeting</span></span> |
