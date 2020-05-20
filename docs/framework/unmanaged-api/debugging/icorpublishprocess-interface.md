---
title: ICorPublishProcess, interface
ms.date: 03/30/2017
api_name:
- ICorPublishProcess
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishProcess
helpviewer_keywords:
- ICorPublishProcess interface [.NET Framework debugging]
ms.assetid: 6d1dc41b-8aa2-4889-bb00-1cbccc00c123
topic_type:
- apiref
ms.openlocfilehash: 8d958e949612b502ab218f5c6b75779174d34e19
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/15/2020
ms.locfileid: "83421083"
---
# <a name="icorpublishprocess-interface"></a>ICorPublishProcess, interface
Fournit des méthodes qui accèdent aux informations à afficher sur un processus.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[EnumAppDomains, méthode](icorpublishprocess-enumappdomains-method.md)|Obtient une instance de [ICorPublishAppDomainEnum](icorpublishappdomainenum-interface.md) qui contient les domaines d’application dans le processus référencé par ce `ICorPublishProcess` .|  
|[GetDisplayName, méthode](icorpublishprocess-getdisplayname-method.md)|Obtient le chemin d’accès complet de l’exécutable pour le processus référencé par ce `ICorPublishProcess` .|  
|[GetProcessID, méthode](icorpublishprocess-getprocessid-method.md)|Obtient l’identificateur de système d’exploitation pour le processus référencé par ce `ICorPublishProcess` .|  
|[IsManaged, méthode](icorpublishprocess-ismanaged-method.md)|Obtient une valeur qui indique si le processus référencé par ce `ICorPublishProcess` est connu comme étant en cours d’exécution du code managé.|  
  
## <a name="requirements"></a>Conditions requises  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorPub. idl, CorPub. h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Interfaces de débogage](debugging-interfaces.md)
- [CorpubPublish (coclasse)](corpubpublish-coclass.md)
