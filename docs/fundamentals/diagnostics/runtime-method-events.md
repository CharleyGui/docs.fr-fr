---
title: Événements d’exécution de méthode
description: Consultez événements du Runtime .NET qui recueillent des informations de diagnostic spécifiques aux méthodes, telles que les événements de méthode CLR, le marqueur de méthode CLR ou les événements détaillés de méthode CLR et MethodJittingStarted.
ms.date: 11/13/2020
helpviewer_keywords:
- Method events (CoreCLR)
- ETW, EventPipe, LTTng method events (CoreCLR)
ms.openlocfilehash: f9d08efa420670cf7a8c863f115ff270998f2dca
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2020
ms.locfileid: "96588594"
---
# <a name="net-runtime-method-events"></a>Événements de la méthode Runtime .NET

Ces événements collectent des informations spécifiques aux méthodes. La charge utile de ces événements est requise pour la résolution des symboles. En outre, ces événements fournissent des informations utiles, telles que des méthodes qui sont chargées et déchargées. Pour plus d’informations sur l’utilisation de ces événements à des fins de diagnostic, consultez [journalisation et traçage d’applications .net](../../core/diagnostics/logging-tracing.md)

Tous les événements de méthode ont le niveau « Informations (4) ». Tous les événements détaillés de méthode ont le niveau « Détaillé (5) ».

Tous les événements de méthode sont déclenchés par le mot clé `JITKeyword` (0x10) ou `NGenKeyword` (0x20) sous le fournisseur de runtime, ou par le mot clé `JitRundownKeyword` (0x10) ou `NGENRundownKeyword` (0x20) sous le fournisseur d’arrêt.

Les versions v2 de ces événements incluent ReJITID, pas les versions v1.

## <a name="methodload_v1-event"></a>Événement MethodLoad_V1

Le tableau ci-dessous montre les informations liées aux événements.

|Événement|ID de l’événement|Description|
|-----------|--------------|-----------------|
|`MethodLoad_V1`|141|Déclenché quand une méthode est chargée juste-à-temps (JIT) ou quand une image NGEN est chargée. Les méthodes dynamiques et génériques n'utilisent pas cette version pour les chargements de méthodes. Les programmes d'assistance JIT n'utilisent jamais cette version.|

|Mot clé pour déclencher l'événement|Level|
|-----------------------------------|-----------|
|`JITKeyword` (0x10)|Informatif (4)|
|`NGenKeyword` (0x20)|Informatif (4)|

