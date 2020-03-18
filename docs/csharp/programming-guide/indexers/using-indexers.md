---
title: Utiliser des indexeurs - Guide de programmation C#
ms.date: 10/03/2018
helpviewer_keywords:
- indexers [C#], about indexers
ms.assetid: df70e1a2-3ce3-4aba-ad80-4b2f3538699f
ms.openlocfilehash: 17162a0dc959a85c03a5cb5757e2b91fe10b0ab3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "77628161"
---
# <a name="using-indexers-c-programming-guide"></a>Utiliser des indexeurs (Guide de programmation C#)

Les indexeurs simplifient, d’un point de vue syntaxique, la création d’une [classe](../../language-reference/keywords/class.md), d’un [struct](../../language-reference/builtin-types/struct.md) ou d’une [interface](../../language-reference/keywords/interface.md) auxquels les applications clientes peuvent accéder exactement comme à un tableau. Le plus souvent, les indexeurs sont implémentés dans les types dont l’objectif premier est d’encapsuler une collection ou un tableau interne. Prenons l’exemple d’une classe `TempRecord` qui représente la température, en Fahrenheit, enregistrée à 10 moments différents sur une période de 24 heures. Elle contient un tableau `temps` de type `float[]` pour stocker les valeurs de température. En implémentant un indexeur dans cette classe, les clients peuvent accéder aux températures dans une instance `TempRecord` sous la forme `float temp = tr[4]` et non sous la forme `float temp = tr.temps[4]`. La notation d’indexeur simplifie non seulement la syntaxe pour les applications clientes, mais elle permet également aux autres développeurs de comprendre de façon plus intuitive l’objectif de la classe.  
  
Pour déclarer un indexeur sur une classe ou un struct, utilisez le mot clé [this](../../language-reference/keywords/this.md), comme dans l’exemple suivant :

```csharp
public int this[int index]    // Indexer declaration  
{  
    // get and set accessors  
}  
```

## <a name="remarks"></a>Notes 

Le type d’un indexeur et le type de ses paramètres doivent être au moins aussi accessibles que l’indexeur lui-même. Pour plus d’informations sur les niveaux d’accessibilité, consultez [Modificateurs d’accès](../../language-reference/keywords/access-modifiers.md).  
  
 Pour plus d’informations sur l’utilisation d’indexeurs avec une interface, consultez [Indexeurs d’interface](./indexers-in-interfaces.md).  
  
 La signature d’un indexeur est composée du nombre et des types de ses paramètres formels. Elle ne comporte ni le type de l’indexeur ni le nom des paramètres formels. Si vous déclarez plusieurs indexeurs dans la même classe, ils doivent avoir des signatures différentes.  
  
 Une valeur d’indexeur n’est pas classée comme variable ; vous ne pouvez donc pas la passer comme paramètre [ref](../../language-reference/keywords/ref.md) ou [out](../../language-reference/keywords/out-parameter-modifier.md).  
  
 Pour affecter à l’indexeur un nom exploitable dans d’autres langages, utilisez <xref:System.Runtime.CompilerServices.IndexerNameAttribute?displayProperty=nameWithType>, comme dans l’exemple suivant :  

```csharp
[System.Runtime.CompilerServices.IndexerName("TheItem")]  
public int this[int index]   // Indexer declaration  
{
    // get and set accessors  
}  
```

Cet indexeur portera le nom `TheItem`. Si vous ne précisez pas le nom de l’attribut, `Item` est utilisé comme nom par défaut.  
  
## <a name="example-1"></a>Exemple 1  
  
L’exemple suivant montre comment déclarer un champ de tableau privé `temps`, et un indexeur. L’indexeur permet d’accéder directement à l’instance `tempRecord[i]`. Comme alternative à l’utilisation de l’indexeur, vous pouvez déclarer le tableau comme membre [public](../../language-reference/keywords/public.md) et accéder directement à ses membres, `tempRecord.temps[i]`.  
  
 Notez que quand l’accès à un indexeur est évalué, par exemple dans une instruction `Console.Write`, l’accesseur [get](../../language-reference/keywords/get.md) est appelé. C’est pourquoi une erreur de compilation se produit s’il n’existe aucun accesseur `get`.  
  
 [!code-csharp[csProgGuideIndexers#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideIndexers/CS/Indexers.cs#1)]  
  
## <a name="indexing-using-other-values"></a>Indexation avec d’autres valeurs

C# ne limite pas le type de paramètre d’indexeur au type entier. Par exemple, il peut être utile d’utiliser une chaîne avec un indexeur. Il est possible d’implémenter un tel indexeur en recherchant la chaîne dans la collection et en retournant la valeur appropriée. Comme les accesseurs peuvent être surchargés, les versions chaîne et entier peuvent coexister.  
  
## <a name="example-2"></a>Exemple 2  
  
L’exemple suivant déclare une classe qui stocke les jours de la semaine. Un accesseur `get` prend une chaîne, le nom d’un jour, et retourne l’entier correspondant. Par exemple, « Sunday » retourne 0, « Monday » retourne 1 et ainsi de suite.  
  
 [!code-csharp[csProgGuideIndexers#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideIndexers/CS/Indexers.cs#2)]  
  
## <a name="robust-programming"></a>Programmation fiable

 La sécurité et la fiabilité des indexeurs peuvent être améliorées de deux manières principales :  
  
- N’oubliez pas d’incorporer une stratégie de gestion des erreurs au cas où le code client passerait une valeur d’index non valide. Dans le premier exemple décrit plus haut dans cette rubrique, la classe TempRecord fournit une propriété Length qui permet au code client de vérifier l’entrée avant de la passer à l’indexeur. Vous pouvez également placer le code de gestion des erreurs à l’intérieur de l’indexeur lui-même. N’oubliez pas d’indiquer aux utilisateurs toutes les exceptions que vous levez dans un accesseur d’indexeur.  
  
- Définissez pour les accesseurs [get](../../language-reference/keywords/get.md) et [set](../../language-reference/keywords/set.md) une accessibilité aussi restrictive que possible. Cela est particulièrement important dans le cas de l’accesseur `set`. Pour plus d’informations, consultez [Restriction d’accessibilité de l’accesseur](../classes-and-structs/restricting-accessor-accessibility.md).  
  
## <a name="see-also"></a>Voir aussi

- [Guide de programmation C#](../index.md)
- [Indexeurs](./index.md)
- [Propriétés](../classes-and-structs/properties.md)
