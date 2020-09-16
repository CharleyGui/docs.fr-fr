---
title: CorBindToCurrentRuntime, fonction
ms.date: 03/30/2017
api_name:
- CorBindToCurrentRuntime
api_location:
- mscoree.dll
- mscoreei.dll
api_type:
- HeaderDef
f1_keywords:
- CorBindToCurrentRuntime
helpviewer_keywords:
- CorBindToCurrentRuntime function [.NET Framework hosting]
ms.assetid: 6105c13e-d9cd-44d2-a95a-924e042830c7
topic_type:
- apiref
ms.openlocfilehash: 9c5d83b5f2ffb06c9fb14f715a3ea7ff12319086
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90547827"
---
# <a name="corbindtocurrentruntime-function"></a>CorBindToCurrentRuntime, fonction
Charge le common language runtime (CLR) dans un processus à l’aide des informations de version stockées dans un fichier XML. Le format du fichier XML est modélisé après le fichier de configuration d’application standard. Pour plus d’informations sur les fichiers de configuration, consultez [Schéma des fichiers de configuration](../../configure-apps/file-schema/index.md).  
  
 Cette fonction a été dépréciée dans le .NET Framework 4. Consultez [chargement du Common Language Runtime dans un processus](/previous-versions/dotnet/netframework-4.0/01918c6x(v=vs.100)).  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT CorBindToCurrentRuntime (  
    [in]  LPCWSTR   pwszFileName,  
    [in]  REFCLSID  rclsid,  
    [in]  REFIID    riid,  
    [out] LPVOID    *ppv  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `pwszFileName`  
 dans Nom d’un fichier de configuration d’application qui spécifie la version du CLR à charger. Si le nom de fichier n’est pas qualifié complet, il est supposé être dans le même répertoire que l’exécutable qui effectue l’appel.  
  
 La version du runtime à charger est décrite par l’attribut version dans l' [\<requiredRuntime>](../../configure-apps/file-schema/startup/requiredruntime-element.md) élément du fichier de configuration.  
  
 Si aucune version n’est spécifiée, ou si l' `<requiredRuntime>` élément est introuvable, la dernière version du CLR qui est installée sur l’ordinateur est chargée.  
  
 `rclsid`  
 dans `CLSID` De la coclasse qui implémente l’interface [ICorRuntimeHost](icorruntimehost-interface.md) ou [ICLRRuntimeHost](iclrruntimehost-interface.md) . Les valeurs prises en charge sont CLSID_CorRuntimeHost ou CLSID_CLRRuntimeHost.  
  
 `riid`  
 dans `IID` De l’interface que vous demandez. Les valeurs prises en charge sont IID_ICorRuntimeHost ou IID_ICLRRuntimeHost.  
  
 `ppv`  
 à Pointeur d’interface retourné.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE. h  
  
 **Bibliothèque :** MSCorEE.dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [CorBindToRuntime, fonction](corbindtoruntime-function.md)
- [CorBindToRuntimeByCfg, fonction](corbindtoruntimebycfg-function.md)
- [CorBindToRuntimeEx, fonction](corbindtoruntimeex-function.md)
- [CorBindToRuntimeHost, fonction](corbindtoruntimehost-function.md)
- [ICorRuntimeHost, interface](icorruntimehost-interface.md)
- [Fonction d'hébergement du CLR déconseillées](deprecated-clr-hosting-functions.md)
