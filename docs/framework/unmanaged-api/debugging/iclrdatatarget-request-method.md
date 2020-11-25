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
ms.openlocfilehash: 4d0cf22b4b0644d6b25d6b3ef884718cb9ca1e42
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95723777"
---
# <a name="iclrdatatargetrequest-method"></a>ICLRDataTarget::Request, méthode

Appelée par les services d’accès aux données common language runtime (CLR) pour demander une opération, comme défini par l’implémentation.  
  
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
 dans Défini par l’utilisateur.  
  
 `inBufferSize`  
 dans Taille de la mémoire tampon d’entrée utilisée pour la demande entrante.  
  
 `inBuffer`  
 dans Mémoire tampon contenant la demande.  
  
 `outBufferSize`  
 dans Taille de la mémoire tampon de sortie, qui est utilisée pour la réponse.  
  
 `outBuffer`  
 à Mémoire tampon contenant la réponse.  
  
## <a name="remarks"></a>Remarques  

 La `Request` méthode facilite l’ajout d’opérations personnalisées non spécifiées. Autrement dit, cette méthode fournit l’extensibilité sans nécessiter de révision de la définition de l’interface.  
  
 Cette méthode est implémentée par le writer de l'application de débogage.  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** ClrData. idl, ClrData. h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICLRDataTarget, interface](iclrdatatarget-interface.md)
