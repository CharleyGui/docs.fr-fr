---
title: Événements du runtime d’exception
description: Consultez événements du Runtime .NET qui recueillent des informations de diagnostic spécifiques aux exceptions et à la gestion des exceptions.
ms.date: 11/13/2020
ms.topic: reference
helpviewer_keywords:
- exception events (CoreCLR)
- exception handling events (CoreCLR)
- ETW, EventPipe, LTTng exception events (CoreCLR)
ms.openlocfilehash: f4f63c8469f9c734b872ddaec8d1d7f7f0427576
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96588659"
---
# <a name="net-runtime-exception-events"></a>Événements d’exception du Runtime .NET

Ces événements de Runtime capturent des informations sur les exceptions levées. Pour plus d’informations sur l’utilisation de ces événements à des fins de diagnostic, consultez [journalisation et traçage d’applications .net](../../core/diagnostics/logging-tracing.md)

## <a name="exceptionthrown_v1-event"></a>Événement ExceptionThrown_V1

|Mot clé pour déclencher l'événement|Level|
|-----------------------------------|-----------|
|`ExceptionKeyword` (0x8000)|Erreur (1)|

 Le tableau ci-dessous montre les informations liées aux événements.

|Événement|ID de l’événement|Moment du déclenchement|
|-----------|--------------|-----------------|
|`ExceptionThrown_V1`|80|Une exception managée est levée.|

|Nom du champ|Type de données|Description|
|----------------|---------------|-----------------|
|`ExceptionType`|`win:UnicodeString`|Type de l’exception, par exemple `System.NullReferenceException`.|
|`ExceptionMessage`|`win:UnicodeString`|Message d’exception réel.|
|`EIPCodeThrow`|`win:Pointer`|Pointeur d’instruction où l’exception s’est produite.|
|`ExceptionHR`|`win:UInt32`|Exception [HRESULT](/openspecs/windows_protocols/ms-erref/0642cb2f-2075-4469-918c-4441e69c548a).|
|`ExceptionFlags`|`win:UInt16`|`0x01`: HasInnerException.<br /><br /> `0x02`: IsNestedException.<br /><br /> `0x04`: IsRethrownException.<br /><br /> `0x08`: IsCorruptedStateException (indique que l’état du processus est endommagé ; consultez [gestion des exceptions d’état endommagé](/archive/msdn-magazine/2009/february/clr-inside-out-handling-corrupted-state-exceptions)).<br /><br /> `0x10`: IsCLSCompliant (une exception qui dérive de <xref:System.Exception> est conforme CLS ; sinon, elle n’est pas conforme CLS).|
|`ClrInstanceID`|`win:UInt16`|ID unique de l'instance de CLR ou CoreCLR.|

## <a name="exceptioncatchstart-event"></a>Événement ExceptionCatchStart

Cet événement est émis lorsqu’un gestionnaire catch d’exception managé commence.

|Mot clé pour déclencher l'événement|Level|
|-----------------------------------|-----------|
|`ExceptionKeyword` (0x8000)|Informatif (4)|

 Le tableau ci-dessous montre les informations liées aux événements.

|Événement|ID de l’événement|Moment du déclenchement|
|-----------|--------------|-----------------|
|`ExceptionCatchStart`|250|Une exception managée est gérée par le Runtime.|

|Nom du champ|Type de données|Description|
|----------------|---------------|-----------------|
|`EIPCodeThrow`|`win:Pointer`|Pointeur d’instruction où l’exception s’est produite.|
|`MethodID`|`win:Pointer`|Pointeur vers le descripteur de méthode sur la méthode où l’exception s’est produite.|
|`MethodName`|`win:UnicodeString`|Nom de la méthode où l’exception s’est produite.|
|`ClrInstanceID`|`win:UInt16`|ID unique de l'instance de CLR ou CoreCLR.|

## <a name="exceptioncatchstop-event"></a>Événement ExceptionCatchStop

Cet événement est émis lorsqu’un gestionnaire catch d’exceptions managées se termine.

|Mot clé pour déclencher l'événement|Level|
|-----------------------------------|-----------|
|`ExceptionKeyword` (0x8000)|Informatif (4)|

 Le tableau ci-dessous montre les informations liées aux événements.

