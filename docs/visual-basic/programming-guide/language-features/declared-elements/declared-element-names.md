---
title: Noms d'éléments déclarés (Visual Basic)
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
ms.openlocfilehash: 7642aea72ddaa3789dba3b2328f271afcb92a16a
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64610551"
---
# <a name="declared-element-names-visual-basic"></a>Noms d'éléments déclarés (Visual Basic)
Chaque élément déclaré a un nom, également appelé un *identificateur*, qui est utilisé par le code pour faire référence à ce dernier.  
  
## <a name="rules"></a>Règles  
 Un nom d’élément dans Visual Basic doit respecter les règles suivantes :  
  
- Il doit commencer par un caractère alphabétique ou un trait de soulignement (`_`).  
  
- Il doit uniquement contenir des caractères alphabétiques, des chiffres décimaux et des traits de soulignement.  
  
- Il doit contenir au moins un caractère alphabétique ou un chiffre décimal s’il commence par un trait de soulignement.  
  
- Il ne doit pas être plus de 1023 caractères.  
  
 La longueur maximale de 1023 caractères s’applique également à la chaîne entière d’un nom qualifié complet, tel que `outerNamespace.middleNamespace.innerNamespace.thisClass.thisElement`.  
  
 L’exemple suivant montre certains noms d’élément valide.  
  
 `aB123__45`  
  
 `_567`  
  
 L’exemple suivant montre certains noms d’élément non valide. Le premier contient uniquement un trait de soulignement, le second commence par un chiffre décimal et le troisième contient un caractère non valide ($).  
  
 `' Three INVALID element names`  
  
 `_`  
  
 `12ABC`  
  
 `xyz$wv`  
  
> [!CAUTION]
>  Les noms d’élément commençant par un trait de soulignement (`_`) ne font pas partie de la [indépendance du langage et composants indépendants du langage](../../../../standard/language-independence-and-language-independent-components.md) (CLS), le code conforme CLS ne peut pas utiliser un composant qui définit les noms de ce type. Toutefois, un trait de soulignement dans n’importe quelle autre position dans un nom d’élément est conforme CLS.  
  
### <a name="name-length-guidelines"></a>Instructions de longueur de nom  
 Dans la pratique, votre nom doit être aussi courte que possible tout en identifiant clairement la nature de l’élément. Cela améliore la lisibilité de votre code et réduit la taille de ligne de longueur et le fichier source.  
  
 En revanche, votre nom ne doit pas être si court que ne pas correctement décrit ce que l’élément représente et comment votre code l’utilise. Ceci est important pour la lisibilité de votre code. Si quelqu'un d’autre tente de le comprendre, ou si vous avez vous-même l’observer beaucoup de temps après que l’avoir écrit, noms d’éléments appropriés peuvent enregistrer un temps considérable.  
  
## <a name="escaped-names"></a>Noms d’échappement  
 En règle générale, un nom d’élément doit correspond à aucun des mots clés réservés par Visual Basic, tel que `Case` ou `Friend`. Toutefois, vous pouvez définir un *nom échappement*, qui est placé entre crochets (`[ ]`). Un nom d’échappement peut correspondre à n’importe quel mot clé Visual Basic, dans la mesure où les crochets supprimer toute ambiguïté. Vous utilisez également les crochets lorsque vous faites référence au nom ultérieurement dans votre code.  
  
 En règle générale, vous devez utiliser des noms échappés uniquement lorsque :  
  
- Votre code a migré à partir d’une version antérieure de Visual Basic qui n’a pas réservé le mot clé utilisé en tant que nom ; ou  
  
- Vous travaillez avec le code écrit dans un autre langage dans lequel le mot clé donné n’est pas réservé.  
  
 Sinon, vous devez envisager de renommer l’élément si son nom est en conflit avec un mot clé. L’environnement de développement intégré (IDE) fournit un moyen simple de le faire. Pour plus d’informations, consultez [Refactoring](/visualstudio/vb-ide/refactoring-vb).  
  
## <a name="case-sensitivity-in-names"></a>Respecte la casse dans les noms  
 Noms d’éléments dans Visual Basic respectent la casse. Cela signifie que lorsque le compilateur compare deux noms qui diffèrent uniquement par la casse des lettres, il les interprète comme le même nom. Par exemple, il considère que `ABC` et `abc` font référence au même élément déclaré.  
  
 Toutefois, le common language runtime (CLR) utilise la liaison de la casse. Ainsi, quand vous générez un assembly ou une DLL et que vous le mettez à disposition d’autres assemblys, la casse de vos noms est respectée. Par exemple, si vous définissez une classe avec un élément nommé `ABC`et que d’autres assemblys utilisent votre classe par le biais du Common Language Runtime, ils doivent faire référence à l’élément en tant que `ABC`. Si vous recompilez votre classe par la suite et modifier le nom de l’élément à `abc`, les autres assemblys utilisent votre classe peuvent ne plus accéder à cet élément. Ainsi, quand vous publiez une version mise à jour d’un assembly, vous ne devez pas modifier la casse des éléments publics.  
  
## <a name="names-and-locales"></a>Noms et paramètres régionaux  
 Comparaison des noms est indépendante des paramètres régionaux. Si deux noms correspondent dans des paramètres régionaux, ils sont garanties à faire correspondre dans tous les paramètres régionaux.  
  
## <a name="see-also"></a>Voir aussi

- [Éléments déclarés](../../../../visual-basic/programming-guide/language-features/declared-elements/index.md)
- [Caractéristiques d’éléments déclarés](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md)
- [Références aux éléments déclarés](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
- [Instructions](../../../../visual-basic/language-reference/statements/index.md)
