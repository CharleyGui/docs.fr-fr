---
title: CreateApplicationContext, fonction
ms.date: 03/30/2017
api_name:
- CreateApplicationContext
api_location:
- fusion.dll
api_type:
- DLLExport
f1_keywords:
- CreateApplicationContext
helpviewer_keywords:
- CreateApplicationContext function [.NET Framework fusion]
ms.assetid: 7bf8a141-b2c0-4058-9885-1cef7dcaa811
topic_type:
- apiref
ms.openlocfilehash: 9418be85f5b72bac8eed7f5ea4af4fc42439b01f
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95683227"
---
# <a name="createapplicationcontext-function"></a>CreateApplicationContext, fonction

Cette fonction prend en charge l’infrastructure .NET Framework et n’est pas destinée à être utilisée directement à partir de votre code.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT CreateApplicationContext (  
    [in]  IAssemblyName  *pName,  
    [out] LPPAPPLICATIONCONTEXT  *ppCtx  
 );  
```  
  
## <a name="parameters"></a>Paramètres  

 `pName`  
 dans Pointeur vers un nom convivial.  
  
 `ppCtx`  
 à Pointeur vers un contexte d’application.  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** Fusion. h  
  
 **Bibliothèque :** Inclus en tant que ressource dans Fusion.dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [IAssemblyCache, interface](iassemblycache-interface.md)
- [Fonctions statiques globales de la fusion](fusion-global-static-functions.md)
- [Global Assembly Cache](../../app-domains/gac.md)
