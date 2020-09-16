---
title: 'Procédure : Générer le modèle objet en Visual Basic ou en C#'
ms.date: 03/30/2017
ms.assetid: a0c73b33-5650-420c-b9dc-f49310c201ee
ms.openlocfilehash: e2491cf18be556cb26f084a178b7bf09448c6904
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90546612"
---
# <a name="how-to-generate-the-object-model-in-visual-basic-or-c"></a><span data-ttu-id="d9442-102">Comment : générer le modèle objet dans Visual Basic ou C\#</span><span class="sxs-lookup"><span data-stu-id="d9442-102">How to: Generate the Object Model in Visual Basic or C\#</span></span>
<span data-ttu-id="d9442-103">Dans [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], un modèle objet dans votre propre langage de programmation est mappé à une base de données relationnelle.</span><span class="sxs-lookup"><span data-stu-id="d9442-103">In [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], an object model in your own programming language is mapped to a relational database.</span></span> <span data-ttu-id="d9442-104">Deux outils sont disponibles pour générer automatiquement un modèle Visual Basic ou C# à partir des métadonnées d’une base de données existante.</span><span class="sxs-lookup"><span data-stu-id="d9442-104">Two tools are available for automatically generating a Visual Basic or C# model from the metadata of an existing database.</span></span>  
  
- <span data-ttu-id="d9442-105">Si vous utilisez Visual Studio, vous pouvez utiliser la Concepteur Objet Relationnel pour générer un modèle objet.</span><span class="sxs-lookup"><span data-stu-id="d9442-105">If you are using Visual Studio, you can use the Object Relational Designer to generate an object model.</span></span> <span data-ttu-id="d9442-106">Le Concepteur O/R fournit une interface utilisateur riche pour vous aider à générer un [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] modèle d’objet.</span><span class="sxs-lookup"><span data-stu-id="d9442-106">The O/R Designer provides a rich user interface to help you generate a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] object model.</span></span> <span data-ttu-id="d9442-107">Pour plus d’informations, consultez [Outils LINQ to SQL dans Visual Studio](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2).</span><span class="sxs-lookup"><span data-stu-id="d9442-107">For more information see, [Linq to SQL Tools in Visual Studio](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2).</span></span>
  
- <span data-ttu-id="d9442-108">Outil en ligne de commande SQLMetal</span><span class="sxs-lookup"><span data-stu-id="d9442-108">The SQLMetal command-line tool.</span></span> <span data-ttu-id="d9442-109">Pour plus d’informations, consultez [SqlMetal.exe (outil de génération de code)](../../../../tools/sqlmetal-exe-code-generation-tool.md).</span><span class="sxs-lookup"><span data-stu-id="d9442-109">For more information, see [SqlMetal.exe (Code Generation Tool)](../../../../tools/sqlmetal-exe-code-generation-tool.md).</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="d9442-110">Si vous ne possédez pas de base de données existante et que vous souhaitez en créer une à partir d'un modèle objet, vous pouvez utiliser votre éditeur de code et <xref:System.Data.Linq.DataContext.CreateDatabase%2A>.</span><span class="sxs-lookup"><span data-stu-id="d9442-110">If you do not have an existing database and want to create one from an object model, you can create your object model by using your code editor and <xref:System.Data.Linq.DataContext.CreateDatabase%2A>.</span></span> <span data-ttu-id="d9442-111">Pour plus d’informations, consultez [Comment : créer dynamiquement une base de données](how-to-dynamically-create-a-database.md).</span><span class="sxs-lookup"><span data-stu-id="d9442-111">For more information, see [How to: Dynamically Create a Database](how-to-dynamically-create-a-database.md).</span></span>  
  
 <span data-ttu-id="d9442-112">La documentation du Concepteur O/R fournit des exemples de génération d’un Visual Basic ou d’un modèle objet C# à l’aide du Concepteur O/R.</span><span class="sxs-lookup"><span data-stu-id="d9442-112">Documentation for the O/R Designer provides examples of how to generate a Visual Basic or C# object model by using the O/R Designer.</span></span> <span data-ttu-id="d9442-113">Les informations suivantes fournissent des exemples d'utilisation de l'outil en ligne de commande SQLMetal.</span><span class="sxs-lookup"><span data-stu-id="d9442-113">The following information provide examples of how to use the SQLMetal command-line tool.</span></span> <span data-ttu-id="d9442-114">Pour plus d’informations, consultez [SqlMetal.exe (outil de génération de code)](../../../../tools/sqlmetal-exe-code-generation-tool.md).</span><span class="sxs-lookup"><span data-stu-id="d9442-114">For more information, see [SqlMetal.exe (Code Generation Tool)](../../../../tools/sqlmetal-exe-code-generation-tool.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="d9442-115"> Exemple</span><span class="sxs-lookup"><span data-stu-id="d9442-115">Example</span></span>  
 <span data-ttu-id="d9442-116">La ligne de commande SQLMetal présentée dans l’exemple suivant produit Visual Basic code comme modèle objet basé sur les attributs de l’exemple de base de données Northwind.</span><span class="sxs-lookup"><span data-stu-id="d9442-116">The SQLMetal command line shown in the following example produces Visual Basic code as the attribute-based object model of the Northwind sample database.</span></span> <span data-ttu-id="d9442-117">Des procédures stockées et des fonctions sont également restituées.</span><span class="sxs-lookup"><span data-stu-id="d9442-117">Stored procedures and functions are also rendered.</span></span>  
  
