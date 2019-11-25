---
title: End <keyword>, instruction
ms.date: 07/20/2015
f1_keywords:
- vb.EndDefinition
helpviewer_keywords:
- End keyword [Visual Basic]
ms.assetid: 42d6e088-ab0f-4cda-88e8-fdce3e5fcf4f
ms.openlocfilehash: 87f4724cc036e6e0bdf0b558854a4034f45b9ab5
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74343734"
---
# <a name="end-keyword-statement-visual-basic"></a><span data-ttu-id="cd4e3-102">End \<keyword> Statement (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cd4e3-102">End \<keyword> Statement (Visual Basic)</span></span>

<span data-ttu-id="cd4e3-103">When followed by an additional keyword, terminates the definition of the statement block introduced by that keyword.</span><span class="sxs-lookup"><span data-stu-id="cd4e3-103">When followed by an additional keyword, terminates the definition of the statement block introduced by that keyword.</span></span>

## <a name="syntax"></a><span data-ttu-id="cd4e3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cd4e3-104">Syntax</span></span>

```vb
End AddHandler
End Class
End Enum
End Event
End Function
End Get
End If
End Interface
End Module
End Namespace
End Operator
End Property
End RaiseEvent  
End RemoveHandler  
End Select
End Set
End Structure
End Sub
End SyncLock
End Try
End While
End With  
```  
  
## <a name="parts"></a><span data-ttu-id="cd4e3-105">Composants</span><span class="sxs-lookup"><span data-stu-id="cd4e3-105">Parts</span></span>

