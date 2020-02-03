---
title: Exceptions et performances
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- tester-doer pattern
- TryParse pattern
- exceptions, throwing
- exceptions, performance
- throwing exceptions, performance
ms.assetid: 3ad6aad9-08e6-4232-b336-0e301f2493e6
ms.openlocfilehash: afa4e748599781a5979823320d8913ff5357d415
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76741645"
---
# <a name="exceptions-and-performance"></a><span data-ttu-id="c3e5e-102">Exceptions et performances</span><span class="sxs-lookup"><span data-stu-id="c3e5e-102">Exceptions and Performance</span></span>
<span data-ttu-id="c3e5e-103">L’une des préoccupations courantes liées aux exceptions est que, si des exceptions sont utilisées pour du code qui échoue régulièrement, les performances de l’implémentation seront inacceptables.</span><span class="sxs-lookup"><span data-stu-id="c3e5e-103">One common concern related to exceptions is that if exceptions are used for code that routinely fails, the performance of the implementation will be unacceptable.</span></span> <span data-ttu-id="c3e5e-104">Il s’agit d’un problème valide.</span><span class="sxs-lookup"><span data-stu-id="c3e5e-104">This is a valid concern.</span></span> <span data-ttu-id="c3e5e-105">Lorsqu’un membre lève une exception, ses performances peuvent être plus lentes.</span><span class="sxs-lookup"><span data-stu-id="c3e5e-105">When a member throws an exception, its performance can be orders of magnitude slower.</span></span> <span data-ttu-id="c3e5e-106">Toutefois, il est possible d’obtenir de bonnes performances tout en respectant strictement les règles d’exception qui interdisent l’utilisation de codes d’erreur.</span><span class="sxs-lookup"><span data-stu-id="c3e5e-106">However, it is possible to achieve good performance while strictly adhering to the exception guidelines that disallow using error codes.</span></span> <span data-ttu-id="c3e5e-107">Deux modèles décrits dans cette section montrent comment procéder.</span><span class="sxs-lookup"><span data-stu-id="c3e5e-107">Two patterns described in this section suggest ways to do this.</span></span>

 <span data-ttu-id="c3e5e-108">❌ n’utilisez pas de codes d’erreur en raison de problèmes liés au fait que les exceptions peuvent affecter les performances de manière négative.</span><span class="sxs-lookup"><span data-stu-id="c3e5e-108">❌ DO NOT use error codes because of concerns that exceptions might affect performance negatively.</span></span>

 <span data-ttu-id="c3e5e-109">Pour améliorer les performances, il est possible d’utiliser le modèle testeur-Doer ou le modèle try-Parse, décrit dans les deux sections suivantes.</span><span class="sxs-lookup"><span data-stu-id="c3e5e-109">To improve performance, it is possible to use either the Tester-Doer Pattern or the Try-Parse Pattern, described in the next two sections.</span></span>

## <a name="tester-doer-pattern"></a><span data-ttu-id="c3e5e-110">Modèle testeur-Doer</span><span class="sxs-lookup"><span data-stu-id="c3e5e-110">Tester-Doer Pattern</span></span>
 <span data-ttu-id="c3e5e-111">Parfois, les performances d’un membre levant une exception peuvent être améliorées en divisant le membre en deux.</span><span class="sxs-lookup"><span data-stu-id="c3e5e-111">Sometimes performance of an exception-throwing member can be improved by breaking the member into two.</span></span> <span data-ttu-id="c3e5e-112">Examinons la méthode <xref:System.Collections.Generic.ICollection%601.Add%2A> de l’interface <xref:System.Collections.Generic.ICollection%601>.</span><span class="sxs-lookup"><span data-stu-id="c3e5e-112">Let’s look at the <xref:System.Collections.Generic.ICollection%601.Add%2A> method of the <xref:System.Collections.Generic.ICollection%601> interface.</span></span>

```csharp
ICollection<int> numbers = ...
numbers.Add(1);
```

 <span data-ttu-id="c3e5e-113">La méthode `Add` lève une exception si la collection est en lecture seule.</span><span class="sxs-lookup"><span data-stu-id="c3e5e-113">The method `Add` throws if the collection is read-only.</span></span> <span data-ttu-id="c3e5e-114">Il peut s’agir d’un problème de performances dans les scénarios où l’appel de méthode est supposé échouer souvent.</span><span class="sxs-lookup"><span data-stu-id="c3e5e-114">This can be a performance problem in scenarios where the method call is expected to fail often.</span></span> <span data-ttu-id="c3e5e-115">L’une des façons d’atténuer le problème consiste à tester si la collection est accessible en écriture avant d’essayer d’ajouter une valeur.</span><span class="sxs-lookup"><span data-stu-id="c3e5e-115">One of the ways to mitigate the problem is to test whether the collection is writable before trying to add a value.</span></span>

```csharp
ICollection<int> numbers = ...
...
if (!numbers.IsReadOnly)
{
    numbers.Add(1);
}
```

 <span data-ttu-id="c3e5e-116">Le membre utilisé pour tester une condition, qui, dans notre exemple, est la propriété `IsReadOnly`, est appelé testeur.</span><span class="sxs-lookup"><span data-stu-id="c3e5e-116">The member used to test a condition, which in our example is the property `IsReadOnly`, is referred to as the tester.</span></span> <span data-ttu-id="c3e5e-117">Le membre utilisé pour effectuer une opération de levée potentielle, la méthode `Add` dans notre exemple, est appelé Doer.</span><span class="sxs-lookup"><span data-stu-id="c3e5e-117">The member used to perform a potentially throwing operation, the `Add` method in our example, is referred to as the doer.</span></span>

 <span data-ttu-id="c3e5e-118">✔️ EXAMINEz le modèle testeur-Doer pour les membres qui peuvent lever des exceptions dans les scénarios courants afin d’éviter les problèmes de performances liés aux exceptions.</span><span class="sxs-lookup"><span data-stu-id="c3e5e-118">✔️ CONSIDER the Tester-Doer Pattern for members that might throw exceptions in common scenarios to avoid performance problems related to exceptions.</span></span>

