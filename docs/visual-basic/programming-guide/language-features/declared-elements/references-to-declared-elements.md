---
title: References to Declared Elements
ms.date: 07/20/2015
helpviewer_keywords:
- declared elements [Visual Basic]
- references [Visual Basic], declared elements
- qualified names [Visual Basic]
ms.assetid: d6301709-f4cc-4b7a-b8ba-80898f14ab46
ms.openlocfilehash: af5be47335b6d48bd6c0bccc30b8db15c9912807
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91085878"
---
# <a name="references-to-declared-elements-visual-basic"></a><span data-ttu-id="c21ac-102">Références aux éléments déclarés (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c21ac-102">References to Declared Elements (Visual Basic)</span></span>

<span data-ttu-id="c21ac-103">Quand votre code fait référence à un élément déclaré, le compilateur Visual Basic correspond au nom dans votre référence à la déclaration appropriée de ce nom.</span><span class="sxs-lookup"><span data-stu-id="c21ac-103">When your code refers to a declared element, the Visual Basic compiler matches the name in your reference to the appropriate declaration of that name.</span></span> <span data-ttu-id="c21ac-104">Si plusieurs éléments sont déclarés avec le même nom, vous pouvez contrôler lequel de ces éléments doit être référencé en *qualifiant* son nom.</span><span class="sxs-lookup"><span data-stu-id="c21ac-104">If more than one element is declared with the same name, you can control which of those elements is to be referenced by *qualifying* its name.</span></span>  
  
 <span data-ttu-id="c21ac-105">Le compilateur tente de faire correspondre une référence de nom à une déclaration de nom avec l’étendue la plus *étroite*.</span><span class="sxs-lookup"><span data-stu-id="c21ac-105">The compiler attempts to match a name reference to a name declaration with the *narrowest scope*.</span></span> <span data-ttu-id="c21ac-106">Cela signifie qu’elle commence par le code qui fait la référence et fonctionne vers l’extérieur à travers les niveaux successifs des éléments contenants.</span><span class="sxs-lookup"><span data-stu-id="c21ac-106">This means it starts with the code making the reference and works outward through successive levels of containing elements.</span></span>  
  
 <span data-ttu-id="c21ac-107">L’exemple suivant montre des références à deux variables portant le même nom.</span><span class="sxs-lookup"><span data-stu-id="c21ac-107">The following example shows references to two variables with the same name.</span></span> <span data-ttu-id="c21ac-108">L’exemple déclare deux variables, chacune nommée `totalCount` , à des niveaux de portée différents dans le module `container` .</span><span class="sxs-lookup"><span data-stu-id="c21ac-108">The example declares two variables, each named `totalCount`, at different levels of scope in module `container`.</span></span> <span data-ttu-id="c21ac-109">Lorsque la procédure `showCount` s’affiche `totalCount` sans qualification, le compilateur Visual Basic résout la référence à la déclaration avec l’étendue la plus étroite, à savoir la déclaration locale à l’intérieur de `showCount` .</span><span class="sxs-lookup"><span data-stu-id="c21ac-109">When the procedure `showCount` displays `totalCount` without qualification, the Visual Basic compiler resolves the reference to the declaration with the narrowest scope, namely the local declaration inside `showCount`.</span></span> <span data-ttu-id="c21ac-110">Lorsqu’il est qualifié `totalCount` avec le module conteneur `container` , le compilateur résout la référence à la déclaration avec la portée plus large.</span><span class="sxs-lookup"><span data-stu-id="c21ac-110">When it qualifies `totalCount` with the containing module `container`, the compiler resolves the reference to the declaration with the broader scope.</span></span>  
  
