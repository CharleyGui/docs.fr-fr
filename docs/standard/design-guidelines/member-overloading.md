---
title: Surcharge de membre
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- default arguments
- members [.NET Framework], overloaded
- member design guidelines [.NET Framework], overloading
- overloaded members
- signatures, members
ms.assetid: 964ba19e-8b94-4b5b-b1e3-5a0b531a0bb1
ms.openlocfilehash: c9cb178e838aab99c22089b527a6bd2e86b325de
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76727841"
---
# <a name="member-overloading"></a><span data-ttu-id="2e422-102">Surcharge de membre</span><span class="sxs-lookup"><span data-stu-id="2e422-102">Member Overloading</span></span>
<span data-ttu-id="2e422-103">Member overloading means creating two or more members on the same type that differ only in the number or type of parameters but have the same name.</span><span class="sxs-lookup"><span data-stu-id="2e422-103">Member overloading means creating two or more members on the same type that differ only in the number or type of parameters but have the same name.</span></span> <span data-ttu-id="2e422-104">For example, in the following, the `WriteLine` method is overloaded:</span><span class="sxs-lookup"><span data-stu-id="2e422-104">For example, in the following, the `WriteLine` method is overloaded:</span></span>

```csharp
public static class Console {
    public void WriteLine();
    public void WriteLine(string value);
    public void WriteLine(bool value);
    ...
}
```

 <span data-ttu-id="2e422-105">Because only methods, constructors, and indexed properties can have parameters, only those members can be overloaded.</span><span class="sxs-lookup"><span data-stu-id="2e422-105">Because only methods, constructors, and indexed properties can have parameters, only those members can be overloaded.</span></span>

 <span data-ttu-id="2e422-106">Overloading is one of the most important techniques for improving usability, productivity, and readability of reusable libraries.</span><span class="sxs-lookup"><span data-stu-id="2e422-106">Overloading is one of the most important techniques for improving usability, productivity, and readability of reusable libraries.</span></span> <span data-ttu-id="2e422-107">Overloading on the number of parameters makes it possible to provide simpler versions of constructors and methods.</span><span class="sxs-lookup"><span data-stu-id="2e422-107">Overloading on the number of parameters makes it possible to provide simpler versions of constructors and methods.</span></span> <span data-ttu-id="2e422-108">Overloading on the parameter type makes it possible to use the same member name for members performing identical operations on a selected set of different types.</span><span class="sxs-lookup"><span data-stu-id="2e422-108">Overloading on the parameter type makes it possible to use the same member name for members performing identical operations on a selected set of different types.</span></span>

 <span data-ttu-id="2e422-109">✔️ DO try to use descriptive parameter names to indicate the default used by shorter overloads.</span><span class="sxs-lookup"><span data-stu-id="2e422-109">✔️ DO try to use descriptive parameter names to indicate the default used by shorter overloads.</span></span>

 <span data-ttu-id="2e422-110">❌ AVOID arbitrarily varying parameter names in overloads.</span><span class="sxs-lookup"><span data-stu-id="2e422-110">❌ AVOID arbitrarily varying parameter names in overloads.</span></span> <span data-ttu-id="2e422-111">If a parameter in one overload represents the same input as a parameter in another overload, the parameters should have the same name.</span><span class="sxs-lookup"><span data-stu-id="2e422-111">If a parameter in one overload represents the same input as a parameter in another overload, the parameters should have the same name.</span></span>

 <span data-ttu-id="2e422-112">❌ AVOID being inconsistent in the ordering of parameters in overloaded members.</span><span class="sxs-lookup"><span data-stu-id="2e422-112">❌ AVOID being inconsistent in the ordering of parameters in overloaded members.</span></span> <span data-ttu-id="2e422-113">Parameters with the same name should appear in the same position in all overloads.</span><span class="sxs-lookup"><span data-stu-id="2e422-113">Parameters with the same name should appear in the same position in all overloads.</span></span>

 <span data-ttu-id="2e422-114">✔️ DO make only the longest overload virtual (if extensibility is required).</span><span class="sxs-lookup"><span data-stu-id="2e422-114">✔️ DO make only the longest overload virtual (if extensibility is required).</span></span> <span data-ttu-id="2e422-115">Shorter overloads should simply call through to a longer overload.</span><span class="sxs-lookup"><span data-stu-id="2e422-115">Shorter overloads should simply call through to a longer overload.</span></span>

 <span data-ttu-id="2e422-116">❌ DO NOT use `ref` or `out` modifiers to overload members.</span><span class="sxs-lookup"><span data-stu-id="2e422-116">❌ DO NOT use `ref` or `out` modifiers to overload members.</span></span>

 <span data-ttu-id="2e422-117">Some languages cannot resolve calls to overloads like this.</span><span class="sxs-lookup"><span data-stu-id="2e422-117">Some languages cannot resolve calls to overloads like this.</span></span> <span data-ttu-id="2e422-118">In addition, such overloads usually have completely different semantics and probably should not be overloads but two separate methods instead.</span><span class="sxs-lookup"><span data-stu-id="2e422-118">In addition, such overloads usually have completely different semantics and probably should not be overloads but two separate methods instead.</span></span>

 <span data-ttu-id="2e422-119">❌ DO NOT have overloads with parameters at the same position and similar types yet with different semantics.</span><span class="sxs-lookup"><span data-stu-id="2e422-119">❌ DO NOT have overloads with parameters at the same position and similar types yet with different semantics.</span></span>

 <span data-ttu-id="2e422-120">✔️ DO  allow `null` to be passed for optional arguments.</span><span class="sxs-lookup"><span data-stu-id="2e422-120">✔️ DO  allow `null` to be passed for optional arguments.</span></span>

 <span data-ttu-id="2e422-121">✔️ DO use member overloading rather than defining members with default arguments.</span><span class="sxs-lookup"><span data-stu-id="2e422-121">✔️ DO use member overloading rather than defining members with default arguments.</span></span>

 <span data-ttu-id="2e422-122">Default arguments are not CLS compliant.</span><span class="sxs-lookup"><span data-stu-id="2e422-122">Default arguments are not CLS compliant.</span></span>

 <span data-ttu-id="2e422-123">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span><span class="sxs-lookup"><span data-stu-id="2e422-123">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="2e422-124">*Réimprimé avec l’autorisation de Pearson Education, Inc. et extrait de [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) par Krzysztof Cwalina et Brad Abrams, publié le 22 octobre 2008 par Addison-Wesley Professional dans le cadre de la série sur le développement Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="2e422-124">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="2e422-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2e422-125">See also</span></span>

- [<span data-ttu-id="2e422-126">Instructions de conception des membres</span><span class="sxs-lookup"><span data-stu-id="2e422-126">Member Design Guidelines</span></span>](../../../docs/standard/design-guidelines/member.md)
- [<span data-ttu-id="2e422-127">Règles de conception de .NET Framework</span><span class="sxs-lookup"><span data-stu-id="2e422-127">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
