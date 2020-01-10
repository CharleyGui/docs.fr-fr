---
title: Utilisation de types d'exceptions standard
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- throwing exceptions, standard types
- catching exceptions
- exceptions, catching
- exceptions, throwing
ms.assetid: ab22ce03-78f9-4dca-8824-c7ed3bdccc27
ms.openlocfilehash: 6b202d618d9d2216c8998181303250081de6781c
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75708982"
---
# <a name="using-standard-exception-types"></a><span data-ttu-id="719a1-102">Utilisation de types d'exceptions standard</span><span class="sxs-lookup"><span data-stu-id="719a1-102">Using Standard Exception Types</span></span>
<span data-ttu-id="719a1-103">Cette section décrit les exceptions standard fournies par l’infrastructure et les détails de leur utilisation.</span><span class="sxs-lookup"><span data-stu-id="719a1-103">This section describes the standard exceptions provided by the Framework and the details of their usage.</span></span> <span data-ttu-id="719a1-104">La liste n’est pas exhaustive.</span><span class="sxs-lookup"><span data-stu-id="719a1-104">The list is by no means exhaustive.</span></span> <span data-ttu-id="719a1-105">Pour plus d’informations sur l’utilisation d’autres types d’exception d’infrastructure, consultez la documentation de référence .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="719a1-105">Please refer to the .NET Framework reference documentation for usage of other Framework exception types.</span></span>  
  
## <a name="exception-and-systemexception"></a><span data-ttu-id="719a1-106">Exception et SystemException</span><span class="sxs-lookup"><span data-stu-id="719a1-106">Exception and SystemException</span></span>  
 <span data-ttu-id="719a1-107">**X DO NOT** lever <xref:System.Exception?displayProperty=nameWithType> ou <xref:System.SystemException?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="719a1-107">**X DO NOT** throw <xref:System.Exception?displayProperty=nameWithType> or <xref:System.SystemException?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="719a1-108">**X DO NOT** catch `System.Exception` ou `System.SystemException` dans le code d’infrastructure, sauf si vous souhaitez lever de nouveau.</span><span class="sxs-lookup"><span data-stu-id="719a1-108">**X DO NOT** catch `System.Exception` or `System.SystemException` in framework code, unless you intend to rethrow.</span></span>  
  
 <span data-ttu-id="719a1-109">**X AVOID** interception `System.Exception` ou `System.SystemException`, sauf dans les gestionnaires d’exceptions de niveau supérieur.</span><span class="sxs-lookup"><span data-stu-id="719a1-109">**X AVOID** catching `System.Exception` or `System.SystemException`, except in top-level exception handlers.</span></span>  
  
## <a name="applicationexception"></a><span data-ttu-id="719a1-110">ApplicationException</span><span class="sxs-lookup"><span data-stu-id="719a1-110">ApplicationException</span></span>  
 <span data-ttu-id="719a1-111">**X DO NOT** lever ou dériver de <xref:System.ApplicationException>.</span><span class="sxs-lookup"><span data-stu-id="719a1-111">**X DO NOT** throw or derive from <xref:System.ApplicationException>.</span></span>  
  
## <a name="invalidoperationexception"></a><span data-ttu-id="719a1-112">InvalidOperationException</span><span class="sxs-lookup"><span data-stu-id="719a1-112">InvalidOperationException</span></span>  
 <span data-ttu-id="719a1-113">**✓ DO** lever un <xref:System.InvalidOperationException> si l’objet est dans un état inapproprié.</span><span class="sxs-lookup"><span data-stu-id="719a1-113">**✓ DO** throw an <xref:System.InvalidOperationException> if the object is in an inappropriate state.</span></span>  
  