|Événement|ID de l’événement|Moment du déclenchement|
|-----------|--------------|-----------------|
|`ExceptionCatchStop`|251|Un gestionnaire catch d’exceptions managé est terminé.|

## <a name="exceptionfinallystart-event"></a>Événement ExceptionFinallyStart

Cet événement est émis lorsqu’une exception managée finally Handler commence.

|Mot clé pour déclencher l'événement|Level|
|-----------------------------------|-----------|
|`ExceptionKeyword` (0x8000)|Informatif (4)|

 Le tableau ci-dessous montre les informations liées aux événements.

|Événement|ID de l’événement|Moment du déclenchement|
|-----------|--------------|-----------------|
|`ExceptionFinallyStart`|252|Une exception managée est gérée par le Runtime.|

|Nom du champ|Type de données|Description|
|----------------|---------------|-----------------|
|`EIPCodeThrow`|`win:Pointer`|Pointeur d’instruction où l’exception s’est produite.|
|`MethodID`|`win:Pointer`|Pointeur vers le descripteur de méthode sur la méthode où l’exception s’est produite.|
|`MethodName`|`win:UnicodeString`|Nom de la méthode où l’exception s’est produite.|
|`ClrInstanceID`|`win:UInt16`|ID unique de l'instance de CLR ou CoreCLR.|

## <a name="exceptionfinallystop-event"></a>Événement ExceptionFinallyStop

Cet événement est émis lorsqu’un gestionnaire catch d’exceptions managées se termine.

|Mot clé pour déclencher l'événement|Level|
|-----------------------------------|-----------|
|`ExceptionKeyword` (0x8000)|Informatif (4)|

 Le tableau ci-dessous montre les informations liées aux événements.

|Événement|ID de l’événement|Moment du déclenchement|
|-----------|--------------|-----------------|
|`ExceptionFinallyStop`|253|Une exception managée finally Handler est terminée.|

## <a name="exceptionfilterstart-event"></a>Événement ExceptionFilterStart

Cet événement est émis lors du début d’un filtrage d’exceptions managées.

|Mot clé pour déclencher l'événement|Level|
|-----------------------------------|-----------|
|`ExceptionKeyword` (0x8000)|Informatif (4)|

 Le tableau ci-dessous montre les informations liées aux événements.

|Événement|ID de l’événement|Moment du déclenchement|
|-----------|--------------|-----------------|
|`ExceptionFilterStart`|254|Un filtrage des exceptions managées commence.|

|Nom du champ|Type de données|Description|
|----------------|---------------|-----------------|
|`EIPCodeThrow`|`win:Pointer`|Pointeur d’instruction où l’exception s’est produite.|
|`MethodID`|`win:Pointer`|Pointeur vers le descripteur de méthode sur la méthode où l’exception s’est produite.|
|`MethodName`|`win:UnicodeString`|Nom de la méthode où l’exception s’est produite.|
|`ClrInstanceID`|`win:UInt16`|ID unique de l’instance de CoreCLR.|

## <a name="exceptionfilterstop-event"></a>Événement ExceptionFilterStop

Cet événement est émis lorsqu’un filtrage d’exceptions managées se termine.

|Mot clé pour déclencher l'événement|Level|
|-----------------------------------|-----------|
|`ExceptionKeyword` (0x8000)|Informatif (4)|

 Le tableau ci-dessous montre les informations liées aux événements.

|Événement|ID de l’événement|Moment du déclenchement|
|-----------|--------------|-----------------|
|`ExceptionFilteringStart`|255|Un filtrage des exceptions managées se termine.|

## <a name="exceptionthrownstop-event"></a>Événement ExceptionThrownStop

Cet événement est émis lorsque le runtime a terminé de gérer une exception managée qui a été levée.

|Mot clé pour déclencher l'événement|Level|
|-----------------------------------|-----------|
|`ExceptionKeyword` (0x8000)|Informatif (4)|
  
 Le tableau ci-dessous montre les informations liées aux événements.

|Événement|ID de l’événement|Moment du déclenchement|
|-----------|--------------|-----------------|
|`ExceptionThrownStop`|256|Un filtrage des exceptions managées se termine.|
