---
title: ICorDebugType::GetBase, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugType.GetBase
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugType::GetBase
helpviewer_keywords:
- ICorDebugType::GetBase method [.NET Framework debugging]
- GetBase method [.NET Framework debugging]
ms.assetid: f24e1af9-c220-4f79-ae62-4153ec17ea81
topic_type:
- apiref
ms.openlocfilehash: 967f8f25e240f484ae86852c740be12cd3a6409e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95681819"
---
# <a name="icordebugtypegetbase-method"></a>ICorDebugType::GetBase, méthode

Obtient un pointeur d’interface vers un ICorDebugType qui représente le type de base, le cas échéant, du type représenté par ce `ICorDebugType` .  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetBase (  
    [out] ICorDebugType   **pBase  
);  
```  
  
## <a name="parameters"></a>Paramètres  

 `pBase`  
 à Pointeur vers l’adresse d’un `ICorDebugType` objet qui représente le type de base.  
  
## <a name="remarks"></a>Remarques  

 La recherche du type de base pour un type est utile pour implémenter les fonctionnalités de débogueur courantes, telles que l’impression de tous les champs d’un objet ou de ses classes parentes.  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