```vb  
' Assume these two modules are both in the same assembly.  
Module container  
    Public totalCount As Integer = 1  
    Public Sub showCount()  
        Dim totalCount As Integer = 6000  
        ' The following statement displays the local totalCount (6000).  
        MsgBox("Unqualified totalCount is " & CStr(totalCount))  
        ' The following statement displays the module's totalCount (1).  
        MsgBox("container.totalCount is " & CStr(container.totalCount))  
    End Sub  
End Module  
Module callingModule  
    Public Sub displayCount()  
        container.showCount()  
        ' The following statement displays the containing module's totalCount (1).  
        MsgBox("container.totalCount is " & CStr(container.totalCount))  
    End Sub  
End Module  
```  
  
## <a name="qualifying-an-element-name"></a><span data-ttu-id="c21ac-111">Qualification d’un nom d’élément</span><span class="sxs-lookup"><span data-stu-id="c21ac-111">Qualifying an Element Name</span></span>  

 <span data-ttu-id="c21ac-112">Si vous souhaitez remplacer ce processus de recherche et spécifier un nom déclaré dans une étendue plus large, vous devez *qualifier* le nom avec l’élément conteneur de la portée plus large.</span><span class="sxs-lookup"><span data-stu-id="c21ac-112">If you want to override this search process and specify a name declared in a broader scope, you must *qualify* the name with the containing element of the broader scope.</span></span> <span data-ttu-id="c21ac-113">Dans certains cas, vous devrez peut-être également qualifier l’élément conteneur.</span><span class="sxs-lookup"><span data-stu-id="c21ac-113">In some cases, you might also have to qualify the containing element.</span></span>  
  
 <span data-ttu-id="c21ac-114">Qualifier un nom signifie le précéder dans votre instruction source avec des informations qui identifient l’emplacement de définition de l’élément cible.</span><span class="sxs-lookup"><span data-stu-id="c21ac-114">Qualifying a name means preceding it in your source statement with information that identifies where the target element is defined.</span></span> <span data-ttu-id="c21ac-115">Ces informations sont appelées une *chaîne de qualification*.</span><span class="sxs-lookup"><span data-stu-id="c21ac-115">This information is called a *qualification string*.</span></span> <span data-ttu-id="c21ac-116">Il peut inclure un ou plusieurs espaces de noms et un module, une classe ou une structure.</span><span class="sxs-lookup"><span data-stu-id="c21ac-116">It can include one or more namespaces and a module, class, or structure.</span></span>  
  
 <span data-ttu-id="c21ac-117">La chaîne de qualification doit spécifier de manière non ambiguë le module, la classe ou la structure contenant l’élément cible.</span><span class="sxs-lookup"><span data-stu-id="c21ac-117">The qualification string should unambiguously specify the module, class, or structure containing the target element.</span></span> <span data-ttu-id="c21ac-118">Le conteneur peut à son tour se trouver dans un autre élément contenant, généralement un espace de noms.</span><span class="sxs-lookup"><span data-stu-id="c21ac-118">The container might in turn be located in another containing element, usually a namespace.</span></span> <span data-ttu-id="c21ac-119">Vous devrez peut-être inclure plusieurs éléments contenant dans la chaîne de qualification.</span><span class="sxs-lookup"><span data-stu-id="c21ac-119">You might need to include several containing elements in the qualification string.</span></span>  
  
#### <a name="to-access-a-declared-element-by-qualifying-its-name"></a><span data-ttu-id="c21ac-120">Pour accéder à un élément déclaré en qualifiant son nom</span><span class="sxs-lookup"><span data-stu-id="c21ac-120">To access a declared element by qualifying its name</span></span>  
  