## <a name="argumentexception-argumentnullexception-and-argumentoutofrangeexception"></a><span data-ttu-id="719a1-114">ArgumentException, ArgumentNullException et ArgumentOutOfRangeException</span><span class="sxs-lookup"><span data-stu-id="719a1-114">ArgumentException, ArgumentNullException, and ArgumentOutOfRangeException</span></span>  
 <span data-ttu-id="719a1-115">**✓ DO** lever <xref:System.ArgumentException> ou l’un de ses sous-types si des arguments incorrects sont passés à un membre.</span><span class="sxs-lookup"><span data-stu-id="719a1-115">**✓ DO** throw <xref:System.ArgumentException> or one of its subtypes if bad arguments are passed to a member.</span></span> <span data-ttu-id="719a1-116">Préférer le type d’exception le plus dérivé, le cas échéant.</span><span class="sxs-lookup"><span data-stu-id="719a1-116">Prefer the most derived exception type, if applicable.</span></span>  
  
 <span data-ttu-id="719a1-117">**✓ DO** définir le `ParamName` propriété lors de la levée d’une des sous-classes de `ArgumentException`.</span><span class="sxs-lookup"><span data-stu-id="719a1-117">**✓ DO** set the `ParamName` property when throwing one of the subclasses of `ArgumentException`.</span></span>  
  
 <span data-ttu-id="719a1-118">Cette propriété représente le nom du paramètre qui a provoqué la levée de l’exception.</span><span class="sxs-lookup"><span data-stu-id="719a1-118">This property represents the name of the parameter that caused the exception to be thrown.</span></span> <span data-ttu-id="719a1-119">Notez que la propriété peut être définie à l’aide de l’une des surcharges de constructeur.</span><span class="sxs-lookup"><span data-stu-id="719a1-119">Note that the property can be set using one of the constructor overloads.</span></span>  
  
 <span data-ttu-id="719a1-120">**✓ DO** utiliser `value` pour le nom du paramètre de valeur implicite d’accesseurs Set de propriété.</span><span class="sxs-lookup"><span data-stu-id="719a1-120">**✓ DO** use `value` for the name of the implicit value parameter of property setters.</span></span>  
  
## <a name="nullreferenceexception-indexoutofrangeexception-and-accessviolationexception"></a><span data-ttu-id="719a1-121">NullReferenceException, IndexOutOfRangeException et AccessViolationException</span><span class="sxs-lookup"><span data-stu-id="719a1-121">NullReferenceException, IndexOutOfRangeException, and AccessViolationException</span></span>  
 <span data-ttu-id="719a1-122">**X DO NOT** autoriser API pouvant être appelées publiquement à lever explicitement ou implicitement <xref:System.NullReferenceException>, <xref:System.AccessViolationException>, ou <xref:System.IndexOutOfRangeException>.</span><span class="sxs-lookup"><span data-stu-id="719a1-122">**X DO NOT** allow publicly callable APIs to explicitly or implicitly throw <xref:System.NullReferenceException>, <xref:System.AccessViolationException>, or <xref:System.IndexOutOfRangeException>.</span></span> <span data-ttu-id="719a1-123">Ces exceptions sont réservées et levées par le moteur d’exécution et, dans la plupart des cas, indiquent un bogue.</span><span class="sxs-lookup"><span data-stu-id="719a1-123">These exceptions are reserved and thrown by the execution engine and in most cases indicate a bug.</span></span>  
  
 <span data-ttu-id="719a1-124">Procédez à la vérification des arguments pour éviter de lever ces exceptions.</span><span class="sxs-lookup"><span data-stu-id="719a1-124">Do argument checking to avoid throwing these exceptions.</span></span> <span data-ttu-id="719a1-125">La levée de ces exceptions expose les détails d’implémentation de votre méthode qui peuvent changer au fil du temps.</span><span class="sxs-lookup"><span data-stu-id="719a1-125">Throwing these exceptions exposes implementation details of your method that might change over time.</span></span>  
  
