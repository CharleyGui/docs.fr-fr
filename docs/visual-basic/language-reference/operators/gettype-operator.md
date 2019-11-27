---
title: GetType Operator
ms.date: 07/20/2015
f1_keywords:
- vb.GetType
helpviewer_keywords:
- GetType operator [Visual Basic]
- GetType keyword [Visual Basic]
ms.assetid: 4f733297-2503-4607-850c-15eba65fff90
ms.openlocfilehash: 4e59bcfaa24c9545ed75c6b5c1d29cad398ac2de
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349550"
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
 L’opérateur `GetType` retourne l’objet <xref:System.Type> pour le `typename`spécifié. Vous pouvez passer le nom de n’importe quel type défini dans `typename`. Ce dernier est détaillé ci-après :  
  
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
 Les exemples suivants illustrent l’opérateur `GetType` en cours d’utilisation.  
  
 [!code-vb[VbVbalrOperators#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#26)]  
  
## <a name="see-also"></a>Voir aussi

- [Priorité des opérateurs en Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [Opérateurs répertoriés par fonctionnalité](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Opérateurs et expressions](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
