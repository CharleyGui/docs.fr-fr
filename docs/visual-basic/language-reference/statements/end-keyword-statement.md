---
title: End <keyword> (instruction)
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
# <a name="end-keyword-statement-visual-basic"></a><span data-ttu-id="77b09-102">End \<mot clé >, instruction (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="77b09-102">End \<keyword> Statement (Visual Basic)</span></span>

<span data-ttu-id="77b09-103">Lorsqu’il est suivi d’un mot clé supplémentaire, termine la définition du bloc d’instructions introduit par ce mot clé.</span><span class="sxs-lookup"><span data-stu-id="77b09-103">When followed by an additional keyword, terminates the definition of the statement block introduced by that keyword.</span></span>

## <a name="syntax"></a><span data-ttu-id="77b09-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="77b09-104">Syntax</span></span>

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
  
## <a name="parts"></a><span data-ttu-id="77b09-105">Composants</span><span class="sxs-lookup"><span data-stu-id="77b09-105">Parts</span></span>

|<span data-ttu-id="77b09-106">Élément</span><span class="sxs-lookup"><span data-stu-id="77b09-106">Part</span></span>|<span data-ttu-id="77b09-107">Description</span><span class="sxs-lookup"><span data-stu-id="77b09-107">Description</span></span>|
|---|---|
|`End`|<span data-ttu-id="77b09-108">Requis.</span><span class="sxs-lookup"><span data-stu-id="77b09-108">Required.</span></span> <span data-ttu-id="77b09-109">Termine la définition de l’élément de programmation.</span><span class="sxs-lookup"><span data-stu-id="77b09-109">Terminates the definition of the programming element.</span></span>|
|`AddHandler`|<span data-ttu-id="77b09-110">Requis pour terminer un accesseur `AddHandler` commencé par une instruction `AddHandler` correspondante dans une [instruction d’événement](event-statement.md)personnalisée.</span><span class="sxs-lookup"><span data-stu-id="77b09-110">Required to terminate an `AddHandler` accessor begun by a matching `AddHandler` statement in a custom [Event Statement](event-statement.md).</span></span>|
|`Class`|<span data-ttu-id="77b09-111">Requis pour terminer une définition de classe commencée par une [instruction de classe](class-statement.md)correspondante.</span><span class="sxs-lookup"><span data-stu-id="77b09-111">Required to terminate a class definition begun by a matching [Class Statement](class-statement.md).</span></span>|
|`Enum`|<span data-ttu-id="77b09-112">Requis pour terminer une définition d’énumération commencée par une [instruction enum](enum-statement.md)correspondante.</span><span class="sxs-lookup"><span data-stu-id="77b09-112">Required to terminate an enumeration definition begun by a matching [Enum Statement](enum-statement.md).</span></span>|
|`Event`|<span data-ttu-id="77b09-113">Requis pour mettre fin à une définition d’événement `Custom` commencée par une [instruction Event](event-statement.md)correspondante.</span><span class="sxs-lookup"><span data-stu-id="77b09-113">Required to terminate a `Custom` event definition begun by a matching [Event Statement](event-statement.md).</span></span>|  
|`Function`|<span data-ttu-id="77b09-114">Requis pour terminer une définition de procédure `Function` commencée par une [instruction de fonction](function-statement.md)correspondante.</span><span class="sxs-lookup"><span data-stu-id="77b09-114">Required to terminate a `Function` procedure definition begun by a matching [Function Statement](function-statement.md).</span></span> <span data-ttu-id="77b09-115">Si l’exécution rencontre une instruction `End Function`, le contrôle retourne au code appelant.</span><span class="sxs-lookup"><span data-stu-id="77b09-115">If execution encounters an `End Function` statement, control returns to the calling code.</span></span>|
|`Get`|<span data-ttu-id="77b09-116">Requis pour terminer une définition de procédure `Property` commencée par une [instruction d’extraction](get-statement.md)correspondante.</span><span class="sxs-lookup"><span data-stu-id="77b09-116">Required to terminate a `Property` procedure definition begun by a matching [Get Statement](get-statement.md).</span></span> <span data-ttu-id="77b09-117">Si l’exécution rencontre une instruction `End Get`, le contrôle retourne à l’instruction qui demande la valeur de la propriété.</span><span class="sxs-lookup"><span data-stu-id="77b09-117">If execution encounters an `End Get` statement, control returns to the statement requesting the property's value.</span></span>|
|`If`|<span data-ttu-id="77b09-118">Requis pour mettre fin à une définition de bloc `If`...`Then`...`Else` commencé par une instruction `If` correspondante.</span><span class="sxs-lookup"><span data-stu-id="77b09-118">Required to terminate an `If`...`Then`...`Else` block definition begun by a matching `If` statement.</span></span> <span data-ttu-id="77b09-119">Voir [si... Puis... Instruction Else](if-then-else-statement.md).</span><span class="sxs-lookup"><span data-stu-id="77b09-119">See [If...Then...Else Statement](if-then-else-statement.md).</span></span>|
|`Interface`|<span data-ttu-id="77b09-120">Requis pour terminer une définition d’interface commencée par une [instruction d’interface](interface-statement.md)correspondante.</span><span class="sxs-lookup"><span data-stu-id="77b09-120">Required to terminate an interface definition begun by a matching [Interface Statement](interface-statement.md).</span></span>|
|`Module`|<span data-ttu-id="77b09-121">Requis pour terminer une définition de module commencée par une [instruction de module](module-statement.md)correspondante.</span><span class="sxs-lookup"><span data-stu-id="77b09-121">Required to terminate a module definition begun by a matching [Module Statement](module-statement.md).</span></span>|
|`Namespace`|<span data-ttu-id="77b09-122">Requis pour terminer une définition d’espace de noms commencée par une [instruction d’espace de noms](namespace-statement.md)correspondante.</span><span class="sxs-lookup"><span data-stu-id="77b09-122">Required to terminate a namespace definition begun by a matching [Namespace Statement](namespace-statement.md).</span></span>|
|`Operator`|<span data-ttu-id="77b09-123">Requis pour terminer une définition d’opérateur commencée par une [instruction d’opérateur](operator-statement.md)correspondante.</span><span class="sxs-lookup"><span data-stu-id="77b09-123">Required to terminate an operator definition begun by a matching [Operator Statement](operator-statement.md).</span></span>|
|`Property`|<span data-ttu-id="77b09-124">Requis pour terminer une définition de propriété commencée par une [instruction de propriété](property-statement.md)correspondante.</span><span class="sxs-lookup"><span data-stu-id="77b09-124">Required to terminate a property definition begun by a matching [Property Statement](property-statement.md).</span></span>|
|`RaiseEvent`|<span data-ttu-id="77b09-125">Requis pour terminer un accesseur `RaiseEvent` commencé par une instruction `RaiseEvent` correspondante dans une [instruction d’événement](event-statement.md)personnalisée.</span><span class="sxs-lookup"><span data-stu-id="77b09-125">Required to terminate a `RaiseEvent` accessor begun by a matching `RaiseEvent` statement in a custom [Event Statement](event-statement.md).</span></span>|
|`RemoveHandler`|<span data-ttu-id="77b09-126">Requis pour terminer un accesseur `RemoveHandler` commencé par une instruction `RemoveHandler` correspondante dans une [instruction d’événement](event-statement.md)personnalisée.</span><span class="sxs-lookup"><span data-stu-id="77b09-126">Required to terminate a `RemoveHandler` accessor begun by a matching `RemoveHandler` statement in a custom [Event Statement](event-statement.md).</span></span>|
|`Select`|<span data-ttu-id="77b09-127">Requis pour mettre fin à une définition de bloc `Select`...`Case` commencé par une instruction `Select` correspondante.</span><span class="sxs-lookup"><span data-stu-id="77b09-127">Required to terminate a `Select`...`Case` block definition begun by a matching `Select` statement.</span></span> <span data-ttu-id="77b09-128">Voir [Sélectionner... Instruction case](select-case-statement.md).</span><span class="sxs-lookup"><span data-stu-id="77b09-128">See [Select...Case Statement](select-case-statement.md).</span></span>  
|`Set`|<span data-ttu-id="77b09-129">Requis pour terminer une définition de procédure `Property` commencée par une [instruction Set](set-statement.md)correspondante.</span><span class="sxs-lookup"><span data-stu-id="77b09-129">Required to terminate a `Property` procedure definition begun by a matching [Set Statement](set-statement.md).</span></span> <span data-ttu-id="77b09-130">Si l’exécution rencontre une instruction `End Set`, le contrôle retourne à l’instruction qui définit la valeur de la propriété.</span><span class="sxs-lookup"><span data-stu-id="77b09-130">If execution encounters an `End Set` statement, control returns to the statement setting the property's value.</span></span>  
|`Structure`|<span data-ttu-id="77b09-131">Requis pour terminer une définition de structure commencée par une [instruction de structure](structure-statement.md)correspondante.</span><span class="sxs-lookup"><span data-stu-id="77b09-131">Required to terminate a structure definition begun by a matching [Structure Statement](structure-statement.md).</span></span>  
|`Sub`|<span data-ttu-id="77b09-132">Requis pour terminer une définition de procédure `Sub` commencée par une [sous-instruction](sub-statement.md)correspondante.</span><span class="sxs-lookup"><span data-stu-id="77b09-132">Required to terminate a `Sub` procedure definition begun by a matching [Sub Statement](sub-statement.md).</span></span> <span data-ttu-id="77b09-133">Si l’exécution rencontre une instruction `End Sub`, le contrôle retourne au code appelant.</span><span class="sxs-lookup"><span data-stu-id="77b09-133">If execution encounters an `End Sub` statement, control returns to the calling code.</span></span>  
|`SyncLock`|<span data-ttu-id="77b09-134">Requis pour terminer une définition de bloc `SyncLock` commencée par une instruction `SyncLock` correspondante.</span><span class="sxs-lookup"><span data-stu-id="77b09-134">Required to terminate a `SyncLock` block definition begun by a matching `SyncLock` statement.</span></span> <span data-ttu-id="77b09-135">Consultez [instruction SyncLock](synclock-statement.md).</span><span class="sxs-lookup"><span data-stu-id="77b09-135">See [SyncLock Statement](synclock-statement.md).</span></span>  
|`Try`|<span data-ttu-id="77b09-136">Requis pour mettre fin à une définition de bloc `Try`...`Catch`...`Finally` commencé par une instruction `Try` correspondante.</span><span class="sxs-lookup"><span data-stu-id="77b09-136">Required to terminate a `Try`...`Catch`...`Finally` block definition begun by a matching `Try` statement.</span></span> <span data-ttu-id="77b09-137">Voir [essayer... Catch... Finally, instruction](try-catch-finally-statement.md).</span><span class="sxs-lookup"><span data-stu-id="77b09-137">See [Try...Catch...Finally Statement](try-catch-finally-statement.md).</span></span>  
|`While`|<span data-ttu-id="77b09-138">Requis pour terminer une définition de boucle `While` commencée par une instruction `While` correspondante.</span><span class="sxs-lookup"><span data-stu-id="77b09-138">Required to terminate a `While` loop definition begun by a matching `While` statement.</span></span> <span data-ttu-id="77b09-139">Voir [tout cela... Instruction End While](while-end-while-statement.md).</span><span class="sxs-lookup"><span data-stu-id="77b09-139">See [While...End While Statement](while-end-while-statement.md).</span></span>  
|`With`| <span data-ttu-id="77b09-140">Requis pour terminer une définition de bloc `With` commencée par une instruction `With` correspondante.</span><span class="sxs-lookup"><span data-stu-id="77b09-140">Required to terminate a `With` block definition begun by a matching `With` statement.</span></span> <span data-ttu-id="77b09-141">Voir [avec... End With](with-end-with-statement.md).</span><span class="sxs-lookup"><span data-stu-id="77b09-141">See [With...End With Statement](with-end-with-statement.md).</span></span>  
|||
  
