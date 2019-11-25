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
# <a name="visual-basic-coding-conventions"></a>Conventions de codage Visual Basic
Microsoft develops samples and documentation that follow the guidelines in this topic. If you follow the same coding conventions, you may gain the following benefits:  
  
- Your code will have a consistent look, so that readers can better focus on content, not layout.  
  
- Readers understand your code more quickly because they can make assumptions based on previous experience.  
  
- You can copy, change, and maintain the code more easily.  
  
- You help ensure that your code demonstrates "best practices" for Visual Basic.  
  
## <a name="naming-conventions"></a>Conventions d'affectation de noms  
  
- For information about naming guidelines, see [Naming Guidelines](../../../standard/design-guidelines/naming-guidelines.md) topic.  
  
- Do not use "My" or "my" as part of a variable name. This practice creates confusion with the `My` objects.  
  
- You do not have to change the names of objects in auto-generated code to make them fit the guidelines.  
  
## <a name="layout-conventions"></a>Conventions de disposition  
  
- Insert tabs as spaces, and use smart indenting with four-space indents.  
  
- Use **Pretty listing (reformatting) of code** to reformat your code in the code editor. For more information, see [Options, Text Editor, Basic (Visual Basic)](/visualstudio/ide/reference/options-text-editor-basic-visual-basic).  
  
- Use only one statement per line. Don't use the Visual Basic line separator character (:).  
  
- Avoid using the explicit line continuation character "_" in favor of implicit line continuation wherever the language allows it.  
  
- Use only one declaration per line.  
  
- If **Pretty listing (reformatting) of code** doesn't format continuation lines automatically, manually indent continuation lines one tab stop. However, always left-align items in a list.  
  
    ```vb  
    a As Integer,  
    b As Integer  
    ```  
  
- Add at least one blank line between method and property definitions.  
  
## <a name="commenting-conventions"></a>Conventions de commentaires  
  
- Put comments on a separate line instead of at the end of a line of code.  
  
- Start comment text with an uppercase letter, and end comment text with a period.  
  
