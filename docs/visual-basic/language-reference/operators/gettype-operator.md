---
title: GetType Operator
ms.date: 07/20/2015
f1_keywords:
- vb.GetType
helpviewer_keywords:
- GetType operator [Visual Basic]
- GetType keyword [Visual Basic]
ms.assetid: 4f733297-2503-4607-850c-15eba65fff90
ms.openlocfilehash: 37644a9c37ffde084120c5f1e1ee8c87a04ffc3c
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84371153"
---
# <a name="gettype-operator-visual-basic"></a>Opérateur GetType (Visual Basic)
Retourne un <xref:System.Type> objet pour le type spécifié. L' <xref:System.Type> objet fournit des informations sur le type, telles que ses propriétés, méthodes et événements.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
GetType(typename)  
```  
  
## <a name="parameters"></a>Paramètres  
  
|Paramètre|Description|  
|---|---|  
|`typename`|Nom du type pour lequel vous souhaitez obtenir des informations.|  
  
## <a name="remarks"></a>Notes  
 L' `GetType` opérateur retourne l' <xref:System.Type> objet pour le spécifié `typename` . Vous pouvez passer le nom de n’importe quel type défini dans `typename` . Notamment :  
  
- Tout Visual Basic type de données, tel que `Boolean` ou `Date` .  
  
- Tout .NET Framework classe, structure, module ou interface, tel que <xref:System.ArgumentException?displayProperty=nameWithType> ou <xref:System.Double?displayProperty=nameWithType> .  
  
- Toute classe, structure, module ou interface définie par votre application.  
  
- Tout tableau défini par votre application.  
  
- Tout délégué défini par votre application.  
  
- Toute énumération définie par Visual Basic, le .NET Framework ou votre application.  
  
 Si vous souhaitez obtenir l’objet de type d’une variable objet, utilisez la <xref:System.Type.GetType%2A?displayProperty=nameWithType> méthode.  
  
 L' `GetType` opérateur peut être utile dans les circonstances suivantes :  
  
- Vous devez accéder aux métadonnées d’un type au moment de l’exécution. L' <xref:System.Type> objet fournit des métadonnées, telles que des membres de type et des informations de déploiement. Vous en aurez besoin, par exemple, pour réfléchir un assembly. Pour plus d’informations, consultez <xref:System.Reflection?displayProperty=nameWithType>.  
  
- Vous souhaitez comparer deux références d’objet pour voir si elles font référence à des instances du même type. Si c’est le cas, `GetType` retourne des références au même <xref:System.Type> objet.  
  
## <a name="example"></a>Exemple  
 Les exemples suivants illustrent l' `GetType` opérateur en cours d’utilisation.  
  
 [!code-vb[VbVbalrOperators#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#26)]  
  
## <a name="see-also"></a>Voir aussi

- [Priorité des opérateurs en Visual Basic](operator-precedence.md)
- [Opérateurs listés par fonctionnalité](operators-listed-by-functionality.md)
- [Opérateurs et expressions](../../programming-guide/language-features/operators-and-expressions/index.md)
