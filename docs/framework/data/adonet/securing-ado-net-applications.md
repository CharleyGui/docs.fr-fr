---
title: Sécurisation des applications ADO.NET
ms.date: 03/30/2017
ms.assetid: 005a1d43-6ee5-471e-ad98-1d30a44d49d5
ms.openlocfilehash: c99c56afca475caafe32cca3f50d074fb82e0e00
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2019
ms.locfileid: "73196726"
---
# <a name="securing-adonet-applications"></a><span data-ttu-id="9e468-102">Sécurisation des applications ADO.NET</span><span class="sxs-lookup"><span data-stu-id="9e468-102">Securing ADO.NET Applications</span></span>
<span data-ttu-id="9e468-103">L'écriture d'une application ADO.NET sécurisée ne se limite pas à éviter les pièges de codage courants, tels que la non validation des entrées d'utilisateur.</span><span class="sxs-lookup"><span data-stu-id="9e468-103">Writing a secure ADO.NET application involves more than avoiding common coding pitfalls such as not validating user input.</span></span> <span data-ttu-id="9e468-104">Une application qui accède à des données présente de nombreux points de défaillance possibles qu’un agresseur peut exploiter pour extraire, manipuler ou détruire des données sensibles.</span><span class="sxs-lookup"><span data-stu-id="9e468-104">An application that accesses data has many potential points of failure that an attacker can exploit to retrieve, manipulate, or destroy sensitive data.</span></span> <span data-ttu-id="9e468-105">Il est donc important de comprendre tous les aspects de la sécurité, depuis le processus de modélisation de menace durant la phase de conception de votre application, jusqu'à son déploiement éventuel et sa maintenance en cours.</span><span class="sxs-lookup"><span data-stu-id="9e468-105">It is therefore important to understand all aspects of security, from the process of threat modeling during the design phase of your application, to its eventual deployment and ongoing maintenance.</span></span>  
  
 <span data-ttu-id="9e468-106">Le .NET Framework fournit de nombreux services, classes et outils utiles permettant de sécuriser et d'administrer des applications de base de données.</span><span class="sxs-lookup"><span data-stu-id="9e468-106">The .NET Framework provides many useful classes, services, and tools for securing and administering database applications.</span></span> <span data-ttu-id="9e468-107">Le Common Language Runtime (CLR) fournit un environnement de type sécurisé pour l'exécution du code, avec une sécurité d'accès du code pour restreindre les autorisations de code managé.</span><span class="sxs-lookup"><span data-stu-id="9e468-107">The common language runtime (CLR) provides a type-safe environment for code to run in, with code access security (CAS) to restrict further the permissions of managed code.</span></span> <span data-ttu-id="9e468-108">L'adoption des procédés de codage sécurisés pour l'accès aux données permet de réduire les dommages infligés par un intrus potentiel.</span><span class="sxs-lookup"><span data-stu-id="9e468-108">Following secure data access coding practices limits the damage that can be inflicted by a potential attacker.</span></span>  
  
 <span data-ttu-id="9e468-109">L'écriture d'un code sécurisé ne protège pas contre les défaillances de sécurité volontaires lors de l'utilisation de ressources non managées telles que des bases de données.</span><span class="sxs-lookup"><span data-stu-id="9e468-109">Writing secure code does not guard against self-inflicted security holes when working with unmanaged resources such as databases.</span></span> <span data-ttu-id="9e468-110">La plupart des bases de données de serveur, telles que SQL Server, possèdent leurs propres systèmes de sécurité qui renforcent la sécurité si ceux-ci sont correctement implémentés.</span><span class="sxs-lookup"><span data-stu-id="9e468-110">Most server databases, such as SQL Server, have their own security systems, which enhance security when implemented correctly.</span></span> <span data-ttu-id="9e468-111">Cependant, même une source de données équipée d'un système de sécurité robuste peut faire l'objet d'une attaque si elle n'est pas configurée de manière appropriée.</span><span class="sxs-lookup"><span data-stu-id="9e468-111">However, even a data source with a robust security system can be victimized in an attack if it is not configured appropriately.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="9e468-112">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="9e468-112">In This Section</span></span>  
 [<span data-ttu-id="9e468-113">Vue d’ensemble de la sécurité</span><span class="sxs-lookup"><span data-stu-id="9e468-113">Security Overview</span></span>](security-overview.md)  
 <span data-ttu-id="9e468-114">Fournit des recommandations pour la conception d'applications ADO.NET sécurisées.</span><span class="sxs-lookup"><span data-stu-id="9e468-114">Provides recommendations for designing secure ADO.NET applications.</span></span>  
  
 [<span data-ttu-id="9e468-115">Sécuriser l’accès aux données</span><span class="sxs-lookup"><span data-stu-id="9e468-115">Secure Data Access</span></span>](secure-data-access.md)  
 <span data-ttu-id="9e468-116">Décrit comment utiliser des données à partir d'une source de données sécurisée.</span><span class="sxs-lookup"><span data-stu-id="9e468-116">Describes how to work with data from a secured data source.</span></span>  
  
 [<span data-ttu-id="9e468-117">Applications clientes sécurisées</span><span class="sxs-lookup"><span data-stu-id="9e468-117">Secure Client Applications</span></span>](secure-client-applications.md)  
 <span data-ttu-id="9e468-118">Décrit des considérations sur la sécurité pour les applications clientes.</span><span class="sxs-lookup"><span data-stu-id="9e468-118">Describes security considerations for client applications.</span></span>  
  
 [<span data-ttu-id="9e468-119">Sécurité d’accès du code et ADO.NET</span><span class="sxs-lookup"><span data-stu-id="9e468-119">Code Access Security and ADO.NET</span></span>](code-access-security.md)  
 <span data-ttu-id="9e468-120">Décrit comment utiliser la sécurité d'accès du code (CAS) pour protéger le code ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="9e468-120">Describes how CAS can help protect ADO.NET code.</span></span> <span data-ttu-id="9e468-121">Explique également comment travailler avec une confiance partielle.</span><span class="sxs-lookup"><span data-stu-id="9e468-121">Also discusses how to work with partial trust.</span></span>  
  
 [<span data-ttu-id="9e468-122">Confidentialité et sécurité des données</span><span class="sxs-lookup"><span data-stu-id="9e468-122">Privacy and Data Security</span></span>](privacy-and-data-security.md)  
 <span data-ttu-id="9e468-123">Décrit les options de chiffrement pour les applications ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="9e468-123">Describes encryption options for ADO.NET applications.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="9e468-124">Rubriques connexes</span><span class="sxs-lookup"><span data-stu-id="9e468-124">Related Sections</span></span>  
 [<span data-ttu-id="9e468-125">Sécurité SQL Server</span><span class="sxs-lookup"><span data-stu-id="9e468-125">SQL Server Security</span></span>](./sql/sql-server-security.md)  
 <span data-ttu-id="9e468-126">Décrit les fonctionnalités de sécurité SQL Server du point de vue d’un développeur.</span><span class="sxs-lookup"><span data-stu-id="9e468-126">Describes SQL Server security features from a developer's perspective.</span></span>  
  
 [<span data-ttu-id="9e468-127">Considérations relatives à la sécurité</span><span class="sxs-lookup"><span data-stu-id="9e468-127">Security Considerations</span></span>](./ef/security-considerations.md)  
 <span data-ttu-id="9e468-128">Décrit la sécurité des applications reposant sur Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="9e468-128">Describes security for Entity Framework applications.</span></span>  
  
 [<span data-ttu-id="9e468-129">Security</span><span class="sxs-lookup"><span data-stu-id="9e468-129">Security</span></span>](../../../standard/security/index.md)  
 <span data-ttu-id="9e468-130">Contient des liens vers des rubriques qui décrivent tous les aspects de la sécurité dans .NET.</span><span class="sxs-lookup"><span data-stu-id="9e468-130">Contains links to topics describing all aspects of security in .NET.</span></span>  
  
 <span data-ttu-id="9e468-131">[Outils de sécurité](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/7w3fd0wb(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="9e468-131">[Security Tools](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/7w3fd0wb(v=vs.90))</span></span>  
 <span data-ttu-id="9e468-132">Outils .NET Framework pour la sécurisation et l'administration de la stratégie de sécurité.</span><span class="sxs-lookup"><span data-stu-id="9e468-132">.NET Framework tools for securing and administering security policy.</span></span>  
  
 <span data-ttu-id="9e468-133">[Ressources de création des applications sécurisées](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms165101(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="9e468-133">[Resources for Creating Secure Applications](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms165101(v=vs.100))</span></span>  
 <span data-ttu-id="9e468-134">Fournit des liens vers des rubriques pour la création d'applications sécurisées.</span><span class="sxs-lookup"><span data-stu-id="9e468-134">Provides links to topics for creating secure applications.</span></span>  
  
 [<span data-ttu-id="9e468-135">Bibliographie relative à la sécurité</span><span class="sxs-lookup"><span data-stu-id="9e468-135">Security Bibliography</span></span>](/visualstudio/ide/securing-applications)  
 <span data-ttu-id="9e468-136">Fournit des liens vers des ressources externes disponibles en ligne et sous forme de documentation.</span><span class="sxs-lookup"><span data-stu-id="9e468-136">Provides links to external resources available online and in print.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9e468-137">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9e468-137">See also</span></span>

- [<span data-ttu-id="9e468-138">ADO.NET</span><span class="sxs-lookup"><span data-stu-id="9e468-138">ADO.NET</span></span>](index.md)
- [<span data-ttu-id="9e468-139">Vue d’ensemble d’ADO.NET</span><span class="sxs-lookup"><span data-stu-id="9e468-139">ADO.NET Overview</span></span>](ado-net-overview.md)
