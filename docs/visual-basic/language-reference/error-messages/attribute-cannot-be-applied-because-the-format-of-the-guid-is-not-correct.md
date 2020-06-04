---
title: "'<attribute>' ne peut pas être appliqué, car le format du GUID '<number>' n'est pas correct"
ms.date: 07/20/2015
f1_keywords:
- vbc32500
- bc32500
helpviewer_keywords:
- BC32500
ms.assetid: 6fa34c55-368e-4d7d-b488-07a3fffe045f
ms.openlocfilehash: 554c38c8f44999feba4cfa04d58ce2f07e955eb1
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409918"
---
# <a name="attribute-cannot-be-applied-because-the-format-of-the-guid-number-is-not-correct"></a>'\<attribute>' ne peut pas être appliqué, car le format du GUID '\<number>' n'est pas correct

Un `COMClassAttribute` bloc d’attributs spécifie un identificateur global unique (Guid) qui n’est pas conforme au format approprié pour un GUID. `COMClassAttribute`utilise des GUID pour identifier de manière unique la classe, l’interface et l’événement de création.  
  
 Un GUID se compose de 16 octets, dont les huit premiers sont numériques et les huit derniers sont binaires. Elle est générée par des utilitaires Microsoft tels que uuidgen. exe et est garantie comme étant unique dans l’espace et dans le temps.  
  
 **ID d’erreur :** BC32500  
  
## <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
1. Déterminez le GUID ou les GUID appropriés nécessaires pour identifier l’objet COM.  
  
2. Vérifiez que les chaînes de GUID présentées au bloc d’attributs `COMClassAttribute` sont copiées correctement.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Guid>
- [Vue d’ensemble des attributs](../../programming-guide/concepts/attributes/index.md)
