---
title: ICLRDataTarget::Request, méthode
ms.date: 03/30/2017
api_name:
- ICLRDataTarget.Request
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataTarget::Request
helpviewer_keywords:
- ICLRDataTarget::Request method [.NET Framework debugging]
- Request method [.NET Framework debugging]
ms.assetid: 4723bd1c-eddb-4ed2-897a-010024a47e01
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5f6926d66a438cfc4fd97d7120e359b737212dde
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67738629"
---
# <a name="iclrdatatargetrequest-method"></a>ICLRDataTarget::Request, méthode
Appelé par les services d’accès aux données du common language runtime (CLR) pour demander une opération, tel que défini par l’implémentation.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT Request (  
    [in] ULONG32            reqCode,  
    [in] ULONG32            inBufferSize,  
    [in, size_is(inBufferSize)]   
        BYTE                *inBuffer,  
    [in] ULONG32            outBufferSize,  
    [out, size_is(outBufferSize)]   
        BYTE                *outBuffer  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `reqCode`  
 [in] Défini par l’utilisateur.  
  
 `inBufferSize`  
 [in] La taille de la mémoire tampon d’entrée, qui est utilisé pour la demande entrante.  
  
 `inBuffer`  
 [in] Une mémoire tampon contenant la demande.  
  
 `outBufferSize`  
 [in] La taille de la mémoire tampon de sortie, qui est utilisé pour la réponse.  
  
 `outBuffer`  
 [out] Une mémoire tampon contenant la réponse.  
  
## <a name="remarks"></a>Notes  
 Le `Request` méthode facilite l’ajout d’opérations personnalisées non spécifiées. Autrement dit, cette méthode fournit une extensibilité sans nécessiter une révision de la définition d’interface.  
  
 Cette méthode est implémentée par le writer de l'application de débogage.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** ClrData.idl, ClrData.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICLRDataTarget, interface](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)
