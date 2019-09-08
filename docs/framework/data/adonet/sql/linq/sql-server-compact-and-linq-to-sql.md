---
title: SQL Server Compact et LINQ to SQL
ms.date: 03/30/2017
ms.assetid: 59022359-a5a2-4c42-9a6a-5c0259c3ad17
ms.openlocfilehash: b5a1a12018bd85cf313c1841e6b67ab2edf67b4a
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70792534"
---
# <a name="sql-server-compact-and-linq-to-sql"></a><span data-ttu-id="81232-102">SQL Server Compact et LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="81232-102">SQL Server Compact and LINQ to SQL</span></span>
<span data-ttu-id="81232-103">SQL Server Compact est la base de données par défaut installée avec Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="81232-103">SQL Server Compact is the default database installed with Visual Studio.</span></span> <span data-ttu-id="81232-104">Pour plus d’informations, consultez [utilisation de SQL Server Compact (Visual Studio)](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2012/aa983321(v=vs.110)).</span><span class="sxs-lookup"><span data-stu-id="81232-104">For more information, see [Using SQL Server Compact (Visual Studio)](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2012/aa983321(v=vs.110)).</span></span>  
  
 <span data-ttu-id="81232-105">Cette rubrique décrit les principales différences d’utilisation, de configuration, de jeux de fonctionnalités et d’étendue [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] de prise en charge.</span><span class="sxs-lookup"><span data-stu-id="81232-105">This topic outlines the key differences in usage, configuration, feature sets, and scope of [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] support.</span></span>  
  
## <a name="characteristics-of-sql-server-compact-in-relation-to-linq-to-sql"></a><span data-ttu-id="81232-106">Caractéristiques de SQL Server Compact par rapport à LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="81232-106">Characteristics of SQL Server Compact in Relation to LINQ to SQL</span></span>  
 <span data-ttu-id="81232-107">Par défaut, SQL Server Compact est installé pour toutes les éditions de Visual Studio. il est donc disponible sur l’ordinateur de développement [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]pour une utilisation avec.</span><span class="sxs-lookup"><span data-stu-id="81232-107">By default, SQL Server Compact is installed for all Visual Studio editions, and is therefore available on the development computer for use with [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span> <span data-ttu-id="81232-108">Mais le déploiement d’une application qui utilise SQL Server Compact [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] et diffère de celle d’une application SQL Server.</span><span class="sxs-lookup"><span data-stu-id="81232-108">But deployment of an application that uses SQL Server Compact and [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] differs from that for a SQL Server application.</span></span> <span data-ttu-id="81232-109">SQL Server Compact ne fait pas partie du .NET Framework et doit par conséquent être fourni avec l'application ou téléchargé séparément depuis le site Microsoft.</span><span class="sxs-lookup"><span data-stu-id="81232-109">SQL Server Compact is not a part of the .NET Framework, and therefore must be packaged with the application or downloaded separately from the Microsoft site.</span></span>  
  
 <span data-ttu-id="81232-110">Notez les caractéristiques suivantes :</span><span class="sxs-lookup"><span data-stu-id="81232-110">Note the following characteristics:</span></span>  
  
- <span data-ttu-id="81232-111">SQL Server Compact est fourni comme une DLL qui peut être utilisée directement sur les fichiers de base de données (extension .sdf).</span><span class="sxs-lookup"><span data-stu-id="81232-111">SQL Server Compact is packaged as a DLL that can be used against database files (.sdf extension) directly.</span></span>  
  
- <span data-ttu-id="81232-112">SQL Server Compact s’exécute dans le même processus que l’application cliente.</span><span class="sxs-lookup"><span data-stu-id="81232-112">SQL Server Compact runs in the same process as the client application.</span></span> <span data-ttu-id="81232-113">L’efficacité de la communication avec SQL Server Compact peut donc être beaucoup plus élevée que la communication avec SQL Server.</span><span class="sxs-lookup"><span data-stu-id="81232-113">The efficiency of communication with SQL Server Compact can therefore be significantly higher than communicating with SQL Server.</span></span> <span data-ttu-id="81232-114">En revanche, SQL Server Compact nécessite l’interopérabilité entre le code managé et le code non managé avec ses coûts de surveillance.</span><span class="sxs-lookup"><span data-stu-id="81232-114">On the other hand, SQL Server Compact does require interoperability between managed and unmanaged code with its attendant costs.</span></span>  
  
- <span data-ttu-id="81232-115">La taille de la DLL SQL Server Compact est faible.</span><span class="sxs-lookup"><span data-stu-id="81232-115">The size of the SQL Server Compact DLL is small.</span></span> <span data-ttu-id="81232-116">Cette fonctionnalité réduit la taille globale de l'application.</span><span class="sxs-lookup"><span data-stu-id="81232-116">This feature reduces the overall application size.</span></span>  
  
- <span data-ttu-id="81232-117">Le runtime de [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] et l'outil en ligne de commande SQLMetal prennent en charge SQL Server Compact.</span><span class="sxs-lookup"><span data-stu-id="81232-117">The [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] runtime and the SQLMetal command-line tool support SQL Server Compact.</span></span>  
  
- <span data-ttu-id="81232-118">Le Concepteur Objet Relationnel ne prend pas en charge SQL Server Compact.</span><span class="sxs-lookup"><span data-stu-id="81232-118">The Object Relational Designer does not support SQL Server Compact.</span></span>  
  
## <a name="feature-set"></a><span data-ttu-id="81232-119">Jeu de fonctionnalités</span><span class="sxs-lookup"><span data-stu-id="81232-119">Feature Set</span></span>  
 <span data-ttu-id="81232-120">L’ensemble de fonctionnalités de SQL Server Compact est bien plus simple que l’ensemble de fonctionnalités de SQL Server des manières suivantes, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] qui peuvent affecter les applications :</span><span class="sxs-lookup"><span data-stu-id="81232-120">The SQL Server Compact feature set is much simpler than the feature set of SQL Server in the following ways that can affect [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] applications :</span></span>  
  
- <span data-ttu-id="81232-121">SQL Server Compact ne prend pas en charge de procédures stockées ou de vues.</span><span class="sxs-lookup"><span data-stu-id="81232-121">SQL Server Compact does not support stored procedures or views.</span></span>  
  
- <span data-ttu-id="81232-122">SQL Server Compact prend en charge uniquement un sous-ensemble de types de données et de fonctions SQL.</span><span class="sxs-lookup"><span data-stu-id="81232-122">SQL Server Compact supports only a subset of data types and SQL functions.</span></span>  
  
- <span data-ttu-id="81232-123">SQL Server Compact prend en charge uniquement un sous-ensemble de constructions SQL.</span><span class="sxs-lookup"><span data-stu-id="81232-123">SQL Server Compact supports only a subset of SQL constructs.</span></span>  
  
- <span data-ttu-id="81232-124">SQL Server Compact fournit uniquement un optimiseur minimal.</span><span class="sxs-lookup"><span data-stu-id="81232-124">SQL Server Compact provides only a minimal optimizer.</span></span> <span data-ttu-id="81232-125">Il est possible que certaines requêtes expirent.</span><span class="sxs-lookup"><span data-stu-id="81232-125">It is possible that some queries might time out.</span></span>  
  
- <span data-ttu-id="81232-126">SQL Server Compact ne prend pas en charge la confiance partielle.</span><span class="sxs-lookup"><span data-stu-id="81232-126">SQL Server Compact does not support partial trust.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="81232-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="81232-127">See also</span></span>

- [<span data-ttu-id="81232-128">Référence</span><span class="sxs-lookup"><span data-stu-id="81232-128">Reference</span></span>](reference.md)