- Insert one space between the comment delimiter (') and the comment text.  
  
     [!code-vb[VbVbalrGuidelines#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#2)]  
  
- Do not surround comments with formatted blocks of asterisks.  
  
## <a name="program-structure"></a>Structure du programme  
  
- When you use the `Main` method, use the default construct for new console applications, and use `My` for command-line arguments.  
  
     [!code-vb[VbVbalrGuidelines#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#3)]  
  
## <a name="language-guidelines"></a>Directives du langage  
  
### <a name="string-data-type"></a>String, type de données  
  
- Utilisez une [interpolation de chaîne](https://docs.microsoft.com/dotnet/visual-basic/programming-guide/language-features/strings/interpolated-strings) pour concaténer les chaînes courtes, comme illustré dans le code suivant.
  
     ```vb
     MsgBox($"hello{vbCrLf}goodbye")
     ```
  
- To append strings in loops, use the <xref:System.Text.StringBuilder> object.  
  
     [!code-vb[VbVbalrGuidelines#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#5)]  
  
### <a name="relaxed-delegates-in-event-handlers"></a>Relaxed Delegates in Event Handlers  
 Do not explicitly qualify the arguments (Object and EventArgs) to event handlers. If you are not using the event arguments that are passed to an event (for example, sender as Object, e as EventArgs), use relaxed delegates, and leave out the event arguments in your code:  
  
 [!code-vb[VbVbalrGuidelines#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#7)]  
  
### <a name="unsigned-data-type"></a>Type de données non signé  
  
- Use `Integer` rather than unsigned types, except where they are necessary.  
  
### <a name="arrays"></a>Tableaux  
  
- Use the short syntax when you initialize arrays on the declaration line. For example, use the following syntax.  
  
     [!code-vb[VbVbalrGuidelines#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#8)]  
  
     Do not use the following syntax.  
  
     [!code-vb[VbVbalrGuidelines#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#9)]  
  
- Put the array designator on the type, not on the variable. For example, use the following syntax:  
  
     [!code-vb[VbVbalrGuidelines#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#11)]  
  
     Do not use the following syntax:  
  
     [!code-vb[VbVbalrGuidelines#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#10)]  
  
- Use the { } syntax when you declare and initialize arrays of basic data types. For example, use the following syntax:  
  
     [!code-vb[VbVbalrGuidelines#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#12)]  
  
     Do not use the following syntax:  
  
     [!code-vb[VbVbalrGuidelines#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#13)]  
  
### <a name="use-the-with-keyword"></a>Use the With Keyword  
 When you make a series of calls to one object, consider using the `With` keyword:  
  
 [!code-vb[VbVbalrGuidelines#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#15)]  
  
### <a name="use-the-trycatch-and-using-statements-when-you-use-exception-handling"></a>Use the Try...Catch and Using Statements when you use Exception Handling  
 N’utilisez pas `On Error Goto`.  
  
### <a name="use-the-isnot-keyword"></a>Use the IsNot Keyword  
 Use the `IsNot` keyword instead of `Not...Is Nothing`.  
  
### <a name="new-keyword"></a>New Keyword  
  
- Use short instantiation. For example, use the following syntax:  
  
     [!code-vb[VbVbalrGuidelines#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#21)]  
  
     The preceding line is equivalent to this:  
  
     [!code-vb[VbVbalrGuidelines#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#22)]  
  
- Use object initializers for new objects instead of the parameterless constructor:  
  
     [!code-vb[VbVbalrGuidelines#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#23)]  
  
### <a name="event-handling"></a>Gestion des événements  
  
- Use `Handles` rather than `AddHandler`:  
  
     [!code-vb[VbVbalrGuidelines#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#24)]  
  
- Use `AddressOf`, and do not instantiate the delegate explicitly:  
  
     [!code-vb[VbVbalrGuidelines#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#25)]  
  
- When you define an event, use the short syntax, and let the compiler define the delegate:  
  
     [!code-vb[VbVbalrGuidelines#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#26)]  
  
- Do not verify whether an event is `Nothing` (null) before you call the `RaiseEvent` method. `RaiseEvent` checks for `Nothing` before it raises the event.  
  
### <a name="using-shared-members"></a>Using Shared Members  
 Call `Shared` members by using the class name, not from an instance variable.  
  
### <a name="use-xml-literals"></a>Use XML Literals  
 XML literals simplify the most common tasks that you encounter when you work with XML (for example, load, query, and transform). When you develop with XML, follow these guidelines:  
  
- Use XML literals to create XML documents and fragments instead of calling XML APIs directly.  
  
- Import XML namespaces at the file or project level to take advantage of the performance optimizations for XML literals.  
  
- Use the XML axis properties to access elements and attributes in an XML document.  
  
- Use embedded expressions to include values and to create XML from existing values instead of using API calls such as the `Add` method:  
  
     [!code-vb[VbVbalrGuidelines#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#27)]  
  
### <a name="linq-queries"></a>Requêtes LINQ  
  
- Use meaningful names for query variables:  
  
     [!code-vb[VbVbalrGuidelines#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#28)]  
  
- Provide names for elements in a query to make sure that property names of anonymous types are correctly capitalized using Pascal casing:  
  
     [!code-vb[VbVbalrGuidelines#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#29)]  
  
- Renommez les propriétés lorsque les noms de propriétés dans le résultat sont ambigus. For example, if your query returns a customer name and an order ID, rename them instead of leaving them as `Name` and `ID` in the result:  
  
     [!code-vb[VbVbalrGuidelines#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#30)]  
  
- Use type inference in the declaration of query variables and range variables:  
  
     [!code-vb[VbVbalrGuidelines#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#31)]  
  
- Align query clauses under the `From` statement:  
  
     [!code-vb[VbVbalrGuidelines#32](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#32)]  
  
- Use `Where` clauses before other query clauses so that later query clauses operate on the filtered set of data:  
  
     [!code-vb[VbVbalrGuidelines#33](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#33)]  
  
- Use the `Join` clause to explicitly define a join operation instead of using the `Where` clause to implicitly define a join operation:  
  
     [!code-vb[VbVbalrGuidelines#34](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#34)]  
  
## <a name="see-also"></a>Voir aussi

- [Instructions de codage sécurisé](../../../standard/security/secure-coding-guidelines.md)
