---
title: Littéral d’instruction de traitement XML
ms.date: 07/20/2015
f1_keywords:
- vb.XmlLiteralProcessingInstruction
helpviewer_keywords:
- XML literals [Visual Basic], processing instruction
- XML processing instruction literal [Visual Basic]
- processing instruction literal [Visual Basic]
ms.assetid: cef4f7f8-0011-4f64-8602-795077ad4f15
ms.openlocfilehash: 9bd1781e01bc4cbf1ce5da8c454ab2f5a679aead
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400174"
---
# <a name="xml-processing-instruction-literal-visual-basic"></a>Littéral d'instruction de traitement XML (Visual Basic)
Littéral représentant un <xref:System.Xml.Linq.XProcessingInstruction> objet.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<?piName [ = piData ] ?>  
```  
  
## <a name="parts"></a>Éléments  
 `<?`  
 Obligatoire. Indique le début du littéral d’instruction de traitement XML.  
  
 `piName`  
 Obligatoire. Nom indiquant l’application ciblée par l’instruction de traitement. Ne peut pas commencer par « XML » ou « XML ».  
  
 `piData`  
 Facultatif. Chaîne indiquant comment l’application ciblée par `piName` doit traiter le document XML.  
  
 `?>`  
 Obligatoire. Indique la fin de l’instruction de traitement.  
  
## <a name="return-value"></a>Valeur renvoyée  
 Objet <xref:System.Xml.Linq.XProcessingInstruction>.  
  
## <a name="remarks"></a>Notes  
 Les littéraux d’instruction de traitement XML indiquent comment les applications doivent traiter un document XML. Quand une application charge un document XML, l’application peut vérifier les instructions de traitement XML pour déterminer comment traiter le document. L’application interprète la signification de `piName` et `piData` .  
  
 Le littéral de document XML utilise une syntaxe similaire à celle de l’instruction de traitement XML. Pour plus d’informations, consultez [littéral de document XML](xml-document-literal.md).  
  
> [!NOTE]
> L' `piName` élément ne peut pas commencer par les chaînes « XML » ou « XML », car la spécification xml 1,0 réserve ces identificateurs.  
  
 Vous pouvez assigner un littéral d’instruction de traitement XML à une variable ou l’inclure dans un littéral de document XML.  
  
> [!NOTE]
> Un littéral XML peut s’étendre sur plusieurs lignes sans avoir besoin de caractères de continuation de ligne. Cela vous permet de copier le contenu d’un document XML et de le coller directement dans un programme de Visual Basic.  
  
 Le compilateur Visual Basic convertit le littéral d’instruction de traitement XML en un appel au <xref:System.Xml.Linq.XProcessingInstruction.%23ctor%2A> constructeur.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant crée une instruction de traitement identifiant une feuille de style pour un document XML.  
  
 [!code-vb[VbXMLSamples#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#28)]  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Xml.Linq.XProcessingInstruction>
- [Littéral de document XML](xml-document-literal.md)
- [Littéraux XML](index.md)
- [Création de code XML dans Visual Basic](../../programming-guide/language-features/xml/creating-xml.md)