1. <span data-ttu-id="c21ac-121">Déterminez l’emplacement dans lequel l’élément a été défini.</span><span class="sxs-lookup"><span data-stu-id="c21ac-121">Determine the location in which the element has been defined.</span></span> <span data-ttu-id="c21ac-122">Cela peut inclure un espace de noms, ou même une hiérarchie d’espaces de noms.</span><span class="sxs-lookup"><span data-stu-id="c21ac-122">This might include a namespace, or even a hierarchy of namespaces.</span></span> <span data-ttu-id="c21ac-123">Dans l’espace de noms de niveau inférieur, l’élément doit être contenu dans un module, une classe ou une structure.</span><span class="sxs-lookup"><span data-stu-id="c21ac-123">Within the lowest-level namespace, the element must be contained in a module, class, or structure.</span></span>  
  
    ```vb  
    ' Assume the following hierarchy exists outside your code.  
    Namespace outerSpace  
        Namespace innerSpace  
            Module holdsTotals  
                Public Structure totals  
                    Public thisTotal As Integer  
                    Public Shared grandTotal As Long  
                End Structure  
            End Module  
        End Namespace  
    End Namespace  
    ```  
  
2. <span data-ttu-id="c21ac-124">Déterminez un chemin d’accès de qualification en fonction de l’emplacement de l’élément cible.</span><span class="sxs-lookup"><span data-stu-id="c21ac-124">Determine a qualification path based on the target element's location.</span></span> <span data-ttu-id="c21ac-125">Commencez par l’espace de noms de niveau supérieur, passez à l’espace de noms de niveau le plus bas, et terminez par le module, la classe ou la structure contenant l’élément cible.</span><span class="sxs-lookup"><span data-stu-id="c21ac-125">Start with the highest-level namespace, proceed to the lowest-level namespace, and end with the module, class, or structure containing the target element.</span></span> <span data-ttu-id="c21ac-126">Chaque élément du chemin d’accès doit contenir l’élément qui le suit.</span><span class="sxs-lookup"><span data-stu-id="c21ac-126">Each element in the path must contain the element that follows it.</span></span>  
  
     <span data-ttu-id="c21ac-127">`outerSpace` → `innerSpace` → `holdsTotals` → `totals`</span><span class="sxs-lookup"><span data-stu-id="c21ac-127">`outerSpace` → `innerSpace` → `holdsTotals` → `totals`</span></span>  
  
3. <span data-ttu-id="c21ac-128">Préparez la chaîne de qualification pour l’élément cible.</span><span class="sxs-lookup"><span data-stu-id="c21ac-128">Prepare the qualification string for the target element.</span></span> <span data-ttu-id="c21ac-129">Placez un point ( `.` ) après chaque élément dans le tracé.</span><span class="sxs-lookup"><span data-stu-id="c21ac-129">Place a period (`.`) after every element in the path.</span></span> <span data-ttu-id="c21ac-130">Votre application doit avoir accès à chaque élément de votre chaîne de qualification.</span><span class="sxs-lookup"><span data-stu-id="c21ac-130">Your application must have access to every element in your qualification string.</span></span>  
  
    ```vb  
    outerSpace.innerSpace.holdsTotals.totals.  
    ```  
  
4. <span data-ttu-id="c21ac-131">Écrivez l’expression ou l’instruction d’assignation qui fait référence à l’élément cible de manière normale.</span><span class="sxs-lookup"><span data-stu-id="c21ac-131">Write the expression or assignment statement referring to the target element in the normal way.</span></span>  
  
    ```vb  
    grandTotal = 9000  
    ```  
  
5. <span data-ttu-id="c21ac-132">Faites précéder le nom de l’élément cible de la chaîne de qualification.</span><span class="sxs-lookup"><span data-stu-id="c21ac-132">Precede the target element name with the qualification string.</span></span> <span data-ttu-id="c21ac-133">Le nom doit suivre immédiatement le point ( `.` ) qui suit le module, la classe ou la structure qui contient l’élément.</span><span class="sxs-lookup"><span data-stu-id="c21ac-133">The name should immediately follow the period (`.`) that follows the module, class, or structure that contains the element.</span></span>  
  
    ```vb  
    ' Assume the following module is part of your code.  
    Module accessGrandTotal  
        Public Sub setGrandTotal()  
            outerSpace.innerSpace.holdsTotals.totals.grandTotal = 9000  
        End Sub  
    End Module  
    ```  
  
