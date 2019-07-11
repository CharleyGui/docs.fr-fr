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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9a02a899fd6fbffd04ef25913adb6a65ade27177
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67755661"
---
# <a name="cordllmain-function"></a>\_CorDllMain (fonction)

Initialise le common language runtime (CLR), recherche le point d’entrée managé dans l’en-tête CLR de l’assembly DLL et commence l’exécution.  
  
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
 [in] Le handle d’instance du module chargé.  
  
 `dwReason`  
 [in] Indique la raison pour laquelle la fonction de point d’entrée DLL est appelée. Ce paramètre peut être une des valeurs suivantes : DLL\_PROCESS_ATTACH, DLL\_THREAD\_attacher, DLL\_THREAD\_attacher ou DLL\_processus\_détacher. Pour obtenir une description de ces valeurs, consultez le `DllMain` documentation dans le kit Platform SDK.  
  
 `lpReserved`  
 [in] Inutilisé.  
  
## <a name="return-value"></a>Valeur de retour  
 Cette méthode retourne `true` de réussite et `false` si une erreur se produit.  
  
## <a name="remarks"></a>Notes  
 Cette fonction est appelée par le chargeur du système d’exploitation pour les assemblys DLL. Pour les assemblys exécutables, le chargeur appelle le [ \_CorExeMain](../../../../docs/framework/unmanaged-api/hosting/corexemain-function.md) fonctionner à la place.  
  
 Le chargeur du système d’exploitation appelle cette méthode, quel que soit le point d’entrée spécifié dans le fichier DLL.  
  
Le `_CorDllMain` fonction est appelée directement par le chargeur du système d’exploitation.
  
 Pour plus d’informations, consultez la section Remarques dans le [ \_CorValidateImage](../../../../docs/framework/unmanaged-api/hosting/corvalidateimage-function.md) rubrique.  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** Cor.h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MsCorEE.dll  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Fonctions statiques globales des métadonnées](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