|<span data-ttu-id="cd4e3-106">Élément</span><span class="sxs-lookup"><span data-stu-id="cd4e3-106">Part</span></span>|<span data-ttu-id="cd4e3-107">Description</span><span class="sxs-lookup"><span data-stu-id="cd4e3-107">Description</span></span>|
|---|---|
|`End`|<span data-ttu-id="cd4e3-108">Requis.</span><span class="sxs-lookup"><span data-stu-id="cd4e3-108">Required.</span></span> <span data-ttu-id="cd4e3-109">Terminates the definition of the programming element.</span><span class="sxs-lookup"><span data-stu-id="cd4e3-109">Terminates the definition of the programming element.</span></span>|
|`AddHandler`|<span data-ttu-id="cd4e3-110">Required to terminate an `AddHandler` accessor begun by a matching `AddHandler` statement in a custom [Event Statement](event-statement.md).</span><span class="sxs-lookup"><span data-stu-id="cd4e3-110">Required to terminate an `AddHandler` accessor begun by a matching `AddHandler` statement in a custom [Event Statement](event-statement.md).</span></span>|
|`Class`|<span data-ttu-id="cd4e3-111">Required to terminate a class definition begun by a matching [Class Statement](class-statement.md).</span><span class="sxs-lookup"><span data-stu-id="cd4e3-111">Required to terminate a class definition begun by a matching [Class Statement](class-statement.md).</span></span>|
|`Enum`|<span data-ttu-id="cd4e3-112">Required to terminate an enumeration definition begun by a matching [Enum Statement](enum-statement.md).</span><span class="sxs-lookup"><span data-stu-id="cd4e3-112">Required to terminate an enumeration definition begun by a matching [Enum Statement](enum-statement.md).</span></span>|
|`Event`|<span data-ttu-id="cd4e3-113">Required to terminate a `Custom` event definition begun by a matching [Event Statement](event-statement.md).</span><span class="sxs-lookup"><span data-stu-id="cd4e3-113">Required to terminate a `Custom` event definition begun by a matching [Event Statement](event-statement.md).</span></span>|  
|`Function`|<span data-ttu-id="cd4e3-114">Required to terminate a `Function` procedure definition begun by a matching [Function Statement](function-statement.md).</span><span class="sxs-lookup"><span data-stu-id="cd4e3-114">Required to terminate a `Function` procedure definition begun by a matching [Function Statement](function-statement.md).</span></span> <span data-ttu-id="cd4e3-115">If execution encounters an `End Function` statement, control returns to the calling code.</span><span class="sxs-lookup"><span data-stu-id="cd4e3-115">If execution encounters an `End Function` statement, control returns to the calling code.</span></span>|
|`Get`|<span data-ttu-id="cd4e3-116">Required to terminate a `Property` procedure definition begun by a matching [Get Statement](get-statement.md).</span><span class="sxs-lookup"><span data-stu-id="cd4e3-116">Required to terminate a `Property` procedure definition begun by a matching [Get Statement](get-statement.md).</span></span> <span data-ttu-id="cd4e3-117">If execution encounters an `End Get` statement, control returns to the statement requesting the property's value.</span><span class="sxs-lookup"><span data-stu-id="cd4e3-117">If execution encounters an `End Get` statement, control returns to the statement requesting the property's value.</span></span>|
|`If`|<span data-ttu-id="cd4e3-118">Required to terminate an `If`...`Then`...`Else` block definition begun by a matching `If` statement.</span><span class="sxs-lookup"><span data-stu-id="cd4e3-118">Required to terminate an `If`...`Then`...`Else` block definition begun by a matching `If` statement.</span></span> <span data-ttu-id="cd4e3-119">See [If...Then...Else Statement](if-then-else-statement.md).</span><span class="sxs-lookup"><span data-stu-id="cd4e3-119">See [If...Then...Else Statement](if-then-else-statement.md).</span></span>|
|`Interface`|<span data-ttu-id="cd4e3-120">Required to terminate an interface definition begun by a matching [Interface Statement](interface-statement.md).</span><span class="sxs-lookup"><span data-stu-id="cd4e3-120">Required to terminate an interface definition begun by a matching [Interface Statement](interface-statement.md).</span></span>|
|`Module`|<span data-ttu-id="cd4e3-121">Required to terminate a module definition begun by a matching [Module Statement](module-statement.md).</span><span class="sxs-lookup"><span data-stu-id="cd4e3-121">Required to terminate a module definition begun by a matching [Module Statement](module-statement.md).</span></span>|
|`Namespace`|<span data-ttu-id="cd4e3-122">Required to terminate a namespace definition begun by a matching [Namespace Statement](namespace-statement.md).</span><span class="sxs-lookup"><span data-stu-id="cd4e3-122">Required to terminate a namespace definition begun by a matching [Namespace Statement](namespace-statement.md).</span></span>|
|`Operator`|<span data-ttu-id="cd4e3-123">Required to terminate an operator definition begun by a matching [Operator Statement](operator-statement.md).</span><span class="sxs-lookup"><span data-stu-id="cd4e3-123">Required to terminate an operator definition begun by a matching [Operator Statement](operator-statement.md).</span></span>|
|`Property`|<span data-ttu-id="cd4e3-124">Required to terminate a property definition begun by a matching [Property Statement](property-statement.md).</span><span class="sxs-lookup"><span data-stu-id="cd4e3-124">Required to terminate a property definition begun by a matching [Property Statement](property-statement.md).</span></span>|
|`RaiseEvent`|<span data-ttu-id="cd4e3-125">Required to terminate a `RaiseEvent` accessor begun by a matching `RaiseEvent` statement in a custom [Event Statement](event-statement.md).</span><span class="sxs-lookup"><span data-stu-id="cd4e3-125">Required to terminate a `RaiseEvent` accessor begun by a matching `RaiseEvent` statement in a custom [Event Statement](event-statement.md).</span></span>|
|`RemoveHandler`|<span data-ttu-id="cd4e3-126">Required to terminate a `RemoveHandler` accessor begun by a matching `RemoveHandler` statement in a custom [Event Statement](event-statement.md).</span><span class="sxs-lookup"><span data-stu-id="cd4e3-126">Required to terminate a `RemoveHandler` accessor begun by a matching `RemoveHandler` statement in a custom [Event Statement](event-statement.md).</span></span>|
|`Select`|<span data-ttu-id="cd4e3-127">Required to terminate a `Select`...`Case` block definition begun by a matching `Select` statement.</span><span class="sxs-lookup"><span data-stu-id="cd4e3-127">Required to terminate a `Select`...`Case` block definition begun by a matching `Select` statement.</span></span> <span data-ttu-id="cd4e3-128">See [Select...Case Statement](select-case-statement.md).</span><span class="sxs-lookup"><span data-stu-id="cd4e3-128">See [Select...Case Statement](select-case-statement.md).</span></span>  
|`Set`|<span data-ttu-id="cd4e3-129">Required to terminate a `Property` procedure definition begun by a matching [Set Statement](set-statement.md).</span><span class="sxs-lookup"><span data-stu-id="cd4e3-129">Required to terminate a `Property` procedure definition begun by a matching [Set Statement](set-statement.md).</span></span> <span data-ttu-id="cd4e3-130">If execution encounters an `End Set` statement, control returns to the statement setting the property's value.</span><span class="sxs-lookup"><span data-stu-id="cd4e3-130">If execution encounters an `End Set` statement, control returns to the statement setting the property's value.</span></span>  
|`Structure`|<span data-ttu-id="cd4e3-131">Required to terminate a structure definition begun by a matching [Structure Statement](structure-statement.md).</span><span class="sxs-lookup"><span data-stu-id="cd4e3-131">Required to terminate a structure definition begun by a matching [Structure Statement](structure-statement.md).</span></span>  
|`Sub`|<span data-ttu-id="cd4e3-132">Required to terminate a `Sub` procedure definition begun by a matching [Sub Statement](sub-statement.md).</span><span class="sxs-lookup"><span data-stu-id="cd4e3-132">Required to terminate a `Sub` procedure definition begun by a matching [Sub Statement](sub-statement.md).</span></span> <span data-ttu-id="cd4e3-133">If execution encounters an `End Sub` statement, control returns to the calling code.</span><span class="sxs-lookup"><span data-stu-id="cd4e3-133">If execution encounters an `End Sub` statement, control returns to the calling code.</span></span>  
|`SyncLock`|<span data-ttu-id="cd4e3-134">Required to terminate a `SyncLock` block definition begun by a matching `SyncLock` statement.</span><span class="sxs-lookup"><span data-stu-id="cd4e3-134">Required to terminate a `SyncLock` block definition begun by a matching `SyncLock` statement.</span></span> <span data-ttu-id="cd4e3-135">See [SyncLock Statement](synclock-statement.md).</span><span class="sxs-lookup"><span data-stu-id="cd4e3-135">See [SyncLock Statement](synclock-statement.md).</span></span>  
|`Try`|<span data-ttu-id="cd4e3-136">Required to terminate a `Try`...`Catch`...`Finally` block definition begun by a matching `Try` statement.</span><span class="sxs-lookup"><span data-stu-id="cd4e3-136">Required to terminate a `Try`...`Catch`...`Finally` block definition begun by a matching `Try` statement.</span></span> <span data-ttu-id="cd4e3-137">See [Try...Catch...Finally Statement](try-catch-finally-statement.md).</span><span class="sxs-lookup"><span data-stu-id="cd4e3-137">See [Try...Catch...Finally Statement](try-catch-finally-statement.md).</span></span>  
|`While`|<span data-ttu-id="cd4e3-138">Required to terminate a `While` loop definition begun by a matching `While` statement.</span><span class="sxs-lookup"><span data-stu-id="cd4e3-138">Required to terminate a `While` loop definition begun by a matching `While` statement.</span></span> <span data-ttu-id="cd4e3-139">See [While...End While Statement](while-end-while-statement.md).</span><span class="sxs-lookup"><span data-stu-id="cd4e3-139">See [While...End While Statement](while-end-while-statement.md).</span></span>  
|`With`| <span data-ttu-id="cd4e3-140">Required to terminate a `With` block definition begun by a matching `With` statement.</span><span class="sxs-lookup"><span data-stu-id="cd4e3-140">Required to terminate a `With` block definition begun by a matching `With` statement.</span></span> <span data-ttu-id="cd4e3-141">See [With...End With Statement](with-end-with-statement.md).</span><span class="sxs-lookup"><span data-stu-id="cd4e3-141">See [With...End With Statement](with-end-with-statement.md).</span></span>  
|||
  
