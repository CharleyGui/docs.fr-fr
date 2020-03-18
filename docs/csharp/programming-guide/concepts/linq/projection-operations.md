---
title: Opérations de projection (C#)
ms.date: 07/20/2015
ms.assetid: 98df573a-aad9-4b8c-9a71-844be2c4fb41
ms.openlocfilehash: f76eeeb779ab08a575e758a9d974573b700ae652
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79168334"
---
# <a name="projection-operations-c"></a><span data-ttu-id="0555f-102">Opérations de projection (C#)</span><span class="sxs-lookup"><span data-stu-id="0555f-102">Projection Operations (C#)</span></span>
<span data-ttu-id="0555f-103">La projection désigne l’opération de transformation d’un objet en une nouvelle forme qui se compose souvent uniquement des propriétés à utiliser ensuite.</span><span class="sxs-lookup"><span data-stu-id="0555f-103">Projection refers to the operation of transforming an object into a new form that often consists only of those properties that will be subsequently used.</span></span> <span data-ttu-id="0555f-104">À l'aide de la projection, vous pouvez créer un nouveau type qui est généré à partir de chaque objet.</span><span class="sxs-lookup"><span data-stu-id="0555f-104">By using projection, you can construct a new type that is built from each object.</span></span> <span data-ttu-id="0555f-105">Vous pouvez projeter une propriété et effectuer une fonction mathématique sur celle-ci.</span><span class="sxs-lookup"><span data-stu-id="0555f-105">You can project a property and perform a mathematical function on it.</span></span> <span data-ttu-id="0555f-106">Vous pouvez également projeter l’objet d’origine sans le modifier.</span><span class="sxs-lookup"><span data-stu-id="0555f-106">You can also project the original object without changing it.</span></span>  
  
 <span data-ttu-id="0555f-107">Les méthodes d’opérateurs de requête standard qui effectuent des opérations de projection sont répertoriées dans la section suivante.</span><span class="sxs-lookup"><span data-stu-id="0555f-107">The standard query operator methods that perform projection are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="0555f-108">Méthodes</span><span class="sxs-lookup"><span data-stu-id="0555f-108">Methods</span></span>  
  
|<span data-ttu-id="0555f-109">Nom de la méthode</span><span class="sxs-lookup"><span data-stu-id="0555f-109">Method Name</span></span>|<span data-ttu-id="0555f-110">Description</span><span class="sxs-lookup"><span data-stu-id="0555f-110">Description</span></span>|<span data-ttu-id="0555f-111">Syntaxe d'expression de requête C#</span><span class="sxs-lookup"><span data-stu-id="0555f-111">C# Query Expression Syntax</span></span>|<span data-ttu-id="0555f-112">Informations complémentaires</span><span class="sxs-lookup"><span data-stu-id="0555f-112">More Information</span></span>|  
|-----------------|-----------------|---------------------------------|----------------------|  
|<span data-ttu-id="0555f-113">Sélectionnez</span><span class="sxs-lookup"><span data-stu-id="0555f-113">Select</span></span>|<span data-ttu-id="0555f-114">Projette les valeurs qui sont basées sur une fonction de transformation.</span><span class="sxs-lookup"><span data-stu-id="0555f-114">Projects values that are based on a transform function.</span></span>|`select`|<xref:System.Linq.Enumerable.Select%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Select%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="0555f-115">SelectMany</span><span class="sxs-lookup"><span data-stu-id="0555f-115">SelectMany</span></span>|<span data-ttu-id="0555f-116">Projette les séquences de valeurs qui sont basées sur une fonction de transformation, puis les aplatit en une seule séquence.</span><span class="sxs-lookup"><span data-stu-id="0555f-116">Projects sequences of values that are based on a transform function and then flattens them into one sequence.</span></span>|<span data-ttu-id="0555f-117">Utilisation de plusieurs clauses `from`</span><span class="sxs-lookup"><span data-stu-id="0555f-117">Use multiple `from` clauses</span></span>|<xref:System.Linq.Enumerable.SelectMany%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.SelectMany%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-examples"></a><span data-ttu-id="0555f-118">Exemples de syntaxe d'expression de requête</span><span class="sxs-lookup"><span data-stu-id="0555f-118">Query Expression Syntax Examples</span></span>  
  
### <a name="select"></a><span data-ttu-id="0555f-119">Sélectionnez</span><span class="sxs-lookup"><span data-stu-id="0555f-119">Select</span></span>  
 <span data-ttu-id="0555f-120">L’exemple suivant utilise la clause `select` pour projeter la première lettre de chaque chaîne dans une liste de chaînes.</span><span class="sxs-lookup"><span data-stu-id="0555f-120">The following example uses the `select` clause to project the first letter from each string in a list of strings.</span></span>  
  
```csharp  
List<string> words = new List<string>() { "an", "apple", "a", "day" };  
  
var query = from word in words  
            select word.Substring(0, 1);  
  
foreach (string s in query)  
    Console.WriteLine(s);  
  
/* This code produces the following output:  
  
    a  
    a  
    a  
    d  
*/  
```  
  
### <a name="selectmany"></a><span data-ttu-id="0555f-121">SelectMany</span><span class="sxs-lookup"><span data-stu-id="0555f-121">SelectMany</span></span>  
 <span data-ttu-id="0555f-122">L’exemple suivant utilise plusieurs clauses `from` pour projeter tous les mots de chaque chaîne dans une liste de chaînes.</span><span class="sxs-lookup"><span data-stu-id="0555f-122">The following example uses multiple `from` clauses  to project each word from each string in a list of strings.</span></span>  
  
```csharp  
List<string> phrases = new List<string>() { "an apple a day", "the quick brown fox" };  
  
var query = from phrase in phrases  
            from word in phrase.Split(' ')  
            select word;  
  
foreach (string s in query)  
    Console.WriteLine(s);  
  
/* This code produces the following output:  
  
    an  
    apple  
    a  
    day  
    the  
    quick  
    brown  
    fox  
*/  
```  
  
## <a name="select-versus-selectmany"></a><span data-ttu-id="0555f-123">Comparaison de Select et SelectMany</span><span class="sxs-lookup"><span data-stu-id="0555f-123">Select versus SelectMany</span></span>  
 <span data-ttu-id="0555f-124">Les deux clauses `Select()` et `SelectMany()` retournent une valeur de résultat (ou des valeurs) à partir des valeurs sources.</span><span class="sxs-lookup"><span data-stu-id="0555f-124">The work of both `Select()` and `SelectMany()` is to produce a result value (or values) from source values.</span></span> <span data-ttu-id="0555f-125">`Select()` retourne une seule valeur de résultat pour chaque valeur source.</span><span class="sxs-lookup"><span data-stu-id="0555f-125">`Select()` produces one result value for every source value.</span></span> <span data-ttu-id="0555f-126">Le résultat global est donc une collection qui a le même nombre d’éléments que la collection source.</span><span class="sxs-lookup"><span data-stu-id="0555f-126">The overall result is therefore a collection that has the same number of elements as the source collection.</span></span> <span data-ttu-id="0555f-127">En revanche, `SelectMany()` retourne un résultat global unique qui contient des sous-collections concaténées à partir de chaque valeur source.</span><span class="sxs-lookup"><span data-stu-id="0555f-127">In contrast, `SelectMany()` produces a single overall result that contains concatenated sub-collections from each source value.</span></span> <span data-ttu-id="0555f-128">La fonction de transformation qui est passée comme argument à `SelectMany()` doit retourner une séquence énumérable de valeurs pour chaque valeur source.</span><span class="sxs-lookup"><span data-stu-id="0555f-128">The transform function that is passed as an argument to `SelectMany()` must return an enumerable sequence of values for each source value.</span></span> <span data-ttu-id="0555f-129">Ces séquences énumérables sont ensuite concaténées par `SelectMany()` pour créer une seule grande séquence.</span><span class="sxs-lookup"><span data-stu-id="0555f-129">These enumerable sequences are then concatenated by `SelectMany()` to create one large sequence.</span></span>  
  
 <span data-ttu-id="0555f-130">Les deux illustrations suivantes montrent en quoi les actions de ces deux méthodes sont différentes d’un point de vue conceptuel.</span><span class="sxs-lookup"><span data-stu-id="0555f-130">The following two illustrations show the conceptual difference between the actions of these two methods.</span></span> <span data-ttu-id="0555f-131">Dans chaque cas, supposons que la fonction (de transformation) du sélecteur sélectionne le tableau de fleurs (Flowers) à partir de chaque valeur source.</span><span class="sxs-lookup"><span data-stu-id="0555f-131">In each case, assume that the selector (transform) function selects the array of flowers from each source value.</span></span>  
  
 <span data-ttu-id="0555f-132">Cette illustration montre de quelle manière `Select()` retourne une collection qui a le même nombre d’éléments que la collection source.</span><span class="sxs-lookup"><span data-stu-id="0555f-132">This illustration depicts how `Select()` returns a collection that has the same number of elements as the source collection.</span></span>  
  
 ![Graphique montrant l’action de Select&#40;&#41;](./media/projection-operations/select-action-graphic.png)  
  
 <span data-ttu-id="0555f-134">Cette illustration montre de quelle façon `SelectMany()` concatène la séquence intermédiaire de tableaux en une seule valeur de résultat final qui contient chaque valeur de chaque tableau intermédiaire.</span><span class="sxs-lookup"><span data-stu-id="0555f-134">This illustration depicts how `SelectMany()` concatenates the intermediate sequence of arrays into one final result value that contains each value from each intermediate array.</span></span>  
  
 ![Graphique montrant l’action de SelectMany&#40;&#41;.](./media/projection-operations/select-many-action-graphic.png )  
  
### <a name="code-example"></a><span data-ttu-id="0555f-136">Exemple de code</span><span class="sxs-lookup"><span data-stu-id="0555f-136">Code Example</span></span>  
 <span data-ttu-id="0555f-137">L’exemple suivant compare le comportement de `Select()` et de `SelectMany()`.</span><span class="sxs-lookup"><span data-stu-id="0555f-137">The following example compares the behavior of `Select()` and `SelectMany()`.</span></span> <span data-ttu-id="0555f-138">Le code crée un « bouquet » de fleurs en prenant les deux premiers éléments de chaque liste de noms de fleurs de la collection source.</span><span class="sxs-lookup"><span data-stu-id="0555f-138">The code creates a "bouquet" of flowers by taking the first two items from each list of flower names in the source collection.</span></span> <span data-ttu-id="0555f-139">Dans cet exemple, la « valeur unique » que la fonction de transformation <xref:System.Linq.Enumerable.Select%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%29> utilise est elle-même une collection de valeurs.</span><span class="sxs-lookup"><span data-stu-id="0555f-139">In this example, the "single value" that the transform function <xref:System.Linq.Enumerable.Select%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%29> uses is itself a collection of values.</span></span> <span data-ttu-id="0555f-140">Cela nécessite d’utiliser la boucle `foreach` supplémentaire pour énumérer chaque chaîne dans chaque sous-séquence.</span><span class="sxs-lookup"><span data-stu-id="0555f-140">This requires the extra `foreach` loop in order to enumerate each string in each sub-sequence.</span></span>  
  
```csharp  
class Bouquet  
{  
    public List<string> Flowers { get; set; }  
}  
  
static void SelectVsSelectMany()  
{  
    List<Bouquet> bouquets = new List<Bouquet>() {  
        new Bouquet { Flowers = new List<string> { "sunflower", "daisy", "daffodil", "larkspur" }},  
        new Bouquet{ Flowers = new List<string> { "tulip", "rose", "orchid" }},  
        new Bouquet{ Flowers = new List<string> { "gladiolis", "lily", "snapdragon", "aster", "protea" }},  
        new Bouquet{ Flowers = new List<string> { "larkspur", "lilac", "iris", "dahlia" }}  
    };  
  
    // *********** Select ***********
    IEnumerable<List<string>> query1 = bouquets.Select(bq => bq.Flowers);  
  
    // ********* SelectMany *********  
    IEnumerable<string> query2 = bouquets.SelectMany(bq => bq.Flowers);  
  
    Console.WriteLine("Results by using Select():");  
    // Note the extra foreach loop here.  
    foreach (IEnumerable<String> collection in query1)  
        foreach (string item in collection)  
            Console.WriteLine(item);  
  
    Console.WriteLine("\nResults by using SelectMany():");  
    foreach (string item in query2)  
        Console.WriteLine(item);  
  
    /* This code produces the following output:  
  
       Results by using Select():  
        sunflower  
        daisy  
        daffodil  
        larkspur  
        tulip  
        rose  
        orchid  
        gladiolis  
        lily  
        snapdragon  
        aster  
        protea  
        larkspur  
        lilac  
        iris  
        dahlia  
  
       Results by using SelectMany():  
        sunflower  
        daisy  
        daffodil  
        larkspur  
        tulip  
        rose  
        orchid  
        gladiolis  
        lily  
        snapdragon  
        aster  
        protea  
        larkspur  
        lilac  
        iris  
        dahlia  
    */  
  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="0555f-141">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0555f-141">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="0555f-142">Vue d’ensemble des opérateurs de requête standard (C#)</span><span class="sxs-lookup"><span data-stu-id="0555f-142">Standard Query Operators Overview (C#)</span></span>](./standard-query-operators-overview.md)
- [<span data-ttu-id="0555f-143">clause de sélection</span><span class="sxs-lookup"><span data-stu-id="0555f-143">select clause</span></span>](../../../language-reference/keywords/select-clause.md)
- [<span data-ttu-id="0555f-144">Comment remplir les collections d’objets à partir de sources multiples (LINQ) (C)</span><span class="sxs-lookup"><span data-stu-id="0555f-144">How to populate object collections from multiple sources (LINQ) (C#)</span></span>](./how-to-populate-object-collections-from-multiple-sources-linq.md)
- [<span data-ttu-id="0555f-145">Comment diviser un fichier en plusieurs fichiers en utilisant des groupes (LINQ) (C)</span><span class="sxs-lookup"><span data-stu-id="0555f-145">How to split a file into many files by using groups (LINQ) (C#)</span></span>](./how-to-split-a-file-into-many-files-by-using-groups-linq.md)
