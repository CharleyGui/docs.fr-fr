---
title: 'Procédure : Générer du code personnalisé en modifiant un fichier DBML'
ms.date: 03/30/2017
ms.assetid: 50ad597a-8598-42d3-82dd-fc7d702ebc37
ms.openlocfilehash: 01890e6b899db6b70049e2d6b8193e5b0f4095fb
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70781983"
---
# <a name="how-to-generate-customized-code-by-modifying-a-dbml-file"></a><span data-ttu-id="b26ca-102">Procédure : Générer du code personnalisé en modifiant un fichier DBML</span><span class="sxs-lookup"><span data-stu-id="b26ca-102">How to: Generate Customized Code by Modifying a DBML File</span></span>
<span data-ttu-id="b26ca-103">Vous pouvez générer des Visual Basic C# ou du code source à partir d’un fichier de métadonnées. dbml (Database Markup Language).</span><span class="sxs-lookup"><span data-stu-id="b26ca-103">You can generate Visual Basic or C# source code from a database markup language (.dbml) metadata file.</span></span> <span data-ttu-id="b26ca-104">Cette approche permet de personnaliser le fichier .dbml par défaut avant de générer le code de mappage de l’application.</span><span class="sxs-lookup"><span data-stu-id="b26ca-104">This approach provides an opportunity to customize the default .dbml file before you generate the application mapping code.</span></span> <span data-ttu-id="b26ca-105">Il s'agit d'une fonctionnalité avancée.</span><span class="sxs-lookup"><span data-stu-id="b26ca-105">This is an advanced feature.</span></span>  
  
 <span data-ttu-id="b26ca-106">Les étapes de ce processus sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="b26ca-106">The steps in this process are as follows:</span></span>  
  
1. <span data-ttu-id="b26ca-107">Générez un fichier .dbml.</span><span class="sxs-lookup"><span data-stu-id="b26ca-107">Generate a .dbml file.</span></span>  
  
2. <span data-ttu-id="b26ca-108">Utilisez un éditeur pour modifier le fichier .dbml.</span><span class="sxs-lookup"><span data-stu-id="b26ca-108">Use an editor to modify the .dbml file.</span></span> <span data-ttu-id="b26ca-109">Notez que le fichier. dbml doit être validé par rapport au fichier de définition de schéma ( [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] . xsd) pour les fichiers. dbml.</span><span class="sxs-lookup"><span data-stu-id="b26ca-109">Note that the .dbml file must validate against the schema definition (.xsd) file for [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] .dbml files.</span></span> <span data-ttu-id="b26ca-110">Pour plus d’informations, consultez [génération de code dans LINQ to SQL](code-generation-in-linq-to-sql.md).</span><span class="sxs-lookup"><span data-stu-id="b26ca-110">For more information, see [Code Generation in LINQ to SQL](code-generation-in-linq-to-sql.md).</span></span>  
  
3. <span data-ttu-id="b26ca-111">Générez le Visual Basic C# ou le code source.</span><span class="sxs-lookup"><span data-stu-id="b26ca-111">Generate the Visual Basic or C# source code.</span></span>  
  
 <span data-ttu-id="b26ca-112">Les exemples suivants utilisent l'outil en ligne de commande SQLMetal.</span><span class="sxs-lookup"><span data-stu-id="b26ca-112">The following examples use the SQLMetal command-line tool.</span></span> <span data-ttu-id="b26ca-113">Pour plus d’informations, consultez [SqlMetal.exe (outil de génération de code)](../../../../tools/sqlmetal-exe-code-generation-tool.md).</span><span class="sxs-lookup"><span data-stu-id="b26ca-113">For more information, see [SqlMetal.exe (Code Generation Tool)](../../../../tools/sqlmetal-exe-code-generation-tool.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="b26ca-114">Exemples</span><span class="sxs-lookup"><span data-stu-id="b26ca-114">Example</span></span>  
 <span data-ttu-id="b26ca-115">Le code suivant génère un fichier .dbml à partir de l'exemple de base de données Northwind.</span><span class="sxs-lookup"><span data-stu-id="b26ca-115">The following code generates a .dbml file from the Northwind sample database.</span></span> <span data-ttu-id="b26ca-116">Vous pouvez utiliser le nom de la base de données ou le nom du fichier .mdf comme source pour les métadonnées de base de données.</span><span class="sxs-lookup"><span data-stu-id="b26ca-116">As source for the database metadata, you can use either the name of the database or the name of the .mdf file.</span></span>  
  
```  
sqlmetal /server:myserver /database:northwind /dbml:mymeta.dbml  
sqlmetal /dbml:mymeta.dbml mydbfile.mdf  
```  
  
## <a name="example"></a><span data-ttu-id="b26ca-117">Exemples</span><span class="sxs-lookup"><span data-stu-id="b26ca-117">Example</span></span>  
 <span data-ttu-id="b26ca-118">Le code suivant génère Visual Basic ou C# un fichier de code source à partir d’un fichier. dbml.</span><span class="sxs-lookup"><span data-stu-id="b26ca-118">The following code generates Visual Basic or C# source code file from a .dbml file.</span></span>  
  
```  
sqlmetal /namespace:nwind /code:nwind.vb /language:vb DBMLFile.dbml  
sqlmetal /namespace:nwind /code:nwind.cs /language:csharp DBMLFile.dbml  
```  
  
## <a name="see-also"></a><span data-ttu-id="b26ca-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b26ca-119">See also</span></span>

- [<span data-ttu-id="b26ca-120">Génération de code dans LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="b26ca-120">Code Generation in LINQ to SQL</span></span>](code-generation-in-linq-to-sql.md)
- [<span data-ttu-id="b26ca-121">SqlMetal.exe (outil de génération de code)</span><span class="sxs-lookup"><span data-stu-id="b26ca-121">SqlMetal.exe (Code Generation Tool)</span></span>](../../../../tools/sqlmetal-exe-code-generation-tool.md)
- [<span data-ttu-id="b26ca-122">Création du modèle objet</span><span class="sxs-lookup"><span data-stu-id="b26ca-122">Creating the Object Model</span></span>](creating-the-object-model.md)
