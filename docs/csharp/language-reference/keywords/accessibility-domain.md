---
description: Domaine d'accessibilité - Référence C#
title: Domaine d'accessibilité - Référence C#
ms.date: 07/20/2015
helpviewer_keywords:
- accessibility domain [C#]
ms.assetid: 8af779c1-275b-44be-a864-9edfbca71bcc
ms.openlocfilehash: 2cfc4cc72a79b33276b7d822a2b31eb518dcf784
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89127059"
---
# <a name="accessibility-domain-c-reference"></a>Domaine d'accessibilité (référence C#)
Le domaine d’accessibilité d’un membre indique dans quelles sections du programme un membre peut être référencé. Si le membre est imbriqué dans un autre type, son domaine d’accessibilité est déterminé à la fois par le [niveau d’accessibilité](./accessibility-levels.md) du membre et par le domaine d’accessibilité du type conteneur immédiat.  
  
 Le domaine d’accessibilité d’un type de niveau supérieur est au moins le texte du programme du projet dans lequel il est déclaré. Cela signifie que le domaine inclut tous les fichiers sources de ce projet. Le domaine d’accessibilité d’un type imbriqué est au moins le texte de programme du type dans lequel il est déclaré. Autrement dit, le domaine est le corps du type, qui inclut tous les types imbriqués. Le domaine d’accessibilité d’un type imbriqué ne dépasse jamais celui du type conteneur. Ces concepts sont illustrés dans l’exemple suivant.  
  
## <a name="example"></a>Exemple  
 Cet exemple comporte un type de niveau supérieur, `T1`, et deux classes imbriquées, `M1` et `M2`. Les classes contiennent des champs qui ont des accessibilités déclarées différentes. Dans la méthode `Main`, un commentaire suit chaque instruction pour indiquer le domaine d’accessibilité de chaque membre. Notez que les instructions qui essaient de référencer les membres inaccessibles sont commentées. Si vous souhaitez voir les erreurs de compilation provoquées par le référencement d’un membre inaccessible, supprimez les commentaires un par un.  
  
[!code-csharp[csrefKeywordsModifiers#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#4)]
  
## <a name="c-language-specification"></a>Spécification du langage C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Référence C#](../index.md)
- [Guide de programmation C#](../../programming-guide/index.md)
- [Mots clés C#](./index.md)
- [Modificateurs d’accès](./access-modifiers.md)
- [Niveaux d'accessibilité](./accessibility-levels.md)
- [Restrictions concernant l’utilisation des niveaux d’accessibilité](./restrictions-on-using-accessibility-levels.md)
- [Modificateurs d’accès](../../programming-guide/classes-and-structs/access-modifiers.md)
- [public](./public.md)
- [priv](./private.md)
- [protected](./protected.md)
- [intérieurs](./internal.md)
