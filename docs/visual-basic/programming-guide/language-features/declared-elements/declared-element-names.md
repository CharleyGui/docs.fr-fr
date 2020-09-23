---
title: Declared Element Names
ms.date: 07/20/2015
helpviewer_keywords:
- declared elements [Visual Basic], case sensitivity
- names [Visual Basic], Visual Basic rules
- naming conventions [Visual Basic]
- element names [Visual Basic]
- declared elements [Visual Basic], identifiers
- declarations [Visual Basic], elements
- declared elements [Visual Basic], valid names
- '[] escape characters [Visual Basic]'
- names [Visual Basic], elements
- declaration statements [Visual Basic], declared elements
- declaring elements [Visual Basic]
- identifiers [Visual Basic], declared elements
- case sensitivity, declared element names
- escape characters [Visual Basic]
- names [Visual Basic], declared elements
- declared elements [Visual Basic], about declared elements
- escaped names [Visual Basic]
- declared elements [Visual Basic], names
- names [Visual Basic], naming conventions
- identifiers [Visual Basic], elements
ms.assetid: 09d8843b-c0dc-4afe-9dab-87c439a69e66
ms.openlocfilehash: 327a18644c1dc1d8dae59016b8e30600357d2ca9
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91086177"
---
# <a name="declared-element-names-visual-basic"></a>Noms d'éléments déclarés (Visual Basic)

Chaque élément déclaré a un nom, également appelé *identificateur*, qui est utilisé par le code pour y faire référence.  
  
## <a name="rules"></a>Règles  

 Un nom d’élément dans Visual Basic doit respecter les règles suivantes :  
  
- Elle doit commencer par un caractère alphabétique ou un trait de soulignement ( `_` ).  
  
- Il doit contenir uniquement des caractères alphabétiques, des chiffres décimaux et des traits de soulignement.  
  
- Il doit contenir au moins un caractère alphabétique ou un chiffre décimal s’il commence par un trait de soulignement.  
  
- Sa longueur ne doit pas dépasser 1023 caractères.  
  
 La limite de longueur de 1023 caractères s’applique également à la chaîne entière d’un nom qualifié complet, par exemple `outerNamespace.middleNamespace.innerNamespace.thisClass.thisElement` .  
  
 L’exemple suivant montre des noms d’éléments valides.  
  
 `aB123__45`  
  
 `_567`  
  
 L’exemple suivant montre des noms d’éléments non valides. Le premier contient uniquement un trait de soulignement, le deuxième commence par un chiffre décimal et le troisième contient un caractère non valide ($).  
  
 `' Three INVALID element names`  
  
 `_`  
  
 `12ABC`  
  
 `xyz$wv`  
  
> [!CAUTION]
> Les noms d’éléments commençant par un trait de soulignement ( `_` ) ne font pas partie de l' [indépendance du langage et des composants indépendants du langage](../../../../standard/language-independence-and-language-independent-components.md) (CLS), de sorte que le code conforme CLS ne peut pas utiliser un composant qui définit ces noms. Toutefois, un trait de soulignement à toute autre position dans un nom d’élément est conforme CLS.  
  
### <a name="name-length-guidelines"></a>Instructions relatives à la longueur de nom  

 En pratique, votre nom doit être le plus bref possible tout en identifiant clairement la nature de l’élément. Cela permet d’améliorer la lisibilité de votre code et de réduire la longueur de ligne et la taille du fichier source.  
  
 En revanche, votre nom ne doit pas être tellement bref qu’il ne décrit pas correctement ce que l’élément représente et comment votre code l’utilise. Cela est important pour la lisibilité de votre code. Si quelqu’un d’autre essaie de le comprendre, ou si vous en examinez un peu plus longtemps après l’avoir écrit, les noms d’éléments appropriés peuvent gagner beaucoup de temps.  
  
## <a name="escaped-names"></a>Noms placés dans une séquence d’échappement  

 En règle générale, un nom d’élément ne doit pas correspondre à un mot clé réservé par Visual Basic, tel que `Case` ou `Friend` . Toutefois, vous pouvez définir un *nom*placé dans une séquence d’échappement, placé entre crochets ( `[ ]` ). Un nom échappé peut correspondre à n’importe quel mot clé Visual Basic, étant donné que les crochets suppriment toute ambiguïté. Vous utilisez également les crochets lorsque vous faites référence au nom plus loin dans votre code.  
  
 En général, vous devez utiliser des noms échappés uniquement lorsque :  
  
- Votre code a migré à partir d’une version antérieure de Visual Basic qui n’a pas réservé le mot clé utilisé comme nom ; ni  
  
- Vous travaillez avec du code écrit dans un autre langage dans lequel le mot clé donné n’est pas réservé.  
  
 Dans le cas contraire, vous devez envisager de renommer l’élément si son nom est en conflit avec un mot clé. L’environnement de développement intégré (IDE) offre un moyen simple de le faire. Pour plus d’informations, consultez [refactorisation](/visualstudio/ide/refactoring-in-visual-studio).  
  
## <a name="case-sensitivity-in-names"></a>Respect de la casse dans les noms  

 Les noms d’éléments dans Visual Basic ne respectent pas la casse. Cela signifie que lorsque le compilateur compare deux noms qui diffèrent uniquement par la casse, il les interprète comme étant le même nom. Par exemple, il considère que `ABC` et `abc` font référence au même élément déclaré.  
  
 Toutefois, le Common Language Runtime (CLR) utilise la liaison qui respecte la casse. Ainsi, quand vous générez un assembly ou une DLL et que vous le mettez à disposition d’autres assemblys, la casse de vos noms est respectée. Par exemple, si vous définissez une classe avec un élément nommé `ABC`et que d’autres assemblys utilisent votre classe par le biais du Common Language Runtime, ils doivent faire référence à l’élément en tant que `ABC`. Si, par la suite, vous recompilez votre classe et que vous changez le nom de l’élément en `abc` , les autres assemblys qui utilisent votre classe ne peuvent plus accéder à cet élément. Ainsi, quand vous publiez une version mise à jour d’un assembly, vous ne devez pas modifier la casse des éléments publics.  
  
## <a name="names-and-locales"></a>Noms et paramètres régionaux  

 Les comparaisons de noms sont indépendantes des paramètres régionaux. Si deux noms correspondent à un paramètre régional, il est garanti qu’ils correspondent dans tous les paramètres régionaux.  
  
## <a name="see-also"></a>Voir aussi

- [Éléments déclarés](index.md)
- [Caractéristiques des éléments déclarés](declared-element-characteristics.md)
- [References to Declared Elements](references-to-declared-elements.md)
- [Publication](../../../language-reference/statements/index.md)
