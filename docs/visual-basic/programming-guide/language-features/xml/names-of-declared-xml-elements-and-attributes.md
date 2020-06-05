---
title: Nom des attributs et des éléments XML déclarés
ms.date: 07/20/2015
helpviewer_keywords:
- declarations [XML in Visual Basic]
- element names [XML in Visual Basic]
- names in XML literals [Visual Basic]
- attribute names [XML in Visual Basic]
- XML literals [Visual Basic], element names
ms.assetid: cc110118-b6cf-4ff9-a4e4-6233c90c9fbf
ms.openlocfilehash: 043243eeee7c24d8c63105047fa3e7e0ed58c7b0
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84374666"
---
# <a name="names-of-declared-xml-elements-and-attributes-visual-basic"></a>Nom des attributs et des éléments XML déclarés (Visual Basic)
Cette rubrique fournit des instructions Visual Basic pour nommer des éléments et des attributs XML dans des littéraux XML.  Dans un littéral XML, vous pouvez spécifier un nom local ou un nom qualifié. Un nom qualifié se compose d’un préfixe d’espace de noms XML, d’un signe deux-points et d’un nom local. Pour plus d’informations sur les préfixes d’espaces de noms XML, consultez [littéral d’élément XML](../../../language-reference/xml-literals/xml-element-literal.md).  
  
## <a name="rules"></a>Règles  
 Un nom local d’un élément ou d’un attribut dans Visual Basic doit respecter les règles suivantes.  
  
- Il peut commencer par un espace de noms. Elle doit commencer par un caractère alphabétique ou un trait de soulignement ( `_` ).  
  
- Il doit contenir uniquement des caractères alphabétiques, des chiffres décimaux, des traits de soulignement, des points (.) et des traits d’Union (-).  
  
- Sa longueur ne doit pas dépasser 1 024 caractères.  
  
- Les signes deux-points qui apparaissent dans les noms indiquent la délimitation de l’espace de noms. Par conséquent, vous ne pouvez utiliser les deux-points que pour spécifier un espace de noms XML pour un nom particulier.  
  
 En outre, vous devez respecter les indications ci-dessous.  
  
- La spécification XML 1,0 réserve tous les noms commençant par la chaîne « XML », quelle que soit la variation de la casse. Par conséquent, n’utilisez pas ces noms pour les noms d’élément et d’attribut.  
  
### <a name="name-length-guidelines"></a>Instructions relatives à la longueur de nom  
 En pratique, un nom doit être aussi bref que possible tout en identifiant clairement la nature de l’élément. Cela permet d’améliorer la lisibilité de votre code et de réduire la longueur de ligne et la taille du fichier source.  
  
 Toutefois, votre nom ne doit pas être tellement bref qu’il ne décrit pas correctement l’élément ou la manière dont votre code l’utilise. Cela est important pour la lisibilité de votre code. Si quelqu’un d’autre essaie de le comprendre ou si vous en examinez un certain temps après l’avoir écrit, les noms d’éléments appropriés peuvent vous faire gagner du temps.  
  
## <a name="case-sensitivity-in-names"></a>Respect de la casse dans les noms  
 Les noms d’éléments XML respectent la casse. Cela signifie que lorsque le compilateur Visual Basic compare deux noms qui diffèrent uniquement par la casse alphabétique, il les interprète comme des noms différents. Par exemple, il interprète `ABC` et `abc` comme faisant référence à des éléments distincts.  
  
## <a name="xml-namespaces"></a>Espaces de noms XML  
 Lorsque vous créez un littéral d’élément XML, vous pouvez spécifier le préfixe d’espace de noms XML pour le nom d’élément. Pour plus d’informations, consultez [littéral d’élément XML](../../../language-reference/xml-literals/xml-element-literal.md).  
  
## <a name="see-also"></a>Voir aussi

- [Création de code XML dans Visual Basic](creating-xml.md)
- [Littéral d’élément XML](../../../language-reference/xml-literals/xml-element-literal.md)
