---
title: ICLRHostBindingPolicyManager, interface
ms.date: 03/30/2017
api_name:
- ICLRHostBindingPolicyManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRHostBindingPolicyManager
helpviewer_keywords:
- ICLRHostBindingPolicyManager interface [.NET Framework hosting]
ms.assetid: f9da168b-366b-4b2b-bdb9-330b6bad5a6b
topic_type:
- apiref
ms.openlocfilehash: 49d1ee4dd0965d4ae5b54b53208809cfbdf7e718
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95725626"
---
# <a name="iclrhostbindingpolicymanager-interface"></a>ICLRHostBindingPolicyManager, interface

Fournit des méthodes pour que l’hôte évalue la stratégie de liaison actuelle et communique les modifications de stratégie pour un assembly spécifié.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[EvaluatePolicy, méthode](iclrhostbindingpolicymanager-evaluatepolicy-method.md)|Évalue la stratégie de liaison pour le compte de l’hôte.|  
|[ModifyApplicationPolicy, méthode](iclrhostbindingpolicymanager-modifyapplicationpolicy-method.md)|Modifie la stratégie de liaison pour l’assembly spécifié et crée une nouvelle version de la stratégie.|  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE. h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICLRAssemblyIdentityManager, interface](iclrassemblyidentitymanager-interface.md)
- [IHostAssemblyStore, interface](ihostassemblystore-interface.md)
- [Interfaces d'hébergement](hosting-interfaces.md)