## <a name="try-parse-pattern"></a><span data-ttu-id="c3e5e-119">Modèle try-parse</span><span class="sxs-lookup"><span data-stu-id="c3e5e-119">Try-Parse Pattern</span></span>
 <span data-ttu-id="c3e5e-120">Pour les API très performantes, il est préférable d’utiliser un modèle encore plus rapide que le modèle testeur-Doer décrit dans la section précédente.</span><span class="sxs-lookup"><span data-stu-id="c3e5e-120">For extremely performance-sensitive APIs, an even faster pattern than the Tester-Doer Pattern described in the previous section should be used.</span></span> <span data-ttu-id="c3e5e-121">Le modèle appelle pour ajuster le nom de membre afin qu’un cas de test bien défini fasse partie de la sémantique de membre.</span><span class="sxs-lookup"><span data-stu-id="c3e5e-121">The pattern calls for adjusting the member name to make a well-defined test case a part of the member semantics.</span></span> <span data-ttu-id="c3e5e-122">Par exemple, <xref:System.DateTime> définit une méthode <xref:System.DateTime.Parse%2A> qui lève une exception en cas d’échec de l’analyse d’une chaîne.</span><span class="sxs-lookup"><span data-stu-id="c3e5e-122">For example, <xref:System.DateTime> defines a <xref:System.DateTime.Parse%2A> method that throws an exception if parsing of a string fails.</span></span> <span data-ttu-id="c3e5e-123">Il définit également une méthode <xref:System.DateTime.TryParse%2A> correspondante qui tente d’analyser, mais retourne la valeur false si l’analyse échoue et retourne le résultat d’une analyse réussie à l’aide d’un paramètre `out`.</span><span class="sxs-lookup"><span data-stu-id="c3e5e-123">It also defines a corresponding <xref:System.DateTime.TryParse%2A> method that attempts to parse, but returns false if parsing is unsuccessful and returns the result of a successful parsing using an `out` parameter.</span></span>

```csharp
public struct DateTime
{
    public static DateTime Parse(string dateTime)
    {
        ...
    }
    public static bool TryParse(string dateTime, out DateTime result)
    {
        ...
    }
}
```

 <span data-ttu-id="c3e5e-124">Lors de l’utilisation de ce modèle, il est important de définir la fonctionnalité try en termes stricts.</span><span class="sxs-lookup"><span data-stu-id="c3e5e-124">When using this pattern, it is important to define the try functionality in strict terms.</span></span> <span data-ttu-id="c3e5e-125">Si le membre échoue pour une raison autre que la tentative bien définie, le membre doit toujours lever une exception correspondante.</span><span class="sxs-lookup"><span data-stu-id="c3e5e-125">If the member fails for any reason other than the well-defined try, the member must still throw a corresponding exception.</span></span>

 <span data-ttu-id="c3e5e-126">✔️ EXAMINEz le modèle try-parse pour les membres qui peuvent lever des exceptions dans les scénarios courants afin d’éviter les problèmes de performances liés aux exceptions.</span><span class="sxs-lookup"><span data-stu-id="c3e5e-126">✔️ CONSIDER the Try-Parse Pattern for members that might throw exceptions in common scenarios to avoid performance problems related to exceptions.</span></span>

 <span data-ttu-id="c3e5e-127">✔️ Utilisez le préfixe « try » et le type de retour booléen pour les méthodes qui implémentent ce modèle.</span><span class="sxs-lookup"><span data-stu-id="c3e5e-127">✔️ DO use the prefix "Try" and Boolean return type for methods implementing this pattern.</span></span>

 <span data-ttu-id="c3e5e-128">✔️ fournissez un membre levant des exceptions pour chaque membre à l’aide du modèle try-parse.</span><span class="sxs-lookup"><span data-stu-id="c3e5e-128">✔️ DO provide an exception-throwing member for each member using the Try-Parse Pattern.</span></span>

 <span data-ttu-id="c3e5e-129">*Parties © 2005, 2009 Microsoft Corporation. Tous droits réservés.*</span><span class="sxs-lookup"><span data-stu-id="c3e5e-129">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="c3e5e-130">*Réimprimé avec l’autorisation de Pearson Education, Inc. et extrait de [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) par Krzysztof Cwalina et Brad Abrams, publié le 22 octobre 2008 par Addison-Wesley Professional dans le cadre de la série sur le développement Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="c3e5e-130">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="c3e5e-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c3e5e-131">See also</span></span>

- [<span data-ttu-id="c3e5e-132">Règles de conception de .NET Framework</span><span class="sxs-lookup"><span data-stu-id="c3e5e-132">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
- [<span data-ttu-id="c3e5e-133">Instructions de conception pour les exceptions</span><span class="sxs-lookup"><span data-stu-id="c3e5e-133">Design Guidelines for Exceptions</span></span>](../../../docs/standard/design-guidelines/exceptions.md)
