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
ms.openlocfilehash: b888ef73d1678fd37c984e4bb223f24e5b65d2cc
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90540717"
---
# <a name="xsubclass-directive"></a>x:Subclass, directive

Modifie le comportement de compilation du balisage XAML lorsque `x:Class` est également fourni. Au lieu de créer une classe partielle basée sur `x:Class` , le fourni `x:Class` est créé en tant que classe intermédiaire, puis votre classe dérivée fournie est supposée reposer sur `x:Class` .

## <a name="xaml-attribute-usage"></a>Utilisation d'attributs XAML

```xaml
<object x:Class="namespace.classname" x:Subclass="subclassNamespace.subclassName">
   ...
</object>
```

## <a name="xaml-values"></a>Valeurs XAML

|||
|-|-|
|`namespace`|Optionnel. Spécifie un espace de noms CLR qui contient `classname` . Si `namespace` est spécifié, un point (.) sépare `namespace` et `classname` .|
|`classname`|Obligatoire. Spécifie le nom CLR de la classe partielle qui connecte le XAML chargé et votre code-behind pour ce XAML. Consultez la section Notes.|
|`subclassNamespace`|Optionnel. Peut être différent de `namespace` si chaque espace de noms peut résoudre l’autre. Spécifie un espace de noms CLR qui contient `subclassName` . Si `subclassName` est spécifié, un point (.) sépare `subclassNamespace` et `subclassName` .|
|`subclassName`|Obligatoire. Spécifie le nom CLR de la sous-classe.|

## <a name="dependencies"></a>Les dépendances

la [directive x :Class](xclass-directive.md) doit également être fournie sur le même objet, et cet objet doit être l’élément racine de la production XAML.

## <a name="remarks"></a>Notes

`x:Subclass` l’utilisation est principalement prévue pour les langages qui ne prennent pas en charge les déclarations de classe partielles.

La classe utilisée en tant que `x:Subclass` ne peut pas être une classe imbriquée et `x:Subclass` doit faire référence à l’objet racine comme expliqué dans la section « dépendances ».

Dans le cas contraire, la signification conceptuelle de `x:Subclass` est non définie par une implémentation des services XAML .net. Cela est dû au fait que le comportement des services XAML .NET ne spécifie pas le modèle de programmation global par lequel le balisage XAML et le code de stockage sont connectés. Les implémentations d’autres concepts liés à `x:Class` et `x:Subclass` sont effectuées par des frameworks spécifiques qui utilisent des modèles de programmation ou des modèles d’application pour définir comment connecter le balisage XAML, le balisage compilé et le code-behind basé sur CLR. Chaque infrastructure peut avoir ses propres actions de génération qui activent une partie du comportement, ou des composants spécifiques qui doivent être inclus dans l’environnement de génération. Dans une infrastructure, les actions de génération peuvent également varier en fonction du langage CLR spécifique utilisé pour le code-behind.

## <a name="wpf-usage-notes"></a>Remarques sur l'utilisation de WPF

`x:Subclass` peut se trouver à la racine d’une page ou à la <xref:System.Windows.Application> racine dans la définition de l’application, qui a déjà `x:Class` . La Déclaration `x:Subclass` sur un élément autre qu’une racine de page ou d’application, ou la spécification d’un élément qui n' `x:Class` existe pas, provoque une erreur au moment de la compilation.

La création de classes dérivées qui fonctionnent correctement pour le `x:Subclass` scénario est assez complexe. Vous devrez peut-être examiner les fichiers intermédiaires (les fichiers. g produits dans le dossier obj de votre projet par compilation de balisage, avec les noms qui incorporent les noms de fichiers. Xaml). Ces fichiers intermédiaires peuvent vous aider à déterminer l’origine de certaines constructions de programmation dans les classes partielles jointes dans l’application compilée.

Les gestionnaires d’événements dans la classe dérivée doivent être `internal override` ( `Friend Overrides` dans Microsoft Visual Basic) pour substituer les stubs des gestionnaires tels qu’ils ont été créés dans la classe intermédiaire pendant la compilation. Sinon, les implémentations de classe dérivée masquent (occultent) l’implémentation de classe intermédiaire et les gestionnaires de classe intermédiaire ne sont pas appelés.

Lorsque vous définissez à `x:Class` la fois et `x:Subclass` , vous n’avez pas besoin de fournir une implémentation pour la classe qui est référencée par `x:Class` . Il vous suffit de lui attribuer un nom via l' `x:Class` attribut afin que le compilateur dispose de conseils pour la classe qu’il crée dans les fichiers intermédiaires (le compilateur ne sélectionne pas de nom par défaut dans ce cas). Vous pouvez attribuer `x:Class` une implémentation à la classe ; Toutefois, il ne s’agit pas du scénario classique d’utilisation de `x:Class` et de `x:Subclass` .

## <a name="see-also"></a>Voir aussi

- [x:Class, directive](xclass-directive.md)
- [XAML et classes personnalisées pour WPF](/dotnet/desktop/wpf/advanced/xaml-and-custom-classes-for-wpf)
