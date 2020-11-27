---
title: Regroupement de connexions
ms.date: 03/30/2017
helpviewer_keywords:
- Internet, connections
- connections [.NET Framework], grouping
- WebRequest class, connection grouping
- network resources, connections
- connection pooling
ms.assetid: 2ec502e8-4ba0-4c22-9410-f28eaf4eee63
ms.openlocfilehash: 8bd4412a4c13dd490fce3118f59b5bb1f0d3ea85
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96250565"
---
# <a name="connection-grouping"></a><span data-ttu-id="c0f5e-102">Regroupement de connexions</span><span class="sxs-lookup"><span data-stu-id="c0f5e-102">Connection Grouping</span></span>

<span data-ttu-id="c0f5e-103">Le regroupement de connexions associe des requêtes spécifiques au sein d’une application unique à un pool de connexions défini.</span><span class="sxs-lookup"><span data-stu-id="c0f5e-103">Connection grouping associates specific requests within a single application to a defined connection pool.</span></span> <span data-ttu-id="c0f5e-104">Cela peut être requis par une application de couche intermédiaire qui se connecte à un serveur principal pour le compte d’un utilisateur et qui utilise un protocole d’authentification prenant en charge la délégation, tel que Kerberos, ou par une application de couche intermédiaire qui fournit ses propres informations d’identification, comme dans l’exemple ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="c0f5e-104">This can be required by a middle-tier application that connects to a back-end server on behalf of a user and uses an authentication protocol that supports delegation, such as Kerberos, or by a middle-tier application that supplies its own credentials, as in the example below.</span></span> <span data-ttu-id="c0f5e-105">Par exemple, supposez qu’un utilisateur (Jean) visite un site web interne qui affiche des informations sur son salaire.</span><span class="sxs-lookup"><span data-stu-id="c0f5e-105">For example, suppose a user, Joe, visits an internal Web site that displays his payroll information.</span></span> <span data-ttu-id="c0f5e-106">Après avoir authentifié Jean, le serveur d’applications de couche intermédiaire utilise ses informations d’identification pour se connecter au serveur principal afin de récupérer des informations sur son salaire.</span><span class="sxs-lookup"><span data-stu-id="c0f5e-106">After authenticating Joe, the middle-tier application server uses Joe's credentials to connect to the back-end server to retrieve his payroll information.</span></span> <span data-ttu-id="c0f5e-107">Ensuite, Suzanne accède au site et demande à consulter les informations relatives à son salaire.</span><span class="sxs-lookup"><span data-stu-id="c0f5e-107">Next, Susan visits the site and requests her payroll information.</span></span> <span data-ttu-id="c0f5e-108">Étant donné que l’application de couche intermédiaire a déjà établi une connexion à l’aide des informations d’identification de Jean, le serveur principal répond avec les informations relatives à Jean.</span><span class="sxs-lookup"><span data-stu-id="c0f5e-108">Because the middle-tier application has already made a connection using Joe's credentials, the back-end server responds with Joe's information.</span></span> <span data-ttu-id="c0f5e-109">Toutefois, si l’application assigne chaque requête envoyée au serveur principal à un groupe de connexions formé à partir du nom d’utilisateur, alors chaque utilisateur appartient à un pool de connexions distinct et ne peut pas partager accidentellement des informations d’authentification avec un autre utilisateur.</span><span class="sxs-lookup"><span data-stu-id="c0f5e-109">However, if the application assigns each request sent to the back-end server to a connection group formed from the user name, then each user belongs to a separate connection pool and cannot accidentally share authentication information with another user.</span></span>  
  
 <span data-ttu-id="c0f5e-110">Pour assigner une requête à un groupe de connexions spécifique, vous devez affecter un nom à la propriété <xref:System.Net.WebRequest.ConnectionGroupName%2A> de votre <xref:System.Net.WebRequest> avant d’exécuter la requête.</span><span class="sxs-lookup"><span data-stu-id="c0f5e-110">To assign a request to a specific connection group, you must assign a name to the <xref:System.Net.WebRequest.ConnectionGroupName%2A> property of your <xref:System.Net.WebRequest> before making the request.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c0f5e-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c0f5e-111">See also</span></span>

- [<span data-ttu-id="c0f5e-112">Gestion des connexions</span><span class="sxs-lookup"><span data-stu-id="c0f5e-112">Managing Connections</span></span>](managing-connections.md)
- [<span data-ttu-id="c0f5e-113">Procédure : assigner des informations utilisateur aux connexions de groupe</span><span class="sxs-lookup"><span data-stu-id="c0f5e-113">How to: Assign User Information to Group Connections</span></span>](how-to-assign-user-information-to-group-connections.md)
