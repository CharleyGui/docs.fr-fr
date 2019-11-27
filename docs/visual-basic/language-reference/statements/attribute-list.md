---
title: Liste d'attributs
ms.date: 07/20/2015
helpviewer_keywords:
- attribute list
- attributes [Visual Basic], applying
ms.assetid: 5880073a-68a4-4b6b-8a07-ace32959a4e2
ms.openlocfilehash: f9332f52622551bb6b944242f71bd80f439982e9
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74354061"
---
# <a name="attribute-list-visual-basic"></a>Liste d'attributs (Visual Basic)
Spécifie les attributs à appliquer à un élément de programmation déclaré. Les attributs multiples sont séparés par des virgules. Voici la syntaxe d’un attribut.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
[ attributemodifier ] attributename [ ( attributearguments | attributeinitializer ) ]  
```  
  
## <a name="parts"></a>Composants  
|||
|---|---|
|`attributemodifier`|Obligatoire pour les attributs appliqués au début d’un fichier source. Il peut s’agir d’un [assembly](../../../visual-basic/language-reference/modifiers/assembly.md) ou d’un [module](../../../visual-basic/language-reference/modifiers/module-keyword.md).|
|`attributename`| Requis. Nom de l'attribut.|
|`attributearguments`|Ce paramètre est facultatif. Liste des arguments positionnels pour cet attribut. Les arguments multiples sont séparés par des virgules.|
|`attributeinitializer`|Ce paramètre est facultatif. Liste d’initialiseurs de variable ou de propriété pour cet attribut. Plusieurs initialiseurs sont séparés par des virgules.|
  
## <a name="remarks"></a>Notes  
 Vous pouvez appliquer un ou plusieurs attributs à presque n’importe quel élément de programmation (types, procédures, propriétés, etc.). Les attributs apparaissent dans les métadonnées de votre assembly. ils peuvent vous aider à annoter votre code ou à spécifier comment utiliser un élément de programmation particulier. Vous pouvez appliquer des attributs définis par Visual Basic et le .NET Framework, et vous pouvez définir vos propres attributs.  

 Pour plus d’informations sur l’utilisation des attributs, consultez [vue d’ensemble des attributs](../../../visual-basic/programming-guide/concepts/attributes/index.md). Pour plus d’informations sur les noms d’attributs, consultez [noms d’éléments déclarés](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).  
  
## <a name="rules"></a>Règles  
  
- **Importation.** Vous pouvez appliquer des attributs aux éléments de programmation les plus déclarés. Pour appliquer un ou plusieurs attributs, vous placez un *bloc d’attributs* au début de la déclaration de l’élément. Chaque entrée de la liste d’attributs spécifie un attribut que vous souhaitez appliquer, ainsi que le modificateur et les arguments que vous utilisez pour cet appel de l’attribut.  
  
- **Chevrons.** Si vous fournissez une liste d’attributs, vous devez la placer entre crochets pointus («`<`» et «`>`»).  
  
- **Partie de la déclaration.** L’attribut doit faire partie de la déclaration de l’élément, et non d’une instruction distincte. Vous pouvez utiliser la séquence de continuation de ligne (« `_`») pour étendre l’instruction de déclaration sur plusieurs lignes de code source.  
  
- **Modificateurs.** Un modificateur d’attribut (`Assembly` ou `Module`) est requis sur chaque attribut appliqué à un élément de programmation au début d’un fichier source. Les modificateurs d’attribut ne sont pas autorisés sur les attributs appliqués aux éléments qui ne sont pas au début d’un fichier source.  
  
- **Arguments.** Tous les arguments positionnels d’un attribut doivent précéder tout initialiseur de variable ou de propriété.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant applique l’attribut <xref:System.Runtime.InteropServices.DllImportAttribute> à une définition squelette d’une procédure `Function`.  
  
 [!code-vb[VbVbalrStatements#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#1)]  
  
 <xref:System.Runtime.InteropServices.DllImportAttribute> indique que la procédure avec attributs représente un point d’entrée dans une bibliothèque de liens dynamiques (DLL) non managée. L’attribut fournit le nom de la DLL comme argument positionnel et les autres informations sous forme d’initialiseurs de variables.  
  
## <a name="see-also"></a>Voir aussi

- [Assembly](../../../visual-basic/language-reference/modifiers/assembly.md)
- [\<mot clé> du module](../../../visual-basic/language-reference/modifiers/module-keyword.md)
- [Vue d’ensemble des attributs](../../../visual-basic/programming-guide/concepts/attributes/index.md)
- [Guide pratique : diviser et combiner des instructions dans le code](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)
