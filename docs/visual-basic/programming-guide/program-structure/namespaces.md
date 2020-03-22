---
title: Espaces de noms
ms.date: 07/20/2015
f1_keywords:
- vb.global
helpviewer_keywords:
- assemblies [Visual Basic], namespaces
- name collisions
- Global keyword [Visual Basic]
- namespace pollution
- names [Visual Basic], avoiding conflicts
- naming conflicts [Visual Basic], namespaces
- namespaces [Visual Basic], assemblies
- Visual Basic code, namespaces
- fully qualified names [Visual Basic]
- naming conventions [Visual Basic], naming conflicts
- namespaces
ms.assetid: cffac744-ab8c-4f1f-ba50-732c22ab4b88
ms.openlocfilehash: ec892167f30a7ded739dc188ab4096cb3a5d154c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400672"
---
# <a name="namespaces-in-visual-basic"></a><span data-ttu-id="41be7-102">Espaces de noms dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="41be7-102">Namespaces in Visual Basic</span></span>
<span data-ttu-id="41be7-103">Les espaces de noms permettent d’organiser les objets définis dans un assembly.</span><span class="sxs-lookup"><span data-stu-id="41be7-103">Namespaces organize the objects defined in an assembly.</span></span> <span data-ttu-id="41be7-104">Les assemblys peuvent contenir plusieurs espaces de noms, qui peuvent à leur tour contenir d’autres espaces de noms.</span><span class="sxs-lookup"><span data-stu-id="41be7-104">Assemblies can contain multiple namespaces, which can in turn contain other namespaces.</span></span> <span data-ttu-id="41be7-105">Les espaces de noms permettent d’éviter les ambiguïtés et de simplifier les références quand de grands groupes d’objets, tels que des bibliothèques de classes, sont utilisés.</span><span class="sxs-lookup"><span data-stu-id="41be7-105">Namespaces prevent ambiguity and simplify references when using large groups of objects such as class libraries.</span></span>  
  
 <span data-ttu-id="41be7-106">Par exemple, le cadre .NET définit la <xref:System.Windows.Forms.ListBox> classe dans l’espace de <xref:System.Windows.Forms?displayProperty=nameWithType> nom.</span><span class="sxs-lookup"><span data-stu-id="41be7-106">For example, the .NET Framework defines the <xref:System.Windows.Forms.ListBox> class in the <xref:System.Windows.Forms?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="41be7-107">Le fragment de code suivant montre comment déclarer une variable en utilisant le nom qualifié complet de cette classe :</span><span class="sxs-lookup"><span data-stu-id="41be7-107">The following code fragment shows how to declare a variable using the fully qualified name for this class:</span></span>  
  
 [!code-vb[VbVbalrApplication#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/Class1.vb#6)]  
  
## <a name="avoiding-name-collisions"></a><span data-ttu-id="41be7-108">Éviter les collisions de noms</span><span class="sxs-lookup"><span data-stu-id="41be7-108">Avoiding Name Collisions</span></span>  
 <span data-ttu-id="41be7-109">.NET Les espaces nominaux du Cadre abordent un problème parfois appelé *pollution par l’espace de nom,* dans lequel le développeur d’une bibliothèque de classe est entravé par l’utilisation de noms similaires dans une autre bibliothèque.</span><span class="sxs-lookup"><span data-stu-id="41be7-109">.NET Framework namespaces address a problem sometimes called *namespace pollution*, in which the developer of a class library is hampered by the use of similar names in another library.</span></span> <span data-ttu-id="41be7-110">Ces conflits avec des éléments existants sont également connus sous le terme de *collisions de noms*.</span><span class="sxs-lookup"><span data-stu-id="41be7-110">These conflicts with existing components are sometimes called *name collisions*.</span></span>  
  
 <span data-ttu-id="41be7-111">Par exemple, si vous créez une classe nommée `ListBox`, vous pouvez l’utiliser dans votre projet sans qualification.</span><span class="sxs-lookup"><span data-stu-id="41be7-111">For example, if you create a new class named `ListBox`, you can use it inside your project without qualification.</span></span> <span data-ttu-id="41be7-112">Toutefois, si vous souhaitez utiliser <xref:System.Windows.Forms.ListBox> la classe cadre .NET dans le même projet, vous devez utiliser une référence entièrement qualifiée pour rendre la référence unique.</span><span class="sxs-lookup"><span data-stu-id="41be7-112">However, if you want to use the .NET Framework <xref:System.Windows.Forms.ListBox> class in the same project, you must use a fully qualified reference to make the reference unique.</span></span> <span data-ttu-id="41be7-113">Si la référence n’est pas unique, Visual Basic produit une erreur indiquant que le nom est ambigu.</span><span class="sxs-lookup"><span data-stu-id="41be7-113">If the reference is not unique, Visual Basic produces an error stating that the name is ambiguous.</span></span> <span data-ttu-id="41be7-114">L’exemple de code suivant montre comment déclarer ces objets :</span><span class="sxs-lookup"><span data-stu-id="41be7-114">The following code example demonstrates how to declare these objects:</span></span>  
  
 [!code-vb[VbVbalrApplication#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/Class1.vb#7)]  
  
 <span data-ttu-id="41be7-115">L’illustration suivante montre deux hiérarchies namespace, `ListBox`toutes deux contenant un objet nommé :</span><span class="sxs-lookup"><span data-stu-id="41be7-115">The following illustration shows two namespace hierarchies, both containing an object named `ListBox`:</span></span>  
  
 ![Capture d’écran qui montre deux hiérarchies namespace.](./media/namespaces/visual-basic-namespace-hierarchy.gif)  
  
 <span data-ttu-id="41be7-117">Par défaut, chaque fichier exécutable que vous créez avec Visual Basic contient un espace de nom du même nom que votre projet.</span><span class="sxs-lookup"><span data-stu-id="41be7-117">By default, every executable file you create with Visual Basic contains a namespace with the same name as your project.</span></span> <span data-ttu-id="41be7-118">Par exemple, si vous définissez un objet dans un projet nommé `ListBoxProject`, le fichier exécutable, ListBoxProject.exe, contient un espace de noms appelé `ListBoxProject`.</span><span class="sxs-lookup"><span data-stu-id="41be7-118">For example, if you define an object within a project named `ListBoxProject`, the executable file ListBoxProject.exe contains a namespace called `ListBoxProject`.</span></span>  
  
 <span data-ttu-id="41be7-119">Plusieurs assemblys peuvent utiliser le même espace de noms.</span><span class="sxs-lookup"><span data-stu-id="41be7-119">Multiple assemblies can use the same namespace.</span></span> <span data-ttu-id="41be7-120">Visual Basic les traite comme un seul ensemble de noms.</span><span class="sxs-lookup"><span data-stu-id="41be7-120">Visual Basic treats them as a single set of names.</span></span> <span data-ttu-id="41be7-121">Par exemple, vous pouvez définir des classes pour un espace de noms appelé `SomeNameSpace` dans un assembly nommé `Assemb1`, et définir des classes supplémentaires pour le même espace de noms d’un assembly nommé `Assemb2`.</span><span class="sxs-lookup"><span data-stu-id="41be7-121">For example, you can define classes for a namespace called `SomeNameSpace` in an assembly named `Assemb1`, and define additional classes for the same namespace from an assembly named `Assemb2`.</span></span>  
  
## <a name="fully-qualified-names"></a><span data-ttu-id="41be7-122">noms qualifiés complets</span><span class="sxs-lookup"><span data-stu-id="41be7-122">Fully Qualified Names</span></span>  
 <span data-ttu-id="41be7-123">Les noms qualifiés complets sont des références d’objet dont le préfixe est le nom de l’espace de noms dans lequel l’objet est défini.</span><span class="sxs-lookup"><span data-stu-id="41be7-123">Fully qualified names are object references that are prefixed with the name of the namespace in which the object is defined.</span></span> <span data-ttu-id="41be7-124">Vous pouvez utiliser les objets définis dans d’autres projets si vous créez une référence à la classe (en choisissant **Ajouter une référence** dans le menu **Projet** ), puis utiliser le nom qualifié complet de l’objet dans votre code.</span><span class="sxs-lookup"><span data-stu-id="41be7-124">You can use objects defined in other projects if you create a reference to the class (by choosing **Add Reference** from the **Project** menu) and then use the fully qualified name for the object in your code.</span></span> <span data-ttu-id="41be7-125">Le fragment de code suivant montre comment utiliser le nom qualifié complet d’un objet provenant de l’espace de noms d’un autre projet :</span><span class="sxs-lookup"><span data-stu-id="41be7-125">The following code fragment shows how to use the fully qualified name for an object from another project's namespace:</span></span>  
  
 [!code-vb[VbVbalrApplication#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/Class1.vb#8)]  
  
 <span data-ttu-id="41be7-126">Les noms qualifiés complets empêchent les conflits de nommage, car ils permettent au compilateur d’identifier l’objet utilisé.</span><span class="sxs-lookup"><span data-stu-id="41be7-126">Fully qualified names prevent naming conflicts because they make it possible for the compiler to determine which object is being used.</span></span> <span data-ttu-id="41be7-127">Toutefois, les noms peuvent devenir longs et compliqués.</span><span class="sxs-lookup"><span data-stu-id="41be7-127">However, the names themselves can get long and cumbersome.</span></span> <span data-ttu-id="41be7-128">Pour contourner ce problème, utilisez l’instruction `Imports` pour définir un *alias*, qui est un nom abrégé utilisable à la place d’un nom qualifié complet.</span><span class="sxs-lookup"><span data-stu-id="41be7-128">To get around this, you can use the `Imports` statement to define an *alias*—an abbreviated name you can use in place of a fully qualified name.</span></span> <span data-ttu-id="41be7-129">L’exemple de code ci-dessous crée les alias de deux noms qualifiés complets, puis utilise ces alias pour définir deux objets.</span><span class="sxs-lookup"><span data-stu-id="41be7-129">For example, the following code example creates aliases for two fully qualified names, and uses these aliases to define two objects.</span></span>  
  
 [!code-vb[VbVbalrApplication#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/Class1.vb#9)]  
  
 [!code-vb[VbVbalrApplication#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/Class1.vb#10)]  
  
 <span data-ttu-id="41be7-130">Si vous utilisez l’instruction `Imports` sans alias, vous pouvez vous servir de tous les noms de l’espace de noms sans qualification, à condition qu’ils soient uniques au sein du projet.</span><span class="sxs-lookup"><span data-stu-id="41be7-130">If you use the `Imports` statement without an alias, you can use all the names in that namespace without qualification, provided they are unique to the project.</span></span> <span data-ttu-id="41be7-131">Si votre projet contient des instructions `Imports` pour les espaces de noms contenant des éléments de même nom, vous devez fournir un nom qualifié complet quand vous l’utilisez.</span><span class="sxs-lookup"><span data-stu-id="41be7-131">If your project contains `Imports` statements for namespaces that contain items with the same name, you must fully qualify that name when you use it.</span></span> <span data-ttu-id="41be7-132">Imaginons, par exemple, que votre projet contient les deux instructions `Imports` suivantes :</span><span class="sxs-lookup"><span data-stu-id="41be7-132">Suppose, for example, your project contained the following two `Imports` statements:</span></span>  
  
 [!code-vb[VbVbalrApplication#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/Class1.vb#11)]  
  
 <span data-ttu-id="41be7-133">Si vous essayez `Class1` d’utiliser sans le qualifier complètement, `Class1` Visual Basic produit une erreur indiquant que le nom est ambigu.</span><span class="sxs-lookup"><span data-stu-id="41be7-133">If you attempt to use `Class1` without fully qualifying it, Visual Basic produces an error stating that the name `Class1` is ambiguous.</span></span>  
  
## <a name="namespace-level-statements"></a><span data-ttu-id="41be7-134">Instructions au niveau de l’espace de noms</span><span class="sxs-lookup"><span data-stu-id="41be7-134">Namespace Level Statements</span></span>  
 <span data-ttu-id="41be7-135">Dans un espace de noms, vous pouvez définir des éléments tels que des modules, des interfaces, des classes, des délégués, des énumérations, des structures et d’autres espaces de noms.</span><span class="sxs-lookup"><span data-stu-id="41be7-135">Within a namespace, you can define items such as modules, interfaces, classes, delegates, enumerations, structures, and other namespaces.</span></span> <span data-ttu-id="41be7-136">Vous ne pouvez pas définir d’éléments tels que des propriétés, des procédures, des variables et des événements au niveau de l’espace de noms.</span><span class="sxs-lookup"><span data-stu-id="41be7-136">You cannot define items such as properties, procedures, variables and events at the namespace level.</span></span> <span data-ttu-id="41be7-137">Ces éléments doivent être déclarés dans des conteneurs tels que des modules, des structures ou des classes.</span><span class="sxs-lookup"><span data-stu-id="41be7-137">These items must be declared within containers such as modules, structures, or classes.</span></span>  
  
## <a name="global-keyword-in-fully-qualified-names"></a><span data-ttu-id="41be7-138">Mot clé Global dans les noms qualifiés complets</span><span class="sxs-lookup"><span data-stu-id="41be7-138">Global Keyword in Fully Qualified Names</span></span>  
 <span data-ttu-id="41be7-139">Si vous avez défini une hiérarchie imbriquée d’espaces de noms, le code à l’intérieur de cette hiérarchie peut ne pas avoir accès à l’espace de noms <xref:System?displayProperty=nameWithType> de .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="41be7-139">If you have defined a nested hierarchy of namespaces, code inside that hierarchy might be blocked from accessing the <xref:System?displayProperty=nameWithType> namespace of the .NET Framework.</span></span> <span data-ttu-id="41be7-140">L’exemple suivant illustre une hiérarchie dans laquelle l’espace de noms `SpecialSpace.System` bloque l’accès à <xref:System?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="41be7-140">The following example illustrates a hierarchy in which the `SpecialSpace.System` namespace blocks access to <xref:System?displayProperty=nameWithType>.</span></span>  
  
```vb  
Namespace SpecialSpace  
    Namespace System  
        Class abc  
            Function getValue() As System.Int32  
                Dim n As System.Int32  
                Return n  
            End Function  
        End Class  
    End Namespace  
End Namespace  
```  
  
 <span data-ttu-id="41be7-141">Le compilateur Visual Basic ne peut donc pas résoudre la référence à <xref:System.Int32?displayProperty=nameWithType>, car `SpecialSpace.System` ne définit pas `Int32`.</span><span class="sxs-lookup"><span data-stu-id="41be7-141">As a result, the Visual Basic compiler cannot successfully resolve the reference to <xref:System.Int32?displayProperty=nameWithType>, because `SpecialSpace.System` does not define `Int32`.</span></span> <span data-ttu-id="41be7-142">Vous pouvez utiliser le mot clé `Global` pour démarrer la chaîne de qualification au niveau le plus externe de la bibliothèque de classes du .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="41be7-142">You can use the `Global` keyword to start the qualification chain at the outermost level of the .NET Framework class library.</span></span> <span data-ttu-id="41be7-143">Cela vous permet de spécifier l’espace de noms <xref:System?displayProperty=nameWithType> ou un autre espace de noms dans la bibliothèque de classes.</span><span class="sxs-lookup"><span data-stu-id="41be7-143">This allows you to specify the <xref:System?displayProperty=nameWithType> namespace or any other namespace in the class library.</span></span> <span data-ttu-id="41be7-144">L'exemple suivant illustre ce comportement.</span><span class="sxs-lookup"><span data-stu-id="41be7-144">The following example illustrates this.</span></span>  
  
```vb  
Namespace SpecialSpace  
    Namespace System  
        Class abc  
            Function getValue() As Global.System.Int32  
                Dim n As Global.System.Int32  
                Return n  
            End Function  
        End Class  
    End Namespace  
End Namespace  
```  
  
 <span data-ttu-id="41be7-145">Utilisez aussi `Global` pour accéder à d’autres espaces de noms à la racine, tels que <xref:Microsoft.VisualBasic?displayProperty=nameWithType>, et aux espaces de noms associés à votre projet.</span><span class="sxs-lookup"><span data-stu-id="41be7-145">You can use `Global` to access other root-level namespaces, such as <xref:Microsoft.VisualBasic?displayProperty=nameWithType>, and any namespace associated with your project.</span></span>  
  
## <a name="global-keyword-in-namespace-statements"></a><span data-ttu-id="41be7-146">Mot clé Global dans les instructions Namespace</span><span class="sxs-lookup"><span data-stu-id="41be7-146">Global Keyword in Namespace Statements</span></span>  
 <span data-ttu-id="41be7-147">Vous pouvez également utiliser le mot clé `Global` dans une [Namespace Statement](../../../visual-basic/language-reference/statements/namespace-statement.md).</span><span class="sxs-lookup"><span data-stu-id="41be7-147">You can also use the `Global` keyword in a [Namespace Statement](../../../visual-basic/language-reference/statements/namespace-statement.md).</span></span> <span data-ttu-id="41be7-148">pour définir un espace de noms hors de l’espace de noms racine de votre projet.</span><span class="sxs-lookup"><span data-stu-id="41be7-148">This lets you define a namespace out of the root namespace of your project.</span></span>  
  
 <span data-ttu-id="41be7-149">Tous les espaces de noms dans votre projet sont basés sur l’espace de noms racine du projet.</span><span class="sxs-lookup"><span data-stu-id="41be7-149">All namespaces in your project are based on the root namespace for the project.</span></span>  <span data-ttu-id="41be7-150">Visual Studio définit le nom de votre projet comme espace de noms racine par défaut pour l’ensemble du code de votre projet.</span><span class="sxs-lookup"><span data-stu-id="41be7-150">Visual Studio assigns your project name as the default root namespace for all code in your project.</span></span> <span data-ttu-id="41be7-151">Par exemple, si votre projet est nommé `ConsoleApplication1`, ses éléments de programmation appartiennent à l’espace de noms `ConsoleApplication1`.</span><span class="sxs-lookup"><span data-stu-id="41be7-151">For example, if your project is named `ConsoleApplication1`, its programming elements belong to namespace `ConsoleApplication1`.</span></span> <span data-ttu-id="41be7-152">Si vous déclarez `Namespace Magnetosphere`, les références à `Magnetosphere` dans le projet doivent accéder à `ConsoleApplication1.Magnetosphere`.</span><span class="sxs-lookup"><span data-stu-id="41be7-152">If you declare `Namespace Magnetosphere`, references to `Magnetosphere` in the project will access `ConsoleApplication1.Magnetosphere`.</span></span>  
  
 <span data-ttu-id="41be7-153">Les exemples suivants utilisent le mot clé `Global` pour déclarer un espace de noms hors de l’espace de noms racine du projet.</span><span class="sxs-lookup"><span data-stu-id="41be7-153">The following examples use the `Global` keyword to declare a namespace out of the root namespace for the project.</span></span>  
  
 [!code-vb[VbVbalrApplication#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/module1.vb#22)]  
  
 <span data-ttu-id="41be7-154">Dans une déclaration d’espace de noms, `Global` ne peut pas être imbriqué dans un autre espace de noms.</span><span class="sxs-lookup"><span data-stu-id="41be7-154">In a namespace declaration, `Global` cannot be nested in another namespace.</span></span>  
  
 <span data-ttu-id="41be7-155">Vous pouvez utiliser la [Application Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic) pour afficher et modifier l’ **espace de noms racine** du projet.</span><span class="sxs-lookup"><span data-stu-id="41be7-155">You can use the [Application Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic) to view and modify the **Root Namespace** of the project.</span></span>  <span data-ttu-id="41be7-156">Pour les nouveaux projets, l’ **espace de noms racine** correspond par défaut au nom du projet.</span><span class="sxs-lookup"><span data-stu-id="41be7-156">For new projects, the **Root Namespace** defaults to the project name.</span></span> <span data-ttu-id="41be7-157">Pour définir `Global` comme espace de noms de premier niveau, effacez l’entrée **Espace de noms racine** pour que la zone soit vide.</span><span class="sxs-lookup"><span data-stu-id="41be7-157">To cause `Global` to be the top-level namespace, you can clear the **Root Namespace** entry so that the box is empty.</span></span> <span data-ttu-id="41be7-158">Quand l’entrée **Espace de noms racine** est effacée, vous n’avez pas besoin de spécifier le mot clé `Global` dans les déclarations d’espace de noms.</span><span class="sxs-lookup"><span data-stu-id="41be7-158">Clearing **Root Namespace** removes the need for the `Global` keyword in namespace declarations.</span></span>  
  
 <span data-ttu-id="41be7-159">Si une instruction `Namespace` déclare un nom qui est également un espace de noms dans le .NET Framework, l’espace de noms .NET Framework n’est plus disponible si le mot clé `Global` n’est pas utilisé dans un nom qualifié complet.</span><span class="sxs-lookup"><span data-stu-id="41be7-159">If a `Namespace` statement declares a name that is also a namespace in the .NET Framework, the .NET Framework namespace becomes unavailable if the `Global` keyword is not used in a fully qualified name.</span></span> <span data-ttu-id="41be7-160">Pour permettre l’accès à cet espace de noms .NET Framework sans utiliser le mot clé `Global` , ajoutez le mot clé `Global` dans l’instruction `Namespace` .</span><span class="sxs-lookup"><span data-stu-id="41be7-160">To enable access to that .NET Framework namespace without using the `Global` keyword, you can include the `Global` keyword in the `Namespace` statement.</span></span>  
  
 <span data-ttu-id="41be7-161">Dans l’exemple suivant, le mot clé `Global` est utilisé dans la déclaration d’espace de noms `System.Text` .</span><span class="sxs-lookup"><span data-stu-id="41be7-161">The following example has the `Global` keyword in the `System.Text` namespace declaration.</span></span>  
  
 <span data-ttu-id="41be7-162">En l’absence du mot clé `Global` dans la déclaration d’espace de noms, l’accès à <xref:System.Text.StringBuilder> n’est pas possible sans spécifier `Global.System.Text.StringBuilder`.</span><span class="sxs-lookup"><span data-stu-id="41be7-162">If the `Global` keyword was not present in the namespace declaration, <xref:System.Text.StringBuilder> could not be accessed without specifying `Global.System.Text.StringBuilder`.</span></span> <span data-ttu-id="41be7-163">Pour un projet nommé `ConsoleApplication1`, les références à `System.Text` accèdent à `ConsoleApplication1.System.Text` si le mot clé `Global` n’est pas utilisé.</span><span class="sxs-lookup"><span data-stu-id="41be7-163">For a project named `ConsoleApplication1`, references to `System.Text` would access `ConsoleApplication1.System.Text` if the `Global` keyword was not used.</span></span>  
  
 [!code-vb[VbVbalrApplication#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/module1.vb#21)]  
  
## <a name="see-also"></a><span data-ttu-id="41be7-164">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="41be7-164">See also</span></span>

- <xref:System.Windows.Forms.ListBox>
- <xref:System.Windows.Forms?displayProperty=nameWithType>
- [<span data-ttu-id="41be7-165">Assemblys dans .NET</span><span class="sxs-lookup"><span data-stu-id="41be7-165">Assemblies in .NET</span></span>](../../../standard/assembly/index.md)
- [<span data-ttu-id="41be7-166">Références et instruction Imports</span><span class="sxs-lookup"><span data-stu-id="41be7-166">References and the Imports Statement</span></span>](references-and-the-imports-statement.md)
- [<span data-ttu-id="41be7-167">Imports (instruction) (espace de noms et type .NET)</span><span class="sxs-lookup"><span data-stu-id="41be7-167">Imports Statement (.NET Namespace and Type)</span></span>](../../language-reference/statements/imports-statement-net-namespace-and-type.md)
- [<span data-ttu-id="41be7-168">Écriture de code dans les solutions Office</span><span class="sxs-lookup"><span data-stu-id="41be7-168">Writing Code in Office Solutions</span></span>](/visualstudio/vsto/writing-code-in-office-solutions)
