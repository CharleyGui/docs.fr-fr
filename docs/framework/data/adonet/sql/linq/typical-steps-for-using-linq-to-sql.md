---
title: Procédure standard d'utilisation de LINQ to SQL
ms.date: 03/30/2017
ms.assetid: 9a88bd51-bd74-48f7-a9b1-f650e8d55a3e
ms.openlocfilehash: dc8c4be1e895ee5c4c7947e6311e5bf71008490f
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91164258"
---
# <a name="typical-steps-for-using-linq-to-sql"></a><span data-ttu-id="36d00-102">Procédure standard d'utilisation de LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="36d00-102">Typical Steps for Using LINQ to SQL</span></span>

<span data-ttu-id="36d00-103">Pour implémenter une application [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], suivez les étapes décrites ultérieurement dans cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="36d00-103">To implement a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] application, you follow the steps described later in this topic.</span></span> <span data-ttu-id="36d00-104">Notez que de nombreuses étapes sont facultatives.</span><span class="sxs-lookup"><span data-stu-id="36d00-104">Note that many steps are optional.</span></span> <span data-ttu-id="36d00-105">Il est tout à fait possible que votre modèle objet soit utilisable dans son état par défaut.</span><span class="sxs-lookup"><span data-stu-id="36d00-105">It is very possible that you can use your object model in its default state.</span></span>  
  
 <span data-ttu-id="36d00-106">Pour un démarrage très rapide, utilisez la Concepteur Objet Relationnel pour créer votre modèle objet et commencez à coder vos requêtes.</span><span class="sxs-lookup"><span data-stu-id="36d00-106">For a really fast start, use the Object Relational Designer to create your object model and start coding your queries.</span></span>  
  
## <a name="creating-the-object-model"></a><span data-ttu-id="36d00-107">Création du modèle objet</span><span class="sxs-lookup"><span data-stu-id="36d00-107">Creating the Object Model</span></span>  

 <span data-ttu-id="36d00-108">La première étape consiste à créer un modèle objet à partir des métadonnées d'une base de données relationnelle existante.</span><span class="sxs-lookup"><span data-stu-id="36d00-108">The first step is to create an object model from the metadata of an existing relational database.</span></span> <span data-ttu-id="36d00-109">Le modèle objet représente la base de données en fonction du langage de programmation du développeur.</span><span class="sxs-lookup"><span data-stu-id="36d00-109">The object model represents the database according to the programming language of the developer.</span></span> <span data-ttu-id="36d00-110">Pour plus d’informations, consultez [le modèle objet LINQ to SQL](the-linq-to-sql-object-model.md).</span><span class="sxs-lookup"><span data-stu-id="36d00-110">For more information, see [The LINQ to SQL Object Model](the-linq-to-sql-object-model.md).</span></span>  
  
### <a name="1-select-a-tool-to-create-the-model"></a><span data-ttu-id="36d00-111">1. Sélectionnez un outil pour créer le modèle.</span><span class="sxs-lookup"><span data-stu-id="36d00-111">1. Select a tool to create the model.</span></span>  

 <span data-ttu-id="36d00-112">Trois outils sont disponibles pour la création du modèle.</span><span class="sxs-lookup"><span data-stu-id="36d00-112">Three tools are available for creating the model.</span></span>  
  
- <span data-ttu-id="36d00-113">Concepteur Objet Relationnel</span><span class="sxs-lookup"><span data-stu-id="36d00-113">The Object Relational Designer</span></span>  
  
     <span data-ttu-id="36d00-114">Ce concepteur fournit une interface utilisateur élaborée pour créer un modèle objet à partir d'une base de données existante.</span><span class="sxs-lookup"><span data-stu-id="36d00-114">This designer provides a rich user interface for creating an object model from an existing database.</span></span> <span data-ttu-id="36d00-115">Cet outil fait partie de l’IDE de Visual Studio et est mieux adapté aux bases de données de taille réduite ou moyenne.</span><span class="sxs-lookup"><span data-stu-id="36d00-115">This tool is part of the Visual Studio IDE, and is best suited to small or medium databases.</span></span>  
  
