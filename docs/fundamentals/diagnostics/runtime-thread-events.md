---
title: Événements d’exécution ThreadPool
description: Consultez événements du pool de threads du Runtime .NET qui recueillent des informations de diagnostic sur le pool de threads dans .NET Core. Les événements de pool de threads sont les événements de pool de threads de travail ou d’e/s.
ms.date: 11/13/2020
ms.topic: reference
helpviewer_keywords:
- ThreadPool events (CoreCLR)
- ETW, thread pool events (CoreCLR)
ms.openlocfilehash: cdd6041c5842d4922c60e33daf6db366f7d35327
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96588677"
---
# <a name="net-runtime-thread-pool-events"></a>Événements du pool de threads du Runtime .NET

Ces événements collectent des informations sur les threads de travail et d’e/s dans le ThreadPool. Pour plus d’informations sur l’utilisation de ces événements à des fins de diagnostic, consultez [journalisation et traçage d’applications .net](../../core/diagnostics/logging-tracing.md)

## <a name="iothreadcreate_v1-event"></a>Événement IOThreadCreate_V1

 Le tableau suivant montre les mots clés et les niveaux.

|Mot clé pour déclencher l'événement|Level|
|-----------------------------------|-----------|
|`ThreadingKeyword` (0x10000)|Informatif (4)|

 Le tableau ci-dessous montre les informations liées aux événements.

|Événement|ID de l’événement|Moment du déclenchement|
|-----------------------------------|-----------|
|`IOThreadCreate_V1`|44|Un thread d'E/S est créé dans le pool de threads.|

 Le tableau ci-dessous montre les données liées aux événements.

|Nom du champ|Type de données|Description|
|----------------|---------------|-----------------|
|`Count`|`win:UInt64`|Nombre de threads d'E/S, y compris le nouveau thread.|
|`NumRetired`|`win:UInt64`|Nombre de threads de travail retirés|
|`ClrInstanceID`|`win:UInt16`|ID unique de l'instance de CLR ou CoreCLR.|

## <a name="iothreadterminate_v1-event"></a>Événement IOThreadTerminate_V1

 Le tableau suivant montre le mot clé et le niveau

|Mot clé pour déclencher l'événement|Level
|-----------------------------------|-----------
|`ThreadingKeyword` (0x10000)|Informatif (4)

 Le tableau ci-dessous montre les informations liées aux événements.

|Événement|ID de l’événement|Moment du déclenchement|
|-----------|--------------|-----------------|
|`IOThreadTerminate`|45|Un thread d’e/s se termine dans le pool de threads.|

 Le tableau ci-dessous montre les données liées aux événements.

|Nom du champ|Type de données|Description|
|----------------|---------------|-----------------|
|`Count`|`win:UInt64`|Nombre de threads d'E/S restant dans le pool de threads|
|`NumRetired`|`win:UInt64`|Nombre de threads d'E/S retirés|
|`ClrInstanceID`|`win:UInt16`|ID unique de l'instance de CLR ou CoreCLR.|

## <a name="iothreadretire_v1-event"></a>Événement IOThreadRetire_V1

 Le tableau suivant montre les mots clés et les niveaux.

|Mot clé pour déclencher l'événement|Level|
|-----------------------------------|-----------|
|`ThreadingKeyword` (0x10000)|Informatif (4)|

 Le tableau ci-dessous montre les informations liées aux événements.

|Événement|ID de l’événement|Moment du déclenchement|
|-----------|--------------|-----------------|
|`IOThreadRetire_V1`|46|Un thread d'E/S devient candidat au retrait.|

 Le tableau ci-dessous montre les données liées aux événements.

|Nom du champ|Type de données|Description|
|----------------|---------------|-----------------|
|`Count`|`win:UInt64`|Nombre de threads d'E/S restant dans le pool de threads|
|`NumRetired`|`win:UInt64`|Nombre de threads d'E/S retirés|
|`ClrInstanceID`|`win:UInt16`|ID unique de l'instance de CLR ou CoreCLR.|

## <a name="iothreadunretire_v1-event"></a>Événement IOThreadUnretire_V1

 Le tableau suivant montre les mots clés et les niveaux.

|Mot clé pour déclencher l'événement|Level|
|-----------------------------------|-----------|
|`ThreadingKeyword` (0x10000)|Informatif (4)|

 Le tableau ci-dessous montre les informations liées aux événements.

