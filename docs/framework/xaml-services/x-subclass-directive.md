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
ms.openlocfilehash: f6f02998a7648693bd731d6b2afdfd4499abaa04
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053908"
---
# <a name="xsubclass-directive"></a>x:Subclass, directive
Modifie le comportement de compilation du balisage XAML lorsque `x:Class` est également fourni. Au lieu de créer une classe partielle basée sur `x:Class`, le fourni `x:Class` est créé en tant que classe intermédiaire, puis votre classe dérivée fournie est supposée reposer sur `x:Class`.  
  
## <a name="xaml-attribute-usage"></a>Utilisation d'attributs XAML  
  
```xaml  
<object x:Class="namespace.classname" x:Subclass="subclassNamespace.subclassName">  
   ...  
</object>  
```  
  
## <a name="xaml-values"></a>Valeurs XAML  
  
|||  
|-|-|  
|`namespace`|facultatif. Spécifie un espace de noms `classname`CLR qui contient. Si `namespace` est spécifié, un point (.) `namespace` sépare et `classname`.|  
|`classname`|Requis. Spécifie le nom CLR de la classe partielle qui connecte le XAML chargé et votre code-behind pour ce XAML. Consultez la section Notes.|  
|`subclassNamespace`|facultatif. Peut être différent de `namespace` si chaque espace de noms peut résoudre l’autre. Spécifie un espace de noms `subclassName`CLR qui contient. Si `subclassName` est spécifié, un point (.) `subclassNamespace` sépare et `subclassName`.|  
|`subclassName`|Requis. Spécifie le nom CLR de la sous-classe.|  
  
## <a name="dependencies"></a>Dépendances  
 la [directive x :Class](x-class-directive.md) doit également être fournie sur le même objet, et cet objet doit être l’élément racine de la production XAML.  
  
## <a name="remarks"></a>Notes  
 `x:Subclass`l’utilisation est principalement prévue pour les langages qui ne prennent pas en charge les déclarations de classe partielles.  
  
 La classe utilisée en tant `x:Subclass` que ne peut pas être une classe imbriquée et `x:Subclass` doit faire référence à l’objet racine comme expliqué dans la section « dépendances ».  
  
 Dans le cas contraire, la `x:Subclass` signification conceptuelle de est non définie par une .NET Framework implémentation des services XAML. Cela est dû au fait que .NET Framework comportement des services XAML ne spécifie pas le modèle de programmation global par lequel le balisage XAML et le code de stockage sont connectés. Les implémentations d’autres concepts liés `x:Class` à `x:Subclass` et sont effectuées par des frameworks spécifiques qui utilisent des modèles de programmation ou des modèles d’application pour définir comment connecter le balisage XAML, le balisage compilé et le code-behind basé sur CLR. Chaque infrastructure peut avoir ses propres actions de génération qui activent une partie du comportement, ou des composants spécifiques qui doivent être inclus dans l’environnement de génération. Dans une infrastructure, les actions de génération peuvent également varier en fonction du langage CLR spécifique utilisé pour le code-behind.  
  
## <a name="wpf-usage-notes"></a>Remarques sur l’utilisation de WPF  
 `x:Subclass`peut se trouver à la racine d’une page <xref:System.Windows.Application> ou à la racine dans la définition de l' `x:Class`application, qui a déjà. La Déclaration `x:Class` sur un élément autre qu’une racine de page ou d’application, ou la spécification d’un élément qui n’existe pas, provoque une erreur au moment de la compilation. `x:Subclass`  
  
 La création de classes dérivées qui fonctionnent `x:Subclass` correctement pour le scénario est assez complexe. Vous devrez peut-être examiner les fichiers intermédiaires (les fichiers. g produits dans le dossier obj de votre projet par compilation de balisage, avec les noms qui incorporent les noms de fichiers. Xaml). Ces fichiers intermédiaires peuvent vous aider à déterminer l’origine de certaines constructions de programmation dans les classes partielles jointes dans l’application compilée.  
  
 Les gestionnaires d’événements dans la classe dérivée `internal override` doivent`Friend Overrides` être (dans Microsoft Visual Basic) pour substituer les stubs des gestionnaires tels qu’ils ont été créés dans la classe intermédiaire pendant la compilation. Sinon, les implémentations de classe dérivée masquent (occultent) l’implémentation de classe intermédiaire et les gestionnaires de classe intermédiaire ne sont pas appelés.  
  
 Lorsque vous définissez à `x:Class` la `x:Subclass`fois et, vous n’avez pas besoin de fournir une implémentation pour la classe qui est `x:Class`référencée par. Il vous suffit de lui attribuer un nom via l' `x:Class` attribut afin que le compilateur dispose de conseils pour la classe qu’il crée dans les fichiers intermédiaires (le compilateur ne sélectionne pas de nom par défaut dans ce cas). Vous pouvez attribuer une `x:Class` implémentation `x:Class` à la classe ; Toutefois, il ne s’agit pas du scénario classique d' `x:Subclass`utilisation de et de.  
  
## <a name="see-also"></a>Voir aussi

- [x:Class, directive](x-class-directive.md)
- [XAML et classes personnalisées pour WPF](../wpf/advanced/xaml-and-custom-classes-for-wpf.md)
