---
title: Sécurisation des applications
ms.date: 03/30/2017
ms.assetid: 005a1d43-6ee5-471e-ad98-1d30a44d49d5
ms.openlocfilehash: af184f64b43c2d3dc39f8c0add08940d3b002c24
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90550753"
---
# <a name="securing-adonet-applications"></a><span data-ttu-id="3e8c4-102">Sécurisation des applications ADO.NET</span><span class="sxs-lookup"><span data-stu-id="3e8c4-102">Securing ADO.NET applications</span></span>

<span data-ttu-id="3e8c4-103">L'écriture d'une application ADO.NET sécurisée ne se limite pas à éviter les pièges de codage courants, tels que la non validation des entrées d'utilisateur.</span><span class="sxs-lookup"><span data-stu-id="3e8c4-103">Writing a secure ADO.NET application involves more than avoiding common coding pitfalls such as not validating user input.</span></span> <span data-ttu-id="3e8c4-104">Une application qui accède à des données présente de nombreux points de défaillance potentiels qu'un intrus peut exploiter en vue d'extraire, de manipuler ou de détruire des données sensibles.</span><span class="sxs-lookup"><span data-stu-id="3e8c4-104">An application that accesses data has many potential points of failure that an attacker can exploit to retrieve, manipulate, or destroy sensitive data.</span></span> <span data-ttu-id="3e8c4-105">Il est donc important de comprendre tous les aspects de la sécurité, depuis le processus de modélisation de menace durant la phase de conception de votre application, jusqu'à son déploiement éventuel et sa maintenance en cours.</span><span class="sxs-lookup"><span data-stu-id="3e8c4-105">It is therefore important to understand all aspects of security, from the process of threat modeling during the design phase of your application, to its eventual deployment and ongoing maintenance.</span></span>  
  
<span data-ttu-id="3e8c4-106">Le .NET Framework fournit de nombreux services, classes et outils utiles permettant de sécuriser et d'administrer des applications de base de données.</span><span class="sxs-lookup"><span data-stu-id="3e8c4-106">The .NET Framework provides many useful classes, services, and tools for securing and administering database applications.</span></span> <span data-ttu-id="3e8c4-107">Le Common Language Runtime (CLR) fournit un environnement de type sécurisé pour l'exécution du code, avec une sécurité d'accès du code pour restreindre les autorisations de code managé.</span><span class="sxs-lookup"><span data-stu-id="3e8c4-107">The common language runtime (CLR) provides a type-safe environment for code to run in, with code access security (CAS) to restrict further the permissions of managed code.</span></span> <span data-ttu-id="3e8c4-108">L'adoption des procédés de codage sécurisés pour l'accès aux données permet de réduire les dommages infligés par un intrus potentiel.</span><span class="sxs-lookup"><span data-stu-id="3e8c4-108">Following secure data access coding practices limits the damage that can be inflicted by a potential attacker.</span></span>  
  
