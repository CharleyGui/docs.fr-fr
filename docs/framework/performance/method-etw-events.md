---
title: Événements ETW de méthode
description: Consultez événements ETW qui collectent des informations spécifiques aux méthodes, telles que les événements de méthode CLR, le marqueur de méthode CLR ou les événements détaillés de méthode CLR et MethodJittingStarted.
ms.date: 03/30/2017
helpviewer_keywords:
- ETW, method events (CLR)
- method events [.NET Framework]
ms.assetid: 167a4459-bb6e-476c-9046-7920880f2bb5
ms.openlocfilehash: f48867a0aef417ad0b19a15d78e0c0f01a7c30a1
ms.sourcegitcommit: cf5a800a33de64d0aad6d115ffcc935f32375164
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/20/2020
ms.locfileid: "86474317"
---
# <a name="method-etw-events"></a>Événements ETW de méthode

Ces événements collectent des informations spécifiques aux méthodes. La charge utile de ces événements est requise pour la résolution des symboles. De plus, ces événements fournissent des informations utiles telles que le nombre de fois qu'une méthode a été appelée.

Tous les événements de méthode ont le niveau « Informations (4) ». Tous les événements détaillés de méthode ont le niveau « Détaillé (5) ».

Tous les événements de méthode sont déclenchés par le mot clé `JITKeyword` (0x10) ou `NGenKeyword` (0x20) sous le fournisseur de runtime, ou par le mot clé `JitRundownKeyword` (0x10) ou `NGENRundownKeyword` (0x20) sous le fournisseur d’arrêt.

## <a name="clr-method-events"></a>Événements de méthode du CLR

Le tableau suivant montre les mots clés et les niveaux. Pour plus d’informations, consultez [niveaux et Mots clés ETW du CLR](clr-etw-keywords-and-levels.md).

|Mot clé pour déclencher l'événement|Level|
|-----------------------------------|-----------|
|`JITKeyword` (0x10)|Informatif (4)|
|`NGenKeyword` (0x20)|Informatif (4)|
|`JitRundownKeyword` (0x10)|Informatif (4)|
|`NGENRundownKeyword` (0x20)|Informatif (4)|

Le tableau ci-dessous montre les informations liées aux événements.

|Événement|ID de l’événement|Description|
|-----------|--------------|-----------------|
|`MethodLoad_V1`|136|Déclenché quand une méthode est chargée juste-à-temps (JIT) ou quand une image NGEN est chargée. Les méthodes dynamiques et génériques n'utilisent pas cette version pour les chargements de méthodes. Les programmes d'assistance JIT n'utilisent jamais cette version.|
|`MethodUnLoad_V1`|137|Déclenché quand un module est déchargé ou quand un domaine d'application est détruit. Les méthodes dynamiques n'utilisent jamais cette version pour les déchargements de méthodes.|
|`MethodDCStart_V1`|137|Énumère les méthodes lors d’un arrêt de début.|
|`MethodDCEnd_V1`|138|Énumère les méthodes lors d'un arrêt de fin.|

Le tableau ci-dessous montre les données d’événements.

