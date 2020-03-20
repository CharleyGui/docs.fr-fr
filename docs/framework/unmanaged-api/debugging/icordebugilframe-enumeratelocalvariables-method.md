---
title: ICorDebugILFrame::EnumerateLocalVariables, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugILFrame.EnumerateLocalVariables
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugILFrame::EnumerateLocalVariables
helpviewer_keywords:
- EnumerateLocalVariables method [.NET Framework debugging]
- ICorDebugILFrame::EnumerateLocalVariables method [.NET Framework debugging]
ms.assetid: 1a67fa1b-2419-4cd0-aad4-6f46a0719b4b
topic_type:
- apiref
ms.openlocfilehash: c071a7ddb7d8d3f0e6487ab85284c45f9a7f0372
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178846"
---
# <a name="icordebugilframeenumeratelocalvariables-method"></a>ICorDebugILFrame::EnumerateLocalVariables, méthode
Obtient un enumérateur pour les variables locales dans ce cadre.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT EnumerateLocalVariables(
    [out] ICorDebugValueEnum    **ppValueEnum  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `ppValueEnum`  
 [en sortie] Un pointeur vers l'adresse d'un objet ICorDebugValueEnum qui est l'énumérateur pour les variables locales de ce frame.  
  
## <a name="remarks"></a>Notes   
 `EnumerateLocalVariables`obtient un enumérateur qui peut énumérer les variables locales disponibles dans le cadre d’appel qui est représenté par cet objet ICorDebugILFrame. La liste peut ne pas inclure toutes les variables locales dans la fonction de fonctionnement, parce que certaines d’entre elles peuvent ne pas être actives.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **.NET Versions-cadre:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
