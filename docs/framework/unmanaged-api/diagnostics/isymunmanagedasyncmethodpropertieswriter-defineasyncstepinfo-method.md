---
title: ISymUnmanagedAsyncMethodPropertiesWriter::DefineAsyncStepInfo, méthode
ms.date: 03/30/2017
ms.assetid: f738a6ed-7cd9-4106-a5cd-355481e5771c
ms.openlocfilehash: f8c77e44183fd92704aa91ca1cfd7e3fa68aa27f
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95719617"
---
# <a name="isymunmanagedasyncmethodpropertieswriterdefineasyncstepinfo-method"></a>ISymUnmanagedAsyncMethodPropertiesWriter::DefineAsyncStepInfo, méthode

Définissez un groupe d’opérations await Async dans la méthode actuelle.  
  
 Chaque décalage de rendement correspond à l’instruction de retour d’une instruction await, identifiant un rendement potentiel. Chaque `breakpointMethod` / `breakpointOffset` paire nous indique où l’opération asynchrone reprend, qui peut se trouver dans une méthode différente.  
  
## <a name="syntax"></a>Syntaxe  
  
```idl  
HRESULT DefineAsyncStepInfo(    [in] ULONG32 count,    [in, size_is(count)] ULONG32 yieldOffsets[],    [in, size_is(count)] ULONG32 breakpointOffset[],     [in, size_is(count)] mdToken breakpointMethod[]);  
```  
  
## <a name="parameters"></a>Paramètres  
  
|Paramètre|Description|  
|---------------|-----------------|  
|`count`||  
|`yieldOffsets`||  
|`breakpointOffset`||  
|`breakpointMethod`||  
  
## <a name="return-value"></a>Valeur renvoyée  

 Retourne `HRESULT`.  
  
## <a name="requirements"></a>Configuration requise  

 **En-tête :** CorSym. idl, CorSym. h  
  
## <a name="see-also"></a>Voir aussi

- [ISymUnmanagedAsyncMethodPropertiesWriter, interface](isymunmanagedasyncmethodpropertieswriter-interface.md)
