---
title: LoadDeHistory Function - WPF non gestiond API référence
titleSuffix: ''
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- LoadFromHistory
api_location:
- PresentationHost_v0400.dll
ms.assetid: d037c062-a911-4949-b251-ccd3e48b1d17
ms.openlocfilehash: be9b8658614e678b4370044a753554859d230fed
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79141573"
---
# <a name="loadfromhistory-function-wpf-unmanaged-api-reference"></a>LoadDeHistory Function (WPF Unmanaged API Reference)
Cette API prend en charge l’infrastructure de la Windows Presentation Foundation (WPF) et n’est pas destinée à être utilisée directement à partir de votre code.  
  
 Utilisé par l’infrastructure de la Windows Presentation Foundation (WPF) pour la gestion des fenêtres.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT LoadFromHistory_export(  
        IStream* pHistoryStream,
        IBindCtx* pBindCtx  
)  
```  
  
## <a name="parameters"></a>Paramètres  
 pHistoryStream (en anglais seulement)  
 Un pointeur à un flux d’informations d’histoire.  
  
 pBindCtx (en)  
 Un pointeur à un contexte de liaison.  
  
## <a name="requirements"></a>Spécifications  
 **Plates-formes:** Voir [.NET Framework System Requirements](../../get-started/system-requirements.md).  
  
 **DLL:**  
  
 Dans le cadre .NET 3.0 et 3.5: PresentationHostDLL.dll  
  
 Dans le cadre .NET 4 et plus tard: PresentationHost_v0400.dll  
  
 **Version cadre .NET:**[!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Informations de référence sur les API non managées WPF](wpf-unmanaged-api-reference.md)
