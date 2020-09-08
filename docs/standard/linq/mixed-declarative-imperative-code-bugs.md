---
title: Bogues mixtes de code déclaratif/impératif-LINQ to XML
description: Découvrez comment reconnaître et éviter les problèmes qui peuvent se produire lorsque le code itère le long d’un axe en apportant des modifications.
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: fada62d0-0680-4e73-945a-2b00d7a507af
ms.openlocfilehash: 280bb62d15ff28d1fd09ca2d0c52c0a0c36d7282
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89553276"
---
# <a name="mixed-declarativeimperative-code-bugs-linq-to-xml"></a><span data-ttu-id="2f5cd-103">Bogues mixtes de code déclaratif/impératif (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="2f5cd-103">Mixed declarative/imperative code bugs (LINQ to XML)</span></span>

<span data-ttu-id="2f5cd-104">LINQ to XML contient différentes méthodes qui vous permettent de modifier directement une arborescence XML.</span><span class="sxs-lookup"><span data-stu-id="2f5cd-104">LINQ to XML contains various methods that allow you to modify an XML tree directly.</span></span> <span data-ttu-id="2f5cd-105">Vous pouvez ajouter des éléments, supprimer des éléments, modifier le contenu d'un élément, ajouter des attributs, et ainsi de suite.</span><span class="sxs-lookup"><span data-stu-id="2f5cd-105">You can add elements, delete elements, change the contents of an element, add attributes, and so on.</span></span> <span data-ttu-id="2f5cd-106">Cette interface de programmation est décrite dans [modifier des arborescences XML](in-memory-xml-tree-modification-vs-functional-construction.md).</span><span class="sxs-lookup"><span data-stu-id="2f5cd-106">This programming interface is described in [Modify XML trees](in-memory-xml-tree-modification-vs-functional-construction.md).</span></span> <span data-ttu-id="2f5cd-107">Si vous effectuez une itération au sein de l’un des axes, par exemple <xref:System.Xml.Linq.XContainer.Elements%2A> , et que vous modifiez l’arborescence XML à mesure que vous itérez au sein de l’axe, vous pouvez vous retrouver avec des bogues étranges.</span><span class="sxs-lookup"><span data-stu-id="2f5cd-107">If you're iterating through one of the axes, such as <xref:System.Xml.Linq.XContainer.Elements%2A>, and you're modifying the XML tree as you iterate through the axis, you can end up with some strange bugs.</span></span>

<span data-ttu-id="2f5cd-108">Ce problème porte parfois le nom de « problème Halloween ».</span><span class="sxs-lookup"><span data-stu-id="2f5cd-108">This problem is sometimes known as "The Halloween Problem".</span></span>

<span data-ttu-id="2f5cd-109">Lorsque vous écrivez du code à l’aide de LINQ qui itère au sein d’une collection, vous écrivez du code dans un style déclaratif.</span><span class="sxs-lookup"><span data-stu-id="2f5cd-109">When you write some code using LINQ that iterates through a collection, you're writing code in a declarative style.</span></span> <span data-ttu-id="2f5cd-110">C’est plus similaire à décrire *ce* que vous souhaitez, au lieu de *la façon dont* vous souhaitez le faire.</span><span class="sxs-lookup"><span data-stu-id="2f5cd-110">It's more akin to describing *what* you want, rather that *how* you want to get it done.</span></span> <span data-ttu-id="2f5cd-111">Si vous écrivez du code qui 1) obtient le premier élément, 2) le teste pour une certaine condition, 3) le modifie et 4) le replace dans la liste, il s'agit de code impératif.</span><span class="sxs-lookup"><span data-stu-id="2f5cd-111">If you write code that 1) gets the first element, 2) tests it for some condition, 3) modifies it, and 4) puts it back into the list, then this would be imperative code.</span></span> <span data-ttu-id="2f5cd-112">Vous indiquez à l’ordinateur *Comment* faire ce que vous voulez faire.</span><span class="sxs-lookup"><span data-stu-id="2f5cd-112">You're telling the computer *how* to do what you want done.</span></span>

<span data-ttu-id="2f5cd-113">Le mélange de ces styles de code dans la même opération entraîne des problèmes.</span><span class="sxs-lookup"><span data-stu-id="2f5cd-113">Mixing these styles of code in the same operation is what leads to problems.</span></span> <span data-ttu-id="2f5cd-114">Tenez compte des éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="2f5cd-114">Consider the following:</span></span>

