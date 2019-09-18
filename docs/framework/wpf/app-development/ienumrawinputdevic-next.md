---
title: IEnumRAWINPUTDEVIC:Next
ms.date: 03/30/2017
helpviewer_keywords:
- Next method [WPF]
ms.assetid: 3698b44d-510e-4d18-b32b-85f17188ee26
ms.openlocfilehash: c7450a9ababa9cf3cb02d572f5ed84f0791d74e4
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053397"
---
# <a name="ienumrawinputdevicnext"></a>IEnumRAWINPUTDEVIC:Next
`celt` Énumère les structures [RAWINPUTDEVICE](/windows/desktop/api/winuser/ns-winuser-rawinputdevice) suivantes dans la liste de l’énumérateur, en les retournant en `rgelt` même temps que le nombre réel d’éléments énumérés dans. `pceltFetched`  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT Next(  
      [in] ULONG celt,  
      [out, size_is(celt), length_is(*pceltFetched)] RAWINPUTDEVICE *rgelt,  
      [out] ULONG *pceltFetched);  
```  
  
## <a name="parameters"></a>Paramètres  
 `celt`  
  
 dans Nombre de structures [RAWINPUTDEVICE](/windows/desktop/api/winuser/ns-winuser-rawinputdevice) retournées dans `rgelt`.  
  
 `rgelt`  
  
 [out] Tableau de taille celt (ou supérieure) destiné à recevoir les structures RAWINPUTDEVICE énumérées.  
  
 `pceltFetched`  
  
 [out] Pointeur vers le nombre d'éléments réellement fournis dans `rgelt`. L'appelant peut passer `NULL` si `rgelt` a la valeur un.  
  
## <a name="property-valuereturn-value"></a>Valeur de propriété/valeur de retour  
 HRESULT : S_OK si le nombre d’éléments fourni est `celt`; S_FALSE dans le cas contraire.
