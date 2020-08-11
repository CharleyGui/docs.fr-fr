---
title: Comment déclarer, instancier et utiliser un délégué-Guide de programmation C#
description: Découvrez comment déclarer, instancier et utiliser un délégué. Consultez les exemples qui couvrent C# 1,0, 2,0 et 3,0 et versions ultérieures.
ms.date: 07/20/2015
helpviewer_keywords:
- delegates [C#], declaring and instantiating
ms.assetid: 61c4895f-f785-48f8-8bfe-db73b411c4ae
ms.openlocfilehash: b741b3bc9c03faaa5fa2c01bd8f70d4be9b099c2
ms.sourcegitcommit: 7476c20d2f911a834a00b8a7f5e8926bae6804d9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/11/2020
ms.locfileid: "88063664"
---
# <a name="how-to-declare-instantiate-and-use-a-delegate-c-programming-guide"></a>Comment déclarer, instancier et utiliser un délégué (Guide de programmation C#)
Dans C# 1.0 et versions ultérieures, vous pouvez déclarer des délégués comme illustré dans l’exemple suivant.  
  
 [!code-csharp[csProgGuideDelegates#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#13)]  
  
 [!code-csharp[csProgGuideDelegates#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#14)]  
  
 C# 2.0 offre un moyen plus simple d’écrire la déclaration précédente, comme illustré dans l’exemple suivant.  
  
 [!code-csharp[csProgGuideDelegates#32](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#32)]  
  
 Dans C# 2.0 et versions ultérieures, vous pouvez aussi utiliser une méthode anonyme pour déclarer et initialiser un [délégué](../../language-reference/builtin-types/reference-types.md), comme illustré dans l’exemple suivant.  
  
 [!code-csharp[csProgGuideDelegates#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#15)]  
  
 Dans C# 3.0 et versions ultérieures, vous pouvez aussi déclarer et instancier des délégués à l’aide d’une expression lambda, comme illustré dans l’exemple suivant.  
  
 [!code-csharp[csProgGuideDelegates#31](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#31)]  
  
 Pour plus d’informations, consultez [expressions lambda](../../language-reference/operators/lambda-expressions.md).  
  
 L’exemple suivant illustre la déclaration, l’instanciation et l’utilisation d’un délégué. La classe `BookDB` encapsule une base de données de librairie qui tient à jour un inventaire des livres. Elle expose une méthode, `ProcessPaperbackBooks`, qui recherche tous les livres de poche dans la base de données et appelle un délégué pour chacun d’entre eux. Le type `delegate` qui est utilisé se nomme `ProcessBookDelegate`. La classe `Test` utilise cette classe pour imprimer les titres et le prix moyen des livres de poche.  
  
 L’utilisation des délégués favorise une bonne séparation des fonctionnalités entre la base de données de librairie et le code client. Le code client n’a aucune connaissance de la façon dont les livres sont stockés, ni de la façon dont le code librairie trouve les livres de poche. Le code librairie n’a aucune connaissance du traitement effectué sur les livres de poche une fois qu’il les a trouvés.  
  
## <a name="example"></a>Exemple  
 [!code-csharp[csProgGuideDelegates#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#12)]  
  
## <a name="robust-programming"></a>Programmation fiable  
  
- Déclaration d’un délégué.  
  
     L’instruction suivante déclare un nouveau type délégué.  
  
     [!code-csharp[csProgGuideDelegates#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#16)]  
  
     Chaque type délégué décrit le nombre et les types des arguments, ainsi que le type de la valeur de retour des méthodes qu’il peut encapsuler. Chaque fois qu’un nouvel ensemble de types d’arguments ou de types de valeur de retour est nécessaire, un nouveau type délégué doit être déclaré.  
  
- Instanciation d’un délégué.  
  
     Une fois que vous avez déclaré un type délégué, vous devez créer un objet délégué et l’associer à une méthode particulière. Pour cela, dans l’exemple précédent vous passez la méthode `PrintTitle` à la méthode `ProcessPaperbackBooks`, comme illustré dans l’exemple suivant :  
  
     [!code-csharp[csProgGuideDelegates#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#17)]  
  
     Cela crée un nouvel objet délégué associé à la méthode [statique](../../language-reference/keywords/static.md)`Test.PrintTitle`. De même, la méthode non statique `AddBookToTotal` sur l’objet `totaller` est passée comme dans l’exemple suivant :  
  
     [!code-csharp[csProgGuideDelegates#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#18)]  
  
     Dans les deux cas, un nouvel objet délégué est passé à la méthode `ProcessPaperbackBooks`.  
  
     Une fois un délégué créé, la méthode à laquelle il est associé ne change jamais. Les objets délégué sont immuables.  
  
- Appel d’un délégué.  
  
     Une fois créé, un objet délégué est généralement passé à un autre code qui appellera le délégué. Pour appeler un objet délégué, vous devez utiliser le nom de l’objet délégué, suivi des arguments entre parenthèses à passer au délégué. Voici un exemple d’appel de délégué :  
  
     [!code-csharp[csProgGuideDelegates#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#19)]  
  
     Vous pouvez appeler un délégué de manière synchrone, comme dans cet exemple, ou de manière asynchrone à l’aide des méthodes `BeginInvoke` et `EndInvoke`.  
  
## <a name="see-also"></a>Voir aussi

- [Guide de programmation C#](../index.md)
- [Événements](../events/index.md)
- [Délégués](./index.md)