|Événement|ID de l’événement|Moment du déclenchement|
|-----------|--------------|-----------------|
|`IOThreadUnretire_V1`|47|Le retrait d’un thread d'E/S est annulé en raison d'une E/S qui se produit au cours d’une période d'attente après que le thread est devenu un candidat au retrait.|

 Le tableau ci-dessous montre les données liées aux événements.

|Nom du champ|Type de données|Description|
|----------------|---------------|-----------------|
|`Count`|`win:UInt64`|Nombre de threads d'E/S dans le pool de threads, y compris celui-ci|
|`NumRetired`|`win:UInt64`|Nombre de threads d'E/S retirés|
|`ClrInstanceID`|`Win:UInt16`|ID unique de l'instance de CLR ou CoreCLR.|

## <a name="threadpoolworkerthreadstart-event"></a>Événement ThreadPoolWorkerThreadStart

|Mot clé pour déclencher l'événement|Level|
|-----------------------------------|-----------|-----------|
|`ThreadingKeyword` (0x10000)|Informatif (4)|

|Événement|ID de l’événement|Description|
|-----------|--------------|-----------------|
|`ThreadPoolWorkerThreadStart`|50|Un thread de travail est créé.|

|Nom du champ|Type de données|Description|
|----------------|---------------|-----------------|
|`ActiveWorkerThreadCount`|`win:UInt32`|Nombre de threads de travail disponibles pour traiter le travail, y compris ceux qui sont déjà en cours d’utilisation.|
|`RetiredWorkerThreadCount`|`win:UInt32`|Nombre de threads de travail qui ne sont pas disponibles pour traiter le travail, mais qui sont gardés en réserve au cas où des threads supplémentaires seraient requis ultérieurement.|
|`ClrInstanceID`|`win:UInt16`|ID unique de l'instance de CLR ou CoreCLR.|

## <a name="threadpoolworkerthreadstop-event"></a>Événement ThreadPoolWorkerThreadStop

|Mot clé pour déclencher l'événement|Level|
|-----------------------------------|-----------|-----------|
|`ThreadingKeyword` (0x10000)|Informatif (4)|

|Événement|ID de l’événement|Description|
|-----------|--------------|-----------------|
|`ThreadPoolWorkerThreadStop`|51|Un thread de travail est arrêté.|

|Nom du champ|Type de données|Description|
|----------------|---------------|-----------------|
|`ActiveWorkerThreadCount`|`win:UInt32`|Nombre de threads de travail disponibles pour traiter le travail, y compris ceux qui sont déjà en cours d’utilisation.|
|`RetiredWorkerThreadCount`|`win:UInt32`|Nombre de threads de travail qui ne sont pas disponibles pour traiter le travail, mais qui sont gardés en réserve au cas où des threads supplémentaires seraient requis ultérieurement.|
|`ClrInstanceID`|`win:UInt16`|ID unique de l'instance de CLR ou CoreCLR.|

## <a name="threadpoolworkerthreadwait-event"></a>Événement ThreadPoolWorkerThreadWait

|Mot clé pour déclencher l'événement|Level|
|-----------------------------------|-----------|-----------|
|`ThreadingKeyword` (0x10000)|Informatif (4)|

|Événement|ID de l’événement|Description|
|-----------|--------------|-----------------|
|`ThreadPoolWorkerThreadWait`|57|Un thread de travail commence à attendre du travail.|

|Nom du champ|Type de données|Description|
|----------------|---------------|-----------------|
|`ActiveWorkerThreadCount`|`win:UInt32`|Nombre de threads de travail disponibles pour traiter le travail, y compris ceux qui sont déjà en cours d’utilisation.|
|`RetiredWorkerThreadCount`|`win:UInt32`|Nombre de threads de travail qui ne sont pas disponibles pour traiter le travail, mais qui sont gardés en réserve au cas où des threads supplémentaires seraient requis ultérieurement.|
|`ClrInstanceID`|`win:UInt16`|ID unique de l'instance de CLR ou CoreCLR.|

## <a name="threadpoolworkerthreadretirementstart-event"></a>Événement ThreadPoolWorkerThreadRetirementStart

|Mot clé pour déclencher l'événement|Level|
|-----------------------------------|-----------|-----------|
|`ThreadingKeyword` (0x10000)|Informatif (4)|

