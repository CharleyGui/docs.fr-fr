---
title: Prise en charge des requêtes
ms.date: 03/30/2017
ms.assetid: 093c22f5-3294-4642-857a-5252233d6796
ms.openlocfilehash: 350644de4a5deb7b8dcb5133c9cc2edb477fd355
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96258437"
---
# <a name="support-for-queries"></a>Prise en charge des requêtes

Le magasin d'instances de workflow SQL enregistre un jeu de propriétés connues dans le magasin. Les utilisateurs peuvent demander des instances à partir de ces propriétés. La liste suivante comprend quelques-unes de ces propriétés connues :  
  
- **Nom du site.** Nom du site Web qui contient le service.  
  
- **Chemin d'accès à l'application relatif.** Chemin d’accès à l’application relatif au site Web.  
  
- **Chemin d'accès au service relatif.** Chemin d’accès au service relatif à l’application.  
  
- **Nom du service.** Nom du service.  
  
- **Espace de noms de service.** Nom de l'espace de noms que le service utilise.  
  
- **Ordinateur actuel.**  
  
- **Dernier ordinateur**. Ordinateur sur lequel l'instance de service de workflow a été exécutée la dernière fois.  
  
> [!NOTE]
> Pour les scénarios auto-hébergés à l'aide de l'hôte du service de workflow, seules les quatre dernières propriétés sont remplies. Pour les scénarios d'application de workflow, seule la dernière propriété est remplie.  
  
 Le runtime du workflow fournit des valeurs pour les trois premières propriétés. L’hôte du service de workflow fournit la valeur pour la propriété **suspendre la raison** . Le magasin d’instances de workflow SQL fournit des valeurs pour la dernière propriété de l' **ordinateur mis à jour** .  
  
 La fonctionnalité de magasin d'instances de workflow SQL vous permet également de spécifier les propriétés personnalisées pour lesquelles vous souhaitez stocker les valeurs dans la base de données de persistance et que vous souhaitez utiliser dans les requêtes. Pour plus d’informations sur les promotions personnalisées, consultez la page [extensibilité du magasin](store-extensibility.md).  
  
## <a name="views"></a>Les vues  

 Le magasin d'instances contient les vues suivantes. Pour plus d’informations, consultez [schéma de base de données de persistance](persistence-database-schema.md) .  
  
### <a name="the-instances-view"></a>Vue Instances  

 La vue Instances contient les champs suivants :  
  
1. **Id**  
  
2. **PendingTimer**  
  
3. **CreationTime**  
  
4. **LastUpdatedTime**  
  
5. **ServiceDeploymentId**  
  
6. **SuspensionExceptionName**  
  
7. **SuspensionReason**  
  
8. **ActiveBookmarks**  
  
9. **CurrentMachine**  
  
10. **LastMachine**  
  
11. **ExecutionStatus**  
  
12. **IsInitialized**  
  
13. **IsSuspended**  
  
14. **IsCompleted**  
  
15. **EncodingOption**  
  
16. **ReadWritePrimitiveDataProperties**  
  
17. **WriteOnlyPrimitiveDataProperties**  
  
18. **ReadWriteComplexDataProperties**  
  
19. **WriteOnlyComplexDataProperties**  
  
### <a name="the-servicedeployments-view"></a>Vue ServiceDeployments  

 La vue ServiceDeployments contient les champs suivants :  
  
1. **SiteName**  
  
2. **RelativeServicePath**  
  
3. **RelativeApplicationPath**  
  
4. **FormName**  
  
5. **ServiceNamespace**  
  
### <a name="the-instancepromotedproperties-view"></a>Vue InstancePromotedProperties  

 La vue InstancePromotedProperties contient les champs suivants. Pour plus d’informations sur les propriétés promues, consultez la rubrique extensibilité de la [Banque](store-extensibility.md) .  
  
1. **InstanceId**  
  
2. **EncodingOption**  
  
3. **PromotionName**  
  
4. **Valeur #** (une plage de champs de **value1** à **Value64**).