6. <span data-ttu-id="c21ac-134">Le compilateur utilise la chaîne de qualification pour rechercher une déclaration claire et non ambiguë à laquelle il peut correspondre à la référence de l’élément cible.</span><span class="sxs-lookup"><span data-stu-id="c21ac-134">The compiler uses the qualification string to find a clear, unambiguous declaration to which it can match the target element reference.</span></span>  
  
 <span data-ttu-id="c21ac-135">Vous devrez peut-être également qualifier une référence de nom si votre application a accès à plus d’un élément de programmation portant le même nom.</span><span class="sxs-lookup"><span data-stu-id="c21ac-135">You might also have to qualify a name reference if your application has access to more than one programming element that has the same name.</span></span> <span data-ttu-id="c21ac-136">Par exemple, les <xref:System.Windows.Forms> <xref:System.Web.UI.WebControls> espaces de noms et contiennent tous les deux une `Label` classe ( <xref:System.Windows.Forms.Label?displayProperty=nameWithType> et <xref:System.Web.UI.WebControls.Label?displayProperty=nameWithType> ).</span><span class="sxs-lookup"><span data-stu-id="c21ac-136">For example, the <xref:System.Windows.Forms> and <xref:System.Web.UI.WebControls> namespaces both contain a `Label` class (<xref:System.Windows.Forms.Label?displayProperty=nameWithType> and <xref:System.Web.UI.WebControls.Label?displayProperty=nameWithType>).</span></span> <span data-ttu-id="c21ac-137">Si votre application utilise les deux, ou si elle définit sa propre `Label` classe, vous devez distinguer les différents `Label` objets.</span><span class="sxs-lookup"><span data-stu-id="c21ac-137">If your application uses both, or if it defines its own `Label` class, you must distinguish the different `Label` objects.</span></span> <span data-ttu-id="c21ac-138">Incluez l’espace de noms ou l’alias d’importation dans la déclaration de la variable.</span><span class="sxs-lookup"><span data-stu-id="c21ac-138">Include the namespace or import alias in the variable declaration.</span></span> <span data-ttu-id="c21ac-139">L’exemple suivant utilise l’alias d’importation.</span><span class="sxs-lookup"><span data-stu-id="c21ac-139">The following example uses the import alias.</span></span>  
  
```vb  
' The following statement must precede all your declarations.  
Imports win = System.Windows.Forms, web = System.Web.UI.WebControls  
' The following statement references the Windows.Forms.Label class.  
Dim winLabel As New win.Label()  
```  
  
## <a name="members-of-other-containing-elements"></a><span data-ttu-id="c21ac-140">Membres d’autres éléments conteneur</span><span class="sxs-lookup"><span data-stu-id="c21ac-140">Members of Other Containing Elements</span></span>  

 <span data-ttu-id="c21ac-141">Quand vous utilisez un membre non partagé d’une autre classe ou structure, vous devez d’abord qualifier le nom du membre à l’aide d’une variable ou d’une expression qui pointe vers une instance de la classe ou de la structure.</span><span class="sxs-lookup"><span data-stu-id="c21ac-141">When you use a nonshared member of another class or structure, you must first qualify the member name with a variable or expression that points to an instance of the class or structure.</span></span> <span data-ttu-id="c21ac-142">Dans l’exemple suivant, `demoClass` est une instance d’une classe nommée `class1` .</span><span class="sxs-lookup"><span data-stu-id="c21ac-142">In the following example, `demoClass` is an instance of a class named `class1`.</span></span>  
  