- <span data-ttu-id="36d00-116">Outil de génération de code SQLMetal</span><span class="sxs-lookup"><span data-stu-id="36d00-116">The SQLMetal code-generation tool</span></span>  
  
     <span data-ttu-id="36d00-117">Cet utilitaire de ligne de commande offre un ensemble d’options légèrement différent du Concepteur O/R.</span><span class="sxs-lookup"><span data-stu-id="36d00-117">This command-line utility provides a slightly different set of options from the O/R Designer.</span></span> <span data-ttu-id="36d00-118">Il est mieux adapté à la modélisation de grandes bases de données.</span><span class="sxs-lookup"><span data-stu-id="36d00-118">Modeling large databases is best done by using this tool.</span></span> <span data-ttu-id="36d00-119">Pour plus d’informations, consultez [SqlMetal.exe (outil de génération de code)](../../../../tools/sqlmetal-exe-code-generation-tool.md).</span><span class="sxs-lookup"><span data-stu-id="36d00-119">For more information, see [SqlMetal.exe (Code Generation Tool)](../../../../tools/sqlmetal-exe-code-generation-tool.md).</span></span>  
  
- <span data-ttu-id="36d00-120">Éditeur de code</span><span class="sxs-lookup"><span data-stu-id="36d00-120">A code editor</span></span>  
  
     <span data-ttu-id="36d00-121">Vous pouvez écrire votre propre code à l’aide de l’éditeur de code Visual Studio ou d’un autre éditeur.</span><span class="sxs-lookup"><span data-stu-id="36d00-121">You can write your own code by using either the Visual Studio code editor or another editor.</span></span> <span data-ttu-id="36d00-122">Nous déconseillons cette approche, qui peut être sujette à des erreurs, lorsque vous disposez d’une base de données existante et que vous pouvez utiliser le Concepteur O/R ou l’outil SQLMetal.</span><span class="sxs-lookup"><span data-stu-id="36d00-122">We do not recommend this approach, which can be prone to errors, when you have an existing database and can use either the O/R Designer or the SQLMetal tool.</span></span> <span data-ttu-id="36d00-123">Toutefois, l'éditeur de code peut s'avérer particulièrement utile pour affiner ou modifier du code déjà généré à l'aide d'autres outils.</span><span class="sxs-lookup"><span data-stu-id="36d00-123">However, the code editor can be valuable for refining or modifying code you have already generated by using other tools.</span></span> <span data-ttu-id="36d00-124">Pour plus d’informations, consultez [Comment : personnaliser des classes d’entité à l’aide de l’éditeur de code](how-to-customize-entity-classes-by-using-the-code-editor.md).</span><span class="sxs-lookup"><span data-stu-id="36d00-124">For more information, see [How to: Customize Entity Classes by Using the Code Editor](how-to-customize-entity-classes-by-using-the-code-editor.md).</span></span>  
  
### <a name="2-select-the-kind-of-code-you-want-to-generate"></a><span data-ttu-id="36d00-125">2. Sélectionnez le type de code que vous souhaitez générer.</span><span class="sxs-lookup"><span data-stu-id="36d00-125">2. Select the kind of code you want to generate.</span></span>  
  
- <span data-ttu-id="36d00-126">Fichier de code source C# ou Visual Basic pour le mappage basé sur les attributs.</span><span class="sxs-lookup"><span data-stu-id="36d00-126">A C# or Visual Basic source code file for attribute-based mapping.</span></span>  
  
     <span data-ttu-id="36d00-127">Vous incluez ensuite ce fichier de code dans votre projet Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="36d00-127">You then include this code file in your Visual Studio project.</span></span> <span data-ttu-id="36d00-128">Pour plus d’informations, consultez [mappage basé sur les attributs](attribute-based-mapping.md).</span><span class="sxs-lookup"><span data-stu-id="36d00-128">For more information, see [Attribute-Based Mapping](attribute-based-mapping.md).</span></span>  
  
- <span data-ttu-id="36d00-129">Fichier XML pour le mappage externe.</span><span class="sxs-lookup"><span data-stu-id="36d00-129">An XML file for external mapping.</span></span>  
  
     <span data-ttu-id="36d00-130">Cette approche vous permet de maintenir les métadonnées de mappage en dehors de votre code d'application.</span><span class="sxs-lookup"><span data-stu-id="36d00-130">By using this approach, you can keep the mapping metadata out of your application code.</span></span> <span data-ttu-id="36d00-131">Pour plus d’informations, consultez [mappage externe](external-mapping.md).</span><span class="sxs-lookup"><span data-stu-id="36d00-131">For more information, see [External Mapping](external-mapping.md).</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="36d00-132">Le Concepteur O/R ne prend pas en charge la génération de fichiers de mappage externes.</span><span class="sxs-lookup"><span data-stu-id="36d00-132">The O/R Designer does not support the generation of external mapping files.</span></span> <span data-ttu-id="36d00-133">Vous devez utiliser l'outil SQLMetal pour implémenter cette fonctionnalité.</span><span class="sxs-lookup"><span data-stu-id="36d00-133">You must use the SQLMetal tool to implement this feature.</span></span>  
  
