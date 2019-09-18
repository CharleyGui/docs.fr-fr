---
title: IEnumRAWINPUTDEVIC:Clone
ms.date: 03/30/2017
helpviewer_keywords:
- Clone method [WPF]
ms.assetid: 2a6a1900-aa55-45fa-9382-241d569a2dc4
ms.openlocfilehash: cd634b4d4a88d83d425b787ed8493f9aa2504988
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053418"
---
# <a name="ienumrawinputdevicclone"></a>IEnumRAWINPUTDEVIC:Clone
Crée un autre énumérateur de périphériques d'entrée brute avec le même état que l'énumérateur actif pour itérer au sein de la même liste.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT Clone( [out] IEnumRAWINPUTDEVICE **ppenum);  
```  
  
## <a name="parameters"></a>Paramètres  
 `ppenum`  
  
 à Adresse de la variable de sortie qui reçoit le pointeur d’interface [IEnumRAWINPUTDEVICE](ienumrawinputdevice.md) . Si la méthode échoue, la valeur de cette variable de sortie n’est pas définie.  
  
## <a name="property-valuereturn-value"></a>Valeur de propriété/valeur de retour  
 HRESULT : Cette méthode prend en charge les valeurs de retour E_INVALIDARG, E_OUTOFMEMORY et E_UNEXPECTED standard.  
  
## <a name="remarks"></a>Notes  
 Cette méthode permet d’enregistrer un point dans la séquence d’énumération afin de retourner ultérieurement à ce point. L’appelant doit libérer ce nouvel énumérateur séparément du premier énumérateur.
