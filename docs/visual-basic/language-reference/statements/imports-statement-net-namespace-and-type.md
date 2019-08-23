---
title: Instruction Imports-espace de noms et type .NET (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Imports
- imports
helpviewer_keywords:
- declared element names [Visual Basic], qualification
- imports [Visual Basic]
- Imports statement [Visual Basic]
- aliases [Visual Basic], Imports statement
- container elements [Visual Basic]
- namespaces [Visual Basic], importing
- Imports statement [Visual Basic], syntax
- import aliases [Visual Basic]
- aliases [Visual Basic], import
- declared elements [Visual Basic], container elements
ms.assetid: 7062f8aa-d890-4232-9eed-92836e13fb6e
ms.openlocfilehash: a0b7a6a5fd16dc0daa620e6b490ddfdeb0e7c80e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69912385"
---
# <a name="imports-statement-net-namespace-and-type"></a>Imports, instruction (espace de noms et type .NET)
Permet de référencer des noms de types sans qualification d’espace de noms.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
Imports [ aliasname = ] namespace  
-or-  
Imports [ aliasname = ] namespace.element  
```  
  
## <a name="parts"></a>Composants  
  
|Terme|Définition|  
|---|---|  
|`aliasname`|facultatif. *Alias d’importation* ou nom auquel le code peut faire référence `namespace` à la place de la chaîne de qualification complète. Consultez [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).|  
|`namespace`|Requis. Nom qualifié complet de l’espace de noms importé. Peut être une chaîne d’espaces de noms imbriqués à n’importe quel niveau.|  
|`element`|facultatif. Nom d’un élément de programmation déclaré dans l’espace de noms. Peut être n’importe quel élément conteneur.|  
  
## <a name="remarks"></a>Notes  
 L' `Imports` instruction permet de référencer directement les types contenus dans un espace de noms donné.  
  
 Vous pouvez fournir un nom d’espace de noms unique ou une chaîne d’espaces de noms imbriqués. Chaque espace de noms imbriqué est séparé de l’espace de noms de niveau supérieur suivant`.`par un point (), comme l’illustre l’exemple suivant.  
  
 `Imports System.Collections.Generic`  
  
 Chaque fichier source peut contenir un nombre quelconque `Imports` d’instructions. Celles-ci doivent suivre les déclarations d’option, `Option Strict` telles que l’instruction, et elles doivent précéder toutes les déclarations `Module` d' `Class` éléments de programmation, telles que les instructions ou.  
  
 Vous pouvez utiliser `Imports` uniquement au niveau du fichier. Cela signifie que le contexte de déclaration pour l’importation doit être un fichier source et ne peut pas être un espace de noms, une classe, une structure, un module, une interface, une procédure ou un bloc.  
  
 Notez que l' `Imports` instruction ne rend pas les éléments d’autres projets et assemblys disponibles pour votre projet. L’importation ne remplace pas la définition d’une référence. Il n’est plus nécessaire de qualifier des noms déjà disponibles pour votre projet. Pour plus d’informations, consultez «importation d’éléments contenants» dans les [références aux éléments déclarés](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).  
  
> [!NOTE]
> Vous pouvez définir des `Imports` instructions implicites à l’aide de la [page références, concepteur de projets (Visual Basic)](/visualstudio/ide/reference/references-page-project-designer-visual-basic). Pour plus d'informations, voir [Procédure : Ajoutez ou supprimez des espaces de noms importés (Visual Basic)](/visualstudio/ide/how-to-add-or-remove-imported-namespaces-visual-basic).  
  
## <a name="import-aliases"></a>Alias d’importation  
 Un *alias d’importation* définit l’alias pour un espace de noms ou un type. Les alias d’importation sont utiles quand vous devez utiliser des éléments portant le même nom et qui sont déclarés dans un ou plusieurs espaces de noms. Pour plus d’informations et pour obtenir un exemple, consultez «qualifier un nom d’élément» dans les [références aux éléments déclarés](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).  
  
 Vous ne devez pas déclarer un membre au niveau du module avec le même `aliasname`nom que. Si c’est le cas, le compilateur `aliasname` Visual Basic utilise uniquement pour le membre déclaré et ne le reconnaît plus comme alias d’importation.  
  
 Bien que la syntaxe utilisée pour déclarer un alias d’importation soit similaire à celle utilisée pour l’importation d’un préfixe d’espace de noms XML, les résultats sont différents. Un alias d’importation peut être utilisé en tant qu’expression dans votre code, alors qu’un préfixe d’espace de noms XML ne peut être utilisé que dans des littéraux XML ou des propriétés d’axe XML en tant que préfixe d’un élément qualifié ou d’un nom d’attribut.  
  
### <a name="element-names"></a>Noms des éléments  
 Si vous fournissez `element`, il doit représenter un *élément conteneur*, autrement dit un élément de programmation qui peut contenir d’autres éléments. Les éléments de conteneur incluent des classes, des structures, des modules, des interfaces et des énumérations.  
  
 La portée des éléments rendus disponibles par une `Imports` instruction varie selon que vous spécifiez. `element` Si vous spécifiez `namespace`uniquement, tous les membres nommés de manière unique de cet espace de noms, et les membres des éléments de conteneur dans cet espace de noms, sont disponibles sans qualification. Si vous spécifiez `namespace` à `element`la fois et, seuls les membres de cet élément sont disponibles sans qualification.  
  
## <a name="example"></a>Exemples  
 L’exemple suivant retourne tous les dossiers dans le dossier C:\ dans le répertoire à <xref:System.IO.DirectoryInfo> l’aide de la classe.  
  
 Le code n’a `Imports` aucune instruction en haut du fichier. Par conséquent, `DirectoryInfo`les <xref:System.Text.StringBuilder>références, <xref:Microsoft.VisualBasic.ControlChars.CrLf> et sont toutes qualifiées complètes avec les espaces de noms.  
  
 [!code-vb[VbVbalrStatements#152](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class12.vb#152)]  
  
## <a name="example"></a>Exemples  
 L’exemple suivant comprend `Imports` des instructions pour les espaces de noms référencés. Par conséquent, il n’est pas nécessaire que les types soient entièrement qualifiés avec les espaces de noms.  
  
 [!code-vb[VbVbalrStatements#153](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class12.vb#153)]  
  
 [!code-vb[VbVbalrStatements#154](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class12.vb#154)]  
  
## <a name="example"></a>Exemple  
 L’exemple suivant comprend `Imports` des instructions qui créent des alias pour les espaces de noms référencés. Les types sont qualifiés avec les alias.  
  
 [!code-vb[VbVbalrStatements#155](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class12.vb#155)]  
  
 [!code-vb[VbVbalrStatements#156](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class12.vb#156)]  
  
## <a name="example"></a>Exemple  
 L’exemple suivant comprend `Imports` des instructions qui créent des alias pour les types référencés. Les alias sont utilisés pour spécifier les types.  
  
 [!code-vb[VbVbalrStatements#157](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class12.vb#157)]  
  
 [!code-vb[VbVbalrStatements#158](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class12.vb#158)]  
  
## <a name="see-also"></a>Voir aussi

- [Namespace (instruction)](../../../visual-basic/language-reference/statements/namespace-statement.md)
- [Espaces de noms dans Visual Basic](../../../visual-basic/programming-guide/program-structure/namespaces.md)
- [Références et l’instruction Imports](../../../visual-basic/programming-guide/program-structure/references-and-the-imports-statement.md)
- [Imports (instruction) (espace de noms XML)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md)
- [Références aux éléments déclarés](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
