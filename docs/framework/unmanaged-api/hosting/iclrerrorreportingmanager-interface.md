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
ms.openlocfilehash: d3816c8a3b6204b053505aa888eb28d696f8990b
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95677839"
---
# <a name="iclrerrorreportingmanager-interface"></a>ICLRErrorReportingManager, interface

Fournit des méthodes qui permettent à l’hôte de configurer des vidages de pile personnalisés pour le rapport d’erreurs.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[BeginCustomDump, méthode](iclrerrorreportingmanager-begincustomdump-method.md)|Spécifie la configuration des vidages de pile personnalisés pour le rapport d’erreurs.|  
|[EndCustomDump, méthode](iclrerrorreportingmanager-endcustomdump-method.md)|Efface la configuration de vidage de pile personnalisée qui a été définie par un appel antérieur à `BeginCustomDump` .|  
|[GetBucketParametersForCurrentException, méthode](iclrerrorreportingmanager-getbucketparametersforcurrentexception-method.md)|Obtient le compartiment Watson pour l’exception actuelle sur le thread appelant.|  
  
## <a name="remarks"></a>Remarques  

 La `BeginCustomDump` méthode définit une configuration de vidage de pile personnalisée. La `EndCustomDump` méthode efface la configuration de vidage de pile personnalisée et libère tous les États associés. Elle doit être appelée une fois que le vidage personnalisé est terminé.  
  
> [!IMPORTANT]
> L’échec de l’appel `EndCustomDump` entraîne une fuite de mémoire.  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE. h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ECustomDumpItemKind, énumération](ecustomdumpitemkind-enumeration.md)
- [Interfaces d'hébergement](hosting-interfaces.md)