|Événement|ID de l’événement|Description|
|-----------|--------------|-----------------|
|`ThreadPoolWorkerThreadRetirementStart`|52|Un thread de travail est retiré.|

|Nom du champ|Type de données|Description|
|----------------|---------------|-----------------|
|`ActiveWorkerThreadCount`|`win:UInt32`|Nombre de threads de travail disponibles pour traiter le travail, y compris ceux qui sont déjà en cours d’utilisation.|
|`RetiredWorkerThreadCount`|`win:UInt32`|Nombre de threads de travail qui ne sont pas disponibles pour traiter le travail, mais qui sont gardés en réserve au cas où des threads supplémentaires seraient requis ultérieurement.|
|`ClrInstanceID`|`win:UInt16`|ID unique de l'instance de CLR ou CoreCLR.|

## <a name="threadpoolworkerthreadretirementstop-event"></a>Événement ThreadPoolWorkerThreadRetirementStop

|Mot clé pour déclencher l'événement|Level|
|-----------------------------------|-----------|-----------|
|`ThreadingKeyword` (0x10000)|Informatif (4)|

|Événement|ID de l’événement|Description|
|-----------|--------------|-----------------|
|`ThreadPoolWorkerThreadRetirementStop`|53|Un thread de travail retiré redevient actif.|

|Nom du champ|Type de données|Description|
|----------------|---------------|-----------------|
|`ActiveWorkerThreadCount`|`win:UInt32`|Nombre de threads de travail disponibles pour traiter le travail, y compris ceux qui sont déjà en cours d’utilisation.|
|`RetiredWorkerThreadCount`|`win:UInt32`|Nombre de threads de travail qui ne sont pas disponibles pour traiter le travail, mais qui sont gardés en réserve au cas où des threads supplémentaires seraient requis ultérieurement.|
|`ClrInstanceID`|`win:UInt16`|ID unique de l'instance de CLR ou CoreCLR.|

## <a name="threadpoolworkerthreadadjustmentsample-event"></a>Événement ThreadPoolWorkerThreadAdjustmentSample

 Le tableau suivant montre les mots clés et les niveaux.

|Mot clé pour déclencher l'événement|Level|
|-----------------------------------|-----------|
|`ThreadingKeyword` (0x10000)|Informatif (4)|

 Le tableau ci-dessous montre les informations liées aux événements.

|Événement|ID de l’événement|Description|
|-----------|--------------|-----------------|
|`ThreadPoolWorkerThreadAdjustmentSample`|54|Fait référence à la collecte d'informations pour un exemple. Autrement dit, une mesure de débit avec un certain niveau d’accès concurrentiel à un instant donné.|

 Le tableau ci-dessous montre les données liées aux événements.

|Nom du champ|Type de données|Description|
|----------------|---------------|-----------------|
|`Throughput`|`win:Double`|Nombre d'achèvements par unité de temps|
|`ClrInstanceID`|`win:UInt16`|ID unique de l'instance de CLR ou CoreCLR.|

## <a name="threadpoolworkerthreadadjustmentadjustment-event"></a>Événement ThreadPoolWorkerThreadAdjustmentAdjustment

 Le tableau suivant montre les mots clés et les niveaux.

|Mot clé pour déclencher l'événement|Level|
|-----------------------------------|-----------|
|`ThreadingKeyword` (0x10000)|Informatif (4)|

 Le tableau ci-dessous montre les informations liées aux événements.

|Événement|ID de l’événement|Description|
|-----------|--------------|-----------------|
|`ThreadPoolWorkerThreadAdjustmentAdjustment`|55|Enregistre une modification dans le contrôle, quand l'algorithme d'injection de thread (hill-climbing) détermine qu'une modification du niveau d'accès concurrentiel a eu lieu.|

 Le tableau ci-dessous montre les données liées aux événements.

|Nom du champ|Type de données|Description|
|----------------|---------------|-----------------|
|`AverageThroughput`|`win:Double`|Débit moyen d'un échantillon de mesures|
|`NewWorkerThreadCount`|`win:UInt32`|Nouveau nombre de threads de travail actifs|
|`Reason`|`win:UInt32`|Raison de l'ajustement<br /><br /> `0x0` Chauffage.<br /><br /> `0x1` Initialisation.<br /><br /> `0x2` -Déplacement aléatoire.<br /><br /> `0x3` -Escalade Move.<br /><br /> `0x4` -Changer de point.<br /><br /> `0x5` Stabilisation.<br /><br /> `0x6` Faim.<br /><br /> `0x7` -Expiration du délai d’attente du thread.|
|`ClrInstanceID`|`win:UInt16`|ID unique de l'instance de CLR ou CoreCLR.|

