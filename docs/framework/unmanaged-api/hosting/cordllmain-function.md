---
title: _CorDllMain, fonction
ms.date: 03/30/2017
api_name:
- _CorDllMain
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- _CorDllMain
helpviewer_keywords:
- _CorDllMain function [.NET Framework hosting]
ms.assetid: bc7b51cf-39d3-48ec-a5cb-2f179fbefff8
topic_type:
- apiref
ms.openlocfilehash: f60f159ab4770023cee7123b39109040243e1ccd
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73136967"
---
# <a name="_cordllmain-function"></a>\_fonction CorDllMain

Initialise le common language runtime (CLR), localise le point d’entrée managé dans l’en-tête CLR de l’assembly de DLL et commence l’exécution.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
BOOL STDMETHODCALLTYPE _CorDllMain (  
   [in] HINSTANCE hInst,  
   [in] DWORD     dwReason,  
   [in] LPVOID    lpReserved  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `hInst`  
 dans Handle d’instance du module chargé.  
  
 `dwReason`  
 dans Indique la raison pour laquelle la fonction de point d’entrée de la DLL est appelée. Ce paramètre peut avoir l’une des valeurs suivantes : DLL\_PROCESS_ATTACH, DLL\_THREAD\_attacher, DLL\_THREAD\_attacher ou DLL\_processus\_détacher. Pour obtenir une description de ces valeurs, consultez la documentation `DllMain` dans le kit de développement Platform SDK.  
  
 `lpReserved`  
 dans Inutilisé.  
  
## <a name="return-value"></a>Valeur de retour  
 Cette méthode retourne `true` pour Success et `false` si une erreur se produit.  
  
## <a name="remarks"></a>Notes  
 Cette fonction est appelée par le chargeur du système d’exploitation pour les assemblys DLL. Pour les assemblys exécutables, le chargeur appelle à la place la fonction [\_du CORExeMain](../../../../docs/framework/unmanaged-api/hosting/corexemain-function.md) .  
  
 Le chargeur du système d’exploitation appelle cette méthode quel que soit le point d’entrée spécifié dans le fichier DLL.  
  
La fonction `_CorDllMain` est appelée directement par le chargeur du système d’exploitation.
  
 Pour plus d’informations, consultez la section Notes de la rubrique [\_CorValidateImage](../../../../docs/framework/unmanaged-api/hosting/corvalidateimage-function.md) .  
  
## <a name="requirements"></a>spécifications  

 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** Cor. h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MsCorEE. dll  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Fonctions statiques globales des métadonnées](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
