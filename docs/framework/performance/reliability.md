---
title: Fiabilité
ms.date: 03/30/2017
helpviewer_keywords:
- SQL Server [.NET Framework]
- managed code, reliability
- reliability [.NET Framework]
- writing reliable code
- code, reliability
ms.assetid: 294aa306-0afe-4cbe-b397-86ba9f1860f8
author: mairaw
ms.author: mairaw
ms.openlocfilehash: acb84c6617cdffabfe276895f81e7df2b04bb8bb
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71046234"
---
# <a name="reliability"></a><span data-ttu-id="3ed73-102">Fiabilité</span><span class="sxs-lookup"><span data-stu-id="3ed73-102">Reliability</span></span>
<span data-ttu-id="3ed73-103">Il est important que l’exécution de code dans les environnements serveur tels que SQL Server puisse vous protéger des exceptions asynchrones.</span><span class="sxs-lookup"><span data-stu-id="3ed73-103">It is important that code executing in server environments such as SQL Server protect against asynchronous exceptions.</span></span> <span data-ttu-id="3ed73-104">La fiabilité, comme nous allons le voir ici, ne se rapporte pas à SQL Server, mais à l’écriture de code pour tout hôte se trouvant dans un environnement .NET Framework 2.0.</span><span class="sxs-lookup"><span data-stu-id="3ed73-104">Reliability, as discussed here, is not specific to SQL Server but to writing reliable code for any host executing in a .NET Framework version 2.0 environment.</span></span> <span data-ttu-id="3ed73-105">Toutefois, étant donné que SQL Server est le premier service qui recourt autant aux nouvelles fonctionnalités de fiabilité de la version 2.0, nous l’avons utilisé comme exemple.</span><span class="sxs-lookup"><span data-stu-id="3ed73-105">However, SQL Server is the first service making extensive use of the new reliability features of version 2.0, so it is used as an example.</span></span>  
  
 <span data-ttu-id="3ed73-106">Les consignes d’exécution de code sont plus strictes pour SQL Server que pour les autres environnements serveur,</span><span class="sxs-lookup"><span data-stu-id="3ed73-106">Code running in SQL Server must deal with more stringent reliability guidelines than other server environments.</span></span> <span data-ttu-id="3ed73-107">en raison de l’opération stable de SQL Server relative à la consommation de ressources.</span><span class="sxs-lookup"><span data-stu-id="3ed73-107">This is due to SQL Server’s steady operation at the edge of resource consumption.</span></span>  <span data-ttu-id="3ed73-108">Les exceptions <xref:System.OutOfMemoryException> et <xref:System.Threading.ThreadAbortException> ne sont pas rares dans l’environnement SQL Server.</span><span class="sxs-lookup"><span data-stu-id="3ed73-108"><xref:System.OutOfMemoryException> and <xref:System.Threading.ThreadAbortException> exceptions are not uncommon in the SQL Server environment.</span></span> <span data-ttu-id="3ed73-109">Ces instructions sont globalement moins axées sur la fiabilité que sur la possibilité, pour du code managé entièrement fiable, d’échouer normalement lors d’un recyclage au niveau d’<xref:System.AppDomain>, qui constitue le principal moyen de maintenir la cohérence et la disponibilité du serveur.</span><span class="sxs-lookup"><span data-stu-id="3ed73-109">These guidelines in general are focused less on reliability and more on allowing fully trusted managed code to fail gracefully in the face of <xref:System.AppDomain>-level recycling, which is the primary way the server maintains consistency and availability.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="3ed73-110">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="3ed73-110">In This Section</span></span>  
 [<span data-ttu-id="3ed73-111">Attributs de programmation et de protection des hôtes SQL Server</span><span class="sxs-lookup"><span data-stu-id="3ed73-111">SQL Server Programming and Host Protection Attributes</span></span>](sql-server-programming-and-host-protection-attributes.md)  
 <span data-ttu-id="3ed73-112">Explique comment l’attribut <xref:System.Security.Permissions.HostProtectionAttribute> est utilisé par SQL Server pour limiter l’exécution du code managé.</span><span class="sxs-lookup"><span data-stu-id="3ed73-112">Describes how the <xref:System.Security.Permissions.HostProtectionAttribute> attribute is used by SQL Server to restrict the execution of managed code.</span></span>  
  
 [<span data-ttu-id="3ed73-113">Bonnes pratiques relatives à la fiabilité</span><span class="sxs-lookup"><span data-stu-id="3ed73-113">Reliability Best Practices</span></span>](reliability-best-practices.md)  
 <span data-ttu-id="3ed73-114">Fournit des instructions pour l’écriture d’un code répondant aux exigences de fiabilité.</span><span class="sxs-lookup"><span data-stu-id="3ed73-114">Provides guidelines for writing code that meets reliability requirements.</span></span>  
  
 [<span data-ttu-id="3ed73-115">Régions d’exécution limitée</span><span class="sxs-lookup"><span data-stu-id="3ed73-115">Constrained Execution Regions</span></span>](constrained-execution-regions.md)  
 <span data-ttu-id="3ed73-116">Décrit la fonction et le comportement des régions d’exécution limitée (CER).</span><span class="sxs-lookup"><span data-stu-id="3ed73-116">Describes the function and behavior of constrained execution regions (CERs).</span></span>  
  
## <a name="reference"></a><span data-ttu-id="3ed73-117">Référence</span><span class="sxs-lookup"><span data-stu-id="3ed73-117">Reference</span></span>  
 <xref:System.Security.Permissions.HostProtectionAttribute>  
  
 <xref:System.Security.Permissions.HostProtectionResource>
