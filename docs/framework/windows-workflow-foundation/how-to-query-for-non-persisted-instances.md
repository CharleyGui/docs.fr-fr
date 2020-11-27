---
title: 'Procédure : interroger des instances non persistantes'
ms.date: 03/30/2017
ms.assetid: 294019b1-c1a7-4b81-a14f-b47c106cd723
ms.openlocfilehash: 54a442dab6700dda33cf05df1fb5c60a96bcbd56
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96279998"
---
# <a name="how-to-query-for-non-persisted-instances"></a>Procédure : interroger des instances non persistantes

Lorsqu'une nouvelle instance de service est créée et que le comportement de magasin d'instances de workflow SQL est défini pour le service, l'hôte de service crée une entrée initiale pour cette instance de service dans le magasin d'instances. Par la suite, lorsque l'instance de service persiste pour la première fois, le comportement de magasin d'instances de workflow SQL stocke l'état de l'instance actuelle avec les données supplémentaires qui sont requises pour l'activation, la récupération et le contrôle.

Si une instance n'est pas persistante après la création de l'entrée initiale pour l'instance, l'instance de service est considérée comme étant dans l'état non persistant. Toutes les instances de service persistantes peuvent être interrogées et contrôlées. Les instances de service non persistantes ne peuvent être ni interrogées, ni contrôlées. Si une instance non persistante est interrompue en raison d'une exception non prise en charge, elle peut être interrogée, mais pas contrôlée.

Les instances de service durables qui ne sont pas encore persistantes restent dans un état non persistant dans les scénarios suivants :

- L'hôte de service se bloque avant que l'instance soit persistante pour la première fois. L'entrée initiale pour l'instance reste dans le magasin d'instances. L'instance n'est pas récupérable. Si un message corrélé arrive, l'instance devient à nouveau active.

- L'instance rencontre une exception non prise en charge avant qu'elle soit persistante pour la première fois. Les scénarios suivants se produisent :

  - Si la valeur de la propriété **UnhandledExceptionAction** est définie sur **abandon**, les informations de déploiement du service sont écrites dans le magasin d’instances et l’instance est déchargée de la mémoire. L'instance reste dans l'état non persistant dans la base de données de persistance.

  - Si la valeur de la propriété **UnhandledExceptionAction** est définie sur **AbandonAndSuspend**, les informations de déploiement du service sont écrites dans la base de données de persistance et l’état de l’instance est défini sur **Suspended**. L'instance ne peut pas reprendre, être annulée ou être terminée. L'hôte de service ne peut pas charger l'instance car l'instance n'est pas encore persistante et, par conséquent, l'entrée de base de données pour l'instance n'est pas terminée.

  - Si la valeur de la propriété **UnhandledExceptionAction** est définie sur **Cancel** ou **Terminate**, les informations de déploiement du service sont écrites dans le magasin d’instances et l’état de l’instance est défini sur **Completed**.

Les sections suivantes fournissent des exemples de requêtes pour rechercher des instances non persistantes dans la base de données de persistance SQL et supprimer ces instances de la base de données.

## <a name="to-find-all-instances-not-persisted-yet"></a>Pour rechercher toutes les instances pas encore persistantes

La requête SQL suivante retourne l'ID et l'heure de création de toutes les instances qui ne sont pas encore persistantes dans la base de données de persistance.

```sql
select InstanceId, CreationTime from [System.Activities.DurableInstancing].[Instances] where IsInitialized = 0;
```

## <a name="to-find-all-instances-not-persisted-yet-and-also-not-loaded"></a>Pour rechercher toutes les instances pas encore persistantes et également non chargées

 La requête SQL suivante retourne l'ID et l'heure de création de toutes les instances qui ne sont pas persistantes et qui ne sont pas non plus chargées.

```sql
select InstanceId, CreationTime from [System.Activities.DurableInstancing].[Instances] where IsInitialized = 0 and CurrentMachine is NULL;
```

## <a name="to-find-all-suspended-instances-not-persisted-yet"></a>Pour rechercher toutes les instances interrompues pas encore persistantes

La requête SQL suivante retourne l'ID, l'heure de création, la raison de l'interruption et le nom de l'exception d'interruption de toutes les instances qui ne sont pas persistantes et qui sont également dans un état interrompu.

```sql
select InstanceId, CreationTime, SuspensionReason, SuspensionExceptionName from [System.Activities.DurableInstancing].[Instances] where IsInitialized = 0 and IsSuspended = 1;
```

## <a name="to-delete-non-persisted-instances-from-the-persistence-database"></a>Pour supprimer des instances non persistantes de la base de données de persistance

Vous devez vérifier régulièrement les instances non persistantes dans le magasin d'instances, et les supprimer si vous êtes sûr que l'instance ne recevra pas de message corrélé. Par exemple, si l'instance se trouve dans la base de données depuis plusieurs mois et que vous savez que le workflow a généralement une durée de vie de quelques jours, il est possible de supposer sans risque que c'est une instance non initialisée qui a bloqué.

En général, il est possible de supprimer sans risque des instances non persistantes qui ne sont pas interrompues ou pas chargées. Vous ne devez pas supprimer **toutes** les instances non persistantes, car ce jeu d’instances comprend des instances qui viennent d’être créées mais qui ne sont pas encore persistantes. Vous devez supprimer uniquement les instances non persistantes qui restent car l'hôte du service de workflow sur lequel l'instance était chargée a provoqué une exception ou l'instance elle-même a provoqué une exception.

> [!WARNING]
> La suppression d'instances non persistantes du magasin d'instances diminue la taille du magasin et peut améliorer les performances des opérations de stockage.