## <a name="threadpoolworkerthreadadjustmentstats-event"></a>Événement ThreadPoolWorkerThreadAdjustmentStats

 Le tableau suivant montre les mots clés et les niveaux.

|Mot clé pour déclencher l'événement|Level|
|-----------------------------------|-----------|
|`ThreadingKeyword` (0x10000)|Détaillé (5)

 Le tableau ci-dessous montre les informations liées aux événements.

|Événement|ID de l’événement|Description|
|-----------|--------------|-----------------|
|`ThreadPoolWorkerThreadAdjustmentStats`|56|Rassemble des données sur le pool de threads.|

 Le tableau suivant présente les données d’événement.

|Nom du champ|Type de données|Description|
|----------------|---------------|-----------------|
|`Duration`|`win:Double`|Durée, en secondes, pendant laquelle ces statistiques ont été collectées.|
|`Throughput`|`win:Double`|Nombre moyen d'achèvements par seconde au cours de cet intervalle.|
|`ThreadWave`|`win:Double`|Réservé à un usage interne.|
|`ThroughputWave`|`win:Double`|Réservé à un usage interne.|
|`ThroughputErrorEstimate`|`win:Double`|Réservé à un usage interne.|
|`AverageThroughputErrorEstimate`|`win:Double`|Réservé à un usage interne.|
|`ThroughputRatio`|`win:Double`|Amélioration relative du débit provoquée par les variations du nombre de threads de travail actifs au cours de cet intervalle.|
|`Confidence`|`win:Double`|Mesure de la validité du champ ThroughputRatio.|
|`NewcontrolSetting`|`win:Double`|Nombre de threads de travail actifs qui servira de référence pour les futures variations du nombre de threads actifs.|
|`NewThreadWaveMagnitude`|`win:UInt16`|Importance des futures variations du nombre de threads actifs.|
|`ClrInstanceID`|`win:UInt16`|ID unique de l'instance de CLR ou CoreCLR.|

## <a name="threadpoolenqueue-event"></a>Événement ThreadPoolEnqueue

 Le tableau suivant montre les mots clés et les niveaux.

|Mot clé pour déclencher l'événement|Level|
|-----------------------------------|-----------|
|`ThreadingKeyword` (0x10000)|Détaillé (5)

 Le tableau ci-dessous montre les informations liées aux événements.

|Événement|ID de l’événement|Description|
|-----------|--------------|-----------------|
|`ThreadPoolEnqueue`|61|Un élément de travail a été mis en file d’attente dans la file d’attente du pool de threads.|

 Le tableau suivant présente les données d’événement.

|Nom du champ|Type de données|Description|
|----------------|---------------|-----------------|
|`WorkID`|`win:Pointer`|Pointeur vers la demande de travail.|
|`ClrInstanceID`|`win:UInt16`|ID unique de l’instance de CoreCLR.|

## <a name="threadpooldequeue-event"></a>Événement ThreadPoolDequeue

 Le tableau suivant montre les mots clés et les niveaux.

|Mot clé pour déclencher l'événement|Level|
|-----------------------------------|-----------|
|`ThreadingKeyword` (0x10000)|Détaillé (5)

 Le tableau ci-dessous montre les informations liées aux événements.

|Événement|ID de l’événement|Description|
|-----------|--------------|-----------------|
|`ThreadPoolDequeue`|62|Un élément de travail a été retiré de la file d’attente du pool de threads.|

 Le tableau suivant présente les données d’événement.

|Nom du champ|Type de données|Description|
|----------------|---------------|-----------------|
|`WorkID`|`win:Pointer`|Pointeur vers la demande de travail.|
|`ClrInstanceID`|`win:UInt16`|ID unique de l’instance de CoreCLR.|

## <a name="threadpoolioenqueue-event"></a>Événement ThreadPoolIOEnqueue

 Le tableau suivant montre les mots clés et les niveaux.

|Mot clé pour déclencher l'événement|Level|
|-----------------------------------|-----------|
|`ThreadingKeyword` (0x10000)|Détaillé (5)

 Le tableau ci-dessous montre les informations liées aux événements.

