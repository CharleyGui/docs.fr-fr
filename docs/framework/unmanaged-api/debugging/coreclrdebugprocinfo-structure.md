---
title: Structure CoreClrDebugProcInfo
ms.date: 03/30/2017
api_name:
- CoreClrDebugProcInfo
api_location:
- mscordbi_macx86.dll
api_type:
- COM
f1_keywords:
- CoreClrDebugProcInfo
helpviewer_keywords:
- remote debugging API [Silverlight]
- CoreClrDebugProcInfo structure
- Silverlight, remote debugging
ms.assetid: 4ddc37da-5c94-4beb-b61c-b54071c0e749
topic_type:
- apiref
ms.openlocfilehash: 5996393fd1a0504f9c3d3f9f07aa0e3d886a0787
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95719695"
---
# <a name="coreclrdebugprocinfo-structure"></a>Structure CoreClrDebugProcInfo

Représente un processus qui s'exécute sur un ordinateur distant.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
struct  CoreClrDebugProcInfo {  
    DWORD m_dwPID;  
    DWORD m_dwInternalID;  
    WCHAR m_wszName[256];  
};  
```  
  
## <a name="members"></a>Membres  
  
|Membre|Description|  
|------------|-----------------|  
|`m_dwPID`|Identificateur de processus affecté par le système d'exploitation.|  
|`m_dwInternalID`|Identificateur de processus affecté par le proxy de débogage distant en cours d'exécution sur l'ordinateur cible. Cet identificateur est moins souvent recyclé que l'identificateur de système d'exploitation.|  
|`m_wszName`|Ligne de commande du processus. Ce membre peut être tronqué.|  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CoreClrRemoteDebuggingInterfaces. h  
  
 **Bibliothèque :** mscordbi_macx86.dll  
  
 **Versions de .NET Framework :** 3,5 SP1
