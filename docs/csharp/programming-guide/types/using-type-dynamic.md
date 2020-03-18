---
title: Utilisation du type dynamic - Guide de programmation C#
ms.date: 07/20/2015
helpviewer_keywords:
- dynamic [C#], about dynamic type
- dynamic type [C#]
ms.assetid: 3828989d-c967-4a51-b948-857ebc8fdf26
ms.openlocfilehash: c5ac5b3692266010f0be8672ef744baaa32e6a03
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75711855"
---
# <a name="using-type-dynamic-c-programming-guide"></a>Utilisation du type dynamic (Guide de programmation C#)

C# 4 introduit un nouveau type, `dynamic`. Il s’agit d’un type statique ; toutefois, un objet de type `dynamic` ignore la vérification des types statiques. Dans la plupart des cas, il fonctionne comme s’il était de type `object`. Au moment de la compilation, un élément de type `dynamic` est supposé prendre en charge n’importe quelle opération. Par conséquent, vous n’avez pas besoin de vous demander si l’objet obtient sa valeur d’une API COM, d’un langage dynamique tel qu’IronPython, du modèle DOM (Document Object Model) HTML, de la réflexion ou d’une autre partie du programme. Toutefois, si le code n’est pas valide, des erreurs sont détectées au moment de l’exécution.

Par exemple, si la méthode d’instance `exampleMethod1` du code suivant ne comporte qu’un seul paramètre, le compilateur reconnaît que le premier appel à la méthode, `ec.exampleMethod1(10, 4)`, n’est pas valide car il contient deux arguments. Cet appel entraîne une erreur du compilateur. Le deuxième appel à la méthode, `dynamic_ec.exampleMethod1(10, 4)`, n’est pas vérifié par le compilateur, car le type de `dynamic_ec` est `dynamic`. Par conséquent, aucune erreur de compilateur n’est signalée. Toutefois, l’erreur ne passe pas indéfiniment inaperçue. Elle est détectée au moment de l’exécution et provoque une exception runtime.

[!code-csharp[CsProgGuideTypes#50](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/usingdynamic.cs#50)]

[!code-csharp[CsProgGuideTypes#56](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/usingdynamic.cs#56)]

Dans ces exemples, le rôle du compilateur consiste à regrouper les informations relatives à l’opération que chaque instruction propose d’exécuter sur l’objet ou l’expression de type `dynamic`. Au moment de l’exécution, les informations stockées sont examinées, et toute instruction non valide provoque une exception runtime.

Le résultat de la plupart des opérations dynamiques est lui-même de type `dynamic`. Par exemple, si vous placez le pointeur de la souris sur `testSum` dans l’exemple suivant, IntelliSense affiche le type **(variable locale) dynamic testSum**.

[!code-csharp[CsProgGuideTypes#51](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/usingdynamic.cs#51)]

Les opérations dans lesquelles le résultat n’est pas `dynamic` incluent :

* Les conversions de `dynamic` vers un autre type.
* Les appels de constructeur qui incluent des arguments de type `dynamic`.

Par exemple, le type de `testInstance` dans la déclaration suivante est `ExampleClass`, et non pas `dynamic` :

[!code-csharp[CsProgGuideTypes#52](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/usingdynamic.cs#52)]

Des exemples de conversion sont présentés dans la section suivante, "Conversions".

## <a name="conversions"></a>Conversions

Les conversions entre des objets dynamiques et d’autres types sont faciles à exécuter. Les développeurs peuvent ainsi passer du comportement dynamique au comportement non dynamique, et vice versa.

Tout objet peut être converti implicitement en type dynamique, comme illustré dans les exemples suivants.

[!code-csharp[CsProgGuideTypes#53](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/usingdynamic.cs#53)]

Inversement, une conversion implicite peut être appliquée de façon dynamique à toute expression de type `dynamic`.

[!code-csharp[CsProgGuideTypes#54](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/usingdynamic.cs#54)]

## <a name="overload-resolution-with-arguments-of-type-dynamic"></a>Résolution de surcharge avec des arguments de type dynamic

La résolution de surcharge a lieu au moment de l’exécution, et non pas au moment de la compilation, si un ou plusieurs arguments d’un appel de méthode sont de type `dynamic`, ou si le récepteur de l’appel de méthode est de type `dynamic`. Dans l’exemple suivant, si la seule méthode `exampleMethod2` accessible est définie pour accepter un argument de chaîne, l’envoi de `d1` en tant qu’argument n’entraîne pas d’erreur du compilateur, mais provoque une exception runtime. La résolution de surcharge échoue au moment de l’exécution car le type de `d1` est `int`, et `exampleMethod2` exige une chaîne.

[!code-csharp[CsProgGuideTypes#55](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/usingdynamic.cs#55)]

## <a name="dynamic-language-runtime"></a>Dynamic Language Runtime

Le composant Dynamic Language Runtime (DLR) est une nouvelle API de .NET Framework 4. Il fournit l’infrastructure qui prend en charge le type `dynamic` en C#, ainsi que l’implémentation des langages de programmation dynamique tels qu’IronPython et IronRuby. Pour plus d’informations sur le DLR, consultez [Vue d’ensemble du Dynamic Language Runtime](../../../framework/reflection-and-codedom/dynamic-language-runtime-overview.md).

## <a name="com-interop"></a>COM interop

C# 4 inclut plusieurs fonctionnalités qui améliorent l’interopérabilité avec les API COM telles que les API Office Automation. L’utilisation du type `dynamic` et des [arguments nommés et facultatifs](../classes-and-structs/named-and-optional-arguments.md) fait partie des améliorations offertes.

De nombreuses méthodes COM autorisent une variation des types d’arguments et du type de retour en désignant les types comme `object`. Cela a nécessité un cast explicite des valeurs pour la coordination avec les variables fortement typées en C#. Si vous compilez en utilisant [l’option -lien (Options compilateurs C),](../../language-reference/compiler-options/link-compiler-option.md) l’introduction du `dynamic` type vous permet de traiter les occurrences des `object` signatures COM comme s’ils étaient de type, `dynamic`et ainsi d’éviter une grande partie du casting. Par exemple, les instructions suivantes permettent de comparer la façon dont vous accédez à une cellule d’une feuille de calcul Microsoft Office Excel avec le type `dynamic` et sans le type `dynamic`.

[!code-csharp[csOfficeWalkthrough#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csofficewalkthrough/cs/thisaddin.cs#12)]

[!code-csharp[csOfficeWalkthrough#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csofficewalkthrough/cs/thisaddin.cs#13)]

## <a name="related-topics"></a>Rubriques connexes

|Intitulé|Description|
|-----------|-----------------|
|[Dynamique](../../language-reference/builtin-types/reference-types.md)|Décrit l’utilisation du mot clé `dynamic`.|
|[Aperçu dynamique du temps d’exécution du langage](../../../framework/reflection-and-codedom/dynamic-language-runtime-overview.md)|Fournit une vue d’ensemble du DLR, qui est un environnement d’exécution ajoutant au Common Language Runtime (CLR) un ensemble de services pour les langages dynamiques.|
|[Procédure pas à pas : Création et utilisation d’objets dynamiques](walkthrough-creating-and-using-dynamic-objects.md)|Fournit des instructions pas à pas pour la création d’un objet dynamique personnalisé et pour la création d’un projet qui accède à une bibliothèque `IronPython`.|
|[Comment accéder aux objets Office Interop à l’aide des fonctionnalités C#](../interop/how-to-access-office-onterop-objects.md)|Montre comment créer un projet qui utilise les arguments nommés et facultatifs, le type `dynamic` et d’autres améliorations qui simplifient l’accès aux objets d’API Office.|
