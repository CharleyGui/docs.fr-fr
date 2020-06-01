---
title: Finaliseurs - Guide de programmation C#
ms.date: 10/08/2018
helpviewer_keywords:
- ~ [C#], in finalizers
- C# language, finalizers
- finalizers [C#]
ms.assetid: 1ae6e46d-a4b1-4a49-abe5-b97f53d9e049
ms.openlocfilehash: a266cfd5996aca7b7a6b297b0775526cf38b8f64
ms.sourcegitcommit: a241301495a84cc8c64fe972330d16edd619868b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/01/2020
ms.locfileid: "84241420"
---
# <a name="finalizers-c-programming-guide"></a>Finaliseurs (Guide de programmation C#)
Les finaliseurs (également appelés **destructeurs**) servent à effectuer les derniers nettoyages nécessaires lorsqu’une instance de classe est collectée par le récupérateur de mémoire.  
  
## <a name="remarks"></a>Remarques  
  
- Les finaliseurs ne peuvent pas être définis dans des structs. Ils sont utilisés uniquement avec les classes.  
  
- Une classe ne peut avoir qu’un seul finaliseur.  
  
- Les finaliseurs ne peuvent pas être hérités ou surchargés.  
  
- Les finaliseurs ne peuvent pas être appelés. Ils sont appelés automatiquement.  
  
- Un finaliseur ne prend pas de modificateur et n’a pas de paramètre.  
  
 Par exemple, voici une déclaration de finaliseur pour la classe `Car`.
  
 [!code-csharp[csProgGuideObjects#86](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#86)]  

Un finaliseur peut aussi être implémenté en tant que définition de corps d’expression, comme l’illustre l’exemple suivant.

[!code-csharp[expression-bodied-finalizer](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-destructor.cs#1)]  
  
 Le finaliseur appelle implicitement <xref:System.Object.Finalize%2A> sur la classe de base de l’objet. Ainsi, un appel à un finaliseur est traduit implicitement en ce code :  
  
```csharp  
protected override void Finalize()  
{  
    try  
    {  
        // Cleanup statements...  
    }  
    finally  
    {  
        base.Finalize();  
    }  
}  
```  
  
 Cela signifie que la méthode `Finalize` est appelée de manière récursive pour toutes les instances de la chaîne d’héritage, de la plus dérivée à la moins dérivée.  
  
> [!NOTE]
> Les finaliseurs vides ne doivent pas être utilisés. Quand une classe contient un finaliseur, une entrée est créée dans la file d’attente `Finalize`. Quand le finaliseur est appelé, le récupérateur de mémoire est appelé pour traiter la file d’attente. Un finaliseur vide entraîne une perte de performances inutile.  
  
 Le programmeur n’a aucun contrôle sur le moment où le finaliseur est appelé, car celui-ci est déterminé par le récupérateur de mémoire. Le récupérateur de mémoire recherche les objets qui ne sont plus utilisés par l’application. S’il considère qu’un objet peut être finalisé, il appelle le finaliseur (s’il y en a un) et libère la mémoire utilisée pour stocker l’objet.

 Dans les applications .NET Framework (mais pas dans les applications .NET Core), les finaliseurs sont également appelés quand le programme se termine.
  
 Il est possible de forcer le nettoyage de la mémoire en appelant <xref:System.GC.Collect%2A>, mais la plupart du temps c’est à éviter car cela peut créer des problèmes de performances.  
  
## <a name="using-finalizers-to-release-resources"></a>Utiliser des finaliseurs pour libérer des ressources  
 En général, C# ne nécessite pas autant de gestion de mémoire que quand vous développez avec un langage qui ne cible pas un runtime avec nettoyage de la mémoire. Cela est dû au fait que le garbage collector .NET gère implicitement l’allocation et la libération de mémoire pour vos objets. Toutefois, quand votre application encapsule des ressources non managées, telles que des fenêtres, des fichiers et des connexions réseau, vous devez utiliser des finaliseurs pour libérer ces ressources. Quand l’objet peut être finalisé, le récupérateur de mémoire exécute la méthode `Finalize` de l’objet.
  
## <a name="explicit-release-of-resources"></a>Libération explicite de ressources  
 Si votre application utilise une ressource externe coûteuse, nous vous recommandons également de proposer un moyen de libérer explicitement la ressource avant que le récupérateur de mémoire ne libère l’objet. Pour cela, vous devez implémenter une méthode `Dispose` à partir de l’interface <xref:System.IDisposable> qui effectue le nettoyage nécessaire pour l’objet. Cela peut améliorer considérablement les performances de l’application. Même avec ce contrôle explicite des ressources, le finaliseur devient un dispositif de protection pour nettoyer les ressources si l’appel à la méthode `Dispose` a échoué.  
  
 Pour plus d’informations sur le nettoyage des ressources, consultez les rubriques suivantes :  
  
- [Nettoyage des ressources non managées](../../../standard/garbage-collection/unmanaged.md)  
  
- [Implémentation d’une méthode dispose](../../../standard/garbage-collection/implementing-dispose.md)  
  
- [using, instruction](../../language-reference/keywords/using-statement.md)  
  
## <a name="example"></a>Exemple  
 L’exemple suivant crée trois classes qui forment une chaîne d’héritage. La classe `First` est la classe de base, `Second` est dérivée de `First`, et `Third` est dérivée de `Second`. Toutes trois ont des finaliseurs. Dans `Main`, une instance de la classe la plus dérivée est créée. Quand le programme s’exécute, notez que les finaliseurs des trois classes sont appelés automatiquement, et dans l’ordre, de la plus dérivée à la moins dérivée.  
  
 [!code-csharp[csProgGuideObjects#85](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#85)]  
  
## <a name="c-language-specification"></a>spécification du langage C#  

Pour plus d’informations, voir la section [Destructeurs](~/_csharplang/spec/classes.md#destructors) de la [spécification du langage C#](/dotnet/csharp/language-reference/language-specification/introduction).
  
## <a name="see-also"></a>Voir aussi

- <xref:System.IDisposable>
- [Guide de programmation C#](../index.md)
- [Constructeurs](./constructors.md)
- [Garbage collection](../../../standard/garbage-collection/index.md)
