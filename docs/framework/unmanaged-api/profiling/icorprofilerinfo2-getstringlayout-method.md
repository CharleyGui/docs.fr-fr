---
title: ICorProfilerInfo2::GetStringLayout, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetStringLayout
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetStringLayout
helpviewer_keywords:
- GetStringLayout method [.NET Framework profiling]
- ICorProfilerInfo2::GetStringLayout method [.NET Framework profiling]
ms.assetid: 43189651-a535-4803-a1d1-f1c427ace2ca
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: faa5ecf63ac3795a58369d94f9fb15f853edb576
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2019
ms.locfileid: "66490712"
---
# <a name="icorprofilerinfo2getstringlayout-method"></a>ICorProfilerInfo2::GetStringLayout, méthode
Obtient des informations sur la disposition d'un objet string. Cette méthode est déconseillée dans le .NET Framework 4 et est remplacée par la [ICorProfilerInfo3::GetStringLayout2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getstringlayout2-method.md) (méthode).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetStringLayout(  
    [out] ULONG *pBufferLengthOffset,  
    [out] ULONG *pStringLengthOffset,  
    [out] ULONG *pBufferOffset);  
```  
  
## <a name="parameters"></a>Paramètres  
 `pBufferLengthOffset`  
 [out] Un pointeur vers l’offset de l’emplacement, relatif à la `ObjectID` pointeur, qui stocke la longueur de la chaîne. La longueur est stockée comme un `DWORD`.  
  
> [!NOTE]
>  Ce paramètre retourne la longueur de la chaîne elle-même, pas la longueur de la mémoire tampon. La longueur de la mémoire tampon n’est plus disponible.  
  
 `PStringLengthOffset`  
 [out] Un pointeur vers l’offset de l’emplacement, relatif à la `ObjectID` pointeur, qui stocke la longueur de la chaîne elle-même. La longueur est stockée comme un `DWORD`.  
  
 `pBufferOffset`  
 [out] Un pointeur vers l’offset de la mémoire tampon, relative à la `ObjectID` pointeur, qui stocke la chaîne de caractères larges.  
  
## <a name="remarks"></a>Notes  
 Le `GetStringLayout` méthode obtient les offsets, relatif à la `ObjectID` pointeur, des emplacements dans lesquels sont stockés les éléments suivants :  
  
- La longueur de la mémoire tampon de la chaîne.  
  
- La longueur de la chaîne elle-même.  
  
- La mémoire tampon qui contient la chaîne réelle de caractères larges.  
  
 Chaînes peuvent être se terminant par null.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorProf.idl, CorProf.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorProfilerInfo, interface](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [ICorProfilerInfo2, interface](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
