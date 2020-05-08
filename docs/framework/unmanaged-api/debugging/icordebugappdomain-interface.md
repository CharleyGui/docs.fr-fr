---
title: ICorDebugAppDomain, interface
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomain
api_location:
- corguids.lib
api_type:
- COM
f1_keywords:
- ICorDebugAppDomain
helpviewer_keywords:
- ICorDebugAppDomain interface [.NET Framework debugging]
ms.assetid: be7ae711-1217-4a44-be40-166e29641b77
topic_type:
- apiref
ms.openlocfilehash: 140e67417f4fad552f972a93bc8c620b440b2370
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2020
ms.locfileid: "82895172"
---
# <a name="icordebugappdomain-interface"></a>ICorDebugAppDomain, interface

Fournit des méthodes pour le débogage de domaines d'application. Cette interface est une sous-classe de ICorDebugController.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[Attach, méthode](icordebugappdomain-attach-method.md)|Attache le débogueur au domaine d’application.|  
|[EnumerateAssemblies, méthode](icordebugappdomain-enumerateassemblies-method.md)|Obtient un énumérateur pour les assemblys dans le domaine d’application.|  
|[EnumerateBreakpoints, méthode](icordebugappdomain-enumeratebreakpoints-method.md)|Obtient un énumérateur pour tous les points d’arrêt actifs dans le domaine d’application.|  
|[EnumerateSteppers, méthode](icordebugappdomain-enumeratesteppers-method.md)|Obtient un énumérateur pour toutes les exécutions pas à pas actives dans le domaine d’application.|  
|[GetId, méthode](icordebugappdomain-getid-method.md)|Obtient l’ID unique du domaine d’application.|  
|[GetModuleFromMetaDataInterface, méthode](icordebugappdomain-getmodulefrommetadatainterface-method.md)|Obtient l’objet ICorDebugModule avec l’interface de métadonnées donnée.|  
|[GetName, méthode](icordebugappdomain-getname-method.md)|Obtient le nom du domaine d’application.|  
|[GetObject, méthode](icordebugappdomain-getobject-method.md)|Obtient un pointeur d’interface vers le domaine d’application common language runtime (CLR).|  
|[GetProcess, méthode](icordebugappdomain-getprocess-method.md)|Obtient le processus qui contient le domaine d’application.|  
|[IsAttached, méthode](icordebugappdomain-isattached-method.md)|Détermine si le débogueur est attaché au domaine d’application.|  
  
## <a name="remarks"></a>Notes   
  
> [!NOTE]
> Cette interface ne prend pas en charge l'appel à distance, que ce soit entre ordinateurs ou entre processus.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Interfaces de débogage](debugging-interfaces.md)
