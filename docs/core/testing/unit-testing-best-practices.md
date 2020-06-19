---
title: Bonnes pratiques pour l’écriture de tests unitaires
description: Découvrez les bonnes pratiques pour écrire des tests unitaires qui améliorent la qualité du code et la résilience pour les projets .NET Core et .NET Standard.
author: jpreese
ms.author: wiwagn
ms.date: 07/28/2018
ms.openlocfilehash: 9115ff69b269e3723820fd8505d1a9f8ca278d12
ms.sourcegitcommit: 45c8eed045779b70a47b23169897459d0323dc89
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/18/2020
ms.locfileid: "84989378"
---
# <a name="unit-testing-best-practices-with-net-core-and-net-standard"></a><span data-ttu-id="d324f-103">Meilleures pratiques pour les tests unitaires avec .NET Core et .NET Standard</span><span class="sxs-lookup"><span data-stu-id="d324f-103">Unit testing best practices with .NET Core and .NET Standard</span></span>

<span data-ttu-id="d324f-104">Il existe de nombreux avantages à écrire des tests unitaires. Ils facilitent la régression, fournissent de la documentation et simplifient la conception.</span><span class="sxs-lookup"><span data-stu-id="d324f-104">There are numerous benefits to writing unit tests; they help with regression, provide documentation, and facilitate good design.</span></span> <span data-ttu-id="d324f-105">Toutefois, les tests unitaires difficiles à lire et fragiles peuvent faire des ravages dans votre code base.</span><span class="sxs-lookup"><span data-stu-id="d324f-105">However, hard to read and brittle unit tests can wreak havoc on your code base.</span></span> <span data-ttu-id="d324f-106">Cet article décrit certaines meilleures pratiques concernant la conception de tests unitaires pour vos projets .NET Core et .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="d324f-106">This article describes some best practices regarding unit test design for your .NET Core and .NET Standard projects.</span></span>

<span data-ttu-id="d324f-107">Dans ce guide, vous allez découvrir certaines bonnes pratiques à suivre pour écrire des tests unitaires résilients et faciles à comprendre.</span><span class="sxs-lookup"><span data-stu-id="d324f-107">In this guide, you'll learn some best practices when writing unit tests to keep your tests resilient and easy to understand.</span></span>

