---
title: IHostMAlloc::DebugAlloc, méthode
ms.date: 03/30/2017
api_name:
- IHostMAlloc.DebugAlloc
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostMAlloc::DebugAlloc
helpviewer_keywords:
- DebugAlloc method [.NET Framework hosting]
- IHostMAlloc::DebugAlloc method [.NET Framework hosting]
ms.assetid: 0bfbc527-bea2-43ce-b041-69186f4440dd
topic_type:
- apiref
ms.openlocfilehash: 3f85e7c7fd54079ddce37f739a3a7bc0fa830d31
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84493290"
---
# <a name="ihostmallocdebugalloc-method"></a>IHostMAlloc::DebugAlloc, méthode
Demande que l’hôte alloue la quantité de mémoire spécifiée à partir du tas et effectue également le suivi de l’emplacement où la mémoire a été allouée.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT DebugAlloc (  
    [in]  SIZE_T  cbSize,
    [in]  EMemoryCriticalLevel dwCriticalLevel,
    [in]  char*   pszFileName,
    [in]  int     iLineNo,
    [out] void**  ppMem  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `cbSize`  
 dans Taille, en octets, de la demande d’allocation de mémoire actuelle.  
  
 `dwCriticalLevel`  
 dans L’une des valeurs [EMemoryCriticalLevel,](ememorycriticallevel-enumeration.md) , indiquant l’impact d’un échec d’allocation.  
  
 `pszFileName`  
 dans Fichier de code de l’exécutable en cours de débogage.  
  
 `iLineNo`  
 dans Numéro de la ligne `pszFileName` où l’allocation a été demandée.  
  
 `ppMem`  
 à Pointeur vers la mémoire allouée, ou null si la demande n’a pas pu être effectuée.  
  
## <a name="return-value"></a>Valeur renvoyée  
  
|HRESULT|Description|  
|-------------|-----------------|  
|S_OK|`DebugAlloc`retourné avec succès.|  
|HOST_E_CLRNOTAVAILABLE|Le CLR n’a pas été chargé dans un processus, ou le CLR est dans un État dans lequel il ne peut pas exécuter de code managé ou traiter correctement l’appel.|  
|HOST_E_TIMEOUT|Le délai d’attente de l’appel a expiré.|  
|HOST_E_NOT_OWNER|L’appelant ne possède pas le verrou.|  
|HOST_E_ABANDONED|Un événement a été annulé alors qu’un thread ou une fibre bloqué était en attente.|  
|E_FAIL|Une défaillance catastrophique inconnue s’est produite. Quand une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus. Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.|  
|E_OUTOFMEMORY|Mémoire disponible insuffisante pour terminer la demande d’allocation.|  
  
## <a name="remarks"></a>Remarques  
 Le CLR obtient un pointeur d’interface vers une instance [IHostMalloc](ihostmalloc-interface.md) en appelant la méthode [IHostMemoryManager :: CreateMAlloc](ihostmemorymanager-createmalloc-method.md) . `DebugAlloc`permet au runtime d’obtenir des informations de fichier de code à utiliser pendant le débogage.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE. h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [IHostMemoryManager, interface](ihostmemorymanager-interface.md)
- [IHostMalloc, interface](ihostmalloc-interface.md)
