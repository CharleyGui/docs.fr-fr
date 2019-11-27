---
title: "Comment : créer une méthode d'extension Add utilisée par un initialiseur de collection"
ms.date: 07/20/2015
helpviewer_keywords:
- collection initializers [Visual Basic]
ms.assetid: f64b52c7-8b11-4410-93a6-cb3aeebcc772
ms.openlocfilehash: 6d5f9d38b413b79f111a14ec3829c57a9797ce54
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346712"
---
# <a name="how-to-create-an-add-extension-method-used-by-a-collection-initializer-visual-basic"></a>Comment : créer une méthode d'extension Add utilisée par un initialiseur de collection (Visual Basic)
Lorsque vous utilisez un initialiseur de collection pour créer une collection, le compilateur Visual Basic recherche une `Add` méthode du type de collection pour lequel les paramètres de la méthode `Add` correspondent aux types des valeurs dans l’initialiseur de collection. Cette méthode `Add` est utilisée pour remplir la collection avec les valeurs de l’initialiseur de collection.  
  
 S’il n’existe aucune méthode `Add` correspondante et que vous ne pouvez pas modifier le code de la collection, vous pouvez ajouter une méthode d’extension appelée `Add` qui accepte les paramètres requis par l’initialiseur de collection. C’est généralement ce que vous devez faire lorsque vous utilisez des initialiseurs de collection pour les collections génériques.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment ajouter une méthode d’extension au type de <xref:System.Collections.Generic.List%601> générique afin qu’un initialiseur de collection puisse être utilisé pour ajouter des objets de type `Employee`. La méthode d’extension vous permet d’utiliser la syntaxe raccourcie de l’initialiseur de collection.  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo1#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializersHowTo1/VB/Module1.vb#1)]  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo1#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializersHowTo1/VB/Module1.vb#2)]  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo1#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializersHowTo1/VB/Module1.vb#3)]  
  
## <a name="see-also"></a>Voir aussi

- [Initialiseurs de collection](../../../../visual-basic/programming-guide/language-features/collection-initializers/index.md)
- [Guide pratique : créer une collection utilisée par un initialiseur de collection](../../../../visual-basic/programming-guide/language-features/collection-initializers/how-to-create-a-collection-used-by-a-collection-initializer.md)
