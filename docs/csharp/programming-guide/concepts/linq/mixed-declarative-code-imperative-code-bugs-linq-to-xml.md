---
title: Bogues liés à l’utilisation combinée de code déclaratif et de code impératif (LINQ to XML) (C#)
description: Les méthodes de LINQ to XML peuvent modifier une arborescence XML directement. L’itération au sein de l’un des axes lors de la modification de l’arborescence XML peut entraîner des bogues impairs.
ms.date: 07/20/2015
ms.assetid: fada62d0-0680-4e73-945a-2b00d7a507af
ms.openlocfilehash: 4eaed10f0a2e64abeb7725dcd70816d75d8a0423
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87165291"
---
# <a name="mixed-declarative-codeimperative-code-bugs-linq-to-xml-c"></a><span data-ttu-id="1ab55-104">Bogues mixtes code déclaratif/code impératif (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="1ab55-104">Mixed Declarative Code/Imperative Code Bugs (LINQ to XML) (C#)</span></span>
[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <span data-ttu-id="1ab55-105">contient diverses méthodes qui vous permettent de modifier directement une arborescence XML.</span><span class="sxs-lookup"><span data-stu-id="1ab55-105">contains various methods that allow you to modify an XML tree directly.</span></span> <span data-ttu-id="1ab55-106">Vous pouvez ajouter des éléments, supprimer des éléments, modifier le contenu d'un élément, ajouter des attributs, et ainsi de suite.</span><span class="sxs-lookup"><span data-stu-id="1ab55-106">You can add elements, delete elements, change the contents of an element, add attributes, and so on.</span></span> <span data-ttu-id="1ab55-107">Cette interface de programmation est décrite dans [Modification d’arborescences XML (LINQ to XML) (C#)](./in-memory-xml-tree-modification-vs-functional-construction-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="1ab55-107">This programming interface is described in [Modifying XML Trees (LINQ to XML) (C#)](./in-memory-xml-tree-modification-vs-functional-construction-linq-to-xml.md).</span></span> <span data-ttu-id="1ab55-108">Si vous itérez au sein de l'un des axes, tels que <xref:System.Xml.Linq.XContainer.Elements%2A>, et que vous modifiez l'arborescence XML à mesure que vous parcourez l'axe, vous pouvez constater des bogues étranges.</span><span class="sxs-lookup"><span data-stu-id="1ab55-108">If you are iterating through one of the axes, such as <xref:System.Xml.Linq.XContainer.Elements%2A>, and you are modifying the XML tree as you iterate through the axis, you can end up with some strange bugs.</span></span>  
  
 <span data-ttu-id="1ab55-109">Ce problème porte parfois le nom de « problème Halloween ».</span><span class="sxs-lookup"><span data-stu-id="1ab55-109">This problem is sometimes known as "The Halloween Problem".</span></span>  
  
## <a name="definition-of-the-problem"></a><span data-ttu-id="1ab55-110">Définition du problème</span><span class="sxs-lookup"><span data-stu-id="1ab55-110">Definition of the Problem</span></span>  
 <span data-ttu-id="1ab55-111">Lorsque vous écrivez du code qui itère au sein d’une collection avec LINQ, vous écrivez du code dans un style déclaratif.</span><span class="sxs-lookup"><span data-stu-id="1ab55-111">When you write some code using LINQ that iterates through a collection, you are writing code in a declarative style.</span></span> <span data-ttu-id="1ab55-112">Cela correspond davantage à décrire *ce que* vous voulez obtenir, plutôt que *comment* vous voulez l’obtenir.</span><span class="sxs-lookup"><span data-stu-id="1ab55-112">It is more akin to describing *what* you want, rather that *how* you want to get it done.</span></span> <span data-ttu-id="1ab55-113">Si vous écrivez du code qui 1) obtient le premier élément, 2) le teste pour une certaine condition, 3) le modifie et 4) le replace dans la liste, il s'agit de code impératif.</span><span class="sxs-lookup"><span data-stu-id="1ab55-113">If you write code that 1) gets the first element, 2) tests it for some condition, 3) modifies it, and 4) puts it back into the list, then this would be imperative code.</span></span> <span data-ttu-id="1ab55-114">Vous indiquez à l’ordinateur *comment* faire ce que vous voulez faire.</span><span class="sxs-lookup"><span data-stu-id="1ab55-114">You are telling the computer *how* to do what you want done.</span></span>  
  
 <span data-ttu-id="1ab55-115">Le mélange de ces styles de code dans la même opération entraîne des problèmes.</span><span class="sxs-lookup"><span data-stu-id="1ab55-115">Mixing these styles of code in the same operation is what leads to problems.</span></span> <span data-ttu-id="1ab55-116">Tenez compte des éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="1ab55-116">Consider the following:</span></span>  
  
 <span data-ttu-id="1ab55-117">Supposez que vous avez une liste liée avec trois éléments (a, b et c) :</span><span class="sxs-lookup"><span data-stu-id="1ab55-117">Suppose you have a linked list with three items in it (a, b, and c):</span></span>  
  
 `a -> b -> c`  
  
 <span data-ttu-id="1ab55-118">Maintenant, supposez que vous souhaitez vous déplacer dans la liste liée et ajouter trois nouveaux éléments (a', b' et c').</span><span class="sxs-lookup"><span data-stu-id="1ab55-118">Now, suppose that you want to move through the linked list, adding three new items (a', b', and c').</span></span> <span data-ttu-id="1ab55-119">Vous souhaitez que la liste liée résultante ressemble à ceci :</span><span class="sxs-lookup"><span data-stu-id="1ab55-119">You want the resulting linked list to look like this:</span></span>  
  
 `a -> a' -> b -> b' -> c -> c'`  
  
 <span data-ttu-id="1ab55-120">Vous écrivez donc du code qui itère au sein de la liste et, pour chaque élément, ajoute un nouvel élément juste après.</span><span class="sxs-lookup"><span data-stu-id="1ab55-120">So you write code that iterates through the list, and for every item, adds a new item right after it.</span></span> <span data-ttu-id="1ab55-121">Votre code verra d'abord l'élément `a` et insérera `a'` après lui.</span><span class="sxs-lookup"><span data-stu-id="1ab55-121">What happens is that your code will first see the `a` element, and insert `a'` after it.</span></span> <span data-ttu-id="1ab55-122">Ensuite, votre code passera au nœud suivant dans la liste, qui sera alors `a'` !</span><span class="sxs-lookup"><span data-stu-id="1ab55-122">Now, your code will move to the next node in the list, which is now `a'`!</span></span> <span data-ttu-id="1ab55-123">Il ajoutera joyeusement un nouvel élément à la liste, `a''`.</span><span class="sxs-lookup"><span data-stu-id="1ab55-123">It happily adds a new item to the list, `a''`.</span></span>  
  
 <span data-ttu-id="1ab55-124">Comment résoudre ce problème dans le monde réel ?</span><span class="sxs-lookup"><span data-stu-id="1ab55-124">How would you solve this in the real world?</span></span> <span data-ttu-id="1ab55-125">Et bien, vous pourriez effectuer une copie de la liste liée d'origine et créer une toute nouvelle liste.</span><span class="sxs-lookup"><span data-stu-id="1ab55-125">Well, you might make a copy of the original linked list, and create a completely new list.</span></span> <span data-ttu-id="1ab55-126">Ou si vous écrivez du code entièrement impératif, vous pourriez rechercher le premier élément, ajouter le nouvel élément, puis avancer de deux pas dans la liste liée, en passant « par-dessus » l'élément que vous venez d'ajouter.</span><span class="sxs-lookup"><span data-stu-id="1ab55-126">Or if you are writing purely imperative code, you might find the first item, add the new item, and then advance twice in the linked list, advancing over the element that you just added.</span></span>  
  
