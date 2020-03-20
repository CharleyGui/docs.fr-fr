---
title: 'Comment : appeler des fonctions de base de données personnalisées'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 4354e5eb-dd45-469d-97fb-1c495705ee59
ms.openlocfilehash: f3177ab98382506770c4655c62573da5c1d96c69
ms.sourcegitcommit: 515469828d0f040e01bde01df6b8e4eb43630b06
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/06/2020
ms.locfileid: "78848754"
---
# <a name="how-to-call-custom-database-functions"></a><span data-ttu-id="27b77-102">Comment : appeler des fonctions de base de données personnalisées</span><span class="sxs-lookup"><span data-stu-id="27b77-102">How to: Call Custom Database Functions</span></span>

<span data-ttu-id="27b77-103">Cette rubrique décrit comment appeler des fonctions personnalisées définies dans la base de données dans des requêtes LINQ to Entities.</span><span class="sxs-lookup"><span data-stu-id="27b77-103">This topic describes how to call custom functions that are defined in the database from within LINQ to Entities queries.</span></span>

<span data-ttu-id="27b77-104">Les fonctions de base de données qui sont appelées à partir de requêtes LINQ to Entities sont exécutées dans la base de données.</span><span class="sxs-lookup"><span data-stu-id="27b77-104">Database functions that are called from LINQ to Entities queries are executed in the database.</span></span> <span data-ttu-id="27b77-105">L'exécution de fonctions dans la base de données peut améliorer les performances de l'application.</span><span class="sxs-lookup"><span data-stu-id="27b77-105">Executing functions in the database can improve application performance.</span></span>

<span data-ttu-id="27b77-106">La procédure ci-dessous fournit un plan de haut niveau pour l'appel d'une fonction de base de données personnalisée.</span><span class="sxs-lookup"><span data-stu-id="27b77-106">The procedure below provides a high-level outline for calling a custom database function.</span></span> <span data-ttu-id="27b77-107">L'exemple qui suit fournit plus de détails sur les étapes de la procédure.</span><span class="sxs-lookup"><span data-stu-id="27b77-107">The example that follows provides more detail about the steps in the procedure.</span></span>

## <a name="to-call-custom-functions-that-are-defined-in-the-database"></a><span data-ttu-id="27b77-108">Pour appeler des fonctions personnalisées définies dans la base de données</span><span class="sxs-lookup"><span data-stu-id="27b77-108">To call custom functions that are defined in the database</span></span>

1. <span data-ttu-id="27b77-109">Créez une fonction personnalisée dans votre base de données.</span><span class="sxs-lookup"><span data-stu-id="27b77-109">Create a custom function in your database.</span></span>

     <span data-ttu-id="27b77-110">Pour plus d’informations sur la création de fonctions personnalisées dans SQL Server, voir [CREATE FUNCTION (Transact-SQL)](/sql/t-sql/statements/create-function-transact-sql).</span><span class="sxs-lookup"><span data-stu-id="27b77-110">For more information about creating custom functions in SQL Server, see [CREATE FUNCTION (Transact-SQL)](/sql/t-sql/statements/create-function-transact-sql).</span></span>

