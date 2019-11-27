---
title: Littéral d'instruction de traitement XML
ms.date: 07/20/2015
f1_keywords:
- vb.XmlLiteralProcessingInstruction
helpviewer_keywords:
- XML literals [Visual Basic], processing instruction
- XML processing instruction literal [Visual Basic]
- processing instruction literal [Visual Basic]
ms.assetid: cef4f7f8-0011-4f64-8602-795077ad4f15
ms.openlocfilehash: 3602a81feae9287a77d060bb46f10eefee4fc05d
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347047"
---
# <a name="xml-processing-instruction-literal-visual-basic"></a>Littéral d'instruction de traitement XML (Visual Basic)
Littéral représentant un objet <xref:System.Xml.Linq.XProcessingInstruction>.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<?piName [ = piData ] ?>  
```  
  
## <a name="parts"></a>Composants  
 `<?`  
 Requis. Indique le début du littéral d’instruction de traitement XML.  
  
 `piName`  
 Requis. Nom indiquant l’application ciblée par l’instruction de traitement. Ne peut pas commencer par « XML » ou « XML ».  
  
 `piData`  
 Ce paramètre est facultatif. Chaîne indiquant comment l’application ciblée par `piName` doit traiter le document XML.  
  
 `?>`  
 Requis. Indique la fin de l’instruction de traitement.  
  
## <a name="return-value"></a>Valeur de retour  
 Objet <xref:System.Xml.Linq.XProcessingInstruction>.  
  
## <a name="remarks"></a>Notes  
 Les littéraux d’instruction de traitement XML indiquent comment les applications doivent traiter un document XML. Quand une application charge un document XML, l’application peut vérifier les instructions de traitement XML pour déterminer comment traiter le document. L’application interprète la signification de `piName` et `piData`.  
  
 Le littéral de document XML utilise une syntaxe similaire à celle de l’instruction de traitement XML. Pour plus d’informations, consultez [littéral de document XML](../../../visual-basic/language-reference/xml-literals/xml-document-literal.md).  
  
> [!NOTE]
> L’élément `piName` ne peut pas commencer par les chaînes « XML » ou « XML », car la spécification XML 1,0 réserve ces identificateurs.  
  
 Vous pouvez assigner un littéral d’instruction de traitement XML à une variable ou l’inclure dans un littéral de document XML.  
  
> [!NOTE]
> Un littéral XML peut s’étendre sur plusieurs lignes sans avoir besoin de caractères de continuation de ligne. Cela vous permet de copier le contenu d’un document XML et de le coller directement dans un programme de Visual Basic.  
  
 Le compilateur Visual Basic convertit le littéral d’instruction de traitement XML en un appel au constructeur <xref:System.Xml.Linq.XProcessingInstruction.%23ctor%2A>.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant crée une instruction de traitement identifiant une feuille de style pour un document XML.  
  
 [!code-vb[VbXMLSamples#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#28)]  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Xml.Linq.XProcessingInstruction>
- [Littéral de document XML](../../../visual-basic/language-reference/xml-literals/xml-document-literal.md)
- [Littéraux XML](../../../visual-basic/language-reference/xml-literals/index.md)
- [Création de code XML dans Visual Basic](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
