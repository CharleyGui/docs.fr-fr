---
title: 'Procédure : créer un participant de persistance personnalisé'
ms.date: 03/30/2017
ms.assetid: 1d9cc47a-8966-4286-94d5-4221403d9c06
ms.openlocfilehash: 633961ac12eed593613eba75862cbc81f2fa68c6
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96275812"
---
# <a name="how-to-create-a-custom-persistence-participant"></a>Procédure : créer un participant de persistance personnalisé

La procédure suivante permet de créer un participant de persistance. Pour obtenir des exemples d’implémentations de participants de persistance, consultez la rubrique participant à l’exemple de [persistance](/previous-versions/dotnet/netframework-4.0/dd699769(v=vs.100)) Sample and [Store Extensibility](store-extensibility.md) .  
  
1. Créez une classe dérivant des classes <xref:System.Activities.Persistence.PersistenceParticipant> ou <xref:System.Activities.Persistence.PersistenceIOParticipant>. La classe PersistenceIOParticipant offre les mêmes points d’extensibilité que la classe PersistenceParticipant, en plus de pouvoir participer aux opérations d’e/s. Effectuez l'une ou l'ensemble des étapes suivantes :  
  
2. Implémentez la méthode <xref:System.Activities.Persistence.PersistenceParticipant.CollectValues%2A>. La méthode **CollectValues** a deux paramètres de dictionnaire, l’un pour le stockage des valeurs en lecture/écriture et l’autre pour le stockage des valeurs en écriture seule (utilisé ultérieurement dans les requêtes). Dans cette méthode, vous devez remplir ces dictionnaires avec les données propres à un participant de persistance. Chaque dictionnaire contient le nom de la valeur comme clé et la valeur elle-même comme un objet <xref:System.Runtime.DurableInstancing.InstanceValue>.  
  
    Les valeurs du dictionnaire readWriteValues sont empaquetées en tant qu’objets **InstanceValue** . Les valeurs du dictionnaire en écriture seule sont empaquetées en tant qu’objets **InstanceValue** avec InstanceValueOptions. optional et InstanceValueOption. WriteOnly Set. Chaque **InstanceValue** fourni par les implémentations de **CollectValues** sur tous les participants de persistance doit avoir un nom unique.
  
    ```csharp  
    protected virtual void CollectValues(out IDictionary<XName,Object> readWriteValues, out IDictionary<XName,Object> writeOnlyValues)
    {
    }
    ```  
  
3. Implémentez la méthode <xref:System.Activities.Persistence.PersistenceParticipant.MapValues%2A>. La méthode **MapValues** prend deux paramètres similaires aux paramètres que la méthode **CollectValues** reçoit. Toutes les valeurs collectées dans l’étape **CollectValues** sont passées via ces paramètres de dictionnaire. Les nouvelles valeurs ajoutées par l’étape **MapValues** sont ajoutées aux valeurs en écriture seule.  Le dictionnaire en écriture seule est utilisé pour fournir des données à une source externe qui n'est pas directement associée aux valeurs d'instance. Chaque valeur fournie par les implémentations de la méthode **MapValues** sur tous les participants de persistance doit avoir un nom unique.  
  
    ```csharp  
    protected virtual IDictionary<XName,Object> MapValues(IDictionary<XName,Object> readWriteValues,IDictionary<XName,Object> writeOnlyValues)
    {
    }
    ```  
  
     La méthode <xref:System.Activities.Persistence.PersistenceParticipant.MapValues%2A> fournit des fonctionnalités non fournies par la méthode <xref:System.Activities.Persistence.PersistenceParticipant.CollectValues%2A>, car elle permet une dépendance sur une autre valeur fournie par un autre participant de persistance qui n'a pas encore été traité par <xref:System.Activities.Persistence.PersistenceParticipant.CollectValues%2A>.  
  
4. Implémentez la méthode **PublishValues** . La méthode **PublishValues** reçoit un dictionnaire contenant toutes les valeurs chargées à partir du magasin de persistance.  
  
    ```csharp  
    protected virtual void PublishValues(IDictionary<XName,Object> readWriteValues)
    {
    }
    ```  
  
5. Implémentez la méthode **BeginOnSave** si le participant est un participant d’e/s de persistance. Cette méthode est appelée lors d'une opération d'enregistrement. Dans cette méthode, vous devez exécuter des e/s complémentaires pour les instances de workflow persistantes (enregistrement).  Si l’hôte utilise une transaction pour la commande de persistance correspondante, la même transaction est fournie dans Transaction.Current.  En outre, les PersistenceIOParticipants peuvent rendre publique une spécification de cohérence transactionnelle. Dans ce cas, l’hôte crée une transaction pour l’épisode de persistance si aucune transaction ne serait utilisée sinon.  
  
    ```csharp  
    protected virtual IAsyncResult BeginOnSave(IDictionary<XName,Object> readWriteValues, IDictionary<XName,Object> writeOnlyValues, TimeSpan timeout, AsyncCallback callback, Object state)
    {
    }
    ```  
  
6. Implémentez la méthode **BeginOnLoad** si le participant est un participant d’e/s de persistance. Cette méthode est appelée lors d'une opération de chargement. Dans cette méthode, vous devez exécuter des e/s complémentaires pour le chargement d’instances de Workflow. Si l’hôte utilise une transaction pour la commande de persistance correspondante, la même transaction est fournie dans Transaction.Current. En outre, les participants d’e/s de persistance peuvent annoncer une exigence de cohérence transactionnelle. dans ce cas, l’hôte crée une transaction pour l’épisode de persistance, si aucune n’est utilisée autrement.  
  
    ```csharp  
    protected virtual IAsyncResult BeginOnLoad(IDictionary<XName,Object> readWriteValues, TimeSpan timeout, AsyncCallback callback, Object state)
    {
    }
    ```
