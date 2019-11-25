---
title: Conventions de codage
ms.date: 07/20/2015
helpviewer_keywords:
- coding conventions [Visual Basic], Visual Basic
- examples [Visual Basic], coding conventions
- Visual Basic code, conventions
ms.assetid: c1df130b-fec6-49a5-becf-0a7e494a1d0f
ms.openlocfilehash: 36cd3a927d2fdf197e6b496d9308fc43a555d59b
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346151"
---
# <a name="visual-basic-coding-conventions"></a><span data-ttu-id="c2951-102">Conventions de codage Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c2951-102">Visual Basic Coding Conventions</span></span>
<span data-ttu-id="c2951-103">Microsoft develops samples and documentation that follow the guidelines in this topic.</span><span class="sxs-lookup"><span data-stu-id="c2951-103">Microsoft develops samples and documentation that follow the guidelines in this topic.</span></span> <span data-ttu-id="c2951-104">If you follow the same coding conventions, you may gain the following benefits:</span><span class="sxs-lookup"><span data-stu-id="c2951-104">If you follow the same coding conventions, you may gain the following benefits:</span></span>  
  
- <span data-ttu-id="c2951-105">Your code will have a consistent look, so that readers can better focus on content, not layout.</span><span class="sxs-lookup"><span data-stu-id="c2951-105">Your code will have a consistent look, so that readers can better focus on content, not layout.</span></span>  
  
- <span data-ttu-id="c2951-106">Readers understand your code more quickly because they can make assumptions based on previous experience.</span><span class="sxs-lookup"><span data-stu-id="c2951-106">Readers understand your code more quickly because they can make assumptions based on previous experience.</span></span>  
  
- <span data-ttu-id="c2951-107">You can copy, change, and maintain the code more easily.</span><span class="sxs-lookup"><span data-stu-id="c2951-107">You can copy, change, and maintain the code more easily.</span></span>  
  
- <span data-ttu-id="c2951-108">You help ensure that your code demonstrates "best practices" for Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="c2951-108">You help ensure that your code demonstrates "best practices" for Visual Basic.</span></span>  
  
## <a name="naming-conventions"></a><span data-ttu-id="c2951-109">Conventions d'affectation de noms</span><span class="sxs-lookup"><span data-stu-id="c2951-109">Naming Conventions</span></span>  
  
- <span data-ttu-id="c2951-110">For information about naming guidelines, see [Naming Guidelines](../../../standard/design-guidelines/naming-guidelines.md) topic.</span><span class="sxs-lookup"><span data-stu-id="c2951-110">For information about naming guidelines, see [Naming Guidelines](../../../standard/design-guidelines/naming-guidelines.md) topic.</span></span>  
  
- <span data-ttu-id="c2951-111">Do not use "My" or "my" as part of a variable name.</span><span class="sxs-lookup"><span data-stu-id="c2951-111">Do not use "My" or "my" as part of a variable name.</span></span> <span data-ttu-id="c2951-112">This practice creates confusion with the `My` objects.</span><span class="sxs-lookup"><span data-stu-id="c2951-112">This practice creates confusion with the `My` objects.</span></span>  
  
- <span data-ttu-id="c2951-113">You do not have to change the names of objects in auto-generated code to make them fit the guidelines.</span><span class="sxs-lookup"><span data-stu-id="c2951-113">You do not have to change the names of objects in auto-generated code to make them fit the guidelines.</span></span>  
  
## <a name="layout-conventions"></a><span data-ttu-id="c2951-114">Conventions de disposition</span><span class="sxs-lookup"><span data-stu-id="c2951-114">Layout Conventions</span></span>  
  
- <span data-ttu-id="c2951-115">Insert tabs as spaces, and use smart indenting with four-space indents.</span><span class="sxs-lookup"><span data-stu-id="c2951-115">Insert tabs as spaces, and use smart indenting with four-space indents.</span></span>  
  
