---
title: Génériques en .NET
description: En savoir plus sur les génériques dans .NET. Définissez & utiliser des génériques, Découvrez leurs avantages & les inconvénients, Découvrez la prise en charge des langages & de la bibliothèque de classes, et bien plus encore.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- generic methods, type inference
- generics [.NET], collections
- generic interfaces [.NET]
- constructed generic types
- nested generic types
- generic type definitions
- generic classes [.NET]
- generics [.NET], interfaces
- generics [.NET], about
- generics [.NET]
- generic collections [.NET]
- generic delegates [.NET]
- generic type arguments
- generics [.NET], delegates
- generics [.NET], features
- constraints [.NET]
- generic types
- generic type parameters
ms.assetid: 2994d786-c5c7-4666-ab23-4c83129fe39c
ms.openlocfilehash: f361e0e250368694d7afa078183b1e5cb7ef1464
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95707865"
---
# <a name="generics-in-net"></a>Génériques en .NET

Les génériques vous permettent d'adapter une méthode, une classe ou une structure au type de données sur lequel elle agit. Par exemple, au lieu d’utiliser la <xref:System.Collections.Hashtable> classe, qui autorise les clés et les valeurs de n’importe quel type, vous pouvez utiliser la <xref:System.Collections.Generic.Dictionary%602> classe générique et spécifier les types autorisés pour la clé et la valeur. Les génériques présentent plusieurs avantages, notamment une plus grande réutilisabilité du code et une meilleure cohérence des types.  

