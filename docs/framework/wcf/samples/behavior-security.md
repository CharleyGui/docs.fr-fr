---
title: Sécurité des comportements
ms.date: 03/30/2017
ms.assetid: 19710ae3-f197-4d28-ba9d-52e465006819
ms.openlocfilehash: 5d09fcc2068133b3bb302850a647a2539ab07ee3
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84575587"
---
# <a name="behavior-security"></a>Sécurité des comportements
Cette section contient des exemples qui indiquent comment configurer la sécurité des comportements de service.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Service Auditing Behavior](service-auditing-behavior.md)  
 Cet exemple montre comment utiliser <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> pour activer l'audit des événements de sécurité pendant des opérations de service.  
  
 [Membership and Role Provider](membership-and-role-provider.md)  
 Cet exemple montre comment un service peut utiliser les fournisseurs d’appartenances et de rôles ASP.NET pour authentifier et autoriser des clients.  
  
 [Authorizing Access to Service Operations](authorizing-access-to-service-operations.md)  
 Cet exemple montre comment utiliser [\<serviceAuthorization>](../../configure-apps/file-schema/wcf/serviceauthorization-element.md) pour permettre l’utilisation de l' <xref:System.Security.Permissions.PrincipalPermissionAttribute> attribut pour autoriser l’accès aux opérations de service.  
  
 [Emprunt de l'identité du client](impersonating-the-client.md)  
 Cet exemple montre comment emprunter l'identité de l'application de l'appelant au niveau du service afin que ce dernier puisse accéder aux ressources système pour le compte de l'appelant.