```vb  
Dim demoClass As class1 = New class1()  
demoClass.someSub[(argumentlist)]  
```  
  
 <span data-ttu-id="c21ac-143">Vous ne pouvez pas utiliser le nom de la classe proprement dit pour qualifier un membre qui n’est pas [partagé](../../../language-reference/modifiers/shared.md).</span><span class="sxs-lookup"><span data-stu-id="c21ac-143">You cannot use the class name itself to qualify a member that is not [Shared](../../../language-reference/modifiers/shared.md).</span></span> <span data-ttu-id="c21ac-144">Vous devez d’abord créer une instance dans une variable objet (dans ce cas `demoClass` ), puis la référencer par le nom de la variable.</span><span class="sxs-lookup"><span data-stu-id="c21ac-144">You must first create an instance in an object variable (in this case `demoClass`) and then reference it by the variable name.</span></span>  
  
 <span data-ttu-id="c21ac-145">Si une classe ou une structure a un `Shared` membre, vous pouvez qualifier ce membre soit avec le nom de la classe ou de la structure, soit avec une variable ou une expression qui pointe vers une instance.</span><span class="sxs-lookup"><span data-stu-id="c21ac-145">If a class or structure has a `Shared` member, you can qualify that member either with the class or structure name or with a variable or expression that points to an instance.</span></span>  
  
 <span data-ttu-id="c21ac-146">Un module n’a pas d’instances distinctes, et tous ses membres sont `Shared` par défaut.</span><span class="sxs-lookup"><span data-stu-id="c21ac-146">A module does not have any separate instances, and all its members are `Shared` by default.</span></span> <span data-ttu-id="c21ac-147">Par conséquent, vous qualifiez un membre de module avec le nom du module.</span><span class="sxs-lookup"><span data-stu-id="c21ac-147">Therefore, you qualify a module member with the module name.</span></span>  
  
 <span data-ttu-id="c21ac-148">L’exemple suivant montre des références qualifiées à des procédures de membre de module.</span><span class="sxs-lookup"><span data-stu-id="c21ac-148">The following example shows qualified references to module member procedures.</span></span> <span data-ttu-id="c21ac-149">L’exemple déclare deux `Sub` procédures, à la fois nommées `perform` , dans différents modules d’un projet.</span><span class="sxs-lookup"><span data-stu-id="c21ac-149">The example declares two `Sub` procedures, both named `perform`, in different modules in a project.</span></span> <span data-ttu-id="c21ac-150">Chacune d’elles peut être spécifiée sans qualification dans son propre module, mais elle doit être qualifiée si elle est référencée ailleurs.</span><span class="sxs-lookup"><span data-stu-id="c21ac-150">Each one can be specified without qualification within its own module but must be qualified if referenced from anywhere else.</span></span> <span data-ttu-id="c21ac-151">Étant donné que la référence finale dans `module3` n’est pas qualifiée `perform` , le compilateur ne peut pas résoudre cette référence.</span><span class="sxs-lookup"><span data-stu-id="c21ac-151">Because the final reference in `module3` does not qualify `perform`, the compiler cannot resolve that reference.</span></span>  
  
```vb  
' Assume these three modules are all in the same assembly.  
Module module1  
    Public Sub perform()  
        MsgBox("module1.perform() now returning")  
    End Sub  
End Module  
Module module2  
    Public Sub perform()  
        MsgBox("module2.perform() now returning")  
    End Sub  
    Public Sub doSomething()  
        ' The following statement calls perform in module2, the active module.  
        perform()  
        ' The following statement calls perform in module1.  
        module1.perform()  
    End Sub  
End Module  
Module module3  
    Public Sub callPerform()  
        ' The following statement calls perform in module1.  
        module1.perform()  
        ' The following statement makes an unresolvable name reference  
        ' and therefore generates a COMPILER ERROR.  
        perform() ' INVALID statement  
    End Sub  
End Module  
```  
  
