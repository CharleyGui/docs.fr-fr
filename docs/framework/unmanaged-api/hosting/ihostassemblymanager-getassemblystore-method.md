---
title: IHostAssemblyManager::GetAssemblyStore, méthode
ms.date: 03/30/2017
api_name:
- IHostAssemblyManager.GetAssemblyStore
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostAssemblyManager::GetAssemblyStore
helpviewer_keywords:
- IHostAssemblyManager::GetAssemblyStore method [.NET Framework hosting]
- GetAssemblyStore method [.NET Framework hosting]
ms.assetid: d0f74593-9bb1-4a11-8096-e29734b20698
topic_type:
- apiref
ms.openlocfilehash: 587861529c340fad9fd817b904e4d3651b236e8d
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/22/2020
ms.locfileid: "83805072"
---
# <a name="ihostassemblymanagergetassemblystore-method"></a>IHostAssemblyManager::GetAssemblyStore, méthode
Obtient un pointeur d’interface vers un [IHostAssemblyStore](ihostassemblystore-interface.md) qui représente la liste des assemblys chargés par l’hôte.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetAssemblyStore (  
    [out] IHostAssemblyStore **ppAssemblyStore  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `ppAssemblyStore`  
 à Pointeur de fonction vers une `IHostAssemblyStore` instance, ou null, si l’hôte n’implémente pas `IHostAssemblyStore` .  
  
## <a name="return-value"></a>Valeur de retour  
  
|HRESULT|Description|  
|-------------|-----------------|  
|S_OK|`GetAssemblyStore`retourné avec succès.|  
|HOST_E_CLRNOTAVAILABLE|Le common language runtime (CLR) n’a pas été chargé dans un processus, ou le CLR est dans un État dans lequel il ne peut pas exécuter de code managé ou traiter correctement l’appel.|  
|HOST_E_TIMEOUT|Le délai d’attente de l’appel a expiré.|  
|HOST_E_NOT_OWNER|L’appelant ne possède pas le verrou.|  
|HOST_E_ABANDONED|Un événement a été annulé alors qu’un thread ou une fibre bloqué était en attente.|  
|E_FAIL|Une défaillance catastrophique inconnue s’est produite. Quand une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus. Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.|  
|E_NOINTERFACE|L’hôte ne fournit pas d’implémentation de `IHostAssemblyStore` .|  
  
## <a name="remarks"></a>Notes  
 `IHostAssemblyStore`fournit des méthodes qui permettent à un hôte de se lier à des assemblys et des modules indépendamment du CLR. Les hôtes fournissent généralement des magasins d’assemblys pour permettre le chargement d’assemblys à partir de formats autres que le système de fichiers.  
  
> [!NOTE]
> Si l’hôte n’implémente pas `IHostAssemblyStore` , `GetAssemblyStore` doit retourner une valeur HRESULT de E_NOINTERFACE et doit avoir la valeur `ppAssemblyStore` null.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE. h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [IHostAssemblyManager, interface](ihostassemblymanager-interface.md)
- [IHostAssemblyStore, interface](ihostassemblystore-interface.md)
