---
title: Fonction Activate-référence des API non managées WPF
titleSuffix: ''
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- Activate
api_location:
- PresentationHost_v0400.dll
ms.assetid: 1400329c-b598-465f-80f2-e3dabf044811
ms.openlocfilehash: 9c0a235e8b94294ab82da88e43f7446c29739c12
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76734515"
---
# <a name="activate-function-wpf-unmanaged-api-reference"></a>Activate, fonction (référence des API non managées WPF)

Cette API prend en charge l’infrastructure Windows Presentation Foundation (WPF) et n’est pas destinée à être utilisée directement à partir de votre code.

Utilisé par l’infrastructure Windows Presentation Foundation (WPF) pour la gestion de Windows.

## <a name="syntax"></a>Syntaxe

```cpp
void Activate(
    const ActivateParameters* pParameters,
    __deref_out_ecount(1) LPUNKNOWN* ppInner,
    );
```

## <a name="parameters"></a>Parameters

`pParameters`\
Pointeur vers les paramètres d’activation de la fenêtre.

`ppInner`\
Pointeur vers l’adresse d’une mémoire tampon à un seul élément qui contient un pointeur vers un objet <xref:Microsoft.VisualStudio.OLE.Interop.IOleDocument>.

## <a name="requirements"></a>Configuration requise pour

**Plateformes :** Consultez [.NET Framework Configuration système requise](../../get-started/system-requirements.md).

**DLL**

Dans les .NET Framework 3,0 et 3,5 : PresentationHostDLL. dll

Dans le .NET Framework 4 et versions ultérieures : PresentationHost_v0400. dll

**Version de .NET Framework :** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]

## <a name="see-also"></a>Voir aussi

- [Référence des API non managées WPF](wpf-unmanaged-api-reference.md)
