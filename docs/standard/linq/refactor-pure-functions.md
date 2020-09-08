---
title: Refactoriser dans des fonctions pures-LINQ to XML
description: Découvrez les fonctions pures et comment les utiliser pour Refactoriser le code.
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 2944a0d4-fd33-4e2e-badd-abb0f9be2fcc
ms.openlocfilehash: 18418a1fc39bee9f08cbe92d42c842e3fc9e148a
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89553773"
---
# <a name="refactor-into-pure-functions-linq-to-xml"></a><span data-ttu-id="3070c-103">Refactoriser dans des fonctions pures (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="3070c-103">Refactor into pure functions (LINQ to XML)</span></span>

<span data-ttu-id="3070c-104">L'un des aspects importants des transformations fonctionnelles pures consiste à apprendre à refactoriser le code à l'aide de fonctions pures.</span><span class="sxs-lookup"><span data-stu-id="3070c-104">An important aspect of pure functional transformations is learning how to refactor code using pure functions.</span></span>

> [!NOTE]
> <span data-ttu-id="3070c-105">La nomenclature courante dans la programmation fonctionnelle consiste à refactoriser les programmes à l'aide de fonctions pures.</span><span class="sxs-lookup"><span data-stu-id="3070c-105">The common nomenclature in functional programming is that you refactor programs using pure functions.</span></span> <span data-ttu-id="3070c-106">En Visual Basic et C++, cela correspond à l'utilisation des fonctions dans les langages respectifs.</span><span class="sxs-lookup"><span data-stu-id="3070c-106">In Visual Basic and C++, this aligns with the use of functions in the respective languages.</span></span> <span data-ttu-id="3070c-107">Toutefois, en C#, les fonctions portent le nom de méthodes.</span><span class="sxs-lookup"><span data-stu-id="3070c-107">However, in C#, functions are called methods.</span></span> <span data-ttu-id="3070c-108">Pour les besoins de cette discussion, une fonction pure est implémentée en tant que méthode en C#.</span><span class="sxs-lookup"><span data-stu-id="3070c-108">For the purposes of this discussion, a pure function is implemented as a method in C#.</span></span>

<span data-ttu-id="3070c-109">Comme mentionné précédemment dans cette section, une fonction pure présente deux caractéristiques utiles :</span><span class="sxs-lookup"><span data-stu-id="3070c-109">As noted previously in this section, a pure function has two useful characteristics:</span></span>

- <span data-ttu-id="3070c-110">Elle n'a aucun effet secondaire.</span><span class="sxs-lookup"><span data-stu-id="3070c-110">It has no side effects.</span></span> <span data-ttu-id="3070c-111">La fonction ne modifie pas les variables ou les données de tout type en dehors de la fonction.</span><span class="sxs-lookup"><span data-stu-id="3070c-111">The function doesn't change any variables or the data of any type outside of the function.</span></span>
- <span data-ttu-id="3070c-112">Elle est cohérente.</span><span class="sxs-lookup"><span data-stu-id="3070c-112">It's consistent.</span></span> <span data-ttu-id="3070c-113">Étant donné le même ensemble de données d'entrée, elle retournera toujours la même valeur de sortie.</span><span class="sxs-lookup"><span data-stu-id="3070c-113">Given the same set of input data, it will always return the same output value.</span></span>

<span data-ttu-id="3070c-114">L'une des manières de basculer vers la programmation fonctionnelle consiste à refactoriser le code existant afin d'éliminer les effets secondaires indésirables et les dépendances externes.</span><span class="sxs-lookup"><span data-stu-id="3070c-114">One way of transitioning to functional programming is to refactor existing code to eliminate unnecessary side effects and external dependencies.</span></span> <span data-ttu-id="3070c-115">De cette manière, vous pouvez créer des versions avec fonctions pures du code existant.</span><span class="sxs-lookup"><span data-stu-id="3070c-115">In this way, you can create pure function versions of existing code.</span></span>

<span data-ttu-id="3070c-116">Cet article explique ce qu’est une fonction pure et ce qu’elle ne fait pas.</span><span class="sxs-lookup"><span data-stu-id="3070c-116">This article discusses what a pure function is and what it's not.</span></span> <span data-ttu-id="3070c-117">Le didacticiel [Didacticiel : manipuler du contenu dans un document WordprocessingML](xml-shape-wordprocessingml-documents.md) montre comment manipuler un document WordprocessingML et propose deux exemples de refactorisation à l’aide d’une fonction pure.</span><span class="sxs-lookup"><span data-stu-id="3070c-117">The [Tutorial: Manipulate content in a WordprocessingML document](xml-shape-wordprocessingml-documents.md) tutorial shows how to manipulate a WordprocessingML document, and includes two examples of how to refactor using a pure function.</span></span>

