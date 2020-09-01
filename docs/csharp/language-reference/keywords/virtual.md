---
description: virtual - Référence C#
title: virtual - Référence C#
ms.date: 07/20/2015
f1_keywords:
- virtual_CSharpKeyword
- virtual
helpviewer_keywords:
- virtual keyword [C#]
ms.assetid: 5da9abae-bc1e-434f-8bea-3601b8dcb3b2
ms.openlocfilehash: 67bdfcf27bb108ca85e94ba7fdce208e4cd83b80
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89141723"
---
# <a name="virtual-c-reference"></a>virtual (référence C#)

Le mot clé `virtual` sert à modifier une méthode, une propriété, un indexeur ou une déclaration event et leur permet d’être substitués dans une classe dérivée. Par exemple, cette méthode peut être substituée par toute classe qui en hérite :

```csharp
public virtual double Area()
{
    return x * y;
}
```

L’implémentation d’un membre virtuel peut être modifiée par un [membre de substitution](override.md) dans une classe dérivée. Pour plus d’informations sur l’utilisation du `virtual` mot clé, consultez contrôle [de version avec les mots clés override et New](../../programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md) et [savoir quand utiliser les mots clés override et New](../../programming-guide/classes-and-structs/knowing-when-to-use-override-and-new-keywords.md).

## <a name="remarks"></a>Remarques

Quand une méthode virtuelle est appelée, un membre de substitution est recherché dans le type d’objet au moment de l’exécution. Le membre de substitution de la classe la plus dérivée est appelé (cela peut être le membre d’origine), si aucune classe dérivée n’a substitué le membre.

Par défaut, les méthodes ne sont pas virtuelles. Vous ne pouvez pas substituer une méthode non virtuelle.

Vous ne pouvez pas utiliser le modificateur `virtual` avec les modificateurs `static`, `abstract`, `private` ou `override`. L’exemple suivant illustre une propriété virtuelle :

[!code-csharp[csrefKeywordsModifiers#26](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#26)]

Les propriétés virtuelles se comportent comme des méthodes virtuelles, à l’exception des différences dans la syntaxe de déclaration et d’appel.

- L’utilisation du modificateur `virtual` sur une propriété statique serait une erreur.

- Une propriété virtuelle héritée peut être substituée dans une classe dérivée en incluant une déclaration de propriété qui utilise le modificateur `override`.

## <a name="example"></a>Exemple

Dans cet exemple, la classe `Shape` contient les deux coordonnées `x` et `y`, ainsi que la méthode virtuelle `Area()`. Différentes classes de formes, telles que `Circle`, `Cylinder` et `Sphere`, héritent de la classe `Shape`, et la surface est calculée pour chaque figure. Chaque classe dérivée a sa propre implémentation de substitution de `Area()`.

Notez que les classes héritées `Circle`, `Sphere` et `Cylinder` utilisent toutes des constructeurs qui initialisent la classe de base, comme indiqué dans la déclaration suivante.

```csharp
public Cylinder(double r, double h): base(r, h) {}
```

Le programme suivant calcule et affiche la zone appropriée pour chaque figure en appelant l’implémentation appropriée de la méthode `Area()`, selon l’objet associé à la méthode.

[!code-csharp[csrefKeywordsModifiers#23](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#23)]

## <a name="c-language-specification"></a>spécification du langage C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Voir aussi

- [Polymorphisme](../../programming-guide/classes-and-structs/polymorphism.md)
- [abstraction](abstract.md)
- [remplacer](override.md)
- [new (modificateur)](new-modifier.md)
