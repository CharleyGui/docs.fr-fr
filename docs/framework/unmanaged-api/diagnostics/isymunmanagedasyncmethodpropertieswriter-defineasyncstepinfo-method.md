---
title: ISymUnmanagedAsyncMethodPropertiesWriter::DefineAsyncStepInfo, méthode
ms.date: 03/30/2017
ms.assetid: f738a6ed-7cd9-4106-a5cd-355481e5771c
ms.openlocfilehash: 5a501cca16f06e7ccd5da9f65a213c6b24c1092c
ms.sourcegitcommit: 7b1497c1927cb449cefd313bc5126ae37df30746
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/16/2020
ms.locfileid: "83441784"
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
  
## <a name="return-value"></a>Valeur de retour  
 Retourne `HRESULT`.  
  
## <a name="requirements"></a>Conditions requises  
 **En-tête :** CorSym. idl, CorSym. h  
  
## <a name="see-also"></a>Voir aussi

- [ISymUnmanagedAsyncMethodPropertiesWriter, interface](isymunmanagedasyncmethodpropertieswriter-interface.md)