<span data-ttu-id="3e8c4-109">L'écriture d'un code sécurisé ne protège pas contre les défaillances de sécurité volontaires lors de l'utilisation de ressources non managées telles que des bases de données.</span><span class="sxs-lookup"><span data-stu-id="3e8c4-109">Writing secure code does not guard against self-inflicted security holes when working with unmanaged resources such as databases.</span></span> <span data-ttu-id="3e8c4-110">La plupart des bases de données de serveur, telles que SQL Server, possèdent leurs propres systèmes de sécurité qui renforcent la sécurité si ceux-ci sont correctement implémentés.</span><span class="sxs-lookup"><span data-stu-id="3e8c4-110">Most server databases, such as SQL Server, have their own security systems, which enhance security when implemented correctly.</span></span> <span data-ttu-id="3e8c4-111">Cependant, même une source de données équipée d'un système de sécurité robuste peut faire l'objet d'une attaque si elle n'est pas configurée de manière appropriée.</span><span class="sxs-lookup"><span data-stu-id="3e8c4-111">However, even a data source with a robust security system can be victimized in an attack if it is not configured appropriately.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="3e8c4-112">Contenu de cette section</span><span class="sxs-lookup"><span data-stu-id="3e8c4-112">In this section</span></span>

 [<span data-ttu-id="3e8c4-113">Présentation de la sécurité</span><span class="sxs-lookup"><span data-stu-id="3e8c4-113">Security Overview</span></span>](security-overview.md)  
 <span data-ttu-id="3e8c4-114">Fournit des recommandations pour la conception d'applications ADO.NET sécurisées.</span><span class="sxs-lookup"><span data-stu-id="3e8c4-114">Provides recommendations for designing secure ADO.NET applications.</span></span>  
  
 [<span data-ttu-id="3e8c4-115">Sécuriser l'accès aux données</span><span class="sxs-lookup"><span data-stu-id="3e8c4-115">Secure Data Access</span></span>](secure-data-access.md)  
 <span data-ttu-id="3e8c4-116">Décrit comment utiliser des données à partir d'une source de données sécurisée.</span><span class="sxs-lookup"><span data-stu-id="3e8c4-116">Describes how to work with data from a secured data source.</span></span>  
  
 [<span data-ttu-id="3e8c4-117">Applications clientes sécurisées</span><span class="sxs-lookup"><span data-stu-id="3e8c4-117">Secure Client Applications</span></span>](secure-client-applications.md)  
 <span data-ttu-id="3e8c4-118">Décrit des considérations sur la sécurité pour les applications clientes.</span><span class="sxs-lookup"><span data-stu-id="3e8c4-118">Describes security considerations for client applications.</span></span>  
  
 [<span data-ttu-id="3e8c4-119">Sécurité d'accès du code et ADO.NET</span><span class="sxs-lookup"><span data-stu-id="3e8c4-119">Code Access Security and ADO.NET</span></span>](code-access-security.md)  
 <span data-ttu-id="3e8c4-120">Décrit comment utiliser la sécurité d'accès du code (CAS) pour protéger le code ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="3e8c4-120">Describes how CAS can help protect ADO.NET code.</span></span> <span data-ttu-id="3e8c4-121">Explique également comment travailler avec une confiance partielle.</span><span class="sxs-lookup"><span data-stu-id="3e8c4-121">Also discusses how to work with partial trust.</span></span>  
  
 [<span data-ttu-id="3e8c4-122">Confidentialité et sécurité des données</span><span class="sxs-lookup"><span data-stu-id="3e8c4-122">Privacy and Data Security</span></span>](privacy-and-data-security.md)  
 <span data-ttu-id="3e8c4-123">Décrit les options de chiffrement pour les applications ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="3e8c4-123">Describes encryption options for ADO.NET applications.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="3e8c4-124">Sections connexes</span><span class="sxs-lookup"><span data-stu-id="3e8c4-124">Related sections</span></span>

 [<span data-ttu-id="3e8c4-125">Aide sur la sécurité des jeux de données et des DataTable</span><span class="sxs-lookup"><span data-stu-id="3e8c4-125">DataSet and DataTable security guidance</span></span>](dataset-datatable-dataview/security-guidance.md)  
 <span data-ttu-id="3e8c4-126">Fournit des conseils de sécurité pour <xref:System.Data.DataSet> et <xref:System.Data.DataTable> .</span><span class="sxs-lookup"><span data-stu-id="3e8c4-126">Provides security guidance for <xref:System.Data.DataSet> and <xref:System.Data.DataTable>.</span></span>

 [<span data-ttu-id="3e8c4-127">Sécurité SQL Server</span><span class="sxs-lookup"><span data-stu-id="3e8c4-127">SQL Server Security</span></span>](./sql/sql-server-security.md)  
 <span data-ttu-id="3e8c4-128">Décrit les fonctionnalités de sécurité SQL Server du point de vue d’un développeur.</span><span class="sxs-lookup"><span data-stu-id="3e8c4-128">Describes SQL Server security features from a developer's perspective.</span></span>  
  
 [<span data-ttu-id="3e8c4-129">Security Considerations</span><span class="sxs-lookup"><span data-stu-id="3e8c4-129">Security Considerations</span></span>](./ef/security-considerations.md)  
 <span data-ttu-id="3e8c4-130">Décrit la sécurité des applications reposant sur Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="3e8c4-130">Describes security for Entity Framework applications.</span></span>  
  
 [<span data-ttu-id="3e8c4-131">Sécurité</span><span class="sxs-lookup"><span data-stu-id="3e8c4-131">Security</span></span>](../../../standard/security/index.md)  
 <span data-ttu-id="3e8c4-132">Contient des liens vers des articles décrivant tous les aspects de la sécurité dans .NET.</span><span class="sxs-lookup"><span data-stu-id="3e8c4-132">Contains links to articles describing all aspects of security in .NET.</span></span>  
  
 <span data-ttu-id="3e8c4-133">[Outils de sécurité](/previous-versions/visualstudio/visual-studio-2008/7w3fd0wb(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="3e8c4-133">[Security Tools](/previous-versions/visualstudio/visual-studio-2008/7w3fd0wb(v=vs.90))</span></span>  
 <span data-ttu-id="3e8c4-134">Outils .NET Framework pour la sécurisation et l'administration de la stratégie de sécurité.</span><span class="sxs-lookup"><span data-stu-id="3e8c4-134">.NET Framework tools for securing and administering security policy.</span></span>  
  
 <span data-ttu-id="3e8c4-135">[Ressources de création des applications sécurisées](/previous-versions/visualstudio/visual-studio-2010/ms165101(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="3e8c4-135">[Resources for Creating Secure Applications](/previous-versions/visualstudio/visual-studio-2010/ms165101(v=vs.100))</span></span>  
 <span data-ttu-id="3e8c4-136">Fournit des liens vers des articles permettant de créer des applications sécurisées.</span><span class="sxs-lookup"><span data-stu-id="3e8c4-136">Provides links to articles for creating secure applications.</span></span>  
  
 [<span data-ttu-id="3e8c4-137">Bibliographie relative à la sécurité</span><span class="sxs-lookup"><span data-stu-id="3e8c4-137">Security Bibliography</span></span>](/visualstudio/ide/securing-applications)  
 <span data-ttu-id="3e8c4-138">Fournit des liens vers des ressources externes disponibles en ligne et sous forme de documentation.</span><span class="sxs-lookup"><span data-stu-id="3e8c4-138">Provides links to external resources available online and in print.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3e8c4-139">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3e8c4-139">See also</span></span>

- [<span data-ttu-id="3e8c4-140">ADO.NET</span><span class="sxs-lookup"><span data-stu-id="3e8c4-140">ADO.NET</span></span>](index.md)
- [<span data-ttu-id="3e8c4-141">Vue d'ensemble d’ADO.NET</span><span class="sxs-lookup"><span data-stu-id="3e8c4-141">ADO.NET Overview</span></span>](ado-net-overview.md)
