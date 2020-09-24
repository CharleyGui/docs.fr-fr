---
title: Transformations de données avec LINQ (C#)
description: Découvrez comment utiliser des requêtes LINQ en C# pour transformer des données. Vous pouvez modifier la séquence en triant et en regroupant et en créant de nouveaux types à l’aide de la clause SELECT.
ms.date: 07/20/2015
helpviewer_keywords:
- LINQ [C#], data transformations
- source elements [LINQ in C#]
- joining multiple inputs [LINQ in C#]
- multiple outputs for one output sequence [LINQ in C#]
- subset of source elements [LINQ in C#]
- data sources [LINQ in C#], data transformations
- data transformations [LINQ in C#]
ms.assetid: 674eae9e-bc72-4a88-aed3-802b45b25811
ms.openlocfilehash: 2fb4166b9dbcecebf06b9dc3a780b02751dd4dc7
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91159148"
---
# <a name="data-transformations-with-linq-c"></a><span data-ttu-id="1bb31-104">Transformations de données avec LINQ (C#)</span><span class="sxs-lookup"><span data-stu-id="1bb31-104">Data Transformations with LINQ (C#)</span></span>

<span data-ttu-id="1bb31-105">LINQ (Language-Integrated Query) n’est pas seulement la récupération des données.</span><span class="sxs-lookup"><span data-stu-id="1bb31-105">Language-Integrated Query (LINQ) is not only about retrieving data.</span></span> <span data-ttu-id="1bb31-106">C’est également un outil puissant pour la transformation de données.</span><span class="sxs-lookup"><span data-stu-id="1bb31-106">It is also a powerful tool for transforming data.</span></span> <span data-ttu-id="1bb31-107">À l’aide d’une requête LINQ, vous pouvez utiliser une séquence source comme entrée et la modifier de nombreuses façons pour créer une séquence de sortie.</span><span class="sxs-lookup"><span data-stu-id="1bb31-107">By using a LINQ query, you can use a source sequence as input and modify it in many ways to create a new output sequence.</span></span> <span data-ttu-id="1bb31-108">Vous pouvez modifier la séquence elle-même sans modifier les éléments eux-mêmes en les triant et en les regroupant.</span><span class="sxs-lookup"><span data-stu-id="1bb31-108">You can modify the sequence itself without modifying the elements themselves by sorting and grouping.</span></span> <span data-ttu-id="1bb31-109">Mais la fonctionnalité la plus puissante des requêtes LINQ est peut-être la possibilité de créer des types.</span><span class="sxs-lookup"><span data-stu-id="1bb31-109">But perhaps the most powerful feature of LINQ queries is the ability to create new types.</span></span> <span data-ttu-id="1bb31-110">Cette opération est effectuée dans la clause [select](../../../language-reference/keywords/select-clause.md).</span><span class="sxs-lookup"><span data-stu-id="1bb31-110">This is accomplished in the [select](../../../language-reference/keywords/select-clause.md) clause.</span></span> <span data-ttu-id="1bb31-111">Par exemple, il est possible de réaliser les tâches suivantes :</span><span class="sxs-lookup"><span data-stu-id="1bb31-111">For example, you can perform the following tasks:</span></span>  
  
- <span data-ttu-id="1bb31-112">Fusionner plusieurs séquences d’entrée en une séquence de sortie unique ayant un nouveau type.</span><span class="sxs-lookup"><span data-stu-id="1bb31-112">Merge multiple input sequences into a single output sequence that has a new type.</span></span>  
  
- <span data-ttu-id="1bb31-113">Créer des séquences de sortie dont les éléments se composent d’une seule propriété ou de plusieurs propriétés de chaque élément de la séquence source.</span><span class="sxs-lookup"><span data-stu-id="1bb31-113">Create output sequences whose elements consist of only one or several properties of each element in the source sequence.</span></span>  
  
- <span data-ttu-id="1bb31-114">Créer des séquences de sortie dont les éléments se composent des résultats des opérations effectuées sur les données sources.</span><span class="sxs-lookup"><span data-stu-id="1bb31-114">Create output sequences whose elements consist of the results of operations performed on the source data.</span></span>  
  
- <span data-ttu-id="1bb31-115">Créer des séquences de sortie dans un format différent.</span><span class="sxs-lookup"><span data-stu-id="1bb31-115">Create output sequences in a different format.</span></span> <span data-ttu-id="1bb31-116">Par exemple, vous pouvez transformer des données de lignes ou de fichiers texte SQL en données XML.</span><span class="sxs-lookup"><span data-stu-id="1bb31-116">For example, you can transform data from SQL rows or text files into XML.</span></span>  
  
 <span data-ttu-id="1bb31-117">Voici une liste non exhaustive d’exemples.</span><span class="sxs-lookup"><span data-stu-id="1bb31-117">These are just several examples.</span></span> <span data-ttu-id="1bb31-118">Bien sûr, ces transformations peuvent être combinées de plusieurs façons dans la même requête.</span><span class="sxs-lookup"><span data-stu-id="1bb31-118">Of course, these transformations can be combined in various ways in the same query.</span></span> <span data-ttu-id="1bb31-119">Par ailleurs, la séquence de sortie d’une requête peut être utilisée comme séquence d’entrée pour une nouvelle requête.</span><span class="sxs-lookup"><span data-stu-id="1bb31-119">Furthermore, the output sequence of one query can be used as the input sequence for a new query.</span></span>  
  
## <a name="joining-multiple-inputs-into-one-output-sequence"></a><span data-ttu-id="1bb31-120">Combinaison de plusieurs entrées en une séquence de sortie</span><span class="sxs-lookup"><span data-stu-id="1bb31-120">Joining Multiple Inputs into One Output Sequence</span></span>  

 <span data-ttu-id="1bb31-121">Vous pouvez utiliser une requête LINQ pour créer une séquence de sortie qui contient des éléments issus de plusieurs séquences d’entrée.</span><span class="sxs-lookup"><span data-stu-id="1bb31-121">You can use a LINQ query to create an output sequence that contains elements from more than one input sequence.</span></span> <span data-ttu-id="1bb31-122">L’exemple suivant montre comment combiner deux structures de données en mémoire, mais les mêmes principes peuvent être appliqués pour combiner des données provenant de sources XML, SQL ou DataSet.</span><span class="sxs-lookup"><span data-stu-id="1bb31-122">The following example shows how to combine two in-memory data structures, but the same principles can be applied to combine data from XML or SQL or DataSet sources.</span></span> <span data-ttu-id="1bb31-123">Prenons l’exemple des deux types de classe suivants :</span><span class="sxs-lookup"><span data-stu-id="1bb31-123">Assume the following two class types:</span></span>  
  
 [!code-csharp[CsLINQGettingStarted#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#7)]  
  
 <span data-ttu-id="1bb31-124">L’exemple suivant présente la requête :</span><span class="sxs-lookup"><span data-stu-id="1bb31-124">The following example shows the query:</span></span>  
  
 [!code-csharp[CSLinqGettingStarted#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#8)]  
  
 <span data-ttu-id="1bb31-125">Pour plus d’informations, consultez [join, clause](../../../language-reference/keywords/join-clause.md) et [select, clause](../../../language-reference/keywords/select-clause.md).</span><span class="sxs-lookup"><span data-stu-id="1bb31-125">For more information, see [join clause](../../../language-reference/keywords/join-clause.md) and [select clause](../../../language-reference/keywords/select-clause.md).</span></span>  
  
## <a name="selecting-a-subset-of-each-source-element"></a><span data-ttu-id="1bb31-126">Sélection d’un sous-ensemble de chaque élément source</span><span class="sxs-lookup"><span data-stu-id="1bb31-126">Selecting a Subset of each Source Element</span></span>  

 <span data-ttu-id="1bb31-127">Pour sélectionner un sous-ensemble de chaque élément de la séquence source, deux méthodes principales s’offrent à vous :</span><span class="sxs-lookup"><span data-stu-id="1bb31-127">There are two primary ways to select a subset of each element in the source sequence:</span></span>  
  
1. <span data-ttu-id="1bb31-128">Pour sélectionner un seul membre de l’élément source, utilisez l’opérateur point.</span><span class="sxs-lookup"><span data-stu-id="1bb31-128">To select just one member of the source element, use the dot operation.</span></span> <span data-ttu-id="1bb31-129">Dans l’exemple suivant, supposons qu’un objet `Customer` contienne plusieurs propriétés publiques comprenant une chaîne nommée `City`.</span><span class="sxs-lookup"><span data-stu-id="1bb31-129">In the following example, assume that a `Customer` object contains several public properties including a string named `City`.</span></span> <span data-ttu-id="1bb31-130">Une fois exécutée, cette requête génère une séquence de sortie de chaînes.</span><span class="sxs-lookup"><span data-stu-id="1bb31-130">When executed, this query will produce an output sequence of strings.</span></span>  
  
    ```csharp
    var query = from cust in Customers  
                select cust.City;  
    ```  
  
2. <span data-ttu-id="1bb31-131">Pour créer des éléments qui contiennent plusieurs propriétés de l’élément source, vous pouvez utiliser un initialiseur d’objet avec un objet nommé ou un type anonyme.</span><span class="sxs-lookup"><span data-stu-id="1bb31-131">To create elements that contain more than one property from the source element, you can use an object initializer with either a named object or an anonymous type.</span></span> <span data-ttu-id="1bb31-132">L’exemple suivant montre comment utiliser un type anonyme pour encapsuler deux propriétés de chaque élément `Customer` :</span><span class="sxs-lookup"><span data-stu-id="1bb31-132">The following example shows the use of an anonymous type to encapsulate two properties from each `Customer` element:</span></span>  
  
    ```csharp
    var query = from cust in Customer  
                select new {Name = cust.Name, City = cust.City};  
    ```  
  
 <span data-ttu-id="1bb31-133">Pour plus d’informations, consultez [Initialiseurs d’objets et de collections](../../classes-and-structs/object-and-collection-initializers.md) et [Types anonymes](../../classes-and-structs/anonymous-types.md).</span><span class="sxs-lookup"><span data-stu-id="1bb31-133">For more information, see [Object and Collection Initializers](../../classes-and-structs/object-and-collection-initializers.md) and [Anonymous Types](../../classes-and-structs/anonymous-types.md).</span></span>  
  
## <a name="transforming-in-memory-objects-into-xml"></a><span data-ttu-id="1bb31-134">Transformation d’objets en mémoire en XML</span><span class="sxs-lookup"><span data-stu-id="1bb31-134">Transforming in-Memory Objects into XML</span></span>  

 <span data-ttu-id="1bb31-135">Les requêtes LINQ facilitent la transformation des données entre les structures de données en mémoire, les bases de données SQL, les jeux de données ADO.NET et les flux ou documents XML.</span><span class="sxs-lookup"><span data-stu-id="1bb31-135">LINQ queries make it easy to transform data between in-memory data structures, SQL databases, ADO.NET Datasets and XML streams or documents.</span></span> <span data-ttu-id="1bb31-136">L’exemple suivant transforme des objets d’une structure de données en mémoire en éléments XML.</span><span class="sxs-lookup"><span data-stu-id="1bb31-136">The following example transforms objects in an in-memory data structure into XML elements.</span></span>  
  
 [!code-csharp[CsLINQGettingStarted#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#9)]  
  
 <span data-ttu-id="1bb31-137">Le code génère la sortie XML suivante :</span><span class="sxs-lookup"><span data-stu-id="1bb31-137">The code produces the following XML output:</span></span>  
  
```xml  
<Root>  
  <student>  
    <First>Svetlana</First>  
    <Last>Omelchenko</Last>  
    <Scores>97,92,81,60</Scores>  
  </student>  
  <student>  
    <First>Claire</First>  
    <Last>O'Donnell</Last>  
    <Scores>75,84,91,39</Scores>  
  </student>  
  <student>  
    <First>Sven</First>  
    <Last>Mortensen</Last>  
    <Scores>88,94,65,91</Scores>  
  </student>  
</Root>  
```  
  
 <span data-ttu-id="1bb31-138">Pour plus d’informations, consultez [Création d’arborescences XML en C# (LINQ to XML)](../../../../standard/linq/create-xml-trees.md).</span><span class="sxs-lookup"><span data-stu-id="1bb31-138">For more information, see [Creating XML Trees in C# (LINQ to XML)](../../../../standard/linq/create-xml-trees.md).</span></span>  
  
## <a name="performing-operations-on-source-elements"></a><span data-ttu-id="1bb31-139">Exécution d’opérations sur les éléments sources</span><span class="sxs-lookup"><span data-stu-id="1bb31-139">Performing Operations on Source Elements</span></span>  

 <span data-ttu-id="1bb31-140">Une séquence de sortie ne contient pas toujours des éléments ou des propriétés d’élément de la séquence source.</span><span class="sxs-lookup"><span data-stu-id="1bb31-140">An output sequence might not contain any elements or element properties from the source sequence.</span></span> <span data-ttu-id="1bb31-141">La sortie peut être plutôt une séquence de valeurs calculée en utilisant les éléments sources comme arguments d’entrée.</span><span class="sxs-lookup"><span data-stu-id="1bb31-141">The output might instead be a sequence of values that is computed by using the source elements as input arguments.</span></span>

 <span data-ttu-id="1bb31-142">La requête suivante prend une séquence de nombres représentant des rayons de cercles, calcule la zone pour chaque rayon et retourne une séquence de sortie contenant des chaînes mises en forme avec la zone calculée.</span><span class="sxs-lookup"><span data-stu-id="1bb31-142">The following query will take a sequence of numbers that represent radii of circles, calculate the area for each radius, and return an output sequence containing strings formatted with the calculated area.</span></span>

 <span data-ttu-id="1bb31-143">Chaque chaîne de la séquence de sortie est mise en forme à l’aide de l' [interpolation de chaîne](../../../language-reference/tokens/interpolated.md).</span><span class="sxs-lookup"><span data-stu-id="1bb31-143">Each string for the output sequence will be formatted using [string interpolation](../../../language-reference/tokens/interpolated.md).</span></span> <span data-ttu-id="1bb31-144">Une chaîne interpolée aura une `$` devant le guillemet ouvrant de la chaîne, et les opérations peuvent être effectuées entre accolades placées à l’intérieur de la chaîne interpolée.</span><span class="sxs-lookup"><span data-stu-id="1bb31-144">An interpolated string will have a `$` in front of the string's opening quotation mark, and operations can be performed within curly braces placed inside the interpolated string.</span></span> <span data-ttu-id="1bb31-145">Une fois ces opérations effectuées, les résultats sont concaténés.</span><span class="sxs-lookup"><span data-stu-id="1bb31-145">Once those operations are performed, the results will be concatenated.</span></span>
  
> [!NOTE]
> <span data-ttu-id="1bb31-146">Les méthodes d’appel dans les expressions de requête ne sont pas prises en charge si la requête est traduite dans un autre domaine.</span><span class="sxs-lookup"><span data-stu-id="1bb31-146">Calling methods in query expressions is not supported if the query will be translated into some other domain.</span></span> <span data-ttu-id="1bb31-147">Par exemple, vous ne pouvez pas appeler une méthode C# ordinaire dans [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)], car SQL Server n’a pas de contexte pour cette méthode.</span><span class="sxs-lookup"><span data-stu-id="1bb31-147">For example, you cannot call an ordinary C# method in [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] because SQL Server has no context for it.</span></span> <span data-ttu-id="1bb31-148">Toutefois, vous pouvez mapper des procédures stockées à des méthodes et appeler celles-ci.</span><span class="sxs-lookup"><span data-stu-id="1bb31-148">However, you can map stored procedures to methods and call those.</span></span> <span data-ttu-id="1bb31-149">Pour plus d’informations, consultez [Procédures stockées](../../../../framework/data/adonet/sql/linq/stored-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="1bb31-149">For more information, see [Stored Procedures](../../../../framework/data/adonet/sql/linq/stored-procedures.md).</span></span>  
  
 [!code-csharp[CsLINQGettingStarted#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#10)]  
  
## <a name="see-also"></a><span data-ttu-id="1bb31-150">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1bb31-150">See also</span></span>

- [<span data-ttu-id="1bb31-151">LINQ (Language-Integrated Query) (C#)</span><span class="sxs-lookup"><span data-stu-id="1bb31-151">Language-Integrated Query (LINQ) (C#)</span></span>](./index.md)
- [<span data-ttu-id="1bb31-152">LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="1bb31-152">LINQ to SQL</span></span>](../../../../framework/data/adonet/sql/linq/index.md)
- [<span data-ttu-id="1bb31-153">LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="1bb31-153">LINQ to DataSet</span></span>](../../../../framework/data/adonet/linq-to-dataset.md)
- [<span data-ttu-id="1bb31-154">LINQ to XML (C#)</span><span class="sxs-lookup"><span data-stu-id="1bb31-154">LINQ to XML (C#)</span></span>](../../../../standard/linq/linq-xml-overview.md)
- [<span data-ttu-id="1bb31-155">Expressions de requête LINQ</span><span class="sxs-lookup"><span data-stu-id="1bb31-155">LINQ Query Expressions</span></span>](../../../linq/index.md)
- [<span data-ttu-id="1bb31-156">clause SELECT</span><span class="sxs-lookup"><span data-stu-id="1bb31-156">select clause</span></span>](../../../language-reference/keywords/select-clause.md)
