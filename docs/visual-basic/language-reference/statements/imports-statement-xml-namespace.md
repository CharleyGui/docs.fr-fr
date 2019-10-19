---
title: Instruction Imports-espace de noms XML (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.ImportsXmlns
helpviewer_keywords:
- XML namespace [Visual Basic], importing
- imports [Visual Basic]
- Imports statement [Visual Basic]
- namespaces [Visual Basic], importing
ms.assetid: 1f4d50a6-08c7-4c2e-8206-ccae35fcd1b4
ms.openlocfilehash: 0fca0caecfd69580510a539317856209108e5a32
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72581768"
---
# <a name="imports-statement-xml-namespace"></a>Imports, instruction (espace de noms XML)

Importe les préfixes d’espaces de noms XML à utiliser dans les littéraux XML et les propriétés d’axe XML.

## <a name="syntax"></a>Syntaxe

```vb
Imports <xmlns:xmlNamespacePrefix = "xmlNamespaceName">
```

## <a name="parts"></a>Composants

`xmlNamespacePrefix`  
Optionnel. Chaîne par laquelle les éléments et attributs XML peuvent faire référence à `xmlNamespaceName`. Si aucun `xmlNamespacePrefix` n’est fourni, l’espace de noms XML importé est l’espace de noms XML par défaut. Doit être un identificateur XML valide. Pour plus d’informations, consultez [noms des éléments et attributs XML déclarés](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).

`xmlNamespaceName`  
Requis. Chaîne identifiant l’espace de noms XML importé.

## <a name="remarks"></a>Notes

Vous pouvez utiliser l’instruction `Imports` pour définir des espaces de noms XML globaux que vous pouvez utiliser avec des littéraux XML et des propriétés d’axe XML, ou en tant que paramètres passés à l’opérateur `GetXmlNamespace`. (Pour plus d’informations sur l’utilisation de l’instruction `Imports` pour importer un alias qui peut être utilisé lorsque des noms de types sont utilisés dans votre code, consultez [instructions Imports (espace de noms et type .net)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).) La syntaxe permettant de déclarer un espace de noms XML à l’aide de l’instruction `Imports` est identique à la syntaxe utilisée dans XML. Par conséquent, vous pouvez copier une déclaration d’espace de noms à partir d’un fichier XML et l’utiliser dans une instruction `Imports`.

Les préfixes d’espaces de noms XML sont utiles lorsque vous souhaitez créer plusieurs éléments XML à partir du même espace de noms. Le préfixe d’espace de noms XML déclaré avec l’instruction `Imports` est global dans le sens où il est disponible pour l’ensemble du code du fichier. Vous pouvez l’utiliser lorsque vous créez des littéraux d’élément XML et lorsque vous accédez à des propriétés d’axe XML. Pour plus d’informations, consultez [littéraux d’élément XML](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md) et [propriétés d’axe XML](../../../visual-basic/language-reference/xml-axis/index.md).

Si vous définissez un espace de noms XML global sans préfixe d’espace de noms (par exemple, `Imports <xmlns="http://SomeNameSpace>"`), cet espace de noms est considéré comme l’espace de noms XML par défaut. L’espace de noms XML par défaut est utilisé pour les littéraux d’élément XML ou les propriétés d’axe d’attribut XML qui ne spécifient pas explicitement un espace de noms. L’espace de noms par défaut est également utilisé si l’espace de noms spécifié est l’espace de noms vide (autrement dit, `xmlns=""`). L’espace de noms XML par défaut ne s’applique pas aux attributs XML des littéraux XML ou aux propriétés d’axe d’attribut XML qui n’ont pas d’espace de noms.

Les espaces de noms XML définis dans un littéral XML, appelés espaces de *noms XML locaux*, ont la priorité sur les espaces de noms XML définis par l’instruction `Imports` comme global. Les espaces de noms XML définis par l’instruction `Imports` sont prioritaires sur les espaces de noms XML importés pour un projet Visual Basic. Si un littéral XML définit un espace de noms XML, cet espace de noms local ne s’applique pas aux expressions incorporées.

Les espaces de noms XML globaux suivent les mêmes règles d’étendue et de définition que les espaces de noms .NET Framework. Par conséquent, vous pouvez inclure une instruction `Imports` pour définir un espace de noms XML global partout où vous pouvez importer un espace de noms .NET Framework. Cela comprend à la fois les fichiers de code et les espaces de noms importés au niveau du projet. Pour plus d’informations sur les espaces de noms importés au niveau du projet, consultez la [page références, concepteur de projets (Visual Basic)](/visualstudio/ide/reference/references-page-project-designer-visual-basic).

Chaque fichier source peut contenir un nombre quelconque d’instructions `Imports`. Celles-ci doivent suivre les déclarations d’option, telles que l’instruction `Option Strict`, et elles doivent précéder les déclarations d’éléments de programmation, telles que les instructions `Module` ou `Class`.

## <a name="example"></a>Exemple

L’exemple suivant importe un espace de noms XML par défaut et un espace de noms XML identifié par le préfixe `ns`. Il crée ensuite des littéraux XML qui utilisent les deux espaces de noms.

[!code-vb[VbXMLSamples#45](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/Module1.vb#45)]

Ce code affiche le texte suivant :

```xml
<ns:outer xmlns="http://DefaultNamespace"
          xmlns:ns="http://NewNamespace">
  <ns:innerElement></ns:innerElement>
  <siblingElement></siblingElement>
  <innerElement />
</ns:outer>
```

## <a name="example"></a>Exemple

L’exemple suivant importe le préfixe d’espace de noms XML `ns`. Il crée ensuite un littéral XML qui utilise le préfixe d’espace de noms et affiche le formulaire final de l’élément.

[!code-vb[VbXMLSamples#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples10.vb#22)]

Ce code affiche le texte suivant :

```xml
<ns:outer xmlns:ns="http://SomeNamespace">
  <ns:middle xmlns:ns="http://NewNamespace">
    <ns:inner1 />
    <inner2 xmlns="http://SomeNamespace" />
  </ns:middle>
</ns:outer>
```

Notez que le compilateur a converti le préfixe d’espace de noms XML d’un préfixe global en définition de préfixe local.

## <a name="example"></a>Exemple

L’exemple suivant importe le préfixe d’espace de noms XML `ns`. Il utilise ensuite le préfixe de l'espace de noms pour créer un littéral XML et accéder au premier nœud enfant avec le nom qualifié `ns:name`.

[!code-vb[VbXMLSamples#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples8.vb#19)]

Ce code affiche le texte suivant :

`Patrick Hines`

## <a name="see-also"></a>Voir aussi

- [Littéral d’élément XML](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)
- [Propriétés d’axe XML](../../../visual-basic/language-reference/xml-axis/index.md)
- [Nom des attributs et des éléments XML déclarés](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)
- [GetXmlNamespace (opérateur)](../../../visual-basic/language-reference/operators/getxmlnamespace-operator.md)
