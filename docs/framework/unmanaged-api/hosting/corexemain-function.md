---
title: _CorExeMain, fonction
ms.date: 03/30/2017
api_name:
- _CorExeMain
api_location:
- mscoree.dll
- clr.dll
- mscorwks.dll
- mscoreei.dll
api_type:
- DLLExport
f1_keywords:
- _CorExeMain
helpviewer_keywords:
- _CorExeMain function [.NET Framework hosting]
ms.assetid: 898f76e2-16f4-4a63-b7d9-dad2d3824d8a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f97e90e3953a01f07d77e604628fbdb79eb9efa0
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67779180"
---
# <a name="corexemain-function"></a>_CorExeMain, fonction
Initialise le common language runtime (CLR), recherche le point d’entrée managé dans l’en-tête CLR de l’assembly exécutable et commence l’exécution.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
__int32 STDMETHODCALLTYPE _CorExeMain ();  
```  
  
## <a name="remarks"></a>Notes  
 Cette fonction est appelée par le chargeur de processus créés à partir d’assemblys exécutables managés. Pour les assemblys DLL, le chargeur appelle le [_CorDllMain](../../../../docs/framework/unmanaged-api/hosting/cordllmain-function.md) fonctionner à la place.  
  
 Le chargeur du système d’exploitation appelle cette méthode, quel que soit le point d’entrée spécifié dans le fichier image.  
  
 Dans Windows 98, Windows ME, Windows NT et Windows 2000, le `_CorExeMain` fonction est appelée indirectement via une correction dans le chargeur du système d’exploitation. Dans tous les autres versions de Windows, elle est appelée directement par le chargeur du système d’exploitation.  
  
 Pour plus d’informations, consultez la section Remarques dans le [_CorValidateImage](../../../../docs/framework/unmanaged-api/hosting/corvalidateimage-function.md) rubrique.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** Cor.h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MsCorEE.dll  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Fonctions statiques globales des métadonnées](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