<span data-ttu-id="d324f-108">Par [John Reese](https://reese.dev) avec des remerciements particuliers à [Roy Osherove](https://osherove.com/)</span><span class="sxs-lookup"><span data-stu-id="d324f-108">By [John Reese](https://reese.dev) with special thanks to [Roy Osherove](https://osherove.com/)</span></span>

## <a name="why-unit-test"></a><span data-ttu-id="d324f-109">Pourquoi un test unitaire ?</span><span class="sxs-lookup"><span data-stu-id="d324f-109">Why unit test?</span></span>

### <a name="less-time-performing-functional-tests"></a><span data-ttu-id="d324f-110">Moins de temps pour effectuer des tests fonctionnels</span><span class="sxs-lookup"><span data-stu-id="d324f-110">Less time performing functional tests</span></span>
<span data-ttu-id="d324f-111">Les tests fonctionnels sont coûteux.</span><span class="sxs-lookup"><span data-stu-id="d324f-111">Functional tests are expensive.</span></span> <span data-ttu-id="d324f-112">Ils impliquent généralement d’ouvrir l’application et d’effectuer une série d’étapes que vous (ou quelqu’un d’autre) devez suivre pour valider le comportement attendu.</span><span class="sxs-lookup"><span data-stu-id="d324f-112">They typically involve opening up the application and performing a series of steps that you (or someone else), must follow in order to validate the expected behavior.</span></span> <span data-ttu-id="d324f-113">Dans la mesure où le testeur ne connaît pas toujours ces étapes, il doit contacter une personne plus compétente dans le domaine concerné pour effectuer le test.</span><span class="sxs-lookup"><span data-stu-id="d324f-113">These steps may not always be known to the tester, which means they will have to reach out to someone more knowledgeable in the area in order to carry out the test.</span></span> <span data-ttu-id="d324f-114">Le test lui-même peut prendre quelques secondes pour des changements mineurs, ou quelques minutes pour des changements plus importants.</span><span class="sxs-lookup"><span data-stu-id="d324f-114">Testing itself could take seconds for trivial changes, or minutes for larger changes.</span></span> <span data-ttu-id="d324f-115">Enfin, ce processus doit être répété pour chaque changement apporté au système.</span><span class="sxs-lookup"><span data-stu-id="d324f-115">Lastly, this process must be repeated for every change that you make in the system.</span></span>

<span data-ttu-id="d324f-116">Les tests unitaires, en revanche, prennent quelques millisecondes. Vous pouvez les exécuter en appuyant sur un bouton sans nécessairement connaître le système dans son ensemble.</span><span class="sxs-lookup"><span data-stu-id="d324f-116">Unit tests, on the other hand, take milliseconds, can be run at the press of a button and do not necessarily require any knowledge of the system at large.</span></span> <span data-ttu-id="d324f-117">La réussite ou non du test dépend du programme d’exécution de tests et non de la personne qui effectue le test.</span><span class="sxs-lookup"><span data-stu-id="d324f-117">Whether or not the test passes or fails is up to the test runner, not the individual.</span></span>

### <a name="protection-against-regression"></a><span data-ttu-id="d324f-118">Protection contre la régression</span><span class="sxs-lookup"><span data-stu-id="d324f-118">Protection against regression</span></span>
<span data-ttu-id="d324f-119">Les défauts de régression sont des défauts introduits quand un changement est apporté à l’application.</span><span class="sxs-lookup"><span data-stu-id="d324f-119">Regression defects are defects that are introduced when a change is made to the application.</span></span> <span data-ttu-id="d324f-120">Il est courant pour les testeurs de tester non seulement les nouvelles fonctionnalités, mais également les fonctionnalités antérieures afin de vérifier que ces dernières fonctionnent toujours comme prévu.</span><span class="sxs-lookup"><span data-stu-id="d324f-120">It is common for testers to not only test their new feature but also features that existed beforehand in order to verify that previously implemented features still function as expected.</span></span>

<span data-ttu-id="d324f-121">Avec les tests unitaires, vous pouvez réexécuter l’intégralité de votre suite de tests après chaque build ou même après avoir changé une ligne de code.</span><span class="sxs-lookup"><span data-stu-id="d324f-121">With unit testing, it's possible to rerun your entire suite of tests after every build or even after you change a line of code.</span></span> <span data-ttu-id="d324f-122">Ainsi, vous avez l’assurance que votre nouveau code ne perturbe pas les fonctionnalités existantes.</span><span class="sxs-lookup"><span data-stu-id="d324f-122">Giving you confidence that your new code does not break existing functionality.</span></span>

### <a name="executable-documentation"></a><span data-ttu-id="d324f-123">Documentation exécutable</span><span class="sxs-lookup"><span data-stu-id="d324f-123">Executable documentation</span></span>
<span data-ttu-id="d324f-124">Il n’est pas toujours évident de déterminer ce que fait une méthode particulière, ou comment elle se comporte en fonction d’une entrée spécifique.</span><span class="sxs-lookup"><span data-stu-id="d324f-124">It may not always be obvious what a particular method does or how it behaves given a certain input.</span></span> <span data-ttu-id="d324f-125">Vous pouvez vous demander : comment se comporte cette méthode si je lui passe une chaîne vide ?</span><span class="sxs-lookup"><span data-stu-id="d324f-125">You may ask yourself: How does this method behave if I pass it a blank string?</span></span> <span data-ttu-id="d324f-126">Null ?</span><span class="sxs-lookup"><span data-stu-id="d324f-126">Null?</span></span>

<span data-ttu-id="d324f-127">Quand vous avez une suite de tests unitaires correctement nommés, chaque test doit pouvoir expliquer clairement la sortie attendue pour une entrée donnée.</span><span class="sxs-lookup"><span data-stu-id="d324f-127">When you have a suite of well-named unit tests, each test should be able to clearly explain the expected output for a given input.</span></span> <span data-ttu-id="d324f-128">De plus, il doit pouvoir vérifier son bon fonctionnement.</span><span class="sxs-lookup"><span data-stu-id="d324f-128">In addition, it should be able to verify that it actually works.</span></span>

### <a name="less-coupled-code"></a><span data-ttu-id="d324f-129">Code moins couplé</span><span class="sxs-lookup"><span data-stu-id="d324f-129">Less coupled code</span></span>
<span data-ttu-id="d324f-130">Quand le code est fortement couplé, il peut être difficile d’effectuer des tests unitaires.</span><span class="sxs-lookup"><span data-stu-id="d324f-130">When code is tightly coupled, it can be difficult to unit test.</span></span> <span data-ttu-id="d324f-131">Si vous ne créez pas de tests unitaires pour le code que vous écrivez, le couplage peut être moins apparent.</span><span class="sxs-lookup"><span data-stu-id="d324f-131">Without creating unit tests for the code that you're writing, coupling may be less apparent.</span></span>

<span data-ttu-id="d324f-132">L’écriture de tests pour votre code permet de le découpler de manière naturelle. Sinon, il est plus difficile à tester.</span><span class="sxs-lookup"><span data-stu-id="d324f-132">Writing tests for your code will naturally decouple your code, because it would be more difficult to test otherwise.</span></span>

## <a name="characteristics-of-a-good-unit-test"></a><span data-ttu-id="d324f-133">Caractéristiques d’un bon test unitaire</span><span class="sxs-lookup"><span data-stu-id="d324f-133">Characteristics of a good unit test</span></span>

- <span data-ttu-id="d324f-134">**Rapidement**.</span><span class="sxs-lookup"><span data-stu-id="d324f-134">**Fast**.</span></span> <span data-ttu-id="d324f-135">Il n’est pas rare pour des projets matures de comporter des milliers de tests unitaires.</span><span class="sxs-lookup"><span data-stu-id="d324f-135">It is not uncommon for mature projects to have thousands of unit tests.</span></span> <span data-ttu-id="d324f-136">Les tests unitaires doivent durer très peu de temps.</span><span class="sxs-lookup"><span data-stu-id="d324f-136">Unit tests should take very little time to run.</span></span> <span data-ttu-id="d324f-137">Millisecondes.</span><span class="sxs-lookup"><span data-stu-id="d324f-137">Milliseconds.</span></span>
- <span data-ttu-id="d324f-138">**Isolé**.</span><span class="sxs-lookup"><span data-stu-id="d324f-138">**Isolated**.</span></span> <span data-ttu-id="d324f-139">Les tests unitaires sont autonomes et peuvent être exécutés de manière isolée. Ils ne dépendent d’aucun facteur externe, par exemple un système de fichiers ou une base de données.</span><span class="sxs-lookup"><span data-stu-id="d324f-139">Unit tests are standalone, can be run in isolation, and have no dependencies on any outside factors such as a file system or database.</span></span>
- <span data-ttu-id="d324f-140">**Renouvelable**.</span><span class="sxs-lookup"><span data-stu-id="d324f-140">**Repeatable**.</span></span> <span data-ttu-id="d324f-141">L’exécution d’un test unitaire doit être cohérente avec ses résultats. En d’autres termes, il retourne toujours le même résultat si vous ne changez rien entre les exécutions.</span><span class="sxs-lookup"><span data-stu-id="d324f-141">Running a unit test should be consistent with its results, that is, it always returns the same result if you do not change anything in between runs.</span></span>
- <span data-ttu-id="d324f-142">**Autovérification**.</span><span class="sxs-lookup"><span data-stu-id="d324f-142">**Self-Checking**.</span></span> <span data-ttu-id="d324f-143">Le test doit pouvoir détecter automatiquement son état de réussite ou d’échec sans aucune interaction humaine.</span><span class="sxs-lookup"><span data-stu-id="d324f-143">The test should be able to automatically detect if it passed or failed without any human interaction.</span></span>
- <span data-ttu-id="d324f-144">**Délai approprié**.</span><span class="sxs-lookup"><span data-stu-id="d324f-144">**Timely**.</span></span> <span data-ttu-id="d324f-145">Écrire un test unitaire ne doit pas prendre un temps disproportionné par rapport au code testé.</span><span class="sxs-lookup"><span data-stu-id="d324f-145">A unit test should not take a disproportionately long time to write compared to the code being tested.</span></span> <span data-ttu-id="d324f-146">Si vous trouvez que le test du code prend beaucoup de temps par rapport à son écriture, optez pour une conception plus facile à tester.</span><span class="sxs-lookup"><span data-stu-id="d324f-146">If you find testing the code taking a large amount of time compared to writing the code, consider a design that is more testable.</span></span>

## <a name="code-coverage"></a><span data-ttu-id="d324f-147">Couverture du code</span><span class="sxs-lookup"><span data-stu-id="d324f-147">Code coverage</span></span>

<span data-ttu-id="d324f-148">Un pourcentage élevé de couverture du code est souvent associé à une qualité de code supérieure.</span><span class="sxs-lookup"><span data-stu-id="d324f-148">A high code coverage percentage is often associated with a higher quality of code.</span></span> <span data-ttu-id="d324f-149">Toutefois, la mesure elle-même *ne peut pas* déterminer la qualité du code.</span><span class="sxs-lookup"><span data-stu-id="d324f-149">However, the measurement itself *cannot* determine the quality of code.</span></span> <span data-ttu-id="d324f-150">La définition d’un objectif de pourcentage de couverture du code trop ambitieux peut être contre-productive.</span><span class="sxs-lookup"><span data-stu-id="d324f-150">Setting an overly ambitious code coverage percentage goal can be counterproductive.</span></span> <span data-ttu-id="d324f-151">Imaginez un projet complexe avec des milliers de branches conditionnelles et imaginez que vous définissez un objectif de couverture du code de 95%.</span><span class="sxs-lookup"><span data-stu-id="d324f-151">Imagine a complex project with thousands of conditional branches, and imagine that you set a goal of 95% code coverage.</span></span> <span data-ttu-id="d324f-152">Actuellement, le projet gère la couverture du code de 90%.</span><span class="sxs-lookup"><span data-stu-id="d324f-152">Currently the project maintains 90% code coverage.</span></span> <span data-ttu-id="d324f-153">La durée nécessaire à la prise en compte de tous les cas de périphérie dans les 5% restants peut être une entreprise importante, et la proposition de valeur est rapidement réduite.</span><span class="sxs-lookup"><span data-stu-id="d324f-153">The amount of time it takes to account for all of the edge cases in the remaining 5% could be a massive undertaking, and the value proposition quickly diminishes.</span></span>

<span data-ttu-id="d324f-154">Un pourcentage élevé de couverture du code n’est pas un indicateur de réussite et n’implique pas non plus la haute qualité du code.</span><span class="sxs-lookup"><span data-stu-id="d324f-154">A high code coverage percentage is not an indicator of success, nor does it imply high code quality.</span></span> <span data-ttu-id="d324f-155">Jusst représente la quantité de code qui est couverte par les tests unitaires.</span><span class="sxs-lookup"><span data-stu-id="d324f-155">It jusst represents the amount of code that is covered by unit tests.</span></span> <span data-ttu-id="d324f-156">Pour plus d’informations, consultez [couverture du code de test unitaire](unit-testing-code-coverage.md).</span><span class="sxs-lookup"><span data-stu-id="d324f-156">For more information, see [unit testing code coverage](unit-testing-code-coverage.md).</span></span>

## <a name="lets-speak-the-same-language"></a><span data-ttu-id="d324f-157">Parlons la même langue</span><span class="sxs-lookup"><span data-stu-id="d324f-157">Let's speak the same language</span></span>
<span data-ttu-id="d324f-158">Le terme *mock* (élément fictif) est malheureusement utilisé à très mauvais escient quand il s’agit de tests.</span><span class="sxs-lookup"><span data-stu-id="d324f-158">The term *mock* is unfortunately very misused when talking about testing.</span></span> <span data-ttu-id="d324f-159">Voici une définition des types les plus courants de *fakes* (éléments fictifs) pour l’écriture de tests unitaires :</span><span class="sxs-lookup"><span data-stu-id="d324f-159">The following defines the most common types of *fakes* when writing unit tests:</span></span>

<span data-ttu-id="d324f-160">*Fake* - Il s’agit d’un terme générique qui permet de décrire un stub ou un mock (objet fictif).</span><span class="sxs-lookup"><span data-stu-id="d324f-160">*Fake* - A fake is a generic term which can be used to describe either a stub or a mock object.</span></span> <span data-ttu-id="d324f-161">Seul le contexte permet de déterminer s’il s’agit d’un stub ou d’un mock (objet fictif).</span><span class="sxs-lookup"><span data-stu-id="d324f-161">Whether it is a stub or a mock depends on the context in which it's used.</span></span> <span data-ttu-id="d324f-162">En d’autres termes, un fake (élément fictif) peut être un stub ou un mob (objet fictif).</span><span class="sxs-lookup"><span data-stu-id="d324f-162">So in other words, a fake can be a stub or a mock.</span></span>

<span data-ttu-id="d324f-163">*Mock* - Il s’agit d’un objet fictif du système qui détermine la réussite ou l’échec d’un test unitaire.</span><span class="sxs-lookup"><span data-stu-id="d324f-163">*Mock* - A mock object is a fake object in the system that decides whether or not a unit test has passed or failed.</span></span> <span data-ttu-id="d324f-164">Un mock commence par être un Fake jusqu’à ce qu’il soit différencié par une assertion.</span><span class="sxs-lookup"><span data-stu-id="d324f-164">A mock starts out as a Fake until it is asserted against.</span></span>

<span data-ttu-id="d324f-165">*Stub* - Un stub permet de remplacer de manière contrôlée une dépendance existante (ou collaborateur) dans le système.</span><span class="sxs-lookup"><span data-stu-id="d324f-165">*Stub* - A stub is a controllable replacement for an existing dependency (or collaborator) in the system.</span></span> <span data-ttu-id="d324f-166">À l’aide d’un stub, vous pouvez tester votre code sans avoir à gérer directement la dépendance.</span><span class="sxs-lookup"><span data-stu-id="d324f-166">By using a stub, you can test your code without dealing with the dependency directly.</span></span> <span data-ttu-id="d324f-167">Par défaut, un fake commence comme par être un stub.</span><span class="sxs-lookup"><span data-stu-id="d324f-167">By default, a fake starts out as a stub.</span></span>

<span data-ttu-id="d324f-168">Prenez l'exemple de l'extrait de code suivant :</span><span class="sxs-lookup"><span data-stu-id="d324f-168">Consider the following code snippet:</span></span>

```csharp
var mockOrder = new MockOrder();
var purchase = new Purchase(mockOrder);

purchase.ValidateOrders();

Assert.True(purchase.CanBeShipped);
```

<span data-ttu-id="d324f-169">Il s’agit d’un exemple de stub appelé mock.</span><span class="sxs-lookup"><span data-stu-id="d324f-169">This would be an example of stub being referred to as a mock.</span></span> <span data-ttu-id="d324f-170">Dans le cas présent, il s’agit bien d’un stub.</span><span class="sxs-lookup"><span data-stu-id="d324f-170">In this case, it is a stub.</span></span> <span data-ttu-id="d324f-171">Vous passez simplement Order pour instancier `Purchase` (le système testé).</span><span class="sxs-lookup"><span data-stu-id="d324f-171">You're just passing in the Order as a means to be able to instantiate `Purchase` (the system under test).</span></span> <span data-ttu-id="d324f-172">Le nom `MockOrder` est également très trompeur, car encore une fois, order n’est pas un mock.</span><span class="sxs-lookup"><span data-stu-id="d324f-172">The name `MockOrder` is also very misleading because again, the order is not a mock.</span></span>

<span data-ttu-id="d324f-173">Il existe une meilleure approche</span><span class="sxs-lookup"><span data-stu-id="d324f-173">A better approach would be</span></span>

```csharp
var stubOrder = new FakeOrder();
var purchase = new Purchase(stubOrder);

purchase.ValidateOrders();

Assert.True(purchase.CanBeShipped);
```

<span data-ttu-id="d324f-174">En renommant la classe en `FakeOrder`, vous avez rendu celle-ci beaucoup plus générique. Vous pouvez utiliser la classe en tant que mock ou stub.</span><span class="sxs-lookup"><span data-stu-id="d324f-174">By renaming the class to `FakeOrder`, you've made the class a lot more generic, the class can be used as a mock or a stub.</span></span> <span data-ttu-id="d324f-175">Selon ce qui est le plus approprié pour le cas de test.</span><span class="sxs-lookup"><span data-stu-id="d324f-175">Whichever is better for the test case.</span></span> <span data-ttu-id="d324f-176">Dans l’exemple ci-dessus, `FakeOrder` est utilisé en tant que stub.</span><span class="sxs-lookup"><span data-stu-id="d324f-176">In the above example, `FakeOrder` is used as a stub.</span></span> <span data-ttu-id="d324f-177">Vous n’utilisez pas `FakeOrder` sous quelque forme que ce soit durant l’assertion.</span><span class="sxs-lookup"><span data-stu-id="d324f-177">You're not using the `FakeOrder` in any shape or form during the assert.</span></span> <span data-ttu-id="d324f-178">`FakeOrder` a simplement été passé à la classe `Purchase` pour répondre aux exigences du constructeur.</span><span class="sxs-lookup"><span data-stu-id="d324f-178">`FakeOrder` was just passed into the `Purchase` class to satisfy the requirements of the constructor.</span></span>

<span data-ttu-id="d324f-179">Pour l’utiliser en tant que Mock, vous pouvez faire quelque chose qui ressemble à ceci</span><span class="sxs-lookup"><span data-stu-id="d324f-179">To use it as a Mock, you could do something like this</span></span>

```csharp
var mockOrder = new FakeOrder();
var purchase = new Purchase(mockOrder);

purchase.ValidateOrders();

Assert.True(mockOrder.Validated);
```

<span data-ttu-id="d324f-180">Dans le cas présent, vous vérifiez une propriété sur le Fake (en le différenciant par assertion). Ainsi, dans l’extrait de code ci-dessus, `mockOrder` est un Mock.</span><span class="sxs-lookup"><span data-stu-id="d324f-180">In this case, you are checking a property on the Fake (asserting against it), so in the above code snippet, the `mockOrder` is a Mock.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="d324f-181">Il est important que cette terminologie soit correcte.</span><span class="sxs-lookup"><span data-stu-id="d324f-181">It's important to get this terminology correct.</span></span> <span data-ttu-id="d324f-182">Si vous appelez vos stubs « mocks », les autres développeurs vont faire de fausses hypothèses par rapport à votre intention.</span><span class="sxs-lookup"><span data-stu-id="d324f-182">If you call your stubs "mocks", other developers are going to make false assumptions about your intent.</span></span>

<span data-ttu-id="d324f-183">Le point principal à retenir à propos des mocks et des stubs est que les mocks sont comme des stubs. Toutefois, vous différenciez le mock (objet fictif) par assertion, contrairement au stub.</span><span class="sxs-lookup"><span data-stu-id="d324f-183">The main thing to remember about mocks versus stubs is that mocks are just like stubs, but you assert against the mock object, whereas you do not assert against a stub.</span></span>

## <a name="best-practices"></a><span data-ttu-id="d324f-184">Meilleures pratiques</span><span class="sxs-lookup"><span data-stu-id="d324f-184">Best practices</span></span>

### <a name="naming-your-tests"></a><span data-ttu-id="d324f-185">Nommage de vos tests</span><span class="sxs-lookup"><span data-stu-id="d324f-185">Naming your tests</span></span>
<span data-ttu-id="d324f-186">Le nom de votre test doit être composé de trois parties :</span><span class="sxs-lookup"><span data-stu-id="d324f-186">The name of your test should consist of three parts:</span></span>

- <span data-ttu-id="d324f-187">Nom de la méthode testée</span><span class="sxs-lookup"><span data-stu-id="d324f-187">The name of the method being tested.</span></span>
- <span data-ttu-id="d324f-188">Scénario de test utilisé</span><span class="sxs-lookup"><span data-stu-id="d324f-188">The scenario under which it's being tested.</span></span>
- <span data-ttu-id="d324f-189">Comportement attendu quand le scénario est appelé</span><span class="sxs-lookup"><span data-stu-id="d324f-189">The expected behavior when the scenario is invoked.</span></span>

#### <a name="why"></a><span data-ttu-id="d324f-190">Pourquoi ?</span><span class="sxs-lookup"><span data-stu-id="d324f-190">Why?</span></span>

- <span data-ttu-id="d324f-191">Les standards de nommage sont importants, car ils expriment explicitement la finalité du test.</span><span class="sxs-lookup"><span data-stu-id="d324f-191">Naming standards are important because they explicitly express the intent of the test.</span></span>

<span data-ttu-id="d324f-192">Les tests ne se limitent pas à la vérification du bon fonctionnement de votre code, ils fournissent également de la documentation.</span><span class="sxs-lookup"><span data-stu-id="d324f-192">Tests are more than just making sure your code works, they also provide documentation.</span></span> <span data-ttu-id="d324f-193">En examinant simplement la suite de tests unitaires, vous devez pouvoir en déduire le comportement de votre code.</span><span class="sxs-lookup"><span data-stu-id="d324f-193">Just by looking at the suite of unit tests, you should be able to infer the behavior of your code without even looking at the code itself.</span></span> <span data-ttu-id="d324f-194">De plus, en cas d’échec des tests, vous pouvez voir exactement quels sont les scénarios qui ne répondent pas à vos attentes.</span><span class="sxs-lookup"><span data-stu-id="d324f-194">Additionally, when tests fail, you can see exactly which scenarios do not meet your expectations.</span></span>

#### <a name="bad"></a><span data-ttu-id="d324f-195">Mauvais :</span><span class="sxs-lookup"><span data-stu-id="d324f-195">Bad:</span></span>
[!code-csharp[BeforeNaming](../../../samples/snippets/core/testing/unit-testing-best-practices/csharp/before/StringCalculatorTests.cs#BeforeNaming)]

#### <a name="better"></a><span data-ttu-id="d324f-196">Mieux :</span><span class="sxs-lookup"><span data-stu-id="d324f-196">Better:</span></span>
[!code-csharp[AfterNamingAndMinimallyPassing](../../../samples/snippets/core/testing/unit-testing-best-practices/csharp/after/StringCalculatorTests.cs#AfterNamingAndMinimallyPassing)]

### <a name="arranging-your-tests"></a><span data-ttu-id="d324f-197">Organisation de vos tests</span><span class="sxs-lookup"><span data-stu-id="d324f-197">Arranging your tests</span></span>
<span data-ttu-id="d324f-198">**Organisation, Action, Assertion** est un modèle courant pour les tests unitaires.</span><span class="sxs-lookup"><span data-stu-id="d324f-198">**Arrange, Act, Assert** is a common pattern when unit testing.</span></span> <span data-ttu-id="d324f-199">Comme son nom l’indique, il comporte trois actions principales :</span><span class="sxs-lookup"><span data-stu-id="d324f-199">As the name implies, it consists of three main actions:</span></span>

- <span data-ttu-id="d324f-200">*Organisation*, création et configuration des objets selon les besoins</span><span class="sxs-lookup"><span data-stu-id="d324f-200">*Arrange* your objects, creating and setting them up as necessary.</span></span>
- <span data-ttu-id="d324f-201">*Agir* sur un objet.</span><span class="sxs-lookup"><span data-stu-id="d324f-201">*Act* on an object.</span></span>
- <span data-ttu-id="d324f-202">*Assertion* de ce qui est prévu</span><span class="sxs-lookup"><span data-stu-id="d324f-202">*Assert* that something is as expected.</span></span>

#### <a name="why"></a><span data-ttu-id="d324f-203">Pourquoi ?</span><span class="sxs-lookup"><span data-stu-id="d324f-203">Why?</span></span>

- <span data-ttu-id="d324f-204">Permet de séparer clairement ce qui est testé des étapes *organisation* et *assertion*.</span><span class="sxs-lookup"><span data-stu-id="d324f-204">Clearly separates what is being tested from the *arrange* and *assert* steps.</span></span>
- <span data-ttu-id="d324f-205">Moins de risques de mélanger les assertions avec le code de l’étape « Action ».</span><span class="sxs-lookup"><span data-stu-id="d324f-205">Less chance to intermix assertions with "Act" code.</span></span>

<span data-ttu-id="d324f-206">La lisibilité est l’un des aspects les plus importants durant l’écriture d’un test.</span><span class="sxs-lookup"><span data-stu-id="d324f-206">Readability is one of the most important aspects when writing a test.</span></span> <span data-ttu-id="d324f-207">La séparation de chacune de ces actions dans le test met clairement en évidence les dépendances nécessaires à l’appel du code, le mode d’appel du code, ainsi que le contenu de l’assertion.</span><span class="sxs-lookup"><span data-stu-id="d324f-207">Separating each of these actions within the test clearly highlight the dependencies required to call your code, how your code is being called, and what you are trying to assert.</span></span> <span data-ttu-id="d324f-208">Bien qu’il soit possible de combiner certaines étapes et de réduire la taille du test, l’objectif principal est de rendre le test aussi lisible que possible.</span><span class="sxs-lookup"><span data-stu-id="d324f-208">While it may be possible to combine some steps and reduce the size of your test, the primary goal is to make the test as readable as possible.</span></span>

#### <a name="bad"></a><span data-ttu-id="d324f-209">Mauvais :</span><span class="sxs-lookup"><span data-stu-id="d324f-209">Bad:</span></span>
[!code-csharp[BeforeArranging](../../../samples/snippets/core/testing/unit-testing-best-practices/csharp/before/StringCalculatorTests.cs#BeforeArranging)]

#### <a name="better"></a><span data-ttu-id="d324f-210">Mieux :</span><span class="sxs-lookup"><span data-stu-id="d324f-210">Better:</span></span>
[!code-csharp[AfterArranging](../../../samples/snippets/core/testing/unit-testing-best-practices/csharp/after/StringCalculatorTests.cs#AfterArranging)]

### <a name="write-minimally-passing-tests"></a><span data-ttu-id="d324f-211">Écrire des tests concluants minimaux</span><span class="sxs-lookup"><span data-stu-id="d324f-211">Write minimally passing tests</span></span>
<span data-ttu-id="d324f-212">L’entrée à utiliser dans un test unitaire doit être la plus simple possible pour vérifier le comportement testé.</span><span class="sxs-lookup"><span data-stu-id="d324f-212">The input to be used in a unit test should be the simplest possible in order to verify the behavior that you are currently testing.</span></span>

#### <a name="why"></a><span data-ttu-id="d324f-213">Pourquoi ?</span><span class="sxs-lookup"><span data-stu-id="d324f-213">Why?</span></span>

- <span data-ttu-id="d324f-214">Les tests deviennent plus résilients face aux futurs changements du code base.</span><span class="sxs-lookup"><span data-stu-id="d324f-214">Tests become more resilient to future changes in the codebase.</span></span>
- <span data-ttu-id="d324f-215">Plus proche du comportement de test que de l’implémentation.</span><span class="sxs-lookup"><span data-stu-id="d324f-215">Closer to testing behavior over implementation.</span></span>

<span data-ttu-id="d324f-216">Les tests qui contiennent plus d’informations que nécessaire pour être réussis ont plus de chances d’introduire des erreurs et peuvent rendre l’intention moins claire.</span><span class="sxs-lookup"><span data-stu-id="d324f-216">Tests that include more information than required to pass the test have a higher chance of introducing errors into the test and can make the intent of the test less clear.</span></span> <span data-ttu-id="d324f-217">Quand vous écrivez des tests, vous devez vous concentrer sur le comportement.</span><span class="sxs-lookup"><span data-stu-id="d324f-217">When writing tests you want to focus on the behavior.</span></span> <span data-ttu-id="d324f-218">La définition de propriétés supplémentaires pour les modèles ou l’utilisation de valeurs différentes de zéro quand cela n’est pas nécessaire, ne fait que nuire à ce que vous essayez de prouver.</span><span class="sxs-lookup"><span data-stu-id="d324f-218">Setting extra properties on models or using non-zero values when not required, only detracts from what you are trying to prove.</span></span>

#### <a name="bad"></a><span data-ttu-id="d324f-219">Mauvais :</span><span class="sxs-lookup"><span data-stu-id="d324f-219">Bad:</span></span>
[!code-csharp[BeforeMinimallyPassing](../../../samples/snippets/core/testing/unit-testing-best-practices/csharp/before/StringCalculatorTests.cs#BeforeMinimallyPassing)]

#### <a name="better"></a><span data-ttu-id="d324f-220">Mieux :</span><span class="sxs-lookup"><span data-stu-id="d324f-220">Better:</span></span>
[!code-csharp[AfterNamingAndMinimallyPassing](../../../samples/snippets/core/testing/unit-testing-best-practices/csharp/after/StringCalculatorTests.cs#AfterNamingAndMinimallyPassing)]

### <a name="avoid-magic-strings"></a><span data-ttu-id="d324f-221">Éviter les chaînes magiques</span><span class="sxs-lookup"><span data-stu-id="d324f-221">Avoid magic strings</span></span>
<span data-ttu-id="d324f-222">Le nommage des variables dans les tests unitaires est aussi important, sinon plus, que le nommage des variables dans le code de production.</span><span class="sxs-lookup"><span data-stu-id="d324f-222">Naming variables in unit tests is as important, if not more important, than naming variables in production code.</span></span> <span data-ttu-id="d324f-223">Les tests unitaires ne doivent pas contenir de chaînes magiques.</span><span class="sxs-lookup"><span data-stu-id="d324f-223">Unit tests should not contain magic strings.</span></span>

#### <a name="why"></a><span data-ttu-id="d324f-224">Pourquoi ?</span><span class="sxs-lookup"><span data-stu-id="d324f-224">Why?</span></span>

- <span data-ttu-id="d324f-225">Évite au lecteur du test d’inspecter le code de production pour déterminer ce qui rend la valeur spéciale.</span><span class="sxs-lookup"><span data-stu-id="d324f-225">Prevents the need for the reader of the test to inspect the production code in order to figure out what makes the value special.</span></span>
- <span data-ttu-id="d324f-226">Montre explicitement ce que vous essayez de *prouver* et non ce que vous essayez d’*accomplir*.</span><span class="sxs-lookup"><span data-stu-id="d324f-226">Explicitly shows what you're trying to *prove* rather than trying to *accomplish*.</span></span>

<span data-ttu-id="d324f-227">Les chaînes magiques peuvent être sources de confusion pour le lecteur de vos tests.</span><span class="sxs-lookup"><span data-stu-id="d324f-227">Magic strings can cause confusion to the reader of your tests.</span></span> <span data-ttu-id="d324f-228">Si une chaîne semble inhabituelle, il peut se demander pourquoi une certaine valeur a été choisie pour un paramètre ou une valeur de retour.</span><span class="sxs-lookup"><span data-stu-id="d324f-228">If a string looks out of the ordinary, they may wonder why a certain value was chosen for a parameter or return value.</span></span> <span data-ttu-id="d324f-229">Cela peut l’amener à examiner de plus près les détails de l’implémentation, au lieu de se concentrer sur le test.</span><span class="sxs-lookup"><span data-stu-id="d324f-229">This may lead them to take a closer look at the implementation details, rather than focus on the test.</span></span>

> [!TIP]
> <span data-ttu-id="d324f-230">Quand vous écrivez des tests, concentrez-vous au maximum sur l’expression de l’intention.</span><span class="sxs-lookup"><span data-stu-id="d324f-230">When writing tests, you should aim to express as much intent as possible.</span></span> <span data-ttu-id="d324f-231">Dans le cas des chaînes magiques, une bonne approche consiste à assigner ces valeurs à des constantes.</span><span class="sxs-lookup"><span data-stu-id="d324f-231">In the case of magic strings, a good approach is to assign these values to constants.</span></span>

#### <a name="bad"></a><span data-ttu-id="d324f-232">Mauvais :</span><span class="sxs-lookup"><span data-stu-id="d324f-232">Bad:</span></span>
[!code-csharp[BeforeMagicString](../../../samples/snippets/core/testing/unit-testing-best-practices/csharp/before/StringCalculatorTests.cs#BeforeMagicString)]

#### <a name="better"></a><span data-ttu-id="d324f-233">Mieux :</span><span class="sxs-lookup"><span data-stu-id="d324f-233">Better:</span></span>
[!code-csharp[AfterMagicString](../../../samples/snippets/core/testing/unit-testing-best-practices/csharp/after/StringCalculatorTests.cs#AfterMagicString)]

### <a name="avoid-logic-in-tests"></a><span data-ttu-id="d324f-234">Éviter la logique dans les tests</span><span class="sxs-lookup"><span data-stu-id="d324f-234">Avoid logic in tests</span></span>
<span data-ttu-id="d324f-235">Durant l’écriture des tests unitaires, évitez la concaténation manuelle des chaînes et les conditions logiques telles que `if`, `while`, `for`, `switch`, etc.</span><span class="sxs-lookup"><span data-stu-id="d324f-235">When writing your unit tests avoid manual string concatenation and logical conditions such as `if`, `while`, `for`, `switch`, etc.</span></span>

#### <a name="why"></a><span data-ttu-id="d324f-236">Pourquoi ?</span><span class="sxs-lookup"><span data-stu-id="d324f-236">Why?</span></span>

- <span data-ttu-id="d324f-237">Moins de risques d’introduire un bogue dans vos tests.</span><span class="sxs-lookup"><span data-stu-id="d324f-237">Less chance to introduce a bug inside of your tests.</span></span>
- <span data-ttu-id="d324f-238">Concentrez-vous sur le résultat final plutôt que sur les détails de l’implémentation.</span><span class="sxs-lookup"><span data-stu-id="d324f-238">Focus on the end result, rather than implementation details.</span></span>

<span data-ttu-id="d324f-239">Quand vous introduisez une logique dans votre suite de tests, le risque d’introduction d’un bogue augmente considérablement.</span><span class="sxs-lookup"><span data-stu-id="d324f-239">When you introduce logic into your test suite, the chance of introducing a bug into it increases dramatically.</span></span> <span data-ttu-id="d324f-240">Votre suite de tests est bien le dernier endroit où vous devez trouver un bogue.</span><span class="sxs-lookup"><span data-stu-id="d324f-240">The last place that you want to find a bug is within your test suite.</span></span> <span data-ttu-id="d324f-241">Le fonctionnement de vos tests doit présenter un niveau de fiabilité élevé, sinon vous n’aurez pas confiance en ces derniers.</span><span class="sxs-lookup"><span data-stu-id="d324f-241">You should have a high level of confidence that your tests work, otherwise, you will not trust them.</span></span> <span data-ttu-id="d324f-242">Les tests auxquels vous ne faites pas confiance n’ont aucune valeur.</span><span class="sxs-lookup"><span data-stu-id="d324f-242">Tests that you do not trust, do not provide any value.</span></span> <span data-ttu-id="d324f-243">L’échec d’un test vous donne l’impression que quelque chose ne va pas dans votre code, et que vous ne pouvez pas l’ignorer.</span><span class="sxs-lookup"><span data-stu-id="d324f-243">When a test fails, you want to have a sense that something is actually wrong with your code and that it cannot be ignored.</span></span>

> [!TIP]
> <span data-ttu-id="d324f-244">Si le recours à la logique dans votre test semble inévitable, scindez-le en deux ou plusieurs tests distincts.</span><span class="sxs-lookup"><span data-stu-id="d324f-244">If logic in your test seems unavoidable, consider splitting the test up into two or more different tests.</span></span>

#### <a name="bad"></a><span data-ttu-id="d324f-245">Mauvais :</span><span class="sxs-lookup"><span data-stu-id="d324f-245">Bad:</span></span>
[!code-csharp[LogicInTests](../../../samples/snippets/core/testing/unit-testing-best-practices/csharp/before/StringCalculatorTests.cs#LogicInTests)]

#### <a name="better"></a><span data-ttu-id="d324f-246">Mieux :</span><span class="sxs-lookup"><span data-stu-id="d324f-246">Better:</span></span>
[!code-csharp[AfterTestLogic](../../../samples/snippets/core/testing/unit-testing-best-practices/csharp/after/StringCalculatorTests.cs#AfterTestLogic)]

### <a name="prefer-helper-methods-to-setup-and-teardown"></a><span data-ttu-id="d324f-247">Préférez les méthodes d’assistance à setup et teardown</span><span class="sxs-lookup"><span data-stu-id="d324f-247">Prefer helper methods to setup and teardown</span></span>
<span data-ttu-id="d324f-248">Si vous avez besoin d’un objet ou d’un état similaire pour vos tests, préférez une méthode d’assistance aux attributs Setup et Teardown, s’ils existent.</span><span class="sxs-lookup"><span data-stu-id="d324f-248">If you require a similar object or state for your tests, prefer a helper method than leveraging Setup and Teardown attributes if they exist.</span></span>

#### <a name="why"></a><span data-ttu-id="d324f-249">Pourquoi ?</span><span class="sxs-lookup"><span data-stu-id="d324f-249">Why?</span></span>

- <span data-ttu-id="d324f-250">Moins de confusion durant la lecture des tests, car l’ensemble du code est visible à partir de chaque test.</span><span class="sxs-lookup"><span data-stu-id="d324f-250">Less confusion when reading the tests since all of the code is visible from within each test.</span></span>
- <span data-ttu-id="d324f-251">Moins de risques d’effectuer une configuration excessive ou insuffisante pour le test donné.</span><span class="sxs-lookup"><span data-stu-id="d324f-251">Less chance of setting up too much or too little for the given test.</span></span>
- <span data-ttu-id="d324f-252">Moins de risques de partager l’état entre les tests, ce qui entraîne la création de dépendances indésirables entre eux.</span><span class="sxs-lookup"><span data-stu-id="d324f-252">Less chance of sharing state between tests which creates unwanted dependencies between them.</span></span>

<span data-ttu-id="d324f-253">Dans les frameworks de tests unitaires, `Setup` est appelé avant chaque test unitaire de votre suite de tests.</span><span class="sxs-lookup"><span data-stu-id="d324f-253">In unit testing frameworks, `Setup` is called before each and every unit test within your test suite.</span></span> <span data-ttu-id="d324f-254">Bien que certains puissent le voir comme un outil utile, cela aboutit généralement à des tests compliqués et difficiles à lire.</span><span class="sxs-lookup"><span data-stu-id="d324f-254">While some may see this as a useful tool, it generally ends up leading to bloated and hard to read tests.</span></span> <span data-ttu-id="d324f-255">Chaque test a généralement des exigences différentes pour être opérationnel.</span><span class="sxs-lookup"><span data-stu-id="d324f-255">Each test will generally have different requirements in order to get the test up and running.</span></span> <span data-ttu-id="d324f-256">Malheureusement, `Setup` vous oblige à utiliser exactement les mêmes exigences pour chaque test.</span><span class="sxs-lookup"><span data-stu-id="d324f-256">Unfortunately, `Setup` forces you to use the exact same requirements for each test.</span></span>

> [!NOTE]
> <span data-ttu-id="d324f-257">xUnit a supprimé SetUp et TearDown depuis la version 2.x</span><span class="sxs-lookup"><span data-stu-id="d324f-257">xUnit has removed both SetUp and TearDown as of version 2.x</span></span>

#### <a name="bad"></a><span data-ttu-id="d324f-258">Mauvais :</span><span class="sxs-lookup"><span data-stu-id="d324f-258">Bad:</span></span>
[!code-csharp[BeforeSetup](../../../samples/snippets/core/testing/unit-testing-best-practices/csharp/before/StringCalculatorTests.cs#BeforeSetup)]

```csharp
// more tests...
```

[!code-csharp[BeforeHelperMethod](../../../samples/snippets/core/testing/unit-testing-best-practices/csharp/before/StringCalculatorTests.cs#BeforeHelperMethod)]

#### <a name="better"></a><span data-ttu-id="d324f-259">Mieux :</span><span class="sxs-lookup"><span data-stu-id="d324f-259">Better:</span></span>
[!code-csharp[AfterHelperMethod](../../../samples/snippets/core/testing/unit-testing-best-practices/csharp/after/StringCalculatorTests.cs#AfterHelperMethod)]

```csharp
// more tests...
```

[!code-csharp[AfterSetup](../../../samples/snippets/core/testing/unit-testing-best-practices/csharp/after/StringCalculatorTests.cs#AfterSetup)]

### <a name="avoid-multiple-asserts"></a><span data-ttu-id="d324f-260">Éviter les assertions multiples</span><span class="sxs-lookup"><span data-stu-id="d324f-260">Avoid multiple asserts</span></span>
<span data-ttu-id="d324f-261">Durant l’écriture des tests, essayez d’inclure uniquement une instruction Assert par test.</span><span class="sxs-lookup"><span data-stu-id="d324f-261">When writing your tests, try to only include one Assert per test.</span></span> <span data-ttu-id="d324f-262">Voici les approches courantes pour utiliser une seule assertion :</span><span class="sxs-lookup"><span data-stu-id="d324f-262">Common approaches to using only one assert include:</span></span>

- <span data-ttu-id="d324f-263">Créez un test distinct pour chaque assertion.</span><span class="sxs-lookup"><span data-stu-id="d324f-263">Create a separate test for each assert.</span></span>
- <span data-ttu-id="d324f-264">Utilisez des tests paramétrables.</span><span class="sxs-lookup"><span data-stu-id="d324f-264">Use parameterized tests.</span></span>

#### <a name="why"></a><span data-ttu-id="d324f-265">Pourquoi ?</span><span class="sxs-lookup"><span data-stu-id="d324f-265">Why?</span></span>

- <span data-ttu-id="d324f-266">En cas d’échec d’une instruction Assert, les assertions qui suivent ne sont pas évaluées.</span><span class="sxs-lookup"><span data-stu-id="d324f-266">If one Assert fails, the subsequent Asserts will not be evaluated.</span></span>
- <span data-ttu-id="d324f-267">Permet de vérifier que vous n’effectuez pas l’assertion de plusieurs cas dans vos tests.</span><span class="sxs-lookup"><span data-stu-id="d324f-267">Ensures you are not asserting multiple cases in your tests.</span></span>
- <span data-ttu-id="d324f-268">Vous donne une idée complète des causes de l’échec des tests.</span><span class="sxs-lookup"><span data-stu-id="d324f-268">Gives you the entire picture as to why your tests are failing.</span></span>

<span data-ttu-id="d324f-269">Quand vous introduisez plusieurs assertions dans un cas de test, vous n’avez pas la garantie que toutes les assertions vont être exécutées.</span><span class="sxs-lookup"><span data-stu-id="d324f-269">When introducing multiple asserts into a test case, it is not guaranteed that all of the asserts will be executed.</span></span> <span data-ttu-id="d324f-270">Dans la plupart des frameworks de tests unitaires, une fois qu’une assertion a été l’objet d’un échec dans un test unitaire, les tests en cours d’exécution sont automatiquement considérés comme défaillants.</span><span class="sxs-lookup"><span data-stu-id="d324f-270">In most unit testing frameworks, once an assertion fails in a unit test, the proceeding tests are automatically considered to be failing.</span></span> <span data-ttu-id="d324f-271">Cela peut être déroutant, car les fonctionnalités qui fonctionnent réellement indiquent un état d’échec.</span><span class="sxs-lookup"><span data-stu-id="d324f-271">This can be confusing as functionality that is actually working, will be shown as failing.</span></span>

> [!NOTE]
> <span data-ttu-id="d324f-272">Il existe une exception usuelle à cette règle : l’assertion d’un objet par différenciation.</span><span class="sxs-lookup"><span data-stu-id="d324f-272">A common exception to this rule is when asserting against an object.</span></span> <span data-ttu-id="d324f-273">Dans ce cas, il est généralement acceptable d’avoir plusieurs assertions sur chaque propriété pour vérifier que l’objet se trouve dans l’état prévu.</span><span class="sxs-lookup"><span data-stu-id="d324f-273">In this case, it is generally acceptable to have multiple asserts against each property to ensure the object is in the state that you expect it to be in.</span></span>

#### <a name="bad"></a><span data-ttu-id="d324f-274">Mauvais :</span><span class="sxs-lookup"><span data-stu-id="d324f-274">Bad:</span></span>
[!code-csharp[BeforeMultipleAsserts](../../../samples/snippets/core/testing/unit-testing-best-practices/csharp/before/StringCalculatorTests.cs#BeforeMultipleAsserts)]

#### <a name="better"></a><span data-ttu-id="d324f-275">Mieux :</span><span class="sxs-lookup"><span data-stu-id="d324f-275">Better:</span></span>
[!code-csharp[AfterMultipleAsserts](../../../samples/snippets/core/testing/unit-testing-best-practices/csharp/after/StringCalculatorTests.cs#AfterMultipleAsserts)]

### <a name="validate-private-methods-by-unit-testing-public-methods"></a><span data-ttu-id="d324f-276">Valider les méthodes privées en effectuant un test unitaire des méthodes publiques</span><span class="sxs-lookup"><span data-stu-id="d324f-276">Validate private methods by unit testing public methods</span></span>
<span data-ttu-id="d324f-277">Dans la plupart des cas, il n’est pas nécessaire de tester une méthode privée.</span><span class="sxs-lookup"><span data-stu-id="d324f-277">In most cases, there should not be a need to test a private method.</span></span> <span data-ttu-id="d324f-278">Les méthodes privées sont un détail d’implémentation.</span><span class="sxs-lookup"><span data-stu-id="d324f-278">Private methods are an implementation detail.</span></span> <span data-ttu-id="d324f-279">Vous pouvez considérer la chose ainsi : les méthodes privées n’existent jamais de manière isolée.</span><span class="sxs-lookup"><span data-stu-id="d324f-279">You can think of it this way: private methods never exist in isolation.</span></span> <span data-ttu-id="d324f-280">À un moment donné, une méthode publique appelle la méthode privée dans le cadre de son implémentation.</span><span class="sxs-lookup"><span data-stu-id="d324f-280">At some point, there is going to be a public facing method that calls the private method as part of its implementation.</span></span> <span data-ttu-id="d324f-281">Vous devez prendre en compte le résultat final de la méthode publique qui appelle la méthode privée.</span><span class="sxs-lookup"><span data-stu-id="d324f-281">What you should care about is the end result of the public method that calls into the private one.</span></span>

<span data-ttu-id="d324f-282">Prenons le cas suivant</span><span class="sxs-lookup"><span data-stu-id="d324f-282">Consider the following case</span></span>

```csharp
public string ParseLogLine(string input)
{
    var sanitizedInput = TrimInput(input);
    return sanitizedInput;
}

private string TrimInput(string input)
{
    return input.Trim();
}
```

<span data-ttu-id="d324f-283">Votre première réaction peut être de commencer à écrire un test pour `TrimInput`, car vous souhaitez vérifier que la méthode fonctionne comme prévu.</span><span class="sxs-lookup"><span data-stu-id="d324f-283">Your first reaction may be to start writing a test for `TrimInput` because you want to make sure that the method is working as expected.</span></span> <span data-ttu-id="d324f-284">Toutefois, il est tout à fait possible que `ParseLogLine` manipule `sanitizedInput` de manière inattendue, ce qui rend inutile tout test de `TrimInput`.</span><span class="sxs-lookup"><span data-stu-id="d324f-284">However, it is entirely possible that `ParseLogLine` manipulates `sanitizedInput` in such a way that you do not expect, rendering a test against `TrimInput` useless.</span></span>

<span data-ttu-id="d324f-285">Le véritable test doit être effectué sur la méthode publique `ParseLogLine`, car c’est ce qui vous intéresse en fin de compte.</span><span class="sxs-lookup"><span data-stu-id="d324f-285">The real test should be done against the public facing method `ParseLogLine` because that is what you should ultimately care about.</span></span>

```csharp
public void ParseLogLine_ByDefault_ReturnsTrimmedResult()
{
    var parser = new Parser();

    var result = parser.ParseLogLine(" a ");

    Assert.Equals("a", result);
}
```

<span data-ttu-id="d324f-286">Ainsi, si vous voyez une méthode privée, recherchez la méthode publique et écrivez vos tests par rapport à cette méthode.</span><span class="sxs-lookup"><span data-stu-id="d324f-286">With this viewpoint, if you see a private method, find the public method and write your tests against that method.</span></span> <span data-ttu-id="d324f-287">Le fait qu’une méthode privée retourne le résultat attendu ne signifie pas que le système qui appelle la méthode privée utilise ce résultat correctement.</span><span class="sxs-lookup"><span data-stu-id="d324f-287">Just because a private method returns the expected result, does not mean the system that eventually calls the private method uses the result correctly.</span></span>

### <a name="stub-static-references"></a><span data-ttu-id="d324f-288">Références statiques de stub</span><span class="sxs-lookup"><span data-stu-id="d324f-288">Stub static references</span></span>
<span data-ttu-id="d324f-289">L’un des principes d’un test unitaire est qu’il doit avoir le contrôle total du système testé.</span><span class="sxs-lookup"><span data-stu-id="d324f-289">One of the principles of a unit test is that it must have full control of the system under test.</span></span> <span data-ttu-id="d324f-290">Cela peut être problématique quand le code de production inclut des appels à des références statiques (par exemple `DateTime.Now`).</span><span class="sxs-lookup"><span data-stu-id="d324f-290">This can be problematic when production code includes calls to static references (e.g. `DateTime.Now`).</span></span> <span data-ttu-id="d324f-291">Examinez le code suivant</span><span class="sxs-lookup"><span data-stu-id="d324f-291">Consider the following code</span></span>

```csharp
public int GetDiscountedPrice(int price)
{
    if(DateTime.Now.DayOfWeek == DayOfWeek.Tuesday)
    {
        return price / 2;
    }
    else
    {
        return price;
    }
}
```

<span data-ttu-id="d324f-292">Comment ce code peut-il faire l’objet d’un test unitaire ?</span><span class="sxs-lookup"><span data-stu-id="d324f-292">How can this code possibly be unit tested?</span></span> <span data-ttu-id="d324f-293">Vous pouvez tenter l’approche suivante</span><span class="sxs-lookup"><span data-stu-id="d324f-293">You may try an approach such as</span></span>

```csharp
public void GetDiscountedPrice_ByDefault_ReturnsFullPrice()
{
    var priceCalculator = new PriceCalculator();

    var actual = priceCalculator.GetDiscountedPrice(2);

    Assert.Equals(2, actual)
}

public void GetDiscountedPrice_OnTuesday_ReturnsHalfPrice()
{
    var priceCalculator = new PriceCalculator();

    var actual = priceCalculator.GetDiscountedPrice(2);

    Assert.Equals(1, actual);
}
```

<span data-ttu-id="d324f-294">Malheureusement, vous allez vite réaliser que vos tests posent quelques problèmes.</span><span class="sxs-lookup"><span data-stu-id="d324f-294">Unfortunately, you will quickly realize that there are a couple problems with your tests.</span></span>

- <span data-ttu-id="d324f-295">Si la suite de tests est exécutée un mardi, le second test est une réussite, mais le premier test est un échec.</span><span class="sxs-lookup"><span data-stu-id="d324f-295">If the test suite is run on a Tuesday, the second test will pass, but the first test will fail.</span></span>
- <span data-ttu-id="d324f-296">Si la suite de tests est exécutée un autre jour, le premier test est une réussite, mais le second test est un échec.</span><span class="sxs-lookup"><span data-stu-id="d324f-296">If the test suite is run on any other day, the first test will pass, but the second test will fail.</span></span>

<span data-ttu-id="d324f-297">Pour résoudre ces problèmes, vous allez devoir introduire un *seam* dans votre code de production.</span><span class="sxs-lookup"><span data-stu-id="d324f-297">To solve these problems, you'll need to introduce a *seam* into your production code.</span></span> <span data-ttu-id="d324f-298">Il existe une approche qui consiste à inclure dans un wrapper le code que vous devez contrôler dans une interface, et à faire en sorte que le code de production dépende de cette interface.</span><span class="sxs-lookup"><span data-stu-id="d324f-298">One approach is to wrap the code that you need to control in an interface and have the production code depend on that interface.</span></span>

```csharp
public interface IDateTimeProvider
{
    DayOfWeek DayOfWeek();
}

public int GetDiscountedPrice(int price, IDateTimeProvider dateTimeProvider)
{
    if(dateTimeProvider.DayOfWeek() == DayOfWeek.Tuesday)
    {
        return price / 2;
    }
    else
    {
        return price;
    }
}
```

<span data-ttu-id="d324f-299">Votre suite de tests devient</span><span class="sxs-lookup"><span data-stu-id="d324f-299">Your test suite now becomes</span></span>

```csharp
public void GetDiscountedPrice_ByDefault_ReturnsFullPrice()
{
    var priceCalculator = new PriceCalculator();
    var dateTimeProviderStub = new Mock<IDateTimeProvider>();
    dateTimeProviderStub.Setup(dtp => dtp.DayOfWeek()).Returns(DayOfWeek.Monday);

    var actual = priceCalculator.GetDiscountedPrice(2, dateTimeProviderStub);

    Assert.Equals(2, actual);
}

public void GetDiscountedPrice_OnTuesday_ReturnsHalfPrice()
{
    var priceCalculator = new PriceCalculator();
    var dateTimeProviderStub = new Mock<IDateTimeProvider>();
    dateTimeProviderStub.Setup(dtp => dtp.DayOfWeek()).Returns(DayOfWeek.Tuesday);

    var actual = priceCalculator.GetDiscountedPrice(2, dateTimeProviderStub);

    Assert.Equals(1, actual);
}
```

<span data-ttu-id="d324f-300">Désormais, la suite de tests a un contrôle total sur `DateTime.Now` et peut créer un stub de n’importe quelle valeur au moment d’appeler la méthode.</span><span class="sxs-lookup"><span data-stu-id="d324f-300">Now the test suite has full control over `DateTime.Now` and can stub any value when calling into the method.</span></span>