## <a name="directives"></a><span data-ttu-id="cd4e3-142">Directives</span><span class="sxs-lookup"><span data-stu-id="cd4e3-142">Directives</span></span>

<span data-ttu-id="cd4e3-143">When preceded by a number sign (`#`), the `End` keyword terminates a preprocessing block introduced by the corresponding directive.</span><span class="sxs-lookup"><span data-stu-id="cd4e3-143">When preceded by a number sign (`#`), the `End` keyword terminates a preprocessing block introduced by the corresponding directive.</span></span>  

```vb
#End ExternalSource
#End If
#End Region
```

|<span data-ttu-id="cd4e3-144">Élément</span><span class="sxs-lookup"><span data-stu-id="cd4e3-144">Part</span></span>|<span data-ttu-id="cd4e3-145">Description</span><span class="sxs-lookup"><span data-stu-id="cd4e3-145">Description</span></span>|
|---|---|
|`#End`|<span data-ttu-id="cd4e3-146">Requis.</span><span class="sxs-lookup"><span data-stu-id="cd4e3-146">Required.</span></span> <span data-ttu-id="cd4e3-147">Terminates the definition of the preprocessing block.</span><span class="sxs-lookup"><span data-stu-id="cd4e3-147">Terminates the definition of the preprocessing block.</span></span>|
|`ExternalSource`|<span data-ttu-id="cd4e3-148">Required to terminate an external source block begun by a matching [#ExternalSource Directive](../directives/externalsource-directive.md).</span><span class="sxs-lookup"><span data-stu-id="cd4e3-148">Required to terminate an external source block begun by a matching [#ExternalSource Directive](../directives/externalsource-directive.md).</span></span>|
|`If`|<span data-ttu-id="cd4e3-149">Required to terminate a conditional compilation block begun by a matching `#If` directive.</span><span class="sxs-lookup"><span data-stu-id="cd4e3-149">Required to terminate a conditional compilation block begun by a matching `#If` directive.</span></span> <span data-ttu-id="cd4e3-150">See [#If...Then...#Else Directives](../directives/if-then-else-directives.md).</span><span class="sxs-lookup"><span data-stu-id="cd4e3-150">See [#If...Then...#Else Directives](../directives/if-then-else-directives.md).</span></span>|
|`Region`|<span data-ttu-id="cd4e3-151">Required to terminate a source region block begun by a matching [#Region Directive](../directives/region-directive.md).</span><span class="sxs-lookup"><span data-stu-id="cd4e3-151">Required to terminate a source region block begun by a matching [#Region Directive](../directives/region-directive.md).</span></span>|
|||

## <a name="remarks"></a><span data-ttu-id="cd4e3-152">Notes</span><span class="sxs-lookup"><span data-stu-id="cd4e3-152">Remarks</span></span>

<span data-ttu-id="cd4e3-153">The [End Statement](end-statement.md), without an additional keyword, terminates execution immediately.</span><span class="sxs-lookup"><span data-stu-id="cd4e3-153">The [End Statement](end-statement.md), without an additional keyword, terminates execution immediately.</span></span>

## <a name="smart-device-developer-notes"></a><span data-ttu-id="cd4e3-154">Smart Device Developer Notes</span><span class="sxs-lookup"><span data-stu-id="cd4e3-154">Smart Device Developer Notes</span></span>  

<span data-ttu-id="cd4e3-155">The `End` statement, without an additional keyword, is not supported.</span><span class="sxs-lookup"><span data-stu-id="cd4e3-155">The `End` statement, without an additional keyword, is not supported.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cd4e3-156">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="cd4e3-156">See also</span></span>

- [<span data-ttu-id="cd4e3-157">End (instruction)</span><span class="sxs-lookup"><span data-stu-id="cd4e3-157">End Statement</span></span>](end-statement.md)
