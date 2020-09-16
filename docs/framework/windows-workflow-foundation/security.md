---
title: Sécurité
ms.date: 03/30/2017
ms.assetid: 737ec121-bfc5-4b75-a504-2d53c2c8af39
ms.openlocfilehash: 09614a4528e83898c894506a99c5992c506b7961
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90559237"
---
# <a name="security"></a>Sécurité
Le magasin d'instances de workflow SQL utilise les rôles de sécurité de base de données suivants pour sécuriser l'accès aux informations d'état de l'instance dans la base de données de persistance.  
  
- **System. Activities. DurableInstancing. InstanceStoreUsers**. Ce rôle dispose d'un accès en lecture et en écriture aux vues publiques et de droits d'exécution sur les procédures stockées impliquées dans la création, le chargement et l'enregistrement des instances.  
  
- **System. Activities. DurableInstancing. InstanceStoreObservers**. Ce rôle dispose d'un accès en lecture seule aux vues publiques.  
  
- **System. Activities. DurableInstancing. WorkflowActivationUsers**. Ce rôle a des droits d'exécution aux procédures stockées impliquées dans le processus de l'activation de l'instance. Pour plus d’informations sur l’activation d’instance, consultez [activation d’instance](instance-activation.md). Le compte d’utilisateur sous lequel un hôte générique (tel que le service de gestion de flux de travail des fonctionnalités d’hébergement de Windows Server AppFabric) s’exécute doit être ajouté à ce rôle de base de données.  
  
 Pour plus d’informations sur la sécurité des magasins de persistance avec Windows Server App fabric, consultez [configuration de la sécurité pour les magasins de persistance dans l’application Fabric](/previous-versions/appfabric/ff431727(v=azure.10)) .  
  
> [!CAUTION]
> Un client qui a accès à ses propres données d'instance dans le magasin d'instances a accès à toutes les autres instances dans le même magasin d'instances. Le magasin d'instances ne prend pas en charge les autorisations de sécurité au niveau de l'instance. Vous devez créer des magasins d'instances distincts et mapper des groupes/utilisateurs différents pour avoir accès aux différents magasins.