## <a name="adding-while-iterating"></a><span data-ttu-id="1ab55-127">Ajout lors de l'itération</span><span class="sxs-lookup"><span data-stu-id="1ab55-127">Adding While Iterating</span></span>  
 <span data-ttu-id="1ab55-128">Supposez par exemple que vous souhaitez écrire du code qui, pour chaque élément d'une arborescence, crée un élément dupliqué :</span><span class="sxs-lookup"><span data-stu-id="1ab55-128">For example, suppose you want to write some code that for every element in a tree, you want to create a duplicate element:</span></span>  
  
```csharp  
XElement root = new XElement("Root",  
    new XElement("A", "1"),  
    new XElement("B", "2"),  
    new XElement("C", "3")  
);  
foreach (XElement e in root.Elements())  
    root.Add(new XElement(e.Name, (string)e));  
```  
  
 <span data-ttu-id="1ab55-129">Ce code entre dans une boucle infinie.</span><span class="sxs-lookup"><span data-stu-id="1ab55-129">This code goes into an infinite loop.</span></span> <span data-ttu-id="1ab55-130">L'instruction `foreach` itère au sein de l'axe `Elements()` et ajoute de nouveaux éléments à l'élément `doc`.</span><span class="sxs-lookup"><span data-stu-id="1ab55-130">The `foreach` statement iterates through the `Elements()` axis, adding new elements to the `doc` element.</span></span> <span data-ttu-id="1ab55-131">Elle finit par itérer également au sein des éléments qu'elle vient d'ajouter.</span><span class="sxs-lookup"><span data-stu-id="1ab55-131">It ends up iterating also through the elements it just added.</span></span> <span data-ttu-id="1ab55-132">Et puisqu'elle alloue de nouveaux objets à chaque itération de la boucle, elle finira par consommer toute la mémoire disponible.</span><span class="sxs-lookup"><span data-stu-id="1ab55-132">And because it allocates new objects with every iteration of the loop, it will eventually consume all available memory.</span></span>  
  
 <span data-ttu-id="1ab55-133">Vous pouvez résoudre ce problème en extrayant la collection en mémoire à l’aide de l’opérateur de requête standard <xref:System.Linq.Enumerable.ToList%2A>, comme suit :</span><span class="sxs-lookup"><span data-stu-id="1ab55-133">You can fix this problem by pulling the collection into memory using the <xref:System.Linq.Enumerable.ToList%2A> standard query operator, as follows:</span></span>  
  
