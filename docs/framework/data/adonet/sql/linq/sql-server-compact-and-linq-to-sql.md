---
title: SQL Server Compact et LINQ to SQL
ms.date: 03/30/2017
ms.assetid: 59022359-a5a2-4c42-9a6a-5c0259c3ad17
ms.openlocfilehash: 5fa8f8ba2b0c5bdb92ad507bd48839a26837ba41
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67742865"
---
# <a name="sql-server-compact-and-linq-to-sql"></a><span data-ttu-id="daa0b-102">SQL Server Compact et LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="daa0b-102">SQL Server Compact and LINQ to SQL</span></span>
<span data-ttu-id="daa0b-103">SQL Server Compact est la base de données par défaut installée avec Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="daa0b-103">SQL Server Compact is the default database installed with Visual Studio.</span></span> <span data-ttu-id="daa0b-104">Pour plus d’informations, consultez [à l’aide de SQL Server Compact (Visual Studio)](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2012/aa983321(v=vs.110)).</span><span class="sxs-lookup"><span data-stu-id="daa0b-104">For more information, see [Using SQL Server Compact (Visual Studio)](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2012/aa983321(v=vs.110)).</span></span>  
  
 <span data-ttu-id="daa0b-105">Cette rubrique décrit les principales différences dans l’utilisation, ensembles de fonctionnalités et la configuration étendue de [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] prennent en charge.</span><span class="sxs-lookup"><span data-stu-id="daa0b-105">This topic outlines the key differences in usage, configuration, feature sets, and scope of [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] support.</span></span>  
  
