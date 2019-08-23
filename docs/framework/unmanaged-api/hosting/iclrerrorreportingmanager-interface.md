---
title: ICLRErrorReportingManager, interface
ms.date: 03/30/2017
api_name:
- ICLRErrorReportingManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRErrorReportingManager
helpviewer_keywords:
- ICLRErrorReportingManager interface [.NET Framework hosting]
ms.assetid: ea8af0d5-4133-4472-8a1f-50570d7e85fa
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2a9d9cff0360e4eb27584fe0f22c1c20396ff8f0
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69966255"
---
# <a name="iclrerrorreportingmanager-interface"></a>ICLRErrorReportingManager, interface
Fournit des méthodes qui permettent à l’hôte de configurer des vidages de pile personnalisés pour le rapport d’erreurs.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[BeginCustomDump, méthode](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-begincustomdump-method.md)|Spécifie la configuration des vidages de pile personnalisés pour le rapport d’erreurs.|  
|[EndCustomDump, méthode](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-endcustomdump-method.md)|Efface la configuration de vidage de pile personnalisée qui a été définie par un `BeginCustomDump`appel antérieur à.|  
|[GetBucketParametersForCurrentException, méthode](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-getbucketparametersforcurrentexception-method.md)|Obtient le compartiment Watson pour l’exception actuelle sur le thread appelant.|  
  
## <a name="remarks"></a>Notes  
 La `BeginCustomDump` méthode définit une configuration de vidage de pile personnalisée. La `EndCustomDump` méthode efface la configuration de vidage de pile personnalisée et libère tous les États associés. Elle doit être appelée une fois que le vidage personnalisé est terminé.  
  
> [!IMPORTANT]
> L’échec de `EndCustomDump` l’appel entraîne une fuite de mémoire.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE. h  
  
 **Bibliothèque** Inclus en tant que ressource dans MSCorEE. dll  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ECustomDumpItemKind, énumération](../../../../docs/framework/unmanaged-api/hosting/ecustomdumpitemkind-enumeration.md)
- [Interfaces d’hébergement](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