<span data-ttu-id="2f5cd-115">Supposez que vous avez une liste liée avec trois éléments (a, b et c) :</span><span class="sxs-lookup"><span data-stu-id="2f5cd-115">Suppose you have a linked list with three items in it (a, b, and c):</span></span>

> <span data-ttu-id="2f5cd-116">a-> b-> c</span><span class="sxs-lookup"><span data-stu-id="2f5cd-116">a -> b -> c</span></span>

<span data-ttu-id="2f5cd-117">Maintenant, supposez que vous souhaitez vous déplacer dans la liste liée et ajouter trois nouveaux éléments (a', b' et c').</span><span class="sxs-lookup"><span data-stu-id="2f5cd-117">Now, suppose that you want to move through the linked list, adding three new items (a', b', and c').</span></span> <span data-ttu-id="2f5cd-118">Vous souhaitez que la liste liée résultante ressemble à ceci :</span><span class="sxs-lookup"><span data-stu-id="2f5cd-118">You want the resulting linked list to look like this:</span></span>

 > <span data-ttu-id="2f5cd-119">a-> a'-> b-> b'-> c-> c'</span><span class="sxs-lookup"><span data-stu-id="2f5cd-119">a -> a' -> b -> b' -> c -> c'</span></span>

<span data-ttu-id="2f5cd-120">Vous écrivez donc du code qui itère au sein de la liste et, pour chaque élément, ajoute un nouvel élément juste après.</span><span class="sxs-lookup"><span data-stu-id="2f5cd-120">So you write code that iterates through the list, and for every item, adds a new item right after it.</span></span> <span data-ttu-id="2f5cd-121">Votre code verra d'abord l'élément `a` et insérera `a'` après lui.</span><span class="sxs-lookup"><span data-stu-id="2f5cd-121">What happens is that your code will first see the `a` element, and insert `a'` after it.</span></span> <span data-ttu-id="2f5cd-122">Maintenant, votre code passera au nœud suivant dans la liste, ce qui signifie `a'` qu’il ajoute un nouvel élément entre a et b à la liste.</span><span class="sxs-lookup"><span data-stu-id="2f5cd-122">Now, your code will move to the next node in the list, which is now `a'`, so it adds a new item between a' and b to the list!</span></span>

<span data-ttu-id="2f5cd-123">Comment pourriez-vous le résoudre ?</span><span class="sxs-lookup"><span data-stu-id="2f5cd-123">How would you solve this?</span></span> <span data-ttu-id="2f5cd-124">Et bien, vous pourriez effectuer une copie de la liste liée d'origine et créer une toute nouvelle liste.</span><span class="sxs-lookup"><span data-stu-id="2f5cd-124">Well, you might make a copy of the original linked list, and create a completely new list.</span></span> <span data-ttu-id="2f5cd-125">Ou, si vous écrivez du code purement impératif, vous pouvez trouver le premier élément, ajouter le nouvel élément, puis avancer deux fois dans la liste liée, en avançant l’élément que vous venez d’ajouter.</span><span class="sxs-lookup"><span data-stu-id="2f5cd-125">Or if you're writing purely imperative code, you might find the first item, add the new item, and then advance twice in the linked list, advancing over the element that you just added.</span></span>

## <a name="example-adding-while-iterating"></a><span data-ttu-id="2f5cd-126">Exemple : ajout en cours d’itération</span><span class="sxs-lookup"><span data-stu-id="2f5cd-126">Example: Adding while iterating</span></span>

<span data-ttu-id="2f5cd-127">Par exemple, supposons que vous souhaitiez écrire du code pour créer un doublon de chaque élément dans une arborescence :</span><span class="sxs-lookup"><span data-stu-id="2f5cd-127">For example, suppose you want to write code to create a duplicate of every element in a tree:</span></span>

```csharp
XElement root = new XElement("Root",
    new XElement("A", "1"),
    new XElement("B", "2"),
    new XElement("C", "3")
);
foreach (XElement e in root.Elements())
    root.Add(new XElement(e.Name, (string)e));
```

```vb
Dim root As XElement = _
    <Root>
        <A>1</A>
        <B>2</B>
        <C>3</C>
    </Root>
For Each e As XElement In root.Elements()
    root.Add(New XElement(e.Name, e.Value))
Next
```

