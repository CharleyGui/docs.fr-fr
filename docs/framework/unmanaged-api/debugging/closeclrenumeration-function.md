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
ms.openlocfilehash: 3a05a779d4a56eb8f881da1824d5ffaa363b5a01
ms.sourcegitcommit: 3caa92cb97e9f6c31f21769c7a3f7c4304024b39
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/25/2019
ms.locfileid: "71274281"
---
# <a name="closeclrenumeration-function"></a>Fonction CloseCLREnumeration
Ferme tous les événements de continuation de common language runtime (CLR) valides situés dans un tableau de handles retournés par la [fonction EnumerateCLRs](enumerateclrs-function.md)et libère la mémoire pour les tableaux de handles et de chemins d’accès aux chaînes.  
  
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
 dans Pointeur vers le tableau de handles d’événement retourné par la [fonction EnumerateCLRs](enumerateclrs-function.md).  
  
 `pStringArray`  
 dans Pointeur vers le tableau de chemins d’accès aux chaînes CLR retourné par la [fonction EnumerateCLRs](enumerateclrs-function.md).  
  
 `dwArrayLength`  
 [in] Valeur DWORD contenant la taille (longueur) de `pHandleArray` ou de `pStringArray` (ils sont identiques).  
  
## <a name="return-value"></a>Valeur de retour  
 S_OK  
 Les handles ouverts par la [fonction EnumerateCLRs](enumerateclrs-function.md) sont fermés, et la mémoire allouée pour le handle et les tableaux de chaînes est libérée.  
  
 E_INVALIDARG  
 La longueur de `pHandleArray` ne correspond pas à la longueur passée dans `dwArrayLength`.  
  
 E_FAIL (ou autres codes de retour E_)  
 La fonction ne peut pas libérer la mémoire pour `pHandleArray` et `pStringArray`.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** dbgshim. h  
  
 **Bibliothèque :** dbgshim. dll  
  
 **Versions de .NET Framework :** 3.5 SP1
