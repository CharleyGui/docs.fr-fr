---
title: La procédure Property Let n'est pas définie et la procédure Property Get n'a pas retourné d'objet
ms.date: 07/20/2015
f1_keywords:
- vbrID451
ms.assetid: 8542382a-689f-4e1b-abc0-c1e2dadb92f4
ms.openlocfilehash: fbeaa224ea9e095f86c37e571492d83bc98b4397
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90871096"
---
# <a name="property-let-procedure-not-defined-and-property-get-procedure-did-not-return-an-object"></a>La procédure Property Let n'est pas définie et la procédure Property Get n'a pas retourné d'objet

Certaines propriétés, méthodes et opérations ne peuvent s’appliquer qu’à des `Collection` objets. Vous avez spécifié une opération ou une propriété qui est exclusive aux collections, mais l’objet n’est pas une collection.  
  
## <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
1. Vérifiez l’orthographe du nom de l’objet ou de la propriété, ou vérifiez que l’objet est un `Collection` objet.  
  
2. Examinez la `Add` méthode utilisée pour ajouter l’objet à la collection afin de vérifier que la syntaxe est correcte et que tous les identificateurs ont été correctement orthographiés.  
  
## <a name="see-also"></a>Voir aussi

- <xref:Microsoft.VisualBasic.Collection>