## <a name="directives"></a><span data-ttu-id="77b09-142">Directives</span><span class="sxs-lookup"><span data-stu-id="77b09-142">Directives</span></span>

<span data-ttu-id="77b09-143">Lorsqu’il est précédé d’un signe dièse (`#`), le mot clé `End` met fin à un bloc de prétraitement introduit par la directive correspondante.</span><span class="sxs-lookup"><span data-stu-id="77b09-143">When preceded by a number sign (`#`), the `End` keyword terminates a preprocessing block introduced by the corresponding directive.</span></span>  

```vb
#End ExternalSource
#End If
#End Region
```

|<span data-ttu-id="77b09-144">Élément</span><span class="sxs-lookup"><span data-stu-id="77b09-144">Part</span></span>|<span data-ttu-id="77b09-145">Description</span><span class="sxs-lookup"><span data-stu-id="77b09-145">Description</span></span>|
|---|---|
|`#End`|<span data-ttu-id="77b09-146">Requis.</span><span class="sxs-lookup"><span data-stu-id="77b09-146">Required.</span></span> <span data-ttu-id="77b09-147">Termine la définition du bloc de prétraitement.</span><span class="sxs-lookup"><span data-stu-id="77b09-147">Terminates the definition of the preprocessing block.</span></span>|
|`ExternalSource`|<span data-ttu-id="77b09-148">Requis pour terminer un bloc source externe commencé par une [Directive #ExternalSource](../directives/externalsource-directive.md)correspondante.</span><span class="sxs-lookup"><span data-stu-id="77b09-148">Required to terminate an external source block begun by a matching [#ExternalSource Directive](../directives/externalsource-directive.md).</span></span>|
|`If`|<span data-ttu-id="77b09-149">Requis pour terminer un bloc de compilation conditionnelle commencé par une directive de `#If` correspondante.</span><span class="sxs-lookup"><span data-stu-id="77b09-149">Required to terminate a conditional compilation block begun by a matching `#If` directive.</span></span> <span data-ttu-id="77b09-150">Voir [#If... Then... #Else directives](../directives/if-then-else-directives.md).</span><span class="sxs-lookup"><span data-stu-id="77b09-150">See [#If...Then...#Else Directives](../directives/if-then-else-directives.md).</span></span>|
|`Region`|<span data-ttu-id="77b09-151">Requis pour terminer un bloc de région source commencé par une [directive de #Region](../directives/region-directive.md)correspondante.</span><span class="sxs-lookup"><span data-stu-id="77b09-151">Required to terminate a source region block begun by a matching [#Region Directive](../directives/region-directive.md).</span></span>|
|||

## <a name="remarks"></a><span data-ttu-id="77b09-152">Notes</span><span class="sxs-lookup"><span data-stu-id="77b09-152">Remarks</span></span>

<span data-ttu-id="77b09-153">L' [instruction end](end-statement.md), sans mot clé supplémentaire, termine immédiatement l’exécution.</span><span class="sxs-lookup"><span data-stu-id="77b09-153">The [End Statement](end-statement.md), without an additional keyword, terminates execution immediately.</span></span>

## <a name="smart-device-developer-notes"></a><span data-ttu-id="77b09-154">Notes de développement Smart Device</span><span class="sxs-lookup"><span data-stu-id="77b09-154">Smart Device Developer Notes</span></span>  

<span data-ttu-id="77b09-155">L’instruction `End`, sans mot clé supplémentaire, n’est pas prise en charge.</span><span class="sxs-lookup"><span data-stu-id="77b09-155">The `End` statement, without an additional keyword, is not supported.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="77b09-156">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="77b09-156">See also</span></span>

- [<span data-ttu-id="77b09-157">End (instruction)</span><span class="sxs-lookup"><span data-stu-id="77b09-157">End Statement</span></span>](end-statement.md)