## <a name="references-to-projects"></a><span data-ttu-id="c21ac-152">Références aux projets</span><span class="sxs-lookup"><span data-stu-id="c21ac-152">References to Projects</span></span>  

 <span data-ttu-id="c21ac-153">Pour utiliser des éléments [publics](../../../language-reference/modifiers/public.md) définis dans un autre projet, vous devez d’abord définir une *référence* à l’assembly ou la bibliothèque de types de ce projet.</span><span class="sxs-lookup"><span data-stu-id="c21ac-153">To use [Public](../../../language-reference/modifiers/public.md) elements defined in another project, you must first set a *reference* to that project's assembly or type library.</span></span> <span data-ttu-id="c21ac-154">Pour définir une référence, cliquez sur **Ajouter une référence** dans le menu **projet** ou utilisez l’option du compilateur de ligne [de commande-Reference (Visual Basic)](../../../reference/command-line-compiler/reference.md) .</span><span class="sxs-lookup"><span data-stu-id="c21ac-154">To set a reference, click **Add Reference** on the **Project** menu, or use the [-reference (Visual Basic)](../../../reference/command-line-compiler/reference.md) command-line compiler option.</span></span>  
  
 <span data-ttu-id="c21ac-155">Par exemple, vous pouvez utiliser le modèle objet XML de l' .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="c21ac-155">For example, you can use the XML object model of the .NET Framework.</span></span> <span data-ttu-id="c21ac-156">Si vous définissez une référence à l' <xref:System.Xml> espace de noms, vous pouvez déclarer et utiliser l’une de ses classes, par exemple <xref:System.Xml.XmlDocument> .</span><span class="sxs-lookup"><span data-stu-id="c21ac-156">If you set a reference to the <xref:System.Xml> namespace, you can declare and use any of its classes, such as <xref:System.Xml.XmlDocument>.</span></span> <span data-ttu-id="c21ac-157">L'exemple suivant utilise <xref:System.Xml.XmlDocument>.</span><span class="sxs-lookup"><span data-stu-id="c21ac-157">The following example uses <xref:System.Xml.XmlDocument>.</span></span>  
  
```vb  
' Assume this project has a reference to System.Xml  
' The following statement creates xDoc as an XML document object.  
Dim xDoc As System.Xml.XmlDocument  
```  
  
## <a name="importing-containing-elements"></a><span data-ttu-id="c21ac-158">Importation d’éléments contenants</span><span class="sxs-lookup"><span data-stu-id="c21ac-158">Importing Containing Elements</span></span>  

 <span data-ttu-id="c21ac-159">Vous pouvez utiliser l' [instruction Imports (espace de noms et type .net)](../../../language-reference/statements/imports-statement-net-namespace-and-type.md) pour *Importer* les espaces de noms qui contiennent les modules ou les classes que vous souhaitez utiliser.</span><span class="sxs-lookup"><span data-stu-id="c21ac-159">You can use the [Imports Statement (.NET Namespace and Type)](../../../language-reference/statements/imports-statement-net-namespace-and-type.md) to *import* the namespaces that contain the modules or classes that you want to use.</span></span> <span data-ttu-id="c21ac-160">Cela vous permet de faire référence aux éléments définis dans un espace de noms importé sans qualification complète de leurs noms.</span><span class="sxs-lookup"><span data-stu-id="c21ac-160">This enables you to refer to the elements defined in an imported namespace without fully qualifying their names.</span></span> <span data-ttu-id="c21ac-161">L’exemple suivant réécrit l’exemple précédent pour importer l' <xref:System.Xml> espace de noms.</span><span class="sxs-lookup"><span data-stu-id="c21ac-161">The following example rewrites the previous example to import the <xref:System.Xml> namespace.</span></span>  
  
