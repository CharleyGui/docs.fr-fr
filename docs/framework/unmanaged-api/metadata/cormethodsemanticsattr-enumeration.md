---
title: CorMethodSemanticsAttr, énumération
ms.date: 03/30/2017
api_name:
- CorMethodSemanticsAttr
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorMethodSemanticsAttr
helpviewer_keywords:
- CorMethodSemanticsAttr enumeration [.NET Framework metadata]
ms.assetid: ca2af325-eb9d-4a91-90e4-267e45b98611
topic_type:
- apiref
ms.openlocfilehash: 347b323951b0125ffa5f82626b2d9b235079492c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95676944"
---
# <a name="cormethodsemanticsattr-enumeration"></a>CorMethodSemanticsAttr, énumération

Contient des valeurs qui décrivent la relation entre une méthode et une propriété ou un événement associé.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef enum CorMethodSemanticsAttr {  
  
    msSetter    =   0x0001,  
    msGetter    =   0x0002,  
    msOther     =   0x0004,  
    msAddOn     =   0x0008,  
    msRemoveOn  =   0x0010,  
    msFire      =   0x0020,  
  
} CorMethodSemanticsAttr;  
```  
  
## <a name="members"></a>Membres  
  
|Membre|Description|  
|------------|-----------------|  
|`msSetter`|Spécifie que la méthode est un `set` accesseur pour une propriété.|  
|`msGetter`|Spécifie que la méthode est un `get` accesseur pour une propriété.|  
|`msOther`|Spécifie que la méthode a une relation avec une propriété ou un événement autre que ceux définis ici.|  
|`msAddOn`|Spécifie que la méthode ajoute des méthodes de gestionnaire pour un événement.|  
|`msRemoveOn`|Spécifie que la méthode supprime les méthodes de gestionnaire pour un événement.|  
|`msFire`|Spécifie que la méthode déclenche un événement.|  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorHdr. h  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Énumérations de métadonnées](metadata-enumerations.md)