<span data-ttu-id="2f5cd-128">Ce code entre dans une boucle infinie.</span><span class="sxs-lookup"><span data-stu-id="2f5cd-128">This code goes into an infinite loop.</span></span> <span data-ttu-id="2f5cd-129">L'instruction `foreach` itère au sein de l'axe `Elements()` et ajoute de nouveaux éléments à l'élément `doc`.</span><span class="sxs-lookup"><span data-stu-id="2f5cd-129">The `foreach` statement iterates through the `Elements()` axis, adding new elements to the `doc` element.</span></span> <span data-ttu-id="2f5cd-130">Elle finit par itérer également au sein des éléments qu'elle vient d'ajouter.</span><span class="sxs-lookup"><span data-stu-id="2f5cd-130">It ends up iterating also through the elements it just added.</span></span> <span data-ttu-id="2f5cd-131">Et puisqu'elle alloue de nouveaux objets à chaque itération de la boucle, elle finira par consommer toute la mémoire disponible.</span><span class="sxs-lookup"><span data-stu-id="2f5cd-131">And because it allocates new objects with every iteration of the loop, it will eventually consume all available memory.</span></span>

<span data-ttu-id="2f5cd-132">Vous pouvez résoudre ce problème en extrayant la collection en mémoire à l’aide de l’opérateur de requête standard <xref:System.Linq.Enumerable.ToList%2A>, comme suit :</span><span class="sxs-lookup"><span data-stu-id="2f5cd-132">You can fix this problem by pulling the collection into memory using the <xref:System.Linq.Enumerable.ToList%2A> standard query operator, as follows:</span></span>

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

```vb
Dim root As XElement = _
    <Root>
        <A>1</A>
        <B>2</B>
        <C>3</C>
    </Root>
For Each e As XElement In root.Elements().ToList()
    root.Add(New XElement(e.Name, e.Value))
Next
Console.WriteLine(root)
```

<span data-ttu-id="2f5cd-133">À présent, le code fonctionne.</span><span class="sxs-lookup"><span data-stu-id="2f5cd-133">Now the code works.</span></span> <span data-ttu-id="2f5cd-134">Il en résulte l'arborescence XML suivante :</span><span class="sxs-lookup"><span data-stu-id="2f5cd-134">The resulting XML tree is the following:</span></span>

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

## <a name="example-deleting-while-iterating"></a><span data-ttu-id="2f5cd-135">Exemple : suppression lors de l’itération</span><span class="sxs-lookup"><span data-stu-id="2f5cd-135">Example: Deleting while iterating</span></span>

<span data-ttu-id="2f5cd-136">Si vous souhaitez supprimer tous les nœuds à un certain niveau, vous pourriez être tenté d'écrire du code ressemblant à celui-ci :</span><span class="sxs-lookup"><span data-stu-id="2f5cd-136">If you want to delete all nodes at a certain level, you might be tempted to write code like the following:</span></span>

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

```vb
Dim root As XElement = _
    <Root>
        <A>1</A>
        <B>2</B>
        <C>3</C>
    </Root>
For Each e As XElement In root.Elements()
    e.Remove()
Next
Console.WriteLine(root)
```

<span data-ttu-id="2f5cd-137">Toutefois, cela ne fait pas ce que vous voulez.</span><span class="sxs-lookup"><span data-stu-id="2f5cd-137">However, this doesn't do what you want.</span></span> <span data-ttu-id="2f5cd-138">Dans ce cas, une fois que vous avez supprimé le premier élément, A, il est supprimé de l’arborescence XML contenue dans la racine et le code dans la méthode Elements qui effectue l’itération ne peut pas trouver l’élément suivant.</span><span class="sxs-lookup"><span data-stu-id="2f5cd-138">In this situation, after you've removed the first element, A, it's removed from the XML tree contained in root, and the code in the Elements method that does the iterating can't find the next element.</span></span>

<span data-ttu-id="2f5cd-139">Cet exemple produit la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="2f5cd-139">This example produces the following output:</span></span>

```xml
<Root>
  <B>2</B>
  <C>3</C>
</Root>
```

