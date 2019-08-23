---
title: Using, instruction (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.using
helpviewer_keywords:
- resource disposal
- Try...Catch...Finally statements, equivalent to Using statement
- resources [Visual Basic], disposing
- Using statement [Visual Basic]
ms.assetid: 665d1580-dd54-4e96-a9a9-6be2a68948f1
ms.openlocfilehash: 346a26ad5751599831d8b0d3e0497e4d488eb76c
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69957547"
---
# <a name="using-statement-visual-basic"></a><span data-ttu-id="a9d1a-102">Using, instruction (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a9d1a-102">Using Statement (Visual Basic)</span></span>
<span data-ttu-id="a9d1a-103">Déclare le début d’un `Using` bloc et acquiert éventuellement les ressources système que le bloc contrôle.</span><span class="sxs-lookup"><span data-stu-id="a9d1a-103">Declares the beginning of a `Using` block and optionally acquires the system resources that the block controls.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a9d1a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a9d1a-104">Syntax</span></span>  
  
```  
Using { resourcelist | resourceexpression }  
    [ statements ]  
End Using  
```  
  
## <a name="parts"></a><span data-ttu-id="a9d1a-105">Composants</span><span class="sxs-lookup"><span data-stu-id="a9d1a-105">Parts</span></span>  
  
|<span data-ttu-id="a9d1a-106">Terme</span><span class="sxs-lookup"><span data-stu-id="a9d1a-106">Term</span></span>|<span data-ttu-id="a9d1a-107">Définition</span><span class="sxs-lookup"><span data-stu-id="a9d1a-107">Definition</span></span>|  
|---|---|  
|`resourcelist`|<span data-ttu-id="a9d1a-108">Obligatoire si vous ne fournissez `resourceexpression`pas.</span><span class="sxs-lookup"><span data-stu-id="a9d1a-108">Required if you do not supply `resourceexpression`.</span></span> <span data-ttu-id="a9d1a-109">Liste d’une ou plusieurs ressources système que ce `Using` bloc contrôle, séparées par des virgules.</span><span class="sxs-lookup"><span data-stu-id="a9d1a-109">List of one or more system resources that this `Using` block controls, separated by commas.</span></span>|  
|`resourceexpression`|<span data-ttu-id="a9d1a-110">Obligatoire si vous ne fournissez `resourcelist`pas.</span><span class="sxs-lookup"><span data-stu-id="a9d1a-110">Required if you do not supply `resourcelist`.</span></span> <span data-ttu-id="a9d1a-111">Variable ou expression de référence faisant référence à une ressource système pour être contrôlée `Using` par ce bloc.</span><span class="sxs-lookup"><span data-stu-id="a9d1a-111">Reference variable or expression referring to a system resource to be controlled by this `Using` block.</span></span>|  
|`statements`|<span data-ttu-id="a9d1a-112">facultatif.</span><span class="sxs-lookup"><span data-stu-id="a9d1a-112">Optional.</span></span> <span data-ttu-id="a9d1a-113">Bloc d’instructions exécutées `Using` par le bloc.</span><span class="sxs-lookup"><span data-stu-id="a9d1a-113">Block of statements that the `Using` block runs.</span></span>|  
|`End Using`|<span data-ttu-id="a9d1a-114">Requis.</span><span class="sxs-lookup"><span data-stu-id="a9d1a-114">Required.</span></span> <span data-ttu-id="a9d1a-115">Met fin à la définition du `Using` bloc et supprime toutes les ressources qu’il contrôle.</span><span class="sxs-lookup"><span data-stu-id="a9d1a-115">Terminates the definition of the `Using` block and disposes of all the resources that it controls.</span></span>|  
  
 <span data-ttu-id="a9d1a-116">Chaque ressource de la `resourcelist` partie possède la syntaxe et les éléments suivants:</span><span class="sxs-lookup"><span data-stu-id="a9d1a-116">Each resource in the `resourcelist` part has the following syntax and parts:</span></span>  
  
 `resourcename As New resourcetype [ ( [ arglist ] ) ]`  
  
 <span data-ttu-id="a9d1a-117">ou</span><span class="sxs-lookup"><span data-stu-id="a9d1a-117">-or-</span></span>  
  
 `resourcename As resourcetype = resourceexpression`  
  
## <a name="resourcelist-parts"></a><span data-ttu-id="a9d1a-118">Composants ResourceList</span><span class="sxs-lookup"><span data-stu-id="a9d1a-118">resourcelist Parts</span></span>  
  
|<span data-ttu-id="a9d1a-119">Terme</span><span class="sxs-lookup"><span data-stu-id="a9d1a-119">Term</span></span>|<span data-ttu-id="a9d1a-120">Définition</span><span class="sxs-lookup"><span data-stu-id="a9d1a-120">Definition</span></span>|  
|---|---|  
|`resourcename`|<span data-ttu-id="a9d1a-121">Requis.</span><span class="sxs-lookup"><span data-stu-id="a9d1a-121">Required.</span></span> <span data-ttu-id="a9d1a-122">Variable de référence qui fait référence à une ressource système `Using` que le bloc contrôle.</span><span class="sxs-lookup"><span data-stu-id="a9d1a-122">Reference variable that refers to a system resource that the `Using` block controls.</span></span>|  
|`New`|<span data-ttu-id="a9d1a-123">Obligatoire si l' `Using` instruction acquiert la ressource.</span><span class="sxs-lookup"><span data-stu-id="a9d1a-123">Required if the `Using` statement acquires the resource.</span></span> <span data-ttu-id="a9d1a-124">Si vous avez déjà acquis la ressource, utilisez la deuxième syntaxe.</span><span class="sxs-lookup"><span data-stu-id="a9d1a-124">If you have already acquired the resource, use the second syntax alternative.</span></span>|  
|`resourcetype`|<span data-ttu-id="a9d1a-125">Requis.</span><span class="sxs-lookup"><span data-stu-id="a9d1a-125">Required.</span></span> <span data-ttu-id="a9d1a-126">Classe de la ressource.</span><span class="sxs-lookup"><span data-stu-id="a9d1a-126">The class of the resource.</span></span> <span data-ttu-id="a9d1a-127">La classe doit implémenter <xref:System.IDisposable> l’interface.</span><span class="sxs-lookup"><span data-stu-id="a9d1a-127">The class must implement the <xref:System.IDisposable> interface.</span></span>|  
|`arglist`|<span data-ttu-id="a9d1a-128">facultatif.</span><span class="sxs-lookup"><span data-stu-id="a9d1a-128">Optional.</span></span> <span data-ttu-id="a9d1a-129">Liste des arguments que vous passez au constructeur pour créer une instance de `resourcetype`.</span><span class="sxs-lookup"><span data-stu-id="a9d1a-129">List of arguments you are passing to the constructor to create an instance of `resourcetype`.</span></span> <span data-ttu-id="a9d1a-130">Consultez la [liste des paramètres](../../../visual-basic/language-reference/statements/parameter-list.md).</span><span class="sxs-lookup"><span data-stu-id="a9d1a-130">See [Parameter List](../../../visual-basic/language-reference/statements/parameter-list.md).</span></span>|  
|`resourceexpression`|<span data-ttu-id="a9d1a-131">Requis.</span><span class="sxs-lookup"><span data-stu-id="a9d1a-131">Required.</span></span> <span data-ttu-id="a9d1a-132">Variable ou expression faisant référence à une ressource système répondant aux exigences `resourcetype`de.</span><span class="sxs-lookup"><span data-stu-id="a9d1a-132">Variable or expression referring to a system resource satisfying the requirements of `resourcetype`.</span></span> <span data-ttu-id="a9d1a-133">Si vous utilisez la deuxième syntaxe, vous devez acquérir la ressource avant de passer le contrôle à `Using` l’instruction.</span><span class="sxs-lookup"><span data-stu-id="a9d1a-133">If you use the second syntax alternative, you must acquire the resource before passing control to the `Using` statement.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a9d1a-134">Notes</span><span class="sxs-lookup"><span data-stu-id="a9d1a-134">Remarks</span></span>  
 <span data-ttu-id="a9d1a-135">Parfois, votre code requiert une ressource non managée, telle qu’un descripteur de fichier, un wrapper COM ou une connexion SQL.</span><span class="sxs-lookup"><span data-stu-id="a9d1a-135">Sometimes your code requires an unmanaged resource, such as a file handle, a COM wrapper, or a SQL connection.</span></span> <span data-ttu-id="a9d1a-136">Un `Using` bloc garantit la suppression d’une ou de plusieurs de ces ressources lorsque votre code est terminé.</span><span class="sxs-lookup"><span data-stu-id="a9d1a-136">A `Using` block guarantees the disposal of one or more such resources when your code is finished with them.</span></span> <span data-ttu-id="a9d1a-137">Cela les rend disponibles pour le code à utiliser.</span><span class="sxs-lookup"><span data-stu-id="a9d1a-137">This makes them available for other code to use.</span></span>  
  
 <span data-ttu-id="a9d1a-138">Les ressources managées sont supprimées par le garbage collector .NET Framework (GC) sans codage supplémentaire de votre part.</span><span class="sxs-lookup"><span data-stu-id="a9d1a-138">Managed resources are disposed of by the .NET Framework garbage collector (GC) without any extra coding on your part.</span></span> <span data-ttu-id="a9d1a-139">Vous n’avez pas besoin `Using` d’un bloc pour les ressources managées.</span><span class="sxs-lookup"><span data-stu-id="a9d1a-139">You do not need a `Using` block for managed resources.</span></span> <span data-ttu-id="a9d1a-140">Toutefois, vous pouvez toujours utiliser un `Using` bloc pour forcer la suppression d’une ressource managée au lieu d’attendre le garbage collector.</span><span class="sxs-lookup"><span data-stu-id="a9d1a-140">However, you can still use a `Using` block to force the disposal of a managed resource instead of waiting for the garbage collector.</span></span>  
  
 <span data-ttu-id="a9d1a-141">Un `Using` bloc comporte trois parties: l’acquisition, l’utilisation et la suppression.</span><span class="sxs-lookup"><span data-stu-id="a9d1a-141">A `Using` block has three parts: acquisition, usage, and disposal.</span></span>  
  
- <span data-ttu-id="a9d1a-142">L' *acquisition* consiste à créer une variable et à l’initialiser pour faire référence à la ressource système.</span><span class="sxs-lookup"><span data-stu-id="a9d1a-142">*Acquisition* means creating a variable and initializing it to refer to the system resource.</span></span> <span data-ttu-id="a9d1a-143">L' `Using` instruction peut acquérir une ou plusieurs ressources, ou vous pouvez acquérir une seule ressource avant d’entrer dans le bloc et la fournir `Using` à l’instruction.</span><span class="sxs-lookup"><span data-stu-id="a9d1a-143">The `Using` statement can acquire one or more resources, or you can acquire exactly one resource before entering the block and supply it to the `Using` statement.</span></span> <span data-ttu-id="a9d1a-144">Si vous fournissez `resourceexpression`, vous devez acquérir la ressource avant de passer le `Using` contrôle à l’instruction.</span><span class="sxs-lookup"><span data-stu-id="a9d1a-144">If you supply `resourceexpression`, you must acquire the resource before passing control to the `Using` statement.</span></span>  
  
- <span data-ttu-id="a9d1a-145">*L’utilisation* consiste à accéder aux ressources et à effectuer des actions avec eux.</span><span class="sxs-lookup"><span data-stu-id="a9d1a-145">*Usage* means accessing the resources and performing actions with them.</span></span> <span data-ttu-id="a9d1a-146">Les instructions entre `Using` et `End Using` représentent l’utilisation des ressources.</span><span class="sxs-lookup"><span data-stu-id="a9d1a-146">The statements between `Using` and `End Using` represent the usage of the resources.</span></span>  
  
- <span data-ttu-id="a9d1a-147">La *suppression* consiste à <xref:System.IDisposable.Dispose%2A> appeler la méthode sur l' `resourcename`objet dans.</span><span class="sxs-lookup"><span data-stu-id="a9d1a-147">*Disposal* means calling the <xref:System.IDisposable.Dispose%2A> method on the object in `resourcename`.</span></span> <span data-ttu-id="a9d1a-148">Cela permet à l’objet de terminer correctement ses ressources.</span><span class="sxs-lookup"><span data-stu-id="a9d1a-148">This allows the object to cleanly terminate its resources.</span></span> <span data-ttu-id="a9d1a-149">L' `End Using` instruction supprime les ressources sous le `Using` contrôle du bloc.</span><span class="sxs-lookup"><span data-stu-id="a9d1a-149">The `End Using` statement disposes of the resources under the `Using` block's control.</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="a9d1a-150">Comportement</span><span class="sxs-lookup"><span data-stu-id="a9d1a-150">Behavior</span></span>  
 <span data-ttu-id="a9d1a-151">Un `Using` bloc se comporte comme un `Try`... construction dans laquelle le `Try` bloc utilise les ressources et le `Finally` bloc les supprime. `Finally`</span><span class="sxs-lookup"><span data-stu-id="a9d1a-151">A `Using` block behaves like a `Try`...`Finally` construction in which the `Try` block uses the resources and the `Finally` block disposes of them.</span></span> <span data-ttu-id="a9d1a-152">Pour cette raison, le `Using` bloc garantit la suppression des ressources, quel que soit le mode de sortie du bloc.</span><span class="sxs-lookup"><span data-stu-id="a9d1a-152">Because of this, the `Using` block guarantees disposal of the resources, no matter how you exit the block.</span></span> <span data-ttu-id="a9d1a-153">Cela est vrai même dans le cas d’une exception non gérée, à l’exception <xref:System.StackOverflowException>de.</span><span class="sxs-lookup"><span data-stu-id="a9d1a-153">This is true even in the case of an unhandled exception, except for a <xref:System.StackOverflowException>.</span></span>  
  
 <span data-ttu-id="a9d1a-154">La portée de chaque variable de ressource acquise `Using` par l’instruction est limitée `Using` au bloc.</span><span class="sxs-lookup"><span data-stu-id="a9d1a-154">The scope of every resource variable acquired by the `Using` statement is limited to the `Using` block.</span></span>  
  
 <span data-ttu-id="a9d1a-155">Si vous spécifiez plusieurs ressources système dans l’instruction `Using` , l’effet est le même que si vous `Using` imbriquez des blocs l’un dans l’autre.</span><span class="sxs-lookup"><span data-stu-id="a9d1a-155">If you specify more than one system resource in the `Using` statement, the effect is the same as if you nested `Using` blocks one within another.</span></span>  
  
 <span data-ttu-id="a9d1a-156">Si `resourcename` a `Nothing`la valeur, aucun <xref:System.IDisposable.Dispose%2A> appel à n’est effectué et aucune exception n’est levée.</span><span class="sxs-lookup"><span data-stu-id="a9d1a-156">If `resourcename` is `Nothing`, no call to <xref:System.IDisposable.Dispose%2A> is made, and no exception is thrown.</span></span>  
  
## <a name="structured-exception-handling-within-a-using-block"></a><span data-ttu-id="a9d1a-157">Gestion structurée des exceptions dans un bloc using</span><span class="sxs-lookup"><span data-stu-id="a9d1a-157">Structured Exception Handling Within a Using Block</span></span>  
 <span data-ttu-id="a9d1a-158">Si vous devez gérer une exception qui peut se produire dans le `Using` bloc, vous pouvez ajouter une opération `Try`... `Finally` .</span><span class="sxs-lookup"><span data-stu-id="a9d1a-158">If you need to handle an exception that might occur within the `Using` block, you can add a complete `Try`...`Finally` construction to it.</span></span> <span data-ttu-id="a9d1a-159">Si vous devez gérer le cas où l' `Using` instruction ne parvient pas à acquérir une ressource, vous pouvez effectuer un test pour voir si `Nothing` `resourcename` est.</span><span class="sxs-lookup"><span data-stu-id="a9d1a-159">If you need to handle the case where the `Using` statement is not successful in acquiring a resource, you can test to see if `resourcename` is `Nothing`.</span></span>  
  
## <a name="structured-exception-handling-instead-of-a-using-block"></a><span data-ttu-id="a9d1a-160">Gestion structurée des exceptions à la place d’un bloc using</span><span class="sxs-lookup"><span data-stu-id="a9d1a-160">Structured Exception Handling Instead of a Using Block</span></span>  
 <span data-ttu-id="a9d1a-161">Si vous avez besoin d’un `Finally` `Try`contrôle plus fin sur l’acquisition des ressources ou si vous avez besoin de code supplémentaire dans le bloc, `Using` vous pouvez réécrire le bloc en tant que... `Finally` construction.</span><span class="sxs-lookup"><span data-stu-id="a9d1a-161">If you need finer control over the acquisition of the resources, or you need additional code in the `Finally` block, you can rewrite the `Using` block as a `Try`...`Finally` construction.</span></span> <span data-ttu-id="a9d1a-162">L’exemple suivant montre le `Try` squelette `Using` et les constructions qui sont équivalents dans l’acquisition et `resource`la suppression de.</span><span class="sxs-lookup"><span data-stu-id="a9d1a-162">The following example shows skeleton `Try` and `Using` constructions that are equivalent in the acquisition and disposal of `resource`.</span></span>  
  
```vb  
Using resource As New resourceType   
    ' Insert code to work with resource.  
End Using  
  
' For the acquisition and disposal of resource, the following  
' Try construction is equivalent to the Using block.  
Dim resource As New resourceType  
Try   
    ' Insert code to work with resource.  
Finally   
    If resource IsNot Nothing Then  
        resource.Dispose()   
    End If  
End Try   
```  
  
> [!NOTE]
> <span data-ttu-id="a9d1a-163">Le code à l' `Using` intérieur du bloc ne doit pas assigner l’objet dans `resourcename` à une autre variable.</span><span class="sxs-lookup"><span data-stu-id="a9d1a-163">The code inside the `Using` block should not assign the object in `resourcename` to another variable.</span></span> <span data-ttu-id="a9d1a-164">Lorsque vous quittez `Using` le bloc, la ressource est supprimée et l’autre variable ne peut pas accéder à la ressource vers laquelle elle pointe.</span><span class="sxs-lookup"><span data-stu-id="a9d1a-164">When you exit the `Using` block, the resource is disposed, and the other variable cannot access the resource to which it points.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a9d1a-165">Exemple</span><span class="sxs-lookup"><span data-stu-id="a9d1a-165">Example</span></span>  
 <span data-ttu-id="a9d1a-166">L’exemple suivant crée un fichier nommé log. txt et écrit deux lignes de texte dans le fichier.</span><span class="sxs-lookup"><span data-stu-id="a9d1a-166">The following example creates a file that is named log.txt and writes two lines of text to the file.</span></span> <span data-ttu-id="a9d1a-167">L’exemple lit également le même fichier et affiche les lignes de texte.</span><span class="sxs-lookup"><span data-stu-id="a9d1a-167">The example also reads that same file and displays the lines of text.</span></span>  
  
 <span data-ttu-id="a9d1a-168">Étant donné <xref:System.IO.TextWriter> que <xref:System.IO.TextReader> les classes et <xref:System.IDisposable> implémentent l’interface, le `Using` code peut utiliser des instructions pour s’assurer que le fichier est fermé correctement après les opérations d’écriture et de lecture.</span><span class="sxs-lookup"><span data-stu-id="a9d1a-168">Because the <xref:System.IO.TextWriter> and <xref:System.IO.TextReader> classes implement the <xref:System.IDisposable> interface, the code can use `Using` statements to ensure that the file is correctly closed after the write and read operations.</span></span>  
  
 [!code-vb[VbVbalrStatements#50](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#50)]  
  
## <a name="see-also"></a><span data-ttu-id="a9d1a-169">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a9d1a-169">See also</span></span>

- <xref:System.IDisposable>
- [<span data-ttu-id="a9d1a-170">Try...Catch...Finally (instruction)</span><span class="sxs-lookup"><span data-stu-id="a9d1a-170">Try...Catch...Finally Statement</span></span>](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
- [<span data-ttu-id="a9d1a-171">Guide pratique pour Supprimer une ressource système</span><span class="sxs-lookup"><span data-stu-id="a9d1a-171">How to: Dispose of a System Resource</span></span>](../../../visual-basic/programming-guide/language-features/control-flow/how-to-dispose-of-a-system-resource.md)
