---
title: Fonction CloseCLREnumeration
ms.date: 03/30/2017
api_name:
- CloseCLREnumeration
api_location:
- dbgshim.dll
api_type:
- COM
f1_keywords:
- CloseCLREnumeration
helpviewer_keywords:
- debugging API [Silverlight]
- Silverlight, debugging
- CloseCLR Enumeration function
ms.assetid: 5e3c3958-80bb-43b1-a96b-dd3e6dbd9cd7
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a9eb9bb1e4abeb98d8d0ba2b052612d918c45f22
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67741084"
---
# <a name="closeclrenumeration-function"></a>Fonction CloseCLREnumeration
Ferme tous valide common language runtime (CLR) continue-startup les événements situés dans un tableau de handles retourné par la [fonction EnumerateCLRs](../../../../docs/framework/unmanaged-api/debugging/enumerateclrs-function.md)et libère la mémoire pour les tableaux de chemin d’accès de handles et de chaînes.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT CloseCLREnumeration (  
    [in]  DWORD      pHandleArray,  
    [in]  LPWSTR**   pStringArray,  
    [in]  DWORD*     dwArrayLength  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `pHandleArray`  
 [in] Pointeur vers le tableau de handles d’événement retourné par la [fonction EnumerateCLRs](../../../../docs/framework/unmanaged-api/debugging/enumerateclrs-function.md).  
  
 `pStringArray`  
 [in] Pointeur vers le tableau de chemins d’accès de la chaîne CLR retourné à partir de la [fonction EnumerateCLRs](../../../../docs/framework/unmanaged-api/debugging/enumerateclrs-function.md).  
  
 `dwArrayLength`  
 [in] Valeur DWORD contenant la taille (longueur) de `pHandleArray` ou de `pStringArray` (ils sont identiques).  
  
## <a name="return-value"></a>Valeur de retour  
 S_OK  
 Handles ouverts par le [fonction EnumerateCLRs](../../../../docs/framework/unmanaged-api/debugging/enumerateclrs-function.md) sont fermés, et de la mémoire allouée pour les tableaux de handles et de chaînes est libérée.  
  
 E_INVALIDARG  
 La longueur de `pHandleArray` ne correspond pas à la longueur passée dans `dwArrayLength`.  
  
 E_FAIL (ou autres codes de retour E_)  
 La fonction ne peut pas libérer la mémoire pour `pHandleArray` et `pStringArray`.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** dbgshim.h  
  
 **Bibliothèque :** dbgshim.dll  
  
 **Versions du .NET framework :** 3.5 SP1
