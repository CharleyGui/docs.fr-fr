---
title: Appels de sécurité non autorisés
ms.date: 03/30/2017
ms.assetid: cb6acdcd-7336-42e1-9ae8-ac891336cd58
ms.openlocfilehash: 5575b108353e9c434ff01e76edc127e8691f0bf4
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96276124"
---
# <a name="security-calls-not-authorized"></a>Appels de sécurité non autorisés

Nom du compteur : Appels de sécurité non autorisés.  
  
## <a name="description"></a>Description  

 Ce compteur est incrémenté lorsque la méthode <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> retourne la valeur `false`. Il indique que le message entrant provient d’un utilisateur valide et qu’il est correctement protégé, mais que l’utilisateur n’est pas autorisé à exécuter des tâches spécifiques.
