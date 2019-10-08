---
title: 'Procédure : Générer le modèle objet en Visual Basic ou en C#'
ms.date: 03/30/2017
ms.assetid: a0c73b33-5650-420c-b9dc-f49310c201ee
ms.openlocfilehash: 7d2c0600534c93f5884eec48a4bdaa3ce99945e9
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72002808"
---
# <a name="how-to-generate-the-object-model-in-visual-basic-or-c"></a><span data-ttu-id="435e1-102">Procédure : Générer le modèle objet dans Visual Basic ou C @ no__t-0</span><span class="sxs-lookup"><span data-stu-id="435e1-102">How to: Generate the Object Model in Visual Basic or C\#</span></span>
<span data-ttu-id="435e1-103">Dans [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], un modèle objet dans votre propre langage de programmation est mappé à une base de données relationnelle.</span><span class="sxs-lookup"><span data-stu-id="435e1-103">In [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], an object model in your own programming language is mapped to a relational database.</span></span> <span data-ttu-id="435e1-104">Deux outils sont disponibles pour générer automatiquement une Visual Basic ou C# un modèle à partir des métadonnées d’une base de données existante.</span><span class="sxs-lookup"><span data-stu-id="435e1-104">Two tools are available for automatically generating a Visual Basic or C# model from the metadata of an existing database.</span></span>  
  
