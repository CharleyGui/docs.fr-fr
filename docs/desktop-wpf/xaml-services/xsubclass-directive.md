---
title: x:Subclass, directive
ms.date: 03/30/2017
f1_keywords:
- Subclass
- xSubclass
- x:Subclass
helpviewer_keywords:
- x:Subclass attribute [XAML Services]
- XAML [XAML Services], x:Subclass attribute
- Subclass attribute in XAML [XAML Services]
ms.assetid: 99f66072-8107-4362-ab99-8171dc83b469
ms.openlocfilehash: e85e0fb5a0e1a865ed84a93767f8152a115bbe5f
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/27/2020
ms.locfileid: "82071366"
---
# <a name="xsubclass-directive"></a>x:Subclass, directive

Modifie le comportement de compilation de `x:Class` balisage XAML quand il est également fourni. Au lieu de créer une `x:Class`classe partielle `x:Class` qui est basée sur , le fourni est créé `x:Class`comme une classe intermédiaire, puis votre classe dérivée fournie devrait être basée sur .

## <a name="xaml-attribute-usage"></a>Utilisation d'attributs XAML

```xaml
<object x:Class="namespace.classname" x:Subclass="subclassNamespace.subclassName">
   ...
</object>
```

## <a name="xaml-values"></a>Valeurs XAML

|||
|-|-|
|`namespace`|facultatif. Spécifie un espace `classname`de nom CLR qui contient . Si `namespace` elle est spécifiée, un `namespace` `classname`point (.) sépare et .|
|`classname`|Obligatoire. Spécifie le nom CLR de la classe partielle qui relie le XAML chargé et votre code-derrière pour cela XAML. Consultez la section Notes.|
|`subclassNamespace`|facultatif. Peut être `namespace` différent de si chaque namespace peut résoudre l’autre. Spécifie un espace `subclassName`de nom CLR qui contient . Si `subclassName` elle est spécifiée, un `subclassNamespace` `subclassName`point (.) sépare et .|
|`subclassName`|Obligatoire. Spécifie le nom CLR de la sous-classe.|

## <a name="dependencies"></a>Les dépendances

[x:La directive de classe](xclass-directive.md) doit également être fournie sur le même objet, et cet objet doit être l’élément racine de la production XAML.

## <a name="remarks"></a>Notes

`x:Subclass`l’utilisation est principalement destinée aux langues qui ne prennent pas en charge les déclarations partielles de classe.

La classe utilisée `x:Subclass` comme la classe ne `x:Subclass` peut pas être une classe imbriquée, et doit se référer à l’objet racine comme expliqué dans la section "Dépendances".

Dans le cas `x:Subclass` contraire, le sens conceptuel de est indéfini par une mise en œuvre .NET XAML Services. C’est parce que le comportement .NET XAML Services ne spécifie pas le modèle de programmation global par lequel le balisage XAML et le code de sauvegarde sont connectés. Les implémentations `x:Class` `x:Subclass` d’autres concepts liés à des cadres spécifiques qui utilisent des modèles de programmation ou des modèles d’application pour définir comment relier la balisage XAML, la majoration compilée et le code-derrière. Chaque cadre peut avoir ses propres actions de construction qui permettent une partie du comportement, ou des composants spécifiques qui doivent être inclus dans l’environnement de construction. Dans un cadre, les actions de construction peuvent également varier en fonction du langage CLR spécifique qui est utilisé pour le code-derrière.

## <a name="wpf-usage-notes"></a>Remarques sur l'utilisation de WPF

`x:Subclass`peut être sur une racine <xref:System.Windows.Application> de page ou sur `x:Class`la racine dans la définition d’application, qui a déjà . Déclarer `x:Subclass` sur tout élément autre qu’une page ou une `x:Class` racine d’application, ou le spécifier là où il n’y en a pas, provoque une erreur de compilation.

Créer des classes dérivées `x:Subclass` qui fonctionnent correctement pour le scénario est assez complexe. Vous devrez peut-être examiner les fichiers intermédiaires (les fichiers .g produits dans le dossier obj de votre projet par balisage compiler, avec des noms qui intègrent les noms de fichiers .xaml). Ces fichiers intermédiaires peuvent vous aider à déterminer l’origine de certaines constructions de programmation dans les classes partielles jointes dans l’application compilée.

Les gestionnaires d’événements de `internal override` `Friend Overrides` la classe dérivée doivent être (dans Microsoft Visual Basic) afin de remplacer les talons pour les manutentionnaires tels qu’ils ont été créés dans la classe intermédiaire pendant la compilation. Dans le cas contraire, les implémentations de classe dérivées cachent (ombre) l’implémentation de classe intermédiaire et les gestionnaires de classe intermédiaire ne sont pas invoqués.

Lorsque vous `x:Class` définissez les deux et `x:Subclass`, vous n’avez pas `x:Class`besoin de fournir une implémentation pour la classe qui est référencé par . Vous n’avez qu’à `x:Class` lui donner un nom via l’attribut de sorte que le compilateur a quelques conseils pour la classe qu’il crée dans les fichiers intermédiaires (le compilateur ne sélectionne pas un nom par défaut dans ce cas). Vous pouvez `x:Class` donner à la classe une mise en œuvre; cependant, ce n’est pas `x:Class` le `x:Subclass`scénario typique pour l’utilisation des deux et .

## <a name="see-also"></a>Voir aussi

- [x:Class, directive](xclass-directive.md)
- [XAML et classes personnalisées pour WPF](../../framework/wpf/advanced/xaml-and-custom-classes-for-wpf.md)
