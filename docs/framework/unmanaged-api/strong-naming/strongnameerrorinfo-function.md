---
title: StrongNameErrorInfo, fonction
ms.date: 03/30/2017
api_name:
- StrongNameErrorInfo
api_location:
- mscoree.dll
- mscorsn.dll
- clr.dll
- mscorwks.dll
- mscoreei.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameErrorInfo
helpviewer_keywords:
- StrongNameErrorInfo function [.NET Framework strong naming]
ms.assetid: e91bf8c3-7c26-4732-938e-2e5b04abfc99
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a6f495500b087b9e24936acd414f1aff463d7f64
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67781077"
---
# <a name="strongnameerrorinfo-function"></a>StrongNameErrorInfo, fonction
Obtient le dernier code d’erreur déclenché par l’une des fonctions de nom fort.  
  
 Cette fonction a été déconseillée.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT StrongNameErrorInfo ();   
```  
  
## <a name="return-value"></a>Valeur de retour  
 Code d’erreur COM dernier défini par une des fonctions à nom fort.  
  
## <a name="remarks"></a>Notes  
 La plupart des méthodes à nom fort retournent une simple `true` ou `false` indication de leur achèvement. Utilisez le `StrongNameErrorInfo` fonction pour récupérer un HRESULT qui spécifie la dernière erreur générée par les fonctions de nom fort.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** StrongName.h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MsCorEE.dll  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