- <span data-ttu-id="435e1-105">Si vous utilisez Visual Studio, vous pouvez utiliser la Concepteur Objet Relationnel pour générer un modèle objet.</span><span class="sxs-lookup"><span data-stu-id="435e1-105">If you are using Visual Studio, you can use the Object Relational Designer to generate an object model.</span></span> <span data-ttu-id="435e1-106">Le Concepteur O/R fournit une interface utilisateur riche pour vous aider à générer un modèle d’objet [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="435e1-106">The O/R Designer provides a rich user interface to help you generate a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] object model.</span></span> <span data-ttu-id="435e1-107">Pour plus d’informations, consultez [Outils LINQ to SQL dans Visual Studio](https://docs.microsoft.com/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2).</span><span class="sxs-lookup"><span data-stu-id="435e1-107">For more information see, [Linq to SQL Tools in Visual Studio](https://docs.microsoft.com/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2).</span></span>
  
- <span data-ttu-id="435e1-108">Outil en ligne de commande SQLMetal</span><span class="sxs-lookup"><span data-stu-id="435e1-108">The SQLMetal command-line tool.</span></span> <span data-ttu-id="435e1-109">Pour plus d’informations, consultez [SqlMetal.exe (outil de génération de code)](../../../../tools/sqlmetal-exe-code-generation-tool.md).</span><span class="sxs-lookup"><span data-stu-id="435e1-109">For more information, see [SqlMetal.exe (Code Generation Tool)](../../../../tools/sqlmetal-exe-code-generation-tool.md).</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="435e1-110">Si vous ne possédez pas de base de données existante et que vous souhaitez en créer une à partir d'un modèle objet, vous pouvez utiliser votre éditeur de code et <xref:System.Data.Linq.DataContext.CreateDatabase%2A>.</span><span class="sxs-lookup"><span data-stu-id="435e1-110">If you do not have an existing database and want to create one from an object model, you can create your object model by using your code editor and <xref:System.Data.Linq.DataContext.CreateDatabase%2A>.</span></span> <span data-ttu-id="435e1-111">Pour plus d'informations, voir [Procédure : Créer dynamiquement une base de données @ no__t-0.</span><span class="sxs-lookup"><span data-stu-id="435e1-111">For more information, see [How to: Dynamically Create a Database](how-to-dynamically-create-a-database.md).</span></span>  
  
 <span data-ttu-id="435e1-112">La documentation relative au Concepteur O/R fournit des exemples de génération d’un Visual Basic C# ou d’un modèle objet à l’aide du concepteur o/r.</span><span class="sxs-lookup"><span data-stu-id="435e1-112">Documentation for the O/R Designer provides examples of how to generate a Visual Basic or C# object model by using the O/R Designer.</span></span> <span data-ttu-id="435e1-113">Les informations suivantes fournissent des exemples d'utilisation de l'outil en ligne de commande SQLMetal.</span><span class="sxs-lookup"><span data-stu-id="435e1-113">The following information provide examples of how to use the SQLMetal command-line tool.</span></span> <span data-ttu-id="435e1-114">Pour plus d’informations, consultez [SqlMetal.exe (outil de génération de code)](../../../../tools/sqlmetal-exe-code-generation-tool.md).</span><span class="sxs-lookup"><span data-stu-id="435e1-114">For more information, see [SqlMetal.exe (Code Generation Tool)](../../../../tools/sqlmetal-exe-code-generation-tool.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="435e1-115">Exemple</span><span class="sxs-lookup"><span data-stu-id="435e1-115">Example</span></span>  
 <span data-ttu-id="435e1-116">La ligne de commande SQLMetal présentée dans l’exemple suivant produit Visual Basic code comme modèle objet basé sur les attributs de l’exemple de base de données Northwind.</span><span class="sxs-lookup"><span data-stu-id="435e1-116">The SQLMetal command line shown in the following example produces Visual Basic code as the attribute-based object model of the Northwind sample database.</span></span> <span data-ttu-id="435e1-117">Des procédures stockées et des fonctions sont également restituées.</span><span class="sxs-lookup"><span data-stu-id="435e1-117">Stored procedures and functions are also rendered.</span></span>  
  
```console  
sqlmetal /code:northwind.vb /language:vb "c:\northwnd.mdf" /sprocs /functions  
```  
  
## <a name="example"></a><span data-ttu-id="435e1-118">Exemple</span><span class="sxs-lookup"><span data-stu-id="435e1-118">Example</span></span>  
 <span data-ttu-id="435e1-119">La ligne de commande SQLMetal présentée dans l'exemple suivant produit du code C# comme modèle objet basé sur les attributs de l'exemple de base de données Northwind.</span><span class="sxs-lookup"><span data-stu-id="435e1-119">The SQLMetal command line shown in the following example produces C# code as the attribute-based object model of the Northwind sample database.</span></span> <span data-ttu-id="435e1-120">Des procédures stockées et des fonctions sont également restituées, et les noms de table sont automatiquement pluralisés.</span><span class="sxs-lookup"><span data-stu-id="435e1-120">Stored procedures and functions are also rendered, and table names are automatically pluralized.</span></span>  
  
```console  
sqlmetal /code:northwind.cs /language:csharp "c:\northwnd.mdf" /sprocs /functions /pluralize  
```  
  
## <a name="see-also"></a><span data-ttu-id="435e1-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="435e1-121">See also</span></span>

- [<span data-ttu-id="435e1-122">Guide de programmation</span><span class="sxs-lookup"><span data-stu-id="435e1-122">Programming Guide</span></span>](programming-guide.md)
- [<span data-ttu-id="435e1-123">Modèle objet LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="435e1-123">The LINQ to SQL Object Model</span></span>](the-linq-to-sql-object-model.md)
- [<span data-ttu-id="435e1-124">Apprentissage par les procédures pas à pas</span><span class="sxs-lookup"><span data-stu-id="435e1-124">Learning by Walkthroughs</span></span>](learning-by-walkthroughs.md)
- <span data-ttu-id="435e1-125">[Guide pratique pour Personnaliser des classes d’entité à l’aide de l’éditeur de code @ no__t-0</span><span class="sxs-lookup"><span data-stu-id="435e1-125">[How to: Customize Entity Classes by Using the Code Editor](how-to-customize-entity-classes-by-using-the-code-editor.md)</span></span>
- [<span data-ttu-id="435e1-126">Mappage basé sur les attributs</span><span class="sxs-lookup"><span data-stu-id="435e1-126">Attribute-Based Mapping</span></span>](attribute-based-mapping.md)
- [<span data-ttu-id="435e1-127">SqlMetal.exe (outil de génération de code)</span><span class="sxs-lookup"><span data-stu-id="435e1-127">SqlMetal.exe (Code Generation Tool)</span></span>](../../../../tools/sqlmetal-exe-code-generation-tool.md)
- [<span data-ttu-id="435e1-128">Mappage externe</span><span class="sxs-lookup"><span data-stu-id="435e1-128">External Mapping</span></span>](external-mapping.md)
- [<span data-ttu-id="435e1-129">Téléchargement d’exemples de base de données</span><span class="sxs-lookup"><span data-stu-id="435e1-129">Downloading Sample Databases</span></span>](downloading-sample-databases.md)
- [<span data-ttu-id="435e1-130">Création du modèle objet</span><span class="sxs-lookup"><span data-stu-id="435e1-130">Creating the Object Model</span></span>](creating-the-object-model.md)
