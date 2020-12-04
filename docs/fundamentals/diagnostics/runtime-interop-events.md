---
title: Événements du runtime d’interopérabilité
description: Consultez événements du Runtime .NET qui recueillent des informations de diagnostic spécifiques à l’interopérabilité.
ms.date: 11/13/2020
ms.topic: reference
helpviewer_keywords:
- Interop events (CoreCLR)
- ETW, EventPipe, LTTng interop events (CoreCLR)
ms.openlocfilehash: 5635fb55b3a6ffa3f5611da80cdb2909e226e2ea
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2020
ms.locfileid: "96588600"
---
# <a name="net-runtime-interop-events"></a>Événements d’interopérabilité du Runtime .NET

Ces événements de Runtime capturent des informations sur la génération du stub Common Intermediate Language (CIL). Pour plus d’informations sur l’utilisation de ces événements à des fins de diagnostic, consultez [journalisation et traçage d’applications .net](../../core/diagnostics/logging-tracing.md)

## <a name="ilstubgenerated-event"></a>Événement ILStubGenerated

|Mot clé pour déclencher l'événement|Level|
|-----------------------------------|-----------|
|`InteropKeyword` (0x2000)|Informatif(4)|
  
|Événement|ID de l’événement|Moment du déclenchement|
|-----------|--------------|-----------------|
|`ILStubGenerated`|88|Un stub IL est généré.|

|Nom du champ|Type de données|Description|
|----------------|---------------|-----------------|
|`ModuleID`|`win:UInt16`|Identificateur de module.|
|`StubMethodID`|`win:UInt64`|Identificateur de la méthode stub|
|`StubFlags`|`win:UInt32`|Indicateurs du stub :<br /><br /> `0x1` -Inverser l’interopérabilité.<br /><br /> `0x2` -COM Interop.<br /><br /> `0x4` -Stub généré par NGen.exe.<br /><br /> `0x8` Disposer.<br /><br /> `0x10` Argument de variable.<br /><br /> `0x20` -Appelé non managé.<br /><br /> `0x40` -Struct Marshal|
|`ManagedInteropMethodToken`|`win:UInt32`|Jeton de la méthode d’interopérabilité managée|
|`ManagedInteropMethodNameSpace`|`win:UnicodeString`|Espace de noms et type englobant de la méthode d’interopérabilité managée.|
|`ManagedInteropMethodName`|`win:UnicodeString`|Nom de la méthode d’interopérabilité managée|
|`ManagedInteropMethodSignature`|`win:UnicodeString`|Signature de la méthode d'interopérabilité managée|
|`NativeMethodSignature`|`win:UnicodeString`|Signature de la méthode native|
|`StubMethodSignature`|`win:UnicodeString`|Signature de la méthode stub|
|`StubMethodILCode`|`win:UnicodeString`|Code Common Intermediate Language (CIL) de la méthode stub.|
|`ClrInstanceID`|`win:UInt16`|ID unique de l'instance de CLR ou CoreCLR.|
