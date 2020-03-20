---
title: CLRDataCreateInstance, fonction
ms.date: 03/30/2017
api_name:
- CLRDataCreateInstance
api_location:
- mscordbi.dll
- mscordacwks.dll
api_type:
- COM
f1_keywords:
- CLRDataCreateInstance
helpviewer_keywords:
- CLRDataCreateInstance function [.NET Framework debugging]
ms.assetid: 440bad90-5a88-45e7-9157-4596801d8d19
topic_type:
- apiref
ms.openlocfilehash: c24963a6e56adfb9f763c6521027744db82cc357
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179359"
---
# <a name="clrdatacreateinstance-function"></a>CLRDataCreateInstance, fonction
Crée un objet d’interface pour l’élément cible spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT CLRDataCreateInstance (  
    [in]  REFIID           iid,
    [in]  ICLRDataTarget  *target,
    [out] void           **iface  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `iid`  
 [dans] L’identifiant de l’interface à instants.  
  
 `target`  
 [dans] Un pointeur vers un objet [ICLRDataTarget](iclrdatatarget-interface.md) implémenté par l’utilisateur qui représente l’élément cible pour lequel créer l’objet d’interface.  
  
 `iface`  
 [out] Un pointeur à l’adresse de l’objet d’interface retourné.  
  
## <a name="remarks"></a>Notes   
 L’objet `ICLRDataTarget` est implémenté par l’auteur de l’application de débogage. La mise en œuvre dépend du type d’élément cible représenté. L’élément cible peut être un processus, un dépotoir de mémoire, une machine à distance, et ainsi de suite.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête:** ClrData.idl  
  
 **Bibliothèque :** CorGuids.lib  
  
 **.NET Versions-cadre:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Fonctions statiques globales du débogage](debugging-global-static-functions.md)
