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
ms.openlocfilehash: b8e05f22a66fabeab28cc83a074471df29aae218
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84291355"
---
# <a name="using-standard-exception-types"></a><span data-ttu-id="9d77a-102">Utilisation de types d'exceptions standard</span><span class="sxs-lookup"><span data-stu-id="9d77a-102">Using Standard Exception Types</span></span>
<span data-ttu-id="9d77a-103">Cette section décrit les exceptions standard fournies par l’infrastructure et les détails de leur utilisation.</span><span class="sxs-lookup"><span data-stu-id="9d77a-103">This section describes the standard exceptions provided by the Framework and the details of their usage.</span></span> <span data-ttu-id="9d77a-104">La liste n’est pas exhaustive.</span><span class="sxs-lookup"><span data-stu-id="9d77a-104">The list is by no means exhaustive.</span></span> <span data-ttu-id="9d77a-105">Pour plus d’informations sur l’utilisation d’autres types d’exception d’infrastructure, consultez la documentation de référence .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="9d77a-105">Please refer to the .NET Framework reference documentation for usage of other Framework exception types.</span></span>

## <a name="exception-and-systemexception"></a><span data-ttu-id="9d77a-106">Exception et SystemException</span><span class="sxs-lookup"><span data-stu-id="9d77a-106">Exception and SystemException</span></span>
 <span data-ttu-id="9d77a-107">❌NE levez pas <xref:System.Exception?displayProperty=nameWithType> ou <xref:System.SystemException?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="9d77a-107">❌ DO NOT throw <xref:System.Exception?displayProperty=nameWithType> or <xref:System.SystemException?displayProperty=nameWithType>.</span></span>

 <span data-ttu-id="9d77a-108">❌N’interceptez pas `System.Exception` ou `System.SystemException` dans le code d’infrastructure, sauf si vous envisagez de lever à nouveau.</span><span class="sxs-lookup"><span data-stu-id="9d77a-108">❌ DO NOT catch `System.Exception` or `System.SystemException` in framework code, unless you intend to rethrow.</span></span>

 <span data-ttu-id="9d77a-109">❌Évitez d’intercepter `System.Exception` ou `System.SystemException` , sauf dans les gestionnaires d’exceptions de niveau supérieur.</span><span class="sxs-lookup"><span data-stu-id="9d77a-109">❌ AVOID catching `System.Exception` or `System.SystemException`, except in top-level exception handlers.</span></span>

## <a name="applicationexception"></a><span data-ttu-id="9d77a-110">ApplicationException</span><span class="sxs-lookup"><span data-stu-id="9d77a-110">ApplicationException</span></span>
 <span data-ttu-id="9d77a-111">❌NE levez pas ou ne dérivez pas de <xref:System.ApplicationException> .</span><span class="sxs-lookup"><span data-stu-id="9d77a-111">❌ DO NOT throw or derive from <xref:System.ApplicationException>.</span></span>

## <a name="invalidoperationexception"></a><span data-ttu-id="9d77a-112">InvalidOperationException</span><span class="sxs-lookup"><span data-stu-id="9d77a-112">InvalidOperationException</span></span>
 <span data-ttu-id="9d77a-113">✔️ Levez une exception <xref:System.InvalidOperationException> si l’objet est dans un État inapproprié.</span><span class="sxs-lookup"><span data-stu-id="9d77a-113">✔️ DO throw an <xref:System.InvalidOperationException> if the object is in an inappropriate state.</span></span>

