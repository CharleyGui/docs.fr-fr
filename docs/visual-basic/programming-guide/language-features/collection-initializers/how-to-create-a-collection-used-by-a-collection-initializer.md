---
title: 'Comment : créer une collection utilisée par un initialiseur de collection'
ms.date: 07/20/2015
helpviewer_keywords:
- collection initializers [Visual Basic]
ms.assetid: c858db10-424d-47e0-92cd-e08087cc5ebc
ms.openlocfilehash: 5eaf9e828455bf2accda86ab52a1ce645f10b9ee
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349062"
---
# <a name="how-to-create-a-collection-used-by-a-collection-initializer-visual-basic"></a>Comment : créer une collection utilisée par un initialiseur de collection (Visual Basic)
Lorsque vous utilisez un initialiseur de collection pour créer une collection, le compilateur Visual Basic recherche une `Add` méthode du type de collection pour lequel les paramètres de la méthode `Add` correspondent aux types des valeurs dans l’initialiseur de collection. Cette méthode `Add` est utilisée pour remplir la collection avec les valeurs de l’initialiseur de collection.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre une collection `OrderCollection` qui contient une méthode `Add` publique qu’un initialiseur de collection peut utiliser pour ajouter des objets de type `Order`. La méthode `Add` vous permet d’utiliser la syntaxe raccourcie de l’initialiseur de collection.  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo2#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializersHowTo2/VB/Module1.vb#4)]  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo2#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializersHowTo2/VB/Module1.vb#1)]  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo2#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializersHowTo2/VB/Module1.vb#2)]  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo2#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializersHowTo2/VB/Module1.vb#3)]  
  
## <a name="see-also"></a>Voir aussi

- [Initialiseurs de collection](../../../../visual-basic/programming-guide/language-features/collection-initializers/index.md)
- [Guide pratique : créer une méthode d’extension Add utilisée par un initialiseur de collection](../../../../visual-basic/programming-guide/language-features/collection-initializers/how-to-create-an-add-extension-method-used-by-a-collection-initializer.md)
