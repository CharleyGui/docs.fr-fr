---
title: Les littéraux XML et les propriétés XML ne sont pas pris en charge dans du code incorporé au sein d'ASP.NET
ms.date: 07/20/2015
f1_keywords:
- vbc31200
- bc31200
helpviewer_keywords:
- BC31200
ms.assetid: 053e8cba-8584-45cc-9fa0-43d122779772
ms.openlocfilehash: d96386f8495685391203826fea85efba47c44951
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92163257"
---
# <a name="bc31200-xml-literals-and-xml-properties-are-not-supported-in-embedded-code-within-aspnet"></a>BC31200 : les littéraux XML et les propriétés XML ne sont pas pris en charge dans le code incorporé dans ASP.NET

Les littéraux XML et les propriétés XML ne sont pas pris en charge dans le code incorporé dans ASP.NET. Pour utiliser les fonctionnalités XML, déplacez le code vers le code-behind.

 Un littéral XML ou une propriété d’axe XML est défini dans du code incorporé ( `<%= =>` ) dans un fichier ASP.net.

 **ID d’erreur :** BC31200

## <a name="to-correct-this-error"></a>Pour corriger cette erreur

- Déplacez le code qui comprend le littéral XML ou la propriété d’axe XML vers un fichier code-behind ASP.NET.

## <a name="see-also"></a>Voir aussi

- [Littéraux XML](../xml-literals/index.md)
- [Propriétés d'axe XML](../xml-axis/index.md)
- [XML](../../programming-guide/language-features/xml/index.md)
