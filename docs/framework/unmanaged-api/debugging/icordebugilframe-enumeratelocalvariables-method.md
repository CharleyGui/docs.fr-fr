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
ms.openlocfilehash: ad1a91e42f582ce96906da5cbf00ca89acb18499
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83210291"
---
# <a name="icordebugilframeenumeratelocalvariables-method"></a>ICorDebugILFrame::EnumerateLocalVariables, méthode
Obtient un énumérateur pour les variables locales dans ce frame.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT EnumerateLocalVariables(
    [out] ICorDebugValueEnum    **ppValueEnum  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `ppValueEnum`  
 [en sortie] Un pointeur vers l'adresse d'un objet ICorDebugValueEnum qui est l'énumérateur pour les variables locales de ce frame.  
  
## <a name="remarks"></a>Remarks  
 `EnumerateLocalVariables`Obtient un énumérateur qui peut répertorier les variables locales disponibles dans le frame d’appel qui est représenté par cet objet ICorDebugILFrame. La liste peut ne pas inclure toutes les variables locales dans la fonction en cours d’exécution, car certaines d’entre elles peuvent ne pas être actives.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
