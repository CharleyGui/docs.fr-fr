---
title: Constructeurs d'instances - Guide de programmation C#
description: Les constructeurs d’instance en C# créent et initialisent toutes les variables de membre d’instance lorsque vous utilisez la nouvelle expression pour créer un objet d’une classe.
ms.date: 07/20/2015
helpviewer_keywords:
- constructors [C#], instance constructors
- instance constructors [C#]
ms.assetid: 24663779-c1e5-4af4-a942-ca554e4c542d
ms.openlocfilehash: d70e786446fb198afb4e0311757cacb65b706f47
ms.sourcegitcommit: 3d84eac0818099c9949035feb96bbe0346358504
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/21/2020
ms.locfileid: "86864200"
---
# <a name="instance-constructors-c-programming-guide"></a>Constructeurs d'instances (Guide de programmation C#)

Les constructeurs d’instances sont utilisés pour créer et initialiser toutes les variables membres d’instance quand vous utilisez l’expression [new](../../language-reference/operators/new-operator.md) pour créer un objet d’une [classe](../../language-reference/keywords/class.md). Pour initialiser une classe [statique](../../language-reference/keywords/static.md) ou des variables statiques dans une classe non statique, vous devez définir un constructeur statique. Pour plus d’informations, consultez [Constructeurs statiques](./static-constructors.md).  
  
 L’exemple suivant présente un constructeur d’instance :  
  
 [!code-csharp[csProgGuideObjects#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#5)]  
  
> [!NOTE]
> Pour plus de clarté, cette classe contient des champs publics. L’utilisation de champs publics n’est pas une pratique de programmation recommandée, car elle octroie à n’importe quelle méthode n’importe où dans un programme un accès sans restriction ni vérification aux mécanismes internes d’un objet. Les données membres doivent généralement être privées et doivent être accessibles uniquement via les propriétés et les méthodes de classe.  
  
 Ce constructeur d’instance est appelé chaque fois qu’un objet basé sur la classe `Coords` est créé. Un constructeur comme celui-ci, qui n’accepte aucun argument, est un *constructeur sans paramètre*. Toutefois, il est souvent utile de fournir des constructeurs supplémentaires. Par exemple, nous pouvons ajouter un constructeur à la classe `Coords` qui nous permet de spécifier les valeurs initiales pour les données membres :  
  
 [!code-csharp[csProgGuideObjects#76](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#76)]  
  
 Cela permet de créer des objets `Coords` avec des valeurs par défaut ou initiales spécifiques, comme suit :  
  
 [!code-csharp[csProgGuideObjects#77](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#77)]  
  
 Si une classe n’a pas de constructeur, un constructeur sans paramètre est généré automatiquement, et les valeurs par défaut sont utilisées pour initialiser les champs objet. Par exemple, [int](../../language-reference/builtin-types/integral-numeric-types.md) est initialisé à 0. Pour plus d’informations sur les valeurs par défaut de type, consultez [valeurs par défaut des types C#](../../language-reference/builtin-types/default-values.md). Par conséquent, comme le constructeur sans paramètre de la classe `Coords` initialise toutes les données membres à zéro, il peut être supprimé entièrement sans modification du fonctionnement de la classe. Un exemple complet d’utilisation de plusieurs constructeurs est fourni dans l’exemple 1, plus loin dans cette rubrique, et un exemple d’un constructeur généré automatiquement est fourni dans l’exemple 2.  
  
 Les constructeurs d’instances peuvent également servir à appeler les constructeurs d’instances des classes de base. Le constructeur de classe peut appeler le constructeur de la classe de base via l’initialiseur, comme suit :  
  
 [!code-csharp[csProgGuideObjects#78](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#78)]  
  
 Dans cet exemple, la classe `Circle` passe des valeurs représentant le rayon et la hauteur au constructeur fourni par `Shape` duquel `Circle` est dérivé. Un exemple complet d’utilisation de `Shape` et `Circle` s’affiche dans cette rubrique en tant qu’exemple 3.  
  
## <a name="example-1"></a>Exemple 1  
 L’exemple suivant illustre une classe avec deux constructeurs de classe, l’un sans argument et l’autre avec deux arguments.  
  
 [!code-csharp[csProgGuideObjects#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#4)]  
  
## <a name="example-2"></a>Exemple 2  
 Dans cet exemple, la classe `Person` n’a aucun constructeur, auquel cas un constructeur sans paramètre est fourni automatiquement, et les champs sont initialisés à leurs valeurs par défaut.  
  
 [!code-csharp[csProgGuideObjects#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#8)]  
  
 Notez que la valeur par défaut d’`age` est `0` et que celle de `name` est `null`.
  
## <a name="example-3"></a>Exemple 3  
 L’exemple suivant illustre l’utilisation de l’initialiseur de classe de base. La classe `Circle` est dérivée de la classe générale `Shape` et la classe `Cylinder` est dérivée de la classe `Circle`. Le constructeur de chaque classe dérivée utilise son initialiseur de classe de base.  
  
 [!code-csharp[csProgGuideObjects#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#9)]  
  
 Pour obtenir d’autres exemples sur l’appel des constructeurs de classe de base, consultez [virtual](../../language-reference/keywords/virtual.md), [override](../../language-reference/keywords/override.md) et [base](../../language-reference/keywords/base.md).  
  
## <a name="see-also"></a>Voir aussi

- [Guide de programmation C#](../index.md)
- [Classes et structs](./index.md)
- [Constructeurs](./constructors.md)
- [Finaliseurs](./destructors.md)
- [static](../../language-reference/keywords/static.md)
