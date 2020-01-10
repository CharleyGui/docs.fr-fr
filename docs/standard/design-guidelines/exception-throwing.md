---
title: Levée d'exceptions
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- exceptions, throwing
- explicitly throwing exceptions
- throwing exceptions, design guidelines
ms.assetid: 5388e02b-52f5-460e-a2b5-eeafe60eeebe
ms.openlocfilehash: 7d1b63e5fde57cbe37a1250d16b6bf74a2d5dc8e
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709398"
---
# <a name="exception-throwing"></a><span data-ttu-id="c62ac-102">Levée d'exceptions</span><span class="sxs-lookup"><span data-stu-id="c62ac-102">Exception Throwing</span></span>
<span data-ttu-id="c62ac-103">Les instructions de levée des exceptions décrites dans cette section nécessitent une bonne définition de la signification de l’échec de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="c62ac-103">Exception-throwing guidelines described in this section require a good definition of the meaning of execution failure.</span></span> <span data-ttu-id="c62ac-104">L’échec de l’exécution se produit chaque fois qu’un membre ne peut pas faire ce qu’il a prévu (ce que signifie le nom du membre).</span><span class="sxs-lookup"><span data-stu-id="c62ac-104">Execution failure occurs whenever a member cannot do what it was designed to do (what the member name implies).</span></span> <span data-ttu-id="c62ac-105">Par exemple, si la méthode `OpenFile` ne peut pas retourner un descripteur de fichier ouvert à l’appelant, elle est considérée comme un échec d’exécution.</span><span class="sxs-lookup"><span data-stu-id="c62ac-105">For example, if the `OpenFile` method cannot return an opened file handle to the caller, it would be considered an execution failure.</span></span>  
  
 <span data-ttu-id="c62ac-106">La plupart des développeurs se familiarisent avec l’utilisation d’exceptions pour les erreurs d’utilisation telles que la division par zéro ou les références null.</span><span class="sxs-lookup"><span data-stu-id="c62ac-106">Most developers have become comfortable with using exceptions for usage errors such as division by zero or null references.</span></span> <span data-ttu-id="c62ac-107">Dans le Framework, les exceptions sont utilisées pour toutes les conditions d’erreur, y compris les erreurs d’exécution.</span><span class="sxs-lookup"><span data-stu-id="c62ac-107">In the Framework, exceptions are used for all error conditions, including execution errors.</span></span>  
  
 <span data-ttu-id="c62ac-108">**X DO NOT** codes d’erreur.</span><span class="sxs-lookup"><span data-stu-id="c62ac-108">**X DO NOT** return error codes.</span></span>  
  
 <span data-ttu-id="c62ac-109">Les exceptions sont le principal moyen de signaler les erreurs dans les infrastructures.</span><span class="sxs-lookup"><span data-stu-id="c62ac-109">Exceptions are the primary means of reporting errors in frameworks.</span></span>  
  
 <span data-ttu-id="c62ac-110">**✓ DO** signale les échecs de l’exécution en levant des exceptions.</span><span class="sxs-lookup"><span data-stu-id="c62ac-110">**✓ DO** report execution failures by throwing exceptions.</span></span>  
  
 <span data-ttu-id="c62ac-111">**✓ CONSIDER** mettre fin au processus en appelant `System.Environment.FailFast` (fonctionnalité de .NET Framework 2.0) au lieu de lever une exception si votre code rencontre une situation où il est risqué pour obtenir de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="c62ac-111">**✓ CONSIDER** terminating the process by calling `System.Environment.FailFast` (.NET Framework 2.0 feature) instead of throwing an exception if your code encounters a situation where it is unsafe for further execution.</span></span>  
  
 <span data-ttu-id="c62ac-112">**X DO NOT** utiliser des exceptions pour le flux normal de contrôle, si possible.</span><span class="sxs-lookup"><span data-stu-id="c62ac-112">**X DO NOT** use exceptions for the normal flow of control, if possible.</span></span>  
  
 <span data-ttu-id="c62ac-113">À l’exception des défaillances système et des opérations avec des conditions de concurrence potentielles, les concepteurs d’infrastructure doivent concevoir des API pour que les utilisateurs puissent écrire du code qui ne lève pas d’exceptions.</span><span class="sxs-lookup"><span data-stu-id="c62ac-113">Except for system failures and operations with potential race conditions, framework designers should design APIs so users can write code that does not throw exceptions.</span></span> <span data-ttu-id="c62ac-114">Par exemple, vous pouvez fournir un moyen de vérifier les conditions préalables avant d’appeler un membre afin que les utilisateurs puissent écrire du code qui ne lève pas d’exceptions.</span><span class="sxs-lookup"><span data-stu-id="c62ac-114">For example, you can provide a way to check preconditions before calling a member so users can write code that does not throw exceptions.</span></span>  
  
 <span data-ttu-id="c62ac-115">Le membre utilisé pour vérifier les conditions préalables d’un autre membre est souvent appelé testeur, et le membre qui effectue réellement le travail est appelé Doer.</span><span class="sxs-lookup"><span data-stu-id="c62ac-115">The member used to check preconditions of another member is often referred to as a tester, and the member that actually does the work is called a doer.</span></span>  
  
 <span data-ttu-id="c62ac-116">Dans certains cas, le modèle testeur-Doer peut avoir une surcharge de performance inacceptable.</span><span class="sxs-lookup"><span data-stu-id="c62ac-116">There are cases when the Tester-Doer Pattern can have an unacceptable performance overhead.</span></span> <span data-ttu-id="c62ac-117">Dans ce cas, le modèle « try-parse » doit être pris en compte (pour plus d’informations, consultez [exceptions et performances](../../../docs/standard/design-guidelines/exceptions-and-performance.md) ).</span><span class="sxs-lookup"><span data-stu-id="c62ac-117">In such cases, the so-called Try-Parse Pattern should be considered (see [Exceptions and Performance](../../../docs/standard/design-guidelines/exceptions-and-performance.md) for more information).</span></span>  
  
 <span data-ttu-id="c62ac-118">**✓ CONSIDER** l’impact sur les performances de lever des exceptions.</span><span class="sxs-lookup"><span data-stu-id="c62ac-118">**✓ CONSIDER** the performance implications of throwing exceptions.</span></span> <span data-ttu-id="c62ac-119">Les taux de rejet supérieurs à 100 par seconde sont susceptibles d’avoir un impact notable sur les performances de la plupart des applications.</span><span class="sxs-lookup"><span data-stu-id="c62ac-119">Throw rates above 100 per second are likely to noticeably impact the performance of most applications.</span></span>  
  
 <span data-ttu-id="c62ac-120">**✓ DO** document toutes les exceptions levées par les membres pouvant être appelés publiquement en raison d’une violation du membre de contrat (au lieu d’une défaillance du système) et les traitent en tant que partie de votre contrat.</span><span class="sxs-lookup"><span data-stu-id="c62ac-120">**✓ DO** document all exceptions thrown by publicly callable members because of a violation of the member contract (rather than a system failure) and treat them as part of your contract.</span></span>  
  
 <span data-ttu-id="c62ac-121">Les exceptions qui font partie du contrat ne doivent pas passer d’une version à l’autre (par exemple, le type d’exception ne doit pas changer et les nouvelles exceptions ne doivent pas être ajoutées).</span><span class="sxs-lookup"><span data-stu-id="c62ac-121">Exceptions that are a part of the contract should not change from one version to the next (i.e., exception type should not change, and new exceptions should not be added).</span></span>  
  
 <span data-ttu-id="c62ac-122">**X DO NOT** ont des membres publics qui peuvent lever ou non basées sur une option.</span><span class="sxs-lookup"><span data-stu-id="c62ac-122">**X DO NOT** have public members that can either throw or not based on some option.</span></span>  
  
 <span data-ttu-id="c62ac-123">**X DO NOT** des membres publics de retournent des exceptions comme valeur de retour ou un `out` paramètre.</span><span class="sxs-lookup"><span data-stu-id="c62ac-123">**X DO NOT** have public members that return exceptions as the return value or an `out` parameter.</span></span>  
  
 <span data-ttu-id="c62ac-124">Le retour d’exceptions à partir d’API publiques au lieu de les lever est à l’encontre de nombreux avantages du rapport d’erreurs basé sur les exceptions.</span><span class="sxs-lookup"><span data-stu-id="c62ac-124">Returning exceptions from public APIs instead of throwing them defeats many of the benefits of exception-based error reporting.</span></span>  
  
 <span data-ttu-id="c62ac-125">**✓ CONSIDER** à l’aide des méthodes de générateur d’exceptions.</span><span class="sxs-lookup"><span data-stu-id="c62ac-125">**✓ CONSIDER** using exception builder methods.</span></span>  
  
 <span data-ttu-id="c62ac-126">Il est courant de lever la même exception à partir de différents emplacements.</span><span class="sxs-lookup"><span data-stu-id="c62ac-126">It is common to throw the same exception from different places.</span></span> <span data-ttu-id="c62ac-127">Pour éviter l’augmentation du code, utilisez des méthodes d’assistance qui créent des exceptions et initialisent leurs propriétés.</span><span class="sxs-lookup"><span data-stu-id="c62ac-127">To avoid code bloat, use helper methods that create exceptions and initialize their properties.</span></span>  
  
 <span data-ttu-id="c62ac-128">En outre, les membres qui lèvent des exceptions ne sont pas Inline.</span><span class="sxs-lookup"><span data-stu-id="c62ac-128">Also, members that throw exceptions are not getting inlined.</span></span> <span data-ttu-id="c62ac-129">Le déplacement de l’instruction throw dans le générateur peut permettre au membre d’être Inline.</span><span class="sxs-lookup"><span data-stu-id="c62ac-129">Moving the throw statement inside the builder might allow the member to be inlined.</span></span>  
  
 <span data-ttu-id="c62ac-130">**X DO NOT** lever des exceptions à partir de blocs de filtre d’exception.</span><span class="sxs-lookup"><span data-stu-id="c62ac-130">**X DO NOT** throw exceptions from exception filter blocks.</span></span>  
  
 <span data-ttu-id="c62ac-131">Lorsqu’un filtre d’exception lève une exception, l’exception est interceptée par le CLR et le filtre retourne la valeur false.</span><span class="sxs-lookup"><span data-stu-id="c62ac-131">When an exception filter raises an exception, the exception is caught by the CLR, and the filter returns false.</span></span> <span data-ttu-id="c62ac-132">Ce comportement ne peut pas être distingué du filtre en cours d’exécution et retourne explicitement false et est donc très difficile à déboguer.</span><span class="sxs-lookup"><span data-stu-id="c62ac-132">This behavior is indistinguishable from the filter executing and returning false explicitly and is therefore very difficult to debug.</span></span>  
  
 <span data-ttu-id="c62ac-133">**X AVOID** lever explicitement des exceptions à partir de blocs finally.</span><span class="sxs-lookup"><span data-stu-id="c62ac-133">**X AVOID** explicitly throwing exceptions from finally blocks.</span></span> <span data-ttu-id="c62ac-134">Les exceptions levées implicitement qui résultent de l’appel de méthodes qui lèvent sont acceptables.</span><span class="sxs-lookup"><span data-stu-id="c62ac-134">Implicitly thrown exceptions resulting from calling methods that throw are acceptable.</span></span>  
  
 <span data-ttu-id="c62ac-135">*Parties © 2005, 2009 Microsoft Corporation. Tous droits réservés.*</span><span class="sxs-lookup"><span data-stu-id="c62ac-135">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="c62ac-136">*Réimprimé avec l’autorisation de Pearson Education, Inc. et extrait de [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) par Krzysztof Cwalina et Brad Abrams, publié le 22 octobre 2008 par Addison-Wesley Professional dans le cadre de la série sur le développement Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="c62ac-136">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c62ac-137">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c62ac-137">See also</span></span>

- [<span data-ttu-id="c62ac-138">Règles de conception de .NET Framework</span><span class="sxs-lookup"><span data-stu-id="c62ac-138">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
- [<span data-ttu-id="c62ac-139">Instructions de conception pour les exceptions</span><span class="sxs-lookup"><span data-stu-id="c62ac-139">Design Guidelines for Exceptions</span></span>](../../../docs/standard/design-guidelines/exceptions.md)