```console  
sqlmetal /code:northwind.vb /language:vb "c:\northwnd.mdf" /sprocs /functions  
```  
  
## <a name="example"></a><span data-ttu-id="d9442-118"> Exemple</span><span class="sxs-lookup"><span data-stu-id="d9442-118">Example</span></span>  
 <span data-ttu-id="d9442-119">La ligne de commande SQLMetal présentée dans l'exemple suivant produit du code C# comme modèle objet basé sur les attributs de l'exemple de base de données Northwind.</span><span class="sxs-lookup"><span data-stu-id="d9442-119">The SQLMetal command line shown in the following example produces C# code as the attribute-based object model of the Northwind sample database.</span></span> <span data-ttu-id="d9442-120">Des procédures stockées et des fonctions sont également restituées, et les noms de table sont automatiquement pluralisés.</span><span class="sxs-lookup"><span data-stu-id="d9442-120">Stored procedures and functions are also rendered, and table names are automatically pluralized.</span></span>  
  
```console  
sqlmetal /code:northwind.cs /language:csharp "c:\northwnd.mdf" /sprocs /functions /pluralize  
```  
  
## <a name="see-also"></a><span data-ttu-id="d9442-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d9442-121">See also</span></span>

- [<span data-ttu-id="d9442-122">Guide de programmation</span><span class="sxs-lookup"><span data-stu-id="d9442-122">Programming Guide</span></span>](programming-guide.md)
- [<span data-ttu-id="d9442-123">Modèle objet LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="d9442-123">The LINQ to SQL Object Model</span></span>](the-linq-to-sql-object-model.md)
- [<span data-ttu-id="d9442-124">Apprentissage par les procédures pas à pas</span><span class="sxs-lookup"><span data-stu-id="d9442-124">Learning by Walkthroughs</span></span>](learning-by-walkthroughs.md)
- [<span data-ttu-id="d9442-125">Procédure : Personnaliser des classes d’entité à l’aide de l’éditeur de code</span><span class="sxs-lookup"><span data-stu-id="d9442-125">How to: Customize Entity Classes by Using the Code Editor</span></span>](how-to-customize-entity-classes-by-using-the-code-editor.md)
- [<span data-ttu-id="d9442-126">Mappage basé sur les attributs</span><span class="sxs-lookup"><span data-stu-id="d9442-126">Attribute-Based Mapping</span></span>](attribute-based-mapping.md)
- [<span data-ttu-id="d9442-127">SqlMetal.exe (outil de génération de code)</span><span class="sxs-lookup"><span data-stu-id="d9442-127">SqlMetal.exe (Code Generation Tool)</span></span>](../../../../tools/sqlmetal-exe-code-generation-tool.md)
- [<span data-ttu-id="d9442-128">Mappage externe</span><span class="sxs-lookup"><span data-stu-id="d9442-128">External Mapping</span></span>](external-mapping.md)
- [<span data-ttu-id="d9442-129">Téléchargement d’exemples de base de données</span><span class="sxs-lookup"><span data-stu-id="d9442-129">Downloading Sample Databases</span></span>](downloading-sample-databases.md)
- [<span data-ttu-id="d9442-130">Création du modèle objet</span><span class="sxs-lookup"><span data-stu-id="d9442-130">Creating the Object Model</span></span>](creating-the-object-model.md)
