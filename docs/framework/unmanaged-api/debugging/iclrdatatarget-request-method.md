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
ms.openlocfilehash: 336ba38bc80fcb2649a12c78691e52c5e4d70bfe
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179113"
---
# <a name="iclrdatatargetrequest-method"></a>ICLRDataTarget::Request, méthode
Appelés par les services d’accès aux données de l’heure courante (CLR) pour demander une opération, tel que défini par la mise en œuvre.  
  
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
 [dans] Défini par l’utilisateur.  
  
 `inBufferSize`  
 [dans] La taille du tampon d’entrée, qui est utilisé pour la demande entrante.  
  
 `inBuffer`  
 [dans] Un tampon contenant la demande.  
  
 `outBufferSize`  
 [dans] La taille du tampon de sortie, qui est utilisé pour la réponse.  
  
 `outBuffer`  
 [out] Un tampon contenant la réponse.  
  
## <a name="remarks"></a>Notes   
 La `Request` méthode facilite l’ajout d’opérations personnalisées non spécifiées. C’est-à-dire que cette méthode fournit l’extéponsabilité sans nécessiter la révision de la définition de l’interface.  
  
 Cette méthode est implémentée par le writer de l'application de débogage.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête:** ClrData.idl, ClrData.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **.NET Versions-cadre:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICLRDataTarget, interface](iclrdatatarget-interface.md)
