---
title: Sécurité
ms.date: 03/30/2017
ms.assetid: 737ec121-bfc5-4b75-a504-2d53c2c8af39
ms.openlocfilehash: f47b75fa1fd345869f560326861ebc31e6b5e1a9
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70045315"
---
# <a name="security"></a>Sécurité
Le magasin d'instances de workflow SQL utilise les rôles de sécurité de base de données suivants pour sécuriser l'accès aux informations d'état de l'instance dans la base de données de persistance.  
  
- **System.Activities.DurableInstancing.InstanceStoreUsers**. Ce rôle dispose d'un accès en lecture et en écriture aux vues publiques et de droits d'exécution sur les procédures stockées impliquées dans la création, le chargement et l'enregistrement des instances.  
  
- **System.Activities.DurableInstancing.InstanceStoreObservers**. Ce rôle dispose d'un accès en lecture seule aux vues publiques.  
  
- **System.Activities.DurableInstancing.WorkflowActivationUsers**. Ce rôle a des droits d'exécution aux procédures stockées impliquées dans le processus de l'activation de l'instance. Pour plus d’informations sur l’activation d’instance, consultez [activation d’instance](instance-activation.md). Le compte d’utilisateur sous lequel un hôte générique (tel que le service de gestion de flux de travail des fonctionnalités d’hébergement de Windows Server AppFabric) s’exécute doit être ajouté à ce rôle de base de données.  
  
 Pour plus d’informations sur la sécurité des magasins de persistance avec Windows Server App fabric, consultez [configuration de la sécurité pour les magasins de persistance dans l’application Fabric](https://go.microsoft.com/fwlink/?LinkId=201208) .  
  
> [!CAUTION]
> Un client qui a accès à ses propres données d'instance dans le magasin d'instances a accès à toutes les autres instances dans le même magasin d'instances. Le magasin d'instances ne prend pas en charge les autorisations de sécurité au niveau de l'instance. Vous devez créer des magasins d'instances distincts et mapper des groupes/utilisateurs différents pour avoir accès aux différents magasins.
