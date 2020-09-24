---
title: Comment tester l’égalité des références (identité)-Guide de programmation C#
description: Découvrez comment tester l’égalité des références (identité). Consultez un exemple de code et affichez des ressources supplémentaires disponibles.
ms.date: 07/20/2015
helpviewer_keywords:
- object identity [C#]
- reference equality [C#]
ms.assetid: 91307fda-267b-4fd2-a338-2aada39ee791
ms.openlocfilehash: 1d1a0e5d80ac8d2a689e75acbc6099b92e16f23f
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91151439"
---
# <a name="how-to-test-for-reference-equality-identity-c-programming-guide"></a>Comment tester l’égalité des références (identité) (Guide de programmation C#)

Il n’est pas utile d’implémenter une logique personnalisée pour prendre en charge les comparaisons d’égalité de références dans vos types. Cette fonctionnalité est fournie pour tous les types par la méthode <xref:System.Object.ReferenceEquals%2A?displayProperty=nameWithType> statique.  
  
 L’exemple suivant montre comment déterminer si deux variables affichent une *égalité de références*, à savoir qu’elles font référence à un même objet en mémoire.  
  
 L’exemple montre aussi pourquoi <xref:System.Object.ReferenceEquals%2A?displayProperty=nameWithType> retourne toujours `false` pour les types valeur et pourquoi vous ne devez pas utiliser <xref:System.Object.ReferenceEquals%2A> pour déterminer l’égalité de chaînes.  
  
## <a name="example"></a>Exemple  

 [!code-csharp[csProgGuideObjects#90](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#90)]  
  
 L’implémentation de `Equals` dans la classe de base universelle <xref:System.Object?displayProperty=nameWithType> assure aussi une vérification de l’égalité de références, mais il est préférable de ne pas l’utiliser, car si une classe se substitue à la méthode, vous risquez d’obtenir des résultats inattendus. Il en va de même pour les opérateurs `==` et `!=`. Quand ils s’appliquent à des types référence, le comportement par défaut de `==` et de `!=` est d’effectuer une vérification de l’égalité des références. Cependant, les classes dérivées peuvent surcharger l’opérateur pour effectuer une vérification d’égalité de valeurs. Pour réduire le risque d’erreurs, il est recommandé d’utiliser systématiquement <xref:System.Object.ReferenceEquals%2A> quand il s’agit de déterminer si deux objets présentent une égalité de références.  
  
 Les chaînes constantes au sein d’un même assembly sont toujours intégrées par le runtime. Autrement dit, une seule instance de chaque chaîne littérale unique est conservée. En revanche, le runtime ne garantit pas que les chaînes créées au moment de l’exécution sont intégrées, ni que deux chaînes constantes égales d’assemblys différents sont intégrées.  
  
## <a name="see-also"></a>Voir aussi

- [Comparaisons d’égalité](./equality-comparisons.md)
