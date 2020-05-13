---
title: ICorDebugILFrame2::EnumerateTypeParameters, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugILFrame2.EnumerateTypeParameters
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugILFrame2::EnumerateTypeParameters
helpviewer_keywords:
- EnumerateTypeParameters method, ICorDebugILFrame2 interface [.NET Framework debugging]
- ICorDebugILFrame2::EnumerateTypeParameters method [.NET Framework debugging]
ms.assetid: 722d0d74-e0df-491f-98c4-62d501dfaf6f
topic_type:
- apiref
ms.openlocfilehash: 9020fed83b1c57cae3cc492872a279afb0195983
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83205173"
---
# <a name="icordebugilframe2enumeratetypeparameters-method"></a>ICorDebugILFrame2::EnumerateTypeParameters, méthode
Obtient un objet ICorDebugTypeEnum qui contient les <xref:System.Type> paramètres de ce frame.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT EnumerateTypeParameters (  
    [out] ICorDebugTypeEnum    **ppTyParEnum  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `ppTyParEnum`  
 Pointeur vers l’adresse d’un objet d’interface ICorDebugTypeEnum qui autorise l’énumération des paramètres de type.  
  
 La liste des paramètres de type inclut les paramètres de type de classe (le cas échéant) suivis des paramètres de type de méthode (le cas échéant).  
  
## <a name="remarks"></a>Remarks  
 Utilisez la méthode [IMetaDataImport2 :: EnumGenericParams,](../metadata/imetadataimport2-enumgenericparams-method.md) pour déterminer le nombre de paramètres de type de classe et de paramètres de type de méthode que cette liste contient.  
  
 Les paramètres de type ne sont pas toujours disponibles.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
