---
title: Opérateur GetType (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.GetType
helpviewer_keywords:
- GetType operator [Visual Basic]
- GetType keyword [Visual Basic]
ms.assetid: 4f733297-2503-4607-850c-15eba65fff90
ms.openlocfilehash: 2e3e05973f2ef72fef5e429bc98cc58b4b21f2c2
ms.sourcegitcommit: 35da8fb45b4cca4e59cc99a5c56262c356977159
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/28/2019
ms.locfileid: "71592151"
---
# <a name="gettype-operator-visual-basic"></a>Opérateur GetType (Visual Basic)
Retourne un objet <xref:System.Type> pour le type spécifié. L’objet <xref:System.Type> fournit des informations sur le type, telles que ses propriétés, méthodes et événements.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
GetType(typename)  
```  
  
## <a name="parameters"></a>Paramètres  
  
|Paramètre|Description|  
|---|---|  
|`typename`|Nom du type pour lequel vous souhaitez obtenir des informations.|  
  
## <a name="remarks"></a>Notes  
 L’opérateur `GetType` retourne l’objet <xref:System.Type> pour le @no__t spécifié-2. Vous pouvez passer le nom de n’importe quel type défini dans `typename`. Notamment :  
  
- Tout Visual Basic type de données, tel que `Boolean` ou `Date`.  
  
- Tout .NET Framework classe, structure, module ou interface, comme <xref:System.ArgumentException?displayProperty=nameWithType> ou <xref:System.Double?displayProperty=nameWithType>.  
  
- Toute classe, structure, module ou interface définie par votre application.  
  
- Tout tableau défini par votre application.  
  
- Tout délégué défini par votre application.  
  
- Toute énumération définie par Visual Basic, le .NET Framework ou votre application.  
  
 Si vous souhaitez obtenir l’objet de type d’une variable objet, utilisez la méthode <xref:System.Type.GetType%2A?displayProperty=nameWithType>.  
  
 L’opérateur `GetType` peut être utile dans les circonstances suivantes :  
  
- Vous devez accéder aux métadonnées d’un type au moment de l’exécution. L’objet <xref:System.Type> fournit des métadonnées, telles que des membres de type et des informations de déploiement. Vous en aurez besoin, par exemple, pour réfléchir un assembly. Pour plus d'informations, consultez <xref:System.Reflection?displayProperty=nameWithType>.  
  
- Vous souhaitez comparer deux références d’objet pour voir si elles font référence à des instances du même type. Si c’est le cas, `GetType` retourne des références au même objet <xref:System.Type>.  
  
## <a name="example"></a>Exemple  
 Les exemples suivants montrent l’opérateur `GetType` en cours d’utilisation.  
  
 [!code-vb[VbVbalrOperators#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#26)]  
  
## <a name="see-also"></a>Voir aussi

- [Priorité des opérateurs en Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [Opérateurs répertoriés par fonctionnalité](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Opérateurs et expressions](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
