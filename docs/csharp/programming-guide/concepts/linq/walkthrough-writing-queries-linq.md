---
title: 'Procédure pas à pas : Écrire des requêtes en C# (LINQ)'
description: Cette procédure pas à pas montre comment les fonctionnalités du langage C# sont utilisées dans les expressions de requête LINQ. Cet article utilise Visual Studio comme environnement de développement.
ms.date: 07/20/2015
helpviewer_keywords:
- LINQ [C#], walkthroughs
- LINQ [C#], writing queries
- queries [LINQ in C#], writing
- writing LINQ queries
ms.assetid: 2962a610-419a-4276-9ec8-4b7f2af0c081
ms.openlocfilehash: d49cb725c9ce9a417f78f638795e98a75a086893
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87302215"
---
# <a name="walkthrough-writing-queries-in-c-linq"></a><span data-ttu-id="73c79-104">Procédure pas à pas : Écrire des requêtes en C# (LINQ)</span><span class="sxs-lookup"><span data-stu-id="73c79-104">Walkthrough: Writing Queries in C# (LINQ)</span></span>
<span data-ttu-id="73c79-105">Cette procédure pas à pas présente les fonctionnalités du langage C# utilisées pour écrire des expressions de requête LINQ.</span><span class="sxs-lookup"><span data-stu-id="73c79-105">This walkthrough demonstrates the C# language features that are used to write LINQ query expressions.</span></span>  
  
## <a name="create-a-c-project"></a><span data-ttu-id="73c79-106">Créer un projet C#</span><span class="sxs-lookup"><span data-stu-id="73c79-106">Create a C# Project</span></span>  
  
> [!NOTE]
> <span data-ttu-id="73c79-107">Les instructions suivantes s’appliquent à Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="73c79-107">The following instructions are for Visual Studio.</span></span> <span data-ttu-id="73c79-108">Si vous utilisez un environnement de développement différent, créez un projet console avec une référence à System.Core.dll et une directive `using` pour l’espace de noms <xref:System.Linq?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="73c79-108">If you are using a different development environment, create a console project with a reference to System.Core.dll and a `using` directive for the <xref:System.Linq?displayProperty=nameWithType> namespace.</span></span>  
  
#### <a name="to-create-a-project-in-visual-studio"></a><span data-ttu-id="73c79-109">Pour créer un projet dans Visual Studio</span><span class="sxs-lookup"><span data-stu-id="73c79-109">To create a project in Visual Studio</span></span>  
  
1. <span data-ttu-id="73c79-110">Démarrez Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="73c79-110">Start Visual Studio.</span></span>  
  
2. <span data-ttu-id="73c79-111">Dans le menu principal, sélectionnez **Fichier**, **Nouveau**, **Projet**.</span><span class="sxs-lookup"><span data-stu-id="73c79-111">On the menu bar, choose **File**, **New**, **Project**.</span></span>  
  
     <span data-ttu-id="73c79-112">La boîte de dialogue **Nouveau projet** s’affiche.</span><span class="sxs-lookup"><span data-stu-id="73c79-112">The **New Project** dialog box opens.</span></span>  
  
3. <span data-ttu-id="73c79-113">Développez **Installé**, **Modèles**, **Visual C#**, puis choisissez **Application console**.</span><span class="sxs-lookup"><span data-stu-id="73c79-113">Expand **Installed**, expand **Templates**, expand **Visual C#**, and then choose **Console Application**.</span></span>  
  
4. <span data-ttu-id="73c79-114">Dans la zone de texte **Nom**, entrez un nom différent ou acceptez le nom par défaut, puis choisissez le bouton **OK**.</span><span class="sxs-lookup"><span data-stu-id="73c79-114">In the **Name** text box, enter a different name or accept the default name, and then choose the **OK** button.</span></span>  
  
     <span data-ttu-id="73c79-115">Le nouveau projet s’affiche dans l’**Explorateur de solutions**.</span><span class="sxs-lookup"><span data-stu-id="73c79-115">The new project appears in **Solution Explorer**.</span></span>  
  
5. <span data-ttu-id="73c79-116">Notez que votre projet a une référence à System.Core.dll et une directive `using` pour l’espace de noms <xref:System.Linq?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="73c79-116">Notice that your project has a reference to System.Core.dll and a `using` directive for the <xref:System.Linq?displayProperty=nameWithType> namespace.</span></span>  
  
## <a name="create-an-in-memory-data-source"></a><span data-ttu-id="73c79-117">Créer une source de données en mémoire</span><span class="sxs-lookup"><span data-stu-id="73c79-117">Create an in-Memory Data Source</span></span>  
 <span data-ttu-id="73c79-118">La source de données pour les requêtes est une simple liste d’objets `Student`.</span><span class="sxs-lookup"><span data-stu-id="73c79-118">The data source for the queries is a simple list of `Student` objects.</span></span> <span data-ttu-id="73c79-119">Chaque enregistrement `Student` comporte un prénom, un nom et un tableau d’entiers représentant les notes d’examens en classe.</span><span class="sxs-lookup"><span data-stu-id="73c79-119">Each `Student` record has a first name, last name, and an array of integers that represents their test scores in the class.</span></span> <span data-ttu-id="73c79-120">Copiez ce code dans votre projet.</span><span class="sxs-lookup"><span data-stu-id="73c79-120">Copy this code into your project.</span></span> <span data-ttu-id="73c79-121">Notez les caractéristiques suivantes :</span><span class="sxs-lookup"><span data-stu-id="73c79-121">Note the following characteristics:</span></span>  
  
- <span data-ttu-id="73c79-122">La classe `Student` se compose de propriétés implémentées automatiquement.</span><span class="sxs-lookup"><span data-stu-id="73c79-122">The `Student` class consists of auto-implemented properties.</span></span>  
  
- <span data-ttu-id="73c79-123">Chaque étudiant de la liste est initialisé avec un initialiseur d’objet.</span><span class="sxs-lookup"><span data-stu-id="73c79-123">Each student in the list is initialized with an object initializer.</span></span>  
  
- <span data-ttu-id="73c79-124">La liste elle-même est initialisée avec un initialiseur de collection.</span><span class="sxs-lookup"><span data-stu-id="73c79-124">The list itself is initialized with a collection initializer.</span></span>  
  
 <span data-ttu-id="73c79-125">La totalité de cette structure de données est initialisée et instanciée sans appels explicites à un constructeur quelconque ni accès au membre explicite.</span><span class="sxs-lookup"><span data-stu-id="73c79-125">This whole data structure will be initialized and instantiated without explicit calls to any constructor or explicit member access.</span></span> <span data-ttu-id="73c79-126">Pour plus d’informations sur ces nouvelles fonctionnalités, consultez [Propriétés implémentées automatiquement](../../classes-and-structs/auto-implemented-properties.md) et [Initialiseurs d’objets et de collection](../../classes-and-structs/object-and-collection-initializers.md).</span><span class="sxs-lookup"><span data-stu-id="73c79-126">For more information about these new features, see [Auto-Implemented Properties](../../classes-and-structs/auto-implemented-properties.md) and [Object and Collection Initializers](../../classes-and-structs/object-and-collection-initializers.md).</span></span>  
  
#### <a name="to-add-the-data-source"></a><span data-ttu-id="73c79-127">Pour ajouter la source de données</span><span class="sxs-lookup"><span data-stu-id="73c79-127">To add the data source</span></span>  
  
- <span data-ttu-id="73c79-128">Ajoutez la classe `Student` et la liste initialisée d’étudiants à la classe `Program` dans votre projet.</span><span class="sxs-lookup"><span data-stu-id="73c79-128">Add the `Student` class and the initialized list of students to the `Program` class in your project.</span></span>  
  
     [!code-csharp[CsLinqGettingStarted#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#11)]  
  
#### <a name="to-add-a-new-student-to-the-students-list"></a><span data-ttu-id="73c79-129">Pour ajouter un nouvel étudiant à la liste des étudiants</span><span class="sxs-lookup"><span data-stu-id="73c79-129">To add a new Student to the Students list</span></span>  
  
1. <span data-ttu-id="73c79-130">Ajoutez un nouvel élément `Student` à la liste `Students` et utilisez le nom et les notes d’examens de votre choix.</span><span class="sxs-lookup"><span data-stu-id="73c79-130">Add a new `Student` to the `Students` list and use a name and test scores of your choice.</span></span> <span data-ttu-id="73c79-131">Essayez d’entrer toutes les informations relatives au nouvel étudiant pour mieux apprendre la syntaxe de l’initialiseur d’objet.</span><span class="sxs-lookup"><span data-stu-id="73c79-131">Try typing all the new student information in order to better learn the syntax for the object initializer.</span></span>  
  
## <a name="create-the-query"></a><span data-ttu-id="73c79-132">Créer la requête</span><span class="sxs-lookup"><span data-stu-id="73c79-132">Create the Query</span></span>  
  
#### <a name="to-create-a-simple-query"></a><span data-ttu-id="73c79-133">Pour créer une requête simple</span><span class="sxs-lookup"><span data-stu-id="73c79-133">To create a simple query</span></span>  
  
- <span data-ttu-id="73c79-134">Dans la méthode `Main` de l’application, créez une requête simple qui, quand elle est exécutée, produit une liste de tous les étudiants dont la note pour le premier test est supérieure à 90.</span><span class="sxs-lookup"><span data-stu-id="73c79-134">In the application's `Main` method, create a simple query that, when it is executed, will produce a list of all students whose score on the first test was greater than 90.</span></span> <span data-ttu-id="73c79-135">Notez que, puisque l’objet `Student` entier est sélectionné, le type de la requête est `IEnumerable<Student>`.</span><span class="sxs-lookup"><span data-stu-id="73c79-135">Note that because the whole `Student` object is selected, the type of the query is `IEnumerable<Student>`.</span></span> <span data-ttu-id="73c79-136">Bien que le code puisse également utiliser un type implicite à l’aide du mot clé [var](../../../language-reference/keywords/var.md), les types explicites sont utilisés pour illustrer clairement les résultats.</span><span class="sxs-lookup"><span data-stu-id="73c79-136">Although the code could also use implicit typing by using the [var](../../../language-reference/keywords/var.md) keyword, explicit typing is used to clearly illustrate results.</span></span> <span data-ttu-id="73c79-137">(Pour plus d’informations sur `var` , consultez [variables locales implicitement typées](../../classes-and-structs/implicitly-typed-local-variables.md).)</span><span class="sxs-lookup"><span data-stu-id="73c79-137">(For more information about `var`, see [Implicitly Typed Local Variables](../../classes-and-structs/implicitly-typed-local-variables.md).)</span></span>  
  
     <span data-ttu-id="73c79-138">Notez également que la variable de portée de la requête, `student`, sert de référence à chaque `Student` dans la source, en fournissant l’accès au membre pour chaque objet.</span><span class="sxs-lookup"><span data-stu-id="73c79-138">Note also that the query's range variable, `student`, serves as a reference to each `Student` in the source, providing member access for each object.</span></span>  
  
 [!code-csharp[CsLINQGettingStarted#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#12)]  
  
## <a name="execute-the-query"></a><span data-ttu-id="73c79-139">Exécuter la requête</span><span class="sxs-lookup"><span data-stu-id="73c79-139">Execute the Query</span></span>  
  
#### <a name="to-execute-the-query"></a><span data-ttu-id="73c79-140">Pour exécuter la requête</span><span class="sxs-lookup"><span data-stu-id="73c79-140">To execute the query</span></span>  
  
1. <span data-ttu-id="73c79-141">Écrivez maintenant la boucle `foreach` qui entraînera l’exécution de la requête.</span><span class="sxs-lookup"><span data-stu-id="73c79-141">Now write the `foreach` loop that will cause the query to execute.</span></span> <span data-ttu-id="73c79-142">Notez les points suivants concernant le code :</span><span class="sxs-lookup"><span data-stu-id="73c79-142">Note the following about the code:</span></span>  
  
    - <span data-ttu-id="73c79-143">Chaque élément de la séquence retournée est accessible via la variable d’itération dans la boucle `foreach`.</span><span class="sxs-lookup"><span data-stu-id="73c79-143">Each element in the returned sequence is accessed through the iteration variable in the `foreach` loop.</span></span>  
  
    - <span data-ttu-id="73c79-144">Le type de cette variable est `Student` et le type de la variable de requête est compatible, `IEnumerable<Student>`.</span><span class="sxs-lookup"><span data-stu-id="73c79-144">The type of this variable is `Student`, and the type of the query variable is compatible, `IEnumerable<Student>`.</span></span>  
  
2. <span data-ttu-id="73c79-145">Après avoir ajouté ce code, générez et exécutez l’application pour visualiser les résultats dans la fenêtre de **console**.</span><span class="sxs-lookup"><span data-stu-id="73c79-145">After you have added this code, build and run the application to see the results in the **Console** window.</span></span>  
  
 [!code-csharp[CsLINQGettingStarted#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#13)]  
  
#### <a name="to-add-another-filter-condition"></a><span data-ttu-id="73c79-146">Pour ajouter une autre condition de filtre</span><span class="sxs-lookup"><span data-stu-id="73c79-146">To add another filter condition</span></span>  
  
1. <span data-ttu-id="73c79-147">Vous pouvez associer plusieurs conditions booléennes dans la clause `where` pour affiner davantage une requête.</span><span class="sxs-lookup"><span data-stu-id="73c79-147">You can combine multiple Boolean conditions in the `where` clause in order to further refine a query.</span></span> <span data-ttu-id="73c79-148">Le code suivant ajoute une condition afin que la requête retourne les étudiants dont la première note est supérieure à 90 et dont la dernière est inférieure à 80.</span><span class="sxs-lookup"><span data-stu-id="73c79-148">The following code adds a condition so that the query returns those students whose first score was over 90 and whose last score was less than 80.</span></span> <span data-ttu-id="73c79-149">La clause `where` doit être semblable au code suivant.</span><span class="sxs-lookup"><span data-stu-id="73c79-149">The `where` clause should resemble the following code.</span></span>  
  
    ```csharp
    where student.Scores[0] > 90 && student.Scores[3] < 80  
    ```  
  
     <span data-ttu-id="73c79-150">Pour plus d’informations, consultez [where, clause](../../../language-reference/keywords/where-clause.md).</span><span class="sxs-lookup"><span data-stu-id="73c79-150">For more information, see [where clause](../../../language-reference/keywords/where-clause.md).</span></span>  
  
## <a name="modify-the-query"></a><span data-ttu-id="73c79-151">Modifier la requête</span><span class="sxs-lookup"><span data-stu-id="73c79-151">Modify the Query</span></span>  
  
#### <a name="to-order-the-results"></a><span data-ttu-id="73c79-152">Pour classer les résultats</span><span class="sxs-lookup"><span data-stu-id="73c79-152">To order the results</span></span>  
  
1. <span data-ttu-id="73c79-153">Il est plus facile d’analyser les résultats s’ils sont classés.</span><span class="sxs-lookup"><span data-stu-id="73c79-153">It will be easier to scan the results if they are in some kind of order.</span></span> <span data-ttu-id="73c79-154">Vous pouvez classer la séquence retournée selon tous les champs accessibles dans les éléments sources.</span><span class="sxs-lookup"><span data-stu-id="73c79-154">You can order the returned sequence by any accessible field in the source elements.</span></span> <span data-ttu-id="73c79-155">Par exemple, la clause `orderby` suivante classe les résultats dans l’ordre alphabétique de A à Z d’après le nom de chaque étudiant.</span><span class="sxs-lookup"><span data-stu-id="73c79-155">For example, the following `orderby` clause orders the results in alphabetical order from A to Z according to the last name of each student.</span></span> <span data-ttu-id="73c79-156">Ajoutez la clause `orderby` suivante à votre requête, juste après l’instruction `where` et avant l’instruction `select` :</span><span class="sxs-lookup"><span data-stu-id="73c79-156">Add the following `orderby` clause to your query, right after the `where` statement and before the `select` statement:</span></span>  
  
    ```csharp
    orderby student.Last ascending  
    ```  
  
2. <span data-ttu-id="73c79-157">Modifiez à présent la clause `orderby` pour qu’elle classe les résultats dans l’ordre inverse d’après la note au premier examen, de la plus élevée à la plus faible.</span><span class="sxs-lookup"><span data-stu-id="73c79-157">Now change the `orderby` clause so that it orders the results in reverse order according to the score on the first test, from the highest score to the lowest score.</span></span>  
  
    ```csharp
    orderby student.Scores[0] descending  
    ```  
  
3. <span data-ttu-id="73c79-158">Modifiez la chaîne de format `WriteLine` pour pouvoir consulter les notes :</span><span class="sxs-lookup"><span data-stu-id="73c79-158">Change the `WriteLine` format string so that you can see the scores:</span></span>  
  
    ```csharp
    Console.WriteLine("{0}, {1} {2}", student.Last, student.First, student.Scores[0]);  
    ```  
  
     <span data-ttu-id="73c79-159">Pour plus d’informations, consultez [orderby, clause](../../../language-reference/keywords/orderby-clause.md).</span><span class="sxs-lookup"><span data-stu-id="73c79-159">For more information, see [orderby clause](../../../language-reference/keywords/orderby-clause.md).</span></span>  
  
#### <a name="to-group-the-results"></a><span data-ttu-id="73c79-160">Pour regrouper les résultats</span><span class="sxs-lookup"><span data-stu-id="73c79-160">To group the results</span></span>  
  
1. <span data-ttu-id="73c79-161">Le regroupement est une fonction puissante des expressions de requête.</span><span class="sxs-lookup"><span data-stu-id="73c79-161">Grouping is a powerful capability in query expressions.</span></span> <span data-ttu-id="73c79-162">Une requête avec une clause group produit une séquence de groupes dont chaque groupe contient lui-même un élément `Key` et une séquence composée de tous les membres de ce groupe.</span><span class="sxs-lookup"><span data-stu-id="73c79-162">A query with a group clause produces a sequence of groups, and each group itself contains a `Key` and a sequence that consists of all the members of that group.</span></span> <span data-ttu-id="73c79-163">La nouvelle requête suivante regroupe les étudiants en utilisant la première lettre de leur nom comme clé.</span><span class="sxs-lookup"><span data-stu-id="73c79-163">The following new query groups the students by using the first letter of their last name as the key.</span></span>  
  
     [!code-csharp[CsLINQGettingStarted#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#14)]  
  
2. <span data-ttu-id="73c79-164">Notez que le type de la requête a maintenant changé.</span><span class="sxs-lookup"><span data-stu-id="73c79-164">Note that the type of the query has now changed.</span></span> <span data-ttu-id="73c79-165">Elle produit désormais une séquence de groupes qui ont un type `char` comme clé et une séquence d’objets `Student`.</span><span class="sxs-lookup"><span data-stu-id="73c79-165">It now produces a sequence of groups that have a `char` type as a key, and a sequence of `Student` objects.</span></span> <span data-ttu-id="73c79-166">Étant donné que le type de la requête a changé, le code suivant modifie également la boucle d’exécution `foreach` :</span><span class="sxs-lookup"><span data-stu-id="73c79-166">Because the type of the query has changed, the following code changes the `foreach` execution loop also:</span></span>  
  
     [!code-csharp[CsLINQGettingStarted#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#15)]  
  
3. <span data-ttu-id="73c79-167">Exécutez l’application et affichez les résultats dans la fenêtre de **console**.</span><span class="sxs-lookup"><span data-stu-id="73c79-167">Run the application and view the results in the **Console** window.</span></span>  
  
     <span data-ttu-id="73c79-168">Pour plus d’informations, consultez [Group, clause](../../../language-reference/keywords/group-clause.md).</span><span class="sxs-lookup"><span data-stu-id="73c79-168">For more information, see [group clause](../../../language-reference/keywords/group-clause.md).</span></span>  
  
#### <a name="to-make-the-variables-implicitly-typed"></a><span data-ttu-id="73c79-169">Pour rendre les variables implicitement typées</span><span class="sxs-lookup"><span data-stu-id="73c79-169">To make the variables implicitly typed</span></span>  
  
1. <span data-ttu-id="73c79-170">Le codage explicite de `IEnumerables` de `IGroupings` peut rapidement s’avérer laborieux.</span><span class="sxs-lookup"><span data-stu-id="73c79-170">Explicitly coding `IEnumerables` of `IGroupings` can quickly become tedious.</span></span> <span data-ttu-id="73c79-171">Vous pouvez écrire la même requête et la même boucle `foreach` beaucoup plus facilement à l’aide de `var`.</span><span class="sxs-lookup"><span data-stu-id="73c79-171">You can write the same query and `foreach` loop much more conveniently by using `var`.</span></span> <span data-ttu-id="73c79-172">Le mot clé `var` ne modifie pas les types de vos objets ; il indique simplement au compilateur de déduire les types.</span><span class="sxs-lookup"><span data-stu-id="73c79-172">The `var` keyword does not change the types of your objects; it just instructs the compiler to infer the types.</span></span> <span data-ttu-id="73c79-173">Remplacez le type de `studentQuery` et la variable d’itération `group` par `var` et réexécutez la requête.</span><span class="sxs-lookup"><span data-stu-id="73c79-173">Change the type of `studentQuery` and the iteration variable `group` to `var` and rerun the query.</span></span> <span data-ttu-id="73c79-174">Notez que, dans la boucle `foreach` interne, la variable d’itération est encore typée comme `Student` et que la requête fonctionne exactement comme précédemment.</span><span class="sxs-lookup"><span data-stu-id="73c79-174">Note that in the inner `foreach` loop, the iteration variable is still typed as `Student`, and the query works just as before.</span></span> <span data-ttu-id="73c79-175">Remplacez la variable d’itération `s` par `var` et exécutez à nouveau la requête.</span><span class="sxs-lookup"><span data-stu-id="73c79-175">Change the `s` iteration variable to `var` and run the query again.</span></span> <span data-ttu-id="73c79-176">Vous pouvez constater que les résultats obtenus sont exactement les mêmes.</span><span class="sxs-lookup"><span data-stu-id="73c79-176">You see that you get exactly the same results.</span></span>  
  
     [!code-csharp[CsLINQGettingStarted#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#16)]  
  
     <span data-ttu-id="73c79-177">Pour plus d’informations sur [var](../../../language-reference/keywords/var.md), consultez [Variables locales implicitement typées](../../classes-and-structs/implicitly-typed-local-variables.md).</span><span class="sxs-lookup"><span data-stu-id="73c79-177">For more information about [var](../../../language-reference/keywords/var.md), see [Implicitly Typed Local Variables](../../classes-and-structs/implicitly-typed-local-variables.md).</span></span>  
  
#### <a name="to-order-the-groups-by-their-key-value"></a><span data-ttu-id="73c79-178">Pour classer les groupes selon leur valeur de clé</span><span class="sxs-lookup"><span data-stu-id="73c79-178">To order the groups by their key value</span></span>  
  
1. <span data-ttu-id="73c79-179">Quand vous exécutez la requête précédente, vous remarquez que les groupes ne sont pas dans l’ordre alphabétique.</span><span class="sxs-lookup"><span data-stu-id="73c79-179">When you run the previous query, you notice that the groups are not in alphabetical order.</span></span> <span data-ttu-id="73c79-180">Pour modifier cet ordre, vous devez fournir une clause `orderby` après la clause `group`.</span><span class="sxs-lookup"><span data-stu-id="73c79-180">To change this, you must provide an `orderby` clause after the `group` clause.</span></span> <span data-ttu-id="73c79-181">Toutefois, pour utiliser une clause `orderby`, vous avez d’abord besoin d’un identificateur servant de référence aux groupes créés par la clause `group`.</span><span class="sxs-lookup"><span data-stu-id="73c79-181">But to use an `orderby` clause, you first need an identifier that serves as a reference to the groups created by the `group` clause.</span></span> <span data-ttu-id="73c79-182">Fournissez l’identificateur à l’aide du mot clé `into`, comme suit :</span><span class="sxs-lookup"><span data-stu-id="73c79-182">You provide the identifier by using the `into` keyword, as follows:</span></span>  
  
     [!code-csharp[csLINQGettingStarted#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#17)]  
  
     <span data-ttu-id="73c79-183">Quand vous exécutez cette requête, vous voyez que les groupes sont désormais classés par ordre alphabétique.</span><span class="sxs-lookup"><span data-stu-id="73c79-183">When you run this query, you will see the groups are now sorted in alphabetical order.</span></span>  
  
#### <a name="to-introduce-an-identifier-by-using-let"></a><span data-ttu-id="73c79-184">Pour introduire un identificateur à l’aide de let</span><span class="sxs-lookup"><span data-stu-id="73c79-184">To introduce an identifier by using let</span></span>  
  
1. <span data-ttu-id="73c79-185">Vous pouvez utiliser le mot clé `let` pour introduire un identificateur pour tous les résultats d’expression dans l’expression de requête.</span><span class="sxs-lookup"><span data-stu-id="73c79-185">You can use the `let` keyword to introduce an identifier for any expression result in the query expression.</span></span> <span data-ttu-id="73c79-186">Cet identificateur peut être pratique, comme dans l’exemple suivant, ou améliorer les performances en stockant les résultats d’une expression afin d’éviter qu’ils ne soient calculés plusieurs fois.</span><span class="sxs-lookup"><span data-stu-id="73c79-186">This identifier can be a convenience, as in the following example, or it can enhance performance by storing the results of an expression so that it does not have to be calculated multiple times.</span></span>  
  
     [!code-csharp[csLINQGettingStarted#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#18)]  
  
     <span data-ttu-id="73c79-187">Pour plus d’informations, consultez [let, clause](../../../language-reference/keywords/let-clause.md).</span><span class="sxs-lookup"><span data-stu-id="73c79-187">For more information, see [let clause](../../../language-reference/keywords/let-clause.md).</span></span>  
  
#### <a name="to-use-method-syntax-in-a-query-expression"></a><span data-ttu-id="73c79-188">Pour utiliser la syntaxe de méthode dans une expression de requête</span><span class="sxs-lookup"><span data-stu-id="73c79-188">To use method syntax in a query expression</span></span>  
  
1. <span data-ttu-id="73c79-189">Comme décrit dans [Syntaxe de requête et syntaxe de méthode dans LINQ](./query-syntax-and-method-syntax-in-linq.md), certaines opérations de requête peuvent être exprimées uniquement à l’aide de la syntaxe de méthode.</span><span class="sxs-lookup"><span data-stu-id="73c79-189">As described in [Query Syntax and Method Syntax in LINQ](./query-syntax-and-method-syntax-in-linq.md), some query operations can only be expressed by using method syntax.</span></span> <span data-ttu-id="73c79-190">Le code suivant calcule la note totale de chaque `Student` dans la séquence source, puis appelle la méthode `Average()` sur les résultats de cette requête pour calculer la note moyenne de la classe.</span><span class="sxs-lookup"><span data-stu-id="73c79-190">The following code calculates the total score for each `Student` in the source sequence, and then calls the `Average()` method on the results of that query to calculate the average score of the class.</span></span>
  
     [!code-csharp[csLINQGettingStarted#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#19)]  
  
#### <a name="to-transform-or-project-in-the-select-clause"></a><span data-ttu-id="73c79-191">Pour transformer ou projeter la clause select</span><span class="sxs-lookup"><span data-stu-id="73c79-191">To transform or project in the select clause</span></span>  
  
1. <span data-ttu-id="73c79-192">Il n’est pas rare qu’une requête produise une séquence dont les éléments diffèrent des éléments des séquences sources.</span><span class="sxs-lookup"><span data-stu-id="73c79-192">It is very common for a query to produce a sequence whose elements differ from the elements in the source sequences.</span></span> <span data-ttu-id="73c79-193">Supprimez ou commentez votre requête et votre boucle d’exécution précédentes, et remplacez-les par le code suivant.</span><span class="sxs-lookup"><span data-stu-id="73c79-193">Delete or comment out your previous query and execution loop, and replace it with the following code.</span></span> <span data-ttu-id="73c79-194">Notez que la requête retourne une séquence de chaînes (pas `Students`) et que ce fait est répercuté dans la boucle `foreach`.</span><span class="sxs-lookup"><span data-stu-id="73c79-194">Note that the query returns a sequence of strings (not `Students`), and this fact is reflected in the `foreach` loop.</span></span>  
  
     [!code-csharp[csLINQGettingStarted#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#20)]  
  
2. <span data-ttu-id="73c79-195">Le code utilisé précédemment dans cette procédure pas à pas indique que la note moyenne de la classe est d’environ 334.</span><span class="sxs-lookup"><span data-stu-id="73c79-195">Code earlier in this walkthrough indicated that the average class score is approximately 334.</span></span> <span data-ttu-id="73c79-196">Pour produire une séquence de `Students` dont la note totale est supérieure à la moyenne de classe, avec les `Student ID` correspondants, vous pouvez utiliser un type anonyme dans l’instruction `select` :</span><span class="sxs-lookup"><span data-stu-id="73c79-196">To produce a sequence of `Students` whose total score is greater than the class average, together with their `Student ID`, you can use an anonymous type in the `select` statement:</span></span>  
  
     [!code-csharp[csLINQGettingStarted#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#21)]  
  
## <a name="next-steps"></a><span data-ttu-id="73c79-197">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="73c79-197">Next Steps</span></span>  
 <span data-ttu-id="73c79-198">Une fois que vous êtes familiarisé avec les aspects de base de l’utilisation de requêtes en C#, vous êtes prêt à lire la documentation et les exemples pour le type spécifique de fournisseur LINQ qui vous intéresse :</span><span class="sxs-lookup"><span data-stu-id="73c79-198">After you are familiar with the basic aspects of working with queries in C#, you are ready to read the documentation and samples for the specific type of LINQ provider you are interested in:</span></span>  
  
 [<span data-ttu-id="73c79-199">LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="73c79-199">LINQ to SQL</span></span>](../../../../framework/data/adonet/sql/linq/index.md)  
  
 [<span data-ttu-id="73c79-200">LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="73c79-200">LINQ to DataSet</span></span>](../../../../framework/data/adonet/linq-to-dataset.md)  
  
 [<span data-ttu-id="73c79-201">LINQ to XML (C#)</span><span class="sxs-lookup"><span data-stu-id="73c79-201">LINQ to XML (C#)</span></span>](./linq-to-xml-overview.md)  
  
 [<span data-ttu-id="73c79-202">LINQ to Objects (C#)</span><span class="sxs-lookup"><span data-stu-id="73c79-202">LINQ to Objects (C#)</span></span>](./linq-to-objects.md)  
  
## <a name="see-also"></a><span data-ttu-id="73c79-203">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="73c79-203">See also</span></span>

- [<span data-ttu-id="73c79-204">LINQ (Language-Integrated Query) (C#)</span><span class="sxs-lookup"><span data-stu-id="73c79-204">Language-Integrated Query (LINQ) (C#)</span></span>](./index.md)
- [<span data-ttu-id="73c79-205">Expressions de requête LINQ</span><span class="sxs-lookup"><span data-stu-id="73c79-205">LINQ Query Expressions</span></span>](../../../linq/index.md)