|Nom du champ|Type de données|Description|
|----------------|---------------|-----------------|
|`MethodID`|`win:UInt64`|Identificateur unique d’une méthode. Pour les méthodes d'assistance JIT, sa valeur correspond à l'adresse de début de la méthode.|
|`ModuleID`|`win:UInt64`|Identificateur du module auquel cette méthode appartient (0 pour les programmes d'assistance JIT).|
|`MethodStartAddress`|`win:UInt64`|Adresse de début de la méthode.|
|`MethodSize`|`win:UInt32`|Taille de la méthode.|
|`MethodToken`|`win:UInt32`|0 pour les méthodes dynamiques et les programmes d'assistance JIT.|
|`MethodFlags`|`win:UInt32`|0x1 : méthode dynamique.<br /><br /> 0x2 : méthode générique.<br /><br /> 0x4 : méthode de code compilé juste-à-temps (JIT) (ou code d'image natif NGEN).<br /><br /> 0x8 : méthode d'assistance.|
|`ClrInstanceID`|`win:UInt16`|ID unique de l’instance de CoreCLR.|

## <a name="methodload_v2-event"></a>Événement MethodLoad_V2

|Événement|ID de l’événement|Description|
|----------------|---------------|-----------------|
|`MethodLoad_V2`|141|Déclenché quand une méthode est chargée juste-à-temps (JIT) ou quand une image NGEN est chargée. Les méthodes dynamiques et génériques n'utilisent pas cette version pour les chargements de méthodes. Les programmes d'assistance JIT n'utilisent jamais cette version.|

|Mot clé pour déclencher l'événement|Level|
|-----------------------------------|-----------|
|`JITKeyword` (0x10)|Informatif (4)|
|`NGenKeyword` (0x20)|Informatif (4)|

|Nom du champ|Type de données|Description|
|----------------|---------------|-----------------|
|`MethodID`|`win:UInt64`|Identificateur unique d’une méthode. Pour les méthodes d'assistance JIT, sa valeur correspond à l'adresse de début de la méthode.|
|`ModuleID`|`win:UInt64`|Identificateur du module auquel cette méthode appartient (0 pour les programmes d'assistance JIT).|
|`MethodStartAddress`|`win:UInt64`|Adresse de début de la méthode.|
|`MethodSize`|`win:UInt32`|Taille de la méthode.|
|`MethodToken`|`win:UInt32`|0 pour les méthodes dynamiques et les programmes d'assistance JIT.|
|`MethodFlags`|`win:UInt32`|0x1 : méthode dynamique.<br /><br /> 0x2 : méthode générique.<br /><br /> 0x4 : méthode de code compilé juste-à-temps (JIT) (ou code d'image natif NGEN).<br /><br /> 0x8 : méthode d'assistance.|
|`ReJITID`|`win:UInt64`|ID ReJIT de la méthode.|
|`ClrInstanceID`|`win:UInt16`|ID unique de l’instance de CoreCLR.|

## <a name="methodunload_v1-event"></a>Événement MethodUnLoad_V1

|Événement|ID de l’événement|Description|
|----------------|---------------|-----------------|
|`MethodUnLoad_V1`|142|Déclenché quand un module est déchargé ou quand un domaine d'application est détruit. Les méthodes dynamiques n'utilisent jamais cette version pour les déchargements de méthodes.|

|Mot clé pour déclencher l'événement|Level|
|-----------------------------------|-----------|
|`JITKeyword` (0x10)|Informatif (4)|
|`NGenKeyword` 0x20|Informatif (4)|

|Nom du champ|Type de données|Description|
|----------------|---------------|-----------------|
|`MethodID`|`win:UInt64`|Identificateur unique d’une méthode. Pour les méthodes d'assistance JIT, sa valeur correspond à l'adresse de début de la méthode.|
|`ModuleID`|`win:UInt64`|Identificateur du module auquel cette méthode appartient (0 pour les programmes d'assistance JIT).|
|`MethodStartAddress`|`win:UInt64`|Adresse de début de la méthode.|
|`MethodSize`|`win:UInt32`|Taille de la méthode.|
|`MethodToken`|`win:UInt32`|0 pour les méthodes dynamiques et les programmes d'assistance JIT.|
|`MethodFlags`|`win:UInt32`|0x1 : méthode dynamique.<br /><br /> 0x2 : méthode générique.<br /><br /> 0x4 : méthode de code compilé juste-à-temps (JIT) (ou code d'image natif NGEN).<br /><br /> 0x8 : méthode d'assistance.|
|`ClrInstanceID`|`win:UInt16`|ID unique de l’instance de CoreCLR.|

## <a name="methodunload_v2-event"></a>Événement MethodUnLoad_V2

|Événement|ID de l’événement|Description|
|----------------|---------------|-----------------|
|`MethodUnLoad_V2`|142|Déclenché quand un module est déchargé ou quand un domaine d'application est détruit. Les méthodes dynamiques n'utilisent jamais cette version pour les déchargements de méthodes.|

|Mot clé pour déclencher l'événement|Level|
|-----------------------------------|-----------|
|`JITKeyword` (0x10)|Informatif (4)|
|`NGenKeyword` 0x20|Informatif (4)|

|Nom du champ|Type de données|Description|
|----------------|---------------|-----------------|
|`MethodID`|`win:UInt64`|Identificateur unique d’une méthode. Pour les méthodes d'assistance JIT, sa valeur correspond à l'adresse de début de la méthode.|
|`ModuleID`|`win:UInt64`|Identificateur du module auquel cette méthode appartient (0 pour les programmes d'assistance JIT).|
|`MethodStartAddress`|`win:UInt64`|Adresse de début de la méthode.|
|`MethodSize`|`win:UInt32`|Taille de la méthode.|
|`MethodToken`|`win:UInt32`|0 pour les méthodes dynamiques et les programmes d'assistance JIT.|
|`MethodFlags`|`win:UInt32`|0x1 : méthode dynamique.<br /><br /> 0x2 : méthode générique.<br /><br /> 0x4 : méthode de code compilé juste-à-temps (JIT) (ou code d'image natif NGEN).<br /><br /> 0x8 : méthode d'assistance.|
|`ReJITID`|`win:UInt64`|ID ReJIT de la méthode.|
|`ClrInstanceID`|`win:UInt16`|ID unique de l’instance de CoreCLR.|

## <a name="r2rgetentrypoint-event"></a>Événement R2RGetEntryPoint

|Événement|ID de l’événement|Description|
|----------------|---------------|-----------------|
|`R2RGetEntryPoint`|159|Déclenché quand une recherche de point d’entrée R2R se termine.|

|Mot clé pour déclencher l'événement|Level|
|-----------------------------------|-----------|
|`JITKeyword` (0x10) |Informatif (4)|
|`NGenKeyword` 0x20 |Informatif (4)|

|Nom du champ|Type de données|Description|
|----------------|---------------|-----------------|
|`MethodID`|`win:UInt64`|Identificateur unique d’une méthode R2R.|
|`MethodNamespace`|`win:UnicodeString`|Espace de noms de la méthode recherchée.|
|`MethodName`|`win:UnicodeString`|Nom de la méthode recherchée.|
|`MethodSignature`|`win:UnicodeString`|Signature de la méthode (liste de noms de types séparés par des virgules).|
|`EntryPoint`|`win:UInt64`|Pointeur vers le point d’entrée de la méthode R2R|
|`ClrInstanceID`|`win:UInt16`|ID unique de l’instance de CoreCLR.|

## <a name="r2rgetentrypointstart-event"></a>Événement R2RGetEntryPointStart

|Événement|ID de l’événement|Description|
|----------------|---------------|-----------------|
|`R2RGetEntryPointStart`|160|Déclenché lors du démarrage d’une recherche de point d’entrée R2R.|

|Mot clé pour déclencher l'événement|Level|
|-----------------------------------|-----------|
|`JITKeyword` (0x10) |Informatif (4)|
|`NGenKeyword` 0x20 |Informatif (4)|

|Nom du champ|Type de données|Description|
|----------------|---------------|-----------------|
|`MethodID`|`win:UInt64`|Identificateur unique d’une méthode R2R.|
|`ClrInstanceID`|`win:UInt16`|ID unique de l’instance de CoreCLR.|

## <a name="methodloadverbose_v1-event"></a>Événement MethodLoadVerbose_V1

|Événement|ID de l’événement|Description|
|-----------|--------------|-----------------|
|`MethodLoadVerbose_V1`|143|Déclenché quand une méthode est chargée juste-à-temps (JIT) ou quand une image NGEN est chargée. Les méthodes dynamiques et génériques utilisent toujours cette version pour les chargements de méthodes. Les programmes d'assistance JIT utilisent toujours cette version.|

|Mot clé pour déclencher l'événement|Level|
|-----------------------------------|-----------|
|`JITKeyword` (0x10) |Informatif (4)|
|`NGenKeyword` 0x20 |Informatif (4)|

|Nom du champ|Type de données|Description|
|----------------|---------------|-----------------|
|`MethodID`|`win:UInt64`|Identificateur unique de la méthode. Pour les méthodes d'assistance JIT, sa valeur correspond à l'adresse de début de la méthode.|
|`ModuleID`|`win:UInt64`|Identificateur du module auquel cette méthode appartient (0 pour les programmes d'assistance JIT).|
|`MethodStartAddress`|`win:UInt64`|Adresse de début.|
|`MethodSize`|`win:UInt32`|Longueur de la méthode.|
|`MethodToken`|`win:UInt32`|0 pour les méthodes dynamiques et les programmes d'assistance JIT.|
|`MethodFlags`|`win:UInt32`|0x1 : méthode dynamique.<br /><br /> 0x2 : méthode générique.<br /><br /> 0x4 : méthode compilée juste-à-temps (JIT) (ou générée par NGen.exe)<br /><br /> 0x8 : méthode d'assistance.|
|`MethodNameSpace`|`win:UnicodeString`|Nom d'espace de noms complet associé à la méthode.|
|`MethodName`|`win:UnicodeString`|Nom complet de classe associé à la méthode.|
|`MethodSignature`|`win:UnicodeString`|Signature de la méthode (liste de noms de types séparés par des virgules).|
|`ClrInstanceID`|`win:UInt16`|ID unique de l’instance de CoreCLR.|

## <a name="methodloadverbose_v2-event"></a>Événement MethodLoadVerbose_V2

|Événement|ID de l’événement|Description|
|-----------|--------------|-----------------|
|`MethodLoadVerbose_V1`|143|Déclenché quand une méthode est chargée juste-à-temps (JIT) ou quand une image NGEN est chargée. Les méthodes dynamiques et génériques utilisent toujours cette version pour les chargements de méthodes. Les programmes d'assistance JIT utilisent toujours cette version.|

|Mot clé pour déclencher l'événement|Level|
|-----------------------------------|-----------|
|`JITKeyword` (0x10) |Informatif (4)|
|`NGenKeyword` 0x20 |Informatif (4)|

|Nom du champ|Type de données|Description|
|----------------|---------------|-----------------|
|`MethodID`|`win:UInt64`|Identificateur unique de la méthode. Pour les méthodes d'assistance JIT, sa valeur correspond à l'adresse de début de la méthode.|
|`ModuleID`|`win:UInt64`|Identificateur du module auquel cette méthode appartient (0 pour les programmes d'assistance JIT).|
|`MethodStartAddress`|`win:UInt64`|Adresse de début.|
|`MethodSize`|`win:UInt32`|Longueur de la méthode.|
|`MethodToken`|`win:UInt32`|0 pour les méthodes dynamiques et les programmes d'assistance JIT.|
|`MethodFlags`|`win:UInt32`|0x1 : méthode dynamique.<br /><br /> 0x2 : méthode générique.<br /><br /> 0x4 : méthode compilée juste-à-temps (JIT) (ou générée par NGen.exe)<br /><br /> 0x8 : méthode d'assistance.|
|`MethodNameSpace`|`win:UnicodeString`|Nom d'espace de noms complet associé à la méthode.|
|`MethodName`|`win:UnicodeString`|Nom complet de classe associé à la méthode.|
|`MethodSignature`|`win:UnicodeString`|Signature de la méthode (liste de noms de types séparés par des virgules).|
|`ReJITID`|`win:UInt64`|ID ReJIT de la méthode.|
|`ClrInstanceID`|`win:UInt16`|ID unique de l’instance de CoreCLR.|

## <a name="methodunloadverbose_v1-event"></a>Événement MethodUnLoadVerbose_V1

|Événement|ID de l’événement|Description|
|-----------|--------------|-----------------|
|`MethodUnLoadVerbose_V1`|144|Déclenché quand une méthode dynamique est détruite, quand un module est déchargé ou quand un domaine d'application est détruit. Les méthodes dynamiques utilisent toujours cette version pour les déchargements de méthodes.|

|Mot clé pour déclencher l'événement|Level|
|-----------------------------------|-----------|
|`JITKeyword` (0x10) |Informatif (4)|
|`NGenKeyword` 0x20 |Informatif (4)|

|Nom du champ|Type de données|Description|
|----------------|---------------|-----------------|
|`MethodID`|`win:UInt64`|Identificateur unique de la méthode. Pour les méthodes d'assistance JIT, sa valeur correspond à l'adresse de début de la méthode.|
|`ModuleID`|`win:UInt64`|Identificateur du module auquel cette méthode appartient (0 pour les programmes d'assistance JIT).|
|`MethodStartAddress`|`win:UInt64`|Adresse de début.|
|`MethodSize`|`win:UInt32`|Longueur de la méthode.|
|`MethodToken`|`win:UInt32`|0 pour les méthodes dynamiques et les programmes d'assistance JIT.|
|`MethodFlags`|`win:UInt32`|0x1 : méthode dynamique.<br /><br /> 0x2 : méthode générique.<br /><br /> 0x4 : méthode compilée juste-à-temps (JIT) (ou générée par NGen.exe)<br /><br /> 0x8 : méthode d'assistance.|
|`MethodNameSpace`|`win:UnicodeString`|Nom d'espace de noms complet associé à la méthode.|
|`MethodName`|`win:UnicodeString`|Nom complet de classe associé à la méthode.|
|`MethodSignature`|`win:UnicodeString`|Signature de la méthode (liste de noms de types séparés par des virgules).|
|`ClrInstanceID`|`win:UInt16`|ID unique de l’instance de CoreCLR.|

## <a name="methodunloadverbose_v2-event"></a>Événement MethodUnLoadVerbose_V2

|Événement|ID de l’événement|Description|
|-----------|--------------|-----------------|
|`MethodUnLoadVerbose_V2`|144|Déclenché quand une méthode dynamique est détruite, quand un module est déchargé ou quand un domaine d'application est détruit. Les méthodes dynamiques utilisent toujours cette version pour les déchargements de méthodes.|

|Mot clé pour déclencher l'événement|Level|
|-----------------------------------|-----------|
|`JITKeyword` (0x10) |Informatif (4)|
|`NGenKeyword` 0x20 |Informatif (4)|

|Nom du champ|Type de données|Description|
|----------------|---------------|-----------------|
|`MethodID`|`win:UInt64`|Identificateur unique de la méthode. Pour les méthodes d'assistance JIT, sa valeur correspond à l'adresse de début de la méthode.|
|`ModuleID`|`win:UInt64`|Identificateur du module auquel cette méthode appartient (0 pour les programmes d'assistance JIT).|
|`MethodStartAddress`|`win:UInt64`|Adresse de début.|
|`MethodSize`|`win:UInt32`|Longueur de la méthode.|
|`MethodToken`|`win:UInt32`|0 pour les méthodes dynamiques et les programmes d'assistance JIT.|
|`MethodFlags`|`win:UInt32`|0x1 : méthode dynamique.<br /><br /> 0x2 : méthode générique.<br /><br /> 0x4 : méthode compilée juste-à-temps (JIT) (ou générée par NGen.exe)<br /><br /> 0x8 : méthode d'assistance.|
|`MethodNameSpace`|`win:UnicodeString`|Nom d'espace de noms complet associé à la méthode.|
|`MethodName`|`win:UnicodeString`|Nom complet de classe associé à la méthode.|
|`MethodSignature`|`win:UnicodeString`|Signature de la méthode (liste de noms de types séparés par des virgules).|
|`ReJITID`|`win:UInt64`|ID ReJIT de la méthode.|
|`ClrInstanceID`|`win:UInt16`|ID unique de l’instance de CoreCLR.|

## <a name="methodjittingstarted_v1-event"></a>Événement MethodJittingStarted_V1

Le tableau suivant montre les mots clés et les niveaux.

|Mot clé pour déclencher l'événement|Level|
|-----------------------------------|-----------|
|`JITKeyword` (0x10) |Détaillé (5)|
|`NGenKeyword` 0x20 |Détaillé (5)|

|Événement|ID de l’événement|Description|
|-----------|--------------|-----------------|
|`MethodJittingStarted_V1`|145|Déclenché quand une méthode est compilée juste-à-temps (JIT).|

|Nom du champ|Type de données|Description|
|----------------|---------------|-----------------|
|`MethodID`|`win:UInt64`|Identificateur unique de la méthode.|
|`ModuleID`|`win:UInt64`|Identificateur du module auquel cette méthode appartient.|
|`MethodToken`|`win:UInt32`|0 pour les méthodes dynamiques et les programmes d'assistance JIT.|
|`MethodILSize`|`win:UInt32`|Taille du Common Intermediate Language (CIL) pour la méthode qui est compilée juste-à-temps (JIT).|
|`MethodNameSpace`|`win:UnicodeString`|Nom complet de classe associé à la méthode.|
|`MethodName`|`win:UnicodeString`|Nom de la méthode.|
|`MethodSignature`|`win:UnicodeString`|Signature de la méthode (liste de noms de types séparés par des virgules).|
|`ClrInstanceID`|`win:UInt16`|ID unique de l’instance de CoreCLR.|

## <a name="methodjitinliningsucceeded-event"></a>Événement MethodJitInliningSucceeded

|Mot clé pour déclencher l'événement|Level|
|-----------------------------------|-----------|
|`JITTracingKeyword` 0x1000 |Détaillé (5)|

|Événement|ID de l’événement|Description|
|-----------|--------------|-----------------|
|`MethodJitInliningSucceeded`|185|Déclenché quand une méthode est correctement Inline par le compilateur JIT.|

|Nom du champ|Type de données|Description|
|----------------|---------------|-----------------|
|`MethodBeingCompiledNamespace`|`win:UnicodeString`|Espace de noms de la méthode en cours de compilation.|
|`MethodBeingCompiledName`|`win:UnicodeString`|Nom de la méthode en cours de compilation.|
|`MethodBeingCompiledNameSignature`|`win:UnicodeString`|Signature de la méthode (liste de noms de types séparés par des virgules) en cours de compilation.|
|`InlinerNamespace`|`win:UnicodeString`|Espace de noms de la méthode inline ("parent").|
|`InlinerName`|`win:UnicodeString`|Nom de la méthode inline ("parent").|
|`InlinerNameSignature`|`win:UnicodeString`|Signature de la méthode inlineer (« parent ») (liste séparée par des virgules des noms de types).|
|`InlineeNamespace`|`win:UnicodeString`|Espace de noms de la méthode inline (« Child »).|
|`InlineeName`|`win:UnicodeString`|Nom de la méthode inline (« Child »).|
|`InlineeNameSignature`|`win:UnicodeString`|Signature de la méthode inline (« Child ») (liste de noms de types séparés par des virgules).|
|`ClrInstanceID`|`win:UInt16`|ID unique de l’instance de CoreCLR.|

## <a name="methodjitinliningfailed-event"></a>Événement MethodJitInliningFailed

|Mot clé pour déclencher l'événement|Level|
|-----------------------------------|-----------|
|`JITTracingKeyword` 0x1000 |Détaillé (5)|

|Événement|ID de l’événement|Description|
|-----------|--------------|-----------------|
|`MethodJitInliningFailed`|192|Déclenché lorsqu’une méthode n’a pas pu être inline par le compilateur JIT.|

|Nom du champ|Type de données|Description|
|----------------|---------------|-----------------|
|`MethodBeingCompiledNamespace`|`win:UnicodeString`|Espace de noms de la méthode en cours de compilation.|
|`MethodBeingCompiledName`|`win:UnicodeString`|Nom de la méthode en cours de compilation.|
|`MethodBeingCompiledNameSignature`|`win:UnicodeString`|Signature de la méthode (liste de noms de types séparés par des virgules) en cours de compilation.|
|`InlinerNamespace`|`win:UnicodeString`|Espace de noms de la méthode inline ("parent").|
|`InlinerName`|`win:UnicodeString`|Nom de la méthode inline ("parent").|
|`InlinerNameSignature`|`win:UnicodeString`|Signature de la méthode inlineer (« parent ») (liste séparée par des virgules des noms de types).|
|`InlineeNamespace`|`win:UnicodeString`|Espace de noms de la méthode inline (« Child »).|
|`InlineeName`|`win:UnicodeString`|Nom de la méthode inline (« Child »).|
|`InlineeNameSignature`|`win:UnicodeString`|Signature de la méthode inline (« Child ») (liste de noms de types séparés par des virgules).|
|`FailAlways`|`win:Boolean`|Indique si la méthode est marquée comme non peut être Inline.|
|`FailReason`|`win:UnicodeString`|Raison de l’échec de l’incorporation.|
|`ClrInstanceID`|`win:UInt16`|ID unique de l’instance de CoreCLR.|

## <a name="methodjittailcallsucceeded-event"></a>Événement MethodJitTailCallSucceeded

|Mot clé pour déclencher l'événement|Level|
|-----------------------------------|-----------|
|`JITTracingKeyword` 0x1000 |Détaillé (5)|

|Événement|ID de l’événement|Description|
|-----------|--------------|-----------------|
|`MethodJitTailCallSucceeded`|192|Déclenché par le compilateur JIT lorsque la fin d’une méthode peut être appelée avec succès.|

|Nom du champ|Type de données|Description|
|----------------|---------------|-----------------|
|`MethodBeingCompiledNamespace`|`win:UnicodeString`|Espace de noms de la méthode en cours de compilation.|
|`MethodBeingCompiledName`|`win:UnicodeString`|Nom de la méthode en cours de compilation.|
|`MethodBeingCompiledNameSignature`|`win:UnicodeString`|Signature de la méthode (liste de noms de types séparés par des virgules) en cours de compilation.|
|`CallerNamespace`|`win:UnicodeString`|Espace de noms de la méthode de l’appelant.|
|`CallerName`|`win:UnicodeString`|Nom de la méthode de l’appelant.|
|`CallerNameSignature`|`win:UnicodeString`|Signature de la méthode de l’appelant (liste de noms de types séparés par des virgules).|
|`CalleeNamespace`|`win:UnicodeString`|Espace de noms de la méthode d’appelé.|
|`CalleeName`|`win:UnicodeString`|Nom de la méthode de l’appelé.|
|`CalleeNameSignature`|`win:UnicodeString`|Signature de la méthode d’appelé (liste de noms de types séparés par des virgules).|
|`TailPrefix`|`win:Boolean`|Indique s’il s’agit d’une instruction de préfixe tail.|
|`TailCallType`|`win:UInt32`|Type de l’appel tail.<br/><br/>0 : appel tail optimisé (épilogue + JMP)<br/><br/>1 : appel tail récursif (appels tail de méthode)<br/><br/>2 : appel tail assistance assisté|
|`ClrInstanceID`|`win:UInt16`|ID unique de l’instance de CoreCLR.|

## <a name="methodjittailcallfailed-event"></a>Événement MethodJitTailCallFailed

|Mot clé pour déclencher l'événement|Level|
|-----------------------------------|-----------|
|`JITTracingKeyword` 0x1000 |Détaillé (5)|

|Événement|ID de l’événement|Description|
|-----------|--------------|-----------------|
|`MethodJitTailCallFailed`|191|Déclenché par le compilateur JIT lorsque la fin d’une méthode n’a pas été appelée.|

|Nom du champ|Type de données|Description|
|----------------|---------------|-----------------|
|`MethodBeingCompiledNamespace`|`win:UnicodeString`|Espace de noms de la méthode en cours de compilation.|
|`MethodBeingCompiledName`|`win:UnicodeString`|Nom de la méthode en cours de compilation.|
|`MethodBeingCompiledNameSignature`|`win:UnicodeString`|Signature de la méthode (liste de noms de types séparés par des virgules) en cours de compilation.|
|`CallerNamespace`|`win:UnicodeString`|Espace de noms de la méthode de l’appelant.|
|`CallerNam`e|`win:UnicodeString`|Nom de la méthode de l’appelant.|
|`CallerNameSignature`|`win:UnicodeString`|Signature de la méthode de l’appelant (liste de noms de types séparés par des virgules).|
|`CalleeNamespace`|`win:UnicodeString`|Espace de noms de la méthode d’appelé.|
|`CalleeName`|`win:UnicodeString`|Nom de la méthode de l’appelé.|
|`CalleeNameSignature`|`win:UnicodeString`|Signature de la méthode d’appelé (liste de noms de types séparés par des virgules).|
|`TailPrefix`|`win:Boolean`|Indique s’il s’agit d’une instruction de préfixe tail.|
|`FailReason`|`win:UnicodeString`|Raison de l’échec de l’appel tail.|
|`ClrInstanceID`|`win:UInt16`|ID unique de l’instance de CoreCLR.|

## <a name="methodiltonativemap-event"></a>Événement MethodILToNativeMap

|Mot clé pour déclencher l'événement|Level|
|-----------------------------------|-----------|
|`JittedMethodILToNativeMapKeyword` 0x20000 |Détaillé (5)|

|Événement|ID de l’événement|Description|
|----------------|---------------|-----------------|
|`MethodILToNativeMap`|190|Mappe l’événement de mappage IL-à-natif pour les méthodes compilées juste-à-temps.|

|Nom du champ|Type de données|Description|
|----------------|---------------|-----------------|
|`MethodID`|`win:UInt64`|Identificateur unique d’une méthode.|
|`ReJITID`|`win:UInt64`|ID ReJIT de la méthode.|
|`MethodExtent`|`win:UInt8`|L’étendue de la méthode avec JIT.|
|`CountOfMapEntries`|`win:UInt8`|Nombre d’entrées de la carte|
|`ILOffsets`|`win:UInt32`|Offset IL.|
|`NativeOffsets`|`win:UInt32`|Offset du code natif.|
|`ClrInstanceID`|`win:UInt16`|ID unique de l’instance de CoreCLR.|
