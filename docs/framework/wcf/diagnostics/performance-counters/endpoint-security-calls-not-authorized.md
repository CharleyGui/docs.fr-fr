---
title: 'Point de terminaison : appels de sécurité non autorisés'
ms.date: 03/30/2017
ms.assetid: d25095ff-9ff0-4c69-a674-4e6a9fe3f4dc
ms.openlocfilehash: 3979eec15759989b638e1cc813cb78a0c008c3a4
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96256506"
---
# <a name="endpoint-security-calls-not-authorized"></a>Point de terminaison : appels de sécurité non autorisés

Nom du compteur : Appels de sécurité non autorisés.  
  
## <a name="description"></a>Description  

 Ce compteur est incrémenté lorsque la méthode <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> retourne la valeur `false`. Il indique que le message entrant provient d’un utilisateur valide et qu’il est correctement protégé, mais que l’utilisateur n’est pas autorisé à exécuter des tâches spécifiques.
