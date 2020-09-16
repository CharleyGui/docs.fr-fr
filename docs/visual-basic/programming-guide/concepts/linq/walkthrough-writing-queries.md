---
title: écriture de requêtes
ms.date: 07/20/2015
helpviewer_keywords:
- queries [LINQ in Visual Basic], writing
- LINQ [Visual Basic], walkthroughs
- LINQ [Visual Basic], writing queries
- writing LINQ queries [Visual Basic]
ms.assetid: f0045808-b9fe-4d31-88d1-473d9957211e
ms.openlocfilehash: c2abca183f1241cff314a4367c7bd9f1b9f239ea
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90554591"
---
# <a name="walkthrough-writing-queries-in-visual-basic"></a><span data-ttu-id="4b924-102">Procédure pas à pas : écriture de requêtes dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="4b924-102">Walkthrough: Writing Queries in Visual Basic</span></span>

<span data-ttu-id="4b924-103">Cette procédure pas à pas montre comment vous pouvez utiliser des fonctionnalités de langage Visual Basic pour écrire des expressions de requête LINQ (Language-Integrated Query).</span><span class="sxs-lookup"><span data-stu-id="4b924-103">This walkthrough demonstrates how you can use Visual Basic language features to write Language-Integrated Query (LINQ) query expressions.</span></span> <span data-ttu-id="4b924-104">La procédure pas à pas montre comment créer des requêtes sur une liste d’objets Student, comment exécuter les requêtes et comment les modifier.</span><span class="sxs-lookup"><span data-stu-id="4b924-104">The walkthrough demonstrates how to create queries on a list of Student objects, how to run the queries, and how to modify them.</span></span> <span data-ttu-id="4b924-105">Les requêtes incorporent plusieurs fonctionnalités, notamment les initialiseurs d’objets, l’inférence de type local et les types anonymes.</span><span class="sxs-lookup"><span data-stu-id="4b924-105">The queries incorporate several features including object initializers, local type inference, and anonymous types.</span></span>