|Nom du champ|Type de données|Description|
|----------------|---------------|-----------------|
|MethodID|win:UInt64|Identificateur unique d’une méthode. Pour les méthodes d'assistance JIT, sa valeur correspond à l'adresse de début de la méthode.|
|ModuleID|win:UInt64|Identificateur du module auquel cette méthode appartient (0 pour les programmes d'assistance JIT).|
|MethodStartAddress|win:UInt64|Adresse de début de la méthode.|
|MethodSize|win:UInt32|Taille de la méthode.|
|MethodToken|win:UInt32|0 pour les méthodes dynamiques et les programmes d'assistance JIT.|
|MethodFlags|win:UInt32|0x1 : méthode dynamique.<br /><br /> 0x2 : méthode générique.<br /><br /> 0x4 : méthode de code compilé juste-à-temps (JIT) (ou code d'image natif NGEN).<br /><br /> 0x8 : méthode d'assistance.|
|ClrInstanceID|win:UInt16|ID unique de l'instance de CLR ou CoreCLR.|

## <a name="clr-method-marker-events"></a>Événements de marqueur de méthode du CLR

Ces événements sont déclenchés uniquement sous le fournisseur d'arrêt. Ils indiquent la fin de l'énumération de méthode pendant un arrêt de début ou de fin. (Autrement dit, ils sont déclenchés quand le mot clé `NGENRundownKeyword`, `JitRundownKeyword`, `LoaderRundownKeyword`ou `AppDomainResourceManagementRundownKeyword` est activé.)

Le tableau suivant montre les mots clés et les niveaux.

|Mot clé pour déclencher l'événement|Level|
|-----------------------------------|-----------|
|`AppDomainResourceManagementRundownKeyword` (0x800)|Informatif (4)|
|`JitRundownKeyword` (0x10)|Informatif (4)|
|`NGENRundownKeyword` (0x20)|Informatif (4)|

Le tableau ci-dessous montre les informations liées aux événements.

|Événement|ID de l’événement|Description|
|-----------|--------------|----------------|
|`DCStartInit_V1`|147|Envoyé avant le démarrage de l'énumération pendant un arrêt de début.|
|`DCStartComplete_V1`|145|Envoyé à la fin de l'énumération pendant un arrêt de début.|
|`DCEndInit_V1`|148|Envoyé avant le démarrage de l'énumération pendant un arrêt de fin.|
|`DCEndComplete_V1`|146|Envoyé à la fin de l'énumération pendant un arrêt de fin.|

Le tableau ci-dessous montre les données d’événements.

|Nom du champ|Type de données|Description|
|----------------|---------------|-----------------|
|ClrInstanceID|win:UInt16|ID unique de l'instance de CLR ou CoreCLR.|

## <a name="clr-method-verbose-events"></a>Événements détaillés de méthode du CLR

Le tableau suivant montre les mots clés et les niveaux.

|Mot clé pour déclencher l'événement|Level|
|-----------------------------------|-----------|
|`JITKeyword` (0x10)|Détaillé (5)|
|`NGenKeyword` (0x20)|Détaillé (5)|
|`JitRundownKeyword` (0x10)|Détaillé (5)|
|`NGENRundownKeyword` (0x20)|Détaillé (5)|

Le tableau ci-dessous montre les informations liées aux événements.

|Événement|ID de l’événement|Description|
|-----------|--------------|-----------------|
|`MethodLoadVerbose_V1`|143|Déclenché quand une méthode est chargée juste-à-temps (JIT) ou quand une image NGEN est chargée. Les méthodes dynamiques et génériques utilisent toujours cette version pour les chargements de méthodes. Les programmes d'assistance JIT utilisent toujours cette version.|
|`MethodUnLoadVerbose_V1`|144|Déclenché quand une méthode dynamique est détruite, quand un module est déchargé ou quand un domaine d'application est détruit. Les méthodes dynamiques utilisent toujours cette version pour les déchargements de méthodes.|
|`MethodDCStartVerbose_V1`|141|Énumère les méthodes lors d’un arrêt de début.|
|`MethodDCEndVerbose_V1`|142|Énumère les méthodes lors d'un arrêt de fin.|

Le tableau ci-dessous montre les données d’événements.

|Nom du champ|Type de données|Description|
|----------------|---------------|-----------------|
|MethodID|win:UInt64|Identificateur unique de la méthode. Pour les méthodes d'assistance JIT, sa valeur correspond à l'adresse de début de la méthode.|
|ModuleID|win:UInt64|Identificateur du module auquel cette méthode appartient (0 pour les programmes d'assistance JIT).|
|MethodStartAddress|win:UInt64|Adresse de début.|
|MethodSize|win:UInt32|Longueur de la méthode.|
|MethodToken|win:UInt32|0 pour les méthodes dynamiques et les programmes d'assistance JIT.|
|MethodFlags|win:UInt32|0x1 : méthode dynamique.<br /><br /> 0x2 : méthode générique.<br /><br /> 0x4 : méthode compilée juste-à-temps (JIT) (ou générée par NGen.exe)<br /><br /> 0x8 : méthode d'assistance.|
|MethodNameSpace|win:UnicodeString|Nom d'espace de noms complet associé à la méthode.|
|MethodName|win:UnicodeString|Nom complet de classe associé à la méthode.|
|MethodSignature|win:UnicodeString|Signature de la méthode (liste de noms de types séparés par des virgules).|
|ClrInstanceID|win:UInt16|ID unique de l'instance de CLR ou CoreCLR.|

## <a name="methodjittingstarted-event"></a>Événement MethodJittingStarted

Le tableau suivant montre les mots clés et les niveaux.

|Mot clé pour déclencher l'événement|Level|
|-----------------------------------|-----------|
|`JITKeyword` (0x10)|Détaillé (5)|
|`NGenKeyword` (0x20)|Détaillé (5)|
|`JitRundownKeyword` (0x10)|Détaillé (5)|
|`NGENRundownKeyword` (0x20)|Détaillé (5)|

Le tableau ci-dessous montre les informations liées aux événements.

|Événement|ID de l’événement|Description|
|-----------|--------------|-----------------|
|`MethodJittingStarted`|145|Déclenché quand une méthode est compilée juste-à-temps (JIT).|

Le tableau ci-dessous montre les données d’événements.

|Nom du champ|Type de données|Description|
|----------------|---------------|-----------------|
|MethodID|win:UInt64|Identificateur unique de la méthode.|
|ModuleID|win:UInt64|Identificateur du module auquel cette méthode appartient.|
|MethodToken|win:UInt32|0 pour les méthodes dynamiques et les programmes d'assistance JIT.|
|MethodILSize|win:UInt32|Taille du langage intermédiaire Microsoft (MSIL) pour la méthode qui est compilée juste-à-temps (JIT).|
|MethodNameSpace|win:UnicodeString|Nom complet de classe associé à la méthode.|
|MethodName|win:UnicodeString|Nom de la méthode.|
|MethodSignature|win:UnicodeString|Signature de la méthode (liste de noms de types séparés par des virgules).|
|ClrInstanceID|win:UInt16|ID unique de l'instance de CLR ou CoreCLR.|

## <a name="see-also"></a>Voir aussi

- [Événements ETW du CLR](clr-etw-events.md)
