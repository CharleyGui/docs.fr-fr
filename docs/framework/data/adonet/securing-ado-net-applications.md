---
title: Sécurisation des applications ADO.NET
ms.date: 03/30/2017
ms.assetid: 005a1d43-6ee5-471e-ad98-1d30a44d49d5
ms.openlocfilehash: d4c9c21f4d1f4a08ca6d676ee7b4c9e80709ba19
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69963121"
---
# <a name="securing-adonet-applications"></a><span data-ttu-id="58ead-102">Sécurisation des applications ADO.NET</span><span class="sxs-lookup"><span data-stu-id="58ead-102">Securing ADO.NET Applications</span></span>
<span data-ttu-id="58ead-103">L'écriture d'une application ADO.NET sécurisée ne se limite pas à éviter les pièges de codage courants, tels que la non validation des entrées d'utilisateur.</span><span class="sxs-lookup"><span data-stu-id="58ead-103">Writing a secure ADO.NET application involves more than avoiding common coding pitfalls such as not validating user input.</span></span> <span data-ttu-id="58ead-104">Une application qui accède à des données présente de nombreux points de défaillance possibles qu’un agresseur peut exploiter pour extraire, manipuler ou détruire des données sensibles.</span><span class="sxs-lookup"><span data-stu-id="58ead-104">An application that accesses data has many potential points of failure that an attacker can exploit to retrieve, manipulate, or destroy sensitive data.</span></span> <span data-ttu-id="58ead-105">Il est donc important de comprendre tous les aspects de la sécurité, depuis le processus de modélisation de menace durant la phase de conception de votre application, jusqu'à son déploiement éventuel et sa maintenance en cours.</span><span class="sxs-lookup"><span data-stu-id="58ead-105">It is therefore important to understand all aspects of security, from the process of threat modeling during the design phase of your application, to its eventual deployment and ongoing maintenance.</span></span>  
  
 <span data-ttu-id="58ead-106">Le .NET Framework fournit de nombreux services, classes et outils utiles permettant de sécuriser et d'administrer des applications de base de données.</span><span class="sxs-lookup"><span data-stu-id="58ead-106">The .NET Framework provides many useful classes, services, and tools for securing and administering database applications.</span></span> <span data-ttu-id="58ead-107">Le Common Language Runtime (CLR) fournit un environnement de type sécurisé pour l'exécution du code, avec une sécurité d'accès du code pour restreindre les autorisations de code managé.</span><span class="sxs-lookup"><span data-stu-id="58ead-107">The common language runtime (CLR) provides a type-safe environment for code to run in, with code access security (CAS) to restrict further the permissions of managed code.</span></span> <span data-ttu-id="58ead-108">L'adoption des procédés de codage sécurisés pour l'accès aux données permet de réduire les dommages infligés par un intrus potentiel.</span><span class="sxs-lookup"><span data-stu-id="58ead-108">Following secure data access coding practices limits the damage that can be inflicted by a potential attacker.</span></span>  
  
 <span data-ttu-id="58ead-109">L'écriture d'un code sécurisé ne protège pas contre les défaillances de sécurité volontaires lors de l'utilisation de ressources non managées telles que des bases de données.</span><span class="sxs-lookup"><span data-stu-id="58ead-109">Writing secure code does not guard against self-inflicted security holes when working with unmanaged resources such as databases.</span></span> <span data-ttu-id="58ead-110">La plupart des bases de données de serveur, telles que SQL Server, possèdent leurs propres systèmes de sécurité qui renforcent la sécurité si ceux-ci sont correctement implémentés.</span><span class="sxs-lookup"><span data-stu-id="58ead-110">Most server databases, such as SQL Server, have their own security systems, which enhance security when implemented correctly.</span></span> <span data-ttu-id="58ead-111">Cependant, même une source de données équipée d'un système de sécurité robuste peut faire l'objet d'une attaque si elle n'est pas configurée de manière appropriée.</span><span class="sxs-lookup"><span data-stu-id="58ead-111">However, even a data source with a robust security system can be victimized in an attack if it is not configured appropriately.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="58ead-112">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="58ead-112">In This Section</span></span>  
 [<span data-ttu-id="58ead-113">Vue d’ensemble de la sécurité</span><span class="sxs-lookup"><span data-stu-id="58ead-113">Security Overview</span></span>](../../../../docs/framework/data/adonet/security-overview.md)  
 <span data-ttu-id="58ead-114">Fournit des recommandations pour la conception d'applications ADO.NET sécurisées.</span><span class="sxs-lookup"><span data-stu-id="58ead-114">Provides recommendations for designing secure ADO.NET applications.</span></span>  
  
 [<span data-ttu-id="58ead-115">Sécuriser l’accès aux données</span><span class="sxs-lookup"><span data-stu-id="58ead-115">Secure Data Access</span></span>](../../../../docs/framework/data/adonet/secure-data-access.md)  
 <span data-ttu-id="58ead-116">Décrit comment utiliser des données à partir d'une source de données sécurisée.</span><span class="sxs-lookup"><span data-stu-id="58ead-116">Describes how to work with data from a secured data source.</span></span>  
  
 [<span data-ttu-id="58ead-117">Applications clientes sécurisées</span><span class="sxs-lookup"><span data-stu-id="58ead-117">Secure Client Applications</span></span>](../../../../docs/framework/data/adonet/secure-client-applications.md)  
 <span data-ttu-id="58ead-118">Décrit des considérations sur la sécurité pour les applications clientes.</span><span class="sxs-lookup"><span data-stu-id="58ead-118">Describes security considerations for client applications.</span></span>  
  
 [<span data-ttu-id="58ead-119">Sécurité d’accès du code et ADO.NET</span><span class="sxs-lookup"><span data-stu-id="58ead-119">Code Access Security and ADO.NET</span></span>](../../../../docs/framework/data/adonet/code-access-security.md)  
 <span data-ttu-id="58ead-120">Décrit comment utiliser la sécurité d'accès du code (CAS) pour protéger le code ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="58ead-120">Describes how CAS can help protect ADO.NET code.</span></span> <span data-ttu-id="58ead-121">Explique également comment travailler avec une confiance partielle.</span><span class="sxs-lookup"><span data-stu-id="58ead-121">Also discusses how to work with partial trust.</span></span>  
  
 [<span data-ttu-id="58ead-122">Confidentialité et sécurité des données</span><span class="sxs-lookup"><span data-stu-id="58ead-122">Privacy and Data Security</span></span>](../../../../docs/framework/data/adonet/privacy-and-data-security.md)  
 <span data-ttu-id="58ead-123">Décrit les options de chiffrement pour les applications ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="58ead-123">Describes encryption options for ADO.NET applications.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="58ead-124">Rubriques connexes</span><span class="sxs-lookup"><span data-stu-id="58ead-124">Related Sections</span></span>  
 [<span data-ttu-id="58ead-125">Sécurité SQL Server</span><span class="sxs-lookup"><span data-stu-id="58ead-125">SQL Server Security</span></span>](../../../../docs/framework/data/adonet/sql/sql-server-security.md)  
 <span data-ttu-id="58ead-126">Décrit les fonctionnalités de sécurité SQL Server du point de vue d’un développeur.</span><span class="sxs-lookup"><span data-stu-id="58ead-126">Describes SQL Server security features from a developer's perspective.</span></span>  
  
 [<span data-ttu-id="58ead-127">Considérations relatives à la sécurité</span><span class="sxs-lookup"><span data-stu-id="58ead-127">Security Considerations</span></span>](../../../../docs/framework/data/adonet/ef/security-considerations.md)  
 <span data-ttu-id="58ead-128">Décrit la sécurité des applications reposant sur Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="58ead-128">Describes security for Entity Framework applications.</span></span>  
  
 [<span data-ttu-id="58ead-129">Sécurité</span><span class="sxs-lookup"><span data-stu-id="58ead-129">Security</span></span>](../../../standard/security/index.md)  
 <span data-ttu-id="58ead-130">Contient des liens vers des rubriques qui décrivent tous les aspects de la sécurité dans .NET.</span><span class="sxs-lookup"><span data-stu-id="58ead-130">Contains links to topics describing all aspects of security in .NET.</span></span>  
  
 <span data-ttu-id="58ead-131">[Outils de sécurité](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/7w3fd0wb(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="58ead-131">[Security Tools](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/7w3fd0wb(v=vs.90))</span></span>  
 <span data-ttu-id="58ead-132">Outils .NET Framework pour la sécurisation et l'administration de la stratégie de sécurité.</span><span class="sxs-lookup"><span data-stu-id="58ead-132">.NET Framework tools for securing and administering security policy.</span></span>  
  
 <span data-ttu-id="58ead-133">[Ressources de création des applications sécurisées](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms165101(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="58ead-133">[Resources for Creating Secure Applications](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms165101(v=vs.100))</span></span>  
 <span data-ttu-id="58ead-134">Fournit des liens vers des rubriques pour la création d'applications sécurisées.</span><span class="sxs-lookup"><span data-stu-id="58ead-134">Provides links to topics for creating secure applications.</span></span>  
  
 [<span data-ttu-id="58ead-135">Bibliographie relative à la sécurité</span><span class="sxs-lookup"><span data-stu-id="58ead-135">Security Bibliography</span></span>](/visualstudio/ide/security-bibliography)  
 <span data-ttu-id="58ead-136">Fournit des liens vers des ressources externes disponibles en ligne et sous forme de documentation.</span><span class="sxs-lookup"><span data-stu-id="58ead-136">Provides links to external resources available online and in print.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="58ead-137">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="58ead-137">See also</span></span>

- [<span data-ttu-id="58ead-138">ADO.NET</span><span class="sxs-lookup"><span data-stu-id="58ead-138">ADO.NET</span></span>](../../../../docs/framework/data/adonet/index.md)
- [<span data-ttu-id="58ead-139">Fournisseurs managés ADO.NET et centre de développement DataSet</span><span class="sxs-lookup"><span data-stu-id="58ead-139">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