<span data-ttu-id="4b924-106">À l’issue de cette procédure pas à pas, vous serez prêt à passer aux exemples et à la documentation du fournisseur LINQ spécifique qui vous intéresse.</span><span class="sxs-lookup"><span data-stu-id="4b924-106">After completing this walkthrough, you will be ready to move on to the samples and documentation for the specific LINQ provider you are interested in.</span></span> <span data-ttu-id="4b924-107">Les fournisseurs LINQ incluent [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] , LINQ to DataSet et [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="4b924-107">LINQ providers include [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)], LINQ to DataSet, and [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span></span>

## <a name="create-a-project"></a><span data-ttu-id="4b924-108">Créer un projet</span><span class="sxs-lookup"><span data-stu-id="4b924-108">Create a Project</span></span>

### <a name="to-create-a-console-application-project"></a><span data-ttu-id="4b924-109">Pour créer un projet d’application console</span><span class="sxs-lookup"><span data-stu-id="4b924-109">To create a console application project</span></span>

1. <span data-ttu-id="4b924-110">Démarrez Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="4b924-110">Start Visual Studio.</span></span>

2. <span data-ttu-id="4b924-111">Dans le menu **Fichier** , pointez sur **Nouveau**, puis cliquez sur **Projet**.</span><span class="sxs-lookup"><span data-stu-id="4b924-111">On the **File** menu, point to **New**, and then click **Project**.</span></span>

3. <span data-ttu-id="4b924-112">Dans la liste **modèles installés** , cliquez sur **Visual Basic**.</span><span class="sxs-lookup"><span data-stu-id="4b924-112">In the **Installed Templates** list, click **Visual Basic**.</span></span>

4. <span data-ttu-id="4b924-113">Dans la liste des types de projets, cliquez sur **application console**.</span><span class="sxs-lookup"><span data-stu-id="4b924-113">In the list of project types, click **Console Application**.</span></span> <span data-ttu-id="4b924-114">Dans la zone **nom** , tapez un nom pour le projet, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="4b924-114">In the **Name** box, type a name for the project, and then click **OK**.</span></span>

    <span data-ttu-id="4b924-115">Un projet est créé.</span><span class="sxs-lookup"><span data-stu-id="4b924-115">A project is created.</span></span> <span data-ttu-id="4b924-116">Par défaut, il contient une référence à System.Core.dll.</span><span class="sxs-lookup"><span data-stu-id="4b924-116">By default, it contains a reference to System.Core.dll.</span></span> <span data-ttu-id="4b924-117">En outre, la liste des **espaces de noms importés** sur la [page références, le concepteur de projets (Visual Basic)](/visualstudio/ide/reference/references-page-project-designer-visual-basic) comprend l' <xref:System.Linq?displayProperty=nameWithType> espace de noms.</span><span class="sxs-lookup"><span data-stu-id="4b924-117">Also, the **Imported namespaces** list on the [References Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/references-page-project-designer-visual-basic) includes the <xref:System.Linq?displayProperty=nameWithType> namespace.</span></span>

5. <span data-ttu-id="4b924-118">Sur la [page compiler, Project Designer (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic), vérifiez que **Option Infer** a la valeur **on**.</span><span class="sxs-lookup"><span data-stu-id="4b924-118">On the [Compile Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic), ensure that **Option infer** is set to **On**.</span></span>

## <a name="add-an-in-memory-data-source"></a><span data-ttu-id="4b924-119">Ajouter une source de données en mémoire</span><span class="sxs-lookup"><span data-stu-id="4b924-119">Add an In-Memory Data Source</span></span>

<span data-ttu-id="4b924-120">La source de données pour les requêtes de cette procédure pas à pas est une liste d' `Student` objets.</span><span class="sxs-lookup"><span data-stu-id="4b924-120">The data source for the queries in this walkthrough is a list of `Student` objects.</span></span> <span data-ttu-id="4b924-121">Chaque `Student` objet contient un prénom, un nom, une année de classe et un classement universitaire dans le corps de l’étudiant.</span><span class="sxs-lookup"><span data-stu-id="4b924-121">Each `Student` object contains a first name, a last name, a class year, and an academic rank in the student body.</span></span>

### <a name="to-add-the-data-source"></a><span data-ttu-id="4b924-122">Pour ajouter la source de données</span><span class="sxs-lookup"><span data-stu-id="4b924-122">To add the data source</span></span>

- <span data-ttu-id="4b924-123">Définissez une `Student` classe et créez une liste d’instances de la classe.</span><span class="sxs-lookup"><span data-stu-id="4b924-123">Define a `Student` class, and create a list of instances of the class.</span></span>

  > [!IMPORTANT]
  > <span data-ttu-id="4b924-124">Le code nécessaire pour définir la `Student` classe et créer la liste utilisée dans les exemples de procédure pas à pas est fourni dans [How to : Create a list of items](how-to-create-a-list-of-items.md).</span><span class="sxs-lookup"><span data-stu-id="4b924-124">The code needed to define the `Student` class and create the list used in the walkthrough examples is provided in [How to: Create a List of Items](how-to-create-a-list-of-items.md).</span></span> <span data-ttu-id="4b924-125">Vous pouvez la copier à partir de là et la coller dans votre projet.</span><span class="sxs-lookup"><span data-stu-id="4b924-125">You can copy it from there and paste it into your project.</span></span> <span data-ttu-id="4b924-126">Le nouveau code remplace le code qui s’est affiché lorsque vous avez créé le projet.</span><span class="sxs-lookup"><span data-stu-id="4b924-126">The new code replaces the code that appeared when you created the project.</span></span>

### <a name="to-add-a-new-student-to-the-students-list"></a><span data-ttu-id="4b924-127">Pour ajouter un nouvel étudiant à la liste des étudiants</span><span class="sxs-lookup"><span data-stu-id="4b924-127">To add a new student to the students list</span></span>

- <span data-ttu-id="4b924-128">Suivez le modèle dans la `getStudents` méthode pour ajouter une autre instance de la `Student` classe à la liste.</span><span class="sxs-lookup"><span data-stu-id="4b924-128">Follow the pattern in the `getStudents` method to add another instance of the `Student` class to the list.</span></span> <span data-ttu-id="4b924-129">L’ajout de l’étudiant vous introduira des initialiseurs d’objets.</span><span class="sxs-lookup"><span data-stu-id="4b924-129">Adding the student will introduce you to object initializers.</span></span> <span data-ttu-id="4b924-130">Pour plus d’informations, consultez [initialiseurs d’objets : types nommés et anonymes](../../language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md).</span><span class="sxs-lookup"><span data-stu-id="4b924-130">For more information, see [Object Initializers: Named and Anonymous Types](../../language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md).</span></span>

## <a name="create-a-query"></a><span data-ttu-id="4b924-131">Créer une requête</span><span class="sxs-lookup"><span data-stu-id="4b924-131">Create a Query</span></span>

<span data-ttu-id="4b924-132">Une fois exécutée, la requête ajoutée dans cette section produit une liste des étudiants dont le classement universitaire les place dans les dix premiers.</span><span class="sxs-lookup"><span data-stu-id="4b924-132">When executed, the query added in this section produces a list of the students whose academic rank puts them in the top ten.</span></span> <span data-ttu-id="4b924-133">Étant donné que la requête sélectionne l’objet complet à `Student` chaque fois, le type du résultat de la requête est `IEnumerable(Of Student)` .</span><span class="sxs-lookup"><span data-stu-id="4b924-133">Because the query selects the complete `Student` object each time, the type of the query result is `IEnumerable(Of Student)`.</span></span> <span data-ttu-id="4b924-134">Toutefois, le type de la requête n’est généralement pas spécifié dans les définitions de requête.</span><span class="sxs-lookup"><span data-stu-id="4b924-134">However, the type of the query typically is not specified in query definitions.</span></span> <span data-ttu-id="4b924-135">Au lieu de cela, le compilateur utilise l’inférence de type local pour déterminer le type.</span><span class="sxs-lookup"><span data-stu-id="4b924-135">Instead, the compiler uses local type inference to determine the type.</span></span> <span data-ttu-id="4b924-136">Pour plus d’informations, consultez [inférence de type local](../../language-features/variables/local-type-inference.md).</span><span class="sxs-lookup"><span data-stu-id="4b924-136">For more information, see [Local Type Inference](../../language-features/variables/local-type-inference.md).</span></span> <span data-ttu-id="4b924-137">La variable de portée de la requête, `currentStudent` , sert de référence à chaque `Student` instance dans la source, `students` , qui fournit l’accès aux propriétés de chaque objet dans `students` .</span><span class="sxs-lookup"><span data-stu-id="4b924-137">The query's range variable, `currentStudent`, serves as a reference to each `Student` instance in the source, `students`, providing access to the properties of each object in `students`.</span></span>

### <a name="to-create-a-simple-query"></a><span data-ttu-id="4b924-138">Pour créer une requête simple</span><span class="sxs-lookup"><span data-stu-id="4b924-138">To create a simple query</span></span>

1. <span data-ttu-id="4b924-139">Recherchez l’emplacement dans la `Main` méthode du projet qui est marqué comme suit :</span><span class="sxs-lookup"><span data-stu-id="4b924-139">Find the place in the `Main` method of the project that is marked as follows:</span></span>

    [!code-vb[VbLINQWalkthrough#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQWalkthrough/VB/Class1.vb#1)]

    <span data-ttu-id="4b924-140">Copiez le code suivant et collez-le dans.</span><span class="sxs-lookup"><span data-stu-id="4b924-140">Copy the following code and paste it in.</span></span>

    [!code-vb[VbLINQWalkthrough#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQWalkthrough/VB/Class1.vb#2)]

2. <span data-ttu-id="4b924-141">Placez le pointeur de la souris au `studentQuery` -dessus de votre code pour vérifier que le type assigné par le compilateur est `IEnumerable(Of Student)` .</span><span class="sxs-lookup"><span data-stu-id="4b924-141">Rest the mouse pointer over `studentQuery` in your code to verify that the compiler-assigned type is `IEnumerable(Of Student)`.</span></span>

## <a name="run-the-query"></a><span data-ttu-id="4b924-142">Exécuter la requête</span><span class="sxs-lookup"><span data-stu-id="4b924-142">Run the Query</span></span>

<span data-ttu-id="4b924-143">La variable `studentQuery` contient la définition de la requête, et non les résultats de l’exécution de la requête.</span><span class="sxs-lookup"><span data-stu-id="4b924-143">The variable `studentQuery` contains the definition of the query, not the results of running the query.</span></span> <span data-ttu-id="4b924-144">Une boucle est un mécanisme classique pour exécuter une requête `For Each` .</span><span class="sxs-lookup"><span data-stu-id="4b924-144">A typical mechanism for running a query is a `For Each` loop.</span></span> <span data-ttu-id="4b924-145">Chaque élément de la séquence retournée est accessible via la variable d’itération de la boucle.</span><span class="sxs-lookup"><span data-stu-id="4b924-145">Each element in the returned sequence is accessed through the loop iteration variable.</span></span> <span data-ttu-id="4b924-146">Pour plus d’informations sur l’exécution des requêtes, consultez [écriture de votre première requête LINQ](writing-your-first-linq-query.md).</span><span class="sxs-lookup"><span data-stu-id="4b924-146">For more information about query execution, see [Writing Your First LINQ Query](writing-your-first-linq-query.md).</span></span>

### <a name="to-run-the-query"></a><span data-ttu-id="4b924-147">Pour exécuter la requête</span><span class="sxs-lookup"><span data-stu-id="4b924-147">To run the query</span></span>

1. <span data-ttu-id="4b924-148">Ajoutez la `For Each` boucle suivante sous la requête dans votre projet.</span><span class="sxs-lookup"><span data-stu-id="4b924-148">Add the following `For Each` loop below the query in your project.</span></span>

    [!code-vb[VbLINQWalkthrough#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQWalkthrough/VB/Class1.vb#3)]

2. <span data-ttu-id="4b924-149">Placez le pointeur de la souris sur la variable `studentRecord` de contrôle de boucle pour voir son type de données.</span><span class="sxs-lookup"><span data-stu-id="4b924-149">Rest the mouse pointer over the loop control variable `studentRecord` to see its data type.</span></span> <span data-ttu-id="4b924-150">Le type de `studentRecord` est déduit comme `Student` étant, car `studentQuery` retourne une collection d' `Student` instances.</span><span class="sxs-lookup"><span data-stu-id="4b924-150">The type of `studentRecord` is inferred to be `Student`, because `studentQuery` returns a collection of `Student` instances.</span></span>

3. <span data-ttu-id="4b924-151">Générez et exécutez l’application en appuyant sur CTRL + F5.</span><span class="sxs-lookup"><span data-stu-id="4b924-151">Build and run the application by pressing CTRL+F5.</span></span> <span data-ttu-id="4b924-152">Notez les résultats dans la fenêtre de console.</span><span class="sxs-lookup"><span data-stu-id="4b924-152">Note the results in the console window.</span></span>

## <a name="modify-the-query"></a><span data-ttu-id="4b924-153">Modifier la requête</span><span class="sxs-lookup"><span data-stu-id="4b924-153">Modify the Query</span></span>

<span data-ttu-id="4b924-154">Il est plus facile d’analyser les résultats de la requête s’ils sont dans un ordre spécifié.</span><span class="sxs-lookup"><span data-stu-id="4b924-154">It is easier to scan query results if they are in a specified order.</span></span> <span data-ttu-id="4b924-155">Vous pouvez trier la séquence retournée en fonction de n’importe quel champ disponible.</span><span class="sxs-lookup"><span data-stu-id="4b924-155">You can sort the returned sequence based on any available field.</span></span>

### <a name="to-order-the-results"></a><span data-ttu-id="4b924-156">Pour classer les résultats</span><span class="sxs-lookup"><span data-stu-id="4b924-156">To order the results</span></span>

1. <span data-ttu-id="4b924-157">Ajoutez la `Order By` clause suivante entre l' `Where` instruction et l' `Select` instruction de la requête.</span><span class="sxs-lookup"><span data-stu-id="4b924-157">Add the following `Order By` clause between the `Where` statement and the `Select` statement of the query.</span></span> <span data-ttu-id="4b924-158">La `Order By` clause classe les résultats par ordre alphabétique de A à Z, en fonction du nom de famille de chaque étudiant.</span><span class="sxs-lookup"><span data-stu-id="4b924-158">The `Order By` clause will order the results alphabetically from A to Z, according to the last name of each student.</span></span>

    ```vb
    Order By currentStudent.Last Ascending
    ```

2. <span data-ttu-id="4b924-159">Pour classer par nom de famille, puis par prénom, ajoutez les deux champs à la requête :</span><span class="sxs-lookup"><span data-stu-id="4b924-159">To order by last name and then first name, add both fields to the query:</span></span>

    ```vb
    Order By currentStudent.Last Ascending, currentStudent.First Ascending
    ```

    <span data-ttu-id="4b924-160">Vous pouvez également spécifier l' `Descending` ordre de Z à A.</span><span class="sxs-lookup"><span data-stu-id="4b924-160">You can also specify `Descending` to order from Z to A.</span></span>

3. <span data-ttu-id="4b924-161">Générez et exécutez l’application en appuyant sur CTRL + F5.</span><span class="sxs-lookup"><span data-stu-id="4b924-161">Build and run the application by pressing CTRL+F5.</span></span> <span data-ttu-id="4b924-162">Notez les résultats dans la fenêtre de console.</span><span class="sxs-lookup"><span data-stu-id="4b924-162">Note the results in the console window.</span></span>

### <a name="to-introduce-a-local-identifier"></a><span data-ttu-id="4b924-163">Pour introduire un identificateur local</span><span class="sxs-lookup"><span data-stu-id="4b924-163">To introduce a local identifier</span></span>

1. <span data-ttu-id="4b924-164">Ajoutez le code dans cette section pour introduire un identificateur local dans l’expression de requête.</span><span class="sxs-lookup"><span data-stu-id="4b924-164">Add the code in this section to introduce a local identifier in the query expression.</span></span> <span data-ttu-id="4b924-165">L’identificateur local contiendra un résultat intermédiaire.</span><span class="sxs-lookup"><span data-stu-id="4b924-165">The local identifier will hold an intermediate result.</span></span> <span data-ttu-id="4b924-166">Dans l’exemple suivant, `name` est un identificateur qui contient une concaténation du prénom et du nom de l’étudiant.</span><span class="sxs-lookup"><span data-stu-id="4b924-166">In the following example, `name` is an identifier that holds a concatenation of the student's first and last names.</span></span> <span data-ttu-id="4b924-167">Un identificateur local peut être utilisé pour des raisons pratiques, ou il peut améliorer les performances en stockant les résultats d’une expression qui serait autrement calculée plusieurs fois.</span><span class="sxs-lookup"><span data-stu-id="4b924-167">A local identifier can be used for convenience, or it can enhance performance by storing the results of an expression that would otherwise be calculated multiple times.</span></span>

    [!code-vb[VbLINQWalkthrough#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQWalkthrough/VB/Class1.vb#4)]

2. <span data-ttu-id="4b924-168">Générez et exécutez l’application en appuyant sur CTRL + F5.</span><span class="sxs-lookup"><span data-stu-id="4b924-168">Build and run the application by pressing CTRL+F5.</span></span> <span data-ttu-id="4b924-169">Notez les résultats dans la fenêtre de console.</span><span class="sxs-lookup"><span data-stu-id="4b924-169">Note the results in the console window.</span></span>

### <a name="to-project-one-field-in-the-select-clause"></a><span data-ttu-id="4b924-170">Pour projeter un champ dans la clause SELECT</span><span class="sxs-lookup"><span data-stu-id="4b924-170">To project one field in the Select clause</span></span>

1. <span data-ttu-id="4b924-171">Ajoutez la requête et la `For Each` boucle à partir de cette section pour créer une requête qui produit une séquence dont les éléments diffèrent des éléments de la source.</span><span class="sxs-lookup"><span data-stu-id="4b924-171">Add the query and `For Each` loop from this section to create a query that produces a sequence whose elements differ from the elements in the source.</span></span> <span data-ttu-id="4b924-172">Dans l’exemple suivant, la source est une collection d' `Student` objets, mais un seul membre de chaque objet est retourné : le prénom des étudiants dont le nom est Garcia.</span><span class="sxs-lookup"><span data-stu-id="4b924-172">In the following example, the source is a collection of `Student` objects, but only one member of each object is returned: the first name of students whose last name is Garcia.</span></span> <span data-ttu-id="4b924-173">Étant donné que `currentStudent.First` est une chaîne, le type de données de la séquence retournée par `studentQuery3` est `IEnumerable(Of String)` , une séquence de chaînes.</span><span class="sxs-lookup"><span data-stu-id="4b924-173">Because `currentStudent.First` is a string, the data type of the sequence returned by `studentQuery3` is `IEnumerable(Of String)`, a sequence of strings.</span></span> <span data-ttu-id="4b924-174">Comme dans les exemples précédents, l’assignation d’un type de données pour `studentQuery3` est laissée au compilateur pour déterminer à l’aide de l’inférence de type local.</span><span class="sxs-lookup"><span data-stu-id="4b924-174">As in earlier examples, the assignment of a data type for `studentQuery3` is left for the compiler to determine by using local type inference.</span></span>

    [!code-vb[VbLINQWalkthrough#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQWalkthrough/VB/Class1.vb#5)]

2. <span data-ttu-id="4b924-175">Placez le pointeur de la souris au-dessus `studentQuery3` de votre code pour vérifier que le type affecté est `IEnumerable(Of String)` .</span><span class="sxs-lookup"><span data-stu-id="4b924-175">Rest the mouse pointer over `studentQuery3` in your code to verify that the assigned type is `IEnumerable(Of String)`.</span></span>

3. <span data-ttu-id="4b924-176">Générez et exécutez l’application en appuyant sur CTRL + F5.</span><span class="sxs-lookup"><span data-stu-id="4b924-176">Build and run the application by pressing CTRL+F5.</span></span> <span data-ttu-id="4b924-177">Notez les résultats dans la fenêtre de console.</span><span class="sxs-lookup"><span data-stu-id="4b924-177">Note the results in the console window.</span></span>

### <a name="to-create-an-anonymous-type-in-the-select-clause"></a><span data-ttu-id="4b924-178">Pour créer un type anonyme dans la clause SELECT</span><span class="sxs-lookup"><span data-stu-id="4b924-178">To create an anonymous type in the Select clause</span></span>

1. <span data-ttu-id="4b924-179">Ajoutez le code de cette section pour voir comment les types anonymes sont utilisés dans les requêtes.</span><span class="sxs-lookup"><span data-stu-id="4b924-179">Add the code from this section to see how anonymous types are used in queries.</span></span> <span data-ttu-id="4b924-180">Vous les utilisez dans des requêtes lorsque vous souhaitez retourner plusieurs champs de la source de données plutôt que des enregistrements complets ( `currentStudent` enregistrements dans des exemples précédents) ou des champs uniques ( `First` dans la section précédente).</span><span class="sxs-lookup"><span data-stu-id="4b924-180">You use them in queries when you want to return several fields from the data source rather than complete records (`currentStudent` records in previous examples) or single fields (`First` in the preceding section).</span></span> <span data-ttu-id="4b924-181">Au lieu de définir un nouveau type nommé qui contient les champs que vous souhaitez inclure dans le résultat, vous spécifiez les champs dans la `Select` clause et le compilateur crée un type anonyme avec ces champs comme propriétés.</span><span class="sxs-lookup"><span data-stu-id="4b924-181">Instead of defining a new named type that contains the fields you want to include in the result, you specify the fields in the `Select` clause and the compiler creates an anonymous type with those fields as its properties.</span></span> <span data-ttu-id="4b924-182">Pour plus d’informations, consultez [types anonymes](../../language-features/objects-and-classes/anonymous-types.md).</span><span class="sxs-lookup"><span data-stu-id="4b924-182">For more information, see [Anonymous Types](../../language-features/objects-and-classes/anonymous-types.md).</span></span>

    <span data-ttu-id="4b924-183">L’exemple suivant crée une requête qui retourne le nom et le rang de garantiront dont le classement universitaire est compris entre 1 et 10, par ordre de classement universitaire.</span><span class="sxs-lookup"><span data-stu-id="4b924-183">The following example creates a query that returns the name and rank of seniors whose academic rank is between 1 and 10, in order of academic rank.</span></span> <span data-ttu-id="4b924-184">Dans cet exemple, le type de `studentQuery4` doit être déduit, car la `Select` clause retourne une instance d’un type anonyme, et un type anonyme n’a pas de nom utilisable.</span><span class="sxs-lookup"><span data-stu-id="4b924-184">In this example, the type of `studentQuery4` must be inferred because the `Select` clause returns an instance of an anonymous type, and an anonymous type has no usable name.</span></span>

    [!code-vb[VbLINQWalkthrough#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQWalkthrough/VB/Class1.vb#6)]

2. <span data-ttu-id="4b924-185">Générez et exécutez l’application en appuyant sur CTRL + F5.</span><span class="sxs-lookup"><span data-stu-id="4b924-185">Build and run the application by pressing CTRL+F5.</span></span> <span data-ttu-id="4b924-186">Notez les résultats dans la fenêtre de console.</span><span class="sxs-lookup"><span data-stu-id="4b924-186">Note the results in the console window.</span></span>

## <a name="additional-examples"></a><span data-ttu-id="4b924-187">Autres exemples</span><span class="sxs-lookup"><span data-stu-id="4b924-187">Additional Examples</span></span>

<span data-ttu-id="4b924-188">Maintenant que vous comprenez les notions de base, voici une liste d’exemples supplémentaires pour illustrer la flexibilité et la puissance des requêtes LINQ.</span><span class="sxs-lookup"><span data-stu-id="4b924-188">Now that you understand the basics, the following is a list of additional examples to illustrate the flexibility and power of LINQ queries.</span></span> <span data-ttu-id="4b924-189">Chaque exemple est précédé d’une brève description de ce qu’il fait.</span><span class="sxs-lookup"><span data-stu-id="4b924-189">Each example is preceded by a brief description of what it does.</span></span> <span data-ttu-id="4b924-190">Placez le pointeur de la souris sur la variable de résultat de la requête pour chaque requête pour voir le type inféré.</span><span class="sxs-lookup"><span data-stu-id="4b924-190">Rest the mouse pointer over the query result variable for each query to see the inferred type.</span></span> <span data-ttu-id="4b924-191">Utilisez une `For Each` boucle pour produire les résultats.</span><span class="sxs-lookup"><span data-stu-id="4b924-191">Use a `For Each` loop to produce the results.</span></span>

[!code-vb[VbLINQWalkthrough#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQWalkthrough/VB/Class1.vb#7)]

## <a name="additional-information"></a><span data-ttu-id="4b924-192">Informations supplémentaires</span><span class="sxs-lookup"><span data-stu-id="4b924-192">Additional Information</span></span>

<span data-ttu-id="4b924-193">Une fois que vous êtes familiarisé avec les concepts de base de l’utilisation des requêtes, vous êtes prêt à lire la documentation et les exemples pour le type spécifique de fournisseur LINQ qui vous intéresse :</span><span class="sxs-lookup"><span data-stu-id="4b924-193">After you are familiar with the basic concepts of working with queries, you are ready to read the documentation and samples for the specific type of LINQ provider that you are interested in:</span></span>

- [<span data-ttu-id="4b924-194">LINQ to Objects</span><span class="sxs-lookup"><span data-stu-id="4b924-194">LINQ to Objects</span></span>](linq-to-objects.md)

- [<span data-ttu-id="4b924-195">LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="4b924-195">LINQ to SQL</span></span>](../../../../framework/data/adonet/sql/linq/index.md)

- [<span data-ttu-id="4b924-196">LINQ to XML</span><span class="sxs-lookup"><span data-stu-id="4b924-196">LINQ to XML</span></span>](../../../../standard/linq/linq-xml-overview.md)

- [<span data-ttu-id="4b924-197">LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="4b924-197">LINQ to DataSet</span></span>](../../../../framework/data/adonet/linq-to-dataset.md)

## <a name="see-also"></a><span data-ttu-id="4b924-198">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4b924-198">See also</span></span>

- [<span data-ttu-id="4b924-199">LINQ (Language-Integrated Query) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4b924-199">Language-Integrated Query (LINQ) (Visual Basic)</span></span>](index.md)
- [<span data-ttu-id="4b924-200">Mise en route de LINQ dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="4b924-200">Getting Started with LINQ in Visual Basic</span></span>](getting-started-with-linq.md)
- [<span data-ttu-id="4b924-201">Inférence de type local</span><span class="sxs-lookup"><span data-stu-id="4b924-201">Local Type Inference</span></span>](../../language-features/variables/local-type-inference.md)
- [<span data-ttu-id="4b924-202">Initialiseurs d'objets : types nommés et anonymes</span><span class="sxs-lookup"><span data-stu-id="4b924-202">Object Initializers: Named and Anonymous Types</span></span>](../../language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)
- [<span data-ttu-id="4b924-203">Types anonymes</span><span class="sxs-lookup"><span data-stu-id="4b924-203">Anonymous Types</span></span>](../../language-features/objects-and-classes/anonymous-types.md)
- [<span data-ttu-id="4b924-204">Introduction à LINQ en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="4b924-204">Introduction to LINQ in Visual Basic</span></span>](../../language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="4b924-205">LINQ</span><span class="sxs-lookup"><span data-stu-id="4b924-205">LINQ</span></span>](../../language-features/linq/index.md)
- [<span data-ttu-id="4b924-206">Requêtes</span><span class="sxs-lookup"><span data-stu-id="4b924-206">Queries</span></span>](../../../language-reference/queries/index.md)
