---
title: La référence d'assembly Friend <reference> n'est pas valide
ms.date: 07/20/2015
f1_keywords:
- vbc31535
- bc31535
helpviewer_keywords:
- BC31535
ms.assetid: 6540c1d0-bb19-4051-a579-2e4f9094585e
ms.openlocfilehash: a42dd99ffaa06dce4823ce5d022fac02ae99c6bd
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92160709"
---
# <a name="bc31535-friend-assembly-reference-reference-is-invalid"></a>BC31535 : la référence d’assembly friend \<reference> n’est pas valide

La référence d’assembly friend \<reference> n’est pas valide. Les assemblys signés avec un nom fort doivent spécifier une clé publique dans leurs déclarations InternalsVisibleTo.

 Le nom d’assembly passé au <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> constructeur d’attribut identifie un assembly avec nom fort, mais il n’inclut pas d' `PublicKey` attribut.

 **ID d’erreur :** BC31535

## <a name="to-correct-this-error"></a>Pour corriger cette erreur

1. Déterminez la clé publique de l’assembly friend avec nom fort. Incluez la clé publique dans le nom de l’assembly passé au <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> constructeur d’attribut à l’aide de l' `PublicKey` attribut.

## <a name="see-also"></a>Voir aussi

- <xref:System.Reflection.AssemblyName>
- [Assemblys friend](../../../standard/assembly/friend.md)
