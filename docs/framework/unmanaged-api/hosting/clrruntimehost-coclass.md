---
title: Coclasse CLRRuntimeHost
ms.date: 03/30/2017
api_name:
- CLRRuntimeHost Coclass
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CLRRuntimeHost
helpviewer_keywords:
- CLRRuntimeHost coclass [.NET Framework hosting]
ms.assetid: 2ac9cbf5-8a2d-4e4f-8831-0dad8ef0a897
topic_type:
- apiref
ms.openlocfilehash: 40766ce5837053493f2e3f1f25fe7d1d63ec695f
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616799"
---
# <a name="clrruntimehost-coclass"></a>Coclasse CLRRuntimeHost
Fournit des interfaces pour la gestion de l’exécution du code par le Runtime.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
coclass CLRRuntimeHost {  
    [default] interface  ICLRRuntimeHost;  
    interface            ICLRValidator;  
};  
```  
  
## <a name="interfaces"></a>Interfaces  
  
|Interface|Description|  
|---------------|-----------------|  
|[ICLRRuntimeHost, interface](iclrruntimehost-interface.md)|Fournit des méthodes pour contrôler l’exécution d’applications par le Runtime.|  
|[ICLRValidator, interface](iclrvalidator-interface.md)|Fournit des méthodes pour la validation des images exécutables portables et pour la création de rapports détaillés des erreurs de validation.|  
  
## <a name="requirements"></a>Conditions requises  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE. idl  
  
 **Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Hébergement des coclasses](hosting-coclasses.md)
