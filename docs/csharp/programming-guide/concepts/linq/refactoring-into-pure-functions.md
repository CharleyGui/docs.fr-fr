---
title: Refactorisation dans des fonctions pures (C#)
ms.date: 07/20/2015
ms.assetid: 2944a0d4-fd33-4e2e-badd-abb0f9be2fcc
ms.openlocfilehash: 4cf91ff078bd1c4582daa05475a91c4a4ecaba3e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "70253113"
---
# <a name="refactoring-into-pure-functions-c"></a><span data-ttu-id="19871-102">Refactorisation dans des fonctions pures (C#)</span><span class="sxs-lookup"><span data-stu-id="19871-102">Refactoring Into Pure Functions (C#)</span></span>

<span data-ttu-id="19871-103">L'un des aspects importants des transformations fonctionnelles pures consiste à apprendre à refactoriser le code à l'aide de fonctions pures.</span><span class="sxs-lookup"><span data-stu-id="19871-103">An important aspect of pure functional transformations is learning how to refactor code using pure functions.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="19871-104">La nomenclature courante dans la programmation fonctionnelle consiste à refactoriser les programmes à l'aide de fonctions pures.</span><span class="sxs-lookup"><span data-stu-id="19871-104">The common nomenclature in functional programming is that you refactor programs using pure functions.</span></span> <span data-ttu-id="19871-105">En Visual Basic et C++, cela correspond à l'utilisation des fonctions dans les langages respectifs.</span><span class="sxs-lookup"><span data-stu-id="19871-105">In Visual Basic and C++, this aligns with the use of functions in the respective languages.</span></span> <span data-ttu-id="19871-106">Toutefois, en C#, les fonctions portent le nom de méthodes.</span><span class="sxs-lookup"><span data-stu-id="19871-106">However, in C#, functions are called methods.</span></span> <span data-ttu-id="19871-107">Pour les besoins de cette discussion, une fonction pure est implémentée en tant que méthode en C#.</span><span class="sxs-lookup"><span data-stu-id="19871-107">For the purposes of this discussion, a pure function is implemented as a method in C#.</span></span>  
  
 <span data-ttu-id="19871-108">Comme mentionné précédemment dans cette section, une fonction pure présente deux caractéristiques utiles :</span><span class="sxs-lookup"><span data-stu-id="19871-108">As noted previously in this section, a pure function has two useful characteristics:</span></span>  
  
- <span data-ttu-id="19871-109">Elle n'a aucun effet secondaire.</span><span class="sxs-lookup"><span data-stu-id="19871-109">It has no side effects.</span></span> <span data-ttu-id="19871-110">La fonction ne change aucune variable et aucune donnée de tout type en dehors de la fonction.</span><span class="sxs-lookup"><span data-stu-id="19871-110">The function does not change any variables or the data of any type outside of the function.</span></span>  
  
- <span data-ttu-id="19871-111">Elle est cohérente.</span><span class="sxs-lookup"><span data-stu-id="19871-111">It is consistent.</span></span> <span data-ttu-id="19871-112">Étant donné le même ensemble de données d'entrée, elle retournera toujours la même valeur de sortie.</span><span class="sxs-lookup"><span data-stu-id="19871-112">Given the same set of input data, it will always return the same output value.</span></span>  
  
 <span data-ttu-id="19871-113">L'une des manières de basculer vers la programmation fonctionnelle consiste à refactoriser le code existant afin d'éliminer les effets secondaires indésirables et les dépendances externes.</span><span class="sxs-lookup"><span data-stu-id="19871-113">One way of transitioning to functional programming is to refactor existing code to eliminate unnecessary side effects and external dependencies.</span></span> <span data-ttu-id="19871-114">De cette manière, vous pouvez créer des versions avec fonctions pures du code existant.</span><span class="sxs-lookup"><span data-stu-id="19871-114">In this way, you can create pure function versions of existing code.</span></span>  
  
 <span data-ttu-id="19871-115">Cette rubrique explique ce qu'est et ce que n'est pas une fonction pure.</span><span class="sxs-lookup"><span data-stu-id="19871-115">This topic discusses what a pure function is and what it is not.</span></span> <span data-ttu-id="19871-116">Le [Didacticiel : manipulation de contenu dans un document WordprocessingML (C#)](./shape-of-wordprocessingml-documents.md) montre comment manipuler un document WordprocessingML et inclut deux exemples illustrant comment refactoriser à l’aide d’une fonction pure.</span><span class="sxs-lookup"><span data-stu-id="19871-116">The [Tutorial: Manipulating Content in a WordprocessingML Document (C#)](./shape-of-wordprocessingml-documents.md) tutorial shows how to manipulate a WordprocessingML document, and includes two examples of how to refactor using a pure function.</span></span>  
  
## <a name="eliminating-side-effects-and-external-dependencies"></a><span data-ttu-id="19871-117">Suppression des effets secondaires et des dépendances externes</span><span class="sxs-lookup"><span data-stu-id="19871-117">Eliminating Side Effects and External Dependencies</span></span>  
 <span data-ttu-id="19871-118">Les exemples suivants comparent deux fonctions non pures et une fonction pure.</span><span class="sxs-lookup"><span data-stu-id="19871-118">The following examples contrast two non-pure functions and a pure function.</span></span>  
  
### <a name="non-pure-function-that-changes-a-class-member"></a><span data-ttu-id="19871-119">Fonction non pure qui modifie un membre de classe</span><span class="sxs-lookup"><span data-stu-id="19871-119">Non-Pure Function that Changes a Class Member</span></span>  
 <span data-ttu-id="19871-120">Dans le code suivant, la fonction `HyphenatedConcat` n'est pas pure car elle modifie le membre de données `aMember` dans la classe :</span><span class="sxs-lookup"><span data-stu-id="19871-120">In the following code, the `HyphenatedConcat` function is not a pure function, because it modifies the `aMember` data member in the class:</span></span>  
  
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
  
 <span data-ttu-id="19871-121">Ce code génère la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="19871-121">This code produces the following output:</span></span>  
  
```output  
StringOne-StringTwo  
```  
  
 <span data-ttu-id="19871-122">Notez qu’il importe peu que les données modifiées aient un accès `public` ou `private`, ou qu’elles correspondent à un membre `static` ou à un membre d’instance.</span><span class="sxs-lookup"><span data-stu-id="19871-122">Note that it is irrelevant whether the data being modified has `public` or `private` access, or is a `static` member or an instance member.</span></span> <span data-ttu-id="19871-123">Une fonction pure ne change aucune donnée en dehors de la fonction.</span><span class="sxs-lookup"><span data-stu-id="19871-123">A pure function does not change any data outside of the function.</span></span>  
  
### <a name="non-pure-function-that-changes-an-argument"></a><span data-ttu-id="19871-124">Fonction non pure qui modifie un argument</span><span class="sxs-lookup"><span data-stu-id="19871-124">Non-Pure Function that Changes an Argument</span></span>  
 <span data-ttu-id="19871-125">En outre, la version suivante de cette même fonction n'est pas pure car elle modifie le contenu de son paramètre, `sb`.</span><span class="sxs-lookup"><span data-stu-id="19871-125">Furthermore, the following version of this same function is not pure because it modifies the contents of its parameter, `sb`.</span></span>  
  
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
  
 <span data-ttu-id="19871-126">Cette version du programme génère la même sortie que la première version, car la fonction `HyphenatedConcat` a modifié la valeur (l'état) de son premier paramètre en appelant la fonction membre <xref:System.Text.StringBuilder.Append%2A>.</span><span class="sxs-lookup"><span data-stu-id="19871-126">This version of the program produces the same output as the first version, because the `HyphenatedConcat` function has changed the value (state) of its first parameter by invoking the <xref:System.Text.StringBuilder.Append%2A> member function.</span></span> <span data-ttu-id="19871-127">Notez que cette altération a lieu en dépit du fait que `HyphenatedConcat` utilise le passage de paramètre avec appel par valeur.</span><span class="sxs-lookup"><span data-stu-id="19871-127">Note that this alteration occurs despite that fact that `HyphenatedConcat` uses call-by-value parameter passing.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="19871-128">Pour les types de référence, si vous passez un paramètre par valeur, une copie de la référence à un objet est passée.</span><span class="sxs-lookup"><span data-stu-id="19871-128">For reference types, if you pass a parameter by value, it results in a copy of the reference to an object being passed.</span></span> <span data-ttu-id="19871-129">Cette copie est toujours associée aux mêmes données d'instance que la référence d'origine (jusqu'à ce que la variable de référence soit assignée à un nouvel objet).</span><span class="sxs-lookup"><span data-stu-id="19871-129">This copy is still associated with the same instance data as the original reference (until the reference variable is assigned to a new object).</span></span> <span data-ttu-id="19871-130">L'appel par référence n'est pas forcément nécessaire pour qu'une fonction modifie un paramètre.</span><span class="sxs-lookup"><span data-stu-id="19871-130">Call-by-reference is not necessarily required for a function to modify a parameter.</span></span>  
  
### <a name="pure-function"></a><span data-ttu-id="19871-131">Fonction pure</span><span class="sxs-lookup"><span data-stu-id="19871-131">Pure Function</span></span>  
<span data-ttu-id="19871-132">Cette autre version du programme montre comment implémenter la fonction `HyphenatedConcat` en tant que fonction pure.</span><span class="sxs-lookup"><span data-stu-id="19871-132">This next version of the program shows how to implement the `HyphenatedConcat` function as a pure function.</span></span>  
  
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
  
 <span data-ttu-id="19871-133">Là encore, cette version génère la même ligne de sortie : `StringOne-StringTwo`.</span><span class="sxs-lookup"><span data-stu-id="19871-133">Again, this version produces the same line of output: `StringOne-StringTwo`.</span></span> <span data-ttu-id="19871-134">Notez que pour conserver la valeur concaténée, elle est stockée dans la variable intermédiaire `s2`.</span><span class="sxs-lookup"><span data-stu-id="19871-134">Note that to retain the concatenated value, it is stored in the intermediate variable `s2`.</span></span>  
  
 <span data-ttu-id="19871-135">L'une des approches qui peuvent se révéler très utiles consiste à écrire des fonctions localement impures (à savoir, qui déclarent et modifient des variables locales) mais globalement pures.</span><span class="sxs-lookup"><span data-stu-id="19871-135">One approach that can be very useful is to write functions that are locally impure (that is, they declare and modify local variables) but are globally pure.</span></span> <span data-ttu-id="19871-136">Ces fonctions possèdent une grande partie des caractéristiques de composabilité requises, mais elles évitent certaines des tâches de programmation fonctionnelle plus compliquées, telles que l'utilisation de la récursivité lorsqu'une simple boucle génèrerait le même résultat.</span><span class="sxs-lookup"><span data-stu-id="19871-136">Such functions have many of the desirable composability characteristics, but avoid some of the more convoluted functional programming idioms, such as having to use recursion when a simple loop would accomplish the same thing.</span></span>  
  
## <a name="standard-query-operators"></a><span data-ttu-id="19871-137">Opérateurs de requête standard</span><span class="sxs-lookup"><span data-stu-id="19871-137">Standard Query Operators</span></span>  
 <span data-ttu-id="19871-138">L'une des caractéristiques importantes des opérateurs de requête standard est qu'ils sont implémentés en tant que fonctions pures.</span><span class="sxs-lookup"><span data-stu-id="19871-138">An important characteristic of the standard query operators is that they are implemented as pure functions.</span></span>  
  
 <span data-ttu-id="19871-139">Pour plus d’informations, consultez [Présentation des opérateurs de requête standard (C#)](./standard-query-operators-overview.md).</span><span class="sxs-lookup"><span data-stu-id="19871-139">For more information, see [Standard Query Operators Overview (C#)](./standard-query-operators-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="19871-140">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="19871-140">See also</span></span>

- [<span data-ttu-id="19871-141">Introduction aux transformations fonctionnelles pures (C#)</span><span class="sxs-lookup"><span data-stu-id="19871-141">Introduction to Pure Functional Transformations (C#)</span></span>](./introduction-to-pure-functional-transformations.md)
- [<span data-ttu-id="19871-142">Programmation fonctionnelle vs programmation impérative (C)</span><span class="sxs-lookup"><span data-stu-id="19871-142">Functional Programming vs. Imperative Programming (C#)</span></span>](./functional-programming-vs-imperative-programming.md)
