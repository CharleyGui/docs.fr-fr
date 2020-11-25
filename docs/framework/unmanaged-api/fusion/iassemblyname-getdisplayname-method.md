---
title: IAssemblyName::GetDisplayName, méthode
ms.date: 03/30/2017
api_name:
- IAssemblyName.GetDisplayName
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyName::GetDisplayName
helpviewer_keywords:
- GetDisplayName method, IAssemblyName interface [.NET Framework fusion]
- IAssemblyName::GetDisplayName method [.NET Framework fusion]
ms.assetid: 9a26547a-9a34-4284-a463-78a7d4b496cf
topic_type:
- apiref
ms.openlocfilehash: 13d71a9da2539c45076e5eb92e153e37c1df4b47
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95727911"
---
# <a name="iassemblynamegetdisplayname-method"></a>IAssemblyName::GetDisplayName, méthode

Obtient le nom explicite de l’assembly référencé par cet objet [IAssemblyName](iassemblyname-interface.md) .  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetDisplayName (  
        [out]      LPOLESTR  szDisplayName,  
        [in, out]  LPDWORD   pccDisplayName,  
        [in]       DWORD     dwDisplayFlags  
);  
```  
  
## <a name="parameters"></a>Paramètres  

 `szDisplayName`  
 à Mémoire tampon de chaîne qui contient le nom de l’assembly référencé.  
  
 `pccDisplayName`  
 [in, out] Taille de `szDisplayName` en caractères larges, y compris un caractère de fin null.  
  
 `dwDisplayFlags`  
 dans Combinaison d’opérations de bits de valeurs [ASM_DISPLAY_FLAGS](asm-display-flags-enumeration.md) qui influencent les fonctionnalités de `szDisplayName` .  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** Fusion. h  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [IAssemblyName, interface](iassemblyname-interface.md)
- [Énumérations de fusion](fusion-enumerations.md)