## <a name="characteristics-of-sql-server-compact-in-relation-to-linq-to-sql"></a><span data-ttu-id="daa0b-106">Caractéristiques de SQL Server Compact par rapport à LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="daa0b-106">Characteristics of SQL Server Compact in Relation to LINQ to SQL</span></span>  
 <span data-ttu-id="daa0b-107">Par défaut, SQL Server Compact est installé pour toutes les éditions de Visual Studio et est donc disponible sur l’ordinateur de développement pour une utilisation avec [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="daa0b-107">By default, SQL Server Compact is installed for all Visual Studio editions, and is therefore available on the development computer for use with [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span> <span data-ttu-id="daa0b-108">Mais le déploiement d’une application qui utilise SQL Server Compact et [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] diffère de celle pour une application SQL Server.</span><span class="sxs-lookup"><span data-stu-id="daa0b-108">But deployment of an application that uses SQL Server Compact and [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] differs from that for a SQL Server application.</span></span> <span data-ttu-id="daa0b-109">SQL Server Compact ne fait pas partie du .NET Framework et doit par conséquent être fourni avec l'application ou téléchargé séparément depuis le site Microsoft.</span><span class="sxs-lookup"><span data-stu-id="daa0b-109">SQL Server Compact is not a part of the .NET Framework, and therefore must be packaged with the application or downloaded separately from the Microsoft site.</span></span>  
  
 <span data-ttu-id="daa0b-110">Notez les caractéristiques suivantes :</span><span class="sxs-lookup"><span data-stu-id="daa0b-110">Note the following characteristics:</span></span>  
  
- <span data-ttu-id="daa0b-111">SQL Server Compact est fourni comme une DLL qui peut être utilisée directement sur les fichiers de base de données (extension .sdf).</span><span class="sxs-lookup"><span data-stu-id="daa0b-111">SQL Server Compact is packaged as a DLL that can be used against database files (.sdf extension) directly.</span></span>  
  
- <span data-ttu-id="daa0b-112">SQL Server Compact s’exécute dans le même processus que l’application cliente.</span><span class="sxs-lookup"><span data-stu-id="daa0b-112">SQL Server Compact runs in the same process as the client application.</span></span> <span data-ttu-id="daa0b-113">L’efficacité de la communication avec SQL Server Compact peut être considérablement plus importante que la communication avec SQL Server.</span><span class="sxs-lookup"><span data-stu-id="daa0b-113">The efficiency of communication with SQL Server Compact can therefore be significantly higher than communicating with SQL Server.</span></span> <span data-ttu-id="daa0b-114">En revanche, SQL Server Compact requiert l’interopérabilité entre le code managé et avec ses coûts connexes.</span><span class="sxs-lookup"><span data-stu-id="daa0b-114">On the other hand, SQL Server Compact does require interoperability between managed and unmanaged code with its attendant costs.</span></span>  
  
- <span data-ttu-id="daa0b-115">La taille de la DLL SQL Server Compact est petite.</span><span class="sxs-lookup"><span data-stu-id="daa0b-115">The size of the SQL Server Compact DLL is small.</span></span> <span data-ttu-id="daa0b-116">Cette fonctionnalité réduit la taille globale de l'application.</span><span class="sxs-lookup"><span data-stu-id="daa0b-116">This feature reduces the overall application size.</span></span>  
  
- <span data-ttu-id="daa0b-117">Le runtime de [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] et l'outil en ligne de commande SQLMetal prennent en charge SQL Server Compact.</span><span class="sxs-lookup"><span data-stu-id="daa0b-117">The [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] runtime and the SQLMetal command-line tool support SQL Server Compact.</span></span>  
  
- <span data-ttu-id="daa0b-118">Le concepteur objet/relationnel ne prend pas en charge SQL Server Compact.</span><span class="sxs-lookup"><span data-stu-id="daa0b-118">The Object Relational Designer does not support SQL Server Compact.</span></span>  
  
## <a name="feature-set"></a><span data-ttu-id="daa0b-119">Jeu de fonctionnalités</span><span class="sxs-lookup"><span data-stu-id="daa0b-119">Feature Set</span></span>  
 <span data-ttu-id="daa0b-120">L’ensemble des fonctionnalités SQL Server Compact est beaucoup plus simple que l’ensemble des fonctionnalités de SQL Server dans les domaines suivants peuvent affecter [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] applications :</span><span class="sxs-lookup"><span data-stu-id="daa0b-120">The SQL Server Compact feature set is much simpler than the feature set of SQL Server in the following ways that can affect [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] applications :</span></span>  
  
- <span data-ttu-id="daa0b-121">SQL Server Compact ne prend pas en charge de procédures stockées ou de vues.</span><span class="sxs-lookup"><span data-stu-id="daa0b-121">SQL Server Compact does not support stored procedures or views.</span></span>  
  
- <span data-ttu-id="daa0b-122">SQL Server Compact prend en charge uniquement un sous-ensemble de types de données et de fonctions SQL.</span><span class="sxs-lookup"><span data-stu-id="daa0b-122">SQL Server Compact supports only a subset of data types and SQL functions.</span></span>  
  
- <span data-ttu-id="daa0b-123">SQL Server Compact prend en charge uniquement un sous-ensemble de constructions SQL.</span><span class="sxs-lookup"><span data-stu-id="daa0b-123">SQL Server Compact supports only a subset of SQL constructs.</span></span>  
  
- <span data-ttu-id="daa0b-124">SQL Server Compact fournit uniquement un optimiseur minimal.</span><span class="sxs-lookup"><span data-stu-id="daa0b-124">SQL Server Compact provides only a minimal optimizer.</span></span> <span data-ttu-id="daa0b-125">Il est possible que certaines requêtes peuvent expirer.</span><span class="sxs-lookup"><span data-stu-id="daa0b-125">It is possible that some queries might time out.</span></span>  
  
- <span data-ttu-id="daa0b-126">SQL Server Compact ne prend pas en charge la confiance partielle.</span><span class="sxs-lookup"><span data-stu-id="daa0b-126">SQL Server Compact does not support partial trust.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="daa0b-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="daa0b-127">See also</span></span>

- [<span data-ttu-id="daa0b-128">Référence</span><span class="sxs-lookup"><span data-stu-id="daa0b-128">Reference</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/reference.md)