```csharp  
XElement root = new XElement("Root",  
    new XElement("A", "1"),  
    new XElement("B", "2"),  
    new XElement("C", "3")  
);  
foreach (XElement e in root.Elements().ToList())  
    root.Add(new XElement(e.Name, (string)e));  
Console.WriteLine(root);  
```  
  
 <span data-ttu-id="1ab55-134">À présent, le code fonctionne.</span><span class="sxs-lookup"><span data-stu-id="1ab55-134">Now the code works.</span></span> <span data-ttu-id="1ab55-135">Il en résulte l'arborescence XML suivante :</span><span class="sxs-lookup"><span data-stu-id="1ab55-135">The resulting XML tree is the following:</span></span>  
  
```xml  
<Root>  
  <A>1</A>  
  <B>2</B>  
  <C>3</C>  
  <A>1</A>  
  <B>2</B>  
  <C>3</C>  
</Root>  
```  
  
## <a name="deleting-while-iterating"></a><span data-ttu-id="1ab55-136">Suppression lors de l'itération</span><span class="sxs-lookup"><span data-stu-id="1ab55-136">Deleting While Iterating</span></span>  
 <span data-ttu-id="1ab55-137">Si vous souhaitez supprimer tous les nœuds à un certain niveau, vous pourriez être tenté d'écrire du code ressemblant à celui-ci :</span><span class="sxs-lookup"><span data-stu-id="1ab55-137">If you want to delete all nodes at a certain level, you might be tempted to write code like the following:</span></span>  
  
```csharp  
XElement root = new XElement("Root",  
    new XElement("A", "1"),  
    new XElement("B", "2"),  
    new XElement("C", "3")  
);  
foreach (XElement e in root.Elements())  
    e.Remove();  
Console.WriteLine(root);  
```  
  
 <span data-ttu-id="1ab55-138">Toutefois, ce code ne fait pas ce que vous voulez.</span><span class="sxs-lookup"><span data-stu-id="1ab55-138">However, this does not do what you want.</span></span> <span data-ttu-id="1ab55-139">Dans cette situation, après que vous avez supprimé le premier élément, A, il est supprimé de l'arborescence XML contenue dans la racine et le code dans la méthode Elements qui effectue l'itération ne peut trouver l'élément suivant.</span><span class="sxs-lookup"><span data-stu-id="1ab55-139">In this situation, after you have removed the first element, A, it is removed from the XML tree contained in root, and the code in the Elements method that is doing the iterating cannot find the next element.</span></span>  
  
 <span data-ttu-id="1ab55-140">Le code ci-dessus génère la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="1ab55-140">The preceding code produces the following output:</span></span>  
  
