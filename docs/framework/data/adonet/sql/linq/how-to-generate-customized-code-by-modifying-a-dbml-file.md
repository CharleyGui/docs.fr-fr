---
title: 'Procédure : Générer du code personnalisé en modifiant un fichier DBML'
ms.date: 03/30/2017
ms.assetid: 50ad597a-8598-42d3-82dd-fc7d702ebc37
ms.openlocfilehash: ab49f76a0d5e7338a93e21ae9a8d1d9d74a21e82
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91173437"
---
# <a name="how-to-generate-customized-code-by-modifying-a-dbml-file"></a><span data-ttu-id="8454c-102">Procédure : Générer du code personnalisé en modifiant un fichier DBML</span><span class="sxs-lookup"><span data-stu-id="8454c-102">How to: Generate Customized Code by Modifying a DBML File</span></span>

<span data-ttu-id="8454c-103">Vous pouvez générer du code source Visual Basic ou C# à partir d’un fichier de métadonnées. dbml (Database Markup Language).</span><span class="sxs-lookup"><span data-stu-id="8454c-103">You can generate Visual Basic or C# source code from a database markup language (.dbml) metadata file.</span></span> <span data-ttu-id="8454c-104">Cette approche permet de personnaliser le fichier .dbml par défaut avant de générer le code de mappage de l’application.</span><span class="sxs-lookup"><span data-stu-id="8454c-104">This approach provides an opportunity to customize the default .dbml file before you generate the application mapping code.</span></span> <span data-ttu-id="8454c-105">Il s'agit d'une fonctionnalité avancée.</span><span class="sxs-lookup"><span data-stu-id="8454c-105">This is an advanced feature.</span></span>  
  
 <span data-ttu-id="8454c-106">Les étapes de ce processus sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="8454c-106">The steps in this process are as follows:</span></span>  
  
1. <span data-ttu-id="8454c-107">Générez un fichier .dbml.</span><span class="sxs-lookup"><span data-stu-id="8454c-107">Generate a .dbml file.</span></span>  
  
2. <span data-ttu-id="8454c-108">Utilisez un éditeur pour modifier le fichier .dbml.</span><span class="sxs-lookup"><span data-stu-id="8454c-108">Use an editor to modify the .dbml file.</span></span> <span data-ttu-id="8454c-109">Notez que le fichier. dbml doit être validé par rapport au fichier de définition de schéma (. xsd) pour les [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] fichiers. dbml.</span><span class="sxs-lookup"><span data-stu-id="8454c-109">Note that the .dbml file must validate against the schema definition (.xsd) file for [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] .dbml files.</span></span> <span data-ttu-id="8454c-110">Pour plus d’informations, consultez [génération de code dans LINQ to SQL](code-generation-in-linq-to-sql.md).</span><span class="sxs-lookup"><span data-stu-id="8454c-110">For more information, see [Code Generation in LINQ to SQL](code-generation-in-linq-to-sql.md).</span></span>  
  
3. <span data-ttu-id="8454c-111">Générez le code source Visual Basic ou C#.</span><span class="sxs-lookup"><span data-stu-id="8454c-111">Generate the Visual Basic or C# source code.</span></span>  
  
 <span data-ttu-id="8454c-112">Les exemples suivants utilisent l'outil en ligne de commande SQLMetal.</span><span class="sxs-lookup"><span data-stu-id="8454c-112">The following examples use the SQLMetal command-line tool.</span></span> <span data-ttu-id="8454c-113">Pour plus d’informations, consultez [SqlMetal.exe (outil de génération de code)](../../../../tools/sqlmetal-exe-code-generation-tool.md).</span><span class="sxs-lookup"><span data-stu-id="8454c-113">For more information, see [SqlMetal.exe (Code Generation Tool)](../../../../tools/sqlmetal-exe-code-generation-tool.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="8454c-114">Exemple</span><span class="sxs-lookup"><span data-stu-id="8454c-114">Example</span></span>  

 <span data-ttu-id="8454c-115">Le code suivant génère un fichier .dbml à partir de l'exemple de base de données Northwind.</span><span class="sxs-lookup"><span data-stu-id="8454c-115">The following code generates a .dbml file from the Northwind sample database.</span></span> <span data-ttu-id="8454c-116">Vous pouvez utiliser le nom de la base de données ou le nom du fichier .mdf comme source pour les métadonnées de base de données.</span><span class="sxs-lookup"><span data-stu-id="8454c-116">As source for the database metadata, you can use either the name of the database or the name of the .mdf file.</span></span>  
  
```console  
sqlmetal /server:myserver /database:northwind /dbml:mymeta.dbml  
sqlmetal /dbml:mymeta.dbml mydbfile.mdf  
```  
  
## <a name="example"></a><span data-ttu-id="8454c-117">Exemple</span><span class="sxs-lookup"><span data-stu-id="8454c-117">Example</span></span>  

 <span data-ttu-id="8454c-118">Le code suivant génère un fichier de code source Visual Basic ou C# à partir d’un fichier. dbml.</span><span class="sxs-lookup"><span data-stu-id="8454c-118">The following code generates Visual Basic or C# source code file from a .dbml file.</span></span>  
  
```console
sqlmetal /namespace:nwind /code:nwind.vb /language:vb DBMLFile.dbml  
sqlmetal /namespace:nwind /code:nwind.cs /language:csharp DBMLFile.dbml  
```  
  
## <a name="see-also"></a><span data-ttu-id="8454c-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8454c-119">See also</span></span>

- [<span data-ttu-id="8454c-120">Génération de code dans LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="8454c-120">Code Generation in LINQ to SQL</span></span>](code-generation-in-linq-to-sql.md)
- [<span data-ttu-id="8454c-121">SqlMetal.exe (outil de génération de code)</span><span class="sxs-lookup"><span data-stu-id="8454c-121">SqlMetal.exe (Code Generation Tool)</span></span>](../../../../tools/sqlmetal-exe-code-generation-tool.md)
- [<span data-ttu-id="8454c-122">Création du modèle objet</span><span class="sxs-lookup"><span data-stu-id="8454c-122">Creating the Object Model</span></span>](creating-the-object-model.md)