```vb  
' Assume this project has a reference to System.Xml  
' The following statement must precede all your declarations.  
Imports System.Xml  
' The following statement creates xDoc as an XML document object.  
Dim xDoc As XmlDocument  
```  
  
 <span data-ttu-id="c21ac-162">En outre, l' `Imports` instruction peut définir un *alias d’importation* pour chaque espace de noms importé.</span><span class="sxs-lookup"><span data-stu-id="c21ac-162">In addition, the `Imports` statement can define an *import alias* for each imported namespace.</span></span> <span data-ttu-id="c21ac-163">Cela peut rendre le code source plus concis et plus facile à lire.</span><span class="sxs-lookup"><span data-stu-id="c21ac-163">This can make the source code shorter and easier to read.</span></span> <span data-ttu-id="c21ac-164">L’exemple suivant réécrit l’exemple précédent pour l’utiliser `xD` en tant qu’alias pour l' <xref:System.Xml> espace de noms.</span><span class="sxs-lookup"><span data-stu-id="c21ac-164">The following example rewrites the previous example to use `xD` as an alias for the <xref:System.Xml> namespace.</span></span>  
  
```vb  
' Assume this project has a reference to System.Xml  
' The following statement must precede all your declarations.  
Imports xD = System.Xml  
' The following statement creates xDoc as an XML document object.  
Dim xDoc As xD.XmlDocument  
```  
  
 <span data-ttu-id="c21ac-165">L' `Imports` instruction ne rend pas les éléments d’autres projets disponibles pour votre application.</span><span class="sxs-lookup"><span data-stu-id="c21ac-165">The `Imports` statement does not make elements from other projects available to your application.</span></span> <span data-ttu-id="c21ac-166">Autrement dit, il ne remplace pas la définition d’une référence.</span><span class="sxs-lookup"><span data-stu-id="c21ac-166">That is, it does not take the place of setting a reference.</span></span> <span data-ttu-id="c21ac-167">L’importation d’un espace de noms supprime simplement la nécessité de qualifier les noms définis dans cet espace de noms.</span><span class="sxs-lookup"><span data-stu-id="c21ac-167">Importing a namespace just removes the requirement to qualify the names defined in that namespace.</span></span>  
  
 <span data-ttu-id="c21ac-168">Vous pouvez également utiliser l' `Imports` instruction pour importer des modules, des classes, des structures et des énumérations.</span><span class="sxs-lookup"><span data-stu-id="c21ac-168">You can also use the `Imports` statement to import modules, classes, structures, and enumerations.</span></span> <span data-ttu-id="c21ac-169">Vous pouvez ensuite utiliser les membres de ces éléments importés sans qualification.</span><span class="sxs-lookup"><span data-stu-id="c21ac-169">You can then use the members of such imported elements without qualification.</span></span> <span data-ttu-id="c21ac-170">Toutefois, vous devez toujours qualifier les membres non partagés des classes et des structures à l’aide d’une variable ou d’une expression qui prend la valeur d’une instance de la classe ou de la structure.</span><span class="sxs-lookup"><span data-stu-id="c21ac-170">However, you must always qualify nonshared members of classes and structures with a variable or expression that evaluates to an instance of the class or structure.</span></span>  
  
## <a name="naming-guidelines"></a><span data-ttu-id="c21ac-171">Indications concernant l'attribution d'un nom</span><span class="sxs-lookup"><span data-stu-id="c21ac-171">Naming Guidelines</span></span>  

 <span data-ttu-id="c21ac-172">Lorsque vous définissez deux ou plusieurs éléments de programmation portant le même nom, une *ambiguïté de nom* peut se produire lorsque le compilateur tente de résoudre une référence à ce nom.</span><span class="sxs-lookup"><span data-stu-id="c21ac-172">When you define two or more programming elements that have the same name, a *name ambiguity* can result when the compiler attempts to resolve a reference to that name.</span></span> <span data-ttu-id="c21ac-173">Si plusieurs définitions sont dans la portée, ou si aucune définition n’est dans la portée, la référence est insoluble.</span><span class="sxs-lookup"><span data-stu-id="c21ac-173">If more than one definition is in scope, or if no definition is in scope, the reference is irresolvable.</span></span> <span data-ttu-id="c21ac-174">Pour obtenir un exemple, consultez « exemple de référence qualifiée » dans cette page d’aide.</span><span class="sxs-lookup"><span data-stu-id="c21ac-174">For an example, see "Qualified Reference Example" on this Help page.</span></span>  
  
 <span data-ttu-id="c21ac-175">Vous pouvez éviter toute ambiguïté de nom en attribuant à tous vos éléments des noms uniques.</span><span class="sxs-lookup"><span data-stu-id="c21ac-175">You can avoid name ambiguity by giving all your elements unique names.</span></span> <span data-ttu-id="c21ac-176">Vous pouvez ensuite faire référence à n’importe quel élément sans avoir à qualifier son nom avec un espace de noms, un module ou une classe.</span><span class="sxs-lookup"><span data-stu-id="c21ac-176">Then you can make reference to any element without having to qualify its name with a namespace, module, or class.</span></span> <span data-ttu-id="c21ac-177">Vous réduisez également le risque de faire référence à un élément incorrect.</span><span class="sxs-lookup"><span data-stu-id="c21ac-177">You also reduce the chances of accidentally referring to the wrong element.</span></span>  
  
