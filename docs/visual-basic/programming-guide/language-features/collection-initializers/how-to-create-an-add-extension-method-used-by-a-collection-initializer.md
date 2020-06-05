---
title: "Comment : créer une méthode d'extension Add utilisée par un initialiseur de collection"
ms.date: 07/20/2015
helpviewer_keywords:
- collection initializers [Visual Basic]
ms.assetid: f64b52c7-8b11-4410-93a6-cb3aeebcc772
ms.openlocfilehash: 4dbe6146b70181864a6717146071f9b93a1f583e
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84414567"
---
# <a name="how-to-create-an-add-extension-method-used-by-a-collection-initializer-visual-basic"></a>Comment : créer une méthode d'extension Add utilisée par un initialiseur de collection (Visual Basic)
Lorsque vous utilisez un initialiseur de collection pour créer une collection, le compilateur Visual Basic recherche une `Add` méthode du type de collection pour lequel les paramètres de la `Add` méthode correspondent aux types des valeurs dans l’initialiseur de collection. Cette `Add` méthode est utilisée pour remplir la collection avec les valeurs de l’initialiseur de collection.  
  
 S’il n' `Add` existe aucune méthode correspondante et que vous ne pouvez pas modifier le code de la collection, vous pouvez ajouter une méthode d’extension nommée `Add` qui accepte les paramètres requis par l’initialiseur de collection. C’est généralement ce que vous devez faire lorsque vous utilisez des initialiseurs de collection pour les collections génériques.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment ajouter une méthode d’extension au type générique <xref:System.Collections.Generic.List%601> afin qu’un initialiseur de collection puisse être utilisé pour ajouter des objets de type `Employee` . La méthode d’extension vous permet d’utiliser la syntaxe raccourcie de l’initialiseur de collection.  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo1#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializersHowTo1/VB/Module1.vb#1)]  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo1#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializersHowTo1/VB/Module1.vb#2)]  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo1#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializersHowTo1/VB/Module1.vb#3)]  
  
## <a name="see-also"></a>Voir aussi

- [Initialiseurs de collection](index.md)
- [Guide pratique : créer une collection utilisée par un initialiseur de collection](how-to-create-a-collection-used-by-a-collection-initializer.md)
