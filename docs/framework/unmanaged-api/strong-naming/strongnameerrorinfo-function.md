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
ms.openlocfilehash: d5eedc34b75d3a0c02969c06454b0f7ec942ed17
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176940"
---
# <a name="strongnameerrorinfo-function"></a>StrongNameErrorInfo, fonction
Obtient le dernier code d’erreur déclenché par l’une des fonctions de nom fort.  
  
 Cette fonction a été dépréciée.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT StrongNameErrorInfo ();
```  
  
## <a name="return-value"></a>Valeur de retour  
 Le dernier code d’erreur COM défini par l’une des fonctions de nom fort.  
  
## <a name="remarks"></a>Notes   
 La plupart des méthodes de `true` `false` nom forte renvoient une simple ou indication d’achèvement réussi. Utilisez `StrongNameErrorInfo` la fonction pour récupérer un HRESULT qui spécifie la dernière erreur générée par les fonctions de nom fort.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête:** StrongName.h (en)  
  
 **Bibliothèque:** Inclus comme une ressource dans MsCorEE.dll  
  
 **.NET Versions-cadre:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