<span data-ttu-id="3070c-118">Les exemples suivants comparent deux fonctions non pures et une fonction pure.</span><span class="sxs-lookup"><span data-stu-id="3070c-118">The following examples contrast two non-pure functions and a pure function.</span></span>

## <a name="example-implement-a-non-pure-function-that-changes-a-static-class-member"></a><span data-ttu-id="3070c-119">Exemple : implémenter une fonction non pure qui modifie un membre de classe statique</span><span class="sxs-lookup"><span data-stu-id="3070c-119">Example: Implement a non-pure function that changes a static class member</span></span>

<span data-ttu-id="3070c-120">Dans le code suivant, la `HyphenatedConcat` fonction n’est pas une fonction pure, car elle modifie le `aMember` membre de classe statique :</span><span class="sxs-lookup"><span data-stu-id="3070c-120">In the following code, the `HyphenatedConcat` function isn't a pure function, because it modifies the `aMember` static class member:</span></span>

```csharp
public class Program
{
    private static string aMember = "StringOne";

    public static void HyphenatedConcat(string appendStr)
    {
        aMember += '-' + appendStr;
    }

    public static void Main()
    {
        HyphenatedConcat("StringTwo");
        Console.WriteLine(aMember);
    }
}
```

```vb
Module Module1
    Dim aMember As String = "StringOne"

    Public Sub HyphenatedConcat(ByVal appendStr As String)
        aMember = aMember & "-" & appendStr
    End Sub

    Sub Main()
        HyphenatedConcat("StringTwo")
        Console.WriteLine(aMember)
    End Sub
End Module
```

<span data-ttu-id="3070c-121">Cet exemple produit la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="3070c-121">This example produces the following output:</span></span>

```output
StringOne-StringTwo
```

<span data-ttu-id="3070c-122">Notez qu’il est inutile de savoir si les données modifiées `public` ont `private` un accès à ou un membre, un membre ou un membre d' `static` `shared` instance.</span><span class="sxs-lookup"><span data-stu-id="3070c-122">Note that it's irrelevant whether the data being modified has `public` or `private` access, or is a `static` member, `shared` member, or instance member.</span></span> <span data-ttu-id="3070c-123">Une fonction pure ne change aucune donnée en dehors de la fonction.</span><span class="sxs-lookup"><span data-stu-id="3070c-123">A pure function doesn't change any data outside of the function.</span></span>

## <a name="example-implement-a-non-pure-function-that-changes-a-parameter"></a><span data-ttu-id="3070c-124">Exemple : implémenter une fonction non pure qui modifie un paramètre</span><span class="sxs-lookup"><span data-stu-id="3070c-124">Example: Implement a non-pure function that changes a parameter</span></span>

<span data-ttu-id="3070c-125">En outre, la version suivante de cette même fonction n’est pas pure car elle modifie le contenu de son paramètre, `sb` .</span><span class="sxs-lookup"><span data-stu-id="3070c-125">Furthermore, the following version of this same function isn't pure because it modifies the contents of its parameter, `sb`.</span></span>

```csharp
public class Program
{
    public static void HyphenatedConcat(StringBuilder sb, String appendStr)
    {
        sb.Append('-' + appendStr);
    }

    public static void Main()
    {
        StringBuilder sb1 = new StringBuilder("StringOne");
        HyphenatedConcat(sb1, "StringTwo");
        Console.WriteLine(sb1);
    }
}
```

```vb
Module Module1
    Public Sub HyphenatedConcat(ByVal sb As StringBuilder, ByVal appendStr As String)
        sb.Append("-" & appendStr)
    End Sub

    Sub Main()
        Dim sb1 As StringBuilder = New StringBuilder("StringOne")
        HyphenatedConcat(sb1, "StringTwo")
        Console.WriteLine(sb1)
    End Sub
End Module
```

<span data-ttu-id="3070c-126">Cette version du programme génère la même sortie que la première version, car la fonction `HyphenatedConcat` a modifié la valeur (l'état) de son premier paramètre en appelant la fonction membre <xref:System.Text.StringBuilder.Append%2A>.</span><span class="sxs-lookup"><span data-stu-id="3070c-126">This version of the program produces the same output as the first version, because the `HyphenatedConcat` function has changed the value (state) of its first parameter by invoking the <xref:System.Text.StringBuilder.Append%2A> member function.</span></span> <span data-ttu-id="3070c-127">Notez que cette modification se produit en dépit du fait que `HyphenatedConcat` utilise le passage de paramètre appel par valeur.</span><span class="sxs-lookup"><span data-stu-id="3070c-127">Note that this alteration occurs despite the fact that `HyphenatedConcat` uses call-by-value parameter passing.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="3070c-128">Pour les types de référence, si vous passez un paramètre par valeur, une copie de la référence à un objet est passée.</span><span class="sxs-lookup"><span data-stu-id="3070c-128">For reference types, if you pass a parameter by value, it results in a copy of the reference to an object being passed.</span></span> <span data-ttu-id="3070c-129">Cette copie est toujours associée aux mêmes données d'instance que la référence d'origine (jusqu'à ce que la variable de référence soit assignée à un nouvel objet).</span><span class="sxs-lookup"><span data-stu-id="3070c-129">This copy is still associated with the same instance data as the original reference (until the reference variable is assigned to a new object).</span></span> <span data-ttu-id="3070c-130">L’appel par référence n’est pas nécessairement requis pour qu’une fonction modifie un paramètre.</span><span class="sxs-lookup"><span data-stu-id="3070c-130">Call-by-reference isn't necessarily required for a function to modify a parameter.</span></span>

