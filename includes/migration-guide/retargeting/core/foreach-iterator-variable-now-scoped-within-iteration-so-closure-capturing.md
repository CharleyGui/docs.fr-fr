---
ms.openlocfilehash: 9a2d6a25a8ab1b8bf65b947557802e0805a7f826
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617203"
---
### <a name="foreach-iterator-variable-is-now-scoped-within-the-iteration-so-closure-capturing-semantics-are-different-in-c5"></a><span data-ttu-id="a899f-101">La variable d’itérateur foreach est désormais délimitée au sein de l’itération. La sémantique de capture de clôture est donc différente (en C# 5)</span><span class="sxs-lookup"><span data-stu-id="a899f-101">Foreach iterator variable is now scoped within the iteration, so closure capturing semantics are different (in C#5)</span></span>

#### <a name="details"></a><span data-ttu-id="a899f-102">Détails</span><span class="sxs-lookup"><span data-stu-id="a899f-102">Details</span></span>

<span data-ttu-id="a899f-103">À compter de C# 5 (Visual Studio 2012), les variables d’itérateur `foreach` sont délimitées au sein de l’itération.</span><span class="sxs-lookup"><span data-stu-id="a899f-103">Beginning with C# 5 (Visual Studio 2012), `foreach` iterator variables are scoped within the iteration.</span></span> <span data-ttu-id="a899f-104">Cela peut provoquer des arrêts d’exécution si le code dépendait du fait que les variables ne soient pas incluses dans la clôture de `foreach`.</span><span class="sxs-lookup"><span data-stu-id="a899f-104">This can cause breaks if code was previously depending on the variables to not be included in the `foreach`'s closure.</span></span> <span data-ttu-id="a899f-105">Les conséquences de ce changement sont qu’une variable d’itérateur passée à un délégué est considérée comme la valeur qu’elle a au moment où le délégué est créé, plutôt que comme la valeur qu’elle a au moment où le délégué est appelé.</span><span class="sxs-lookup"><span data-stu-id="a899f-105">The symptom of this change is that an iterator variable passed to a delegate is treated as the value it has at the time the delegate is created, rather than the value it has at the time the delegate is invoked.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="a899f-106">Suggestion</span><span class="sxs-lookup"><span data-stu-id="a899f-106">Suggestion</span></span>

<span data-ttu-id="a899f-107">Dans l’idéal, le code doit être mis à jour pour prévoir ce nouveau comportement du compilateur.</span><span class="sxs-lookup"><span data-stu-id="a899f-107">Ideally, code should be updated to expect the new compiler behavior.</span></span> <span data-ttu-id="a899f-108">Si vous avez besoin de l’ancienne sémantique, la variable d’itérateur peut être remplacée par une autre variable placée explicitement en dehors de la portée de la boucle.</span><span class="sxs-lookup"><span data-stu-id="a899f-108">If the old semantics are required, the iterator variable can be replaced with a separate variable which is explicitly placed outside of the loop's scope.</span></span>

| <span data-ttu-id="a899f-109">Nom</span><span class="sxs-lookup"><span data-stu-id="a899f-109">Name</span></span>    | <span data-ttu-id="a899f-110">Valeur</span><span class="sxs-lookup"><span data-stu-id="a899f-110">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="a899f-111">Étendue</span><span class="sxs-lookup"><span data-stu-id="a899f-111">Scope</span></span>   | <span data-ttu-id="a899f-112">Majeure</span><span class="sxs-lookup"><span data-stu-id="a899f-112">Major</span></span>       |
| <span data-ttu-id="a899f-113">Version</span><span class="sxs-lookup"><span data-stu-id="a899f-113">Version</span></span> | <span data-ttu-id="a899f-114">4,5</span><span class="sxs-lookup"><span data-stu-id="a899f-114">4.5</span></span>         |
| <span data-ttu-id="a899f-115">Type</span><span class="sxs-lookup"><span data-stu-id="a899f-115">Type</span></span>    | <span data-ttu-id="a899f-116">Reciblage</span><span class="sxs-lookup"><span data-stu-id="a899f-116">Retargeting</span></span> |