## <a name="defining-and-using-generics"></a>Définition et utilisation des génériques

 Les génériques sont des classes, des structures, des interfaces et des méthodes qui possèdent des espaces réservés (ou paramètres de type) pour un ou plusieurs des types qu'ils stockent ou utilisent. Une classe de collection générique peut utiliser un paramètre de type comme espace réservé pour le type des objets qu'elle stocke. Les paramètres de type apparaissent alors comme les types de ses champs, et les types de paramètre, comme ses méthodes. Une méthode générique peut utiliser son paramètre de type comme le type de sa valeur de retour ou comme le type de l'un de ses paramètres formels. Le code suivant montre une définition de classe générique simple.  
  
 [!code-cpp[Conceptual.Generics.Overview#2](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.generics.overview/cpp/source.cpp#2)]
 [!code-csharp[Conceptual.Generics.Overview#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.generics.overview/cs/source.cs#2)]
 [!code-vb[Conceptual.Generics.Overview#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.generics.overview/vb/source.vb#2)]  
  
 Quand vous créez une instance de classe générique, vous spécifiez les types à substituer aux paramètres de type. Cela crée une nouvelle classe générique, appelée classe générique construite, avec les types substitués là où s'affichent les paramètres de type. Le résultat est une classe de type sécurisé adaptée à votre choix de types, comme le montre le code suivant.  
  
 [!code-cpp[Conceptual.Generics.Overview#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.generics.overview/cpp/source.cpp#3)]
 [!code-csharp[Conceptual.Generics.Overview#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.generics.overview/cs/source.cs#3)]
 [!code-vb[Conceptual.Generics.Overview#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.generics.overview/vb/source.vb#3)]  

### <a name="generics-terminology"></a>Terminologie relative aux génériques  

 Les termes suivants sont employés quand on aborde le sujet des génériques de .NET :  
  
- Une *définition de type générique* est une déclaration de classe, de structure ou d'interface qui fonctionne comme un modèle, avec des espaces réservés pour les types qu'elle peut contenir ou utiliser. Par exemple, la classe <xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWithType> peut contenir deux types : des clés et des valeurs. Étant donné qu'une définition de type générique n'est qu'un modèle, vous ne pouvez pas créer d'instances d'une classe, d'une structure ou d'une interface qui correspond à une définition de type générique.  
  
- Les *paramètres de type générique*, ou *paramètres de type*, sont des espaces réservés compris dans une définition de type ou de méthode générique. Le type générique <xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWithType> possède deux paramètres de type, `TKey` et `TValue`, qui représentent les types de ses clés et de ses valeurs.  
  
- Un *type générique construit*, ou *type construit*, est le résultat de la spécification de types pour les paramètres de type générique d'une définition de type générique.  
  
- Un *argument de type générique* correspond à tout type substitué par un paramètre de type générique.  
  
- Le terme général *type générique* correspond à la fois aux types construits et aux définitions de type générique.  
  
- La *covariance* et la *contravariance* des paramètres de type générique permettent d'utiliser des types génériques construits dont les arguments de type sont plus dérivés (covariance) ou moins dérivés (contravariance) qu'un type construit cible. La covariance et la contravariance sont désignées collectivement sous le nom de *variation*. Pour plus d’informations, consultez [Covariance et contravariance](covariance-and-contravariance.md).  
  
- Les *contraintes* sont des limites appliquées aux paramètres de type générique. Par exemple, vous pouvez limiter un paramètre de type aux types qui implémentent l'interface générique <xref:System.Collections.Generic.IComparer%601?displayProperty=nameWithType> afin que les instances de ce type puissent être classées. Vous pouvez également limiter les paramètres de type à des types qui ont une classe de base particulière, qui ont un constructeur sans paramètre, ou qui sont des types référence ou des types valeur. Les utilisateurs du type générique ne peuvent pas remplacer les arguments de type qui ne respectent pas les contraintes.  
  
- Une *définition de méthode générique* est une méthode qui comporte deux listes de paramètres : une liste de paramètres de type générique et une liste de paramètres formels. Les paramètres de type peuvent apparaître comme le type de retour ou comme les types des paramètres formels, comme le montre le code suivant.  
  
 [!code-cpp[Conceptual.Generics.Overview#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.generics.overview/cpp/source.cpp#4)]
 [!code-csharp[Conceptual.Generics.Overview#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.generics.overview/cs/source.cs#4)]
 [!code-vb[Conceptual.Generics.Overview#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.generics.overview/vb/source.vb#4)]  
  
 Les méthodes génériques peuvent appartenir à des types génériques ou non génériques. Il est important de noter qu'une méthode n'est pas générique simplement parce qu'elle appartient à un type générique, ou encore parce qu'elle a des paramètres formels dont les types sont les paramètres génériques du type englobant. Une méthode est générique uniquement si elle possède sa propre liste de paramètres de type. Dans le code suivant, seule la méthode `G` est générique.  
  
 [!code-cpp[Conceptual.Generics.Overview#5](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.generics.overview/cpp/source.cpp#5)]
 [!code-csharp[Conceptual.Generics.Overview#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.generics.overview/cs/source.cs#5)]
 [!code-vb[Conceptual.Generics.Overview#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.generics.overview/vb/source.vb#5)]  
  
## <a name="advantages-and-disadvantages-of-generics"></a>Avantages et inconvénients des génériques

 Il existe de nombreux avantages à l'utilisation de collections et de délégués génériques :  
  
- Sécurité de type. Grâce aux génériques, le compilateur se charge de la cohérence des types à votre place. Il est inutile d'écrire du code pour tester le type de données nécessaire, car il est appliqué au moment de la compilation. Ainsi, le besoin d'un cast de type et le risque d'erreurs au moment de l'exécution sont réduits.  
  
- Moins de code est nécessaire et il est plus facile de le réutiliser. Il n'est pas nécessaire d'hériter d'un type de base et de substituer des membres. Par exemple, <xref:System.Collections.Generic.LinkedList%601> peut être utilisé immédiatement. Vous pouvez créer une liste liée de chaînes à l'aide de la déclaration de variable suivante :  
  
     [!code-cpp[HowToGeneric#24](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/source2.cpp#24)]
     [!code-csharp[HowToGeneric#24](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/source2.cs#24)]
     [!code-vb[HowToGeneric#24](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/source2.vb#24)]  
  
- Performances améliorées. Les types de collections génériques sont généralement plus efficaces pour le stockage et la manipulation des types valeur, car ceux-ci ne nécessitent pas de boxing.  
  
- Les délégués génériques permettent d'effectuer des rappels de type sécurisé sans avoir à créer plusieurs classes déléguées. Par exemple, le délégué générique <xref:System.Predicate%601> permet de créer une méthode qui implémente vos propres critères de recherche pour un type particulier et d'utiliser votre méthode avec les méthodes du type <xref:System.Array> telles que <xref:System.Array.Find%2A>, <xref:System.Array.FindLast%2A>et <xref:System.Array.FindAll%2A>.  
  
- Les génériques simplifient le code généré dynamiquement. Quand vous utilisez des génériques avec du code généré dynamiquement, vous n'avez pas besoin de générer le type. Cela permet d'augmenter le nombre de scénarios dans lesquels vous pouvez utiliser des méthodes dynamiques légères au lieu de générer des assemblys entiers. Pour plus d'informations, consultez [Guide pratique pour définir et exécuter des méthodes dynamiques](../../framework/reflection-and-codedom/how-to-define-and-execute-dynamic-methods.md) et <xref:System.Reflection.Emit.DynamicMethod>.  
  
 Voici quelques-unes des limitations des génériques :  
  
- Les types génériques peuvent être dérivés de la plupart des classes de base, telles que <xref:System.MarshalByRefObject> (et les contraintes peuvent être utilisées pour exiger que les paramètres de type générique dérivent de classes de base comme <xref:System.MarshalByRefObject>). Toutefois, .NET ne prend pas en charge les types génériques liés au contexte. Un type générique peut être dérivé de <xref:System.ContextBoundObject>. Toutefois, si vous tentez de créer une instance de ce type, une exception <xref:System.TypeLoadException>sera levée.  
  
- Les énumérations ne peuvent pas avoir de paramètres de type générique. Une énumération ne peut être générique que de manière secondaire (par exemple, parce qu'elle est imbriquée dans un type générique qui est défini à l'aide de Visual Basic, C# ou C++). Pour plus d’informations, consultez la section "Énumérations" dans [Common Type System](../base-types/common-type-system.md).  
  
- Les méthodes dynamiques légères ne peuvent pas être génériques.  
  
- Dans Visual Basic, C# et C++, un type imbriqué qui est inclus dans un type générique ne peut pas être instancié, à moins que des types aient été assignés aux paramètres de type de tous les types englobants. En d'autres termes, un type imbriqué défini à l'aide de ces langages comprend les paramètres de type de tous ses types englobants. Ainsi, les paramètres de type des types englobants peuvent être utilisés dans les définitions de membres d'un type imbriqué. Pour plus d'informations, consultez "Types imbriqués" dans <xref:System.Type.MakeGenericType%2A>.  
  
    > [!NOTE]
    > Un type imbriqué qui est défini par émission de code dans un assembly dynamique ou avec [Ilasm.exe (IL Assembler)](../../framework/tools/ilasm-exe-il-assembler.md) n’a pas besoin d’inclure les paramètres de type de ses types englobants. Toutefois, s’il ne les inclut pas, les paramètres de type ne seront pas dans la portée de la classe imbriquée.  
  
     Pour plus d'informations, consultez "Types imbriqués" dans <xref:System.Type.MakeGenericType%2A>.  

## <a name="class-library-and-language-support"></a>Bibliothèque de classes et prise en charge des langages  

 .NET fournit plusieurs classes de collection génériques dans les espaces de noms suivants :  
  
- L'espace de noms <xref:System.Collections.Generic> contient la plupart des types de collections génériques fournis par .NET, comme les classes génériques <xref:System.Collections.Generic.List%601> et <xref:System.Collections.Generic.Dictionary%602>.  
  
- L'espace de noms <xref:System.Collections.ObjectModel> contient d’autres types de collections génériques, tels que la classe générique <xref:System.Collections.ObjectModel.ReadOnlyCollection%601>, qui sont utiles pour exposer des modèles objet aux utilisateurs de vos classes.  
  
 Les interfaces génériques qui servent à l'implémentation des comparaisons d'égalité et de tri sont fournies dans l'espace de noms <xref:System> , en même temps que les types délégués génériques pour les gestionnaires d'événements, les conversions et les prédicats de recherche.  
  
 La prise en charge des génériques a été ajoutée à l'espace de noms <xref:System.Reflection> pour l'examen des types et des méthodes génériques, à <xref:System.Reflection.Emit> pour l'émission d'assemblys dynamiques qui contiennent des types et des méthodes génériques, et à <xref:System.CodeDom> pour la génération de graphiques source comprenant des génériques.  
  
 Le Common Language Runtime fournit de nouveaux codes d'opérations et préfixes pour la prise en charge des types génériques dans le langage MSIL (Microsoft Intermediate Language), notamment <xref:System.Reflection.Emit.OpCodes.Stelem>, <xref:System.Reflection.Emit.OpCodes.Ldelem>, <xref:System.Reflection.Emit.OpCodes.Unbox_Any>, <xref:System.Reflection.Emit.OpCodes.Constrained>et <xref:System.Reflection.Emit.OpCodes.Readonly>.  
  
 Visual C++, C# et Visual Basic fournissent une prise en charge complète de la définition et de l'utilisation des génériques. Pour plus d'informations sur la prise en charge des langages, consultez [Types génériques en Visual Basic](../../visual-basic/programming-guide/language-features/data-types/generic-types.md), [Introduction aux génériques](../../csharp/programming-guide/generics/index.md) et [Vue d'ensemble des génériques dans Visual C++](/cpp/windows/overview-of-generics-in-visual-cpp).

## <a name="nested-types-and-generics"></a>Types imbriqués et génériques  

 Un type qui est imbriqué dans un type générique peut dépendre des paramètres de type du type générique englobant. Le Common Language Runtime considère que les types imbriqués sont génériques, même s'ils n'ont pas leurs propres paramètres de type générique. Lorsque vous créez une instance d'un type imbriqué, vous devez spécifier les arguments de type pour tous les types génériques englobants.  

## <a name="related-topics"></a>Rubriques connexes  
  
|Titre|Description|  
|-----------|-----------------|  
|[Collections génériques dans .NET](collections.md)|Aborde les classes de collection générique et d’autres types génériques de .NET.|  
|[Délégués génériques pour la manipulation de tableaux et de listes](delegates-for-manipulating-arrays-and-lists.md)|Aborde les délégués génériques pour les conversions, les prédicats de recherche et les actions à effectuer sur les éléments d'un tableau ou d'une collection.|  
|[Interfaces génériques](interfaces.md)|Traite des interfaces génériques qui fournissent des fonctionnalités communes à plusieurs familles de types génériques.|  
|[Covariance et contravariance](covariance-and-contravariance.md)|Aborde la covariance et la contravariance dans les paramètres de type générique.|  
|[Types de collections couramment utilisés](../collections/commonly-used-collection-types.md)|Fournit des informations récapitulatives sur les caractéristiques et les scénarios d’utilisation des types de collections de .NET, notamment les types génériques.|  
|[Quand utiliser des collections génériques](../collections/when-to-use-generic-collections.md)|Traite des règles générales permettant de déterminer le moment auquel utiliser des types de collections génériques.|  
|[Procédure : définir un type générique avec l’émission de réflexion](../../framework/reflection-and-codedom/how-to-define-a-generic-type-with-reflection-emit.md)|Explique comment générer des assemblys dynamiques qui incluent des types et des méthodes génériques.|  
|[Generic Types in Visual Basic](../../visual-basic/programming-guide/language-features/data-types/generic-types.md)|Explique la fonction des génériques pour les utilisateurs de Visual Basic et fournit des procédures concernant l'utilisation et la définition des types génériques.|  
|[Introduction aux génériques](../../csharp/programming-guide/generics/index.md)|Fournit une vue d'ensemble de la définition et de l'utilisation des types génériques pour les utilisateurs de C#.|  
|[Vue d’ensemble des génériques dans Visual C++](/cpp/windows/overview-of-generics-in-visual-cpp)|Explique la fonction des génériques pour les utilisateurs C++, y compris les différences entre les génériques et les modèles.|  

## <a name="reference"></a>Informations de référence  

 <xref:System.Collections.Generic>  
  
 <xref:System.Collections.ObjectModel>  
  
 <xref:System.Reflection.Emit.OpCodes?displayProperty=nameWithType>  
