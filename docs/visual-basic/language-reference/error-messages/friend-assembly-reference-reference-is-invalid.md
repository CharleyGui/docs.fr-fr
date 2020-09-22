---
title: La référence d'assembly Friend <reference> n'est pas valide
ms.date: 07/20/2015
f1_keywords:
- vbc31535
- bc31535
helpviewer_keywords:
- BC31535
ms.assetid: 6540c1d0-bb19-4051-a579-2e4f9094585e
ms.openlocfilehash: 72c030d18d5339908c5088e104f6a8ad3e76943b
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90874096"
---
# <a name="friend-assembly-reference-reference-is-invalid"></a>La référence d'assembly Friend \<reference> n'est pas valide

La référence d’assembly friend \<reference> n’est pas valide. Les assemblys signés avec un nom fort doivent spécifier une clé publique dans leurs déclarations InternalsVisibleTo.  
  
 Le nom d’assembly passé au <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> constructeur d’attribut identifie un assembly avec nom fort, mais il n’inclut pas d' `PublicKey` attribut.  
  
 **ID d’erreur :** BC31535  
  
## <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
1. Déterminez la clé publique de l’assembly friend avec nom fort. Incluez la clé publique dans le nom de l’assembly passé au <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> constructeur d’attribut à l’aide de l' `PublicKey` attribut.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Reflection.AssemblyName>
- [Assemblys friend](../../../standard/assembly/friend.md)
