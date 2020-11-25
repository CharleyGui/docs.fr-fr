---
title: ICeeGen::GetSectionBlock, méthode
ms.date: 03/30/2017
api_name:
- ICeeGen.GetSectionBlock
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICeeGen::GetSectionBlock
helpviewer_keywords:
- GetSectionBlock method [.NET Framework metadata]
- ICeeGen::GetSectionBlock method [.NET Framework metadata]
ms.assetid: 05c78aaf-5bbd-497e-9ae2-55f4fae0c5fb
topic_type:
- apiref
ms.openlocfilehash: 9ce3afded5f914ecf970d8db738becc7f5cfff84
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95723140"
---
# <a name="iceegengetsectionblock-method"></a>ICeeGen::GetSectionBlock, méthode

Obtient un bloc de section de la base de code.  
  
 Cette méthode est obsolète et ne doit pas être utilisée.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetSectionBlock (  
    [in]  HCEESECTION    section,
    [in]  ULONG          len,  
    [in]  ULONG          align     = 1,  
    [out] void           **ppBytes = 0  
);
```  
  
## <a name="parameters"></a>Paramètres  

 `section`  
 dans Section à partir de laquelle récupérer un bloc de la base de code.  
  
 `len`  
 dans Longueur du bloc à récupérer.  
  
 `align`  
 dans Octet, relatif au début de la section, avec lequel aligner le premier octet du bloc. Il s’agit de la position du bloc dans la section.  
  
 `ppBytes`  
 à Pointeur vers un emplacement qui reçoit l’adresse du bloc récupéré.  
  
## <a name="remarks"></a>Remarques  

 Appelez `GetSectionBlock` uniquement si vous avez des exigences de section spéciales qui ne sont pas gérées par d’autres méthodes.  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** Cor. h  
  
 **Bibliothèque :** Utilisé en tant que ressource dans MsCorEE.dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICeeGen, interface](iceegen-interface.md)