|Événement|ID de l’événement|Description|
|-----------|--------------|-----------------|
|`ThreadPoolIOEnqueue`|63|Un thread met en file d’attente une notification de fin d’e/s après une fin d’e/s asynchrone.|

 Le tableau suivant présente les données d’événement.

|Nom du champ|Type de données|Description|
|----------------|---------------|-----------------|
|`NativeOverlapped`|`win:Pointer`|Réservé à un usage interne.|
|`Overlapped`|`win:Pointer`|Réservé à un usage interne.|
|`MultiDequeues`|`win:Boolean`|Réservé à un usage interne.|
|`ClrInstanceID`|`win:UInt16`|ID unique de l’instance de CoreCLR.|

## <a name="threadpooliodequeue-event"></a>Événement ThreadPoolIODequeue

 Le tableau suivant montre les mots clés et les niveaux.

|Mot clé pour déclencher l'événement|Level|
|-----------------------------------|-----------|
|`ThreadingKeyword` (0x10000)|Détaillé (5)

 Le tableau ci-dessous montre les informations liées aux événements.

|Événement|ID de l’événement|Description|
|-----------|--------------|-----------------|
|`ThreadPoolIODequeue`|64|Un thread met en file d’attente la notification d’achèvement d’e/s.|

 Le tableau suivant présente les données d’événement.

|Nom du champ|Type de données|Description|
|----------------|---------------|-----------------|
|`NativeOverlapped`|`win:Pointer`|Réservé à un usage interne.|
|`Overlapped`|`win:Pointer`|Réservé à un usage interne.|
|`MultiDequeues`|`win:Boolean`|Réservé à un usage interne.|
|`ClrInstanceID`|`win:UInt16`|ID unique de l’instance de CoreCLR.|

## <a name="threadpooliopack-event"></a>Événement ThreadPoolIOPack

 Le tableau suivant montre les mots clés et les niveaux.

|Mot clé pour déclencher l'événement|Level|
|-----------------------------------|-----------|
|`ThreadingKeyword` (0x10000)|Détaillé (5)|

 Le tableau ci-dessous montre les informations liées aux événements.

|Événement|ID de l’événement|Description|
|-----------|--------------|-----------------|
|`ThreadPoolIOPack`|65|Le pack d’e/s avec chevauchement de pool de threads est appelé.|

 Le tableau suivant présente les données d’événement.

|Nom du champ|Type de données|Description|
|----------------|---------------|-----------------|
|`NativeOverlapped`|`win:Pointer`|Réservé à un usage interne.|
|`Overlapped`|`win:Pointer`|Réservé à un usage interne.|
|`ClrInstanceID`|`win:UInt16`|ID unique de l’instance de CoreCLR.|

## <a name="threadcreating-event"></a>Événement ThreadCreating

 Le tableau suivant présente les mots clés et le niveau.

|Mot clé pour déclencher l'événement|Level|
|-----------------------------------|-----------|
|`ThreadingKeyword` (0x10000)|Informatif (4)|

 Le tableau ci-dessous montre les informations liées aux événements.

|Événement|ID de l’événement|Description|
|----------------|---------------|-----------------|
|`ThreadCreating`|70|Le thread a été créé.|

 Le tableau ci-dessous montre les données liées aux événements.

|Nom du champ|Type de données|Description|
|----------------|---------------|-----------------|
|`ID`|`win:Pointer`|ID du thread|
|`ClrInstanceID`|`win:UInt16`|ID unique de l’instance de CoreCLR.|

## <a name="threadrunning-event"></a>Événement ThreadRunning

 Le tableau suivant présente les mots clés et le niveau.

|Mot clé pour déclencher l'événement|Level|
|-----------------------------------|-----------|
|`ThreadingKeyword` (0x10000)|Informatif (4)|

 Le tableau ci-dessous montre les informations liées aux événements.

|Événement|ID de l’événement|Description|
|----------------|---------------|-----------------|
|`ThreadRunning`|71|Le thread a commencé à s’exécuter.|

 Le tableau ci-dessous montre les données liées aux événements.

|Nom du champ|Type de données|Description|
|----------------|---------------|-----------------|
|`ID`|`win:Pointer`|ID du thread|
|`ClrInstanceID`|`win:UInt16`|ID unique de l’instance de CoreCLR.|