## <a name="example-implement-a-pure-function"></a><span data-ttu-id="3070c-131">Exemple : implémenter une fonction pure</span><span class="sxs-lookup"><span data-stu-id="3070c-131">Example: Implement a pure function</span></span>

<span data-ttu-id="3070c-132">Cette autre version du programme montre comment implémenter la fonction `HyphenatedConcat` en tant que fonction pure.</span><span class="sxs-lookup"><span data-stu-id="3070c-132">This next version of the program shows how to implement the `HyphenatedConcat` function as a pure function.</span></span>

```csharp
class Program
{
    public static string HyphenatedConcat(string s, string appendStr)
    {
        return (s + '-' + appendStr);
    }

    public static void Main(string[] args)
    {
        string s1 = "StringOne";
        string s2 = HyphenatedConcat(s1, "StringTwo");
        Console.WriteLine(s2);
    }
}
```

```vb
Module Module1
    Public Function HyphenatedConcat(ByVal s As String, ByVal appendStr As String) As String
        Return (s & "-" & appendStr)
    End Function

    Sub Main()
        Dim s1 As String = "StringOne"
        Dim s2 As String = HyphenatedConcat(s1, "StringTwo")
        Console.WriteLine(s2)
    End Sub
End Module
```

<span data-ttu-id="3070c-133">Là encore, cette version génère la même ligne de sortie : `StringOne-StringTwo`.</span><span class="sxs-lookup"><span data-stu-id="3070c-133">Again, this version produces the same line of output: `StringOne-StringTwo`.</span></span> <span data-ttu-id="3070c-134">Notez que pour conserver la valeur concaténée, elle est stockée dans la variable intermédiaire `s2` .</span><span class="sxs-lookup"><span data-stu-id="3070c-134">Note that to retain the concatenated value, it's stored in the intermediate variable `s2`.</span></span>

<span data-ttu-id="3070c-135">L'une des approches qui peuvent se révéler très utiles consiste à écrire des fonctions localement impures (à savoir, qui déclarent et modifient des variables locales) mais globalement pures.</span><span class="sxs-lookup"><span data-stu-id="3070c-135">One approach that can be very useful is to write functions that are locally impure (that is, they declare and modify local variables) but are globally pure.</span></span> <span data-ttu-id="3070c-136">Ces fonctions possèdent une grande partie des caractéristiques de composabilité requises, mais elles évitent certaines des tâches de programmation fonctionnelle plus compliquées, telles que l'utilisation de la récursivité lorsqu'une simple boucle génèrerait le même résultat.</span><span class="sxs-lookup"><span data-stu-id="3070c-136">Such functions have many of the desirable composability characteristics, but avoid some of the more convoluted functional programming idioms, such as having to use recursion when a simple loop would accomplish the same thing.</span></span>

## <a name="standard-query-operators"></a><span data-ttu-id="3070c-137">Opérateurs de requête standard</span><span class="sxs-lookup"><span data-stu-id="3070c-137">Standard query operators</span></span>

<span data-ttu-id="3070c-138">L’une des caractéristiques importantes des opérateurs de requête standard est qu’ils sont implémentés en tant que fonctions pures.</span><span class="sxs-lookup"><span data-stu-id="3070c-138">An important characteristic of the standard query operators is that they're implemented as pure functions.</span></span>

<span data-ttu-id="3070c-139">Pour plus d’informations, consultez [vue d’ensemble des opérateurs de requête standard (C#)](../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md) et [vue d’ensemble des opérateurs de requête standard (Visual Basic)](../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md).</span><span class="sxs-lookup"><span data-stu-id="3070c-139">For more information, see [Standard Query Operators Overview (C#)](../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md) and [Standard Query Operators Overview (Visual Basic)](../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="3070c-140">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3070c-140">See also</span></span>

- [<span data-ttu-id="3070c-141">Présentation des transformations fonctionnelles pures</span><span class="sxs-lookup"><span data-stu-id="3070c-141">Introduction to pure functional transformations</span></span>](introduction-pure-functional-transformations.md)
- [<span data-ttu-id="3070c-142">Programmation fonctionnelle et programmation impérative</span><span class="sxs-lookup"><span data-stu-id="3070c-142">Functional programming vs. imperative programming</span></span>](functional-vs-imperative-programming.md)
