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
ms.openlocfilehash: 90abfcd573795ae529714e21b13f90d6e15c7dad
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95732266"
---
# <a name="strongnameerrorinfo-function"></a>StrongNameErrorInfo, fonction

Obtient le dernier code d’erreur déclenché par l’une des fonctions de nom fort.  
  
 Cette fonction a été dépréciée.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT StrongNameErrorInfo ();
```  
  
## <a name="return-value"></a>Valeur de retour  

 Dernier code d’erreur COM défini par l’une des fonctions Strong Name.  
  
## <a name="remarks"></a>Remarques  

 La plupart des méthodes Strong Name renvoient une simple `true` ou une `false` indication de la réussite de l’opération. Utilisez la `StrongNameErrorInfo` fonction pour récupérer un HRESULT qui spécifie la dernière erreur générée par les fonctions Strong Name.  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** StrongName. h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MsCorEE.dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