2. <span data-ttu-id="27b77-111">Déclarez une fonction dans la partie SSDL (Store Schema Definition Language) de votre fichier .edmx.</span><span class="sxs-lookup"><span data-stu-id="27b77-111">Declare a function in the store schema definition language (SSDL) of your .edmx file.</span></span> <span data-ttu-id="27b77-112">Le nom de la fonction doit être le même que le nom de la fonction déclarée dans la base de données.</span><span class="sxs-lookup"><span data-stu-id="27b77-112">The name of the function must be the same as the name of the function declared in the database.</span></span>

     <span data-ttu-id="27b77-113">Pour plus d’informations, voir [Élément fonction fonction (SSDL)](/ef/ef6/modeling/designer/advanced/edmx/ssdl-spec#function-element-ssdl).</span><span class="sxs-lookup"><span data-stu-id="27b77-113">For more information, see [Function Element (SSDL)](/ef/ef6/modeling/designer/advanced/edmx/ssdl-spec#function-element-ssdl).</span></span>

3. <span data-ttu-id="27b77-114">Ajoutez une méthode correspondante à une classe dans votre code d'application et appliquez un attribut <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute> à la méthode. Notez que les paramètres <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.NamespaceName%2A> et <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.FunctionName%2A> de l'attribut sont respectivement le nom de l'espace de noms du modèle conceptuel et le nom de la fonction dans le modèle conceptuel.</span><span class="sxs-lookup"><span data-stu-id="27b77-114">Add a corresponding method to a class in your application code and apply a <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute> to the method Note that the <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.NamespaceName%2A> and <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.FunctionName%2A> parameters of the attribute are the namespace name of the conceptual model and the function name in the conceptual model respectively.</span></span> <span data-ttu-id="27b77-115">La résolution des noms de fonctions pour LINQ respecte la casse.</span><span class="sxs-lookup"><span data-stu-id="27b77-115">Function name resolution for LINQ is case sensitive.</span></span>

4. <span data-ttu-id="27b77-116">Appelez la méthode dans une requête LINQ to Entities.</span><span class="sxs-lookup"><span data-stu-id="27b77-116">Call the method in a LINQ to Entities query.</span></span>  

## <a name="example"></a><span data-ttu-id="27b77-117"> Exemple</span><span class="sxs-lookup"><span data-stu-id="27b77-117">Example</span></span>

<span data-ttu-id="27b77-118">L'exemple suivant montre comment appeler une fonction de base de données personnalisée dans une requête LINQ to Entities.</span><span class="sxs-lookup"><span data-stu-id="27b77-118">The following example demonstrates how to call a custom database function from within a LINQ to Entities query.</span></span> <span data-ttu-id="27b77-119">L'exemple utilise le modèle School.</span><span class="sxs-lookup"><span data-stu-id="27b77-119">The example uses the School model.</span></span> <span data-ttu-id="27b77-120">Pour plus d’informations sur le modèle de l’école, voir [Créer la base de données sur les échantillons scolaires](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399731(v=vs.100)) et générer le fichier [.edmx de l’école](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399739(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="27b77-120">For information about the School model, see [Creating the School Sample Database](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399731(v=vs.100)) and [Generating the School .edmx File](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399739(v=vs.100)).</span></span>

<span data-ttu-id="27b77-121">Le code suivant ajoute la fonction `AvgStudentGrade` à l'exemple de base de données School.</span><span class="sxs-lookup"><span data-stu-id="27b77-121">The following code adds the `AvgStudentGrade` function to the School sample database.</span></span>

> [!NOTE]
> <span data-ttu-id="27b77-122">La procédure d'appel d'une fonction de base de données personnalisée est la même indépendamment du serveur de base de données.</span><span class="sxs-lookup"><span data-stu-id="27b77-122">The steps for calling a custom database function are the same regardless of the database server.</span></span> <span data-ttu-id="27b77-123">Toutefois, le code ci-dessous est spécifique à la création d'une fonction dans une base de données SQL Server.</span><span class="sxs-lookup"><span data-stu-id="27b77-123">However, the code below is specific to creating a function in a SQL Server database.</span></span> <span data-ttu-id="27b77-124">Le code pour la création d'une fonction personnalisée sur d'autres serveurs de bases de données peut différer.</span><span class="sxs-lookup"><span data-stu-id="27b77-124">The code for creating a custom function in other database servers might differ.</span></span>

[!code-sql[DP L2E MapToDBFunction#1](~/samples/snippets/tsql/VS_Snippets_Data/dp l2e maptodbfunction/tsql/create_avgstudentgrade.sql#1)]

## <a name="example"></a><span data-ttu-id="27b77-125"> Exemple</span><span class="sxs-lookup"><span data-stu-id="27b77-125">Example</span></span>

<span data-ttu-id="27b77-126">Ensuite, déclarez une fonction dans le langage de définition du schéma de magasin (SSDL) de votre fichier *.edmx.*</span><span class="sxs-lookup"><span data-stu-id="27b77-126">Next, declare a function in the store schema definition language (SSDL) of your *.edmx* file.</span></span> <span data-ttu-id="27b77-127">Le code suivant `AvgStudentGrade` déclare la fonction dans SSDL :</span><span class="sxs-lookup"><span data-stu-id="27b77-127">The following code declares the `AvgStudentGrade` function in SSDL:</span></span>

[!code-xml[DP L2E MapToDBFunction#2](~/samples/snippets/csharp/VS_Snippets_Data/dp l2e maptodbfunction/cs/school.edmx#2)]

## <a name="example"></a><span data-ttu-id="27b77-128"> Exemple</span><span class="sxs-lookup"><span data-stu-id="27b77-128">Example</span></span>

<span data-ttu-id="27b77-129">Maintenant, créez une méthode et cartographiez-la à la fonction déclarée dans le SSDL.</span><span class="sxs-lookup"><span data-stu-id="27b77-129">Now, create a method and map it to the function declared in the SSDL.</span></span> <span data-ttu-id="27b77-130">La méthode dans la classe suivante est mappée à la fonction définie dans le langage SSDL (ci-dessus) à l'aide d'un attribut <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute>.</span><span class="sxs-lookup"><span data-stu-id="27b77-130">The method in the following class is mapped to the function defined in the SSDL (above) by using an <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute>.</span></span> <span data-ttu-id="27b77-131">Lorsque cette méthode est appelée, la fonction correspondante dans la base de données est exécutée.</span><span class="sxs-lookup"><span data-stu-id="27b77-131">When this method is called, the corresponding function in the database is executed.</span></span>

[!code-csharp[DP L2E MapToDBFunction#3](~/samples/snippets/csharp/VS_Snippets_Data/dp l2e maptodbfunction/cs/program.cs#3)]
[!code-vb[DP L2E MapToDBFunction#3](~/samples/snippets/visualbasic/VS_Snippets_Data/dp l2e maptodbfunction/vb/module1.vb#3)]

## <a name="example"></a><span data-ttu-id="27b77-132"> Exemple</span><span class="sxs-lookup"><span data-stu-id="27b77-132">Example</span></span>

<span data-ttu-id="27b77-133">Enfin, appelez la méthode dans une requête LINQ to Entities.</span><span class="sxs-lookup"><span data-stu-id="27b77-133">Finally, call the method in a LINQ to Entities query.</span></span> <span data-ttu-id="27b77-134">Le code suivant affiche le nom des étudiants et la moyenne des notes sur la console :</span><span class="sxs-lookup"><span data-stu-id="27b77-134">The following code displays students' last names and average grades to the console:</span></span>

[!code-csharp[DP L2E MapToDBFunction#4](~/samples/snippets/csharp/VS_Snippets_Data/dp l2e maptodbfunction/cs/program.cs#4)]
[!code-vb[DP L2E MapToDBFunction#4](~/samples/snippets/visualbasic/VS_Snippets_Data/dp l2e maptodbfunction/vb/module1.vb#4)]

## <a name="see-also"></a><span data-ttu-id="27b77-135">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="27b77-135">See also</span></span>

- <span data-ttu-id="27b77-136">[Présentation d'un fichier .edmx](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc982042(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="27b77-136">[.edmx File Overview](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc982042(v=vs.100))</span></span>
- [<span data-ttu-id="27b77-137">Requêtes dans LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="27b77-137">Queries in LINQ to Entities</span></span>](queries-in-linq-to-entities.md)
