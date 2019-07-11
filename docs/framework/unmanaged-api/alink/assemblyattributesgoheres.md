---
title: AssemblyAttributesGoHereS
ms.date: 03/30/2017
api_name:
- System.Runtime.CompilerServices.AssemblyAttributesGoHereS
api_location:
- mscorlib.dll
api_type:
- Assembly
f1_keywords:
- AssemblyAttributesGoHereS
helpviewer_keywords:
- AssemblyAttributesGoHereS type
- Alink API, AssemblyAttributesGoHereS type
ms.assetid: 4e817f35-a2bc-4403-9e6f-f731e6b9fe23
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 135938c4ed91423145ca46b743620f4236f7f818
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67742261"
---
# <a name="assemblyattributesgoheres"></a>AssemblyAttributesGoHereS

Utilisé par ALink en tant qu'espace réservé pour stocker des informations sur les attributs personnalisés.

## <a name="syntax"></a>Syntaxe

```csharp
internal sealed class AssemblyAttributesGoHereS
```

## <a name="remarks"></a>Notes

Les références à ce type peuvent être incorporées dans les netmodules dont les sources contiennent des attributs personnalisés d'assembly. Quand vous générez un manifeste d'assembly à partir d'un ou plusieurs netmodules qui contiennent des références à ces types, ALink utilise les informations associées à ces références pour émettre des attributs personnalisés réels. Par conséquent, ce type n'est jamais instancié et ses références sont utilisées uniquement dans le cadre du processus de génération et n'ont aucune utilité dans l'assembly final.

Les références à ce type indiquent des attributs personnalisés qui sont liés à la sécurité et ne peuvent pas être utilisés plusieurs fois.

Ces types sont marqués « internes » dans le .NET Framework et se trouvent dans le <xref:System.Runtime.CompilerServices> espace de noms.

## <a name="requirements"></a>Configuration requise

mscorlib.dll

## <a name="see-also"></a>Voir aussi

- [AssemblyAttributesGoHere](assemblyattributesgohere.md)
- [AssemblyAttributesGoHereM](assemblyattributesgoherem.md)
- [AssemblyAttributesGoHereSM](assemblyattributesgoheresm.md)
