---
title: GetAppIdAuthority, fonction
ms.date: 03/30/2017
api_name:
- GetAppIdAuthority
api_location:
- fusion.dll
- clr.dll
api_type:
- COM
f1_keywords:
- GetAppIdAuthority
helpviewer_keywords:
- GetAppIdAuthority function [.NET Framework fusion]
ms.assetid: 9f968dad-0d09-47fb-bebc-94c39a0d16ad
topic_type:
- apiref
ms.openlocfilehash: 5e731ac1c652b8b4505073a3a10463ae0ce21ac0
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95724492"
---
# <a name="getappidauthority-function"></a>GetAppIdAuthority, fonction

Obtient un pointeur vers une instance [IAppIdAuthority](iappidauthority-interface.md) qui gère les clés pour les identités et les références de l’application.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetAppIdAuthority (  
    [out] IAppIdAuthority **ppIAppIdAuthority  
 );  
```  
  
## <a name="parameters"></a>Paramètres  

 `ppIAppIdAuthority`  
 à Pointeur retourné `IAppIdAuthority` .  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** Isolation. h  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [IAppIdAuthority, interface](iappidauthority-interface.md)
- [Fonctions statiques globales de la fusion](fusion-global-static-functions.md)