## <a name="argumentexception-argumentnullexception-and-argumentoutofrangeexception"></a><span data-ttu-id="9d77a-114">ArgumentException, ArgumentNullException et ArgumentOutOfRangeException</span><span class="sxs-lookup"><span data-stu-id="9d77a-114">ArgumentException, ArgumentNullException, and ArgumentOutOfRangeException</span></span>
 <span data-ttu-id="9d77a-115">✔️ ne levez pas <xref:System.ArgumentException> d’exception ou un de ses sous-types si des arguments incorrects sont passés à un membre.</span><span class="sxs-lookup"><span data-stu-id="9d77a-115">✔️ DO throw <xref:System.ArgumentException> or one of its subtypes if bad arguments are passed to a member.</span></span> <span data-ttu-id="9d77a-116">Préférer le type d’exception le plus dérivé, le cas échéant.</span><span class="sxs-lookup"><span data-stu-id="9d77a-116">Prefer the most derived exception type, if applicable.</span></span>

 <span data-ttu-id="9d77a-117">✔️ définir la propriété lors de la levée de l' `ParamName` une des sous-classes de `ArgumentException` .</span><span class="sxs-lookup"><span data-stu-id="9d77a-117">✔️ DO set the `ParamName` property when throwing one of the subclasses of `ArgumentException`.</span></span>

 <span data-ttu-id="9d77a-118">Cette propriété représente le nom du paramètre qui a provoqué la levée de l’exception.</span><span class="sxs-lookup"><span data-stu-id="9d77a-118">This property represents the name of the parameter that caused the exception to be thrown.</span></span> <span data-ttu-id="9d77a-119">Notez que la propriété peut être définie à l’aide de l’une des surcharges de constructeur.</span><span class="sxs-lookup"><span data-stu-id="9d77a-119">Note that the property can be set using one of the constructor overloads.</span></span>

 <span data-ttu-id="9d77a-120">✔️ Utilisez `value` pour le nom du paramètre de valeur implicite des accesseurs set de propriété.</span><span class="sxs-lookup"><span data-stu-id="9d77a-120">✔️ DO use `value` for the name of the implicit value parameter of property setters.</span></span>

## <a name="nullreferenceexception-indexoutofrangeexception-and-accessviolationexception"></a><span data-ttu-id="9d77a-121">NullReferenceException, IndexOutOfRangeException et AccessViolationException</span><span class="sxs-lookup"><span data-stu-id="9d77a-121">NullReferenceException, IndexOutOfRangeException, and AccessViolationException</span></span>
 <span data-ttu-id="9d77a-122">❌N’autorisez pas les API pouvant être appelées publiquement à lever explicitement ou implicitement <xref:System.NullReferenceException> , <xref:System.AccessViolationException> ou <xref:System.IndexOutOfRangeException> .</span><span class="sxs-lookup"><span data-stu-id="9d77a-122">❌ DO NOT allow publicly callable APIs to explicitly or implicitly throw <xref:System.NullReferenceException>, <xref:System.AccessViolationException>, or <xref:System.IndexOutOfRangeException>.</span></span> <span data-ttu-id="9d77a-123">Ces exceptions sont réservées et levées par le moteur d’exécution et, dans la plupart des cas, indiquent un bogue.</span><span class="sxs-lookup"><span data-stu-id="9d77a-123">These exceptions are reserved and thrown by the execution engine and in most cases indicate a bug.</span></span>

 <span data-ttu-id="9d77a-124">Procédez à la vérification des arguments pour éviter de lever ces exceptions.</span><span class="sxs-lookup"><span data-stu-id="9d77a-124">Do argument checking to avoid throwing these exceptions.</span></span> <span data-ttu-id="9d77a-125">La levée de ces exceptions expose les détails d’implémentation de votre méthode qui peuvent changer au fil du temps.</span><span class="sxs-lookup"><span data-stu-id="9d77a-125">Throwing these exceptions exposes implementation details of your method that might change over time.</span></span>

