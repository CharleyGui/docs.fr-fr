---
title: Analyse du code source LINQ to SQL
ms.date: 03/30/2017
ms.assetid: cba3eef8-e108-4478-b588-ad59580e133e
ms.openlocfilehash: e34364496a791031cc87cf07efd3d2adca39d93c
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67743591"
---
# <a name="analyzing-linq-to-sql-source-code"></a><span data-ttu-id="5e7f4-102">Analyse du code source LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="5e7f4-102">Analyzing LINQ to SQL Source Code</span></span>
<span data-ttu-id="5e7f4-103">En exécutant les étapes suivantes, vous pouvez générer le code source [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] à partir de l'exemple de base de données Northwind.</span><span class="sxs-lookup"><span data-stu-id="5e7f4-103">By using the following steps, you can produce [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] source code from the Northwind sample database.</span></span> <span data-ttu-id="5e7f4-104">Vous pouvez comparer des éléments du modèle objet avec des éléments de la base de données pour mieux comprendre comment les différents éléments sont mappés.</span><span class="sxs-lookup"><span data-stu-id="5e7f4-104">You can compare elements of the object model with elements of the database to better see how different items are mapped.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5e7f4-105">Les développeurs qui utilisent Visual Studio peuvent utiliser le Concepteur O/R pour générer ce code.</span><span class="sxs-lookup"><span data-stu-id="5e7f4-105">Developers using Visual Studio can use the O/R Designer to produce this code.</span></span>  
  
1. <span data-ttu-id="5e7f4-106">Si vous n'avez pas déjà l'exemple de base de données Northwind sur votre ordinateur de développement, vous pouvez le télécharger gratuitement.</span><span class="sxs-lookup"><span data-stu-id="5e7f4-106">If you do not already have the Northwind sample database on your development computer, you can download it free of charge.</span></span> <span data-ttu-id="5e7f4-107">Pour plus d’informations, consultez [téléchargement d’exemples de bases de données](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md).</span><span class="sxs-lookup"><span data-stu-id="5e7f4-107">For more information, see [Downloading Sample Databases](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md).</span></span>  
  
2. <span data-ttu-id="5e7f4-108">Utilisez l'outil en ligne de commande SQLMetal pour générer un fichier source Visual Basic ou C#.</span><span class="sxs-lookup"><span data-stu-id="5e7f4-108">Use the SqlMetal command-line tool to generate a Visual Basic or C# source file.</span></span> <span data-ttu-id="5e7f4-109">Pour plus d’informations, consultez [SqlMetal.exe (outil de génération de code)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).</span><span class="sxs-lookup"><span data-stu-id="5e7f4-109">For more information, see [SqlMetal.exe (Code Generation Tool)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).</span></span> <span data-ttu-id="5e7f4-110">En tapant les commandes suivantes à une invite de commandes, vous pouvez générer les fichiers sources Visual Basic et C# qui incluent des procédures stockées et des fonctions :</span><span class="sxs-lookup"><span data-stu-id="5e7f4-110">By typing the following commands at a command prompt, you can generate Visual Basic and C# source files that include stored procedures and functions:</span></span>  
  
    - `sqlmetal /code:northwind.vb /language:vb "c:\northwnd.mdf" /sprocs /functions /pluralize`  
  
    - `sqlmetal /code:northwind.cs /language:csharp "c:\northwnd.mdf" /sprocs /functions /pluralize`  
  
## <a name="see-also"></a><span data-ttu-id="5e7f4-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5e7f4-111">See also</span></span>

- [<span data-ttu-id="5e7f4-112">Référence</span><span class="sxs-lookup"><span data-stu-id="5e7f4-112">Reference</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/reference.md)
- [<span data-ttu-id="5e7f4-113">Informations générales</span><span class="sxs-lookup"><span data-stu-id="5e7f4-113">Background Information</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)
