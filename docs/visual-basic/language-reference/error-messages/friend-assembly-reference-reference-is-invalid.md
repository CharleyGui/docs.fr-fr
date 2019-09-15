---
title: La référence d'assembly Friend <reference> n'est pas valide
ms.date: 07/20/2015
f1_keywords:
- vbc31535
- bc31535
helpviewer_keywords:
- BC31535
ms.assetid: 6540c1d0-bb19-4051-a579-2e4f9094585e
ms.openlocfilehash: 6eb46c6479adc69eaf65b34c69aa69977b4d62ef
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/13/2019
ms.locfileid: "70972394"
---
# <a name="friend-assembly-reference-reference-is-invalid"></a>Le > de \<référence de l’assembly friend n’est pas valide
Le > de \<référence d’assembly friend n’est pas valide. Les assemblys signés avec un nom fort doivent spécifier une clé publique dans leurs déclarations InternalsVisibleTo.  
  
 Le nom d’assembly passé <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> au constructeur d’attribut identifie un assembly avec nom fort, mais il n' `PublicKey` inclut pas d’attribut.  
  
 **ID d’erreur :** BC31535  
  
## <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
1. Déterminez la clé publique de l’assembly friend avec nom fort. Incluez la clé publique dans le nom de l’assembly passé <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> au constructeur d’attribut à `PublicKey` l’aide de l’attribut.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Reflection.AssemblyName>
- [Assemblys friend](../../../standard/assembly/friend.md)
