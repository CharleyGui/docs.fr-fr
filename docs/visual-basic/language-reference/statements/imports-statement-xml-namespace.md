---
title: Instruction Imports-espace de noms XML
ms.date: 07/20/2015
f1_keywords:
- vb.ImportsXmlns
helpviewer_keywords:
- XML namespace [Visual Basic], importing
- imports [Visual Basic]
- Imports statement [Visual Basic]
- namespaces [Visual Basic], importing
ms.assetid: 1f4d50a6-08c7-4c2e-8206-ccae35fcd1b4
ms.openlocfilehash: a3184d68b0e4cdff5d4296a5a638e22b4e83bcde
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404535"
---
# <a name="imports-statement-xml-namespace"></a>Imports, instruction (espace de noms XML)

Importe les préfixes d’espaces de noms XML à utiliser dans les littéraux XML et les propriétés d’axe XML.

## <a name="syntax"></a>Syntaxe

```vb
Imports <xmlns:xmlNamespacePrefix = "xmlNamespaceName">
```

## <a name="parts"></a>Éléments

`xmlNamespacePrefix`  
Facultatif. Chaîne par laquelle les éléments et attributs XML peuvent faire référence `xmlNamespaceName` . Si aucun `xmlNamespacePrefix` n’est fourni, l’espace de noms XML importé est l’espace de noms XML par défaut. Doit être un identificateur XML valide. Pour plus d’informations, consultez [noms des éléments et attributs XML déclarés](../../programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).

`xmlNamespaceName`  
Obligatoire. Chaîne identifiant l’espace de noms XML importé.

## <a name="remarks"></a>Notes

Vous pouvez utiliser l' `Imports` instruction pour définir des espaces de noms XML globaux que vous pouvez utiliser avec des littéraux XML et des propriétés d’axe XML, ou comme paramètres passés à l' `GetXmlNamespace` opérateur. (Pour plus d’informations sur l’utilisation de l' `Imports` instruction pour importer un alias qui peut être utilisé lorsque des noms de types sont utilisés dans votre code, consultez [instructions Imports (espace de noms et type .net)](imports-statement-net-namespace-and-type.md).) La syntaxe permettant de déclarer un espace de noms XML à l’aide de l' `Imports` instruction est identique à la syntaxe utilisée dans XML. Par conséquent, vous pouvez copier une déclaration d’espace de noms à partir d’un fichier XML et l’utiliser dans une `Imports` instruction.

Les préfixes d’espaces de noms XML sont utiles lorsque vous souhaitez créer plusieurs éléments XML à partir du même espace de noms. Le préfixe d’espace de noms XML déclaré avec l' `Imports` instruction est global dans le sens où il est disponible pour l’ensemble du code dans le fichier. Vous pouvez l’utiliser lorsque vous créez des littéraux d’élément XML et lorsque vous accédez à des propriétés d’axe XML. Pour plus d’informations, consultez [littéraux d’élément XML](../xml-literals/xml-element-literal.md) et [propriétés d’axe XML](../xml-axis/index.md).

Si vous définissez un espace de noms XML global sans préfixe d’espace de noms (par exemple, `Imports <xmlns="http://SomeNameSpace>"` ), cet espace de noms est considéré comme l’espace de noms XML par défaut. L’espace de noms XML par défaut est utilisé pour les littéraux d’élément XML ou les propriétés d’axe d’attribut XML qui ne spécifient pas explicitement un espace de noms. L’espace de noms par défaut est également utilisé si l’espace de noms spécifié est l’espace de noms vide (autrement dit, `xmlns=""` ). L’espace de noms XML par défaut ne s’applique pas aux attributs XML des littéraux XML ou aux propriétés d’axe d’attribut XML qui n’ont pas d’espace de noms.

Les espaces de noms XML définis dans un littéral XML, appelés espaces de *noms XML locaux*, ont la priorité sur les espaces de noms XML qui sont définis par l' `Imports` instruction comme étant global. Les espaces de noms XML définis par l' `Imports` instruction sont prioritaires sur les espaces de noms XML importés pour un projet Visual Basic. Si un littéral XML définit un espace de noms XML, cet espace de noms local ne s’applique pas aux expressions incorporées.

Les espaces de noms XML globaux suivent les mêmes règles d’étendue et de définition que les espaces de noms .NET Framework. Par conséquent, vous pouvez inclure une `Imports` instruction pour définir un espace de noms XML global partout où vous pouvez importer un espace de noms .NET Framework. Cela comprend à la fois les fichiers de code et les espaces de noms importés au niveau du projet. Pour plus d’informations sur les espaces de noms importés au niveau du projet, consultez la [page références, concepteur de projets (Visual Basic)](/visualstudio/ide/reference/references-page-project-designer-visual-basic).

Chaque fichier source peut contenir un nombre quelconque d' `Imports` instructions. Celles-ci doivent suivre les déclarations d’option, telles que l' `Option Strict` instruction, et elles doivent précéder les déclarations d’éléments de programmation, telles que les `Module` `Class` instructions ou.

## <a name="example"></a>Exemple

L’exemple suivant importe un espace de noms XML par défaut et un espace de noms XML identifié par le préfixe `ns` . Il crée ensuite des littéraux XML qui utilisent les deux espaces de noms.

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

L’exemple suivant importe le préfixe d’espace de noms XML `ns` . Il crée ensuite un littéral XML qui utilise le préfixe d’espace de noms et affiche le formulaire final de l’élément.

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

L’exemple suivant importe le préfixe d’espace de noms XML `ns` . Il utilise ensuite le préfixe de l'espace de noms pour créer un littéral XML et accéder au premier nœud enfant avec le nom qualifié `ns:name`.

[!code-vb[VbXMLSamples#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples8.vb#19)]

Ce code affiche le texte suivant :

`Patrick Hines`

## <a name="see-also"></a>Voir aussi

- [Littéral d’élément XML](../xml-literals/xml-element-literal.md)
- [Propriétés d'axe XML](../xml-axis/index.md)
- [Nom des attributs et des éléments XML déclarés](../../programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)
- [GetXmlNamespace, opérateur](../operators/getxmlnamespace-operator.md)
