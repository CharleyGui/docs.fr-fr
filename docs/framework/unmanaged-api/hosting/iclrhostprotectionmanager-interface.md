---
title: ICLRHostProtectionManager, interface
ms.date: 03/30/2017
api_name:
- ICLRHostProtectionManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRHostProtectionManager
helpviewer_keywords:
- ICLRHostProtectionManager interface [.NET Framework hosting]
ms.assetid: ce2770ae-23d0-45d9-8bcf-46504ac5020e
topic_type:
- apiref
ms.openlocfilehash: e8ead998907d55b0bfbf82e5f6f4e7c504f657ec
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95714157"
---
# <a name="iclrhostprotectionmanager-interface"></a>ICLRHostProtectionManager, interface

Permet à l’hôte de bloquer des classes, des méthodes, des propriétés et des champs managés spécifiques de s’exécuter dans du code de confiance partielle.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[SetEagerSerializeGrantSets](iclrhostprotectionmanager-seteagerserializegrantsets-method.md)|Fournit une garantie que certaines conditions de concurrence rares qui peuvent provoquer des erreurs d’common language runtime fatales (CLR) ne se produiront jamais.|  
|[SetProtectedCategories, méthode](iclrhostprotectionmanager-setprotectedcategories-method.md)|Spécifie les catégories de types et de membres managés dont l’exécution doit être bloquée dans du code de confiance partielle.|  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE. h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [EApiCategories, énumération](eapicategories-enumeration.md)
- [ICLRControl, interface](iclrcontrol-interface.md)
