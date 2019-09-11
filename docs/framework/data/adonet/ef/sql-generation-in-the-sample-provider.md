---
title: Génération SQL dans le Fournisseur d'exemples
ms.date: 03/30/2017
ms.assetid: e70f553d-4622-4627-928e-1aa2ee605d8e
ms.openlocfilehash: a59f1fecf85d63208c3388204c962b5838902ba7
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70854319"
---
# <a name="sql-generation-in-the-sample-provider"></a><span data-ttu-id="75573-102">Génération SQL dans le Fournisseur d'exemples</span><span class="sxs-lookup"><span data-stu-id="75573-102">SQL Generation in the Sample Provider</span></span>
<span data-ttu-id="75573-103">L' [exemple de fournisseur Entity Framework](https://code.msdn.microsoft.com/windowsdesktop/Entity-Framework-Sample-6a9801d0) illustre les nouveaux composants des fournisseurs de données ADO.net qui prennent en charge l’Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="75573-103">The [Entity Framework Sample Provider](https://code.msdn.microsoft.com/windowsdesktop/Entity-Framework-Sample-6a9801d0) demonstrates the new components of ADO.NET Data Providers that support the Entity Framework.</span></span>  <span data-ttu-id="75573-104">Il utilise une base de données SQL Server 2005 et est implémenté comme un wrapper pour le fournisseur de données System.Data.SqlClient ADO.NET 2.0.</span><span class="sxs-lookup"><span data-stu-id="75573-104">It works with a SQL Server 2005 database and is implemented as a wrapper for the System.Data.SqlClient ADO.NET 2.0 Data Provider.</span></span>  
  
 <span data-ttu-id="75573-105">Le module Génération SQL du Fournisseur d’exemples (situé sous le dossier Génération SQL, à l’exception du fichier DmlSqlGenerator.cs) prend un DbQueryCommandTree d’entrée et produit une instruction SQL SELECT unique.</span><span class="sxs-lookup"><span data-stu-id="75573-105">The SQL Generation module of the Sample Provider (located under the SQL Generation folder, except for the file DmlSqlGenerator.cs) takes an input DbQueryCommandTree and produces a single SQL SELECT statement.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="75573-106">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="75573-106">In This Section</span></span>  
 <span data-ttu-id="75573-107">Cette section comprend les rubriques suivantes :</span><span class="sxs-lookup"><span data-stu-id="75573-107">This section includes the following topics:</span></span>  
  
 [<span data-ttu-id="75573-108">Architecture et conception</span><span class="sxs-lookup"><span data-stu-id="75573-108">Architecture and Design</span></span>](architecture-and-design.md)  
  
 [<span data-ttu-id="75573-109">Procédure pas à pas : Génération SQL</span><span class="sxs-lookup"><span data-stu-id="75573-109">Walkthrough: SQL Generation</span></span>](walkthrough-sql-generation.md)  
  
## <a name="see-also"></a><span data-ttu-id="75573-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="75573-110">See also</span></span>

- [<span data-ttu-id="75573-111">Génération SQL</span><span class="sxs-lookup"><span data-stu-id="75573-111">SQL Generation</span></span>](sql-generation.md)