- <span data-ttu-id="c2951-116">Use **Pretty listing (reformatting) of code** to reformat your code in the code editor.</span><span class="sxs-lookup"><span data-stu-id="c2951-116">Use **Pretty listing (reformatting) of code** to reformat your code in the code editor.</span></span> <span data-ttu-id="c2951-117">For more information, see [Options, Text Editor, Basic (Visual Basic)](/visualstudio/ide/reference/options-text-editor-basic-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="c2951-117">For more information, see [Options, Text Editor, Basic (Visual Basic)](/visualstudio/ide/reference/options-text-editor-basic-visual-basic).</span></span>  
  
- <span data-ttu-id="c2951-118">Use only one statement per line.</span><span class="sxs-lookup"><span data-stu-id="c2951-118">Use only one statement per line.</span></span> <span data-ttu-id="c2951-119">Don't use the Visual Basic line separator character (:).</span><span class="sxs-lookup"><span data-stu-id="c2951-119">Don't use the Visual Basic line separator character (:).</span></span>  
  
- <span data-ttu-id="c2951-120">Avoid using the explicit line continuation character "_" in favor of implicit line continuation wherever the language allows it.</span><span class="sxs-lookup"><span data-stu-id="c2951-120">Avoid using the explicit line continuation character "_" in favor of implicit line continuation wherever the language allows it.</span></span>  
  
- <span data-ttu-id="c2951-121">Use only one declaration per line.</span><span class="sxs-lookup"><span data-stu-id="c2951-121">Use only one declaration per line.</span></span>  
  
- <span data-ttu-id="c2951-122">If **Pretty listing (reformatting) of code** doesn't format continuation lines automatically, manually indent continuation lines one tab stop.</span><span class="sxs-lookup"><span data-stu-id="c2951-122">If **Pretty listing (reformatting) of code** doesn't format continuation lines automatically, manually indent continuation lines one tab stop.</span></span> <span data-ttu-id="c2951-123">However, always left-align items in a list.</span><span class="sxs-lookup"><span data-stu-id="c2951-123">However, always left-align items in a list.</span></span>  
  
    ```vb  
    a As Integer,  
    b As Integer  
    ```  
  
- <span data-ttu-id="c2951-124">Add at least one blank line between method and property definitions.</span><span class="sxs-lookup"><span data-stu-id="c2951-124">Add at least one blank line between method and property definitions.</span></span>  
  
## <a name="commenting-conventions"></a><span data-ttu-id="c2951-125">Conventions de commentaires</span><span class="sxs-lookup"><span data-stu-id="c2951-125">Commenting Conventions</span></span>  
  
- <span data-ttu-id="c2951-126">Put comments on a separate line instead of at the end of a line of code.</span><span class="sxs-lookup"><span data-stu-id="c2951-126">Put comments on a separate line instead of at the end of a line of code.</span></span>  
  
- <span data-ttu-id="c2951-127">Start comment text with an uppercase letter, and end comment text with a period.</span><span class="sxs-lookup"><span data-stu-id="c2951-127">Start comment text with an uppercase letter, and end comment text with a period.</span></span>  
  
- <span data-ttu-id="c2951-128">Insert one space between the comment delimiter (') and the comment text.</span><span class="sxs-lookup"><span data-stu-id="c2951-128">Insert one space between the comment delimiter (') and the comment text.</span></span>  
  
     [!code-vb[VbVbalrGuidelines#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#2)]  
  
- <span data-ttu-id="c2951-129">Do not surround comments with formatted blocks of asterisks.</span><span class="sxs-lookup"><span data-stu-id="c2951-129">Do not surround comments with formatted blocks of asterisks.</span></span>  
  
## <a name="program-structure"></a><span data-ttu-id="c2951-130">Structure du programme</span><span class="sxs-lookup"><span data-stu-id="c2951-130">Program Structure</span></span>  
  
- <span data-ttu-id="c2951-131">When you use the `Main` method, use the default construct for new console applications, and use `My` for command-line arguments.</span><span class="sxs-lookup"><span data-stu-id="c2951-131">When you use the `Main` method, use the default construct for new console applications, and use `My` for command-line arguments.</span></span>  
  
     [!code-vb[VbVbalrGuidelines#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#3)]  
  
## <a name="language-guidelines"></a><span data-ttu-id="c2951-132">Directives du langage</span><span class="sxs-lookup"><span data-stu-id="c2951-132">Language Guidelines</span></span>  
  
### <a name="string-data-type"></a><span data-ttu-id="c2951-133">String, type de données</span><span class="sxs-lookup"><span data-stu-id="c2951-133">String Data Type</span></span>  
  
- <span data-ttu-id="c2951-134">Utilisez une [interpolation de chaîne](https://docs.microsoft.com/dotnet/visual-basic/programming-guide/language-features/strings/interpolated-strings) pour concaténer les chaînes courtes, comme illustré dans le code suivant.</span><span class="sxs-lookup"><span data-stu-id="c2951-134">Use [string interpolation](https://docs.microsoft.com/dotnet/visual-basic/programming-guide/language-features/strings/interpolated-strings) to concatenate short strings, as shown in the following code.</span></span>
  
     ```vb
     MsgBox($"hello{vbCrLf}goodbye")
     ```
  
- <span data-ttu-id="c2951-135">To append strings in loops, use the <xref:System.Text.StringBuilder> object.</span><span class="sxs-lookup"><span data-stu-id="c2951-135">To append strings in loops, use the <xref:System.Text.StringBuilder> object.</span></span>  
  
     [!code-vb[VbVbalrGuidelines#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#5)]  
  
### <a name="relaxed-delegates-in-event-handlers"></a><span data-ttu-id="c2951-136">Relaxed Delegates in Event Handlers</span><span class="sxs-lookup"><span data-stu-id="c2951-136">Relaxed Delegates in Event Handlers</span></span>  
 <span data-ttu-id="c2951-137">Do not explicitly qualify the arguments (Object and EventArgs) to event handlers.</span><span class="sxs-lookup"><span data-stu-id="c2951-137">Do not explicitly qualify the arguments (Object and EventArgs) to event handlers.</span></span> <span data-ttu-id="c2951-138">If you are not using the event arguments that are passed to an event (for example, sender as Object, e as EventArgs), use relaxed delegates, and leave out the event arguments in your code:</span><span class="sxs-lookup"><span data-stu-id="c2951-138">If you are not using the event arguments that are passed to an event (for example, sender as Object, e as EventArgs), use relaxed delegates, and leave out the event arguments in your code:</span></span>  
  
 [!code-vb[VbVbalrGuidelines#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#7)]  
  
### <a name="unsigned-data-type"></a><span data-ttu-id="c2951-139">Type de données non signé</span><span class="sxs-lookup"><span data-stu-id="c2951-139">Unsigned Data Type</span></span>  
  
- <span data-ttu-id="c2951-140">Use `Integer` rather than unsigned types, except where they are necessary.</span><span class="sxs-lookup"><span data-stu-id="c2951-140">Use `Integer` rather than unsigned types, except where they are necessary.</span></span>  
  
### <a name="arrays"></a><span data-ttu-id="c2951-141">Tableaux</span><span class="sxs-lookup"><span data-stu-id="c2951-141">Arrays</span></span>  
  
- <span data-ttu-id="c2951-142">Use the short syntax when you initialize arrays on the declaration line.</span><span class="sxs-lookup"><span data-stu-id="c2951-142">Use the short syntax when you initialize arrays on the declaration line.</span></span> <span data-ttu-id="c2951-143">For example, use the following syntax.</span><span class="sxs-lookup"><span data-stu-id="c2951-143">For example, use the following syntax.</span></span>  
  
     [!code-vb[VbVbalrGuidelines#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#8)]  
  
     <span data-ttu-id="c2951-144">Do not use the following syntax.</span><span class="sxs-lookup"><span data-stu-id="c2951-144">Do not use the following syntax.</span></span>  
  
     [!code-vb[VbVbalrGuidelines#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#9)]  
  
- <span data-ttu-id="c2951-145">Put the array designator on the type, not on the variable.</span><span class="sxs-lookup"><span data-stu-id="c2951-145">Put the array designator on the type, not on the variable.</span></span> <span data-ttu-id="c2951-146">For example, use the following syntax:</span><span class="sxs-lookup"><span data-stu-id="c2951-146">For example, use the following syntax:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#11)]  
  
     <span data-ttu-id="c2951-147">Do not use the following syntax:</span><span class="sxs-lookup"><span data-stu-id="c2951-147">Do not use the following syntax:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#10)]  
  
- <span data-ttu-id="c2951-148">Use the { } syntax when you declare and initialize arrays of basic data types.</span><span class="sxs-lookup"><span data-stu-id="c2951-148">Use the { } syntax when you declare and initialize arrays of basic data types.</span></span> <span data-ttu-id="c2951-149">For example, use the following syntax:</span><span class="sxs-lookup"><span data-stu-id="c2951-149">For example, use the following syntax:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#12)]  
  
     <span data-ttu-id="c2951-150">Do not use the following syntax:</span><span class="sxs-lookup"><span data-stu-id="c2951-150">Do not use the following syntax:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#13)]  
  
### <a name="use-the-with-keyword"></a><span data-ttu-id="c2951-151">Use the With Keyword</span><span class="sxs-lookup"><span data-stu-id="c2951-151">Use the With Keyword</span></span>  
 <span data-ttu-id="c2951-152">When you make a series of calls to one object, consider using the `With` keyword:</span><span class="sxs-lookup"><span data-stu-id="c2951-152">When you make a series of calls to one object, consider using the `With` keyword:</span></span>  
  
 [!code-vb[VbVbalrGuidelines#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#15)]  
  
### <a name="use-the-trycatch-and-using-statements-when-you-use-exception-handling"></a><span data-ttu-id="c2951-153">Use the Try...Catch and Using Statements when you use Exception Handling</span><span class="sxs-lookup"><span data-stu-id="c2951-153">Use the Try...Catch and Using Statements when you use Exception Handling</span></span>  
 <span data-ttu-id="c2951-154">N’utilisez pas `On Error Goto`.</span><span class="sxs-lookup"><span data-stu-id="c2951-154">Do not use `On Error Goto`.</span></span>  
  
### <a name="use-the-isnot-keyword"></a><span data-ttu-id="c2951-155">Use the IsNot Keyword</span><span class="sxs-lookup"><span data-stu-id="c2951-155">Use the IsNot Keyword</span></span>  
 <span data-ttu-id="c2951-156">Use the `IsNot` keyword instead of `Not...Is Nothing`.</span><span class="sxs-lookup"><span data-stu-id="c2951-156">Use the `IsNot` keyword instead of `Not...Is Nothing`.</span></span>  
  
### <a name="new-keyword"></a><span data-ttu-id="c2951-157">New Keyword</span><span class="sxs-lookup"><span data-stu-id="c2951-157">New Keyword</span></span>  
  
- <span data-ttu-id="c2951-158">Use short instantiation.</span><span class="sxs-lookup"><span data-stu-id="c2951-158">Use short instantiation.</span></span> <span data-ttu-id="c2951-159">For example, use the following syntax:</span><span class="sxs-lookup"><span data-stu-id="c2951-159">For example, use the following syntax:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#21)]  
  
     <span data-ttu-id="c2951-160">The preceding line is equivalent to this:</span><span class="sxs-lookup"><span data-stu-id="c2951-160">The preceding line is equivalent to this:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#22)]  
  
- <span data-ttu-id="c2951-161">Use object initializers for new objects instead of the parameterless constructor:</span><span class="sxs-lookup"><span data-stu-id="c2951-161">Use object initializers for new objects instead of the parameterless constructor:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#23)]  
  
### <a name="event-handling"></a><span data-ttu-id="c2951-162">Gestion des événements</span><span class="sxs-lookup"><span data-stu-id="c2951-162">Event Handling</span></span>  
  
- <span data-ttu-id="c2951-163">Use `Handles` rather than `AddHandler`:</span><span class="sxs-lookup"><span data-stu-id="c2951-163">Use `Handles` rather than `AddHandler`:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#24)]  
  
- <span data-ttu-id="c2951-164">Use `AddressOf`, and do not instantiate the delegate explicitly:</span><span class="sxs-lookup"><span data-stu-id="c2951-164">Use `AddressOf`, and do not instantiate the delegate explicitly:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#25)]  
  
- <span data-ttu-id="c2951-165">When you define an event, use the short syntax, and let the compiler define the delegate:</span><span class="sxs-lookup"><span data-stu-id="c2951-165">When you define an event, use the short syntax, and let the compiler define the delegate:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#26)]  
  
- <span data-ttu-id="c2951-166">Do not verify whether an event is `Nothing` (null) before you call the `RaiseEvent` method.</span><span class="sxs-lookup"><span data-stu-id="c2951-166">Do not verify whether an event is `Nothing` (null) before you call the `RaiseEvent` method.</span></span> <span data-ttu-id="c2951-167">`RaiseEvent` checks for `Nothing` before it raises the event.</span><span class="sxs-lookup"><span data-stu-id="c2951-167">`RaiseEvent` checks for `Nothing` before it raises the event.</span></span>  
  
### <a name="using-shared-members"></a><span data-ttu-id="c2951-168">Using Shared Members</span><span class="sxs-lookup"><span data-stu-id="c2951-168">Using Shared Members</span></span>  
 <span data-ttu-id="c2951-169">Call `Shared` members by using the class name, not from an instance variable.</span><span class="sxs-lookup"><span data-stu-id="c2951-169">Call `Shared` members by using the class name, not from an instance variable.</span></span>  
  
### <a name="use-xml-literals"></a><span data-ttu-id="c2951-170">Use XML Literals</span><span class="sxs-lookup"><span data-stu-id="c2951-170">Use XML Literals</span></span>  
 <span data-ttu-id="c2951-171">XML literals simplify the most common tasks that you encounter when you work with XML (for example, load, query, and transform).</span><span class="sxs-lookup"><span data-stu-id="c2951-171">XML literals simplify the most common tasks that you encounter when you work with XML (for example, load, query, and transform).</span></span> <span data-ttu-id="c2951-172">When you develop with XML, follow these guidelines:</span><span class="sxs-lookup"><span data-stu-id="c2951-172">When you develop with XML, follow these guidelines:</span></span>  
  
- <span data-ttu-id="c2951-173">Use XML literals to create XML documents and fragments instead of calling XML APIs directly.</span><span class="sxs-lookup"><span data-stu-id="c2951-173">Use XML literals to create XML documents and fragments instead of calling XML APIs directly.</span></span>  
  
- <span data-ttu-id="c2951-174">Import XML namespaces at the file or project level to take advantage of the performance optimizations for XML literals.</span><span class="sxs-lookup"><span data-stu-id="c2951-174">Import XML namespaces at the file or project level to take advantage of the performance optimizations for XML literals.</span></span>  
  
- <span data-ttu-id="c2951-175">Use the XML axis properties to access elements and attributes in an XML document.</span><span class="sxs-lookup"><span data-stu-id="c2951-175">Use the XML axis properties to access elements and attributes in an XML document.</span></span>  
  
- <span data-ttu-id="c2951-176">Use embedded expressions to include values and to create XML from existing values instead of using API calls such as the `Add` method:</span><span class="sxs-lookup"><span data-stu-id="c2951-176">Use embedded expressions to include values and to create XML from existing values instead of using API calls such as the `Add` method:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#27)]  
  
### <a name="linq-queries"></a><span data-ttu-id="c2951-177">Requêtes LINQ</span><span class="sxs-lookup"><span data-stu-id="c2951-177">LINQ Queries</span></span>  
  
- <span data-ttu-id="c2951-178">Use meaningful names for query variables:</span><span class="sxs-lookup"><span data-stu-id="c2951-178">Use meaningful names for query variables:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#28)]  
  
- <span data-ttu-id="c2951-179">Provide names for elements in a query to make sure that property names of anonymous types are correctly capitalized using Pascal casing:</span><span class="sxs-lookup"><span data-stu-id="c2951-179">Provide names for elements in a query to make sure that property names of anonymous types are correctly capitalized using Pascal casing:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#29)]  
  
- <span data-ttu-id="c2951-180">Renommez les propriétés lorsque les noms de propriétés dans le résultat sont ambigus.</span><span class="sxs-lookup"><span data-stu-id="c2951-180">Rename properties when the property names in the result would be ambiguous.</span></span> <span data-ttu-id="c2951-181">For example, if your query returns a customer name and an order ID, rename them instead of leaving them as `Name` and `ID` in the result:</span><span class="sxs-lookup"><span data-stu-id="c2951-181">For example, if your query returns a customer name and an order ID, rename them instead of leaving them as `Name` and `ID` in the result:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#30)]  
  
- <span data-ttu-id="c2951-182">Use type inference in the declaration of query variables and range variables:</span><span class="sxs-lookup"><span data-stu-id="c2951-182">Use type inference in the declaration of query variables and range variables:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#31)]  
  
- <span data-ttu-id="c2951-183">Align query clauses under the `From` statement:</span><span class="sxs-lookup"><span data-stu-id="c2951-183">Align query clauses under the `From` statement:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#32](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#32)]  
  
- <span data-ttu-id="c2951-184">Use `Where` clauses before other query clauses so that later query clauses operate on the filtered set of data:</span><span class="sxs-lookup"><span data-stu-id="c2951-184">Use `Where` clauses before other query clauses so that later query clauses operate on the filtered set of data:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#33](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#33)]  
  
- <span data-ttu-id="c2951-185">Use the `Join` clause to explicitly define a join operation instead of using the `Where` clause to implicitly define a join operation:</span><span class="sxs-lookup"><span data-stu-id="c2951-185">Use the `Join` clause to explicitly define a join operation instead of using the `Where` clause to implicitly define a join operation:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#34](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#34)]  
  
## <a name="see-also"></a><span data-ttu-id="c2951-186">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c2951-186">See also</span></span>

- [<span data-ttu-id="c2951-187">Instructions de codage sécurisé</span><span class="sxs-lookup"><span data-stu-id="c2951-187">Secure Coding Guidelines</span></span>](../../../standard/security/secure-coding-guidelines.md)
