---
title: Méthode MemoryStream. InternalGetOriginAndLength (System.IO)
author: mairaw
ms.author: mairaw
ms.date: 11/19/2019
topic_type:
- apiref
api_name:
- System.IO.MemoryStream.InternalGetOriginAndLength
api_location:
- mscorlib.dll
api_type:
- Assembly
ms.openlocfilehash: d2bfa087fe2fb247f963cfa687c27056363d5696
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74284030"
---
# <a name="memorystreaminternalgetoriginandlength-method"></a>MemoryStream. InternalGetOriginAndLength, méthode

Obtient les valeurs internes de l’origine et de la longueur du flux de mémoire.

```csharp
internal void InternalGetOriginAndLength(out int origin, out int length)
```

## <a name="parameters"></a>Paramètres

- `origin` <xref:System.Int32>\
  Lorsque cette méthode est retournée, offset du tableau d’octets spécifié lors de la création d’un objet <xref:System.IO.MemoryStream>. Contient 0 si le tableau d’octets a été créé par <xref:System.IO.MemoryStream>.

- `length` <xref:System.Int32>\
  Lorsque cette méthode est retournée, nombre d’octets dans le flux de mémoire.

## <a name="remarks"></a>Notes

> [!WARNING]
> La méthode `MemoryStream.InternalGetOriginAndLength` est interne et n’est pas destinée à être utilisée directement dans votre code.
>
> Microsoft ne prend pas en charge l’utilisation de cette méthode dans une application de production en l’absence de toute circonstance.

## <a name="requirements"></a>Conditions requises

**Espace de noms :** <xref:System.IO>

**Assembly :** mscorlib. dll (dans mscorlib. dll)

**Versions de .NET Framework :** Disponible depuis 2,0.
