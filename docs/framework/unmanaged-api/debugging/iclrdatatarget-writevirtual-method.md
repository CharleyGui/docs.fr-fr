---
title: ICLRDataTarget::WriteVirtual, méthode
ms.date: 03/30/2017
api_name:
- ICLRDataTarget.WriteVirtual
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataTarget::WriteVirtual
helpviewer_keywords:
- ICLRDataTarget::WriteVirtual method [.NET Framework debugging]
- WriteVirtual method [.NET Framework debugging]
ms.assetid: d627e8b7-a605-40ac-b9bb-da9a3f1b66d9
topic_type:
- apiref
ms.openlocfilehash: bd2f67c2d7230d3873b4dc0df73ac1be778a0828
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179098"
---
# <a name="iclrdatatargetwritevirtual-method"></a>ICLRDataTarget::WriteVirtual, méthode
Rédige les données du tampon spécifié à l’adresse de mémoire virtuelle spécifiée.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT WriteVirtual (  
    [in] CLRDATA_ADDRESS    address,  
    [in, size_is(bytesRequested)]
        BYTE                *buffer,  
    [in] ULONG32            bytesRequested,  
    [out] ULONG32           *bytesWritten  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `address`  
 [dans] Une CLRDATA_ADDRESS qui stocke l’adresse mémoire virtuelle.  
  
 `buffer`  
 [dans] Un pointeur vers un tampon qui stocke les données à écrire.  
  
 `bytesRequested`  
 [dans] Le nombre d’octets à écrire.  
  
 `bytesWritten`  
 [out] Un pointeur sur le nombre réel d’octets qui ont été écrits.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête:** ClrData.idl, ClrData.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **.NET Versions-cadre:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICLRDataTarget, interface](iclrdatatarget-interface.md)
