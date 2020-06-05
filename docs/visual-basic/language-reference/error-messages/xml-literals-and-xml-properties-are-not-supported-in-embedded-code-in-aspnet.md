---
title: Les littéraux XML et les propriétés XML ne sont pas pris en charge dans du code incorporé au sein d'ASP.NET
ms.date: 07/20/2015
f1_keywords:
- vbc31200
- bc31200
helpviewer_keywords:
- BC31200
ms.assetid: 053e8cba-8584-45cc-9fa0-43d122779772
ms.openlocfilehash: bda92b4244631f66142499a94be562854b35437e
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84406467"
---
# <a name="xml-literals-and-xml-properties-are-not-supported-in-embedded-code-within-aspnet"></a>Les littéraux XML et les propriétés XML ne sont pas pris en charge dans du code incorporé au sein d'ASP.NET
Les littéraux XML et les propriétés XML ne sont pas pris en charge dans le code incorporé dans ASP.NET. Pour utiliser les fonctionnalités XML, déplacez le code vers le code-behind.  
  
 Un littéral XML ou une propriété d’axe XML est défini dans du code incorporé ( `<%= =>` ) dans un fichier ASP.net.  
  
 **ID d’erreur :** BC31200  
  
## <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
- Déplacez le code qui comprend le littéral XML ou la propriété d’axe XML vers un fichier code-behind ASP.NET.  
  
## <a name="see-also"></a>Voir aussi

- [Littéraux XML](../xml-literals/index.md)
- [Propriétés d'axe XML](../xml-axis/index.md)
- [XML](../../programming-guide/language-features/xml/index.md)