```xml  
<Root>  
  <B>2</B>  
  <C>3</C>  
</Root>  
```  
  
 <span data-ttu-id="1ab55-141">La solution consiste à nouveau à appeler <xref:System.Linq.Enumerable.ToList%2A> afin de matérialiser la collection, comme suit :</span><span class="sxs-lookup"><span data-stu-id="1ab55-141">The solution again is to call <xref:System.Linq.Enumerable.ToList%2A> to materialize the collection, as follows:</span></span>  
  
```csharp  
XElement root = new XElement("Root",  
    new XElement("A", "1"),  
    new XElement("B", "2"),  
    new XElement("C", "3")  
);  
foreach (XElement e in root.Elements().ToList())  
    e.Remove();  
Console.WriteLine(root);  
```  
  
 <span data-ttu-id="1ab55-142">Ce code produit la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="1ab55-142">This produces the following output:</span></span>  
  
```xml  
<Root />  
```  
  
 <span data-ttu-id="1ab55-143">En guise d'alternative, vous pouvez éliminer l'itération en appelant <xref:System.Xml.Linq.XElement.RemoveAll%2A> sur l'élément parent :</span><span class="sxs-lookup"><span data-stu-id="1ab55-143">Alternatively, you can eliminate the iteration altogether by calling <xref:System.Xml.Linq.XElement.RemoveAll%2A> on the parent element:</span></span>  
  
```csharp  
XElement root = new XElement("Root",  
    new XElement("A", "1"),  
    new XElement("B", "2"),  
    new XElement("C", "3")  
);  
root.RemoveAll();  
Console.WriteLine(root);  
```  
  
## <a name="why-cant-linq-automatically-handle-this"></a><span data-ttu-id="1ab55-144">Pourquoi LINQ ne peut-il gérer cela automatiquement ?</span><span class="sxs-lookup"><span data-stu-id="1ab55-144">Why Can't LINQ Automatically Handle This?</span></span>  
 <span data-ttu-id="1ab55-145">Une approche consisterait à toujours tout placer en mémoire au lieu d'effectuer une évaluation différée.</span><span class="sxs-lookup"><span data-stu-id="1ab55-145">One approach would be to always bring everything into memory instead of doing lazy evaluation.</span></span> <span data-ttu-id="1ab55-146">Toutefois, cela serait très coûteux en termes de performances et d'utilisation de la mémoire.</span><span class="sxs-lookup"><span data-stu-id="1ab55-146">However, it would be very expensive in terms of performance and memory use.</span></span> <span data-ttu-id="1ab55-147">En fait, si LINQ (et LINQ to XML) devait suivre cette approche, cela échouerait dans les situations de monde réel.</span><span class="sxs-lookup"><span data-stu-id="1ab55-147">In fact, if LINQ and (LINQ to XML) were to take this approach, it would fail in real-world situations.</span></span>  
  
 <span data-ttu-id="1ab55-148">Une autre approche possible consisterait à placer une certaine syntaxe de transaction dans LINQ et à faire en sorte que le compilateur tente d'analyser le code et de déterminer si une collection spécifique nécessite une matérialisation.</span><span class="sxs-lookup"><span data-stu-id="1ab55-148">Another possible approach would be to put in some sort of transaction syntax into LINQ, and have the compiler attempt to analyze the code and determine if any particular collection needed to be materialized.</span></span> <span data-ttu-id="1ab55-149">Toutefois, tenter de déterminer tout le code qui a des effets secondaires est une tâche incroyablement complexe.</span><span class="sxs-lookup"><span data-stu-id="1ab55-149">However, attempting to determine all code that has side-effects is incredibly complex.</span></span> <span data-ttu-id="1ab55-150">Considérez le code suivant :</span><span class="sxs-lookup"><span data-stu-id="1ab55-150">Consider the following code:</span></span>  
  
