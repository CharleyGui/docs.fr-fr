---
title: ICLRDataTarget3::GetExceptionRecord, méthode
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICLRDataTarget3.GetExceptionRecord
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 6643c2af-2ee6-4789-aa25-1d8eaf500c94
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b667ac16a4bbe6bdab1814b66fb1121b34b2d945
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69039580"
---
# <a name="iclrdatatarget3getexceptionrecord-method"></a>ICLRDataTarget3::GetExceptionRecord, méthode
Appelé par les services d'accès aux données du Common Langage Runtime (CLR) pour récupérer l'enregistrement d'exception associé au processus cible. Par exemple, pour une cible de vidage, cela équivaut à l’enregistrement d’exception passé via l' `ExceptionParam` argument à la fonction [entrée](/windows/desktop/api/minidumpapiset/nf-minidumpapiset-minidumpwritedump) dans la bibliothèque d’aide au débogage Windows (dbghelp).  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetExceptionRecord(  
    [in] ULONG32 bufferSize,  
    [out] ULONG32* bufferUsed,  
    [out, size_is(bufferSize] BYTE* buffer  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `bufferSize`  
 [en entrée] La taille de la mémoire tampon d'entrée, en octets. Doit être égal à `sizeof(` [MINIDUMP_EXCEPTION](/windows/win32/api/minidumpapiset/ns-minidumpapiset-minidump_exception)`)`.  
  
 `bufferUsed`  
 [en sortie] Un pointeur vers un type `ULONG32` qui reçoit le nombre d'octets réellement écrits dans la mémoire tampon.  
  
 `buffer`  
 [en sortie] Un pointeur vers une mémoire tampon qui reçoit une copie de l'enregistrement de l'exception. L’enregistrement d’exception est retourné en tant que type [MINIDUMP_EXCEPTION](/windows/win32/api/minidumpapiset/ns-minidumpapiset-minidump_exception) .  
  
## <a name="return-value"></a>Valeur de retour  
 La valeur de retour est `S_OK` en cas de réussite ou un code d'échec `HRESULT` en cas d'échec. Les codes `HRESULT` peuvent comprendre, sans y être limités, ce qui suit :  
  
|Code de retour|Description|  
|-----------------|-----------------|  
|`S_OK`|La méthode a réussi. L'enregistrement de l'exception a été copié dans la mémoire tampon de sortie.|  
|`HRESULT_FROM_WIN32(ERROR_NOT_FOUND)`|Aucun enregistrement d'exception n'est associé à la cible.|  
|`HRESULT_FROM_WIN32(ERROR_BAD_LENGTH)`|La taille de la mémoire tampon d'entrée est différente de `sizeof(MINIDUMP_EXCEPTION)`.|  
  
## <a name="remarks"></a>Notes  
 [MINIDUMP_EXCEPTION](/windows/win32/api/minidumpapiset/ns-minidumpapiset-minidump_exception) est une structure définie dans dbghelp. h et imagehlp. h dans le SDK Windows.  
  
 Cette méthode est implémentée par le writer de l'application de débogage.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** ClrData. idl, ClrData. h  
  
 **Bibliothèque** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[v451_update](../../../../includes/net-current-v451-nov-plus.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICLRDataTarget3, interface](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-interface.md)
- [GetExceptionContextRecord, méthode](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-getexceptioncontextrecord-method.md)
- [GetExceptionThreadID, méthode](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-getexceptionthreadid-method.md)
