---
title: IEnumRAWINPUTDEVIC:Skip
ms.date: 03/30/2017
helpviewer_keywords:
- Skip method [WPF]
ms.assetid: c967b0f8-1c6a-459c-8c16-d4f08918ab65
ms.openlocfilehash: a74f71345a22f6d766c2d5966ca5d2cb33ab756e
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053375"
---
# <a name="ienumrawinputdevicskip"></a>IEnumRAWINPUTDEVIC:Skip
Indique à l’énumérateur d’ignorer les éléments `celt` suivants dans l’énumération afin que l’appel suivant à [IEnumRAWINPUTDEVIC : Next](ienumrawinputdevic-next.md) ne retourne pas ces éléments.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT Skip( [in] ULONG celt);  
```  
  
## <a name="parameters"></a>Paramètres  
 `celt`  
  
 dans Nombre d’éléments à ignorer.  
  
## <a name="property-valuereturn-value"></a>Valeur de propriété/valeur de retour  
 HRESULT : S_OK si le nombre d’éléments fourni est `celt`; S_FALSE dans le cas contraire.