<span data-ttu-id="2f5cd-140">La solution consiste à nouveau à appeler <xref:System.Linq.Enumerable.ToList%2A> afin de matérialiser la collection, comme suit :</span><span class="sxs-lookup"><span data-stu-id="2f5cd-140">The solution again is to call <xref:System.Linq.Enumerable.ToList%2A> to materialize the collection, as follows:</span></span>

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

```vb
Dim root As XElement = _
    <Root>
        <A>1</A>
        <B>2</B>
        <C>3</C>
    </Root>
For Each e As XElement In root.Elements().ToList()
    e.Remove()
Next
Console.WriteLine(root)
```

<span data-ttu-id="2f5cd-141">Cet exemple produit la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="2f5cd-141">This example produces the following output:</span></span>

```xml
<Root />
```

<span data-ttu-id="2f5cd-142">En guise d'alternative, vous pouvez éliminer l'itération en appelant <xref:System.Xml.Linq.XElement.RemoveAll%2A> sur l'élément parent :</span><span class="sxs-lookup"><span data-stu-id="2f5cd-142">Alternatively, you can eliminate the iteration altogether by calling <xref:System.Xml.Linq.XElement.RemoveAll%2A> on the parent element:</span></span>

```csharp
XElement root = new XElement("Root",
    new XElement("A", "1"),
    new XElement("B", "2"),
    new XElement("C", "3")
);
root.RemoveAll();
Console.WriteLine(root);
```

```vb
Dim root As XElement = _
    <Root>
        <A>1</A>
        <B>2</B>
        <C>3</C>
    </Root>
root.RemoveAll()
Console.WriteLine(root)
```

## <a name="example-why-linq-cant-automatically-handle-these-issues"></a><span data-ttu-id="2f5cd-143">Exemple : pourquoi LINQ ne peut pas gérer automatiquement ces problèmes</span><span class="sxs-lookup"><span data-stu-id="2f5cd-143">Example: Why LINQ can't automatically handle these issues</span></span>

<span data-ttu-id="2f5cd-144">Une approche consisterait à toujours tout placer en mémoire au lieu d'effectuer une évaluation différée.</span><span class="sxs-lookup"><span data-stu-id="2f5cd-144">One approach would be to always bring everything into memory instead of doing lazy evaluation.</span></span> <span data-ttu-id="2f5cd-145">Toutefois, cela serait très coûteux en termes de performances et d'utilisation de la mémoire.</span><span class="sxs-lookup"><span data-stu-id="2f5cd-145">However, it would be very expensive in terms of performance and memory use.</span></span> <span data-ttu-id="2f5cd-146">En fait, si LINQ, et LINQ to XML, devaient adopter cette approche, cela échouerait dans les situations réelles.</span><span class="sxs-lookup"><span data-stu-id="2f5cd-146">In fact, if LINQ, and LINQ to XML, were to take this approach, it would fail in real-world situations.</span></span>

<span data-ttu-id="2f5cd-147">Une autre approche possible consisterait à placer une certaine syntaxe de transaction dans LINQ et à faire en sorte que le compilateur tente d’analyser le code pour déterminer si une collection particulière devait être matérialisée.</span><span class="sxs-lookup"><span data-stu-id="2f5cd-147">Another possible approach would be to put some sort of transaction syntax into LINQ, and have the compiler attempt to analyze the code to determine if any particular collection needed to be materialized.</span></span> <span data-ttu-id="2f5cd-148">Toutefois, tenter de déterminer tout le code qui a des effets secondaires est une tâche incroyablement complexe.</span><span class="sxs-lookup"><span data-stu-id="2f5cd-148">However, attempting to determine all code that has side-effects is incredibly complex.</span></span> <span data-ttu-id="2f5cd-149">Considérez le code suivant :</span><span class="sxs-lookup"><span data-stu-id="2f5cd-149">Consider the following code:</span></span>

```csharp
var z =
    from e in root.Elements()
    where TestSomeCondition(e)
    select DoMyProjection(e);
```

```vb
Dim z = _
    From e In root.Elements() _
    Where (TestSomeCondition(e)) _
    Select DoMyProjection(e)
```

