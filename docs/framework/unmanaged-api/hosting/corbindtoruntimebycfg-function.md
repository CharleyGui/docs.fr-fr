---
title: CorBindToRuntimeByCfg, fonction
ms.date: 03/30/2017
api_name:
- CorBindToRuntimeByCfg
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- CorBindToRuntimeByCfg
helpviewer_keywords:
- CorBindToRuntimeByCfg function [.NET Framework hosting]
ms.assetid: ded1e492-a782-4185-9c66-709e421c1782
topic_type:
- apiref
ms.openlocfilehash: d319382b577844a804c3e4562676491a15de5f63
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95673772"
---
# <a name="corbindtoruntimebycfg-function"></a>CorBindToRuntimeByCfg, fonction

Charge le common language runtime (CLR) dans un processus à l’aide des informations de version lues à partir d’un fichier XML.  
  
 Cette fonction a été dépréciée dans le .NET Framework 4.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT CorBindToRuntimeByCfg (  
    [in]  IStream     *pCfgStream,  
    [in]  DWORD        reserved,  
    [in]  DWORD        startupFlags,  
    [in]  REFCLSID     rclsid,  
    [in]  REFIID       riid,
    [out] LPVOID FAR*  ppv  
);  
```  
  
## <a name="parameters"></a>Paramètres  

 `pCfgStream`  
 dans Pointeur vers un `IStream` objet qui lit le fichier XML.  
  
 `reserved`  
 [in] Réservé pour une future utilisation. Utilisez 0 (zéro) comme valeur.  
  
 `startupFlags`  
 dans Valeur de l’énumération [STARTUP_FLAGS](startup-flags-enumeration.md) qui spécifie le comportement de démarrage du CLR.  
  
 `rclsid`  
 dans `CLSID` De la coclasse qui implémente l’interface [ICorRuntimeHost](icorruntimehost-interface.md) ou [ICLRRuntimeHost](iclrruntimehost-interface.md) . Les valeurs prises en charge sont CLSID_CorRuntimeHost ou CLSID_CLRRuntimeHost.  
  
 `riid`  
 dans `IID` De l' `ICorRuntimeHost` `ICLRRuntimeHost` interface ou. Les valeurs prises en charge sont IID_ICorRuntimeHost ou IID_ICLRRuntimeHost.  
  
 `ppv`  
 à Pointeur vers l’adresse de l’interface retournée.  
  
## <a name="remarks"></a>Remarques  

 Le format du fichier XML est modélisé après le fichier de configuration d’application standard. Pour plus d’informations sur les fichiers XML, consultez [schéma du fichier de configuration](../../configure-apps/file-schema/index.md).  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE. h  
  
 **Bibliothèque :** MSCorEE.dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [CorBindToCurrentRuntime, fonction](corbindtocurrentruntime-function.md)
- [CorBindToRuntime, fonction](corbindtoruntime-function.md)
- [CorBindToRuntimeEx, fonction](corbindtoruntimeex-function.md)
- [CorBindToRuntimeHost, fonction](corbindtoruntimehost-function.md)
- [ICorRuntimeHost, interface](icorruntimehost-interface.md)
- [Fonction d'hébergement du CLR déconseillées](deprecated-clr-hosting-functions.md)