## <a name="stackoverflowexception"></a><span data-ttu-id="719a1-126">StackOverflowException</span><span class="sxs-lookup"><span data-stu-id="719a1-126">StackOverflowException</span></span>  
 <span data-ttu-id="719a1-127">**X DO NOT** lever explicitement <xref:System.StackOverflowException>.</span><span class="sxs-lookup"><span data-stu-id="719a1-127">**X DO NOT** explicitly throw <xref:System.StackOverflowException>.</span></span> <span data-ttu-id="719a1-128">L’exception doit être levée explicitement uniquement par le CLR.</span><span class="sxs-lookup"><span data-stu-id="719a1-128">The exception should be explicitly thrown only by the CLR.</span></span>  
  
 <span data-ttu-id="719a1-129">**X DO NOT** catch `StackOverflowException`.</span><span class="sxs-lookup"><span data-stu-id="719a1-129">**X DO NOT** catch `StackOverflowException`.</span></span>  
  
 <span data-ttu-id="719a1-130">Il est presque impossible d’écrire du code managé qui reste cohérent en présence de dépassements de pile arbitraires.</span><span class="sxs-lookup"><span data-stu-id="719a1-130">It is almost impossible to write managed code that remains consistent in the presence of arbitrary stack overflows.</span></span> <span data-ttu-id="719a1-131">Les parties non managées du CLR restent cohérentes en utilisant des sondes pour déplacer les débordements de pile vers des emplacements bien définis plutôt que en sauvegardant des débordements de pile arbitraires.</span><span class="sxs-lookup"><span data-stu-id="719a1-131">The unmanaged parts of the CLR remain consistent by using probes to move stack overflows to well-defined places rather than by backing out from arbitrary stack overflows.</span></span>  
  
## <a name="outofmemoryexception"></a><span data-ttu-id="719a1-132">OutOfMemoryException</span><span class="sxs-lookup"><span data-stu-id="719a1-132">OutOfMemoryException</span></span>  
 <span data-ttu-id="719a1-133">**X DO NOT** lever explicitement <xref:System.OutOfMemoryException>.</span><span class="sxs-lookup"><span data-stu-id="719a1-133">**X DO NOT** explicitly throw <xref:System.OutOfMemoryException>.</span></span> <span data-ttu-id="719a1-134">Cette exception doit être levée uniquement par l’infrastructure CLR.</span><span class="sxs-lookup"><span data-stu-id="719a1-134">This exception is to be thrown only by the CLR infrastructure.</span></span>  
  
## <a name="comexception-sehexception-and-executionengineexception"></a><span data-ttu-id="719a1-135">COMException, SEHException et ExecutionEngineException</span><span class="sxs-lookup"><span data-stu-id="719a1-135">ComException, SEHException, and ExecutionEngineException</span></span>  
 <span data-ttu-id="719a1-136">**X DO NOT** lever explicitement <xref:System.Runtime.InteropServices.COMException>, <xref:System.ExecutionEngineException>, et <xref:System.Runtime.InteropServices.SEHException>.</span><span class="sxs-lookup"><span data-stu-id="719a1-136">**X DO NOT** explicitly throw <xref:System.Runtime.InteropServices.COMException>,  <xref:System.ExecutionEngineException>, and <xref:System.Runtime.InteropServices.SEHException>.</span></span> <span data-ttu-id="719a1-137">Ces exceptions doivent être levées uniquement par l’infrastructure CLR.</span><span class="sxs-lookup"><span data-stu-id="719a1-137">These exceptions are to be thrown only by the CLR infrastructure.</span></span>  
  
 <span data-ttu-id="719a1-138">*Parties © 2005, 2009 Microsoft Corporation. Tous droits réservés.*</span><span class="sxs-lookup"><span data-stu-id="719a1-138">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="719a1-139">*Réimprimé avec l’autorisation de Pearson Education, Inc. et extrait de [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) par Krzysztof Cwalina et Brad Abrams, publié le 22 octobre 2008 par Addison-Wesley Professional dans le cadre de la série sur le développement Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="719a1-139">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="719a1-140">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="719a1-140">See also</span></span>

- [<span data-ttu-id="719a1-141">Règles de conception de .NET Framework</span><span class="sxs-lookup"><span data-stu-id="719a1-141">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
- [<span data-ttu-id="719a1-142">Instructions de conception pour les exceptions</span><span class="sxs-lookup"><span data-stu-id="719a1-142">Design Guidelines for Exceptions</span></span>](../../../docs/standard/design-guidelines/exceptions.md)