```csharp  
var z =  
    from e in root.Elements()  
    where TestSomeCondition(e)  
    select DoMyProjection(e);  
```  
  
 <span data-ttu-id="1ab55-151">Un tel code d'analyse devrait analyser les méthodes TestSomeCondition et DoMyProjection, et toutes les méthodes appelées par ces méthodes, pour déterminer si du code a des effets secondaires.</span><span class="sxs-lookup"><span data-stu-id="1ab55-151">Such analysis code would need to analyze the methods TestSomeCondition and DoMyProjection, and all methods that those methods called, to determine if any code had side-effects.</span></span> <span data-ttu-id="1ab55-152">Mais le code d'analyse ne pourrait pas simplement rechercher le code qui aurait des effets secondaires.</span><span class="sxs-lookup"><span data-stu-id="1ab55-152">But the analysis code could not just look for any code that had side-effects.</span></span> <span data-ttu-id="1ab55-153">Il lui faudrait sélectionner uniquement le code ayant des effets secondaires sur les éléments enfants de `root` dans cette situation.</span><span class="sxs-lookup"><span data-stu-id="1ab55-153">It would need to select for just the code that had side-effects on the child elements of `root` in this situation.</span></span>  
  
 <span data-ttu-id="1ab55-154">LINQ to XML ne tente pas d'effectuer une telle analyse.</span><span class="sxs-lookup"><span data-stu-id="1ab55-154">LINQ to XML does not attempt to do any such analysis.</span></span>  
  
 <span data-ttu-id="1ab55-155">Il vous incombe d'éviter ce genre de problèmes.</span><span class="sxs-lookup"><span data-stu-id="1ab55-155">It is up to you to avoid these problems.</span></span>  
  
## <a name="guidance"></a><span data-ttu-id="1ab55-156">Assistance</span><span class="sxs-lookup"><span data-stu-id="1ab55-156">Guidance</span></span>  
 <span data-ttu-id="1ab55-157">En premier lieu, ne mélangez pas de code déclaratif et impératif.</span><span class="sxs-lookup"><span data-stu-id="1ab55-157">First, do not mix declarative and imperative code.</span></span>  
  
 <span data-ttu-id="1ab55-158">Même si vous connaissez exactement la sémantique de vos collections et la sémantique des méthodes qui modifient l'arborescence XML, si vous écrivez du code intelligent qui évite ces catégories de problèmes, votre code devra être maintenu par d'autres développeurs dans le futur et ils n'auront peut-être pas la même vision du problème que vous.</span><span class="sxs-lookup"><span data-stu-id="1ab55-158">Even if you know exactly the semantics of your collections and the semantics of the methods that modify the XML tree, if you write some clever code that avoids these categories of problems, your code will need to be maintained by other developers in the future, and they may not be as clear on the issues.</span></span> <span data-ttu-id="1ab55-159">Si vous combinez des styles de codage déclaratifs et impératifs, votre code sera plus fragile.</span><span class="sxs-lookup"><span data-stu-id="1ab55-159">If you mix declarative and imperative coding styles, your code will be more brittle.</span></span>  
  
 <span data-ttu-id="1ab55-160">Si vous écrivez du code qui matérialise une collection afin d'éviter ces problèmes, ajoutez des commentaires appropriés à votre code de sorte que les programmeurs de maintenance comprennent le problème. </span><span class="sxs-lookup"><span data-stu-id="1ab55-160">If you write code that materializes a collection so that these problems are avoided, note it with comments as appropriate in your code, so that maintenance programmers will understand the issue.</span></span>  
  
 <span data-ttu-id="1ab55-161">En second lieu, si les performances et autres considérations le permettent, utilisez uniquement du code déclaratif.</span><span class="sxs-lookup"><span data-stu-id="1ab55-161">Second, if performance and other considerations allow, use only declarative code.</span></span> <span data-ttu-id="1ab55-162">Ne modifiez pas votre arborescence XML existante.</span><span class="sxs-lookup"><span data-stu-id="1ab55-162">Don't modify your existing XML tree.</span></span> <span data-ttu-id="1ab55-163">Générez-en une nouvelle.</span><span class="sxs-lookup"><span data-stu-id="1ab55-163">Generate a new one.</span></span>  
  
```csharp  
XElement root = new XElement("Root",  
    new XElement("A", "1"),  
    new XElement("B", "2"),  
    new XElement("C", "3")  
);  
XElement newRoot = new XElement("Root",  
    root.Elements(),  
    root.Elements()  
);  
Console.WriteLine(newRoot);  
```  