## <a name="shadowing"></a><span data-ttu-id="c21ac-178">Copie shadow</span><span class="sxs-lookup"><span data-stu-id="c21ac-178">Shadowing</span></span>  

 <span data-ttu-id="c21ac-179">Lorsque deux éléments de programmation partagent le même nom, l’un d’eux peut masquer ou *occulter*l’autre.</span><span class="sxs-lookup"><span data-stu-id="c21ac-179">When two programming elements share the same name, one of them can hide, or *shadow*, the other one.</span></span> <span data-ttu-id="c21ac-180">Un élément occulté n’est pas disponible à des fins de référence ; au lieu de cela, lorsque votre code utilise le nom d’élément occulté, le compilateur Visual Basic le résout en l’élément occultant.</span><span class="sxs-lookup"><span data-stu-id="c21ac-180">A shadowed element is not available for reference; instead, when your code uses the shadowed element name, the Visual Basic compiler resolves it to the shadowing element.</span></span> <span data-ttu-id="c21ac-181">Pour obtenir une explication plus détaillée des exemples, consultez [occultation dans Visual Basic](shadowing.md).</span><span class="sxs-lookup"><span data-stu-id="c21ac-181">For a more detailed explanation with examples, see [Shadowing in Visual Basic](shadowing.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c21ac-182">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c21ac-182">See also</span></span>

- [<span data-ttu-id="c21ac-183">Declared Element Names</span><span class="sxs-lookup"><span data-stu-id="c21ac-183">Declared Element Names</span></span>](declared-element-names.md)
- [<span data-ttu-id="c21ac-184">Caractéristiques des éléments déclarés</span><span class="sxs-lookup"><span data-stu-id="c21ac-184">Declared Element Characteristics</span></span>](declared-element-characteristics.md)
- [<span data-ttu-id="c21ac-185">Gestion des propriétés des projets et des solutions</span><span class="sxs-lookup"><span data-stu-id="c21ac-185">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
- [<span data-ttu-id="c21ac-186">Variables</span><span class="sxs-lookup"><span data-stu-id="c21ac-186">Variables</span></span>](../variables/index.md)
- [<span data-ttu-id="c21ac-187">Imports, instruction (espace de noms et type .NET)</span><span class="sxs-lookup"><span data-stu-id="c21ac-187">Imports Statement (.NET Namespace and Type)</span></span>](../../../language-reference/statements/imports-statement-net-namespace-and-type.md)
- [<span data-ttu-id="c21ac-188">Nouvel opérateur</span><span class="sxs-lookup"><span data-stu-id="c21ac-188">New Operator</span></span>](../../../language-reference/operators/new-operator.md)
- [<span data-ttu-id="c21ac-189">Public</span><span class="sxs-lookup"><span data-stu-id="c21ac-189">Public</span></span>](../../../language-reference/modifiers/public.md)