- <span data-ttu-id="36d00-134">Un fichier DBML, que vous pouvez modifier avant de générer un fichier de code final.</span><span class="sxs-lookup"><span data-stu-id="36d00-134">A DBML file, which you can modify before generating a final code file.</span></span>  
  
     <span data-ttu-id="36d00-135">Il s'agit d'une fonctionnalité avancée.</span><span class="sxs-lookup"><span data-stu-id="36d00-135">This is an advanced feature.</span></span>  
  
### <a name="3-refine-the-code-file-to-reflect-the-needs-of-your-application"></a><span data-ttu-id="36d00-136">3. affinez le fichier de code pour refléter les besoins de votre application.</span><span class="sxs-lookup"><span data-stu-id="36d00-136">3. Refine the code file to reflect the needs of your application.</span></span>  

 <span data-ttu-id="36d00-137">À cet effet, vous pouvez utiliser le Concepteur O/R ou l’éditeur de code.</span><span class="sxs-lookup"><span data-stu-id="36d00-137">For this purpose, you can use either the O/R Designer or the code editor.</span></span>  
  
## <a name="using-the-object-model"></a><span data-ttu-id="36d00-138">Utilisation du modèle objet</span><span class="sxs-lookup"><span data-stu-id="36d00-138">Using the Object Model</span></span>  

 <span data-ttu-id="36d00-139">L'illustration suivante montre la relation entre le développeur et les données dans un scénario à deux niveaux.</span><span class="sxs-lookup"><span data-stu-id="36d00-139">The following illustration shows the relationship between the developer and the data in a two-tier scenario.</span></span> <span data-ttu-id="36d00-140">Pour d’autres scénarios, consultez [applications multicouches et distantes avec LINQ to SQL](n-tier-and-remote-applications-with-linq-to-sql.md).</span><span class="sxs-lookup"><span data-stu-id="36d00-140">For other scenarios, see [N-Tier and Remote Applications with LINQ to SQL](n-tier-and-remote-applications-with-linq-to-sql.md).</span></span>  
  
 ![Capture d’écran qui montre le modèle d’objet LINQ.](./media/the-linq-to-sql-object-model/linq-object-model-two-tier.png)  
  
 <span data-ttu-id="36d00-142">Maintenant que vous disposez du modèle objet, vous pouvez décrire les demandes d'informations et manipuler des données dans ce modèle.</span><span class="sxs-lookup"><span data-stu-id="36d00-142">Now that you have the object model, you describe information requests and manipulate data within that model.</span></span> <span data-ttu-id="36d00-143">Pensez en termes d'objets et de propriétés dans votre modèle objet et non pas en termes de lignes et de colonnes de la base de données.</span><span class="sxs-lookup"><span data-stu-id="36d00-143">You think in terms of the objects and properties in your object model and not in terms of the rows and columns of the database.</span></span> <span data-ttu-id="36d00-144">Vous ne traitez pas directement avec la base de données.</span><span class="sxs-lookup"><span data-stu-id="36d00-144">You do not deal directly with the database.</span></span>  
  
 <span data-ttu-id="36d00-145">Lorsque vous demandez [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] à d’exécuter une requête que vous avez décrite ou `SubmitChanges()` d’appeler sur les données que vous avez manipulées, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] communique avec la base de données dans la langue de la base de données.</span><span class="sxs-lookup"><span data-stu-id="36d00-145">When you instruct [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] to either execute a query that you have described or call `SubmitChanges()` on data that you have manipulated, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] communicates with the database in the language of the database.</span></span>  
  
 <span data-ttu-id="36d00-146">La procédure standard d'utilisation du modèle objet créé est présentée ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="36d00-146">The following represents typical steps for using the object model that you have created.</span></span>  
  
### <a name="1-create-queries-to-retrieve-information-from-the-database"></a><span data-ttu-id="36d00-147">1. Créez des requêtes pour récupérer des informations de la base de données.</span><span class="sxs-lookup"><span data-stu-id="36d00-147">1. Create queries to retrieve information from the database.</span></span>  

 <span data-ttu-id="36d00-148">Pour plus d’informations, consultez [concepts de requête](query-concepts.md) et exemples de [requêtes](query-examples.md).</span><span class="sxs-lookup"><span data-stu-id="36d00-148">For more information, see [Query Concepts](query-concepts.md) and [Query Examples](query-examples.md).</span></span>  
  
