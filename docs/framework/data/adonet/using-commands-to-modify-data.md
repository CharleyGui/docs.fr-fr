---
title: Utilisation des commandes pour modifier les données
ms.date: 03/30/2017
ms.assetid: f4160389-b9ff-4b74-b655-437c76dcd586
ms.openlocfilehash: e2f61dbf74f28d026ae91a2bc8f5bb78530ffeac
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91177252"
---
# <a name="using-commands-to-modify-data"></a><span data-ttu-id="b6b0d-102">Utilisation des commandes pour modifier les données</span><span class="sxs-lookup"><span data-stu-id="b6b0d-102">Using Commands to Modify Data</span></span>

<span data-ttu-id="b6b0d-103">À l'aide d'un fournisseur de données .NET Framework, vous pouvez exécuter des procédures stockées ou des instructions DDL (CREATE TABLE et ALTER COLUMN, par exemple) pour effectuer une manipulation de schéma sur une base de données ou un catalogue.</span><span class="sxs-lookup"><span data-stu-id="b6b0d-103">Using a .NET Framework data provider, you can execute stored procedures or data definition language statements (for example, CREATE TABLE and ALTER COLUMN) to perform schema manipulation on a database or catalog.</span></span> <span data-ttu-id="b6b0d-104">Ces commandes ne retournent pas de lignes en tant que requête, donc l’objet **Command** fournit un **ExecuteNonQuery** pour les traiter.</span><span class="sxs-lookup"><span data-stu-id="b6b0d-104">These commands do not return rows as a query would, so the **Command** object provides an **ExecuteNonQuery** to process them.</span></span>  
  
 <span data-ttu-id="b6b0d-105">Outre l’utilisation de **ExecuteNonQuery** pour modifier le schéma, vous pouvez également utiliser cette méthode pour traiter les instructions SQL qui modifient les données, mais qui ne retournent pas de lignes, telles que Insert, Update et DELETE.</span><span class="sxs-lookup"><span data-stu-id="b6b0d-105">In addition to using **ExecuteNonQuery** to modify schema, you can also use this method to process SQL statements that modify data but that do not return rows, such as INSERT, UPDATE, and DELETE.</span></span>  
  
 <span data-ttu-id="b6b0d-106">Bien que les lignes ne soient pas retournées par la méthode **ExecuteNonQuery** , les paramètres d’entrée et de sortie et les valeurs de retour peuvent être passés et retournés via la collection **Parameters** de l’objet **Command** .</span><span class="sxs-lookup"><span data-stu-id="b6b0d-106">Although rows are not returned by the **ExecuteNonQuery** method, input and output parameters and return values can be passed and returned via the **Parameters** collection of the **Command** object.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="b6b0d-107">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="b6b0d-107">In This Section</span></span>  

 [<span data-ttu-id="b6b0d-108">Mise à jour des données dans une source de données</span><span class="sxs-lookup"><span data-stu-id="b6b0d-108">Updating Data in a Data Source</span></span>](updating-data-in-a-data-source.md)  
 <span data-ttu-id="b6b0d-109">Décrit l'exécution de commandes ou de procédures stockées qui modifient les données dans une base de données.</span><span class="sxs-lookup"><span data-stu-id="b6b0d-109">Describes how to execute commands or stored procedures that modify data in a database.</span></span>  
  
 [<span data-ttu-id="b6b0d-110">Exécution d'opérations du catalogue</span><span class="sxs-lookup"><span data-stu-id="b6b0d-110">Performing Catalog Operations</span></span>](performing-catalog-operations.md)  
 <span data-ttu-id="b6b0d-111">Décrit l'exécution des commandes qui modifient le schéma de base de données.</span><span class="sxs-lookup"><span data-stu-id="b6b0d-111">Describes how to execute commands that modify database schema.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b6b0d-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b6b0d-112">See also</span></span>

- [<span data-ttu-id="b6b0d-113">Extraction et modification de données dans ADO.NET</span><span class="sxs-lookup"><span data-stu-id="b6b0d-113">Retrieving and Modifying Data in ADO.NET</span></span>](retrieving-and-modifying-data.md)
- [<span data-ttu-id="b6b0d-114">Commandes et paramètres</span><span class="sxs-lookup"><span data-stu-id="b6b0d-114">Commands and Parameters</span></span>](commands-and-parameters.md)
- [<span data-ttu-id="b6b0d-115">Vue d'ensemble d’ADO.NET</span><span class="sxs-lookup"><span data-stu-id="b6b0d-115">ADO.NET Overview</span></span>](ado-net-overview.md)
