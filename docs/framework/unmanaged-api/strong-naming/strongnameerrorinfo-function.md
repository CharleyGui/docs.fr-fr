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
ms.openlocfilehash: 021fa1668247bc59a4412d2b5f4bac3f5ee8cc6b
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70799113"
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
  
## <a name="remarks"></a>Notes  
 La plupart des méthodes Strong Name renvoient une `true` simple `false` ou une indication de la réussite de l’opération. Utilisez la `StrongNameErrorInfo` fonction pour récupérer un HRESULT qui spécifie la dernière erreur générée par les fonctions Strong Name.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** StrongName.h  
  
 **Bibliothèque** Inclus en tant que ressource dans MsCorEE. dll  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