<span data-ttu-id="2f5cd-150">Un tel code d'analyse devrait analyser les méthodes TestSomeCondition et DoMyProjection, et toutes les méthodes appelées par ces méthodes, pour déterminer si du code a des effets secondaires.</span><span class="sxs-lookup"><span data-stu-id="2f5cd-150">Such analysis code would need to analyze the methods TestSomeCondition and DoMyProjection, and all methods that those methods called, to determine if any code had side-effects.</span></span> <span data-ttu-id="2f5cd-151">Mais le code d'analyse ne pourrait pas simplement rechercher le code qui aurait des effets secondaires.</span><span class="sxs-lookup"><span data-stu-id="2f5cd-151">But the analysis code could not just look for any code that had side-effects.</span></span> <span data-ttu-id="2f5cd-152">Il lui faudrait sélectionner uniquement le code ayant des effets secondaires sur les éléments enfants de `root` dans cette situation.</span><span class="sxs-lookup"><span data-stu-id="2f5cd-152">It would need to select for just the code that had side-effects on the child elements of `root` in this situation.</span></span>

<span data-ttu-id="2f5cd-153">LINQ to XML n’essaie pas d’effectuer une telle analyse.</span><span class="sxs-lookup"><span data-stu-id="2f5cd-153">LINQ to XML doesn't attempt to do any such analysis.</span></span> <span data-ttu-id="2f5cd-154">C’est à vous d’éviter ces problèmes.</span><span class="sxs-lookup"><span data-stu-id="2f5cd-154">It's up to you to avoid these problems.</span></span>

## <a name="example-use-declarative-code-to-generate-a-new-xml-tree-rather-than-modify-the-existing-tree"></a><span data-ttu-id="2f5cd-155">Exemple : utiliser du code déclaratif pour générer une nouvelle arborescence XML au lieu de modifier l’arborescence existante</span><span class="sxs-lookup"><span data-stu-id="2f5cd-155">Example: Use declarative code to generate a new XML tree rather than modify the existing tree</span></span>

<span data-ttu-id="2f5cd-156">Pour éviter de tels problèmes, ne mélangez pas de code déclaratif et impératif, même si vous connaissez exactement la sémantique de vos collections et la sémantique des méthodes qui modifient l’arborescence XML.</span><span class="sxs-lookup"><span data-stu-id="2f5cd-156">To avoid such problems, don't mix declarative and imperative code, even if you know exactly the semantics of your collections and the semantics of the methods that modify the XML tree.</span></span> <span data-ttu-id="2f5cd-157">Si vous écrivez du code qui évite les problèmes, votre code devra être maintenu par d’autres développeurs à l’avenir, et ils ne seront peut-être pas aussi clairs pour les problèmes.</span><span class="sxs-lookup"><span data-stu-id="2f5cd-157">If you write code that avoids problems, your code will need to be maintained by other developers in the future, and they may not be as clear on the issues.</span></span> <span data-ttu-id="2f5cd-158">Si vous combinez des styles de codage déclaratifs et impératifs, votre code sera plus fragile.</span><span class="sxs-lookup"><span data-stu-id="2f5cd-158">If you mix declarative and imperative coding styles, your code will be more brittle.</span></span>  <span data-ttu-id="2f5cd-159">Si vous écrivez du code qui matérialise une collection afin d'éviter ces problèmes, ajoutez des commentaires appropriés à votre code de sorte que les programmeurs de maintenance comprennent le problème. </span><span class="sxs-lookup"><span data-stu-id="2f5cd-159">If you write code that materializes a collection so that these problems are avoided, note it with comments as appropriate in your code, so that maintenance programmers will understand the issue.</span></span>

<span data-ttu-id="2f5cd-160">Si les performances et autres considérations le permettent, utilisez uniquement du code déclaratif.</span><span class="sxs-lookup"><span data-stu-id="2f5cd-160">If performance and other considerations allow, use only declarative code.</span></span> <span data-ttu-id="2f5cd-161">Ne modifiez pas votre arborescence XML existante.</span><span class="sxs-lookup"><span data-stu-id="2f5cd-161">Don't modify your existing XML tree.</span></span> <span data-ttu-id="2f5cd-162">Au lieu de cela, générez-en un nouveau, comme indiqué dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="2f5cd-162">Instead, generate a new one as shown in the following example:</span></span>

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

```vb
Dim root As XElement = _
    <Root>
        <A>1</A>
        <B>2</B>
        <C>3</C>
    </Root>
Dim newRoot As XElement = New XElement("Root", _
    root.Elements(), root.Elements())
Console.WriteLine(newRoot)
```