## <a name="stackoverflowexception"></a><span data-ttu-id="9d77a-126">StackOverflowException</span><span class="sxs-lookup"><span data-stu-id="9d77a-126">StackOverflowException</span></span>
 <span data-ttu-id="9d77a-127">❌NE levez pas explicitement <xref:System.StackOverflowException> .</span><span class="sxs-lookup"><span data-stu-id="9d77a-127">❌ DO NOT explicitly throw <xref:System.StackOverflowException>.</span></span> <span data-ttu-id="9d77a-128">L’exception doit être levée explicitement uniquement par le CLR.</span><span class="sxs-lookup"><span data-stu-id="9d77a-128">The exception should be explicitly thrown only by the CLR.</span></span>

 <span data-ttu-id="9d77a-129">❌N’interceptez pas `StackOverflowException` .</span><span class="sxs-lookup"><span data-stu-id="9d77a-129">❌ DO NOT catch `StackOverflowException`.</span></span>

 <span data-ttu-id="9d77a-130">Il est presque impossible d’écrire du code managé qui reste cohérent en présence de dépassements de pile arbitraires.</span><span class="sxs-lookup"><span data-stu-id="9d77a-130">It is almost impossible to write managed code that remains consistent in the presence of arbitrary stack overflows.</span></span> <span data-ttu-id="9d77a-131">Les parties non managées du CLR restent cohérentes en utilisant des sondes pour déplacer les débordements de pile vers des emplacements bien définis plutôt que en sauvegardant des débordements de pile arbitraires.</span><span class="sxs-lookup"><span data-stu-id="9d77a-131">The unmanaged parts of the CLR remain consistent by using probes to move stack overflows to well-defined places rather than by backing out from arbitrary stack overflows.</span></span>

## <a name="outofmemoryexception"></a><span data-ttu-id="9d77a-132">OutOfMemoryException</span><span class="sxs-lookup"><span data-stu-id="9d77a-132">OutOfMemoryException</span></span>
 <span data-ttu-id="9d77a-133">❌NE levez pas explicitement <xref:System.OutOfMemoryException> .</span><span class="sxs-lookup"><span data-stu-id="9d77a-133">❌ DO NOT explicitly throw <xref:System.OutOfMemoryException>.</span></span> <span data-ttu-id="9d77a-134">Cette exception doit être levée uniquement par l’infrastructure CLR.</span><span class="sxs-lookup"><span data-stu-id="9d77a-134">This exception is to be thrown only by the CLR infrastructure.</span></span>

## <a name="comexception-sehexception-and-executionengineexception"></a><span data-ttu-id="9d77a-135">COMException, SEHException et ExecutionEngineException</span><span class="sxs-lookup"><span data-stu-id="9d77a-135">ComException, SEHException, and ExecutionEngineException</span></span>
 <span data-ttu-id="9d77a-136">❌NE levez pas explicitement <xref:System.Runtime.InteropServices.COMException> , <xref:System.ExecutionEngineException> et <xref:System.Runtime.InteropServices.SEHException> .</span><span class="sxs-lookup"><span data-stu-id="9d77a-136">❌ DO NOT explicitly throw <xref:System.Runtime.InteropServices.COMException>,  <xref:System.ExecutionEngineException>, and <xref:System.Runtime.InteropServices.SEHException>.</span></span> <span data-ttu-id="9d77a-137">Ces exceptions doivent être levées uniquement par l’infrastructure CLR.</span><span class="sxs-lookup"><span data-stu-id="9d77a-137">These exceptions are to be thrown only by the CLR infrastructure.</span></span>

 <span data-ttu-id="9d77a-138">*Parties © 2005, 2009 Microsoft Corporation. Tous droits réservés.*</span><span class="sxs-lookup"><span data-stu-id="9d77a-138">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="9d77a-139">*Réimprimé avec l’autorisation de Pearson Education, Inc. et extrait de [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) par Krzysztof Cwalina et Brad Abrams, publié le 22 octobre 2008 par Addison-Wesley Professional dans le cadre de la série sur le développement Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="9d77a-139">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="9d77a-140">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9d77a-140">See also</span></span>

- [<span data-ttu-id="9d77a-141">Directives de conception d’infrastructure</span><span class="sxs-lookup"><span data-stu-id="9d77a-141">Framework Design Guidelines</span></span>](index.md)
- [<span data-ttu-id="9d77a-142">Instructions de conception pour les exceptions</span><span class="sxs-lookup"><span data-stu-id="9d77a-142">Design Guidelines for Exceptions</span></span>](exceptions.md)