### <a name="2-override-default-behaviors-for-insert-update-and-delete"></a><span data-ttu-id="36d00-149">2. Remplacez les comportements par défaut pour l’insertion, la mise à jour et la suppression.</span><span class="sxs-lookup"><span data-stu-id="36d00-149">2. Override default behaviors for Insert, Update, and Delete.</span></span>  

 <span data-ttu-id="36d00-150">Cette étape est facultative.</span><span class="sxs-lookup"><span data-stu-id="36d00-150">This step is optional.</span></span> <span data-ttu-id="36d00-151">Pour plus d’informations, consultez [Personnalisation des opérations d’insertion, de mise à jour et de suppression](customizing-insert-update-and-delete-operations.md).</span><span class="sxs-lookup"><span data-stu-id="36d00-151">For more information, see [Customizing Insert, Update, and Delete Operations](customizing-insert-update-and-delete-operations.md).</span></span>  
  
### <a name="3-set-appropriate-options-to-detect-and-report-concurrency-conflicts"></a><span data-ttu-id="36d00-152">3. Définissez les options appropriées pour détecter et signaler les conflits d’accès concurrentiel.</span><span class="sxs-lookup"><span data-stu-id="36d00-152">3. Set appropriate options to detect and report concurrency conflicts.</span></span>  

 <span data-ttu-id="36d00-153">Vous pouvez conserver les valeurs par défaut de votre modèle pour la gestion des conflits d'accès concurrentiel ou les adapter à vos besoins.</span><span class="sxs-lookup"><span data-stu-id="36d00-153">You can leave your model with its default values for handling concurrency conflicts, or you can change it to suit your purposes.</span></span> <span data-ttu-id="36d00-154">Pour plus d’informations, consultez [Comment : spécifier les membres qui sont testés pour les conflits d’accès concurrentiel](how-to-specify-which-members-are-tested-for-concurrency-conflicts.md) et [Comment : spécifier le moment où des exceptions d’accès concurrentiel sont levées](how-to-specify-when-concurrency-exceptions-are-thrown.md).</span><span class="sxs-lookup"><span data-stu-id="36d00-154">For more information, see [How to: Specify Which Members are Tested for Concurrency Conflicts](how-to-specify-which-members-are-tested-for-concurrency-conflicts.md) and [How to: Specify When Concurrency Exceptions are Thrown](how-to-specify-when-concurrency-exceptions-are-thrown.md).</span></span>  
  
### <a name="4-establish-an-inheritance-hierarchy"></a><span data-ttu-id="36d00-155">4. établissez une hiérarchie d’héritage.</span><span class="sxs-lookup"><span data-stu-id="36d00-155">4. Establish an inheritance hierarchy.</span></span>  

 <span data-ttu-id="36d00-156">Cette étape est facultative.</span><span class="sxs-lookup"><span data-stu-id="36d00-156">This step is optional.</span></span> <span data-ttu-id="36d00-157">Pour plus d’informations, consultez [prise en charge de l’héritage](inheritance-support.md).</span><span class="sxs-lookup"><span data-stu-id="36d00-157">For more information, see [Inheritance Support](inheritance-support.md).</span></span>  
  
### <a name="5-provide-an-appropriate-user-interface"></a><span data-ttu-id="36d00-158">5. fournissez une interface utilisateur appropriée.</span><span class="sxs-lookup"><span data-stu-id="36d00-158">5. Provide an appropriate user interface.</span></span>  

 <span data-ttu-id="36d00-159">Cette étape est facultative et dépend de l'utilisation ultérieure de votre application.</span><span class="sxs-lookup"><span data-stu-id="36d00-159">This step is optional, and depends on how your application will be used.</span></span>  
  
### <a name="6-debug-and-test-your-application"></a><span data-ttu-id="36d00-160">6. déboguez et testez votre application.</span><span class="sxs-lookup"><span data-stu-id="36d00-160">6. Debug and test your application.</span></span>  

 <span data-ttu-id="36d00-161">Pour plus d’informations, consultez [prise en charge du débogage](debugging-support.md).</span><span class="sxs-lookup"><span data-stu-id="36d00-161">For more information, see [Debugging Support](debugging-support.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="36d00-162">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="36d00-162">See also</span></span>

- [<span data-ttu-id="36d00-163">Prise en main</span><span class="sxs-lookup"><span data-stu-id="36d00-163">Getting Started</span></span>](getting-started.md)
- [<span data-ttu-id="36d00-164">Création du modèle objet</span><span class="sxs-lookup"><span data-stu-id="36d00-164">Creating the Object Model</span></span>](creating-the-object-model.md)
- [<span data-ttu-id="36d00-165">Procédures stockées</span><span class="sxs-lookup"><span data-stu-id="36d00-165">Stored Procedures</span></span>](stored-procedures.md)
