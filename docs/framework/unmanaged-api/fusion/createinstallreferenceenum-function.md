---
title: Fonction CreateInstallReferenceEnum
ms.date: 03/30/2017
api_name:
- CreateInstallReferenceEnum
api_location:
- fusion.dll
- clr.dll
- mscorwks.dll
api_type:
- DLLExport
f1_keywords:
- CreateInstallReference
helpviewer_keywords:
- CreateInstallReference function [.NET Framework fusion]
ms.assetid: 80dbbbf8-54fc-4894-b74a-0179d3201083
topic_type:
- apiref
ms.openlocfilehash: 0f62b05ebbd8b27dba160c8281c1d40748c90fc9
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95688833"
---
# <a name="createinstallreferenceenum-function"></a>Fonction CreateInstallReferenceEnum

Obtient un pointeur vers une instance [IInstallReferenceEnum](iinstallreferenceenum-interface.md) qui représente une liste des références d’une application à l’assembly spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT CreateInstallReferenceEnum (  
    [out] IInstallReferenceEnum **ppRefEnum,  
    [in]  IAssemblyName         *pName,  
    [in]  DWORD                 dwFlags,  
    [in]  LPVOID                pvReserved  
 );  
```  
  
## <a name="parameters"></a>Paramètres  

 `ppRefEnum`  
 à Pointeur retourné `IInstallReferenceEnum` .  
  
 `pName`  
 dans [IAssemblyName](iassemblyname-interface.md) qui identifie l’assembly pour lequel énumérer les références.  
  
 `dwFlags`  
 dans Indicateurs qui influencent le comportement de l’énumérateur.  
  
 `pvReserved`  
 dans Réservé pour une future extensibilité. `pvReserved` doit être une référence null.  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** Fusion. h  
  
 **Bibliothèque :** Fusion.dll et Mscorwks.dll. Utilisez Fusion.dll au lieu de Mscorwks.dll pour vous assurer que vous ciblez la version correcte du .NET Framework.  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [IInstallReferenceEnum, interface](iinstallreferenceenum-interface.md)
- [IAssemblyName, interface](iassemblyname-interface.md)
- [Fonctions statiques globales de la fusion](fusion-global-static-functions.md)
